---
title: "Default Sound Card keeps changing. -- PLEASE Help"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by djseto on 2007-04-10
For some reason the default sound card keeps changing and I dont know why. I used the "sudo asoundconf set-default-card XXXX" command to change it and it worked for a while but now all of sudden, no matter how many times I type that command, when I reboot, its showing the wrong sound card. It keeps defaulting my sound card to the PCHDTV-5500 chip and not the HDA NVidia chip on the motherboard. What is going on???

I looked at some past posts and it seems this was a common issue, but I have yet to find a definitive solution. I have (2) PCHDTV-5500 cards and the onboard NVidia chip. Things alway seem to boot in this order:

cx88_alsa
cx88_alsa
snd_hda_intel

I've tried adding lines like:

install sound-slot-0 snd_hda_intel
install sound-slot-1 cx88_alsa
install sound-slot-2 cx88_alsa

to my /etc/modprobe.d/alsa-base file and its always Russian Roulette as to which card is default after each boot. This has been driving me crazy and this is the last thing I need to work to get MythTV running properly

Thanks

---

### Post by moffa on 2007-04-10
Please see:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

under: Configuring default soundcards / stopping multiple soundcards from switching

---

### Post by DoorGunner on 2007-04-10
I have a Soundblaster sound card with a via82xx on board sound. The Via kept interferring with my sound blaster. What i did to prevent it from interfering was to go to /etc/modprobe.d/blacklist and add an entry for via82xx. You may be able to do the same for your redundant sound problem.

---

### Post by djseto on 2007-04-10
> **moffa said:**
> Please see:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

under: Configuring default soundcards / stopping multiple soundcards from switching

Tried it. It doesnt work. I am running the AMD64 version of Ubuntu. Could this be my problem? I knew nothing about Linux before I started my MythTV project, but as I debugged my MythTV install, I came across a lot of older threads saying 64bit versions of Ubuntu are buggy. Is that still the case? Can I install the 32 bit w/o having to format and start over? I really dont want do the MythTV install again for the 5th time in a week since I started this project

---

### Post by deadgobby on 2007-04-10
Here is simple thing for you to do. And it not the link provided. The trick is to go into you BIOS and disable the on board sound card. That way when your system boots up all sound will plug through the sound card and it will not default. After you have that on board sound card disable. Boot up and then install ALSA mixer. If you run Gnome you can install ALSA Gnome ALSA mixer through Synaptic. Or you can install the simple form of ALSA mixer through the Terminal.  The command to install through the Terminal would be

sudo aptitude install alsamixer

Once install type in the terminal

alsamixer

Here are a couple of screen shots between the two.

Gnome mixer after it is install can be found in 
Apps> Sound> Gnome Mixer

PS you are better off installing 32bit for AMD than using 64bit. There is more support at this point for 32bit. Linux world works fast and yet behind on 64 programming and softeware.
[https://help.ubuntu.com/community/Installation/32bitonAMD64](https://help.ubuntu.com/community/Installation/32bitonAMD64)

Gobby

---

### Post by djseto on 2007-04-10
Thank you.  I want the sound to come through my on board sound card though. I am doing a fresh 32bit install right now, so hopefully that will fix all my issues.

---

### Post by djseto on 2007-04-10
I installed the 32bit version and I still get the random sound card changes. Any more ideas? Please!

---

### Post by djseto on 2007-04-10
bump

---

### Post by djseto on 2007-04-11
Bump again. If no one has an answer, can you please point me somewhere that might? This problem is extremely frustrating

---

### Post by deadgobby on 2007-04-12
If you have 2 sound cards it will play sounds from 2 different areas. Like the on board will play the internet and the sound card will play every thing els. 
 Your sound preference at the speaker icon and your System>Sound need to match up.  If you do not match them up it will default over and over again. Let me reboot my machine and look into BIOS. I'll be back to edit this.
Gobby
 OK I was thinking I can disable the sound card. Well not with BIOS. Any ways try to match up the sound preferences.

---

### Post by DoorGunner on 2007-04-12
I dont think that there was  ever a clear cut solution to all of this. I know that i had the same problems you did . However, I persisted to work with the sudo nano /etc/modprobe.d/alsa-base. and I think in mine in stead of ... i put in a remove insted of install on the via8237 line.

Note: you may not have via trying to takeover your sound like I did. However, the idea is similar to what you are facing.

> # Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
remove snd-via8237 /sbin/modprobe --ignore-remove snd-via8237 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }


in this section i hashed out all the unused stuff

> # Prevent abnormal drivers from grabbing index 0
options snd-emu10k1 index=0
#options snd-bt87x index=-2
#options cx88-alsa index=-2
#options saa7134-alsa index=-2
#options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-3
#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci


Yours may look different but try and follow the idea of what i did.

I then tried and do the /etc/modprobe.d/blacklist and add the offending module. In my case it was the  snd-via82xx. You can add something similar to what I did.....but for your offending cards

> #added by jms to prevent via problems
blacklist snd-via82xx
blacklist snd-via8237

One Last thing..... i had to add snd-emu10k1 for my sound blaster card to the /etc/modules list. You may have to add the appropriate diver to this as well

if all goes well on your next reboot you should have your sound back. if this happens quickly do the sudo alsactl store 0. Then everything should work from now on.

I had a bitch of a time to get it to work. But it did eventually work and there was really no one thing that did it. I personally think alsa is a piss poor system. I know that Open Solaris had proper drivers for all cards and they worked way better.

Good luck with this

---

### Post by djseto on 2007-04-12
> **deadgobby said:**
> If you have 2 sound cards it will play sounds from 2 different areas. Like the on board will play the internet and the sound card will play every thing els. 
 Your sound preference at the speaker icon and your System>Sound need to match up.  If you do not match them up it will default over and over again. Let me reboot my machine and look into BIOS. I'll be back to edit this.
Gobby

I dont have 2 soundcards per say. I have one soundcar, the onboard one. The other two things that show up as sound cards are part of my PCHDTV-5500 capture card. What do you mean by sound preference at the speaker icon? When I roll my mouse over the speaker icon in the upper right hand corner in GNOME, it says "Headphones 58%" (with the percent being my current volume).

---

### Post by deadgobby on 2007-04-12
Right click the mouse at the speaker icon and go to Preferences.
Gobby

---

### Post by RomeReactor on 2007-04-12
Hi. Just right-click on the speaker icon and select the card you want as the default.

---

### Post by djseto on 2007-04-12
Good News and Bad News:

Good News: I dont F'ing belive it was THAT simple to make my onboard audio default at startup. I literally spent HOURS today trying to get find an answer

Bad News: My PCHDTV cards are decoding the analog audio from the Cable feed, but for some reason its not being outputted via my SPDIF. This was working earlier. I dont know if this caused it or if something I tried earlier in the day broke it. I verified that Capture is set on the "LINE IN" and on the "Capture" inputs in Alsamixer as it was when this was working. 

This has been my trouble all week long. I fix one thing, another thing breaks. Thanks for the help with this default card issue. Any ideas on my new problem?

---

### Post by djseto on 2007-04-12
Looks like my problem is back. Its back to sound card russian roulette. Any more ideas?

---

### Post by djseto on 2007-04-13
bump for help

---

### Post by deadgobby on 2007-04-13
You'll need to goto PCHDTV and install the linux drivers. It may work. 
[http://pchdtv.com/](http://pchdtv.com/)
 If you do not know how to install from Source AKA tar file. See these links
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
 Do not install the Fedora or Mandriva drivers. Just click on the first link Driver and DL the driver. Read the links on how to install from source and see if it clears up your problem. 
 Please do not get fluster using Linux. Stand firm and take on the challenge. I started Linux 3 years ago and was getting piss off at it. I did not throw in the towel. I was not about to get Linux the best of me.

---

### Post by djseto on 2007-04-13
I got it to work. I had the latest drivers already installed. I ended up putting the 5500's cards in the blacklist. After some fumbling, I realized that even though the 5500 doesnt show up in my sound cards choices, they still continue to work so I was able to run the analog output from the 5500 into my Line In on my sound card.

---

### Post by deadgobby on 2007-04-13
So this is solved righty right;-)

---

