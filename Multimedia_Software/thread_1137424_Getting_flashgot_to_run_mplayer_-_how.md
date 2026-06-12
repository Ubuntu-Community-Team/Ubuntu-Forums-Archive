---
title: "Getting flashgot to run mplayer - how?"
date: 2009-04-25
forum: Multimedia Software
---

### Post by ticket on 2009-04-25
I want to use flashgot (firefox plug-in) to start up mplayer.
This will allow me to use mpplayer instead of the embedded flash driver to play .flv videos.

flashgot automatically grabs the URL of the streaming video and provides a mechanism for passing the URL to the user's chosen downloader - in this case mplayer.

The flashgot mechanism works by providing the user with a gui template to allow the user to define the executable location of mplayer and the arguments to be passed to it. The symbol flashgot uses for the stream url argument is [URL].

Ideally I would like place "[URL]" in flashgot's gui template, so mplayer gets called like this:

```
    mplayer "[URL]"
```


The quotes are needed to stop the bash shell from interpreting the URL string. (for some reason bash breaks the URL string at every '&' character in the URL, and youtube URLs have a lot of '&' in them).

Unfortunately flashgot prevents the user typing in quotes in the template, so a shell script is needed to do the job.
But if I try:


```
    #!/bin/bash
    mplayer "$1"
```


bash still breaks up the string [URL] being passed to mplayer. What is the right way to do this?

Given a solution to the above, there is still some work to do - the URL contains a comment string near its end, beginning with '#'. The # and all what follows it needs to be stripped off, otherwise mplayer complains. Something like sed ought to be able to do this.

Once all the above is done, we can all watch full screen flash using mplayer. Yay!

---

### Post by ticket on 2009-04-26
*theRube* at flashgot forums gave me some useful advice:

[http://forums.informaction.com/viewtopic.php?f=6&t=922&sid=3cb49500d459006418f9803f6d5c803d](http://forums.informaction.com/viewtopic.php?f=6&t=922&sid=3cb49500d459006418f9803f6d5c803d)

By setting flashgot.media.guessName to false in about:options, a useable URL is passed to mplayer.

Unfortunately on youtube, mplayer still hiccups over some videos and crashes on the high quality ones.  In one case this appears to be due to a flv format mplayer doesn't support - kinda surprising.  For HQ streams, having both the browser and mplayer displaying the stream at the same time, even if only briefly (unavoidable using this method) may be the cause of the crash.

The best way to solve this problem is to get mplayer to embed itself in place of the flash player.  This is what the greasemonkey script called HQTube does, but that is specific to youtube streams.

HQtube at:
[http://userscripts.org/scripts/show/24999](http://userscripts.org/scripts/show/24999)

What I need is a modified HQTube script that can capture streams the same way as flashgot does.  

Unfortunately I have no idea how to hack the HQTube script. I'll post the author for a feature request, but can any of the gurus here accomplish this?

The prize is real time HQ full screen flash video that doesn't kill your machine!

---

