---
title: "advanced graphics question.... can anyone help me?"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by xxFelixDCatxx on 2007-01-02
okay here's the scenario....

I have dual graphics cards in my computer.  One is an nvidea, the other a radeon.  I want to use dual screens across both, but can't figure out how in the world to do so.

I've been told that by default it should just work, but obviously this is not the case...

Sooooo.... can anyone help me with this, or should I just resign myself to windows?  at this point in time this issue is the only one that is keeping me from going totally ubuntu in all aspects of my computing.

---

### Post by pseudonym on 2007-01-02
Just out of curiosity, is there any particular reason why you are using two cards when I am guessing that at least one of them has multiple monitor outputs?...

---

### Post by xxFelixDCatxx on 2007-01-02
as much as i wish i had multiple outputs on one of the two cards, sadly I don't.

---

### Post by Lord Illidan on 2007-01-02
> **xxFelixDCatxx said:**
> okay here's the scenario....

I have dual graphics cards in my computer.  One is an nvidea, the other a radeon.  I want to use dual screens across both, but can't figure out how in the world to do so.

I've been told that by default it should just work, but obviously this is not the case...

Sooooo.... can anyone help me with this, or should I just resign myself to windows?  at this point in time this issue is the only one that is keeping me from going totally ubuntu in all aspects of my computing.

Ouch, one nvidia, and one ATI? Does it work in windows? I have no idea what it would do under Linux.

---

### Post by xxFelixDCatxx on 2007-01-02
sadly after googling for about an hour.... i still don't see anything... I know anything is possible in linux, but obviously multiple moniter computing is not something linux supports...

too bad really, I'm not switching to an OS in which I would lose one of my 19in widescreen moniters.

---

### Post by Lord Illidan on 2007-01-02
> **xxFelixDCatxx said:**
> sadly after googling for about an hour.... i still don't see anything... I know anything is possible in linux, but obviously multiple moniter computing is not something linux supports...

too bad really, I'm not switching to an OS in which I would lose one of my 19in widescreen moniters.
No, it does support multiple monitor computing and multiple graphics cards. But when you interchange two brands, then it gets very difficult.

Read this, might help : [http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards](http://gentoo-wiki.com/HOWTO_Dual_Monitors#Setting_up_Two_Graphics_Cards)

---

### Post by xxFelixDCatxx on 2007-01-02
> **Lord Illidan said:**
> Ouch, one nvidia, and one ATI? Does it work in windows? I have no idea what it would do under Linux.

it works great under windows.... in fact I was surprised, but it was plug and play, automaticially set up everything for me.  sad but windows really does handle multiple moniter computing fairly well.

under linux it defaults to the AGP card.... or the Nvidea, i believe it's just ignoring the PCI card, but when i run the fglx (not sure if that's the right one, i've pulled another all nighter, and command line is starting to escape me)  and it does pull up the configuration for the ATI card, and it's obvious Linux knows it's there.

---

### Post by xxFelixDCatxx on 2007-01-02
> **Lord Illidan said:**
> No, it does support multiple monitor computing and multiple graphics cards. But when you interchange two brands, then it gets very difficult.

heh, more of a figure of speech really.... I'm a huge fan of plug and play, and to my knowlege (limited really to Ubuntu) there's no other way to get it working without a lot of command line interface, or a GUI way of doing this...

I'm actually beginning to doubt that it's possible, I can't seem to find any mention of cross brand graphics card spanning.

---

### Post by pseudonym on 2007-01-02
> **xxFelixDCatxx said:**
> I'm actually beginning to doubt that it's possible, I can't seem to find any mention of cross brand graphics card spanning.
Oh, it is possible. You have to manually edit your /etc/X11/xorg.conf file, which isn't hard. I had a dual-head multi-brand set up once with an AGP Matrox card and a PCI nvidia one. I followed [this howto]("http://www.linux.com/article.pl?sid=03/10/05/025207") to set it up. It's a little old, but the details are the same. Except where the author talks about the XF-86Config4 file, you just substitute xorg.conf. He's using the XFree86 X server, while these days we use Xorg. But they are configured in essentially the same way.

HTH :)

---

### Post by tseliot on 2007-01-02
> **xxFelixDCatxx said:**
> I have dual graphics cards in my computer.  One is an nvidea, the other a radeon.  I want to use dual screens across both, but can't figure out how in the world to do so.
If you're planning to use both the proprietary drivers then you can't.

fglrx and nvidia will conflict because of some files.

---

### Post by dmcdante on 2007-02-25
first of all, i'm sure you can do it somehow. there's always a way.
could be that there's no dri on one of them, but multiple monitor gaming is a thing you sure can live without. use the proprietary driver for one and the free one for the other, it'll be fine. google for "multiple monitors xorg" and you'll find a lot. don't give up!

---

