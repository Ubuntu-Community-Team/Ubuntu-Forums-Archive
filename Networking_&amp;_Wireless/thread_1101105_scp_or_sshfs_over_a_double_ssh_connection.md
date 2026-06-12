---
title: "scp or sshfs over a double ssh connection"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by JonJ678 on 2009-03-19
Hello. 
There are three computers involved, say A B C. A has access to B, B has access to C. A does not have access to C. 
Consequently, from A, I ssh into B. I then, from B, ssh into C. This much works excellently. 

However I cannot work out how to send files down this connection. I can sit in B and scp from C, then sit in A and scp from B, but this is untidy and limited by the available hard drive capacity of B which is approximately sod all. 

Ideally I would like to mount a directory in C onto A using sshfs, or be able to scp directly from C to A. I suspect the problem is my not knowing what command to use. 

Presently, from A, ssh jonj678@ip then entering password gets me to B
Then, from B, ssh -p port jonj678@ip then entering a different password gets me to C.

How do I combine these into a single line in order to adapt it for scp/sshfs/freenx? I think the answer lies in | but I don't know how to use it

I hope that's coherent :)

edit: i suspect this would be easier if I didn't need the -p option

---

### Post by Jose Catre-Vandis on 2009-03-20
Yep, you probably need to enable password access to B from A and C from B to allow a command to apss right through. You can do this securely (see [here]("http://ubuntuforums.org/showthread.php?t=728643"))

Then you should be able to figure out the command you need to run.

You may also need to edit your sudoers file to allow the user on B to action sudo commands without a password! (see [here]("http://napkins.wordpress.com/2009/02/18/using-nopasswd-in-sudoers-on-ubuntu/"))

So for example to login into B from A and mount a directory from C
```
ssh user@B 'sudo mount ...etc'
```
(mount will depend on how you are sharing C)

Hopefully this should get you started, I am not an expert at this!

---

### Post by Jose Catre-Vandis on 2009-03-20
I have had a further play with this and can see that if SSH without a password is enabled on both B and C you should be able to mount a directory on A from C with either a single line or a simple script. (I haven't been able to fully test as no time to set up passwordlessness on all machines here).

Commands required:

1. shh into B then mount a directory from C onto B using sshfs
```
ssh user@B 'sshfs user@C:/directorytomountinC  /mountpointonB'
```
2.Mount that directory (mountpointonB) on A using sshfs
```
sshfs user@C:/directorytomountinB  /mountpointonA
```

(I mounted in my home directories for this test to avoid sudo / password /permissions issues)

To reverse all this you need to run similar command but using:
```
fusermount -u /mountpoint
``` to unmount the directories

---

### Post by rdgraham on 2011-03-30
I usually do this with port forwarding. I.e. if machines are 'bridge' and 'remote' in a terminal

ssh -C bridgeuser@bridge -L 8081:remote:22

enter password for the bridge machine. Leave this terminal open. Note that you can use any convenient port on the local machine, here I used 8081.

Now on your local machine you can ssh/sshfs or use the gnome 'connect to server' and connect to localhost on port 8081 which will actually be the remote machine.

---

