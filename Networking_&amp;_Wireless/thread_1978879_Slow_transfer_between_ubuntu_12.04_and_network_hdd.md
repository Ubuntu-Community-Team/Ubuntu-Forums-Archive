---
title: "Slow transfer between ubuntu 12.04 and network hdd"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by joehc on 2012-05-12
Hey guys

When I transfer a file from my ubuntu machine to my network hard drive it is extremely slow, like 100 kb/s.

My machine has ubuntu 12.04, and has a wired connection to my router. My extern hard drive is connected to my WD TV LIVE which also is wired connected to my router.

The funny thing is that, if I switch to Windows, the speed is just fine. And when I used ubuntu 10.04 there were no problems with the speed.

I have install samba, and even if I mount the network hard drive or just use network explore in nautilus it is the same slow speed.

Can anyone help me?

---

### Post by ashgla on 2012-05-18
Yep, they appear to have broken something.
I have 2 other pcs at home with 10.?? and 11.04 installed and all mount a vfat NAS drive. I add a line into /etc/fstab using smbfs. Reasonable response fro the server with the older systems.

Installed 12.04 on 4 year old Dell Vostro. 
12.04 is very slow talking to the NAS samba server. Even the file manager is slow in just showing me the files in a directory. The server hosts all my Thunderbird email folder so that any machine can get to them and this takes about 30 seconds to just open and then is very slow retrieving files. I tried changing the fstab driver to cifs but its the same thing.

Any help would be appreciated.

---

### Post by joehc on 2012-05-18
> **ashgla said:**
> Yep, they appear to have broken something.
:(

---

### Post by sebboon on 2012-05-18
So am I !!

My 12.04 Ubuntu Server has really slow data transfert.

The network interface works great up to 1.6 MB from the net.

But the network share (with samba and nfs) doesn't provide a better transfert rate than 30 kb/s from server to client.

But I can send a file from client to server at 11 Mb/s (from Samba) .... 

I'm about to install a fresh debian to check if the problem also exists....

---

### Post by joehc on 2012-05-19
> **sebboon said:**
> So am I !!

My 12.04 Ubuntu Server has really slow data transfert.

The network interface works great up to 1.6 MB from the net.

But the network share (with samba and nfs) doesn't provide a better transfert rate than 30 kb/s from server to client.

But I can send a file from client to server at 11 Mb/s (from Samba) .... 

I'm about to install a fresh debian to check if the problem also exists....

pls give an update of how it went

---

### Post by sebboon on 2012-05-19
I've just installed Debian 6.05

_Same issue with Samba :_
server to client = 50 kb/s
client to server = 10 000 kb/s

(I don't try nfs share yet ... )

#WTF ?

---

### Post by ashgla on 2012-05-19
Follow up from post above.
Trashed 12.04 and took my 11.04 and 11.10 ubuntu install disk and reinstalled onto the Dell Vostro. Still really poor network link to my samba server. Note I have these systems on an Acer Netbook and a Dell desktop with good network speed.

So ... this is interesting. It's clearly not the 12.04 install that's causing the slowdown which leaves only 2 options.
1- My dell Vostro is causing the problem. Unlikely since web browsing speeds are fine
2- latest smbfs is broken. I apt-get smbfs and then add the line into fstab. How can I install an older version of smfs?

---

### Post by Morbius1 on 2012-05-19
> **ashgla said:**
> 2- latest smbfs is broken. I apt-get smbfs and  then add the line into fstab. How can I install an older version of  smfs?
I don't have an answer to your dilemma but I would like to point out that smbfs is deprecated.

The package "smbfs" is a dummy package that has only one dependency and that is it's replacement: **cifs-utils**.

You might want to go into fstab and replace "smbfs" with "cifs" and see if it has any affect on speed.

---

### Post by joehc on 2012-05-20
> **Morbius1 said:**
> I don't have an answer to your dilemma but I would like to point out that smbfs is deprecated.

The package "smbfs" is a dummy package that has only one dependency and that is it's replacement: **cifs-utils**.

You might want to go into fstab and replace "smbfs" with "cifs" and see if it has any affect on speed.
Im not that experienced with fstab, but how does smbfs effect the network explore in nautilus? Should I uninstall smbfs and just have cifs installed?

---

### Post by sebboon on 2012-05-21
I also tried to update my ethernet driver (downgrade to r8168 from r8169 [realtek])

without success... it sucks I will reinstall a 11.04 version asap

---

### Post by joehc on 2012-05-31
Any news on this matter?

---

### Post by sebboon on 2012-05-31
For me it was a PEBKAC applied to network...

**PEBCAS** : Problem Exists Between Client And Server

When I upgraded my server I also add some ram modules and do I exchanged some cable...

My bug was a deffective RJ45 cable ... I can notice before because it was plugged on another read-only machine.

The only thing I have done before changing the cable is to downgrade my network driver realtek r8169 to r8168, by adding a new package repository taht old propretary firmware (nonfree)(debian repo, since I have migrate to debian) 

To check if your network adapter is a realtek, you can type this :
```
lspci | grep r816
```

Good Luck !

---

### Post by joehc on 2012-05-31
> **sebboon said:**
> For me it was a PEBKAC applied to network...

**PEBCAS** : Problem Exists Between Client And Server

When I upgraded my server I also add some ram modules and do I exchanged some cable...

My bug was a deffective RJ45 cable ... I can notice before because it was plugged on another read-only machine.

The only thing I have done before changing the cable is to downgrade my network driver realtek r8169 to r8168, by adding a new package repository taht old propretary firmware (nonfree)(debian repo, since I have migrate to debian) 

To check if your network adapter is a realtek, you can type this :
```
lspci | grep r816
```

Good Luck !

Well, I get this:

 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

So I should find another driver version?

---

### Post by ashgla on 2012-06-02
I've solved this issue for myself. I did fresh installs on an old Dell Vostro. 12.04 then 11.xx then 10.xx and all slowed down my wireless transfer dramatically (see posts above).

After a lot of screwing around I suspected the network card driver. The answer is that the Vostro has a low power version of the Broadcom wifi chip... from lspci .

 Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

I suspected that Ubuntu was installing the driver for the regular chip. The regular chip driver can be installed with ...

 sudo apt-get install firmware-b43-installer

Removing the Ubuntu installed driver and using the above command line gave the same painfully slow network but ... installing the low power version ...

  sudo apt-get install firmware-b43-lpphy-installer

has my network running at its usual fast pace.

---

### Post by joehc on 2012-06-03
> **ashgla said:**
> I've solved this issue for myself. I did fresh installs on an old Dell Vostro. 12.04 then 11.xx then 10.xx and all slowed down my wireless transfer dramatically (see posts above).

After a lot of screwing around I suspected the network card driver. The answer is that the Vostro has a low power version of the Broadcom wifi chip... from lspci .

 Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

I suspected that Ubuntu was installing the driver for the regular chip. The regular chip driver can be installed with ...

 sudo apt-get install firmware-b43-installer

Removing the Ubuntu installed driver and using the above command line gave the same painfully slow network but ... installing the low power version ...

  sudo apt-get install firmware-b43-lpphy-installer

has my network running at its usual fast pace.
Thanks for your answer

But does this not only concern wireless connection? I am using lan-connection and still I have the slow transfer

---

### Post by joehc on 2012-06-08
bump

---

### Post by kid1000002000 on 2012-06-21
Some of us are having related issues. Have you tried from a Windows client to the linux samba server?

see:
[https://bugzilla.samba.org/process_bug.cgi](https://bugzilla.samba.org/process_bug.cgi)
[http://www.overclockers.com/forums/showthread.php?t=683188](http://www.overclockers.com/forums/showthread.php?t=683188)

---

### Post by joehc on 2012-06-22
Wuhu, it just automitically started working. Must have been an update. Anyone else who can confirm this?

---

### Post by GerMulvey on 2012-07-12
i have the same issue.
win7 network speed perfect, ubuntu 12.04 very slow speed to same pc

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
and I have changed driver to R8168 driver but still get transfers under 100kB/s


ubuntu 12.04 64 bit btw - still can't change my user details!

Even stranger - sme network to another pc 86 MB file 2 seconds to the other pc 14 mins for the same file yet in windows 2 seconds. 
Could this be a pc specific issue to the one machine perhaps?

---

### Post by Ghilteras on 2012-07-17
same identical problem here with ubuntu 12 and lspci:


04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)


if I upload a file from win to linux I get 100-200kb/s which is SLOW, but if I do the other way around I'm 30kb/s which is total crap.

must find a fix asap, cannot have a LAN like this

---

### Post by The Foz on 2012-08-08
I am having similar problems.

I have Ubuntu 10.04, which shares file systems using Samba. My Windows 7 client is able to read files at only 1.5Mbps. A Windows-XP client Virtual Machine is able to read files at around 50Mbps (i.e. using Samba, but not using the network adaptor).

I have a "Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 21)", so not the low power version of the chip described in some of the posts above.

---

### Post by futo on 2013-01-06
[SIZE=1]Same problem with 12.04 and Samba getting files from a NAS.

My laptop is with the newest i7 3840qm 2.8 GHz for mobile units, ssd & ordinary hd, r8168 eth. card and a lot of other fine stuff. The driver for the network card is the r8168-driver and not the r8169-driver which comes with a Ubuntu/kernel installation.

Describing (and showing) the problem here also: [http://youtu.be/cSZ9X9y9_hc](http://youtu.be/cSZ9X9y9_hc)

Have tried to add the&#65279; following two lines&#65279; (placed under 'Misc', all 3 combinations)&#65279; in /etc/samba/smb.conf:
SO_RCVBUF=8192 SO_SNDBUF=8192
socket options = TCP_NODELAY

- First when I wrote them in ONE LINE, like this, it worked a little better:
socket options = TCP_NODELAY&#65279; SO_RCVBUF=8192 SO_SNDBUF=8192

- The speed jumped from 1MB or less to around 3 MB. Nice, but still not anything like 1000Mb/s


Checked eth0 with mii-tool and ethtool:

mii-tool says half duplex and ethtool says full duplex.
Tried to change the setting 'in' mii-tool, but that didn't change anything.
Don't know&#65279; why the different results and what to try at this point to manage these two different results.

-------------------------------

Here the formulation of the problem from the YouTube page:

The NAS and the Ubuntu 12.04-laptop are connected to the same switch - and these three parts run a 1000 Mbit/s-network.

The Ubuntu 10.04-PC is connected to the internet-routeren with a 100 Mbit/s-network - and this internet-routeren feeds also the switchen where the NAS and the Ubuntu 12.04-laptop is connected to.

THE PART OF THE NETWORK WITH 1000 Mbit/s:
The NAS can deliver op to 100 MByte/s = 800 Mbit/s (losely calculated)
The network of the switch can deliver 1000 Mbit/s = 125 MByte/s (losely calculated)
The Ubuntu 12.04-laptop runs with 1000 Mbit/s and a test shows that it downloads from the NAS with around 8.0 MByte/s = 16 Mbit/s (losely calculated). (THIS SLOW SPEED IS A PROBLEM!)

THE PART OF THE NETWORK WITH 100 Mbits/s:
The network of the internet-router delivers 100 Mbit/s = 12.5 MByte/s (losely calculated)
The Ubuntu 10.04-PC runs 100 Mbit/s and a test shows that it downloads from the NAS with around 4.7 MByte/s. (only half of the possible speed, but not the problem right here)

As I was chatting on a IRC channel next to testing the download from the NAS I came on the idea to isolate the switch from the router - not that this interfered with the download between the NAS and the Ubuntu 12.04-laptop. The speed dropped to far under 1 MByte/s !!! even thou it is supposed to be between 50 MByte/s and 100 MByte/s !!! ...

... thus confirming the original test (from when the video was uploaded) described in the following:



First I store from the Ubuntu 10.04-PC some bulky files around 14 GB on the LaCie. This runs with 9.3 MByte/s. This speed fits perfect into the capacity of the 100 Mbit/s ethernet card of this computer.

When the files are completely transferede to the NAS server I go on with the next steps.

From the Ubuntu 12.04-laptop (a brand new laptop by Okt. 2012 with all of the best) I now drag and drop the same files from the NAS server to the desktop. The transfer rate is now ONLY 1 - 2 MB/s !!! - What happens?... This is actually a computer with a 1.000 Mbit/s ethernet card!!! A card ten times faster than that on the other computer.


NO COMES THE FUNNY PART: While the Ubuntu 12.04-laptop is fetching the data from the NAS, I now start to fetch another big bulky file from the same NAS to the desktop on same computer. When these two cuncurrent transfers are running from the same NAS to the same computer, then the transfer rate jumps to what ist expected: around 50 - 100 MByte/s. ... Thats weird!

As soon as the second transfer stops, the speed of the first transfer drops to 1 - 2 MByte/s again.

Crazy stuff! - What happens?... Is it Lacie, Ubuntu or Samba?...


-------------------------

Came on the idea to try a sftp session to the NAS from the 12.04-machine. Speed is around 4.7 MB/s.

Could this exclude Samba as reason?... Is it more in eth0/TCP somewhere the problem lies?.... [SIZE=1]Are there any config[SIZE=1]uration-files for the network-card or TCP somewhere?....[/SIZE][/SIZE]

-------------------------

Using testparm didn't reveal anything interesting, as far as I can see:

```
laila@laila:~$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
ERROR: lock directory /var/run/samba does not exist
ERROR: pid directory /var/run/samba does not exist
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    print ok = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
```
[/SIZE]

---

### Post by GregorDS on 2013-07-17
I noticed that If I transfer one file the speed is not great but is acceptable (6.5Mb/s) but if I start a new transfer the speed drops to less than half the previous rate AND NEVER REGAINS original speed if the second file finishes or is stopped.

---

