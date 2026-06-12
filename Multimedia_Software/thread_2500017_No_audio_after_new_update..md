---
title: "No audio after new update."
date: 2024-08-18
forum: Multimedia Software
---

### Post by Kermilli on 2024-08-18
Hi,
                  []("https://askubuntu.com/posts/1523793/timeline")  
          
                                        I recently installed the new updates and after restarting I don't have audio anymore.

 
This is my alsa log

 [http://alsa-project.org/db/?f=2fc34b761ef5f3f91cb250c90f3c19829b7bdc8c](http://alsa-project.org/db/?f=2fc34b761ef5f3f91cb250c90f3c19829b7bdc8c)

 
I followed sound troubleshooting from this page up to step 7 ,  because It looks like it might not help if I try further and I might be  better off with a fresh install. [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

 
Here are my Alsa Mixer Screenshot and pavucontrol screenshots.

 [URL="https://ibb.co/BCYtyjb"]
https://ibb.co/BCYtyjb[/URL] [URL="https://ibb.co/yP2ZxH2"]
https://ibb.co/yP2ZxH2[/URL]

 
What Should I do?

 Thanks!

---

### Post by Yellow Pasque on 2024-08-21
Did you do a cold boot, or have you only restarted since applying update?
The analog device is not showing up in aplay (only HDMI audio). You should have an alc3226 device like this in aplay:
```
card 1: PCH [HDA Intel PCH], device 0: ALC3226 Analog [ALC3226 Analog]
```

Unfortunately, alsainfo doesn't seem to grab dmesg info anymore. Can you give output of:
```
journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"
```

---

