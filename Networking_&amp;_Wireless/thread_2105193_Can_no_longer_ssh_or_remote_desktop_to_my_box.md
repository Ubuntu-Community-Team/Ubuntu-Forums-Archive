---
title: "Can no longer ssh or remote desktop to my box"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by squarethumps on 2013-01-15
I need some help fixing ssh. 

I recently upgraded to 12.04 from ~10.10.  Everything is fine ( excepting the new desktop which is awkward .. but anyway ) except that I can no longer ssh to this machine.

sshd is running and I can successfully  'ssh localhost', but I can not ssh to this machine from another machine on the network.

root@argonaut:~# netstat -lnp --tcp --udp -l | grep ssh
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      899/sshd        
tcp6       0      0 :::22                   :::*                    LISTEN      899/sshd        

I can neither remote desktop nor ssh and I was able to do these things before.

I need some direction on this please.

---

### Post by Lars Noodén on 2013-01-15
Is the firewall somehow active or modified?

```

sudo ufw status numbered

```

---

### Post by ahallubuntu on 2013-01-15
> **squarethumps said:**
> I need some help fixing ssh. 

I recently upgraded to 12.04 from ~10.10.  Everything is fine ( excepting the new desktop which is awkward .. but anyway )

If you want the "old desktop" back, open Ubuntu Software Center, install "Gnome Shell," logout, and before logging back in, choose "Gnome Classic" as the login session.  This is Gnome 3 which is slightly different from 10.10's Gnome 2 but very close.  I switched from 10.04 to 12.04 recently and very quickly got used to Gnome 3 "Classic."

> **squarethumps said:**
> except that I can no longer ssh to this machine.

sshd is running and I can successfully  'ssh localhost', but I can not ssh to this machine from another machine on the network.

I have been able to ssh into 12.04 machines so I know it works.  But you do have to install the ssh server.  Can you confirm you installed that?  Open a terminal and type

```

sudo apt-get update
sudo apt-get install ssh
```     

Did you enable a firewall that might have blocked port 22?  If you didn't enable or install a firewall, just installing the ssh server would open that port and allow machines on the local network to connect.

> **squarethumps said:**
> I can neither remote desktop nor ssh and I was able to do these things before.

I need some direction on this please.

In 12.04, Remote Desktop is called "Desktop Sharing."  You'll find it works better if you use a login session that doesn't use "effects."  If you tried my suggestion of Gnome Classic above, use "Gnome Classic (without effects)" instead for the machine into which you will remote desktop, so the screen refresh works correctly.  (Or if you're getting used to Unity, login with Unity 2D.)  Otherwise, you'll have issues with desktop windows not being refreshed.

---

### Post by squarethumps on 2013-03-26
AAAAAAAAAARRRRRRGGGGGGGGGGHHHHHHHHHH!!!!!!!!!!!!!!

THANK YOU for the replies.  I never got an e-mail notification saying that someone had replied so I thought I was all alone  :( 

> Is the firewall somehow active or modified?


```
root@argonaut:~# ufw status numbered
Status: active

     To                         Action      From
     --                         ------      ----
[ 1] 5900                       ALLOW IN    Anywhere
[ 2] 5900                       ALLOW IN    Anywhere (v6)

root@argonaut:~# 
```


> If you want the "old desktop" back, open Ubuntu Software Center, install  "Gnome Shell," logout, and before logging back in, choose "Gnome  Classic" as the login session.  This is Gnome 3 which is slightly  different from 10.10's Gnome 2 but very close.  I switched from 10.04 to  12.04 recently and very quickly got used to Gnome 3 "Classic."

Yes, thank you.  I'm had been forcing myself to get used to it.  Everything I've read points to this not going away in Ubuntu, which I really prefer over the other distros, so I might as well accept it, eh?  Resistance is futile.

> sudo apt-get update sudo apt-get install ssh

```

root@argonaut:~# apt-get update
.
.< I omitted these "Hit"s.
.

Fetched 2,831 kB in 17s (161 kB/s)                                             
Reading package lists... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@argonaut:~# 

```

So I'm not sure what to do after I do apt-get update and it tells me to do apt-get update again  ..... 


```
root@argonaut:~# apt-get install ssh
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ssh is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 25 not upgraded.
root@argonaut:~# 
```

I feel certain that it is running for some other reasons as well  :
```

root@argonaut:~# ps -ef | grep sshd
root       873     1  0 10:10 ?        00:00:00 /usr/sbin/sshd -D
root      3662  3447  0 10:51 pts/4    00:00:00 grep sshd
root@argonaut:~# 

```

Additionally I am able to ssh localhost .. which I think is a strong indication that sshd is functioning correctly in it's own right .. .

> Did you enable a firewall that might have blocked port 22?  If you  didn't enable or install a firewall, just installing the ssh server  would open that port and allow machines on the local network to connect.

I don't believe that I have installed or configured any firewall on this machine ... 

> In 12.04, Remote Desktop is called "Desktop Sharing."  You'll find it  works better if you use a login session that doesn't use "effects."  If  you tried my suggestion of Gnome Classic above, use "Gnome Classic  (without effects)" instead for the machine into which you will remote  desktop, so the screen refresh works correctly.  (Or if you're getting  used to Unity, login with Unity 2D.)  Otherwise, you'll have issues with  desktop windows not being refreshed.

Yes, previously when I was able to use Desktop Sharing ( prior to this issue ) I did have to disable Compiz and that would refresh the screen.  I have experience what you describe and corrected it as you described, but since this issue started I've not been able to even connect to the machine, let alone worry about screen refreshing.


THANKS AGAIN for viewing and responding.   I'll see why I didn't get an e-mail notification, or check back each day to see the activity.

---

### Post by squarethumps on 2013-03-26
ok .. well I immediately went to work with the firewall and I see that  the firewall was the problem.  I don't remember "enabling" it at all but  I must have at some point in the past.  :oops:

THANKS for the direction and guidance.  The solution for at least the ssh was to : 

 ```
sudo ufw allow 22
```

I'm sure the solution for Desktop Sharing will be similar.

---

### Post by WhaleVPS on 2013-03-26
Did you turn the firewall on or it came on after upgrade?

---

### Post by squarethumps on 2013-03-26
I must have turned it on.  I see the following couple of lines in my root user history, and it must have been a while ago so I forgot I did this.  

I was trying to fix my Remote Desktop ( which still isn't working ) and I was following some instructions on some website that told me to 

 ```
sudo ufw enable
sudo ufw allow 5900
```

I now seem to remember that my ssh used to work, but my Remote Desktop is what really stopped working after the upgrade.  

I'll be starting a new post with the Remote Desktop issue.

---

### Post by Iowan on 2013-03-26
I have taken the liberty of tagging this thread SOLVED.
It's easy enough to change back if you disagree.

---

