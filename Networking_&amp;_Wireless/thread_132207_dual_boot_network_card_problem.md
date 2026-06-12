---
title: "dual boot network card problem"
date: 2006-02-17
forum: Networking &amp; Wireless
---

### Post by balaram on 2006-02-17
I'm dual booted Ubuntu and Windows 2000. My network card installs in both Ubuntu and Windows and will initially connect in both system, yet whenever I boot into Windows and then boot back into Ubuntu I lose the ability to connect to the net; unless I shut the computer off and physically disconnect the ethernet cable from the network card. Upon re-insertion of the cable and reboot into Ubuntu the internet connection will again work.
     Biostar Nvdia tforce 6100 mobo (proprietary network card, video , audio)
     AMd Sempron 3000 CPU

---

### Post by bscbrit on 2006-02-18
Next time the fault occurs, please use this thread for troubleshooting to identify exactly why the card has stopped working i.e. has the driver been corrupted, has DNS switched off etc.

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

We should then be able to help you fix the problem.

---

### Post by sujitg on 2006-03-02
I am very new to Linux & ubuntu in particular, I wanted to try out Ubuntu, so was thinking of installing Ubuntu with Dual boot option on a machine already running Windows 2000 Professional. 

Could you direct me to some documentation or tutorial that will help me do this?

Thanks

SUJIT

---

### Post by boosted_sled on 2006-05-08
I have exactly the same problem, which I just discovered this morning.  One thing I noticed was that on my router's DHCP client list the host is listed as the windows side name even though I've rebooted into linux.  A few things I'm going to try tonight are

(1) try make both OS's fixed IP rather than dhcp
(2) change the windows host name to match the linux - don't think this will do anything
(3) do ipconfig /release from windows before reboot

---

### Post by Iowan on 2006-05-08
[QUOTE=sujitg]I am very new to Linux & ubuntu in particular, I wanted to try out Ubuntu, so was thinking of installing Ubuntu with Dual boot option on a machine already running Windows 2000 Professional. 

Could you direct me to some documentation or tutorial that will help me do this?

Thanks

SUJIT[/QUOTE]
[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29]("https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28dual%29%7C%28boot%29")
You might also: SEARCH for "dual boot", check the Beginner  and How-To forums, start your own thread.  ;)

---

### Post by listenxtoxmetal on 2007-07-01
Not sure my post belongs in here exactly but let me explain anyways. I run Windows Xp and Ubuntu feisty. My problem is similar to the fellow who started this strand only in the reverse. I can get online without issue when I boot to linux. Boot to windows and I can not obtain my IP address. I use comcast they give IP address's dhcp. not sure if any other info would be helpful but this problem has perplexed me and all the comcast help persons.

---

### Post by fiddlemonster on 2008-06-27
I have tried to go to the tutorial suggested but the link won't work. I have the following problem:

1. Windows boot after cache dumping through power button: **Network works!** 

2. Shut down

3. Turn on, boot Windows again: **NIC OK**

4. Shut down

5. Turn on, boot Ubuntu 8.04: **No network**

6. Shut down

7. Cache dumping through power button

8. Turn on, boot Ubuntu: **Network works!** 

9. After ending ubuntu session, shut down

10. Turn on, boot Windows: **No network**

Etcetera....

It seems every time I switch OS, the NIC does not kick in. I have to do this trick every time I switch, but if I shut down and reboot on the same OS, it is usually no problem. 

Would anyone shine some light upon this?

Thanks!!!

---

