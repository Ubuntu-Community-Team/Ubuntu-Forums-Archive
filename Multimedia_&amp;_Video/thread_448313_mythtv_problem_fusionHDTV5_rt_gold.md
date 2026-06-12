---
title: "mythtv problem fusionHDTV5 rt gold"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by Brian_alvarez on 2007-05-19
I just installed mythtv using the instruction here: [https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty) but I can't seem to get my FusionHDTV5 rt gold to work. When I tell myth to search for channels it doesn't find anything (nor does it show any signal strength). I was under the impression that card needs to be setup as a dvb dtv capture card but myth doesn't seem to see the card under that setting.  I also tried setting it up as a pcHDTV DTV capture card (w/v4l drivers) myth seems to recognize the card under this setting, but it still won't detect channels or any signal strength.  I haven't set up any drivers for the card because I was under the impression that ubuntu recognizes it straight out the box.  I'm a bit of an linux newb (jsut started about 3 weeks ago). Any help would be greatly appriciated :)

---

### Post by newlinux on 2007-05-19
did you load the cx88_dvb, cx88_alsa, and cx8800 modules. 

It should be set up as a dvb card after loading those modules. What types of channels are scanning for (QAM,ATSC)? What are your scan settings.

[http://www.mythtv.org/wiki/index.php/DVICO_FusionHDTV5_Gold](http://www.mythtv.org/wiki/index.php/DVICO_FusionHDTV5_Gold)

---

### Post by Brian_alvarez on 2007-05-19
I'm not sure I understand how to load those modules. I'm sort of new and the link doesn't really give commands.  I was looking in my hardware info panel and it looks like it sees the card. here's sort of what it looks like.

     CX23880/1/2/3 PCI Video and Audio Decoder
               video device
               video device
     CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
                cx88 digital ALSA Capture Device
                Conexant CX8801 ALSA Control Device
                Conexant CX8801 OSS Control Device
                Conexant CX8801 OSS PCM Device
                Conexant CX8801 OSS PCM Device
     CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]

other info: running feisty fawn (kernal 2.6.20-15-generic)
capturing video form a cable signal in the U.S both digital and ntsc

I also found this link [http://linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x](http://linuxtv.org/v4lwiki/index.php/Cx88_devices_(cx2388x))
But I'm not sure how to  compile a custome kernel or if I really need to.

B

---

### Post by newlinux on 2007-05-19
to load modules temporarilly use modprobe, e.g.

```

sudo modprobe cx88-dvb

```

If it loads the module successfully it will just return the command prompt with no message.
You shouldn't need a custom kernel. And you will be using DVB drivers if you want digital stations (analog stations should work out of the box in Feisty). V4L is what you would use if you only wanted analog.

after loading the modules take a look at the output of the command:

dmesg


And post the results and the scan settings you are using in myth if you still having problems. If you are still having problems, also try using:

tvtime

and let us know if you get any analog stations with that. 

I have the Fusion 5 RT Lite - and analog worked out of the box, but I still had to load cx88-dvb to get digital to work.

---

### Post by Brian_alvarez on 2007-05-20
Well I was sort of able to get myth going I have digital channels in myth but no sound.  I was also able to get analog channels with tvtime(also no sound).  Do I need to set up analog like it's a whole separate card?
thanks for all your help so far.

[PHP][ 6349.218313] cx88[0]: video y / packed - dma channel status dump
[ 6349.218330] cx88[0]:   cmds: initial risc: 0x0e962000
[ 6349.218334] cx88[0]:   cmds: cdt base    : 0x00180440
[ 6349.218337] cx88[0]:   cmds: cdt size    : 0x0000000c
[ 6349.218341] cx88[0]:   cmds: iq base     : 0x00180400
[ 6349.218344] cx88[0]:   cmds: iq size     : 0x00000010
[ 6349.218348] cx88[0]:   cmds: risc pc     : 0x15af2a48
[ 6349.218351] cx88[0]:   cmds: iq wr ptr   : 0x0000010c
[ 6349.218355] cx88[0]:   cmds: iq rd ptr   : 0x00000100
[ 6349.218358] cx88[0]:   cmds: cdt current : 0x00000458
[ 6349.218362] cx88[0]:   cmds: pci target  : 0x051d2660
[ 6349.218365] cx88[0]:   cmds: line / byte : 0x00f00000
[ 6349.218369] cx88[0]:   risc0: 0x80008200 [ sync resync count=512 ]
[ 6349.218376] cx88[0]:   risc1: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218383] cx88[0]:   risc2: 0x0e5a05a0 [ INVALID sol eol irq2 22 20 19 cnt1 count=1440 ]
[ 6349.218392] cx88[0]:   risc3: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218398] cx88[0]:   iq 0: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218406] cx88[0]:   iq 1: 0x0e5a05a0 [ arg #1 ]
[ 6349.218409] cx88[0]:   iq 2: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218416] cx88[0]:   iq 3: 0x0e5a10e0 [ arg #1 ]
[ 6349.218419] cx88[0]:   iq 4: 0x180003e0 [ write sol count=992 ]
[ 6349.218425] cx88[0]:   iq 5: 0x0e5a1c20 [ arg #1 ]
[ 6349.218428] cx88[0]:   iq 6: 0x140001c0 [ write eol count=448 ]
[ 6349.218434] cx88[0]:   iq 7: 0x12cf8000 [ arg #1 ]
[ 6349.218437] cx88[0]:   iq 8: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218444] cx88[0]:   iq 9: 0x12cf8760 [ arg #1 ]
[ 6349.218447] cx88[0]:   iq a: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218454] cx88[0]:   iq b: 0x12cf92a0 [ arg #1 ]
[ 6349.218457] cx88[0]:   iq c: 0x04d9f580 [ INVALID eol 23 22 20 19 cnt0 resync 14 13 12 count=1408 ]
[ 6349.218468] cx88[0]:   iq d: 0x1c0005a0 [ write sol eol count=1440 ]
[ 6349.218474] cx88[0]:   iq e: 0x051d20c0 [ arg #1 ]
[ 6349.218477] cx88[0]:   iq f: 0x80008200 [ sync resync count=512 ]
[ 6349.218483] cx88[0]: fifo: 0x00180c00 -> 0x183400
[ 6349.218485] cx88[0]: ctrl: 0x00180400 -> 0x180460
[ 6349.218489] cx88[0]:   ptr1_reg: 0x00182280
[ 6349.218492] cx88[0]:   ptr2_reg: 0x00180488
[ 6349.218495] cx88[0]:   cnt1_reg: 0x00000000
[ 6349.218498] cx88[0]:   cnt2_reg: 0x00000000
[ 6349.218507] cx88[0]/0: [c2104480/2] timeout - dma=0x15af2000
[ 6349.218510] cx88[0]/0: [c2104980/3] timeout - dma=0x1f0f2000
[/PHP]

---

### Post by newlinux on 2007-05-20
You shouldn't add it as a separate card to get analog. In the Capture card initial setup screen there is an analog options button, where you setup the analog portion of the card. Then define an analog video source and assign it to the V4L television input. This is detailed in mythtv-setup portion of the link I provided above. There is also a little glitch that happens too, which is in there as well (and I get this glitch, but it doesn't affect recordings). I don't lose sound however...

Usually when analog and digital sound don't work something is muted. take a look at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) to troubleshoot.

I had problems with analog sound, but not digital. I had to use an internal jumper cable to the sound card, and then set that input as the capture input in alsamixer. Then everything worked.

---

### Post by newlinux on 2007-05-20
oh, and you will need to put cx88-dvb in your /etc/modules file so that it will load everytime you reboot.

```

gksudo gedit /etc/modules

```
put cx88-dvb at the end of the file.

---

### Post by newlinux on 2007-05-20
sorry, one more thing. Did you load the cx88_alsa module? If not you may need this for digital sound:

```

sudo modprobe cx88_alsa

```

you may need to load cx8800 module too.

And if these work, you'll want to put these in /etc/modules too.

---

### Post by strat_53711 on 2007-08-05
I tried loading the cx88-dvb drivers and get a "No such device".

The Lite card is based on the BT878.

The Gold card based on the CX23882.

???

---

