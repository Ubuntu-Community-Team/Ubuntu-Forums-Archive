---
title: "FlacDecoder: Failed to open input. Error 5."
date: 2009-11-11
forum: Mythbuntu
---

### Post by boof1988 on 2009-11-11
When I try to play music (formatted as .m4a / .aac ) using Mythbuntu, I get the error indicated in the attached screenshot (and in the thread title).

I have no clue how to fix this.  The music files will play (in Terminal) using mplayer as well as using Rhythmbox.

Just don't understand what "FlacDecoder: Failed to open input. Error 5." means and how to fix it.

Any help is appreciated.

---

### Post by boof1988 on 2009-11-12
Bump please :)

Also... I have attached a screenshot for the same music (.m4a) file being played with mplayer.

Thanks again for any help with this.

---

### Post by boof1988 on 2009-11-12
Bump :)

---

### Post by boof1988 on 2009-11-13
I'm trying to bump the tread at different times of the day in order to get a different audience.

Hope it works.

:-k

---

### Post by boof1988 on 2009-11-14
Bump :)

---

### Post by boof1988 on 2009-11-14
Bump again.

;)

---

### Post by boof1988 on 2009-11-15
Again... Bump...

---

### Post by boof1988 on 2009-11-16
Bump... ;)

---

### Post by boof1988 on 2009-11-19
Bump :)

---

### Post by SiHa on 2009-11-19
Can you play any music at all? Someone had the same problem here:
[http://www.minimyth.org/forum/viewtopic.php?f=2&t=745](http://www.minimyth.org/forum/viewtopic.php?f=2&t=745), and it looks like it was because Mythmusic couldn't actually access the music files.
If this is ona remote frontend, you need the music folder from the backend shared (Samba / NFS) and mounted locally at the same place on the frontend.
Or, perhaps it's a permissions issue, does the Mythv group have read access to the files?

---

### Post by halj32 on 2009-11-19
have you tried installing ffmpeg??
I use kaffeine with the xine backend +ffmpeg
plays everything so far

---

### Post by gslug79 on 2009-11-19
> **SiHa said:**
> Can you play any music at all? Someone had the same problem here:
[http://www.minimyth.org/forum/viewtopic.php?f=2&t=745](http://www.minimyth.org/forum/viewtopic.php?f=2&t=745), and it looks like it was because Mythmusic couldn't actually access the music files.
If this is ona remote frontend, you need the music folder from the backend shared (Samba / NFS) and mounted locally at the same place on the frontend.
Or, perhaps it's a permissions issue, does the Mythv group have read access to the files?

+1

I had this problem some time ago after a clean reinstall on the the frontend. The music was on an NFS share mounted at /mnt/server-name and I had forgotten to symlink /var/lib/mythtv/music to the mount point.

---

### Post by boof1988 on 2009-11-19
> **SiHa said:**
> Can you play any music at all? Someone had the same problem here:
[http://www.minimyth.org/forum/viewtopic.php?f=2&t=745](http://www.minimyth.org/forum/viewtopic.php?f=2&t=745), and it looks like it was because Mythmusic couldn't actually access the music files.
If this is ona remote frontend, you need the music folder from the backend shared (Samba / NFS) and mounted locally at the same place on the frontend.
Or, perhaps it's a permissions issue, does the Mythv group have read access to the files?

Thanks for the help and the link.

The music files are on the same machine as the Master Backend with Frontend.  I'm pretty sure that Mythmusic had the correct path to the music files.  Using the word ***_had_*** because I had some other issues that I couln't fix as well so I decided to reinstall.

I suspect that it may have been a permissions error.  Since (I think) that I changed some permissions (can't remember why) around the time that I noticed that the music stopped working.

I could still play the files in mplayer.

Thanks again for your help and I'll try to remember this information next time I have trouble.

All The Best,
Boof1988

---

### Post by boof1988 on 2009-11-19
> **halj32 said:**
> have you tried installing ffmpeg??
I use kaffeine with the xine backend +ffmpeg
plays everything so far

I think that I had/have ffmpeg installed.

I'm not sure if I even need to have a full-blown Mythbuntu machine.  I'll try to do some research on using the packages you mention (kaffeine and xine) and see if they'll suit me or not.

Thanks for your help and good counsel,
Boof1988

---

### Post by boof1988 on 2009-11-19
> **gslug79 said:**
> +1

I had this problem some time ago after a clean reinstall on the the frontend. The music was on an NFS share mounted at /mnt/server-name and I had forgotten to symlink /var/lib/mythtv/music to the mount point.

Thanks for the advice...  I'll keep an eye out for this problem in the future.

Thanks for your help,
Boof1988

---

