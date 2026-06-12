---
title: "Laptop with no ethernet and no wireless either"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by #1 fisherman on 2010-09-11
Hello i  am new to ubuntu forums.I am trying to get this laptop`s wireless to connect to my router or any wireless connection. It does not have an ethernet port,so it has been tough.I have been reading everything i can,but cant get it to work.Maybe I need a different wireless card or a usb adapter.The one I have is a Texas Intruments acx100.Can  anyone tell me if this should work.I have ndiswrapper installed and the windows driver for it but still nothing.Help would be appriciated.

---

### Post by Drigy on 2010-09-11
I believe you have a HOW TO on the following site: [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/) .
Also you have a Wiki on the same site for a more detailed information. The thing is that i have a same problem with a different USB WiFi device.

As we are both referring to a same problem with a different hardware i will post my question here:
I have a Canyon CNP-WF581N3 and i found drivers on tis site: [http://www.canyon-tech.com/products/connectivity/wireless/CNP-WF518N3#pr-switcher](http://www.canyon-tech.com/products/connectivity/wireless/CNP-WF518N3#pr-switcher)
Here is where I found Linux drivers with a detailed instructions to install, but not detailed enough for me :D or plain enough :D As I 'make' i get some errors.

---

### Post by #1 fisherman on 2010-09-11
I just ran the command ndiswrapper -l 
it says tiacxln driver installed 
device {104c:8400} present 
so it detects the device and thinks it has the right driver installed right.
should it detect any wirless connection in range weather it connecs to it or not.
I am not real computer literatebut trying to be 
thanks for the reply

---

### Post by Drigy on 2010-09-12
I think you should be able to see available wireless networks, even if not connected. But when you install the drivers you should most likely exit Network manager with 'pkill nm-applet'. Nut I am no expert neither.

And try 'ifconfig' in terminal too, to see if your wlan0 is available

---

### Post by MaindotC on 2010-09-12
If you are using the shell then the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) shows you precisely how to configure your wireless adapter.  You'll have to associate the adapter with an access point's SSID, ESSID, and any special protection that exists on the wireless network.  If you are having difficulty with this, please be sure to let us know precisely where you are having difficulty and post any output that is different than what the guide suggests.

---

