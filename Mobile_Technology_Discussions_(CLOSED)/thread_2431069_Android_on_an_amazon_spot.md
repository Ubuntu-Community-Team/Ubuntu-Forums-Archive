---
title: "Android on an amazon spot?"
date: 2019-11-11
forum: Mobile Technology Discussions (CLOSED)
---

### Post by casey-earnshaw on 2019-11-11
Hi Everyone

I have an Amazon spot that has been powered down and sat in a drawer for over a year now because creepy technology. I recently found it again during a clear out and I got thinking. Would it be theoretically possible to put just stock android on this, or even better an arm based distro? I couldn't see any way of inputting to the device though but I found out that the panel on the back is actually hiding a USB port:

[ATTACH=CONFIG]284390[/ATTACH]

Unfortunately I have absolutely no experience with changing the software on android devices. I have heard that you can install stock android on a phone to remove a vendors bloatware but I wouldn't know how to do it. I was just wondering if this is something that can be done with these things as well? I've been trying to look online for stuff but a lot of it just talks about the potential or just the fact that it is actually running android or the fact that it can be hacked maliciously. 
And if there isn't any way of actually getting another OS on, is it likely there will ever be? Should this go back in the drawer or into recycling?

Many thanks

---

### Post by slickymaster on 2019-11-11
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by jetsam on 2019-11-11
Everything with a CPU can be reprogrammed arbitrarily by definition ;)

The Spot may make it difficult, but that often only adds to the challenge...

I should modestly suggest you browse a different forum if you're truly interested in learning how to do this.  The guys and gals here are cooler than most, and stay mostly white/gray hat:
[https://hackaday.com/]("https://hackaday.com/")

---

### Post by casey-earnshaw on 2019-11-11
> **slickymaster said:**
> Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

Oh, I'm sorry, I'll try not to do that again. Thank you for fixing it for me.

> **jetsam said:**
> Everything with a CPU can be reprogrammed arbitrarily by definition :wink:

The Spot may make it difficult, but that often only adds to the challenge...

I should modestly suggest you browse a different forum if you're truly  interested in learning how to do this.  The guys and gals here are  cooler than most, and stay mostly white/gray hat:
[https://hackaday.com/](https://hackaday.com/)

Hmm. I found through that link a link to this article on medium: [https://medium.com/@micaksica/exploring-the-amazon-echo-dot-part-2-into-mediatek-utility-hell-b452f62e5e87](https://medium.com/@micaksica/exploring-the-amazon-echo-dot-part-2-into-mediatek-utility-hell-b452f62e5e87)

It does sound like there is potential but sadly this was written 2 years ago and maybe this is really as far as its got. I guess I'll keep an eye out on the hackaday website but it's not looking too hopeful at moment.

---

### Post by jetsam on 2019-11-11
If you start thinking about the hardware as modifiable instead of fixed, it can open up some possibilities.  That little death star of a case and its usb port and external components could be put to use with a new small pcb motherboard...  like a raspberry pi.  Its not necessarily trivial, but there's always a question of how much effort is worthwhile for something you would like to do.

It can save a lot of time to just bypass the closed chipsets and install an open platform: transplant the brains, keep the body ;)

Search for "echo spot teardown" and see if it gives you any ideas: here's one good one:
[Amazon Echo Spot Teardown]("https://www.youtube.com/watch?v=1OuPDbWOz2s")

It's surprisingly sturdy with that die-cast frame taking up half the enclosure.  That could be removed entirely.  Re-using the display would be advanced juju; it could more easily be replaced by a smaller oled display.
Raspberry Pi Zeros aren't much money:
[Amazon Link: Argon-Forty-Raspberry-Barebones-Audio-Video]("https://www.amazon.com/Argon-Forty-Raspberry-Barebones-Audio-Video/dp/B075FRRVLR/ref=sr_1_12?keywords=raspberry+pi+zero&link_code=qs&qid=1573500459&sourceid=Mozilla-search&sr=8-12")
The barest bones version without wifi is just $5.00 at Adafruit (plus tax and shipping, though):
[https://www.adafruit.com/product/2885](https://www.adafruit.com/product/2885)

...have fun with it :)  If you decide it's too much bother, I'd recommend just donating it to a thrift store.  Maybe someone will get some further use out of it.

---

