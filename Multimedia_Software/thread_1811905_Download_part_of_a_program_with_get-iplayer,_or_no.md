---
title: "Download part of a program with get-iplayer, or not ?"
date: 2011-07-25
forum: Multimedia Software
---

### Post by grey1beard on 2011-07-25
Is it possible to use get-iplayer to download only a particular part of a programme, i.e. knowing the timing of the item, rather than the whole ?

I'm using ubuntu 10.04.3 on a Toshiba satellite A30 with on-board sound.

Many thanks

John

---

### Post by grey1beard on 2011-07-26
well, once again I've managed to find a way.
It may not be the simplest solution, but as no one has offered a route, this is what I'm trying.....

First I downloaded the whole program using **get_iplayer**(that's a pain with a 3 hour prog).
Then converted the whole file to an MP3 format using **Sound Converter**.
Updated my **VLC Media Player** to version 1.1.11, as the *Jump to Specific Time* doesn't work in the version 1.0.6 in 10.04 that I'm running. 
Then got **mp3splt** and **mp3wrap** as editing tools via Terminal. 

Any comments ?

---

### Post by ron999 on 2011-07-26
> **grey1beard said:**
> 
Then converted the whole file to an MP3 format using **Sound Converter**.

Any comments ?

**get_iplayer** has a built-in mp3 converter for radio shows.
Use it like this:-
```
get_iplayer --get --type=radio --pid=b012qmf9 --aactomp3
```

---

### Post by grey1beard on 2011-07-26
> **ron999 said:**
> 
.......Use it like this:-
```
get_iplayer --get --type=radio --pid=b012qmf9 --aactomp3
```

I'd be grateful for a bit more detail.
e.g.say I was downloading radio program number 1111.
How do I use your code to convert ? Do I combine the code , like

get_iplayer --get --type=radio 1111 --pid=b012qmf9 --aactomp3

or do I use it after I have got the program ?

MITA

John

---

