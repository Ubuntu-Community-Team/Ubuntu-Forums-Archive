---
title: "Composite Video Capture Card"
date: 2009-04-06
forum: Mythbuntu
---

### Post by lessonz on 2009-04-06
I'm looking for a capture card capable of capturing the composite signal (RCA, the Red, White, and Yellow cables) from my cable box.  I can't seem to find one that is still being produced.  Any suggestions?  Should I just try to track down a used Hauppauge?  If so, which of the old models should I try to grab?

TIA

---

### Post by newlinux on 2009-04-07
Don't know about newer ones, but I have a PVR-150 that has composite and S-video inputs. If you can find one of those... Keep in mind their are multiple models of the PVR-150 - make sure you get one with the inputs you are looking for...

---

### Post by lessonz on 2009-04-07
Okay, there's one vote for an older piece of hardware.  Anyone know of a new piece that's supported?  Thanks again.

---

### Post by newlinux on 2009-04-07
I assume you are looking PCIe. Might want to look into the Hauppage HVR-1800. I think it has composite inputs. Some reported the audio in wasn't working a few months back, but I think that may be resolved in newer kernels.

There are some threads here about it...

---

### Post by lessonz on 2009-04-07
Unfortunately, the HVR-1800 is S-Video not composite.

---

### Post by newlinux on 2009-04-07
ahh, yes it has composite (stereo) ***audio*** in - I didn't look at closely enough. I don't think any of the newer HVR-1600, HVR-1800, Hvr1250, HVR-2250 hauppages have composite video in.

---

### Post by Zhono on 2009-04-07
I just bought an AVerTV PVR 150 off of ebay for $15, It has the composite video in, and the red and white for audio. But I don't know how hard it'd be to find another one of them floating around for cheap.

You can get this one from Newegg. [http://www.newegg.com/Product/Product.aspx?Item=N82E16815260017]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815260017")

It's only $20, and has free shipping. It's got the composite video in, but for the audio you'd have to use an adapter to go from your red and white jacks to a regular stereo jack. 4 or 5 bucks at Radioshack(or your local equivalent) I think.

I've also read a few thread that say it takes a bit of doing to get that card working in a linux box, but it can be done.

---

### Post by nickrout on 2009-04-08
> **newlinux said:**
> ahh, yes it has composite (stereo) ***audio*** in - I didn't look at closely enough. I don't think any of the newer HVR-1600, HVR-1800, Hvr1250, HVR-2250 hauppages have composite video in.

Composite has nothing to do with audio. It is a video standard. It just happens to be commonly connected by (yellow) RCA plugs, which are also commonly used for audio (red and white).

Anyway a composite signal can be easily converted to s-video via a small adaptor like this:

[http://www.parts-express.com/pe/showdetl.cfm?Partnumber=180-141%20%20%20%20%20%20%20%20&FTR=180-141&CFID=8309662&CFTOKEN=47881178](http://www.parts-express.com/pe/showdetl.cfm?Partnumber=180-141%20%20%20%20%20%20%20%20&FTR=180-141&CFID=8309662&CFTOKEN=47881178)

---

### Post by lessonz on 2009-04-08
nickrout, thank you very much.  I was aware S-Video was analog, but I didn't know it was so easy to convert from one to the other.  This sounds like the best solution.

newlinux, thanks for your sticking with the topic.  Zhono, thanks for giving me an alternative.

I appreciate all of your help.

---

### Post by nickrout on 2009-04-08
for more info it really is worth reading the wikipedia pages

[http://en.wikipedia.org/wiki/Composite_video](http://en.wikipedia.org/wiki/Composite_video)
[http://en.wikipedia.org/wiki/S-video](http://en.wikipedia.org/wiki/S-video)

And you can move on to the higher forms like:

[http://en.wikipedia.org/wiki/Component_video](http://en.wikipedia.org/wiki/Component_video)
[http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)
[http://en.wikipedia.org/wiki/Hdmi](http://en.wikipedia.org/wiki/Hdmi)

There is a lot of good information about digital video on wikipedia too - codecs, formats etc.

---

