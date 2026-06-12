---
title: "Repair and integrity check for .ogg Files"
date: 2011-01-24
forum: Multimedia Software
---

### Post by jabz on 2011-01-24
Hi, 

is there a way to "repair" or check the integrity of ogg files? They all work on my desktop but some seem broken on my mobile (Nexus One). I have the feeling my converter may have corrupted some files or the conversion was corrupted by the original file. 

Any ideas? 
Thanks.

---

### Post by cascade9 on 2011-01-24
I dont know of any way to check integrity on .ogg files. That doesnt mean that there isnt a way, I havent paid much attention to ogg since I found .flac. 

Normally if you doget a corrupted file, its full of hiss, blips and cracking. If the files just refuse to play, its more likely that you've encoded the files at a bitrate, sample rate or some with other feature (eg album art)  that is not supported by your nexus one.

---

### Post by jabz on 2011-01-26
Thank you for your reply. 

I was looking into this. The bitrate is fine. As I've cleaned up all Meta-Tags (like album art, etc.) it seems to be the sampling rate is the problem. Do you have any suggestions how I can check and / or change the sampling rate?

Thank you for your help.

---

### Post by cascade9 on 2011-01-26
Seems like the .ogg that came with (some?) nexus ones used 48KHz sample rate. If it doesnt support a 44.1KHz sample rate, then somebody should be told off (the vast majroity of .ogg files I've ever seen are 44.1KHz, like CDs). 

Anyway, that came from here- 

[http://www.google.com/support/forum/p/android/thread?tid=6ee9dd75fa4edaa6&hl=en](http://www.google.com/support/forum/p/android/thread?tid=6ee9dd75fa4edaa6&hl=en)

As for how to check the sample ate on your .ogg files, offhand the only things I know that will do it are deadbeef and VLC. Deadbeef displays the sample rate at teh bottom of the player window by defualt IIRC. VLC, Tools-> Codec Information-> Codec Details. 

I'm sure that there are a lot of other linux media players that will show you the sample rate, I just dont know of them.

To actually change the sample rate, get soundconverter, then convert to .wav, then either try rencoding them to .ogg should do the trick. If that fails, sox should be able to change the sample rate. I'm sure theres got to be a better way to do that, but I honestly dont know. 

I rarely ever transcode audio, and if I do its from .flac to .mp3 (for my portable media player).

---

