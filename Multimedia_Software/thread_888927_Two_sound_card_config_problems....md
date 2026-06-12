---
title: "Two sound card config problems..."
date: 2008-08-13
forum: Multimedia Software
---

### Post by lostpenguin on 2008-08-13
Hello there,

 Just done a fresh install of hardy heron and I'm trying to configure the sound cards. I have one on board card and one sb audigy se. The problem is that half my programs use the pci card and the other half use the onboard card.

 I have been trawling the forums for a solution, found a couple with solutions that didn't really help me :(. Found this one, but am a little unsure... some help would be much appreciated...

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (Comprehensive Sound Problem Solutions Guide v0.5e)

I was just going to make my pci card the defualt but i'm not sure its set up properly...

when I type 'cat /proc/asound/modules' i get this:

 0 snd_ca0106
 1 snd_usb_audio
 2 snd_hda_intel

The hda one is the on board one, but the ca0106 isn't the audigy (I don't think). When i use the gui volume controls that come with ubuntu ca0106 is muted, yet I get full sound from the card through Amarok (using the ALSA plugin) and firefox.

I was going to follow the guide above and alter the file '/etc/modprobe.d/alsa-base' but am not really sure if thats right.

 The last part of the file reads:

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


How do I solve this problem? Please help, I'm new to linux and rather confused!

Thanks

---

### Post by kostkon on 2008-08-13
There is a possibility that some of your applications use *ALSA* directly and some pass their sound through *PulseAudio* (e.g. *Totem*, *Rhythmbox*). It seems that *PulseAudio* uses as the default output device one of your soundcards whereas *ALSA* uses the other.

Now, one option you have is to install the *PulseAudio Device Chooser* utility (*padevchooser* package) and use it to change the default card used by *PulseAudio*.

If you want you can make all your Applications to use *PulseAudio* so that you have a more uniform control over your audio; you'll need to follow [this how-to]("http://ubuntuforums.org/showthread.php?t=789578").

If you want to make *ALSA* as default, you can set it in *System -> Preferences -> Sound*. Although, it may not work 100%, some applications may still try to use *PulseAudio*.

---

### Post by lostpenguin on 2008-08-13
Thankyou so much! Thats just the job! Thats the last kink ironed out in ubuntu for now! 

 I got fed up with vista being slow, so moved to linux. I really like ubuntu and its philosophy. Its been a steep learning curve over the last couple of weeks but with the help of the forums its all been worked out!

Thanks for the help!

 not-so-lostpenguin

---

### Post by lostpenguin on 2008-08-14
Hello again. That solution didn't last. Now each time i start ubuntu I seem to get all sound coming out of either the on board sound card or the pci card, and it seems to be random to which it is...

 I have been trawling the forums for a solution, but havn't found one. I have pulse audio manager installed but don't know how to tell it to only use the CA0106 pci card. When i open up the devices section there are different options for each card, but no way of making one the default...

 I've tried to fix various problems with lots of different forum guides and just want to start over again without reinstalling ubuntu.




 how do I remove all the different types of drivers for the sound cards, all the different sound servers etc and just start again and only install the ALSA drivers for the pci card and only the pulse audio? 

 I've been struggling with this for days now, why is it so difficult? 

  PLEASE HELP ME!

---

### Post by markbuntu on 2008-08-14
Go here, there is a lot of information that you should know about setting up your sound defaults and many other things:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by lostpenguin on 2008-08-14
Thanks Markbuntu, I followed that guide, a little long winded but I manager to get it all sorted out, I didn't have the pulse audio volume manager plug in for the pulse-audio device chooser within which you get a list of all programs running. From this menu you just right click on the program you want too use a different sound card and change the default!

Thanks for the link, much appreciated!

---

### Post by markbuntu on 2008-08-14
Ok, no problem. I aplogize for the longwindedness but when you try to be comprehensive about a complicated issue.... but I bet you learned a lot.

Now could you please mark this thread as solved using the thread tools at the top of the page.

---

