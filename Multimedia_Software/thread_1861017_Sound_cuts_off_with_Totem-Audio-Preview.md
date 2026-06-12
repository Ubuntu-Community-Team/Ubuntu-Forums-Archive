---
title: "Sound cuts off with Totem-Audio-Preview"
date: 2011-10-15
forum: Multimedia Software
---

### Post by wpshooter on 2011-10-15
I am using Lucid.

Why is it that when I try to play a LARGE MP3 sound file with the Totem-Audio-Preview by just moving the mouse over the Large MP3 file (in this case - Simple Minds (don't forget about me - extended mix) that before the complete song is played the sound cuts off ?

I can open that same MP3 in the Totem program (i.e. not Totem-Audio-Preview) and the song is played completely thru without the sound cutting off ?

Am I correct that this may have something to do with the amount of memory installed on the particular computer ?  The reason I am thinking this is because I ALSO have an older computer that has only 1/2 as much installed memory as the computer that is being used in the above instance and it also does this sound cutoff thing but it also does it on MP3 files that are much smaller than the one mentioned above.

OR IS THIS JUST A BUG IN THE TOTEM-AUDIO-PREVIEW PROGRAM ???

First computer has 1gb memory, second computer has 512 mb memory.

Thanks.

---

### Post by wpshooter on 2011-10-21
> **wpshooter said:**
> I am using Lucid.

Why is it that when I try to play a LARGE MP3 sound file with the Totem-Audio-Preview by just moving the mouse over the Large MP3 file (in this case - Simple Minds (don't forget about me - extended mix) that before the complete song is played the sound cuts off ?

I can open that same MP3 in the Totem program (i.e. not Totem-Audio-Preview) and the song is played completely thru without the sound cutting off ?

Am I correct that this may have something to do with the amount of memory installed on the particular computer ?  The reason I am thinking this is because I ALSO have an older computer that has only 1/2 as much installed memory as the computer that is being used in the above instance and it also does this sound cutoff thing but it also does it on MP3 files that are much smaller than the one mentioned above.

OR IS THIS JUST A BUG IN THE TOTEM-AUDIO-PREVIEW PROGRAM ???

First computer has 1gb memory, second computer has 512 mb memory.

Thanks.

Anyone know the answer to this ???

Thanks.

---

### Post by Swagman on 2011-10-23
Dunno the answer to that one but since upgrading to 11:10 the preview option doesn't work anymore..

ie: When I hover over the music file the preview no longer plays.

At least you get some of it !!

---

### Post by mc4man on 2011-10-23
> **Swagman said:**
> Dunno the answer to that one but since upgrading to 11:10 the preview option doesn't work anymore..

ie: When I hover over the music file the preview no longer plays.

At least you get some of it !!

New thing, you may like better, may not - 
```
sudo apt-get install gnome-sushi
```

Then highlight an audio or video file > press spacebar
Note that sushi will not warn if codec support in gstreamer is missing - in that case will do nothing
> 
Why is it that when I try to play a LARGE MP3 sound file with the Totem-Audio-Preview by just moving the mouse over the Large MP3 file (in this case - Simple Minds (don't forget about me - extended mix) that before the complete song is played the sound cuts off ?

Not sure - doesn't seem like even if the mp3 was cached completely it would take up that much mem. Don't remember this being an issue
What does a "LARGE" mp3 imply

---

### Post by wpshooter on 2011-10-24
> **mc4man said:**
> New thing, you may like better, may not - 
```
sudo apt-get install gnome-sushi
```

Then highlight an audio or video file > press spacebar
Note that sushi will not warn if codec support in gstreamer is missing - in that case will do nothing

Not sure - doesn't seem like even if the mp3 was cached completely it would take up that much mem. Don't remember this being an issue
What does a "LARGE" mp3 imply

LARGE, in the case of "Simple Minds - Don't Forget About Me - Extended Version" is 15mb.  Most other MP3 that ARE played successfully to the end are good bit less than 1/2 that size.

Thanks.

---

### Post by wpshooter on 2011-10-24
> **Swagman said:**
> Dunno the answer to that one but since upgrading to 11:10 the preview option doesn't work anymore..

ie: When I hover over the music file the preview no longer plays.

At least you get some of it !!

Swagman:

You are not getting any sound under 11:10 because preview parameter is set to OFF/NEVER by DEFAULT under 11:10.

Go to "Preview sound files" parameter under places/home/edit/preferences and change from NEVER to local only.

Thanks.

---

### Post by mc4man on 2011-10-24
> **wpshooter said:**
> LARGE, in the case of "Simple Minds - Don't Forget About Me - Extended Version" is 15mb.  Most other MP3 that ARE played successfully to the end are good bit less than 1/2 that size.

Thanks.
I currently don't have an install earlier than 11.04 so can't check. I guess I'd 1st. make sure this is size based vs. time based
(in any case, if this is a bug vs. intended or a local issue I'd not expect much interest in fixing  with gnome/nautilus having moved on to 3.X

---

### Post by wpshooter on 2011-10-24
> **mc4man said:**
> I currently don't have an install earlier than 11.04 so can't check. I guess I'd 1st. make sure this is size based vs. time based
(in any case, if this is a bug vs. intended or a local issue I'd not expect much interest in fixing  with gnome/nautilus having moved on to 3.X

I just installed 11.04 and it looks to be gnome 2.something.

Where are you getting this gnome/nautilus 3.X ?

Thanks.

---

### Post by mc4man on 2011-10-24
> **wpshooter said:**
> I just installed 11.04 and it looks to be gnome 2.something.

Where are you getting this gnome/nautilus 3.X ?

Thanks.

That's what being used now in 11.10 & the upcoming 12.04
Ex. of sushi previewer in screens, 1 an audio, the other a vid. There is a usable progress bar overlay also available when cursor is in preview window

---

### Post by wpshooter on 2011-10-24
> **mc4man said:**
> That's what being used now in 11.10 & the upcoming 12.04
Ex. of sushi previewer in screens, 1 an audio, the other a vid. There is a usable progress bar overlay also available when cursor is in preview window

You are talking about that thing that they appear to be referring to as "Unity".  Which I tried and seems like a lot of work done for no good reason !!!  Nothing wrong with the old interface that was on older versions, they just need to leave the interface alone and concentrate on getting the bugs out of the O/S.

Thanks.

---

### Post by Swagman on 2011-10-24
> **wpshooter said:**
> Swagman:

You are not getting any sound under 11:10 because preview parameter is set to OFF/NEVER by DEFAULT under 11:10.

Go to "Preview sound files" parameter under places/home/edit/preferences and change from NEVER to local only.

Thanks.

Thanks for tip, unfortunately there appears to be no sound preview option in Oneiric (11:10)

[[IMG]http://img88.imageshack.us/img88/1096/previewbc.th.jpg[/IMG]](http://img88.imageshack.us/i/previewbc.jpg/)

---

### Post by wpshooter on 2011-10-30
> **Swagman said:**
> Thanks for tip, unfortunately there appears to be no sound preview option in Oneiric (11:10)

[[IMG]http://img88.imageshack.us/img88/1096/previewbc.th.jpg[/IMG]](http://img88.imageshack.us/i/previewbc.jpg/)

Yeah, I see that you are correct.

Looks like they figured if they could not fix this problem, just eliminate it by not allowing you to use totem-preview on sound files !!!

---

### Post by DAB4970 on 2012-01-25
I have the same issue with 11.04.  If I'm not mistaken, there's a fix to this.  It is to extend the time (minutes/seconds) for the 'previewing', possibly in GCONF-EDITOR?  If there is someone who knows how to do this, please advise.  Thanks.

---

