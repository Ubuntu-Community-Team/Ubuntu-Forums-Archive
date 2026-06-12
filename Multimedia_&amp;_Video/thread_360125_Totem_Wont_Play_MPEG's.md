---
title: "Totem Wont Play MPEG's"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by CarlosinFL on 2007-02-12
So Ubuntu came with Totem installed which I have always used in Debian Sarge and Etch however in 6.10, I can't open a simple MPEG. I could understand .WMV since I have no codecs installed but what do I need to do to enable Totem to play an MPEG? 

[IMG]http://img263.imageshack.us/img263/8508/mpegks2.png[/IMG]

---

### Post by RomeReactor on 2007-02-12
Hi. If you're using Totem-Xine, open the Terminal and

```
sudo apt-get install libxine1 libxine-extracodecs
```

If you're using Totem-Gstreamer, then it's

```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-x
```

---

### Post by Robor on 2007-02-13
Thanks very much RomeReactor.  I was getting the same error as Carlwill.  I had the default Totem (GStreamer) installed.  I installed all of the extras for it you listed.  That got rid of the error and I got sound but no video.  I uninstalled totem-gstreamer and tried totem-xine and all of the extras you listed.  I get the same thing.  No errors and audio but no video.  

What I don't understand is this is my work desktop install.  I have another Ubuntu install on my personal laptop.  Both are Edgy.  On both systems I've got 'Totem Movie Player 2.16.2  --  Movie Player using xine-lib version 1.1.2 and GNOME'.  I'm trying to play the same exact movie (FantasticMachine.wmv) and my desktop doesn't play it but my laptop does.  Both are ATI video cards by the way.  Not sure if it matters/helps but I do have Beryl/AiXGL on my laptop and standard Gnome on my desktop.

---

### Post by Datalanche on 2007-02-13
> **Robor said:**
> I'm trying to play the same exact movie (FantasticMachine.wmv) and my desktop doesn't play it but my laptop does. 

You may need the w32codecs package if it is a WMV9 file. Here's how to get that working: [https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)

---

