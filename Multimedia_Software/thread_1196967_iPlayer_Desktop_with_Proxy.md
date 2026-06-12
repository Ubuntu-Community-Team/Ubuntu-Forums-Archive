---
title: "iPlayer Desktop with Proxy"
date: 2009-06-25
forum: Multimedia Software
---

### Post by FokkerCharlie on 2009-06-25
Hi Everyone

I have set up a paid proxy service for my use for time spent away from home in the UK to watch BBC iPlayer.  It's working well for programmes streamed directly off the site.

However, I cannot get the iPlayer desktop application to play ball.  If I try to download a program (rather than playing it there and then from the website flash player), it tells me that it's not possible... until I set the proxy up in 'Network Proxy' in Settings > Prefs. Then, the program seems to download fine, so it appears that I'm successfully fooling both the website and the Adobe AIR app.

However, when I come to play the video, I see a message telling me that the content is temporarily unavailable. If I close and restart iPlayer desktop, then I see a message telling me that the content has expired and has been removed from my computer. Pah!

Interestingly, programs I have downloaded while at home in the UK still play fine when abroad, regardless of proxy settings. And ideas on how to work round this one?

Also, I cannot get the BBC 'Watch Live' service to work. I see "This content doesn't seem to be working. Please try later". (NB, NOT 'This content unavailable in your location'). I don't know if it's related to the above problem or not...
Error message from Flash:
Title: GenericKind:FMSConnectionError.FMS_CONNECTION_API
Description: CDN Failover, final connection failed
Code: 222222

Here's the really interesting bit:  it works on Vista, after installing and enabling the tool here:

[http://foxyproxy.mozdev.org/proxyservice/video-and-audio.html]("http://foxyproxy.mozdev.org/proxyservice/video-and-audio.html")
(see the download under point 2).

That's properly infuriating.  Can any one of you experts give me a clue as to how/if it might be possible to get this functionality on Ubuntu?  I'm using AMD64, 9.04.

In summary:
-Watching direct from iPlayer website works OK.
-Watching live does not, but DOES work under Vista.
-Downloading via the AIR app works, but playback fails.  This also works in Vista.

Advice appreciated!
Charlie

---

### Post by FokkerCharlie on 2009-06-25
A little bit more info-

I've just discovered that after downloading to iPlayer desktop in Ubuntu, I can move the 'repository' folder to my Vista partition, and play the programme there.

Go figure.

Charlie

---

