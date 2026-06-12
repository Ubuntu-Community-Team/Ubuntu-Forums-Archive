---
title: "no Surround sound"
date: 2010-09-16
forum: Multimedia Software
---

### Post by kpsg25690 on 2010-09-16
I am currently running lucid lynx but have been facing this problem since jaunty.
I have a gigabyte g31m-es2l motherboard with 8 channel onboard audio.
i have the three jacks in the back hooked up as follows:-
Green:-Rear
Pink:-Front
Blue:-Subwoofer/centre

And the above setup works perfectly in windows7(i have a dual boot system) but i cannot seem to make it work in ubuntu.
sound comers only from the rear speakers and also if i insert a headphone jack into the front panel i hear sound coming from both the speakers and the headphones.

for more information about my setup follow the [[COLOR="Red"]link[/COLOR]]("http://www.alsa-project.org/db/?f=c8b55cc2a170a9a0896f61848de2df390b3008cf")

I hope i can finally hear surround sound on my ubuntu system.
Thanks

And i've tried quite a few guides on the same and have come up with no result.

---

### Post by MohanaRao on 2010-09-16
Dude/Dudette The refer the following link and do required modifications [https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound). It work's really

---

### Post by kpsg25690 on 2010-09-16
Already tried that,doesn't help

when i try to test 5.1 using the following command

speaker-test -Dplug:surround51 -c6 -l1 -twav

I receive the following error

Playback open error: -16,Device or resource busy

P.S. Its dude man

---

### Post by lidex on 2010-09-17
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by kpsg25690 on 2010-09-17
I already posted the link to the output in my post.

i'll post it again:-
[http://www.alsa-project.org/db/?f=c8b55cc2a170a9a0896f61848de2df390b3008cf]("http://www.alsa-project.org/db/?f=c8b55cc2a170a9a0896f61848de2df390b3008cf")

---

### Post by lidex on 2010-09-17
> **kpsg25690 said:**
> I already posted the link to the output in my post.

i'll post it again:-
[http://www.alsa-project.org/db/?f=c8b55cc2a170a9a0896f61848de2df390b3008cf]("http://www.alsa-project.org/db/?f=c8b55cc2a170a9a0896f61848de2df390b3008cf")

Can you post this info please:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by kpsg25690 on 2010-09-17
Thanks for the reply.
Here the output:-
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


---

### Post by lidex on 2010-09-17
I'm a little confused. Your alsa-base.conf file shows no tweaks yet alsa-info shows this:
```
!!Modprobe options (Sound related)
!!--------------------------------

snd-intel8x0: ac97_quirk=1 buggy_irq=1 enable=1 index=0
snd-hda-intel: model=3stack enable=yes
snd-hda-intel: model=auto position_fix=1 enable=yes

```
If you have removed these modifiers, I'll need you to post updated alsa-info

---

### Post by kpsg25690 on 2010-09-18
I'll post the information again after running both commands again.

Here's the script info link:-
[http://www.alsa-project.org/db/?f=3b04dbd87198f830e28aa3174025e0441fe71e9d]("http://www.alsa-project.org/db/?f=3b04dbd87198f830e28aa3174025e0441fe71e9d")

and heres the terminal output:-
> # autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2


Hope this helps..
Thanks for the replies.

---

### Post by lidex on 2010-09-18
Still there. Do you have a '~/.asoundrc'? If so post the contents.

Also this:
>  Onboard Audio

Audio Chipset
    Realtek ALC883

Audio Channels
    2/4/5.1/7.1-channel (Note)
    Note: To configure 7.1-channel audio, you need connect with the port of HD Audio standard via front panel and enable the multi-channel audio feature through the audio driver.



What is the dual-bios feature?

---

### Post by kpsg25690 on 2010-09-18
The file ~/.acoundrc is empty.
Dual bios is a feature of the motherboard which has two bios chips and is used to recover from any error in the bios contents of the first chip.
it's coming in all new gigabyte boards.

btw i ran the alsa upgrade script given in your signature,but no difference..

---

### Post by lidex on 2010-09-19
Those modprobe options need to go but I can't figure out where they are. Do you know?

---

### Post by kpsg25690 on 2010-09-19
i have no idea man..
i am kind of a noob when it comes to these things

---

### Post by lidex on 2010-09-19
OK. So you ran the alsa-upgrade script. Let's see where we stand. Please run the alsa-info script again:
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by kpsg25690 on 2010-09-20
here's the link:-

[http://www.alsa-project.org/db/?f=67cd8c5203735b505df4fd8a4502dc51865c5836]("http://www.alsa-project.org/db/?f=67cd8c5203735b505df4fd8a4502dc51865c5836")

---

### Post by kpsg25690 on 2010-09-21
bump!!
i need some help with this guys..

---

### Post by lidex on 2010-09-21
Did you set up another config file to fix your audio at some point? Also try removing /etc/asound.conf

---

### Post by kpsg25690 on 2010-09-24
i tried removing asound.conf doesn't help any..

---

### Post by lidex on 2010-09-25
How did you get v. 1.0.23 alsa? Did you use the guide from monospacewhatever? Did you compile with some extra options?

The only thing I can suggest at this time is reverting to your default alsa install so we can have some idea where we are.
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```

**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**

Now this:
```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```

**Reboot.**

---

### Post by kpsg25690 on 2010-10-03
i did a clean install but still the same problem.

---

### Post by lidex on 2010-10-03
> **kpsg25690 said:**
> i did a clean install but still the same problem.

OK. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by kpsg25690 on 2010-10-04
here's the link.
[http://www.alsa-project.org/db/?f=1c5f9d4b2b8b60ba1f02fa6a589774595f88c106]("http://www.alsa-project.org/db/?f=1c5f9d4b2b8b60ba1f02fa6a589774595f88c106")

---

### Post by lidex on 2010-10-05
> **kpsg25690 said:**
> here's the link.
[http://www.alsa-project.org/db/?f=1c5f9d4b2b8b60ba1f02fa6a589774595f88c106]("http://www.alsa-project.org/db/?f=1c5f9d4b2b8b60ba1f02fa6a589774595f88c106")

Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by kpsg25690 on 2010-10-06
Nothing man,no change.
sub woofer not working,neither do speakers mute when i connect headphones.
my linux box would be perfect if only surround sound would work..

---

### Post by lidex on 2010-10-06
> **kpsg25690 said:**
> Nothing man,no change.
sub woofer not working,neither do speakers mute when i connect headphones.
my linux box would be perfect if only surround sound would work..
What options do you have now in profiles? You need to select the proper one.

---

### Post by kpsg25690 on 2010-10-07
i don't understand.
could you please explain what i need to do?

---

### Post by lidex on 2010-10-07
> **kpsg25690 said:**
> i don't understand.
could you please explain what i need to do?

Open your 'Sound Preferences' - you should be able to access it from the volume icon in the panel. On the 'Hardware' tab, make sure the correct sound card is selected then use the drop-down menu below to select the correct profile. You'll need to have one with a surround output.

---

### Post by kpsg25690 on 2010-10-22
i've tried every possible configuration but only two of the speakers work and speakers do not mute when i connect headphones.
i've also changed to maverick and have the same problem.
it's a full install not an update..

---

### Post by lidex on 2010-10-22
> **kpsg25690 said:**
> i've tried every possible configuration but only two of the speakers work and speakers do not mute when i connect headphones.
i've also changed to maverick and have the same problem.
it's a full install not an update..

If you're on maverick now we'll need to see your current status. Would you mind running the alsa-info script again?

---

### Post by kpsg25690 on 2010-10-23
here's the link:-
[http://www.alsa-project.org/db/?f=bf945d696962a456b1dc0c25433820d0615475a5]("http://www.alsa-project.org/db/?f=bf945d696962a456b1dc0c25433820d0615475a5")

---

### Post by lidex on 2010-10-23
OK. Looks like the cruft is gone anyway. Now to try some alsa-base.conf options - one at a time - to see if we can get this thing going.

These models I would try first (insert after 'model=', no space):
```
3stack-dig
3stack-6ch
3stack-6ch-dig
auto
```
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model= 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by kpsg25690 on 2010-10-24
i tried the options and i got the following results:-
the first option showed no change:- i tried to test 4.1 and 5.1 profiles but only the front two speakers worked.

the next three options changed the profiles in the hardware tab but there was no 5.1 or 4.1 options,only stereo options.
[IMG]http://ubuntuone.com/p/Lyd/[/IMG]

shouldn't that show 3 outputs instead of 1 output?

---

### Post by lidex on 2010-10-24
I don't think so. Try returning your alsa-base.conf to default and then follow the guide here:
[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by kpsg25690 on 2010-10-31
i tried the guide,no help.

---

