---
title: "FFmpeg stoped working after reinstall"
date: 2011-04-15
forum: Multimedia Software
---

### Post by stuart.reinke on 2011-04-15
It's been along time since I had to put my tail between my legs anf come to the forum to ask a question. However, I have a problem that has me stumped and can't seem to find an answer for. 

I've been using WinFF as a frontend for FFmpeg since I was on Intrepid. Every time the same thing after a fresh install. Add Medibuntu then install the extra codecs ffmpeg and winff and everything worked. 

The other day I decided to do some spring cleaning on my machine and start over with a new installation of Lucid. I had the installer format the root partition while leaving /home alone. Afterward I went about reinstalling winff/ffmpeg just like I,ve done in the past. But now when I try to convert an AVI video into MP4 to play on my BlackBerry I get an error that states "unknown encoder libfaac"

I've checked in synaptic. It's installed. I tried another reinstall. No luck. Googled but couldn't find an answer that would work. 

Everything was perfect before the reinstall. Now I get this error. I didn't upgrade or anything just a straight reinstall of Lucid. 

If anyone has any suggestions I would be grateful. If you need more info first just ask. I might not be able to answer untill later when I'm in front of my computer but will get you the needed information. 

Thanks in advance.

---

### Post by FakeOutdoorsman on 2011-04-15
Ubuntu updated FFmpeg and its libraries in the repository recently (due to some security issues which weren't of much concern in my opinion). Medibuntu did not release any updated packages yet.  Therefore your package manager will choose the newest package, which is the one from the Ubuntu repository which does not support *libfaac* for AAC encoding.

Last I checked the new Medibuntu packages are currently in their "staging" repository. Shouldn't be much longer now until they are available in the normal, regular Medibuntu repository...unless they already released them and I haven't noticed.

So your choices are:
[list]
[*]Go into Synaptic and install the older ffmpeg and libavcodec-extra-52 packages
[*]Wait for Medibuntu to release their updated packages
[*]Use the Medibuntu staging repo
[*]Compile FFmpeg
[/list]

---

### Post by stuart.reinke on 2011-04-15
Thanks FakeOutdoorsman. It appears that I should have put off my spring cleaning. Just like i have done with my house. Lol. 

I think I will try to install the older versions from medibuntu with synaptic. 

Will update manager want to replace them with the newer releases from the ubuntu repo right away?

---

### Post by stuart.reinke on 2011-04-15
Thanks FakeOutdoorsman. It appears that I should have put off my spring cleaning. Just like i have done with my house. Lol. 

I think I will try to install the older versions from medibuntu with synaptic. 

Will update manager want to replace them with the newer releases from the ubuntu repo right away?

Oops. Double post.

---

### Post by FakeOutdoorsman on 2011-04-16
> **stuart.reinke said:**
> Will update manager want to replace them with the newer releases from the ubuntu repo right away?

Probably, but you can lock the package in Synaptic if I remember correctly. I don't remember how exactly, but it shouldn't be hard to do.

---

### Post by stuart.reinke on 2011-04-16
Thanks for all the help FakeOutdoorsman. The old packages got ffmpeg working again.

---

### Post by FakeOutdoorsman on 2011-04-24
According to bug [#738134](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/738134) Medibuntu has released their updated FFmpeg related packages, so you can probably unlock and then update. I'm not sure what Ubuntu versions they have provided updates for.

---

