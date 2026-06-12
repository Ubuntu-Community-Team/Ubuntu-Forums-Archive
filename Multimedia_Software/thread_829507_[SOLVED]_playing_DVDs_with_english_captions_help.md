---
title: "[SOLVED] playing DVDs with english captions help"
date: 2008-06-14
forum: Multimedia Software
---

### Post by scotcella on 2008-06-14
Hi all,

Been using Ubuntu for a while- now using Hardy with most stuff running out of the box with a few exceptions. I've managed to fix each of my issues (blue tooth, wireless etc etc) one at a time with very minimal fuss.

My little project is trying to make DVDs play on my laptop, I followed and installed medibuntu or what ever it is called and it worked straight away after i restarted my little darling.

Now my problem lies with subtitles and the main menu which does not give me that option when i start up the dvd. It just goes straight to playing the dvd in the Movie Player software that came with Hardy. 

Do i need to install another movie player software so I can access the menu, special features, subtitles/language settings etc?

I definately need to have subtitles as I am deaf, so hence my question.

---

### Post by mc4man on 2008-06-15
What you want to install is vlc and or totem-xine, both have good subtitle support. (vlc is overall a 'better' player) run
```
sudo apt-get install vlc totem-xine
```
 try both and take your pick
If you want totem-xine to be your default totem player (recommended), run
```
sudo update-alternatives --config totem
``` and choose 2

If you want vlc to be your default (autoplay) player for dvds read here
[http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

### Post by scotcella on 2008-06-15
Many thanks, that did the trick!

I'm really impressed.

---

