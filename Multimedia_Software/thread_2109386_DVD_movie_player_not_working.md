---
title: "DVD movie player not working"
date: 2013-01-27
forum: Multimedia Software
---

### Post by prodriver on 2013-01-27
I'm a newbe and Just installed Ubuntu 11.10 on second computer. When I put in a DVD movie and select movie player I receive the following message&quot; AN ERROR OCCURRED Could not read DVD this may be because the DVD is encrypted and a DVD decryption library is not installed&quot; I'm lost. What must I do to get the DVD to play. Thanks

---

### Post by Frogs Hair on 2013-01-27
11.10 reaches end of life in 3 months so you may just want to install 12.04 before spending too much time on 11.10. For DVD playback you need to add this repository from Repository How To   :[http://www.medibuntu.org/](http://www.medibuntu.org/)

After you have added the repository install the package below. ```
sudo apt-get install libdvdcss2 
```

---

