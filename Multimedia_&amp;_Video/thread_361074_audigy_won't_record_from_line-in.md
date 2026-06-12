---
title: "audigy won't record from line-in"
date: 2007-02-13
forum: Multimedia &amp; Video
---

### Post by eradicator_006 on 2007-02-13
Hello

I just installed a SB Audigy Platinum in to my soon to be mythtv box.  I did a server install of dapper and installed what i needed using apt.  I am unable to record from the line-in port on the card.  If I unmute line under playback I get sound to the speakers so this shows the line-in port is actually working.  For some reason "Line" is not listed under capture devices in alsamixer.  Here is what arecord -l tells me:

**** List of CAPTURE Hardware Devices ****
card 0: Audigy [Audigy 1 [SB0090]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy [Audigy 1 [SB0090]], device 1: emu10k1 mic [Mic Capture]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy [Audigy 1 [SB0090]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Right now I am using a custom 2.6.19 kernel.  I did try the latest official ubuntu kernel and had the same results.  Using the onboard nforce2 audio things work perfect (this is disabled in the bios now).

Does anybody know how to enable the line-in port as a capture device?  I've been puzzled over this all day and would really like to get it working. 

Thanks

---

### Post by Cresho on 2008-03-02
I hate myself.  I found something regarding this issue.  I know gutsy has a problem recording line in or mic in for that matter.  Hardy heron works fine.  I can record from line in through analog mix just fine and I also found something regarding about adding something to line in record.  Ill post as soon as i find my bookmark.

---

### Post by neodarksaver on 2008-04-06
i have the same problem in hardy. i have audigy platinum ex. the mic doesnt work from the external box.

---

