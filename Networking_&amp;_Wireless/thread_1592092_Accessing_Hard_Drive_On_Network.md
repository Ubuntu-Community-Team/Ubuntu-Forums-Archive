---
title: "Accessing Hard Drive On Network?"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-10
I have a network where several machines are connected through a switch. I'd like all machines to be able to read/write to/from the hard drives of the other machines.  for example:

machine1 will read/write files that are on the hard drive of machine2
machine2 will read/write files that are on the hard drive of machine1
machine3 will read/write files that are on the hard drive of machine1
machine3 will read/write files that are on the hard drive of machine2
etc etc...

all of this reading/writing will be done through the terminal, and programatically. rather than SSHing into a machine to read/write files from it, I'd be happy to set up some 'conventions' on how to access hard drives of various machines. for example:

'hdd1' will refer to the hard drive of machine1 (that has the static IP of 192.168.0.1). 
'hdd2' will refer to the hard drive of machine1 (that has the static IP of 192.168.0.2). 
'hdd3' will refer to the hard drive of machine1 (that has the static IP of 192.168.0.3). 
etc etc...


this way, when I want to read/write a file, its PATH will be something like ~/hdd1/myfile.txt;  ~/hdd2/anotherfile.txt; 

the question is, how do I achieve this?

thanks in advance!

---

### Post by SeijiSensei on 2010-10-10
If they're all Linux machines, use NFS.  If some are running Windows, you'll need to run Samba.

From a security and reliability perspective, you really don't want to expose the entire directory tree of each machine to all the other machines.  Create specific directories to hold the shared material.

---

### Post by csharpplus on 2010-10-10
Thanks for your reply.

> If they're all Linux machines, use NFS
All machines are with Ubuntu 10.04; How do I know if I use NFS? (what is the default when installing the Ubuntu CD)?

> From a security and reliability perspective, you really don't want to  expose the entire directory tree of each machine to all the other  machines.  Create specific directories to hold the shared material. 	
Suppose I created a directory on 'machine1'. how do I expose it to the other machines?  how do I access it from the terminal of another machine?

also, would it help at all to associate all machines with the same group? does it simplify things?

thank you.

---

### Post by SeijiSensei on 2010-10-10
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889) 

is a good place to start.

---

### Post by csharpplus on 2010-10-10
Thanks! I appreciate your help.

---

