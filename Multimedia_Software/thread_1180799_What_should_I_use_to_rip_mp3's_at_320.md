---
title: "What should I use to rip mp3's at 320?"
date: 2009-06-07
forum: Multimedia Software
---

### Post by pseudomonasaeruginosa on 2009-06-07
I've searched with a variety of keywords and can't find anything that makes sense that will tell me how to do this.
I feel stupid, but I haven't needed to do this before, and I can't figure out how, so I'm asking.
What program should I use, and how, to rip a cd at 320 to mp3 format?
I need it specifically at 320- and at mp3- and I don't care if it's better to do the variable thing.
I've tried several programs and they all seem to be telling me I want to rip at an average of 256 with up to 320 where it's complex, and I don't want that, I want 320.
I really appreciate any help.

---

### Post by SuperSonic4 on 2009-06-07
I've heard good things about abcde although I do not know how to use it myself

Audex and K3B work but both are KDE apps.

At a push you can use cli lame to convert uncompressed wav files

---

### Post by Arup on 2009-06-07
Ripper X, its in the repos.

---

### Post by logos34 on 2009-06-07
you need to distinguish between ripping and encoding--two different things. 

For good rips, at a minimum you want to be using (full) cdparanoia.  Pick from among [these recommended apps]("https://help.ubuntu.com/community/CDRipping#Other%20CD%20Ripping%20Software").  Rubyripper is a two-pass secure ripper.  If you want the best, use Exact Audio Copy (AccurateRip).  EAC runs on Wine.  

Any of them will allow you to specify CBR 320 mp3 output.  You need lame:

sudo apt-get install ubuntu-restricted-extras

---

### Post by andrew.46 on 2009-06-08
Hi SuperSonic,

> **SuperSonic4 said:**
> I've heard good things about abcde although I do not know how to use it myself

It is pretty easy to use:

HOWTO: Convert music CDs to MP3 using the Command Line
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

and to manipulate the bitrate this section should be altered:

```

# Specify your required encoding options here. Multiple options can
# be selected as '--preset standard --another-option' etc.
**[COLOR="Purple"]LAMEOPTS='--preset extreme' [/COLOR]**

```

Andrew

---

### Post by logos34 on 2009-06-08
> **andrew.46 said:**
> 
**[COLOR="Purple"]LAMEOPTS='--preset extreme'[/COLOR]**
[/CODE]

If you want 320, then I believe you would substitute:
> 
**LAMEOPTS='--preset [COLOR="Red"]insane[/COLOR]**'

[http://wiki.hydrogenaudio.org/index.php?title=Recommended_LAME#Technical_information](http://wiki.hydrogenaudio.org/index.php?title=Recommended_LAME#Technical_information)

---

### Post by glotz on 2009-06-08
> **pseudomonasaeruginosa said:**
> I've tried several programs and they all seem to be telling me I want to rip at an average of 256 with up to 320 where it's complex, and I don't want that, I want 320.That makes no sense to me, why would you want to do that?

---

### Post by logos34 on 2009-06-08
> **glotz said:**
> That makes no sense to me, why would you want to do that?

some people just want the highest lossy setting, never mind the fact that you can't tell it from vbr -V0, or that filesize is inflated (but who cares in this day and age of terabyte hdds and multi-GB flash players?)

---

