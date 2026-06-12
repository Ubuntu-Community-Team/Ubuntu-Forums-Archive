---
title: "Hardware problems DVD Audiophile 2496 GF MX4000"
date: 2006-03-05
forum: Multimedia &amp; Video
---

### Post by craig552 on 2006-03-05
I've got a few issues with oome of my hardware.

Firstly my DVD drive initially wouldn't play DVD's. 
**sudo apt-get install libdvdcss2**
didn't solve the problem, but 
**sudo /usr/share/doc/libdvdread3/examples/install-css.sh**
did. However, playback is quite poor, the video skips, and the colour is a bit off.

Secondly my soundcard Audiophile 2496 wouldn't playback properly. But a quick forum search told me that it'll never work in 5.10. *([http://www.ubuntuforums.org/showthread.php?t=76788&highlight=2496)](http://www.ubuntuforums.org/showthread.php?t=76788&highlight=2496))*

Finally my graphics card, a cheep GF MX4000. Wouldn't allow X to load. Not a big problem, the onboard graphics work fine.

Other than these few issues, I've found Ubuntu a wonderful OS, naturally easy to use and very satisfying. I hope these little problems can be worked out for the next release. This is all that's holding me back on the big leap from Windows.

If anyone has any sugestions that may help resolve these problems, you'd make me very happy.

---

### Post by NoNo_231 on 2006-03-05
Maybe this link could help you playing the dvds without the problems you mention. Take a look.
[http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

For codecs you could try automatix (it's the easy way). 
[http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=138405&highlight=automatix)

---

### Post by craig552 on 2006-03-08
Thanks for that Instaling ALSA from Automatix solved the soundcard problem.
And i found this page which fixed my graphics card
[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
The DMA thing didn't work though - nevermind, I'll keep looking.

---

