---
title: "any drivers needed for ATI Radeon 9600 XT"
date: 2010-12-27
forum: Multimedia Software
---

### Post by wpshooter on 2010-12-27
On an install of Maverick should I have to be installing any video drivers for my ATI Radeon 9600 XT video card (yes, I know it is old as is most of the other components in my computer but they suffice for what I need done with a computer) other than the video drivers that are installed by the Maverick O/S ?

The reason I am asking this is because on rare random occasions (majority of the time the computer boots fine), I will get bios videos but then after the bios screens the video will go black and Maverick will not boot to the desktop - just black/blank screen.  I know it is not getting to the desktop because if I wait a good while and do ALT, CRL, DEL, the system will reboot without me even having to hit the ENTER key after having done that combination, because if the system was at the desktop and I hit ALT, CRL, DEL combination, I should then have to hit ENTER key to shutdown or arrow down key DOWN, then ENTER key to restart.

Strangely enough, I have another computer which has almost the same hardware components in it as this computer except the video card in it is an ATI Radeon 9600 but is NOT the XT model and it never exhibits the problem described above.

Thanks.

---

### Post by VonSpyder on 2010-12-27
This sounds more like a failing hard drive or failing memory than a video card issue if you are occasionally still making it to Ubuntu on boot.

---

### Post by ajgreeny on 2010-12-27
Try re-seating then card in the AGP or whatever it has.  Perhaps it sometimes just makes a bad connection to your mobo.

---

### Post by wpshooter on 2010-12-28
> **VonSpyder said:**
> This sounds more like a failing hard drive or failing memory than a video card issue if you are occasionally still making it to Ubuntu on boot.

Already tried another hard drive, still has the same problem. 

Not impossible to have the same problem with 2 different hard drives but after trying another drive, I sort of doubt that it is the hard drive.

Thanks.

---

### Post by wpshooter on 2010-12-28
> **ajgreeny said:**
> Try re-seating then card in the AGP or whatever it has.  Perhaps it sometimes just makes a bad connection to your mobo.

Already reseated the AGP card, still same random problem.

Is this more likely an intermittent problem with the video card hardware than it would be a possible problem with the monitor itself ?

Have not had a chance to try another video card yet.

Can an ifffy video card cause the computer to not properly boot all the way up to the Ubuntu O/S ?

Thanks.

---

### Post by Yellow Pasque on 2010-12-28
It could be a problem with the way Ubuntu displays boot info using plymouth. For example, your filesystem should be automatically checked once in every 30 boots or so, which would cause an extended wait at the plymouth boot screen. Do you ever see the plymouth boot screen (purple splash screen with ubuntu logo)? If no, then the next time you get a blank screen, press 'C' (I think) to cancel the filesystem checks (or wait a long time for the check to complete) and you will probably get a video signal.

---

### Post by Yellow Pasque on 2010-12-28
> should I have to be installing any video drivers for my ATI Radeon 9600 XT video card
Oh, and to answer the original question, no (though you can try the newer open-source driver by using: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa) ).

---

### Post by wpshooter on 2010-12-28
> **Temüjin said:**
> It could be a problem with the way Ubuntu displays boot info using plymouth. For example, your filesystem should be automatically checked once in every 30 boots or so, which would cause an extended wait at the plymouth boot screen. Do you ever see the plymouth boot screen (purple splash screen with ubuntu logo)? If no, then the next time you get a blank screen, press 'C' (I think) to cancel the filesystem checks (or wait a long time for the check to complete) and you will probably get a video signal.

I have seen the disk checking text at the bottom of the logo screen and the disk check seems to go O.K. and it boots to the O/S desktop.

BUT for instance yesterday, I completely installed Karmic from scratch on a completely blank hard drive from the ALTERNATE CD version and after I had the O/S installed and after that I downloaded and applied ALL of the available updates for Karmic and when I was prompted for the restart at the end of the updates and computer rebooted, went thru the bios/startu screen fine and then after that the video just goes blank, i.e. the "A" (analog light on my Samsung flat panel just goes off - "B" on the flat panel is for digital signal) and after that no more video.  If I do ALT, CRT, DEL at that point the system reboots (without me hitting any other key) which sort of tells me that it has not booted to the Ubuntu O/S) and more likely than not the system goes ahead and reboots and video works fine all the way up to the Ubuntu desktop.

In other words, I can never tell when I boot the computer whether I am going to wind up with video on the Ubuntu desktop so that I can use a working O/S.  Majority of the time works just fine but on rare occasions at random no video after initial BIOS screens.  Like I said earlier, I have tried another hard drive, same thing.

Thanks.

---

### Post by VonSpyder on 2010-12-28
try another vid card see if it still does it.

---

### Post by wpshooter on 2010-12-31
> **VonSpyder said:**
> try another vid card see if it still does it.

So, I finally got time to put the ATI Radeon 9600 into the computer that was using the ATI Radeon 9600XT (the computer that was having the video problems) and I then completely reinstalled Ubuntu Maverick from scratch and so far I have not gotten the BLANK/BLACK (no video) problem.  But I have only restarted the machine a few times so far.  But it is looking like that this change of video cards "may" have fixed the problem.

Also, I noticed that on the ATI Radeon 9600XT card (the one with which I was having the problem) that it had a built-on-board fan (whereas the plain 9600 has only a heat sink but no fan) that there was a little (not a great amount) of dust on and around the fan and surrounding heat sink area of the card.

I cleaned/blew the dust off of it.

Is it possible that just having this small amount of dust build-up on the fan/heat sink is what was causing the intermittent loss of video problems ?  

I am going to install it in the computer from which I took the plain 9600 card from and see if the video problem recurs but I was just wondering how sensitive these cards might be to dust build up.

Thanks.

---

