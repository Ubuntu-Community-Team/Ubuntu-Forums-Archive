---
title: "Banshee and m3u Playlists"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Niva on 2011-05-08
Hello everyone.  I'm sure there's a better place for this than the Ubuntu forums but I want to post about it and hopefully get a good answer.

I just upgraded to 11.04 and I see Banshee is the default now instead of Rhythmbox.  It appears that Banshee has capabilities to generate playlists, and import playlists... but none of that works for me.  At least without reading the documentation.

Can Banshee read an existing m3u playlist without going through some voodoo/terminal magic?

Note: Rhythmbox did that quite easily.  Surprises me such a simple feature would give me trouble on the new default under Ubuntu.

---

### Post by Funkey Monkey on 2011-07-30
> **Niva said:**
>  It appears that Banshee has capabilities to generate playlists, and import playlists... but none of that works for me.


 I am having difficulties importing .m3u playlist created by Banshee into Banshee.

 I recently formatted my pc, and I am now trying to import my backed up playlists. With no success.  Could you please guide me (point me) in the correct direction to figure out how to get my playlists imported into Banshee?

 Regards,
Funkey Monkey

---

### Post by madelus on 2011-11-06
Don't know if you solved it, but if not, here is how it works:

See into playlist file - there are **relative paths** in it. 
Confusing thing is that they are **relative to the place where you've saved your m3u file while exporting**!

So an entry in m3u looks like this (Muzyka is name of the Music folder in polish):
../../../Muzyka/Metallica/Death Magnetic/Metallica - The Unforgiven III.mp3
While importing paths in m3u file must be relative to the place where this file now is.

If the Muzyka folder is in your home directory then - for example:
1. place m3u file on desktop
2. edit m3u file in gedit and replace all ../../../ to ../ and save it (ctrl+h would help)
3. import playlist from this file

This worked for me.

---

