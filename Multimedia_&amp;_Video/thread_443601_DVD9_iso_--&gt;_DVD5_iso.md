---
title: "DVD9 iso --&gt; DVD5 iso?"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by tuckie on 2007-05-14
I'm using my ubuntu box to store full size rips of my DVDs for easy viewing over the network.  What I would like is a command line driven application that can take the iso (This may require mounting the iso, which I'm fine with) and convert it to a DVD5 (ala dvdShrink) so that I can then burn the disk onto a single layer dvd.  Thanks in advance!

---

### Post by Emerzen on 2007-05-14
I've used xdvdshrink, k9copy, and DVD9t5 to accomplish shrinking iso's for burning to single layer.  I believe they are all frontends for CLI tools, but I'm not familiar w/ the CLI use of them.  I believe they're all available in the repo's or Automatix.

However, for streaming I suggest a more compact container.  I use AcidRip to shrink my movies and stream them w/ VLC.  -Have fun.

---

### Post by tuckie on 2007-05-14
I had found the DVD9t5 app just by looking through the package manager, but I couldnt get it to recognize the mounted iso (and it isnt cli driven)  As for streaming over the network, I just use the full size isos via samba to my xbox running xbmc, which works fine.

---

### Post by Emerzen on 2007-05-14
k9copy should be in the repo's and I xdvdshrink is available via automatix.  i use k9copy most frequently though xdvdshrink is more configurable.  I should mention that dvdshrink can be run under wine too.  let me know if you have any trouble with these suggestions.

---

### Post by Emerzen on 2007-05-14
I forgot: w/ dvd9to5 you don't need to mount the dvd, just point it to the correct drive.  If you've already ripped the movie as an iso to your harddrive, then you would have to mount it.  But, I think you have to point it to the VIDEO_TS folder in the directory the iso is mounted under.

---

### Post by tuckie on 2007-05-14
Now... can any of this be done completely from command line?  I have a folder filled with movie iso's that are full size, and would like to easily burn some of them onto dvd, but would like to come up with a script to make the process easier (run script, type in moviename, generate dvd5 iso).

---

### Post by Emerzen on 2007-05-14
I'm sure that any of these programs can be done through the command line as they are all graphical front-ends to command line tools.  My suggestion is to go to the home page of any of the above where they will typically describe the programs that they act as the frontend for.  From there you can research the command line tool per se to learn how to use it.  Hope that helps.

---

