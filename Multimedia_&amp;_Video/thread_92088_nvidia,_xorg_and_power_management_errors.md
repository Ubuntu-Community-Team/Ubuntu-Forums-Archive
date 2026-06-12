---
title: "nvidia, xorg and power management errors"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by tassoman on 2005-11-18
Hi all, :KS 
 I've just installed 5.10 from scratch but at the end of games, my X is a tile of cyan @ on a pink background.

Ok ok.. maybe default nv drivers aren't the good choice for nvidia.

I've followed the howto install nvidia-glx, i've done, but now when X serve the login screen, my monitor goes in standby mode.

I've tried reading logs, but no (EE) was found. I've tried with syslog, but i dunno.
I've tried lsmod and nvidia driver is correctly there.

Some hint? I wouldn't give up to ubuntu nvidia should be the most compatible video card. :(

---

### Post by Teroedni on 2005-11-18
give me outputs of 
sudo gedit /etc/X11/xorg.conf
and
sudo gedit /var/log/Xorg.0.log

remeber to use code so the text dont get formatted

---

### Post by tassoman on 2005-11-18
[http://www.tassoman.com/xorg.conf](http://www.tassoman.com/xorg.conf)

[http://www.tassoman.com/Xorg.0.log](http://www.tassoman.com/Xorg.0.log)

Thanks in advance

---

### Post by Teroedni on 2005-11-19
VertRefresh	43-60

this is a little low
You need to find out your monitors horinz and vertical sync rate(frequency)

Do you got a manual ?
Or if you know the model name you could search for it on google and get your horinz and vertical frequency

---

### Post by tassoman on 2005-11-19
I've updated with corrected refresh rates but problem still remain :(

---

### Post by tassoman on 2005-11-19
Reading my Xorg.0.log we could find those (WW)arnings:

[LIST]
[*](WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
[*](WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
[*](WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
[*]**(WW) Open APM failed (/dev/apm_bios) (No such file or directory)**
[*](WW) Ignoring request to load module GLcore
[*](WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
[*](WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
[/LIST]

Exluding fonts, and bad resolutions, there is a problem with GLcore and apm.

Wich module loads missing /dev/apm_bios?

---

### Post by Teroedni on 2005-11-19
i got the same error myself so i dont think that is the problem. My card works perfectly:)


Could you post the lastest xorg.0.log

---

### Post by tassoman on 2005-11-19
You can find it at [http://www.tassoman.com/Xorg.0.log.2](http://www.tassoman.com/Xorg.0.log.2)

I found a new WW: 
**(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0**

Thanks for patience ;)

---

### Post by Teroedni on 2005-11-21
so what does glxinfo give you

```
sudo glxinfo
```

also can you start xscreensaver via the menu ??

---

### Post by tassoman on 2005-11-21
I gave up. Since formatting and starting from zero, I'll give a try to PCBSD.

Btw thanks for support.

---

### Post by tassoman on 2005-11-26
Hi! i'm back! :rolleyes: 

I've trashed pcbsd, and re installed Badger (Tasso).
Now I'm loading X with vesa drivers.
Nvidia drivers still make my screen switch off.

Video card is a Point Of View 6600 GT and should be supported. Some help plz?

---

### Post by jenci on 2005-12-14
I have same problem with NVidia 6600. With Ubuntu, Gentoo, SuSe & Debian. Maybe EDID problem?

---

### Post by tassoman on 2005-12-14
The problem was just to unplug the second CRT cable. :-|

---

