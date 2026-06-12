---
title: "Signs of a router going bad?"
date: 2005-12-17
forum: Networking &amp; Wireless
---

### Post by ToiletDuck on 2005-12-17
Hi all,
  

 Im not sure what to really look for if this is the case. I currently have a D-link 614+ 4 port wireless router wich is going on 3 years since i started using it and lastnight it all started. I called my ISP Friday night to find out why the Inet for me was slow. And it turned out that they were having issues. Ok, it made sense. But today its the same thing. When browsing pages it may take 2+minutes for a page to come up and mail? I cannot even access it at all. BTW im using Evolution for my mail.

Now if i hook the cable modem directly to my computer then i have zero problems works like it always has. Another thing to note is my wife's machine is running XP through wireless and it has zero problems. But i can run wireless on Ubuntu but i still have the same problem with the wireless as i do if i had it hardwired to the router. So both hardwire and wireless are giving me problems while running through the router. What can i do or look for to see if this is a router going bad? Please remember that this just came on since Friday night.:confused: 

I currently use:
Ubuntu 5.10
512 ram
120 gig HD
linksys wireless-g Model# WMP54G  still experimenting though

Thanks

---

### Post by Lambert on 2005-12-17
A couple things to try.

Open a terminal and run these commands

ping -c 5 82.211.81.130

then 

ping -c 5 [www.ubuntulinux.com](www.ubuntulinux.com)

and compare the times. If there is a huge difference then there is a hostname resolver problem.



After testing that then try turning off ipv6 from firefox and see if there is a difference

 In the address bar type about:config*. Find this line *network.dns.disableIPv6* and double click on it to change the value to *true[I].

these don't test your router but settings with in ubuntu.
[/I]

---

### Post by ToiletDuck on 2005-12-17
Lambert, 

 THanks for the quick reply here is the output from the terminal

jeff@JeffInTheBatcave:~$ ping -c 5 82.211.81.130
PING 82.211.81.130 (82.211.81.130) 56(84) bytes of data.
64 bytes from 82.211.81.130: icmp_seq=1 ttl=46 time=107 ms
64 bytes from 82.211.81.130: icmp_seq=2 ttl=46 time=108 ms
64 bytes from 82.211.81.130: icmp_seq=3 ttl=46 time=108 ms
64 bytes from 82.211.81.130: icmp_seq=4 ttl=46 time=110 ms
64 bytes from 82.211.81.130: icmp_seq=5 ttl=46 time=111 ms

--- 82.211.81.130 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4003ms
rtt min/avg/max/mdev = 107.384/109.349/111.406/1.420 ms
jeff@JeffInTheBatcave:~$

jeff@JeffInTheBatcave:~$ ping -c 5 [www.ubuntulinux.com](www.ubuntulinux.com)
PING [www.ubuntulinux.com](www.ubuntulinux.com) (82.211.81.130) 56(84) bytes of data.
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=1 ttl=46 time=110 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=2 ttl=46 time=109 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=3 ttl=46 time=109 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=4 ttl=46 time=108 ms
64 bytes from gentoo.ubuntu.com (82.211.81.130): icmp_seq=5 ttl=46 time=111 ms

--- [www.ubuntulinux.com](www.ubuntulinux.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 20481ms
rtt min/avg/max/mdev = 108.683/109.868/111.165/0.968 ms


I did the firefox deal and turned disabled the IPv6 and it seems to run a little faster. So i say thankyou for the help. Also Evolution has also been able to connect to my mail server? Would changing the IPv6 to true help that as well?

---

### Post by Lambert on 2005-12-18
My first post shows my signature. Click on the WTG and towards the bottom of the guide is a section on turning ipv6 off system wide.

With this info and your info about other pcs working with no problem I don't think your router is failing.

You say a little faster, but is it not to normal speed? After disabling ipv6 system wide post back if it's normal speed or still appears a little slow.

---

### Post by ToiletDuck on 2005-12-19
Lambert,

 Once agin thanks for your help. Lastnight i decided to wipe the HD and start over. But this time i installed Ubuntu with the wireless card only, instead of the hard line. And now everything is back to normal.:D 

And to top it off this wireless card was recognized after the reinstall i have had to do nothing to get it running.

---

### Post by walker45 on 2005-12-19
I had a problem developed similar to this one ever since I started working on getting my wireless card to work with WPA in Ubuntu.  I noticed it only occured with both my wireless card and ethernet card were both "active" in System/Administration/Networking.  

This might have been occuring b/c the browser was looking for packets from both cards.  Only a theory though.  :cool:

---

### Post by ToiletDuck on 2005-12-19
[QUOTE=walker45]I had a problem developed similar to this one ever since I started working on getting my wireless card to work with WPA in Ubuntu.  I noticed it only occured with both my wireless card and ethernet card were both "active" in System/Administration/Networking.  

This might have been occuring b/c the browser was looking for packets from both cards.  Only a theory though.  :cool:[/QUOTE]

 I to had the on-board lan going when it all started, but i also disabled the lan after some head scratching and reading what Lambert posted. So maybe you have a valid theroy?

---

