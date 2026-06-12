---
title: "Microphone not working"
date: 2011-11-17
forum: Multimedia Software
---

### Post by new123 on 2011-11-17
Hi,
I had this problem not only on Lubuntu, but Ubuntu and Mint. On Windows my mic works as it should.
Its integrated to headphones (*[CNR-HS3]("http://www.canyon-tech.com/products/voip/headsets/CNR-HS3")*) and my sound card is 'Realtek AC'97 Audio for VIA (R) Audio Controller'; maybe its just because my soundcard is not installed but I dont know how to check whether is or not.

---

### Post by Rodney9 on 2011-11-17
> **new123 said:**
> Hi,
I had this problem not only on Lubuntu, but Ubuntu and Mint. On Windows my mic works as it should.
Its integrated to headphones (*[CNR-HS3]("http://www.canyon-tech.com/products/voip/headsets/CNR-HS3")*) and my sound card is 'Realtek AC'97 Audio for VIA (R) Audio Controller'; maybe its just because my soundcard is not installed but I dont know how to check whether is or not.


Go to Menu - Accessories - LXTerminal and type in this code  
```
alsamixer
```
make sure your mic is selected by using the space bar.

Further sound troubleshooting
Have a look at this site - 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and this one, more up todate, but still a work in progress, however very good - 

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

For How-To's, Information and Screen-Casts on [COLOR="Blue"]Lubuntu[/COLOR] go to the
Lubuntu One Stop Thread - 

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)


Rodney

---

