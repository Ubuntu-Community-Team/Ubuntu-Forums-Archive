---
title: "Kodi 17 doesn't update on Ubuntu Gnome 17.04 (Zesty)?"
date: 2017-04-21
forum: Multimedia Software
---

### Post by russkyca on 2017-04-21
All of a sudden, I have a problem with software not wanting to update... I don't like how you have to figure out what to click so you can see what the software is!!!   Finally, I figured out it's Kodi software.   

I can re-produce it, doing these steps.
1) Select Software Updater
Message:   Updated Software is Available for this Computer.  Do you want to install it now?   (Yes!  Why not?!?)
Kodi is checked   (says:   the updates have already been downloaded (there's a button for 'Install Now' - so I click it)
2) Sometimes it shows what didn't work but most of the time - it doesn't!   Very buggy!   I'm talking about 'Software Updater' which is an awfully written program!  

 This is on top of another problem (unrelated to Kodi) trying to watch a video (stream video) - which I use a TV - to do so.   I use 'second displays' in Display settings and drag over the video from the Chrome browser.   At some point, it crashes/freezes and half the screen is fragmented or pixelated (I don't know what you call it!).   I posted about it in another thread - in the General section.   But, these increasing problems are very frustrating!

---

### Post by sp40140 on 2017-04-25
Hello
If you just want to install the updates, you can disable the ppa for kodi from software sources. And that will bypass the kodi.
If you want to fix kodi error, then I think you have a kodi deb file already in "/var/cache/apt/archives/". search for anything kodi related in that folder (ls kodi*) and remove it. That should fix the kodi conflict.

---

