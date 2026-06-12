---
title: "smplayer seek problems with any videos on kubuntu"
date: 2013-03-05
forum: Multimedia Software
---

### Post by Jaoyur on 2013-03-05
I have ubuntu 12.04.02 with kde 4.10 with 3d effects.  have a ATI msi R6870 video card fglrx proprietary drivers 13.1.
  My problem is: If I play any video with smplayer, while seeking, the picture freezes  and the audio keeps playing, I also hear some audio distortion while  seeking more.
  It does not happens with VLC, vlc works well.
  Here is my mplayer log and other informations:

[LIST] 
[*]mplayer.log  [http://paste.ubuntu.com/5571853/](http://paste.ubuntu.com/5571853/) 
[/LIST]
  I have also tried to disable kwin effects (ctrl-shift-f12) and to disable ati video tearing reduction, but it did not help.
      
How to solve it?

Thanks

---

### Post by andrew.46 on 2013-03-05
Your best bet at the beginning of unraveling this problem is to build a more recent version of MPlayer, current is:

```

andrew@skamandros~$ mplayer | head -n 1
MPlayer SVN-r35928-4.7.2 (C) 2000-2013 MPlayer Team

```

---

### Post by Jaoyur on 2013-03-05
ok where can I download it?

---

### Post by andrew.46 on 2013-03-05
Looks like the Daily Build PPA has gone a little quiet which is a pity. The Ubuntu community wiki has a reasonably complex page which describes the process:

[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

Hopefully you can walk through this, although it looks like it is really aimed at 12.10 I suspect not that much has changed between versions...

---

### Post by SeijiSensei on 2013-03-05
Are you using a VA-API-enabled version of mplayer?  That supports offloading of graphics decoding to the video card.  I only ever use NVIDIA hardware with its equivalent VDPAU interface, so I have no personal experience with VA-API, but you might [try this approach](http://www.webupd8.org/2012/11/install-mplayer-with-va-api-hardware.html).

---

### Post by Yellow Pasque on 2013-03-05
VA-API won't work without some other packages (fglrx may automatically pull them nowadays though): [http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29](http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide#Hardware_Video_Decode_Acceleration_.28EXPERIMENTAL.29)

Also, as the link suggests, using xbmc is the best option for most people running fglrx/Catalyst.

---

