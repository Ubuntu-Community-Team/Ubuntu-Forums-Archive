---
title: "ATI TV Wonder Pro Sound issues"
date: 2006-10-04
forum: Multimedia &amp; Video
---

### Post by Stolie on 2006-10-04
Good Day,

So, I have a TV wonder pro that I bought before I made the switch to linux. Everything worked fine (oddly enough) in windows, but not in linux!  So, let me get to my problem:

I get great video output from my card, but it doesn't seem to want to put out any sound. I originally thought that it was an issue of communication between it and my sound card (ca0106), but it's not. I plugged both headphones AND powered speakers directly into the tv card, and no sound at all. 

All I'm trying to do is play game consoles thru my computer! It's one of the last things I need to get working to make my transition complete.

Any ideas, all?

Cheers

---

### Post by Stolie on 2006-10-05
Sorry for the double post, but I just came across something. I ran a dmesg and this is what I got when I grep for Leadtek:

```
desktop:~$ dmesg|grep Lead
[17179584.728000] CORE cx88[0]: subsystem: 1002:00f9, board: Leadtek Winfast 2000XP Expert [card=5,insmod option]
[17179584.940000] cx88[0]: Leadtek eeprom invalid.
[17179584.940000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input1

```

And if I grep for "tuner":

```
desktop:~$ dmesg|grep tuner
[17179584.728000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179585.364000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179585.364000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179585.364000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))

```

And, if I grep for "cx" because of the cx88xx driver:

```
desktop:~$ dmesg|grep cx
[17179584.728000] cx2388x v4l2 driver version 0.0.5 loaded
[17179584.728000] CORE cx88[0]: subsystem: 1002:00f9, board: Leadtek Winfast 2000XP Expert [card=5,insmod option]
[17179584.940000] cx88[0]: Leadtek eeprom invalid.
[17179584.940000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input1
[17179584.940000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 193, latency: 32, mmio: 0xae000000
[17179585.364000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179585.472000] cx88[0]/0: registered device video0 [v4l2]
[17179585.472000] cx88[0]/0: registered device vbi0
[17179585.472000] cx88[0]/0: registered device radio0

```

Any thoughts? I think I may have to change the CX driver to see the ATI card, but I'm unsure how to do that...

EDIT-- Ok, I figured it out! After much searching, I figured out that the "Leadtek" portion was completely wrong. I found a post on linuxquestions.org (i think) that gave me an idea. This card is type=4 in the CARDLIST.cx88, so all we needed to do was force it to set this as the type:
```
sudo nano /etc/modprobe.conf
```
```
options cx88xx card=4
```

And that's all there is to it! Solves the sound issue, Video's great, all works fine!

---

### Post by jinx099 on 2006-11-14
> **Stolie said:**
> Sorry for the double post, but I just came across something. I ran a dmesg and this is what I got when I grep for Leadtek:

```
desktop:~$ dmesg|grep Lead
[17179584.728000] CORE cx88[0]: subsystem: 1002:00f9, board: Leadtek Winfast 2000XP Expert [card=5,insmod option]
[17179584.940000] cx88[0]: Leadtek eeprom invalid.
[17179584.940000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input1

```

And if I grep for "tuner":

```
desktop:~$ dmesg|grep tuner
[17179584.728000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[17179585.364000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[17179585.364000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179585.364000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))

```

And, if I grep for "cx" because of the cx88xx driver:

```
desktop:~$ dmesg|grep cx
[17179584.728000] cx2388x v4l2 driver version 0.0.5 loaded
[17179584.728000] CORE cx88[0]: subsystem: 1002:00f9, board: Leadtek Winfast 2000XP Expert [card=5,insmod option]
[17179584.940000] cx88[0]: Leadtek eeprom invalid.
[17179584.940000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input1
[17179584.940000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 193, latency: 32, mmio: 0xae000000
[17179585.364000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[17179585.472000] cx88[0]/0: registered device video0 [v4l2]
[17179585.472000] cx88[0]/0: registered device vbi0
[17179585.472000] cx88[0]/0: registered device radio0

```

Any thoughts? I think I may have to change the CX driver to see the ATI card, but I'm unsure how to do that...

EDIT-- Ok, I figured it out! After much searching, I figured out that the "Leadtek" portion was completely wrong. I found a post on linuxquestions.org (i think) that gave me an idea. This card is type=4 in the CARDLIST.cx88, so all we needed to do was force it to set this as the type:
```
sudo nano /etc/modprobe.conf
```
```
options cx88xx card=4
```

And that's all there is to it! Solves the sound issue, Video's great, all works fine!


I'm having a similar problem, but I have an Audigy 2 ZS.  I can plug in headphones directly to the tv card, but nothing on the line-in works on the audigy.  Any ideas?  Can you post the thread from linuxquestion.org?

---

### Post by Stolie on 2006-11-14
Not sure about the Audigy 2 ZS. This was an issue with the ATI TV Wonder Pro not being configured correctly. Actually had nothing to do with my sound card.

Sorry I couldn't be of more help!

---

