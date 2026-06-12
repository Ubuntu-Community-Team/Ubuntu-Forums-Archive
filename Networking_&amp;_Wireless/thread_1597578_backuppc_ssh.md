---
title: "backuppc ssh"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by sidestrand on 2010-10-15
About a year ago I installed BackupPC on a flashed Linkstation (Freelink).  It works wonders backing the family Windows machines, but I cannot get it to talk to my Ubuntu laptop.

The problem seems to be with SSH.  I can SSH to the Linkstation from my laptop no problem  I can SSH to the laptop from Root on the Linkstation, but I cannot SSH to the laptop from the Linkstation as either user Me or user BackupPC.  In both user instances I get the message 'Host key verification failed'.

I've tried all the advice I've found on the web, including deleting my keys and preparing new ones.

I'm really stumped.  I feel that it may have something to do with Ubuntu not having a root password, but I may be wrong.

This is very frustrating!  Any ideas gratefully received.

---

### Post by n5wy on 2010-10-21
There is an article in a recent linux magazine I just read about setting up BackupPC. It mentions a technique for preventing the sort of problem you describe. I do not have the article handy, or I would look it up for you. 

As I recall, it said to generate a ssh keypair for the user backuppc, install the keypair on the relevant client/server machines, and if you have a linux client it may be necessarry to add the 'backuppc' userid to the Sudoers file. This way, the ssh connection can authenticate (using the backuppc userid ssh keypair), then the machine will give sudo permission to the backuppc userid to traverse directories and read/write files from the places that a normal (not-root) user can't go.

Perrhaps try using the ssh keygen command to generate a keypair for backuppc (the default backuppc UID) and then use the documented procedure for modifying the sudoers file (visudo) and adding an entry there for the backuppc UID to have root access without a password. 

Hope this gets you in the right direction.

---

### Post by n5wy on 2010-10-21
I found it. It was published in _*Linux Format Special Edition "Master Linux Now"*_ 

To summarize, it says that since rsync uses SSH to grant access to backuppc user on the server, then permission will be required to read anything other that the home directory files or files owned by backuppc.

Generate a keypair for the backuppc user on the server with:
```
su -s /bin/sh -c "ssh-keygen -t rsa" backuppc
```

This makes a keypair for the UID backuppc. The first part is needed since backuppc does not have a shell defined by default. The resulting output of this is a keypair that is plopped into the folder [B]/var/lib/Backuppc/.ssh

[/B]The next step would be to copy the public part of the keypair to a USB stick and move it to the client pc you are trying to backup to the server pc. You should have already created ssh keypairs for the root users of the client and server machines. Copy the keypair for backuppc from the USB stick to the client pc with this:
```
cat /media/usbstick/id_rsa.pub >> /root/.ssh/authorized_keys
```

The rest of the article goes into further detail on the various setup options in the config files for fine tuning Backuppc. I intend to give it a try myself as soon as I can get to it. 

JAR

---

