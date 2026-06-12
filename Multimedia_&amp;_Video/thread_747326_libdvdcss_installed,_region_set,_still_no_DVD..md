---
title: "libdvdcss installed, region set, still no DVD."
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by whistlingtony on 2008-04-06
Hi All,

I picked up two DVDs yesterday: Harry Potter and the goblet of fire and Harry Potter and the order of the phoenix. The latter plays fine. The former doesn't play at all. The disc looks fine, no scratches. I had this problem with another disc too, although I can't remember the name now.

I've been watching DVDs for a while now with no problem. I didn't change anything in my system beyond the usual updates.

libdvdcss2 is installed. Libdvdnav and libdvdread are installed. 

I looked through the forums. It seems I'm not the only one having this problem.
[http://ubuntuforums.org/showthread.php?t=641239](http://ubuntuforums.org/showthread.php?t=641239)
[http://ubuntuforums.org/showthread.php?t=194469](http://ubuntuforums.org/showthread.php?t=194469)
[http://ubuntuforums.org/showthread.php?t=98988](http://ubuntuforums.org/showthread.php?t=98988)

I have tried VLC, Mplayer, Totem, Xine, and Kaffeine.  no luck. Out of desperation I recently used regionset to set my region. That didn't change a thing.

My repositories are set to use medibuntu. I'm going to set them to Marillat and see if they have a newer version of libdvdcss2, libdvdnav, or libdvdread. 

Help!!!!!  

Thanks all,

-Tony Diethelm

P.S.
Totem error is: The source seems encrypted, and can't be read. Are you trying to play an encypted DVD without libdvdcss?

tony@Tony-VostroLinuxLappy:~$ totem dvd://dev/dvd

libdvdnav: Using dvdnav version 1.1.7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HARRY_POTTER_GOBLET_OF_FIRE
libdvdnav: DVD Serial Number: 33934297
libdvdnav: DVD Title (Alternative): HARRY_POTTER_GOBLET_OF_FIRE
libdvdnav: Unable to find map file '/home/tony/.dvdnav/HARRY_POTTER_GOBLET_OF_FIRE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001af
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00009c35
libdvdread: Elapsed time 0
libdvdread: Found 1 VTS's
libdvdread: Elapsed time 0
libdvdnav: Using dvdnav version 1.1.7 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: HARRY_POTTER_GOBLET_OF_FIRE
libdvdnav: DVD Serial Number: 33934297
libdvdnav: DVD Title (Alternative): HARRY_POTTER_GOBLET_OF_FIRE
libdvdnav: Unable to find map file '/home/tony/.dvdnav/HARRY_POTTER_GOBLET_OF_FIRE.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

---

### Post by wolfen69 on 2008-04-06
another totem error? typical. i'm not saying you have to do this, but i always go to synaptic and uninstall totem and totem related. and i never have a problem after that. i have noticed totem *can* conflict with certain things. might be worth trying.

---

### Post by mc4man on 2008-04-06
if you can't get it going ( goblet of fire) post vlc output from terminal. That title would have had structure protection, where the later release (order of the phoenix) didn't (region 1 at least). In any event the s.p. shouldn't affect vlc.
if you tried playing first in totem you could try going into home directory >.dvdcss , find the folder for goblet of fire and delete it. Then try vlc again
+1 for removing totem in gutsy - no problems leaving in hardy though

---

### Post by warp99 on 2008-04-06
The trouble with the disc you are have please place it in the DVD tray, open a terminal and enter the following:

```
export DVDCSS_METHOD=title && totem dvd:// 
```

Does the encrypted DVD play?

---

### Post by whistlingtony on 2008-04-06
Thanks for the replies!

export DVDCSS_METHOD=title && totem dvd:// 

The above worked, movie played in Totem... Err... What does that mean?

After that I went in and deleted ~/.dvdcss/HARRY_POTTERetcetcetcOF_FIRE. VLC then ran it without a problem.... Er... What does that mean?

So.. What's my fix?

---

### Post by warp99 on 2008-04-06
Add the following string to your bashrc file:

```
echo "export DVDCSS_METHOD=title" >> ~/.bashrc
```

Edit:

From the libdvdcss readme file:

> Running lidvdcss
================

The behaviourof the library can be affected by changing two environment
variables:
  DVDCSS_METHOD={title|disc|key}: method for key decryption
    title: decrypted title key is guessed from the encrypted sectors of
           the stream. Thus it should work with a file as well as the
           DVD device. But it sometimes takes much time to decrypt a title
           key and may even fail. With this method, the key is only checked
           at the beginning of each title, so it won't work if the key
           changes in the middle of a title.
    disc: the disc key is first cracked ; then all title keys can be
           decrypted instantly, which allows us to check them often,
    key: the same as "disc" if you don't have a file with player keys at
           compilation time. If you do, the decryption of the disc key
           will be faster with this method. It is the one that was used by
           libcss.
           This is the default method,
  DVDCSS_VERBOSE={0|1|2}: libdvdcss verbosity
    0: no error messages, no debug messages (this is the default)
    1: only error messages
    2: error and debug messages

You see libdvdcss is not a specification, it's a hack. A very good one, but nevertheless still a hack. So sometimes it has a problem decoding certain DVDs with it's default parameters. If you run into trouble with different DVDs you can quickly change the environment by using the 'export DVDCSS_METHOD={title|disc|key}' string or make it permanent by adding it to your .bashrc file.

---

### Post by whistlingtony on 2008-04-06
Thanks Warp!

So, a fix, and an explanation. Thanks.

Ah, there's nothing like breaking federal laws to watch my own DVD on my own laptop.

---

### Post by big dizzle on 2008-04-12
> **warp99 said:**
> The trouble with the disc you are have please place it in the DVD tray, open a terminal and enter the following:

```
export DVDCSS_METHOD=title && totem dvd:// 
```

Does the encrypted DVD play?

ok, when i try to just play the dvd (in my case aliens resurection, original dvd, not a copy) i get the following:

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

I install the suggested plugins, and still get the same message.

When I try the command you are suggesting from the terminal (export DVDCSS_METHOD=title && totem dvd://), I get the following...

Could not open location; you might not have permission to open the file.

I'm at a loss.  I can't get any dvd's to work.  none of them are copies.  do i need to chmod something?

---

