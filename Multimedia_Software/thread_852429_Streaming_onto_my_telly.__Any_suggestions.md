---
title: "Streaming onto my telly.  Any suggestions?"
date: 2008-07-07
forum: Multimedia Software
---

### Post by the lemming on 2008-07-07
I have an Ubuntu laptop and a Vista desktop which I have just managed to network together quite happily so that they can share my MP3 and MP4 files.

My ultimate goal is to be able to stream my MP4 movies onto the telly but I don't know how to go about this or more to the point what to buy so I would appreciate some advice or recommendations.

Does anybody have any suggestions for streaming media content onto a telly, which uses a SCART plug, by using either Ubuntu or Vista?

Cheers

---

### Post by the lemming on 2008-07-12
Bump

Anybody able to advise me?

Cheers

---

### Post by bossa on 2008-07-12
I have never done done this ,but dont you just need the right cable and use you TV as the monitor.

[http://www.youtube.com/watch?v=eWRzYMsNEZM](http://www.youtube.com/watch?v=eWRzYMsNEZM)

Hope this helps

---

### Post by Lycus on 2008-07-12
> **the lemming said:**
> Bump

Anybody able to advise me?

Cheers

Apparently, assuming your current videocard supports multiple outputs, you'll just need to get a converter device to convert that connection to a SCART one. I had to actually look-up what SCART was, it doesn't exist here in the States.

So, see what outputs your videocard supports, then get an appropriate converter (unless you can find a videocard with native SCART output), and you'll have to configure your videocard's settings, which will be an altogether different matter of discussion.

Edit: Just noticed you're using a laptop (as your sig says). So, you may have to look for a VGA or DVI to SCART adapter of some sort. May even have to go through a couple of adapters/converters (e.g., VGA to composite, composite/audio to SCART).

Good luck.

---

### Post by the lemming on 2008-07-12
> **Lycus said:**
> Apparently, assuming your current videocard supports multiple outputs, you'll just need to get a converter device to convert that connection to a SCART one.


Hello

I tried a SCART converter about 3 years ago but got mixed results.  When I used my bog standard telly as a monitor I was not able to read the text because it was too blurry.  And when I played a movie it was spoiled by ghosting.


With these experiences I'm looking for a media streamer which I can then use to interact between either my Vista box or my Linux laptop.

Thanks for the suggestion.

---

### Post by issih on 2008-07-12
On a "bog standard telly" things are blurry, simply because the resolution is too low.. the overall resolution is something like 720*576 for pal, its not really cleanly delineated into pixel, and its interleaved. All these things mean that normal tv's don't make good computer monitors.

Watching videos however is generally ok, although the difference between progressive and interlaced video formats can make things look jagged if your videocard can't compensate.

Connecting the laptop up should work fine, e.g. via a composite or an svideo cable going through a scart adaptor, you'll just have to accept the limitations of the resolution and use something that has a nice big interface, e.g. myth tv or maybe elisa media center. that is probably your cheapest solution to be honest.

If you want something standalone, there are a various bits of hardware that can act as hardware streamers, google media streamers or something similar. Most of them are basically big hard drives with a dinky (probably linux based) pc strapped onto them which handles the streaming and networking duties.

For a while I just had my desktop hooked up to the tv as a second monitor. Once that was done I simply made a little script to launch vlc on that monitor in fullscreen with the web interface and ncurses interface activated.

Then I could sit on the couch with my laptop (or indeed my nintendo ds) ssh in to the main box and fire of the script, then use the remote interfaces to select videos. That was quite cool

---

