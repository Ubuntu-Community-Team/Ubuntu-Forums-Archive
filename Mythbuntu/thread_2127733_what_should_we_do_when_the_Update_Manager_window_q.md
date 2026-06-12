---
title: "what should we do when the Update Manager window quits updating?"
date: 2013-03-20
forum: Mythbuntu
---

### Post by neutron68 on 2013-03-20
I've got the mythtv 0.25 update repository selected in the Mythbuntu Control Centre.
I've also checked Mythbuntu Updates repository.

I started the Update Manager tonight (12.04.2 64-bit). 
It downloaded a list of around 40 updates,  
I saw a Samba update and a perl update and a at least one linux-headers (a kernal update?)
It downloaded the files and then stared applying them.

The progress bar moved in the Applying Changes window moved from left to right and all looked fine.  
At around 80%, the window stopped updating.
When I dragged another window over the top of the Update Manager, it was wiped clean - nothing in it, after that.

What does that mean?  
Has it locked up?  
Is one of the updates bad?  
What should I do?

When I ran the top command in a Terminal window, I saw update-notifier and update-manager bounce around in the list of processes.

This same thing happened about a week ago when I tried an update.  I left the machine on in that state all night.  In the morning, nothing had changed so I shut off the pc and went to work.  I guessed that maybe one of the update repositories was down and the Update Manager was stuck in a wait situation?
In trying it again tonight, it appears to be doing the exact same thing's doing the same thing!  

Is anyone else seeing this?

To get an idea of the updates it pulled down I typed the "apt-get -s upgrade" command in a terminal window:
```
eric@Mythbuntu:~/Desktop$ apt-get -s upgrade
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
42 not fully installed or removed.
Conf libapt-inst1.4 (0.8.16~exp12ubuntu10.10 Ubuntu:12.04/precise-updates [amd64])
Conf libudev0 (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf libgudev-1.0-0 (1:175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf libnspr4 (4.9.5-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf libnss3 (3.14.3-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf libwbclient0 (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [amd64])
Conf linux-image-3.5.0-26-generic (3.5.0-26.42~precise1 Ubuntu:12.04/precise-updates [amd64])
Conf libsmbclient (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [amd64])
Conf apt-utils (0.8.16~exp12ubuntu10.10 Ubuntu:12.04/precise-updates [amd64])
Conf udev (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf libdevmapper1.02.1 (2:1.02.48-4ubuntu7.2 Ubuntu:12.04/precise-updates [amd64])
Conf dmsetup (2:1.02.48-4ubuntu7.2 Ubuntu:12.04/precise-updates [amd64])
Conf apt-transport-https (0.8.16~exp12ubuntu10.10 Ubuntu:12.04/precise-updates [amd64])
Conf apache2.2-bin (2.2.22-1ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Conf apache2-utils (2.2.22-1ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Conf perl-modules (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [all])
Conf perl (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf apache2.2-common (2.2.22-1ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Conf apache2-mpm-prefork (2.2.22-1ubuntu1.3 Ubuntu:12.04/precise-updates [amd64])
Conf gir1.2-gudev-1.0 (175-0ubuntu9.3 Ubuntu:12.04/precise-updates [amd64])
Conf gstreamer0.10-pulseaudio (0.10.31-1ubuntu1.2 Ubuntu:12.04/precise-updates [amd64])
Conf libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.2 Ubuntu:12.04/precise-updates [amd64])
Conf liblvm2app2.2 (2.02.66-4ubuntu7.2 Ubuntu:12.04/precise-updates [amd64])
Conf libnspr4-0d (4.9.5-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf libnss3-1d (3.14.3-0ubuntu0.12.04.1 Ubuntu:12.04/precise-updates [amd64])
Conf libperl5.14 (5.14.2-6ubuntu2.3 Ubuntu:12.04/precise-updates [amd64])
Conf libusbmuxd1 (1.0.7-2ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
Conf linux-image-generic-lts-quantal (3.5.0.26.33 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-3.5.0-26 (3.5.0-26.42~precise1 Ubuntu:12.04/precise-updates [all])
Conf linux-headers-3.5.0-26-generic (3.5.0-26.42~precise1 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-generic-lts-quantal (3.5.0.26.33 Ubuntu:12.04/precise-updates [amd64])
Conf linux-generic-lts-quantal (3.5.0.26.33 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-3.2.0-39 (3.2.0-39.62 Ubuntu:12.04/precise-updates [all])
Conf linux-headers-3.2.0-39-generic (3.2.0-39.62 Ubuntu:12.04/precise-updates [amd64])
Conf linux-headers-generic (3.2.0.39.47 Ubuntu:12.04/precise-updates [amd64])
Conf linux-libc-dev (3.2.0-39.62 Ubuntu:12.04/precise-updates [amd64])
Conf nautilus-data (1:3.4.2-0ubuntu7 Ubuntu:12.04/precise-updates [all])
Conf samba-common (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [all])
Conf samba-common-bin (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [amd64])
Conf samba (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [amd64])
Conf smbclient (2:3.6.3-2ubuntu2.4 Ubuntu:12.04/precise-updates [amd64])
Conf usbmuxd (1.0.7-2ubuntu0.1 Ubuntu:12.04/precise-updates [amd64])
```

---

### Post by Bullwinkle_Moose on 2013-03-21
Be patient and wait.  It looks like it may have been doing a linux kernal update and whenever it does one of those, it will appear to stall for what seems like a very long time, but eventually it will move on.

Of course if it has been several hours and it still hasn't moved, then all bets are off.  But a stall of several minutes is not that uncommon, especially if your system is a bit on the old/slow side.

---

### Post by neutron68 on 2013-03-21
> **Bullwinkle_Moose said:**
> Be patient and wait.  It looks like it may have been doing a linux kernal update and whenever it does one of those, it will appear to stall for what seems like a very long time, but eventually it will move on.

Of course if it has been several hours and it still hasn't moved, then all bets are off.  But a stall of several minutes is not that uncommon, especially if your system is a bit on the old/slow side.

All bets are off, then.  ;)

This same thing happened about a week ago when I tried an update. I left the machine on in that apparent stalled state **overnight** (8 hours). 
The next morning, nothing had changed so I shut off the pc and went to work.

I'm guessing there's a new bug?

Eric

---

### Post by bpmod on 2013-03-26
> **neutron68 said:**
> The progress bar moved in the Applying Changes window moved from left to right and all looked fine.  
At around 80%, the window stopped updating.
When I dragged another window over the top of the Update Manager, it was wiped clean - nothing in it, after that.

What does that mean?  
Has it locked up?  
Is one of the updates bad?  
What should I do?

Is anyone else seeing this?
I, too, am seeing this.

It is always at samba-common that it stops. After waiting several hours, I try to stop the update and restart, but it keeps telling me that an update failed and I should do a partial update. Then the partial update fails because the update is already in progress. So, the only solution at that point is to re-install Mythbuntu from scratch.

Brian

---

### Post by GaryP2 on 2013-03-26
I suspect that the Samba update is trying to present you with a dialog prompt to make a  decision on either keeping your current configuration or overwriting it with the package update configuration. I just did an update through the command line last weekend and got prompted to make decisions for both MySQL and also Samba.

I got frustrated when the Update Manager GUI hung in a similar fashion as you are describing and switched over to doing my updates through the command line only now ([see this thread]("http://ubuntuforums.org/showthread.php?t=2083187")). I believe others on this forum recommend ditching Update Manager in favor of command line updates. [Search here]("https://www.google.com/search?q=ubuntu+update+manager+vs+apt-get") to learn about apt-get vs. Update Manager.

```
sudo apt-get update
sudo apt-get upgrade

```
And at least periodically:
```
sudo apt-get dist-upgrade

```

---

### Post by neutron68 on 2013-03-30
I just did search for related bugs and I found one.  It's been unsolved for almost 2 years!

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/674118](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/674118)

---

