---
title: "HELP with streaming video files...any suggestions?"
date: 2010-11-03
forum: Multimedia Software
---

### Post by steven.smith on 2010-11-03
Hey there all. I have a VPS with Ubuntu 9.04. I wanted to stream files off the server with formats such as .avi, .mkv, and .wmv. I know there are html scripts that you can embed in a webpage, but they are neither fast nor convenient; along with the fact that they require each and every file to be added makes it plain worthless.

So far, I've tried using WMP and VLC to connect to the files using the http method, but even then buffering was horrible and the files ended up choppy and barely watchable. Same goes for the ftp method. 


So the question is, is there some kind of php script that allows me to stream movies (with the .avi,.mkv,etc... formats)?

The closest I've came is xmoovStream. However, this only works with flash video files. And the whole point of streaming is ruined if I have to convert each and every file to .flv.

A friend of mine suggested using DivX Web Player, but I'm a little hesitant to try it out seeing as Windows Media Player and VLC failed. So anybody have any helpful suggestions?

:confused:

---

### Post by steven.smith on 2011-03-11
Update****************

   Well, it's been a little while now. I was looking through my posts on my account and noticed this thread was still here. I figured out an alternate solution that does what I wanted and decided that I would post here what I did.


   The following assumes you already have a web server running (either through apache or something else) and that you have php installed.


   My solution is quite simple. I used the PHP Simple Directory script (download at [http://sourceforge.net/projects/simpledirectory/?showfeed=news](http://sourceforge.net/projects/simpledirectory/?showfeed=news)). It's really easy to install (just put the ONE file in the directory that you want and set the username and password and you're done).


   Download/install VLC Media Player. I've tried other media players, but VLC seems to be the best in this situation. Now, go back to the media file you want to play on your server (using Simple Directory) and copy/paste the URL link of the file into VLC (either by pressing Ctrl+V in VLC or entering it manually in 'open file').



   Know that VLC sucks at playing .wmv files, so avoid it if you can. VLC plays mp4 files the best. I've tried playing .avi, .mp4, and .mkv files and they work perfectly (barely any skipping and seek/track works well).



Note: For best performance, change the buffer size so there isn't any skipping.



  I know this solution seems pretty obvious, but I'm not sure if most people know how easy it is to stream files without having to setup a streaming server. Either way, this solution turned out perfectly for me. I didn't have to wait to download video files and could watch any file *when* I wanted without having to download them. 



  Hope this helps somebody.

---

