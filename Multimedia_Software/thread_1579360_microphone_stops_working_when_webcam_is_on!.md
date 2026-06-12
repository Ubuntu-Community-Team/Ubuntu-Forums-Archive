---
title: "microphone stops working when webcam is on!?"
date: 2010-09-21
forum: Multimedia Software
---

### Post by wolfskingirl on 2010-09-21
Hi guys ... I have a strange problem I can not find any solution to...
My microphone stops working the moment I start my camera. I first noticed it on skype, but then, after many tryings , it is doing it no mater which prorgams I use... even if you just start cheese ! Does anyone have a similar problem or solution to my worries!? 

My laptop is HP Pavillion dm3-1039wm, I am running 10.04.1 LTS

wolfskingirl@wolfskingirl:~$ uname -a
Linux wolfskingirl 2.6.32-24-generic-pae #43-Ubuntu SMP Thu Sep 16 15:30:27 UTC 2010 i686 GNU/Linux
wolfskingirl@wolfskingirl:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
wolfskingirl@wolfskingirl:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Sep 19 2010 for kernel 2.6.32-24-generic-pae (SMP).
wolfskingirl@wolfskingirl:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD81B1C5

==> /proc/asound/card1/codec#0 <==
Codec: ATI RS690/780 HDMI
wolfskingirl@wolfskingirl:~$ 

Thanks :)

---

### Post by Ghost|BTFH on 2010-09-23
Just a guess, but does your webcam perhaps have its own built-in mic?

If so, when it switches to the webcam, it might also be dragging along the webcam's mic, which may not be configured properly in your ubuntu setup.

IF that is the case, I'm not sure what you would have to do to resolve that, other than perhaps turning on the webcam and then going into your Sound setup and manually switching to the main mic again.

You could also check to see if it's just muting it, I've seen weirder things happen.

Cheers,
Ghost|BTFH

---

### Post by wolfskingirl on 2010-09-23
Thanks for the reply Ghost|BTFH
Unfortunatelly none of the suggested settings is working. Does not matter if I use external microphone plugged in or the internal mic of the webcam. It is all fine and works great until the moment I start the webcam. The mic is not muted, just stops working. All other sounds are ok. Are there any webcam settings I can play with? I am running out of ideas here... :(

---

### Post by Ghost|BTFH on 2010-09-23
So, ALL mics stop working at that time?

When you turn on the webcam and go into your Sound setup, what does it show for input devices available???

Cheers,
Ghost|BTFH

---

### Post by wolfskingirl on 2010-09-24
Yes, all mics stop working when the camera is on. As input devices I have "microphone" and "Line-In". Does not matter which one you use... same effect! 
In alsamixer all looks fine. 
In /etc/modprobe.d/alsa-base.conf
I added 
options snd-hda-intel model=auto  (also tried model=basic and model=hp-dm3) but nothing is changing. For some reason mic and webcam are not working at the same time!
:confused:

---

### Post by 0N3 on 2010-09-24
go to sound preferences and select Mic 2 'its under input tab im sure

---

### Post by wolfskingirl on 2010-09-24
I do not have microphone2 as an option
under input devices I only have 
microphone
and
line in

---

### Post by lkjoel on 2010-09-24
Is your sound card working?
Try replacing it.

---

### Post by Ahz The Cat on 2010-09-25
I am having the same problem with my new Lenovo laptop (AMD64).  After installing  gnome alsamixer gui and fiddling around, I'm presented with two microphone options in Alsa Mixer, front mic and mic. When   set to mic, I get sound input , but when I switch to front mic, it shows as muted in the sound preferences.  When I try to unmute, front mic is killed and the setting on the Alsa mixer reverts back to mic.  Strange indeed.  Perhaps this also happens upon activating the webcam in skype...  I havent had a chance to investigate, as it is hard to find someone to help me troubleshoot this issue via skype...

The whole shebang works perfectly in W7 tho, so I seriously doubt it is a sound card failure....

** I should add I'm using Lucid 64 and the latest version of Skype from the repositories**

---

### Post by Ahz The Cat on 2010-09-28
So....ah...any ideas team?

---

### Post by wolfskingirl on 2010-10-01
I still trying to figure out my problem. Webcam and microphone just do not work at the same time. Any other ideas? :confused:

---

### Post by Ghost|BTFH on 2010-10-02
Quick question, because it sounds like you're not using Pulse...are you using ALSA as your main source of sound?

---

### Post by wolfskingirl on 2010-10-02
I do not know what am I using anymore... I tried so many options... but anyway... I have this problem since day 1... this was a clean install on a new laptop. I just wiped off completely the win7 it came with, installed 10.04.1 LTS and noticed this problem of the webcam and mic not working at the same time. Everything else is great. So... at least at the start I was with pulse audio...
:confused:

---

### Post by wolfskingirl on 2010-10-02
Some sceenshots

---

### Post by wolfskingirl on 2010-10-02
At the moment I am using ALSA and the microphone is working fine, but either way... pulso or alsa... the mic stops working the moment I start the webcam... it is very weird and so far I could not find anyone with a similar issue! :(

---

### Post by Ghost|BTFH on 2010-10-03
Without being in front of the computer, it's hard to come up with solution ideas, but...

I would try setting it to Pulse, going into the audio properties and cranking the mic volume up as high as you can (taking it over 100% if necessary) and making sure your input/output controls do not change after plugging in the webcam.

Basically, I'd set everything up - verify it's working - plug in the webcam, go back and check all settings to verify nothing changed in the process...if nothing changed, I'd look at hardware issues.  If something changed, that'd be the culprit most likely.

Having the ALSA added into the mix just adds more locations you'd have to look to find the potential issue - it could be changing something in the ALSA mixer and leaving Pulse settings alone, which would make you believe everything's the same, yet it wouldn't be.

Does this make sense?

As a firm believer in ALSA for a long time, I have finally become a convert of Pulse Audio - they have the bugs worked out of it and it does what it should have since day one - allow for seamless audio integration.

Cheers,
Ghost|BTFH

---

### Post by wolfskingirl on 2010-10-04
Thanks Ghost|BTFH

It is not a hardware isssue because before deleting Win7 I made a few video calls with skype and it was working fine. My worries started with Ubuntu 10.04.1. It is obvious that this particular problem is a combination of the HP dm3-1039wm hardware and the OS I am running and I am looking for some sort of workaround so that I can continue using skype with video. I also have another laptop and small home server and both are running 10.04.1 LTS just fine... no such strange cam/mic issues...

I tried your suggestions, but the result is still the same. Mic stops working the moment the webcam is on... regardless of the application I use. It drives me nuts! :(

---

### Post by bcschmerker on 2010-10-05
After reading the prior posts this Thread, I strongly suspect a driver interference issue.  What model camera is on your rig?  Some cameras, that do not comply with the [USB Video Class](http://linuxuvc.berlios.de), have issues with their drivers hogging resources needed for audio capture.

---

### Post by urasay on 2010-10-05
i have the same problem with my HP Pavilion dv4-1120us. i did not notice earlier that the microphone stops working when i start the cam. i am just hoping that upgrading to 10.10 LTS will fix this.

---

### Post by wolfskingirl on 2010-10-05
Yeah... it drives me nuts I can not find a solution to this... lately I am thinking to upgrade to 10.10 and hopefully it will fix this issue...

---

### Post by wolfskingirl on 2010-10-08
I tested with live Fedora 13... same thing - microphone stops working when I start the webcam!

---

### Post by wolfskingirl on 2010-10-09
Tested with Ubuntu 8.04 - no sounds at all, Ubuntu 9.10 - again microphone stops working when I start the webcam. So although I am waiting for 10.10 to be released tomorrow, I somehow doubt it is going to sort out my problem.

It works great with external usb webcam though ... But it defeats the purpose... this is a laptop and I would like to use its built in webcam and mic. !:(

---

### Post by wolfskingirl on 2010-10-10
Just tested the new 10.10 :( Unfortunately nothing has changed in my case. Microphone stops working when webcam is on. No particular application just as before... cheese, skype, etc. I should try KDE, but I'm not a fan... rather stick to GNOME...:confused::(

---

### Post by Ahz The Cat on 2010-10-14
I'd guess you would have the same issues in KDE that you're having in gnome.  I still haven't found a way to get my webcam running, and after fiddling around with the settings, the mic has stopped working as well.  

Is it possible to dump PulseAudio in favor of tried and true ALSA and get these issues ironed out?

---

### Post by wolfskingirl on 2010-10-14
I have not tried to completely remove pulse audio. I was hoping someone will come up with some sort of workaround ... in the meantime I am using an external usb webcam with built in mic. :( What bugs me the most is the fact I can not find any similar problems online... weird issue ...

---

### Post by eduardoska on 2010-10-15
I Have this same problem! It's annoying because i can't use skype properly, i have to choose either speak or be seen!
Anyone found a solution on this?

---

### Post by eduardoska on 2010-10-15
I Found this solution to solve this problem on a hp dv4

First
```
sudo gedit /etc/modprobe.d/alsa-base.conf

```
Add following to the bottom:

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

Save changes and restart

Found it on:
[http://ubuntuforums.org/showthread.php?t=988474]("http://ubuntuforums.org/showthread.php?t=988474")

---

### Post by Ahz The Cat on 2010-10-15
Eduardoska-

That fixed the problem for me....skype works just fine now.  Thanks so much!:guitar:

---

### Post by eduardoska on 2010-10-15
I hope this fixes the problem for everyone else. I searched for the solution like 6 months!

---

### Post by lkjoel on 2010-10-17
> **eduardoska said:**
> I hope this fixes the problem for everyone else. I searched for the solution like 6 months!

That only works for certain laptops.

---

### Post by wolfskingirl on 2010-10-18
Wow... it was about time !
Thank you very much eduardoska !!!

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

work fine for me as well! 
I had tested with a very similar code just that the top line was with a model=auto and it was not making any difference.... oooops... actually...
my code was 
options snd-hda-intel model=auto
rather than 
options snd_hda_intel model=laptop

anyway it was not working but now internal microphone and webcam are working together just fine!

Thnaks again!

wolfskingirl :)

---

### Post by bcschmerker on 2010-10-22
> **eduardoska said:**
> I Found this solution to solve this problem on a hp dv4

First
```
sudo gedit /etc/modprobe.d/alsa-base.conf

```
Add following to the bottom:

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

Save changes and restart

Found it on:
[http://ubuntuforums.org/showthread.php?t=988474]("http://ubuntuforums.org/showthread.php?t=988474")

Nice work getting a Realtek® ALC-series audio chip to function correctly during video streaming.  Would:  
```
options snd-emu10k1 position_fix=1 enable=yes
  
```execute a similar fix for users of Creative Laboratories® Sound Blaster® Live! and Audigy (except SE) PCI audio cards?  I'm having a little trouble getting a USB Video Class camera to stream at all on my hybrid Everex® and would rather be prepared in advance, in case I run into a similar streaming-priority bug.

---

### Post by wolfskingirl on 2010-10-22
Thanks to all who were taking part in solving the mic/webcam issue !

If anyone knows more about those problems and wishes to share experience about code and hardware ... please do not hesitate to post it to this thread. 

Those having problems will certainly  appreciate it! Just as I did. My laptop now works in perfect harmony with Ubuntu 10.04.1 LTS ! 

Cheers!

wolfskingirl :)

---

### Post by d.zerocool.m on 2010-11-08
> **eduardoska said:**
> 
Add following to the bottom:

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes



Totally new to Fedora 14.  Looks like this bit of code has resolved the issue for many (am currently using HP dv4 1120us). My question is where exactly do I add the code?  To the bottom of? Can anyone provide a screenshot?

Thanks..

---

### Post by Thelinuxgeek on 2010-11-08
Wow, that's weird. OK so you say that it stops working, eh? My only guess is that your webcam has a mic built-in and when your webcam and mic are plugged in at the same time, it goes kaput. Sorry, but if that's the case then nothing much can be done.

---

### Post by lkjoel on 2010-11-08
Have you tried upgrading to Ubuntu 10.10?

---

### Post by d.zerocool.m on 2010-11-09
Okay - located the alsa-base.conf file and found that there was absolutely no code in there.  Can anyone supply the full code for the file?

---

### Post by Yezinki on 2010-11-12
Hi there,

I am facing a similar issue with my Dell XPS 1730 laptop & Sony Vaio VGC-LS1 desktop using Logitech Quick cam Pro 9000 USB with built in mic.

Can see & hear on the other end but my video & audio wont go simultaneously?

Plus Ubuntu becomes very non responsive?

Any clues how could get em fixed.

Regards!

---

### Post by artemiss on 2011-01-28
> **eduardoska said:**
> I Found this solution to solve this problem on a hp dv4

First
```
sudo gedit /etc/modprobe.d/alsa-base.conf

```Add following to the bottom:

options snd_hda_intel model=laptop
options snd-hda-intel position_fix=1 enable=yes

Save changes and restart

Found it on:
[http://ubuntuforums.org/showthread.php?t=988474](http://ubuntuforums.org/showthread.php?t=988474)


I was having the same problem and although this seemed to fix the microphone/ webcam clash, now my sound doesn't work at all.  As having sound is much more important to me than a microphone I removed the lines from the config file and restarted, but there is still no sound.  I cannot find a way to get the sound back on my computer now, microphone or not. Can anyone help me?

lspci | grep Audio yeilds:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]

and I have a HP dv4-2145dx laptop

Thanks!

---

### Post by artemiss on 2011-01-29
Ok, so I reinstalled the alsa packages and got my sound back, but I still don't have a functioning microphone.

---

### Post by bcschmerker on 2011-04-22
> **d.zerocool.m said:**
> Okay - located the alsa-base.conf file and found that there was absolutely no code in there.  Can anyone supply the full code for the file?From my own Everex® running 10.04-LTS, here's what printed out from cat /etc/modprobe.d/alsa-base.conf, as an example: 
```
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

```Your system will probably differ from the above, but a typical way to lock a Creative SB Live! or Audigy (except SE) into this stack in the face of potential issues with camera drivers might be: 
```
# Set emu10k1 priority position
options snd-emu10k1 position_fix=1 enable=yes
```at the base of the data "stack" in alsa-base.conf, using GNOME Text Editor (gksudo gedit /etc/modprobe.d/alsa-base.conf).

---

