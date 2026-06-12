---
title: "sound system stops working"
date: 2009-04-26
forum: Multimedia Software
---

### Post by sawatdee on 2009-04-26
My sound system stops working after a day or two, unless I reboot. I use my sound system for playing CDs, playing sounds over the Internet (like youtube), and other applications that play sounds. When I run one of these applications, then I can no longer play sounds from the others. For example, today I rebooted my system. I was using the gxine firefox plugin to listen to Internet radio, then I played a youtube video. After that I could no longer play the Internet radio station I had been listening to. I suspect the apps are not releasing the sound system when they are done using it or something. Is there any way to reset the sound system in ubuntu without rebooting the entire system? Or better yet, is there a way I get make sure the sound system is available to all apps if none is using it?

---

### Post by markbuntu on 2009-04-26
It seems you have two separate problems. You can fix the second one here

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)


The first problem, your sound failing after some time is an ongoing problem that can only be fixed with a alsa driver/kernel update. Hopefully that will come soon. In the meantime you can do this to restore your sound and avoid rebooting.

Close all your sound using applications.

In a terminal:

```

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

```

---

### Post by sawatdee on 2009-04-27
Well, pulseaudio seems to be garbage. I installed it as the directions said at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio), and now I can't play CDs and any time I try to play a youtube video, firefox dies, it disappears completely. Now I have to figure out how to uninstall that garbage and get my system back to the way it was when the sound almost worked.

---

### Post by boglio on 2009-04-27
I'm always use alsa for everything, pulseaudio just fails horribly in my experience.

---

### Post by markbuntu on 2009-04-28
The problems with pulseaudio are due to the continuing faulty implementation in Ubuntu. This is not a pulseaudio problem, it is a Ubuntu problem. That said, if you do take the few minutes to set it up properly it works just fine and does many things that are impossible with ALSA or OSS.

I cannot vouch for any directions other than the one below which are very specific to the various Ubuntu distros that include Pulseaudio. 

If you are using Hardy 8.04 or Intrepid 8.10

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you are using Jaunty 9.04

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

If you are using KDE4.x or Kubuntu 8.10 or 9.04 and want to use pulseaudio with it.

[http://ubuntuforums.org/showthread.php?t=1055591](http://ubuntuforums.org/showthread.php?t=1055591)

These have been used by thousands of people to get their sound working properly.


sawatdee,
That wiki has not been updated in over a year and much has changed. Please follow one of the links above to get your sound working properly. If you are actually using Gutsy 7.10. you should probably upgrade to 8.04 because 7.10 is reaching the end of its supported life.

---

