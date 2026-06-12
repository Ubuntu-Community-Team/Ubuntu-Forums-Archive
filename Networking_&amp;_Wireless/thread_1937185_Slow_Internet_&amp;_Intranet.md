---
title: "Slow Internet &amp; Intranet"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by BWGreg on 2012-03-07
I found a few threads, but I could not find one specific to my hardware. I have an [Asus M5A78L-M LX PLUS]("http://ubuntuforums.org/support.asus.com/download.aspx?SLanguage=en&m=M5A78L-M%20LX%20PLUS&p=1&s=24&os=30&hashedid=IZxHVUuVo8OWSDbz") and a freshly updated installation of Ubuntu 11.10. I am folding@home on the PC and the intranet and internet is slow. I see download speeds topping out around 200kbps on a 1.5mbps rated line. I also have a shared folder HFM reads from a Win 7 PC and it times out quite often.
 
 
I do have a 2nd hard drive for a dual boot of Win 7. If I download a file on Ubuntu, it tops out at 200KB/s. If I download the same file on Win 7 it tops out a 1.7MB/s.
 
I am hard-wired to a D-Link DIR-615 router running DD-WRT firmware that is connected to a cable modem with Time Warner.
 
 
As you can see in the link to my motherboard, there is no Linux driver support. I was thinking it may be driver related, but this is actually my first time using Ubuntu and I have very little knowledge of Linux.

Edit:

Here is my ifconfig information if that helps:

> eth0      Link encap:Ethernet  HWaddr 54:04:a6:97:bf:be  
          inet addr:192.168.1.148  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe97:bfbe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:180692 errors:0 dropped:180692 overruns:0 frame:180692
          TX packets:114777 errors:0 dropped:317 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252787301 (252.7 MB)  TX bytes:9993696 (9.9 MB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1941 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1941 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124943 (124.9 KB)  TX bytes:124943 (124.9 KB)
Cable is fine and router port is fine, but I tried another cable and router port just in case, but still really slow. If you guys have some idea's, I would gladly try them. Until then, I will try a PCI NIC when I get home later.

---

### Post by dandnsmith on 2012-03-07
I have a concern that you don't understand the difference between speeds quoted in bits and bytes.
Conventionally KBps is kilo bytes per sec, whereas kbps is kilo bits per sec.
You apparently have a capability for 1.7Mega Bytes per sec on a 1.5 mega bits per sec line (I'll ignore the difference between Mega and milli, since you couldn't possibly be talking speeds in fractions of a bit per sec).
Given this confusion, you may really be quoting consistent figures, since the Bytes per sec would have to be multiplied by at least 8 to get bits per sec.

---

### Post by BWGreg on 2012-03-07
To be precise, the Ubuntu dowload manager reads 200 KB/sec while the Win 7 download manager reads 1.7 MB/sec. It takes 11 minutes to download a 101 MB file in Ubuntu vs <1 minute in Windows 7.
 
I know what you are talking about. My rated speed is 15 Mbps / 8 = Ubuntu is slow! ](*,)
 
Make sense now? Have any helpful suggestions? My spare NIC card is dead, so I cannot test that idea.

---

### Post by Sergius14 on 2012-03-07
You have to download the same file from the same source to do a good comparison.

Many services uses Akamai while other don't, and also the ISP's may have cached popular dowloads.

It is very common to download, for ex. from Microsoft, at top speed because Akamai Edge Service (this company distributes a file worldwide with a server in each ISP) while Ubuntu relies only con ver few mirrors (usually Universities).

---

### Post by BWGreg on 2012-03-07
Yes I did download the same file from the same server, but I used IE9 vs Pre-loaded Firefox. Let me grab a more recent version of Firefox for both Win 7 and Ubuntu so I can make the comparisson more fair. I fixed the intranet timeouts by dissabling the lock on the computer after the default of 10 mins.
 
That makes sense on the updates where I see <100 KB/s. I will try not to worry about those.
 
At least I am getting somewhere and learning a little. I am new to Linux, but I have installed older versions before; I just never learned how to use them. Thanks for both of your helpful posts so far.
 
Edit: Same result using like browsers.

---

### Post by dandnsmith on 2012-03-08
I've just realised what the motherboard is that you're using - one of my machines (built before xmas) has that one.
For networking you have to be aware that the driver module r8169, loaded by default by recent Ubuntu and Mint (at least) has a problem and needs to be replaced by using the r8168.
Problem manifests by interface going to sleep, and being slow to get going again - especially if you've been dual booting with Windows.

There are threads relating to this problem, and the solutions suggested, but my brain is refusing to cooperate as to where I've put the info - a search on the forums or via google may give you the gen.

[this thread](http://ubuntuforums.org/showthread.php?t=1465703) gives the basic stuff

---

### Post by BWGreg on 2012-03-08
Ok, let me try that out. I have a completed work unit for folding@home that keeps timing out when attempting to upload it to Stanford because of the slow speeds, so hopefully you have just given me the info to fix it. I will not be able to try anything until tonight though. I will report back and let you know. Until then, if any other idea's come up with anyone, please let me know.

EDIT: 

I tried to install driver 8168 to replace 8169 and I just barely caught a ss of the terminal error before it automatically closed:

[IMG]http://www.overclock.net/image/id/1954571/width/900/height/900/flags/LL[/IMG]

---

### Post by Sergius14 on 2012-03-08
It is laptop or PC?

Many times the speed are reduce for power saving.

Of course that there is an issue and needs to be fixed, but keep in mind this.

Drivers/Power.

You can try another drivers o Kernel Version.


I another post that I made (with no replies) I show how a Server behaves completelly different between Server vs Virtual  Kernel versions (it is a VM).

---

### Post by BWGreg on 2012-03-08
It is a Desktop that is dedicated to [EMAIL="folding@home"]folding@home[/EMAIL] and me learning how to use the O/S. Does Linux have Power Profiles like Windows does?
 
I am going to start over if I cannot get this slow network fixed. I will not put Win 7 on a dual boot if I do not fix the slow network. I will clear CMOS. I will then re-test, but I do want to follow through with getting the Realtek Driver on the system first. 
 
 
The screenshot shows some permission issues I have no idea on how to fix, but I will try googling them when I get home today.

Edit:

This thread is solved. dandnsmith pointed me to the resolution. I had to login as root to install the Realtek driver 8168 to replace 8169. I am now at full speed! Your memory was spot on Mr. and you deserve a big THANKS!!

---

