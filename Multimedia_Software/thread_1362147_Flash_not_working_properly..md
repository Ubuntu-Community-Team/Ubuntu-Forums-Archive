---
title: "Flash not working properly."
date: 2009-12-22
forum: Multimedia Software
---

### Post by Dmikegarcia on 2009-12-22
Every time I load a video on youtube it is extremely choppy. Only on some though(There is no problem with sound, it plays fine). Going into full screen or popping the video out seems to solve the choppiness problem. This also happens on other websites that have flash videos. I installed flash from the official flash website, but the problem was still there when I had the flash from the software center installed.

---

### Post by Orbegoso on 2009-12-22
Yeah, I'm pretty much having the same problem. Any ideas?

---

### Post by Dmikegarcia on 2009-12-22
:confused: I really need help here.

---

### Post by Orbegoso on 2009-12-23
Bump, I still need help here, any ideas?

---

### Post by Dmikegarcia on 2009-12-23
Bump, please if you have ANY ideas at all I'd greatly appreciate it.

---

### Post by HappyFeet on 2009-12-23
You are more likely to get help if you post more info. What version of ubuntu? 32bit or 64bit? How did you install flash? Information like that is important.

---

### Post by Dmikegarcia on 2009-12-23
It's Ubuntu 9.10. 32 bit, and I've tried flash directly from the flash site and the software center. They both act the same.

---

### Post by HappyFeet on 2009-12-23
Are you running compiz? What video drivers have you installed?

---

### Post by Dmikegarcia on 2009-12-23
Not running Compiz. And according to synaptic package manager, I have the latest video drivers for my graphics card.

---

### Post by Dmikegarcia on 2009-12-23
By the way, I haven't installed any drivers. I'm assuming the latest ones came with the version of Ubuntu(9.10) I installed on the computer.

---

### Post by HappyFeet on 2009-12-23
> **Dmikegarcia said:**
> I have the latest video drivers for my graphics card.

What kind of card is it?

---

### Post by celticbhoy on 2009-12-28
I am having the same problem - did you manage to get it sorted

---

### Post by badrra on 2009-12-30
I solved this problem. Try this one. 

[http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/](http://badrra.wordpress.com/2009/12/03/watch-youtube-using-vlc-mozilla-plugin/)

---

### Post by soulmatic09 on 2010-01-05
This worked for me, I compiled it from several posts:

> 
sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install flashplugin-nonfree


---

### Post by adanon on 2010-01-05
I executed the commands in previous post and my many flash problems have gone away.

Many thanks!

9.10, 64bit.

---

