---
title: "Am I screwed for sound?"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by Visceral Monkey on 2008-01-18
I have two sound sources. One is an X-Fi card, which I know has beta drivers for the 64 bit machines, but no 5.1 support. (I *am* running 64 bit)

The other is the Karajan sound module on my dfi ultra d.

[PHP]14: PCI 04.0: 0401 Multimedia audio controller                  
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10de_59
  Unique ID: 8otl.dHipVU0XmF1
  SysFS ID: /devices/pci0000:00/0000:00:04.0
  SysFS BusID: 0000:00:04.0
  Hardware Class: sound
  Model: "nVidia CK804 AC'97 Audio Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x0059 "CK804 AC'97 Audio Controller"
  SubVendor: pci 0x10de "nVidia Corporation"
  SubDevice: pci 0xcb84 
  Revision: 0xa2
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  I/O Ports: 0xf000-0xf0ff (rw)
  I/O Ports: 0xec00-0xecff (rw)
  Memory Range: 0xfe02d000-0xfe02dfff (rw,non-prefetchable)
  IRQ: 22 (1199 events)
  Module Alias: "pci:v000010DEd00000059sv000010DEsd0000CB84bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unkno[/PHP]

No matter what I do, for the life of me I can't get any sound using the Karajan module. Nothing. I'm afraid the X-Fi driver would be usless be cause it doesnt offer 5.1 sound and I have everything going through my stereo via 5.1ch input.

Does anyone have any idea how to get the Karajan sound module working in Ubuntu 64? If I can't fix it, I'll have to give up on Ubuntu as I need sound..

This is on Gutsy x86-64 btw.
Now, when I plug in my old creature speakers (just two little white speakers and freaky looking sub) I *do* get sound, but not when trying to use it via my stereo via 5.1, which I'm pretty sure the Karjan can output.

---

### Post by Visceral Monkey on 2008-01-20
Lots of work for a simple fix. Turns our you just need the linux driver here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false)

It's installs and configures everything for you. You must have the jumpers on the side of the sound module set to the original settings (blue covers over jumpers 5 and 6 and 9 and 10), you must NOT have sound plugged into the front of the motherboard and for 5.1 you use the center and rear channel plus and BELOW that you use the green plug named "front".

---

### Post by rosegarden78 on 2008-01-20
Audacity for sound and Rosegarden for music studio are what I'm using - and Fluidsynth to load sound founts for MIDI.  You have to load fluidsynth and sound fonts by hand last time I checked but they rock!  Hammer Sound website has nice free sound fonts.  They come with free cinematic scores in MIDI format for demo purposes.  I love my Linux music studio.

---

