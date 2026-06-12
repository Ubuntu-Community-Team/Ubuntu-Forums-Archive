---
title: "Sounds works sometimes or not at all"
date: 2007-10-01
forum: Multimedia &amp; Video
---

### Post by Heaf on 2007-10-01
i installed ubuntu 7.04  so i installed all usefull programs and i got sound work but then when i just turned off my pc 

NOW sounds work sometimes or not at all  and  when the sounds work  the quality is terrible 
vlc and movie players will play tracks but when i try amarok or xmms  comes error witch says that my drivers are blocked or something like that  
i tried re-install ALSA mixer nothing happened 

my soundcard is creative SB live 5.1  is there any other way to get them work?


HeLP! 
HeLP!

---

### Post by disraeli on 2007-10-01
Does sound work at random boots? If so, maybe you have an integrated soundcard and Ubuntu selects one of your two soundcards at each boot because you didn't set the default card (this happened to me when I installed ubuntu 7.04).

---

### Post by Heaf on 2007-10-01
okay thaks can u litle advise me how did u do that 

sry bad english

---

### Post by jigatai on 2007-10-01
This is exactly what is happening with me, i run a 32 bit Version of Ubuntu on an AMD 64 machine, i thought this was the reason i sometimes had sound working and at others not a whisper.  

Being fairly new to Linux in general i downloaded the x86 version to test out the live CD, then  i installed it properly, only to have the sound bug out on me 5/10 boot-ups.  

I changed to the 64 bit version but that didn't even load properly and crashed my machine every time just before the GUI loaded (i may have downloaded wrong version tho) so then swapped back to x86 and the then-new 6.10 release to have my sound not work at all!  Being persistent i stuck around for 7.04 and my sound returned, but still only coming on 50% of the time.  

I love using Linux, and Ubuntu, and a solution to this problem would mean i can nearly make a complete migration from Windoze.  i thought my machine mite be detecting my integrated sound before my SB Audigy2 card and therefore initiating that instead but i have no idea what .conf file or similar file to look in to change my default sound device.

Regards

James:guitar:

---

### Post by jigatai on 2007-10-01
Just found this - [http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset/](http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset/)

it seems to work for me, nut i havent rebooted lots of times yet to make sure it does work properly, i'll test it later on and report back my findings.

James:guitar:

---

### Post by rodgerpb on 2007-10-01
If you have an onboard sound card AND a PCI or other sound card  - disable the onboard sound in computer BIOS (before ubuntu boots up)

Rodger

---

### Post by jigatai on 2007-10-02
I have now booted Ubuntu back up at least a dozen times now, and altho the login-screen sound of a quick drum beat doesn't always initiate when the login screen loads up,i have 100% success rate with the sound starting from when i have hit enter after entering my username and password.  Obviously the bash script i created from the above tutorial only initiates on login, but this doesnt worry me, i can now enjoy my music collection on Ubuntu all the time!

James

---

### Post by disraeli on 2007-10-02
> **jigatai said:**
> Just found this - [http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset/](http://www.lockergnome.com/nexus/linux/2007/09/23/setting-the-default-sound-card-usb-headset/)

it seems to work for me, nut i havent rebooted lots of times yet to make sure it does work properly, i'll test it later on and report back my findings.

James:guitar:

Yes, that's exactly what I did and worked for me

---

