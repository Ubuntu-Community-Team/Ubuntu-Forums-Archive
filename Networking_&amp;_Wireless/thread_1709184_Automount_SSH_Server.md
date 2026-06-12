---
title: "Automount SSH Server"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by mauro24 on 2011-03-17
I wonder how to set my computer to connect to a server on start up.  I hate to reload my pictures in shotwell every start up.  I can connect through ssh connection, but i want it done automatically on start up.  I'm not an expert, so break it barny style, or link me to a guide that i haven't found yet. Thanks.

Ubuntu 10.10 64Bit

---

### Post by joberly on 2011-03-17
Well, you can start [here]("http://www.debianadmin.com/mount-a-remote-file-system-through-ssh-using-sshfs.html") by using sshfs. Then, you can put the command (however you utilize it) in /etc/rc.local


Is this on a local network?

---

### Post by mauro24 on 2011-03-17
Yes it is a local network, my server is running ubuntu 10.10 32 bit.  Thanks for the link, but the  article was written about 4 years ago, and the example they showed in there didn't help in my limited linux knowledge.  I would like something more recent and that can show examples, and believe me I've tried to google, but maybe I don't know what i'm looking for.  
I just want let's say my computer on start up to mount the external hard drive that is attached to my server. I hope I explained myself.  thanks

---

### Post by BkkBonanza on 2011-03-18
How are you mounting the drive now when you do it manually?

---

### Post by mauro24 on 2011-03-18
When I want to use the files in that external hdd i use Connect to Server using SSH.  I can do that fine, but i don't want to do that manually anymore.  I don't use samba because is slow.

---

### Post by joberly on 2011-03-18
> **mauro24 said:**
> Yes it is a local network, my server is running ubuntu 10.10 32 bit.  Thanks for the link, but the  article was written about 4 years ago, and the example they showed in there didn't help in my limited linux knowledge.  I would like something more recent and that can show examples, and believe me I've tried to google, but maybe I don't know what i'm looking for.  
I just want let's say my computer on start up to mount the external hard drive that is attached to my server. I hope I explained myself.  thanks

Well, the article I linked to does work. If you'd rather not try, then that's your call. They DO give an example of how to mount the filesystem through sshfs. You simply take the command and add it to the file /etc/rc.local

Anyway, the question BkkBonanza asked about how you are mounting the external drive is needed if we are going to help you further. I'm assuming your 'server' has a GUI and it is simply recognising the external drive on its' own, and you are not mounting it through fstab?

---

### Post by matt_symes on 2011-03-18
Hi

Well here is a newer example from help.ubuntu.com (last edited 2010-12-28 ). It's a step by step example.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Please don't be rude to people trying to help you :(

Kind regards

---

### Post by mauro24 on 2011-03-18
create the mount point

#mkdir /mnt/remote

#chown [user-name]:[group-name] /mnt/remote/

Add yourself to the fuse group

adduser [your-user] fuse

switch to your user and mount the remote filesystem.

sshfs [email]remote-user@remote.server[/email]:/remote/directory /mnt/remote/

If you want to mount a directory other than the home directory, you can specify it after the colon. Actually, a generic sshfs command looks like this:

$ sshfs [user@]host:[dir] mountpoint [options]

Ok I'm going to show what i understood from this example, this example is going to help me mount that external hard drive automatically after every start up.
Server local ip 192.168.0.5
my computer 192.168.0.3
and external hdd is @ server/media/Backup

so first i need to mount the home directory of the user@host

#sshfs 192.168.0.3@192.168.0.5: /media/Backup

when i do this, it asks for the server password i assume, i add it three time and i get this

read: Connection reset by peer

so now i'm going to follow the example, everything is done in my computer I assume

#sudo mkdir /mnt/remote
#sudo chown 192.168.0.3:fuse-group /mnt/remote/

I don't know what they mean by group name, is it the servers ip or just any name i used fuse-group and it came back with invalid user name, that's what i'm saying the example is lame, I just understand half of it I think?

also on the username part is it the ip address or just the name of the computer user?

---

### Post by mauro24 on 2011-03-18
> **matt_symes said:**
> Hi

Well here is a newer example from help.ubuntu.com (last edited 2010-12-28 ). It's a step by step example.

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

Please don't be rude to people trying to help you :(

Kind regards
thanks matt i'm going to try that.

---

### Post by mauro24 on 2011-03-18
Ok matt thanks for link, but I already can connect to the server using Connect to Server through SSH.  But What I want to do is get it so it does it automatically on my computer boots up.

---

### Post by mauro24 on 2011-03-18
Ok let's start from fresh.  To solve the issue i have with Shotwell and Banshe that i have to import the pictures and music everytime i start the programs is to mount the hard drive with the files before i start the mentioned programs.  That solves my  problem, it's not big deal because i have bookmark for the mount, so I don't have to go to Connect to Sever and add all the information everytime.  so that solves my problem.

Now back to the second problem.  If it is posible, it would be nice that my computer could mount that hard drive on my server when my computer starts up.  Not being lazy, just fun to know how to do that:P

---

### Post by matt_symes on 2011-03-18
Hi

I am actually trying to set this up myself. I have been meaning to do this for a little while.

On my server i have openssh-server installed, with key authentication and a non default ssh port.

My client has sshfs installed and i can mount it using

```
sshfs -p 2222 -o idmap=user matthew@192.168.1.99:/mnt/storage ~/sshfs_server
```

and unmount with

```
fusermount -u ~/sshfs_server
```

However my entry in /etc/fstab is not working

```
sshfs#matthew@192.168.1.99:/mnt/storage /home/matthew/sshfs_server fuse defaults,idmap=user,port=2222 0 0
```

I think this may be due to my wireless connection connecting after trying to mount the file system.

If i can fix it i will tell you how.

Kind regards

---

### Post by BkkBonanza on 2011-03-18
When you use the Connect to Server in Nautilus it actualy uses "sftp over ssh". sftp doesn't have an ability to mount on the filesystem but involves a series of commands that Nautilus executes to provide a list and management functions. Using a bookmark is the simplest approach here as outside Nautilus (or another sftp ready program) there isn't a method for mounting.

I think the closest approach to sftp is using sshfs to mount a remote location on the filesystem. This is generally a single command (once the initial fuse and user/group stuff is configured) that can be placed in the /etc/rc.local file (this is a script that is run during the boot process).

The user:group values mentioned in a post above are simply the user and group that the mount point should be given for permissions. Typically you would just use your own user for both values but it could vary depending on the situation.

You make a mount point and set it's ownership so you can access it with,

sudo mkdir /mnt/remote
sudo chown me:me /mnt/remote
(where me is your user name)
(this makes the mount point *yours* so you can use it)

First test this mount command and if it works then you would add the mount command into the /etc/rc.local file,

sshfs user@server:/path/to/location /mnt/remote
(where user is the user name you usually use to login to the remote server)
(same as you would use in Nautilus)

(really what this does is open an ssh session with the server and run a fuse based program that does the sftp commands to emulate a mounted filesystem that appears transparently on your filesystem)

To have this work at boot you would need to set up ssh to work with a key instead of password. Well, you could code a password into the login but that's less secure since it is visible in /etc/rc.local. Using a key isn't hard but is an extra step of setup to avoid being prompted during booting.

---

### Post by BkkBonanza on 2011-03-18
Matt,
You may want to try using the sshfs command as a post-up script in the interfaces file. It allows a script to be run after the interface is up and has an IP (presumably from the wifi AP using DHCP). That may work.

eg.
in the suitable section,

post-up sshfs ...etc...  || true

(the true bit makes it not clobber the interface if it fails)

---

### Post by matt_symes on 2011-03-18
Hi

> **BkkBonanza said:**
> Matt,
You may want to try using the sshfs command as a post-up script in the interfaces file. It allows a script to be run after the interface is up and has an IP (presumably from the wifi AP using DHCP). That may work.

eg.
in the suitable section,

post-up sshfs ...etc...  || true

(the true bit makes it not clobber the interface if it fails)

@BkkBonanza. Cheers for the heads up on this one. That was a good explanation.

My problems was my wireless interface was not up when trying to mount the sshfs from fstab at start up. This was confirmed by choosing the manual recovery option and then checking with ifconfig. (I also had a problem with root not having my keys)

Was able to set it up manually in fstab but not automatically at startup. ie mount ~/sshfs_server.

Thanks for the work around. Saves me having to think. :KS I will try it soon.

Hopefully this will help others.

Kind regards

---

### Post by mauro24 on 2011-03-18
> **BkkBonanza said:**
> When you use the Connect to Server in Nautilus it actualy uses "sftp over ssh". sftp doesn't have an ability to mount on the filesystem but involves a series of commands that Nautilus executes to provide a list and management functions. Using a bookmark is the simplest approach here as outside Nautilus (or another sftp ready program) there isn't a method for mounting.

I think the closest approach to sftp is using sshfs to mount a remote location on the filesystem. This is generally a single command (once the initial fuse and user/group stuff is configured) that can be placed in the /etc/rc.local file (this is a script that is run during the boot process).

The user:group values mentioned in a post above are simply the user and group that the mount point should be given for permissions. Typically you would just use your own user for both values but it could vary depending on the situation.

You make a mount point and set it's ownership so you can access it with,

sudo mkdir /mnt/remote
sudo chown me:me /mnt/remote
(where me is your user name)
(this makes the mount point *yours* so you can use it)

First test this mount command and if it works then you would add the mount command into the /etc/rc.local file,

sshfs user@server:/path/to/location /mnt/remote
(where user is the user name you usually use to login to the remote server)
(same as you would use in Nautilus)

(really what this does is open an ssh session with the server and run a fuse based program that does the sftp commands to emulate a mounted filesystem that appears transparently on your filesystem)

To have this work at boot you would need to set up ssh to work with a key instead of password. Well, you could code a password into the login but that's less secure since it is visible in /etc/rc.local. Using a key isn't hard but is an extra step of setup to avoid being prompted during booting.
this is what I did based on your example


mauricio@Ely:~$ sudo mkdir /mnt/remote
[sudo] password for mauricio: 
mkdir: cannot create directory `/mnt/remote': File exists
mauricio@Ely:~$ sudo chown mauricio:mauricio /mnt/remote
mauricio@Ely:~$ sshfs mauricio@192.168.0.5:/media/Backup /mnt/remote
mauricio@192.168.0.5's password: 
mauricio@192.168.0.5's password: 
mauricio@192.168.0.5's password: 
read: Connection reset by peer

Everything went fine until they ask for a password, I used my computer and my server password but both didn't work.  Did i do anything wrong?

---

### Post by BkkBonanza on 2011-03-18
Verify that you can ssh normally to that server. 
eg.
ssh mauricio@192.168.0.5

I'm not sure why it asks 3 times for a password. I don't recall it doing that when I used it before. Unless the password is wrong and it's retrying.

---

### Post by mauro24 on 2011-03-18
> **BkkBonanza said:**
> Verify that you can ssh normally to that server. 
eg.
ssh mauricio@192.168.0.5

I'm not sure why it asks 3 times for a password. I don't recall it doing that when I used it before. Unless the password is wrong and it's retrying.
I don't know what password to use, i used both my computer password and the server password and they didn't work

mauricio@Ely:~$ ssh mauricio@192.168.0.5
mauricio@192.168.0.5's password: 
Permission denied, please try again.
mauricio@192.168.0.5's password: 
Permission denied, please try again.
mauricio@192.168.0.5's password: 
Permission denied (publickey,password).

i assume is the same password i used to connect to the server manually through sftp the first time.

---

### Post by BkkBonanza on 2011-03-18
Yes, it should be the same password. It should be the one for the mauricio account on that machine, the same one you would login with at the console screen.

Are you sure the user name on that server is mauricio? Other than that you'll have to resolve that problem before tackling the sshfs one.

Try again with Nautilus - presumably that shouldn't work either if the password is wrong.

---

### Post by matt_symes on 2011-03-18
Hi

> I don't know what password to use, i used both my computer password and the server password and they didn't work

It should be the same password you use to log on to the server as your user.

Can you logon to the server with that password directly ? Have you forgotten the password and need to reset it ?

Kind regards

---

### Post by mauro24 on 2011-03-18
Now i'm a little confused, when i'm doing 
sudo mkdir /mnt/remote
sudo chown me:me /mnt/remote
am i doing that in my computer or in the server.  so if is in the the server then
sudo mkdir /mnt/remote
sudo chown server:server /mnt/remote (user name in server is server how easy!)
sshfs server@192.168.0.5:/media/Backup /mnt/remote

when I do that from my computer i get this

mauricio@Ely:~$ sudo mkdir /mnt/remote
[sudo] password for mauricio: 
mkdir: cannot create directory `/mnt/remote': File exists
mauricio@Ely:~$ sudo chown server:server /mnt/remote
chown: invalid user: `server:server'


am i on the wrong path, should i do it from the server?

---

### Post by matt_symes on 2011-03-18
Hi

> sudo mkdir /mnt/remote
sudo chown me:me /mnt/remote

This is on your local client

and then

```
sshfs mauricio@192.168.0.5:/path/on/remote/server /mnt/remote
```

1. mauricio@192.168.0.5 is the user name and ip address of your server

2. /mnt/remote is the path on the local client.

3. /path/on/remote/server is the path on your server you want be be able to see from /mnt/remote on your client machine.

then if you type (on your client) ls /mnt/remote you will see all the files on your remote machine under the path on your remote machine.

Kind regards

---

### Post by matt_symes on 2011-03-18
Hi 

Let me talk you through my set up.

On my server i have a directory called /mnt/storage. This is the directory i want mapped to my client.

So i create a mount point on my client called /mnt/remote_storage.

```
sudo mkdir /mnt/remote_storage
sudo chown matthew:matthew /mnt/remote_storage
```

I can then mount that using sshfs on my client.

```
sshfs -o idmap=user matthew@199.168.1.99:/mnt/storage /mnt/remote_storage
```

I can then view the files on my server at the local directory /mnt/remote_storage on my client by writing

```
ls /mnt/remote_storage
```

Hope this helps.

Kind regards

---

### Post by mauro24 on 2011-03-18
> **matt_symes said:**
> Hi



This is on your local client

and then

```
sshfs mauricio@192.168.0.5:/path/on/remote/server /mnt/remote
```

1. mauricio@192.168.0.5 is the user name and ip address of your server

2. /mnt/remote is the path on the local client.

3. /path/on/remote/server is the path on your server you want be be able to see from /mnt/remote on your client machine.

then if you type (on your client) ls /mnt/remote you will see all the files on your remote machine under the path on your remote machine.

Kind regards

Ok now i understand this what i did 

sudo mkdir /mnt/remote
sudo chown mauricio:mauricio /mnt/remote
sshfs server@192.168.0.5:/media/Backup /mnt/remote
(the user name in the server is server)
then the password was asked i used the servers password and it worked.

and now do i have to add all those commands to the /etc/rc.local file so it does at every start up?

---

### Post by matt_symes on 2011-03-18
Hi

> and now do i have to add all those commands to the /etc/rc.local file so it does at every start up?

Yes. I have not tried that yet. I have been too busy. Please tell me if it works.

Kind regards

---

### Post by mauro24 on 2011-03-18
i added the commands

sudo mkdir /mnt/remote
sudo chown mauricio:mauricio /mnt/remote
sshfs server@192.168.0.5:/media/Backup /mnt/remote

to the client /etc/rc.local file using

sudo gedit /etc/rc.local

I restarted the client computer, and the Backup storage wasn't mounted.  :(
I'm using a wireless connection, I don't know if that has to do with anything.

---

### Post by matt_symes on 2011-03-18
Hi

```
sshfs server@192.168.0.5:/media/Backup /mnt/remote
```

That is the only command you should need to add to rc.local. 

It may be failing because it requires a password. Have a look into using keys for passwordless login. More secure anyway.

[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

I will test this myself tomorrow and tell you how i got it to work if you still have not fixed this.

Kind regards

---

