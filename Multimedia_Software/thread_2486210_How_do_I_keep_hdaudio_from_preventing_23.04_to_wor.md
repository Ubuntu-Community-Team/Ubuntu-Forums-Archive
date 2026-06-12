---
title: "How do I keep hdaudio from preventing 23.04 to work?"
date: 2023-04-22
forum: Multimedia Software
---

### Post by cigtoxdoc on 2023-04-22
Please see screen output shown below.  PC with 23.04 locked up before getting to login screen.  Had to do Ctrl-Alt-F2 to continue login.

Ubuntu 23.04  john-Precision-7720 tty2

John-Precision-7720 login: john
Password:
Welcome to Ubuntu 23.04 (GNU/Linux 6.2.0020-generic x86_64)

0 updates can be applied immediately.

Last login: Fri Apr 21 04:05:29 EDT 2023 on tty2
john@john-Precision-7720:~$   [33.113078]  snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
[   33.113302] snd_hda_codec_generic hdaudioC0D2: Unable to sync register 0x2f0d00. -5
[   33.114804] snd_hda_codec_generic hdaudioC0D0: Unable to sync register 0x2b0d00. -5
[   33.114948] snd_hda_codec_generic hdaudioC0D0: Unable to sync register 0x2b0d00. -5


How do I fix this problem?

Thank you,

John

---

### Post by cigtoxdoc on 2023-04-25
The only way I was able to resolve this problem was to download the Ubuntu Unity 23.04 installer and reinstall the OS.  This also fixed two other problems.  Audio from built-in speakers works correctly and consistently and Ubuntu got the correct video driver installef.

---

