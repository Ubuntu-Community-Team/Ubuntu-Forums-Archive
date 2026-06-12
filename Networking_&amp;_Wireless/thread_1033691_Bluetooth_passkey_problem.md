---
title: "Bluetooth passkey problem"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by futuregps on 2009-01-07
Hi!!
I'm the new one here:) I spent a lot of time searching for answer of my problem,
I try to connect my Gps bluetooth adapter do my Ubuntu desktop,and the problem is that the Gps adapter using "0000" passkey , but the gnome-bluetooth-applet give mi some random passkeys and I can't pair it. For e.g. I click to set up ne device , then chose from list my bluetooth gps adapter and then  bt-applet show me message: "type this passkey: 8244"  and here is the problem , a can't use random passkey , I need "0000"'s Pin.

Bluetooth working good ,I can pair with mobile phone , but with cell is much easier because I can type random passkey .

Sorry for my English, it's not my mother tong.

So please Ubuntu's mates , what I should do to use four zeros as a passkey to pair my hardware.I'm using Ubuntu 8.10.
-------------------------------------------------
The simple answers are always the best: hciconfig hci0 auth
than just type: hcitool cc <addres od your adapter>
you'll see the popup to type pincode

simple -- this is known bug of bluez-utils in ubuntu 8.10

Bye and I hope that this post help someone.

---

