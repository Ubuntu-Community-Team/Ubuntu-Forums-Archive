---
title: "Java Plugin not working on Epiphany-Webkit?"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Fatfool on 2009-03-06
I've Just installed Epiphany-(Webkit) and although the flash plugin works, the Java one doesn't (version 6.10)

thats odd as Firefox and opera are able to access the java plugin.

any Lines I need to copy into the terminal to display the output?

reason is that I something like Google Chrome (or IE) to access a certain site which doesn't work with Firefox + Java. Or are there other webkit browsers currently avaliable?

---

### Post by Fatfool on 2009-03-06
hmmm... no one?

---

### Post by Fatfool on 2009-03-07
erm, could I get some help here? I understand Epiphany isn't used that much but any indication of what is going wrong here? or should this thread be in the general help area?

---

### Post by Ayuthia on 2009-03-07
Arora is another webkit based browser, but it is still pretty new and uses Qt.  I ran Arora in Gentoo and it works with flash and java.

Unfortunately, I only know that Konqueror and Arora that use webkit.  They are both KDE/Qt based.  I am not for sure of other webkit-based versions.

---

### Post by Fatfool on 2009-03-08
> **Ayuthia said:**
> Arora is another webkit based browser, but it is still pretty new and uses Qt.  I ran Arora in Gentoo and it works with flash and java.

Unfortunately, I only know that Konqueror and Arora that use webkit.  They are both KDE/Qt based.  I am not for sure of other webkit-based versions.
hmmm... but isn't that for KDE? i'm on GNOME......

and did it work right away? (as in Java and flash were already installed before you installed Arora and they worked within Arora when you installed that at a later date)

---

### Post by Ayuthia on 2009-03-08
> **Fatfool said:**
> hmmm... but isn't that for KDE? i'm on GNOME......

and did it work right away? (as in Java and flash were already installed before you installed Arora and they worked within Arora when you installed that at a later date)

Arora is build using Qt, but it will work in Gnome because Ubuntu will just install the Qt packages it needs to make it work.

Arora worked fine for me with Java and flash (they were installed before Arora).  The only thing is that it does need the Qt libraries to be at version 4.5 or else flash will not work.  I am not for sure which version Intrepid is currently using.

---

### Post by Fatfool on 2009-03-08
> **Ayuthia said:**
> Arora is build using Qt, but it will work in Gnome because Ubuntu will just install the Qt packages it needs to make it work.

Arora worked fine for me with Java and flash (they were installed before Arora).  The only thing is that it does need the Qt libraries to be at version 4.5 or else flash will not work.  I am not for sure which version Intrepid is currently using.
I see. ok thanks will try it and see how it goes.

---

### Post by Fatfool on 2009-03-11
> **Ayuthia said:**
> Arora is build using Qt, but it will work in Gnome because Ubuntu will just install the Qt packages it needs to make it work.

Arora worked fine for me with Java and flash (they were installed before Arora).  The only thing is that it does need the Qt libraries to be at version 4.5 or else flash will not work.  I am not for sure which version Intrepid is currently using.
Nope. It doesn't work as well.

it seems that all the webkit browsers simply don't have the java plugin?!?

at least Arora doesn't crash at java sites though. it just doesn't load.

---

### Post by Ayuthia on 2009-03-11
What site are you trying to load?  In Intrepid, I installed epiphany-webkit with non-free-codecs (from [www.medibuntu.org](www.medibuntu.org)) and it seems to work with java (tested it with checking the atomic clock -- [http://www.time.gov/](http://www.time.gov/)).

---

### Post by Fatfool on 2009-03-12
> **Ayuthia said:**
> What site are you trying to load?  In Intrepid, I installed epiphany-webkit with non-free-codecs (from [www.medibuntu.org](www.medibuntu.org)) and it seems to work with java (tested it with checking the atomic clock -- [http://www.time.gov/](http://www.time.gov/)).
say anything on addictinggames.com

I've checked on the java site and it shows that theres no java plugin for any of the webkit browsers.

---

### Post by Ayuthia on 2009-03-12
It looks like Arora needs to have Qt4.5 to make it work with that site.  I was able to get it to work in Gentoo but not in Intrepid.  I am pretty sure that Arora would work fine with that site in Jaunty since Jaunty should be using Qt4.5.  I was not able to test epiphany-webkit in Jaunty because the dependencies are not ready yet.

---

### Post by Fatfool on 2009-03-13
> **Ayuthia said:**
> It looks like Arora needs to have Qt4.5 to make it work with that site.  I was able to get it to work in Gentoo but not in Intrepid.  I am pretty sure that Arora would work fine with that site in Jaunty since Jaunty should be using Qt4.5.  I was not able to test epiphany-webkit in Jaunty because the dependencies are not ready yet.
Oh..... so i guess I gotta wait one more month to get jaunty in and then try again......

---

