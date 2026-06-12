---
title: "using live CD  Mythbuntu 9.04 on dell 1530"
date: 2009-04-26
forum: Mythbuntu
---

### Post by moseleyb on 2009-04-26
Hi folks,

Trying to get an understanding of mythbuntu and I have made the iso and booted up to the start up screen and I get to the mythbuntu live session configuration tabed windows that asks for what  password I want and so forth but then i click start session and a non-themed screen that is blue asks me for local host info and what port to use and I am confused. I don't have a backend I just simply what to try mythbuntu on my dell 1530 laptop to understand it better and eventually use it as a pvr. Can anyone help with suggestions of how to answer these questions and get me into mythtv?

Aloha,

Psych

---

### Post by phroman on 2009-04-26
I haven't tried the live cd but is it possible that it is frontend only?

---

### Post by moseleyb on 2009-04-26
Hmm... pretty new at this so I don't know. I don't see much value to the live CD as a product demo under these curcumstances but maybe I don't get what I am supposed to do with it.

---

### Post by nickrout on 2009-04-26
The livecd is a frontend only. It needs a backend to connect to or it simply will not work.

wiki.mythtv.org has a manual that has lots of screenshots if you want to get the flavour of mythtv. 

Also if you have ubuntu on your laptop already you can try mythtv by installing it on there with:

```
sudo aptitude install mythbuntu-desktop
```

If you don't like what you see:

```
sudo aptitude remove mythbuntu-desktop
```

Make sure you use aptitude not apt-get as aptitude will remember and remove all the dependencies it installed.

---

### Post by moseleyb on 2009-04-28
thanks!

---

