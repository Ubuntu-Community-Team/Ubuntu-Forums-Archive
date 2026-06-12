---
title: "Change LIRC boot parameters &amp; USB reciever mounting"
date: 2008-04-17
forum: Multimedia &amp; Video
---

### Post by Vonagio on 2008-04-17
I have Mythbuntu 7.10 working perfectly with my IR remote control...

Only after restarting LIRC with different parameters once the GUI has loaded. I stop lirc (usually by running irw, which crashes it!), then start it with this:

```
sudo lircd --device=/dev/lirc0 --output=/dev/lircd
```

This points lirc at the correct device.

I don't know how to make the lirc service load like this during boot, is it possible? If not how do i run a startup script to make the service stop and reload?

Also, every time i start up the machine the USB ir reciever doesnt connect/power on, how do I make it load/mount on boot?

Thanks, Von

---

### Post by Vonagio on 2008-04-19
I'm still non the wiser about changing the startup command for lirc, I don't know how services are started, does a command run (i.e. are the commands "lircd" or "gdm" or "mythbackend" done when the OS starts up?), and is it possible to change these?

If anyone has any info or further reading on system startup that might help me.

Thanks, Von

---

### Post by Vonagio on 2008-04-20
I've managed to fix lirc now, i ended up changing the lirc settings in /etc/lirc/hardware.conf.

However, I am still at a loss with the ir receiver problem. Whenever the system is booted, the receiver is off (the green light that signals 'on' isn't lit), I simply reinsert the usb plug and restart mythfrontend to get it to work...

Any ideas why the usb device isn't loaded/mounted?

---

