---
title: "Nero Linux"
date: 2012-05-08
forum: Multimedia Software
---

### Post by kuvanito on 2012-05-08
miss nero?
no more,come and get it! [http://www.nero.com/eng/downloads-linux4-update.php]("http://www.nero.com/eng/downloads-linux4-update.php")

---

### Post by oldsoundguy on 2012-05-08
I didn't even use that bloated piece of invasive crap in Windows .. Ashampoo works great in Windows and have not had any issues with Brassero in Linux.

---

### Post by kelvin spratt on 2012-05-08
You give your email then download 
Its a good bit of kit in Linux

---

### Post by kuvanito on 2012-05-08
you may be sorry for your comments,wait until you find out 4 urself

---

### Post by kelvin spratt on 2012-05-08
> **kuvanito said:**
> you may be sorry for your comments,wait until you find out 4 urself
Who may be sorry

---

### Post by kuvanito on 2012-05-08
oldsoundguy
nero has always been a good product,at least 4 me,better than (Brasero good 4 nothing)
I still do not underestand why ubuntu+canonical keep Brasero?
so far they got it right with thunderbird 4 evolution but brasero,hummmmmmmmmm anything but brasero 4 me......

---

### Post by ajgreeny on 2012-05-08
> **kuvanito said:**
> oldsoundguy
nero has always been a good product,at least 4 me,better than (Brasero good 4 nothing)
I still do not underestand why ubuntu+canonical keep Brasero?
so far they got it right with thunderbird 4 evolution but brasero,hummmmmmmmmm anything but brasero 4 me......
What is wrong with brasero?  I did once always use k3b, as I liked KDE more than gnome, and used to add kubuntu-desktop to ubuntu, but when I found ubuntu 8.04, a great ubuntu version, I started using gnome, and therefore brasero, and have found it to be great ever since.  It is quick, burns anything I give it without a problem, and is simple to use.

---

### Post by kelvin spratt on 2012-05-08
> **ajgreeny said:**
> What is wrong with brasero?  I did once always use k3b, as I liked KDE more than gnome, and used to add kubuntu-desktop to ubuntu, but when I found ubuntu 8.04, a great ubuntu version, I started using gnome, and therefore brasero, and have found it to be great ever since.  It is quick, burns anything I give it without a problem, and is simple to use.
There is nothing wrong with brasero as a basic burner I use it for convenience, That said I paid a lot of money for my Plextor dvd writer which I use for serious work then I use Nero to compliment it result nil coasters. cheap DVD writer for for normal use and usually brasero.

---

### Post by kuvanito on 2012-05-08
nothing wrong with brasero
takes twice the ammount of time it takes Nero,K3B or any other and more often it fails,just nothing wrong with it.....come on guys,you got to b kidding
any ways,my post was to give you a link.JUST IN CASE......

---

### Post by cottfcfan on 2012-05-09
I've been using Nero Linux for about 2 years.
The quality of the burn IMO is far superior to the native Linux apps, but then it is commercial software that upto now has had to be paid for.
Well worth having though if it's now free.

---

### Post by shantiq on 2012-05-09
thank you for link kuvanito

mind you you get a month and then you have to pay [or do i misunderstand]; not sure how this is better than k3b or command line


for example

> RIP and burn  with  ICEDAX/WODIM
===================


       To copy an audio CD in the most accurate way, first run

           icedax dev=/dev/cdrom -vall cddb=0 -B -Owav

       and then to write run

wodim dev=/dev/cdrw  -v   speed=2 -dao -useinfo -text  *.wav 





from cue    cdrdao write --eject --speed 8 --device /dev/sr0  --driver generic-mmc   name.cue



I WONDER how this performs for speed ...

---

### Post by kuvanito on 2012-05-09
up to now it's been free
i have not read the whole thingy but mine came with a key and just in case i have a key to input.
speed,what speed? Lightning!!!! I burn 12.04 in 55 seconds on to a cd,that's right a cd,even thou 12.04 is 701 MB Nero burns it to a CD no problem and it works....

---

### Post by dzchimp on 2012-05-09
K3b always works fine for me. But I have nero too, for specific files

---

### Post by kuvanito on 2012-05-09
can we burn Blue Rays Discs with Brasero? I don't know but Nero Linux 4 does it.That I know :guitar:

---

### Post by Jakin on 2012-07-24
Mind if i switch up the topic abit? I like nero linux for its "save tracks" feature, and it has worked since ubuntu 7.10 amd64. However since upgrading to 12.04 amd64- outputing file to any format at all is grayed out. Anyone know what could be causing this? Missing packages or something???
Before some suggests a different program, i use nero linux for its ability to output HE-AAC VBR with .m4a extension; as far as i know only nero can do this. (but if someone knows a program that can accomplish this EXACT thing and also internet tag lookup, im game) i have heard that k3b will do this, using nero AAC linux binaries, but have yet to figure out how to set those binaries up for k3b to use.

[http://imageshack.us/f/651/snapshot2qa.png/](http://imageshack.us/f/651/snapshot2qa.png/)

Screenshot of what i mean ^

---

### Post by Kreaninw on 2012-07-25
It's not a matter of open source or not, even if it's free or not. When something has to be done, only quality and effort do. However, when it does cost, worthiness comes into play.

That's beside the point, I have bad experiences with Brasero. Beside its interface which is better than some others, it's the worse burning app I have ever tried. I fail to burn MP3 CD with Brasero, a universal MP3 CD that can be play in any supported players, not just some decent players, that's what Ashampoo does for me on Windows. And that's I fail several time burning with Brasero, it's 50/50 situation, not worth it. Sometime it even made my writer hang, can't eject my disc.

I don't know why Ubuntu still include Brasero in their OS, that piece of junk app. And the worse is Ubuntu waste their money/time to support them(I don't know what critical update means.). It's just a bad move after all.

---

### Post by cottfcfan on 2012-07-25
Jakin...
re: Your problem.
I had the same thing and this resolved it.
Run the following in a terminal:
```
sudo mkdir /usr/lib64
```
```
sudo ln -s /usr/lib/nero /usr/lib64
```
Should do the trick.

---

### Post by kuvanito on 2012-07-25
> **Kreaninw said:**
> It's not a matter of open source or not, even if it's free or not. When something has to be done, only quality and effort do. However, when it does cost, worthiness comes into play.

That's beside the point, I have bad experiences with Brasero. Beside its interface which is better than some others, it's the worse burning app I have ever tried. I fail to burn MP3 CD with Brasero, a universal MP3 CD that can be play in any supported players, not just some decent players, that's what Ashampoo does for me on Windows. And that's I fail several time burning with Brasero, it's 50/50 situation, not worth it. Sometime it even made my writer hang, can't eject my disc.

I don't know why Ubuntu still include Brasero in their OS, that piece of junk app. And the worse is Ubuntu waste their money/time to support them(I don't know what critical update means.). It's just a bad move after all.

I can feel your pain because I feel the same way you do but do as I do after a clean install (sudo apt-get remove brasero* and sudo apt-get purge brasero* Be Gone MF) hehehehehe :)

---

### Post by Jakin on 2012-07-25
Wow, as i was reading this topic, i thought those commands had to do with just being able to burn, not ripping. Did work :) Thanks cottfcfan.

---

### Post by cottfcfan on 2012-07-25
No problem, wasn't me though, got that workaround off someone else on the forum.

---

### Post by rongden on 2012-07-25
I don't use it [.]("http://text4freeonline.com")[.]("http://www.footballbettingnews.co.uk/")

---

### Post by wvonstockhausen on 2012-07-31
I'm using Nero10 video for editing in Windows. Does Nero has a free Ubuntu version or is there a comparable Linux video editing software?

---

### Post by kd5mkv on 2012-07-31
Well I do like Brasero, I have made plenty discs without any problems.
Windows didn't offer anything I like, the nero version I had couldn't burn
an iso for a boot disc. I will try this nerolinux and let you'll know, which is best.

---

