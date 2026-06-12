---
title: "Need help with streaming e-books."
date: 2008-08-29
forum: Multimedia Software
---

### Post by frewhy on 2008-08-29
Hi there.
Just want to start with saying that I'm completely new to Ubuntu and Linux in general. I installed EEE Ubuntu last night on my girlfriends new Asus PC 900. This forum really helped me out with its great walktroughs, like getting w32codecs etc. Big thanks!

Me and my girlfriend like to listen to streaming e-books from a Swedish library service, and that's were I got my current problem. The streams are working fine (maybe some minor lagg), but I can't fast forward or jump directly to the place in the chapter were we stopped listening the time before. (this works without any problem in Windows MP). Each file(chapter) is ~50min, so if we stop listening like half an hour into the chapter it's a pain to "listen" 30minutes before we get to the point were we last logged out (fell asleep ;) )

Tech info:
The stream is a mms stream. ASF format. 
Web browser is FF3.
OS: EEE Ubuntu

I've tried and got working audio with: Gecko and Mplayer.
I've also tried VLC, it seems to work when i paste URL directly into the player, the file loads, it starts playing, I can fast forward but there is no sound. The VLC mozilla plugin dont work. Just says "No video" and not loading.



Really hope that someone can help me with this since i don't know were to look. Maybe its just some strings in a config file or some setting i have missed. 

Regards

---

### Post by djRobbieF on 2008-08-29
Please provide a url to one of these streams so I can test some theories and post you an actual working reply.

Cheers.

---

### Post by frewhy on 2008-08-29
This should do it:
mms://212.112.169.73/ISBN9170024847/asf/Avsnitt01.asf

The last part "Avsnitt01.asf" translates to "Part01.asf" so you can change the last digits to try other chapters.

---

### Post by djRobbieF on 2008-08-29
This should work for you:

1) Install Multimedia Codecs (See my thread here:  [http://ubuntuforums.org/showthread.php?t=903573](http://ubuntuforums.org/showthread.php?t=903573))

2) You need a compatible sound player; neither Totem or VLC will work for the particular link you provided.  In terminal type:  *sudo apt-get install smplayer*

3) Now you're ready.  Click the link to play your audio book.  Your Ubuntu system will ask you to open it with Totem, or "Choose".  Click Choose.

4) In the dialogue under "Location", type:  */usr/bin/smplayer* then press Open.

5) Check off "Remember my choice for mms links", if you like.

6) Press OK.  It will take several moments to buffer, and then will start playing for you.

---

### Post by frewhy on 2008-08-29
Thanks. Trying it atm. Hope it will work, just want to make it clear that I've already got the stream working with sound, the problem is that I can't navigate as I would like to.

---

### Post by djRobbieF on 2008-08-29
Oh?  What do you mean?  Sorry--I might have misunderstood (my directions will just give you audio on the stream).  Was there some visual navigation in the file on Windows or something?

---

### Post by djRobbieF on 2008-08-29
Oh -- sorry!  I just re-read your post and realized you're having trouble with track seeking  :(

Bummer... it doesn't work in sm either.

I'll look around...

---

### Post by frewhy on 2008-08-29
Yeah. Maybe i filled my first post with too much jibberish :)

As I wrote i got sound with both Gecko and Mplayer. But none of thoose programs let me fast forward or "navigate" in the stream. In Windows Media Player it works so that you can just click somewere on the "timeline", i.e. if i fall asleep 30min into chapter2 I can choose to jump 30min into the chapter the next time I want to listen.

---

### Post by djRobbieF on 2008-08-29
Yeah; because all the Linux apps I tested with don't allow it, I'm guessing it's the decoders...  which sucks.  Sorry!!

---

### Post by frewhy on 2008-08-29
/cry

---

### Post by djRobbieF on 2008-08-29
That's just my guess; but maybe someone else here might no more about it.  Sorry.

---

### Post by djRobbieF on 2008-08-29
After looking into it a bit further, it just looks like the ASF files have to be indexed.  Do you always listen to them streaming?  Or could you download them, index them, and then listen to them?

---

### Post by frewhy on 2008-08-30
I always listen to them streaming since I can't download them when using Windows MP. 

Is there a possibility to download the streams using any linux software? I tried to find info about this on the forums but from what I see i must "record" the files while playing them, meaning that a 50min chapter will take 50mins to "download"?

---

### Post by rvm4000 on 2008-08-30
You can save it with mplayer:
```

mplayer mms://212.112.169.73/ISBN9170024847/asf/Avsnitt01.asf -dumpstream -dumpfile file.asf

```

(This just saves the stream, it's not played)

---

### Post by frewhy on 2008-08-31
Thanks!

---

