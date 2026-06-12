---
title: "Mythtv transcoding"
date: 2012-05-11
forum: Multimedia Software
---

### Post by chuckrp on 2012-05-11
I am new to Mythtv. I can record tv shows over the air and watch them. Volume of the recordings is a little low but I would like to know how to transcode the shows I record into XVID OR DIVX using the User Jobs in the program. If I understand it right, I can remove the commercials in a User job and convert in another. Maybe I can do it in one step.
Can someone explain this to me or help me out with this?

---

### Post by chuckrp on 2012-05-12
I have read some of the posts dealing with transcoding. Are they still current? Should I use some of these 4-5 year old instructions?

---

### Post by singedwings on 2012-05-18
This is an area of myth that is not well documented. What exactly are you trying to transcode? eg a recording from a tv card of some sort in the my recordings.

---

### Post by chuckrp on 2012-05-22
I want to record tv shows with my card, remove the commercials and then transcode into an xvid file. I can then save the show to dvd so my son can watch it in Germany.

---

### Post by singedwings on 2012-05-23
Assuming you are recording *.mpg, if the source is hd it is more complicated. The easiest way to remove the comercials is with the frontend. I have never got on with the auto removal options and find the manual method easy and exact. While watching a recording```
m
Jobs
Edit Recording
```this brings up the editor. Use the left and right arrows to find the start point you want to cut. You must select the nearest 'Keyframe' for the cut if transcoding (which you are). Use the up and down arrows to adjust the amount that time leaps with each press of the left and right arrows. When you find the start of the cut you want press```
Enter
```find the end of the cut you want and press 'Enter' again. You will see the cut turn black in the timeline. When finished```
Escape
Save Cut List And Exit
```Now you are ready to transcode. This is set up in the backend set up. I always use lossless myself so the exact settings you will want for xvid you will need to work out. My personal tip is not to bother changing the names of 'High, Medium and Low Quality' transcoder settings, just change the settings themselves. As when doing the next bit the frontend gui would not be updated with the new name. I don't know if this is still valid, I just never bothered to try and see if it has been fixed.

Whilst watching the recording that you have added the cuts to```
m
Jobs
Begin Transcoding
High Quality
```for example. Thats it, you can exit the recording now and some time later the system will finish the transcoding. Recordings are in /var/lib/mythtv/recordings. Good luck.

---

### Post by Amraks on 2012-09-04
I think its safe to say he knows that way of doing it but.

How do you convert recordings to xvid/divx

---

