---
title: "Using NetworkManager for BT - cell phone tethering"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by harisund on 2010-03-17
What I currently do is run this script - 

```

rfcomm release 0
CHANNEL = `sdptool search --bdaddr=00:21:FE:A5:C9:4A dun | grep Channel | cut -c14`
rfcomm bind 0 00:21:FE:A5:C9:4A ${CHANNEL}
wvdial e71bt

```

And my /etc/wvdial.conf is configured for AT&T connection here in the US. 

Question is, is there anyway I can integrate it with NetworkManager, instead of having to run this script? 

There's a "Broadband" option on NetworkManager, but I am not able to get it to recognize my cell phone as a modem. The bluetooth applet only allows for file transfer :(

---

### Post by PaulEdwards on 2010-03-19
I am also keenly interested in this functionality.

I have a rooted T-Mobile G1 running Android 2.1 (works great BTW).
Whenever I enable the Internet Tethering via USB option on the G1 and connect it to my Fujitsu P-1510D TabletPC (running Ubuntu 9.10 Karmic Koala) with the USB cable, NetworkManager automagically establishes a Wired Network connection and I can browse the web instantly.

I do have [Wireless Tether for Root Users]("http://code.google.com/p/android-wifi-tether/") on my phone which facilitates the phone becoming a BlueTooth PAN. I set it up properly, and can even get the tablet to connect to the PAN using Blueman Device Manager, but browsing to or pinging google.com fails.

I did setup a Mobile Broadband connection, but I don't know how to activate it. I suspect this may be the key.

Please help me determine what I am doing wrong.

Thanks in advance.

---

### Post by alexfish on 2010-03-20
Hi all

does this  help Ubuntu Linux on the Move


[LIST]
[*][Connecting  via Mobile Telephones with inbuilt modems ]("http://www.pcurtis.com/ubuntu-mobile.htm#mobile_telephone")
[LIST]
[*][Bluetooth  connection to a Phone Modem]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth")
[LIST]
[*][Bluetooth  - basics and pairing]("http://www.pcurtis.com/ubuntu-mobile.htm#bluetooth_basic")
[*][Creating a  Bluetooth Phone Dial-Up Network Device]("http://www.pcurtis.com/ubuntu-mobile.htm#bt_device")
[/LIST]
[*][GPRS Access via  Mobile Phone]("http://www.pcurtis.com/ubuntu-mobile.htm#gprs")
[*][Using Windows Mobile  Devices as Modems]("http://www.pcurtis.com/ubuntu-mobile.htm#xda")
[/LIST]
[/LIST]
regards

alexfish

---

### Post by t0p on 2010-03-23
Oh my word, it looks like this is an issue that has yet to be solved.

Let me add my voice to this, as I too require the ability to use my phone as bluetooth modem *through network manager*.  I am fond of my privacy, and I like to use VPN services when browsing.  If I use my cellphone as modem over usb datacable, network manager recognises the phone as a "wired connection" and I can connect through network manager and use VPNs as I please.  But if I connect to the phone over bluetooth, network manager doesn't see it so I have to use ppp and VPN is unavailable.

Or maybe I've got it wrong?  Maybe there is a way to use a dial-up connection with VPN?  If so, please enlighten me.  In the meantime: Bah! Humbug!

---

