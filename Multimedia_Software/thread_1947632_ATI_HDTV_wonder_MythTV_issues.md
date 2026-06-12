---
title: "ATI HDTV wonder /MythTV issues"
date: 2012-03-27
forum: Multimedia Software
---

### Post by ratdude747 on 2012-03-27
I have an ATI HDTV wonder card (using 11.10) and getting it to work has been a headache.

What does work:

-Me-TV detects my digital cable signal and found 16 unencrypted channels. I used a custom starter file for the scanning (made using w_scan).

What kinda works:

- TvTime shows all my signals but I cannot get the audio to work at all. I only tested the composite input, which is all I care about (I have it connected to a VCR). I tried messing with things in alsamixer, which did not help (in the past with line-in cabled cards, this fixed the audio issue).

What doesn't work:

- MythTV has been a failure. It detects the cards and I was able add both the analog and digital tuner but when I go to scan for the QAM channels using the digital tuner, it will not open the card. 


What I would like to know:

1. is there any known fix for the TvTime audio issue?

2. For MythTV,

   A. Is setting up 2 tuners the correct way to enable both the digital Tuner and the composite input, or will just the digital tuner do (it shows both the svideo and the composite inputs on BOTH tuners)

   B. For the digital QAM bit, what would be the correct video source setting be? No grabber? EIT? 
   
   C. If A was "2 tuners", what if anything should I do with the unused inputs (digital composite/svideo, analog Television)? Video source?

   D. For the composite and svideo inputs, what should I set for the source? "(none)"?

   E. If none of the above is related, is there any suggestions on getting the digital tuner to open? It is likely not a firmware issue since I installed nonfree firmware and me-tv has no issues with the tuner.

---

### Post by Zefirum on 2012-03-27
Check out this thread... This is what worked for me when Mythtv was not recognizing the card.  Let me know if this works and maybe I can help you with the settings.  

[http://ubuntuforums.org/showthread.php?p=11549535](http://ubuntuforums.org/showthread.php?p=11549535)

---

### Post by AKADAP on 2012-03-27
Forget the analog part of the ATI HDTV Wonder, it is not supported. (It is a frame grabber with no compression support, developers don't seem to want to deal with it)

The digital part works fine in MythTV. Yes you need the firmware binary blob which I suspect you have as it is working with MeTV, I don't know why you would have trouble with MythTV.

---

### Post by ratdude747 on 2012-03-28
> **Zefirum said:**
> Check out this thread... This is what worked for me when Mythtv was not recognizing the card.  Let me know if this works and maybe I can help you with the settings.  

[http://ubuntuforums.org/showthread.php?p=11549535](http://ubuntuforums.org/showthread.php?p=11549535)

I'll try that.

> **AKADAP said:**
> Forget the analog part of the ATI HDTV Wonder, it is not supported. (It is a frame grabber with no compression support, developers don't seem to want to deal with it)

The digital part works fine in MythTV. Yes you need the firmware binary blob which I suspect you have as it is working with MeTV, I don't know why you would have trouble with MythTV.

I installed the firmware, yes.

As for analog not being supported, what do you mean? The video half worked in TvTime just fine... and if needed, I know a trick to make the audio work if I had to (run a cable from the RCA audio to the line-in on the soundcard). Even MythTV detected the analog part as a V4L card, so What is unsupported?

---

### Post by AKADAP on 2012-03-28
> **ratdude747 said:**
> 
As for analog not being supported, what do you mean? The video half worked in TvTime just fine... and if needed, I know a trick to make the audio work if I had to (run a cable from the RCA audio to the line-in on the soundcard). Even MythTV detected the analog part as a V4L card, so What is unsupported?

It is buggy to the point of being unusable, and bug reports are ignored.

I can count on the fingers of one hand the number of times I have sucessefully gotten a picture out of the card, and I don't think I've ever gotten sound out of it in spite of wasting hours trying to get the V4L drivers to work.

---

### Post by ratdude747 on 2012-03-29
I found a fix (for now) for the audio issues in TvTime
 
Just like with my old analog cards that used a line-out cable that went to the sound card, after some fixes in alsamixer, enabling the input the tuner is connected to enables audio. the only glitch since the audio is bypassing the tuner card, the audio plays whenever audio comes in over the input.

---

### Post by ratdude747 on 2012-03-29
> **Zefirum said:**
> Check out this thread... This is what worked for me when Mythtv was not recognizing the card.  Let me know if this works and maybe I can help you with the settings.  

[http://ubuntuforums.org/showthread.php?p=11549535](http://ubuntuforums.org/showthread.php?p=11549535)

I tried it to no avail... 

I uploaded a screenshot of what happens when I go to scan...

Any other suggestions?

---

### Post by AKADAP on 2012-03-29
> **ratdude747 said:**
> I tried it to no avail... 

I uploaded a screenshot of what happens when I go to scan...

Any other suggestions?

/dev/video0 is the analog tuner on the ATI. As I said, it does not work.

Try /dev/dvb/adapter0/frontend0

card type is "DVB DTV capture card (v3.x)"

---

