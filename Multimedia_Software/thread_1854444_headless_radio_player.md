---
title: "headless radio player"
date: 2011-10-04
forum: Multimedia Software
---

### Post by Bradburts on 2011-10-04
Hi,
I want to build a headless radio player.
I have installed mpd 0.15.4.
A lot of the popular UK stations won't play and give the error:
 
ERROR: problems decoding "[http://mediasrv.musicradio.com/2CR](http://mediasrv.musicradio.com/2CR)"
How do I debug this?
How would I identify the media format being used?
 
I have attempted compiling and installing mpd 0.16.4 but ended up with even fewer supported formats. Figuring out the build is going to take me a while!
 
I nervous about spending more time with mpd as I cannot even find the streams to bbc services e.g. bbc radio 1, so I am not sure that using mpd will get me what I want.
 
Is mpd the right solution? Should I be looking at using some other server/player for UK and especially bbc radio stations?

---

### Post by wolfen69 on 2011-10-04
[http://mediasrv.musicradio.com/2CR](http://mediasrv.musicradio.com/2CR) works for me in vlc player. I went to Media>Network Stream and pasted it in and hit play. No problem. You need to have the proper codecs to stream properly.

---

### Post by Bradburts on 2011-10-05
Thanks. 
Don't think that I can run vlc player headless.
 
I will need the right codecs of course. I am looking for some 'get started help' especially how to recognise the formats and how to shoehorn into mpd. 
For example if I download the [[COLOR=#000000]http://mediasrv.musicradio.com/2CR[/COLOR]]("http://mediasrv.musicradio.com/2CR") I get:
 
[Reference]
Ref1=http://mediasrv.musicradio.com/2CR?MSWMExt=.asf
Ref2=http://81.20.48.50:80/2CR?MSWMExt=.asf
 
None of these links work inside mpd either.
 
I don't know what file type I am looking at and therefore cannot check for version/patch compatability.
I think that .asf is a media container but don't know how to find the stream inside.
 
PS 
I got the bbc streams working by downloading the .asx files and cutting & pasting the mms streams into mpd. 
Lot happier with the prospects of mpd now but do need to figure out how to deal with each format; recognising a format would be a start!

---

### Post by collisionystm on 2011-10-05
I know you are building a media player... I found something cool the other day. Ever heard of GeexBox? It is worth checking out.

---

### Post by aeiah on 2011-10-05
try mplayer. it can run headless and play streams fairly easily. its also fairly verbose when things go wrong.

the only advantage of mpd in this instance is that you can easily output to different sound interfaces and create a playlist of radio stations.

oh, and [mpd also runs nicely on an openwrt router]("http://mightyohm.com/blog/2008/10/building-a-wifi-radio-part-1-introduction/") :guitar:

---

### Post by Bradburts on 2011-10-05
Thanks, both look interesting.
Shame GeeXboX would be a dead end for me, ARM support is limited to a couple of systems and expensive systems at that. 
I will give mplayer a go. I assume that mplayer has remote clients like mpd?
As long as I have a command line I should be able to knock some scripts together and create a playlist manager similar to mpc.
 
 
Still looking for advice on how to recognise the various streams if anyone can point.
AFAIK asf uses wma and mpd works with wma,
I am guessing then that I just need to identify the stream in [[COLOR=#000000]http://mediasrv.musicradio.com/2CR[/COLOR]]("http://mediasrv.musicradio.com/2CR") 
I am guessing that the format is asx but its different to other examples I have seen. What format is this url? How do I identify the supported stream?

---

### Post by wolfen69 on 2011-10-05
> **Bradburts said:**
> 
Don't think that I can run vlc player headless.


Yes you can.

---

### Post by Bradburts on 2011-10-05
Great, lots of choice.
mplayer copes with the streams I have given it so far. Won't do asx directly but copes with the manually extracted link.
Only uses 5% of my VM CPU & 14Mb. mpd uses 30% and 11Mb.
Off to find a command line playlist manager.

---

### Post by andrew.46 on 2011-10-06
> **Bradburts said:**
> mplayer copes with the streams I have given it so far. Won't do asx directly but copes with the manually extracted link.

Try adding the *-playlist* option and MPlayer should play these streams...

---

