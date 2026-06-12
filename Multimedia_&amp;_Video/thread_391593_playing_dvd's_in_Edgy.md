---
title: "playing dvd's in Edgy"
date: 2007-03-23
forum: Multimedia &amp; Video
---

### Post by drumkitcat on 2007-03-23
Hi,

I'm running Ubuntu 6.1 Edgy on a Toshiba Satellite A40 laptop which has a dvd combo drive.

Can someone tell me what software is available to be able to play dvd movies on my laptop?

I often travel with work, and it's nice to drop in a movie to watch at night, but at the moment I haven't been able to find anything that will play dvd movies.

Any suggestions?

---

### Post by yabbadabbadont on 2007-03-23
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Read through that and if you have any questions, please post them.

---

### Post by drumkitcat on 2007-03-30
> **yabbadabbadont said:**
> [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Read through that and if you have any questions, please post them.

Ok, thanks.  I've installed the "libdvdread3" package from the repository.  
I did a reboot, and put a commercial dvd (ie, not a copied dvd) into the dvd combo drive on my laptop.

Totem is the default player for some reason... and it came up with an error message saying "Totem could not play 'dvd:///media/cdrom0'.  No URI handler implemented for "dvd".

I then tried it with Mplayer, and get an error saying "error opening/initializing the selected video_out (-vo) device"

How can I go about fixing this?

---

### Post by drumkitcat on 2007-03-30
Ok, never mind - I did look through the forum using the tag 'dvd' and found a thread where it showed how to implement the totem-xine and lib-codecs etc required.

I followed the procedure and it works perfectly!! (although, after installing the libdvdcss, and other packages, there was suddenly about 95mb of updates for me to install...ugh..) but anyway, the problem is solved, and now I can play dvd's perfectly on my Toshiba laptop.

Thanks everyone for your help - these forums are amazing!  (although sometimes you do have to be patient, and sometimes you do have to dig a little to find what you're looking for..but yeah, awesome!!)

---

### Post by FNGtyler on 2007-03-31
I am  having problems getting  mplayer to work. well dvd's period
I download and installed libdvdread3
then i opened up terminal and typed
sudo /usr/share/doc/libdvdread3/install-css.sh
everything seemed to go fine
i then put in a purchased copy of office space loaded mplayer
and i get the following error
"error opening/initializing the selected video_out (-vo) device"

any ideas?

---

### Post by drumkitcat on 2007-03-31
hi,
sorry I cannot post a direct link to the solution as I'm on my pda. But, the answer is here:
1. in this multimedia & video thread type 'dvd' in the search box, or look for the thread titled "playing dvds" - it lists the procedure and it worked beautifully right away ending with "now get the popcorn, you're done"

hope that helps!
Paul

---

### Post by johnny4north on 2007-03-31
i had to set the Preferences-Audio to "OSS/ioctl audio output" Video to "xv X11/Xv" and checked the "Enable direct rendering" Click OK restart Mplayer ..you also need to add the Repositories 
go here for more info - [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

