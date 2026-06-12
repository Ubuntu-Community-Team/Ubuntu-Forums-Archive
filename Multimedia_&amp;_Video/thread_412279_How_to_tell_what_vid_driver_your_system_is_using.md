---
title: "How to tell what vid driver your system is using"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by Thrasonic on 2007-04-17
How can I tell what video driver my Ubuntu system is using?  I'm using 6.10.

---

### Post by heimo on 2007-04-17
> **Thrasonic said:**
> How can I tell what video driver my Ubuntu system is using?  I'm using 6.10.

Running:
```
grep -i Driver /etc/X11/xorg.conf
```
should give you couple lines from Xorgs configuration file, and one is video driver (ati,nvidia,nv,vesa,fglrx,radeon,via,i810 etc). Then you can check which device you have by running:
```
lspci | grep -i VGA
```

---

### Post by Thrasonic on 2007-05-01
Here's what I get when I do that:

bubba@kubuntu:~$ grep -i Driver /etc/X11/xorg.conf
        Driver      "kbd"
        Driver      "mouse"
        Driver      "wacom"
        Driver      "wacom"
        Driver      "wacom"
        Option      "VendorName" "ATI Proprietary Driver"
        Driver      "vesa"
        Driver      "fglrx"
bubba@kubuntu:~$ lspci | grep -i VGA
03:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71ce

It seems like it's not using the ATI driver, correct?  If not how can I fix this?

---

### Post by rumli on 2007-05-01
Edit: sorry, I posted an incorrect answer.

---

### Post by Thrasonic on 2007-05-02
bump

---

### Post by rumli on 2007-05-03
Try posting  your entire /etc/X11/xorg.conf file.

```
cat /etc/X11/xorg.conf
```

---

