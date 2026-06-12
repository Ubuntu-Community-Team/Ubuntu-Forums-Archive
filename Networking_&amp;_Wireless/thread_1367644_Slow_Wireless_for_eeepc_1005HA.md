---
title: "Slow Wireless for eeepc 1005HA"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by ResidentSuprhero on 2009-12-29
I've basically just started using Ubuntu.  After having very inconsistent wireless connection to a Linksys router, I ran

```
sudo apt-get install linux-backports-modules-karmic
```

This resulted in my connection strength going from about 40% to about 90% but I still have slow download speeds.  Downloads start at around 150kB/s (slow) and quickly drop to around 1500B/S (very very slow).

I'm sure there is more information that you may need to solve the problem.  Any help would be greatly appreciated.

---

### Post by ResidentSuprhero on 2010-01-08
It was my wireless router.

---

### Post by acascianelli on 2010-01-08
What was the problem with your router, I think I'm having a similar problem.

Are you running DD-WRT on your router by chance?

---

### Post by Coolin55 on 2010-01-08
I am having similar troubles with an Asus eee 1000HA.  My connection is fine at work, but intolerably slow at home where I am running a netgear router with DD-WRT.  Any additional info would be appreciated!

---

### Post by pound_forthesound on 2010-01-10
> **ResidentSuprhero said:**
> I've basically just started using Ubuntu.  After having very inconsistent wireless connection to a Linksys router, I ran

```
sudo apt-get install linux-backports-modules-karmic
```

This resulted in my connection strength going from about 40% to about 90% but I still have slow download speeds.  Downloads start at around 150kB/s (slow) and quickly drop to around 1500B/S (very very slow).

I'm sure there is more information that you may need to solve the problem.  Any help would be greatly appreciated.

I have a similar slow wireless problem on my 1005ha.  I tried to use the command you suggested but i get the following error:

```
harry@harry-laptop:~$ sudo apt-get install linux-backports-modules-karmic
[sudo] password for harry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  linux-backports-modules-karmic: Depends: linux-backports-modules-karmic-generic (= 2.6.31.18.31) but it is not going to be installed
E: Broken packages
harry@harry-laptop:~$ 

```

After that, I tried to install the package it said was missing with:

```
harry@harry-laptop:~$ sudo apt-get install linux-backports-modules-karmic-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  linux-backports-modules-karmic-generic: Depends: linux-backports-modules-2.6.31-18-generic but it is not installable
E: Broken packages
harry@harry-laptop:~$ 
```

Does anyone know why this isn't working for me?  Why would that package not be installable?

---

### Post by pound_forthesound on 2010-01-10
Okay I figured it out, I just had to install the KDE RC1 updates first.

Edit: after a reboot, wireless seems to be working much better.  Excellent!

---

### Post by abiheiri on 2010-01-20
[SIZE=3]Man![/SIZE] #-o I am smacking myself right now.. 

In the previous ubuntu version (9.04) the wifi did not work by default so I had to manually install the backports package.

But in 9.10 It worked out of the box so I totally forgot about backports and my wifi has been running choppy, slooow as hell and disconnecting often....

Now I installed the backports and everything works as it should...gah! :-({|=

---

### Post by acascianelli on 2010-01-21
I think my problem may have been ISP related because I have not had this problem occur again for a while now.

---

### Post by CrushX on 2010-04-11
Hi - apologies in advance is this is too obvious - when you refer to 'installing the backports" - which specific backports fixed the problem and where can I find them?

thanks

---

