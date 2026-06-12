---
title: "Audacity or Ardour?"
date: 2006-08-25
forum: Multimedia &amp; Video
---

### Post by SnakeFingers on 2006-08-25
I'm curious about the record/mix software forum members are using. This kind of app is an essential part of a studio, can anyone share their experiences (good or bad) with either Audacity or Ardour?

Thanks in advance,

Mark

---

### Post by zettberlin on 2006-08-25
> **SnakeFingers said:**
>  Audacity or Ardour?


Audacity is nice for jobs like doing very long recordings (like: live etc) and to bring a LP to CD.

For everything else Ardour is the Alpha and Omega on my Box.

It has all the important things for HD-Recording/Arranging/Mixing Audacity lacks:

- integrating perfectly with jack
- can be synced with sequencers (Muse works flawless)
- having single samples(regions) or a multitude moved on the timeline and from track to track as one wishes, while the track is being played.
- using/changing loopranges as the track is being played.
- having a professional mixer that allows plugins being used/changed in "realtime".
- complete automation with curves


Regarding stability and performance both seem to be on par. Audacity still has got  destructive editing functionality I often miss in Ardour - still it is no match for HD-Recording with many tracks and especially when it comes to overdubbing.

The main flaw of Audacity is, that it does not work with jack/alsa - if this is being changed, i would use it some more.

---

### Post by dolson on 2006-08-25
So far I have used Audacity as my only software in all of my songs (check my site) except for one (titled Originem) which I used ZynAddSubFX and Rosegarden, with a small bit of Audacity.

I am looking to migrate to Ardour though, because of a lot of the reasons that zettberlin mentioned. The thing is for me that Audacity doesn't require JACK, and I only wanted a multitrack recorder, with the bare minimum of effort required to learn it. My results were decent for a bedroom musician, I think, but Ardour can get me much closer to quality.

Audacity 2 is going to be better in many ways (using a newer portaudio I believe will allow ALSA and JACK), but Ardour 2 is also coming out, and it will be even better. It now has MIDI support in CVS MIDI branch, which I really hope is integrated ASAP.

Really, Audacity is a really good editor, and a basic multitracker, whereas Ardour is a really good multitracker with realtime modifications, automations, etc etc. So, it depends on what you want and need.

---

### Post by SnakeFingers on 2006-08-27
Dana, Zettberlin,

Thanks for the info on the relative strengths and weaknesses of the 2 packages. I'm not too interested in recording synths or keyboards. Mostly I will record acoustic guitar & vocals and edit digital field recordings. I've installed Audacity, and from what you've said, it may be the best tool for me.

Mark

---

### Post by zettberlin on 2006-08-27
> **SnakeFingers said:**
> Mostly I will record acoustic guitar & vocals


For this i would recommend Ardour very much.

> **SnakeFingers said:**
> 
 and edit digital field recordings.

Such jobs are indeed well done with Audacity. Yet if you want to cut very accurate (for loops etc), you´ll maybe have a look at Rezound. Rezound is not made for very large recordings so having those fieldrecordings digitized and basically cut with Audacity would be my first choice also.The resulting smaller  chunks could then be imported in Rezound to extract smaller parts with first-class accuracy/comfort.

---

### Post by dolson on 2006-08-28
Not sure why you would need ReZound and Audacity. You can zoom in far enough in Audacity that you can see each individual audio sample. The only thing I like more about ReZound is the red indicators where audio clips. But I live without it, generally.

---

### Post by zettberlin on 2006-08-28
> **dolson said:**
> Not sure why you would need ReZound and Audacity.

Because you can alter the length of a loop in Rezound while it is playing and thus you cannot only see but hear also, what you are cutting - KILLERFEATURE afaic. In Audacity i have to restart the loop everytime i move the selection a few samples.

Still Audacity performs much better with large recordings. I had an 80minutes Interview recorded in Rezound once and it took several minutes to refresh after zoom or move around in the file. The same recording loaded into Audacity gave no trouble at all. Rezound works great with files up to 7-8 min, real big chunks are better edited with Audacity or Ardour - so a combination makes sense to me.

---

### Post by dolson on 2006-08-29
Ah, yes, I understand now. That is a requested feature for Audacity, and I'm sure it'll make it to 2.0. Or at least I hope so. :)

---

### Post by bennyp on 2006-08-31
I much prefer Ardour. I find Audacity's interface to be not quite to my liking. Ardour takes some getting used to, but once one is settled in, it's much more logical that audacity's UI.

Check out my [Ardour tutorial](http://www.out-of-order.ca/ardourtut.php) if you want to get into the swing of it.

---

### Post by dolson on 2006-08-31
Hi bennyp... Thanks for the link to the tutorial.

Would it be possible to have this on my site? I would like to simply save these pages into a PDF file, and keep it on my server for archival purposes and link to you. If the link goes down, then I would have the PDFs available. I don't have time right now to write my own wiki page tutorials for Ardour, so this would be good to have in the meantime. It is hard to find good documentation for these applications.

---

### Post by bennyp on 2006-08-31
> **dolson said:**
> Hi bennyp... Thanks for the link to the tutorial.

Would it be possible to have this on my site? I would like to simply save these pages into a PDF file, and keep it on my server for archival purposes and link to you. If the link goes down, then I would have the PDFs available. I don't have time right now to write my own wiki page tutorials for Ardour, so this would be good to have in the meantime. It is hard to find good documentation for these applications.

Yeah, that would be okay. I'm hoping I'll be able to revamp the tut this fall when 2.0 comes out. I'll try to keep you informed.

---

### Post by Aliby on 2006-09-22
The Tutorial's link IS down. Where can wee access it?
NOTE: this is also a (broken) link on the Ubuntu Studio WIKI

---

### Post by dolson on 2006-09-22
I will put the link to the PDF backups I made on the site.

---

### Post by heydabop on 2006-09-22
I use Audacity a lot, I like all the effects it has. I've never even heard of Ardour, I'll have to check it out.

---

### Post by kellogs on 2006-09-25
I just tried Ardour and Rezound... well I find Ardour easier, and you can manage loops and samples easily, its a good way to sample all the loops I make in seq24. for now a good solution to the mess of having to open every synth and every preset on every song . ;) 

just one little thing, you have to manually put in the mixer/editor(look for the option somewhere) "Sync with jack" for it to work with all connected programs to jack.

---

### Post by bennyp on 2007-06-08
Hey folks, the [new tutorial]("http://www.out-of-order.ca/tutorials/ardour/") is almost finished, you can get a sneak peak at it though on my site out-of-order.ca. Please don't copy it until it's done, thanks.

Incidentally, if you'll be in the Toronto area June 17th, I'm running a workshop at the Linuxcaffé to highlight Ardour and other free audio apps.

[http://www.linuxcaffe.ca/node/22080](http://www.linuxcaffe.ca/node/22080)

---

