---
title: "How to increase screen resolution in text mode"
date: 2007-07-04
forum: Multimedia &amp; Video
---

### Post by elev on 2007-07-04
I'm using tty2 in Feisty to run rtorrent and the resolution is so low I cannot view all of the rtorrent screen.  How can I change the screen resolution for just the plain old terminal?
Thanks in advance:)

---

### Post by Sockerdrickan on 2007-07-04
seconded

---

### Post by fackamato on 2007-07-04
In your /boot/grub/menu.lst:

```
kernel          /vmlinuz-2.6.20-16-lowlatency root=UUID=193285c5-e56b-4532-911d-f8d8b2dd9877 ro quiet splash locale=sv_SE **vga=0x31B**
```

[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)

[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by elev on 2007-07-04
Thanks the table in the ubuntu help link worked like a charm.

Thanks.

---

