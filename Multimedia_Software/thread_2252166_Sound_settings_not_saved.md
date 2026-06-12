---
title: "Sound settings not saved"
date: 2014-11-09
forum: Multimedia Software
---

### Post by bobptz on 2014-11-09
In Sound Settings, whenever I set my input to  "Microphone (built in audio)" and then I close the window, it goes back to "Digital  input (S/PDIF)".  I do not need to reboot for this to happen.  This happens only for the input tab, for the output works  fine.

The problem is displayed perfectly on this video:  [https://www.youtube.com/watch?v=U8ObMRANL3A](https://www.youtube.com/watch?v=U8ObMRANL3A)

It is the same problem reported here:  [http://askubuntu.com/questions/459479/sound-settings-not-saved](http://askubuntu.com/questions/459479/sound-settings-not-saved).  I tried the solution (installed pavucontrol), but in my case it did not help.

I have ubuntu 14.04 64 bit.  I have a Logitech C920 webcam with builtin microphone.  This is the S/PDIF entry that gets selected all the time.

update:
1) The settings are lost when I REOPEN the Sound Settings.  As long as they are closed the microphone works ok.
2) I did a "tail -f /var/log/syslog" to monitor opening/closing the sound settings.  Nothing changed in the system log.

---

### Post by Jim_Menegay on 2014-11-12
I found this: [https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1](https://launchpad.net/ubuntu/+source/unity-control-center/14.04.3+14.04.20140922-0ubuntu1)
Looks like a fix, but haven't tried it.

---

### Post by bobptz on 2014-11-15
I did look at it several times.  I could not understand what I was supposed to do.

This issue is a confirmed bug, many people have complained:  
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1334329](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1334329)

---

