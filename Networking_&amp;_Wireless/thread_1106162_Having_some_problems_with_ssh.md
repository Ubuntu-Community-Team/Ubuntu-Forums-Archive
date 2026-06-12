---
title: "Having some problems with ssh"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by B4RR13N705 on 2009-03-25
Hi, im new on this forum and i use ubuntu Hardy on my desktop. Im having some problems with ssh. I want to connect to another pc. ssh comes installed with ubuntu. I tried to connect to myself ip

ssh 190.224.72.12

And i only get

ssh: connect to host 190.224.72.12 port 22: Connection refused

I am new on this remote connection and i dont know what to do, i checked on System, Services and ssh is activated. Maybe i need to install another package? or is a port problem? Please help me!
Thanx! :guitar:

---

### Post by Slim Odds on 2009-03-25
The format is:```
ssh username@host
```

You need a username.

---

### Post by B4RR13N705 on 2009-03-25
I just tried that command, i created a new user called guest so i did
> 
ssh guest@190.224.72.12

And i get de same stuff
> 
ssh: connect to host 190.224.72.12 port 22: Connection refused

Only 1 thing, when you say that i have to create a new user, do you mean create a new user on my pc? cuz i do that and i get the same!
Sorry but its my first time :)

---

### Post by Slim Odds on 2009-03-25
Is the ssh server running on the remote machine?

---

### Post by B4RR13N705 on 2009-03-25
I think is not, whats the name of the package? so i check it with synaptic. If it is not, i just installed it and it should work right?

---

### Post by kpatz on 2009-03-25
You'll need to install openssh-server on the remote machine (the one you're trying to connect TO, 190.224.72.12).

The ssh client comes ready to go in an ubuntu install but not the server.

---

### Post by B4RR13N705 on 2009-03-25
I installed the package!
But i get the same error :confused:
Notice that i want to connect to myself remotely, can i do that? maybe thats why i cant connect. I will try to connect to another pc! :popcorn:

---

### Post by Slim Odds on 2009-03-25
Since you are connecting to a remote machine, you have to connect to any account that exists on **that** machine.

---

### Post by BkkBonanza on 2009-03-25
Once you have openssh-server installed check with

netstat -ln

that there is a line indicating that sshd is listening on 127.0.0.1:22
If not then also check with,

ps ax

that sshd is running. If not then you will need to start it manually. I think it should have been started for you though. 

You get the message connection refused port 22 typically when nothing is there listening.

---

### Post by Bachstelze on 2009-03-25
@B4RR13N705 > where exactly are you now, and where is the machine you're trying to connect to?

---

### Post by B4RR13N705 on 2009-03-25
Hey! i put the command that you told me
```

netstat -ln

```
And it prints a los of stuff
One line prints this
```

unix  2      [ ACC ]     FLUJO      ESCUCHANDO    15281    /tmp/keyring-NjcaOf/ssh

```
I also try
```

ps ax

```
and i get
```

 6134 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/seahorse-agent --execute x-session-manager

```
And this one:
```

 7910 ?        Ss     0:00 /usr/sbin/sshd

```
I think that is running correctly, i dont know why i cant connect!
To the staff member:
Im in my home and im tryng to connect to my OWN desktop just for learning ssh and have some experience on it.

---

### Post by BkkBonanza on 2009-03-25
Looks like sshd is running. On your netstat output it's the lines at the top starting with tcp that matter. Scroll back and view those looking for one on port 22.

I've never heard of anyone ssh into their own machine. Not sure if it works or not. Don't see why not, I guess.

---

### Post by B4RR13N705 on 2009-03-25
I have checked in google, and it seems that you cant connect to your own machine, anyway, i will try as soon as possible to connect to a friend pc or something to check and the i tell you!
Thanx 4 everything!

---

