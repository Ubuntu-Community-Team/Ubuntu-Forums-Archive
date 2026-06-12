---
title: "Some problems configuring Mytbuntu"
date: 2012-06-23
forum: Mythbuntu
---

### Post by MPsico on 2012-06-23
Hi all.

I'm new to mythbuntu, I was using Openelec for a while, but I wanted a change.

So, I managed to install mythbuntu and get the LiveTV working, I can see the TV.

Some problems:

- No sound at all, I have an ATI HD4200 card, and the box is connected through HDMI directly to the TV set. I installed the catalyst drivers, but still have no sound at all. I have tried some workaround I've found in the forums with no luck. Any help?

- After I've installed the Catalyst drivers I get a lot of tearing in the live tv, I was checking around but i don't know where is any setting that could solve this issue.

- Changing between channels takes a long, and it appears a windows saying something that I should already get a lock signal or something like that, is very annoying, is there any way to disable that warning and making the change between channels faster? at least in openelec is a bit faster.

- I have a remote, an Imon VERIS, I have configured that in the myth setup, but I can't get the whole keys to work, what I have to do? I have read some post in the forum about this without any  conclusion.

Thanks in advance for your attention!!!

---

### Post by Lester_Burnham on 2012-06-24
Hi,

Did the AT HD4200 work OK. In openlec? Nvidia 9300 on is the better option.
For the remote. Open a terminal and type irw, then hit enter and press keys on remote. You will see the key name come up. These are the button names that should be used In your ~/.lirc/mythtv for mythtv to operate. 

Lester

---

### Post by MPsico on 2012-06-24
> **Lester_Burnham said:**
> Hi,

Did the AT HD4200 work OK. In openlec? Nvidia 9300 on is the better option.
For the remote. Open a terminal and type irw, then hit enter and press keys on remote. You will see the key name come up. These are the button names that should be used In your ~/.lirc/mythtv for mythtv to operate. 

Lester

Hi Lester, thanks for helping me out.

And yes, the HD4200 work over openelec, passing sound through HDMI to the TV. The only thing I have to do there (over openelec) is to make an asound.conf file with this information:

```
pcm.!default {
   type plug
    slave {
      pcm "hw:x,y"
      rate 48000
   }
}
```

where x and y goes in function of the aplay -l out, in my case 1,3.

I think I have to do the same here, but I don't know where is the asound.conf or similar in mythbuntu.

About the irw command, I will give it a try...

The tearing problem seems to be solved checking an option on the catalyst control center.

Still need some help with the changing channels banner that appears and is very annoying...

---

### Post by steeldriver on 2012-06-24
I had to create a similar default pcm device in asound.conf to get HDMI audio from flashplugin - you probably won't have one by default - it goes at /etc/asound.conf

or iirc you can do it per-user in ~/.asoundrc

---

### Post by MPsico on 2012-06-24
> **Lester_Burnham said:**
> Hi,

Did the AT HD4200 work OK. In openlec? Nvidia 9300 on is the better option.
For the remote. Open a terminal and type irw, then hit enter and press keys on remote. You will see the key name come up. These are the button names that should be used In your ~/.lirc/mythtv for mythtv to operate. 

Lester

Tried the irw thing.

Didn't work, I type irw, hit enter, but nothing happens when I press the remote keys. Even when I press the key that actually works.

Any other idea?

---

### Post by MPsico on 2012-06-24
> **steeldriver said:**
> I had to create a similar default pcm device in asound.conf to get HDMI audio from flashplugin - you probably won't have one by default - it goes at /etc/asound.conf

or iirc you can do it per-user in ~/.asoundrc

I have created the asound.conf on /etc/

nothing happens, still no sound at all, neither mythtv or outside mythtv.

Any idea?

---

### Post by nickrout on 2012-06-24
> **MPsico said:**
> I have created the asound.conf on /etc/

nothing happens, still no sound at all, neither mythtv or outside mythtv.

Any idea?

In mythtv did you scan for audio devices and choose one that worked?

---

### Post by MPsico on 2012-06-24
> **nickrout said:**
> In mythtv did you scan for audio devices and choose one that worked?

I have scanned, and tried all the devices, noone works... I don't have sound outside mythtv, so I think the problem is there... For example, I don't have sound playing a video using vlc...

Using alsamixer command I get this:

[IMG]http://i45.tinypic.com/ibdlbp.png[/IMG]

F6 to select card:

[IMG]http://i49.tinypic.com/i69g9j.png[/IMG]

I select the HDMI, and I got this:

[IMG]http://i47.tinypic.com/5yg2aa.png[/IMG]

If i exit alsamixer all come back to the first stage.

Any idea to solve this?

---

### Post by nickrout on 2012-06-24
Please we don't need the output of your terminal screen. Try giving us the ooutputs of ```
aplay -l 
```and ```
aplay -L
```

What options did mythtv give you when you scanned for audio devices?

---

### Post by MPsico on 2012-06-24
aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

aplay -L:

```
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default
sysdefault:CARD=SB
    HDA ATI SB, ALC889A Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC889A Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC889A Digital
    Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
    HDA ATI HDMI, HDMI 0
    HDMI Audio Output
dmix:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct sample snooping device
hw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
    HDA ATI HDMI, HDMI 0
    Hardware device with all software conversions
```

Mythtv gives the same options that aplay -L output...

---

### Post by MPsico on 2012-06-24
I have already solved, the spdif out was muted, in alsamixer hit M and now I have sound.

Hope it get saved, because there is no option for that in alsamixer.

Ok, sound and tearing solved.

Still can't make the remote working and the banner when I change between channels is very annoying it tell me about a lock signal or something like that, is there any way to remove this? And finally if there is a way to speed up changing between channels would be great...

Do I have to make a new post with this or just we can continue with those subject on this one?

---

### Post by MPsico on 2012-06-24
Now the remote thing:

I have a lot of this in dmesg:

```
[  264.439817] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000100
[  264.503814] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  264.567822] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  264.631813] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  264.783817] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  800.420219] imon 5-3:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[  800.783918] imon 5-3:1.0: Looks like you're trying to use an IR protocol this device does not support
[  800.783929] imon 5-3:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[  805.338615] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  805.378614] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10001f2
[  805.450632] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  805.490611] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10001f2
[  805.522622] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fef2
[  805.562608] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100faf2
[  805.602625] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fbf4
[  805.634627] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ffff
[  805.690632] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fe04
[  805.722631] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f205
[  805.802638] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f2fd
[  805.834638] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f2f6
[  805.874642] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f2f3
[  805.914642] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f2f3
[  805.946643] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f3f2
[  806.026649] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100faf2
[  806.058651] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100faf2
[  806.098652] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fbf4
[  806.290668] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  817.299297] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10009fb
[  817.339300] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10001fe
[  817.419297] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  817.555312] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  817.603315] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff0e
[  817.683287] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[  817.715309] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[  817.755311] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[  817.795325] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff04
[  817.979338] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  818.035341] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100040e
[  818.115336] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100010e
[  818.147347] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100010e
[  818.379361] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  818.491367] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100010e
[  818.531369] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100030e
[  840.940658] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  840.988677] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000002
[  841.028678] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000004
[  841.060670] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff09
[  841.100665] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000109
[  841.140682] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  841.548714] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  841.684701] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000009
[  841.724704] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff09
[  841.756719] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff07
[  841.836723] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  842.188747] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  842.284738] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  842.964777] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  843.236806] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  843.324802] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  843.372801] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000002
[  843.420813] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff02
[  843.476814] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  845.316914] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  847.565058] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  847.613061] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  847.661057] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  847.717066] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff04
[  847.749069] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff04
[  847.789070] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  858.165684] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  858.221667] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff02
[  858.325692] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  858.381677] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  858.453698] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  859.389763] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  859.461743] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  859.525763] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  859.589767] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  864.030029] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  864.118031] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000104
[  864.158031] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000101
[  864.286039] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  864.342042] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[  864.414055] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100010e
[  864.454051] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fc0e
[  864.718064] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  871.406467] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  871.462465] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  871.606471] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  871.654475] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f2f3
[  871.694480] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f3f2
[  871.766487] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f5f2
[  871.806486] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f4f2
[  871.838488] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f6f2
[  871.878490] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fdf2
[  871.918492] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fff2
[  871.950493] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  871.990497] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fff2
[  872.030499] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  872.070501] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fff2
[  872.102503] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  872.142505] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000f2
[  872.502530] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  872.598531] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  972.128263] imon 5-3:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[  972.466567] imon 5-3:1.0: Looks like you're trying to use an IR protocol this device does not support
[  972.466577] imon 5-3:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
[  974.260692] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[  974.308691] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff02
[  974.364695] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  974.940731] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff00
[  975.004736] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f707
[  975.036736] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f207
[  975.116719] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f209
[  975.156724] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f208
[  975.188736] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f209
[  975.228748] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20a
[  975.268751] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20a
[  975.300753] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20a
[  975.340756] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20c
[  975.380757] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20c
[  975.412760] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20c
[  975.452762] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f20c
[  975.492765] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100f80e
[  975.564771] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff01
[  976.292816] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[  976.604835] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[ 1002.494436] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[ 1002.766454] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1002.814454] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fb0e
[ 1002.886470] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[ 1002.926468] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[ 1003.142476] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1003.206480] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100050e
[ 1003.278455] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100060e
[ 1003.318487] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100050e
[ 1003.438484] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1003.486496] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[ 1003.566505] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100020e
[ 1003.598506] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100020e
[ 1005.278596] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000100
[ 1005.326613] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000200
[ 1005.366619] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000cfa
[ 1005.398616] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000cfb
[ 1005.486625] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10001fe
[ 1005.534612] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000fe
[ 1005.686622] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000100
[ 1005.742620] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[ 1005.798631] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[ 1005.846644] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10003f9
[ 1005.878644] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10005f6
[ 1005.918650] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10004f7
[ 1006.486684] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1006.630698] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1035.400491] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000004
[ 1035.440494] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[ 1035.512476] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100000e
[ 1035.552484] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100ff0e
[ 1035.592500] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x100fa0e
[ 1035.624503] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1037.296597] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10000ff
[ 1037.984654] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000001
[ 1038.032654] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x10007fe
[ 1038.064657] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
[ 1038.144663] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
[ 1038.176664] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000ef7
[ 1038.216666] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000ef6
[ 1038.256666] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000ef5
[ 1038.296670] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000ef6
[ 1038.328670] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
[ 1038.368677] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
[ 1038.408678] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
[ 1038.440680] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efb
[ 1038.480681] imon 5-3:1.0: imon_incoming_packet: unknown keypress, code 0x1000efa
```

I have tried configuring an Imon Pad, an Imon IR and finally an IMON VERIS, that's my remote actually with no luck.

I have tried the irw thing but this does nothing.

Any idea?

---

### Post by Lester_Burnham on 2012-06-24
Hi,

How did you setup remote? In mythbuntu control centre?
The channel change banner is probably there because it can't get lock on the channel, so it's not the problem. More than likely your signal or TV card setup. What are you using?

Just as a test stop lirc and try sudo ir-keytable and see what it returns, then sudo ir-keytable -t
I have an imon that worked OK with lirc on a Thermaltake Bach case

Ignore below, I see you got it fixed.
I would try un-muting ATI HDMI with 'm' key and set Mythtv to use card=HDMI dev 3 option and see how you go.

Lester

---

### Post by MPsico on 2012-06-25
> **Lester_Burnham said:**
> Hi,

How did you setup remote? In mythbuntu control centre?


Yes I set it up using mythbuntu control centre.

[quote=Lester_Burnham]
The channel change banner is probably there because it can't get lock on the channel, so it's not the problem. More than likely your signal or TV card setup. What are you using?
[/quote]

It says something that the channel is already locked and I should already be watching that, but disappears after a second. I don't think the problem is the signal because this doesn't happen with openelec for example, the changing between channels is really faster.

I using a DVB-T usb stick, it's a generic one, it's recognized as ITE9135, I set it up as DVB-T V3.X or something like that on the backend. I didn't  ouch any other options there.

[quote=Lester_Burnham]
Just as a test stop lirc and try sudo ir-keytable and see what it returns, then sudo ir-keytable -t
I have an imon that worked OK with lirc on a Thermaltake Bach case
[/quote]

I don't have any "lirc" process going around, I do have a "lircd" process, I have stopped it, then i type sudo ir-keytable and it says that i don't have installed ir-keytable program.

so i installed irkeytable using sudo apt-get install ir-keytable

then i run sudo ir-keytable, i got this out:

```
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
	Driver imon, table rc-imon-pad
	Supported protocols: RC-6 other 
	Enabled protocols: 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event13) with:
	Driver it913x, table rc-kworld-315u
	Supported protocols: NEC 
	Enabled protocols: 
	Repeat delay = 500 ms, repeat period = 125 ms

```

and sudo ir-keytable -t:

> Testing events. Please, press CTRL-C to abort.

and nothing happens after 10 minutes I stopped it.

I want to thanks again all the help!

---

### Post by MPsico on 2012-06-25
I have tried again the sudo ir-keyable -t command, and press buttons on the remote.

I have output then:

```
1340660117.505888: event MSC: scancode = 1007f00
1340660117.505892: event key down: KEY_DOWN (0x006c)
1340660117.505893: event sync
1340660117.756826: event key up: KEY_DOWN (0x006c)
1340660117.756828: event sync
1340660120.320709: event MSC: scancode = 2000028
1340660120.320715: event key down: KEY_ENTER (0x001c)
1340660120.320716: event sync
1340660120.568840: event key up: KEY_ENTER (0x001c)
1340660120.568843: event sync
1340660134.594899: event MSC: scancode = 1008000
1340660134.594907: event key down: KEY_UP (0x0067)
1340660134.594909: event sync
1340660134.844834: event key up: KEY_UP (0x0067)
1340660134.844836: event sync
1340660136.841985: event MSC: scancode = 2000028
1340660136.841989: event key down: KEY_ENTER (0x001c)
1340660136.841990: event sync
1340660137.092839: event key up: KEY_ENTER (0x001c)
1340660137.092841: event sync
1340660158.681678: event MSC: scancode = 200001e
1340660158.681681: event key down: KEY_NUMERIC_1 (0x0201)
1340660158.681681: event sync
1340660158.932817: event key up: KEY_NUMERIC_1 (0x0201)
1340660158.932819: event sync
1340660159.281462: event MSC: scancode = 200001e
1340660159.281466: event key down: KEY_NUMERIC_1 (0x0201)
1340660159.281466: event sync
1340660159.532833: event key up: KEY_NUMERIC_1 (0x0201)
1340660159.532835: event sync
1340660159.825256: event MSC: scancode = 200001f
1340660159.825259: event key down: KEY_NUMERIC_2 (0x0202)
1340660159.825260: event sync
1340660160.076812: event key up: KEY_NUMERIC_2 (0x0202)
1340660160.076813: event sync
1340660160.153165: event MSC: scancode = 2000020
1340660160.153171: event key down: KEY_NUMERIC_3 (0x0203)
1340660160.153172: event sync
1340660160.404811: event key up: KEY_NUMERIC_3 (0x0203)
1340660160.404812: event sync
1340660161.969480: event MSC: scancode = 288795b7
1340660161.969484: event key down: KEY_CHANNELDOWN (0x0193)
1340660161.969485: event sync
1340660162.220834: event key up: KEY_CHANNELDOWN (0x0193)
1340660162.220837: event sync
1340660162.673251: event MSC: scancode = 289395b7
1340660162.673257: event key down: KEY_CHANNELUP (0x0192)
1340660162.673259: event sync
1340660162.924826: event key up: KEY_CHANNELUP (0x0192)
1340660162.924828: event sync

```

---

### Post by bance on 2012-06-26
Hi,

I followed [this]("http://forum.xbmc.org/showthread.php?tid=104541") howto to get my remote working.....

But I haven't been able to get the settings to stick after a reboot.

HTH Steve.

---

### Post by MPsico on 2012-06-26
> **bance said:**
> Hi,

I followed [this]("http://forum.xbmc.org/showthread.php?tid=104541") howto to get my remote working.....

But I haven't been able to get the settings to stick after a reboot.

HTH Steve.


Well, no luck at all, even worst, usually some keys of the remote do work, for example the directional arrows, the escape, etc, the numeric pad, or the channel up, channel down don't work.

I've tried the second method, and the remote stopped working at all, none key was working.

I've to reboot the system and everything cames to normal.

When i use this command:

```
ir-keytable -c -p NEC,RC-5,RC-6,JVC,SONY,LIRC -t
```

I didn't get any output and the remote is like dead...

Any help please? This is really annoying, I will check it out how is this configured in openelec, because there worked without any further configuration.

---

### Post by Lester_Burnham on 2012-06-26
Hi,

You shouldn't need to run that command. 
sudo ir-keytable -t will only run if you stop lirc

I forgot to get back to this post yesterday. Sorry.

Have a look at this post for an MCE remote and see if you understand how it works.
[http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/](http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/)

You will more than likely need to create a config for your remote to relate the irevent codes to lirc codes.
Do a sudo or-keytable -t for all keys and attach it here.

Can can configure it without lirc. But I prefer the lirc method.

Lester

---

### Post by MPsico on 2012-06-27
> **Lester_Burnham said:**
> Hi,

You shouldn't need to run that command. 
sudo ir-keytable -t will only run if you stop lirc

I forgot to get back to this post yesterday. Sorry.

Have a look at this post for an MCE remote and see if you understand how it works.
[http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/](http://www.pcmediacenter.com.au/forum/topic/46168-mce-keyboard-working-in-mythbuntu-1204/)

You will more than likely need to create a config for your remote to relate the irevent codes to lirc codes.
Do a sudo or-keytable -t for all keys and attach it here.

Can can configure it without lirc. But I prefer the lirc method.

Lester

Here is the output for all the keys of the remote:

```
sudo ir-keytable -t
Testing events. Please, press CTRL-C to abort.
1340838352.890248: event MSC: scancode = 288195b7
1340838352.890256: event key down: KEY_EXIT (0x00ae)
1340838352.890257: event sync
1340838353.058243: event key up: KEY_EXIT (0x00ae)
1340838353.058245: event sync
1340838362.178321: event MSC: scancode = 2a8115b7
1340838362.178330: event key down: KEY_PLAY (0x00cf)
1340838362.178331: event sync
1340838362.429063: event key up: KEY_PLAY (0x00cf)
1340838362.429065: event sync
1340838373.394452: event MSC: scancode = 298115b7
1340838373.394461: event key down: KEY_RECORD (0x00a7)
1340838373.394463: event sync
1340838373.586427: event key up: KEY_RECORD (0x00a7)
1340838373.586429: event sync
1340838374.634438: event MSC: scancode = 2a8195b7
1340838374.634445: event key down: KEY_REWIND (0x00a8)
1340838374.634447: event sync
1340838374.818442: event key up: KEY_REWIND (0x00a8)
1340838374.818444: event sync
1340838376.690485: event MSC: scancode = 2a9115b7
1340838376.690494: event key down: KEY_PAUSE (0x0077)
1340838376.690495: event sync
1340838376.858486: event key up: KEY_PAUSE (0x0077)
1340838376.858488: event sync
1340838377.570491: event MSC: scancode = 2b8115b7
1340838377.570500: event key down: KEY_FASTFORWARD (0x00d0)
1340838377.570501: event sync
1340838377.682500: event key up: KEY_FASTFORWARD (0x00d0)
1340838377.682503: event sync
1340838378.562496: event MSC: scancode = 298195b7
1340838378.562503: event key down: KEY_NEXT (0x0197)
1340838378.562504: event sync
1340838378.738505: event key up: KEY_NEXT (0x0197)
1340838378.738507: event sync
1340838379.762526: event MSC: scancode = 2b9715b7
1340838379.762535: event key down: KEY_STOP (0x0080)
1340838379.762537: event sync
1340838379.938527: event key up: KEY_STOP (0x0080)
1340838379.938529: event sync
1340838382.922547: event MSC: scancode = 2b9115b7
1340838382.922554: event key down: KEY_PREVIOUS (0x019c)
1340838382.922556: event sync
1340838383.122550: event key up: KEY_PREVIOUS (0x019c)
1340838383.122552: event sync
1340838396.937781: event MSC: scancode = 200002c
1340838396.937789: event key down: KEY_SPACE (0x0039)
1340838396.937791: event sync
1340838397.161794: event key up: KEY_SPACE (0x0039)
1340838397.161796: event sync
1340838398.129804: event MSC: scancode = 200002a
1340838398.129812: event key down: KEY_BACKSPACE (0x000e)
1340838398.129814: event sync
1340838398.297789: event key up: KEY_BACKSPACE (0x000e)
1340838398.297791: event sync
1340838414.674095: event MSC: scancode = 1008000
1340838414.674103: event key down: KEY_UP (0x0067)
1340838414.674105: event sync
1340838414.925039: event key up: KEY_UP (0x0067)
1340838414.925041: event sync
1340838416.986147: event MSC: scancode = 1007f00
1340838416.986156: event key down: KEY_DOWN (0x006c)
1340838416.986157: event sync
1340838417.237050: event key up: KEY_DOWN (0x006c)
1340838417.237052: event sync
1340838420.274246: event MSC: scancode = 100007f
1340838420.274255: event key down: KEY_RIGHT (0x006a)
1340838420.274257: event sync
1340838420.525039: event key up: KEY_RIGHT (0x006a)
1340838420.525041: event sync
1340838421.762235: event MSC: scancode = 1000080
1340838421.762243: event key down: KEY_LEFT (0x0069)
1340838421.762244: event sync
1340838422.013058: event key up: KEY_LEFT (0x0069)
1340838422.013060: event sync
1340838427.418393: event MSC: scancode = 2000029
1340838427.418404: event key down: KEY_ESC (0x0001)
1340838427.418406: event sync
1340838427.522373: event key up: KEY_ESC (0x0001)
1340838427.522375: event sync
1340838442.923732: event MSC: scancode = 2b9595b7
1340838442.923740: event key down: KEY_MUTE (0x0071)
1340838442.923742: event sync
1340838443.123734: event key up: KEY_MUTE (0x0071)
1340838443.123736: event sync
1340838446.979850: event MSC: scancode = 28a395b7
1340838446.979859: event key down: KEY_VOLUMEUP (0x0073)
1340838446.979860: event sync
1340838447.131858: event key up: KEY_VOLUMEUP (0x0073)
1340838447.131860: event sync
1340838448.051879: event MSC: scancode = 28a595b7
1340838448.051888: event key down: KEY_VOLUMEDOWN (0x0072)
1340838448.051889: event sync
1340838448.211885: event key up: KEY_VOLUMEDOWN (0x0072)
1340838448.211887: event sync
1340838449.451918: event MSC: scancode = 289395b7
1340838449.451924: event key down: KEY_CHANNELUP (0x0192)
1340838449.451926: event sync
1340838449.571918: event key up: KEY_CHANNELUP (0x0192)
1340838449.571920: event sync
1340838450.587938: event MSC: scancode = 288795b7
1340838450.587944: event key down: KEY_CHANNELDOWN (0x0193)
1340838450.587945: event sync
1340838450.747945: event key up: KEY_CHANNELDOWN (0x0193)
1340838450.747947: event sync
1340838454.611052: event MSC: scancode = 200001e
1340838454.611058: event key down: KEY_NUMERIC_1 (0x0201)
1340838454.611060: event sync
1340838454.771057: event key up: KEY_NUMERIC_1 (0x0201)
1340838454.771059: event sync
1340838455.531060: event MSC: scancode = 200001f
1340838455.531066: event key down: KEY_NUMERIC_2 (0x0202)
1340838455.531068: event sync
1340838455.635077: event key up: KEY_NUMERIC_2 (0x0202)
1340838455.635079: event sync
1340838456.243074: event MSC: scancode = 2000020
1340838456.243079: event key down: KEY_NUMERIC_3 (0x0203)
1340838456.243080: event sync
1340838456.435099: event key up: KEY_NUMERIC_3 (0x0203)
1340838456.435101: event sync
1340838457.019115: event MSC: scancode = 2000021
1340838457.019121: event key down: KEY_NUMERIC_4 (0x0204)
1340838457.019122: event sync
1340838457.171120: event key up: KEY_NUMERIC_4 (0x0204)
1340838457.171121: event sync
1340838457.867126: event MSC: scancode = 2000022
1340838457.867132: event key down: KEY_NUMERIC_5 (0x0205)
1340838457.867134: event sync
1340838458.011141: event key up: KEY_NUMERIC_5 (0x0205)
1340838458.011143: event sync
1340838458.611168: event MSC: scancode = 2000023
1340838458.611174: event key down: KEY_NUMERIC_6 (0x0206)
1340838458.611176: event sync
1340838458.795164: event key up: KEY_NUMERIC_6 (0x0206)
1340838458.795166: event sync
1340838459.451185: event MSC: scancode = 2000024
1340838459.451192: event key down: KEY_NUMERIC_7 (0x0207)
1340838459.451193: event sync
1340838459.643167: event key up: KEY_NUMERIC_7 (0x0207)
1340838459.643169: event sync
1340838461.035237: event MSC: scancode = 2000025
1340838461.035244: event key down: KEY_NUMERIC_8 (0x0208)
1340838461.035246: event sync
1340838461.203214: event key up: KEY_NUMERIC_8 (0x0208)
1340838461.203216: event sync
1340838461.811248: event MSC: scancode = 2000026
1340838461.811254: event key down: KEY_NUMERIC_9 (0x0209)
1340838461.811256: event sync
1340838462.003237: event key up: KEY_NUMERIC_9 (0x0209)
1340838462.003239: event sync
1340838464.587313: event MSC: scancode = 2000027
1340838464.587319: event key down: KEY_NUMERIC_0 (0x0200)
1340838464.587320: event sync
1340838464.763318: event key up: KEY_NUMERIC_0 (0x0200)
1340838464.763320: event sync
1340838465.459350: event MSC: scancode = 2200025
1340838465.459356: event key down: KEY_NUMERIC_STAR (0x020a)
1340838465.459358: event sync
1340838465.627336: event key up: KEY_NUMERIC_STAR (0x020a)
1340838465.627338: event sync
1340838466.539382: event MSC: scancode = 2200020
1340838466.539387: event key down: KEY_NUMERIC_POUND (0x020b)
1340838466.539389: event sync
1340838466.667368: event key up: KEY_NUMERIC_POUND (0x020b)
1340838466.667370: event sync
1340838469.444446: event MSC: scancode = 2b8515b7
1340838469.444452: event key down: KEY_VIDEO (0x0189)
1340838469.444453: event sync
1340838469.628471: event key up: KEY_VIDEO (0x0189)
1340838469.628474: event sync
1340838470.468496: event MSC: scancode = 299195b7
1340838470.468503: event key down: KEY_AUDIO (0x0188)
1340838470.468504: event sync
1340838470.652502: event key up: KEY_AUDIO (0x0188)
1340838470.652504: event sync
1340838471.900520: event MSC: scancode = 2ba115b7
1340838471.900526: event key down: KEY_IMAGES (0x01ba)
1340838471.900527: event sync
1340838472.068548: event key up: KEY_IMAGES (0x01ba)
1340838472.068550: event sync
1340838473.244579: event MSC: scancode = 28a515b7
1340838473.244586: event key down: KEY_TV (0x0179)
1340838473.244587: event sync
1340838473.420592: event key up: KEY_TV (0x0179)
1340838473.420594: event sync
1340838474.628605: event MSC: scancode = 2aa395b7
1340838474.628611: event key down: KEY_SCREEN (0x0177)
1340838474.628613: event sync
1340838474.812624: event key up: KEY_SCREEN (0x0177)
1340838474.812626: event sync
1340838475.756652: event MSC: scancode = 29a595b7
1340838475.756659: event key down: KEY_ZOOM (0x0174)
1340838475.756660: event sync
1340838475.924641: event key up: KEY_ZOOM (0x0174)
1340838475.924643: event sync
1340838476.804667: event MSC: scancode = 2ab715b7
1340838476.804677: event key down: KEY_CAMERA (0x00d4)
1340838476.804678: event sync
1340838476.972691: event key up: KEY_CAMERA (0x00d4)
1340838476.972693: event sync
1340838477.692711: event MSC: scancode = 288515b7
1340838477.692720: event key down: KEY_BOOKMARKS (0x009c)
1340838477.692722: event sync
1340838477.844719: event key up: KEY_BOOKMARKS (0x009c)
1340838477.844721: event sync
1340838478.668741: event MSC: scancode = 29a395b7
1340838478.668748: event key down: KEY_DVD (0x0185)
1340838478.668750: event sync
1340838478.852744: event key up: KEY_DVD (0x0185)
1340838478.852746: event sync
1340838479.476764: event MSC: scancode = 2ba395b7
1340838479.476773: event key down: KEY_MENU (0x008b)
1340838479.476774: event sync
1340838479.660780: event key up: KEY_MENU (0x008b)
1340838479.660782: event sync
1340838480.492796: event MSC: scancode = 298595b7
1340838480.492802: event key down: KEY_SUBTITLE (0x0172)
1340838480.492804: event sync
1340838480.668809: event key up: KEY_SUBTITLE (0x0172)
1340838480.668812: event sync
1340838481.412827: event MSC: scancode = 2b8595b7
1340838481.412833: event key down: KEY_LANGUAGE (0x0170)
1340838481.412835: event sync
1340838481.636831: event key up: KEY_LANGUAGE (0x0170)
1340838481.636833: event sync
1340838590.743907: event key down: KEY_ENTER (0x001c)
1340838590.743909: event sync
1340838590.927920: event key up: KEY_ENTER (0x001c)
1340838590.927922: event sync

```

---

### Post by Lester_Burnham on 2012-06-27
Hi, 

I'll create a file and get back to you with more instructions.

Lester

---

### Post by Lester_Burnham on 2012-06-28
Hi,

All those codes are already in my lircd.conf.devinput to save me some time, just copy the files to the same paths I did.

Any files you change, make a copy for backup first,but you can see below, I backed up a couple. Extract files to home directory. They will be extracted to ~/lirc_files/
Make sure files copied accross have the same permissions as the ones you've replaced.

```
sudo cp ~/lirc_files/lird.conf.devinput /usr/share/lirc/remotes/mceusb/lircd.conf.devinput
sudo cp /etc/lirc/lird.conf. /etc/lircd.conf.old
sudo cp ~/lirc_files/lircd.conf /etc/lirc/lircd.conf
cd /etc/lirc/

```
Now check what input event your remote is. As you can see, mine is /dev/input/event4 (rc-rc6-mce)
Now list what is in /dev/input/by-id/ to grab the full path to you remote. (if you use this, changing USB ports doesn't effect it)
```
xbmc@e6300:~$ sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event15) with:
	Driver (null), table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc2/ (/dev/input/event16) with:
	Driver (null), table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 125 ms

xbmc@e6300:~$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00 -> ../event3

```
So the path to enter into /etc/lirc/hardware.conf would be:
```
/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00
```
Now we will backup our old hardware.conf to hardware.conf.old and then edit hardware.conf
```
sudo cp /etc/lirc/hardware.conf /etc/lirc/hardware.conf.old
```
Here is my edited hardware.conf (notice the LOAD_MODULES="false")
You can edit the copy of your old one, inserting the path to your imon, found above. Dont copy the whole thing, just change the parts in bold.
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER="**devinput**"
REMOTE_DEVICE="**/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00**"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="**false**"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Now move my mythtv and irexec files extracted earlier to ~/.lirc/ and make permissions the same as the other files in there. If you use my irexec, mythtv will start with the LiveTV (KEY_TUNER) button and XBMC if installed with the DVD (KEY_DVD) button.

Now restart lirc
```
sudo service lirc restart
```

See how you go with that, then try an irw and press some buttons.
I might have missed something, but I think it's all there.

Lester

---

### Post by MPsico on 2012-06-28
> **Lester_Burnham said:**
> Hi,

All those codes are already in my lircd.conf.devinput to save me some time, just copy the files to the same paths I did.

Any files you change, make a copy for backup first,but you can see below, I backed up a couple. Extract files to home directory. They will be extracted to ~/lirc_files/
Make sure files copied accross have the same permissions as the ones you've replaced.

```
sudo cp ~/lirc_files/lird.conf.devinput /usr/share/lirc/remotes/mceusb/lircd.conf.devinput
sudo cp /etc/lirc/lird.conf. /etc/lircd.conf.old
cd /etc/lirc/
```
Now check what input event your remote is. As you can see, mine is /dev/input/event4 (rc-rc6-mce)
Now list what is in /dev/input/by-id/ to grab the full path to you remote. (if you use this, changing USB ports doesn't effect it)
```
xbmc@e6300:~$ sudo ir-keytable 
Found /sys/class/rc/rc0/ (/dev/input/event4) with:
	Driver mceusb, table rc-rc6-mce
	Supported protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Enabled protocols: NEC RC-5 RC-6 JVC SONY LIRC other 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc1/ (/dev/input/event15) with:
	Driver (null), table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 125 ms
Found /sys/class/rc/rc2/ (/dev/input/event16) with:
	Driver (null), table rc-dib0700-rc5
	Supported protocols: NEC RC-5 RC-6 
	Enabled protocols: RC-5 
	Repeat delay = 500 ms, repeat period = 125 ms

xbmc@e6300:~$ ls -l /dev/input/by-id/
total 0
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Microsoft_Microsoft_3-Button_Mouse_with_IntelliEye_TM_-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 May 15 20:32 usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00 -> ../event3

```
So the path to enter into /etc/lirc/hardware.conf would be:
```
/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00
```
Now we will backup our old hardware.conf to hardware.conf.old and then edit hardware.conf
```
sudo cp /etc/lirc/hardware.conf /etc/lirc/hardware.conf.old
```
Here is my edited hardware.conf (notice the LOAD_MODULES="false")
You can edit the copy of your old one, inserting the path to your imon, found above. Dont copy the whole thing, just change the parts in bold.
```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Transceivers/Remotes (all)"
REMOTE_MODULES="lirc_dev mceusb"
REMOTE_DRIVER="**devinput**"
REMOTE_DEVICE="**/dev/input/by-id/usb-Philips_eHome_Infrared_Transceiver_PH00Q7WZ-event-if00**"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="**false**"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""
```

Now move my mythtv and irexec files extracted earlier to ~/.lirc/ and make permissions the same as the other files in there. If you use my irexec, mythtv will start with the LiveTV (KEY_TUNER) button and XBMC if installed with the DVD (KEY_DVD) button.

Now restart lirc
```
sudo service lirc restart
```

See how you go with that, then try an irw and press some buttons.
I might have missed something, but I think it's all there.

Lester

Lester, thanks again for your help.

You missed here one step, the one editing lircd.conf to point to the new lircd.conf.devinput

Now I can execute irw and I have signal for every press button.

However, under mythtv now I have the numeric pad, and the up-down channel and volume key, and the stop, play and that, but no anymore the directional pad, or the escape key.

And no key seems to trigger the epg for example.

I think now is time to edit something to tell mythtv the right keys.

Also, I see that outside mythtv the numeric keys for example don't work, I have irw and i see the press key, but nothing happens on the screen.

Any idea?

---

### Post by Lester_Burnham on 2012-06-28
[QUOTE=MPsico;12061451]Lester, thanks again for your help.
You missed here one step, the one editing lircd.conf to point to the new lircd.conf.devinput
Any idea?y]

I included the file, but forgot to move it over. Thanks

[QUOTE=MPsico;12061451]
Now I can execute irw and I have signal for every press button.

However, under mythtv now I have the numeric pad, and the up-down channel and volume key, and the stop, play and that, but no anymore the directional pad, or the escape key.

And no key seems to trigger the epg for example.

I think now is time to edit something to tell mythtv the right keys.

Also, I see that outside mythtv the numeric keys for example don't work, I have irw and i see the press key, but nothing happens on the screen.[\QUOTE]
Now you need to go through your ~/.lirc/mythtv at the bottom, everything with program = "devinput" and make sure the irw names match the button names in there.

I'm not sure about the remote working as a keyboard when mythtv is not running. The aim here was to get the remote working with mythtv. If I get a chance. I'll check out my other type of imon on another system and check the config, as it worked fine, without tweaking.

Lester

---

### Post by MPsico on 2012-06-30
> **Lester_Burnham said:**
> [QUOTE=MPsico;12061451]Lester, thanks again for your help.
You missed here one step, the one editing lircd.conf to point to the new lircd.conf.devinput
Any idea?y]

I included the file, but forgot to move it over. Thanks

[QUOTE=MPsico;12061451]
Now I can execute irw and I have signal for every press button.

However, under mythtv now I have the numeric pad, and the up-down channel and volume key, and the stop, play and that, but no anymore the directional pad, or the escape key.

And no key seems to trigger the epg for example.

I think now is time to edit something to tell mythtv the right keys.

Also, I see that outside mythtv the numeric keys for example don't work, I have irw and i see the press key, but nothing happens on the screen.[\QUOTE]
Now you need to go through your ~/.lirc/mythtv at the bottom, everything with program = "devinput" and make sure the irw names match the button names in there.

I'm not sure about the remote working as a keyboard when mythtv is not running. The aim here was to get the remote working with mythtv. If I get a chance. I'll check out my other type of imon on another system and check the config, as it worked fine, without tweaking.

Lester

Ok, I've modified some entries in the mythtv file, now we are getting close to something operational.

Some doubts: What's the key to change between audio channels? and the key to activate subtitles? and the key to activate teletext?

More, how can we do to change channel without pressing enter button? I mean there is a channel_up and channel_down button, I want that the change of channel take effect immediately after I press one of that keys.

Once I have the TV set it up we will have to move to the video library, I've managed to add a source, but all the videos are messed up, series and movies, even different series all messed up, It's not organized by folders like under XBMC. Also It don't recognize the most of the videos and don't download the corresponding metadata (under XBMC there is no problem with this).

Also, the main problem now is the time that take changing between channels, I think it's ridiculous slow compared to tvheadend+xbmc, or the internal tv tune card. Is there any way to speed up the process? I think the main problem here is that mythtv record everything, i don't think that's a good idea, is there a way to disable this "feature"?

---

### Post by Lester_Burnham on 2012-06-30
> **MPsico said:**
> Ok, I've modified some entries in the mythtv file, now we are getting close to something operational.

Some doubts: What's the key to change between audio channels? and the key to activate subtitles? and the key to activate teletext?
I am not sure, as I normally just hit the home button on an MCE remote to bring up the menu in live TV. Which I think is linked to the M key. Have a look [here]("http://www.mythtv.org/wiki/Keybindings") to see what the mythtv keyboard bindings are. they should be up to date. If you look in mythweb settings > Mythtv > key bindings. You can set your own key combos in there and add that to your lirc mythtv file.

Be careful not to duplicate existing combos. I just use mythtv as is and it's fine for me. You need to remember, the more you customise, if you lose all, the more work it is later to get it going again. Each to their own :)
> **MPsico said:**
> 
More, how can we do to change channel without pressing enter button? I mean there is a channel_up and channel_down button, I want that the change of channel take effect immediately after I press one of that keys.
 No idea with that one. I mainly watch recordings.
> **MPsico said:**
> Once I have the TV set it up we will have to move to the video library, I've managed to add a source, but all the videos are messed up, series and movies, even different series all messed up, It's not organized by folders like under XBMC. Also It don't recognize the most of the videos and don't download the corresponding metadata (under XBMC there is no problem with this).
I still use XBMC for this, plus I only have minimal torrent TV. My movies are setup in mythtv, but that's all.
Mainly because it's meant to handle the different frame rates better, without too much xorg config.
If you read the wiki, there are fairly strict naming conventions for season episode material, plus a statement that they don't really care for pirated material.

On my frontend / backend:
I just have XBMC setup as a menu item on mythtv front page. The downside is some updates remove it again.
There other way you can do it, is to use irexec and set a button for XBMC (I use DVD button, because I don't play DVDs). If using ACPI wake, you need to add XBMC to your mythtvshutdowncheck script.
Usage: Live TV button to enter mythtv. Exit mythtv and press DVD button to launch XBMC. (Set shutdown to quit only in XBMC)

Lester

---

### Post by Lester_Burnham on 2012-06-30
> **MPsico said:**
> Also, the main problem now is the time that take changing between channels, I think it's ridiculous slow compared to tvheadend+xbmc, or the internal tv tune card. Is there any way to speed up the process? I think the main problem here is that mythtv record everything, i don't think that's a good idea, is there a way to disable this "feature"?

You might be better of just tweaking what you had.
Mythtv has always been on the slower side, depending on tuners and signal strength. Maybe it is just more careful on getting a lock.

There is some settings for using quick tuning in the backend setup under inputs I think. (where you scan for channels) The down side could be if it effects recordings failing because of no lock.

Lester

---

### Post by nickrout on 2012-07-01
> **Lester_Burnham said:**
> You might be better of just tweaking what you had.
Mythtv has always been on the slower side, depending on tuners and signal strength. Maybe it is just more careful on getting a lock.

There is some settings for using quick tuning in the backend setup under inputs I think. (where you scan for channels) The down side could be if it effects recordings failing because of no lock.

Lester

I am beginning to think that mythtv is not what MPisco wants. He doesn't seem satisfied with how it works or the philosophy of it's design. 

MPisco LiveTV is not mythtv's primary role. It is an added bonus.

Record what you want to watch, watch it when you want to. Forget livetv, it has little relevance to mythtv's designed usage.

---

### Post by Lester_Burnham on 2012-07-01
> **nickrout said:**
> I am beginning to think that mythtv is not what MPisco wants. He doesn't seem satisfied with how it works or the philosophy of it's design. 

MPisco LiveTV is not mythtv's primary role. It is an added bonus.

Record what you want to watch, watch it when you want to. Forget livetv, it has little relevance to mythtv's designed usage.

Hi,

Yeah, I was trying to work out MPsico's intended usage and arrived at the conclusion, that maybe the system is in a bedroom hooked up to a TV or monitor with no tuner. I would maybe then use live TV from time to time.

The problem being the OP has come across from XBMC (which is very polished at what it does), so now they are trying to add the full blown TV support instead of TV Headend. I think the best option is a combination of mythtv + XBMC.

I am also surprised the remote (imon Veris) does not work out of the box. At the moment I think it's set up as an imon pad. The codes didn't seem to match a veris either!

That's what I use.

Lester

---

### Post by MPsico on 2012-07-03
Thanks for all the answers and the help.

I have came to the same conclusion: Mythbuntu (MythTV being specific) it's not what I looking for.

I have an HTPC that is plugged to the main tv of the house, so I need:

LiveTV: That needs to work flawlessly, good EPG, fast channel changing, full remote support.

Videos: I have two folders, Movies and TVSeries, I need that the system be able to organize and play them with no problem, changing between audio channels and subtitles.

A torrent client, reachable via webui.

Jdownloader, again reachable via webui.

Samba, to access to the folders and administrate the downloads in the different categories.

I've already tried:

XBMCBuntu+TVHeadend=Impossible to make that TVHeadend recognize the DVB-T hardware.

OPENELEC+TVHeadend=Very unstable, lot of restarts every day, very annoying. Adding any new program could be a pain in the ***. I was not able to had jdownloader operational.

MYTHBUNTU=Haven't tested so much like OPENELEC, I have some crashes, and the livetv is not really good, too slow changing channels, it records everything, I don't want that. The media library is a mess, everything is messed up.

What would you recommend to me?

---

### Post by nickrout on 2012-07-03
> **MPsico said:**
> Thanks for all the answers and the help.

I have came to the same conclusion: Mythbuntu (MythTV being specific) it's not what I looking for.

I have an HTPC that is plugged to the main tv of the house, so I need:

LiveTV: That needs to work flawlessly, good EPG, fast channel changing, full remote support.

Videos: I have two folders, Movies and TVSeries, I need that the system be able to organize and play them with no problem, changing between audio channels and subtitles.

A torrent client, reachable via webui.

Jdownloader, again reachable via webui.

Samba, to access to the folders and administrate the downloads in the different categories.

I've already tried:

XBMCBuntu+TVHeadend=Impossible to make that TVHeadend recognize the DVB-T hardware.

OPENELEC+TVHeadend=Very unstable, lot of restarts every day, very annoying. Adding any new program could be a pain in the ***. I was not able to had jdownloader operational.

MYTHBUNTU=Haven't tested so much like OPENELEC, I have some crashes, and the livetv is not really good, too slow changing channels, it records everything, I don't want that. The media library is a mess, everything is messed up.

What would you recommend to me?

Well if you want tvheadend you could use ubuntu as your basis and install the necessary packages. I have run tvheadend on my mythbuntu master backend, although obviously both tvheadend and mythtv-backend cannnot access a tuner at the same time.

mythtv will do all you want, although the channel change time is longer than other methods because of the delay involved in recording everything. That's a design philosphy that you won't change in a month of sundays!

Specific issues: videos metadata - myth is fussy about naming, there is a very specific wiki article about naming. Frankly i think XBMC probably does this better, but Myth does it well too, if set up properly.

switching audio and subtitles - no issue, myth can do that.

remote, no issue.

samba is installed by default in mythbuntu.

torrenting: I use rtorrent, commandline, do it over ssh from another computer. I think there are also some web frontends for it.

jdownloader: never heard of it, but if there is a ubuntu package, there's nothing to stop you installing it.

Again, all those extras (torrent, jdownloader, samba etc) are also available in a machine using XBMC. I use XBMC as well as mythtv on my frontends.

In fact you have an HTPC with mythbuntu installed now. Just add the packagaes you want, and turn mythbackend off if you wish.

---

### Post by Lester_Burnham on 2012-07-04
Hi,

meTV is another TV app. Not sure how polished it is.
[http://vk7hse.hobby-site.org/blog/2010/07/me-tv-1-3-0-new-ui-layout-and-more/](http://vk7hse.hobby-site.org/blog/2010/07/me-tv-1-3-0-new-ui-layout-and-more/)
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

For torrents, transmission has a web GUI.
I  would continue to use XBMC With another app for live TV. If you can find one you're happy with.

Lester

---

### Post by MPsico on 2012-07-07
> **Lester_Burnham said:**
> Hi,

meTV is another TV app. Not sure how polished it is.
[http://vk7hse.hobby-site.org/blog/2010/07/me-tv-1-3-0-new-ui-layout-and-more/](http://vk7hse.hobby-site.org/blog/2010/07/me-tv-1-3-0-new-ui-layout-and-more/)
[https://launchpad.net/me-tv](https://launchpad.net/me-tv)

For torrents, transmission has a web GUI.
I  would continue to use XBMC With another app for live TV. If you can find one you're happy with.

Lester

mmm, meTV seems to be like an application to watch livetv, I want something more integrated...

For now I will have to stay with openelec, the problem with it is to get jdownloader working, and it's really unstable, i think that's tvheadend fault...

I would try vdr, but seems there is really few information about it

---

### Post by nickrout on 2012-07-07
> **MPsico said:**
> mmm, meTV seems to be like an application to watch livetv, I want something more integrated...

For now I will have to stay with openelec, the problem with it is to get jdownloader working, and it's really unstable, i think that's tvheadend fault...

I would try vdr, but seems there is really few information about it

Why openelec? why not just install xbmc and tvheadend on the ubuntu install you already have.

---

### Post by Lester_Burnham on 2012-07-08
> **nickrout said:**
> Why openelec? why not just install xbmc and tvheadend on the ubuntu install you already have.

And I'm pretty sure there is a fork of XBMC including tvheadend.
Hmmm...Maybe that fork is openlec.

---

### Post by nickrout on 2012-07-08
> **Lester_Burnham said:**
> And I'm pretty sure there is a fork of XBMC including tvheadend.
Hmmm...Maybe that fork is openlec.

He has an existing mythbuntu setup, I fail to see the difficulty in simply adding the required packages to that.

---

### Post by MPsico on 2012-07-08
I've already tried xbmcbuntu, but I was not able to tvheadend detect the dvb-t stick, I don't know why...

I think I would try again and ask in the xbmc o ubuntu forums to get the dvb-stick detected...

---

### Post by Lester_Burnham on 2012-07-09
> **MPsico said:**
> I've already tried xbmcbuntu, but I was not able to tvheadend detect the dvb-t stick, I don't know why...

I think I would try again and ask in the xbmc o ubuntu forums to get the dvb-stick detected...

It might just need firmware in /lib/firmware
What is it?

Lester

---

### Post by MPsico on 2012-07-09
It's a generic usb stick, It's detected as ite9135... I have no problem under windows, mythbuntu and openelec, but under xbmcbuntu tvheadend doesn't detect, though I think linux detects it... I have to install xbmcbuntu and check it out...

---

### Post by nickrout on 2012-07-09
> **MPsico said:**
> It's a generic usb stick, It's detected as ite9135... I have no problem under windows, mythbuntu and openelec, but under xbmcbuntu tvheadend doesn't detect, though I think linux detects it... I have to install xbmcbuntu and check it out...

does tvheadend detect it under mythbuntu? (switch mythbackend off first so there is no risk it is locking the card).

Also IIRC you need to restart tvheadend AFTER plugging in a usb stick.

It is easy to tell if the OS has detected the stick. dmesg and ls /dev/dvb* will tell you.

By the way there is no such thing as a "generic usb stick" - there are a number of different chipsets. Some are supported by linux, some are not. Some depend on the kernel and/or whether the patest dvb/v4l drivers are included.

---

### Post by MPsico on 2012-07-09
> **nickrout said:**
> does tvheadend detect it under mythbuntu? (switch mythbackend off first so there is no risk it is locking the card).

Also IIRC you need to restart tvheadend AFTER plugging in a usb stick.

It is easy to tell if the OS has detected the stick. dmesg and ls /dev/dvb* will tell you.

By the way there is no such thing as a "generic usb stick" - there are a number of different chipsets. Some are supported by linux, some are not. Some depend on the kernel and/or whether the patest dvb/v4l drivers are included.

Well, I don't know what is exactly the chipset of my usb stick. I do know that openelec and mythbuntu detects it as ite9135.

The stick is always plugged in.

I will make a fresh install of xbmcbuntu and tell you guys what happens.

---

### Post by MPsico on 2012-07-09
Well, I have installed the last xbmcbuntu and then I followed the tutorial for adding pvr functionality with the "pulse-eight" packages.

I activated the tvheadend client on xbmc.

But I'm not able of accessing the tvheadend backend webui. It keeps asking me for a username and password that I never set up during the installation.

Reading the forums says that the username and password are set it up during installation, so I have installed tvheadend once again using sudo apt-get install tvheadend, then I can set a username and password, but it's not working, when I try to access to the webui it don't recognize them.

I don't know what to do.

I think there is some things that must be more easy, I don't think there is really a necessary of a password for tvheadend backend webui. (it's not grant access to my bank accounts!!!)

Any help?

Wait!!! now it works!!! I don't know what I've touched but now I can access the webui...

Though, the tvcard is not detected, as every time I've installed xbmcbuntu...

---

### Post by MPsico on 2012-07-09
Reviewing the dmesg seems that I don't get the card detected by linux neither...

---

### Post by Lester_Burnham on 2012-07-10
> **MPsico said:**
> Reviewing the dmesg seems that I don't get the card detected by linux neither...

xbmcbuntu might be using an older kernel, compared to openlec.
What does lsusb show.

If you look at the [wiki page]("http://linuxtv.org/wiki/index.php/ITE_IT9135") for the ite9135, it says support was added from kernel 3.2 onwards.

The quick look I had at xbmcbuntu, seemed to be around kernel 3.0
you might only need the firmware.

Lester

---

### Post by MPsico on 2012-07-10
> **Lester_Burnham said:**
> xbmcbuntu might be using an older kernel, compared to openlec.
What does lsusb show.

If you look at the [wiki page]("http://linuxtv.org/wiki/index.php/ITE_IT9135") for the ite9135, it says support was added from kernel 3.2 onwards.

The quick look I had at xbmcbuntu, seemed to be around kernel 3.0
you might only need the firmware.

Lester

I see, so what should I do?

---

### Post by nickrout on 2012-07-11
> **MPsico said:**
> I see, so what should I do?

Run ubuntu 12.04, it has kernel 3.2.

So will your mythbuntu install (assuming it was 12.04), but suggestions to run what you want to do on ubuntu or mythbuntu seem to fall on deaf ears.

---

