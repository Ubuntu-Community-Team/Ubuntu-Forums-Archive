---
title: "Screen Image Blown to Bits! DVI D, 13.04"
date: 2013-09-02
forum: Multimedia Software
---

### Post by AnotherBrian on 2013-09-02
I leave my system running, having watched perhaps a video, and I leave.  Later when I return, the system is sometimes locked up and the monitor displays bits and pieces of prior interactions.  For example it displays  "Password: *******" and then in another location it might display something else. Random characters are also present. I am unable to recover the system via say through ctrl-alt-1 or other techniques. I found nothing in the logs at /var/log that suggested a problem.

The fact that this problem occurs when I am away from the system makes me wonder if this is related to a suspend mode / power management issue. 

I am using a new GEFORCE GT640 2 Gig video card and a new monitor (2560x1440) using DVI D.  
It is a brand new 13.04 clean install.  The installation process picks x.org nouveau (open source) display driver.  
Tried to use the tested proprietary video driver but ran into problems there too (Don't recall the issues).  

Along the way on this too I tried numerous techniques and got the system into a funky mode where booting up failed and would result in a test mode being displayed. First there would be grey scale screen, followed by colored verticle wide stripes, etc which was repeated.  I suspected that the video card was in some sort of test mode.  

Suggestions on debugging the problem?!  Defective video card? Need additional memory for video card?

---

### Post by Yellow Pasque on 2013-09-02
If it only occurs with nouveau driver, then I would chalk it up to the nouveau driver, which struggles with power management.
Personally, for such a new card, I would use latest nvidia driver from xorg-edgers PPA:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-325
```
I use the nvidia 325.x driver for my 8400GS on Debian. It works well (though I can't comment on suspend/resume since I don't use it).

---

### Post by AnotherBrian on 2013-09-04
Thanks for the response.  Learned some more and so will share. 

My monitor is the QNIX 2710, a low priced DVI D monitor.   The host computer determines the type of monitor attached to itself via Extended Display Identification Data (EDID).  A cyclic redundancy number is provided by the monitor so that the host can determine if the data it received is same known to the monitor.   Turns out the manufacturer has the wrong CRC programmed into the monitor.  The xorg software discovers this fact and then makes various incorrect assumptions about the monitor. Xorg emits error messages mentioning that the EDID CRC number is invalid in the Xorg log file located at /var/log.  Also found a log that said xorg was catching a sig 6 and crashing.   

Interestingly it is reported that microsoft os does not perform the crc verfication resulting in the monitor working just fine in the windows enviroment.

Tried using your suggestions resulting in the video card or the monitor omitting screen testing patterns. 

Doing a search on qnix and xorg and you can find configuration files xorg.conf which can be used by xorg for the qnix monitor.  The config file is placed in /etc/X11 directory.  The presence of the config file results in xorg not checking the CRC number (and probably bypasses the entire EDID interface).  This is confirmed by the fact that EDID CRC issues are no longer mentioned in the xorg log file.  Using the config file worked with a new 13.04 install updated to current fixes.   But I was still getting sig 6 crashes. 

The config file did not work with the software updates that you suggested and instead got the test pattern. 

Now running with clean 13.04 install with updates without an xorg.conf file.  Runs fine with no sig 6 crashes and no xorg.conf file. Maybe some fixes were in the works and are now installed. 

Also interesting is that it is reported that this monitor can be run at an accelerated refresh rate beyond the advertised speed by using xorg.conf files.  

Thank you for your input, it assisted in me further understanding the issue.

---

