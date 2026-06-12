---
title: "Very low volume sound"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Belgatom on 2007-03-01
AFter my first experiment on a desktop, I want to Ubuntize my laptop as well. I currently have a few problems (probably more but let's just see).

Sound is currently enormously silent. It's existent, I can here the Examples but ever so slightly. This I was only able to find out when using the headphone jack. I have no idea if the built in speakers work. They probably do but are so quiet I can't hear them.

Some technical info:

Sony PCG-TR5 EB (Japanese model)
Running Edgy Eft 6.10 installed
Soundcard info : Intel 82801

Any more info needed, just ask.

---

### Post by covox on 2007-03-01
I'm having exactly the same problem. Same soundcard (snd-hda-intel), runing Feisty, it arrived with kernel update 2.6.20-9 (reverting to 2.6.20-8 brings the sound back).

When running alsamixer, it appears that theres a new sound level called "Master", and it's switched on, but there's no volume slider to adjust it with. With PCM and the lappy volume control cranked up to the maximum, you can hear sound - however it's incredibly soft.

Using a slightly older kernel which doesn't have the new ALSA driver (in my case, 2.60.20-8) fixes the problem. This should probably be reported on Malone, but I have no idea where :/

---

### Post by darksider415 on 2007-03-01
I've also noticed this with Kubuntu Feisty, same card, only on a Toshiba A105-S4002 this time. 

Here's the output from lspci -v, if this is any aid to someone who can help with a possible solution.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff10
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f0b40000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

---

### Post by jethro10 on 2007-03-01
I got this sometimes and noticed it was after an automatic update. So.....

I double clicked the volume control in the top right of gnome, in the GUI, and moved the sliders to maximum for everything I could possibly find. It worked !! No alsa mixer from the command line.

It's happened a few times as well.


Cross your fingers.

J

---

### Post by jekylczar on 2007-03-01
Count me in as well...very low sound on Toshiba Satellite A100...:(   2.6.20-9 kernel...

---

### Post by Belgatom on 2007-03-06
Still beginner here: how do I find out the version of the kernel? 

How do I role it back to a previous version?

---

### Post by jekylczar on 2007-03-06
the way I am doing it now is to just arrow down when the grub boot menu comes up...that boots me into the previous kernel...to check your kernel version from the command line you type:

cat /proc/version

that should do it.

Does anyone know if they have fixed this bug yet?  I'm holding back on loading updates because of it...

---

### Post by jekylczar on 2007-04-03
did anyone ever find what was causing this?  I still have very low sound if I boot into a higher kernel version....how can I fix it?

---

### Post by jekylczar on 2007-04-03
i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

---

### Post by PacifistWarMachine on 2007-04-20
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

Thanks, that fixed it :).

---

### Post by ronocdh on 2007-04-20
> **PacifistWarMachine said:**
> Thanks, that fixed it :).
On my tower I have a very old SoundBlaster card; I too am experiencing this very low volume, but also a constant hiss when there is supposed to be silence. I've never experienced this before, so it's clearly from the upgrade to Feisty (I did a fresh install).

Is the fix provided above likely to resolve my hiss problem?

---

### Post by ronocdh on 2007-04-20
> **ronocdh said:**
> On my tower I have a very old SoundBlaster card; I too am experiencing this very low volume, but also a constant hiss when there is supposed to be silence. I've never experienced this before, so it's clearly from the upgrade to Feisty (I did a fresh install).

Is the fix provided above likely to resolve my hiss problem?

I went to the GUI volume control pref pane and disabled "analog/digital output jack" under Switches. No more hiss! =)

---

### Post by organelas on 2007-04-21
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

I'm running Feisty on a Toshiba SatelliteA100, and adding this line did not work... Any ideas? 

My problem is exactly the same, volume was fine on Edgy, but after the upgrade it became very low... and volume-control GUIs are set to max volume!

Thanks!

---

### Post by organelas on 2007-04-21
ops! not used to reboot to make things work on linux :) 

It worked after rebooting! thanks!!!

---

### Post by theringoffire67 on 2007-04-26
Yeah, that worked great for me too, THANKS!

---

### Post by satish_vell on 2007-04-28
Thanks, it worked after a reboot

---

### Post by airafroman on 2007-05-05
It worked for me too, very clear instructions, thx!

---

### Post by wheredidrealitygo on 2007-05-06
excellent fix, i was having this same problem on a toshiba satellite A100 laptop and this provided an awesome resolution! thanks!!

---

### Post by nwadams on 2007-05-07
yay, joins club...i have an A100 toshiba laptop too...and it worked...well sort of, it still isn't as loud as it is in windows:(

---

### Post by rev9ers on 2007-05-08
great fix! thanks

---

### Post by moran on 2007-05-08
> **organelas said:**
> ops! not used to reboot to make things work on linux :) 

It worked after rebooting! thanks!!!

I have a Toshiba Satellite too A105 and  the same problem with the sound but in the file alsa-base i can't find the option to modify here i'm puttin my file, so any help?

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

---

### Post by wheredidrealitygo on 2007-05-09
you should be putting this: options snd-hda-intel model=3stack

after the last options row at the very bottom.

so it goes from this:

options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

to this

options snd-usb-usx2y index=-2
options snd-hda-intel model=3stack
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

then save it, and reboot the system, should work then.

---

### Post by moran on 2007-05-10
ok but when i try to save it a message tell me tha i can't do it because of permission, should i do it in the terminal?

---

### Post by Onesimus on 2007-05-10
You should maybe try:

sudo gedit /etc/modprobe.d/alsa-base 

from the terminal window.


I have a slightly similar problem.  My sound is extremely quiet in RhythmMusic, but absolutely fine
in Audacity.  Has anyone had similar experiences ?

---

### Post by Bazarov on 2007-05-10
Similar deal, but with NO sound after upgrading to Feisty.

"option" line tricks did nothing for me. 

Downloaded and installed the latest ALSA drivers (a la this [HOWTO]("https://help.ubuntu.com/community/HdaIntelSoundHowto"); but still no luck.

Better yet, Amarok and Adept will not load, Kmixer is disabled, and Kaffeine freezes if I try to play a movie. My guess is that all of those (except Adept) are failing when trying to access sound-gear.

Thoughts?

---

### Post by moran on 2007-05-10
ok thanks for the solution it work the way you told me :lolflag:

---

### Post by Onesimus on 2007-05-11
Unfortunately, adding the line did not work for me.  

However, I have now resolved my issue of low sound in RhythmBox Music Player, but OK sound in Audicity.

I right-clicked on the volume control in the top right of the screen.  Selected Preferences and then choose
PCM device to control.  I don't know what PCM is - because there is no help pages or even any explanation.

Selecting this, and then pushing the volume control up - regained my volume in RhythmBox.

---

### Post by MasterOfTheHat on 2007-05-14
Awesome! This worked for me, too. 

Just FYI:
Compaq Evo N1000c laptop
Intel Corporation 82801CA/CAM sound card
Feisty Fawn 2.6.20-15-generic

---

### Post by zedfrugnug on 2007-05-14
For me turning up all the volumes with alsa mixer worked.
However I noticed that the alsa mixer does not respond at all to  master volume.
It only responds  to PCM en Headphone settings.

Is this a bug? It doesn't seem logical to me:???:

---

### Post by hondaman on 2007-05-17
The 3stack fix did not help my low sound volume on my toshiba p105-s9337

---

### Post by Casla on 2007-05-19
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

I ve got no idea what those options do.:confused: but it DID fix my problem. :KS

---

### Post by WhiteSlash on 2007-10-16
May Ubuntu be with you :) It worked.

---

### Post by kugrian on 2007-10-23
Just bumping this as it worked for me after 3 days of searching (on 7.10 as well :)).

---

### Post by lxtubman on 2007-10-24
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack


this worked on my toshiba satelite!

now... can you explain waht your doing in this line?

---

### Post by craetech on 2007-10-26
> **Onesimus said:**
> However, I have now resolved my issue of low sound in RhythmBox Music Player, but OK sound in Audicity.

I right-clicked on the volume control in the top right of the screen.  Selected Preferences and then choose
PCM device to control.  I don't know what PCM is - because there is no help pages or even any explanation.

Selecting this, and then pushing the volume control up - regained my volume in RhythmBox.
Yes, the above fix worked for me too. I'm using KDE (Kubuntu Fiesty) on a self-assembled desktop. I brought up KMix by left-clicking on the speaker icon in the system tray and then Mixer button. Switched to the Input tab, and pushed the PCM slider up (was 45% by default). In Windows, this is the equalevent to the Wave slider.

Thanks much, Onesimus.

Btw, PCM is short for Paracetamol. *rolls eyes*

---

### Post by ravidreams on 2007-11-04
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

Thank you very much for this simple fix. i had this problem in gutsy+toshiba

---

### Post by bharris25 on 2007-11-06
Thanks worked for my Toshiba A105 Satellite...finally.  Been messing around with the sound since beta testing gutsy.

---

### Post by fiskking on 2007-11-10
went into text editor to add to file but did not have permission to do so... any help?

---

### Post by kugrian on 2007-11-11
Type: 
```
gksudo gedit /etc/modprobe.d/alsa-base
```
into the terminal and open it that way.

---

### Post by viceyo on 2007-11-17
Hi, I had the same problem and that line fixed it. But I still have one problem:

The icon of the sound appears to be muted (although I do have sound). I checked the volume preferences and found out that it is displaying the line-in volume. When I move the slider up sound gets a lot of distortion so I have to put the slider down again to have good sound.

I just want to have the general volume control showing on the icon.

Any ideas on how to do this?

Thanks for your help.

---

### Post by subru77 on 2007-11-20
I used this page to fix the problem . It works :)

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by kingedmonds on 2007-12-20
Worked a treat for me.:guitar:

---

### Post by bw44 on 2008-01-04
> **Onesimus said:**
> Unfortunately, adding the line did not work for me.  

However, I have now resolved my issue of low sound in RhythmBox Music Player, but OK sound in Audicity.

I right-clicked on the volume control in the top right of the screen.  Selected Preferences and then choose
PCM device to control.  I don't know what PCM is - because there is no help pages or even any explanation.

Selecting this, and then pushing the volume control up - regained my volume in RhythmBox.

Thanks for this! I also did what **jekylczar** suggested in an earlier post> adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

But like you I don't understand what the the "Master" and "PCM" controls are, and why this works (sort of).  I have a Compaq Presario C300 with the Intel HDA snd-intel8x0 driver, and I noticed the following.

When my Volume Control Preferences setting is "Master' (right click on volume icon) the up and down volume control buttons and the mute button on my keyboard (above the function keys) are active and can change the volume control indicator in the Volume Control Playback tab.  And if I press the mute button on my keyboard it lights and the mute indicator appears on the panel icon in the upper right corner of the gnome desktop, But there's no change to the sound level from barely audible!

When I switch to the Volume Control Preferences "PCM" setting, I get control of the volume with the panel icon, but the connection between the keyboard buttons and the software is broken.

Does anyone know if there's a way to have both volume control and use of the keyboard buttons? (Really the best of both worlds!)

Thanks for any help.

---

### Post by secretkeeper81 on 2008-01-18
> **jekylczar said:**
> i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base 

options snd-hda-intel model=3stack

You rock..!! :guitar: It worked for me too, on a Toshiba Satellite A100-114 with Kubuntu 7.10! Thank you so much!

---

### Post by Helven Ink on 2008-01-21
sudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

Fixed my sound problem! Toshiba Satellite A105-S4164 with Ubuntu 7.04 Feisty Fawn
Thanks!

---

### Post by max7 on 2008-01-24
> adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

Helped me with Toshiba A100

Thanks

---

### Post by fireball2217 on 2008-01-25
Ok so im brand new to linux and I have a question.  Where do I go to add this stuff.  Im suffering from the same sound issue and it looks like this should be the fix but I dont really know how to go about fixing it.

---

### Post by mssg131187 on 2008-04-19
Thanks, its working just fine

---

### Post by mssg131187 on 2008-04-19
> **fireball2217 said:**
> Ok so im brand new to linux and I have a question.  Where do I go to add this stuff.  Im suffering from the same sound issue and it looks like this should be the fix but I dont really know how to go about fixing it.

Open Applications> Accessories> Terminal
Then type the following:
sudo gedit /etc/modprobe.d/alsa-base
Then type your password if it asks for it
Once gedit opens up with this document scroll down to the end of the page 
the last three line will look like this:

options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack           **(Add this line here, so its third last)**
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Save and restart the computer it should work...

---

### Post by Pontiac on 2008-04-21
I ran into this same issue tonight.  Previously, I had no issues with audio.  Tonight, I'd been wrestling with the issue.  What I found was that even though my master and PCM were at 100%, I had to crank the speakers to full to hear anything.  I started mucking with the other sliders and found that the Surround 3D was set to 0.  When I moved it up, audio got louder.

---

### Post by gatorbrit on 2008-04-28
> **mssg131187 said:**
> Open Applications> Accessories> Terminal
Then type the following:
sudo gedit /etc/modprobe.d/alsa-base
Then type your password if it asks for it
Once gedit opens up with this document scroll down to the end of the page 
the last three line will look like this:

options snd-usb-caiaq index=-2
options snd-hda-intel model=3stack           **(Add this line here, so its third last)**
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Save and restart the computer it should work...

This was the key for me - awesome!!!  THanks so much!!

---

### Post by feedmeh8 on 2008-06-17
perfect :D thanks much , it worked like a miracle

---

