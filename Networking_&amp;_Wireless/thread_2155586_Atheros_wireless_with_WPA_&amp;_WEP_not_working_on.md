---
title: "Atheros wireless with WPA &amp; WEP not working on Ubuntu 12.04"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by mr72 on 2013-06-18
Alright. This problem is finally gone too far.

My company changed their wireless networks and now I can't connect my laptop (Acer C7 Chromebook with Ubuntu 12.04) refuses to work on either the WEP guest or the WPA2 production network.

The guest network is plain old WEP and the production network is WPA2:
WPA2 Enterprise
AES
PEAP 1
MSCHAPv2

I have Atheros wifi:
$ lspci | grep Wireless
01:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

And the problems are as follows:

WPA2 authentication fails, even though the credentials are correct. If I leave wireless networking turned on, every couple of minutes it brings up the authentication dialog, and stacks a new one on top of the old one.

the WEP network will authenticate about once after reboot, and then run ok for a while from minutes to an hour. Then authentication fails and it prompts me to enter the passphrase, I enter it over and over and it never authenticates again.

I guess there likely is a bug in the ath9k driver, but I can't take a new kernel to fix it. New kernel will break other things I absolutely require such as VirtualBox. There are some quirks you get running Ubuntu on a Chromebook...

$ uname -r
3.4.0

Can anyone help me find a workaround or a fix? Maybe give me some advice on how to debug this? It is becoming a real serious problem for me.

---

### Post by mr72 on 2013-06-18
Replying to my own query, hoping to prompt responses, maybe it is [this]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/1024508")?

Behavior is similar, if not identical.

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by mr72 on 2013-06-18
> **ahallubuntu said:**
> Have you tried disabling hardware encryption?

[http://www.emmolution.org/?p=253](http://www.emmolution.org/?p=253)

Yes. Isn't that supposed to fix slow connections? I was not having connection speed issues, but I tried it a few weeks ago just in case, and it didn't help with my problem.

---

### Post by mr72 on 2013-06-19
More info:

"WPA & WPA Personal" works (my home network), "WPA2 Enterprise" (office network) does not.

WEP "Shared Key" or "Open System" doesn't make a difference, neither works.

So WEP and WPA2 Enterprise are both broken ... but WPA Personal works.


I have a capture of /var/log/syslog applicable to NetworkManager during one of these failed attempts to connect, if this will help diagnose the problem.

---

### Post by mr72 on 2013-06-19
OK, still no interest here, but I think maybe this is related:

[https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343)

---

### Post by mr72 on 2013-06-20
I tried Diane Trout's fix in [comment #21]("https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/969343/comments/21"), which allowed it to connect once but then a few minutes later it disconnected and refuses to authenticate a second time. This fix, however, continued to work correctly for my home network which is WPA Personal. I am going to continue experimenting and see if I can't get it to work more than once, but once is more than it ever worked before.

Here's how to install this alternate version.

```

sudo apt-add-repository ppa:diane-trout/wpasupplicant-gnutls
sudo apt-get update
sudo apt-get remove wpasupplicant
sudo apt-get install wpasupplicant=0.7.3-6ubuntu3.gnutls1
sudo apt-get install network-manager

```

Removing wpasupplicant will alsporemove network-manager, which is why you have to reinstall it after adding the gnu. Easiest after doing this to reboot in order to get everything working.

---

### Post by mr72 on 2013-06-28
Does anyone have input to this issue? I really need to get it fixed. All help is appreciated.

---

### Post by mr72 on 2013-07-01
Am I posting this in the wrong forum? Where should I go to get help resolving this issue?

---

### Post by qi.qi84 on 2013-10-28
Hi OP,

I've just installed Ubuntu 12.04 yesterday and I'm experiencing similar issues. My wireless PCI card is: atheros ar 5614. Its a desktop wireless card and the reason im using this is because my modem is on the other side of the lounge room.

Did you end up getting your connection issues resolved?

If you have can you please kindly advice how this is done?

Thank you.

> **mr72 said:**
> Alright. This problem is finally gone too far.

My company changed their wireless networks and now I can't connect my laptop (Acer C7 Chromebook with Ubuntu 12.04) refuses to work on either the WEP guest or the WPA2 production network.

The guest network is plain old WEP and the production network is WPA2:
WPA2 Enterprise
AES
PEAP 1
MSCHAPv2

I have Atheros wifi:
$ lspci | grep Wireless
01:00.0 Network controller: Atheros Communications Inc. AR9462 Wireless Network Adapter (rev 01)

And the problems are as follows:

WPA2 authentication fails, even though the credentials are correct. If I leave wireless networking turned on, every couple of minutes it brings up the authentication dialog, and stacks a new one on top of the old one.

the WEP network will authenticate about once after reboot, and then run ok for a while from minutes to an hour. Then authentication fails and it prompts me to enter the passphrase, I enter it over and over and it never authenticates again.

I guess there likely is a bug in the ath9k driver, but I can't take a new kernel to fix it. New kernel will break other things I absolutely require such as VirtualBox. There are some quirks you get running Ubuntu on a Chromebook...

$ uname -r
3.4.0

Can anyone help me find a workaround or a fix? Maybe give me some advice on how to debug this? It is becoming a real serious problem for me.

---

