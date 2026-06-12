---
title: "radio stream doesn't work for firefox"
date: 2012-11-01
forum: Multimedia Software
---

### Post by fekioh on 2012-11-01
I am trying to stream the Greek national radio stations (e.g. [http://www.ert.gr/deytero/](http://www.ert.gr/deytero/)) in Ubuntu with firefox but it doesn't work. 

A pop-up opens but the stream is not playing and the only link they provide is  this ([http://www.interoperabilitybridges.com/windows-media-player-firefox-plugin-download](http://www.interoperabilitybridges.com/windows-media-player-firefox-plugin-download)) to download windows media player firefox plugin which I have installed already. 

I can of course manually find the stream url in the source of the pop-up ([http://tvradio.ert.gr/radio/liveradio/asx/deytero.asx](http://tvradio.ert.gr/radio/liveradio/asx/deytero.asx)) and stream it through, say, rythmbox. 

Any ideas, how to make it play in the browser?

Thanks

---

### Post by fekioh on 2012-11-01
Hi, 

Sorry, this is the correct link to the pop-up window (which doesn't play in firefox):

[http://tvradio.ert.gr/radio/liveradio/deytero.asp](http://tvradio.ert.gr/radio/liveradio/deytero.asp)

Thanks

---

### Post by howefield on 2012-11-01
Do any of them work for you ?

I have this one working but the others are more problematic :-)

---

### Post by fekioh on 2012-11-01
Hi howefield,

So you got one of the stations playing from the pop-up? That's what I understand from the screenshot.

It is not working for me. The pop-up window you sent opens, but there is no sound in any of the stations whatsoever...

---

### Post by howefield on 2012-11-01
The screenshot I attached was only to show how it looked as it streamed.

After installing some gstreamer codecs, I now have 2 stations playing directly in the browser, the one above and erasport.

However, they all play if I select a channel and then right click in the player area and select open with "Movie Player".

---

### Post by fekioh on 2012-11-01
Yes, they also play for me with an external player. I just wanted to find out why they don't play from the browser.

Which codecs did you install? 

Thnx

---

### Post by howefield on 2012-11-01
gstreamer0.10-ffmpeg
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly

---

