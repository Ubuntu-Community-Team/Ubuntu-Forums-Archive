---
title: "Weird. I connect Windows to Ubuntu Server but not Ubuntu to server. Help?"
date: 2010-09-25
forum: Networking &amp; Wireless
---

### Post by rcayea on 2010-09-25
Hey everyone,

As the title says, I am able to connect my two windows (7 and vista) to Samba/UbuntuServer and browse, cut, paste, etc. However, I can't for the life of me connect with my Ubuntu machines. Anyone know where I should start to trouble shoot?

I get to the stage: "Opening Workgroup" and then I get unable to mount location. Failed to retrieve share list from server.

Thanks,
Randy

---

### Post by rcayea on 2010-09-26
b u m p

---

### Post by blueturtl on 2010-09-26
This is the "master browser wars" problem. One or more of your systems are attempting to seize the position of "master browser".

Of all the computers connected to your network, you need to insure that

a) The server has the highest priority and will thus be granted the "master browser" rank by the other computers

b) The other computers have low priority and will always fail a battle against the server.

c) All have the same workgroup.

When two or more systems declare themselves master browser, they will be blind to clients mapped by the other master. Confusing? It's Microsoft tech...

edit: Look for these settings in your smb.conf on the Ubuntu computers that can't connect:

```
domain master = Yes #(needs to be NO unless it's the server)
local master = Yes #(needs to be NO unless it's the server)
preferred master = Yes #(needs to be NO unless it's the server)
os level = 65 #(number value controls priority, lower value to competitor should ensure submission)
```

---

### Post by rcayea on 2010-09-26
Aw. thank you much! I will give it a go and report back. I did read something about master browsers in "using Samba" but I didn't quite understand what I read.

---

### Post by rcayea on 2010-09-26
No luck. I actually had to add these lines to my cfg file:
local master = Yes
preferred master = Yes
os level = 65 


Thanks for trying. Any other ideas?

---

### Post by luvshines on 2010-09-26
Can you browse the shares from ubuntu command line ??

Listing the shares:
smbclient -L <ip-of-server> -U<valid-user>%<valid-password>

Accessing them:
smbclient //<ip-of-server>/<share-name> -U<valid-user>%<valid-password>

---

### Post by rcayea on 2010-09-26
> **luvshines said:**
> Can you browse the shares from ubuntu command line ??

Listing the shares:
smbclient -L <ip-of-server> -U<valid-user>%<valid-password>

Accessing them:
smbclient //<ip-of-server>/<share-name> -U<valid-user>%<valid-password>

Thanks for that help. It is encouraging because I am able to list and browse from the command line. I had success with both commands. 

Where do I go from here?

---

### Post by luvshines on 2010-09-27
I generally use the shares by mounting them at some place and then browsing them there :)

Haven't tried accessing them from nautilus much, but 
smb://<server-name> does work on my system through nautilus

What error does it give on yours ??

---

### Post by luvshines on 2010-09-27
Might also want to check this

[http://ubuntuforums.org/showthread.php?t=450131](http://ubuntuforums.org/showthread.php?t=450131)

---

### Post by rcayea on 2010-09-27
> **luvshines said:**
> I generally use the shares by mounting them at some place and then browsing them there :)

Haven't tried accessing them from nautilus much, but 
smb://<server-name> does work on my system through nautilus

What error does it give on yours ??

I tried both of your tips. This one and the link you added in another post. I get nothing with both. 

with the smb://, I get the error that No such file or directory. Odd, because I can connect with CLI.

---

### Post by rcayea on 2010-09-27
I feel like i get so close to connecting that I would like to look in the log file for error messages or something to show what is wrong. 

Where in the Log File would I look for information about not being able to connect to my server from Ubuntu?

thanks,
Randy

---

### Post by rcayea on 2010-09-28
Bump. Anyone with any idea where to look in the log file for errors?

---

### Post by rcayea on 2010-09-28
As I continue to try to figure out my issue with Ubuntu Desktop connecting to Ubuntu Server I found this error message in the system log. If I am way off base, don't laugh too loud at me, because I am taking a total guess. 

But would this mean anything for my connection:

failed to register lockdv1 RPC service (errno 97).

---

### Post by luvshines on 2010-09-29
You have the firewalls disabled, right ??

sudo service iptables stop
sudo ufw disable

This gives lots of tips:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Also, the errors message for nautilus may be logged in the location mentioned in this defect:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/481197](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/481197)

We had this link working till tomorrow, but it's down today i guess. Had loads of troubleshoot :'(
[http://ubuntu.swerdna.org/ubulanprimer.html#firewall](http://ubuntu.swerdna.org/ubulanprimer.html#firewall)

---

