---
title: "brasero prob.... weird one too!!!"
date: 2014-04-11
forum: Multimedia Software
---

### Post by nealien on 2014-04-11
okay so i made a cd using brasero. the first disc played only the first 5 1/2 songs (didn't matter what player i used.... my car, my xbox, and rthymbox).  i burned a second and it locked up during the burning process and ruined another disc. not quite sure what's going wrong with it. my first thought was codecs but that wouldn't make sense for 5.5 songs to play and then the other 16 to not play. the other 16 won't play on ANYTHING including ubuntu rythmbox, (not from the cd anyway). someone please help me. linux is so great but the amount of bugs im having to deal with is stupid!!!!!

---

### Post by nealien on 2014-04-11
also im using verbatim 74 min cd-r discs and a phillips 48x dvdrw/cd-rw drive. i burned the second disc at 24x just to see if the speed was a prob.  it wasnt....  sadly

---

### Post by RedRat on 2014-04-11
> **nealien said:**
> okay so i made a cd using brasero. the first disc played only the first 5 1/2 songs (didn't matter what player i used.... my car, my xbox, and rthymbox).  i burned a second and it locked up during the burning process and ruined another disc. not quite sure what's going wrong with it. my first thought was codecs but that wouldn't make sense for 5.5 songs to play and then the other 16 to not play. the other 16 won't play on ANYTHING including ubuntu rythmbox, (not from the cd anyway). someone please help me. linux is so great but the amount of bugs im having to deal with is stupid!!!!!

I gave up on brasero a long, long time ago. It still seems to be buggy. I now use K3B, it works great and have yet to throw disks away.

---

### Post by nealien on 2014-04-11
i installed that to try it out about an hour ago.  it won't even attempt to burn a disc. it just gives errors regarding codecs.... which again, doesn't make sense. i could see it not working on all songs if they weren't made with the same codec but to only play half a song?!?!? what the crap dude!? im not opposed to installing some codec packs but im not 100% sure how to do that in a linux environment. im a+ certified and mcse but linux is still very new to me.  im not a pc noob so this makes it even more frustrating.

---

### Post by nealien on 2014-04-12
bump

---

### Post by speartip on 2014-04-12
3 things to try.

1st. have you installed the restricted extras?
```
sudo apt-get install ubuntu-restricted-extras
```

2nd. go to edit/plugins in Brasero & make sure all the boxes are ticked (all the plugins are installed) If not install them using synaptic/software centre.

3rd Always burn discs at the lowest possible speed.

I have followed the above tips using Brasero on 12.04 & have never had one bad burn since.

ps I always use Taiyo Yuden discs or other similar quality.

---

### Post by RedRat on 2014-04-12
> **nealien said:**
> i installed that to try it out about an hour ago.  it won't even attempt to burn a disc. it just gives errors regarding codecs.... which again, doesn't make sense. i could see it not working on all songs if they weren't made with the same codec but to only play half a song?!?!? what the crap dude!? im not opposed to installing some codec packs but im not 100% sure how to do that in a linux environment. im a+ certified and mcse but linux is still very new to me.  im not a pc noob so this makes it even more frustrating.

Something ain't quite right here. K3B is merely a disk burning tool. You can actually drag and drop files to your unburned CD with Nautilus or Thunar, K3B is just a fancy GUI with some other features and it really shouldn't care what codecs were used for the creation of the mp3's. Are you trying to make an audio CD from mp3s? This is what it sounds like it is doing. Actually, you should have all the necessary codecs installed when you installed Ubuntu. There are some programs available that can create audio CD tracks from mp3s, can't remember their names right now but they would be in Synaptic. You are not clear on exactly what you are trying to do. 

There is another possibility and that is that your CD writer might just be crapping out. I had one that did about two years ago. Perhaps you got a hold of a bunch of bad disks??? (I know, not likely, but you know what happens now and again).

---

