---
title: "create and setup ubuntu home network"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by dutchgirl on 2010-11-26
Hello, I'm trying to figure out how to setup a home network with my three ubuntu boxes. I've looked around online and tried from what i know with windows to setup a file sharing network, but i haven't had any luck. I've been using ubuntu now for almost seven months and would really like to figure this out to expand my setup. Thanks in advance for your time and help.

---

### Post by spiky001 on 2010-11-26
Have you looked in to ssh?

---

### Post by dutchgirl on 2010-11-30
Yes, I currently use ssh to transfer files, but, I'm looking for a way to create a home network with a user interface similar to the network on windows on my three ubuntu boxes.

---

### Post by dutchgirl on 2010-12-03
By using samba I have discovered a way to setup the network I have been trying to establish. By right clicking on any folder you want to share and goto sharing from there you will be able to establish a gui based network. Once installed you will have to go to terminal and create users and pws. here is the terminal command for the string:

sudo smbpasswd -a [username]

after entering the command it will prompt you for a pw. this will be the pw for the added user. At this point from any ubuntu box as well as windows you will be able to access this shared folder on the network. I hope others will find this post helpful.

---

### Post by fraserf88 on 2010-12-03
dutchgirl, I would like to thank you. I have been banging my head against the keyboard for a few hours now trying to figure out why I couldnt acess my samba shares. I have never had to use this command before to use samba. In the past it  just defaulted to my user name and password used to log in to the pc. Why this has changed I dont know, but it was driving me crazy up until I stumbled on your thread. Thank you so much :D

---

### Post by dutchgirl on 2010-12-04
no worries, I literally just stumbled a crossed it myself. It took me almost three months to figure this out. Heh, kinda sad, but, at least I learned something new :p

---

### Post by Boondoklife on 2010-12-04
And here is a great script to automate the mounting of shares in gnome.

[http://ubuntuforums.org/showpost.php?p=9322776&postcount=77](http://ubuntuforums.org/showpost.php?p=9322776&postcount=77)

---

### Post by miesogeno on 2010-12-06
hi dutchgirl, i did it just like explained but after i confirmed the password it returned "Failed to add entry for user [whatever]"


i have samba installed, obviously, am i missing something else?

---

### Post by dutchgirl on 2010-12-06
just checking, but, u did substitute {username} with the actual username minus [ ] correct? If so, copy and paste from start to error what the read out in terminal states. Furthermore. upon successful creation of user and pw, I had to reboot my boxes in order to get the network viewable from all boxes. I hope this was helpful.

---

### Post by miesogeno on 2010-12-06
well, i thought i was pretty smart for replacing [username] for [the actual username], but in the end i left the [].
i guess overjudged my intelect.

it worked now. thanks!

---

### Post by Boondoklife on 2010-12-06
> **miesogeno said:**
> well, i thought i was pretty smart for replacing [username] for [the actual username], but in the end i left the [].
i guess overjudged my intelect.

it worked now. thanks!

[CENTER]*Epic Facepalm*
[IMG]http://i176.photobucket.com/albums/w166/bak42/icon_facepalm.gif[/IMG]
[/CENTER]

---

### Post by dutchgirl on 2010-12-06
no worries, I'm glad I could help :|]

---

