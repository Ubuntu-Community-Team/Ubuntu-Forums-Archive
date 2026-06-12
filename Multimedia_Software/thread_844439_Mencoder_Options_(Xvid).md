---
title: "Mencoder Options (Xvid)"
date: 2008-06-29
forum: Multimedia Software
---

### Post by Major_Kong on 2008-06-29
Could someone tell me which options does the xvid profiles (simples profile, advanced profile, etc.) restrict or change ? 

Or point me to a irc channel/forum where i can get these answears ?


PS: And which options regard only a 2-pass encoding ?

---

### Post by chewearn on 2008-06-30
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#XviD](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide#XviD)

[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html)

---

### Post by Major_Kong on 2008-06-30
> [http://www.mplayerhq.hu/DOCS/HTML/en...feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en...feat-xvid.html)

Tks, but i still need a clarification on second pass opts.

---

### Post by chewearn on 2008-06-30
> **Major_Kong said:**
> Tks, but i still need a clarification on second pass opts.

I don't quite understand.  You will like an explanation for what the options do?  Or how to pass the option to mencoder?

For two-pass encoding, the first pass analyze video to create the optimum bitrate profile.  The second pass is the actual encoding, so any encoding options you enabled, will be applied during the second pass.

---

### Post by Major_Kong on 2008-06-30
Neither.

I want the options that affect the second pass only. Options that are solely for the second pass.

---

### Post by chewearn on 2008-07-01
> **Major_Kong said:**
> Neither.

I want the options that affect the second pass only. Options that are solely for the second pass.

Ok, I understand now.  Here is an [FAQ]("http://www.gromkov.com/faq/conversion/xvid_options.html"), which I think implicitly answer the question, but I'm not knowledgeable to give an intepretation.

---

