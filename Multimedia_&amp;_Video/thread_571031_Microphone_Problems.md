---
title: "Microphone Problems"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by bubba_chubs123 on 2007-10-08
Hey Everyone,

I'm somewhat of an Ubuntu virgin when it comes to a lot of things, but I think I've gotten the feel of it lately.

I have a question in regards to my Microphone and Sound Card. I have checked almost every fix on here in existence and it doesn't seem to be helping.

I have an MSI motherboard with built-in Audio (as listed below via the lspci -v command):
04:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Micro-Star International Co., Ltd. K8N Diamond
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at d880 [size=32]
        Capabilities: <access denied>

When I attempt to record anything at all (Skype, Sound Recorder etc.) I can hear my voice through the speakers perfectly, but cannot for the life of me get anything to record. I have tried to make several test calls with Skype, to which the person on the other end cannot hear me. I've checked all Volume Controls and had every bar that I needed cranked to the max.  Under the 'Recording' tab I have 'Toggle Audio Recording' set for the Microphone.

The one strange thing I noticed is that under the 'Switches' tab, I only have 'IEC958' listed, and when I check it, I cannot hear anything through the speakers. For 'Digital Capture Source' I have 'IEC958 in' selected, but I have tried all the '* in' options. 

I know you guys are amazing when it comes to these types of issues, so I thought I would give it a shot.

I'm running Feisty Fawn.

Thanks!

---

### Post by mikeym on 2007-10-14
I have almost exactly the same experience. The only way I seem to be able to hear anything from my mic is to select the combination of 'Digital Capture Source: IEC958 in'  and IEC958 unselected in the switches section. I also have to turn up capture feedback - nothing else will register anything - and even with these settings it wont record. 

What am I doing wrong?

---

### Post by mikeym on 2007-10-14
I've found settings that will let mine work now. Turning off Capture feadback, Audio Recording from the microphone enabled, IEC958 off in switches, digital capture source as 'i2s in' and 'shared mic / Line in' as 'Mic in'.

---

