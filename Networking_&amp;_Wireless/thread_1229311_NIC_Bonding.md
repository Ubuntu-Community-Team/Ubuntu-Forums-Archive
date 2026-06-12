---
title: "NIC Bonding?"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by new2linux09 on 2009-08-01
Hello I hope I didn't miss another thread with this if so please point me in the right direction...

I recently reinstalled my xubuntu, with the latest release, in my previous install I had bonding successfully working. The tutorial I followed is: [http://pmjdebruijn.blogspot.com/2006/04/ubuntu-bonding.html]("http://pmjdebruijn.blogspot.com/2006/04/ubuntu-bonding.html")

This method worked fine in the last version of xubuntu. I have installed ifenslave-2.6 and changed my /etc/network/interfaces file. I restarted /etc/init.d/networking and everything came up fine. ifconfig shows both nics receiving the same designated IP address as well as a bond0 listing all same ip. before starting i tested the nic and everything worked fine. I can ping my gateway address but not my WAN and cant load google.com. I could load google when running the single nic before bonding. There is no firewall. The fresh install is done on a separate hard drive and if i switch and boot back into the previous install there everything works fine again.

Any ideas what could be going on with the new version of xubuntu and why this might not be working?? 

Thanks in advance.

---

### Post by Crafty Kisses on 2009-08-02
I have a perfect network bond running as of right now, so I will try and help you. Have you made sure the network bonding module is running? You can run as root:
```
modprobe bonding
```

---

### Post by new2linux09 on 2009-08-02
I did not check that. I tried running modprobe bonding and got a "WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release."

I entered it as sudo and as just modprobe bonding. Did i enter it wrong?

---

### Post by new2linux09 on 2009-08-02
i just ran the command > sudo modprobe --list | grep bonding 
and it returned the message > kernal/drivers/net/bonding/bonding.ko

---

### Post by Crafty Kisses on 2009-08-02
What are the results of the following?
```
lsmod | grep bonding
```

---

### Post by new2linux09 on 2009-08-02
results are:

bonding         96512 0

---

### Post by Crafty Kisses on 2009-08-02
Hmmm, strange. What does the following say?
```
route
```

---

### Post by new2linux09 on 2009-08-02
It gives a bunch of info that I wish i could copy and paste. What am I looking for? 

It lists under destination 192.168.2.0 for bond0 eth0 and eth1 and genmask 255.255.255.0 for those three.

then lists link-local with genmask 255.255.0.0 for bond0

then two default listings both gateway ip 192.168.2.1 for eth1 and bond0 only

---

### Post by Crafty Kisses on 2009-08-02
That is really strange, because it appears this isn't a Gateway issue. I'd suggest you test your NICS by running "mii-tool" if you don't have mii-tool you can install it by running as root:
```
apt-get install mii-tool
```
It will tell you the integrity of your NICS, hope this helps.

---

### Post by new2linux09 on 2009-08-02
In finding a way to do this bond originally I found lots of tutorial options all of which were slightly different. Could it be something in the way it was originally configured? Although it did work fine with the last version of Ubuntu. 

To create the bond I added:   bonding mode=active-backup miimon=100  to my /etc/modules file

To the /etc/network/interfaces file I added:
auto bond0
iface bond0 inet static
address 192.168.2.6
netmask 255.255.255.0
gateway 192.168.2.1
dns-nameservers 202.124.224.2, 202.124.224.11
post-up ifenslave bond0 eth0 eth1
pre-down ifenslave -d bond0 eth0 eth1

---

### Post by new2linux09 on 2009-08-02
I tested both nics independently and both work fine until bonded. 

after running mii-tool I got :

SIOCGMIIPHY on 'eth0' failed: Operation not permitted

it lists that for eth0 through eth7 and then

no MII interfaces found

---

### Post by new2linux09 on 2009-08-02
with a root comand mii-tool returned

eth0: negotiated 1000baseT-FD flow-control, link ok
eth1: negotiated 1000baseT-FD flow-control, link ok
eth2: no link

eth2 is the onboard nic not being used

---

### Post by Crafty Kisses on 2009-08-02
Well the funny thing is, I setup my network bond very similar to yours and it works perfectly, then again I'm on Ubuntu. I seen a thread very similar to this a while back and in fact I had a similar problem, there was a line in the following directory if I recall the directory was:
```
/proc/net/bonding/bond
```
Something to that nature, and in that was a configuration file, and there was a line in there that read:
```
mode=0
```
What you could do is you could change that to the following:
```
mode=1
```
Then that would get the network bond working again if you're on a 64-bit architecture machine, which I'm not even sure that you are. It's just an idea, but I myself now want to get this solved. ;-)

---

### Post by new2linux09 on 2009-08-02
The file path /proc/net/bonding/bond
leads me to a new file. Know anything I could enter specifically? Sorry I'm new to linux file structures.

I really would like this solved as well. This is for a high school computer lab and acts as the file server for small files. I installed a larger hard drive and wanted to run the latest version but I guess I could try rolling back and installing the older version of xubuntu and set it up see if that will work. Although i'm not sure why the new version is being so picky.

---

### Post by new2linux09 on 2009-08-02
Could mode=1 be added to the /etc/modules file where it currently lists mode as active?

---

### Post by Crafty Kisses on 2009-08-02
Hmm, have you read **[[B]this**]("https://help.ubuntu.com/community/UbuntuBonding")[/B]? Now if this doesn't solve your issue, I'm still going to help you. ;-)

---

### Post by new2linux09 on 2009-08-02
No I haven't looks like its slightly different config let me run through it really quick and i'll repost with my results.

---

### Post by new2linux09 on 2009-08-02
still tinkering with those settings but now on a networking restart I'm showing a:

"Ignoring unknown interface eth0=eth0

---

### Post by new2linux09 on 2009-08-02
Following the how to from the Ubuntu forums... when i restart the network I get the following:

"Illegal operation: The specified slave interface 'eth0' is already a slave
Master 'bond0' , Slave 'eth0' : Error: Enslave failed
"Illegal operation: The specified slave interface 'eth1' is already a slave
Master 'bond0' , Slave 'eth1' : Error: Enslave failed
SIOCADDRT: File exists
Failed to bring up bond0"

Could there be something left over from previous attempts causing the new bond to not load properly?

---

### Post by new2linux09 on 2009-08-02
Well a sort of solution... I reinstalled the previous version of xubuntu and ran through the ubuntu community tutorial [https://help.ubuntu.com/community/UbuntuBonding]("https://help.ubuntu.com/community/UbuntuBonding") the bond works flawlessly right from the start.

Any ideas why this would not work in the new version (9 "Jaunty Jackalope")??

I'm not sure what was modified in the updated release but it works perfectly in the previous version. In the tutorial I noticed that in the /etc/modprobe.d/bonding file the bond mode was listed as "mode=0" while in the interfaces file its listed as "bond-mode 4"
What is the difference? Or perhaps why would it be listed differently between the two files?

---

### Post by Crafty Kisses on 2009-08-02
That is really weird. The only thing I could think of is some update or new implementation they put in to 9.04 that is causing issues of bonding your NICS. It might also be possible that you're using a different kernel and there is a conflict somewhere. I would definitely send a bug report to Launchpad. Again though I have a working Network bond here on my Linux box using very similar configuaration, if not very similar, exactly the same.

---

### Post by new2linux09 on 2009-08-02
Can a bug report be a generalized issue if i havn't narrowed down something specific? I'm wondering if theres an issue with the xubuntu build specifically. The nics are just Intel Gigabit nothing fancy and quite common.

---

### Post by Crafty Kisses on 2009-08-02
Sure, you can just explain what's happening.

---

### Post by nutznboltz on 2009-08-18
Related thread:

[http://ubuntuforums.org/showthread.php?t=835732](http://ubuntuforums.org/showthread.php?t=835732)

---

