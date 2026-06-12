---
title: "Movie Player and VLC media player not playing DVD"
date: 2011-08-01
forum: Multimedia Software
---

### Post by rx170 on 2011-08-01
Hi 
When playing coyright protected DVD's in Ubuntu 10.10: the following errors occur:
Movie Player Error message:
Error occured Could not read from resource
VLC media Player Error message:
Playback failure:
DVDRead could not read block 0.
Non copyright protected DVD's play fine

Any help would be appreciated Thanks!

---

### Post by beew on 2011-08-01
Did you install libdvdcss2?

---

### Post by rx170 on 2011-08-01
I did

---

### Post by rx170 on 2011-11-22
I am responding to myself long time later
figured it out inserted a dvd with region code2 it played fine.
I never got an error message when playing a dvd with region code 1.
Changing the region code fixed the problem

sudo regionset 

is the command then I changed it to region code 1
all set

---

### Post by boazjones on 2011-11-23
Thank you for the info. This is taken from the link within the Ubuntu Forums:

[http://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](http://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)


Open a Terminal and type:

sudo apt-get install libdvdread4

sudo /usr/share/doc/libdvdread4/install-css.sh

    Rebooting may be necessary. 



Using Oneiric Ocelot (Linux kicks butt - all day... everyday)

---

