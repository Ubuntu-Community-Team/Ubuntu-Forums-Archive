---
title: "Karmic: Mounts with SMB:// not showing up in all nautilus windows"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by Mriswithe on 2009-11-25
I did some searching and couldn't find anything that addressed this, so here goes: 

I usually mount shares on other local computers, both windows and linux flavors, by entering "smb://192.168.0.5" to mount them and get to them. In 9.04 when I did this it would pop on my desktop as well as in nautilus and such. Now in karmic it is appearing in the "Places" area of nautilus as well as my desktop like it used to, but the only thing different is when I go to select a download location with something like downthemall it is not seeing the mount in the links to the left. I can't find it anywhere so that I can do a direct dump to the networked computer. 

I am on a clean install of 9.10 and have had very few other problems with karmic, anyone have an idea of what changed or if this is a known issue? 


Thank you for your help,

Mriswithe

---

### Post by Mriswithe on 2009-12-07
Am I not providing some piece of information that is required to know what I am talking about or is it something that no one really knows?

Mriswithe

---

### Post by fedgel on 2010-01-07
Hi

Just came across nautilus being unable to recognise smb:// location.
I solved by installing smbfs.
Either look for it in synaptic or
on the command line:
sudo apt-get install smbfs

---

