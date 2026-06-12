---
title: "Can't connect to FreeNX server from NoMachine"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by gunnarflax on 2011-02-18
Hi! I've followed these tutorials to set up an [openSSH]("https://help.ubuntu.com/10.10/serverguide/C/openssh-server.html") and a [freenx]("https://help.ubuntu.com/community/FreeNX") server. I have installed nomachine on my windows 7 laptop and when I connect to the server I receive the error message: 

"Authentication failed for user [username]"

But I have no idea why. Which user am I supposed to log in with? Is it the same user as I use on the server or is this a separate nx user? When I receive this message is it because of the user or the ssh key I use?

Please give me whatever help you can because I'm completely stuck...

---

### Post by gunnarflax on 2011-02-20
bump*

---

### Post by gunnarflax on 2011-03-07
Problem solved. I made a fresh install of the whole system and now I tried setting it up again. This time I didn't install openssh-server first, it was included in the freenx package. Then I just followed the instructions here:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

During installation I chose to use the default nomachine ssh-key and afterwards I ran
```
sudo dpkg-reconfigure freenx-server
```
and made a new ssh-key which I copied over to the client and it worked flawlessly out of the box. Yay, first time ever for me :P

So this is solved I guess :)

---

### Post by gabrielcz on 2013-03-29
So, you "solve" your problem re installing the whole system? :confused::confused::confused::confused::confused::confused::confused:

---

### Post by matt_symes on 2013-03-29
Old thread; Closed.

---

