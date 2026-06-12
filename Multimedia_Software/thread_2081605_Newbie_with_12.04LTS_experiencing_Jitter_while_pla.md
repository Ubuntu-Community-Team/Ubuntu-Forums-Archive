---
title: "Newbie with 12.04LTS experiencing Jitter while playing audio."
date: 2012-11-07
forum: Multimedia Software
---

### Post by Pawan Kumar G on 2012-11-07
Hi friends,

I am new to ubuntu and this forum. This is my first post.

I have installed/reinstalled Ubuntu as a dual boot along with my Windows 7 and it looks awesome.

On playing an mp3 file, I could see that the player stops every .5 second and the music is completely jittered.

**What all I tried :**

1)copied the mp3 file into my home and tried playing. same result.
2)Installed VLC player and tried the same problem persists.
3)Went to youtube and played a video, the same thing happens.
4)and Eventually landed up here 
Please help me out friends.

Thanks 
Pawan

---

### Post by sydbat on 2012-11-07
Welcome to the forum.

Questions...

1) When you say "I have installed/reinstalled Ubuntu as a dual boot along with my Windows 7", is this via WUBI, or an actual separate partition for each OS?

2) How are you accessing your music files? A shared folder with Windows?

3) What are the specifications for your computer (processor type, video card, etc)? Is it store bought (HP, Dell, etc)?

I know there will be more questions for you, but answering these initial ones can begin the process of us helping you.

---

### Post by Pawan Kumar G on 2012-11-07
> **sydbat said:**
> Welcome to the forum.

Questions...

1) When you say "I have installed/reinstalled Ubuntu as a dual boot along with my Windows 7", is this via WUBI, or an actual separate partition for each OS?

2) How are you accessing your music files? A shared folder with Windows?

3) What are the specifications for your computer (processor type, video card, etc)? Is it store bought (HP, Dell, etc)?

I know there will be more questions for you, but answering these initial ones can begin the process of us helping you.

Hi Sydbat, thanks..
Here are my answers :
1)I have tried both the versions. Initially, i tried through WUBI. then I created a flash disk that boots ubuntu. 
Something strange here : Before installing ubuntu through the flash disk, I created a partition of 50 GB for UBUNTU then restarted my system, inserted the flash disk, it did not ask where to install. it just went on installing.

2)I tried either ways : I even copied a music file from a windows folder to my ubuntu home/music location.

3)The processor : intel dual core with 2GB DDR2 and 500 GB of disk space. I know this is not the best config, but windows 7 runs well in this system. It isnt from any manufacturer. I had self assembled it.

Also, please note : the problem persists when I play a youtube video. so do you suspect any overall throughput delay which is not visible when browsing/working with spreadsheets but is clearly identified when playing music?

Thanks,

Pawan

---

### Post by sydbat on 2012-11-08
Pawan,

What is your motherboard? I have encountered similar problems with my clients who have audio trouble, and it usually has to do with the on-board audio. Some motherboards with on-board audio have trouble with Linux, why I do not know.

If you have access to a separate sound card, try that and see if it clarifies things. I have found this *usually* works.

---

