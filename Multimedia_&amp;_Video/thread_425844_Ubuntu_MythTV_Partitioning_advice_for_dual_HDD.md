---
title: "Ubuntu MythTV Partitioning advice for dual HDD"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by DiscMan on 2007-04-27
I am wanting to convert my home PC from Windows XP to Ubuntu. I am a very experienced Windows user as I develop software for Microsoft platforms for work, but I am new to Linux. The main reason for the conversion is that I want my home PC to run as a MythTV Backend and regular desktop. I have always wanted to try Linux as well and this was a great excuse! 

I have 2 hard drives... a 40gb IDE and a new 320gb IDE. I plan to use the 320gb mainly for storage of my recordings. Two people will be using this box as regular desktop (internet, email, word processing etc).

What partitioning scheme would you recommend that I use? I was thinking of using LVM2 as I like the idea of being flexible and being able to expand any partitions if my initial sizings are out. I don't know how to use LVM2 with Ubuntu though.

I was thinking of separating /var/video to it's own partition given that the recordings can be multi-gigabyte in size and I want to use the JFS filesystem for this partition only. I also thought that having this on a separate physical drive would have less impact on my desktop experience when recordings were underway at the same time.

So what if on hda I have SWAP (1gb), / (10gb) and /home (rest ~29gb) and on hdb I have /var/video? My system is an Athon XP 1700+ with 1.25gb RAM and ASUS A7V266-E motherboard.

Should I be using LVM2? Suggestions?

I don't mind getting my hands dirty; I was just looking for some pointers in the right direction.

Thanks in advance for any help. 

Jason

---

### Post by DiscMan on 2007-04-28
One more question, are recordings typically stored in /var/video or /var/lib? The mythtv guide shows /var/video as an example, but the Ubuntu mythtv feisty guide partitions /var/lib.

Thanks!
Jason

---

### Post by Erlander on 2007-04-29
Have a look at this guide:

[https://help.ubuntu.com/community/MythTV_Feisty](https://help.ubuntu.com/community/MythTV_Feisty)

and follow the link to Frontend, Backend, regular desktop.

It should answer most of your questions.

Re Mount points for partitions:  Mythtv setup will allow you to change them to suit your needs.

I personally have my home folder on the separate hard disc and a folder off it fro Mythtv recordings.

Rob

---

