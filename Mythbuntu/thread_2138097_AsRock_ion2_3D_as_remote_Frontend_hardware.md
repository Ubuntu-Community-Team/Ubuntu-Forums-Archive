---
title: "AsRock ion2 3D as remote Frontend hardware"
date: 2013-04-22
forum: Mythbuntu
---

### Post by gga96 on 2013-04-22
Hi All,

I have been trying to get this thing sorted for the past 4 weeks.

My intallation disk is MythBuntu 12.04.1, 32bit. I have an AsRock ion2 3D for my remote frontend. It worked well out of the box and installed and connected to the backend as expected.  

Some days later I have run Update Manager and on the next reboot the desktop is corrupted. I have now re-installed about 4 or 5 times with the same eventual corrupted desktop outcome, but now with frontend not connecting to the DB.

I believe it is software causing the problem, but first I have to eliminate possible hardware problems.

How do I give the hardware a vigorous and comprehensive test under linux???
Has anyone had problems with this hardware???
Has anyone had problems with resent Updates???

Being a linux newbie I am at the end of my rope with MythBuntu and its remote frontend. I do not know what to do next.

Any help is appreciated.
Glen

---

### Post by PhilWig on 2013-04-23
Hi Glen,
Still fighting it.

1.   try a memory test and leave it running for several hours rather than minutes - there is probably one available in your boot menu.
2.   Check disk SMART data.  eg Gparted live disk I think has smartmontools / GsmartControl.
Phil

---

### Post by gga96 on 2013-04-23
Good Morning Phil,
Nice to hear from you.

I have run long BIOS memory tests with no errors and GSmartControl for the HDD but again no errors.

[FONT=Verdana][COLOR=#222222]Getting no response from the very busy Network forum.[/COLOR][/FONT]
 
Today I will set up the conditions that existed the first time an attempt was made to install the remote frontend.
The static IP was configured in the pre 12.04 way and the MythBuntu remote frontend installed no errors. I suspect the installer software does not handle the post 12.04 LAN connection correctly and leaves one in a fatal loop broken by Alt F11.
I could be wrong but I need to disprove the theory.

Time will tell.
Glen

---

### Post by gga96 on 2013-04-23
Just started the frontend install, got to "Master Backend Info" screen, and hit "Test Connection" and response is:
 "Failed to connect to database at 'mythconverg'@'192.168.1.3' for user 'mythtv' with password 'HFyzH9pX'." 
All the quoted data above is correct. It can only find this data on the backend but it cannot connect to the DB.

Installation aborted.

I need some serious guru help!

P.S. Continued install to get clean desktop, will use Alt F11 to escape install loop.

---

### Post by gga96 on 2013-04-23
Current thinking eliminates the following:
-the hardware is ok I think
-the installer software is probably not to blame.

I installed XBMC on win 7 machine, installed add-in MythTV, setup MySQL data and it could not connect to DB.
Pinged &#8220;C:\Users\Glen>ping -t 192.168.1.3&#8221; from Win 7, no errors.

So the possibilities are:
-backend static IP implementation error
-router mis-configured
-and or DB corruption.

I am still in need of some serious help!

Glen

---

### Post by PhilWig on 2013-04-24
Check:
Backend address set twice in backend setup>general.
Also there is a tick box to be set but for the life of me I cannot find it.  This suggests it's in control centre: 
[http://askubuntu.com/questions/97335/how-do-i-connect-a-mythtv-frontend-to-a-mythtv-backend-on-mythbuntu-11-10](http://askubuntu.com/questions/97335/how-do-i-connect-a-mythtv-frontend-to-a-mythtv-backend-on-mythbuntu-11-10)
hth
Phil

---

### Post by gga96 on 2013-04-24
[B]YES it was in Control Centre. THANK YOU PHIL!
[/B]
I don't know how it got disabled.  Nearly four weeks down with lots of side affects.
I am glad it was something under my nose and not more complicated.

This thread is CLOSED.
Back to getting a sleepy frontend.

Thanks again Phil you have been a [SIZE=2]persistent [/SIZE]help!
Regards
Glen

---

