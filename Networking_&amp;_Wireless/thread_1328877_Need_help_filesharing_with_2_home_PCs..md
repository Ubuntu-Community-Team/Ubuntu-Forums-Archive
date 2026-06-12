---
title: "Need help filesharing with 2 home PCs."
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by jessiebrownjr on 2009-11-16
Howdy folks! I have a Desktop thats hardwired into my router. Its running Ubuntu 9.04 gnome. My laptop is wirelessly connected to the same network, running same OS. How do I set up firesharing between the two? I haven't found an easy how to or one that didn't confuse me, so any help is appreciated.

---

### Post by dmizer on 2009-11-16
Please see the 4th link in my sig.

Note: if you want both machines to be able to host and view shares, you'll have to set both machines up as both a server and a client.

---

### Post by jessiebrownjr on 2009-11-17
> **dmizer said:**
> Please see the 4th link in my sig.

Note: if you want both machines to be able to host and view shares, you'll have to set both machines up as both a server and a client.

OK, following the tutorial...
my desktop is now exporting the directory i want to be able to share with full read write access (im assuming) my laptop is also exporting, with read only. checked it on the opposing PC.

Ok that being said, I still am getting access denied. Is there an access list etc im supposed to be setting up? Looking on the internet on various distros, kinda confused.
```

jessie@ubntu:~$ exportfs -a
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export "192.168.0.100:/home/jessie/laptopmnt".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: could not open /var/lib/nfs/etab for locking
exportfs: can't lock /var/lib/nfs/etab for writing
```When I typed showmount -e desktopiphere, it showed my directory i wanted.

How do I get them to be both like you edited?

---

### Post by dmizer on 2009-11-17
> **jessiebrownjr said:**
> Ok that being said, I still am getting access denied. Is there an access list etc im supposed to be setting up? Looking on the internet on various distros, kinda confused.

Are you getting access denied from both computers?

If so, make sure you've entered the correct IP range in the /etc/exports file. If you don't know your IP address, you can check it by looking at the output of:
```
ifconfig
```

---

### Post by jessiebrownjr on 2009-11-18
> **dmizer said:**
> Are you getting access denied from both computers?

If so, make sure you've entered the correct IP range in the /etc/exports file. If you don't know your IP address, you can check it by looking at the output of:
```
ifconfig
```

hey thanks for the help. On my desktop, I was able to mount my laptop's share today, however, on my laptop, I got access denied trying to mount a share that was housed on the desktop. Ill try to make all the files mimmic each other later.. Is there something I can do to allow all local IPS?


Some questions.. is there a way to remotely end all people mounted to you, to not cause any system error client side if the server goes down?
Laptop=server, desktop = client today. I turned off the server, client went wonkey, wouldn't let me unmount, had to reboot client.

---

### Post by dmizer on 2009-11-18
The howto shows you how to share files to all local IPs. If you need more help, you'll need to post some information like:

Your server's current /etc/exports file,
Your client's current /etc/fstab file
And the output of: ifconfig

---

### Post by jessiebrownjr on 2009-11-21
> **dmizer said:**
> The howto shows you how to share files to all local IPs. If you need more help, you'll need to post some information like:

Your server's current /etc/exports file,
Your client's current /etc/fstab file
And the output of: ifconfig
what is the importance of fstab?

---

### Post by sahabcse on 2009-11-21
fstab is used for permanently mount the devices. eg)nfs share, samba share, hardish partition etc.

for more info #man fstab

---

### Post by dmizer on 2009-11-21
> **jessiebrownjr said:**
> what is the importance of fstab?
Well, I assumed you were mounting the share with a permanent reference in /etc/fstab rather than using a manual mount command every time you wanted to access the share. If you're only using a manual mount command directly from the command line, then I'll need to see the command you used to mount the share instead of needing to see /etc/fstab

---

