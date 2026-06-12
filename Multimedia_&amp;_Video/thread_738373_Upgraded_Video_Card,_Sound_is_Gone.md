---
title: "Upgraded Video Card, Sound is Gone"
date: 2008-03-28
forum: Multimedia &amp; Video
---

### Post by jbuda123 on 2008-03-28
I upgraded my video card (from a very old Radeon to an Nvidia GeForce 6200, both AGP). The install of *that* went very smooth. But now I notice I don't have any audio. I've looked at a lot of posts and it looks like my card it being identified. From the Comprehensive Sound Guide: 

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and

```
$ lspci -v | grep Audio
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

So of course you're thinking it's the alsamixer volume thing (I've seen that suggestion everywhere and I recall I had this problem the day I first installed ubuntu). But it's not that. The Master, PCM, Line are all unmuted and at 100%. I've tried a variety of mute/unmute combos for some of the other volumes (PC Speaker, Aux, etc.). There is an "External Amp" one that I've tried both muted and unmuted. Nothing.

Any suggestions? Is there any way the new Nvidia card/driver is somehow conflicting with the soudn? I thought maybe I pulled a wire out when I was swapping the cards, but it's on-board audio so it's soldered right to the motherboard - there aren't even any wires. I'm sure it's something stupid but I can't figure out what's going on. It's Ubuntu Gutsy.

Thanks in advance for any suggestions or comments.

---

### Post by ubuntu-freak on 2008-03-29
I think you should reinstall Gutsy fresh, or the Hardy beta. Could just be that your hardware needs to be detected again. Out of curiousity. did you try putting the old card back in to see if sound reappeared?
 
Hope that helps, I'm no expert on sound issues.
 
Nathan

---

