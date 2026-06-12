---
title: "Keystation 49e not recognized"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by bluemorris on 2008-03-10
Hi,
I can't seem to get my M-Audio Keystation 49e recognized in Jack or Rosegarden.

When I type lsusb into the terminal I get:

```
Bus 004 Device 002: ID 040d:6204 VIA Technologies, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0a4d:0090 Evolution Electronics, Ltd 
Bus 003 Device 001: ID 0000:0000  

```

From what I have read, "Evolution Electronics" is the M-Audio Keystation keyboard. So it looks like Ubuntu has found it. But when I run Jack and look in "Connections" under the "Midi" tab it's not there.

It also does not appear in Rosegarden.

I'm running Ubuntu Studio Gutsy
Alsa 1.0.16
Sound card is M-Audio Revolution 7.1

Interestingly, I tried running the live CD of Dynebolic Ubuntu and in that Rosegarden recognized the keyboard fine, but in Ubuntu Studio Rosegarden and Jack don't find it.

I would rather use Ubuntu Studio so any help anyone can give me would be much appreciated!

---

### Post by bluemorris on 2008-03-12
They keyboard also works fine in Windows XP, so I don't understand why it's not working in Ubuntu. If anyone could help me with this I'd really appreciate it. I would much prefer to work in Ubuntu rather than going back to Windows.
Thanks!

---

### Post by Larrxi on 2008-03-12
Hello!

I got my Keystation 49e working in Ubuntu. I dont have midi on my sound card so i had to use a software synth. Just install Timidity and choose Timidity as output in Rosegarden.

---

### Post by bluemorris on 2008-03-12
> **Larrxi said:**
> I got my Keystation 49e working in Ubuntu. I dont have midi on my sound card so i had to use a software synth. Just install Timidity and choose Timidity as output in Rosegarden.

Thanks for your response. 

I do have Timidity installed. I can use soft synths, but not with my keyboard. Rosegarden and Jack don't seem to be able to find my keyboard. The Keystation doesn't show up in Jack or Rosegarden as an input device. 

It seems to work for other people so I don't understand why it doesn't work on my system. Argh.

---

### Post by Larrxi on 2008-03-13
You don't have to use Jack when you use Timidity. :)

---

### Post by peter3 on 2008-03-14
Here's what I get when I run aconnect:
peter3@heron:~/music/sf$ aconnect -io
client 0: 'System' [type=kernel]
    0 'Timer           '
    1 'Announce        '
client 14: 'Midi Through' [type=kernel]
    0 'Midi Through Port-0'
client 16: 'SBLive 5.1 [SB0060]' [type=kernel]
    0 'EMU10K1 MPU-401 (UART)'
client 17: 'Emu10k1 WaveTable' [type=kernel]
    0 'Emu10k1 Port 0  '
    1 'Emu10k1 Port 1  '
    2 'Emu10k1 Port 2  '
    3 'Emu10k1 Port 3  '
client 24: 'Keystation 49e' [type=kernel]
    0 'Keystation 49e MIDI 1'
peter3@heron:~/music/sf$ 

Then I run asfxload korgpiano.sf2, to load up the EMU10K
followed by 
aconnect 24:0 17:0 to hook the keyboard up to the wavetable.
Then my feeble playing produces sound.

Good Luck.

---

### Post by bluemorris on 2008-03-17
Thanks, but I've just reinstalled Ubuntu Studio and it's working now. I must have messed something up a while back and it's too difficult to figure out what :)

---

### Post by eric71 on 2008-03-18
Perhaps you blacklisted the snd-usb-audio module at one time or another.

---

