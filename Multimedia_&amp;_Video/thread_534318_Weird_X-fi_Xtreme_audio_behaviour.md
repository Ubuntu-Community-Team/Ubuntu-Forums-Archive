---
title: "Weird X-fi Xtreme audio behaviour"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by aphylius on 2007-08-25
Hello,

I own a Create labs X-fi xtreme audio card, and I can't get proper sound out of it.
When I follow all the steps in the [comprehensive sound problems guide]("http://ubuntuforums.org/showthread.php?t=205449") I get success for all the steps, but no sound. All programs look like they're playing, but I get no sound whatsoever.
So I figure it's a alsamixer issue. considering this, I played around a bit with the alsamixer settings, and accidentaly unmuted the IEC958 swith. bang! sound through my speakers. Nice but heavily distorted sound. But at least it was sound, so I started googleing for this distorted sound issue, but all I can find about that is that I need to turn off the iec958 switch, which would result in no sound at all in my case.

How could this be? I've read that numerous people have gor their X-fi extreme audio working properly since it's just a Audigy LS (and my ubuntu says it's just a audigy). I'm almost up to the point to just trash the card and use my onboard audio again.

---

### Post by MikeyZ on 2008-01-22
I've got the same problem here as well. The damn thing just doesn't seem to want to work.

---

### Post by Yellow Pasque on 2008-01-22
The last time I checked, X-fi is only supported with beta drivers, and only for the amd64 version.
[http://ubuntuforums.org/showthread.php?t=571656](http://ubuntuforums.org/showthread.php?t=571656)

EDIT: That's what you get for buying into the Creative monopoly :P

---

### Post by MikeyZ on 2008-01-23
Well, I guess some people don't read everything, just half of it.

The X-fi Xtreme Audio isn't a X-fi based chip. It's an spin-off of the Audigy and partly supported by the Alsa-driver (though they don't mention it).

I just send an email to Creative with the request to send me an adress. I'll mail it back and maby I'll even ask if they can post the pictures when the shove it up in the "darkest area that the body has" of the person responsible for not supporting linux.

I never buy a Creative again and that's final. I thought, well they probably know by now it's not bad to support linux. Even Ati and nVidia give somewhat support, so why can't they. Especially in a time that nearly every motherbord has a soundchip on-board, it's good to support your customers. Further more, I thought, well I want to do myself a pleasure with good sounds. I think I've enjoyed it for about 5 minutes, that was installing the card into the system. It was over, when I found out the thing isn't supported and even not fully as a "Audigy".

---

### Post by gmantu on 2008-01-30
If it helps, I just got an X-Fi Extreme Audio working by downloading and compiling the latest alsa-driver-1.0.15 per the following: [http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html]("http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg21618.html")

Summery from that post/email:
Install compile tools if needed: sudo apt-get install build-essential 
Download  alsa-driver-1.0.15 from [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
tar xvf alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
sudo ./configure
make
sudo make install
Reboot

Note: You may need to adjust mixer settings (per the above post) to ensure analog output is turned on.
Note: Only the front speakers work for me. I am not sure if surround sound is supported. I suspect not, but if someone knows, please enlighten us.

---

### Post by UberError on 2008-02-09
Thanks gmantu .... worked like a charm

---

