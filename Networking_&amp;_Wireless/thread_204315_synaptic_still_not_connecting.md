---
title: "synaptic still not connecting"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by mighk on 2006-06-26
Hi all 
i have one xp box connected to net, lubuntu box connecting through eth0
i can browse with firefox on ubuntu but can't use synaptic, 
i have edited bashrc as suggested
tried other fixes suggested 
checked and rechecked my proxy settings, If i use the local address of xp box or the server address of my isp , still no difference. suggestions please?
thanks
mighk

---

### Post by tonyr on 2006-06-26
What happens when you try to use Synaptic?

---

### Post by mighk on 2006-06-27
Synaptic refuses all connections with the isp, error message, 
Could not download all repository indexes ................
could not connect to 196.38.72.9 : 8080
can ping above address 
changed network pref. in synaptic to the network address from ipconfig on my Xp box, but synaptic still uses above address
Looked at starter guide but can't find what i need 
Is there a log file i can access that will give me aclearer picture ? 
thanks. 
mighk

---

### Post by mighk on 2006-06-27
more error messages from synaptic
apache2: could not determine servers fuilly qualified domain name, using 127.0.0.1 for servername
Where can i edit this and what do i ediot it with ?
thanks mighk

---

### Post by tonyr on 2006-06-28
On my machine, I have not changed any of the default settings for Synaptic. 
In Synaptin under Settings->Preferences->Network I have selected
**Direct connection to the internet**, and have had no problem
with Synaptic connecting to repositories.

I'm not sure what you are talking about when you say you have made suggested fixes
and changes to bashrc, since I have not had to do anything like that.

Have you talked to the people at your ISP?  They may be blocking some things.

---

### Post by mighk on 2006-06-28
Thanks 
tried in preferences to set network as direct connection
still no joy
get the following after sudo apt-get -f install
apache2: could not determiine the servers fully qualified domain name, using 127.0.0.1 ('which i think is the loopback address')

i also get a  "could not resolve "ipaddress"" after trying synaptic again

thanks
 mighk
is there a way i can reinstall synaptic to get the settings back to default ?

---

### Post by m_pav on 2006-06-28
see this thread.

[http://ubuntuforums.org/showthread.php?p=1182547#post1182547](http://ubuntuforums.org/showthread.php?p=1182547#post1182547)

---

