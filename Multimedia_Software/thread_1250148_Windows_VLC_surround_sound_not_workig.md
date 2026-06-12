---
title: "Windows VLC surround sound not workig"
date: 2009-08-26
forum: Multimedia Software
---

### Post by gurudev1000 on 2009-08-26
Hi,
There are loads of tutorials and sections here that might help in getting audio problems work. However, apologies, but my head if fuming with so much info not registering.

My problem is, I have more than a few AVI videos that have 5.1 channel sound. My MoBo is Biostar 740G with built in audio that support surround. Now, I have only two speakers. However, when on Windows, and running VLC, I realised that activating the surround sound in the movie created louder and clearer sound through the two speakers. I want to be able to do that, but this is the error I get in JAUNTY, VLC

Audio output failed:
The audio device "surround51" is already in use.
Audio output failed:
VLC could not open the ALSA device "surround51" (Device or resource busy).

I have gone here [http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html) and done everything instructed there.  In fact, I forgot to check the surround sound before. So, I don't know if changing some settings might have caused this 'problem' or if it was always there. I wouldn't remeber the old settings to go back to them.
Everything else I can think of so far works right, the MP3s, stereo channel video, etc. Just the surround channel doesn't, at least in VLC. And, as I mentioned, that work with Windows. So, I know there is nothing wrong with the file or the hardware and its positioning.

I would appreciate your help. I have seen some questions on this forum go unanswered. If that happens with me, my Ubuntu experience is doomed.

Otherwise, 
Thank you guys for all the other amazing help you provide.

---

### Post by gurudev1000 on 2009-08-26
No one to help???? :(:(

---

### Post by eMJayy on 2009-09-28
Just came across the identical error message while trying to play a DVD with surround sound in VLC 1.0.2 for the first time. I don't know which version of VLC you are using, but you should be using 1.0.2, as I'm finding that it's working very well in Ubuntu. 

In any case, I solved the issue by going to 

System > Preferences > Sound

then I clicked on the 'Sounds' tab and un-ticked the "Play alerts and sound effects" box. Problem solved. 

For whatever reason, the system sounds were using the surround51 driver and preventing VLC from using it. Normally, I use Xine to playback DVDs and the surround sound works flawlessly in that program, whether the system sounds are activated or not.

---

