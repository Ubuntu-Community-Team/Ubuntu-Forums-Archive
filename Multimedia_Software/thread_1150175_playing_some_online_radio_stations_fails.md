---
title: "playing some online radio stations fails"
date: 2009-05-05
forum: Multimedia Software
---

### Post by flyingsliverfin on 2009-05-05
whenever I try to get online radio from places like KPBS ( [http://www.kpbs.org/kpbs01.asx](http://www.kpbs.org/kpbs01.asx) )
it says it needs to get the 
Microsoft Media Server (MMS) protocol source , but can't find them

either I need to find how to get it or how to make it run from other things (like vlc or reaplayer) movie player doesn't work either.

also, what is the terminal command for reaplayer? 

thx

---

### Post by kostkon on 2009-05-07
I think you need to install the windows codecs package called *w32codecs* (or *w64codecs* for 64bit systems) that is offered by the [*Medibuntu* repository]("http://medibuntu.org/").

Add this repository to your software sources list (instructions [here]("https://help.ubuntu.com/community/Medibuntu")) and then install this package.

Hope that helps.

---

### Post by flyingsliverfin on 2009-05-07
yep thanks

---

### Post by colau on 2009-05-07
w32codecs is the key.

---

