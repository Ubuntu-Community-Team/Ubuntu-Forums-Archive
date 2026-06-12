---
title: "Changing Resolution"
date: 2005-12-20
forum: Multimedia &amp; Video
---

### Post by DJiNN on 2005-12-20
I know this has probably been answered before, but i can't seem to find it using a search (Well, not one that works anyway).... :) 

I have just installed Breezy onto an old PIII Deskpro, & the screen that i used was a small LCD, & the default res came up as 800x600 @ 60Hz.... Now, i have hooked it up to an EiZO F764-T (to watch films etc) & would like to UP the screen size & refresh rate, but i can't find a way to do it. 

I don't mind having a crack at the command line, so if anyone could explain the process or point to a How To or a link, i would be very grateful.....

Thanks for taking the time to read this.

DJiNN

---

### Post by lutrafobic on 2005-12-20
To fix this:

Open a terminal and type:  ```
sudo dpkg-reconfigure xserver-xorg 
```

This will start a configure software that will ask you simple questions about you harddrive. e.g.  -Do you have a 3 button mouse?  -What resolutions can you screen handle?


cheers

---

### Post by DJiNN on 2005-12-20
[QUOTE=lutrafobic]To fix this:

Open a terminal and type:  ```
sudo dpkg-reconfigure xserver-xorg 
```

This will start a configure software that will ask you simple questions about you harddrive. e.g.  -Do you have a 3 button mouse?  -What resolutions can you screen handle?


cheers[/QUOTE]

Hi lutrafobic, thanks for the reply. Just tried this & it's saying that the xserver is not installed & no info is available.... confused?... yes i am a bit, but i'm sure that i'll get it cracked in the end. :)

Any ideas as to what i could try next? 

Many thanks for your help.....

DJiNN

---

### Post by douwe flinx on 2005-12-20
This was something I was looking for.
I entered the command line and was able to change some values to my wishes, but how do I get Ubuntu to take my changes, because after bringing in my vlue, nothing happens.:(

---

### Post by polt on 2005-12-20
You can change your video configuration directly in /etc/X11/xorg.conf. Backup your current file before you make the changes. Be careful, your video may not work if the settings are wrong! If you have a problem, use Ctrl-Alt-F1 to get back into terminal mode, then recover your backup.

I found nVidia settings described in detail on their website. You can also find a description of this file on the x.org website.

---

