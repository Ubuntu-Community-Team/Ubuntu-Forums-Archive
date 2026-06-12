---
title: "way to check who is on my home network"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by orrymr on 2011-04-06
Hi all,
what's the command to check who is currently on my home network?

---

### Post by josephmills on 2011-04-06
there are a bunch of programs for this auto scan is one and it is real easy to use. nmap is one a little harder to use as it is from the cli there is a gui version called zenmap but I have not used it there is also wireshark which is a gui also I like to use auto scan my self

---

### Post by orrymr on 2011-04-06
Thanks.

Say I now want to SSH into another machine (a mac) on my home network, what do I need to know? I know its local IP address is 192.168.0.4 and sudo nmap -O 192.168.0.4
 returns:
```

Nmap scan report for 192.168.0.4
Host is up (0.0017s latency).
Not shown: 997 closed ports
PORT     STATE SERVICE
88/tcp   open  kerberos-sec
548/tcp  open  afp
3301/tcp open  unknown
MAC Address: 00:1E:C2:AE:FB:EE (Apple)
Device type: general purpose
Running: Apple Mac OS X 10.5.X
OS details: Apple Mac OS X 10.5 - 10.6 (Leopard - Snow Leopard) (Darwin 9.0.0b5 - 10.0.0)
Network Distance: 1 hop

```
So does this now mean I can remotely access this machine through any of those 3 ports?  And if so, what is the syntax?

Thanks again

---

### Post by spiky001 on 2011-04-06
What are you trying to achieve

---

### Post by orrymr on 2011-04-06
My friend's laptop is at my place, and the only way we can copy data from machine to machine is via a USB stick. My USB stick is 4GB big, which is a problem because we want to transfer a whole lot. I've got a wireless home network, so we figured this would be the best way to move data across. Is there a better way?

---

### Post by decoherence on 2011-04-06
according to your nmap output, the ssh server is not running on your friend's mac. he will have to configure that first, then either give you a user account or give you the credentials for his account. once you've done that, an example syntax for copying files via ssh from your computer to his is

```
 scp yourfile username@192.168.0.4:~/ 
```

which will take 'yourfile' from your computer and put it in the home directory of whichever 'username' you provided. to go the other way around and pull a file off your friend's computer, you basically just reverse the order

```
 scp username@192.168.0.4:hisfile ~/
```

which will dump 'hisfile' in to your home directory.

'hisfile' or 'yourfile' should be replaced with a proper path, ie '~/Documents/MyGreatSpreadsheet.xls' or whatever. in other words, the syntax is 'scp file-to-copy destination-to-copy-to'

As to checking who is on your network, the best way to do this is through your router. The particulars differ by model but in general routers can give you a table, often on a web page for consumer models, that lists the current IP addresses in use and their associated MAC (hardware) addresses.

---

