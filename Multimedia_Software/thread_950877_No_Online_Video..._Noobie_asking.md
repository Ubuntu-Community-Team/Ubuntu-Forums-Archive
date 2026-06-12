---
title: "No Online Video... Noobie asking"
date: 2008-10-17
forum: Multimedia Software
---

### Post by Tim 3255 on 2008-10-17
Hi to all.
I just make the jump to Ubuntu 8.1. It's a little overwhelming but I'll get hang of it eventually!
One area that really has me stumped is the lack of online video regardless of browser used (Firefox 3.03, Opera and Epiphany for sure). I even loaded IE for Linux with Wine and videos didn't play there either!
My unit is a Thinkpad X40 and so far everything is working as it should, including CD and DVD playback, but videos on Yahoo (for example) or YouTube show only a blank screen where the video should be. I have all the latest drivers and codecs, I think!
Any help would be most appreciated. 
Tim

---

### Post by sirhalos on 2008-10-17
Ubuntu doesn't come with codecs or flash (youtube uses) by default. However this site should help you out you just copy and paste what they say in your terminal. Keep the site bookmarked it comes in handy.

[http://ubuntuguide.org](http://ubuntuguide.org)

What you are looking for though is installing flash paste this in a terminal window.

sudo apt-get install flashplugin-nonfree

And installing codecs paste this in a terminal window.

sudo apt-get install ubuntu-restricted-extras

---

### Post by Tim 3255 on 2008-10-17
I appreciate the links and info. I reloaded flash and the codecs through terminal but  unfortunately still no video. There is a little improvement however. After about 20 seconds the Yahoo video screen expands slightly to form a rectangle and a blue rotating circle appears in the middle...that's it.
Tim

---

