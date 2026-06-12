---
title: "Mythweb Direct Download - file extension names"
date: 2010-08-06
forum: Mythbuntu
---

### Post by hundred1906 on 2010-08-06
When I use Mythweb to output a recording as an .mpg file (using the Direct Download button) the file ends up with a name suffix consisting of ".mpg..mpg.". Ie too many mpg suffixes.

This has started to occur only since a recent update of my system to 10.04, which included a Mythtv update.

There must be a parameter setting somewhere that describes the suffix, but where is it. Or where else do I look in my set-up to resolve this as a problem.

---

### Post by hundred1906 on 2010-08-07
Anyone able to help with this, please? Does anyone else have this as a problem?

---

### Post by ian dobson on 2010-08-08
Hi,

I'm seeing this aswell, since upgrading to autobuilds. I can still watch the downloaded videos with vlc on my windows laptop so it's not a problem for me.

Regards
Ian Dobson

---

### Post by tgm4883 on 2010-08-08
It's an upstream bug that was fixed in trunk. I'm not sure if it was fixed in 0.23.1 though.

---

### Post by ian dobson on 2010-08-08
> **tgm4883 said:**
> It's an upstream bug that was fixed in trunk. I'm not sure if it was fixed in 0.23.1 though.

So how do you get 0.23.1? I already have autobuilds enabled and have just done am apt-get update/upgrade and am at 25423.

Regards
Ian Dobson

---

### Post by pu15e on 2010-08-08
> **tgm4883 said:**
> It's an upstream bug that was fixed in trunk. I'm not sure if it was fixed in 0.23.1 though.

Our network is up to date as of a week or two ago (recent enough to fix the fanart dilemna), yet still doubles up the .mpg extensions through MythWeb...

While a slight annoyance, it doesn't bother me too much - the recordings I pull through MythWeb are always gonna be transcoded anyways, so thus will always wind up with a new (.avi) filename at any rate. Even before transcoding the files are completely usable as they still have an .mpg extension at the end of the day :-)

Cheers,
 Mattt.

---

### Post by tgm4883 on 2010-08-10
Hmm, I can't find the bug report right now, I'll continue searching.

As for auto-builds, there is now a 0.23.1 PPA, 0.23.0 PPA will not receive more updates. You can manually edit the sources for 0.23.1, you will need to disable mythbuntu-repos to do this though. I'll update mythbuntu-repos when I can, but it will probably be after thursday (feature freeze)

[https://edge.launchpad.net/~mythbuntu/+archive/0.23.1](https://edge.launchpad.net/~mythbuntu/+archive/0.23.1)

---

