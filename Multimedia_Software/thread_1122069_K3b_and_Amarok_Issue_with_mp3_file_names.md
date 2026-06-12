---
title: "K3b and Amarok Issue with mp3 file names"
date: 2009-04-10
forum: Multimedia Software
---

### Post by dbsoundman on 2009-04-10
I have a really strange and aggrivating issue with K3b and Amarok right now. It seems, for some reason, K3b is adding a carriage return to the end of each mp3 file name. When I open up the file properties dialog, it shows up as some sort of odd character that looks like the "4" side of a dice. Here is an example:

02 - Damien Rice - Volcano.mp3<dice character>

This seems to be preventing Amarok from importing these new songs. How can I fix this issue in K3b? I don't know how it got there but I definitely don't like it!

Thanks,
Dan

---

### Post by 0cton on 2009-04-10
Idk why it is doing that, could be with some compatibiltiy mode with windows or smth? and it's truncating file names... just an idea..
one temporary solution would be to make a script that renames all thooose files in mass (I think its not possible to do it with the rename command though)
btw K3b is a cd burner in what context do you mena its renaming files?
when burning them to a cd?

---

### Post by dbsoundman on 2009-04-13
I'm using K3b to copy CDs to my hard drive. I initially started using it instead of sound juicer simply because it was a lot easier to set up (at least in my perception at the time). I thought about making some sort of bulk rename script, but I would still rather fix the problem, it seems very specific and strange...

-Dan

---

### Post by wolfen69 on 2009-04-13
amarok needs **libxine1-ffmpeg** to play mp3's. you may need the medibuntu repos enabled to get it.

---

### Post by dbsoundman on 2009-04-13
I've already done that, long ago. I have been using Amarok on this machine for a couple months now with no problems. The real problem, I discovered, is that K3b is adding a carriage return to the end of the filename of each track it rips, for some reason, so Amarok doesn't recognize it as a valid file. It rips them in as

```
filename.mp3<return>
```

and I don't know why. I started a new thread about this problem, anyone have a clue about the possible issue here?

-Dan

---

### Post by djbushido on 2009-04-13
Um, this is a very good question...
First, maybe try another CD ripper, there are millions.
Second, I agree that a script is probably a good idea to mass rename. Actually, at least in XFCE, there is a program for batch re-naming, might be part of Thunar though.
Finally, the character that you are seeing is the literal character code (as far as I know). The system is saying that it doesn't have a character in the font-set for this, and also happens for alternate language fonts.

---

### Post by dbsoundman on 2009-04-13
You're right, I am seeing the character code. I wonder if this has something to do with the fact that I use the alternate international keyboard layout?

-Dan

---

### Post by djbushido on 2009-04-13
Most likely no. At least, as long as you have the right fonts installed.
If K3b is generating a CR in the filename, that's it's fault.

---

