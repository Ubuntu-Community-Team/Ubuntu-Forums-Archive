---
title: "How to Install Twinhan on Linux V1.4.2"
date: 2009-01-30
forum: Mythbuntu
---

### Post by bryanf2009 on 2009-01-30
I am new to Linux.  I have installed MythTv.  Now I just need to get the Driver installted for the Twinhan 1034

I have downloaded the Linux Driver/Software from [http://www.twinhan.com/download_driver&software.asp](http://www.twinhan.com/download_driver&software.asp)

My problem is I dont knwo how to install a programs on Linux.  I understand the basics of TAR.  I have put the file on a CD.  Now I am at the Terminal Window (been a long time since I used Unix commands).  what comes to mind off the bat is ls -l, man, cd, etc.  I understand that I should issue a TAR command but not sure where to put it...

Can anyone help me?  Sorry for being so green at this.

---

### Post by bryanf2009 on 2009-01-30
Ok - I have made good progress.  

There seems to be 3 parts to this
[LIST]
[*]dvb-apps-997424a1799e
[*]linuxdriver
[*]script
[/LIST]

This is what I have done so far
[LIST]
[*]I have manged to get the "tar" file unpackaged and placed it in /tmp/Twinhan.
[*]I manged to "make" and install the dvb-apps-997424a1799e
[*]I manged to "make" the linuxdriver.  However the install seemed a bit of an issue.  It said it was an invalid format (I will get the exact message in a bit.
[/LIST]

I will keep you posted

---

### Post by bryanf2009 on 2009-02-03
I downloaded the latest DVB-S2 drivers from [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)

Now my Twinhan 1034 shows up within MythTV.  Now I just have to configure the Multisitch/DiSEqC as I have 4 LNBs coming into a 17 In 8 Out multiswitch.

Anyone have experience configuring DiSEqC with a multiswitch within MythTV?

---

### Post by jetblackstar on 2009-06-07
I can only presume by you posting in the Ubuntu forums you are running Ubuntu Linux ;) . Which version are you running (eg 8.04)?
I am battling to get a Twinhan SP300 (1034) DVB-S card working with MythTV myself. MythBuntu 8.04 has recognised the card straight off, no driver needed. The card works with Kaffine (another media and DVB application) but not with myth.
However MythTV crashes when ever it tries to use this card :P

The drivers you pointed out were originally meant for Fedora Core 6, and were made in 2006 ish. It may work better, since they were made by TwinHand themselves (i think) but it's also possible they wont work with Ubuntu, I'm a little nervous about putting them in myself. 

What exact errors were the linuxdrivers section of the Twinhan driver giving you?
-Jet

---

### Post by richard.e.morton on 2010-05-18
> **bryanf2009 said:**
> I downloaded the latest DVB-S2 drivers from [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)

Now my Twinhan 1034 shows up within MythTV.  Now I just have to configure the Multisitch/DiSEqC as I have 4 LNBs coming into a 17 In 8 Out multiswitch.

Anyone have experience configuring DiSEqC with a multiswitch within MythTV?

I the above download a branch of the v4l driver framework or is it the main trunk; sorry I cant work it out.
Looking at the commits the relevant changes were 18 months ago - [http://mercurial.intuxication.org/hg/s2-liplianin/rev/149a5c57c1e2](http://mercurial.intuxication.org/hg/s2-liplianin/rev/149a5c57c1e2)

so should this now be available as a package in Ubuntu?

If so which package?

thanks

Rich

---

