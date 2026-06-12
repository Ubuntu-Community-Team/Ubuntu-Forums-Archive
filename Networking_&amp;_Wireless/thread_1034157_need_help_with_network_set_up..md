---
title: "need help with network set up."
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by roamin on 2009-01-08
Hi, im new to the world of linux. i got 2 computers now installed with ubuntu. at first i set one up with ubuntu put it on the network and after some research i was able to connect it to my windows xp computer and download all the files from the xp machine thru the network.

well the xp machine is erased, it is now ubuntu and i can't get it to show files from my first machine thru the network.

Iv just about gone nuts trying everything i can think of, and after reading many posts all over the web im pretty frustrated.

can someone guide me as to how to do this?

I have both computers hooked up to my router but i can't get either one to show up any files from the other.iv already set file sharing to the files i want to transfer but they just don't show up.

under network i have the "windows network" icon show up on both computers but nothing else under it except files from the same computer.

my computer knowledge is intermediate and pretty much beginner on linux.

---

### Post by agim on 2009-01-08
You may have to use Samba. This is usually what is used to share files between windows and ubuntu.

Someone else can help with the implementation, or you can go to there website and try it yourself.

[http://us1.samba.org/samba/](http://us1.samba.org/samba/)

---

### Post by roamin on 2009-01-08
i ran into that in my readings and i downloaded it on both computers.but other than that i don't understand how to actually use it after installing it.

---

### Post by agim on 2009-01-08
I have never worked with it, so I can't help. I know that there are a few good books on the subject, and they are usually available at B&N or Borders.
Or maybe someone can help here, but it may be pretty involved. I just don't know. Get some advice from someone who has done it before.

---

### Post by spcwingo on 2009-01-08
I was under the impression that samba was used for windows shares and nfs was used for linux shares.  OP: Try installing nfs.

```
sudo apt-get install nfs-common
```

You should then be able to access it through places on the task bar.  It would probably also help to assign the machines hosting the shares static IP addresses although DHCP will try to reassign the same address every time it is not guaranteed.  I hope this helps.

---

### Post by roamin on 2009-01-08
well i solved my issue, i looked into the nfs thing most of the information on ither samba or nfs is very confusing to me since i don't understand half the stuff thats going on. but from bits and pieces i was able to put something together that worked.

basically i made sure i had samba installed and updated using the codes i found on samba websites.

then i gathered the information i needed. system>administration>network tools.and under network device picked my active ethernet and wrote down the ip address

then i whent places>home folder  created a folder and named it "shared" right clicked on it chose "sharing options" picked "share this folder" and closed it.

then i whent to Places>connect to server. Chose server type "windows share". server i put the ip address i wrote down, and under "share" i put the name of the folder i created and pressed "connect"

then i loged on my other computer whent Places>connect to server.
and put the exact same info, connected.. and thats it!
i now had acess to that fold on the other computer and im currently transfering all 100gigs of the files i wanted.

hope this info helps someone else. all the codes and making your own servers and hostnames, chaging codes, adding coders etc etc posted on the web just confused the heck out of me since i still don't know what thats talking about.

---

### Post by albinootje on 2009-01-08
> **roamin said:**
>  I have both computers hooked up to my router but i can't get either one to show up any files from the other.iv already set file sharing to the files i want to transfer but they just don't show up.


You have several options, amongst others :
1) NFS, fast, quite easy to set up, can be annoying when the nfs-server times out, insecure by default because it doesn't use authentication.
2) Samba, perhaps a little harder to set up depending on the situation.
3) ssh, very easy to set up, secure by default.

What you tried with the "Sharing Options" is about Samba.

Let's look at NFS to start with.

For this example let us assume the following :
Computer A has ip address 192.168.0.2
Computer B has ip address 192.168.0.3

Install the nfs-server on both machine with the following command :
```

sudo apt-get install nfs-kernel-server

```

(If you're using firewall software, make sure that NFS and portmapper can do the traffic they need.)

That should install portmap.
Make sure it's running :
```

sudo /etc/init.d/portmap restart

```

Let's assume that you want to share /data.
Edit /etc/exports on both machines, so that it looks like this :
```

/data       192.168.0.0/255.255.255.0(rw,sync,subtree_check)

```
Restart the nfs-server on both machines after this :
```

sudo /etc/init.d/nfs-kernel-server restart

```

Check whether nfs and portmapper are running :
```

rpcinfo -p

```

Try on machine A to mount /data from machine B :
```

sudo mkdir /media/test
sudo mount 192.168.0.2:/data /media/test -t nfs

```
If you don't get any errors, check the content of /media/test.
And check out the output of :
```

mount
df -h

```

---

### Post by albinootje on 2009-01-08
> **roamin said:**
>  hope this info helps someone else. all the codes and making your own servers and hostnames, chaging codes, adding coders etc etc posted on the web just confused the heck out of me since i still don't know what thats talking about.

Good that you have it working! :)

Just FYI, from time to time the commands on the terminal are :
* Very handy to troubleshout, because errors in GUI apps can be 
  limited or confusing.
* Faster, and also much easier to write down here.
* Practical, because it also works on the command line when connecting
  remotely to a Linux server.

Please mark this thread as SOLVED, thanks.

---

