---
title: "AverMedia M150-D"
date: 2008-12-27
forum: Mythbuntu
---

### Post by D8TA on 2008-12-27
I have been trying to get this card to work for just shy of two weeks. I was running Windows XP with MediaPortal and everything worked fine. I have been using Linux for about 8 months and want to ditch Windows, I've never installed Vista only seen screenshots of this OS. Anyways, I have installed Mythbuntu trying to get my cable, Insight, to broadcast to this tuner card so I can  start using Mythbuntu as a PVR. I cannot seem to get the card to work. I've tried this, [http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D](http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D) but still nothing. I read on this forum where someone else was experiencing problems but no one supplied any assistance, [http://ubuntuforums.org/showthread.php?t=960314](http://ubuntuforums.org/showthread.php?t=960314)

Has anyone got this card to work? If so, please help me out.

Thanks in advance!

---

### Post by D8TA on 2009-01-04
Well, I finally got video from my cable using this card. Not sure what I did but it does show some decent video. However, the audio sounds like satan has possessed everyone that speaks. It is really low and sloooow. My Mythbuntu installation was done on a Dell Dimension 2400 with a 2.4Ghz processor, 1GB of RAM, and an 80GB hard drive. I have my recordings going to another hard drive which is 120GB in size. Everything else is using the standard on-board video and audio with the cable coming in on the AverMedia M-150D card.

Any suggestions? I came close to installing Vista Ultimate to see what happens but really want to avoid installing that. I have been Microsoft free for over 9 months and am shooting for a year.

---

### Post by fenian on 2009-01-05
Did you install xawtv?
If not install it with the command...

> sudo apt-get install xawtv

Then run the commands...

> v4lctl -c /dev/video0 setchannel $1
v4lctl -c /dev/video0 volume mute off

You can also try video1 in place of video0 in the above commands.

---

### Post by Caysho on 2009-01-05
According to the [mythtv wiki]("http://www.mythtv.org/wiki/index.php/AVerMedia_M150-D#Issues_and_Problems"), the card is quirky.
I would use a different card.  I have two AverTV 777 cards, but I think they've been discontinued.

---

### Post by D8TA on 2009-01-28
> **fenian said:**
> Did you install xawtv?
If not install it with the command...



Then run the commands...



You can also try video1 in place of video0 in the above commands.

Finally got a chance to test this out. Still a no-go. The video looks fine and I can change channels and everything works great. My only issue is still the sound which is sloooow and sounds demonic. This is on a Dell 2400 and I am using the onboard sound. I can play music files just fine and watch DVD movies just fine. Do you think getting a different sound card would do any good? I thought about purchasing a different capture card but hate to spend the cash. If it is recommended I do so can anyone recommend a card for under $50. I am using Insight cable and am new to this MythTV thing so not sure if a digital or analog card will make a difference. Just really want to get this system up and running.

Thanks in advance for the suggestions.

---

