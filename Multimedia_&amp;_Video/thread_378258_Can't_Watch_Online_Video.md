---
title: "Can't Watch Online Video"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by NautTboy on 2007-03-07
After trying to play dvd and vcd with unsuccessful attempt, I'm testing online video now.

I'd download all the video player available for ubuntu.  I'd even did the addon for firefox and media  player connectivity.  I can watch on youtube.com 
 
Anyone with a good solution?

---

### Post by ssavelan on 2007-03-10
sudo apt-get install libxine-extracodecs

use totem-xine

try to remove all other plugins

use totem mozilla plugin

the extracodecs should help you play many formats... i don't know how to set up gstreamer-based stuff... xine is good and easy.

---

### Post by NautTboy on 2007-03-11
[B][COLOR=black]Well  here's is what I got when I put in my DVD. [I]First picture

[/I]Here is what @mozilla plug-in page. Window media player unavailable. *second picture*
[/COLOR][/B]

What is MRL, keep getting "NO MRL"

---

### Post by ingo on 2007-03-29
I had a similar problem using Kaffeine and DVBT - kept on getting > xine: cannot find input plugin for MRLSo I went into adept and installed every library that showed up under "libd" and hey presto! I can watch the telly!

---

