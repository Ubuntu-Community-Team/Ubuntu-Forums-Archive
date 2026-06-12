---
title: "Vlc ffmpeg AMR and 3GP video problems"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Digitallysick on 2009-07-21
I can't play 3GP videos with any audio, I can't convert them either. I have tried many guides and its not working

My understanding is ffmpeg removed the amr audio, how can I fix this?

---

### Post by andrew.46 on 2009-07-21
Hi Digitallysick,

> **Digitallysick said:**
> My understanding is ffmpeg removed the amr audio, how can I fix this?

This is partly true. The *latest* svn FFmpeg no longer compiles against the amr wrapper script + libraries kindly provided [by this gent]("http://www.penguin.cz/~utx/amr") and thus it will also no longer compile against the amr -dev files held by Medibuntu. However both the svn MPlayer and the svn FFmpeg will now compile against the libopencore-amr libraries:

[http://ubuntuforums.org/showpost.php?p=7584660&postcount=409](http://ubuntuforums.org/showpost.php?p=7584660&postcount=409)

The svn MPlayer recognises these libraries when installed in this way and no './configure' changes are required. Just to confuse the issue a little older versions of MPlayer and FFmpeg will play amr files using the non-free libraries :-).

All the best,

Andrew

---

### Post by Digitallysick on 2009-07-21
You really have to give this to me in laymens terms, I have tried every amr file I can download, or make and it doesn't work. I have vlc , I don't know how to get this working =( 

sadly i'm stuck with these stupid files until I can convert them to something else

---

### Post by andrew.46 on 2009-07-21
Hi Digitallysick,

> **Digitallysick said:**
> You really have to give this to me in laymens terms, I have tried every amr file I can download, or make and it doesn't work. I have vlc , I don't know how to get this working =( 

sadly i'm stuck with these stupid files until I can convert them to something else

My apologies, I am often told that I make things sound too complicated :-). Most software available under Ubuntu will *not* come with support for amr, this includes vlc, FFmpeg and MPlayer. This is because amr is a proprietary format, somebody owns it and expects to be paid for its use.

If it is legal in your country of origin there are several ways around this:

[LIST=1]
[*]**vlc**: This can be compiled with support for amr and my own copy is compiled in this way. I am not sure where you can download a vlc package that has been compiled in this way.
[*]**MPlayer**: This can be compiled with support for amr. Packages compiled in this way can be found in the [Medibuntu repositories]("https://help.ubuntu.com/community/Medibuntu").
[*]**FFmpeg**: This can be compiled with support for amr and is your best bet for converting these files. I am not sure whether a package exists that is compiled in this way but you would not go wrong by following [the Fakeoutdoorsman's guide]("http://ubuntuforums.org/showthread.php?t=786095") and the [extra post on amr]("http://ubuntuforums.org/showpost.php?p=6320667&postcount=9").
[/LIST]

Having said all of this be prepared for the fairly ordinary sound with most amr files :-). I can see that you are keen for a vlc option, perhaps somebody here can suggest a vlc package that has been compiled against the amr libraries?

All the best,

Andrew

---

### Post by mc4man on 2009-07-21
You really should post what release of ubuntu you're using, in cases like this it does make a difference.

Unlike the sanity shown by mplayer vlc doesn't provide it's own ffmpeg libraires and is affected to some degree by the ffmpeg libs it's built off of and more so by installed ffmpeg shared libs.
For amr you need vlc built off of  amr enabled ffmpeg libs and amr enabled ffmpeg libs installed

In the case of amr vlc uses avcodec (libavcodec) to decode amr, if your libavcodec isn't able to decode amr then vlc won't either.

For the most part vlc doesn't care what libavcodec uses to decode, just that it can and ultimately does. (there are some senarios where it will but I don't think that's an issue here, if you are building ffmpeg and vlc then it might

If you get a pop up from vlc that samr is not supported, blah, blah then that **usually** indicates your ffmpeg libs were built without amr support.

If the video plays with no pop up and no sound then that **usually **indicates your missing the appropriate lib's for ffmpeg (libamr* or while unlikely in this case the opencore ones

(usually refers to having a vlc built off of a arm enabled ffmpeg libs, which maybe as prev. noted hard to find

this short post shows vlc can play amr, and the decoder used. (note that those 2 exact lines will show whether the 'older' libamr* libs are used or the new opencore ones

[http://ubuntuforums.org/showthread.php?p=7405287#post7405287](http://ubuntuforums.org/showthread.php?p=7405287#post7405287)

So post what release of ubuntu (or xubuntu) your using

---

### Post by andrew.46 on 2009-07-22
Hi mc4man,

> **mc4man said:**
> In the case of amr vlc uses avcodec (libavcodec) to decode amr, if your libavcodec isn't able to decode amr then vlc won't either.

Thanks for pointing that out I had not realised that this was the case. My blindness to this fact was due to the fact that I did not examine [alien bob's script]("http://connie.slackware.com/~alien/slackbuilds/vlc/build/vlc.SlackBuild") closely enough, it is explicitly pointed out there in the not so fine print :-).

Thanks again!

Andrew

---

### Post by mc4man on 2009-07-22
What Im finding is that it appears that one would need to build their own vlc and ffmpeg to enable arm in ubuntu and vlc.

None of the repo, ppa versions will play, even with the unstripped ffmpeg libs, libarm*, ect. ect. (or even a built arm enabled ffmpeg


I've gotten in the habit now of building ffmpeg as a package set with shared libs in /usr.
The advantage there is you get unstripped libs and matching -dev's (plus any patches one chooses to add. 

(( it is surprisingly easy to do, for hardy I've built/rebuilt most all of the media packages and plugins and created a local repo

Because of that I thought arm playback was a piece of cake, obviously not, apologizes to those having trouble.

The potential hassle now would be if you build the 'new' ffmpeg, one would need to rebuild vlc off of it. (only for arm, nothing else is affected atm, again basing what I see from building, installing vlc as a package set

For arm mplayer seems to be the best choice, vlc the worst

Edit:
happened to be on a jaunty live cd tonight, vlc will now play arm audio or video with arm audio only when built off of  arm enabled ffmpeg libs and only when those libs are also available as shared.

---

### Post by andrew.46 on 2009-07-22
Hi

> **mc4man said:**
> For amr mplayer seems to be the best choice, vlc the worst

And I just triple-checked by installing the Jaunty Medibuntu MPlayer and it most definitely supports amr 'out of the box':

```

andrew@skamandros:~$ mplayer | head -n1 && mplayer -ac help | grep amr
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
ffamrnb     ffmpeg    working   AMR Narrowband  [libamr_nb]
ffamrwb     ffmpeg    working   AMR Wideband  [libamr_wb]

```

I am a big fan of MPlayer so perhaps a little biased but it seems MPlayer always comes out on top :-).

Andrew

---

