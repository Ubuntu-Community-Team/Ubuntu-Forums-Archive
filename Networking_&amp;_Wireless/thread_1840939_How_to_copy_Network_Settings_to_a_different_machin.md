---
title: "How to copy Network Settings to a different machine"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by ajmctaggart on 2011-09-08
Hi all,

I have 30 Netbooks (+1 for my testing) used in our company for Academic Tutoring.

I rolled a customized version of 10.04 LTS running standard Gnome on my netbook, and used Clonezilla to copy this to the other 30.

One "small" (huge) mistake I made was that when I cloned the machines, I had not setup the 6 different wireless networks that these netbooks will be connecting to (5 locations in which these netbooks will be used so 5 SSIDs + 1 backup wifi router in case one goes down).

Now, I could enter SSIDs and (VERY Long) passphrases 180 times, but who the heak wants to do that?  

The name of each machine is different ~ acer1 acer2 etc...but other than that the systems are identical.  I manually went into each machine and changed the name in /etc/hostname and /etc/network/hosts.

Also, there is no encryption key for wireless networks (I had to agree on the test unit to store the networks in this insecure manner).

The 6 routers are setup using WPA2 with AES.

Is there a way to input these 6 networks on MY test netbook, and then copy them over to each netbook to save the effort of 180x with SSIDs and passphrases?

Please say there is...otherwise it's going to be a long long weekend, haha...

---

### Post by RyanRahl on 2011-09-08
Your connections settings are stored here:

/home/<user>/.gconf/system/networking/connections

to get it done as quickly as possible I would set them all up and put the connection info on a server and use rsync to transfer all of the data.

---

### Post by ajmctaggart on 2011-09-08
Thanks RyanRahl!

Do you foresee any issues since the machines are named differently?

---

### Post by RyanRahl on 2011-09-08
It should be fine, all that the folder contains is xml descriptions of your Netowork Manager connection entries with the text fields, dropdown menus and check boxes having respective data.

---

### Post by ajmctaggart on 2011-09-08
Sounds like EXACTLY what I was hoping for - Thanks!

---

### Post by ajmctaggart on 2011-09-12
I was able to move the ".gconf/system/networking" via flash drive, but it prompts for password for the network.  

Any idea where my Keyring is stored?

Thanks for your help!

---

