---
title: "gpsk31 will not start"
date: 2015-01-17
forum: Multimedia Software
---

### Post by janl162 on 2015-01-17
I just installed gpsk31 from the software center, and it will not start. I'm running 64 bit Ubuntu 14.04 LTS.

Click the icon and nothing happens, so I tried running it from the terminal and got the following error message:

init_audio: can't open /dev/dsp
Hint: you might want to try to load snd_pcm_oss kernel module
Cannot initialize audio device: /dev/dsp -1

Seems like OSS has long since been depreciated. Is there a way to make it work with the standard pulse audio?

---

### Post by Yellow Pasque on 2015-01-17
Try this:
```
sudo apt-get install pulseaudio-utils
padsp gpsk31
```

---

### Post by janl162 on 2015-01-17
That brought about progress. 

Pulse audio-utils was already installed, 

sudo padsp gpsk31  got the user interface to open, but it still threw this error:

(gpsk31:9022): IBUS-WARNING **: The owner of /home/janet/.config/ibus/bus is not root!
Cannot open PTT device /dev/ttyS1: Input/output error

Seems like /dev/ttyS1 is a RS232 serial port. . . and my laptop has no traditional RS232 serial ports. . .

Thanks.

---

### Post by Yellow Pasque on 2015-01-17
What happens if you try running without sudo?
```
padsp gpsk31
```

I don't have a serial port either, but I still have /dev/ttyS1 and the program runs for me.

---

### Post by janl162 on 2015-01-18
The user interface opens, but it throws this error:

Cannot open PTT device /dev/ttyS1: Permission denied

Essentially the same error.

---

### Post by Yellow Pasque on 2015-01-18
You can try putting your user in the "dialout" group (in /etc/group file) to give permission.

---

### Post by janl162 on 2015-01-18
That might have solved it. Maybe. It's still throwing the error message about /dev/ttyS1 though.

---

### Post by steeldriver on 2015-01-18
What PTT device do you have? do you have a driver for it? is the system recognising it - does it show up in /var/log/syslog when you plug it in?

---

