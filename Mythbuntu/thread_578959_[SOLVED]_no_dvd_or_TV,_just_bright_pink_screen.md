---
title: "[SOLVED] no dvd or TV, just bright pink screen"
date: 2007-10-17
forum: Mythbuntu
---

### Post by govee on 2007-10-17
I was having a problem with the MCC and did apt-get update as Superm1 suggested and that fixed it (thanks). I decided to move on to my next prob which was Mplayer does not work. I realized that the W64 codecs were now available so I selected them and I atleast get a pink picture were before Mplayer would just fail. I then went to watch tv and lucky me it shows the same thing. II have searched and cant find anything that helps.

---

### Post by superm1 on 2007-10-17
> **govee said:**
> I was having a problem with the MCC and did apt-get update as Superm1 suggested and that fixed it (thanks). I decided to move on to my next prob which was Mplayer does not work. I realized that the W64 codecs were now available so I selected them and I atleast get a pink picture were before Mplayer would just fail. I then went to watch tv and lucky me it shows the same thing. II have searched and cant find anything that helps.
What type of movie are you trying to play?  The w64codecs/w32codecs packages were typically only useful for wmv3 in my experience.  I say were because mplayer now has native wmv3 support.

---

### Post by superm1 on 2007-10-17
As I re-read your post.  What video driver are you using.  A pink screen is characteristic of a few things:

- Using the second (non video overlay) screen in a dual screen setup
- HD video on too poor of a video card
- Not enough video ram for video playback
- Some poorly performing open source video drivers.


If you have a proprietary driver available for your card, I would recommend activating it.

---

### Post by govee on 2007-10-18
I should state that I was able to watch Tv before this. I have a Geforce 6200 with 256MB RAM, runnning the proprietary drivers. Maybe I need a liitle Codecs lesson. If I am running the AMD64 OS which of the codecs should I be running. There are 4 selections W32, W64, some sort of LIB, and FFMPEG. I currently have the last 3 selected and installed. I was just  trying to watch a real DVD (store bought, not ripped). I was looking in the player settings and for DVD the player command is internal, nut for VCD it is very different, something along the lines of /dev/cdrom!@$%#$%#$ that last part I dont remember. Why so different?

---

### Post by govee on 2007-10-18
I just turned on my machine and TV worked fine. I exited out of the frontend and opened Mplayer attempted towatch a dvd and I got the funky picture same as before(sound has always worked).I closed Mplayer and went back into the frontend and now that picture is gooned up as well. I just logged out and in and the tv picture is good again. 

What settings is the Mplayer messing up?
 I did some searching and saw a thread that spoke of the lidvdcss2 and a problem with it coming from the Medibuntu repositories, so I used synaptic reloaded the libdvdcss2 and the other 2 libdvd files and dvd playback now works! I have no idea what the issue was but its gone.

---

### Post by hamil on 2007-11-24
I found my solution in another thread in this forum. You can read it here:
[Ubuntuforum thread](http://ubuntuforums.org/showpost.php?p=2896078&postcount=2)

---

