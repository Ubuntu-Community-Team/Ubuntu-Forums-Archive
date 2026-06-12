---
title: "Quick question about NFSv4 ACLs"
date: 2013-08-21
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2013-08-21
I have a folder on my system where I want to make all newly created files and directories have specific permissions. I want newly created files to be set to 664 (instead of the umask's 644) and directories to be set to 775. Changing the umask will not work, because it is system wide (for each user anyway) - I just want this one folder and its subdirectories to be effected.

The best way I found to do this is to use NFSv4 ACLs. The thing is - I don't need any of the extended features that NFSv4 ACLs provide - I just want to be able to set all newly created files to 664 and folders to 775. Instead of going through every single flag of NFSv4 ACLs and figuring out what they all do, what I've done is this:

```
#Created a test file
$ touch testfile

#Wiped out all of its ACLs
$ sudo setfacl -b testfile

#Gave it regular permissions that I want all files to have
$ sudo chmod 664 testfile

#Checked what the ACLs were changed to
$ getfacl testfile[INDENT]# file: testfile
# owner: user
# group: user
            owner@:rw-p--aARWcCos:------:allow
            group@:rw-p--a-R-c--s:------:allow
         everyone@:r-----a-R-c--s:------:allow[/INDENT]

#Set the directory that I wanted to change to these permissions based on the previous command's output:
$ sudo setfacl -a0 owner@:rwpaARWcCos:fi:allow directory_in_question
$ sudo setfacl -a2 group@:rwpaRcs:fi:allow directory_in_question
$ sudo setfacl -a4 everyone@:raRcs:fi:allow directory_in_question

```

I did the same with a test folder, and used the "di" flags instead of "fi" on the ACLs. 

Am I right to assume that this is a good way to figure out the default mapping of chmod style permissions to NFSv4 ACLs?

---

### Post by TheFu on 2013-08-21
Have you considered changing the umask just for your ID?  Do this in the ~/.profile or ~/.bashrc.

**umask 002** should be it.

This should apply only to your userid and impact any Linux file system - including NFS mounts.

---

### Post by terminator14 on 2013-08-21
Like you said, this would change the permissions of every file and folder being created anywhere on the filesystem by that user - not just the NFS share that I'm looking to change. Also, not only would I have to do this for each user on every NFS client, but I would also have to do this for every root user on every NFS client. This would result in weakened security, system-wide, for every single system of every NFS client that connects to the server.

I already have the solution for how to do what I want - with ACLs. It works, and it works better than the umask way, as it only has to be done once, and only on the server. My question is specifically about figuring out which flags to use on the NFSv4 ACLs, and if I can just do what I did without figuring out what every NFSv4 flag does.

---

