---
title: "Best Profesional Image Bacup Tool?"
date: 2009-09-22
forum: Networking &amp; Wireless
---

### Post by fryser_d on 2009-09-22
Hi there, I want to install a **professional backup tool** installed on a Linux server, with **Windows and Mac Workstations**. Every night the server wakeup all computers and restore an image according to the computer connected(MAC ADDRESS). Ex: Laptop=>Windows and soft for THIS Laptop, Mac=>MAC_OS for this PC, etc...

[LIST=1][*]Wake from LAN[*]boot PXE on lan[*]Restore image when asked or scheduled, Remotely[*]Can manage backup[*]Web Gui (if possible)[*]Free
[/LIST] :popcorn:

I searched a lot on the net but none looks to fit the requirements 

You have
[LIST]
[*]BackupPC
[*]AMANDA
[*]Bacula
[/LIST]
But they use archive not images. :lolflag:

"Acronis" can do all that but the server is Windows not Linux, and 800$ -.-"

Can any of these do what I want?
[LIST]
[*]systemimager
[*]g4l
[*]partimage
[/LIST]

I know I saw that in my school, but how are you doing it with Linux? :confused:

Thx again for your time.
Fryser

---

### Post by fryser_d on 2009-09-22
Up! \\:D/

---

### Post by fryser_d on 2009-09-23
up! up! :guitar:

---

### Post by fryser_d on 2009-09-24
An idea someone? :KS

---

### Post by JonRohan on 2009-09-24
Why would you want to restore an image to a computer every night? Doesn't really make sense.

---

### Post by fryser_d on 2009-09-26
> Why would you want to restore an image to a computer every night? Doesn't really make sense.

Thanks for answering.

Actually it's commonly used by administrators to prevent users to:

1- Installing malwares, without preventing users to install good utilities 
2- Always a fresh installation, at the morning, no slow machines.
3- Force centralize work into a server, with all the backup and security that it's involved.

Pretty much all "big" organizations use that system. I want to know how to do it on Linux! :)

I'd love some suggestions; thanks for your time.
Fryser.

---

### Post by we_r_disturbed on 2009-09-27
I've had a lot of success making images using clonezilla, however I haven't used it in the setup you specifically requested.  There is a server edition that does some of the things you want.

[http://clonezilla.org/clonezilla-server-edition/](http://clonezilla.org/clonezilla-server-edition/)

It might get you pointed in the right direction.

---

### Post by Roasted on 2009-09-27
Good luck with Clonezilla Server. I spent 4 months trying to get it working and never got it working. I even posted exact steps I did, from installing Ubuntu, what keystrokes I did, etc, and I couldn't find anybody to figure out why my install didn't work. I'm sure once it works it's great. I've seen videos of people using it. But I just couldn't get it to work.

I ended up going to FOG - Linux based, runs on Ubuntu, web GUI, and images Windows workstations. IT DOES NOT IMAGE MAC, currently, but it's amazing for imaging Windows workstations. I've heard Mac support is in the future, but not currently supported. 

With their new version (0.27) it runs with a scheduling option as well.

In two months at work I have imaged 1,600 computers using my laptop (Core 2 Duo, 4gb RAM, gigabit ethernet) with Ubuntu 9.04 64 bit + FOG 0.26, and recently they came out with FOG 0.27 so I'm running that now since 0.27 supports Windows 7 and we're moving to that before long.

I have heard of a Mac imaging solution known as Deploy Studio, which I BELIEVE is free. I'm not sure, but FOG is truly amazing to use with Windows workstations, I'd recommend it 1000 times over again. If Deploy Studio is an option for Macs, then run with it. I don't have Macs to deal with (thankfully) :P so I can't offer any help in the Mac department besides hearing someone else suggest Deploy Studio previously.

---

### Post by fryser_d on 2009-09-29
God! Roasted...

I think you got it! o_0
=D>

I'm getting on it right away... 
thx again ^ ^
Fryser

---

### Post by Roasted on 2009-10-01
Just an FYI - FOG came out with version 0.28 about two days ago. So far I've used it with imaging about 25 computers and it's been solid. 

If you need help setting it up, post back here. I'm pretty good with answering simple questions in terms of how you use it and get things going, but since you seem to be wanting to put it on your entire network, I'm not too experienced there. I need to keep things simple, efficient, and portable, and since I travel a lot I keep FOG on my laptop and run around with that gig switch and some ethernet cables. That way I can set up anywhere and I don't need a dedicated FOG server in each building. :)

Good luck!

---

