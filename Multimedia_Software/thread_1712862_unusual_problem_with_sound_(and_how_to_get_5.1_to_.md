---
title: "unusual problem with sound (and how to get 5.1 to work)"
date: 2011-03-23
forum: Multimedia Software
---

### Post by Filip19 on 2011-03-23
Hey to all

After completing a bunch of tasks that did god knows what I am know currently hearing sound from the back-right speaker in my 5.1 system.

this is my sound card, i think:

> [FONT=Courier New]00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Micro-Star International Co., Ltd. Device 7310
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
        Subsystem: Micro-Star International Co., Ltd. Device 7310
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Micro-Star International Co., Ltd. Device 7310
        Flags: 66MHz, fast devsel, IRQ 11
        I/O ports at dc00 [SIZE=32]
        I/O ports at 5000 
        I/O ports at 6000 
        Capabilities: <access denied>
        Kernel driver in use: nForce2_smbus
        Kernel modules: i2c-nforce2

00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Micro-Star International Co., Ltd. Device 7310
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20[/SIZE][/FONT]
The volume control in the task bar serves no use. I cannot change the volume that way, therefore the "surround" preference doesn't do squat either.

A while back I was trixing with the sound. I unistalled a bunch, like alsa, and pulseaudio. Right now ALSAMIXER works for me, but I want to know how to get the 5.1 surround system to work!

another curious thing is that if I go to system -> preferences there is no SOUND option there.
Im running ubuntu 10.10 and I am a total noob. Can someone help me with this?

---

### Post by lidex on 2011-03-24
> another curious thing is that if I go to system -> preferences there is no SOUND option there.
That's because you removed pulseaudio.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Filip19 on 2011-03-25
Hmm, if i understood it right, this is what i should post here (?):

[http://www.alsa-project.org/db/?f=7c0cc3ff2b2d7439a6285b926a920dc34606ba7d](http://www.alsa-project.org/db/?f=7c0cc3ff2b2d7439a6285b926a920dc34606ba7d)

---

### Post by lidex on 2011-03-31
You're using digital or analog output?
Try going into alsamixer and change the 'Channel Mode' from 2ch to 6ch
**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by Filip19 on 2011-04-01
Digital, I think... how can I know?

I tried changing to 6ch in alsamixer, i rebooted and nothing. The problem must lie deeper than that... before I could go to preferences -> sound and check the option "5.1 surround", except then there was a horrifying echoe. I followed a guide and eventually uninstalled pulseaudio... thats why the volume control in the task bar doesnt do anything for me now.

Any more ideas? Still, thanks for the support.

---

### Post by lidex on 2011-04-01
> Digital, I think... how can I know?
Which jack(s) are you using - spdif(digital) or 1/8 inch mini-headphone(analog)? You may have removed pulse prematurely as it typically routes the signal through the various channels. With straight alsa you probably need to do some manual configuring with asound.conf

[http://alsa.opensrc.org/Intel8x0](http://alsa.opensrc.org/Intel8x0)
[http://alsa.opensrc.org/.asoundrc](http://alsa.opensrc.org/.asoundrc)
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

### Post by Filip19 on 2011-04-03
I dont have .asoundrc ! terminal cant find it, i cant find it manually when browsing through folders. 
By the way - i have an analog input, normal... you know, three jacks for the 5.1 surround. 
how do i install that .asoundrc? 
can you write me some command i can put into the terminal?

---

### Post by lidex on 2011-04-05
> **Filip19 said:**
> I dont have .asoundrc ! terminal cant find it, i cant find it manually when browsing through folders. 
By the way - i have an analog input, normal... you know, three jacks for the 5.1 surround. 
how do i install that .asoundrc? 
can you write me some command i can put into the terminal?

[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#troubles](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#troubles)

---

### Post by Filip19 on 2011-04-06
Dude, all this pages assume I have knowledge about all the files and settings. i need step by step instructions, for example: "open terminal", "search this file" "change =0 to =1". I thought having ubuntu would be easy thanks to all the support but everyone just seems to think everyone knows everything

---

### Post by lidex on 2011-04-06
If you want it to be easy re-install pulseaudio.

---

### Post by Filip19 on 2011-05-15
Seriously, can someone help me? It is said Ubuntu has such great support but Im 2 months without surround-sound... ! Ive read pulseaudio can screw with your microphone, i dont want that. Right now I only have alsa and if I change my preferences in the task bar volume control to "surround" well it doesnt do **** then.

anyone?

---

