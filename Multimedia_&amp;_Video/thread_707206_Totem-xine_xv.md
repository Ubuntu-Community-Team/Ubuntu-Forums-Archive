---
title: "Totem-xine xv?"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by grozni on 2008-02-25
Hi,


I've installed totem-xine, previously I've used totem-gstreamer, but he didn't want to play DVD's. I've switched to totem-xine, but I can't find option to disable XV, my card is x3100 and video is broken when compiz is active. I don't want to loose compiz, previously I've used gstreamer-properties and then disable xv from there, but in case totem-xine I can't find that option. So how to disable XV in totem-xine? Thanks

---

### Post by erginemr on 2008-02-25
While using totem-gstreamer, had you installed "gstreamer-plugins-bad" and "gstreamer-plugins-ugly", too? (You may need to install them.)

And had you visited the Medibuntu site: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and added the Medibuntu repository to Synaptic and installed libdvdcss2?

If not, you may consider taking these steps and revert back to totem-gstreamer to see if it helps.

Besides, there are two more fantastic video players that can also play DVD's: VLC and MPlayer. You may consider giving a try to them. Both are in the repositories.

---

### Post by grozni on 2008-02-25
I don't remembe installing these

"gstreamer-plugins-bad" and "gstreamer-plugins-ugly"


I have medibutntu repositories and I have installed libdvdcss2. I have also installed VLC and Mplayer. I don't like VLC much, and my mplayer is broken for DVD, althought I have disabled XV. The only players that currently work are Smplayer and Xine. I will try Totem-gstreamer with these plugins installed. Thanks

---

### Post by grozni on 2008-02-26
I've switched back to Totem-gstrreamer. All plugins you said are installed, I've reinstalled them, but I keep getting Totem cannot play DVD bacause it does not have appropriate plugins. Any suggestion? Thanks

---

### Post by erginemr on 2008-02-26
Can you please do a final check that the attached highlighted packages are installed in Synaptic?

---

### Post by erginemr on 2008-02-26
Although I do not prefer using Automatix as I don't like scripts doing some business behind my back, I admit that it has made the life of many Ubuntu users easier. So, as a last resort you can try Automatix to enable DVD playback:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by Eddie Wilson on 2008-02-26
Totem-gstreamer broke for me this weekend also. It had been working just fine. I got the same stupid error message plugins not insatlled and Vlc gave me the error could not open dvd. Changed to Totem-xine and have had no problems. Also this is not a hardware problems as I have read in several other threads. My dvd burner is only a couple of weeks old. This has got to be an Ubuntu problem. Maybe updates could have broken something. Anyway I'm just as happy with Totem-xine.

Eddie

---

