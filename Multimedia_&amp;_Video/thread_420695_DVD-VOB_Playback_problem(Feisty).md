---
title: "DVD-VOB Playback problem(Feisty)"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Neecapp on 2007-04-23
I am running Feisty Fawn.

Okay. So, this is the problem I am having.

For some reason I can put the dvd into my drive and it will come up and play perfectly fine.

But, if I go to the dvd folder and look at the VOB files and try to play them they are all garbled up and don't play right. Thus leads to any wine program trying to backup the dvd making garbled up video.

Also.. if I use Vobcopy.. they resulting vobs play perfectly fine.

Is there any way to fix this?

---

### Post by seamless on 2007-04-23
The problem is dvd's are encrypted. When you play the dvd the dvd is decryptd. Playing the vobs directly they are not. Vobcopy stipps the copy protection from the vobs which is why the resulting vobs play fine. Your best bet is to use something like Vobcopy or dvddecryptor before you backup.

---

### Post by Neecapp on 2007-04-23
after I use Vobcopy what's the best way to go from there to burning it to a dvd?

Obviously I would have to shrink it and such.. but if I use dvdshrink it says it can't find VIDEO_TS.IFO.

Thanks!
-Neecapp

---

### Post by seamless on 2007-04-23
K3b would be the easist solution.

You can also make an iso by:
$ mkisofs -dvd-video -o dvd.iso /home/you/dvd/
$ growisofs -dvd-compat -speed=x -Z /dev/pathtodvdburner=/home/you/dvd.iso
Just be sure you have the proper dvd directory structure setup if you use the command line method. If you are unsure open the entire VIDEO_TS folder with something like VLC to make sure it's correct. If it isn't you can use dvdauthor to create the proper layout.

---

### Post by Neecapp on 2007-04-23
Yeah but the movie is 6.5gb and the dvd is 4.7gb so.. k3b won't shrink it. I guess this is a much longer process then I thought. (Using VobCopy.. I used to just copy it to my hd then use FixVTS and k9copy to finish it off.. but I just got a skipping movie from that.. even burning at 4x.. so going to try this and see if it fixes it)<sigh>

Also.. is there a graphic front end for DVDAuthor?

Thanks,
Neecapp

---

### Post by swoskow on 2007-04-25
> **Neecapp said:**
> 

Also.. is there a graphic front end for DVDAuthor?

Thanks,
Neecapp


Yes QDVDAuthor - it should be in the add/remove programs or get it through synaptic

---

