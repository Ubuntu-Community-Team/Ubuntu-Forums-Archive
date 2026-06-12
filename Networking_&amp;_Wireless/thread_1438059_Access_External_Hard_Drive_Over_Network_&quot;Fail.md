---
title: "Access External Hard Drive Over Network &quot;Failed to Mount Location&quot;"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by doogiekd on 2010-03-24
dear friends, 

i have one desktop computer that has a large external hard drive attached.

there are files on the external hard drive that i want to share over the network - the network consists of all ubuntu machines.

when attempting to access those share enabled files from another computer over the network, i get the following error message:

"Unable to Mount Location. Failed to Mount Windows Share."

note that all the other three machines are sharing files without any problems. also, note that when i create a share folder on the primary (internal) hard drive of the computer connected to the external hard drive, other computers can access the files without any problem.

something is preventing the external hard drive from being mounted when accessed from another computer over the network. i have also tried sharing the entire external hard drive, but the problem continues.

any solutions to this problem?

thank you, 

doogiekd

---

### Post by johnson.d on 2010-03-26
You can use the manual method of mounting and sharing of the external drive from the Ubuntu machine. You can use the following procedure.

1) Remove the share and unmount the drive in Nautilus.

2) **Mount the external drive manually**:

The external drive can be mounted using the following command:

```
$ sudo mount -t <file-system> /dev/< dev-file eg:sdb1,sdb2> /<mount-point>
```

3) **Sharing the drive through Samba**:

You need to the edit /etc/samba/smb.conf file and add the following lines to it.

```
[<share-name>]
path = /<mount-point>
browseable = yes
read only = no
guest ok = yes
```

Now restart the Samba service using the following command:

```
$ sudo /etc/init.d/samba restart
```

After restarting the service you can browse and access the share from Windows or a Linux machine.

---

