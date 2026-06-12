---
title: "VLC DVD &quot;leaking pictures&quot; playback problem"
date: 2008-12-12
forum: Multimedia Software
---

### Post by bedhead75 on 2008-12-12
I just did a fresh install of Ubuntu Ibex 8.10 (64-bit) on a new system.  I installed VLC and then installed the necessary libraries to watch DVDs ( sudo apt-get install libdvdread3 libdvdcss2 ubuntu-restricted-extras libdvdnav4 ).  When I run VLC from the terminal and open the disk, I can access the main DVD menu fine, but when I click to play the movie, the video window just closes, and shortly after I get the following error in the terminal:

[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap

    I had no problems watching DVD's in Hardy 8.04 on my old 32-bit system.  Does anyone have a fix?

---

### Post by razy60 on 2008-12-12
Have you tried mplayer its in add/remove, I found that i had better luck with movies using that than vlc.

Raz

---

### Post by euriconeto on 2009-04-10
> **bedhead75 said:**
> I just did a fresh install of Ubuntu Ibex 8.10 (64-bit) on a new system.  I installed VLC and then installed the necessary libraries to watch DVDs ( sudo apt-get install libdvdread3 libdvdcss2 ubuntu-restricted-extras libdvdnav4 ).  When I run VLC from the terminal and open the disk, I can access the main DVD menu fine, but when I click to play the movie, the video window just closes, and shortly after I get the following error in the terminal:

[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap

    I had no problems watching DVD's in Hardy 8.04 on my old 32-bit system.  Does anyone have a fix?

Same here. I had ubuntu 8.10 and both Totem and VLC worked fine. After upgrading to Jaunty none works for any DVD.

Any help?
Cheers,
Eurico

---

### Post by grzen on 2009-06-13
> **bedhead75 said:**
> I just did a fresh install of Ubuntu Ibex 8.10 (64-bit) on a new system.  I installed VLC and then installed the necessary libraries to watch DVDs ( sudo apt-get install libdvdread3 libdvdcss2 ubuntu-restricted-extras libdvdnav4 ).  When I run VLC from the terminal and open the disk, I can access the main DVD menu fine, but when I click to play the movie, the video window just closes, and shortly after I get the following error in the terminal:

[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap
[00000573] main decoder error: decoder is leaking pictures, resetting the heap

    I had no problems watching DVD's in Hardy 8.04 on my old 32-bit system.  Does anyone have a fix?

I'm seeing something very similar on my laptop... With Ubuntu 8.10, my DVDs played relatively well, but since the upgrade to 9.04 the performance is just poor: the sound is not synchronised and the video stream itself can't be followed by a human being, it's just a random arrangement of squares moving around the window...

Same errors (?) in the vlc command line:[INDENT][FONT=Courier New][00000487] main decoder error: decoder is leaking pictures, resetting the heap
[00000487] main decoder error: decoder is leaking pictures, resetting the heap
[00000492] main video output error: picture to date 0x8baa714 has invalid status 6
[00000492] main video output error: picture to display 0x8baa714 has invalid status 6
[00000487] main decoder error: decoder is leaking pictures, resetting the heap
[00000487] main decoder error: decoder is leaking pictures, resetting the heap
(...)
[/FONT][/INDENT]Anyone seeing the same?

Thanks!
Nicolas

---

### Post by PhilMaster on 2009-06-24
Same problem with Jaunty 64-bit. Solved by choosing video output X11 in the 'Tools > Preferences > Video' menu.

---

### Post by grzen on 2009-07-11
To follow up on my previous post, I ended up installing the [latest]("https://launchpad.net/%7Ec-korn/+archive/vlc") version of VLC.
Also made sure I had the latest libdvdnav4 as per instructions found [here]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Ubuntu%209.04%20%28i386,%20amd64%29").
... so that DVD/VLC-related packages now looked like:
nicolas@hugin:~$ dpkg -l | grep -e "dvd\|vlc"
ii  dvd+rw-tools                                       7.1-4
ii  libdvdcss-dev                                       1.2.10-0.2medibuntu1
ii  libdvdcss2                                              1.2.10-0.2medibuntu1
ii  libdvdnav4                                            4.1.3-3
ii  libdvdread4                                           4.1.3-4ubuntu2
ii  libvlc2                                                       1.0.0-1~ppa3
rc  libvlccore0                                           0.9.9a-2ubuntu1
ii  libvlccore2                                            1.0.0-1~ppa3 
ii  mozilla-plugin-vlc                           1.0.0-1~ppa3
ii  vlc                                                               1.0.0-1~ppa3
ii  vlc-data                                                   1.0.0-1~ppa3
ii  vlc-nox                                                     1.0.0-1~ppa3
ii  vlc-plugin-pulse                                1.0.0-1~ppa3
(my apologies for the poor rendering of the above list)

After that, I've retried playing DVDs and the segmentation fault had disappeared, though DVD playback was still failing with the following errors:
 VLC - "libmpeg2 decoder error: invalid picture encountered"
 totem - "An error occured: The source seems encrypted, and cannot be read. Are you trying to play an encrypted DVD without libdvdcss?"

Not sure if this was an improvement or not... I then decided to create a new user to test, and guess what? DVDs were playing OK!!!
Since I could not be certain how long I had tried to be playing DVDs with an incorrect combination of libdvdcss and libdvdread, I then deleted the whole content of my user's ~/.dvdcss directory. This appears to have solved the last errors I was getting.
So far, all the DVDs I've tested appear to be playing correctly in both VLC + totem, including ones notorious for being encrypted/not correctly formatted - including BBC DVDs, old "art & essai" B&W movies, etc...

---

