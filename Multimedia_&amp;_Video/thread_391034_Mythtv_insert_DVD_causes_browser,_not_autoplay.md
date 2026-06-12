---
title: "Mythtv: insert DVD causes browser, not autoplay"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by rbm0307 on 2007-03-22
I am unable to get Mythtv to autoplay any DVD when inserted into the player.  Rather, a browser window will open showing the DVD root directory with audio_ts and video_ts folders.  From this point, I can play the DVD if I select "Play DVD" from the Optical Devices menu. This indicates that the DVD codecs and mplayer components are functioning properly, to me. 

I have configured Ubuntu in Gnome to ignore disk insertions so that the insertion event is picked up by Mythtv.  I've also configured Mythtv to monitor the DVD/CD reader and to autoplay DVD when inserted.

What else must I do to get this function to work?

Thanks.

---

### Post by pssturges on 2007-06-26
Hi,

I'm having the exact same problem, did you ever find a solution? The browser you are seeing is actually mythgallery.

Phil

---

### Post by pssturges on 2007-06-27
bump

---

### Post by rbm0307 on 2007-06-27
> **pssturges said:**
> Hi,

I'm having the exact same problem, did you ever find a solution? The browser you are seeing is actually mythgallery.

Phil
I've not been able to resolve this problem yet.  I've been working on getting sound on IVTV on the backend working properly so haven't had the time to investigate further.

I realize that it is mythgallery but no filetype is associated with that component in my setup which is the confusing part.

Robert.

---

### Post by rbm0307 on 2007-07-19
Strange coincidence but I managed to fix my problem with DVD insertion recognition by configuring KeyBindings in MythWeb.

I was fine tuning my Mythtv .lircrc file for a new remote (MS MCE remote) and configured several of the KeyBindings in MythWeb, including the Launch DVD menu key binding.  By default, this binding is blank.  However, when I associated it with "Ctrl+3" key sequence (to be compatible with my .lircrc setup), DVD insertion and recognition functioned properly.  Specifically, Xine was launched when a DVD was inserted as expected.

This workaround may function for an installation that doesn't use LIRC also.

Cheers,

Robert.

---

