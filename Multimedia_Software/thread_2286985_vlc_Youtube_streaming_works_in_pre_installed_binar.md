---
title: "vlc Youtube streaming works in pre installed binary but stops working after intsall"
date: 2015-07-16
forum: Multimedia Software
---

### Post by monkeybrain20122 on 2015-07-16
I have a strange problem with vlc 2.2.1. I compiled it myself. I was testing it out for streaming videos from youtube but it didn't work. I remembered that it was compiled without librtmp-dev. So I installed that, downloaded a fresh tarball of the source and recompiled. It built a binary in the build folder, it worked. So I installed it with 

```
sudo checkinstall
```

But streaming Youtube no longer worked for the installed version. So I deleted the .config, still didn't work. So I removed vlc from system and ran checkinstall again. Still the installed version doesn't work but the pre-installed binary in my /home is working perfectly. Could it be some kind of permission thing?


Pretty strange.

---

### Post by monkeybrain20122 on 2015-07-16
Ok, I fixed it but I am still puzzled. I deleted the folder /usr/lib/vlc/lua/playlist and then replaced it with /share/lua/playlist from the build folder and it works now. But I think these files are copied to the file system during installation???!!

---

### Post by monkeybrain20122 on 2015-07-20
Any insight to the puzzle??

---

### Post by mc4man on 2015-07-20
Doesn't work here at all in my current vlc's, either run of the mill yt vids or yt  vevo vids . 
What is the difference between the 2? ( are the installed ones whatever.lauc or whatever.lua ( c means compiled

---

### Post by monkeybrain20122 on 2015-07-20
It works on all Youtube videos tested including Vevo. Not sure why but they are different. Another thing I found is that subtitle fetching doesn't work in the installed version but works in the compiled binary before installing. /usr/lib/vlc/lua/extensions has only one file : VLSub.luac but /share/lua/extension has in addition VLSub.lua, which is the one needed to work (you can delete the .luac which won't make a difference, it would work with the .lua)

Edited: yes you are right. The build folder contains lua and luac but the installed one has only luac.

---

### Post by mc4man on 2015-07-20
Which vlc source are you building?
(- the *.lua are just that in the source, when you build vlc & install they are compiled into  .luac (that goes for all the installed .lua files/scripts. Notice you can read a .lua, not a .luac

---

### Post by monkeybrain20122 on 2015-07-20
Vlc-2.2.1. tarball fetched from here [http://download.videolan.org/pub/videolan/vlc/](http://download.videolan.org/pub/videolan/vlc/)

---

### Post by mc4man on 2015-07-20
So maybe vlc works with .lua scripts  but is failing on  when it,(vlc),  compiles them, (some or all?) into .luac binaries?

---

### Post by monkeybrain20122 on 2015-07-20
Seems so.

---

### Post by mc4man on 2015-07-20
Which lua are you using? The lua compiler is in the lua5.X package. Likely now lua5.2, maybe try (if inclined to pursue) only making lua5.1 available to vlc when it builds..

---

### Post by monkeybrain20122 on 2015-07-20
I have lua5.1,  liblua5.1-0,  liblua.5.2-0, liblua5.1-0-dev and liblua5.2-dev installed.

---

### Post by mc4man on 2015-07-21
Then you&#8217;d be using the lua5.1 compiler, I've 5.2 here. Guess it's some vlc issue...
ot - 
If you had use for vlc 2.2.x  supporting embedded WebVVT subs then attached patch adds support ( the 'official' webm sub
A sample, can only be dl'ed > r. click > save as..
[http://files.jxself.org/elephants_dream.webm](http://files.jxself.org/elephants_dream.webm)

---

### Post by monkeybrain20122 on 2015-07-21
> **mc4man said:**
> Then you’d be using the lua5.1 compiler, I've 5.2 here. Guess it's some vlc issue...
ot - 
If you had use for vlc 2.2.x  supporting embedded WebVVT subs then attached patch adds support ( the 'official' webm sub
A sample, can only be dl'ed > r. click > save as..
[http://files.jxself.org/elephants_dream.webm](http://files.jxself.org/elephants_dream.webm)

Thanks.

---

### Post by mc4man on 2015-07-21
Without trying on a more specific basis just went ahead here & deleted everything, (folders & files) in /usr/lib/vlc/lua & replaced with the uncompiled .lua scripts from the source. Now yt urls work..
(- in regards to yt likely could be narrowed down to a couple of .luac files, though if it can't do some right then no basis to think it does any correct.

---

### Post by mc4man on 2015-07-22
To update - 
started over purging vlc* & making sure there was no /usr/lib/vlc folder nor anything in ~/.local/share/vlc/lua
Then did a re-install & yt urls work ok. So must have been sometime leftover from older install or some fool around in ~/

(here using lua5.2 for vlc builds..

---

### Post by monkeybrain20122 on 2015-07-28
> **mc4man said:**
> To update - 
started over purging vlc* & making sure there was no /usr/lib/vlc folder nor anything in ~/.local/share/vlc/lua
Then did a re-install & yt urls work ok. So must have been sometime leftover from older install or some fool around in ~/

(here using lua5.2 for vlc builds..

Doesn't work here. Recompiled vlc after deleting all old vlc* folder and still the same problem. Where did you get lua5.2? I am on 15.04

---

### Post by mc4man on 2015-07-28
> **monkeybrain20122 said:**
> Doesn't work here. Recompiled vlc after deleting all old vlc* folder and still the same problem. Where did you get lua5.2? I am on 15.04
In synaptic - screen

---

### Post by monkeybrain20122 on 2015-08-06
lua5.2 works.

---

### Post by mc4man on 2015-08-06
> **monkeybrain20122 said:**
> lua5.2 works.

There is very little need for lua51; liblua5.1 now, build with the 5.2 dev whenever possible.

---

### Post by monkeybrain20122 on 2015-08-06
> **mc4man said:**
> There is very little need for lua51; liblua5.1 now, build with the 5.2 dev whenever possible.

liblua5.1-dev and lua5.1 can be removed, but removing liblua5.1 will remove apache.

---

### Post by mc4man on 2015-08-06
> **monkeybrain20122 said:**
> liblua5.1-dev and lua5.1 can be removed, but removing liblua5.1 will remove apache.

That fits very little to me...
It appears apache2 could use liblua-5.2 but upstream isn't interested in switching as it could break the lua mod for users of only 5.1
(- there is this mod_pLua thing that uses either but probably provides something else, no clue..

---

