---
title: "Compatible Sound Cards?"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by BitTorrentBuddha on 2006-01-29
OK, after messing around trying to get my sound working on my SiS onboard sound card, I've decided to just go and buy a new one, what I need to know is what kind of cards are supported, I don't have any big constraints, just PCI and less than $20... all it needs to do is give me sound.

---

### Post by christhemonkey on 2006-01-29
Sound Blaster Live! 5.1
I think, maybe not less than $20...

---

### Post by BitTorrentBuddha on 2006-01-29
hmm, that looks good, but I don't need 5.1, just stereo. anybody know any cheaper cards?

---

### Post by BitTorrentBuddha on 2006-02-01
bump :(

---

### Post by Joss on 2006-02-02
Just because the sound card supports 5.1 doesn't mean that you can't run it 2.1 or even just 2.0 (stereo)

I have a creative card that goes up to 7.1 but I use just 2.1 and it has a config option for all the modes it supports.

So you really just need to check whether the card supports that (as $20 is about min price really) I'm sure Creative's site or Google will get you there.

- Joss

---

### Post by Sutekh on 2006-02-02
[QUOTE=Joss]Just because the sound card supports 5.1 doesn't mean that you can't run it 2.1 or even just 2.0 (stereo)

I have a creative card that goes up to 7.1 but I use just 2.1 and it has a config option for all the modes it supports.

So you really just need to check whether the card supports that (as $20 is about min price really) I'm sure Creative's site or Google will get you there.

- Joss[/QUOTE]
Which Creative card do you have?  Is it external/internal?  What sound module does it use (emu101k et. al)?
My SB Live 24bit has been giving me huge grief.  I cannot for the life of me get 5.1 working, although a speaker test works on all speakers
```

speaker-test -c6 -D plug:surround51
```

---

### Post by BitTorrentBuddha on 2006-02-02
All I need is the cheapest sound card I can get that supports 2.0 and works under ubuntu though.

---

### Post by Joss on 2006-02-11
I'm not a guru, but the alsa guys pretty much do the linux sound support and this link shows the various creative cards supported. (you can search other brands too)
[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-Creative_Labs#matrix")

I had a quick search of these forums for success stories and Soundblaster live! seems to work and the advice i found is get a PCI card (as it tends to autoconfigure) as opposed to ISA based cards, which you do have to manually configure.

Lastly, does your mb have onboard sound? I used that for ages! and it's free.

cost is down to eBay / local store, but the low end cards all seem to be <$10/£15 .

good luck

-- Sutekh .. I'm using just 2.1 I don't like surroud sound much ;P


- Joss

---

