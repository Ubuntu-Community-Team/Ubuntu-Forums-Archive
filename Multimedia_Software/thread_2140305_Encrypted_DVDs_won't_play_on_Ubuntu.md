---
title: "Encrypted DVDs won't play on Ubuntu"
date: 2013-04-29
forum: Multimedia Software
---

### Post by nitrox26 on 2013-04-29
Hello everyone,

I am sorry if this has already been posted, but I haven't found an answer to my problem yet.
I have recently installed Ubuntu 12.04 on my girlfriends notebook and she now complains that her DVDs won't play in VLC or any other video player.
Whenever I try to insert a DVD and open it up with VLC player, it just crashes without any error message or similar. Also MPlayer and SMplayer don't work.
I might add that certain other DVDs do play. The movies we are talking about in specific are
So Undercover, region code 2, does not work
some twilight movie, region code 2, also does not work

however, tv series like Gossip Girl, region code 2 as well, do work.

Now I have of course done my reserach on this topic and found out that

1. either libdvdcss2 is not installed --> it is, I checked and I have tried it with different sources (from the "regular" Ubuntu repository, the medibuntu repo and some others)
2. libdvdread4 or similar are not installed --> also they are installed
3. sudo /usr/share/doc/libdvdread4/install-css.sh was missing --> I've done that too
4. the region code of the DVD might be wrong --> the DVDs have region code 2, whereas the computer is from Canada (which is in the code 1 region). I have also used regionset to set the code of the DVD drive to 2 but it somehow still doesn't play.

I have no idea what could be the cause of this problem but I would be really thankful for any help.

Thanks for your effort in advance, 

nitrox26

---

### Post by andrew.46 on 2013-05-11
Can you try to run one of the troublesome dvds from the commandline and then post the complete terminal output here? Something like the following should do:

```

mplayer -mouse-movements -nocache dvdnav://

```

This will hopefully have a few hints in the terminal output...

---

### Post by trovador on 2013-05-21
Hi I've a similar problem and I haven't Idea how to run a dvd from terminal could you post the command pleae ?
Thank you

---

