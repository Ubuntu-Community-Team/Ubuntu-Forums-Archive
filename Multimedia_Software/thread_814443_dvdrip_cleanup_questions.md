---
title: "dvd::rip cleanup questions"
date: 2008-05-31
forum: Multimedia Software
---

### Post by DarkW0lf on 2008-05-31
I would like to copy and watch my dvd's from a hard drive and had three things I am looking to find out if they can be cleaned up.

1. Chapter Navigation ?
I don't mean menus, just being able to select next/previous chapter. All attempts to copy just makes one big file with no chapters (Big file is okay but why not any chapters ? ).

2. Weird subtitles ?
Out of sync a little bit but for the most part okay. What's weird is that the color I think is white but turns sort of yellow when over a character's face or similar background. And it's not selectable (can't turn subs on or off in player).

3. Volume Level ?
Same volume as when used on a standalone player (well dvd::rip makes a good exact copy of that :P ) but since most of my DVD's are 5.0 being encoded to 2 channel I get the same problem as with my 2 channel standalone equipment, voices too quiet to hear (hence my use of subs) I thought I had dvd::rip set to correct that but maybe I don't.

DVD::rip works nice and these are the only things I would like to cleanup.

Dependencies in case there is something I need that I don't have.

```

  Program              Version   
  -------------------------------
  dvd::rip             0.98.6    
  transcode            1.0.2     
  ImageMagick          6.2.4     
  ffmpeg               SVN-rUNKNOWN,
  xvid4conf            not installed
  subtitle2pgm         not installed
  lsdvd                0.16      
  rar                  not installed
  mplayer              not installed
  ogmtools             1.5       
  dvdxchap             1.5       
  mjpegtools           not installed
  xine                 not installed
  fping                2.4       
  hal                  0.5.9     
  -------------------------------

```

---

### Post by DarkW0lf on 2008-06-28
Ping,

Well, anybody ???

---

### Post by DarkW0lf on 2008-08-01
I could probably live with the sound issues ( since it does copy the dvd reliably, the movie disc has the same effect with the audio on standalone equipment ).

I would like to however get chapter navigation ( just next/previous is enough ) and clean up subtitles a bit.

---

### Post by mc4man on 2008-08-01
Personally if i was ripping to the hdd and or making a back up or play disk, I'd keep it in mpeg2, dvd structure. For that you could use k9copy among others. Without the .ifo's your not going to have chapter navigation in a normal sense.
As far as the subs dvd:rip can either render them onto the video (always on ) or create a vobsub file (on or off, not compatible with 'chapters')

As far as 'chapters' it does that by creating separate files.

losing the orig. audio stream would be a no go at least for me

> Most DVD titles are divided into chapters. With dvd::rip's chapter mode you will have one file per chapter after transcoding. You can select all or individual chapters. Note, that you can't combine chapter and cluster mode.
Note that vobsub creation (refer to subtitles) is disabled in chapter mode. 

> dvd::rip supports the first two. transcode can render one subtitle straight on the movie. The disadvantage: the subtitles aren't optional anymore, you can't switch them off. Also it's not possible to have more than one subtitle with your movie.

With vobsub files switching off is still possible. A vobsub file mainly contains the original DVD subtitle stream. A vobsub capable movie player (e.g. mplayer) can read vobsub files and renders the subtitles on-thy-fly. You can have more than one stream in a vobsub file. The quality is the same as of the original DVD. So having subtitles in vobsub files is really a good choice. 

from [http://exit1.org/dvdrip/doc/concepts.cipp#concept_rip_mode](http://exit1.org/dvdrip/doc/concepts.cipp#concept_rip_mode)

---

### Post by DarkW0lf on 2008-12-20
I don't recall any option regarding ifo's in dvd::rip and am not familiar with k9copy.

I was trying a mostly straight forward process to play dvd's from harddrive.

So if I need the ifo for chapters, k9copy can do that right ?

---

### Post by bcondemi111 on 2008-12-21
Have many problems with DVDRIP. I have a firewire dvd player and is mounted and can read and play any dvd. When I use ripdvd to save the movie on my drive, get error messages and it can't read the dvd in the player. what am I doing wrong?

BC

---

### Post by DarkW0lf on 2008-12-26
Under storage (the first tab) do you have the firewire drive selected ?

Anyone know where I can find subtitle2pgm ? It isn't in the repos.
It is dvd::rip dependency if I want to edit subtitles and I can't find it.

---

### Post by kiloraw on 2008-12-31
I just downloaded dvdrip and copied a dvd and it split the dvd into different vob files,
Is there a way I can make it only have one vob file?

---

