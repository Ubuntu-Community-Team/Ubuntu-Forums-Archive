---
title: "Recording streaming audio with Audacity"
date: 2011-02-24
forum: Multimedia Software
---

### Post by squrl on 2011-02-24
I have searched till my eyes are sore. 

Can someone point me to a how to to record streaming audio with Audacity or at worst give me a few tips on where to start. I have tried every combination but get nowhere.

Thanks

---

### Post by ron999 on 2011-02-24
Hi
Is there a particular reason for using Audacity to record the stream?

---

### Post by An Sanct on 2011-02-24
First result from google (keywords: Audacity streaming recording)

> **Can Audacity record RealAudio or other streaming audio?**

**Windows and Linux**

 With most Windows and Linux audio devices, it is possible to record  whatever sound the computer is currently playing, including internet  radio streams.
 In the drop-down menu on Audacity's mixer toolbar, choose &#8220;Wave Out&#8221;  or &#8220;Stereo Mix&#8221; as the input source.  (The exact name may be different,  depending on your computer's sound drivers.)  When you press the **Record** button, Audacity will capture whatever sound is playing on your computer's speakers. **Note:**  on Windows Vista or 7, you must choose the required input source in the  "Recording Device" dropdown in the "Audio I/O" tab of Preferences  ("Devices" tab in Audacity Beta). On Windows, if you don't have a &#8220;Wave  Out&#8221; or &#8220;Stereo Mix&#8221; option, or if it won't record, go to the system  Control Panel and try to enable this option there. For instructions see:  [Using the Control Panel]("http://audacityteam.org/wiki/index.php?title=Mixer_Toolbar_Issues#Using_the_Control_Panel") on the Wiki.
 If this doesn't work on your computer, you can instead use a cable to  connect your computer's &#8220;Line Out&#8221; (speaker) port to its &#8220;Line In&#8221;  port, and use Audacity to record from Line In.
 **Note:** Do not enable "software playthrough" when recording computer playback, because this creates a series of echoes.
PS. If I would stream, VLC would be my first option ...

PS II. Another opinion: [http://www.ofzenandcomputing.com/zanswers/527](http://www.ofzenandcomputing.com/zanswers/527)

---

### Post by squrl on 2011-02-24
No there is no reason to use Audacity. It worked well for converting vinyl and tapes so thought it would be good for streaming.



I tried the mixer toolbar and there is no drop down that I can find. Only input and output levels.

---

### Post by ron999 on 2011-02-24
> **squrl said:**
> No there is no reason to use Audacity
Play the stream through VLC media player and use the red button to record it. (Look in View -> Advanced Controls).

---

### Post by squrl on 2011-02-24
I tried vlc with the record button but havent been able to get it to turn red and poking at it doesn't work. Its kind of like the alsa mixer. Two dozen buttons and none seem to do anything.

Thanks for the help. I guess I'm getting to old for this crap. I'll just continue to wish I knew how. I have a long list of those. LOL

---

### Post by emptythevoid on 2011-03-01
I've been able to use Audacity in the past to record the "mixer" (internal audio) of my PC, but it seems very dependent on how well your computer's hardware works with PulseAudio.  You have to tell Audacity which inputs to use, and you may need to go to your sound preferences and select your "input" there (in this case, hopefully, one of those options will work).  

I used to be able to do this on a Lenovo T61p without any issue, but my newer Dell Precision m6500 with Ubuntu 10.04 won't play right.

---

### Post by nudnikian on 2012-10-22
> **ron999 said:**
> Hi
Is there a particular reason for using Audacity to record the stream?

 I just installed Ubu12.04 and wanted to do a quick grab of a time shifted Hawaii stream (diff zone).  i've been recording analog and streaming radio for 25yrs since using receivers and VHS tapes, then since 90s digital capture w/ computers.  I expected to find quick answers to a setup that should take 30 seconds.  I have been using audacity on Win 98/XP for many (10+) yrs (can't remember when first used).  It has menus.  It is easy to use.  Suddenly with Ubuntu I have a version of audacity that has no menus or has to be full screened (idiotic) to get a menu.  What is this compulsion to hide menus in Unity? YOUR QUESTION &quot;is there a particular reason...to record a stream?&quot;  why not?  What is it's purpose?  I have never used Audacity for anything else. I'm going on an hour now for a simple setup to capture radio streams. The reason I (we) use audacity is to edit audio clips and convert to MP3.  Incredible

---

### Post by wildmanne39 on 2012-10-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

