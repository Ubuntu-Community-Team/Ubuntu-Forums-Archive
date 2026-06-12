---
title: "[SOLVED] fail to write dvd"
date: 2007-10-30
forum: Multimedia Production
---

### Post by Claus7 on 2007-10-30
Hello,

I want to backup avi files in a dvd. For this I try to use cd / dvd creator. For cds everything is ok. I burned ubuntu iso without any problem. Yet, when I try to write dvd is sais something like there is not enough memory in the place (dvd) I want to write data. Every time that sais this, the amount of space it displays is the same as that of the avi files I want to write.
Any ideas?

Regards!

---

### Post by jdackle on 2007-10-31
Well, from the top of my head:

You actually need a bit more space on the dvd than the total size of your files (I've noticed this before and I assume it is due to the extra space that is needed on a dvd filesystem to describe the files...).

Then, if by "cd / dvd creator" you mean GnomeBaker, it seems to have the bad habit of assuming you have the smallest (in terms of content capacity) possible kind of media - have you checked the option on the lowest position about the media size? Does it match the one you're using?

Hope that helped.

---

### Post by Claus7 on 2007-11-01
Hello,

thank you for your answer. I'm using cd / dvd creator from Places. About the media size I haven't seen such an option to cd /dvd creator.  I do not think that this is the same program with the one you are mentioning. Yet, I will try to use this and see if it is working. 

Regards!

---

### Post by netyire on 2007-11-01
Try K3B (its in the repositories). Just make sure to install libk3b-mp3 in order to prevent it from complaining about missing dependencies.

---

### Post by Claus7 on 2007-11-02
Hello,

I had tried k3b with no success with an empty dvd. The weird thing was that the program said that I had success (I could hear the tadahh sound), yet nothing was written to the dvd. Probably I had a malfunctioning dvd or maybe it was "disabled" as I was trying to write to it...Maybe while I was trying to use cd / dvd creator an "image" was written, yet the files not? And as a result the k3b thought the dvd written? Because when I inserted the dvd, a message appeared which was telling what I wanted to do with this empty dvd. I do not know. I just make assumptions. 
So I tried to use k3b once more with another dvd, being successful this time!

I mark this post as solved, yet the cd / dvd creator didn't work.
The result is that k3b is ideal for burning dvds.

Thank you,
Regards!

---

