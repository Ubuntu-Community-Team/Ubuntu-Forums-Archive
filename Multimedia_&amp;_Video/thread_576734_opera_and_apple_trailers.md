---
title: "opera and apple trailers"
date: 2007-10-15
forum: Multimedia &amp; Video
---

### Post by psycho_NIX on 2007-10-15
hi all,
i can watch the in firefox using VLC plugin (gstreamer), but in opera it doesn't works. i have added link to VLC plugin in opera plugin section but it still wont show me trailers. woul anyone help me to make it work in opera?
thnx

---

### Post by Kulgan on 2007-10-17
Same for me... 

Also tried mplayer and totem plugins, with no difference. I have flash 9 working fine, though it had to be converted from the rpm to be installable on ubuntu... 

-K

---

### Post by Kulgan on 2007-10-17
ok, so I got media working with GXine, even though the plugin isn't as good (IMHO) as that of VLC or mplayer. This is what I did:

Install from reops:
libxine1-plugins (1.1.4-2ubuntu3)
gxineplugin (0.5.11-1ubuntu2)

And if these are not included as dependancies, make sure they are installed:
gxine (0.5.11-1ubuntu2)
gxineplugin (0.5.11-1ubuntu2)
libmodplug0c2 (1:0.7-5.2build1)
libxine1 (1.1.4-2ubuntu3)
libxine-extracodecs (1.1.4-2ubuntu3)
libxine1-console (1.1.4-2ubuntu3)
libxine1-ffmpeg (1.1.4-2ubuntu3)
libxine1-gnome (1.1.4-2ubuntu3)
libxine1-kde (1.1.4-2ubuntu3) <- for some reason that got included as well...

If Opera is open, restart it. Then go to Tools -> Preferences -> Advanced -> Downloads.
For each mime-type that you want to open in Xine, select it and click edit. 

Click "Use Plug-in" and select the Xine plugin from the drop-down list that appears. Restart Opera again, and it should work. 

-K

---

