---
title: "[SOLVED] Mic recording 10th time"
date: 2008-01-30
forum: Multimedia Production
---

### Post by ene_dene on 2008-01-30
Every now and then similar thread arises; I've got a mic, I can hear my self and it wouldn't record. And every time there is no solution, except for cases where user didn't set mic on record. On attachment that I've put here you can see that that is not a problem. So what is the problem? I'm looking all over net for hours now and thinking going back to windows where I don't have such elementary problems, it sucks, yeah, but at least I can use Skype. That SHOULD be working, why do these ALSA guys think that you need to be a professional in order to record microphone I don't know, but it is damaging Linux popularity very much.

---

### Post by Stochastic on 2008-01-30
what program are you using to record?  what are that program's settings?  are there other sound apps running?

---

### Post by ene_dene on 2008-01-31
> **Stochastic said:**
> what program are you using to record?  what are that program's settings?  are there other sound apps running?
Any program that I use for recording, directly or indirectly doesn't work in case of microphone. For example: sound recorder is set to record microphone and there is no sound. If I set it to record something else, master for example, it works just fine.
Skype is another example, no one can hear me. Here are few commands from console about my settings of sound card:
cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0xe000, irq 5

lspci -v | grep Creative
00:0a.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 1021


**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM
 Playback]
  Subdevices: 31/32
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
card 0: Audigy2 [Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture                                /PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by ene_dene on 2008-02-03
Anyone? Is this really impossible to solve?

---

### Post by eye208 on 2008-02-03
> **ene_dene said:**
> That SHOULD be working, why do these ALSA guys think that you need to be a professional in order to record microphone I don't know, but it is damaging Linux popularity very much.
No, it is damaging Creative Labs popularity. ALSA recording works fine here.

---

### Post by ene_dene on 2008-02-03
> **eye208 said:**
> No, it is damaging Creative Labs popularity. ALSA recording works fine here.
Yeah, right...

---

### Post by eye208 on 2008-02-03
> **ene_dene said:**
> Yeah, right...
I'm not kidding. Ask music producers what they think about Creative Labs. You're in for a big surprise.

Clever marketing does not make a good product. Creative Labs should be concerned about making their cards work with Linux. Apparently they're not.

Vote with your wallet.

---

### Post by ene_dene on 2008-02-04
> **eye208 said:**
> I'm not kidding. Ask music producers what they think about Creative Labs. You're in for a big surprise.

Clever marketing does not make a good product. Creative Labs should be concerned about making their cards work with Linux. Apparently they're not.

Vote with your wallet.
The card works fine in Windows. If 99% of they buyers use Windows, then it is logical that their primary concern is for Win users. Most people will rather stay on Windows if some hardware works, than buy new hardware and go to Linux.
One thing I can't understand is, how can I hear microphone, record anything else, but microphone recording just doesn't work. It looks to me that this is software problem then. Even if it is possible to set this card to record mic in Linux it is really irritating that it's so hard to set it to work fine.

---

### Post by darsu on 2008-02-04
I don't know if this applies to your card, but:

I use a Creative SBLive. The graphical mixer program Aumix, which I use, has a slider named IGain that Alsamixer doesn't show. I don't know what the IGain slider actually *is*, but it needs to be turned up: if it isn't, I can hear things but not record.

(I'm pretty certain it was the IGain slider. I haven't recorded anything in a while and I tend to forget these details fast...)

---

### Post by eye208 on 2008-02-04
> **ene_dene said:**
> The card works fine in Windows.
No it doesn't. Take a look at their support forums, especially for Windows Vista.

By the way, did you ask for help there?

---

### Post by ene_dene on 2008-02-04
> **eye208 said:**
> No it doesn't. Take a look at their support forums, especially for Windows Vista.

By the way, did you ask for help there?
Well, we can debate all day does it work or not in windows/linux, the fact is that my card works fine in windows and it doesn't work fine with ALSA/linux.

No, I didn't asked for help there, never had any problems with card till now. I can try, although I'm a bit sceptical since guys on linux forums don't know the solution.

---

### Post by eye208 on 2008-02-05
> **ene_dene said:**
> I can try, although I'm a bit sceptical since guys on linux forums don't know the solution.
From the [ALSA project website](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1):
> **Audigy4 capture**

First, one needs to identify one's sound card. Open a terminal windows and type:

```
cat /proc/asound/cards
```

This has been tested with the following cards:

```
0 [Audigy2 ]: Audigy2 - Audigy 4 [SB0610]
Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0x9400, irq 201
```

This note applies only to the SB0610 and may or may not work for other Audigy 4 cards.

The controls that have been tested and verified are: Mic and Line-in. In order to get sound capture working, set the following controls as they affect both Mic and Line-in: On the alsamixer Capture display:

[LIST=1]
[*]Master -> 100% or 0dB (affects both analog and digital capture sources)
[*]Analog Mix -> 100% or 0dB (affects only analog sources)
[/LIST]

Controls that affect Mic input: On the alsamixer Playback display: (these will eventually appear on the capture display once developers add the feature):

[LIST=1]
[*]Mic boost (If you need +20dB boost)
[*]Mic Select -> Mic1
[/LIST]

On the alsamixer Capture display:

[LIST=1]
[*]Mic -> 100%
[/LIST]

Controls that affect Line-in input: 1) Line -> 100% or +12dB
Your card is a SB0610. See if that works for you.

---

### Post by ene_dene on 2008-02-05
[quote="eye208"]Your card is a SB0610. See if that works for you.[/quote]
YES, it finally works! Thank you very much!

---

### Post by chrisc999 on 2008-03-12
I have an audigy 2 oem which ubuntu reports as being an audigy 2 platinum, I had exactly the same problems however you can record from the mic if you open alsamixer gui and turn up both the analog mix sliders one of which controls the monitor volume and the other the mic recording level, you also need to have the mic level turned up as well.  I hope this helps

---

### Post by pisse on 2008-03-28
I don't have a Line-in control in alsamixer.. but the volume control has.. doesn't effect anything as I've noticed.

My soundcard has a guitar plug at the front of the computer. Creative SB Audigy 2
How do I get alsa to "activate" that line in? Do I need other drivers or so?

---

