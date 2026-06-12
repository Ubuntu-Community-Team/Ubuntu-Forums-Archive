---
title: "Ubuntu + Win 7 Media Sharing"
date: 2010-09-12
forum: Multimedia Software
---

### Post by ooomalley on 2010-09-12
Hello all,

I have an Ubuntu media server hooked up to my stereo and there's one piece of functionality that's missing from my home-media-sharing nirvana: I'd like to be able to use Windows 7's "Play to" feature to play music that is on my Win 7 box on the server (and thus the stereo). I would also like to be able to play music from an Ubuntu laptop (or Ubuntu desktop, for that matter) to the server as well.

I've searched around for the last couple days and haven't found anything that quite works. Most of the things I've found are DLNA "digital media servers," when I think I want a bit of software that will allow my server to be a DLNA "digital media renderer". There must be some piece of software out there that works for this but my google-fu is (apparently) weak.

I acknowledge that this is a silly question--I have mpd set up with a variety of clients so that I can control what's playing from a laptop, desktop, smartphone, etc. etc. I have a streaming server set up so I can stream from my server to anywhere in the world. But I have this strange desire to be able to play songs that are on my desktop that haven't made it over to the server yet (for whatever reason) over the stereo. Please, indulge me!

Thanks,
Peter

---

### Post by ooomalley on 2010-09-12
Mere minutes after that plea for help, of course, I figured something out: the Coherence plug-in for Rhythmbox. (It's the package "rhythmbox-plugin-coherence", unsurprisingly.) It didn't work at first, I had to do some routing stuff (on the server):
```
sudo route add -net 239.0.0.0 netmask 255.0.0.0 eth1
```
(Note that for most people it's probably eth0.) I'm not entirely sure what that does but it makes it so that other DLNA/UPnP/whatever devices can find it on the network.

I can now use Win 7's "Play to" to play music to rhythmbox on my server. Awesome!

There are some issues remaining:
[LIST]
[*]When a song finishes playing it goes to whatever is next on Rhythmbox's Play Queue, or failing that, whatever is highlighted in the main section.  This can be overcome by not having anything in the play queue and to have the main view set to show nothing. It's mildly annoying, though.
[*]You have to start rhytmbox. I'd prefer something a bit more daemonized.
[/LIST]

I'll be trying out the Coherence gstreamer thing, but I haven't had luck with it yet. As my dear governator says, "I'll be back!"

P.S. The rhythmbox plugin didn't work off the bat. There was a python error that I had to fix. I changed this:
```
seconds = int(h)*3600 + int(m)*60 + int(s)
```
to this:
```
seconds = int(float(h))*3600 + int(float(m))*60 + int(float(s))
```

Not particularly ingenious or foolproof, but it did the job.

---

