---
title: "Verizon Mobile Broadband: Activate without Windows"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by natefoo on 2010-06-03
Has anyone ever successfully activated a new mobile broadband device without VZ Access Manager in Windows (or OS X)?  Every single thread I'm finding (mostly here on ubuntuforums but also elsewhere) seems to suggest it cannot be done.

Here's my full story:

[http://ubuntuforums.org/showthread.php?t=1500039](http://ubuntuforums.org/showthread.php?t=1500039)

Since most people can move the card or USB dongle to another system, or they already have windows installed, activating on Windows is easy.  I'm not so fortunate since I have no other hardware which will work with this card, and I don't have a very convenient way to get Windows installed on this netbook.  I can maaaaaaaaybe make a bootable USB install of XP and do it that way, but this is a ridiculous pile of nonsense for something that should be a simple operation.  The defunct VZ Access Manager for Linux used to be able to do it, but it's completely incompatible with modern udev, and my attempts at hacking it have so far been failures.  Anyone have any ideas?  I tried having wvdial send *22899 and *22890, although I suspect these only work on voice devices.

---

### Post by alexfish on 2010-06-04
Don't know how to do this: but this may be of help
 
post #2
 [How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")
 

 at the foot of the page there is a link to the &#8220;CDMA AT command &#8220; reference manual ,with reference to Qualcomm and Verizon specific AT commands , if the device needs to be programmed then this would possibly best do through a serial terminal , if using Ubuntu then one of the best serial terminals is  { moserial }
 

 the only other alternate would be to load Virtual box and then install that &#8220;W?n???s&#8221;
 

 that's all I can help on
 

 Regards
 

 alexfish

---

### Post by natefoo on 2010-06-04
Ah thanks, I thought I had it with your docs, but alas, none of it worked.  Here's what it SHOULD be:

AT+WSPC=1,*Your Verizon ESID* (000000 if you're lucky)
AT+WMDN=*Your Verizon MDM number* (usually your phone number)
AT+WCMT=1

AT+WSPC=1,*ESID*
AT+WIMI=31000*Your Verizon MIN number* (usually your phone number)
AT+WCMT=1
ATD*22899;

I ended up installing Windows.  Reinstalling UNE now and my fingers are crossed...

---

### Post by natefoo on 2010-06-05
Success, for the record.  I still wish there'd been a way to activate w/o Windows.  Not even VirtualBox or BartPE would do it because the *(!@#$ Dell/Qualcomm Gobi driver installer returns "Incompatible platform" unless you're running Windows natively.

---

