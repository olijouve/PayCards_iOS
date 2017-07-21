PAY.CARDS RECOGNIZER
===================

[Source Code](https://github.com/faceterteam/PayCardsRecognizer_iOS_Source)

[iOS SDK](https://github.com/faceterteam/PayCardsRecognizer_iOS_Source)

Sample app
----------

See PayCardsRecognizerExample project

Installation
------------

##### If you use [CocoaPods](http://cocoapods.org):

```ruby
pod 'PayCardsRecognizer'
```

##### If you don't use CocoaPods:

1. Download the latest version of the SDK (PayCardsRecognizer.framework).
2. Add the PayCardsRecognizer.framework to your Xcode project.
3. Add the PayCardsRecognizer.framework to Embedded Binaries.

Usage
------------

```swift
import PayCardsRecognizer

class RecognizerViewController: UIViewController, PayCardsRecognizerPlatformDelegate {

	var recognizer: PayCardsRecognizer!
	
	override func viewDidLoad() {
	    super.viewDidLoad()
	    recognizer = PayCardsRecognizer(delegate: self, resultMode: .sync, container: self.view)
	}
	
	override func viewWillAppear(_ animated: Bool) {
	    super.viewWillAppear(animated)
	    
	    recognizer.startCamera()
	}
	    
	override func viewDidDisappear(_ animated: Bool) {
	    super.viewDidDisappear(animated)
	    
	    recognizer.stopCamera()
	}
	
	// PayCardsRecognizerPlatformDelegate
	
	func payCardsRecognizer(_ payCardsRecognizer: PayCardsRecognizer, didRecognize result: PayCardsRecognizerResult) {
		result.recognizedNumber // Card number
		result.recognizedHolderName // Card holder
		result.recognizedExpireDateMonth // Expire month
		result.recognizedExpireDateYear // Expire year
	}

}
```