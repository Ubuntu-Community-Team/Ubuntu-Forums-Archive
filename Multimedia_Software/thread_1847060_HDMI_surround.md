---
title: "HDMI surround"
date: 2011-09-20
forum: Multimedia Software
---

### Post by petri on 2011-09-20
I have ASUS P5N7A-VM and I can't get HDMI surround to work. HDMI stereo does work but... in w7 HDMI surround does work så motherboard is functional.

Here's an output för aplay -l

```
~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: NVidia [HDA NVidia], enhet 0: ALC1200 Analog [ALC1200 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: NVidia [HDA NVidia], enhet 1: ALC1200 Digital [ALC1200 Digital]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: NVidia [HDA NVidia], enhet 3: NVIDIA HDMI [NVIDIA HDMI]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

```
sry about the foreign :D but chipset(?) is readable



and speaker-test -c 6 -r 48000 -D hw:0,3 gives

0 - Front Left:   OK
4 - Center:       Played Rear Left
1 - Front Right:  OK
3 - Rear Right:   Played LFE
2 - Rear Left:    Played Center
5 - LFE: Played   Rear Right

Is there any hope get HDMI surround working? And if not which motherboard/graphics card will work out of the box?

---

### Post by BicyclerBoy on 2011-09-20
Looks like a nVidia ION/MCP7A chipset mobo graphics/HDA.

Did you notice the speaker-test channel order is messed up ?
There is an alsa bug affecting this chipset audio.

You did not say if there was any sound with 
speaker-test -c 6 -r 48000 -D hw:0,3 ?

speaker-test -c 2 -r 44100 -D hw:0,3

You should be able to use AC3/DTS 5.1 over HDMI (digital pass-thru'.
Can't test that with speaker-test unfortunately.

GT430/220/240/520 work with std driver packages but you still need to edit one file (GT520 needs no file edits).
I would not recommend GT520 for HTPC.

---

### Post by petri on 2011-09-20
speaker-test -c 6 -r 48000 -D hw:0,3 buzzes and it is in my first post.


speaker-test -c 2 -r 44100 -D hw:0,3 buzzes on both speakers OK.




> You should be able to use AC3/DTS 5.1 over HDMI (digital pass-thru'.
Now how can I do that? Shouldn't there be an alternative to "HDMI surround" in panelprogram: speaker-preferences-hardware tab?

How about HD6850, anyone with that graphics card?

---

### Post by BicyclerBoy on 2011-09-20
Your first post & 2nd does not report what is happening with speaker-test..
Are the speakers in the correct position/placement?
Pink noise (boiling water hissing) ?
The alsa version reported ? (you truncated the output)

Digital pass-thru' AC3 etc can not be controlled from pulse-audio or alsa  preferences.
Digital pass-thru' must be controlled from the media player (same in windows).
(VLC. MythTV, mplayer XBMC are all capabable)

Your HDA audio h/w does not report the audio capabilities ELD from any receiver.

Are you connecting the HDMI audio to a HT amp AVR ?
It is basically pointless using LPCM5.1 or AC3 on a TV..

I would not recommend any AMD video card for HTPC (at the present time).
XvBA (XvBS) is >3 yrs behind VDPAU & counting..

---

### Post by petri on 2011-10-02
Well I changed hardware and still no sound. Thought I should start a new thread: [http://ubuntuforums.org/showthread.php?p=11304524#post11304524](http://ubuntuforums.org/showthread.php?p=11304524#post11304524)

---

