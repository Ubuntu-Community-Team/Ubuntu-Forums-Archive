---
title: "Not allowed to read DVD?!"
date: 2008-02-16
forum: Multimedia &amp; Video
---

### Post by enigma_0Z on 2008-02-16
OK. I've got an odd one.

Popeed a DVD into my computer and i couldn't play it as a normal user. Totem came up and said that I wasn't allowed to. I checked the permissions, and while the AUDIO_TS dir had permssions of 555 (rx,rx,rx), VIDEO_TS only had 444 (no execute).

I can play the DVD as root, and I am in the process of creating an image as a normal user right now, but for some reason, the permissions are screwy.

This only happens on this DVD, however, any other DVD in my collection does just fine.

Does anyone know what's going on with this or how I can fix it? Thanks.

---

### Post by VMan on 2008-02-16
I have experienced a very similar problem.  Some (not all) of the DVDs I recorded using a DVD recorder hooked up to my TV exhibit the exact same behavior you describe.  The work around was to become root, copy the files onto my HD, change the permissions, and then do the editing work on them.  

I haven't had time to figure out why this happens with some and others work just fine.  If you figure out what's going on, would you send me a PM to check this thread?  I'll post here when I get a chance to look into it more (might be a while though).

---

### Post by vjones777 on 2008-03-20
Interesting.  I found the very same symptoms (though I didn't check the permissions).  I burnt a DVD using a Samsung DVD-VCR combo unit (DVD-VR357).  

Initially, though it would playback ok on the Samsung unit, it wouldn't on another DVD player and it showed up as blank disk when I inserted it into the laptop (Ubuntu-gnome).  Not too suprising as I hadn't 'finalised' the disk.   

After finalising the disk it would play back fine on the other stand alone DVD player, but when I inserted it into the lappie it refused to play.  Nautilus showed just the VIDEO_TS folder.  Totem's error message is misleading, saying "Totem could not play 'dvd://'.  The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"
Browsing as root (sudo ls at the command line) (or gksudo nautilus) allows the disk to be seen and played.

All rather strange, but I'm glad this workaround works.

---

