---
title: "wma+mp3 with *NO INTERNET* connection?"
date: 2011-07-30
forum: Multimedia Software
---

### Post by paulofelora on 2011-07-30
Hi - have an odd and frustrating situation. Running 11.04 on a personal laptop, deployed in a (very) foreign country with no *private* internet connection, only US gov't machines. Can-absolutely-NOT connect my personal laptop to the web. Trying to get the restricted-format package or WHATEVER it is I need to play wma & mp3 files, but everything I've seen starts off with wget or apt-get blah-blah-blah, which I cannot do. When I try to manually download packages one at a time, transferring them over (laboriously) to my laptop, I go straight to Dependency Hell, do not collect $200, do not pass Go. Does anybody know of a *complete* package that I can download *ONCE* and install, which will give me the plug-ins I need to play audio files? thanks, paul

---

### Post by shantiq on 2011-07-30
ok i have attached lame here which goes into   /usr/bin


or do  once lame is in your home folder   ```
sudo mv lame /usr/bin
```


and then that is your mp3 reading sorted...   i take it as read you can carry files across on usb stick

==========================================================================

as regards wma i would have thought portable player like Deadbeef should sort that out so**[SIZE="2"]==> here goes [/SIZE]** [[COLOR="Blue"]deadbeef portable [/COLOR]should cater to both of your needs here]("http://sourceforge.net/projects/deadbeef/files/portable/0.5.0/deadbeef-0.5.0-static-i686.tar.bz2/download")

you simply need to transfer it to you laptop and double-click on the deadbeef icon in the package/no install

**in fa\ct** with this you can also forget about lame above if you want it as just one stop solution
mind you lame will also allow you to convert from and to mp3 so might be cool to have it too

---

### Post by paulofelora on 2011-07-30
Most excellent - thank you so much ShanTiq! I never would have learned about Deadbeef - I'll try this right now - paul

---

### Post by paulofelora on 2011-07-30
Tell you what, that Deadbeef is the cat's meow! Doesn't get any easier or simpler - thank you ShanTiq!

---

### Post by shantiq on 2011-07-30
nice one :KS  as you'll see here you can also pimp it up [a lot]("http://ubuntuforums.org/showpost.php?p=9516552&postcount=15")

---

### Post by fman23 on 2011-07-30
32-bit or 64-bit?

---

### Post by shantiq on 2011-07-30
either;)

---

### Post by fman23 on 2011-07-30
no, i was going to make a superdeb ( [http://hacktolive.org/wiki/SuperDeb_Creator](http://hacktolive.org/wiki/SuperDeb_Creator) ) with all of the restricted plugins in it and i was asking paulofelora which architecture he is using.  This way he could burn the cd and install the plugins on the system without internet.

---

### Post by shantiq on 2011-07-31
nice idea fman but all plugins seem to be already there in linked file see attached image ( or maybe there are even more available)

---

