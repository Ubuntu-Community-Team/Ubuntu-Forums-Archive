---
title: "ATI FireGL v7300  issues.."
date: 2008-09-29
forum: Multimedia Software
---

### Post by w0ts0n on 2008-09-29
Hey All, 

First off I would like to say this site and flavor of Linux is the best I have used so far, that said I hope you can help me out here.

Now let me give you a bit of back story..

I installed Ubuntu (after a few issues with the disc) and updated the driver that Ubuntu found for my graphics card "ATI accelerated graphics driver" this was nice everything was going smooth, after I updated everything I started messing with compiz and mac4lin just for fun..
Everything was going great.

I then decided to map to my server, mapping went okay, now here is where the issue arose. I played an AVI file (with correct codecs in VLC) and it was jerky at medium size and I noticed the the visual effects where also a bit jerky. 
So me being me assumed there was a graphics card issue.

I went on the ATI site and found this handy Linux driver:
[http://ati.amd.com/support/drivers/linux/linux-firegl.html](http://ati.amd.com/support/drivers/linux/linux-firegl.html)

I ran this using the following command:
cd ~/Desktop
sudo sh  ati-driver-installer-8.523.1.1-x86.x86_64.run

Everything was running smooth, I got a GUI for the driver install, next next next etc etc.. rebooted same problem. I went to the ATI catylst center (now added to my applications) and was told there was no ati drivers.. after a little reading I found out that the old driver may be causing issues... so I used a piece of software (envyNG??) to remove the old driver and install the new one.. same issue but worse, this time the screen res was HUGE... reinstalling didn't work also..

FORMAT:

So a fresh format surely this driver should work now right?? WRONG this time it installed as normal but no ATI cytlst shown... reboot... after logging in a white screen with just a mouse (after a few flickers).. rebooted several times same problem. 

FORMAT:

Here I am, afraid to try again as I don't want to wait 25 minutes to install again..

Any insight and help would be great. 

System info:

QuadCore 2.4 Q6600
FIREGLv7300
2gb of ram 
Ubuntu latest stable release (from the main site)

---

### Post by w0ts0n on 2008-09-29
Update!
I tried again and this time with a little more success, I got the ATI driver loaded on and the ati control panel was working, reboot White screen of death again (WSOD lol)

Any insight?

---

### Post by Cophian on 2008-09-30
I have a ATI Radeon 9550 and think i have the same problem.

The only way i can get back into Ubuntu is to disable ATI drive at start-up and the system is slow and jerky 
re install restricted driver and reboot and I get the out of range on my monitor
i wonder if the driver has been updated and have bugs in it???

I hope somebody works it out soon so i can go back to linux, windows is nealy as slow as a broken linux

---

### Post by w0ts0n on 2008-09-30
> **Cophian said:**
> I have a ATI Radeon 9550 and think i have the same problem.

The only way i can get back into Ubuntu is to disable ATI drive at start-up and the system is slow and jerky 
re install restricted driver and reboot and I get the out of range on my monitor
i wonder if the driver has been updated and have bugs in it???

I hope somebody works it out soon so i can go back to linux, windows is nealy as slow as a broken linux

FYI I had the out of range issue also, switching from DVI to VGA fixed that one particular issue, but my existing one still is a major problem.

---

### Post by Cophian on 2008-09-30
Watson

Can you tell me how you did that

thanks

---

### Post by w0ts0n on 2008-09-30
> **Cophian said:**
> Watson

Can you tell me how you did that

thanks

Unplugged the DVI [http://www.global-b2b-network.com/direct/dbimage/50270101/Dvi_Cable.jpg](http://www.global-b2b-network.com/direct/dbimage/50270101/Dvi_Cable.jpg) 

and replaced with a VGA:
[http://www.chinawholesalegift.com/pic/Electrical-Gifts/Computer-Hardware-Accessories/Cable-Adaptor/VGA-Cable-1329256622.jpg](http://www.chinawholesalegift.com/pic/Electrical-Gifts/Computer-Hardware-Accessories/Cable-Adaptor/VGA-Cable-1329256622.jpg)

---

### Post by Cophian on 2008-09-30
Thanks for your reply but im using the VGA so ill keep looking

---

### Post by w0ts0n on 2008-10-03
Anyone know a fix for this? I really want to use Ubuntu..

---

### Post by w0ts0n on 2008-10-15
Okay, I have resolved this issue now and I am loving Ubuntu.

For those looking for help all I can say is EnvyNG.
This program saved my life.
Go to packet manager and install it, use it.
I would suggest running updates first.

---

