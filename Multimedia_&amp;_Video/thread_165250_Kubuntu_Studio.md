---
title: "Kubuntu Studio"
date: 2006-04-24
forum: Multimedia &amp; Video
---

### Post by Menno on 2006-04-24
hi,

i want 3 things that CCRMA / demudi can't give:
 
1. low-latency 
2. nvidiadrivers with twinview 
3. NTFS reading. 

I'd love to make the big switch to Linux.
Is this all possible (using Kubuntu however)?

---

### Post by niviche on 2006-04-24
> 
3. NTFS reading. 


See [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by Menno on 2006-04-24
hi Niviche,
what i mean is that with CCRMA (based on Fedora) there is a realtime kernel with very low latency, but because of this i cannot install nvidiadrivers (or very difficult and i'm a newbie so this will be too difficult) and still maintain low latency. NTFS-intergration in this kernel is also influencing the low latency kernel negativly, so i've understood
So all these minimum requirements must be met for me to switch over to Linux.
i'm hoping with the approach of Ubuntu Studio it can be done?

---

### Post by niviche on 2006-04-24
Well, have you tested this way to read NTFS partition? I am not sure what you mean by low-latency, but this might just be it.

---

### Post by Menno on 2006-04-24
i'm looking for the right Linux distrubution for me to work with audio and music. When playing a synthesizer with a midikeyboard there must be low-latency, so when i press a key i hear the sound immediately and not half a second later. For that i need a stripped down kernel that is very fast.
However i want to use nvidiadrivers and NTFSreading as well. These things have a negative influence on the low-latency

---

### Post by niviche on 2006-04-24
Ok.

Have you tested Ubuntu / Kubuntu, or do you just assume that it doesn't do the trick?

---

### Post by dolson on 2006-04-25
YOU have to set your latency in JACK, otherwise, you're up to the sanity of the packager for each distro.

If you know that you require the patched kernel, then you ought to follow the wiki so you can see how to do it all. Dapper will be improved overall, but anyhow...

You really ought to read the studio setup page in the wiki to get a grasp of what you have to do.

If you want a distro that is out of the box-ready, then you need to look elsewhere until the Edgy is released.

---

