---
title: "Google Earth Looking Different"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by desaivarun_104lts on 2011-04-08
Hi,

Recently i installed Google Earth in my Acer Aspire one 532H,Natty OS,Google earth looking different..The words are farer from one each other..I don't know why they are looking like that..

The screenshots of the google earth are below.

[http://imgur.com/p4Pjh&akSN1&Dg2Z5&wtEvp](http://imgur.com/p4Pjh&akSN1&Dg2Z5&wtEvp)

Any ideas what to do..

---

### Post by oldsoundguy on 2011-04-08
call Google and complain.  They wrote the program, not anybody associated with Ubuntu.

(it IS telling you that you are running at an INCOMPATIBLE resolution .. that is, most likely, the reason behind the funky display!)

---

### Post by Kivech on 2011-04-23
Actually it does this in any resolution, so it is not that weird to ask about it here.

I have the exact same issue. It seems to me that the font in Natty might be a problem.

Did anyone successfully install Googleearth on Natty? If so, please share us your tricks.

---

### Post by SevenMachines on 2011-04-23
dont know about your resolution warning, google earth uses qt4 fonts though. so you can change them using 
```
 $ qtconfig-qt4
```
might help

---

### Post by Erlander on 2011-04-24
I had Google Earth installed under v10.10 and upgraded to Natty.

It is working well.  So it is possible!

I can't say any more than that.  Might be interesting if I do a clean install!

---

### Post by Hreinsi on 2011-04-24
[http://gamblis.com/2011/03/31/how-to-install-google-earth-in-ubuntu-natty-narwhal-11-04](http://gamblis.com/2011/03/31/how-to-install-google-earth-in-ubuntu-natty-narwhal-11-04)

Works for me):P

---

### Post by nanouser on 2011-04-24
Google Earth runs great on this Acer Aspire One 522 Netbook. I did have to install the ATI restricted driver as the open source Gallium driver had problems displaying the maps, most of the map area was black.

I downloaded Google Earth directly from Google and installed it using Ubuntu Software Center. It did complain about running at 1280x720. Fonts looked normal, not spaced out like yours. Here is a thread on the Google Earth forums that may help with you font rendering problem: [http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=3fe67ea84f63bcd8&hl=en)

---

