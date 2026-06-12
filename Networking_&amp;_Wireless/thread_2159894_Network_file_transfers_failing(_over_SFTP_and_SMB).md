---
title: "Network file transfers failing( over SFTP and SMB)"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by Gfurst on 2013-07-04
I'm trying to transfer large files between to machines with Ubuntu recently installed. 13.04

First time I've tried using my wi-fi lan at home, connecting over with Nautilus built-in sftp. The transfer was very slow, below 100kb/s.
I'd just thought it might be wi-fi bad signal and interference, its pretty bad here, however internet was way faster than straight lan.

After sorting out my wi-fi, i thought about connecting both laptop and netbook through a lan cable, after researching a bit found i could do just that.
Setting the wired ipv4 option for Link-Local only, it worked, pinged fine and even connecting through sftp i could see all files on the other side.
However trying to copy the files i want, transfer begins, slowly, still below 100kb/s, after a few seconds the transfer hangs there, can't ping the other pc any more and have to cancel.
Tried now using a SMB share, somewhat same result, transfer begins a bit faster, around 600kb/s but still slow for Ethernet, hangs after a few seconds giving errors.

I've changed the lan cable just in case, in fact the first one I've tried was only 3-pin, but still same thing on another cable.
I was confused at first but but his got to be something Nautilus related, I may try the transfer another way.
Worth note that after cancelling the transfer they will sort of re-connect a bit after, doesn't show anything but ping will be good.

Thanks for anyone taking a interest and helping with this.

Edit: today I've tried once more, this time transferring from my netbook to the laptop( inverse of before), tried both SMB and SFTP without success.
The netbook however has installed xfce desktop environment, different from nautilus, i can assume the issue other.

---

### Post by Gfurst on 2013-07-09
No replies to this, i thought it would at least pick someone's interest...
There was a kernel update, I'll try it again, different environment, but I think it won't change.

---

### Post by Morbius1 on 2013-07-09
If this is just a one time thing why not use http instead:

On the machine with the large files open a terminal and change to the parent folder containing the files you want to transfer:
```
cd /path/to/parent/folder
```
Then run the following command to set up a ***[COLOR=#0000cd]temporary[/COLOR]*** http server:
```
python -m SimpleHTTPServer
```
Then on the client machine open up your Internet browser and point it to:
```
http://192.168.0.100:8000
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the machine with the large files.*[/COLOR]

As long as you don't have an "index.html" file in the directory it will show the contents of the folder as down-loadable entities. 

When transfer is complete kill the http server by entering Ctrl-C in the terminal.

---

### Post by Gfurst on 2013-07-09
Hey Morbius thanks for the reply.  My problem persists:

Connecting the same two, a laptop and a netbook between direct wired Cat5 ethernet cable, local link.
They can see each other, ping and even connect the file system, the transfer begins but get stuck at which ping is lost, after cancelling the transfer it resumes back.

ping before transfer begins:
```
 ping -c 6 169.254.8.249
PING 169.254.8.249 (169.254.8.249) 56(84) bytes of data.
64 bytes from 169.254.8.249: icmp_req=1 ttl=64 time=0.360 ms
64 bytes from 169.254.8.249: icmp_req=2 ttl=64 time=0.375 ms
64 bytes from 169.254.8.249: icmp_req=3 ttl=64 time=0.351 ms
64 bytes from 169.254.8.249: icmp_req=4 ttl=64 time=0.347 ms
64 bytes from 169.254.8.249: icmp_req=5 ttl=64 time=0.346 ms
64 bytes from 169.254.8.249: icmp_req=6 ttl=64 time=0.344 ms

--- 169.254.8.249 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 4998ms
rtt min/avg/max/mdev = 0.344/0.353/0.375/0.026 ms


```
ping after transfer stuck:
```
ping -c 6 169.254.8.249
PING 169.254.8.249 (169.254.8.249) 56(84) bytes of data.
From 169.254.6.149 icmp_seq=1 Destination Host Unreachable
From 169.254.6.149 icmp_seq=2 Destination Host Unreachable
From 169.254.6.149 icmp_seq=3 Destination Host Unreachable
From 169.254.6.149 icmp_seq=4 Destination Host Unreachable
From 169.254.6.149 icmp_seq=5 Destination Host Unreachable
From 169.254.6.149 icmp_seq=6 Destination Host Unreachable

--- 169.254.8.249 ping statistics ---
6 packets transmitted, 0 received, +6 errors, 100% packet loss, time 5031ms
pipe 3

```

The transfer will even have a cool 9 Mb/s rate, about 220Mb before freezing.
The python trick did open http server, but followed the same scenario as before.
It doesn't matter which protocol I use, it always gets stuck similarly.
ps: Nautilus crashed in the first process as well.

Now I'm trying a transfer over my wireless lan, is going ok with a miserable 60Kb/s rate.
It did this as well before, getting stuck at some point, i don't know why so low, but that's another case.

The following is a screen cap of the web transfer stuck:
[ATTACH=CONFIG]244560[/ATTACH]

---

### Post by Gfurst on 2013-07-09
I've found a temporary solution at least.
Using my Mac as intermediary, directly connecting the two wired with Cat5 cable, mounting SSHFS with Macfusion and then transfering the files with a cool 11Mb/s.
50 min to down about 35 Gigs, pretty cool :D

[ATTACH=CONFIG]244561[/ATTACH]

Between the netbook and Mac at least, maybe the laptop( the other one) is faulty, will report back if this works.

---

### Post by Gfurst on 2013-07-09
Okay, so i could transfer all the files from netbook to my iMac, from my iMac to laptop however its even worse than before, won't even start the transfer and is locked...
No one with any idea why would this be??

---

