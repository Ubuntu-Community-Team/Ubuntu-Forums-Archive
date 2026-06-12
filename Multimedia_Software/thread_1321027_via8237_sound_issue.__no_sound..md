---
title: "via8237 sound issue.  no sound."
date: 2009-11-09
forum: Multimedia Software
---

### Post by juntjoo on 2009-11-09
so i have this sound issue, for which @ 1st i went to this thread for help: 

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

which was posted by someone with a comprehensive guide solution, but it appears the author isn't around anymore and that it was like 3 years old, so i thought i would try starting a new thread to see if i could attract people with new ideas.  until then i'm trying to follow the steps from this guide and here is how far i had gone... 

i'm on step 2 of the guide:
"Success - At this point, you should see your sound card listed. This is a positive sign because it means that Ubuntu is detecting the presence of your soundcard, but the drivers are not installed/running. Leave your shell running since you will need it."

and this is what i found for the audio results:

"00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
Subsystem: Micro-Star International Co., Ltd. Device b014
Flags: medium devsel, IRQ 22
I/O ports at d000 [size=256]
Capabilities: <access denied>
Kernel driver in use: VIA 82xx Audio
Kernel modules: snd-via82xx"

which confuses me a little. do i now need to go to that alsa sound driver archive you instruct in the next step? what should i do now? thanx!

yeah, i just visited this alsa project database place. i need a little guidance. it's a bit advanced for me. where do i start? anyone care to help. thanks in advance. my previous post shows a little bit about my situation.

---

### Post by Bunnybugs on 2009-11-09
You can skip the 4 steps, and move further on with '**_[SIZE=3]ALSA driver Compilation[/SIZE]_**[SIZE=3]'

[SIZE=1]Or, remove the 'Software Modem' driver (System>Administration>Hardware Drivers, Select 'Software Modem', and click 'Remove'

This wil help you get your sounds back...

The thread you refer to helps you only for one, or maybe 2 start-ups...

There is a major bug in the named driver, that shuts down your sound system....

If this doesn't work, you still can try the named thread...

Don't forget to reboot after removing the driver

EDIT:

The alsa source database has changed since the production of that guide...

so, it ain't available anymore!
[/SIZE][/SIZE]

---

### Post by juntjoo on 2009-11-10
Thanks meng!  I'll give it a shot in a bit and report back with my results!

---

### Post by Bunnybugs on 2009-11-10
Ur welcome:)

---

### Post by juntjoo on 2009-11-11
oh boy.  on step 6 of ALSA driver Compilation it says:

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=<enter driver name here e.g. via82xx> --with-oss=yes 
sudo make  

but the terminal comes back with:

bogi@bogi-desktop:/usr/src$ sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=via82xx
sudo: ./configure: command not found

besides which getting to this point was a complete blur.  it's been a bit cyclical and i don't really understand so much the steps i'm taking.  seems like i've been sent back to "step 4" a lot.  

checking with system testing my mic works but i still have no sound.  what else did i do....

oh yeah, i also went through: 

Getting the ALSA drivers from a *fresh* kernel

steps though i don't know what happened when it finished cuz when i came back(was taking a lot of time like over an hour) the comp was frozen with nothing on the screen and when i restarted it i somehow ended up with some new "xubuntu" version of ubuntu -did my drunk roommate do that somehow?  it's cool anyway, but how do i get my sound to work?***falling off my chair in exhaustion***

---

### Post by Bunnybugs on 2009-11-11
Go to System>Administration>Hardware Drivers...

Select the 'Software Modem' Driver, and press remove!

Reboot your system, This will help... The sound issue comes from the Software modem driver! Remove is located on the 'Activate' button on my screen, but says remove[IMG]http://img257.imageshack.us/img257/8937/screenshothardwaredrive.png[/IMG]

---

### Post by juntjoo on 2009-11-13
thanks again, tho i have "no proprietary drivers" in that list.  zero.  any other ideas?  thanks

---

### Post by juntjoo on 2009-11-13
tho it might actually have something to do with the fact that lately i've been logged into a "failsafe" session due to this issue:

[http://ubuntuforums.org/showthread.php?t=1317265](http://ubuntuforums.org/showthread.php?t=1317265)


but maybe not.  maybe you know better.  i'll check that later

---

### Post by deadtom on 2009-12-23
Having the same issue here since upgrading to 9.10. Sound card shows up fine, everything is detected fine but no sound.

No slmodem installed.
I tried removing pulseaudio.
I tried reinstalling ALSA.
I've completely reinstalled and patched Kubuntu.

HELP?

[I]$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/I]

----------------------------------------------------

[I]$ lspci | grep Audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)[/I]

----------------------------------------------------

[I]$ dmesg | grep Audio
[    9.694798] VIA 82xx Audio 0000:00:11.5: PCI INT C -> Link[ALKC] -> GSI 22 (level, low) -> IRQ 22
[    9.694961] VIA 82xx Audio 0000:00:11.5: setting latency timer to 6

[/I]----------------------------------------------------
[I]
$ lsmod | grep snd
snd_wavefront          37332  0
snd_cs4236             29620  0
snd_wss_lib            26012  2 snd_wavefront,snd_cs4236
snd_via82xx            23576  2
snd_ac97_codec        101216  1 snd_via82xx
snd_opl3_lib           10396  2 snd_wavefront,snd_cs4236
ac97_bus                1532  1 snd_ac97_codec
snd_hwdep               7200  2 snd_wavefront,snd_opl3_lib
snd_pcm_oss            37920  0
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  5 snd_cs4236,snd_wss_lib,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          9156  3 snd_wss_lib,snd_via82xx,snd_pcm
snd_mpu401              7016  0
snd_mpu401_uart         6940  4 snd_wavefront,snd_cs4236,snd_via82xx,snd_mpu401
snd_seq_dummy           2656  0
snd_seq_oss            28576  0
snd_seq_midi            6432  0
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  4 snd_wss_lib,snd_opl3_lib,snd_pcm,snd_seq
snd_rawmidi            22208  3 snd_wavefront,snd_mpu401_uart,snd_seq_midi
snd_seq_device          6920  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    59204  21 snd_wavefront,snd_cs4236,snd_wss_lib,snd_via82xx,snd_ac97_codec,snd_opl3_lib,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
soundcore               7264  1 snd
gameport               11368  3 snd_via82xx,ns558
[/I]

---

### Post by deadtom on 2009-12-27
erm.... bump

---

### Post by migel628 on 2010-01-16
I'm hitting the same problem w/ a fresh install of 9.10.  I'm using a MSI K8MM-V (MS-7142) motherboard w/ Turion64 CPU.  The problem looks to be related to this:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297744](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/297744)

And possibly this:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/433151](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/433151)

---

### Post by pi/roman on 2010-01-18
I also have a via 8237 chip.  I also did not have any sound until I muted the external amplifier by running alsamixer from terminal moving over to external mixer control and pressing m to mute it.  Another way is opening sound preferences under output tab selecting analog output / no amplifier.  I have sound although it is very choppy and I am currently seeking a solution to that.

I didn't have the modem problem, but if it is necessary to remove that driver and it is not available in the list as none of mine are either, maybe it would be possible to blacklist it such as placing a line "blacklist snd-via82xx-modem" in /etc/modprobe.d/blacklist.

---

