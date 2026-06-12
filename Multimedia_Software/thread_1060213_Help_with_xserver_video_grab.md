---
title: "Help with xserver video grab"
date: 2009-02-04
forum: Multimedia Software
---

### Post by Pitboss on 2009-02-04
Hi all. I'm new to linux and ubuntu and I'm searching for a way to grab video from the xserver. I installed ffmpeg and I used the following command:

```

ffmpeg -f x11grab -s cif -r 24 -i :0.0 ~/test.mpg

```

Well this works, but the cif resolution is pretty small. And only a little part of the screen was grabbed.

So I tried to use the above with -s 1680x1050. And for a minute of would-be recording my computer was constantly crashing. When I played the video the speed was 3 frames / minute :)

So I'll appreciate any ideas and advice.

Thanks in advance.

---

### Post by Pitboss on 2009-02-06
I read about all kind of desktop recorders, like recordmydesktop, byzanz, xvidcap. I tried them all and the recording doesn't seem to work with any of them it's too SLOW. The graphical frontend of recordmydesktop crashes and I should kill it in order to proceed normal work. I believe that the problem is my videocard or its driver. The card is ati hd 3600 series and the driver is the newest fglrx , compiz works fine but I can't record video from the desktop ;(. If anybody has got this working I'll appreciate any help.

---

