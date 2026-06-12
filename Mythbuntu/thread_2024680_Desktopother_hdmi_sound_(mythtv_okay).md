---
title: "Desktop/other hdmi sound (mythtv okay)"
date: 2012-07-14
forum: Mythbuntu
---

### Post by iitywygms on 2012-07-14
Hi all.  I have been searching for weeks and have not found a solution.
No hdmi sound at all on desktop,youtube, or xbmc.

I have sound in mythtv no problem.  Configured as ALSA:hdmi:CARD=NVidia,Dev=1


kernel = 3.2.0-27-generic
Processor = Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
video = gt430
mythbuntu = .25 latest fixes
alsa = 1.0.25
nvidia driver = 295.40

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have tried every possible solution I can find on the web and NOTHING gets me hdmi sound in the desktop or anywhere else except mythtv.

Yes, I can use the spdif output for mythtv and everywhere else.  However, the spdif out has a very loud and annoying popping sound when exiting and entering live tv.

So I want to use hdmi.  And hdmi should work right??

Suggestions?  Am I missing something simple?
Is mythtv not allowing other programs to use the hdmi sound?
Yes, alsamixer is all unmuted.

Appreciate the help.

---

### Post by nickrout on 2012-07-15
> **iitywygms said:**
> Hi all.  I have been searching for weeks and have not found a solution.
No hdmi sound at all on desktop,youtube, or xbmc.

I have sound in mythtv no problem.  Configured as ALSA:hdmi:CARD=NVidia,Dev=1


kernel = 3.2.0-27-generic
Processor = Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz
video = gt430
mythbuntu = .25 latest fixes
alsa = 1.0.24
nvidia driver = 295.40

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have tried every possible solution I can find on the web and NOTHING gets me hdmi sound in the desktop or anywhere else except mythtv.

Yes, I can use the spdif output for mythtv and everywhere else.  However, the spdif out has a very loud and annoying popping sound when exiting and entering live tv.

So I want to use hdmi.  And hdmi should work right??

Suggestions?  Am I missing something simple?
Is mythtv not allowing other programs to use the hdmi sound?
Yes, alsamixer is all unmuted.

Appreciate the help.

"Other" programmes usually send sound to the default alsa device. You can use /etc/asound.conf to set the default audio device to the hdmi device and all should be sweet.

---

### Post by iitywygms on 2012-07-15
I tried several varations of asound.conf

Maybe I had it set up wrong?

What would I put in asound.conf to map all audio to hdmi?

Thanks.

---

### Post by nickrout on 2012-07-15
> **iitywygms said:**
> I tried several varations of asound.conf

Maybe I had it set up wrong?

What would I put in asound.conf to map all audio to hdmi?

Thanks.

something like:

```
pcm.!default {
type plug
slave.pcm {
type hw
card 1
device 3
}
}
```

Play with the device number until it works.

---

### Post by iitywygms on 2012-07-15
Did a copy and paste of the above.
Reboot and still nothing.  Mythtv still works fine.

I had tried various asound.conf in the past and never found one that worked.
This is really confusing.

---

### Post by nickrout on 2012-07-15
> **iitywygms said:**
> Did a copy and paste of the above.
Reboot and still nothing.  Mythtv still works fine.

I had tried various asound.conf in the past and never found one that worked.
This is really confusing.

play with the device number

---

### Post by iitywygms on 2012-07-15
Tried 3,7,8,9

rebooted after each try.  Still no sound.
If it matters, spdif works without having to have a asound.conf or anything.
Strange that it works without making a asound.conf but nothing else does.
There is no asoundrc in my hidden home directory either.
This is just bizarre to me.

---

### Post by steeldriver on 2012-07-15
I don't really understand alsa but what worked for me was a (simpler) default 

```
pcm.!default { 
      type hw 
      card 1 
      device 3 
}
```

(obviously change your card / device as appropriate)

---

### Post by nickrout on 2012-07-15
> **iitywygms said:**
> Tried 3,7,8,9

rebooted after each try.  Still no sound.
If it matters, spdif works without having to have a asound.conf or anything.
Strange that it works without making a asound.conf but nothing else does.
There is no asoundrc in my hidden home directory either.
This is just bizarre to me.

To me too. Make sure there is not some mixer issue with something being muted or volume right down. alsamixer in a terminal is easy to use.

Try steeldrivers file, and try device numbers 1,2,3,4,5 etc, in other words try all the digits, not just the ones presented by aplay -l

---

### Post by anonymousdog on 2012-07-15
Try
```
pcm.!default hdmi:NVidia
```

---

### Post by iitywygms on 2012-07-15
Tried this.
pcm.!default hdmi:NVidia

no go

tried this.

pcm.!default { 
      type hw 
      card 1 
      device 3 
}

Changing the device to all numbers from 1 - 9.

no go.

Confusion for sure.

Appreciate all the help guys.

---

### Post by iitywygms on 2012-07-17
Is there a alsa forum or somewhere I can get some specific help?
You all have been very helpful.

---

### Post by nickrout on 2012-07-17
> **iitywygms said:**
> Is there a alsa forum or somewhere I can get some specific help?
You all have been very helpful.

I suggest the mythtv-users mailing list. Jean-Yves Avenard who seems to  be writing all the myth audio code lately, hangs out there and if you are lucky will answer :)

---

### Post by tazz4vr on 2012-07-17
How about - [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

Although it shows last modified in 08, however there are updates shown from Jan 2012.... who knows, maybe there is something in there that may help you or anyone else having the same issue.

---

### Post by BicyclerBoy on 2012-07-17
MythTV does not do anything that special except it works.
And it works without configuring the desktop system wide audio.
It closes pulse audio server if you are not using a pulse device..

Config desktop env pulse audio:
Install & run pavucontrol, click on configuration tab & select one of the 4 HDMI devices listed..

Different versions of alsa (user space) & pulse audio results in varying reports of success.
The recent pulse audio updates in 12.04 supports pass-thru' modes & HDA audio modes.

Check hw device with PCM:
speaker-test -l 2 -c 6 -r 48000 -D hw:1,3

I'm not sure how MythTV enumerates the HDMI devices so also try:
-D hw:1,7
-D hw:1,8
-D hw:1,9


Check the ELD audio capabilities:
dmesg | grep HDMI
cat /proc/asound/card1/eld#0.0
(assumes hw:1,3 works)
eld#1.0 == hw:1,7 etc..

---

### Post by iitywygms on 2012-07-18
> **BicyclerBoy said:**
> MythTV does not do anything that special except it works.
And it works without configuring the desktop system wide audio.
It closes pulse audio server if you are not using a pulse device..

Config desktop env pulse audio:
Install & run pavucontrol, click on configuration tab & select one of the 4 HDMI devices listed..

Different versions of alsa (user space) & pulse audio results in varying reports of success.
The recent pulse audio updates in 12.04 supports pass-thru' modes & HDA audio modes.

Check hw device with PCM:
speaker-test -l 2 -c 6 -r 48000 -D hw:1,3

I'm not sure how MythTV enumerates the HDMI devices so also try:
-D hw:1,7
-D hw:1,8
-D hw:1,9


Check the ELD audio capabilities:
dmesg | grep HDMI
cat /proc/asound/card1/eld#0.0
(assumes hw:1,3 works)
eld#1.0 == hw:1,7 etc..

If I run this speaker-test as you suggest

I always get an error.  No matter if I run 1,3 or 7,8,9

speaker-test 1.0.25

Playback device is hw:1,7
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 22 to 5461
Period size range from 11 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

Also, I do not have pulse audio installed. Never have.  And hdmi works everywhere on my 3 other computers using the same version of mythbuntu.
I did install the pulse audio volume control you suggested but when I start it, it errors with a message that it cannot find pulse audio.  As expected.

I also ran the other stuff you suggested.  Not sure what I am suppose to see but here are the results.

Completely appreciate the help.


dmesg | grep HDMI
[    3.515394] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
[    3.539378] HDMI status: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=0
[    3.563367] HDMI status: Codec=2 Pin=5 Presence_Detect=0 ELD_Valid=0
[    3.587378] HDMI status: Codec=3 Pin=5 Presence_Detect=0 ELD_Valid=0
[    3.587475] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    3.587556] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    3.587624] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    3.587689] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[    6.452361] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[    6.458736] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=0
[    6.470873] HDMI hot plug event: Codec=1 Pin=5 Presence_Detect=0 ELD_Valid=1
[    6.478731] HDMI status: Codec=1 Pin=5 Presence_Detect=1 ELD_Valid=1
[    7.246573] HDMI: detected monitor H/K AVR
[    7.246575]       at connection type HDMI
[    7.246578] HDMI: available speakers: FL/FR LFE FC RL/RR RLC/RRC
[    7.246583] HDMI: supports coding type LPCM: channels = 8, rates = 32000 44100 48000 96000 176400 192000 384000, bits = 16 20 24
[    7.246587] HDMI: supports coding type MLP (Dolby TrueHD): channels = 2, rates = 44100 48000 96000 176400 192000 384000
[    7.246591] HDMI: supports coding type MLP (Dolby TrueHD): channels = 6, rates = 44100 48000 96000 176400 192000 384000
[    7.246594] HDMI: supports coding type MLP (Dolby TrueHD): channels = 8, rates = 44100 48000 96000 176400 192000 384000
[    7.246598] HDMI: supports coding type DTS-HD: channels = 8, rates = 44100 48000 96000 176400 192000 384000
[    7.246601] HDMI: supports coding type AC-3: channels = 6, rates = 32000 44100 48000, max bitrate = 640000
[    7.246605] HDMI: supports coding type DTS: channels = 6, rates = 32000 44100 48000 96000 176400, max bitrate = 1536000
[    7.246608] HDMI: supports coding type E-AC-3/DD+ (Dolby Digital Plus): channels = 8, rates = 44100 48000



cat /proc/asound/card1/eld#1.0
monitor_present		1
eld_valid		1
monitor_name		H/K AVR
     
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0x6720
product_id		0x6040
port_id			0x20000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count		8
sad0_coding_type	[0x1] LPCM
sad0_channels		8
sad0_rates		[0x1ee0] 32000 44100 48000 96000 176400 192000 384000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0xc] MLP (Dolby TrueHD)
sad1_channels		2
sad1_rates		[0x1ec0] 44100 48000 96000 176400 192000 384000
sad2_coding_type	[0xc] MLP (Dolby TrueHD)
sad2_channels		6
sad2_rates		[0x1ec0] 44100 48000 96000 176400 192000 384000
sad3_coding_type	[0xc] MLP (Dolby TrueHD)
sad3_channels		8
sad3_rates		[0x1ec0] 44100 48000 96000 176400 192000 384000
sad4_coding_type	[0xb] DTS-HD
sad4_channels		8
sad4_rates		[0x1ec0] 44100 48000 96000 176400 192000 384000
sad5_coding_type	[0x2] AC-3
sad5_channels		6
sad5_rates		[0xe0] 32000 44100 48000
sad5_max_bitrate	640000
sad6_coding_type	[0x7] DTS
sad6_channels		6
sad6_rates		[0x6e0] 32000 44100 48000 96000 176400
sad6_max_bitrate	1536000
sad7_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad7_channels		8
sad7_rates		[0xc0] 44100 48000

---

### Post by iitywygms on 2012-07-18
too add to the above.

If I run speaker-test like this.

speaker-test -D plug:surround51 -c 6 -l 1 -t wav

it works but no sound comes through.

speaker-test 1.0.25

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 22 to 5461
Period size range from 11 to 2730
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left
 4 - Center
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
 5 - LFE
Time per period = 8.531848

---

### Post by BicyclerBoy on 2012-07-18
Your surround51 device is probably card0..see if it shows up in:
aplay -L

The hot-plug event & eld file both show codec #1 (hw:1,7) is the connected device. (assuming there is no modprobe snd-hda-intel probe_mask option)

Try:
speaker-test -l 2 -c 8 -r 48000 -D hw:1,7
speaker-test -l 2 -c 8 -r 48000 -D plughw:1,7
The plughw device does auto translation of rates/channels etc.
Does running as sudo work ?
Your "user" is a member of the audio group?

FWIHR There are some bugs in alsa 1.0.25, including the archive from alsa.org. Apparently alsa git is good.

This should have worked but the error (xrun_recovery etc...) may be a vital clue.
# /etc/asound.conf
pcm.!default {
type hw
card 1
device 7
}


Pavucontrol is useless without pulse audio..did not see you had removed it. I never had problems with pulse interfering with alsa.

To get default apps to use alsayYou may have to run:
gstreamer-properties & set ALSA as default input/output

Programs like mplayer, vlc, clementine etc can be directed to any specific audio device.

---

### Post by iitywygms on 2012-07-18
I will try as you suggest when I can later today.
Running speaker-test as sudo did not help.
My user is a memeber of the audio group.

FYI  I posted the output of alsainfo script here.

[http://pastebin.com/r7V1PMFh](http://pastebin.com/r7V1PMFh)

Really appreciate your time and help.

---

### Post by tjg on 2012-07-18
I've recently solved several sound issues by using pavucontrol (apt-get install pavucontrol, then pavucontrol to run) which gives you a much more granular sound settings gui than the one now packaged with 12.04.
 
give it a shot.
 
Thanks,
 
Tjg
 
EDIT:: sorry, late post and missed the pulse removal as well....

---

### Post by iitywygms on 2012-07-18
BicyclerBoy.

I ran the commands you suggested.

speaker-test -l 2 -c 8 -r 48000 -D hw:1,7
speaker-test -l 2 -c 8 -r 48000 -D plughw:1,7

Both ran but with no sound.

I tried to run this, gstreamer-properties, but it was not installed.
I do not have gnome installed.  I am running xfce.

I don't think this is an alsa bug as this did not work when I was using a previous version of alsa either.

I am completly perplexed with this one.
Other suggestions?

---

### Post by BicyclerBoy on 2012-07-19
Was there any errors (like last time) ?

The previous errors:
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

Could be related to buffer size over-run/under-run &/or permissions problems.

Don't know what Xfce uses for system wide sound maybe nothing..Each app for themselves.

So MythTV does do some magic after all!

---

### Post by iitywygms on 2012-07-19
> **BicyclerBoy said:**
> Was there any errors (like last time) ?

The previous errors:
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted

Could be related to buffer size over-run/under-run &/or permissions problems.

Don't know what Xfce uses for system wide sound maybe nothing..Each app for themselves.

So MythTV does do some magic after all!

No errors at all.  Just no sound.

I am getting a ton of suggestions from the mailing list so I will report back here if and when I find a solution.

Thanks to all for the help.

---

### Post by anonymousdog on 2012-07-19
Shot in the dark (since we're now looking for zebras instead of horses): Since the FE is using the card in a way that will give it exclusive control of audio, is there any chance at all that your testing has been conducted while MythTV FE was running (and the tests, therefore, produced no sound)?

---

### Post by iitywygms on 2012-07-19
I have always closed mythtv before performing test.  Even gone as far as re-booting straight to the desktop.
Thanks for the suggestion.

---

### Post by iitywygms on 2012-08-21
Removed 12.04 and installed 11.04.  All is normal now.

---

### Post by BicyclerBoy on 2012-08-22
Saw your post on mythtv mailing list...
Sounds like an alsa/kernel regression (no pun intended).

Wonder why it only effects you ?
Combination of mobo & video card?

---

### Post by iitywygms on 2012-08-22
> **BicyclerBoy said:**
> Saw your post on mythtv mailing list...
Sounds like an alsa/kernel regression (no pun intended).

Wonder why it only effects you ?
Combination of mobo & video card?

That's what I am thinking.
Or the upgrade from 11.04 to 12.04 hosed something up.
This clean install is good.  I had a bunch of old stuff I no longer wanted installed anyway.

If I had to guess, I would say some program or something was holding onto that portion of alsa that flips on the sound for flash and such.  Why it would work for some things and not for others just baffled me.

Anyway, thanks for the help.

---

### Post by iitywygms on 2012-09-29
I just wanted to follow up with something I found.
I updated my 11.04 install last week, and bam.  Lost sound over hdmi again, except for mythtv.  Not an upgrade to 12.04, just an update to 11.04

This time, I confogured .asoundrc in my home directory and made changes there. Doing so fixed the sound issues.
As a test, I tried the same settings in the etc/asuond.conf.  Doing so DOES NOTHING in my system.
So if you have issues with sound, try both .asoundrc and asound.conf
I probably would have saved myself days of grief if I would have known this before.

---

### Post by BicyclerBoy on 2012-09-29
Bizarre..

This should have worked before..regardless of the .asoundrc file.
speaker-test -l 2 -c 6 -r 48000 -D hw:1,7
speaker-test -l 2 -c 2 -r 48000 -D hw:1,7

Mythbuntu does use Xfce as its default desktop ?

---

### Post by iitywygms on 2012-10-01
> **BicyclerBoy said:**
> Bizarre..

This should have worked before..regardless of the .asoundrc file.
speaker-test -l 2 -c 6 -r 48000 -D hw:1,7
speaker-test -l 2 -c 2 -r 48000 -D hw:1,7

Mythbuntu does use Xfce as its default desktop ?

Yes, it is xfce.  
I remember doing the above test, and never got any sound.
I can try again just to see what happens.

---

### Post by dheianevans on 2012-10-26
just found this thread. posted today that i had lost hdmi application sound (myth is fine) after moving to 12.04

I'm able to get headphone sound from firefox(youtube) but nothing over the HDMI.

I've pasted this in both asound.conf and ~/.asoundrc:

pcm.!default {
 type plug
 slave.pcm {
 type hw
 card 1
 device 9
 }
}

I'm hoping it's just some glaring error in this file that I'm missing.

---

### Post by BicyclerBoy on 2012-10-28
The browsers just use the first card listed (I think)..
You could try setting the default sound card to the nVidia device..

in ~/.asoundrc
defaults.pcm.card 1

AFAIK
MythTV enumerates the alsa subdevices of nvidia card [3,7,8,9] as (0-3)

---

### Post by dheianevans on 2012-10-28
Argh...followed the first step here and it's basically turning my xfce mythbuntu pvr into a gnome desktop!

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by dheianevans on 2012-10-28
As  per one of the tutorials suggestions, I've posted a question (with full debug system info) over at:

[https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/212597](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/212597)

---

### Post by dheianevans on 2012-10-28
> **BicyclerBoy said:**
> 
in ~/.asoundrc
defaults.pcm.card 1


Sadly that didn't work. I love these issues that just crop up after upgrading a system that's been working for 18 months. :(

---

### Post by dheianevans on 2012-10-29
An update: fiddling around with /etc/pulse/default.pa and pavucontrol I was able to get sound in a browser.

So now I have:

1) sound in Myth Recordings/Video (that's never changed)
2) sound in a web browser (just got it)
3) NO SOUND in Myth's Internet Video's, mythnetvision.

---

### Post by topcat5 on 2012-10-30
What worked for me for HDMI sound via GT430 card were the instructions in this document.  

[https://help.ubuntu.com/community/SoundTroubleshootingGuide]("https://help.ubuntu.com/community/SoundTroubleshootingGuide")

Scroll down to the HDMI sound section.  The magic fix for me was to add the following configuration to /etc/modprobe.d
```
options snd-hda-intel probe_mask=0x8
```

(create a anyfilename.conf file and place in that directory)   Your hardware might require a different value especially if your video card is the 2nd card in the system.  I had disabled the Intel graphics in bios.

After you reboot, you may need to reconfigure .asoundrc and MythTV sound.

---

### Post by dheianevans on 2012-10-30
topcat5,

Thanks. The only problem is that I already looked at that guide.

There's a major stumbling block though.

/proc/asound/NVidia is empty

I have files in NVidia_1, but running

grep "eld_valid *1" /proc/asound/NVidia_1/eld* gives me nothing,
so I can't go on to the next step.

---

### Post by dheianevans on 2012-10-31
Okay...fixed it. Used info in this page: [http://omappedia.org/wiki/Ubuntu_PA#PA_through_HDMI](http://omappedia.org/wiki/Ubuntu_PA#PA_through_HDMI)

#load-module module-udev-detect
load-module module-alsa-sink device=plughw:1,9 sink_name=output
### Make some devices default
set-default-sink output

Suddenly everything's working. as for the choppy podcast, I think it may be an issue with the podcast as I added another one and it seems fine

---

