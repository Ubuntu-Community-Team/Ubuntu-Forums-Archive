---
title: "Cinelerra CV Surround Sound [extra channel issue]"
date: 2010-03-23
forum: Multimedia Software
---

### Post by beccatoria on 2010-03-23
Hi guys. I'm using Karmic, 64 bit with Cinelerra CV. Usually I edit projects in stereo sound simply because I do not have a surround sound setup, but in this instance, I have access to 5.1 surround sound audio and would like to keep it intact in the finished product. 
 
I've done some research and from the Cinelerra manual, I set up the 6 tracks as instructed for surround sound - no problems there. 
 
The problem is that when I set up the six different speakers in the project settings, any speaker set dead ahead or dead behind, still defaults to the left or right speaker of my computer/headphones, etc. I presume this is just a function of Cinelerra not being able to split the audio output between two speakers and so defaulting to one speaker or the other, and that it would play fine were I actually playing the finished product back in a full surround sound setup. I cannot check this as I do not *have* a surround sound setup. 
 
However, obviously, I would like to be able to also play the project back in stereo sound systems without having to put up with only getting audio out of one headphone/speaker which is highly irritating. This must be possible as, well, usually 5.1 surround sound video plays the centre audio channel back across both speakers in stereo systems. 
 
Is there a way to get Cinelerra to split the output between both speakers? 
 
If not, I can fix the issue by simply adding another speaker one degree further on from the centre channel so that it comes from the other speaker. That fixes the issue nicely for stereo playback. But I do not know what that would do to a surround sound setup, and again, cannot test this as I do not have one. 
 
Would a surround sound system simply refuse to play back a channel mapped to a seventh speaker? Would it instead direct the channel to one of the other speakers, and if so, which one? If it was the central one, then there would be no problem, but if it was one of the others, that would be problematic as the dialogue would then be coming from the central speaker and one of the side speakers which would create a lopsided effect. 
 
Any help would be greatly appreciated. I am a total newb when it comes to 5.1 so the simpler then better...

---

### Post by wildhostile on 2010-03-23
Hi beccatoria,

I'm not much specialist myself but to pan sound with Cinelerra you will have to use "keyframes" whith which you will be able to choose which of the speakers will speak and the moment it will.
You already set 6 channels. (Note that you can place them the way you want in Settings -> Format first by moving them). You have now to choose them by clicking on the little window in which there are six little yellow square that represent the speakers. Click and move the red cross to speaker(s) you want to activate.
I'm never tried it (and I don't have surround sound here neither) but I guess you can either:
- choose to share the sound between two speakers (Cinelerra give the possibility ... you will see) or:
- make two versions for your final project: a "normal" one and a "surround" one.

[ac3 test file]("http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3")

---

### Post by beccatoria on 2010-03-23
Awesome, thank you for pointing out the extra panning function in the patchbay - that has solved my problems, I simply set the "centre" dialogue track to the very centre of all the speakers and the problem was solved.

---

