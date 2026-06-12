---
title: "Wireless Question"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Customprofile on 2010-07-22
I have searched the forums and from I can read I have not seen anything on two items I have a questions about.
 
I have: 
Dell Studio 1737, 
Ubuntu 10.04 LTS,
2.6.32-23.generic x86_64, 
 
Intel WiMAX Link 5150 and ITE IT8512 CIR Receiver, how can I tell if the drivers were installed for these two items and or they are working correctly? When I installed Ubuntu every thing on the laptop seems to work just fine but sometimes on boot this message appears just before the login screen and I think it has to do with the ITE IT8512 CIR Receiver:
 
[ 14.319165] i2400m_usb 2-5:1.0: 'RF Concrol' (0x4602) command fail: -84 - invalid state (3) 
 
 
 
The WiMAX use to display this message but now it does not. Below are the Windows drivers for these two items from Dells' site if you need then for anything, as I do not know if you need them to make or edit a driver for Ubuntu. Thank you for your time.
 
ITE IT8512 CIR Receiver
[http://tinyurl.com/2bogtq6](http://tinyurl.com/2bogtq6)
 
Intel WiMAX Link 5150
[http://tinyurl.com/293mwyd](http://tinyurl.com/293mwyd)

---

### Post by Customprofile on 2010-07-23
If I need to post any information from Ubuntu please let me know and let me know the code to produce the information.
I am sorry from not knowing Ubuntu, all I have ever known is Windows and when I installed Ubuntu the other day is my first experience with Linux. Anyway thank you for your time and help and please be patient with me.

---

### Post by dca on 2010-07-23
So, the WIMAX is the broadband access chip?

I guess if you right-click on the network-manager applet on top panel, choose 'Edit Connections', and click on the 'Mobile Broadband' tab.  If it displays Clearwire or Sprint or whatever maybe it's working?
 
Sorry, just throwing it out there, these newer Dell laptops have some of the weirdest cards thrown in.  Heck, one uses a Dell wireless card that uses a Broadcom chipset that I never even new existed...

---

### Post by Customprofile on 2010-07-23
Yea the WiMAX seems to be working it is just the ITE IT8512 CIR Receiver that shows that message(as listed above) right before the login screen. So I need to know how to check it or see if the driver is installed or what I need to to. Thank you.

---

### Post by dca on 2010-07-23
Don't know much about that CIR Receiver, so, is the InfaRed in the 'off' state perhaps and that's throwing the error?

---

### Post by dca on 2010-07-23
If there's no known Linux drivers available for that device does it at least allow you to disable in BIOS?
 
[http://en.community.dell.com/support-forums/laptop/f/3518/t/19280434.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/t/19280434.aspx)
 
that guy above in hyper-link couldn't get it to work either...

---

### Post by Customprofile on 2010-07-23
I was not able to turn it off in the BIOS, but if there is not a driver for it I am ok as I do not have an infrared deviced for it anyway. I was just wanting to get it all installed. So it is no really big deal as long as it will not hurt the operation of the Ubuntu install and as long as it will function then I am good...
 
Thanks DCA!

---

