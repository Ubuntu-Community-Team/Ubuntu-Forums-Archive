---
title: "Soundblaster Audigy 2 AC3 Passthrough - Howto"
date: 2006-07-17
forum: Multimedia &amp; Video
---

### Post by dave_euser on 2006-07-17
After a few days of fighting, I finally managed to get pure 5.1 AC3 sent from my digital coax output on a Audigy 2. Out of the box, ubuntu had PCM 2 channel output from just about anything (mp3 players, non-AC3 video, tv tuner), but no AC3 passthrough.

Ended up by creating my ~/.asoundrc as per this post:
[http://www.mythtv.org/pipermail/mythtv-users/2005-May/088049.html](http://www.mythtv.org/pipermail/mythtv-users/2005-May/088049.html)

Hopefully this saves someone else the frustration. ;-)

Here are the contents of what should be your new .asoundrc:

```

# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
### analog as your default
### -jarod
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
#  slave.pcm "dmix-digital"
}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 0
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-digital {
 type hw
 card 0
}

```

---

### Post by LordRaiden on 2006-07-17
Looks very useful. I'll link to this in my guide so that people with SB Audigy 2 who want 5.1 (there are many out there for sure!) can give it a try.

---

### Post by eXecu7or on 2006-07-25
Does this apply or can it be modified for the ALC882D codec from Realtek? Realtek advertises it has Dolby Digital Live, but is it available in linux? (I suspect DDL is only a software layer).

Another thing: I'm using a tvtuner connected to the mobo's line in connector on the pcb. Can Ubuntu be set-up so that the line in analog input gets outputted to the coax digital out?

---

### Post by gometro33 on 2006-10-24
I'm sorta new to Ubuntu and Linux and have been having this problem for a little while now.

I'm not entirely sure how this works but I am eager to try anything at this point.  The problem is that I have no idea where to put the .asoundrc file that you (dave_euser) posted.  Where does this go?  Thanks.

---

### Post by LordRaiden on 2006-10-25
gometro33 in your home directory i.e.

if your username in Ubuntu is moocow it would go under the .asoundrc file would be under /home/moocow

---

### Post by GameManK on 2006-12-10
Thank you! had to to this on edgy as well.

BTW, you have to set your movie player to 5.1 not AC3 passthrough when you set it up this way.

---

### Post by herbster on 2007-03-18
I have a Soundblaster Audigy SE (recognized as Audigy LS in Ubuntu) and MP3s in Amarok and DVDs play really well, but .avi DVD rips (in XViD with AC3) get some wierd crackling happening at moments and a few hi-pitched "squeals", like a millisecond long popping here and there. I am using Logitech X-540 5.1 speaker system. I can tell it must be AC3 that isn't at its best.

Should I do what dave has posted, would it apply for me ??

---

### Post by GameManK on 2007-03-18
> **herbster said:**
> I have a Soundblaster Audigy SE (recognized as Audigy LS in Ubuntu) and MP3s in Amarok and DVDs play really well, but .avi DVD rips (in XViD with AC3) get some wierd crackling happening at moments and a few hi-pitched "squeals", like a millisecond long popping here and there. I am using Logitech X-540 5.1 speaker system. I can tell it must be AC3 that isn't at its best.

Should I do what dave has posted, would it apply for me ??

No, the AC3 pass through is if you want to play through another device connected through S/PDIF.  Your speakers are connected directly to your card (same as my speakers :)) so this doesn't apply to you AFAIU.

---

### Post by manro on 2007-04-29
Hi!

I already try all to make my Audigy2 Value to send 5.1 through s/pdif but nothing seems to work! ... Here's the output of the aplay -l command:

```
manro@ubuntu-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 2 Value [SB0400]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
manro@ubuntu-desktop:~$
```

I'll really appreciate any help!

Regards,
MaNRo

---

### Post by Greyfox_75 on 2007-12-21
All you should need to do to get AC3 pass through is change your Xine settings for speaker arrangement to pass through.  (Im a Kubuntu user and Kaffeine has a nice GUI for changing Xine settings)

Works out of the box in under 30 seconds from startup as long as all of your audio/video apps use Xine.

P.S.You may have to make sure that the Optical Raw switch is off if your receiver doesn't support raw input.

---

