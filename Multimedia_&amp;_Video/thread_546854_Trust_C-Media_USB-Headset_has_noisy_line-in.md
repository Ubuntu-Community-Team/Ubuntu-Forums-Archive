---
title: "Trust C-Media USB-Headset has noisy line-in"
date: 2007-09-09
forum: Multimedia &amp; Video
---

### Post by asdir on 2007-09-09
Suddenly during a skype conference my friends complained about a **static noise** and that my voice was muted a lot and they could not hear me through that. This pretty much is what I heard when I tried to call the SkypeTestCall-bot.
I can be ruled out that this problem is due to the mic or its sound-card or due to Skype since I tried it on my laptop also and with TeamSpeak. On the laptop the problem appeared as sudden as before and TeamSpeak had exactly the same problem.
I tried purging and reinstalling linux-sound-base, alsa-base and alsa-utils (all 3 at once), but it did not work. (Yes, I restarted the PC first.)

My system is Feisty (both desktop and laptop), I have another Soundcard, a SB-Live, and an onboard-card, which is turned off in the BIOS.

Any takers? Anything you need to know?

(Had other problems before, too: When a particular friend of mine was in the conference everyone had a slight problem understanding me. As soon as he left the problem vanished with him. I wonder if those too are connected, since he was in the conference when the problem described above appeared.)

---

### Post by bretticus on 2007-10-04
I have the same problem and the same setup...

```
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4670]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SBLive! Value [CT4670]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4670]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Headset [BT Headset], device 0: Bluetooth SCO PCM [BT SCO PCM]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any luck in figuring this one out? I tried ekiga with the same result (from the setup.) Only happens on this computer. I upgraded from feisty to gutsy recently (in hopes that things would be better)...no change.  This is bizarre! Music plays just fine. It's only when I combine "sound in" and "sound out" that I seem to have the scratchiness/fuzziness (sounds like a Star Wars bounty hunter!) For example, when I change "sound in" under skype, the test call playback clears up (of course this does me no good because I can't talk back.) Using the same device for both produces the raspy sound. I, as well, did the apt purging and reinstalling linux-sound-base, alsa-base and alsa-utils.

Ideas?

---

### Post by asdir on 2007-10-05
After shutting down, unplugging, restarting, shutting down, plugging it in, restarting again, it worked for me. However, I think the problem will be back soon. At least it was the same before I had it the first time: Worked for a couple of days, then it didn't without a noticeable change.

---

### Post by bretticus on 2007-10-09
asdir,

Thanks for the update. I have never been able thus far to get anything other than the static, raspy sound when using Skype. I can get a clear sound on sound out only...Youtube, VLC, etc.

Glad you can make yours work even sometimes.

---

### Post by questpro on 2007-10-09
Hi guyz,

I am also using the C-Media USB headset. Can you hear the sound in both sides of the headset when using skype?? Please let me know how did you manage to do that?

Thanks in advance :)

EDIT: I can only hear in one side of the headset when using skype voice call.

---

### Post by asdir on 2007-10-10
sorry to disappoint you both, but we seem to have different problems: I do not have the problem in skype only, but also with any other program that uses line in (teamspeak for instance).
Also I hear what I should be hearing perfectly on both sides.

If I can come up with a solution for my prob, I will still post it here though.

---

