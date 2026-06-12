---
title: "DVD stops after first chapter"
date: 2008-08-05
forum: Multimedia Software
---

### Post by myrmidon666 on 2008-08-05
Hello,

I have spent the last two hours trying to fix this problem with no luck.

When I try to play a DVD everything is fine until the end of the first chapter. At the end of the first chapter I get different errors depending on the video player.

Movie Player (Default Ubuntu 8.04): Cannot read from source
VLC and Mplayer: video becomes choppy (or plays audio w/ no video or video plays for a few seconds and stops for a minute then plays again)and then crashes.

I have installed the libdvdcss2, libdvdnav4, libdvdread3, unbutu-restricted-extras packages. Then I installed gxine, vlc, and mplayer.

I also went through the steps to add the medibuntu repository for Hardy and I ran sudo /usr/share/doc/libdvdread3/install-css.sh

Any help would be appreciated. If you need logs you will need to tell me how to access them. Thank you.

---

### Post by hermes0710 on 2008-08-06
Do you get this behavior with every dvd? Seems like an I/O error (damaged dvd?)

---

### Post by unoodles on 2008-08-06
Hi, try this: open a terminal and type 'vlc'. Then open the disc in the vlc player. Look in the terminal and you will see the output of dvdcss cracking the CSS. Look through and make sure it was able to find all the keys.

---

### Post by myrmidon666 on 2008-08-08
Well, it looks like it's just one of those computer gremlins (or demons or fluke or whatever you want to call it). I just got done playing 20 other DVDs. Some of the DVDs were older and some were brand new and in between. 

When using VLC from the command line I get one line of output from each DVD played. Usually something about a52 decoder. The only DVD that has messed up out of 21 is the disk I wrote the post about. The DVD plays fine in my DVD player just not on my computer.

I have decided to re purchase the DVD and see if the problem still exists. I'm thinking the lens might be more sensitive to scratches on the computer. I'll post here to let people know the outcome of the repurchase or the use of other DVDs if it happens again.

Thank you both for your help.

---

