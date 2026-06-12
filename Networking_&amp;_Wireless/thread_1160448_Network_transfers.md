---
title: "Network transfers"
date: 2009-05-15
forum: Networking &amp; Wireless
---

### Post by John Long on 2009-05-15
I'm transfering a few hundred gigabytes of files from a 7.10 box to 9.04 box over a Linksys WRT54G router. Both computers are less than a year old and say they have 10/100/1000 network cards but my transfer rates are only 5-7 MB/sec.

Shouldn't the transfer be going faster and if so, how can I increase it? I have about 20 hours left...

Thanks for the help! 

Johnny

---

### Post by puppywhacker on 2009-05-15
5-7 MegaByte/sec is 40-56 megabit/sec. The wrt54g is a 100 mbit/sec switch. where 100mbit/sec is the theoretical max which you'll never actually get to see, 75% of that is already a miracle. The transfer method itself is also of influence, ethernet chops everything into 1500 byte blocks and this takes some time. some modern nic's support jumbo-packets, but it's hardly used.

To copy a lot of data quickly connect the two pc's without switch (use a crossover cable if none of your interfaces support autosensing)

Even quicker is to stick the harddisk in the other machine, nothing beats an internal bus-transfer.

---

### Post by John Long on 2009-05-16
Great, thanks for the info! Both my NICs have autosensing, how do I connect them? I plug them together and it appears to connect but then what?

Thanks again,
Johnny.

---

### Post by puppywhacker on 2009-05-17
ok,

check that your ethernet-link is up and speedy

```
sudo mii-tool eth0

```
next you assign them ip-addresses so they can talk to eachother in the same ip-range, e.g. 192.168.11.1 and 192.168.11.2. you can temporary assign them in a terminal. it won't survive a reboot. 

```
ifconfig eth0 192.168.11.1
```

next you can copy files using ftp where you have one server like proftpd and one client. ftp isn't encrypted, but that speeds up operations.

```

ftp user@192.168.11.2
get /home/user
```

maybe easier is to use scp or sftp between the computers, since you don't have to setup a server for that, maybe an sshd-server if not installed by default. The thing is that the default encryption cipher is AES which is considered uncrackable, but it comes with a performance cost, so use the weak cipher rc4 to copy bulk data

```
scp -c arcfour user@192.168.11.2:/home/user /home/backup

```

---

