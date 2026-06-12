---
title: "ALC1200 sound problems"
date: 2009-10-17
forum: Mythbuntu
---

### Post by jrbless on 2009-10-17
I purchased an ASUS M3A78-EM motherboard for use in a MythTV frontend/backend system. It is an install of the Mythbuntu 9.04 with all upgrades applied. I was able to get the video and networking to work fine, but am having a problem with the audio - it only comes through in stereo and not surround.

The integrated audio chipset is a "Realtek ALC1200" and I am needing to use the spdif output (to connect to a home theater system). I have installed the newest ALSA drivers that are available (alsa-driver-1.0.21 and alsa-firmware-1.0.20).

uname -a gives:
Linux MythTV 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686 GNU/Linux


aplay -l gives:
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L gives:
default:CARD=SB
    HDA ATI SB, ALC1200 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC1200 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


I've gone into alsamixer and unmuted everything, but I'm still only getting stereo sound. I'm definitely a novice when it comes to this stuff, but I had seen the above commands run and the output seemed helpful to try debugging the problem.

Ideally, I would like to use AC3 and DTS passthrough for sound output.

If anyone can give me a pointer in how to proceed, I'd greatly appreciate it!
James

---

### Post by jyavenard on 2009-10-18
Set your audio device in mythtv settings as:
ALSA:spdif

for both default and passthrough.

Set number of speakers to Stereo if using 0.21 or 0.22, set to 5.1 is using trunk >= 22432
Check AC3 and DTS.

---

### Post by jrbless on 2009-10-18
Thanks for your reply!  When I do that, I get no sound at all.  When I leave the audio device as "default" for normal and passthrough, I get sound but it's in stereo.  When I check the AC3 and DTS passthrough, I get a "chittering"/static sound, but only in stereo.  The other speakers don't give any sound and the receiver doesn't show a signal to them.  Max audio channels is set to 5.1.

Summary of settings and results (all settings have max audio channels set to 5.1):

Config 1:
audio device: ALSA:Default
passthrough: default
AC3/DTS passthrough: not checked
result: sound works for mp3s and videos, but is only in stereo

Config 2:
audio device: ALSA:spdif
passthrough: default
AC3/DTS passthrough: not checked
result: no sound at all for anything

Config 3:
 audio device: ALSA:spdif
 passthrough: ALSA:iec958:{ AES0 0x02 }
 AC3/DTS passthrough: not checked
 result: no sound at all for anything

Config 4:
  audio device: ALSA:Default
  passthrough: default
  AC3/DTS passthrough: checked
  result: mp3s play fine (stereo only, as expected since they are just stereo).  videos have a chittering/static in stereo

Config 5:
   audio device: ALSA:Default
   passthrough: ALSA:iec958:{ AES0 0x02 }
   AC3/DTS passthrough: checked
   result: mp3s play fine (stereo only, as expected since they are just stereo).  videos have no sound at all


Any other ideas to try?
James

---

### Post by jyavenard on 2009-10-18
I avoid any board with an ALC1200 for that exact reason... It's a controller only made for Asus, and it's closed source... support has always been a pain.

Anyhow.

Edit: Dumb question, did you make sure to uncheck all the IEC958 in alsamixer ??? By default they are muted


Use ALSA:default as this works for you, uncheck DTS/AC3. You'll get sound in stereo for all.

I can only assume you have set up some .asoundrc ; which in these days and age isn't necessary on most distribution. You should let the system do its job.

Uninstall any pulseaudio related programs, and uninstall the pulseaudio daemon

You could also try using:
```
ALSA:plughw:0,1
```


And see how it goes, check AC3/DTS for those. Note, you only check those if your TV or amplifier can handle AC3 or DTS

---

### Post by jrbless on 2009-10-19
I did unmute both of the IEC958 items in alsamixer (the entries were "IEC958" and "IEC958 D").  I also unmuted the other surround-sound related entries (surround, center, side, LFE).

I don't have a .asoundrc or /etc/asound.conf

How do I figure out which pulseaudio (or related) applications are installed and how do I remove them?

I don't know what to do with the "ALSA:plughw:0,1" code snippet you referrenced.  Can you please elaborate on where it needs to go?

My home theater system can handle both the AC3 and DTS just fine.  It's a Harman/Kardon AVR 146.  My previous MythTV system was from the MonolithMC company.  They sold prebuilt MythTVs based on the Asus Pundit -R and I was able to have it work fine in surround-sound mode before the motherboard recently died (the reason for me purchasing this new motherboard and some other related hardware for this MythTV build).

A possibly bigger problem is that running "speaker-test -c6 --rate 48000 -twav" only gives me stereo (front left and front right).  This would indicate to me that Ubuntu is not configured correctly for the sound card (and MythTV running on top of it will only be able to get up to whatever the o/s is able to).

Thanks!
James

---

### Post by novellahub on 2009-10-19
Have you tried upgrading the BIOS?  I had to do that in my ECS GF8200 setup along with the ALSA upgrade in order to get sound over HDMI working on my setup. 

Also this page helped me out quite a bit:

[http://www.mythtv.org/wiki/AllensDigitalAudioHowto](http://www.mythtv.org/wiki/AllensDigitalAudioHowto)

---

### Post by jyavenard on 2009-10-19
> **jrbless said:**
> 
I don't know what to do with the "ALSA:plughw:0,1" code snippet you referrenced.  Can you please elaborate on where it needs to go?


wherever you entered ALSA:spdif before

in mythtv general configuration screen

---

### Post by jrbless on 2009-10-20
:guitar:Thanks to both of you!  It works now.

The steps to make surround sound work on the ASUS M3A78-EM motherboard (possibly more generically the Realtek ALC1200 audio chipset, but untested):

1. Install Mythbuntu 9.04 and run the update manager to install all updates
2. Open a terminal on the mythtv box
3. Run "alsamixer" and unmute the following options: "surround", "center", "LFE", "side", "iec958", "iec958 d".  After unmuting them, set their volume levels.  I personally set them to 55, but you could probably max them out if desired.  The rightmost setting in alsamixer is the number of channels.  The options on my system were "6ch" and "8ch".  6ch is for a 5.1 surround system and 8ch is for a 7.1 surround system.  Select the one appropriate for your home theater.
4. Close the terminal window
5. On MythFrontend, some settings need changed.  Go through "utilities/setup"->"setup"->"general"->3rd screen.  Set the "audio device" at the top to "ALSA:spdif".  Leave the number of channels set to "2" (even though we're wanting surround sound).  Check both the "AC3" and "DTS" passthrough checkboxes.

When going to play a movie, you'll have surround sound now.  Music and recordings also work, but only in stereo (they may play in surround sound if that is how the sound was recorded, for example from a HD channel.  This specifically is untested because I don't have any recordings or music that is in surround sound).

James

---

