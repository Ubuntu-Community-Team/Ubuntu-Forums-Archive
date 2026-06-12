---
title: "Anyway, sound is not wokring in Edgy!!"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by Jabran Asghar on 2007-02-11
Hi,

It may seem to be just another "Sound is not working" kind of thread, but please bear with it. I have spent hours trying solutions from different threads, but I am still not able to hear pretty voice of my Ubuntu in a consistent way. Below is what I have:

a) 3 sound cards: 
a1) Creatice Audigy ZS2, 
a2) Internal Sound card for headphone (Intel HC6)
a3) Logitech USB Headset.

b) "aplay -l" lists all of the above cards cards, that means Ubuntu has detected them correctly.

c) "cat /proc/asound/modules" lists following:
>  
0 snd_intel8x0
 1 snd_usb_audio
 2 snd_emu10k1

This shows that the drivers for each of the cards are loaded. Anyway, I have tried modprobe for each of the above card, and there is no error message i.e. driver loads correctly.

d) I have alsa-oss package installed.

e) I have put in "/etc/modprobe.d/alsa-base" the following:
> 
options snd-A index=1
options snd-B index=2
options snd-C index=0

i.e, I want USB Audio to have the highest priority and the Internal Headphones to have the the lowest.

f) I have restarted ALSA using "/etc/init.d/alsa-utils restart". (I have also tested rebooting the system anyway to make sure no settings remains unloaded.)

g) I have set mixer settings to reasonable volumes for all of the sound cards (using "alsamixer -c n", where n is the sound card number as mentioned above.)

h) In "Multimedia System Selector" under preferences, I have selected "ALSA" for input and output.


After doing all above I get NO SOUND!!

Ok, if not "No sound", then at least once some sound from Movie Player and SongBird, but from other applications --> none. After a reboot, no sound at all from any of the applications. Also I observed earlier that one application was outputting sound through one soundcard, and the other application was outputting through the other! I heave heard sound from each of the three cards at-least once.

Changing preferred soundcard using "Sound" option under preferences has no noticeable effect.

I have also tried purging + reinstalling "linux-sound-base alsa-base alsa-utils" modules, and going through the above steps afterwards, but no success. I have tried [this]("http://www.ubuntuforums.org/showthread.php?t=205449") sticky as well.

Can anybody tell me please what is the problem with Ubuntu sound system?

I guess from the above listed results that sound driver is loaded for each of the sound card, what only remains is to tell all the audio applications to use a particular sound card? BUT, How do I do that???

Any hints there?

Jabran

---

### Post by Jabran Asghar on 2007-02-12
Anyone there?

---

### Post by Jabran Asghar on 2007-02-17
Well, worked out something ... following solved the problem  (though still other things remain to check further)

-Remove all existing sound configuration
$sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$sudo apt-get install linux-sound-base alsa-base alsa-utils
VERY IMPORTANT:Packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
$sudo apt-get install gdm ubuntu-desktop

$sudo rm /etc/asound.conf
$sudo rm /etc/modprobe.d/alsa-base

-Reboot

-Find out the name of the card:
$cat /proc/asound/cards

 0 [Audigy2        ]: Audigy2 - Audigy 2 ZS [SB0350]
                      Audigy 2 ZS [SB0350] (rev.4, serial:0x20021102) at 0xd8c0, irq 169
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:1d.2-1.3, full speed
 2 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with AD1980 at 0xdffffa00, irq 58

-Then add this lines to  /etc/asound.conf. These will prioritize the use of "Headset" device among other devices.

> pcm.!default {
type hw
card Headset
}
ctl.!default {
type hw
card Headset
}


- System-->Preferences-->Sound --> Device --> SELECT ALSA for everything and USB Audio for conferencing and recording.
- System-->Preferences-->Multimedia System Selector -->SELECT ALSA for Audio input/output

- Click right mouse button on volume control icon --> Preferences --> Select Logitech USB for volume controls. (Or open ALSA mixer and select File->ChangeDevice-> Logitech USB Headset)

After doing above USB headset was selected correctly as the default sound device. Flash, MoviePlayer, SoundBird Kaffiene etc. output sound to USB Headset. Skype worked correctly (though needed to select USB headset in its audio properties).

When USB is disconnected, Audigy2 ZS also works correctly.

Problems to be resolved further:
-Realplayer and Mplayer still does not play sound (May be they are using OSS instead of ALSA. skype works
-USB headset Volume buttone and mic control does not work.
-Soundcard can be used used only by one program at one time.
-Vmware is perhaps still using OSS, have to select "/dev/dsp2" in virtual Machine settings for WinXP for its Audiocontroller. To use sound in VmWare, other applications (using sound cards) must be closed (and vice versa).

Will check further to resolved the remaining problems, but sound is now working.

---

### Post by Jabran Asghar on 2007-02-18
Was happy too soon! After reboot, next day it did not work :mad:

---

### Post by nfinitone on 2007-03-05
Hey Jabran,
I think you're experiencing the same problem I mentioned in my thread: [Sound disabled]("http://ubuntuforums.org/showthread.php?t=360918"). I haven't gotten a response from *anyone* in this board. So maybe you and I can work together to resolve this.

Tell me this, in the applications in which there is no sound, try connecting your speakers to the jack on that particular card and see if you hear anything. What I'm getting is that some apps are using my SBLive card, which should be default, and randomly other applications are using the onboard sound card, which by the way, is completely disabled in the BIOS.

---

