---
title: "&quot;Fake&quot; MKV file doesn't play, but does in Windows"
date: 2016-03-30
forum: Multimedia Software
---

### Post by toxicdaniel on 2016-03-30
How to make it work?

---

### Post by Rob Sayer on 2016-03-30
According to your other posts you're actually using Mint, so while you may get suggestions to install ubuntu-restricted-extras, I wouldn't install them on a Mint system.  BTW I have 2 Mint installs.

You may have dl'ed and installed the Mint version without codecs.  Go into synaptic package manager, hit the search button, enter mint-meta-codecs.  If it isn't installed, install it.

I'm also not sure what you mean by a fake video file, but I wouldn't be too eager to try playing it in Windows.  I'd run an AV scan if I were you.

---

### Post by Yellow Pasque on 2016-03-30
What do you mean by "fake" mkv? Give us the mediainfo on one of these files so we know hat we're actually dealing with here:
```
sudo apt-get install mediainfo
mediainfo somefakemkv.mkv
```

---

