---
title: "Ubuntu forgets my TV Tuner Card on Reboot!"
date: 2009-04-13
forum: Multimedia Software
---

### Post by sikander3786 on 2009-04-13
I have got a cheap Elite TV Tuner Card with saa7130 chip on it. I made it work under ubuntu after indefinite tries by using these commands.

sudo modprobe -vr saa7134_dvb
sudo modprobe -vr saa7134_alsa
sudo modprobe -vr saa7134
sudo modprobe -v saa7134 card=21

Now the problem is that when i reboot my computer, i have to re-enter these commands in the terminal to get my card working. Otherwise TV Time (the software i use for watching TV) can't capture even a single channel. So how can i make these changes permanent so that i don't have to re-enter my card no. every time i reboot.
Thanks

---

### Post by cariboo on 2009-04-13
I have to add the following file to /etc/modprobe.d:

```
alias char-major-81 videodev
alias char-major-81-0 saa7134
options saa7134 card=17
```

The file is named saa7134, and I just copy it to the above mentioned directory every time I do a reinstall. You would of course have to change the card number.

Once I have copied the file I just reload the modules and it works the way it should.

Jim

---

