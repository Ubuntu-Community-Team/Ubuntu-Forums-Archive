---
title: "I have a problem with Pulseaudio and my SBLive"
date: 2008-12-17
forum: Multimedia Software
---

### Post by sefs on 2008-12-17
Hi all,

I need some assistance.

I am on 8.10 Intrepid with all the latest updates, but can not use my mic at all.

Is this a know issue?

How can I configure 8.10 + PulseAudio + SB Live to recognize my mic.

It worked in 8.04

Thanks.

---

### Post by b0b138 on 2008-12-17
Did you check that its not muted?

---

### Post by sefs on 2008-12-17
Just to be certain where would I check that exactly.

---

### Post by b0b138 on 2008-12-17
double click the speaker icon by the clock

---

### Post by sefs on 2008-12-18
The mic shows up in the playback tab and is not muted. Is that normal? 

Should it be on the playback tab or the recording tab?

---

### Post by markbuntu on 2008-12-18
It should be on in the recording tab if you want it to go anywhere but your speakers.

---

### Post by sefs on 2008-12-19
To be sure my soundcard mic is not broken i popped in a Xubuntu 8.04 Live CD and sure enough I can get the mic to record thru the soundblaster...so it is this new setup that 8.10 has done.  

Now how do I get the mic onto the recording tab is this mess.

Also another thing is when I type alsamixer on the terminal...I only get one column that says Master.  

If I killall pulseaudio and run alsamixer again i get mutiple columns of devices.

I do not even know why ubuntu would put a mic on the playback tab as opposed to to the recording tab.  It just does not make sense to me and is very vexing.

---

