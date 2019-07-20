# Network-Connectivity

## Network Connectivity is new framework for check your Network Connection. 

Added Some screens here.

![](https://github.com/pawankv89/Network-Connectivity/blob/master/images/screen_1.PNG)
![](https://github.com/pawankv89/Network-Connectivity/blob/master/images/screen_2.PNG)

## Usage

``` swift 


import UIKit
import Network

class ViewController: UIViewController {

@IBOutlet weak var wifiImageView: UIImageView!
@IBOutlet weak var wifiStatusLabel: UILabel!

override func viewDidLoad() {
super.viewDidLoad()
// Do any additional setup after loading the view.

//How to check for internet connectivity using NWPathMonitor
let monitor = NWPathMonitor()

let queue = DispatchQueue(label: "Monitor")
monitor.start(queue: queue)

//let cellMonitor = NWPathMonitor(requiredInterfaceType: .cellular)

monitor.pathUpdateHandler = { path in
if path.status == .satisfied {
print("We're connected!")

DispatchQueue.main.sync {
self.wifiImageView.image = UIImage(named: "wifi")
self.wifiStatusLabel.text = "We're connected!"
self.wifiStatusLabel.textColor = .green
}

} else {
print("No connection.")

DispatchQueue.main.sync {
self.wifiImageView.image = UIImage(named: "wifi_not")
self.wifiStatusLabel.text = "No connection."
self.wifiStatusLabel.textColor = .red
}
}

print(path.isExpensive)
}
}


}



```

## License

This code is distributed under the terms and conditions of the [MIT license](LICENSE).

## Change-log

A brief summary of each this release can be found in the [CHANGELOG](CHANGELOG.mdown). 
