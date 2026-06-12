---
title: "Ubuntu as a home media server"
date: 2011-07-22
forum: Multimedia Software
---

### Post by Canoemarc on 2011-07-22
Dear Fora,
 
I have been using Ubuntu 10.10 for a few months now, though I still would classify my self as a newbie.
 
I have revived an old laptop (ACER, AMD 3400 64 bit) and have managed to transfer all my media from my Win 7 laptop via an ethernet cable. (I am not quite sure exactly how this happened-several attempts at accessing media folders from each computer, eventually something went as expected and I just copied the files over!!)
 
The question is this:
 
I would like to use said old laptop as a media server, over my home wireless network.
If this works well and is secure then I would consider also using it as a server for some of my personal work files also.
 
When I speak to people or read on forums or even watch on youtube I am confronted with several different options:
 
Samba file share, Mythbuntu and myth TV, Ubuntu server edition, virtual box and so on.
 
What is the easiest, reliable and secure way of acheiveing a media distribution server which is compatilble with another Ubuntu laptop, a Win 7 laptop and my internet radio?
 
Is there a facility to have the old (and noisy) laptop running in a spare room, and using a sleep and wake function (saving power) to access the files without actually having to physically switch it on or off? Or will it have to be on continuously?
 
I would be grateful for any help or advice.
 
But please keep things ridiculously simple!!
 
Thanks in anticipation

---

### Post by exinfernis on 2011-07-22
My friend, I am no expert at all, I have been running Ubuntu 10.10 for the last 6 months and I have the same quest on my mind. A home server. What I am going to do is this:
Setup a Ubuntu server with a couple of HDDs and be done with it.
Samba is a utility for sharing resources on the network and is really old and really good at it. The laptop you are reffering to is good for a file server by means of sharing a certain number of folders for the rest of your computers to see. You dont really have to switch it on and off though, it will go to sleep whenever not used, and you can setup wake on lan (in the bios) if supported to ...wake it .... when a file is needed.

Virtual box is a virtualisation suite like Vmware's Workstation. You can build a virtual OS system hosted on the laptop's OS but it would be a loss of resources much more needed for other uses.

Myth...whatever, is a ready made distribution for your purpose but not for a files server only. Take look into it , its good but just for what it is supposed to do. By all means, really take a look into it...its dazzling.

My opinion, would be to setup ubuntu server and samba and go from there...

Regards, and welcome to the forums... :)

---

