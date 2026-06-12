---
title: "IDJC locks up when Skype logs in"
date: 2008-06-29
forum: Multimedia Software
---

### Post by Bentai on 2008-06-29
Using the latest version of Ubuntu, IDJC 0.7.7 and Skype 2.0
My soundcard is a Soundblaster Live Value.

IDJC runs fine on it's own, it connects, streams music etc. Skype works fine on it's own. I've attempted to use the [instructions]("http://www.onlymeok.nildram.co.uk/voip.html") off the IDJC site to allow me to use Skype/Teamspeak on IDJC. Jack has been fully installed, and I tried two kinds of code in the ~/.asoundrc file:
```
pcm.idjcvoip {
type plug
slave { pcm "idjcjack" }
}
pcm.idjcjack {
type jack
playback_ports {
0 idjc-mx:voip_recv_lt
1 idjc-mx:voip_recv_rt
}
capture_ports {
0 idjc-mx:voip_send_lt
1 idjc-mx:voip_send_rt
}
}
```

And type two:
```
pcm.idjcvoip {
   type plug
   slave.pcm {
      type jack
      playback_ports {
         0 idjc-mx:voip_recv_lt
         1 idjc-mx:voip_recv_rt
      }
      capture_ports {
         0 idjc-mx:voip_send_lt
         1 idjc-mx:voip_send_rt
      }
   }
}
```
When I log into Skype, IDJC locks up. I've tried running it from terminal to see if any errors are generated there but I get nothing. There really seems to be no reason why the program locks up and I am at a loss. Any help? :)

---

### Post by Bentai on 2008-06-30
Daytime *bump*

---

### Post by StephenF on 2008-06-30
You also need alsa-plugins installed (the Ubuntu package name may vary) but I believe the version supplied with Ubuntu and not installed by default is still not capable of interfacing with JACK. Consequently the virtual device will not work. This leaves you stuck with the task of compiling your own.

---

### Post by Bentai on 2008-06-30
Ah yes, I had installed 'libasound-plugin' from the package manager to no avail. I'll see about uninstalling that version and do a fresh outside compile.

---

