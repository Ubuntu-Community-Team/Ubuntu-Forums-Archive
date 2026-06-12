---
title: "wmv playback (9.10)"
date: 2009-11-21
forum: Multimedia Software
---

### Post by coffee on 2009-11-21
I installed 9.10 a bit ago and just realized I can not play the *.wmv files I have saved.  This is not really critical just frustrating.

I was able to play the files in 9.04.

I have 'ubuntu-restricted-extras', gstreamer(all of them) and w64condecs installed as I did in 9.04.  

When I try and play them I get:
 [IMG]http://ubuntuforums.org/attachment.php?attachmentid=137079&stc=1&d=1258829526[/IMG]

and in vlc I get:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=137080&stc=1&d=1258829558[/IMG]

Is there something special I need to do in 9.10 to get this working?

Help would be appreciated.

thanks
coffee

---

### Post by HappyFeet on 2009-11-21
Looking it up, I noticed other people had the same problem. One person tried Songbird, and they played. Sorry, I can't be of much more help.

---

### Post by rtalcott on 2009-11-21
Same problem here and I have been unable to get it to work....

Also...the Bloomberg stream will no longer play on any of my machines...have no clue about that either.mms://media2.bloomberg.com/btv_US200.asf
rt

---

### Post by coffee on 2009-11-22
I have run into other media file trouble as well *.flv and one other that I can not remember at this time.

---

### Post by coffee on 2009-11-25
After working with a luanchpad bug report ([[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/486915")) I got this fixed.

Open Synaptic and look up libavcodec52.

If you have libavcodec-extra-52 installed remove it

Install libavcodec52

I had the dvdstyler package installed, this caused the libav change on my rig.  It sounds like people have had trouble with the OpenShot as well there is a thread [[COLOR="Blue"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1281367") about how to fix it.

coffee

---

