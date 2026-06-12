---
title: "No video sound when flash is open"
date: 2008-05-02
forum: Multimedia Software
---

### Post by mistersam on 2008-05-02
If I have a website or screenlet open that uses the flash plugin with sound, my videos won't have audio. For example, if I'm at [www.slacker.com](www.slacker.com) and listen to music, pause, and open a video on my hard drive, there won't be sound. I need to navigate away from the page or close the web browser first, then re-open the video file.

---

### Post by coolen on 2008-05-02
I'm getting the same issue. It's a problem with PulseAudio. In the betas, there was apparently a plugin to allow Flash to use PA nicely, but it caused Firefox to crash periodically, and so was removed. As a result, Flash uses ALSA, and won't play nicely with PA.

There's a workaround outlined [here]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox"), but it didn't work for me.

Looking for an answer...

---

### Post by mistersam on 2008-05-02
No luck.

On the other hand, I did try it the following way:

remove the flashplugin-nonfree
install gnash and the mozilla plugin

Then it worked: I could have sound on both flash and a video. However, there are some issues with flash (cannot pause youtube video, etc..)

---

### Post by coolen on 2008-05-02
Yeah, I know I should support Gnash, but I like to be able to paus YouTube videos and be relatively sure that flash will display correctly.

That workaround was suggested for the beta, so it may have broken for the final release.

---

### Post by Zorael on 2008-05-02
Well, if ALSA is set up to use pulse as its default output device, Pulse should mix and take care of things before sending it to your chosen sink (likely speakers/headphones).

What does your /etc/asound.conf look like?
```
zorael@sunspire:/etc$ cat asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

---

### Post by Zorael on 2008-05-02
Doh, make sure the **libflashsupport** package is installed, too.
```
$ sudo aptitude install libflashsupport
```

And if the /etc/asound.conf file doesn't exist, create it with that content.

Failing that, try the instructions over at [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio). Namely, the Known Issues parts.

---

### Post by coolen on 2008-05-02
Yeah, I tried that. Firefox crashed as soon as I went to YouTube.

---

### Post by digibuy.co.uk on 2008-05-02
having exact same problems with a few of my sites!

[http://www.digibuy.co.uk/](http://www.digibuy.co.uk/)
[http://www.digibuy.us/](http://www.digibuy.us/)

---

### Post by Zorael on 2008-05-02
The libflashsupport package I'm using seems to be the one linked towards from the Perfect Setup; the amd64 one. As such my system differs from yours, if you're running i386, in which case I'm likely not much help.

[http://ubuntuforums.org/showpost.php?p=4350045&postcount=12](http://ubuntuforums.org/showpost.php?p=4350045&postcount=12)

Retracing my steps as far as I'm able. libflashsupport svn20080217 is the file from the above link.
```
zorael@sunspire:~$ apt-cache policy libflashsupport libao2 libao-pulse
libflashsupport:
  Installed: svn20080217
  Candidate: svn20080217
  Version table:
 *** svn20080217 0
        100 /var/lib/dpkg/status
     1.9-0ubuntu1 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
libao2:
  Installed: 0.8.8-3
  Candidate: 0.8.8-3
  Version table:
 *** 0.8.8-3 0
        500 http://se.archive.ubuntu.com hardy/main Packages
        100 /var/lib/dpkg/status
libao-pulse:
  Installed: 0.9.3-1
  Candidate: 0.9.3-1
  Version table:
 *** 0.9.3-1 0
        500 http://se.archive.ubuntu.com hardy/universe Packages
        100 /var/lib/dpkg/status
```
```
zorael@sunspire:~$ cat /etc/asound.conf
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
zorael@sunspire:~$ cat /etc/libao.conf
default_driver=pulse
```
You could try compiling your own libflashsupport.

---

