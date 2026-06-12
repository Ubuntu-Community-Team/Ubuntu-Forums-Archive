---
title: "[SOLVED] Won't install LastFM"
date: 2008-06-28
forum: Multimedia Software
---

### Post by Crazy K on 2008-06-28
I recently tried to install LastFM to my computer, but I get this error:

[http://img.photobucket.com/albums/v434/CrazyK12/Screenshot-1.png](http://img.photobucket.com/albums/v434/CrazyK12/Screenshot-1.png)

What does this mean? 

Also do I have to do this:
[I]
Last.FM .deb apt repository.
This repo should be valid for all debian based distributions which ship with =>Qt 4.2 or have =>Qt 4.2 in their repos. Ubuntu/Debian/etc.

First, import our GPG key:

wget -q [http://apt.last.fm/last.fm.repo.gpg](http://apt.last.fm/last.fm.repo.gpg) -O- | sudo apt-key add -

Then add one of the following lines to your /etc/apt/sources.list file, then apt-get update, and apt-get install lastfm.

Stable:
deb [http://apt.last.fm/](http://apt.last.fm/) debian stable

Testing:
deb [http://apt.last.fm/](http://apt.last.fm/) debian testing [/I]

And if so, how do you do this?

---

### Post by Crazy K on 2008-06-29
Ok, I tried to mess around with it myself, but I couldn't figure it out. So, I need a detailed list on how to install LastFM on my Ubuntu. Please help.

---

### Post by rainwalker on 2008-06-29
Yes, you have to follow those steps.

1. In a terminal, run ```
wget -q http://apt.last.fm/last.fm.repo.gpg -O- | sudo apt-key add -
```

2. Open System > Administration > Software Sources and add > deb [http://apt.last.fm/](http://apt.last.fm/) debian stable to the list in the "Third-Party Software" tab

3. Refresh your package list when it asks you, then install the Las.fm package via Synaptic

---

### Post by Crazy K on 2008-07-02
When I add the deb [http://apt.last.fm/](http://apt.last.fm/) debian stable to the Software Sources, do I click on Revert? I don't get it. 

I don't know where this Synaptic is.

Alright, I found it, just took me a while to figure it out, it works now. Thanks a ton! :)

---

### Post by rainwalker on 2008-07-02
Don't forget to mark your thread as solved :)
It's under Thread Tools at the top

---

### Post by rossjman1 on 2008-07-02
If I were you I would use the testing version vs. the stable. Debians stable repos(in general) have applications that arnt very new.

---

