---
title: "Banshee won't change last.fm settings"
date: 2009-11-03
forum: Multimedia Software
---

### Post by OLFP on 2009-11-03
This is killing me right now. Banshee keeps automatically filling in the worng username and password for last.fm.  It doesn't matter if I change it, always goes back to an old name and a huge password string (which is wrong).

Where are the config files? Where is it getting my old name and that bizarre password from? I've tried removing ./config/banshee-1 and purging the banshee installation, but it keeps finding my old user name and the wrong password string.

---

### Post by travis.j.haynes on 2011-06-21
I realize this post is old, but I figured if anybody else has ever run into this problem, I might as well post my solution for it...

Start gconf-editor, and change apps/banshee-1/plugins/lastfm/username

How odd, not to mention extremely frustrating, that the program blocks you from being able to re-enter your user name after one attempt, and the only way around it is to hack into the configuration manually!

---

### Post by Jesua on 2012-06-22
I think that the solution goes first on the last.fm site.

First create a new account and log in to it.

Then on Banshee, form the menu Edit>Preferences>Source Specific choose the Last.fm Source, then log out and log in with the new credentials, on the website you will be asked to grant permissions to the aplication wait a few seconds and then click on the button on Banshee that says "Finish Log In".

Hope it helps...

---

