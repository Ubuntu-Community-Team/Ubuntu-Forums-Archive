---
title: "Max Resolution 800 x 600...help, I'm stumped."
date: 2010-01-04
forum: Multimedia Software
---

### Post by qkzoo on 2010-01-04
I'm pretty new to Ubuntu, I just installed my first copy (of any Linux distro) two weeks (or so) ago.  When I go to Preferences => Display, the max resolution I can set is 800 x 600.  I have (an old) HP M50 for a monitor, and even though it's old, the original specs on it support 1024 x 768 (or close to that).  How do I get this resolution?  I've done a bunch of Google's and read something about setting or changing something in my /etc/X11/xorg.conf file, so I went there, and it doesn't exist.  A friend of mine has the exact same issue, but he has an HP v50 LCD (or something like that) and his max resolution is 800 x 600, also. I read a few other things on the net, but they too, flew right over my head.  Was hoping someone here could help walk me through the steps...

Thanks,

Q

---

### Post by Peekie on 2010-01-04
Are you sure it's your monitor? I would guess it's got something to do with your video card. What kind of video card do you have?

And Ubuntu 9.10 doesn't use a xorg.conf file by default. However if you create one it will get used. See this thread for more information: [No xorg.conf file in Ubuntu 9.1?]("http://ubuntuforums.org/showthread.php?t=1340780")

---

### Post by =not4prophet= on 2010-01-04
I had a similar problem and had to create a xorg.conf file with settings for my LCD monitor to force ubuntu to display at 1024x768

```
Section "Monitor"
  Identifier "Monitor1"
  Vendername "Generic LCD"
  Horizsync 31.5-48.0
  Vertrefresh 56.0-65.0
EndSection

Section "Screen"
  Identifier "Screen1"
  Monitor "Monitor1"
  Subsection "Display"
    Modes "1024x768"
  EndSubsection
EndSection
```

---

### Post by qkzoo on 2010-01-04
Not sure about the video card, it's an HP Pavilion, pretty sure it's built right into the mother board...  How did you figure out the settings for your monitor?

---

### Post by HappyFeet on 2010-01-04
Post the output of 
```
lspci
```

---

### Post by =not4prophet= on 2010-01-05
All LCD monitors operate within the same narrow horizontal sync and vertical refresh ranges, so I just used generic settings.  

Most likely you have a video card that uses a driver that does not support kernel mode setting, older ATI chipsets are a good example of this. Among other things, it can prevent your graphics card from properly detecting your monitors abilities using the newest X server included in Ubuntu 9.10.

If you want the actual settings for your monitor, the horizontal sync and vertical refresh ranges should be included in your monitors documentation, and on some monitors the info is available through the on-screen control panel.  You could also use gtf to generate a custom modeline for your xorg.conf, but since all you are trying to do is get 1024x768, the generic monitor settings from my previous post should be all you need in your xorg.conf file.

---

