---
title: "Streaming Audio Error"
date: 2009-11-29
forum: Multimedia Software
---

### Post by Reirol on 2009-11-29
Alright, I have a Windows xp computer that I use as my main gaming computer, and i have a Ubuntu based server that i store all my music and DVD movies onto so that i can stream them at my pleasure, anywhere in my home. 

This system worked great up until about a week ago.
I am still able to stream the audio files from server to client, but if the client computer (the windows xp computer) starts to move around in the directory of the server music folder the music will stop with different results in different music players:

In Winamp the music will create about a half second loop and will loop forever if allowed.

VLC will give this error message...
```
File reading failed: [COLOR=#ff0000]VLC could not read the file.[/COLOR]

```Then VLC will start the song from the start again.

I'm was inclined to believe was is that the head of the hard drive could not be in two places at one time, Physics ya know, but i moved the music files from the main 80gb hard drive that only had a 4mb cache, to a 160gb hard drive that has a 8mb cache. Unfortunately, the results were the same.

Now I'll ask the money question...
Why has it suddenly started to do this, and what can I do to fix it?
[COLOR=#ff0000][COLOR=#000000]

[/COLOR][/COLOR]

---

### Post by Reirol on 2009-11-30
bump

---

### Post by RedRat on 2009-11-30
Well it sounds as if you might have some kind of disk read error. How old is your hard drive? If the files on the smaller drive had errors in them, moving them to a larger drive will not help. You might try running the command that fixes errors on the disk (right now that command escapes me).

---

### Post by Reirol on 2009-12-01
First off, thanks for your reply.

Here's what I'm going to try:
I will be using a live cd to check the integrity of the disks, then I will actually boot off the CD and use fsck, As i understand it those are two different diagnostic procedures. After those have finished, I will check the SMART logs on the hard drives to see if the hard drive realizes if it has any problems. 

Please notify me if I am missing anything.

I will report back with my progress.

---

### Post by RedRat on 2009-12-02
> **Reirol said:**
> First off, thanks for your reply.

Here's what I'm going to try:
I will be using a live cd to check the integrity of the disks, then I will actually boot off the CD and use fsck, As i understand it those are two different diagnostic procedures. After those have finished, I will check the SMART logs on the hard drives to see if the hard drive realizes if it has any problems. 

Please notify me if I am missing anything.

I will report back with my progress.

It sounds as if your original hard drive might have had some problems and files might have been scrambled. Copying a scrambled file to another hard drive yields still a scrambled file. Definitely check your original hard drive for errors and see if it can be repaired. Sometimes, you lose data but then you don't have that data now. A lot will depend on exactly how the errors were caused, ie..physical damage or magnetic damage.

---

