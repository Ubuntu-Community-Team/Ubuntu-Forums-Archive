---
title: "WIFE Approved"
date: 2007-10-24
forum: Mythbuntu
---

### Post by besmith2@hotmail.com on 2007-10-24
So I sucked up a little and finally got MythTV running thanks to MythBuntu. I literally was in the basement for 2 months trying every thing out there and finally got MythBuntu running. Of course I needed to make up for my absence on the couch with the wife for the past months. I recorded Oprah for her and she was extremely pleased. 

This is awesome I have a Buffalo LinkTheatre Networked DVD player with uPNP and it just works with MythBuntu...... Just works :D

You guys are awesome. 

Happy wife happy me :P So the next phase is to build a couple of frontends with you know the regular stuff and remotes. Does anyone have a suggestion on a usb remote that just works?


THANKS MythBuntu!!!

---

### Post by BillDozer on 2007-10-24
I'm using a MCE USB 2 remote that was included with my Hauppauge 500 PVR card, and that worked without too much hassle.

---

### Post by tgm4883 on 2007-10-24
Second the MCEUSB2 remote

---

### Post by JLB on 2007-10-24
Again, the MCE remotes work well and are cheap to procure (Ebay). I think with LIRC, they are "out of the box" nowadays. Back in the day they were not too hard to get working. I use an Actisys IR-200L blaster as well.

---

### Post by reclusivemonkey on 2007-10-24
*DON'T* get a Soundgraph iMON VFD. I bought this specifically for MythTV after doing some research and seeing it was supported in Linux. I tested it out in my Feisty desktop on just the Myth FE and it worked great. However, it now doesn't work in Mythbuntu (or a stock Gutsy install) and no one seems to know anything about it... =[

---

### Post by PiXeLStick on 2007-10-24
About the Imon VFD driver.  In order to get it to work (the way that you would see as proper) is to apply a patch to the lirc sources.  I don't have the link right off, but you can check with the knoppmyth forums.

I have successfully run the imon remote with knoppmyth with several incarnations.  Tomorrow I will see if I can find a link to the patch which will enable the pad and mousing functions too.

---

### Post by reclusivemonkey on 2007-10-25
> **PiXeLStick said:**
> About the Imon VFD driver.  In order to get it to work (the way that you would see as proper) is to apply a patch to the lirc sources.  I don't have the link right off, but you can check with the knoppmyth forums.

I have successfully run the imon remote with knoppmyth with several incarnations.  Tomorrow I will see if I can find a link to the patch which will enable the pad and mousing functions too.

Thanks, I would really appreciate that as I have asked in #unbuntu-mythtv, #mythtv-uk and here and no one seems to be able to help.

[http://ubuntuforums.org/showthread.php?t=579944](http://ubuntuforums.org/showthread.php?t=579944)

---

### Post by shad0w_walker on 2007-10-25
Got to throw in my vote for the MCE remote, the best media center remote i have ever come across (Never thought i'd say something like that about anything Microsoft) and it is a piece of cake to setup with LIRC now.

---

### Post by superm1 on 2007-10-25
Not to mention the mceusb2 remote is what multiple of the developers for mythbuntu use, so it will have one of the best out of box experiences of all the remotes :)

---

### Post by PiXeLStick on 2007-10-25
This looks to be a good site with the patches to use according to the version of LIRC.

[http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller](http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller)

To get more information about the driver, you can go to the Official imon driver forum at [http://venky.ws/forums](http://venky.ws/forums).

It would be nice if LIRC would include the patches or a special "out of the box" solution could be found for Mythbuntu.

There is also a forum topic at the driver forum about this subject "patch to make the imon PAD generate mouse events" that is continuously being updated.

---

### Post by dannyboy79 on 2007-10-25
pvr-350 remote works good for me and with the correct lircd.conf and a serial IR blaster to control my cable box, all is well at my house!!!! BUT, the pvr-350 remote/ir receiver plugs into the pvr-350 card so if you don't have the card I don't think it would do you much good.

---

### Post by reclusivemonkey on 2007-10-25
> **PiXeLStick said:**
> This looks to be a good site with the patches to use according to the version of LIRC.

[http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller](http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller)

To get more information about the driver, you can go to the Official imon driver forum at [http://venky.ws/forums](http://venky.ws/forums).

It would be nice if LIRC would include the patches or a special "out of the box" solution could be found for Mythbuntu.

There is also a forum topic at the driver forum about this subject "patch to make the imon PAD generate mouse events" that is continuously being updated.

Thanks dude I will give this a go.

---

