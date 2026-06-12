---
title: "ThinkPad T530 combo jack problem, microphone not working."
date: 2013-04-02
forum: Multimedia Software
---

### Post by darkone24.7 on 2013-04-02
Hi all,
I am having a problem with Lenovo ThinkPad T530 laptop 

00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
01:00.1 Audio device: nVidia Corporation GF108 High Definition Audio Controller (rev a1)

The problem is that only input device I can use is built in microphone. When I connect headset to 3.5 inch combo jack microphone on headset isn't working. Built in microphone is still active. So there is no audio input at combo jack and there is audio input on built in microphone. I am a Linux noob and I have no idea how to fix the problem. Thank you in advance for any help.

---

### Post by Kirboosy on 2013-04-02
Hi! I had a similar problem with my Dell Duo but I believe it uses a similar chipset. Try the following command

[FONT=Verdana]Run the following command into a Terminal
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
``` 
At the very bottom of the file add the following line.
```
options snd-hda-intel model=ideapad
```

Save and close the file, REBOOT! Hopefully that solves the problem.

I am taking a stab in the dark on this one. If that doesn't fix it I would undo the changes above and hopefully someone else knows the solution. :)

~Caboose

[/FONT]

---

