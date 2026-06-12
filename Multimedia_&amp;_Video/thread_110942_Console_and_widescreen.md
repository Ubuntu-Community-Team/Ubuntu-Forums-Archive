---
title: "Console and widescreen"
date: 2006-01-01
forum: Multimedia &amp; Video
---

### Post by splater on 2006-01-01
Hi,

when Ubuntu boots or when I enter in real console mode, I can't see all the screen, the bottom doesn't appear .. I have a widescreen 15'4 .

I don't think this is a Xorg prolem, isn't it? I don't know what to do to correct this problem, someone to help me ??

Thx

---

### Post by splater on 2006-01-01
I find an partly solucion to my problem. I change my menu.lst (grub loader) and added ```
vga=0x318 video=vesafb:mtrr,ywrap
```

below you can find the new line:
```

/boot/vmlinuz-2.6.12-9-686 root=/dev/hda3 vga=0x318 video=vesafb:mtrr,ywrap ro quiet splash

```

Hope it can help somebody. I read that th1280x800 is peharps not possible to have in a virtual console but it's quite good in 1024x768!!!! If someone knows how to made it work in 1280x800, please respond !!!

For some more informations:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10]("http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10")

---

### Post by funkyhat on 2007-02-09
I've got my console running at 1280x800 (ATi card), all I did was add radeonfb on a new line in /etc/modules
(I think this method will only work if you are using the open source radeon drivers, I heard radeonfb and the binary ATi drivers don't mix)

---

