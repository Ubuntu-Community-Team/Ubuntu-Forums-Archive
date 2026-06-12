---
title: "image scanning software"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by dysolve on 2008-01-05
hello all, this might sound funny but I am looking for software that will let me bulk scan images.. I have about 3000 ( no joke) to scan in. i just want something i can put the photos on the scanner bed press preview after checking the preview I then press  scan but once i press the scan button it automaticcly saves the images as jpg in a very good res and then i do the same again for the next image.. 
thanks
David.

---

### Post by JKyleOKC on 2008-01-05
Have you looked at Xsane? It includes the capability to do bulk scanning and control your automatic document feeder. My scanner is only flatbed with no feeder so I don't know how well it works though...

---

### Post by Yoshiman007 on 2008-01-05
I am in need of software for scanning as well, and I have looked at Xsane, but I believe that my scanner (HP psc 2210 all-in-one) is not supported by it...Is there any way to make my printer work, or should I try new software?

---

### Post by carrett on 2008-01-05
xsane is the standard, mostly widely supported scanner program out there. One thing you may have to do after installing it is add yourself to the scanner group:

```
sudo adduser yourusername scanner
```

---

### Post by Yoshiman007 on 2008-01-06
I tried adding myself to the scanner group, but I was already in that group. I have also tried installing older HPLIP drivers that would possibly support my printer (the PSC 2210). But that seemed to get me only the slightest bit further. I can still print and successfully configure my printer through the cups server ([http://localhost:631](http://localhost:631)) but Sane still insists that i have no scanner attached. I have also edited the /etc/sane.d/dll.conf and added a few other hp items besides the ones there, so now i have hpoj, hplip, hpaio, hpijs, in there. Still no success. I may attempt to downgrade sane in hopes of a cure. Thanks for the suggestion, and any more ideas would still be appreciated!

---

