---
title: "Creative Zen 4GB"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by zergling on 2007-11-14
Hi everyone,
I open this thread because I would like to buy the creative zen 4 gb
[http://www.amazon.com/Creative-Zen-4-GB-Black/dp/B000UV4EU6/ref=sr_1_15?ie=UTF8&s=electronics&qid=1195068098&sr=1-15](http://www.amazon.com/Creative-Zen-4-GB-Black/dp/B000UV4EU6/ref=sr_1_15?ie=UTF8&s=electronics&qid=1195068098&sr=1-15)
But, my worry is.. Can I use this device with Ubuntu? Can I rip my favorite dvd movie such as Space Balls in the Zen ? Is this a good device or should i get another deice? if so, which one?
Bye and Thanks for your help :)
Ciao!

---

### Post by little_penguin on 2007-11-22
The very latest Creative Zen 4GB media player (also available as 8G or 16GB) is NOT compatible with linux. I know this first hand - bought it myself and had to return it - it turns out it is MTP only, so it can only be used with Windows. The usual tips about using Gnomad2 and libmtp did not work for this player either (despite people having had success with earlier Creative Zen models like the Creative Zen Vision M).

---

### Post by Libertino on 2008-02-04
my creative zen 4GB didn't work at all in 7.10. After updating libmtp and gnomad2 from the Jbbr.net repository to version 0,25 and 2.91 respectively I was finally able to copy files to the player. however, i am still looking for a way to play songs from the player directly. rhythmbox doesn't do it yet on my system, allthough also updated from the jbbr.net repository.

in opensuse 10.3 updating amarok to amarok-xine allowed copying files to and from the player. however, amarok too doesn't play songs from the player

---

### Post by Libertino on 2008-02-28
Finally , after deleting and reinstalling Rhythmbox from the jbbr.net repository it plays music  from the Player. So, the Creative Zen 4GB is not incompatible with Linux.

---

### Post by yabbies on 2008-02-28
I just bought a creative zen 4gb.

I really enjoy it. As I do have windows on a laptop for smooth transitioning, I have gotten it to work with ubuntu thanks to tiagoboldt

and this [walkthrough]("http://tiagoboldt.net/blog/creative-zen-linux/")

The good news is it works with linux.
The bad news is that you like or use amarok or rhythmbox you will no longer be able to keep them installed. Cause they use an old version libmtp6 and you need to use and create a newer version libmtp and libmtpfs.

it works like a charm. Good Luck

---

### Post by mendieta on 2008-03-05
Thank you guys for posting your experiences. I just got this beauty as a present. I read this thread, so I decided to boot directly into my Kubuntu 8.04 (hardy) partition (still in alpha, as of this posting). I already had an "MTP Device" configured in amarok, and using this same device I was able to copy music right away. 

Awesome !

---

### Post by stoanhart on 2008-03-06
> The bad news is that you like or use amarok or rhythmbox you will no longer be able to keep them installed. Cause they use an old version libmtp6 and you need to use and create a newer version libmtp and libmtpfs.

After you compile libmtp, during the "checkinstall" phase, you are asked to specify the version of the software for the .deb file. I believe if you set the version to "0.2.6-0ubuntu3" and make sure the package has the same name of "libmtp6" you may be able to reinstall amarok/rhythmbox. 

Afterall, they check for libmtp6 >= 0.2.1-0ubuntu3 as a dependency. Give that a shot. I just ordered this player for my girlfriend's birthday, so I will be trying this shortly.

Pascal

---

### Post by thedaylights on 2008-03-07
> **yabbies said:**
> I just bought a creative zen 4gb.
The good news is it works with linux.
The bad news is that you like or use amarok or rhythmbox you will no longer be able to keep them installed. Cause they use an old version libmtp6 and you need to use and create a newer version libmtp and libmtpfs.


Have you tried this thread?
[http://ubuntuforums.org/showthread.php?t=662567&highlight=amarok+zen](http://ubuntuforums.org/showthread.php?t=662567&highlight=amarok+zen)

---

### Post by omega_user on 2008-03-09
I too have been thinking of getting an MP3 player.  My old ipod 30gb Video seems to have disappeared.  However, I now am completely off windows and don't own any way of running a windows machine (refused to set up a dual-boot and now cant undo cus I used XFS).  I would really like to get either the small Creative Zen or a larger Zune 80, but both seem to be either completely unusable (Zune) or irritating to get to work (Zen).  I truly don't want to have to use Windows again, but the current market in MP3 Players is making me doubt linux and the mp3 player manufacturers.  MTP is a pointless feature to me and I like arranging all my stuff in raw filesystem form, I don't even use a music organizer like Rythmbox.

So If any of you know a straightforward, nice, and supportive mp3 player (ie Ubuntu Gutsy, Xvid, .flac and the whole 9 yards) please tell.

*note: iRiver?

---

### Post by hinge on 2008-05-27
Hi,

I just bought a ZEN 4 GB - really nice, but also really hard to get working under linux.
I run Kubuntu 8.04 and in the long run I'd like to get the device up and running with amarok.
I've tried to install libmtp, mpt-tools and mtpfs via some of the guides sugested here. I am somewhat successful;
I can detect the device both via dmesg/lsusb and mtp-detect, but the latter is veeeeery slow. I can mount the device using mtpfs but when I try to list the dir content in is again veeeery slow and it only lists one dir - 'Playlists' no subfolders in there or anything else.
I've noticed that every time I connect or mount to the device the screen (on the device) goes black and I can only do that one command - after that I'll have to reset the device (on the needle hole reset button) to be able to connect again....

Has anybody else seen anything like this ?
I have tried on two computers - my regular with kubuntu and a spare with ubuntu - same result.
I have the newest firmware on the device.

I'd be glad to post more output....

pretty please...

---

### Post by mendieta on 2008-05-27
> **hinge said:**
> Hi,

I just bought a ZEN 4 GB - really nice, but also really hard to get working under linux.
I run Kubuntu 8.04 and in the long run I'd like to get the device up and running with amarok.

Hi

Is this the device?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16855102033](http://www.newegg.com/Product/Product.aspx?Item=N82E16855102033)

See my post above, it works just fine for me in Kubuntu 8.04. It does not get autodetected, but it works fine as an mtp device. Also: for data transfers, it works just fine in gnomad2. 

Incidentally, I gave this as a present to someone who runs winxp, and it was so, so, so much harder to get it working there (many reboots, re-install the software, all in all a couple hours work, YMMV)

Cheers!

---

### Post by hinge on 2008-05-28
> **mendieta said:**
> Hi

Is this the device?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16855102033](http://www.newegg.com/Product/Product.aspx?Item=N82E16855102033)

See my post above, it works just fine for me in Kubuntu 8.04. It does not get autodetected, but it works fine as an mtp device. Also: for data transfers, it works just fine in gnomad2. 

Incidentally, I gave this as a present to someone who runs winxp, and it was so, so, so much harder to get it working there (many reboots, re-install the software, all in all a couple hours work, YMMV)

Cheers!

Hi mendieta,

You are not experiencing extreme slowness ? 
And you followed this [link]("http://tiagoboldt.net/blog/creative-zen-linux/")

I cannot run the last command when installing libmtp:
```
sudo checkinstall -D make install
```

Solved that by just doing a 
```
make install
```

Did the whole procedure again just now - same result :confused:

---

### Post by mendieta on 2008-05-29
> **hinge said:**
> Hi mendieta,

You are not experiencing extreme slowness ? 
And you followed this [link]("http://tiagoboldt.net/blog/creative-zen-linux/")


No, and no :-) 

It's working just fine, out of the box, in 8.04. It didn't work at all in 7.10, because the device was newer than the software (btw, your signature says Kubuntu Gutsy, but I guess you are running Hardy)

Some people, in 7.10, chose to upgrade libmtp, doing things like the ones described in the link you referred ... but this is not needed anymore.

Best

---

### Post by pedrotuga on 2008-05-30
It works with gnomad2 for me, except for the videos.

On creative's website it says that is supports mpeg4 videos. Do they mean that it's possible to convert from that format? If so, that's pretty disonest comercial.

Anyway... any tips why my videos won't work? They simply don't show in the player. Do they need to be in some special format? which one?

---

### Post by hinge on 2008-05-30
Hi,

just wanted to report in...I got everything working just now.

Everything can be apt'ed (libmtp7, mtp-tools, mtpfs) out of the repository. Even works with directly in amarok.

The reason to my problems were solved after I used the windows app ZEN media explorer to completely format the device.

And yes I use Hardy - despite my signature (I'll change ut as soon as I'm done playing with my ZEN)

I love (K)ubuntu - thank you

---

### Post by mendieta on 2008-05-31
> **pedrotuga said:**
> 
Anyway... any tips why my videos won't work? They simply don't show in the player. Do they need to be in some special format? which one?

I am bumping your question up since I am having a similar same issue. I can see the video files are there, but they invariably crash the device. I tried with avi's created by my Canon photo camera, I tried decoding and encoding in different formats, I always failed. It would be nice to hear from someone who actually succeded.

I don't use windows at all, but their windows software converts your videos into whatever crap they support. They should support several video formats, and at least exit gracefully, not just crash and force you to reset!

Other than that, I love the player ...

---

### Post by hinge on 2008-06-01
The specification to the Video format on ZEN is xvid in 320x240 - otherwise it will not play. I use mencoder to reformat my video for the device. E.g.

```

mencoder {name_of_infile} -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,scale=320:240    -o {name_of_outfile}


```

I have set the bitrate to 200 which seems OK for cartoons (my kids use the device when going on long cartrips). If it is a real movie the bitrate may need to be set higher.

Please post back if this does not help

Hinge

---

### Post by mendieta on 2008-06-01
> **hinge said:**
> The specification to the Video format on ZEN is xvid in 320x240 - otherwise it will not play. I use mencoder to reformat my video for the device. E.g.

```

mencoder {name_of_infile} -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,scale=320:240    -o {name_of_outfile}


```


Hinge, you made my day! And my next car/plane trips with my little ones a lot easier :-)

One little thing is: the output filename needs to have the avi extension apparently. 

Thanks so much! Cheers!

---

### Post by hinge on 2008-06-02
Well, you helped me too - now we're even ;-)

---

### Post by Metaleks on 2008-06-05
The player seems to work as an mtp-device.  I can do all sorts of things with it via mtp-tools.  But, it doesn't seem to work with Amarok  :(  Any ideas?

EDIT:  It works fine in Rhythmbox...maybe if I reinstall Amarok?

EDIT:  Nada.  Very interesting.  I wonder what the issue could be.

---

### Post by hinge on 2008-06-05
Mine worked as described in post #15 in this thread. I did not do anything in amarok. I mount it using mtpfs...
Have you tried that ?

hinge

---

### Post by Metaleks on 2008-06-05
Thanks, but it didn't work.  In any case, I've switched over to Banshee (staying true to my GNOME roots ;)).  It recognizes it perfectly just like Rhythmbox.  And it synchronizes it well...version 1.0 will be out later this week, and I'm liking what I'm seeing so far.  It's no Amarok, but it certainly has a cleaner interface, and it's feature rich (and it has a video feature, so I can transfer music and videos now to my Zen).  Couldn't be happier!

Another compatible media player on Linux it seems.

For those of you wondering, libmtp7 is an absolute must, and all that's needed, to get your system to recognize your zen.  Thanks again, Hinge. :)

---

### Post by mendieta on 2008-06-22
> **hinge said:**
> The specification to the Video format on ZEN is xvid in 320x240 - otherwise it will not play. I use mencoder to reformat my video for the device. E.g.

```

mencoder {name_of_infile} -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,scale=320:240    -o {name_of_outfile}

```


One more time, thanks so much Hinge. I wrote a little bash function to do this to a bunch of files sequentially (encoding takes a long time):


```

zen-convert ()
{
    for i in $@;
    do
        mencoder "$i" -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_typ
e=mpeg -vf pp=de,scale=320:240 -o "$i".avi
    done
}

```

This goes in .bashrc. Then, in a directory with, say, flash videos, I do "zen-convert *.flv" and go for a coffee ;-)

---

### Post by hinge on 2008-06-29
Really cute mendieta,

Just tried it out. Funny thing I have used linux (kubuntu) as my sole OS for years now, but I have never used .bashrc - I just never came across it.

But I will be using in the future 

I still have one problem with the videos that I convert. I can not fastforward or rewind them on the zen - can you do that ?
I can do it in mplayer.

Hinge

---

### Post by mendieta on 2008-07-05
Sorry for the delay, just back from a trip

> **hinge said:**
> 
Funny thing I have used linux (kubuntu) as my sole OS for years now, but I have never used .bashrc - I just never came across it.


Yes, it's pretty useful. Whatever you define works as a built-in, you can do things like "type zen-convert" and see what it does.

> 
I still have one problem with the videos that I convert. I can not fastforward or rewind them on the zen - can you do that ?
I can do it in mplayer.


Same here! But I don't think it's the encoding, I think the zen doesn't have this function ... or I couldn't find it

I have a worse problem I discovered when I really watched a full video: audio goes slower than video, and the clip finishes early. Pretty annoying. But I am using exactly the same command  as you. The difference, perhaps, is the source, I am decoding flash video from youtube (that I get with youtube-dl). If you have a clue how to fix it, it would be great. I'll google for it too ...

---

### Post by mcallenSchmee on 2008-07-15
> **hinge said:**
> The specification to the Video format on ZEN is xvid in 320x240 - otherwise it will not play. I use mencoder to reformat my video for the device. E.g.

```

mencoder {name_of_infile} -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,scale=320:240    -o {name_of_outfile}


```

I have set the bitrate to 200 which seems OK for cartoons (my kids use the device when going on long cartrips). If it is a real movie the bitrate may need to be set higher.

Please post back if this does not help

Hinge

I used this and the video plays, but it won't fast forward or rewind. Does anyone else have the same problem?

---

### Post by Jompa on 2008-07-16
How do you get videos to work in Banshee? Music works fine, but I can't play, see or transfer movies.

---

### Post by hinge on 2008-07-16
> **mcallenSchmee said:**
> I used this and the video plays, but it won't fast forward or rewind. Does anyone else have the same problem?

Yep, I have that same problem - I believe that I posted a question about it.

Meanwhile I have bought a 4 GB SD flash card and when I put the same movies on that card I have no problems. This makes me think that it is the MTP that does something to the xvid - or maybe the palyer it self...

The way I do it now is that I put pictures and music on the internal storage and video on the sd flash card...easy way to solve that, and cheap, I payed 15 EUR / 20 USD for the 4 gb sd card.

Of cause it wold be nice if someone came up with the right solution

Hinge

---

### Post by Jompa on 2008-07-17
> **hinge said:**
> The specification to the Video format on ZEN is xvid in 320x240 - otherwise it will not play. I use mencoder to reformat my video for the device. E.g.

```

mencoder {name_of_infile} -oac mp3lame -lameopts abr:br=128  -ovc xvid -xvidencopts bitrate=200:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,scale=320:240    -o {name_of_outfile}


```

I have set the bitrate to 200 which seems OK for cartoons (my kids use the device when going on long cartrips). If it is a real movie the bitrate may need to be set higher.

Please post back if this does not help

Hinge

What do I write in {name_of_infile} and {name_of_outfile}? Tried writing the address of the file, but it didn't find it.

---

### Post by Metaleks on 2008-07-17
> **Jompa said:**
> What do I write in {name_of_infile} and {name_of_outfile}? Tried writing the address of the file, but it didn't find it.
Assuming you're in the directory of the file you want to convert, *{name_of_infile}* should become YOUR_FILE_NAME.WHATEVER, and your *{name_of_outfile}* should be the name of whatever you want your new file to be! It can be anything.

---

### Post by Jompa on 2008-07-17
I get this error every time:
> MEncoder 2:1.0~rc2-0ubuntu13 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz (Family: 6, Model: 15, Stepping: 13)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
File not found: '{Scrubs.S06E06'
Failed to open {Scrubs.S06E06.
Cannot open file/device.

---

### Post by mcallenSchmee on 2008-07-17
> **hinge said:**
> 
I still have one problem with the videos that I convert. I can not fastforward or rewind them on the zen - can you do that ?
Hinge

I can fastforward and rewind videos if I transfer them using banshee 1.0. The version in the repos can't handle video. I got 1.0 from [_getdeb_]("http://www.getdeb.net/app/Banshee") . Also, if anyone is wondering, IRiverter works for converting videos.

---

### Post by Jompa on 2008-07-18
I got it to work using IRiverter and the newest banshee, thanks alot :D

---

