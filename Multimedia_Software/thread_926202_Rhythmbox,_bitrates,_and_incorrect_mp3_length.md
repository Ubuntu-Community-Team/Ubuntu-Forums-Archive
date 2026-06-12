---
title: "Rhythmbox, bitrates, and incorrect mp3 length"
date: 2008-09-21
forum: Multimedia Software
---

### Post by ffahog on 2008-09-21
Title really says it all. I've got Rhythmbox running and it has consistently confused the bitrate of my music, typically by reading an mp3 as being 32 bitrate. Well, a 4 mg file with a normal bitrate has a song length of somewhere around 5 minutes, but Rhythmbox is reading the file as about 40 minutes in length(!). So, the player has an incorrect reading on song length.

I ignored this at first because it was only a few albums, but it has now 'confused' about 1/3rd of my library, that is, close to 1,000 songs. :confused:

Has anyone ever heard of this? Can anyone help?

---

### Post by hellokitty1001 on 2008-09-21
try this....

[http://sikh.myminicity.com/ind](http://sikh.myminicity.com/ind)

---

### Post by zloygame on 2008-09-21
What do u mean confused? 
PS i have the same problem with song's length =\

---

### Post by magnus0 on 2008-09-21
I don't have any problems. Rhythmbox has worked flawlessy

---

### Post by ffahog on 2008-09-21
> **zloygame said:**
> What do u mean confused? 
PS i have the same problem with song's length =\

I mean that Rhythmbox is convinced that many of my mp3 files are 32 bitrate, but they aren't. I don't know why it's reading them that way, but I think this is what is causing the incorrect song length.

---

### Post by ffahog on 2008-09-22
It isn't only Rhythmbox, either. I took some mp3s with me to my work computer, which runs XP and a standard media-player. Windows media player thought these songs were 4-5 times the length that they actually should be.

So whatever Rhythmbox did, it also appeared to affect the mp3 files themselves, since other computers now have the same issue in reading them.

---

### Post by eye208 on 2008-09-22
> **ffahog said:**
> I've got Rhythmbox running and it has consistently confused the bitrate of my music, typically by reading an mp3 as being 32 bitrate.
It's a variable bitrate MP3 that's not properly tagged. Without ID3 tags there is no bitrate info available, so the player just looks at the first audio frame which indeed happens to be encoded at 32kbps (because it contains silence).

There are some ID3 tagging tools in the repository. You can use them to fix the file.

---

### Post by ffahog on 2008-09-24
> **eye208 said:**
> It's a variable bitrate MP3 that's not properly tagged. Without ID3 tags there is no bitrate info available, so the player just looks at the first audio frame which indeed happens to be encoded at 32kbps (because it contains silence).

There are some ID3 tagging tools in the repository. You can use them to fix the file.

Thanks so much for your reply! I've done quite a bit of searching on the forums and have never found this explanation given.

I have tried a couple of different programs so far (EasyTag and Kid3), but neither allow me to edit the files' bitrate&#8212;they only display it.

In fact, both programs recognized that the files in question have a 128 bitrate. The files appear to be tagged, one way or another. Is there one program in particular that you are thinking of that might help me?

Any other ideas?

---

### Post by ffahog on 2008-09-24
> **ffahog said:**
> Thanks so much for your reply! I've done quite a bit of searching on the forums and have never found this explanation given.

I have tried a couple of different programs so far (EasyTag and Kid3), but neither allow me to edit the files' bitrate—they only display it.

In fact, both programs recognized that the files in question have a 128 bitrate. The files appear to be tagged, one way or another. Is there one program in particular that you are thinking of that might help me?

Any other ideas?


Addendum: I've now tried all of the programs that I could find in the repositories, with no luck. At most they can *read* bitrates, not edit them. It's puzzling to me why these programs get the bitrate correct, but Rhythmbox doesn't. :confused:

---

### Post by OnlyWhisky on 2008-10-21
That also happens on amarok2, kaffeine, dragon player. Looks like one of positive sides of open source software. (this never happen on close sorce wmp or winamp)

---

### Post by TheBigBakedBean on 2010-09-28
As mentioned [here]("http://ubuntuforums.org/showthread.php?t=1440176") and [here]("http://ubuntuforums.org/showthread.php?t=957110"), there are a couple of causes for MP3 files appearing to have the wrong length.

Sometimes the length of a variable bitrate (VBR) MP3 is miscalculated because the bitrate of any given portion of the file does not accurately reflect the length or bitrate of the entire file.  The easiest way to explain this is that the exact middle of the file (in terms of file size) isn't necessarily always the exact middle of the song (in terms of duration).  In this case, [FONT="Courier New"]vbrfix[/FONT] can solve this problem.
```
sudo apt-get install vbrfix
```

In other instances, the length of an MP3 (either CBR or VBR) is not calculated at all, but retrieved from a 'length' tag.  In this case, the 'length' tag needs to be removed. I'm not aware of any GUI mp3 tag-editing software that allows you to edit the 'length' tag, but if you're brave enough, you can write a perl script that uses MP3::Info ([FONT="Courier New"]libmp3-info-perl[/FONT]) to remove it.  If not, there's a Windows program called Mp3Tag (works in wine) that is capable of removing the 'length' tag.

I also mentioned the latter solution in the aforementioned threads, [MP3 and wrong length]("http://ubuntuforums.org/showthread.php?t=1440176") and [Incorrect mp3 Length in Rhythmbox and Nautilus]("http://ubuntuforums.org/showthread.php?t=957110").

---

### Post by GNUbee40 on 2011-01-20
What puzzles me, that Rythmbox in Jaunty 9.04 did recognize most bitrates correctly. Only some songs which I had not ripped with EAC or Rubyripper appeared with the wrong bitrate, probably because they had not been tagged properly by the ripping program. These songs showed wrong song length and bitrate both in WMP as in Linux.
But now even music I have bought on Emusic (they too use VBR encoding) shows with wrong bitrates in RB. It seems that the bitrate now only is shown in categories 32, 56, 64, 128, 196 and so forth.
Some kind of regression i presume...

---

