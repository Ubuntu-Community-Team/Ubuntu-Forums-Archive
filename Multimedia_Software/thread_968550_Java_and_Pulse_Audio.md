---
title: "Java and Pulse Audio"
date: 2008-11-02
forum: Multimedia Software
---

### Post by ubun_two on 2008-11-02
I am on the new installation of Intrepid 64bit.

When I play a Java applet game on Firefox, the sound initially work, but then it just stops after a short while.  I am not playing any other software playing sound or music at this time.  

After this happens, if I try to play music through other software like Rhythmbox, I get the following message on log

pulseaudio[6618]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy
pulseaudio[7590]: alsa-util.c: Error opening PCM device hw:0: Device or resource busy

I looked around, and it seems something similar has happened with Hardy, but I haven't found any articles on this regarding Intrepid.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/226342]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/226342")
[http://ubuntuforums.org/showthread.php?t=739893]("http://ubuntuforums.org/showthread.php?t=739893")

One of the suggestion I read was to kill the pulseaudio.  I tried that.  While log no longer displayed errors, no sound came out of my speaker either.

Does anyone have any idea about getting around this?

Thanks.

---

### Post by jamesstansell on 2008-11-02
> openjdk-6 (6b12~pre2-0ubuntu2) intrepid; urgency=low

  * Fix pulse-java build failure on amd64.


Pulse support was recently added to openjdk6/icedtea6 and some 64-bit issue was fixed shortly before Intrepid was released.

Not sure though, if that's really related to your issue.

---

### Post by ubun_two on 2008-11-03
> **jamesstansell said:**
> Pulse support was recently added to openjdk6/icedtea6 and some 64-bit issue was fixed shortly before Intrepid was released.

Not sure though, if that's really related to your issue.
Is the fix in the release version of Intrepid?

---

### Post by jamesstansell on 2008-11-03
> **ubun_two said:**
> Is the fix in the release version of Intrepid?

The one I quoted is.

---

