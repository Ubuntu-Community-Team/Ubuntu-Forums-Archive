---
title: "wired network woes"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by dragon99 on 2010-03-18
Using a dell latitude 620 running Karmic I can establish both a wired network connection and wireless. The wireless works faultlessly.

However the wired network loses the ability to connect to internet after a few minutes browsing. The network applet in the panel shows the network connection is active but I cant load any webpage. Checking the network settings all look ok, but unable to load any web page

I know its not a router issue or firewall issue. I run Jaunty on my desktop by wired connection to the same netgear router without any problems, same goes for any of my XP pc.

If I delete the wired connection, and then add it back as a new connection it all works well for a few minutes and then for no apparent reason loses connectivity to internet.

Any ideas how to resolve this issue is much appreciated.

dragon

---

### Post by dragon99 on 2010-03-18
I also getting the exact same problem in Karmic with IBM Thinkpad R60, works wireless no prob but no wired connectivity

---

### Post by 2hot6ft2 on 2010-03-18
Try this.
Right click on the network manager applet and choose Edit Connections.
Wireless tab then your connection and Edit.
Clear the check box for Connect Automatically at the top.
Apply, close. reboot.
See if your wired connection stays connected, that's what I had to do with mine otherwise it would get confused since they both had IP Addresses I guess.

You could also try left clicking the applet and the wifi connections disconnect, but I didn't want to do that every time.

---

### Post by dragon99 on 2010-03-18
No joy, even physically turned the radio off. The wired network is still showing as active, but still cant open a webpage. ifconfig shows that an ip address is acquired. Here's the output from ifconfig:

dragon:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:cb:0a:b1  
          inet addr:192.168.193.124  Bcast:192.168.193.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fecb:ab1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:153 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81961 (81.9 KB)  TX bytes:18035 (18.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

I dont understand what the errors are, timing out perhaps?

---

### Post by Iowan on 2010-03-19
Unfortunately, this seems to be a [recurring]("http://ubuntuforums.org/showthread.php?t=1429604") theme - network connects, but won't browse. I'm still hoping to see the cure - but haven't yet. You can try checking gateway (with **route -n**), and contents of */etc/resolv.conf*. If nothing unusual shows up there, you can try pinging internet by name or address. The next step involved checking protocols - but I haven't wrapped my brain around that one yet.

---

### Post by dragon99 on 2010-03-19
Already tried pinging address both lan & wan a couple of days ago, with mixed results. I can see the gateway, & I can sometimes connect to a webpage this way eg yahoo, but its not loading the page correctly ie its just a page full of hyperlinks. Firefox shows an error, cant remember the exact detail. 

Strange that I have no prob with jaunty on desktop pc using wired connection on the same router & lan as the dell. That would suggest that there is an issue with karmic.

---

### Post by Arnoldijzermans on 2010-03-21
Same problem here, but I have it since 2.6.31-20, using a wireless linksys 5430 something.

Now running kernel 19 to post the problem. Will check the things mentioned in previous posts, but to add. The complete network connection is lost, so besides internet not even able to print!

Using WICD as a networkmanager btw.

will keep you posted of results

cheerio

edit: having the problem in 2.6.31-19 now as well. Weird

---

### Post by legatek on 2010-04-29
I was having a problem maintaining a wired connection, similar to what is described on this thread. I was finally able to fix it by blacklisting ipv6 in /etc/modprobe.d/blacklist.conf.

---

### Post by MOB_Figga on 2010-04-30
I'm not the only one I see:

I wanted to start a new thread about this, cause I also have this problem: internet works for some time (I have a wired connection) but after that, it takes ages to load and this loading will fail even though the network manager (the icon) shows I have a connection.. would that blacklisting also help me?

---

