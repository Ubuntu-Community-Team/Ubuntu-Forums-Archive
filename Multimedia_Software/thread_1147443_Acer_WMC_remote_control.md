---
title: "Acer WMC remote control"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Pedro Villarroel on 2009-05-03
is there a way to use my windows media center remote control (it came with my acer portatil) in Ubuntu?
i instaled a media center aplication alrady.

i hope there is a way, the remote control is the last thing that makes me restart to windows:S we use ir a lot ...

thans in advance

Pedro Villarroel

PD: sorry for my bad english...

---

### Post by xc3RnbFO8P on 2009-05-03
First type **irw** in Terminal and try the remote.

---

### Post by Pedro Villarroel on 2009-05-03
nothing happends... :(

---

### Post by xc3RnbFO8P on 2009-05-03
In Synaptic Package Manager install:
lirc
lirc-modules-source
lirc-x

and restart the computer

---

### Post by Pedro Villarroel on 2009-05-03
done, what do i do now?
:)

---

### Post by xc3RnbFO8P on 2009-05-03
Do **irw** in Terminal and try again.

---

### Post by Pedro Villarroel on 2009-05-03
the same, nothing happend, the console is like waiting but nothing hapends...

---

### Post by xc3RnbFO8P on 2009-05-03
Do **dmesg** in Terminal
look for something like this:
> 12.267150] lirc_???: ??? remote driver for LIRC $Revision: 1.71 $ 

---

### Post by Pedro Villarroel on 2009-05-03
i have to go out :( wife needs me, ill guess ill try again tomorrow, tanks a lot for the help...

---

### Post by Pedro Villarroel on 2009-05-05
is this what u asked me for?

[   25.812606] lirc_dev: IR Remote Control driver registered, major 61 
[   25.830118] 
[   25.830120] lirc_mceusb2: Philips eHome USB IR Transceiver and Microsoft MCE 2005 Remote Control driver for LIRC $Revision: 1.44 $
[   25.830123] lirc_mceusb2: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>

---

### Post by xc3RnbFO8P on 2009-05-05
This what I get:
> rig@rig-desktop:~$ irw
67 0 KEY_UP event5
^[[A69 0 KEY_LEFT event5
^[[D73 0 KEY_VOLUMEUP event5
72 0 KEY_VOLUMEDOWN event5
192 0 KEY_CHANNELUP event5
193 0 KEY_CHANNELDOWN event5
> sudo /etc/init.d/lirc restart
and **irw** again try the remote

---

