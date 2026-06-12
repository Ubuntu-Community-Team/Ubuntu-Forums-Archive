---
title: "using an external midi device to control jack transport"
date: 2010-10-16
forum: Multimedia Software
---

### Post by BcRich on 2010-10-16
Hi there
i'm a bit of a noob to ubuntu but i do have a basic understanding of programming, but nothing too serious. The reason i am mentioning this is because i have a little project that i need some help with. 
Currently i use JACK to control the transport of all the aps i use to make music with ardour, hydrogen and rosegarden mainly. 
I also have an external midi drum machine that i sometimes hook up into the mix via midi in/out, my drum machine (yamaha ry8) to be exact can send and receive midi data. my question is can i use the transport controls on my external drum machine to control JACK's transport controls?
If there is already am app that does something like that, excellent! but if not i'd be very grateful if some one could point me in the right direction to get started on making something like that :)
many thanks
:)

---

### Post by BcRich on 2010-10-16
sorry using bad google search phrases (should have tried title of this post first) found something called QJackMMC, trying it out...

---

### Post by BcRich on 2010-10-16
I can't seem to get this app to work. it tells me i need liblash.so.1 
```
./qjackmmc: error while loading shared libraries: liblash.so.1: cannot open shared object file: No such file or directory

```
yet i have lash installed, does anybody know what it's talking about? thanks :)

---

### Post by apmontgo on 2011-05-19
In the spirit of "better late than never", I'm resurrecting this thread to point out that the latest version of QJackMMC / jackctlmmc no longer requires LASH (it's optional and will be properly detected during the ./configure step), so you shouldn't encounter this problem with the new version.

You can download it here:
[http://jackctlmmc.sourceforge.net](http://jackctlmmc.sourceforge.net)

the install instructions are contained within the download or on the main page.

Enjoy...

-- Alex

---

