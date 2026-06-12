---
title: "cant connect to network/net please help"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by tom wills on 2009-01-11
Hi im a compleat noob when it comes to ubuntu just got it last night after i finished the instal the net wasnt working .

i have a windows pc and an ubuntu pcs side by side but no way of moveing files over . there both connected thro a netgear router.

the ubuntu has somthing about: Auto eth0 i dont have a clue how to configur it.

I was a windows fanboy XD

I also dont have a clue what version of ubuntu i have i just know its ubuntu.

Thanks in advance

to add to the post the pc was freshly built yesterday

The eth0 is set to auto maybe it has the wrong mac ad ?

---

### Post by tom wills on 2009-01-11
anyone ? please i need to get this pc on the net : /.

terminal is showing everythings being picked up..

i cant post any of it because im on a windows pc atm ....

Please help : /

---

### Post by tom wills on 2009-01-11
ive looked thro the forums and cant find anything to fix my problem

the connection is thro the mobo its not thro a pci card.

the specs of the pc are:

Abit A-N78HD NVIDIA GeForce 8200
4 gb corshair ram
ati 3850hd
AMD Phenom 9650

i havnt got a clue what version of ubuntu it is my friend burned the disks

---

### Post by tom wills on 2009-01-11
ive looked thro the forums and cant find anything to fix my problem

the connection is thro the mobo its not thro a pci card.

the specs of the pc are:

Abit A-N78HD NVIDIA GeForce 8200
4 gb corshair ram
ati 3850hd
AMD Phenom 9650

i havnt got a clue what version of ubuntu it is my friend burned the disks

---

### Post by Iowan on 2009-01-11
You're probably getting tired of the monologue, so I'll throw in some information. Just an FYI - Try CTRL-ALT-F1... The version number *should* be listed there.  In addition, whenever I start Firefox, I get a "Welcome to Ubuntu 7.10" page (guess which version I have...).

If you're gonna move files between Ubuntu and Windows, you're *probably* gonna need [Samba]("https://help.ubuntu.com/community/SettingUpSamba"), although if file transfer (as opposed to file sharing) is your only goal, you might be able to use [SSH]("https://help.ubuntu.com/7.10/server/C/openssh-server.html") or even [FTP]("https://help.ubuntu.com/7.04/server/C/ftp-server.html")

If the problem is network connection, it would help to (somehow) post information from **ifconfig**, **sudo lshw -C network** and perhaps contents of */etc/network/interfaces* file... otherwise, I can only guess what might be causing problems.

---

### Post by ugm6hr on 2009-01-11
A bit more detail would be helpful.  I assume you connect to a router via an ethernet cable (if not - please restate your situation).

I would suggest using a USB stick to transfer files for the time being - so that we can help.  You have to give us the output from the following commands (I have included as many as I can think that might be relevant to allow you to transfer everything at once):

```
uname -a
lsb_release -a
lspci -nn
lshw -class network
ifconfig
```

---

