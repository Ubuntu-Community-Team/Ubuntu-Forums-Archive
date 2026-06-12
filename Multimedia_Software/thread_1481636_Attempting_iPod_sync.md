---
title: "Attempting iPod sync"
date: 2010-05-12
forum: Multimedia Software
---

### Post by skawars on 2010-05-12
After now almost fully migrating to Ubuntu from w7, i'd like to find a way to manage my 120gb iPod classic.

I have a 120gb iPod classic, and more than 120gb of music, so have always used the sync feature on iTunes, using the checkboxes to deselect the stuff i don't listen to much.

I've been told that Banshee is now meant to "work like iTunes" in lucid lynx, but fail to see how it can do so. Although Banshee is failing to detect my iPod at all for some reason (any ideas?), so it's hard to see how it's mean to work.

Rhythmbox detects the iPod and shows all the music, but has no form of sync feature so is pretty useless for such as vast amount of music.

Any advice? cheers

---

### Post by boombox1387 on 2010-05-26
Banshee's tool for detecting iPods (podsleuth) has been having a hard time with the new Ubuntu.  I think a fix has been committed (and released?) but it hasn't been packaged up for Ubuntu yet, as far as I know.

If you're new to Ubuntu, you may not yet be familiar with PPAs.  In Ubuntu, PPAs are a great way to "subscribe" to third-party sources of software.  By adding a PPA to your list of sources, application developers can automatically push updates directly to your Update Manager.  If you haven't already, I'd recommend subscribing to the [Banshee-stable PPA]("https://launchpad.net/~banshee-team/+archive/ppa").  When the fix for iPod support in Ubuntu becomes available, you'll automatically get the update.

As far as checkboxes goes, Banshee doesn't use them.  You can sync to a playlist, though, so you can make a playlist of all the songs you want to sync (or make a playlist of all of your songs, then remove the ones you don't want to sync), and sync your iPod to that.

Hope this helps (and I hope that fix for iPods in Ubuntu gets released soon)!

---

