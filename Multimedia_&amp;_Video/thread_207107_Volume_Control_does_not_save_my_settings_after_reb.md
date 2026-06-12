---
title: "Volume Control does not save my settings after reboot"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by xpix on 2006-07-01
Hello,

I would like Volume Control to remember the settings I make for the MASTER.
For example I am unlinking the 2 Channels and lower the volume for the right channel.

Everything is OK until I reboot. After reboot the Channels are linked and have the same volume.

Any ideas on how to make Ubuntu to remember my settings?

Other Info:
Used Device:Via 8235(Alsa Mixer)

PS: Any ideas are welcomed as I am not afraid to do some coding(hacking :))

Thx

---

### Post by LordRaiden on 2006-07-02
I had the same trouble before (same card), but I can't remember exactly how I fixed it. Go to /etc/ and look for something like asound.conf (or something with asound in the name). Delete the file if you find it. Then go to alsamixer and set your volume settings as desired. Finally, do the following ```
sudo alsactl store 0
``` Tell me if that works for you and I'll add it to my guide below.

---

### Post by xpix on 2006-07-03
Thx, LordRaiden

I will try and get back to you if it works

---

### Post by xpix on 2006-07-04
[QUOTE=LordRaiden]I had the same trouble before (same card), but I can't remember exactly how I fixed it. Go to /etc/ and look for something like asound.conf (or something with asound in the name). Delete the file if you find it. Then go to alsamixer and set your volume settings as desired. Finally, do the following ```
sudo alsactl store 0
``` Tell me if that works for you and I'll add it to my guide below.[/QUOTE]

I could not find any asound.com in the etc folder but I did ```
sudo alsactl store 0
``` and it saved my settings.

Thx LordRaiden \\:D/

---

### Post by vhof on 2007-10-15
Worked for me *but* only partially. 
There are controls which are not restored like microphone's volume/capture, and settings like Duplicate Front...
[B]
UPDATE: Installing Gutsy solved all of these problems.[/B]

---

### Post by matthewcraig on 2007-11-23
The file you are thinking about is not in /etc

Actually the file is /var/lib/alsa/asound.state

ALSA can get into a confused state even in Gutsy, so wanted to update thread.

---

### Post by mac-duff on 2008-01-02
Hi,
well, I have deleted the file asound.state in/var/lib/alsa/asound.state as well as in etc and run the command: sudo alsactl store 0 but still have the problem that my soundsettings will not be saved after a rebbot.
Does anybody has a further tip? I am using Ubuntu 7.10

thx

---

### Post by _godbout_ on 2008-03-12
Same problem here, but on Hardy.
Any idea?

---

### Post by stumpalump on 2008-04-02
Same problem here. Alsamixer won't keep my settings on reboot regardless of doing alsactl store.

If it helps any, I tried installing OSS beta for my xfi and had to remove it completely and reinstall Alsa from a fresh kernel to get to this point. Sound works now but alsamixer settings won't save.

Lord..... if ya list'nin...... HELLP!

---

### Post by JedV on 2008-05-02
I'm also experiencing this in Hardy (AMD64).  Any help?

---

### Post by jmandawg on 2008-05-16
Same thing here in xfce4-mixer on hardy AMD64.

---

### Post by MattThLinuxNewb on 2008-05-18
I'm also having this problem after upgrading to Hardy from Gutsy (My master volume resets back to 80% every time I reboot). This didn't happen for me in any previous Ubuntu versions. Is this Hardy bug documented elsewhere?

---

### Post by toumpas on 2008-07-10
It looks like the "external amplifier" auto-enabled switch is a common problem. 

In my case it looks like its enabled (because i only get sound through the phone jack on my laptop) but there is no GUI switch or CLI switch is Alsamixer... Thus i cant disable it.. 

Any walkthrough please?:popcorn:

---

### Post by Derviansoul on 2008-07-21
Hello

i recompiled the drivers a few days ago, and i tried to store the mixer settings with ```
sudo alsactl store 0
``` but when i restart it's settings are back to normal, i have to do everytime after ```
sudo alsactl restore
```

anyone knows why isn't alsa loading the settings from the alsactl at the startup, i gess a simple script to load those setting wont do any harm but doesn't seem right to me:S

any ideas?
regards

---

