---
title: "subtitles for xine and fullscreen for VLC"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by mojoman on 2007-01-02
Hi,

I have two problems with media player that I sure could use some help with. I use xine or VLC and both are great player but...

1) Xine won't play subtitles. Actually, none of my players will save VLC. I tried checking the various tracks for subs. I made sure that the .sub-file has the same name as the .avi-file (it's usually, but not always, .sub and .avi). They are in the same folder. I tried with different movies and subs, that I know work in VLC or in BS-player under windows. I'm freash out of ideas on this one. ](*,)  

Now, I would just leave it at that and just stick to VLC (which, IMHO, is almost as good as xine) but...

2) When I go fullscreen with VLC I still got that ugly bar on top of the window as well as the Gnome bar visible. That's not a pleasent movie experience... This problem has been up for discusion before ( [http://www.ubuntuforums.org/showthread.php?t=87085&highlight=vlc+full+screen](http://www.ubuntuforums.org/showthread.php?t=87085&highlight=vlc+full+screen) ) but, hey, it's still a problem ;) 

I got Totem as well but I hate it and I also have MPlayer but it hates me and none of them play my subs anyway. Given a choice I would really like to stick with xine but I really need those subtitles.

Does anyone has a take on this? :-k 

Best regards
/Mojoman

---

### Post by mojoman on 2007-03-11
Just an update. I got fullscreen for VLC going (for quite some time now).  It was just a setting but it is very contra-inuitive (or, my mind just doesn't work the way other's do, which would also explain it).

However, the subtitles are still a problem. VLC seem to play all subtitles. Xine only plays .srt. How come?

/Mojoman

---

### Post by jocheem67 on 2007-03-12
Well, I've tested .ssa and .sub ( microdvd ) and they do work in totem.

I think you need to get the extension right:

'bb.avi"  goes with "bb.ssa"....

totem just picks them up, these are by the way both downloaded subs and ones I ripped myself.

By the way: xine does not load subs that are directly ripped from a dvd ( extension also .sub )..

You need to convert those to .srt or .ssa or another format that's text-based.

Maybe this is your problem?

Mplayer and VLC do play those subs ( directly from dvd ) but text-based subs are better, and readable by stand-alones....

---

### Post by mojoman on 2007-03-13
Ok, looks like I'm getting somewhere!

I tried an .avi with .srt. and it worked liked a charm in any player. Tried another .avi with .sub and it didn't work in any of the players. 

All the subs I got are downloaded so I guess I have to convert any .sub in order to play them. Google gave me some tips on ow to convert them, among other with a pearl script. Do you have anything else to recommend as a nifty converter?

VLC is a nice player, especially now that I got the fullscreen going, and it's fairly good with subtitles as well and between it and Xine I'm all set. :popcorn: 

Thanks!
/Mojoman

---

### Post by jocheem67 on 2007-03-13
Yeah


Try subtitle-editor, it converts easilly every subtitle in a lot of formats. 

.sub is an extension used by more formats, maybe it's going wrong there. If your .sub files are images, then you have to do a conversion into text-based subtitles... If not, just convert the .sub files into .srt or .ssa or .smi...

for your player .srt seems to work allright, so I suggest using that format. I prefer .ssa  ( sub station alpha ).

One of therse days I'll write a tutorial on subtitle ripping and editing in ubuntu. I've been struggling for a long time, but I seem to have found some good ways dealing with them.

Her's the link for subtitle-editor: [http://repository.debuntu.org/](http://repository.debuntu.org/)

It requires some editing of your sources.list but nothing complicated.

Let me know if it worked out?

---

### Post by mojoman on 2007-03-14
Hi,

Sounds very interesting and I added the repo but I got this when I ran apt-get update:
```

Failed to fetch http://repository.debuntu.org/dists/dapper/Release  Unable to find expected entry  multiverse/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

It might just be temporary down so I'll give it a go later. When I did a apt-cache search for the package it didn't show up but that's probably just because my apt-get update didn't connect.

I'll check again tomorrow and post back then.

All the best
/mojoman

---

### Post by jocheem67 on 2007-03-15
well, I guess you can also put in the other repositories ( edgy / feisty ). After all, it's only bout subtitleeditor which is the same for all releases.

again about subtitles: it's all about trial and error.

I've got a Peekton stand-alone with a hacked firmware. I've been messing around with the thing extensively. His reading of subs is rather tricky, it reads .srt but only with a certain encoding, (utf-8 and iso-something ). Totem and vobsub under xp read all subs I throw at them mostly, but standalone players are kind of tricky.

mplayer and vlc are known to be the best readers in linux, but they are not that user-friendly I feel.

i'm thinking of buying a combined machine that's certified for "nero-digital"...I wanna encode then with x.264 instead of xvid 9 ( avidemux rocks ), way better quality with that codec. Ideal would be a machine that's also capable of recording television. The kiss-dp600 seems okay , is not that expensive but cannot record.....hmmmmm....i'll just keep on dreaming.....

Keep me posted. Cheers.

---

### Post by mojoman on 2007-03-17
Hi,

Still no luck with subtitleeditor for dapper and I'm suspecting that it's connected to me running 64-bit BUT I had a look at the debian etch repositories and sure enough, there it was. So, I installed it on my laptop instead (which is running on 32-bit etch with fluxbox) and it installed fine. I couldn't read .subs (not recognizing the format) but I'm gonna go RTFM for subtitleeditor and see what I can come up with. When I started it I got a "can't find config: config" message so this is probably what I need to fix and I'll try to find some time for it during the weekend. 

Thanks for the help! I'll keep you posted.

---

