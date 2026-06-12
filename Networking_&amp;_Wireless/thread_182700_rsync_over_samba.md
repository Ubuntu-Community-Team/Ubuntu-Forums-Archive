---
title: "rsync over samba?"
date: 2006-05-26
forum: Networking &amp; Wireless
---

### Post by extraspecialbitter on 2006-05-26
I have a small home LAN consisting of 5 Windows XP clients and 2 Ubuntu Breezy clients.  All connect to the internet without problems via a Netgear FVS318 router.  All share folders and a pair of printers via Samba.  What I'd like to do now is to back up directories between the two Ubuntu boxes using rsync.  The problem is that while the individual hostnames are visible to samba (using "smbclient -L <hostname>"), they cannot be seen in DNS.  I can ping IP addresses, but cannot perform a reverse lookup to retrieve the hostname.

Further complicating matters is the fact that rsync doesn't seem to want to work via IP address:

[FONT="Courier New"]
pablo@ubuntu=> rsync -avz /home/pablo/mp3/Insound/ pablo@192.168.0.7:/home/pablo/mp3/Insound/
ssh: connect to host 192.168.0.7 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)[/FONT]

Nor will it work to an smbmounted filesystem:

[FONT="Courier New"]pablo@ubuntu=> sudo smbmount //grandpaboy/home /mnt
Password:
pablo@ubuntu=> /home/pablo/mp3/Insound/ pablo@ubuntu=>
pablo@ubuntu=> rsync -avz /home/pablo/mp3/Insound/ /mnt/pablo/mp3/Insound/
building file list ... done
./
rsync: failed to set times on "/mnt/pablo/mp3/Insound/.": Operation not permitted (1)
BRMC_AintNoEasyWay.mp3
CRIB_hey_scenesters.mp3
...
washingtonsocial.mp3
wow_and_flutter_freezer_burn.mp3
yoyo.mp3
zero_zero_back_to_hell.mp3
rsync: mkstemp "/mnt/pablo/mp3/Insound/.BRMC_AintNoEasyWay.mp3.52Apzg" failed: Permission denied (13)
rsync: mkstemp "/mnt/pablo/mp3/Insound/.CRIB_hey_scenesters.mp3.KKUZ1E" failed: Permission denied (13)
...
rsync: mkstemp "/mnt/pablo/mp3/Insound/.washingtonsocial.mp3.6KDcmY" failed: Permission denied (13)
rsync: mkstemp "/mnt/pablo/mp3/Insound/.wow_and_flutter_freezer_burn.mp3.CQNKIC" failed: Permission denied (13)
rsync: mkstemp "/mnt/pablo/mp3/Insound/.yoyo.mp3.9XOiyj" failed: Permission denied (13)
rsync: mkstemp "/mnt/pablo/mp3/Insound/.zero_zero_back_to_hell.mp3.HUrRd2" failed: Permission denied (13)
rsync: failed to set times on "/mnt/pablo/mp3/Insound/.": Operation not permitted (1)

sent 180561725 bytes  received 1192 bytes  6813694.98 bytes/sec
total size is 185684196  speedup is 1.03
rsync error: some files could not be transferred (code 23) at main.c(791)
[/FONT]

I can use a standard copy command to the smbmounted filesystem, or cut and paste between the local and network file browsers, but I'd like to eventually script and automate the process, while also taking advantage of rsync's ability to copy only files that have changed. 

Can anyone help?  :confused: 

Thanks in advance...

---

