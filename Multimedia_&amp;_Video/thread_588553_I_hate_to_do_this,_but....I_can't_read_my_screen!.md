---
title: "I hate to do this, but....I can't read my screen!"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by ohiomoto on 2007-10-23
I looked through the topics and either didn't see my problem or understand what I was reading.  So please forgive me.

Since this is my first post, I should warn you that I'm pretty stupid with this stuff.  I know just enough to get me in trouble.  I screw stuff up and then learn just enough to screw up even more stuff.  

Like any good fool would do, I clicked the "upgrade" button while using my (near) perfectly good Ubuntu 7.04 OS on my Dell C-610 laptop.  (My first Linux install and I was really happy with it.)  

The upgrade went fine.  **I adjusted my screen resolution to 1024x768.** Then I messed around a little and it seemed as though everything was in order except that my Dell/Broadcom wireless card wouldn't work.  (Same as in 7.04)  So plugged in my trusty D-Link 650+ card.  It didn't make the connection and I haven't learned how to do much with the shell, so I went with the old Windows stantby...the reboot.

Here is where my problem begins.  My system rebooted fine except that my screen just flickers and I can't read or see anything.  After the boot screen that says "ubuntu", my OS boots with the Ubuntu colors.  But it has a horizontal lines running from the bottom of the screen to the top.  I can hear the login prompt and I can even type in my user ID and password (though I can't see them) and log on to the system.  From there, if I use the mouse, I can see a vertical line running up the screen and it moves side to side if I move the courser side to side.  So it appears to me as though everything is working except for my screen settings (refresh rate??).

Everything still works fine in XP.

So my questions are as follows:

1. What happened and can it be fixed?

2. I tried to boot to the earlier kernels.  I thought 7.04 would still be there, but it isn't.  My 7.10 recovery kernels look fine, but I don't know how to use them.  Both 7.10 kernels flicker.  Can I use the recovery kernels to fix the problem?

3. I have a live 7.04 CD as well a Knoppix image on disk.  Is it possible to use it to fix the problem or reload 7.04?

I'm a little afraid of #3.  The last time I tried to use the CD, I messed up my grub and was no longer able to boot to ether OS on my hard drive.  I couldn't figure out how to fix the problem and ended up doing a clean install of both XP and Ubuntu...it was a disaster.

Thanks in advance for any help offered.

Tim

---

### Post by ohiomoto on 2007-10-23
I tired this command that I found in another thread:

dpkg-reconfigure xserver-xorg

I got a little freaked out that I could be making things worse, so I bailed.  Funny thing is, that the system booted up at the default 1280x800 resolution and works fine now.  

One thing I noticed is that when I changed the screen resolution the first time, I used the "Administration"/"Screens and Graphics" menu.  After trying "Preferences"/"Screen Resolution" option to change it to 1024X768.  I rebooted and it seems fine.  

?????

---

