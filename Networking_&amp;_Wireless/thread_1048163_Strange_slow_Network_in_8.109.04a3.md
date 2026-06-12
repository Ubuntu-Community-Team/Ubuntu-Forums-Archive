---
title: "Strange slow Network in 8.10/9.04a3"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by masakari on 2009-01-23
Hello,

i have a really weird problem with two installations of ubuntu. I experimented a lot so i have to explain.

i have 2 machines using ubuntu 64bit, a notebook with gbit nic, and a self made little server (asus a8n sli) with two onboard nics gbit, and one e1000 pci adapter for testing. i want to copy larger files (1gbyte and more) over network and used sftp via openssh on both, and copied them from a winxp64 machine (filezilla, which works fine, makes the 90mbyte/s easily with raid system).

but both machines only get 10-15 mbyte/s. the harddrives are bored, they definitely can handle more than that.

i switched to an ftp server, but same speed. thought of bad cable, changed it, no difference. tested the switch and got an debian raid5 server from my friend, 90mbyte/s...

downloaded from internet an iso image on the ubuntu machine, with only 300kbyte/s. same download, same server on windows with 750kbyte/s which could me my bandwith limit. testet ubuntu 9.04 alpha with no differnece, slow. i am trying opensuse 11.1 today on the server but my notebook wont be changed, because it runs fine except for that network problem.

is there anything i can use to test the network? i dont see the bottleneck, status monior says cpu is bored, memory just fine and network not fully occupied.
maybe i should test the server version on it? someone steals about 3/4 of my bandwith :-(

---

### Post by netztier on 2009-01-23
> **masakari said:**
> Hello,
but both machines only get 10-15 mbyte/s. the harddrives are bored, they definitely can handle more than that.


[SIZE="4"]**1. harddrive performance**[/SIZE]
Check the drive's performance with **sudo hdparm -tT /dev/sdXn** to see if they actually do work well. On my dualcore laptop (HP Compaq 6910p), this looks like follows. I should add that /dev/sda is *not* the internal SATA disk (that one should be considerably faster than 32MB/sec), but a PATA disk in the MultiBay slot.

```
marc@torch:~$ sudo hdparm -tT /dev/sda1
/dev/sda1:
 Timing cached reads:   5934 MB in  2.00 seconds = 2974.26 MB/sec
 Timing buffered disk reads:   98 MB in  3.04 seconds =  32.27 MB/sec
```
 
My old server (P-III 500MHz) with a SATA RAID-1 (/dev/md2) setup shows this:

```
marc@blaze:~$ sudo hdparm -tT /dev/md2
/dev/md2:
 Timing cached reads:   266 MB in  2.00 seconds = 132.88 MB/sec
 Timing buffered disk reads:  136 MB in  3.04 seconds =  44.80 MB/sec

```

Then, try **iPerf** from the universe repositories to do a raw TCP throughput test.

[SIZE="4"]**2. raw TCP**[/SIZE]

on the computer receving the data stream:
```

user@client:~$ **iperf -s**

```
on the computer sending the data:
```

user@server:~$ **iperf -c <client's IP> -t 30 -i 5**

```

This should give numbers in the high-hundreds of Mbit/s - depending on the hardware and NIC performance. This gives you a ballpark figure about what these computers' network-I/O subsystems are capable of - and of course about the network between them.


[SIZE="4"]**3. tcp stream from file** [/SIZE]
on the computer receiving the data stream:
```

user@client:~$ **iperf -s**

```
on the computer sending the data (reading 1000Megs from /path/to/file):
```

user@server:~$ **iperf -c <client's IP> -n 1000M -F /path/to/file -i 5**

```

This should give numbers in the range of how fast the disk-I/O subsystem and the network-I/O subsystem can work together on the sender system. 

The reason why I suggest iPerf instead of ftp, scp, samba or nfs for this test is precisely the nature of these protocols: they all have more or less protocol overhead that will impact performance. Before going down the "which protocol is best and how do I tune it?" road, it's better to do a few basic tests first and go into the complexity later on. 


regards

Marc

---

### Post by masakari on 2009-01-23
that are exactly the informations i needed, i will test it when i am at home. 
with my notebook i can make my tests here but it is not so important. it works and i have no need to tune it...

thanks, i will post withe the results i get.

---

### Post by masakari on 2009-01-23
seems a little bit strange...

/dev/sda1:
 Timing cached reads:   1210 MB in  2.00 seconds = 605.23 MB/sec
 Timing buffered disk reads:  228 MB in  3.01 seconds =  75.86 MB/sec


from server to notebook:

[  3]  0.0- 5.0 sec    101 MBytes    170 Mbits/sec
[  3]  5.0-10.0 sec  68.2 MBytes    114 Mbits/sec
[  3] 10.0-15.0 sec  66.4 MBytes    111 Mbits/sec
[  3] 15.0-20.0 sec  66.3 MBytes    111 Mbits/sec
[  3] 20.0-25.0 sec  67.4 MBytes    113 Mbits/sec
[  3] 25.0-30.0 sec  68.6 MBytes    115 Mbits/sec
[  3]  0.0-30.0 sec    438 MBytes    122 Mbits/sec

it seems ok for me but anyway... 14mbyte/s seems to slow when using sftp. i am testing opensuse now on the server. maybe i will learn more about it. final goal is ubuntu or debian server on this machine...


*edit*
done it the other way from notebook to server..

[  3] local 192.168.123.16 port 60573 connected with 192.168.123.14 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec    197 MBytes    330 Mbits/sec
[  3]  5.0-10.0 sec    216 MBytes    363 Mbits/sec
[  3] 10.0-15.0 sec    309 MBytes    518 Mbits/sec
[  3] 15.0-20.0 sec    216 MBytes    362 Mbits/sec
[  3] 20.0-25.0 sec    232 MBytes    389 Mbits/sec
[  3] 25.0-30.0 sec    330 MBytes    554 Mbits/sec
[  3]  0.0-30.0 sec  1.47 GBytes    420 Mbits/sec

his hardrive performance
/dev/sda1:
 Timing cached reads:   960 MB in  2.00 seconds = 480.01 MB/sec
 Timing buffered disk reads:  140 MB in  3.03 seconds =  46.20 MB/sec

*edit2*
Client connecting to 192.168.123.16, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.123.14 port 56291 connected with 192.168.123.16 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec  1.31 Gbits    262 Mbits/sec
[  3]  5.0-10.0 sec  3.11 Gbits    622 Mbits/sec
[  3] 10.0-15.0 sec  3.40 Gbits    681 Mbits/sec
[  3]  0.0-15.8 sec  8.39 Gbits    531 Mbits/sec

done with 1000M parameter. no i am installing and testing... good to have 3 computers :-)

---

### Post by masakari on 2009-01-24
Ok, here a little update what i found out.

installed suse, wont work with my usb devices so i skipped it. installed debian, performance was about 20% slower than ubunut (sick). installed windows xp64 with stupid filezilla, 100 mbyte/s.... performance was amazing.

argh, i am starting to think that something went wrong with my board and any debian based distribution. maybe i test fedora or gentoo. 

everything feels like 100mbit on it. i dont want a windows server its stupid. i want my sftp.

---

### Post by netztier on 2009-01-25
> **masakari said:**
> installed windows xp64 with stupid filezilla, 100 mbyte/s.... performance was amazing.


Which protocol does filezilla use? 

If it's SFTP or SCP, which encryption mechanisms does it use?

---

### Post by masakari on 2009-01-25
i switched completely to ftp now. the cpus of different machines might be to different to compare.

tested a lot, this is what i found out:

a8n-sli premium normally nvidia onboard nic, but also tested e1000 pci and onboard marvell sometimes with no difference
debian 4.06 64bit slow speed with vsftp ~10mbyte/s
ubuntu 8.10/9.04a3 64bit slow speed vsftp and pureftp ~15mbyte/s
ubuntu 8.10 32bit slow speed vsftp ~15mbyte/s
win xp 64bit with filezilla server ~65 mbyte/s
fedora 10 64bit vsftp ~65 mbyte/s
the numbers from iperf are accordingly, max speed of the a8n-sli was only about 200mbit. 

my notebook was slow because of the sftp. i will try an ftp server on it sometimes.

tested ubuntu 8.10 64bit on my phenom with ati chipset (m32a something i dont remember...) iperf was about 450 mbit, with 64kbyte tcp window it was up to 800mbit. i couldnt installed ftp cause i had no suitable client which would be fast enought to hit this cap. this is a very nice ubuntu machine i should add, working like hell.... sadly i have to use windows cause its a working machine i need with some software.

i am currently thinking of testing an msi k8n with ubuntu. its the machine i gave to my father he will miss it if i take it so long so i need a suitable time frame for it.
next idea is to buy another phenom, but thats a little bit waste of money i think.

i never used fedory before, i like the apt packaging and other stuff from debian so i try to get another mobo test, maybe i can change it.

---

### Post by masakari on 2009-01-27
tested a msi 7125 board, same chipset same sata subsytem, same problem. 
i have no idea where the problem exactly is. my notebook runs about 30 mbyte/s with his ftp. its not really fast but its ok.

the only solution i have is to switch to a new board or using another distribution.

---

### Post by masakari on 2009-01-29
installed everything now. i am using ubuntu 8.04 amd64 now, mdadm software raid, with an truecrypt ext3 on it.

md-resync consumes a lot of cpu power, but i think i can solve this with completely reformating it. 

network speeds are good. i had about 70mbyie/s from my single drive, an about 50 mbyte/s from my truecrypt raid with resync running in background. if resync is complete i think i get over 80 mbyte with the raid whisch is perfekt for me. 

i think that nforce4 support ist partially broken wirh a newer ubuntu version than 8.04,

---

