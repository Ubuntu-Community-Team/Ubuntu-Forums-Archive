---
title: "Looking for possibilities to switch profile when disconnecting headphones"
date: 2017-04-21
forum: Multimedia Software
---

### Post by takayoshi on 2017-04-21
Hi,

I spent the last days researching and testing... without success.
What I want to achieve:
I want to build a HTPC using ubuntu in a minimal configuration and kodi. When connecting a TV via HDMI sound should be sent through HDMI. As soon as headphones are connected, output shall be rerouted to analog connectors (headphones/headset). When disconnecting the headphones, sound should be switched back to HDMI.

What I got down so far:
I installed a minimal system with only xorg, openbox, pulseaudio, alsa and kodi. Autostarting kodi without a desktop manager works fine, pulseaudio fires up as well (snd_hda_intel). I have to use pavucontrol or pacmd to choose the right profile (HDMI). Connecting headphones to the analog jacks works as expected - the profile switches and sound is played only using the analog connectors. Disonnecting headphones has no effect at all, the profile remains the same, doesn't switch back to HDMI. However, I can choose the profile using pacmd, wich works fine. Unfortunately it is not possible to reactivate the analog profile again after doing so.

The question:
Is there any information on how to achieve automatic switching when disconnecting headphones?

Commands I used:
```

# switch to hdmi output profile
[FONT=monospace][COLOR=#000000]pacmd set-card-profile 0 output:hdmi-stereo-extra1+input:analog-stereo

```
[/COLOR][/FONT]```

[FONT=monospace][COLOR=#000000]# switch to analog output profile
[/COLOR][/FONT][FONT=monospace][COLOR=#000000]pacmd set-card-profile 0 output:analog-stereo+input:analog-stereo[/COLOR]
[/FONT]
```

There is an indicator showing if there is something connected to the audio jacks:
```

[FONT=monospace][COLOR=#000000]grep -A 20 "Speaker Playback Switch" /proc/asound/card0/codec#0 | grep Pin-ctls | cut -d" " -f5[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]  Control: name="[/COLOR][COLOR=#FF5454]**Speaker Playback Switch**[/COLOR][COLOR=#000000]", index=0, device=0 [/COLOR]
   ControlAmp: chs=3, dir=Out, idx=0, ofs=0 
 Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 
 Amp-Out vals:  [0x00 0x00] 
 Pincap 0x00010014: OUT EAPD Detect 
 EAPD 0x2: EAPD 
 Pin Default 0x90170110: [Fixed] Speaker at Int N/A 
   Conn = Analog, Color = Unknown 
   DefAssociation = 0x1, Sequence = 0x0 
   Misc = NO_PRESENCE 
 Pin-ctls: 0x00: 
 Unsolicited: tag=00, enabled=0 
 Power states:  D0 D1 D2 D3 EPSS 
 Power: setting=D3, actual=D3 
 Connection: 1 
    0x0c 
Node 0x15 [Vendor Defined Widget] wcaps 0xf00000: Mono 
Node 0x16 [Vendor Defined Widget] wcaps 0xf00000: Mono 
Node 0x17 [Pin Complex] wcaps 0x40050c: Mono Amp-Out 
 Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1 
 Amp-Out vals:  [0x80]
[/FONT]
```
Pin-ctls changes when unplugging the headphones to
```

[FONT=monospace] Pin-ctls: 0x00: OUT[/FONT]

```

Showing the active profile:[FONT=monospace]
[/FONT]```

[FONT=monospace][COLOR=#000000]pacmd list-cards
[/COLOR]...
active profile: [/FONT][COLOR=#000000][FONT=monospace]output:analog-stereo+input:analog-stereo
[/FONT][/COLOR][FONT=monospace]...
[/FONT]
```

Any advice what I might have missed?

Thanks in advance!

Cheers

Yoshi

---

### Post by tuese on 2017-04-21
related [https://github.com/yktoo/indicator-sound-switcher](https://github.com/yktoo/indicator-sound-switcher)

---

