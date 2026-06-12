---
title: "Leadtek WinFast DVT200H USB TV Tuner"
date: 2008-10-22
forum: Multimedia Software
---

### Post by passbe on 2008-10-22
Another TV tuner problem :P

I have just purchased a Leadtek WinFast DVT200H USB TV Tuner ([http://www.leadtek.com/eng/tv_tuner/overview.asp?pronameid=413](http://www.leadtek.com/eng/tv_tuner/overview.asp?pronameid=413)).

Dmesg and Lsmod show they recognize the USB device but it doesn't load a module, i have tried inserting cx88-dvb into /etc/modules, it seems to load

```

cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
cx88/2: cx2388x dvb driver version 0.0.6 loaded
cx88/2: registering cx8802 driver, type: dvb access: shared

```

 but tvtime and kaffeine don't seem to see the device (both complain about no /dev/video0). I'm not looking for a how to guide, more just advice on where to go from here. 

Thank you.

---

### Post by passbe on 2008-10-22
still no luck, however upon connecting the device i do see Leadtek appear with the command lsusb.

---

