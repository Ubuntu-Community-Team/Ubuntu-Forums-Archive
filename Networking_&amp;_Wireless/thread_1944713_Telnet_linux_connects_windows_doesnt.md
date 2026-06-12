---
title: "Telnet linux connects windows doesnt"
date: 2012-03-21
forum: Networking &amp; Wireless
---

### Post by The Chupacabra on 2012-03-21
Hello-
I have a program running on Ubuntu 11.10 64bit, which listens for clients on port 2468. I can successfully connect to this port with telnet on the local machine (with both localhost and the ip). I can also successfully connect to that port from a RHLE 4.0 computer. However, when I try to establish a connection from a windows xp machine on the same network, the command prompt clears itself and shows just a blinking cursor - like it connects but none of the "connected to *.*.*.*" shows up. As soon as i hit any key the connection drops and throws me back to a c:\ prompt. I did run netstat on Ubuntu while windows was in this quasi connected state and netstat did indicate that there was an established connection between ubuntu and windows.

I can ping the Ubuntu box fine from xp. I have ufw disabled, and I set all apparmor profiles to complain - none of this made any difference.

Any help is greatly appreciated, thanks.

---

### Post by SeijiSensei on 2012-03-21
Have you tried another telnet client like [putty]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")?  While putty is most commonly used for SSH, it also supports the telnet protocol.

The standard Microsoft telnet client often seemed quite limited to me.

---

### Post by The Chupacabra on 2012-03-21
Yes I have tried putty from the windows box, but it doesn't do any better. If I have putty set to close the window after connection closes, when I hit the connect button the putty terminal window pops up for a split second then closes. I have also double checked the firewall and and antivirus software on the windows box to make sure they are off.

---

### Post by dandnsmith on 2012-03-22
Have you tried telnetting to the mail port as a sanity check, just to see if it does the same? I've always found the Windows telnet to work, even though rather limited - the only other thing I've used in this terminal connection game (from Windows) is Hyperterminal (but that may not be available any longer) or kermit (look for updated versions).

---

### Post by The Chupacabra on 2012-03-22
Derek-
I have never set up any sort of mail server on the ubuntu box. Does Ubuntu 11.10 have a smtp server running by default.
 
But I tried to telnet to port 25 any way and I get an actual "Connection Failed" message. 
 
Hyperterminal is installed with the xp os, so I gave that a shot. When connecting to port 2468 on the Ubuntu box, there is a connection timer in the lower left corner of Hyperterminal that begins to count, but I get no text/connection messages in the window at all - just a blinking cursor exactly like what I see when I telnet from a windows command prompt.

---

### Post by jonobr on 2012-03-22
Hello


try running tcpdump on the ubuntu box 

```
sudo tcpdump -i any port 2468
```

See what happens when you try to telnet on that port.
If you see nothing then nothing is being received from the client.


Im feeling though if you can do it from local and if you can do it from RHEL then it sounds as if it may be windows not allowing it?

Another thing you can do is installing wireshark on windows and seeing whats going on that way,.

---

### Post by The Chupacabra on 2012-03-22
Hi Jonobr-

Here is the output of the tcpdump:

This is the output of the initial connection:
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes
21:09:39.760270 IP (tos 0x0, ttl 128, id 10867, offset 0, flags [DF], proto TCP (6), length 48 )
    172.16.1.50.42610 > server1.local.2468: Flags [S], cksum 0x4b01  (correct), seq 3126751928, win 65535, options [mss 1408,nop,nop,sackOK],  length 0
21:09:39.761188 IP (tos 0x0, ttl 128, id 10868, offset 0, flags [DF], proto TCP (6), length 40)
    172.16.1.50.42610 > server1.local.2468: Flags [.], cksum 0x8fd0 (correct), ack 2886286247, win 65535, length 0

Then when I press any key I get disconnected and this is what shows up:
21:12:31.750150 IP (tos 0x0, ttl 128, id 12324, offset 0, flags [DF], proto TCP (6), length 41)
    172.16.1.50.42610 > server1.local.2468: Flags [P.], cksum 0x2ac7 (correct), seq 0:1, ack 1, win 65535, length 1
21:12:31.751344 IP (tos 0x0, ttl 128, id 12325, offset 0, flags [DF], proto TCP (6), length 40)
    172.16.1.50.42610 > server1.local.2468: Flags [.], cksum 0x8fce (correct), ack 2, win 65535, length 0
21:12:31.755251 IP (tos 0x0, ttl 128, id 12326, offset 0, flags [DF], proto TCP (6), length 40)
    172.16.1.50.42610 > server1.local.2468: Flags [F.], cksum 0x8fcd (correct), seq 1, ack 2, win 65535, length 0

---

### Post by jonobr on 2012-03-23
Hi 

It seems as if the server is receiving packets on that interface from 172.16.1.50 however, it is not replying to them.
This would imply that all is ok on the client.
I can also see in the connection attempt that the port used is as you said - 2468.

Could you run a comparable trace using the windows RHEL machine and post the tcpdump?

I am inclined to ignore connecting via local as it does not go down the complete stack to do this

Thanks

Jonobr

---

### Post by The Chupacabra on 2012-03-23
Ok, here is the tcpdump when RedHat connects correctly:
 
[COLOR=black][FONT=Tahoma]tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes[/FONT][/COLOR]
[FONT=Tahoma][COLOR=black]15:44:34.518432 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has server1.local tell 172.16.1.207, length 46[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]15:44:34.518542 IP (tos 0x0, ttl 64, id 6516, offset 0, flags [DF], proto TCP (6), length 44)[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]172.16.1.207.32904 > server1.local.2468: Flags [S], cksum 0x84db (correct), seq 1801693993, win 5840, options [mss 1460], length 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]15:44:34.518664 IP (tos 0x0, ttl 64, id 6518, offset 0, flags [DF], proto TCP (6), length 40)[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]172.16.1.207.32904 > server1.local.2468: Flags [.], cksum 0x4b80 (correct), ack 1902370724, win 5840, length 0[/COLOR][/FONT]
[FONT=Tahoma][COLOR=black]15:44:39.532686 ARP, Ethernet (len 6), IPv4 (len 4), Reply 172.16.1.207 is-at 00:22:19:23:34:4f (oui Unknown), length 46[/COLOR][/FONT]

---

### Post by jonobr on 2012-03-23
Hey 

Are you doing something with Mac addresses?

---

### Post by The Chupacabra on 2012-03-23
I have not specifically done anything to or with mac addresses.

 I did use slightly different arguments during the RH connection dump though. During the windows connection I used: ```
tcpdump -v src 172.16.1.50 and dst port 2468
```For the RH connection I used: ```
tcpdump -v src 172.16.1.207
```

---

### Post by The Chupacabra on 2012-03-26
According to the creator of the software, the linux telnet server behaves differently than windows telnet expects. So in order to connect to the ubuntu box from windows I have to use putty with specific options configured.

---

