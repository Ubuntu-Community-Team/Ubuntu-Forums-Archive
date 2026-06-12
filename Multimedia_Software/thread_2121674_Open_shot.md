---
title: "Open shot"
date: 2013-03-02
forum: Multimedia Software
---

### Post by brianv7 on 2013-03-02
I can't get the transitions to work, I place them inbetween the cuts but on playback they don't work. what could i be doing wrong?:guitar:

---

### Post by tgalati4 on 2013-03-02
What version are you running?

In a terminal:

tgalati4@Mint14-Extensa ~ $ apt-cache policy openshot
openshot:
  Installed: (none)
  Candidate: 1.4.3-1
  Version table:
     1.4.3-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages


Have you gone through these steps:

[http://www.openshotusers.com/help/1.3/en/ar01s19.html](http://www.openshotusers.com/help/1.3/en/ar01s19.html)

---

### Post by uc50_ic4more on 2013-03-02
> **brianv7 said:**
> I can't get the transitions to work, I place them inbetween the cuts but on playback they don't work. what could i be doing wrong?:guitar:

If by "in between" you mean that you have a clip, then the transition, then another clip, to quote teh interweb: "your doing it wrong" :^)

On the timeline, instead of this:

CLIPONE|TRANSITION|CLIPTWO

it has to appear like this:

CLIPONE
        TRANSITION
        CLIPTWO

**IF** the formatting of the spacing and text above appears to you how I intended it, the transition is taking place UNDER the "NE" in "CLIPONE" and OVER the "CL" in "CLIPTWO"; meaning that the transition's effects would take place during the overlap of "NE" and "CL".

EDIT: Nope. After posting my reply, I see the forum's software has removed the spacing necessary to properly display this... I'll try 'er again with underscores:

CLIPONE
        _____TRANSITION
        _____CLIPTWO

---

### Post by QIII on 2013-03-02
*Thread moved to** Multimedia & Video***

---

### Post by brianv7 on 2013-03-03
thanks i'll try that, i was used to vegas, or imovie, wheres u just split a clip and then slip a trans in, if i'm reading you right its stacked tracks? i'll play around with it. I just wanted to get away totally  from windows and mac and i'm looking form something decent with a limited learning curve, i m hoping open shot is it. tanx 4 replying  :guitar:

---

### Post by uc50_ic4more on 2013-03-03
> **brianv7 said:**
> thanks i'll try that, i was used to vegas, or imovie, wheres u just split a clip and then slip a trans in, if i'm reading you right its stacked tracks? i'll play around with it. I just wanted to get away totally  from windows and mac and i'm looking form something decent with a limited learning curve, i m hoping open shot is it. tanx 4 replying  :guitar:

I've used Vegas (and loved it passionately) and currently use Final Cut. The offerings you'll find for Linux will all be limited in function and learning curve.

---

