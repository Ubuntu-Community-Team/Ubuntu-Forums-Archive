---
title: "USB Audio Compatibility/Usability"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by Face1 on 2006-06-01
I posted this on the old breezy forum, but got no response and then everyone moved here, so I'm going to ask it again:

I'm getting a laptop. A laptop being a laptop, it's not gonna have great sound, as it has puny little lappy speakers. So, I figure usb audio would be nice, I'd love to be able to connect normal speakers. So I found [**this**]("http://www.newegg.com/Product/Product.asp?Item=N82E16829102174"). Good enough sound quality for me, etc, seems like a quality product. One of the reviewers even commented that it worked great with linux.

Well, there is one thing that worries me (hey, it's a $50 investment, I gotta be careful). I'm not going to take this around with me when I'm not in my room, and I'm certainly not going to be lugging my speakers around. I'm going to want to frequently connect/disconnect this. And when I disconnect it, I'd really like for the sound output to be routed to the lappy speakers, and when I reconnect it, sound routed back to it. Will this be possible? I'm inexperienced, but I'd be more than willing to utilize a script or two to get this working. Unfortunately, I have no understanding of what goes on in a linux system when a USB device is plugged in, and how the sound card in use is chosen.

Thanks!

---

### Post by Tweek84 on 2006-06-02
I have an older USB soundcard from creative. It's the extigy model which I believe is simply an external audigy.

Anyway, it works just fine with Breezy and Dapper.

---

### Post by DeXOR on 2006-06-02
I have a USB Sound Blaster and I'm having issues getting it to work with Ubuntu. I cannot select it as the default sound card and I get all sound through the speakers on my laptop. Anyone know how to fix this?

---

### Post by 23meg on 2006-06-02
Face1: I'm using an M-Audio Quattro external USB audio device and if I choose it as my preferred sound device, all ALSA apps default to it, and when it's disconnected, they fall back to my laptop's internal sound chip. This works by default in Dapper. It didn't in Breezy; it needed some extra ALSA config tweaking and even then I found it to be a bit shaky.

Advice: don't buy Creative gear; they're a horrible company. Bad support, undelivered promises, high profit margin, misleading specs, etc. Get an equivalent M-Audio or something similar.

---

### Post by asc on 2006-06-02
[QUOTE=Face1]
And when I disconnect it, I'd really like for the sound output to be routed to the lappy speakers, and when I reconnect it, sound routed back to it. Will this be possible? I'm inexperienced, but I'd be more than willing to utilize a script or two to get this working. Unfortunately, I have no understanding of what goes on in a linux system when a USB device is plugged in, and how the sound card in use is chosen.[/QUOTE]
This is possible and I have a similar configuration where I use both the internal sound card and the USB device at the same time. Unfortuantely, there is no unified audio interface for *any* GNU/Linux kernel so switching devices is application dependent. For ALSA, your USB card will appear as hw1:0, for OSS it will be /dev/dsp1 and JACK is the same as ALSA.

If that isn't confusing enough, you have to tell your applications what device to use, which is done differently for each application.

I believe the developers are trying to solve this issue by integrating everything into gstreamer but I haven't had much success with media formats using anything other than xmms and mplayer. YMMV.

---

### Post by dcroal on 2006-06-02
System > Preferences > Sound > Default Sound Card always works for me. In fact when I plug a USB sound device a bubble pops up offering to take me there directly.

---

### Post by Face1 on 2006-06-02
Okay, well, I'll be using breezy, so it looks like I'll be (mostly) in the clear.  I've noticed the problems with the sound interface(s) (it's hard not to), but I think that I can deal with it.  Most everything I use uses alsa anyway.

[QUOTE=23meg]Advice: don't buy Creative gear; they're a horrible company. Bad support, undelivered promises, high profit margin, misleading specs, etc. Get an equivalent M-Audio or something similar.[/QUOTE]

Yeah, I've heard stuff along these lines before.  However, they do make good products (in my experience).  The card that I linked to above seems to be good, and have a somewhat reasonable price.  USB audio is not the most popular flavor of soundcard out there, so there isn't a huge amount of choice.  Are you advising me against this card because you do not like the company, or you think it will not work well.  I think that it probably will work well, especially since a linux user already said that it did.

---

### Post by 23meg on 2006-06-02
I'm not advising against this particular product but against the whole company, for reasons I stated. Buying a product from a company with bad practices feeds that company and yields more nasty practices, even if the product in question is a relatively good one. And not buying from companies makes a difference; it may be the single most important thing that makes a difference. It's the best way to punish them.

I'm **sure** you'll find other products by M-Audio or other companies that work equally well, if not better. Don't be lazy; do a few searches, ask around what other products in your price range work well with Linux and get something else, that's my advice.

---

