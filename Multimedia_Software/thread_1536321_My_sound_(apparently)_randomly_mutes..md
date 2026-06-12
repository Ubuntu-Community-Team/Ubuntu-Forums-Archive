---
title: "My sound (apparently) randomly mutes."
date: 2010-07-22
forum: Multimedia Software
---

### Post by jpmelos on 2010-07-22
Hello, people.

I'm using Ubuntu 10.04 up-to-date in my laptop HP Pavilion dv4-1290br.

My sound seems to randomly get muted, after a few hours the laptop is on. I've checked the volumes, I've compiled and installed the very latest ALSA driver, tested it trying to play music and changing the volume in hardware and software. Nothing works. The sound simply gets muted until I reboot.

Any help is very appreciated. Thank you.

---

### Post by lidex on 2010-07-23
Remove any conflicting sound config files:
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**
Now this. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

