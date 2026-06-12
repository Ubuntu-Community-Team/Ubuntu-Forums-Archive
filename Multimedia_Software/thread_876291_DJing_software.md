---
title: "DJing software"
date: 2008-07-31
forum: Multimedia Software
---

### Post by PCessna on 2008-07-31
Hello all, I am a DJ for an Internet Radio station, and I need a program to allow me to broadcast my music out to a shoutcast server (that runs on Linux :P). I'm a nuub with programs for linux lol, and I'm not exactly sure what to get, and before I go digging though add and remove programs, Does anyone have any suggestions?

Winamp I don't see on their site for Linux or though program manager, so I highly doubted and doubt it will be available for Linux

Cheers
-PCessna

---

### Post by djxcon on 2008-07-31
I am using Icecast and Ices2 to broadcast a music stream; however I do not believe that this will broadcast to Shoutcast at this time.  

Instead, it broadcasts to:
[http://dir.xiph.org/]("http://dir.xiph.org/")

While you are on the hunt for a shoutcast program...you may want to look into Icecast/Ices2 in the mean time.

You may also want to check out Internet DJ Console (though I have not used it):
[http://ubuntuforums.org/showthread.php?t=423715]("http://ubuntuforums.org/showthread.php?t=423715")
[http://ubuntuforums.org/showthread.php?t=488602]("http://ubuntuforums.org/showthread.php?t=488602")

---

### Post by Rumel on 2008-07-31
I think VLC might do it.

---

### Post by PCessna on 2008-07-31
No suggestions work. More please, or I count it impossible to DJ on Linux :[

---

### Post by DGortze380 on 2008-07-31
I quick google search turns up this source package for broadcasting to a shoutcast server from audio card/cd/mp3. ;)

[http://www.shoutcast.com/download/broadcast.phtml](http://www.shoutcast.com/download/broadcast.phtml)

This also turned up in a quick google search. Might help.
[http://forums.winamp.com/showthread.php?postid=1283812](http://forums.winamp.com/showthread.php?postid=1283812)

Some success with WinAMP on WINE.
[http://forums.winamp.com/showthread.php?threadid=253846](http://forums.winamp.com/showthread.php?threadid=253846)

And some info an VLC and Streaming to Shoutcast.
[http://ubuntuforums.org/showthread.php?t=423715](http://ubuntuforums.org/showthread.php?t=423715)

Just takes a little searching and configuration, I haven't found a single thing you absolutely, totally can't do on Linux. Some things just take a little longer and some extra work.

---

### Post by tuxxy on 2008-07-31
LMMS is worth a look

[http://packages.ubuntu.com/gutsy/sound/lmms](http://packages.ubuntu.com/gutsy/sound/lmms)

> LMMS aims to be a free alternative to popular (but commercial and closed- source) programs like FruityLoops, Cubase and Logic giving you the ability of producing music with your computer by creating cool loops, synthesizing and mixing sounds, arranging samples, having more fun with your MIDI-keyboard and much more

Open terminal and type,

```
sudo apt-get install lmms
```

If no look search for lmms in synaptic

---

### Post by mondoUNC on 2008-07-31
Audacious or XMMS are both winamp clones, I know XMMS has a ton of plugins but i don't know if they stream. Might be worth checking out though.

Look for them, and all the plugins in Synaptic

---

### Post by PCessna on 2008-08-01
:mad:

NONE of these suggestions work. I need a program that streams, not a program that MAY stream, or can SOMEWHAT stream, or STREAM TO A SPECIFIC LOCATION. I need a program that completely do the SAME as WinAmp without wine, WinAmp doesn't work properly through wine, I've already tried it and wasted my time. 

At this Point, **Windows** is the _only_ operating system that can *DJ* through *shoutcast*.

---

### Post by DGortze380 on 2008-08-01
> **PCessna said:**
> :mad:

NONE of these suggestions work. ... I need a program that completely do the SAME as WinAmp without wine, 

Then go install windows. We're trying to help you figure it out, but it will take some searching and some trial and error. If you need something asap that is identical to winamp, then use winamp.

---

### Post by bsund on 2008-08-02
[http://web.bethere.co.uk/idjc/](http://web.bethere.co.uk/idjc/)

Seems to do what you want.

---

### Post by PCessna on 2008-08-02
> **bsund said:**
> [http://web.bethere.co.uk/idjc/](http://web.bethere.co.uk/idjc/)

Seems to do what you want.
Come ON. It doesn't lean you stream, Crashes on hardy, and a already said I didn't want it and it didn't work..

I guess I'll just wait for a real answer.

---

### Post by DGortze380 on 2008-08-02
> **PCessna said:**
> Come ON. It doesn't lean you stream, Crashes on hardy, and a already said I didn't want it and it didn't work..

I guess I'll just wait for a real answer.

Alright, really now. We're trying to help you out here. And instead of looking for yourself, putting some work into finding something, or at least being grateful for the fact that total strangers are trying to help you you're going to criticize them for it.

Go ahead and wait as long as you like. I gave you your answer. You want WinAmp, not any substitute go use WinAmp and stop being a jacka&& to the people tryign to help.

---

### Post by PCessna on 2008-08-02
> **DGortze380 said:**
> Alright, really now. We're trying to help you out here. And instead of looking for yourself, putting some work into finding something, or at least being grateful for the fact that total strangers are trying to help you you're going to criticize them for it.

Go ahead and wait as long as you like. I gave you your answer. You want WinAmp, not any substitute go use WinAmp and stop being a jacka&& to the people trying to help.

I understand your point, but how dare you call me a donkey's butt because you're so mad.

If you'd like to make a point, Just don't say the word. I've already learned my lesson, but seeing you've been here almost a year really someone should of got your 'REAR END' into shape.

Please think before using even censored insults. You said the word with fancy characters, and it insults me. Thanks so much for the help, but not for the insults.

-PCessna

---

### Post by DGortze380 on 2008-08-02
> **PCessna said:**
> I understand your point ... Thanks so much for the help, but not for the insults.

-PCessna

Now that is appropriate. Thank You. I apologize for offending you.

---

### Post by PCessna on 2008-08-07
Anyone else :(

---

### Post by chele on 2011-08-01
A bit late, perhaps, but the folks who develop [Airtime]("http://www.sourcefabric.org/en/products/airtime_overview/") recommend [Mixxx]("http://www.mixxx.org/").

Both are in active development, it is recommended to use the sourcefabric repository and the mixxx ppa, instructions for both are on the respective websites.

---

