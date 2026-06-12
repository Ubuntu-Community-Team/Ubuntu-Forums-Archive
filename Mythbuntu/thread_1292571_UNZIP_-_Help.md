---
title: "UNZIP - Help"
date: 2009-10-16
forum: Mythbuntu
---

### Post by Kevin Chapman on 2009-10-16
:( Hope someone can help me, I'm new to linux and I've downloaded the files for my Hauppauge HVR-2200 card which I was hoping to get working on Mythbuntu. When I go to install them from the terminal using 'sh extract.sh' I get an error saying:
 
Unzip: not found
 
 I followed a thread on the forum that said to use 'apt-get install unzip' but I get a message back saying:
 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 
 
What am I doing wrong here?

---

### Post by vinutux on 2009-10-16
> **Kevin Chapman said:**
> :( Hope someone can help me, I'm new to linux and I've downloaded the files for my Hauppauge HVR-2200 card which I was hoping to get working on Mythbuntu. When I go to install them from the terminal using 'sh extract.sh' I get an error saying:
 
Unzip: not found
 
 I followed a thread on the forum that said to use 'apt-get install unzip' but I get a message back saying:
 
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 


 
What am I doing wrong here?

if you are using root/admin account go back to nomal account first..........

1. close any aptfront-ends working now first like synaptic, update manager or add/remove....

2. add sudo infont of your cammand ```
sudo apt-get install unzip
```

---

### Post by Kevin Chapman on 2009-10-17
Vinutux, thanks very much for your reply, I did have 'sudo apt-get install unzip' just left the sudo off, sorry re that.
 
Rebooted machine and ran 'sudo apt-get install unzip' now I get : 'cannot find unzip'. This was my problem originally before playing around in Linux and getting the other error. 
 
Any help would be appreciated as I am a novice with this, also I have noticed other users posting a similar problem on other forums but have not found a satisfactory answer.
 
Kevin

---

### Post by vinutux on 2009-10-17
System -> Administration -> Synaptic package manager 

Seach for unzip .... Right click mark for installation > apply and install

---

### Post by Kevin Chapman on 2009-10-18
Thanks for all your help Vinutux,
 
That worked, now I have another problem with the headers but I'll research before creating another thread
 
Kevin

---

