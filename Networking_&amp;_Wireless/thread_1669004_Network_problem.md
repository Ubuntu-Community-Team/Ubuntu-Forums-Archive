---
title: "Network problem"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by RapeField on 2011-01-17
I have some problem with my network, i can't connect to Internet with Ubuntu desktop version. I'm using my network cable but cant seem to get Internet.

Sorry if I give useless information but don't know what to give you.

I'm new to Ubuntu so I really need good explanation :D

---

### Post by dineshs on 2011-01-17
To what device your ethernet cable is plugged in?
What do you get for these terminal commands(applications-accessories-terminal)```
sudo lshw -C network
``````
ping 4.2.2.1 -c3
```

---

### Post by RapeField on 2011-01-17
> **dineshs said:**
> To what device your ethernet cable is plugged in?
What do you get for these terminal commands(applications-accessories-terminal)```
sudo lshw -C network
``````
ping 4.2.2.1 -c3
```

Well on the lshw:

*-network DISABLED

and then som other text

on ping:

connect: Network is unreachable

I'ts Cisco

---

### Post by dineshs on 2011-01-17
Which ubuntu version are you using?
Do you have a network manager icon on right top of the panel?If yes right click the icon and ensure that enable networking is ticked.
Ensure that the device is enabled in BIOS

---

### Post by RapeField on 2011-01-17
> **dineshs said:**
> Which ubuntu version are you using?
Do you have a network manager icon on right top of the panel?If yes right click the icon and ensure that enable networking is ticked.
Ensure that the device is enabled in BIOS

Im using the latest version, downloaded it today.

Yes, and yes it's enabled.

I'm going to check the bios, but I'm quite sure its enabled because it was working on Windows Server.Edit: It's enabled.

---

### Post by dineshs on 2011-01-17
Can you try post#3 [here]("http://ubuntuforums.org/showthread.php?t=1505217") ?
(prefix [COLOR="Blue"]sudo[/COLOR] before each command) then restart
If there is no luck pl post the contents of```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```(all should be enabled)

---

### Post by RapeField on 2011-01-17
> **dineshs said:**
> Can you try post#3 [here]("http://ubuntuforums.org/showthread.php?t=1505217") ?
(prefix [COLOR=Blue]sudo[/COLOR] before each command) then restart
If there is no luck pl post the contents of```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```(all should be enabled)


Apperantly I don't have
/var/lib/NetworkManager/NetworkManager.state  
It says that I can't save it because theres no such file.

The other commands in the thread did'nt work either because it couldn't find /var/lib....etc

I could mention that when I had Windows server edition that the network didn't work either. I could connect to the Local network but not the Internet.

---

### Post by decrepit on 2011-01-17
Try navigating to the address in nautilus, then just double click the file.

I'd be surprised if you don't have the file

---

### Post by RapeField on 2011-01-17
> **decrepit said:**
> Try navigating to the address in nautilus, then just double click the file.

I'd be surprised if you don't have the file


Found it and everything was on.


Could it help if I change IP, and if how do i do?

---

### Post by decrepit on 2011-01-19
this is what dineshs was talking about 2 days ago, did you try it?

> Re: Networking disabled
Have you had a failed hibernate that locked up and you had to do a hard reboot?

Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist.../msg07864.html](http://osdir.com/ml/debian-bugs-dist.../msg07864.html) (or LaunchPad bug #524565) for details and a fix (which worked for me):
Code:

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start



---

### Post by RapeField on 2011-01-19
> **decrepit said:**
> this is what dineshs was talking about 2 days ago, did you try it?

Yes I have, but I'm quite sure that it's not Ubuntu but something else because the network didn't work on Windows Server either, but I could be wrong.

---

### Post by RapeField on 2011-01-22
Solved it, some how Debian (my old serevr) had put up 40 connections to my router so i couldnt connect. But I jsut removed them. Thanks for all the help :D

---

