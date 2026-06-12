---
title: "help getting kworld remote working (no keymap)"
date: 2012-02-19
forum: Multimedia Software
---

### Post by superfrank on 2012-02-19
Hi, I have recently installed a kworld pc160-2t pci dvb-t tuner which is based on the af9015 chipset. I have got this working with one tuner so far, as the second tuner is unreliable due to a driver issue. I haven't got anything out of the remote yet, and in fact I can see with dmesg that no keymap is installed at boot time.  

```
[   31.058541] Registered IR keymap rc-empty 
[   31.058604] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/usb3/3-1/rc/rc0/input4 
[   31.058713] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:1e.0/0000:05:01.2/usb3/3-1/rc/rc0 
[   31.058716] dvb-usb: schedule remote query interval to 500 msecs.  
```

I have tried cat /dev/input/event4 and this never displays anything when I press a button (and I have tested the batteries in the remote with a voltmeter).   I'm not sure whether I should expect to see anything for unrecognised keycodes though. How should I go about finding an appropriate keymap for my remote? Or alternatively getting access to whatever the remote control transmits and making my own keymap?

edit: I have successfully received events by closing X/mythtv and using evtest. I guess I need to make myself a keymap from this now.

---

### Post by superfrank on 2012-02-19
I have managed to get the remote working now - I had to create my own keymap and install it manually (details here for anyone that's interested: [http://francisfisher.me.uk/problem/2012/kworld-pc160-2t-remote-control-on-ubuntu-linux-11-10-2/](http://francisfisher.me.uk/problem/2012/kworld-pc160-2t-remote-control-on-ubuntu-linux-11-10-2/)).

I have a further question - how do I find out what I need to put into /etc/rc_maps.cfg to make my keymap load? i.e. what is the name of the driver or table I need to use?

---

### Post by superfrank on 2012-02-20
so it turns out that this was what I needed to force load a custom keymap for the driver:

af9015	*	/etc/rc_keymaps/kworld_pc160-2t

Next step, I need to make a patch for the kernel that will include this keymap and automatically associate it with the hardware.

---

