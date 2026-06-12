---
title: "Configuring Wired Network Authentication 802.1x"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by ajblanck on 2011-02-04
Hello,

I just installed Ubuntu on my laptop and I'm having a bit of difficulty connecting to the internet. I'm at the University of Pittsburgh, and like many other colleges, we have to authenticate in order to use the wired ethernet connections in our rooms.

I've tried to use the network manager to connect by enabling 802.11x authentication, and changing the settings to the following:

Authentication: PEAP
Anonymous Identity: tried both blank and my user nameInner Authentication: MSCHAPv2
CA Certificate: I used the certificate that my school supplies

After entering these settings and some other variations, I always just see the network icon look like it's connecting or searching but I never am connected to the network. Sometimes I'm thrown back to the configuration panel where I entered by username and password, but I never get an error or any kind.

My searches on this forum lead me to many mentions of wpa_supplicant for authentication, but I'm not sure if that's necessary anymore with Ubuntu 10.10 since I found some mentions that network manager now uses wpa_supplicant

Other info on my system:
Computer: MacbookPro 6.2
Ubuntu Version: 10.10

If anybody has any advice, I would appreciate it. I apologize if I have missed some other obvious answer here on the forum, but I wasn't able to locate anything relating to this issue that was posted recently

Thanks in advance!

---

### Post by ajblanck on 2011-02-05
*bump*

---

### Post by ajblanck on 2011-02-07
*bump*, again

If there's anything that I can post that would make this problem easier to diagnose, please tell me and I'll gladly post the output of whatever commands would be useful.

---

### Post by ajblanck on 2011-02-08
Okay, so here's some of the Network Manager's output in /var/logs/daemon.log

The line: "Activation (eth0/wired): connection 'PITTNET' requires no security. No secrets needed." seems strange. This connection should require security, unless I am misunderstanding something.

```

Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0/wired): asking for new secrets
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): device state change: 6 -> 4 (reason 0)
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0/wired): connection 'PITTNET' requires no security. No secrets needed.
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): supplicant interface state:  starting -> ready
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'password' value '<omitted>'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'key_mgmt' value 'IEEE8021X'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'eapol_flags' value '0'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'eap' value 'PEAP'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'fragment_size' value '1300'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'phase1' value 'peapver=0'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'ca_cert' value '/home/alex/Documents/updated-verisign-intermediate-certificate.cer'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: added 'identity' value '<omitted>'
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> Config: set interface ap_scan to 1
Feb  8 00:52:13 Alex-MBP-Linux NetworkManager[661]: <info> (eth0) supplicant connection state:  disconnected -> associated
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <warn> Activation (eth0/wired): association took too long.
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): device state change: 5 -> 9 (reason 7)
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <info> Marking connection 'PITTNET' invalid.
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <warn> Activation (eth0) failed.
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): device state change: 9 -> 3 (reason 0)
Feb  8 00:52:38 Alex-MBP-Linux NetworkManager[661]: <info> (eth0): deactivating device (reason: 0).

```

---

### Post by ajblanck on 2011-02-10
It's amazing that nobody has replied to this thread yet. I'm sure someone has experienced this type of situation before.

I'd really appreciate some suggestions from anyone, as it's difficult to do much with Ubuntu without an Internet connection.

---

### Post by ajblanck on 2011-02-24
I'm quite baffled by the complete lack of responses here. Ubuntu is known for its great community support, but clearly some posts (like this one) fall through the cracks. Could someone please reply to this thread?

---

### Post by Rhizoid on 2011-02-25
Hi,

Sorry you've had no other responses... I've just started a very old laptop which is running 10.10 and which was working fine with a wired connection the other day - but which now cannot connect via wired or wireless connection - similar errors it seems.

Bear with me while I have a read of the logs and see if I can make head or tail of anything - you are not alone.

---

### Post by Rhizoid on 2011-02-25
Ok - turns out mine wasn't so complicated.  Unfortunately, they're also possibly not as related as I first thought.

Today I've had a spate of new devices attached to my home network and it runs a very limited DHCP scope - circa 10 addresses with a 12 hour lease cycle.  Long and the short was I was out of addresses to lease.  A quick prune of non-existent devices and my old laptop connects just as it ever did.

Sorry this isn't likely to be of much use in directly addressing your problem - however, the "took too long" message in the log you posted is very similar, well worth checking with the network management that you've got credentials correct as an incorrect password or too many incomplete connection attempts (read as suspended user a/c) might be the cause.

Keep us updated with how you get on ;)

---

### Post by ajblanck on 2011-02-27
Yeah, that does sound like you had a different issue. Thanks for trying to help.

My problem is almost certainly with the authentication step of connection. I have not tried the computer on a normal wired connection that does not require authentication, but I suspect it would work fine. I have been able to connect the computer to non-WPA Enterprise hotspots. I know that I have the correct credentials as well, as I am able to connect successfully with both mac osx and windows 7. If anybody else has some ideas, I'd appreciate them.

I'd also like to note that this thread seems like it was viewed a fair amount of times. I suppose that there are other people in my position coming across this thread while looking for a solution via Google.

---

### Post by macrowiz49 on 2011-05-15
Gah... I'm having the same problem with the same settings you posted.  In Maverick, I just installed wicd and removed network manager, and that seemed to work fine.  This doesn't work on Natty though, I keep getting a "bad password" error when I use wicd. Not sure what to do now :/

---

### Post by ajblanck on 2011-05-15
> **macrowiz49 said:**
> Gah... I'm having the same problem with the same settings you posted.  In Maverick, I just installed wicd and removed network manager, and that seemed to work fine.  This doesn't work on Natty though, I keep getting a "bad password" error when I use wicd. Not sure what to do now :/

I eventually did the same thing (using wicd instead of network manager). However, this only worked on wifi. I couldn't get wicd to authenticate on the wired network; it looks like that might not be supported. I have not tried this on Natty although I did just update.

---

### Post by teriyaki-89 on 2012-05-02
i am having the same problem but my pc sometimes connects to network via 802.1x and sometimes not. I was using network-manager and suppose there is some bugs with network manager, cause network sniffs showed no packages were going out my interface when i could not connect to network with 802.1x security

What helped is **/etc/init.d/network-manager restart**

Does anyone have scripts so i write 802.1x information to /etc/network/interfaces not using network manager?

Does anyone know how to fix bug?

---

