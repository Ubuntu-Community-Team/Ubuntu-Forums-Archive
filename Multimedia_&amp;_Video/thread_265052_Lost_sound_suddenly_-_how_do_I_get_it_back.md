---
title: "Lost sound suddenly - how do I get it back?"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by n00buntu NJ on 2006-09-25
I've had Ubuntu running on this computer for at least 6 months, and I've never had a problem with sound.  

Yesterday I was attempting to install some video-editting application called LIVES, decided I didn't like it, did a "sudo apt-get remove --purge lives" to get rid of it, and now I don't have any sound.  

So far I've tried [THESE]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME") instructions to try to fix it, but it didn't work.  

Any help would be greatly appreciated!

I attached the output of "lspci" if it will help...

Also, the volume applet in gnome-panel is displaying a red X.  If I click on it I get the following message:

"No volume control GStreamer plugins and/or devices found."

---

### Post by Kateikyoushi on 2006-09-25
Seems your sound card is listed in lspci but the alsa driver is not loaded.
[Try this guide.]("http://www.ubuntuforums.org/showthread.php?t=205449")
General help and point 3, is where I would start.

---

### Post by n00buntu NJ on 2006-09-26
Thanks for the link - I'll try this later on tonight (I hope), I didn't get home from work until late last night...

But this looks like what I need.

---

### Post by n00buntu NJ on 2006-09-30
OK, I still can't get it to work again.  

I still don't have sound after following every possible instruction from that thread.  My volume icon in the my panel still has the red X on it and it says "No volume control GStreamer plugins and/or devices found." when I click on it.  I've also tried to do 

apt-get remove --purge gstreamer-*  (which also removes ubuntu-desktop)

followed by 

apt-get install ubuntu-desktop (which re-installs all the gstreamer plugins)


Does anybody have any ideas how I can find out if my sound card is just fried?  It's the integrated sound on my motherboard, and I wouldn't be supprised if it was toast.

I've attached the output of lspci -v too, it shows my sound card on it - does that mean that it's not dead?  I'm at a loss, and I'm thinking it would just be easier to buy a new sound card...

Thanks for any help...

---

