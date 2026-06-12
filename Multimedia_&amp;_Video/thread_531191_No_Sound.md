---
title: "No Sound"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by Robt57 on 2007-08-21
I have installed UBUNTU 7 on this computer ( Pen III 997 )  and I cannot get the sound to work even though it works in windows. The sound card is a Creative Sound Blaster ISA Interface. The model Number is CT4520. I am new to UBUNTU & Linux so am Lost. Every thing else seems to be working.
                        Can anyone Help
                                                       Bob Slater

---

### Post by mohnkern on 2007-08-21
First type:

lspci | grep -e creative

You should see a line appear that shows your sound card.  If you don't you'll need to run modprobe to put in the right module.

If you do an lspci | grep -e creative and see your card listed, try typing:

asoundconf list

and see if it's listed there.

---

### Post by dabl on 2007-08-21
What does ```
alsamixer
``` give you?

---

### Post by AlexEagar on 2008-02-16
[Solution Source]("http://ubuntuforums.org/archive/index.php/t-115697.html")
[Explanation]("http://www.osnews.com/permalink?f298700")

Add the following line to /etc/modules and then reboot.

snd-sbawe

---

