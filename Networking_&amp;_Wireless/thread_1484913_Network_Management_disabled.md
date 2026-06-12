---
title: "Network Management disabled"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by 9AndS on 2010-05-16
Kubuntu 10.04 LTS (Lucid Lynx) is what I'm using. And I just got a problem with the network-manager.
The problem is similar to a bug described [[COLOR="Navy"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+bug/555571"), but changing
```
NetworkingEnabled=true
```
does not help because it is already "true".
Any help would be appreciated.

---

### Post by dineshs on 2010-05-16
the following link 
[http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
says that the file /etc/network/interfaces should only contain
```
auto lo 
iface lo inet loopback
```

---

### Post by 9AndS on 2010-05-16
It does contain only those lines.
So far I've managed to connect to the internet by removing network-manager and installing wicd instead.

---

### Post by chaosgrimm on 2010-05-16
may want to check this too:

/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

---

### Post by 9AndS on 2010-05-17
In fact I did check that.
The problem occurred when the system failed to restore from Hibernate mode. For a lot of people changing "NetworkingEnabled" to "true" works and fixes the problem. But I already have that enabled. I've checked config files and everything seems to be ok. I even tried:
```
NetworkingDisabled=false
```
but no luck.

---

### Post by tnttrx on 2010-05-18
here's the same problem, too.

network management was disabled after failing on resuming from sleep:
battery went out, so instead of resuming, there was a clean startup 

changing to

```
[ifupdown]
managed=true 
```

didn't help.

but, 

```
NetworkingEnabled=true
```

solved the problem.

then again, maybe it's the combination of both options that solved the problem.

---

### Post by jetpeach on 2010-06-01
thanks, same thing just happened to me after my battery died completely. changed the [ifupdown] managed=true  did not solve the problem. 
but changing the file /var/lib/NetworkManager/NetworkManager.state to networking enabled did fix the problem.

---

### Post by zadehas on 2010-07-09
For what it's worth, I can confirm that changing the NetworkingEnabled to true in  /var/lib/NetworkManager/NetworkManager.state solved the problem for me too.

Thank you

---

### Post by downinit on 2010-07-10
I am having this problem on my system (Kubuntu 10.04) and I get the:  "NetworkingEnabled=false" message in Kate. But when I change it to 'true' and try to save, I get an error message that I cannot save a backup of file, followed by a message that I do not have permission to change the file.  I have not used Kubuntu very much, and I have forgotten everything I learned about Terminal and Root. I have searched high and low for ways to login as root, but none of them are for 10.04 and none of the older ones work.  


Could someone who speaks plain english (for those of us who are not experts) tell me how to change this file, either in Terminal, or in Kate.  What do I need to do to get permission to modify the file?  The more simple the explanation, the better, as this seems to be a common problem and I am sure I am not the only non-expert that has run across it.  I really do not want to have to reinstall 9.10, I have over-written this poor hard drive too many times as it is.  Thank you

---

### Post by dineshs on 2010-07-10
You are using kate......... to open the file .Try [COLOR="Blue"]sudo kate ......[/COLOR]

---

### Post by 9AndS on 2010-07-13
Open terminal window and type
```
kdesudo dolphin
```
hit enter, type your password and dolphin window will open in sudo mode.

---

### Post by OldGaf on 2010-08-16
NetworkingEnabled=true

This worked for me when helping my sister on the phone (in another country)

Thank a lot !

---

### Post by gr8bits on 2010-09-23
> **downinit said:**
> I am having this problem on my system (Kubuntu 10.04) and I get the:  "NetworkingEnabled=false" message in Kate. But when I change it to 'true' and try to save, I get an error message that I cannot save a backup of file, followed by a message that I do not have permission to change the file.  I have not used Kubuntu very much, and I have forgotten everything I learned about Terminal and Root. I have searched high and low for ways to login as root, but none of them are for 10.04 and none of the older ones work.  


Could someone who speaks plain english (for those of us who are not experts) tell me how to change this file, either in Terminal, or in Kate.  What do I need to do to get permission to modify the file?  The more simple the explanation, the better, as this seems to be a common problem and I am sure I am not the only non-expert that has run across it.  I really do not want to have to reinstall 9.10, I have over-written this poor hard drive too many times as it is.  Thank you

I was having the same problem and this simple step worked for me.Maybe this is the step others also tried explaining here, but in plain English (em also a linux N00b)

Access the file from var/lib/NetworkManager/
Right click on that file(NetworkManager), 
choose open with,
one the box opened, type sudo kate on the blank space at the to[p of box.
The file will be opened in kate.
Now try editing it (change the false values to true) and save. You won't be having a problem to save. 
Now reboot and the network will be connected.

Anyway this worked for me. hope this will be helpful for some of the starters like me.

---

### Post by gr8bits on 2010-09-23
> **gr8bits said:**
> I was having the same problem and this simple step worked for me.Maybe this is the step others also tried explaining here, but in plain English (em also a linux N00b)

Access the file from var/lib/NetworkManager/
Right click on that file(NetworkManager), 
choose open with,
one the box opened, type sudo kate on the blank space at the to[p of box.
The file will be opened in kate.
Now try editing it (change the false values to true) and save. You won't be having a problem to save. 
Now reboot and the network will be connected.

Anyway this worked for me. hope this will be helpful for some of the starters like me.

A small addition to the above steps, initially for accessing the file you shud use 'sudo dolphin'. ie, type 'sudo dolphin' on the search window from application launcher, u will get 'run sudo dolphin'. Click it to open. Dolphin will open up. Now get to the NetworkManager file and do the steps as told in my previous post quoted.

---

### Post by cypher_zero on 2010-10-05
The above worked for me.  For clarification, here's the exact steps that need to be taken:

 1) Open a command line and type in:
```
sudo dolphin
```
Alternatively you can type 'sudo dolphin' into the search window from application launcher and you  will get 'run sudo dolphin.' Either method works.
This will open dolphin as a super user.

2) In Dolphin, navigate to ```
/var/lib/NetworkManager/
```

3) Open NetworkManager.state in Kate

4) Change the line that says ```
NetworkingEnabled=false
```to 
```
NetworkingEnabled=true 
```

5) Reboot computer.

It should work fine after that.  I've used this same method several times thus far.

cypher

---

### Post by AliceKingsley on 2010-10-12
This was a huge help. Thanks to cypher_zero for the step-by-step. :KS

---

### Post by luck_gh0st on 2011-01-07
Thanks guy! This worked on my Mint Lucid KDE  on my parallels VM on my macbook.

---

### Post by dowell_p on 2011-01-08
This worked perfect. Lesson learned, don't let your battery die!

---

### Post by ptrakk on 2013-01-24
thanks

---

