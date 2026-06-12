---
title: "mplayer2"
date: 2012-03-28
forum: Multimedia Software
---

### Post by Xtyn on 2012-03-28
Hello, I was just wondering why mplayer2 is the default player in Lubuntu 12.04 when it obviously does not work, it's a pile of cr*p and from what I read it has been discontinued. What's wrong with mplayer1 or any other functional player out there?

---

### Post by andrew.46 on 2012-03-30
I don't use LUbuntu I have to admit but as far as I was aware MPlayer2 continues to be actively developed as a fork of the MPlayer project. I have been wrong before though :).

---

### Post by qyot27 on 2012-04-19
Even though this is a couple weeks late...


> **andrew.46 said:**
> I don't use LUbuntu I have to admit but as far as I was aware MPlayer2 continues to be actively developed as a fork of the MPlayer project. I have been wrong before though :).
It is actively developed.  A quick look at the git repository ([http://git.mplayer2.org/](http://git.mplayer2.org/)) confirms it in case of any doubt.

*mencoder* was discontinued as part of the changes made in MPlayer2.  The encoding branch by divverent takes its place, which I'd recommend even if only for it using sh instead of Python.

There is also possibly some confusion about the name 'MPlayer2' itself, since 'mplayer2.exe' is the name of the Windows Media Player 6.4 binary on Windows XP (and WMP6.4 is indeed 'discontinued' in the same sense as Windows XP itself is - you can't even use WMP6.4 on Vista or above).  Same name, different program.


And while I certainly don't think it matters to hammer this point in since the OP hasn't been seen in 3 weeks, it's general manners not to call something crap unless you give specific reasons for it being so, or to say something 'obviously doesn't work' without providing information about what you're attempting to do and the errors you're getting.  I've been using MPlayer2 as my main player in Ubuntu for over a year now (partially because it's a cinch to build, and partially because it supports certain things better than the original branch), and I've had zero issues with it.  I won't discount that maybe there's something the matter with the repository version in the OP's case, but that's likely to be a build or configuration issue, not an intrinsic one in the player, as it could be easily resolved by rebuilding it locally or changing some of said config opts.

---

### Post by Xtyn on 2012-04-24
I've tried it again today from the liveUSB, a daily build for 23 apr, 3 days before the release and this is what I get: [http://i.imgur.com/VWm3L.png](http://i.imgur.com/VWm3L.png)

I even installed lubuntu-restricted-extras again, just to check. Still does not work. A month ago I installed it on the laptop, and it worked fine when I removed mplayer2 and installed mplayer1.

My laptop is an LG lw60 express with pentium M at 1.6 GHz, intel 915GM GPU, 1 GB of RAM, nothing special really. I won't make a bug report, I don't use it, although it's the only one in the Ubuntu family that I like. If they can't do it right, they should just put VLC, that always works.

---

### Post by SeijiSensei on 2012-04-24
I just built a brand-new copy of mplayer2 from the source code at [http://www.mplayer2.org/](http://www.mplayer2.org/).  I played an H.264-encoded 1080p subtitled Blu-ray rip with nary a problem using smplayer as the front-end.

You don't tell us what kind of content you're trying to play, but I'll say right now that a Pentium M with an i915 adapter is going to have a tough time playing 720p or higher material encoded with H.264.  That's going to be true with any player software.  Have any XviD-encoded files in the AVI container?  How does it do with those?

---

### Post by Xtyn on 2012-04-24
> **SeijiSensei said:**
> I just built a brand-new copy of mplayer2 from the source code at [http://www.mplayer2.org/](http://www.mplayer2.org/).  I played an H.264-encoded 1080p subtitled Blu-ray rip with nary a problem using smplayer as the front-end.
As far as I can remember, I tried mplayer2 on Debian, it worked, but I didn't like it, can't remember why exactly.

> **SeijiSensei said:**
> 
You don't tell us what kind of content you're trying to play, but I'll say right now that a Pentium M with an i915 adapter is going to have a tough time playing 720p or higher material encoded with H.264.  That's going to be true with any player software.  Have any XviD-encoded files in the AVI container?  How does it do with those?
I can run 720p fine on this, not higher. The file in the screenshot is 854x480, so 480p, it's Big Buck Bunny actually. Mplayer2 on Lubuntu does not play anything on my laptop, no matter the format or quality.

This was just a rant, I'm not trying to get mplayer2 to work, mplayer1 works great, I don't need anything else.

---

### Post by qyot27 on 2012-04-24
> **Xtyn said:**
> I've tried it again today from the liveUSB, a daily build for 23 apr, 3 days before the release and this is what I get: [http://i.imgur.com/VWm3L.png](http://i.imgur.com/VWm3L.png)
That error points to it being an issue with subtitles.  Considering the preference in Ubuntu (possibly Debian also) for shared libraries, I'd wager a guess that lib[color="black"]a[/color]ss4 isn't installed.  It's the library mplayer2 relies on for rendering subtitles.

A different way of confirming this would probably be to use the -no[color="black"]a[/color]ss parameter.

---

### Post by Xtyn on 2012-04-24
> **qyot27 said:**
> I'd wager a guess that lib[color="black"]a[/color]ss4 isn't installed.  It's the library mplayer2 relies on for rendering subtitles.
Look here: [http://packages.ubuntu.com/precise/mplayer2](http://packages.ubuntu.com/precise/mplayer2)
So, libass4 is a dependency for mplayer2. I highly doubt that it's somehow missing from Lubuntu, synaptic would give all sorts of errors if that was the case. Moreover, I recently installed a custom Ubuntu 12.04 with openbox and tried mplayer2 out of curiosity, to see if it was Lubuntu's fault. It did not work, mplayer1 obviously worked fine.

I don't really care what the problem is, maybe the developers should care but I don't. It would have been nice if they included by default a functional movie player.

---

### Post by marinara on 2012-04-24
Why is it crashing?  I assure you if it was broken for everyone I would know about it.

---

### Post by Xtyn on 2012-04-26
I've just installed Lubuntu 12.04 final, which is actually the same as the daily image from 23 April, which I tested before, so the problem obviously remains.

I tried to send the crash report, but it said that mplayer2 is an unofficial package, so it did not send the report.

I don't really care if it works or not for myself, because I don't use it anyway, but if some developer wants to get to the bottom of this, I can help with details, I have no idea what's the problem with mplayer2. VLC works fine, as you can see, I did not install mplayer1 because it replaces mplayer2.

[[IMG]http://i.imgur.com/BUxevl.png[/IMG]](http://i.imgur.com/BUxev.png)

---

### Post by Xtyn on 2012-04-26
This seems to be a known bug:
[https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974774](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974774)
[https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974125](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974125)
[https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/976465](https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/976465)

---

### Post by down_quark on 2012-04-26
I generally don't trust mplayer binaries because their codec sources aren't updated frequently. 
I've been using mplayer2 compiled from [source]("http://git.mplayer2.org/mplayer2-build/") since the anime world started using 10bit, and it's very reliable.
Compiling it yourself would ensure no instruction set issues, which those bug reports indicate.

---

### Post by roten on 2013-01-13
There is still problems with mplayer in Lubuntu: mplayer2. After 8 months, the default media player in Lubuntu 12.04 just stops. Yes, I have an old computer, that's why I use Lubuntu. Why not have vlc as the default player?

---

### Post by sudodus on 2013-01-14
There is a fix now according to this link :-)
[[COLOR="Red"]https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974125[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/mplayer2/+bug/974125")

See this link how to enable ''ubuntu-proposed', where you can find the new and working version of mplayer2
[[COLOR="red"]https://wiki.ubuntu.com/Testing/EnableProposed[/COLOR]]("https://wiki.ubuntu.com/Testing/EnableProposed")

I hope it will soon come into the standard repo.

---

