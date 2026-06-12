---
title: "can't do simple LAN network sharing files between two ubuntu pc's"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by ismailmarmoush on 2009-03-11
hi i've been all the week trying and reading installing samba and removing it .. 

all i need is to share files between two pc's they both use ubuntu same version

i tried shares-admin 
i tried samba sharing 
i tried nautilius sharing 

none is working .. the most common thing appears is :
i'm on pc-1 for ex  i go places-> network --> i see   pc-1 and pc-2 when i enter anyone of them i see  the pc-1 shared files .. 

i'm using 3-com router and built in lan devices 

plz help me .

---

### Post by cb951303 on 2009-03-11
between 2 linux computers it's advised to use NFS (although samba would work too)

for samba:

```
sudo tasksel
```
Check **Samba file server** and click <Ok> then

```

sudo apt-get install system-config-samba
```
Go to Menu > System > Admin > Samba

Configure it to your liking:popcorn:

---

### Post by ismailmarmoush on 2009-03-11
i tried my liking :D configuration and it didn't work in first place .. would you plz tell me the common configurations used in tht matter !

---

### Post by cb951303 on 2009-03-11
* I keep authentication mode as "Share" in Preferences > Settings > Security
* I check "Writable" and "Visible" for the shared directory
* Also I select "Allow access to everyone"

That should do the trick
BTW, to access the shared folders I use the remote computers IP directly like this "smb://192.168.1.111/"

---

