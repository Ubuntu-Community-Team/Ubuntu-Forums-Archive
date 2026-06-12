---
title: "CS4236 sound card in Jaunty"
date: 2009-04-28
forum: Multimedia Software
---

### Post by b@sh_n3rd on 2009-04-28
Hi, I run Jaunty on an old DELL OptiPlex GXa that includes the "Crystal Semiconductor CS4236" audio drive. There appear to be problems setting up the drivers for this card in Intrepid and Jaunty, which I've used that have produced this problem. Ever since I tried Intrepid Ibex, I seem to have trouble with sound. Eventually I get it working after trying all sorts of remedies. The latest Jaunty Jackalope, too, produces this problem. What I understood when reading the Community Documentation is that this driver is disabled to avoid a system crash. Hardy Heron had no problem whatsoever.

I've noticed that many users, especially that of OptiPlex GX1, GXa and other systems that include the CS4236 chip run into this problem where some fixes work and some don't. It's quite aggravating to have no sound on a PC and the CS4236B is quite a good audio device as I've experienced. To make a long story short, as a quick troubleshooting method, to other users of this chip and for myself too (:D) I'd like to figure out how exactly I could get this chip working directly, successfully, without trying a hundred different remedies.

I noticed that even though I add "snd-cs4236" to the "/etc/modules" file, my card isn't recognised. In other words, I don't get "CS4236" in my "devices" list. When it is, in the "Sound Preferences" window, under "Default Mixer Tracks", in the "Device:" drop down list I could select something like "Playback: CS4236 xxxxx (alsamixer)" and sound would be enabled. It seems my system takes it's own cool time to play sound which annoys me very much :D. Thanks in advance.

---

### Post by b@sh_n3rd on 2009-04-28
OK, I've run into a problem. I follow the "HowToSetupSoundCards" section in the community documentation and am able to load the driver for my CS4236B. When I run "sudo alsamixer" I can control the sliders as they should be and the program shows "CS4236B" under "Card" and "Chip". When I run "aplay -l" it returns; "aplay:device_list:217: no soundcards found..." How can I fix this? :(

**EDIT:** Oh yeah, and when I run "asoundconf list" it returns,

"Names of available sound cards:
CS4236B"

Which means it detects my card. But no sound or no "alsamixer" option in "default mixer tracks"

---

### Post by b@sh_n3rd on 2009-04-28
I got it! Here is the basic principal to fix sound on the CS4236 chip to anyone that has problems with it.

add "snd-cs4236" to the /etc/modules file by typing "gksu gedit /etc/modules" in a console. Then, when you reboot the system the driver for the chip is loaded. If you want to load the driver without rebooting, type "sudo modprobe snd-cs4236" in a console. To check if your sound card is loaded and is working, try running "sudo alsamixer" in a console. 

When the drivers are loaded, go to "System > Administration > Users and Groups". Then, make sure "Use audio devices" is selected under the "User Privileges" tab. You may have to re-login to activate your new user privileges. Next, go to "System > Preferences > Audio" select "ALSA" for all drop down boxes, Or any other option if you prefer and change "Device:" under "Default Mixer Tracks" to "CS4236B (Alsa mixer)" ["CS4236B (OSS Mixer)" if you prefer it when using OSS]. That's it, now you should have sound on your CS4236 (or equivalent). Hope this helps many :D.

This might work for any other sound card too. Just substitute "CS4236" and "snd-cs4236" with your sound card.

**EDIT:** In my case, when ALSA is selected in "System > Preferences > Audio", sound doesn't work on GNOME. To fix this, instead of selecting ALSA, select OSS but with "alsamixer" for device. This is on the CS4236B.

---

### Post by ericd68 on 2009-04-29
Thanks. With this, I was able to resolve my issues with the Dell Optiples GX1 I use. Really helpful! :KS

---

### Post by b@sh_n3rd on 2009-04-30
wow cool. You're welcome. I was always frustrated to get this working everytime i try a new version of Ubuntu. The thing is, i tend to experiment with ubuntu in ways that get me to reinstall. I'm glad this finally helped someone. BTW, how old is your GX1? I'm using a GXa which is 11yrs old :D. I'm just a great fan of DELL coz of this. My avatar says it all :D.

PS: BTW, how'd u find this thread? Just curious :D.

---

### Post by jfenn2199 on 2009-08-20
Another thanks, I was setting up a machine for my father-in-law and he had this GX1 laying around and it used to be hooked up to a schools network and since it no longer was XP didn't want to boot so I grabbed a 9.04 disk and ran it live and he said to load it in.  The only problem was the sound card and now that's fixed.  So thank you very much :guitar:

---

### Post by tgalati4 on 2009-08-20
I'm running Linux Mint 5 (based on Intrepid) XFCE version on my GX1.  It's 1999 vintage with max RAM at 768 MB.  A PIII, 500 MHz, bare minimum, but OK for light tasks.

It's a solid workhorse machine.  Definitely recommend any used Dell business class machines for Ubuntu.

---

