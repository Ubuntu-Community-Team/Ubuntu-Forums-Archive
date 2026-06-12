---
title: "VP8 released, it's free, will Ubuntu adopt it?"
date: 2010-05-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kahumba on 2010-05-19
Hi,
Google released VP8 for free, it's official:
[http://www.webmproject.org/about/faq/](http://www.webmproject.org/about/faq/)

Do you think Ubuntu 10.10 will support it by default like it now supports Theora video without the user having to download codecs first?

Will it eventually use VP8 (WebM) by default for its demo video(s)?

---

### Post by philinux on 2010-05-19
Yeah there was a thread started in the cafe an hour ago. Youtube will transcode all the videos to this format. Firefox should catch up I hope.

---

### Post by ubuntu27 on 2010-05-19
Cool! I never heard about this new format.

Thank you for sharing. I hope it spreads

---

### Post by andrewabc on 2010-05-19
> **philinux said:**
> Yeah there was a thread started in the cafe an hour ago. Youtube will transcode all the videos to this format. Firefox should catch up I hope.

Are you saying youtube is switching to this video codec (instead of h.264 which they were doing)?

Or that if you have web browser that supports HTML5 + this codec, youtube will detect it and recode to play?

---

### Post by kahumba on 2010-05-19
> **philinux said:**
> Youtube will transcode all the videos to this format.
Is there an official statement from Google about this?
Google only mentions using it for 720p videos and higher.
I've only seen Mozilla mentioning what you're saying (but Mozilla ain't Google), so I'm still a bit wary.

---

### Post by Merk42 on 2010-05-19
Well Canonical can't support it until Maverick, since they don't support new versions of Firefox

---

### Post by null_pointer_us on 2010-05-19
Hey, this is great news! :)

Software patents... *sigh*

I've read so many stories about silly software patents being granted though absurdly vague documents that could apply to damn near anything.

Sometimes I wish someone would try to file a patent describing, in patent language so (typically) vague that no one can tell what it does until someone actually tries to enforce it, some key part of the software patent filing/royalty collection process.

Then sue the U.S. Patent Office to recover, say, 1% of all royalties on patents granted by that office -- not so much to win the suit as to enjoy watching the process invalidate itself.

I bet there are tons of obvious legal reasons why that wouldn't work, but it'd be hilarious if a brilliant legal team could find a way to pull off something like that.

---

### Post by zekopeko on 2010-05-19
> **Merk42 said:**
> Well Canonical can't support it until Maverick, since they don't support new versions of Firefox

Not true. IIRC the plan is to support new versions of Firefox after Mozilla stops supporting the current version in Lucid and later. That means after Mozilla stops supporting Firefox 3.6 Lucid users will get the next stable version as a regular upgrade.

---

### Post by 23meg on 2010-05-19
[QUOTE=kahumba]Do you think Ubuntu 10.10 will support it by default like it now supports Theora video without the user having to download codecs first?[/QUOTE]

GStreamer in upstream git [already supports it]("http://blogs.gnome.org/uraeus/2010/05/19/webm-and-gstreamer/") on day one, and since Maverick will almost certainly have the up to date GStreamer and related components, the answer is "very likely".

---

### Post by 23meg on 2010-05-19
> **Merk42 said:**
> Well Canonical can't support it until Maverick, since they don't support new versions of Firefox

1) WebM is not necessarily tied to Firefox or even the web

2) You might be interested in reading [this]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model")

---

### Post by Schendje on 2010-05-19
Yeah, all YouTube videos will indeed be using VP8. In fact, you can already try them out right now. (By enabling the HTML5 demo and adding "&webm=1" to search result URLs)

New Firefox nightlies have appeared with support for WebM. I tried it out on YouTube... It's not perfect yet but it's nice. :)

---

### Post by Merk42 on 2010-05-19
> **23meg said:**
> 1) WebM is not necessarily tied to Firefox or even the web

2) You might be interested in reading [this]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model")
> **zekopeko said:**
> Not true. IIRC the plan is to support new versions of Firefox after Mozilla stops supporting the current version in Lucid and later. That means after Mozilla stops supporting Firefox 3.6 Lucid users will get the next stable version as a regular upgrade.

I know, I suppose I should have been clearer.

Canonical won't support it **when it's released**, they'll only support it once the latest incompatible version goes EOL.

---

### Post by ranch hand on 2010-05-19
Mozilla, some may be interested in knowing, has a website.  They offer FF for free.  Download and install instructions are even included.  Easy enough that even I can do it.  Pretty neat.

---

### Post by ghindo on 2010-05-19
All upstream projects (Chromium, Firefox, ffmpeg, gstreamer) should take care of this for us.  The only thing Canonical will really have to do is to encode videos in VP8.

---

### Post by plun on 2010-05-19
Phoronix article
[http://www.phoronix.com/scan.php?page=news_item&px=ODI2OA](http://www.phoronix.com/scan.php?page=news_item&px=ODI2OA)

> The code can be found at WebMProject.org. WebM/VP8 support in HTML5 can already be found in t**he nightly builds of Google's Chromium and Mozilla's Firefox as of today**. Opera support for this new open-source format is coming very soon. 

Just to visit [Chromium]("https://launchpad.net/~chromium-daily/+archive/ppa") and [Mozilla daily ppa]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa") (Firefox 3.7)  and install... and then go out and test....:popcorn:


--

---

### Post by Merk42 on 2010-05-19
> **ranch hand said:**
> Mozilla, some may be interested in knowing, has a website.  They offer FF for free.  Download and install instructions are even included.  Easy enough that even I can do it.  Pretty neat.

Which isn't supported by Canonical, so I dunno if that counts as "Ubuntu adopting it" and therefore off topic :)

---

### Post by ranch hand on 2010-05-19
It may be off topic but one of the points made was that you get auto updates from mozilla for FF on other OS'.

I am generally happy with the default but I do have the new one running on 9.04 just fine.

---

### Post by Merk42 on 2010-05-19
> **ranch hand said:**
> It may be off topic but one of the points made was that you get auto updates from mozilla for FF on other OS'.

I am generally happy with the default but I do have the new one running on 9.04 just fine.

I think that the conversation is going toward the topic [here](http://ubuntuforums.org/showthread.php?t=1478564)

So back on topic, would PiTiVi in 10.10 be able to export to VP8 format?

---

### Post by zekopeko on 2010-05-19
> **Merk42 said:**
> I think that the conversation is going toward the topic [here](http://ubuntuforums.org/showthread.php?t=1478564)

So back on topic, would PiTiVi in 10.10 be able to export to VP8 format?

Yes. Read planet.gnome.org. There is initial support for VP8 in Gstreamer and ffmpeg.

---

### Post by anders_c_ on 2010-05-19
has anyone seen any tests and comparisons between VP8, theora and h264? I mean, do we even have a reason to be happy about another free codec or is worse than what we already have :P

---

### Post by zekopeko on 2010-05-19
> **anders_c_ said:**
> has anyone seen any tests and comparisons between VP8, theora and h264? I mean, do we even have a reason to be happy about another free codec or is worse than what we already have :P

[http://x264dev.multimedia.cx/?p=377](http://x264dev.multimedia.cx/?p=377)

Summary: Worse then h264, better then xvid. Better then Theora by far. Problem is it's similar to h264 so there is potential for patent lawsuits since MPEG-LA members hold some 1000 patents on video/audio stuff.

---

### Post by Ibidem on 2010-05-19
There's a comment in that review about some code predating h264...
As far as "worse than h264", it's actually slightly better than h264 Baseline (which is the most similar part of h264); but that's the lowest level for h264 and the only level for VP8.
Regarding Theora, apparently it's derived from VP3 (an ancient version of the same line)- see [here]("http://www.theora.org/faq/#20").  That should give you an idea.

Opera has a development version, including a [compressed Ubuntu installer (13 MB)]("http://snapshot.opera.com/webm/opera-10.54-21867-webm.i386.linux.tar.bz2"), that supports WebM.
Chromium will support it soon (ppa version); the claims about Youtube have a source [here]("http://www.youtube.com/html5"), but seem to be exaggerating things.
We probably all know that Firefox will support it.

---

### Post by krazyd on 2010-05-20
> **zekopeko said:**
> [http://x264dev.multimedia.cx/?p=377](http://x264dev.multimedia.cx/?p=377)

Summary: Worse then h264, better then xvid. Better then Theora by far. Problem is it's similar to h264 so there is potential for patent lawsuits since MPEG-LA members hold some 1000 patents on video/audio stuff.

I don't think that's really a problem. With Google behind it, I'm sure it won't take too long to catch up quality-wise.

---

### Post by kahumba on 2010-05-20
> **krazyd said:**
> I don't think that's really a problem. With Google behind it, I'm sure it won't take too long to catch up quality-wise.

Also, for normal users complaining about VP8 it's like getting a modern BMW for free and complaining it's not a Ferrari.
By far, the overwhelming majority of users and web developers are more than happy with VP8, plus it will keep improving and bugs fixed and hardware acceleration is coming, so the future is very bright unless Microsoft and Apple sue Google themselves or through some proxy and manage to win their (probably upcoming) patent claims, certainly these companies are studying now this scenario. Google issued a check and mate to their future video dominance of the world and they can't fight through innovation, luckily for them they have huge patent portfolios so time will tell what happens next.

---

### Post by philinux on 2010-05-20
> **andrewabc said:**
> Are you saying youtube is switching to this video codec (instead of h.264 which they were doing)?

Or that if you have web browser that supports HTML5 + this codec, youtube will detect it and recode to play?

[http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/](http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/)

Point #4.

---

### Post by MacUntu on 2010-05-20
Edit: I'm stupid, link already posted.

---

### Post by jppr on 2010-05-20
[http://my.opera.com/desktopteam/blog/](http://my.opera.com/desktopteam/blog/)

---

### Post by andrewabc on 2010-05-20
> **philinux said:**
> [http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/](http://hacks.mozilla.org/2010/05/firefox-youtube-and-webm/)

Point #4.

Still doesn't say if youtube is still going to continue converting everything to h.264

Unless they plan on having several different file formats for each video. flash, h.264 and VP8?

---

### Post by zekopeko on 2010-05-20
> **krazyd said:**
> I don't think that's really a problem. With Google behind it, I'm sure it won't take too long to catch up quality-wise.

Read the blog post. It looks like Google won't break backward compatibility for the sake of fixing the codec. What you see know is what you are going to get for the foreseeable future.

---

### Post by zekopeko on 2010-05-20
> **andrewabc said:**
> Still doesn't say if youtube is still going to continue converting everything to h.264

Unless they plan on having several different file formats for each video. flash, h.264 and VP8?

Flash, h.264 and VP8 aren't file formats. One is a developer platform the other two are codecs.

They will most likely code videos in h.264 Baseline for phones for the moment.

---

### Post by Reiger on 2010-05-20
> **krazyd said:**
> I don't think that's really a problem. With Google behind it, I'm sure it won't take too long to catch up quality-wise.

The problems, from the linked article, though are:
(a) It appears that VP8 is so similar to H.264 (baseline) that the `Unencumbered by Patents' claim is dubious at best.
(b) It cannot match the high quality or speed of H.264 in more performance oriented settings.
(c) There is no hardware acceleration available. There are issues with the format that make it hard to produce hardware acceleration for it, too.
(d) The spec is a piece of software which is currently frozen. Google already rejected bugfixes based on the argument that the software is the spec, the spec is frozen ergo the bugs can't be fixed.

So the conclusion is that if you want high quality video you might as well use an open source H.264 encoder for better speed/quality & hardware support. Unless On2's patent pool covers the H.264 patents, too (somehow) this means that VP8 has no real benefit except over the rock-bottom version of H.264.

This, of course, changes if the MPEG-LA sharks decide that VP8 defeats their patents; or if On2's patents are such to invalidate claims against VP8 (and possibly claims on H.264 as well). In that case VP8 becomes a godsent for those beholden to the mercy of MPEG-LA (i.e. people in countries where software patents are valid).

---

### Post by 23meg on 2010-05-20
For those who'd like to do a quick tryout, the chromium-daily PPA now has WebM support.

---

### Post by phillw on 2010-05-20
> **23meg said:**
> For those who'd like to do a quick tryout, the chromium-daily PPA now has WebM support.

Hmm, I might just be a 'naughty boi' and pop the daily build ppa for chromium back on. It can play with the 'proposed' updates for 10.04.1 that the system is accepting. Roll on the RC of A1 10.10 :-D

Regards,

Phill.

---

### Post by ghindo on 2010-05-20
> **Reiger said:**
> (c) There is no hardware acceleration available. There are issues with the format that make it hard to produce hardware acceleration for it, too.This is untrue.  [As has been shown with Theora]("http://www.schleef.org/blog/2009/11/11/theora-on-ti-c64x-dsp-and-omap3/"), a DSP doesn't necessarily work with only one specific codec.  I don't believe there is any technical reason why VP8 wouldn't be able to leverage existing hardware.  **Edit:** [Theora dev xiphmont explains]("http://xiphmont.livejournal.com/50239.html?thread=139327#t139327"):
> The vast majority of 'hardware' h.264 implementations are just embedded general purpose DSPs. Theora had already gone onto a few, VP8 can be added the same way.
Additionally, Google has been working with hardware vendors like [Nvidia, AMD, Qualcomm, and Texas Instruments]("http://www.webmproject.org/about/supporters/") to assure adequate hardware support in the future.

Could you be more specific about these supposed issues with VP8 which hinder hardware acceleration?  I have never heard anything like that before.

---

### Post by ghindo on 2010-05-20
Sorry for the double post, but if you haven't checked out Xiph developer Chris Montgomery's post (and comments) about WebM, I would recommend it:  [http://xiphmont.livejournal.com/50239.html](http://xiphmont.livejournal.com/50239.html)

---

### Post by zekopeko on 2010-05-20
> **ghindo said:**
> This is untrue.  [As has been shown with Theora]("http://www.schleef.org/blog/2009/11/11/theora-on-ti-c64x-dsp-and-omap3/"), a DSP doesn't necessarily work with only one specific codec.  I don't believe there is any technical reason why VP8 wouldn't be able to leverage existing hardware.  Additionally, Google has been working with hardware vendors like [Nvidia, AMD, Qualcomm, and Texas Instruments]("http://www.webmproject.org/about/supporters/") to assure adequate hardware support in the future.

Could you be more specific about these supposed issues with VP8 which hinder hardware acceleration?  I have never heard anything like that before.

This is sweet. I was looking for some info if this will be possible for VP8. The first thing they should do is make this work since mobile phones and other devices with hardware decoding are probably the biggest obstacle for WebM, next to IE.

---

### Post by jlaki on 2010-05-20
Could that mean that Google providing the open source codec for Youtube will, after a while, even drop the so-much-hated flash player and provide an open source one?

Oh yes, I would like that. :O

---

### Post by Merk42 on 2010-05-20
> **jlaki said:**
> Could that mean that Google providing the open source codec for Youtube will, after a while, even drop the so-much-hated flash player and provide an open source one?

Oh yes, I would like that. :O

Considering Flash will support VP8 they can do BOTH

---

### Post by krazyd on 2010-05-20
> **zekopeko said:**
> Read the blog post. It looks like Google won't break backward compatibility for the sake of fixing the codec. What you see know is what you are going to get for the foreseeable future.

You need to read past the first sentence:
> **Are VP8 or WebM subject to change?**

The VP8 and WebM specifications as released on May 19th, 2010 are final. We believe that the code and tools can evolve and improve for many years without requiring changes to the core specifications. *We’ll maintain a separate branch of the code, however, for bold new ideas that could alter the specifications. If there are significant improvements to warrant a new revision we might adopt them, but only after careful consideration and after discussing suggested changes with the WebM community.*

> **zekopeko said:**
> Then why did they refuse a patch?

I'm not sure where you found that they refused a patch, but there are many reasons why they might have.

From their Roadmap, seems there is quite a bit of room for improvement before changing the spec.
[http://www.webmproject.org/code/roadmap/](http://www.webmproject.org/code/roadmap/)

---

### Post by bapoumba on 2010-05-21
4 posts removed.
If this is a discussion you cannot keep civil, please do not post, thanks.

---

### Post by zekopeko on 2010-05-21
> (a) It appears that VP8 is so similar to H.264 (baseline) that the `Unencumbered by Patents' claim is dubious at best.

Well that didn't take long:

[http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/](http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/)

---

### Post by ssam on 2010-05-21
VP8 seems to be very good news. especially with the weight of youtube behind it.

theora still has life in to though. there big improvements in the encoder with each release. have a look at the screet shots in [http://people.xiph.org/~xiphmont/demo/theora/demo9.html](http://people.xiph.org/~xiphmont/demo/theora/demo9.html)
and as i understand if you encode a video with the new encoder it will still play in old players.

there is also [http://en.wikipedia.org/wiki/Dirac_%28codec%29](http://en.wikipedia.org/wiki/Dirac_%28codec%29)

---

### Post by kahumba on 2010-05-21
> **zekopeko said:**
> Well that didn't take long:

[http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/](http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/)

Also, notice that they were ok with VP8 until Google acquired it, which once again proves that corporations use terms like "intellectual property" and "patents" to attack competitors, and these terms have almost nothing to do anymore with the reason(s) patents were created in the first place.
Yes, there are  benefits from patents, but the damage is far, far greater! Hence their complete abolition is the only sane way to go, because otherwise it's a matter of days before corporations find loopholes in the new, would-be-fixed, patent system.

---

### Post by screaminj3sus on 2010-05-21
> **kahumba said:**
> Also, notice that they were ok with VP8 until Google acquired it, which once again proves that corporations use terms like "intellectual property" and "patents" to attack competitors, and these terms have almost nothing to do anymore with the reason(s) patents were created in the first place.
Yes, there are  benefits from patents, but the damage is far, far greater! Hence their complete abolition is the only sane way to go, because otherwise it's a matter of days before corporations find loopholes in the new, would-be-fixed, patent system.

QFT. Our patent system is garbage.

---

### Post by seeker5528 on 2010-05-21
> **zekopeko said:**
> Well that didn't take long:

[http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/](http://digitaldaily.allthingsd.com/20100520/googles-royalty-free-webm-video-may-not-be-royalty-free-for-long/)

[sarcasm]
Hmmm.

Didn't SCO already prove that selling people a license to run something you didn't create based on nothing more than your word that 'there is no way they could have created that without infringing on our patents' is not a business winning strategy?[/sarcasm]

EDIT: As an after thought. I decided to add the sarcasm tags, just in case someone might be tempted to think that was a serious question.

Later, Seeker

---

### Post by xzero1 on 2010-05-24
> **screaminj3sus said:**
> QFT. Our patent system is garbage.

Software patents are garbage. But I'd like to fix it this way: You get to keep your software patents monopoly, but we get to sue you as a class for any bugs and/or compatibility issues in your code. Of course, if we need to spend our time to fix the issue then we can just send them the bill. Just like we can sue for any defective product.

Do you think MPEG-LA would take *that* deal?

---

### Post by zekopeko on 2010-05-24
> **xzero1 said:**
> Software patents are garbage. But I'd like to fix it this way: You get to keep your software patents monopoly, but we get to sue you as a class for any bugs and/or compatibility issues in your code. Of course, if we need to spend our time to fix the issue then we can just send them the bill. Just like we can sue for any defective product.

Do you think MPEG-LA would take *that* deal?

Sure they would. It wouldn't fly in any sane court.

---

### Post by xzero1 on 2010-05-24
> **zekopeko said:**
> Sure they would. It wouldn't fly in any sane court.

I'm saying that the law be changed to enforce this as a tradeoff for this software patent bullshit. The courts would have to enforce it.

---

### Post by ssam on 2010-05-24
> **screaminj3sus said:**
> **QFT**. Our patent system is garbage.

are you a physicist?

---

### Post by alexan on 2010-05-24
Transmaggeddon [v.0.16](http://www.linuxrising.org/transmageddon/files/) support vp8, you also may need the gstream ppa to get it work.

VLC are already [on it](http://people.videolan.org/~jb/webm) ([http://webcache.googleusercontent.com/search?q=cache:EWh6RQdU5ggJ:people.videolan.org/~jb/webm/+webm+site:.videolan.org&cd=1&ct=clnk](http://webcache.googleusercontent.com/search?q=cache:EWh6RQdU5ggJ:people.videolan.org/~jb/webm/+webm+site:.videolan.org&cd=1&ct=clnk) )
It's time to test the effectiveness of this webm. :guitar:

---

