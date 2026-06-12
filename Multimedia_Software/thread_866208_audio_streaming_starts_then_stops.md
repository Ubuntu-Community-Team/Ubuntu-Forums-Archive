---
title: "audio streaming starts then stops"
date: 2008-07-21
forum: Multimedia Software
---

### Post by rwigle on 2008-07-21
One of my favourite things is listening to classical music while I work. I am being driven to distraction trying to get audio streaming from 

[http://www.naxosradio.com](http://www.naxosradio.com)

to work properly. I read the sticky thread and I have tried several variations from other threads (vlc, mplayer, gnome-player) in each case I get the same behaviour:

The streaming starts after a small delay, plays for a while and then stops (seems to stop at the end of a "track").

Have I missed a setting?

If someone else would go to that URL and try the free 15 minutes (making sure you hear more than one track) that would at least give me a sense of whether there is any hope.

I even wound back to firefox 2, which seemed to make zero difference. This works fine on Firefox/XP.

Ubuntu 8.04 Firefox (various versions with various players). I have the same behaviour on my old Dell test-bed and my brand new Dell laptop.

---

### Post by ajgreeny on 2008-07-21
Yes, same here.  I tried the 15 mij trial, but the stream stopped at the end of the track which was playing when it opened, with no way I could see to move forward a track, to take advantage of the free 15 minutes.  I can't even see what the stream file type is from that front page, though if you go to a particular music type and then click on a specific CD, the samples there are mp3s, so probably the main streams are also mp3.

have you tried adding the stream url to streamtuner to see if that works better than forefox?

---

### Post by kostkon on 2008-07-21
The same happened to me. The stream stopped after the end of the first track. I'm using totem-xine.

It may has something to do with their javascript code.

---

### Post by rwigle on 2008-07-22
> **ajgreeny said:**
> Yes, same here.  I tried the 15 mij trial, but the stream stopped at the end of the track which was playing when it opened, with no way I could see to move forward a track, to take advantage of the free 15 minutes.  I can't even see what the stream file type is from that front page, though if you go to a particular music type and then click on a specific CD, the samples there are mp3s, so probably the main streams are also mp3.

have you tried adding the stream url to streamtuner to see if that works better than forefox?


Not sure how to do this. All I can see is a very long URL when I open a "channel".

From your reply and the other post, it makes me think this could be on Naxos' end.(?)


One more thing I noticed... Under the "Windows" directions they say to set "Sound scheme = No sound" Is there a corresponding setting in Ubuntu?

---

### Post by rwigle on 2008-07-23
I did notice aposting about Naxos (their non-radio service). It suggests that they use those complex URLS to mask the source channels, rather than open a stream for each individual (excuse the erros I am sure I ammaking).

I sent a tech request to Naxos and they are looking into it. I was expecting them to say that Linux si not supported, so we'll see. I will post the resolution once I have it.

---

### Post by rwigle on 2008-07-28
Still no progress, but I am going to keep at this.

The people at Naxos don't support Linux, but they are trying to help. They suggested using totem as the plug in for Mozilla. I tried that, but the same behaviour.  I.e. The stream starts playing, but stops at the end of the track.

[http://www.naxosradio.com](http://www.naxosradio.com)

ubuntu 8.04 with Firefox 3.0.1

I have asked what format they use, to make sure that totem is associated with that format.

---

### Post by kostkon on 2008-07-29
> **rwigle said:**
> Still no progress, but I am going to keep at this.

The people at Naxos don't support Linux, but they are trying to help. They suggested using totem as the plug in for Mozilla. I tried that, but the same behaviour.  I.e. The stream starts playing, but stops at the end of the track.

[http://www.naxosradio.com](http://www.naxosradio.com)

ubuntu 8.04 with Firefox 3.0.1

I have asked what format they use, to make sure that totem is associated with that format.
Hmmm, strange. It works for me now. They may have changed something.

After the first track it started playing the second track just fine. Although, suddenly the stream was cut off, but I assume my 15 minutes trial was over.

As I said, I am using totem-xine with the totem-mozilla firefox plugin.

---

### Post by rwigle on 2008-08-06
I installed totem-xine and totem-mozilla then rebooted and I have the same issue. I still get ONE track, no matter what. (WITH a subscription!)

Can someone who gets MORE than one track from the free sample tell my what applications are associated with what formats in Firefox's preferences? Thanks in advance.

---

### Post by rwigle on 2008-08-08
I have done a few more tweaks, but still the same. I hear one track and then nothing. This is on two separate machines running Hardy and Gutsy respectively. If anyone is a subscriber and has this running, I'd appreciate knowing what version of browser, and what apps are associated with the audio streaming sources for (e.g. Firefox).

---

### Post by rwigle on 2008-09-12
About every 3 days I try web radio again.

It now seems to work fine.

Hardy Heron, Firefox 3.0.1 (using totem to handle windows media audio)

I recommend this classical music service and hope it works for you.

[http://www.naxosradio.com](http://www.naxosradio.com)

Remember to allow cookies.

---

