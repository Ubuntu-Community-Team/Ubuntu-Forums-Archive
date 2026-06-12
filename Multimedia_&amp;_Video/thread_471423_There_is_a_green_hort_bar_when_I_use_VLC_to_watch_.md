---
title: "There is a green hort bar when I use VLC to watch a mov file"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by yinglcs2 on 2007-06-12
Hi,

I using VLC 0.8.6 on ubuntu 7.0.4. When I use vlc to watch a mov file (transformers720p), there is a green hort bar in the screen.  I get the file from here: [http://www.mediafire.com/?eywmzynawny](http://www.mediafire.com/?eywmzynawny)

Can you please tell how to fix it?

I attached the screen shot.

---

### Post by luisbg on 2007-06-12
The video plays perfect in my computer.

My first suggestion is to check if you have the same problem with any other trailers from the site, all mov with the same codec, and compare it to other (like the mandela video that comes with ubuntu).

If the problem persists in all the videos you must have some issues with Xorg and VLC. Check the configurations of VLC.

Luis

---

### Post by osxdude on 2007-06-12
It looks like there are shadows. IDK why this is happengng. Change your Deinterlacing setting.

---

### Post by smithman89 on 2007-06-12
Hi, i read up on this when reading my monitor manual.  The green bar acts as some anchoring line (or something, they called it an anchor).  Its a monitor problem.  I have the line because im using a very old CRT monitor (still pretty kick ***, its 19" 1600x1200).

Edit:  Mine is different though, it only appears as a very thin line on the top and bottom of the videos.  Thats alot larger than the one i have.

---

### Post by nphx on 2007-06-25
VLC > Settings > Preferences > click Advanced options > Video > Output modules > Select alternative from Default, try out some other modules and see which one works best. Remember to click on Save after making changes.

---

### Post by Galphanore on 2008-03-11
Thanks nphx, I was having this problem and your suggestion fixed it in a snap.

---

