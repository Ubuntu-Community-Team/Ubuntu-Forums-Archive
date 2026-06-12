---
title: "Bluetooth and Bose Soundlink"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by dionp2 on 2010-04-04
Hi, 

I've bought a Bose sound link and it's been working fine with ubuntu up until now. I go up into the bluetooth applet in the top RHS of the screen and click 
--> Set up new device.

It finds my mobile phone just fine (Nokia N95) and transfers files to it no probs, but with the Soundlink system it occasionally flashes up the Bose Soundlink like it should to find it but then it disappears in about half a second and I can not continue to connect to it. 

I know it was working fine all day up till an hour ago. I had been trying to connect to it from my mobile phone to stream from there and the phone would not see the Soundlink. This when I thought I'd test the reconnection of the device from Ubuntu because it had been flawless up until now. I deleted the Soundlink connection from the Bluetooth menu in Ubunutu and tried to re-establish a connection. Then it just does what I described above.

Steps I've taken
1. Removed battery from Soundlink and rebooted the laptop. Once it rebooted I then put the battery back in. Scanned for new devices, pressed the plus or little radio symbol on the bose remote. Same as above.

2.Tried on another computer. Same with the same Targus ultramini USB Bluetooth adaptor (part number ACB74AU) 

3. Have turned off bluetooth from the icon --> pulled out the USB Bluetooth adaptor and put it back in. --> Same issue.

4. 
From terminal -->
hcitool scan 
It finds the mobile phone just fine but not the Soundlink.

Specs :
Ubuntu 9.10 - the Karmic Koala
Nokia N95
Targus ultramini USB Bluetooth adaptor (part number ACB74AU)
Toshiba A50 laptop computer



Anyone have any ideas?

---

### Post by dionp2 on 2010-04-04
OK, it's a case of RTBM.

The wireless connection button on the remote control, well you have to hold it down CONTINUOUSLY whilst connecting to it from any Bluetooth device. Doing this also seems to reset the wireless connectivity from the Soundlink. Actually this is not in the manual that came with the product. It's in the trouble shooting guide you get from their website.

[http://owners.bose.com/controller?event=VIEW_STATIC_PAGE_EVENT&url=/products/multimedia/soundlink/index.jsp](http://owners.bose.com/controller?event=VIEW_STATIC_PAGE_EVENT&url=/products/multimedia/soundlink/index.jsp)

---

