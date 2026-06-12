---
title: "nx nomachine problem"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by Henry80 on 2009-01-18
Hi guys, i'm in trouble without find a solution for my problem with NXnomachine server/client
Thats the problem:
when i connect with nx client to a ubuntu nxserver machine with a new session everything works properly but, when i connect in shadow session mode, i have problem with keyboard, just few keys are listened to the server machine and above all in wrong way, like c key has a behaiv like an arrow key and however no letter's keys are listen to the server machine.
Few information useful for help me could be:
server nx on ubuntu 8.10 machine
client nx tried with remote access from lan with another machine installed ubuntu7.10 and windows xp...
i hope u can help me...
Thank you very much. Enrico

---

### Post by Macchi on 2009-01-18
There seems to be bug report on this issue with NX software. Thus the problem is probably not in Ubuntu. Check [http://www.nomachine.com/tr/view.php?id=TR02F02001](http://www.nomachine.com/tr/view.php?id=TR02F02001)
Hope you will find a solution.


By the way I use NX for a couple of servers and it is quite cool. I have had a few issues with the early versions of nx but now it got much better later. Their licensing could offer better conditions to the community since their products have been built up based on open source. Their free (as beer) server is quite limited with only two users.

For two years ago I had a minor key translation problem on NX using a combination of nx client and synergy (the later allows sharing keyboard and mouse across different computers).

---

### Post by Henry80 on 2009-01-18
Thank you for the answer.
Another question: how may i update the nx node package from the linux terminal?? 
Thank you. Enrico

---

### Post by Macchi on 2009-01-19
Ciao Enrico,

Not all NX packages are available on the Ubuntu repositories, thus nxnode and nxserver will not be updated automatically upon new releases. 

Thus you can download the latest binary versions from Nomachine, save them locally on a folder called nx on your Desktop, remove the old packages and install the latest version with the following commands on a terminal:

(suppress the # comments, of course)

```

# To Remove NX packages use: sudo apt-get remove <package names>
# (You may use the --purge option to completely remove configuration files
#  I do that often to be sure the newest version starts on a fresh
#  environment. But this practice may erase important settings)

sudo apt-get remove --purge nxclient nxnode nxserver


# Move into the folder where you have stored the latest nx packages
# to be installed. It is also easier to archive the whole folder
# for future reference.

cd Desktop/nx


# Install the downloaded packages

sudo dpkg -i nx*


# Done!

```

---

