---
title: "Epson 4990 software download requires sane 1.0.3"
date: 2010-11-02
forum: Multimedia Software
---

### Post by sofasurfer on 2010-11-02
I am trying to install the software for the Epson 4990 scanner from [http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL2.do)
But I read that before installing Image Scan I MUST install Sane 1.0.3. However, it appears that Sane only goes up to 1.0.2. What gives?

---

### Post by davidmohammed on 2010-11-02
what version of ubuntu are you using? - lucid version of sane is 1.0.14-9 (according to synaptic manager)

---

### Post by sofasurfer on 2010-11-02
Thats right, and I am using Lucid. I looked on the sane website - [http://www.sane-project.org/source.html](http://www.sane-project.org/source.html) - and it shows no 1.0.3 version.Gonna be hard to install it if it does not exist.

---

### Post by davidmohammed on 2010-11-02
what is the actual file you are downloading on that webpage?

I tried iscan_2.26.0-3.ltdl7_i386.deb - that works OK.

---

### Post by sofasurfer on 2010-11-02
I clicked on the line that says - HTTP: alioth.debian.org (USA, provided by Debian) 

Where did you find - iscan_2.26.0-3.ltdl7_i386.deb? Is that the sane package?

EDIT:: Woops! My stupidity!! iscan is the scanner driver. I will try it without worrying about the newest sane package.

---

### Post by sofasurfer on 2010-11-02
I just did a search for "sane 1.0.3" and found lots of references to it but I do not see anything to download it.

---

### Post by davidmohammed on 2010-11-02
try typing "sane" into synaptic manager.  Install the 1.0.14-9 version.  Then download iscan_2.26.0-3.ltdl7_i386.deb and install that.

---

### Post by sofasurfer on 2010-11-02
I installed iscan without doing anything else and it appears to work fine. I'll be darned. Now I just need to learn to use this scanner.

---

### Post by sofasurfer on 2010-12-09
I have iscan installed and it works. However, the scanner does not scan the right side of the scanner glass for about one inch in.
Any idea why, and what I can do about it?

---

