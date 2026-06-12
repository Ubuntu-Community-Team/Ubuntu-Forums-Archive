---
title: "[SOLVED] Installing Mythbuntu 7.10: Can't setup backend, results in logout."
date: 2008-04-10
forum: Mythbuntu
---

### Post by Cyborg28 on 2008-04-10
Hi,

I have tried installing mythbuntu 3 times now, each time more generically than the last.  **I have tried a basic integrated frontend+backend setup with no advanced options.** I always have the same problem.  I get all the way through the install and on step 15/15, where you can configure schedules direct and the backend and go to finish I get logged out when  I go to configure the backend. 

If I resart the machine without the CD I go straight to mythtv frontend and it cant connect to the backend (I assume b/c it has not been set up all the way). So I exit mythtv, try and launch backend setup or mythtv setup and get kicked to the login screen. From there I can log back in and get back to the front end just to start the process all over.

I cant even launch a terminal window from the desktop, just get logged out.

Please help.

Cyborg28 :confused:

My system:

Intel 810/815 series Mobo with onboard video (working)
Intel Onboard Nic Working
Intel PIII 933 CPU
384 MB PC100/133 ram
WinTV PVR-150 (cant get far enough to test)
20 GB IDE HDD (270MB Swap, the rest ext3 root)
IDE CD ROM
Silicon Image PCI SATA RAID Card (No HDDs attached yet, worked with ubuntu server 7.10)
Adaptec/Texas Instruments ieee1394 PCI host card:):)

---

### Post by tgm4883 on 2008-04-10
Strange.  Are you using any funky characters anywhere during setup?

---

### Post by Cyborg28 on 2008-04-10
@tgm4883:

US English (lang), US English (key)
U/C & L/C Letters & Numbers.

Nothing else.

 Could this be a hardware/driver conflict or problem?  I tried to make everything as vanilla as possible the last time I installed. The only thing I did slightly out of the ordinary was change the computer name from username-desktop to mythserv and partion the hdd manualy to have just 270 MB swap + remainder ext3 mounted at / (root).

Do I have to play with MySQL passwords for an absolute default install?

C.

---

### Post by Cyborg28 on 2008-04-10
OK - this must be hardware.

I am writing this in firefox on the live CD.  I cant launch terminal in the live cd.  I get the same scrambled screen, followed by some text re: LIRC, followed by a white screen, followed by a beige screeen followed by the login screen.  I have checked the integrity of the MythBuntu CD and run memtest and everything is fine.

I can open windows dammit, I'm using firefox, I can launch and get 90% of the way through the installer properly.  What the heck is wrong here??!!!??!!?

C.

---

### Post by volkswagner on 2008-04-10
You said you can run Ubuntu 7.10?  You may want to install Ubuntu 7.10 and add mythtv via synaptic.

I have had a cd, and checksum pass.  Tried a new download via torrent.  That solved my problem "unable to complete install".

---

### Post by Cyborg28 on 2008-04-10
Is the terminal application / window in Applications -> Accesories on the live CD supposed to work?  Does it work for anyone?  It does not work for me in MuthBuntu or xUbuntu. I just get booted out to the login screen!

Aaaaarrrrgggghhhh!

This is written from firefox in the xUbuntu live CD.

C.

---

### Post by volkswagner on 2008-04-11
> **Cyborg28 said:**
> Is the terminal application / window in Applications -> Accesories on the live CD supposed to work?  Does it work for anyone?  It does not work for me in MuthBuntu or xUbuntu. I just get booted out to the login screen!

C.

Yes.  The terminal should work.  I would suggest download a new iso.  Burn a new copy, possibly slower burn.

---

### Post by Cyborg28 on 2008-04-11
Hi Volks,

I have tried 2 DLs of Mythbuntu and 1 DL of xUbuntu, burned on an NEC burner under MacOS X and an LG burner under vista.

I'm done with xUbuntu.  Ubuntu 7.10 works fine.  I have been using the server version for two months on the machine in question and it has been ok.  I tried a desktop ubuntu  7.10 Live CD on the machine and terminal fired right up.

I think there is a problem with intel 810 / 815 graphics and xUbuntu 7.10, but I don't have the time to be the guinea pig that debugs that.  Maybe I'll give it a shot in a month or two when a Mythbuntu Hardy goes gold.

Now to figure out how to apt-get myself some mythtv on ubuntu.

*edit* you mentioned synaptic.  What is it?

C.

---

### Post by volkswagner on 2008-04-11
Once Ubuntu 7.10 is installed.  Synaptic is in System>Administration>Synaptic Package Manager.  You will also find Update manager, as you may want to run this first.

You may want to enable universe and multiverse, in synaptic.

From synaptic >Settings>Repositories>Ubuntu Software
You may also need to enable 3rd party.


EDIT:  When searching for software packages, click on any package.  You can then start typing, ie: mythtv.

---

### Post by Cyborg28 on 2008-04-16
Please Set This to Solved.

I think the xUbuntu 7.10 ISO is not compatible with intel 810 / 815 integrated graphics chipsets.

I have solved the problem by first installing Ubuntu 7.10, then adding mythtv.  This is working fine.

Is it normal that installing mythtv in ubuntu "brands" the entire install as mythbuntu? I now have a mythbuntu startup & login screen.

Also xfce now works on my machine. I think it was also installed with mythtv.   If I run xfce does that mean that I am getting the benefits of a lighter desktop environment on my low performance system?  Gnome is still installed and I can chose it at login, so is there a benefit to using xfce over gnome?

Thanks,

Cy

---

### Post by volkswagner on 2008-04-16
Yes, XFCE is light weight.  It is normal for the new Mythbuntu splash/login.  Glad you got it working.  BTW you set the thread as solved.  Go to thread tools at the top.

---

### Post by Cyborg28 on 2008-04-16
Volks,

Yes but if gnome is installed is it still using resources (other than disk space) when I am in an xfce or a terminal session?

Do I save resources by logging out of my myth backend and letting it run headless even if gnome and xfce are installed?

Thanks,

C.

---

### Post by tenchi19134 on 2008-08-13
*bump*
You are using a nVidia GeForce FX series which has a problem with the backend setup. Try using an other video card. That's what both my cousin and I did to our machines and when we finished I put my GeForce FX 5700VE back in as he did with his GeForce FX 5200 Ultra.

I hope that buy this time someone actually needs this info cause I did. :)

---

