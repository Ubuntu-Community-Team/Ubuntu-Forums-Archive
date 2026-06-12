---
title: "which sound card?"
date: 2008-04-04
forum: Multimedia Production
---

### Post by lolzlolz on 2008-04-04
which sound card should i choose my requirements are:
under $50
works in windows vista and ubuntu
gives good sound in games and music
supports jack and midi (my onboard sound card doesnt support jack)
works with rosegarden (in other words jack again)
what cards do you guys suggest?
thanks :)

---

### Post by lolzlolz on 2008-04-07
bump,
i was thinking one in the xfi series, is there any specific kind there that does these things or is that not a good choice?

---

### Post by FakeOutdoorsman on 2008-04-07
Take a look at this before you buy: [Hardware Support Components Sound Cards]("https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards") [Ubuntu Wiki]
I use a Chaintech AV-710 which works fine for me. lspci output:
```
03:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)
```

---

### Post by FakeOutdoorsman on 2008-04-07
Creative hasn't been nice lately:
[Daniel_K, Who Fixed Creative's Broken Vista Drivers, Speaks Out]("http://blog.wired.com/gadgets/2008/04/daniel_k-who-fi.html")

Looks like there are some issues with the X-Fi:
[Creative labs X-Fi sound card unsupported]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/63352")

---

### Post by Sandsound on 2008-04-07
Creative... ?  [-X

I haven't looked back since I got my Audiophile 24/96, you can get it at a fair price if you by a used one.
There's just NO way to compare it's sound quality with Creative Xfi.

---

### Post by warbread on 2008-04-08
> **Sandsound said:**
> Creative... ?  [-X

I haven't looked back since I got my Audiophile 24/96, you can get it at a fair price if you by a used one.
There's just NO way to compare it's sound quality with Creative Xfi.

I definitely second this, but it's a different beast from other sound cards.  There's no 1/8" output, so you'll either need speakers with RCA inputs or an audio receiver.  TurtleBeach makes some decent cards, as well, but I don't quite know their typical price range.

---

### Post by FakeOutdoorsman on 2008-04-08
> **warbread said:**
> There's no 1/8" output, so you'll either need speakers with RCA inputs or an audio receiver.

You can also use an RCA -> female minijack cable.  Might degrade the quality, but it wouldn't matter too much with headphones.

---

### Post by warbread on 2008-04-08
> **FakeOutdoorsman said:**
> You can also use an RCA -> female minijack cable.  Might degrade the quality, but it wouldn't matter too much with headphones.

You could, and I in fact use a 1/4" to RCA adapter to run my mixer into my soundcard to great effect.  An 1/8" female jack on the output channel is a good way to get stereo, but that may not be enough for someone who's used to 5.1 or even 7.1 sound.  And yes, a separate receiver will split the signal, but it's not true surround sound.  For that, one needs either surround output on the card or an SPDI/F optical output.

---

