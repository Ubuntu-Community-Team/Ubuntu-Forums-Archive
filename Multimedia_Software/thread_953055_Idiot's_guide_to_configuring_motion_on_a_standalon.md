---
title: "Idiot's guide to configuring motion on a standalone machine"
date: 2008-10-19
forum: Multimedia Software
---

### Post by rawlyn on 2008-10-19
Hi, I'm new to these forums so if this is in the wrong section I apologise.

I've installed the 'motion' package using
```
sudo apt-get install motion
```
but I haven't got the foggiest idea how to configure it for my needs. I've searched the net high and low for a guide to it that I can understand easily, but without much luck.

What I want to do is set it up so that I can run it before leaving my desk, so that it will monitor any unwanted visitors to my office while I'm not there. It don't want it running all the time, and I don't want it running over a network, but most of the guides I can find are all about getting it running through a server, over ftp, etc.
I simply want it set up so I can initiate it from a script or whatever, and get it to save captured video to somewhere in my home directory.

Can anyone help me? I'm so confused by all the documentation I can find! Thanks in advance for any advice.

If it makes a difference, I'm running Ubuntu Eee (on an Eee PC - obviously I suppose).

---

### Post by antarctica7 on 2008-11-18
open a console window and enter the following

```

mkdir .motion
sudo cp /etc/motion/motion.conf ./.motion
sudo chown <username> ./.motion/motion.conf
gedit ./.motion.conf

```
change <username> to your user name.

You can now create a Launcher icon on your desktop or in your menu for 'motion' or just type it in a terminal.

What this does is copy the default motion.conf from /etc/motion to a hidden directory 'motion' in your home folder, changes ownership to you, and opens the file in gedit. It is in the .motion (hidden) directory because if you start the program from your home directory it will look there first before loading the config file in /etc/motion.

Configuration is fairly easy, you don't have to edit anything really. But you can go through the config file and it has comments for each option.

I'm still having problems with changing the height and width :( It keeps changing to 176x144 at run time. I think I've narrowed it down to a video4linux device issue.

Anyways, good luck.

---

