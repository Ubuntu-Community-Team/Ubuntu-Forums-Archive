---
title: "Dialup help needed"
date: 2005-01-04
forum: Networking &amp; Wireless
---

### Post by Kaddo on 2005-01-04
I'm just about ready to install my new Ubuntu.
I've been warned there will be issues, starting with the modem.
From what I could understand, the easiest is with an external.
So, I picked up one. It's a 56K US Robotics, serial.
The WinXP recognized it and works well on that platform without any tweaking. 
What will I need to do in order to make it also work with Linux, once installed? 
Your helpful comments and suggestions will be most appreciated.

---

### Post by twisted_steel on 2005-01-04
From looking at the US Robotics [site]("http://www.usr.com/support/s-main-menu.asp"), it looks like there is a very good chance your modem would be supported.  One of the [recent modems]("http://www.usr.com/support/product-template.asp?prod=5686e"), for example, mentions a firmware update utility for Linux. If you plug the modem into your serial port before booting into Ubuntu, it should find it and put the device in /dev/modem. Otherwise, it may reside in /dev/ttyS0, assuming it is connected to the first serial port.
  
  Assuming it is properly detected, you can then follow the [guide]("http://www.ubuntuforums.org/showthread.php?t=6319") on the forums or the [howto guide]("http://www.ubuntulinux.org/wiki/DialupModemHowto") on the wiki.

---

### Post by Kaddo on 2005-01-08
[QUOTE=twisted_steel]From looking at the US Robotics [site]("http://www.usr.com/support/s-main-menu.asp"), it looks like there is a very good chance your modem would be supported.  One of the [recent modems]("http://www.usr.com/support/product-template.asp?prod=5686e"), for example, mentions a firmware update utility for Linux. If you plug the modem into your serial port before booting into Ubuntu, it should find it and put the device in /dev/modem. Otherwise, it may reside in /dev/ttyS0, assuming it is connected to the first serial port.
  
  Assuming it is properly detected, you can then follow the [guide]("http://www.ubuntuforums.org/showthread.php?t=6319") on the forums or the [howto guide]("http://www.ubuntulinux.org/wiki/DialupModemHowto") on the wiki.[/QUOTE]

Success!
Thank you, Twisted Steel.
Viki's instructions worked very well.
I would like to monitor the speed of my connection, 
the Modem Lights doesn't seem to be doing it. 
Any hints, please?

---

### Post by tiiim on 2005-01-08
[QUOTE=Kaddo]Success!
Thank you, Twisted Steel.
Viki's instructions worked very well.
I would like to monitor the speed of my connection, 
the Modem Lights doesn't seem to be doing it. 
Any hints, please?[/QUOTE]
 im guessing it be
applications ->sys. tools ->network tools

---

### Post by twisted_steel on 2005-01-10
Selecting Modem Interface in the Network Device dropdown gives the stats for your dialup connection.  Unfortunately it says 'not available' for my link speed, but this could be because I have a winmodem.

---

### Post by Kaddo on 2005-01-11
[QUOTE=twisted_steel]Selecting Modem Interface in the Network Device dropdown gives the stats for your dialup connection.  Unfortunately it says 'not available' for my link speed, but this could be because I have a winmodem.[/QUOTE]

Also not available on mine. I thought of changing the string, but can't find that either.

I'm not able to read the speed, but it is noticeably lower than when using the same modem on Windows. 
After the v. 92 update, I'm doing 45.2 Kbps on that (up from 44), which is reasonable, I suppose. Why wouldn't be the same under Linux? 

How did you get a Winmodem to work on Linux?

---

### Post by twisted_steel on 2005-01-11
I don't know why it would be slower in Linux. For me the speed seems the same, although I haven't done any speed tests to figure out if it's true.
  
 Just to clarify, a winmodem is an internal software modem. In my case it is the one installed in my laptop. A HOWTO on the forums has been set up here:
  [http://www.ubuntuforums.org/showthread.php?t=6361]("http://www.ubuntuforums.org/showthread.php?t=6361")

---

