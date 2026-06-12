---
title: "Playing video with proprietary nVidia freeze Xorg since WMV installation"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by DuboisS on 2007-06-03
Hi,
This is my first post here...


I use Ubuntu 7.04 with nVidia proprietary driver. Everything was good until Totem asked me if I wished to install a **WMV codec**, and I my answer was Yes.

Since then, I am unable to play any Video (WMV, MPEG). If I do, the system freeze. I must keep pressing the X (to close the window) for ~10 seconds in order to close Totem. I discovered that Xorg was taking 97% or more CPU. I tried VLC and the problem was the same. I tried to reinstall Totem and the closed driver as well.

I discovered that the open driver (nv) doesn't have that kind of problem. I can't live with NV because it doesn't support well the twin view mode with my video card.

I would like to fixe it or, at least, recover my original configuration.
Any help would be appreciated.


Sylvain

---

### Post by diebels on 2007-06-03
You remember which package was installed by totem's suggestion?

Probably one of:
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse

Uninstall it.

To get wmv working, you could try installing gstreamer0.10-pitfdll from universe and w32codecs from [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)

---

### Post by loathsome on 2007-06-03
Or you could try launching [COLOR="DarkSlateGray"]**$ sudo gstreamer properties**[/COLOR] and go to the «Video» tab and then go Plugin &#8594; X Window System (No Xv)

---

### Post by DuboisS on 2007-06-03
Thank you, you people of Norway.

Unfortunately, both "removing ugly* & bad* gstreamer" and "gstreamer-properties" didn't changed anything.
I didn't pay attention to what codec was installed while playing WMV file, but I guess you (diebels) pointed out the right ones. As soon as I get back my Ubuntu Live-CD, I would test it...

Meanwhile, I could say that Totem freeze Xorg while playing songs as well, for instance Ogg files. Rhythmbox works fine with the same Music files. Thus, I suspect that a configuration file was altered.

A complete removing of Totem and reinstalling it wasn't a success, even with only open codecs.

---

### Post by loathsome on 2007-06-04
> **DuboisS said:**
> Thank you, you people of Norway.

Unfortunately, both "removing ugly* & bad* gstreamer" and "gstreamer-properties" didn't changed anything.
I didn't pay attention to what codec was installed while playing WMV file, but I guess you (diebels) pointed out the right ones. As soon as I get back my Ubuntu Live-CD, I would test it...

Meanwhile, I could say that Totem freeze Xorg while playing songs as well, for instance Ogg files. Rhythmbox works fine with the same Music files. Thus, I suspect that a configuration file was altered.

A complete removing of Totem and reinstalling it wasn't a success, even with only open codecs.
Did you try my tip? :)

And by the way, I recommend installing these codes: [http://ubuntu.loathsome.us/doc/media-plugins](http://ubuntu.loathsome.us/doc/media-plugins) - they work with every single media file I've ever tried.

Good luck.

---

### Post by DuboisS on 2007-06-04
> **loathsome said:**
> Did you try my tip? :)

And by the way, I recommend installing these codes: [http://ubuntu.loathsome.us/doc/media-plugins](http://ubuntu.loathsome.us/doc/media-plugins) - they work with every single media file I've ever tried.

Good luck.

Christian,
Your tip didn't fixed up my problem with Totem, but it gave me an idea:

I took back VLC and I selected **Setup=>Preferences=>Video=>Output modules=>_X11 Video Output_** (Advanced Options must be checked) and it is working!

With that in mind, I think I shall be able to find a solution on the web to fixes Totem as well.
Thanks.

Sylvain

---

### Post by DuboisS on 2007-06-06
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Using the 9631 drivers (nvidia-glx), add to the **Device section** of **/etc/X11/xorg.conf** this line in order to avoid lockups :
**Option "UseDisplayDevice" "DFP"**

---

### Post by DuboisS on 2007-06-06
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=2796282#post2796282](http://ubuntuforums.org/showthread.php?p=2796282#post2796282) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **DuboisS said:**
> **This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Using the 9631 drivers (nvidia-glx), add to the **Device section** of **/etc/X11/xorg.conf** this line in order to avoid lockups :
**Option "UseDisplayDevice" "DFP"**

Oops, my URL wasn't appropriate.
Sorry!

---

