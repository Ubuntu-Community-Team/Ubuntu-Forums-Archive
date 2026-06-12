---
title: "Help! Newb with X31 Thinkpad and Ubuntu 6.06"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by landwomble on 2006-07-13
Hi All,
I'm a complete linux newbie, but have taken the plunge on a laptop,  with a view to migrating all my boxes over once I'm happy.
I've installed 6.06 successfully on my IBM Thinkpad X31 but have a few issues.
What I'd *love* is to get XGL/Compiz working.  The X31's got an ATI Radeon Mobility M6 LY, so it has some 3D ability but every install I've done of the fglxr ATI drivers has killed x stone dead so on booting I get a blue screen telling me that my .conf file's bust.  Not knowing enough to fix this, I've had to do a reinstall at that point, aaargh!
glxgears etc *appear* to have 3d acceleration already though using the standard driver that comes with 6.06.

Couple of questions:
Are the ATI drivers necessary for XGL/Compiz?
If so, can someone point me to an idiot's guide to installing them?
Is there a nice, simple way to install XGL/Compiz that's safe for a noob, and how can I back out of the changes if it's borked?
Anyone got a good suggestion for backing up my installation generally - e.g. to USB DVDRW or similar?  It's a dual boot laptop with the missus' install of XP so I'd only want to backup the linux partitions - presumably on restore GRUB wouldn't notice the difference?

Also, my mark 1 3Com Officeconnect wifi card doesn't play ball.  It's listed in installed hardware via iwconfig or iwlist (I forget!) but just won't associate with my access point with or without wep.  Tried with standard Ubuntu driver and ndiswrapper and it's not having it - seen a few posts about dapper being funny with wireless.  Any pointers?  
Alternately, any pointers on PCMCIA wifi cards that work out of the box?
Last question (promise!) is if I buy another wifi card and insert it into my current install, will Ubuntu autodetect the card and install default drivers a la Windows or is there some incantation I need to do?

All help appreciated!

Cheers all.

---

### Post by Maggot on 2006-07-13
> **landwomble said:**
> Couple of questions:
Are the ATI drivers necessary for XGL/Compiz?

I'm gonna have to say "Yes" but not 100% sure.

> If so, can someone point me to an idiot's guide to installing them?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> Is there a nice, simple way to install XGL/Compiz that's safe for a noob, and how can I back out of the changes if it's borked?

Never used this but might help:  [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

---

### Post by landwomble on 2006-07-13
[QUOTE=Maggot;1249995]I'm gonna have to say "Yes" but not 100% sure.


[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Cheers!
Tried the link above and ended up hosing X, then reinstalling.  If it screws my X config, is there an easy way of rolling back the changes?

---

### Post by Maggot on 2006-07-13
> **landwomble said:**
> Cheers!
Tried the link above and ended up hosing X, then reinstalling.  If it screws my X config, is there an easy way of rolling back the changes?

If you are talking just about the ATI drivers, then you should be able to backup your /etc/X11/xorg.conf file BEFORE attempting ATI driver.

If you mess it up, restore the /etc/X11/xorg.conf

---

### Post by landwomble on 2006-07-14
cool.  so all video and x-related shenanigans are stored in that file then?  excuse the naivety here!
presumably all i need to do in that case is rename the old one back  and all will be well?

---

### Post by Maggot on 2006-07-14
More or less yes.  That file tells the computer what hardware and options to run X with and yes, if you save a good copy of the file before playing, restoring it 'should' bring you back to normal.

Being a computer, anything can happen though :D

---

### Post by 2hansen on 2006-07-31
But the fglrx-driver unfortunately does not support the ATI Radeon Mobility M6 LY card.

---

### Post by gnottage on 2006-08-01
> **landwomble said:**
> Also, my mark 1 3Com Officeconnect wifi card doesn't play ball.  It's listed in installed hardware via iwconfig or iwlist (I forget!) but just won't associate with my access point with or without wep.  Tried with standard Ubuntu driver and ndiswrapper and it's not having it - seen a few posts about dapper being funny with wireless.  Any pointers?  
Alternately, any pointers on PCMCIA wifi cards that work out of the box?
Last question (promise!) is if I buy another wifi card and insert it into my current install, will Ubuntu autodetect the card and install default drivers a la Windows or is there some incantation I need to do?

I have an X31, that's currently running Breezy (5.10). Mine came with 802.11b support, but I got an 802.11a/b/g card off ebay and fitted it (along with bluetooth). I'd expect the socket to be present on yours, but perhaps not the antenae. The WiFi card was picked up fine, it just worked! The IBM site had all the details on how to dismantle the laptop and change parts over - something that I really appreciate.

---

### Post by jgcamp99 on 2006-12-18
Would XGL/Compiz even run decently on the 16 MB video that the X31 has ?

---

