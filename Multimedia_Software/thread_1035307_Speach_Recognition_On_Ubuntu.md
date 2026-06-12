---
title: "Speach Recognition On Ubuntu"
date: 2009-01-09
forum: Multimedia Software
---

### Post by martrn on 2009-01-09
After searching over 494,000+ links from Google and spending quite a few days in the search I was wondering if anybody could point me in the right direction for getting any kind of speech recognition working on ubuntu.

I first tried getting, Sphinx [http://cmusphinx.sourceforge.net/html/cmusphinx.php]("http://cmusphinx.sourceforge.net/") to work as it comes in the latest version and compiled, however the every day instruction in getting Sphinx to work with the acoustic model architecture, is not quiet so clear cut, and achieving anything other than an inaccurate or annoying response is not going to be happening any time soon.  OK I have read the disclaimer that Sphinx is not a final product and thought I might get a level of response but that was't going to be.

I therefore look at the Julius Speech Recognition Engine.
See :- ([http://julius.sourceforge.jp/en_index.php]("http://julius.sourceforge.jp/"))
The Blurb looks good with "Julius" with making claims bout it being high-performance, two-pass large vocabulary continuous speech recognition (LVCSR) decoder software for speech-related tasks based on word N-gram and context-dependent HMM, it can perform almost real-time decoding on most current PCs in 60k word dictation task.

This was good until I tried compiling it where it then Julius (decoding program,) needs a language model (with verbs) and acoustic model (actual sounds) for the target language.  This has vague reminiscences of trying to get someone to speak or teach them to talk.

Has anyone actually got a working speech recognition system working On Ubuntu. ?

---

### Post by gettinoriginal on 2009-01-09
After all that searching, you have probably already seen this, but thought I would pass it along:

[http://live.gnome.org/GnomeVoiceControl](http://live.gnome.org/GnomeVoiceControl)

---

