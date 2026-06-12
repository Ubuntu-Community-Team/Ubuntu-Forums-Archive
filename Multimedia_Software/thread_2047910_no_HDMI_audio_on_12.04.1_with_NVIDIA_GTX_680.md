---
title: "no HDMI audio on 12.04.1 with NVIDIA GTX 680"
date: 2012-08-25
forum: Multimedia Software
---

### Post by xoloki on 2012-08-25
Yesterday, I upgraded my old 10.04 install to 12.04.1 in order to get HDMI audio working on my GTX 680.  It appears to be working, other than the actual lack of sound.

The kernel thinks it found the HDMI connection:

```

[   52.666642] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[   52.672052] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
[   52.735114] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1
[   52.740082] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1
[   53.512047] HDMI: detected monitor HT-RC160
[   53.512051]      at connection type HDMI
[   53.512060] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[   53.512072] HDMI: supports coding type LPCM: channels = 2, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   53.512084] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 88200 96000 176400 192000, bits = 16 20 24
[   53.512094] HDMI: supports coding type AC-3: channels = 8, rates = 32000 44100 48000, max bitrate = 640000
[   53.512102] HDMI: supports coding type DTS: channels = 8, rates = 44100 48000, max bitrate = 1536000
[   53.512109] HDMI: supports coding type DSD (One Bit Audio): channels = 6, rates = 44100
[   53.512116] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000
[   53.512124] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 88200 96000 176400 192000
[   53.512132] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 48000 96000 192000

```

ALSA thinks the card is there:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I made sure the HDMI SPDIF interfaces were not muted in alsamixer:

[IMG]http://www.divisionbyzero.com/joey/alsamixer-play.png[/IMG]

I have the HDMI card configured in pavucontrol:

[IMG]http://www.divisionbyzero.com/joey/pavucontrol-conf.png[/IMG]

And when I play a movie in mplayer, the output tab shows audio:

[IMG]http://www.divisionbyzero.com/joey/pavucontrol-output.png[/IMG]

As does the play tab:

[IMG]http://www.divisionbyzero.com/joey/pavucontrol-play.png[/IMG]

If I try to use aplay to directly talk to HDMI, I get a weird error:

```

xoloki@xocotl:~/Pictures$ aplay -D hw:1,3 /usr/share/sounds/purple/alert.wav 
Playing WAVE '/usr/share/sounds/purple/alert.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono
aplay: set_params:1087: Channels count non available

```

I get the same error if I try the other 3 ports:

```

xoloki@xocotl:~/Pictures$ aplay -D hw:1,7 /usr/share/sounds/purple/alert.wav 
Playing WAVE '/usr/share/sounds/purple/alert.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono
aplay: set_params:1087: Channels count non available
xoloki@xocotl:~/Pictures$ aplay -D hw:1,8 /usr/share/sounds/purple/alert.wav 
Playing WAVE '/usr/share/sounds/purple/alert.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono
aplay: set_params:1087: Channels count non available
xoloki@xocotl:~/Pictures$ aplay -D hw:1,9 /usr/share/sounds/purple/alert.wav 
Playing WAVE '/usr/share/sounds/purple/alert.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono
aplay: set_params:1087: Channels count non available

```

If I use aplay without specifying the device, I get no errors (but no sound):

```

xoloki@xocotl:~/Pictures$ aplay  /usr/share/sounds/purple/alert.wav 
Playing WAVE '/usr/share/sounds/purple/alert.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono

```

Finally, I verified that the master volume is not turned down for playback:

[IMG]http://www.divisionbyzero.com/joey/mixer-hdmi.png[/IMG]

This is running on xubuntu 12.04.1 on amd64 upgraded yesterday from 10.04.  HDMI audio works in XP on this machine, so I know there is no hardware issue.  

Does anyone have any suggestions?  This is driving me insane, especially since by all appearances it should be working.

thanks,

Xolotl Loki

---

### Post by Cheesemill on 2012-08-25
Whenever I've used HDMI audio with an Nvidia card there have been 3 different HDMI outputs for me to choose from in pavucontrol, all labelled 'Digital Stereo (HDMI) Output'.

I've just had to try all 3 until I found the one which works.

---

### Post by xoloki on 2012-08-25
> **Cheesemill said:**
> Whenever I've used HDMI audio with an Nvidia card there have been 3 different HDMI outputs for me to choose from in pavucontrol, all labelled 'Digital Stereo (HDMI) Output'.

I've just had to try all 3 until I found the one which works.

Thanks for the quick response!

In the Configuration tab of pavucontrol, the Profile drop-down has 4 instances of "Digital Stereo (HDMI) Output" and 4 instances of "Digital Surround 5.1 (HDMI) Output".  I've tried all 8 profile options, and never got any sound.

Do I need to restart pulse or anything after changing the profile?

---

### Post by Cheesemill on 2012-08-25
> **xoloki said:**
> Thanks for the quick response!

In the Configuration tab of pavucontrol, the Profile drop-down has 4 instances of "Digital Stereo (HDMI) Output" and 4 instances of "Digital Surround 5.1 (HDMI) Output".  I've tried all 8 profile options, and never got any sound.

Do I need to restart pulse or anything after changing the profile?
I've never had to restart, I've just clicked on 'Test Speakers' each time I've made a different choice to check if I've chosen the correct option.

If you have any options for IEC958 outputs it might be worth trying those as well.

---

### Post by xoloki on 2012-08-25
> **Cheesemill said:**
> I've never had to restart, I've just clicked on 'Test Speakers' each time I've made a different choice to check if I've chosen the correct option.

If you have any options for IEC958 outputs it might be worth trying those as well.

pavucontrol doesn't have a "Test Speakers" button.  Is this something in the Sound properties page of the default UI?  I'm running Xubuntu, but I can make a new user and try configuring via Unity.

---

### Post by Cheesemill on 2012-08-25
It's in the sound settings in Ubuntu, I don't have a Xubuntu installation handy at the moment so I'm having to go by memory (It's obviously not that good at the moment though).

---

### Post by xoloki on 2012-08-26
> **Cheesemill said:**
> It's in the sound settings in Ubuntu, I don't have a Xubuntu installation handy at the moment so I'm having to go by memory (It's obviously not that good at the moment though).

I installed ubuntu-desktop and unity, made a new user, logged in and tried configuring with the sound settings page:

[IMG]http://www.divisionbyzero.com/joey/hdmi-unity.png[/IMG]

Regardless of which Profile I selected in pavucontrol, the sound setting page always thought HDMI was using Port 2.  pavucontrol itself would recognize that each Profile would have a different Port number.  

You can see this in the screenshot.

Sound settings would only allow me to change between stereo and 5.1, both running on Port 2.  Neither produced any sound, either from the Test Sound dialog or background playing.  

Still nothing in dmesg or pulseaudio output to suggest anything is going wrong.

---

### Post by xoloki on 2012-08-26
I also tried upgrading my NVIDIA driver.  First I upgraded to the current-updates version, which had no effect.  I then tried updating to the x-updates NVIDIA driver, which is version 304.37-0ubuntu1~precise~xup1.  Still no sound :(

---

### Post by pqwoerituytrueiwoq on 2012-08-26
try each of the options in the 1st select box here (i have 4 labeled hdmi but only the last one works for me)
it is possible that hdmi audio is not supported on the 680 by the kernel yet
there is a trick you can use to make analog audio work if all else fails
[http://ubuntuforums.org/showthread.php?t=1926721](http://ubuntuforums.org/showthread.php?t=1926721)
i am using a 550 TI

---

### Post by xoloki on 2012-08-27
> **pqwoerituytrueiwoq said:**
> try each of the options in the 1st select box here (i have 4 labeled hdmi but only the last one works for me)


I tried that, pavucontrol gives me 4 options for stereo HDMI and 4 for 5.1 HDMI (see screenshot in my original post).  None of them gives any sound when selected.

> **pqwoerituytrueiwoq said:**
> 
it is possible that hdmi audio is not supported on the 680 by the kernel yet


That's what I'm afraid of.  I'm going to see if I can get a straight answer from NVIDIA as to whether HDMI audio should work on stock ubuntu 12.04.  If it should, I may have to do a clean install.

> **pqwoerituytrueiwoq said:**
> 
there is a trick you can use to make analog audio work if all else fails
[http://ubuntuforums.org/showthread.php?t=1926721](http://ubuntuforums.org/showthread.php?t=1926721)
i am using a 550 TI

Can you link directly to which post in that thread you're talking about?  I see lots of external links and people claiming to solve different problems, mostly on old versions of ubuntu.

---

### Post by pqwoerituytrueiwoq on 2012-08-28
[http://ubuntuforums.org/showpost.php?p=11716011&postcount=12](http://ubuntuforums.org/showpost.php?p=11716011&postcount=12) (force analog audio to tv)
[http://ubuntuforums.org/showpost.php?p=11716011&postcount=19](http://ubuntuforums.org/showpost.php?p=11716011&postcount=19) (i got hdmi working)

---

### Post by xoloki on 2012-11-03
HDMI audio suddenly started working for me one day, but stopped after the next reboot (which I postponed until the system froze after literally months of running).

Out of frustration, I had started using my bluetooth headset to listen to audio from the computer.  This worked perfectly, with pavucontrol allowing me to control the profile and what applications were using the headset.  Then one day I fell asleep without turning the headset off.  It ran out of battery overnight, and when I woke up in the morning, I could hear audio through my stereo (from the SWTOR server select screen).

This was similar to one of the suggested troubleshooting steps, but for some reason it only worked that one time.  Since the reboot, I have let the headset die overnight several times, with no HDMI audio in the morning.

I'm at the point of being willing to pay for Canonical support just to get this fixed.  I've wasted far more time than the $105/year/desktop fee would be worth.  This is the first time I've failed to get Linux audio working since 1996.

---

### Post by BicyclerBoy on 2012-11-03
Can you explain your hookup?

PC ---hdmi--> HT amp --hdmi--> monitor ?

Your amp brand has been known to cause trouble because of the way it adds it own EDID data..(not wrong but different)..

Don't select Digital 5.1 surround..you want Digital stereo HDMI & then tick the boxes that your amp supports (AC3 DTS etc)..

speaker-test -c 2 -r 48000 -l 2 -D hw:1,9
speaker-test -c 2 -r 48000 -l 2 -D hw:1,8
speaker-test -c 2 -r 48000 -l 2 -D hw:1,7
speaker-test -c 2 -r 48000 -l 2 -D hw:1,3

With amp & monitor attached & turned on post the contents of any files here that are not zero length:
ls -al /proc/asound/card0/eld*

---

### Post by xoloki on 2012-11-05
Thanks so much for the reply.  This is really driving me crazy.

> **BicyclerBoy said:**
> Can you explain your hookup?

PC ---hdmi--> HT amp --hdmi--> monitor ?


Yes, that's the path in question (also two DVI outputs to mirrored LCDs, but no audio in that path).

> **BicyclerBoy said:**
> 
Your amp brand has been known to cause trouble because of the way it adds it own EDID data..(not wrong but different)..


Makes sense.

> **BicyclerBoy said:**
> 
Don't select Digital 5.1 surround..you want Digital stereo HDMI & then tick the boxes that your amp supports (AC3 DTS etc)..


That's the config which briefly worked.  Also, I'm using port 2 because pacmd says it's the available one:

```

hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, available: yes)

```

> **BicyclerBoy said:**
> 
speaker-test -c 2 -r 48000 -l 2 -D hw:1,9
speaker-test -c 2 -r 48000 -l 2 -D hw:1,8
speaker-test -c 2 -r 48000 -l 2 -D hw:1,7
speaker-test -c 2 -r 48000 -l 2 -D hw:1,3


My card ID is now 0, not 1 (not sure when that changed):

```

xoloki@xocotl:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

When I try devices hw:0,[389], it works but with no sound.

With device 7 (which is hdmi-output-1 aka DisplayPort 2) I get:

```

Playback device is hw:0,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy

```

If I change the port in pavucontrol or pacmd, whichever I choose then becomes busy when I run speaker-test.

> **BicyclerBoy said:**
> 
With amp & monitor attached & turned on post the contents of any files here that are not zero length:
ls -al /proc/asound/card0/eld*


```

xoloki@xocotl:~$ ls -al /proc/asound/card0/eld*
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.0
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.1
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.2
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.3

```

The timestamp appears to be current time when I ran the ls command.

---

### Post by xoloki on 2012-11-05
> **xoloki said:**
> ```

xoloki@xocotl:~$ ls -al /proc/asound/card0/eld*
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.0
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.1
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.2
-rw-r--r-- 1 root root 0 Nov  5 09:09 /proc/asound/card0/eld#0.3

```
The timestamp appears to be current time when I ran the ls command.

Sorry, I should have tried cat before assuming the files were actually empty:

```

xoloki@xocotl:~$ for i in /proc/asound/card0/eld*; do echo "$i"; cat "$i"; done

/proc/asound/card0/eld#0.0
monitor_present		0
eld_valid		0

/proc/asound/card0/eld#0.1
monitor_present		1
eld_valid		1
monitor_name		HT-RC160
    
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0xcb3d
product_id		0x869
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count		8
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0x1] LPCM
sad1_channels		8
sad1_rates		[0x1ee0] 32000 44100 48000 88200 96000 176400 192000
sad1_bits		[0xe0000] 16 20 24
sad2_coding_type	[0x2] AC-3
sad2_channels		8
sad2_rates		[0xe0] 32000 44100 48000
sad2_max_bitrate	640000
sad3_coding_type	[0x7] DTS
sad3_channels		8
sad3_rates		[0xc0] 44100 48000
sad3_max_bitrate	1536000
sad4_coding_type	[0x9] DSD (One Bit Audio)
sad4_channels		6
sad4_rates		[0x40] 44100
sad5_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad5_channels		8
sad5_rates		[0xc0] 44100 48000
sad6_coding_type	[0xb] DTS-HD
sad6_channels		8
sad6_rates		[0x1ec0] 44100 48000 88200 96000 176400 192000
sad7_coding_type	[0xc] MLP (Dolby TrueHD)
sad7_channels		8
sad7_rates		[0x1480] 48000 96000 192000

/proc/asound/card0/eld#0.2
monitor_present		0
eld_valid		0

/proc/asound/card0/eld#0.3
monitor_present		0
eld_valid		0


```

---

### Post by BicyclerBoy on 2012-11-05
Well the eld files tells us

speaker-test -c 2 -r 48000 -l 2 -D hw:0,7

is the right sub-device..

Odd that pulse is locking the alsa device..don't think that's normal but could be wrong.

The /proc/asound/card0/ folder should be root:audio..
I think you are a member of audio group becuase of the aplay output..
Alsa seems to have bizarre permissions on some folders.

Have you added any extra stuff to :
- /etc/asound.conf (anything pulse?)
- /etc/pulse/default.pa (added any modules ?)
- .asoundrc

Added anything in /etc/modprobe.d/*.conf that would effect snd-hda-intel ?

---

### Post by xoloki on 2012-11-05
> **BicyclerBoy said:**
> Well the eld files tells us

speaker-test -c 2 -r 48000 -l 2 -D hw:0,7

is the right sub-device..


That's good :)

> **BicyclerBoy said:**
> 
Odd that pulse is locking the alsa device..don't think that's normal but could be wrong.


It seems wrong from the various troubleshooting guides I've seen.

> **BicyclerBoy said:**
> 
The /proc/asound/card0/ folder should be root:audio..
I think you are a member of audio group becuase of the aplay output..
Alsa seems to have bizarre permissions on some folders.


This is a very old install, going back to xubuntu 9.04.  I upgraded to 10.04, then to 12.04.1.  So I'm not surprised there's cruft.  

If I ran a live CD, would I be able to test this?  Or do I need the NVIDIA binary drivers to use HDMI audio?  I'm totally willing to reinstall if I have a reason to believe it will fix this.

> **BicyclerBoy said:**
> 
Have you added any extra stuff to :
- /etc/asound.conf (anything pulse?)


I don't even have /etc/asound.conf.  Is that a problem?

> **BicyclerBoy said:**
> 
- /etc/pulse/default.pa (added any modules ?)


I know at some point I messed with /etc/pulse/default.pa, but it was after I'd started troubleshooting.  Is there a simple way to get the default file reinstalled?

> **BicyclerBoy said:**
> 
- .asoundrc


My .asoundrc is completely commented out.

> **BicyclerBoy said:**
> 
Added anything in /etc/modprobe.d/*.conf that would effect snd-hda-intel ?


xoloki@xocotl:~$ grep snd-hda-intel /etc/modprobe.d/*.conf

Nothing, unless I need to do more than a simple grep.

---

### Post by xoloki on 2012-11-05
I think I had mplayer running before when I tried speaker-test, because now it doesn't complain about the device being busy.  But sadly still no sound:

```

xoloki@xocotl:~$  speaker-test -c 2 -r 48000 -l 2 -D hw:0,7

speaker-test 1.0.25

Playback device is hw:0,7
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 32 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
Time per period = 5.639933
 0 - Front Left
 1 - Front Right
Time per period = 5.971984

```

---

### Post by BicyclerBoy on 2012-11-06
I would look for & comment out any lines:
"load-module module-alsa-sink"
"load-module module-alsa-source"
in the file /etc/pulse/default.pa.

Check your user is a member of pulse & pulse-access groups.

The .asoundrc is an old file from previous..

Grep for snd_hda_intel as well.. either the "-" & "_" are used randomly..

Failing all this...I would add the xorg-edgers ppa to get a later kernel. This will get you a later alsa kernel module..It is possible the audio codecs on the GTX680 are different to others ..

---

### Post by xoloki on 2012-11-09
> **xoloki said:**
> 
If I ran a live CD, would I be able to test this?  Or do I need the NVIDIA binary drivers to use HDMI audio?  I'm totally willing to reinstall if I have a reason to believe it will fix this.


I found the answer to this at 

 [ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html")

You do in fact need to be running the NVIDIA binary drivers to get HDMI sound.  So unless there's a way to boot the LiveCD with NVIDIA drivers, I will not be able to test this short of a full re-install.

---

### Post by xoloki on 2012-11-09
> **BicyclerBoy said:**
> I would look for & comment out any lines:
"load-module module-alsa-sink"
"load-module module-alsa-source"
in the file /etc/pulse/default.pa.


There weren't any.  The NVIDIA troubleshooting guide I linked above actually suggested adding 

load-module module-alsa-sink device=hw:1,7

No difference with and without that line.

> **BicyclerBoy said:**
> 
Check your user is a member of pulse & pulse-access groups.


```

xoloki@xocotl:~$ groups
xoloki adm dialout cdrom audio video plugdev fuse lpadmin admin sambashare pulse pulse-access debian-tor

```


> **BicyclerBoy said:**
> 
The .asoundrc is an old file from previous..

Grep for snd_hda_intel as well.. either the "-" & "_" are used randomly..


Nothing with 

  grep -i 'snd.*hda.*intel' /etc/modprobe.d/*.conf

> **BicyclerBoy said:**
> 
Failing all this...I would add the xorg-edgers ppa to get a later kernel. This will get you a later alsa kernel module..It is possible the audio codecs on the GTX680 are different to others ..

I'll definitely try that before re-installing.  But at this point I'm ready to try plugging the HDMI cable directly into the TV, which is what the NVIDIA tech support people wanted me to try first.  If that works, I may just give up on having nice 7.2 positional sound, at least for a while ;)

Thanks for all your help!

---

### Post by xoloki on 2012-11-09
> **xoloki said:**
> 
I'm at the point of being willing to pay for Canonical support just to get this fixed.  I've wasted far more time than the $105/year/desktop fee would be worth.  This is the first time I've failed to get Linux audio working since 1996.


In case anyone is curious, after an automated email telling me they would get in touch in 2 business days, I have heard nothing back from Canonical.  Apparently they are not interested in taking my money to fix this problem for me.

This is sad, because one of the reasons to use Ubuntu is to have Canonical support available if needed.  Clearly this is not the case if you want simple fee for service.

---

### Post by BicyclerBoy on 2012-11-09
Sorry.. Made a mistake...
your audio device is hw:0,3. (from eld files)
Hard to get good help these days..

eld#0.0  links to pin codec 3 first ELD record (TV)
eld#0.1  links to pin codec 3 2nd ELD record (amp)

Not sure why 1st record has been blanked out, could this be the problem with this model AVR?

Can you try:
speaker-test -c 2 -r 48000 -l 2 -D hw:0,3

The entry in /etc/pulse/default.pa:
load-module module-alsa-sink device=hw:1,7
is a work-around for pulse alsa bugs in earlier versions.

You still have nvidia as card0  or card1 ??
You have to run nVidia driver for HDA hdmi audio..You can install it in a LiveCD session & then run by logging out/login to restart X.

---

### Post by xoloki on 2012-11-11
> **BicyclerBoy said:**
> Sorry.. Made a mistake...
your audio device is hw:0,3. (from eld files)
Hard to get good help these days..


Perhaps, but I do appreciate the effort :)

> **BicyclerBoy said:**
> 
eld#0.0  links to pin codec 3 first ELD record (TV)
eld#0.1  links to pin codec 3 2nd ELD record (amp)

Not sure why 1st record has been blanked out, could this be the problem with this model AVR?


Definitely possibly.

> **BicyclerBoy said:**
> 
Can you try:
speaker-test -c 2 -r 48000 -l 2 -D hw:0,3


Still no sound.  I get the device busy error if I have device #3 configured in pavucontrol, and there are output clients.  Otherwise, it run with no error (but no sound).

> **BicyclerBoy said:**
> 
The entry in /etc/pulse/default.pa:
load-module module-alsa-sink device=hw:1,7
is a work-around for pulse alsa bugs in earlier versions.

You still have nvidia as card0  or card1 ??


Yes:

```

xoloki@xocotl:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

> **BicyclerBoy said:**
> 
You have to run nVidia driver for HDA hdmi audio..You can install it in a LiveCD session & then run by logging out/login to restart X.

I'll try that next.  If that works, then it's re-install time.  If it doesn't, then I'll try connecting HDMI directly to the TV.

Thanks again for all your help.

---

### Post by xoloki on 2012-11-21
Today I found a way to make HDMI audio work on my system.  

I had noticed that when running nvidia-settings, I heard a series of clicks from the HT amp.  This same series occurred whenever there was an HDMI renegotiation, so I wondered if audio would work immediately after this.  

So I tried running mplayer, then nvidia-settings.  Suddenly I had audio!

But when I killed mplayer, and restarted it, audio was gone.  I noticed the series of clicks when mplayer exited, so clearly the cleanup was triggering an audio reset somewhere.  I remembered though that I was using VDPAU in my .mplayer/config, so I changed my mplayer vo to xv.  Now I was able to run mplayer repeatedly and not lose audio.

Throughout this I was always able to reset audio to a working state by running nvidia-settings, FSM be praised.

I had another scare with WINE; just switching into and out of a fullscreen WINE app would reset audio to not working, which was very annoying.  But by running my WINE app in fullscreen/windowed, with a normal WM window set to always-on-top, I was finally able to switch in and out of WINE without triggered the audio reset.

I even updated my kernel, rebooted, and this still works.  So I'm almost ready to declare victory.

---

