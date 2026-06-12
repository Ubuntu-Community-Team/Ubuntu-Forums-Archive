---
title: "Install bug, fixed for final Ubuntu 7.10, still exists on Mythbuntu"
date: 2007-10-24
forum: Mythbuntu
---

### Post by technoboi on 2007-10-24
My hardware:
Abit iL-90MV motherboard with 'on board' graphics.
Intel 'Mobile' Core 2 Duo CPU T5600
2GB Corsair memory.

I posted a problem, about 2 weeks ago, re Mythbuntu that later I found existed on Ubuntu 7.10 beta. This problem was FIXED for the final release of Ubuntu 7.10 desktop and that installs perfectly.
However, it still exists on Mythbuntu. 
This applies to running the install disk. I tried standard mode and lost the video. Then I tried 'safe graphics mode' This is what happened:-

Up comes the 'cylon eye' going back and forth on the 'Mythbuntu' screen. Then it turns into a progress bar and makes it way to the end. Then the same thing flashes on and off, obviously the same thing is trying to execute without success. This is what keeps flashing up:
...................................................
LIRC not configured.
read/usr/share/doc/lirc/html/configure.html

Starting lirc daemon:
Starting deferred execution scheduler atd
Starting periodic scheduler crond
Checking battery state
Running local boot scripts (/etc/rc.local)
..................................................
Then up came a screen stating:-
....................................................
'The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on.
...........................................................
I click 'OK' and the 'LIRC not configured' etc. message comes up again.
That is as far as it goes.

To reiterate, Ubuntu 7.10 Beta  had this bug, as did Mythbuntu 'beta'. 
Ubuntu desktop 7.10 FINAL no longer has this bug but Mythbuntu 7.10 (22 October 2007) retains the bug.

---

### Post by superm1 on 2007-10-24
> **technoboi said:**
> My hardware:
Abit iL-90MV motherboard with 'on board' graphics.
Intel 'Mobile' Core 2 Duo CPU T5600
2GB Corsair memory.

I posted a problem, about 2 weeks ago, re Mythbuntu that later I found existed on Ubuntu 7.10 beta. This problem was FIXED for the final release of Ubuntu 7.10 desktop and that installs perfectly.
However, it still exists on Mythbuntu. 
This applies to running the install disk. I tried standard mode and lost the video. Then I tried 'safe graphics mode' This is what happened:-

Up comes the 'cylon eye' going back and forth on the 'Mythbuntu' screen. Then it turns into a progress bar and makes it way to the end. Then the same thing flashes on and off, obviously the same thing is trying to execute without success. This is what keeps flashing up:
...................................................
LIRC not configured.
read/usr/share/doc/lirc/html/configure.html

Starting lirc daemon:
Starting deferred execution scheduler atd
Starting periodic scheduler crond
Checking battery state
Running local boot scripts (/etc/rc.local)
..................................................
Then up came a screen stating:-
....................................................
'The display server has been shut down about 6 times in the last 90 seconds. It is likely that something bad is going on.
...........................................................
I click 'OK' and the 'LIRC not configured' etc. message comes up again.
That is as far as it goes.

To reiterate, Ubuntu 7.10 Beta  had this bug, as did Mythbuntu 'beta'. 
Ubuntu desktop 7.10 FINAL no longer has this bug but Mythbuntu 7.10 (22 October 2007) retains the bug.
Well that would be odd, the Mythbuntu disks were generated *after* the Ubuntu disks, so all Ubuntu disk changes should have been reflected in them.  

Can you checkout /var/log/Xorg.0.log & /var/log/Xorg.0.log.old

And post them here if you're not sure.

---

### Post by technoboi on 2007-10-25
> **superm1 said:**
> Well that would be odd, the Mythbuntu disks were generated *after* the Ubuntu disks, so all Ubuntu disk changes should have been reflected in them.  

Can you checkout /var/log/Xorg.0.log & /var/log/Xorg.0.log.old

And post them here if you're not sure.
Firstly, I am certain about what I have stated re the bugs on the beta versions. I have, today, tried out the beta disks for Ubuntu and Mythbuntu again. They both produce the same problem. I also know that I got a perfect install with the final 7.10 of Ubuntu but the Mythbuntu final behaves in just the same way as the beta version.

>Can you checkout /var/log/Xorg.0.log & /var/log/Xorg.0.log.old
I am sorry but I don't understand what you are asking me to do. The heading I made, using the word 'install'  is misleading. I don't get anywhere near an 'install'. I am just loading up the disk. There is no install so I can't see how I can check the files - unless i am not understanding you properly.
Thank you.

---

### Post by superm1 on 2007-10-25
> **technoboi said:**
> Firstly, I am certain about what I have stated re the bugs on the beta versions. I have, today, tried out the beta disks for Ubuntu and Mythbuntu again. They both produce the same problem. I also know that I got a perfect install with the final 7.10 of Ubuntu but the Mythbuntu final behaves in just the same way as the beta version.


This is the second instance that I've seen that the xorg.conf generation is different on a standard Ubuntu versus a Mythbuntu disk.  This shouldn't be happening since the same source files are used in both instances, so it's a bit hard to explain.

The other instance that this happened to someone, they ended up copying the xorg.conf that they got from a standard Ubuntu disk into the Mythbuntu installer bootup.  
> 
>Can you checkout /var/log/Xorg.0.log & /var/log/Xorg.0.log.old
I am sorry but I don't understand what you are asking me to do. The heading I made, using the word 'install'  is misleading. I don't get anywhere near an 'install'. I am just loading up the disk. There is no install so I can't see how I can check the files - unless i am not understanding you properly.
Thank you.

What I would recommend doing is starting an ssh server on the disk after it boots up.

At that console, type:
```
sudo /etc/init.d/ssh start
```

Change your password on the Live bootup
```
passwd
```

Determine your ip address
```
ifconfig
```

Then from a remote machine:

Windows:
[LIST]
[*]Connect using putty[/LIST]Linux:
[LIST]
[*]Open a terminal and connect to your machine using the command 'ssh'[/LIST]Mac
[LIST]
[*]Connect using a terminal like you would on linux[/LIST]```
ssh ubuntu@SERVER
```

You can now look at log files using
```
cat /var/log/Xorg.0.log
```

or 

```
nano /var/log/Xorg.0.log
```

---

### Post by Lobenroter on 2007-10-26
Hello, here the same problem with the configuration:

MSI K9N Neo-F V2
MSI RX1550-TD128EH, 128MB, PCI-Express

Xorg.0.log and Xorg.0.log are in the zip file

---

### Post by technoboi on 2007-10-28
> **Lobenroter said:**
> Hello, here the same problem with the configuration:

MSI K9N Neo-F V2
MSI RX1550-TD128EH, 128MB, PCI-Express

Xorg.0.log and Xorg.0.log are in the zip file

Thanks for posting the files. I just couldn't understand how to start up the SSH server, just from the boot up disk, when  when the system wasn't even installed and hadn't got so far as working as a live disk.  I don't know how you did it because  it didn't make sense to me, I couldn't see how I could get a prompt without anything being installed. With the bug  I got it seemed impossible to me.
Hopefully the files will help bring a solution.

---

### Post by JPorter on 2007-10-29
Guys, it's not an Ubuntu/Mythbuntu problem, it's an ATI driver problem, at least in most of the cases that I've seen.


You may want to try installing the fglrx driver from the recovery console and boot again, to give it a shot.  This is assuming that you've completed an install using the Alternate cd.


You will need wired internet access.  Boot to recovery console and do this:
```
sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv
```

If your first step failed because you didn't have internet access ("could not resolve" errors), you should run:```
sudo ifconfig eth0 down

sudo dhclient eth0
```

Of course, substitute eth0 for whatever your wired ethernet connection is (eth1, etc).  Follow the above driver install steps.


And then reboot normally. Hopefully this should get you up and running.  Best of luck to you.

---

### Post by Bigmikev on 2007-10-29
Hello.

I am new to this site and I am experiencing the same problem.  I have an ATI Raedeon 2600HD video card.  I did the settings that you had suggested and now all I get is a blank screen when the os loads.  I did a fresh install of the OS but I had issues viewing the live CD because the display server kept crashing.  I was able to get the install to go but now I am stuck.  I am a newbie to the Linux world but I work in IT so I am pretty reliable when it comes to doing anything.

Please let me know if there is anything I can do.

Thanks.

mike

---

### Post by technoboi on 2007-10-30
> **JPorter said:**
> Guys, it's not an Ubuntu/Mythbuntu problem, it's an ATI driver problem, at least in most of the cases that I've seen.
.
I am not sure that we are talking about the same bug. I want to use Mythbuntu NOT Ubuntu. I can load Ubuntu standard desktop with NO problems whatsoever. There isn't, afaik, an alternate version of Mythbuntu. I have tried installing MythTV onto Ubuntu before. After many, many hours of work I did get some success on what was a very slow and unsuitable computer. Knowing all the time it takes to get MythTV working I opted to try Mythbuntu.  All the Linux Media Centre type programs I've tried  are a b****r to install despite what is claimed on the various web sites. I am hoping that Mythbuntu will be the exception and be much easier to commission.
I think I can see where you are coming from though. You are suggesting installing the alternate verion of Ubuntu so that the driver can be updated and then put MythTV on that? OK, but that defeats the whole point of Mythbuntu.
I am not so good at Linux. I learned quite a lot by installing MythTV last time but I've forgotten most of what I did. One problem I find is that guides are often very parochial. They are often geared to the US. Those outside the US, and there are lots of us :-)  , have to work out the necessary changes we need to make and this, to those of us who might be technically apt, but new to Linux, makes the learning curve  steeper.

---

### Post by lewis42 on 2007-10-30
I tried Mythbunu and Ubuntu and saw the error described at the top both times.   I'll try the alternative install as suggested.

---

### Post by JPorter on 2007-10-30
> **technoboi said:**
> I think I can see where you are coming from though. You are suggesting installing the alternate verion of Ubuntu so that the driver can be updated and then put MythTV on that? OK, but that defeats the whole point of Mythbuntu.

The root issues are:

A)  Many newer ATI cards need an updated driver (fglrx) to boot the LiveCD (or the OS in general) without crashing.  There is not a good (easy) way to force use of the fglrx driver when loading a LiveCD, at least not that I have heard yet.

B)  Mythbuntu NEEDS an Alternate (text-based) install CD.  This is a major omission in my opinion.  No wonder so many people are having Mythbuntu install problems... the LiveCD doesn't work at all on certain configurations!

---

### Post by Bigmikev on 2007-11-07
I am just writing to follow up and see if anyone has any success yet with the regular install of Unbuntu as apposed to the Mythbuntu install?  I have not attempted it yet but I will this weekend.

Mike

---

### Post by laga on 2007-11-09
> **JPorter said:**
> 
B)  Mythbuntu NEEDS an Alternate (text-based) install CD.  This is a major omission in my opinion.  No wonder so many people are having Mythbuntu install problems... the LiveCD doesn't work at all on certain configurations!

Since you can just use a regular alternate CD for Ubuntu and install mythbuntu with a  few very simple steps afterwards it's not that much of an issue.

We're going to provide an alternate CD some time in the future, though.

---

### Post by Bigmikev on 2007-11-12
Well.  Unfortunately my luck with Unbuntu and ATI seems to be running out.  

I tried installing Unbuntu with the live CD and everything worked fine.  I was able to get in to the OS temporarily.  Then the screen started to bug out and the display was not correct.  After rebooting, I was unable to get back in.  

Unless anyone has any suggestions or any help with Unbuntu and an ATI HD 2900XT I will not be able to use Mythbuntu like I wanted to.

---

