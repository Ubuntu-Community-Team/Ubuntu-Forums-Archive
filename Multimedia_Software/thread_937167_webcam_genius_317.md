---
title: "webcam genius 317"
date: 2008-10-03
forum: Multimedia Software
---

### Post by vitordesouza on 2008-10-03
I can not install a Geninus 317 webcam. I am running ubuntu 8.04 hardy

uname -a gives
Linux kaon 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

When I plug the camera the file /dev/audio1 appears.

lsusb gives:
Bus 003 Device 002: ID 093a:2623 Pixart Imaging, Inc. 

I have already tried:
easycam2, cheese, camorama, xawtv, mplayer and installing spca5xx manually.

Nothing solved the problem.

Please, anyone has any other suggestion.

Why the hell is it so difficult to make a webcam to work in ubuntu ?

---

### Post by mindoms on 2008-10-04
Nobody answered, so im gonna try to help you

please make sure the webcam is plugged in and post the output to
```

ls -l /dev/video*

```

---

### Post by vitordesouza on 2008-10-06
Thank you for the help.
Here you have it:

vitor@kaon:~$ ls -l /dev/video*
ls: cannot access /dev/video*: No such file or directory

vitor@kaon:~$ ls -l /dev/audio*
crw-rw----+ 1 root audio 14,  4 2008-10-06 08:06 /dev/audio
crw-rw----+ 1 root audio 14, 20 2008-10-06 08:06 /dev/audio1

---

