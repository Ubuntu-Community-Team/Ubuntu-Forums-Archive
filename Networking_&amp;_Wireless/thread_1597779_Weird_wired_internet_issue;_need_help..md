---
title: "Weird wired internet issue; need help."
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by GARoss on 2010-10-15
I just did a clean installed of Ubuntu 10.10 amd64 over Ubuntu 10.04 x86. No issues with internet using 10.04.

What is happening is I cannot connect to the internet if I restart the PC. From a cold start, the internet works perfectly. Do an update, restart & no internet. Shut down, then cold start & the internet works like a charm. It has happen this way every time so far.
 
This is weird especially since I had no internet issues while using 10.04 on this PC. What on earth would cause that?

---

### Post by GARoss on 2010-10-16
When the internet is somehow not connected when it normally works, how can I use the terminal or other to find what isn't working? What do I type in the terminal? I did try to connect manually to eth0 but that fails.:(

Anyone?

---

### Post by Iowan on 2010-10-16
From the terminal, a few quick checks:
1. **ifconfig -a** to verify machine has IP address
2. **ping <routerIP>**  - can you reach router/gateway?
3. **ping google.com** - is net... working?
4. **ping 74.125.95.104** (that's one Google IP address) to see if it's a DNS problem.

---

### Post by darknight2183 on 2010-10-16
do a restart, the open Application->Accessories->Terminal

type "cat /var/log/dmesg |grep eth0"

Look to see if there is a line that says "ADDRCONF(NETDEV_UP): eth0: link is not ready" If there is, then the connection state isn't linking to your home's router.

If not, type "cat /var/log/syslog |grep dhclient"
Look to see that there was a successful handshake between your router/modem, it should look something like "dhclient: DHCPREQUEST of 192.168.x.x on eth0 to 192.168.x.x"

Assuming that all that goes to hell, do an "lsmod" and find the module that is associated to your NIC. Then try adding that to /etc/modules and restart

Also, what happens if you issue the command "/etc/init.d/networking restart" after you've restarted the machine and don't have internet access.

---

### Post by GARoss on 2010-10-17
> **Iowan said:**
> From the terminal, a few quick checks:
1. **ifconfig -a** to verify machine has IP address
2. **ping <routerIP>**  - can you reach router/gateway?
3. **ping google.com** - is net... working?
4. **ping 74.125.95.104** (that's one Google IP address) to see if it's a DNS problem.

I've attached the results while the internet was working (see right attached) & nonworking (see left attached). The ifconfig -a of non working lacks line 2 where the ip address should be. Google pings fail without connection but loop endlessly when connected.

---

### Post by Iowan on 2010-10-17
By <routerIP>, I meant the router's actual IP address - *probably* 192.168.1.1...

---

### Post by GARoss on 2010-10-17
> **darknight2183 said:**
> do a restart, the open Application->Accessories->Terminal

type "cat /var/log/dmesg |grep eth0"

Look to see if there is a line that says "ADDRCONF(NETDEV_UP): eth0: link is not ready" If there is, then the connection state isn't linking to your home's router.

Working or non both say, [   11.650564] ADDRCONF(NETDEV_UP): eth0: link is not ready, in terminal.

> If not, type "cat /var/log/syslog |grep dhclient"
Look to see that there was a successful handshake between your router/modem, it should look something like "dhclient: DHCPREQUEST of 192.168.x.x on eth0 to 192.168.x.x"

Working & Not working have this line.

> Assuming that all that goes to hell, do an "lsmod" and find the module that is associated to your NIC. Then try adding that to /etc/modules and restart

I don't see any reference to NIC with internet working or not.

> Also, what happens if you issue the command "/etc/init.d/networking restart" after you've restarted the machine and don't have internet access.

nothing happens.

---

### Post by theautates on 2010-10-17
looking at the images you have provided it seems to me that your pc is not receiving any ip from your dhcp server.

If you would look at the line 2 of your "working" connection there is clearly an ip assigned to your pc which is 192.168.1.5 . 
also what is your network device? if your using realtek then you may want to read the links.

try these links: (got from dineshs)
[http://ubuntuforums.org/showthread.php?t=1480328&page=2](http://ubuntuforums.org/showthread.php?t=1480328&page=2)
[http://wiki.hetzner.de/index.php/Ins...network_driver](http://wiki.hetzner.de/index.php/Ins...network_driver)
[http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411)

let me know what happened

---

### Post by GARoss on 2010-10-17
> **Iowan said:**
> By <routerIP>, I meant the router's actual IP address - *probably* 192.168.1.1...

Sorry, I'm not sharp as a tack with computers!:rolleyes:

---

### Post by GARoss on 2010-10-17
This is really odd. From a cold boot the internet usually works. It's a new install so when I restart after upgrades is when I can't connect. On the Windows side I never had issues. No internet issues with 10.04 pryior to installing 10.10, either.

---

### Post by GARoss on 2010-10-17
> **theautates said:**
>  
also what is your network device? if your using realtek then you may want to read the links.

let me know what happened
Thanks. The motherboard is an Intel DG965RY & the spec sheet says 
[I]Gigabit (10/100/1000 Mbits/sec) LAN subsystem using the Intel® 82566DC
Gigabit Ethernet Controller
[/I]

I'll try some of the suggestions you posted. The issue seems to happen after a restart (although if failed to connect during install) but works on cold starts or if the PC is shut all the way down. Weird!

---

### Post by theautates on 2010-10-18
So just to clarify things...

There is no problem with your connection during your first install right? then when you have upgraded and restarted your os you are now having some problems with your ethernet card correct? 

What does the 'lshw -C Network' command says?

---

### Post by dineshs on 2010-10-18
when the connection is not working try
1)run```
sudo dhclient eth0
```and see if it works
If not
2)run```
sudo service network-manager stop
```
```
sudo service network-manager start
```and see

---

### Post by GARoss on 2010-10-18
> **theautates said:**
> So just to clarify things...

There is no problem with your connection during your first install right? then when you have upgraded and restarted your os you are now having some problems with your ethernet card correct? 

What does the 'lshw -C Network' command says?

Thanks,
I had Ubuntu 10.04 32-bit & Windows 7 64-bit as dual boot. Never had internet connection issues with either. I wanted to install 10.10 64-bit over 10.04 32-bit; to do a clean install. 

When the install disc booted, it could not connect to the internet nor could I connect manually from the install desktop. Proceeded  with install. On restart I still couldn't connect so I restarted & went in Win7 to see if there were issues there. Internet was OK so booted back into Ubuntu 10.10 & this time the internet worked. Updated the software & required a restart but no internet on restart. Restarted; still no internet. Shut down completely, then booted to find internet working. Installed graphic driver & restarted to no internet. Shut down completely, then booted to find internet working. That is the pattern but not always as occasionally it does not connect from a cold start, too. It seems to have a personality of its own.

I'll try 'lshw -C Network' when I boot that PC again & report.

---

### Post by GARoss on 2010-10-18
> **theautates said:**
> 
What does the 'lshw -C Network' command says?

See attached. This is the same with the internet connected or not connected.

---

### Post by GARoss on 2010-10-18
> **dineshs said:**
> when the connection is not working try
1)run```
sudo dhclient eth0
```and see if it works
If not
2)run```
sudo service network-manager stop
```
```
sudo service network-manager start
```and see

See attached. Left is with internet not connected. Right - connected

---

### Post by theautates on 2010-10-18
> **GARoss said:**
> See attached. This is the same with the internet connected or not connected.

hmm... so you do have your ethernet driver installed.

Now we have to find out if the driver you have is matching your current kernel.
first type: 'uname  -r', this will show you the current version of the kernel that your using.
next type: 'modprobe e1000e', this will show you if the version of the driver you have is build specifically for your current kernel. 

if the version of your driver and your kernel version didn't match then i suggest download the latest driver for your intel network controller and follow this instruction >> [here]("http://www.linuxquestions.org/questions/linux-hardware-18/network-card-invalid-module-format-715906/")

---

### Post by GARoss on 2010-10-19
> **theautates said:**
> hmm... so you do have your ethernet driver installed.

Now we have to find out if the driver you have is matching your current kernel.
first type: 'uname  -r', this will show you the current version of the kernel that your using.
next type: 'modprobe e1000e', this will show you if the version of the driver you have is build specifically for your current kernel. 

if the version of your driver and your kernel version didn't match then i suggest download the latest driver for your intel network controller and follow this instruction >> [here]("http://www.linuxquestions.org/questions/linux-hardware-18/network-card-invalid-module-format-715906/")

2.6.35-22-generic & no report when typing modprobe e1000e. See attached.

---

### Post by 73ckn797 on 2010-11-23
Similar issue. When cold booted, no Internet connection. This happens intermittently on the 3rd or 4th start-up. If I reboot all is working fine.

I am going to monitor this thread and try the suggestions next time it starts with no Internet connection.

Running 10.04. Never had this problem with 9.10 or earlier.

---

### Post by cariboo on 2010-11-23
> **GARoss said:**
> 2.6.35-22-generic & no report when typing modprobe e1000e. See attached.

That's normal, Linux only tells you, you have done something wrong, it doesn't say a thing when you do it right. :)

---

