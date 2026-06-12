---
title: "Ripping CD's with tracks that blend together"
date: 2010-11-14
forum: Multimedia Software
---

### Post by Bartender on 2010-11-14
Sorry; I'm sure this has been asked before but a search didn't reveal anything obvious.

I've been ripping some of our CD's to .ogg and .mp3 for listening at work with a Sansa Fuze.  Have used RubyRipper but lately been using Rhythmbox.  The app finds titles online, and it's all pretty easy.

Some rips are louder or quieter and that's a little annoying.  But the biggest problem is with tracks that blend together and the app can't figure out how to dissect them.  The Eagles "Dalton" CD is a mess.  Also some Don Henley tracks, Creedence Clearwater, Stone Temple Pilots, etc.

I could use RubyRipper to rip the entire CD as one file.  Or use RubyRipper to rip just the troublesome tracks as one file.  Or maybe screw around with the tracks in Audacity?  Was hoping that some of you have better fixes.

---

### Post by aeronutt on 2010-11-14
For ripping, I use ripit, a command line tool.  I've never noticed any problem as you've described (but maybe I haven't ripped a CD with the attributes that would cause the problem).

Here's ripit with the options I run:

```
ripit --outputdir <location> --device /dev/cdrom --ripper 1 --coder 0 --lameopt "-V1 -q2 -ms" --quality off --genre "" --bitrate off --dirtemplate '"$artist/$album"' --playlist 1 --eject --save
```

---

### Post by Schrute Farms on 2010-11-14
One tip I can give is to make sure you use a ripper that uses LAME.  LAME seems to do a better job at gapless ripping.  I used RipperX in the past, until it started acting weird, then I switched to GRIP.  GRIP is a little bit of a pain to get set up the way you want it, but once it is, it works like a charm.  You can use RubyRipper with LAME, but I find RubyRipper to be too slow. If your CDs are in decent shape, I don't think they have to be double checked for errors.  You can usually set a ripper to use LAME somewhere in the preferences.  If you're not sure if you have LAME installed, it is in the repositories.

I know that the stock UI of the Fuze will still put small gaps between tracks.  If you use RockBox, it will play any LAME ripped mp3s without any gaps in between.  RockBox works great on my V1 Fuze.  It says it's still unstable for the V2, but I've heard it works fine as long as you start in the original UI before plugging in the USB.   [URL="http://www.rockbox.org"]WWW.Rockbox.org
[/URL] 
You can use Replay Gain to help your tracks all be at the same volume.  I've heard it works well, but I've never used it, so I can't help much there, besides saying Google it.

---

### Post by Bartender on 2010-11-15
Thanks for the ideas.

RubyRipper is awful slow, but I figured out the basics so stuck with it.  GRIP was too geeky for me!

I looked into Replay Gain.  The Sansa Fuze forums has a [how-to]("http://forums.sandisk.com/t5/Fuze/Replay-Gain-A-how-to-informational/td-p/104400").  It looked a little complicated, and I'm on dial-up just to make the downloading parts more fun.  I set that project aside months ago and haven't revisited.  Maybe it's time to try it.

EDIT: MediaMonkey is a Windows app, dangit.  They claim it'll run in WINE.  I'm trying to move AWAY from that other OS, but have gotten to the point where I'll use it if that's the path of least resistance.

---

### Post by Schrute Farms on 2010-11-15
Give RipperX a spin.  It is not nearly as geeky as GRIP.  Simple to set up.
The only problem I had with it is that it quit tagging any track after #10 for some reason, and only on one computer.  Other than that, it is pretty simple to use & works well.  Just because I had problems doesn't mean you will.

---

