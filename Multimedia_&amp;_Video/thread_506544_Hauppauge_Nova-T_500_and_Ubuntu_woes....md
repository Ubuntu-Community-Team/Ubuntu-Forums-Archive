---
title: "Hauppauge Nova-T 500 and Ubuntu woes..."
date: 2007-07-21
forum: Multimedia &amp; Video
---

### Post by dave_chimaera on 2007-07-21
Hi everyone, hope someone can help!

Basically I'm trying to build a MythTV HTPC around this card and Ubuntu and I can't get the damn thing working :( 

I've followed the instructions [Here]("http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux") (EfficientPC) to the letter but it just isn't coming up - following the test instructions [here]("http://parker1.co.uk/mythtv_dvb.php") just gives a 'tuning failed' error message. I know for a fact the card works - I got it up and working fine on the Windows partition on the system.

One thing that did concern me was the 'sudo make load' step - a number of the modules had errors (Unknown symbol in module, mostly)

Hope someone can help!

EDIT: Should add - I think its a driver issue rather than signal, aside from the fact it all works fine in Windows, Myth was complaining that it couldn't open the device - my guess is I screwed up somewhere - and I'd be very grateful if someone could tell me where :) 

Running 32bit Ubuntu Feisty on 3800+ AMDX2, 2gig DDR2 Asus nVidia 6150 MB

---

### Post by MrHippocampus on 2007-07-22
I recommend looking at the site which helped me get the same card working, [link]("http://www.omskakas.se/2007/01/howto-hauppauge-nova-t-500-pci-under-linux.html"), the instructions are different in quite a few ways but reading it should give you some ideas of what to try. Be sure to read through all of the comments at the bottom too as some contain useful info.

The chip used by this card is known to be very problematic, but if you persevere you should get it working :)

---

### Post by dave_chimaera on 2007-07-23
Funnily enough I found that same guide last night and got it working - thanks!

---

### Post by ge00rg on 2007-07-23
dave_chimaera: Could you post any more details on your solution to this problem please?  I'm stuck with the same problem and can't get the card working...  Any help would be much appreciated.

Cheers

George

---

### Post by dave_chimaera on 2007-07-23
I followed this guide [Here (efficientpc.co.uk)]("http://wiki.efficientpc.co.uk/index.php/Install_Nova-T_500_On_Ubuntu_Linux") to set it up with a couple of minor changes - first I did a sudo make unload before the sudo make load step and I also did a reboot (the changes made in /etc/modprobe.d/options didn't apply til then). 

On reboot check that /sys/module/dvb_usb_dib0700/parameters/force_lna_activation contains a 1 rather than a 0.

I then did a test following this guide [here]("http://parker1.co.uk/mythtv_dvb.php") but I had to make my own channel config guide - the nearst one supplied (uk-EmleyMoor) wasn't good enough to get a signal so made one for uk-Sheffield and ran the scan and that was it - worked perfectly. Only took 24 hours and four complete ubuntu installs to crack it :) After that I installed Myth and went through the install with no difficulties at all - just gotta get MythVideo and my remote working properly now :)

If you're trying to do the DVB testing and not having much luck I'd check the initial scan config file - there wasn't the right one for me so I had to make my own, but its possible the one for yours, if present, may be out of date. If so you can get the appropriate scan info from one of the DVB websites for your transmitter.

---

