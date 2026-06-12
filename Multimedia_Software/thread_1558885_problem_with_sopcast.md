---
title: "problem with sopcast"
date: 2010-08-22
forum: Multimedia Software
---

### Post by darklord06 on 2010-08-22
hello,

I have a problem with the sopcast application, I managed to install it, first by installing libstdc++5 (apt://libstdc++5) then adding ppa:jason-scheunemann/ppa to install sopcast player (apt://sopcast-player) plus sp-auth (apt://sp-auth).
Once installed the application launches succesfully but i have only about 10% of the channels in the channel list that are actually working, among the chinese channels (the one i'm most interested in) only CCTV3 is working, for every other chinese channel i always get a "connecting" message. i tried to update the channel list but it unfortunately did not change anything.

could anybody help me out ? I also tried installing the windows version of sopcast trough wine and it is even worst (there isn't any working channel, i always get a "can't connect to sopcast service message) I am a complete linux newbie and i don't know what to do.

thank you

I'm using linux mint 9

---

### Post by gordintoronto on 2010-08-23
Do you start at cctv.com, select your channel and then P2P?

---

### Post by darklord06 on 2010-08-23
hello,

thank you for your reply but I affraid i don't understand, In sopcast i just selected various channels in the channel list (mainly chinese channels) and it just kept on trying to connect

---

### Post by gordintoronto on 2010-08-23
I didn't realize that Sopcast included a viewer, I thought it was an add-on to your web browser. I have watched CCTV9 (English channel from China) in Windows 7, it requires an add-on for Explorer. My wife is Chinese, and she wants to watch all the channels.

---

### Post by darklord06 on 2010-08-30
I found a way to fix my problem, I replaced the channel server.
I used [http://www.sopcast.cn/gchlxml](http://www.sopcast.cn/gchlxml) instead of [http://www.sopcast.com/gchlxml](http://www.sopcast.com/gchlxml)  and now everything works !

---

### Post by gordintoronto on 2010-09-01
Terrific!  Perhaps you could use the thread tools to mark the thread as solved!

---

