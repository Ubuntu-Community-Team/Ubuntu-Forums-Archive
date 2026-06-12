---
title: "Strange video problems...."
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by sumigamer on 2007-06-06
Hi folks I am new to Ubuntu.

I have just installed VLC 0.8.6. The problems is that when I play any kind of video file, it works properly, till i dont touch anything. Even if I try to increase the volume, the screen goes black, and I can only hear the audio. Strangely, VLC doesnt do this in Windows. What do I do???

The next problem is that only some files of the same format play!!! I can open only one .mov file, and others dont work. 

Next, i tried xine. It plays all formats perfectly, except that no controls show up, and I cant control the playback. Rest everything plays fine.

Then I tried Mplayer. It doesnt play any format. when i try to...it gives me the foilowing error - "Error opening/initializing the selected video_out _(-vo) device."

Darn!!!


Then comes Totem. The first time i tried to play a wmv file, it gave me an error that the required codec isnt installed( i was running it the first time) OK. It downloaded the stuff for me, and then I tried to play the file again. But only the audio is heard, and instead of one playlist window, two show up.


I just dont get it as to why these players are acting so strange......

Any help would be great.......

---

### Post by empthollow on 2007-06-06
you can  specify which vo or video out device to use in mplayer.  right click on the window and choose preferences, then go to the video tab.  you shouldn't have to restart it to test it just press play again.

---

### Post by simosx on 2007-06-16
There is a bug in the video driver that causes black windows on video playback.
See [http://simos.info/blog/archives/594](http://simos.info/blog/archives/594) for an easy workaround.

---

