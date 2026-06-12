---
title: "External Folder Sharing"
date: 2011-05-21
forum: Networking &amp; Wireless
---

### Post by annirun on 2011-05-21
I want to make one of my folders on my laptop with Ubuntu 11.04 accessible externally (like from school or a friend's house) on windows.  I know how to use SAMBA to make it accessible internally with \\internal ip address\folder name\ and how to do port forwarding but don't know what to put for TCP or even if that is the way to do this. How do I set up the external access?

---

### Post by OM NOM NOM on 2011-05-21
In order to get external file share access security, try SFTP (Secure File Transfer Protocol)

First, install Openssh on the computer you wish to share files FROM:

```
sudo apt-get install openssh 
```Open SSH will by default install an SSH and SFTP server onto your machine. 

SSH/SFTP by default runs over port 22, so you'll want to do some port forwarding from your router to port 22. Port 22 gets scanned a lot so you won't want to directly open it up on your router. 

Your port forwarding rule should look something like this:

inbound WAN TCP (some high number of your choosing -> Lan TCP port 22.

Now go get yourself a free Dynamic DNS address at dyndns.org or somewhere similar. Create an account, then go back into your router and tell it your accout info and DYndns address.

On your remote client machine, install Filezilla:

```
sudo apt-get install filezilla
```You will need to have partner repositories checked ON in Synaptic Package Manager to get it. 

In Filezilla, create a new remote site. Fill it in with your Dynamic DNS address and external port number, choose username/password authentication and voila! secure remote access!

Once you log in, you'll a bunch of hidden directories with a "."extension before them. If you want to hide them, go to View -> filename filters in enable them in Filezilla. Then you'll only see you normal directories within your home folder.

Good luck!

---

### Post by annirun on 2011-05-22
Thanks for your help.  I was hoping I could find a way to access them without installing something like filezilla on the client and just rune the run line like i can internally but oh well.

---

