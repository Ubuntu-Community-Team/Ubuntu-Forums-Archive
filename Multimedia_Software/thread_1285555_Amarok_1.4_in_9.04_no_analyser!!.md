---
title: "Amarok 1.4 in 9.04 no analyser!?!"
date: 2009-10-07
forum: Multimedia Software
---

### Post by Marco7 on 2009-10-07
I recently downgraded to Amarok 1.4 version on my Ubuntu 9.04 system.

I first installed it through the Amorok website by downloading debs of the program and various dependencies and installing them.  Don't ask me why I did it that way...

The analyser didn't work. By this I mean the little jumping bars animation that goes along with the music. I love that thing. So I tried installing more Amarok debs from the website, anything that said analyser.  

Then I opened a terminal and did a (sudo apt-get install Amarok14) to install a fresh installation over the old one and that seemed to work but still no analyser.

I think my installation might be missing some packages, or maybe it has something to do with my audio card, that uses it's own ASLA driver as a mixer.  Volume control master volume switch slider doesn't work, but it leads to a mixer window that does.

Please help, I can't go on listening to music on my computer without the corresponding visualisation!

---

### Post by Marco7 on 2009-10-08
None of my visualisations seem to be responding.  They open and seem to be on-line, but receive no input, or audio output, or whatever.

---

### Post by Marco7 on 2009-10-08
Got it.

I changed from the yauap engine to the xine engine and that enabled my visualisaitons.

I seem to remember that being the default engine when I was running hardy.

I may have enabled the xine engine the other day while making my system multimedia ready using the sticky at the top of this forum (Comprehensive Multimedia & Video Howto)

---

