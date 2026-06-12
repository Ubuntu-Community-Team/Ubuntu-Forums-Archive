---
title: "[SOLVED] Problems with k9copy"
date: 2008-03-31
forum: Multimedia &amp; Video
---

### Post by co0lingFir3 on 2008-03-31
Hey folks!
I'm using k9copy to rip my DVDs to XVIDs. I changed the default audio settings in order to obtain ac3 6 channel audio output in avi container. that seems to work nicely by adding the ```
-channels 6
``` line. however i encountered two problems with k9copy:
[LIST=1]
[*]While i'm ripping DVDs and also after i've ripped them in the session i have no audio in playing any video file in VLC. but when i play a file in totem or mplayer it works like a charm. there is no audio in vlc until i reboot my laptop. whats that problem about? ps: is it normal that pulse audio is the default sound driver in mplayer?
[*]i have problems with my ripped xvids: if i open the file in vlc i got no sound and if i "jump forward" the programm is stuck. if i open it in mplayer sound works fine but if i jump to another sequence in the film the sound starts from the beginning whereas the picture works fine. however there's no problem in totem video player. and even on my standalone it seems to work. how can i solve this problem? :confused:
[/LIST]

greets,
co0lingFir3 :)

---

### Post by warp99 on 2008-03-31
These players (mplayer/VLC/Kaffeine/Totem/Xine) have their own little quirks when opening different files. I noticed that Totem, which uses the Xine engine, seems to work the best with most file formats.

The only problem with Totem is that you don't have as much control over preferences then with the Xine GUI front end. You may what to install the Xine GUI so you can have access to more settings to make any adjustments to the video. Hope this helps.

---

### Post by co0lingFir3 on 2008-03-31
Thanks for your reply, warp. The strange thing is however that even in Windows Vista i get the same results with VLC/mPlayer as in Ubuntu. So am i unable to rip accordingly or are the players buggy? Are there some better tools which can rip dvds to xvids with 6 channel audio (please include howto/tutorial) ;)?
and what about my first problem? this seems quite weird to me...

---

### Post by warp99 on 2008-03-31
I use a tool call Acidrip which is a front end GUI for mencoder. You can use mencoder for ripping if you like, but this is very command line intensive. The program is in the multiverse repositories so you have to enable these. To have 6 channel audio you would set the audio dialog box to 'copy' instead of 'mp3' and this will copy the audio directly from the DVD as is.

The only tricky thing about Acidrip is that you have to set the bitcode rate by increasing or decreases the size of the output file and the dialog box for this is on one tab while the bitrate dialog box is on another tab. So you have to switch back and forth between the two tabs in order to set the correct bitrate.

I use Acidrip all the time to rip DVDs to my MythTV media server. It's fast, simple, and best of all it 'just works'.

Edit:

Here are some simple instructions for Acidrip:

[http://www.togaware.com/linux/survivor/AcidRip_Simple.html](http://www.togaware.com/linux/survivor/AcidRip_Simple.html)

Set the Bits/Px at 0.249 instead of 0.2 as the guide suggests for the best quality.

---

### Post by co0lingFir3 on 2008-04-01
Well i figuered out why it was not working in vlc/mplayer. I reencoded the 6 channel ac3 audio. If i just copy it from the dvd it works flawlessly. Dunno if this is a problem with vlc/mplayer or mencoder. the main thing is it's working now :D

---

