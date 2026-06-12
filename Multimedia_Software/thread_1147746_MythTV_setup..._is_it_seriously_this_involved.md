---
title: "MythTV setup... is it seriously this involved?"
date: 2009-05-03
forum: Multimedia Software
---

### Post by knottshawk on 2009-05-03
So I'm coming from a Windows media center background and thought I'd give MythTV a shot. I installed it and fired it up expecting, I guess ignorantly, that it would have basic functionality without my help. I was mistaken... My mouse didn't work, the bottom buttons were cut off so I couldn't read them (24" monitor), and it doesn't DO anything media wise (doesn't see my TV tuner card, etc)

So... 
A) What's the easiest way to set this thing up? (Would mythbuntu help or is it just the same thing in different clothes?)
B) Is it worthwhile?

Honestly I'm just dreading reading through MythTV's dozens of pages of setup and support just to "try this out".

---

### Post by dano1 on 2009-05-04
it takes some work imo but i get a kick out of it. not where i want it to be yet but getting close. not plug n play if thats what ur looking for though.

---

### Post by knottshawk on 2009-05-04
Well, before I invest the time, is the end result of MythTV like Windows Media Center? Really I just want to be able to watch and record TV on my computer... so if MythTV is over-complicated for that, what should I use?

---

### Post by JoseRijo on 2009-05-13
Mythbuntu is definitely the way to go.  I switched from a MythTV install over Debian and it was a lot simpler.  Of course, everything gets simpler with each new version of the kernel.

Good luck!

---

### Post by Mythbuster1848 on 2009-05-13
Mythbuntu or Knopmyth are as close as it comes to zero-config. The better you understand your hardware, the less work you'll have to do. Have a look at the MythTV Wiki ([www.mythtv.org](www.mythtv.org)) and make sure your hardware is supported. 

If all your hardware is listed as completely supported, the most recent version of Mythbuntu will work almost immediately. I've played with installing MythTV from packages onto a stock Fedora install, Mythdora, and most recently Mythbuntu. We've come a long way. 

A bit of config work is the price we pay for complete and total control over the system. I think it's well worth it.

---

### Post by abasel on 2009-05-13
I am busy setting up following:

[http://www.mythtv.org/wiki/Ubuntu-8.10_Source_Install]("http://http://www.mythtv.org/wiki/Ubuntu-8.10_Source_Install")

Towards the end it says "You have to create a file for mythtv for databse connections ~mythtv/.mythtv/mysql.txt"

But I don't understand enough about Linux to know where I must put "mysql.txt" ie which directory (The one above doesn't seem to exist).

---

### Post by JoseRijo on 2009-05-14
So just make the directory.  But remember that the permissions should match the mythtv user:

sudo su - mythtv -c 'mkdir ~/test1'

or better yet, login as the mythtv user.

The same applies for the mysql.txt file itself:

sudo su - mythtv -c 'vi ~/test1/test.txt'
(replace vi with whichever editor you're comfortable with).

---

### Post by abasel on 2009-05-14
Thanks for that.... what does "~" mean or stand for?

~/test1/test.txt

---

### Post by TheIndecisive1 on 2009-05-14
> **abasel said:**
> Thanks for that.... what does "~" mean or stand for?

~/test1/test.txt

the "~" is shorthand for a user's home directory. For example "~/test1/test.txt" is the same as "/home/username/test1/test.txt"

---

