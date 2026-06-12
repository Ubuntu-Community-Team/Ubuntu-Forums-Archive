---
title: "Firefox can't play embedded mp3"
date: 2010-02-28
forum: Multimedia Software
---

### Post by vgn253 on 2010-02-28
I present here a problem i previously found in:
[http://ubuntuforums.org/showthread.php?t=1280102](http://ubuntuforums.org/showthread.php?t=1280102)
( I can't replay or write on that thread but i can confirm the problem)
this is the problem:

On some web pages ( eg: [http://www.wordreference.com/enit/choose]("http://http://www.wordreference.com/enit/choose"))
.mp3 links can't be succesfully played. (in the above case: the english/US sound of the word)

html code of the link is:

span id=dummyspan></span>
<a title='UK pronunciation' href='' onClick='DHTMLSound("/audio/en/uk/3297-2.mp3"); return false;'>
<img style='border: none' src='/images/speaker5.png' alt='sound' width='16' height='16'></a>

I'm running Firefox 3.55 on Ubuntu x64 9.10 but the problem exists in ubuntu 9.04 too. 

I tried to solve the problem changing 
sound application preferences (from preferences>applications tab)
with no result.

I can play multimedia files from other sources (on the web) and from local files.
Working around I saw that no mplayer-referred module seems to be loaded.
"lsmod | grep player" shows no entry.
Trying to charge "by hand" the module with:
"sudo insmod mplayerplug-in.so"
 result in:
"insmod: error inserting 'mplayerplug-in.so': -1 Invalid module format"


thanks in advance

---

