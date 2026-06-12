---
title: "External sound card not producing sound in all the speaker"
date: 2011-09-08
forum: Multimedia Software
---

### Post by dhrayofhope on 2011-09-08
[SIZE=3]Hi all,[/SIZE] 
[SIZE=3]I m using an external sound card in my desktop....., (the driver name is C-Media PCI)...[/SIZE] 
[SIZE=3]I have a 5.1 sound system connected to this sound card.... by three input jack....to the three seperate slots in the external sound card.....[/SIZE] 
 
[SIZE=3]Actually sound comes in only one speaker......[/SIZE] 
[SIZE=3]How to get the sound from all the speakers.....[/SIZE] 
 
[SIZE=3]Only center and rear-right speaker along with the sub-woofer are producing sound.......the rear-right speaker is louder than the center one.... i can not hear any sound from the other speakers........[/SIZE] 
 
[SIZE=3]And how can I adjust the separate volumes of individual speakers..... [/SIZE] 
[SIZE=3]Please help...........[/SIZE] 
 
 
[SIZE=3]Thanks in advance........[/SIZE] 
 
[SIZE=3]necessary info:---[/SIZE] 
 
[SIZE=3]aplay -l[/SIZE] 
[SIZE=3]----------output----------------------------------------------------------------------------------[/SIZE] 
[SIZE=3]*** List of PLAYBACK Hardware Devices ****[/SIZE] 
[SIZE=3]card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC][/SIZE] 
[SIZE=3]Subdevices: 1/1[/SIZE] 
[SIZE=3]Subdevice #0: subdevice #0[/SIZE] 
[SIZE=3]card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC][/SIZE] 
[SIZE=3]Subdevices: 1/1[/SIZE] 
[SIZE=3]Subdevice #0: subdevice #0[/SIZE] 
[SIZE=3]card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958][/SIZE] 
[SIZE=3]Subdevices: 1/1[/SIZE] 
[SIZE=3]Subdevice #0: subdevice #0[/SIZE] 
[SIZE=3]card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog][/SIZE] 
[SIZE=3]Subdevices: 1/1[/SIZE] 
[SIZE=3]Subdevice #0: subdevice #0[/SIZE] 
[SIZE=3]card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital][/SIZE] 
[SIZE=3]Subdevices: 1/1[/SIZE] 
[SIZE=3]Subdevice #0: subdevice #0[/SIZE] 
[SIZE=3]----------------------------------------------------------------------------------------------------[/SIZE] 
 
[SIZE=3]Help please....:(:(:(

[/SIZE]```
for i in `lspci -nn | grep '04[80][13]' | awk '{print $1}'`; do lspci -vvvs $i; done

```
[SIZE=3]00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device 8249
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at dfef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
    Subsystem: C-Media Electronics Inc CM8738
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 6000ns max)
    Interrupt: pin A routed to IRQ 17
    Region 0: I/O ports at c800
Capabilities: <access denied>
Kernel driver in use: C-Media PCI
Kernel modules: snd-cmipci

---

### Post by lkjoel on 2011-09-09
Run this Terminal command:
```
alsamixer -c 0
```
And please post a screenshot

---

### Post by dhrayofhope on 2011-09-10
> **lkjoel said:**
> Run this Terminal command:
```
alsamixer -c 0
```And please post a screenshot

Thank God, :pThank you again......
this helps a lot..... i have tested something on that but still i need your help.....;)

Here is the screenshot of the settings before....
[IMG]file:///tmp/moz-screenshot.png[/IMG][ATTACH]201841[/ATTACH]

for testing the sound i have unmuted everything.... and make the settings as below (see the second screenshot attached just below):--
[ATTACH]201842[/ATTACH]

effect:--- 
front right:  louder sound
front left:    normal sound 
center:       below normal sound
rear left:    Hazy sound and too low to hear](*,)
rear right:  normal sound
Woofer:     working properly

now what is the effect of synth and line? because the pcm holds the control of both the four speakers., and how to configure the sound of the center speaker?

And i have a little knowledge of "Line Synth PCM"...](*,) is this three are responsible for the individual volume control??

Please show me some light ..........
Thank you in advance......

---

### Post by lkjoel on 2011-09-11
Don't worry about synth and line. You can go to the right, and scroll the screen to see more controls.

---

### Post by dhrayofhope on 2011-09-12
> **lkjoel said:**
> Don't worry about synth and line. You can go to the right, and scroll the screen to see more controls.

Thanks...:p
But how to remove the hazzy sound coming from the rear left speaker as i said in previous post....

and what about AUX and PC Speaker?? 
i think pc speaker is the small speaker attached to motherboard ... m I right?? so that will be for the sound coming at the time of booting.....

and what about AUX..... does anything (AUX, synth, pcm) effects to the sound.....???:!:

Thanks in advance.......:popcorn:

---

