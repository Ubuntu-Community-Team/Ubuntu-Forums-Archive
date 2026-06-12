---
title: "Native VNC Resolution Issue"
date: 2008-03-11
forum: Mythbuntu
---

### Post by thatkidandy on 2008-03-11
Trying to connect to my box via VNC (via vncserver set up from the control panel) results in a scrambled mess, resembling a resolution issue similar to this: [http://www.steinnsteinsson.com/remote.jpg]("http://www.steinnsteinsson.com/remote.jpg"). It is not the viewer client, I have tried ultra/real/tight. I saw in a couple of threads that the issue could have been my XORG conf, but playing around with the setup yielded no fruitful results (part of my setup is listed below). 

Any suggestions? Thanks for any help in advance :)


```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        Defaultdepth    16
        Option          "SecurityTypes" "VncAuth"
        Option          "UserPasswdVerifier"    "VncAuth"
        Option          "PasswordFile"  "/root/.vnc/passwd"
EndSection

Section "Module"
        Load            "vnc"
EndSection

```

---

### Post by thatkidandy on 2008-03-11
*smacks head*

did not scroll down to see thread with similar problem below, sorry for redundance
[http://ubuntuforums.org/showthread.php?t=708027]("http://ubuntuforums.org/showthread.php?t=708027")

this is still not resolved however...

---

