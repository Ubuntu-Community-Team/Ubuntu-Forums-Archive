---
title: "so many distros for audio..."
date: 2007-10-07
forum: Multimedia Production
---

### Post by leader303 on 2007-10-07
first of all, hi to everybody!

i'm new here, new to linux and searching for a good distribution for audio/midi needs. i know there are some, but...
what are the differences? which ones have you tried and compared? which ones have 64bit versions?
i need my interface (edirol ua-101) supported, very low latencies, vst support, and i'm interested in this wine.asio thing, since i'll have to integrate one or another program from my xp-times.

thanks in advance,
good night.

---

### Post by Stochastic on 2007-10-08
Hi and Welcome,

I have tried a number of linux audio distros and I most certainly prefer (and currently run) UbuntuStudio [http://www.ubuntustudio.org](http://www.ubuntustudio.org). It doesn't have a 64bit version yet but I think the next release (10 days away) might have that as an option.  Overall it's one of the more user-friendly audio distros you'll come across and with the large community behind it, it is most likely going to see the largest development speeds.
64studio is also a worthy contender (or was last time I tried it) as it is 64 bit, designed on a debian system, and is directed purely toward music.  But I found many of the programs I had come to know and love lacking from its repos.

You mentioned VST support, but unfortunately for the time being, if you want VSTs you need to run a 32bit system and there's a little bit of work to get it configured.  Here's a guide I wrote for getting VST support in UbuntuStudio [How To: Install VST support (fst) in UbuntuStudio](http://ubuntuforums.org/showthread.php?t=557466)

Hopefully you'll find the world of FOSS very welcoming and useful, just as I have.

---

### Post by dz0004455 on 2007-10-08
ya, definatly ubuntu studio, its based on ubuntu, and i'm kinda running it right now, i just installed the themes, and all of the software, and its great!

---

### Post by paulg on 2007-10-11
I think 64studio maybe the best (possibly only?) contender for 64bit support presently. I think VST support is easily added to this distro. It's based on Debian so a lot of the repositories would work if you needed anything out

I personally use Ubuntu Studio but my computer is a desktop first and [poor excuse for a] home studio second. Ubuntu Studio comes with all the conveniences of Feisty/Gutsy. I also don't have a 64bit processor.

Other contenders would be dynebolic - a Live CD that can be installed locally' and the one distribution that's been around the longest that is based on Fedora Core (sorry, don't remember the acronym for it right now). 

:guitar:

---

### Post by distort on 2007-10-19
There's also pure:dyne, which is based on dyne:bolic and specializes on music.

---

### Post by Rexbron! on 2007-10-19
> **paulg said:**
> I think 64studio maybe the best (possibly only?) contender for 64bit support presently. I think VST support is easily added to this distro. It's based on Debian so a lot of the repositories would work if you needed anything out

I personally use Ubuntu Studio but my computer is a desktop first and [poor excuse for a] home studio second. Ubuntu Studio comes with all the conveniences of Feisty/Gutsy. I also don't have a 64bit processor.

Other contenders would be dynebolic - a Live CD that can be installed locally' and the one distribution that's been around the longest that is based on Fedora Core (sorry, don't remember the acronym for it right now). 

:guitar:

Ubuntu Studio 7.10 has full 64-bit support.

---

### Post by angelsguitar on 2007-12-23
> **paulg said:**
> I think 64studio maybe the best (possibly only?) contender for 64bit support presently. I think VST support is easily added to this distro. It's based on Debian so a lot of the repositories would work if you needed anything out

I personally use Ubuntu Studio but my computer is a desktop first and [poor excuse for a] home studio second. Ubuntu Studio comes with all the conveniences of Feisty/Gutsy. I also don't have a 64bit processor.

Other contenders would be dynebolic - a Live CD that can be installed locally' and the one distribution that's been around the longest that is based on Fedora Core (sorry, don't remember the acronym for it right now). 

:guitar:

There's a version of Ubuntu Studio for 64bit processors already. I have both the 32 and 64 bit versions.

I have tested 64studio too.  It's a really nice distro for audio and music work, but it didn't suit me.  I agree: Ubuntu Studio gives all the conveniences of a regular Ubuntu distro, plus it's preconfigured for audio work.  Besides, it's a lot easier to customize; everything just works with little or no work.:)

The Fedora Core distro you are talking about is Planet CCRMA. I can't comment on that one, as I have not used it.

---

### Post by Pocadotty on 2007-12-25
I have used Planet CCRMA a bit, and I didn't care for it much.  Probably because I am not a fedora fan. :|

I use UbuntuStudio (7.10) and love it. It has the benefit of Ubuntu's ease of use with a lot of audio performance.  The realtime kernel is great for audio work, but I also have the generic kernel for when I am not doing media production (because the realtime kernel is very specialized and has some trade offs that only become important when doing a lot of "normal" tasks)

---

### Post by oskar2000 on 2007-12-26
Well, I do like Fedora, and CCRMA is a very reliable project. It might be a good idea to stay one or two releases behind though.
I prefer Ubuntu... All the ubuntu studio packages are available through the official ubuntu repos. I don't understand why projects like this one feel the need to make their own fork and artwork. If you have ubuntu, you just need to install the meta packages... not even that. Get the realtime kernel + the programs you need, and you're good to go.
There is no work around to use 32 bit wine with a 64 bit jack... 
Overall it's still too much hassle for too little gain... stick with 32 bit.

---

