---
title: "Print Share Is Not Accessible"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by digiPixel on 2009-03-22
For some reason whenever I click on the "Verify..." button in the "Printing" window for adding a new remote printer, the following message appears:

    **This print share is not accessible**

This problem does not appear on other machines with Ubuntu or Xubuntu. There is a security issue somewhere with CUPS but I have been unable to find out what it is. Does anyone have any idea as to what the problem is and its solution?

---

### Post by jbeiter on 2009-05-05
Any luck on this? I've been trying to share this printer for weeks myself. Other Ubuntu systems get this error and Mac systems just print and get paused.

Man I hate cups. I wonder if the old unix lp system still works on Linux. It was a bear to configure but at least it worked.  Cups has nice GUIs that don't bloody work.

---

### Post by atsab on 2010-08-17
Bump!
Any one have any info on this im having the same problem
ubuntu 10.04

---

### Post by b110datto on 2010-08-17
I have this problem too.
But mine is printing to a shared printer on a windows box.
I thought it must be a windows problem as I havn't done any updates to my Ubuntu PC's.
Havn't had a chance to look into it yet.
We are using 9.1 KK and 10.4 LL both no longer print.

---

### Post by willz06jw on 2010-08-20
Howdy,

Use the config-system-samba package (it's a samba GUI). It will make sure you don't overlook some small sambatism. 

If you search in the Ubuntu Software Center for Samba, it will be one of the ones listed (it will be listed as just "Samba" stragely). 

This will put a link to the GUI in your system/administration menu.

I removed some of the security and everything started working hunkey-dory.

Have a good one,
Will from Texas

---

### Post by Jossboss on 2011-10-12
On kubuntu this can happen because the system converts spaces in the share name to '20's eg if one clicks on the browse name for HP Color LaserJet CM1312 MFP Series PCL 6 the printer configuration echos HP20ColorLaserJet20CM131220MFP20Series20PCL206
you can't edit this at the time of entry, but if you click forwards a couple of times then after you complete the wizard go back and edit the device URI on the printer settings tab and replace the 20s with spaces. After that things work.

---

### Post by ahrambc on 2012-06-10
> **Jossboss said:**
> On kubuntu this can happen because the system converts spaces in the share name to '20's eg if one clicks on the browse name for HP Color LaserJet CM1312 MFP Series PCL 6 the printer configuration echos HP20ColorLaserJet20CM131220MFP20Series20PCL206
you can't edit this at the time of entry, but if you click forwards a couple of times then after you complete the wizard go back and edit the device URI on the printer settings tab and replace the 20s with spaces. After that things work.

 Thank you very much.  It works fine with me

---

### Post by marco07 on 2012-06-10
Am experiencing a similar problem as OP. Have spent almost entire weekend googling, reading many suggestions and following various samba instructions to no avail. Please, if anyone finds a solution, post it here and let us get rid of this frustrating issue.
Thanks!****

---

### Post by ahrambc on 2012-10-01
> **marco07 said:**
> Am experiencing a similar problem as OP. Have spent almost entire weekend googling, reading many suggestions and following various samba instructions to no avail. Please, if anyone finds a solution, post it here and let us get rid of this frustrating issue.
Thanks!


Remove all the spaces from the name of the Windows shared printer, and then Linux will identfy it easly.

---

