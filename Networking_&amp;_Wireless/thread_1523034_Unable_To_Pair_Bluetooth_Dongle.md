---
title: "Unable To Pair Bluetooth Dongle"
date: 2010-07-03
forum: Networking &amp; Wireless
---

### Post by prasenjit007 on 2010-07-03
Hello Guys..
I have a laptop with no bluetooth on it.So i bought a bluetooth dongle.It works flawlessly under windows but i am having a problem with it under Ubuntu (As well as other Linux distros). As soon as i plug the dongle i see a bluetooth icon in the Notification Area.
When i click on it and choose setup new device....its scans and shows all the bluetooth devices like my Nokia 5800 xpressmusic cell phone but when i try to pair it simply fails....
I have tried all the Pin codes available and even tried the custom pin option but still no success. By the way right now i am using Ubuntu 10.04..i have also tried it with other linux OS but still the problem remains.... 
Any help would be greatly appreciated....
Thnks in advance....

---

### Post by hansdown on 2010-07-03
Hi prasenjit007.

Have you installed bluetooth?

It's in synaptic package manager.

system> administration> synaptic package manager.

---

### Post by artemyv on 2010-07-03
> **prasenjit007 said:**
> Hello Guys..
I have a laptop with no bluetooth on it.So i bought a bluetooth dongle.It works flawlessly under windows but i am having a problem with it under Ubuntu (As well as other Linux distros). As soon as i plug the dongle i see a bluetooth icon in the Notification Area.
When i click on it and choose setup new device....its scans and shows all the bluetooth devices like my Nokia 5800 xpressmusic cell phone but when i try to pair it simply fails....
I have tried all the Pin codes available and even tried the custom pin option but still no success. By the way right now i am using Ubuntu 10.04..i have also tried it with other linux OS but still the problem remains.... 
Any help would be greatly appreciated....
Thnks in advance....

My bluetooth dongle works out-of-the box...
Please try the following:
System -> Preferences -> Bluetooth

 Setup new device

Select your device and click Forward

You should see the pin-code to be entered in your device.

AS I understand - you do not see it?
Or you do not see the prompt to enter the code on your phone?

In any case - open the terminal and print dmesg

post here the last several lines that deal with the bluetooth device handling.

Thanks

---

