---
title: "Slow internet connection on Kubuntu 10.10 64 bits"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by Kurush Ishraqu on 2011-04-26
Hi! I have found a lot of topics with this same title, but after reading them I decided to write this.

I've been using Kubuntu 10.10 from four months now, without problems in my wired or wireless connections. But since four days ago, I don't know why, my connection, both wired and wireless, drop down; the max speed i get now is exactly 10% of the one I was getting before: 50 Kib/s.

With this came another problem that was not present before: every time I use Transmission, my connection dies, and I have not made any change to the configurations of the client.

What could be happening?

Thanks in advance!

PS: sorry for my English.

---

### Post by uncaspi on 2011-04-26
To ensure you not have got any trojans, open a terminal and issue this command.  sudo /sbin/tcpdump -i eth0
I assume your wired card is eth0.
If there are heavy traffic through your card when all internet applications are shutted down, you have an intruder.

---

### Post by Kurush Ishraqu on 2011-04-26
Ok; I don't know how to interpret all that information. I shutted down  everything that could be using internet (even amarok), and that command  gives me a lot of output. Here is a sample of it.

```

00:28:42.459422 IP 192.168.1.103.57276 > 239.255.255.250.1900: UDP, length 133
00:28:42.459823 IP 192.168.1.102.57275 > 239.255.255.250.1900: UDP, length 133
00:28:42.500432 ARP, Request who-has 192.168.1.107 tell 192.168.1.1, length 46
00:28:42.674714 IP6 fe80::24aa:54c3:xxxx:xxxx.xxxxx > ff02::c.1900: UDP, length 146
00:28:43.500748 ARP, Request who-has 192.168.1.107 tell 192.168.1.1, length 46
00:28:44.379718 ARP, Request who-has 192.168.1.1 tell 192.168.1.101, length 46
00:28:44.501208 ARP, Request who-has 192.168.1.107 tell 192.168.1.1, length 46
00:28:44.560268 IP 192.168.1.104.6646 > 192.168.1.255.6646: UDP, length 170
00:28:44.760377 ARP, Request who-has 192.168.1.1 tell 192.168.1.103, length 46
00:28:44.760393 ARP, Request who-has 192.168.1.1 tell 192.168.1.103, length 46
00:28:45.752929 IP6 fe80::24aa:54c3:e9b5:2c7c.62540 > ff02::c.1900: UDP, length 146
00:28:49.296721 IP 192.168.1.111.mdns > 224.0.0.251.mdns: 0 [6a] [8q]  TXT (QM)? alejandro [78:xx:00:xx:xx:xx]._workstation._tcp.local. PTR  (QM)? _plasma._tcp.local. PTR (QM)? _services._dns-sd._udp.local. PTR  (QM)? _workstation._tcp.local. PTR (QM)? _touch-able._tcp.local. SRV  (QM)? alejandro [b8:ac:6f:70:b0:5b]._workstation._tcp.local. TXT (QM)?  alejandro [b8:xx:xx:70:xx:xx]._workstation._tcp.local. TXT (QM)?  C545BE46F34586FD._touch-able._tcp.local. (396)
00:28:49.714391 IP6 fe80::24aa:54c3:xxxx:xxxx.xxxxx > ff02::c.1900: UDP, length 146
00:28:51.621903 IP6 fe80::b40d:ca37:xxxx:xxxx.xxxxx > ff02::1:3.hostmon: UDP, length 23
00:28:51.622272 IP 192.168.1.101.64822 > 224.0.0.252.hostmon: UDP, length 23
00:28:51.722232 IP6 fe80::b40d:ca37:xxxx:xxxx.xxxxx > ff02::1:3.hostmon: UDP, length 23
00:28:51.722240 IP 192.168.1.101.64822 > 224.0.0.252.hostmon: UDP, length 23
00:28:51.922402 IP 192.168.1.101.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
00:28:52.672456 IP 192.168.1.101.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
00:28:52.926821 IP6 fe80::24aa:54c3:xxxx:xxxx.xxxxx > ff02::c.1900: UDP, length 146
00:28:53.422691 IP 192.168.1.101.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
00:28:53.499910 ARP, Request who-has 192.168.1.107 tell 192.168.1.1, length 46
00:28:54.175090 IP6 fe80::b40d:ca37:xxxx:xxxx.xxxxx > ff02::1:3.hostmon: UDP, length 23
00:28:54.175464 IP 192.168.1.101.50234 > 224.0.0.252.hostmon: UDP, length 23
00:28:54.275425 IP6 fe80::b40d:ca37:xxxx:xxxx.xxxxx > ff02::1:3.hostmon: UDP, length 23
00:28:54.275431 IP 192.168.1.101.50234 > 224.0.0.252.hostmon: UDP, length 23
00:28:54.475620 IP 192.168.1.101.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
00:28:54.500214 ARP, Request who-has 192.168.1.107 tell 192.168.1.1, length 46
00:28:55.225623 IP 192.168.1.101.netbios-ns > 192.168.1.255.netbios-ns: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST


```

---

### Post by uncaspi on 2011-04-27
Ok there should be no traffic if all internet app is shutted off. Seems you've got an intruder. Open a new user account and log in and see if the problem persist. sudo adduser test

---

### Post by Kurush Ishraqu on 2011-04-27
I'm writing from the new account. The problem persist: the internet connection has a max in 50 Kib/s, both wired and wireless, and the command you post gives information even with all internet-related apps closed.

---

