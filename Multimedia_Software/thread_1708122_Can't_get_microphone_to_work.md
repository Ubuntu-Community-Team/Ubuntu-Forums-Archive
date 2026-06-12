---
title: "Can't get microphone to work"
date: 2011-03-16
forum: Multimedia Software
---

### Post by Another Monkey on 2011-03-16
I have a Dell Dimension 9200 (DXP061) with a Create eXtreme Music card.  The box has a front mic jack and I can't get that to work.
In the "Sound Preferences", it shows two possible hardware sources: "Internal Audio" and "SB X-fi".
In "Input" I have multiple choices for "Connector" when "Internal Audio analog stereo is selected" ("Microphone 1/Line-In" etc) and for "SB X-Fi Analog Mono" there are none.
I have tried every combination in there, plus every combination I can think of in "alsamixer" and the microphone still does not work (I know the microphone itself is OK).

How do I get this working?  What steps can I work through to figure out what's wrong?

---

### Post by Another Monkey on 2011-03-19
The answer appears to be that Ubuntu does not fully support Creative cards.  Technically the answer might be that Creative hasn't released enough driver information (I can't find the links tot he articles, sorry).  I really don't care, the front jack doesn't work regardless of politics.
If you are lucky enough to have an on-board sound-card as well as a Creative device, you should be able to use the rear jack on the case (not the Creative card) and then enable input for the internal sound device (using "pavucontol" or "Sound Preferences").
To find out what you have, execute this in a terminal:
```
lspci | grep -i audio
```
Example output:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
04:04.0 Multimedia audio controller: Creative Labs SB X-Fi

```
I am marking this as "Solved" as it offers a solution that worked for me and may help others, even though it doesn't use the X-Fi for input.

---

