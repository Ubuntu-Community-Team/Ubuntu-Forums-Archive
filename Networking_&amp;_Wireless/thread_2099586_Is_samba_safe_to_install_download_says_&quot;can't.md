---
title: "Is samba safe to install? download says &quot;can't be authenticated!&quot;"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by s1baker on 2012-12-29
Is samba safe to install?

 When I go to either the software center or synaptic to install, it says:
> 
 "you are about to install software that can't be authenticated! Doing this could allow a malicious individual to damage or take control of your system"

I installed samba on a machine maybe 6 months ago and I don't recall this message.

---

### Post by 2F4U on 2012-12-30
Samba from the default Ubuntu repositories is safe to install. Are you trying to install from a PPA? What is your mirror? Do you get the same message for other applications?

---

### Post by deadflowr on 2012-12-30
> **s1baker said:**
> Is samba safe to install?

 When I go to either the software center or synaptic to install, it says:


I installed samba on a machine maybe 6 months ago and I don't recall this message.

Do you have any added repos maybe? PPAs and the such.

If so, maybe open synaptic and look at versions in the properties of samba.Perhaps another repos/PPA has a newer version or something.

Myself, having recently installed samba, did not see this message.

---

### Post by s1baker on 2012-12-30
here is a png of the message I get when I try to install from the software center:

---

### Post by s1baker on 2012-12-30
~also, failed to mention, this is a relatively new install of Xubuntu, not an install of Ubuntu with Xubuntu installed on top of it. 12.04.01 LTS
64 bit install, so maybe there is some libaries I would have obtained with Ubuntu that I didn't get with Xubuntu? 

Here is two png's of software sources:

---

### Post by Elfy on 2012-12-30
From a terminal run

```
sudo apt-get update
```

should give you some idea of which repo you need to authenticate

---

### Post by s1baker on 2012-12-30
Thanks Elfy, I did sudo apt-get update, got a long list downloaded, and the install of samba went through smoothly.

---

