---
title: "HOWTO: Sierra Wireless USB 598"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by CRCarl on 2009-04-22
This modem almost, nearly works with NetworkManager Applet 0.7.0 right out of the box, just one tweak - 

You need to modify your /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi file.


```
sudo vim /usr/share/hal/fdi/information/10freedesktop/10-modem.fdi
```

find the section starting on line 220

> <!-- Sierra Wireless -->
<match key="@info.parent:usb.vendor_id" int="0x1199">
<!-- EM5625,2x MC5720,2x MC5725,AirCard 595,AirCard 597E,USB Dongle 595U,AirCard 580, Compass 597 -->
<match key="@info.parent:usb.product_id" int_outof="0x0017;0x0018;0x0218;0x0020;0x0220;0x00 19;0x0021;0x0120;0x0112;0x0023;***0x0025***">
<match key="@info.parent:usb.interface.number" int="0">
<match key="serial.port" int="0">
<append key="modem.command_sets" type="strlist">IS-707-A</append>
</match>
</match>
</match>

Add the product_id 0x0025 as above. Save the file, exit. Remove the modem, re-insert. You should see a CDMA connection option under Mobile Broadband when you click on the NetworkManager Applet.

Craig

---

### Post by Ariccanfly on 2009-08-13
after doing above i also had to download a stupid program from sierrawireless.com/support
and run it in win or mac to "register my modem" or something.

dmesg is your friend, I could tell that registering it fixed it right away.
I think I had to unplug it and disable wireless or somthing picky like that

Anyways I'm using it now to post this. ubuntu 9.04, acer-one net book.

:guitar:

---

### Post by tezeutextil on 2009-08-25
I have just bout an USB Key Sierra Wireless 598 with telus mobility.
Here is how I have managed to make it work:
1. Upgrade to ubuntu 9.04 (The previous version was giving lots of headake)
  9.04 has recognized the card automatically.
I just had to enter the 

phonenumber: #777

user name: "phonenumbertoconnectto"@1x.telusmobility.com    
Ex: [email]4383520000@1x.telusmobility.com[/email]

password: "imei of your card" ex: 096xxxxxxxxxx

Afther that it was not working so I had to Install it on a Window PC and activate it.
The Win instalation kit  is on the card.
After the instalation you have to Activate the card. AutoActivation works just fine.

After that pluging the card back into Ubuntu worked just fine.

Good luck, and thank you Ubuntu team.

---

### Post by billzeeabob on 2009-09-07
Have any of you done a speed test?

---

### Post by levesqu6 on 2010-11-15
this method worked well for me in 10.04

download: 0.89mb/s
upload:0.99mb/s
ping:30ms

Sprint is my provider. I think it would be faster if it wasnt the middle of the day.

---

