---
title: "Dialing a connection on cell phone, over bluetooth?"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by wizardfait on 2009-06-06
I know this is possible under windows, as once you link a phone to a computer over bluetooth (That supports this feature of course) that it becomes a "Standard modem over Bluetooth link" which you can then create a dial-up connection using that modem, and all is well.

How do you do this under Ubuntu? I attempted it, and I could not find a way to create a dial-up connection, let alone tell it to use a specific device.

I connected my phone over bluetooth so I could navigate it, and that worked properly. I went into the network manager, and set up a mobile broadband connection... Which worked when I plugged my phone in to USB, but not over bluetooth. Do we NOT have that functionality in Linux/Ubuntu? Or am I merely not doing something right?

---

### Post by EmoDx on 2009-06-06
I was looking at the same thing this morning. I connected my bluetooth adapter and was able to pair with my phone. I went to the bluetooth manager icon on the top tool bar and enabled all the functions. But there isn't native DUN functionality in the manager.

I tried going to System -> Administration -> Network. I tried every possible combination of settings in Point to Point networking. No luck there.

I downloaded Gnome PPP. I tried every possible combination there also. No luck.

I am now thinking the OS doesn't recognize the phone as a Bluetooth modem. There isn't an indication in the phone or the OS that the phone is even being accessed as a modem.

I am off to use the search function to see if I can find anything useful.

---

### Post by wizardfait on 2009-06-06
If you find anything, please let me know! :)

---

### Post by GeorgeVita on 2009-06-06
Hi **wizardfait** & **EmoDx**,

I cannot directly help but I found a relative HowTo:
**[http://ubuntuforums.org/showthread.php?t=1177608](http://ubuntuforums.org/showthread.php?t=1177608)**

Some technical points there are interesting.

Regards,
George

---

### Post by wizardfait on 2009-06-06
Lol, I think you made a mistake, that's a link to THIS thread...

---

### Post by Heero_Yuy_X on 2009-11-29
I googled this a bit, I don't remember where I found it but here is the gist of it :

Install Blueman, pair it with your phone and choose dialup service.
Go to Network connections, choose Mobile Broadband, add and setup your connection as you would a USB one..

Most sites only stated how to install blueman and didnt really show how to use it :(

I think what blueman does is simulate a usb connection or probably integrate with Network Connections... 

Hope I helped ;)

Edit : Forgot to mention that blueman replaces your default bluetooth manager! You could open it from System > Preferences > Bluetooth Manager

---

