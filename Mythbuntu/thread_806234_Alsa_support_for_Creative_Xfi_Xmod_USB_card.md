---
title: "Alsa support for Creative Xfi Xmod USB card"
date: 2008-05-24
forum: Mythbuntu
---

### Post by ebike on 2008-05-24
Hi There all,

I have a Mythbuntu box currently running Gutsy quite happily with the above sound card (which is awesome by the way.)

I notice however that there is no driver support for this card in Hardy Heron. I would like to make the change to Hardy but am reluctant to do so without support for this card.

My current choices are:
1. Use the OSS4.0 drivers and ditch Alsa completely 
(By the way has anyone done this in mythbuntu, could do with some feedback.
2. Wait for Alsa support


Any and all help appreciated as allways.

---

### Post by ebike on 2008-06-08
Thanks for all the replies folks! :rolleyes:

Actually I am marking this thread as solved, as since the latest update of the kernel "2.6.24-18-generic" the ALSA driver is again working for this card ..... :frown:bad boys for breaking Ubuntu, and taking so long to come up with a fix  ......:shock:

---

### Post by halfex on 2008-06-14
I have one too, and Ubuntu Hardy with unmodified alsa and kernel configs.

It works for me, but I have a weird problem. When I try to set Mmod's PCM volume (with gnome-volume-control), it goes totally down, the channel lock breaks, and sometimes the device go to muted. I have to play with left channel's volume to make it audible and play with right to stereo. But the left volume is jump down usually, when I slide right fader up :(

Have anyone got this problem too?

---

### Post by halfex on 2008-06-14
-

---

### Post by ebike on 2008-06-14
Yep, I sorta have that problem, but mainly when watching movies with VLC, LiveTV or recordings are normally fine. When I startup a movie, the PWM slide goes to nearly zero, and I can only crank it up to half in VLC. I have to use alsamixer to crank up the PWM sliders so I can get some decent volume ...

---

### Post by shlag on 2008-06-26
> **halfex said:**
> 
It works for me, but I have a weird problem. When I try to set Mmod's PCM volume (with gnome-volume-control), it goes totally down, the channel lock breaks, and sometimes the device go to muted. I have to play with left channel's volume to make it audible and play with right to stereo. But the left volume is jump down usually, when I slide right fader up :(

Have anyone got this problem too?

This is problem in gnome-volume-control.
My xfce4-mixer works well.

But i use hardware volume control with xbindkeys.

xbindkeys config (~/.xbindkeysrc):

"amixer -c 0 get PCM | grep off > /dev/null; if [ $? =  1 ]; then amixer -q -c 0 set PCM mute; else amixer -q -c 0 set PCM unmute; fi;"
  m:0x10 + c:160

"pgrep amixer; if [ $? = 1 ]; then amixer -c 0 set PCM 3dB+; fi;"
  m:0x10 + c:176

"pgrep amixer; if [ $? = 1 ]; then amixer -c 0 set PCM 3dB-; fi;"
  m:0x10 + c:174
	
do not forget to add xbindkeys to autoload of your DE

---

### Post by mndar on 2009-01-14
Does the volume knob on the device work?
What about the digital out and other outputs ?

---

### Post by mndar on 2009-02-25
I bought the USB X-Fi. Its working well with ALSA using the snd-usb-audio module. Have a look here [http://mndar.phpnet.us/usbxfi](http://mndar.phpnet.us/usbxfi)

---

### Post by ceminino on 2010-02-17
> **mndar said:**
> I bought the USB X-Fi. Its working well with ALSA using the snd-usb-audio module. Have a look here [http://mndar.phpnet.us/usbxfi](http://mndar.phpnet.us/usbxfi)


how do you compile this module? 
it seems surround works with this driver and not with the default alsa driver on karmic (snd-usb-audio), 

lsmod  output of alsa driver:

AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0603 Line Connector
        bAssocTerminal          0
        bNrChannels             2
        wChannelConfig     0x0003
          Left Front (L)
          Right Front (R)
        iChannelNames           0 
        iTerminal               0 


lsmod output reported on [http://mndar.phpnet.us/usbxfi](http://mndar.phpnet.us/usbxfi)

AudioControl Interface Descriptor:
        bLength                12
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bNrChannels             6
        wChannelConfig     0x003f
          Left Front (L)
          Right Front (R)
          Center Front (C)
          Low Freqency Enhancement (LFE)
          Left Surround (LS)
          Right Surround (RS)
        iChannelNames           0 
        iTerminal               0

---

