---
title: "NVidia &quot;legacy&quot; driver  dosen't work !"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by astromech on 2007-05-22
I've got a NVidia Riva tnt2 Model 64 32mb video card and the driver that's supposed to work for it only gives me 800x600 and 640 x480 resolution .The one that's running is the free one and gives me 1024x1280 but I get trails when moving windows when I'm surfing.The "glx" nvidia driver didn't work at all . System specs:PIII @ 733, 256 mb SDRAM ,Ubuntu 7.04 Any help for this???btw>Desktop effects could not be enabled.

---

### Post by king_arthur on 2007-05-22
The problem might be with the settings (frequencies) required by your monitor.
The standard Xserver.config uses far to slow frequencies unless you specify differently.
 I have exactly the same h/w that you are using and I got even glx enabled, hence Google Earth and Picasa work like a charm, albeit a bit slow. :)

There are many how-to's around to overcome the issue.
Google is your friend. You can start looking [here]("http://www.rockhopper.dk/linux/software/configuring-x.html") for some hints.

/P

---

### Post by astromech on 2007-05-25
> **king_arthur said:**
> The problem might be with the settings (frequencies) required by your monitor.
The standard Xserver.config uses far to slow frequencies unless you specify differently.
 I have exactly the same h/w that you are using and I got even glx enabled, hence Google Earth and Picasa work like a charm, albeit a bit slow. :)

There are many how-to's around to overcome the issue.
Google is your friend. You can start looking [here]("http://www.rockhopper.dk/linux/software/configuring-x.html") for some hints.

/P

I have reconfigured x   .Now I get the right resolution. there are still issues that I'm working on .Such as windows making trails when I move them while firefox is on.

---

