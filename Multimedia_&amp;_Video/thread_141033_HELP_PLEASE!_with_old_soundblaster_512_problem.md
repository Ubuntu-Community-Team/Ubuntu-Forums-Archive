---
title: "HELP PLEASE! with old soundblaster 512 problem"
date: 2006-03-07
forum: Multimedia &amp; Video
---

### Post by stevesherrin on 2006-03-07
I apologize in advance for my ignorance... I am a complete newbie (1hr old) to linux and am havin trouble with my soundcard.  it is a pci Sounblaster 512 (circa 1999), and I have tried lspci but it doesn't detect the card.  Additionally I found drivers for the card at opensource.creative.com but it is all source and header files, I'm not sure how to build and install.  I have also tried an old ISA version of the SB card, but it was not detected either.   Any advice?

---

### Post by Teroedni on 2006-03-07
have you tried several different pci ports?



Open a terminal window and use this command

```
sudo lshw -class multimedia
```

If your card is connected and is working, you should get a output here.

---

