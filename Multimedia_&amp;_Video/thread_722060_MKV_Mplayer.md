---
title: "MKV Mplayer"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by turtlesarefunny on 2008-03-12
I've tried to find a solution for this, but after a bit of Googling, I'm getting absolutely nowhere.

What's the best way view MKV files with A S S subs? VLC can play the actual audio and video, but the subtitle rendering is wrong, but MPlayer won't even play MKV for me, and I don't know how to enable it (I have downloaded the CCCP and it works in VLC, anyway).

I prefer VLC to MPlayer, so is it possible for it to work there? I doubt it would be, but you never know.

If not, how do I get MPlayer to play MKVs? Every time I try, an error pops up that says "Video:Cannot read properties"

---

### Post by yabbadabbadont on 2008-03-12
You might try the only other major video player in linux, xine.

Install either xine-ui or gxine (both use the xine-lib backend) and see if they can play them.  You'll probably want to use gxine as it is a native Gnome application and is easier to use and configure than is xine-ui.

---

### Post by eye208 on 2008-03-12
> **turtlesarefunny said:**
> If not, how do I get MPlayer to play MKVs?
I have a MKV file with A.S.S. subtitles here, and MPlayer plays it just fine. Maybe yours is broken?

---

### Post by sloggerkhan on 2008-03-12
I use smplayer mplayer front end. Don't have any trouble. Sometimes ubuntu is behind the latest version, and if so, then I get it from the project website.
In smplayer, in the subtitles preferences (ctrl-p), just make sure the ssa/*** subtitles box is checked and you'll get the nice subs you're used to.

---

### Post by 6205 on 2008-03-12
For MKV in Mplayer you will probably need [COLOR="Blue"]x264[/COLOR] and [COLOR="Blue"]libmatroska0[/COLOR] packages, because many matroska videos are using this codec...VLC should play MKV videos without a problem, but installing those packages won't hurt anyway...

---

### Post by turtlesarefunny on 2008-03-12
> **eye208 said:**
> I have a MKV file with A.S.S. subtitles here, and MPlayer plays it just fine. Maybe yours is broken?
I installed it with Synaptic, but mine won't play MKVs for some reason. I have no idea what to do. >_<

> I use smplayer mplayer front end. Don't have any trouble. Sometimes ubuntu is behind the latest version, and if so, then I get it from the project website.
In smplayer, in the subtitles preferences (ctrl-p), just make sure the ssa/*** subtitles box is checked and you'll get the nice subs you're used to.I got it from the source, and though I've read through how to compile and can go through the motions, it still confuses me, since I'm a complete newbie. :/

> or MKV in Mplayer you will probably need x264 and libmatroska0 packages, because many matroska videos are using this codec...VLC should play MKV videos without a problem, but installing those packages won't hurt anyway..
I'll try that and see what happens.

edit: got those packages, and mplayer still won't play the MKVs

> You might try the only other major video player in linux, xine.

Install either xine-ui or gxine (both use the xine-lib backend) and see if they can play them. You'll probably want to use gxine as it is a native Gnome application and is easier to use and configure than is xine-ui.
If nothing else works, I suppose I could try that :)

Thank you for the replies so far

---

### Post by sloggerkhan on 2008-03-12
I used *.deb file to do smplayer...
Installing from source isn't too bad, but it's kinda messy.

---

### Post by turtlesarefunny on 2008-03-13
[Well, this is the result of SMPlayer]("http://www.flickr.com/photos/24631177@N04/2330659440/")

It's a step up from absolutely nothing. Kinda trippy.

Seems to only be Matroska. Just to make sure it wasn't something else, I tried an AVI and it worked perfectly.

Edit: Argh, MKV used to at least play with messed up subtitles in VLC, but now it won't even start.

---

### Post by sloggerkhan on 2008-03-13
you do have w32codecs installed, right?

Also, what is set as your video overlay?

---

### Post by turtlesarefunny on 2008-03-13
I believe I'm using xv.

I just added the win32 codecs, and it works now!

---

### Post by fosix on 2008-07-10
> **eye208 said:**
> I have a MKV file with A.S.S. subtitles here, and MPlayer plays it just fine. Maybe yours is broken?

which version do you use? Dapper? I am using Dapper but mplayer doesn't play mkv sound

---

