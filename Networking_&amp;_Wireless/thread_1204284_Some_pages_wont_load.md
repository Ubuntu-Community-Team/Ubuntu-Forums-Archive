---
title: "Some pages wont load"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by Drianos on 2009-07-04
Hello everyone, I am having a problem with some pages that wont load and i was wondering if anyone experience the same or know how to solve the problem. I dont remember all of the pages but this two are the more important.
[http://www.ubuntu-es.org/index.php?q=forum](http://www.ubuntu-es.org/index.php?q=forum)
[http://www.megaupload.com](http://www.megaupload.com)

I try reinstalling flash(using a older version) but nothing happens.
So far I have try to load the pages with mozilla, swiftfox, seamonkey and opera, none load the pages.
Also i can acces does pages with other computers in my house.

---

### Post by computer13137 on 2009-07-04
[www.ubuntu-es.org]("http://www.ubuntu-es.org") is not loading for me either.  I've never heard of that website.

It's most likely an issue with your DNS cache.  Have you rebooted the computer\router lately?

Can other PCs in your house access the websites in question?

Are  you able to ping these websites?  Please paste the results of the following commands.

```
ping -c 4 www.ubuntu-es.org
ping -c 4 www.megaupload.com
ping -c 4  www.ubuntuforums.org
```-Kirk

---

### Post by Drianos on 2009-07-04
I leave my computer for a while, when i come back ubuntu-es load, but not megaupload, I rebooted the router after reading your replay and now noone will load.I maek all the posible test in 4 computers, here are the results:
-Desktop(ubuntu/wire):noone
-Portable(ubuntu/wifi):noone
-Portable(vista/wifi):megaupload
-Desktop(current)(ubuntu/wire):noone,(xp/wire):megaupload ,(vmware workstation/xp/wire):megaupload

All with mozilla firefox since i have try 4 browsers in my computer and all gave the same result.

Iam only intersted in fixing megaupload for now.
Here is what the terminal give me:

```
adrian@adrian-desktop:~$ ping -c 4 www.ubuntu-es.org
PING www.ubuntu-es.org (150.128.97.33) 56(84) bytes of data.
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=1 ttl=48 time=237 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=2 ttl=48 time=241 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=3 ttl=48 time=238 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=4 ttl=48 time=238 ms

--- www.ubuntu-es.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 237.734/238.845/241.442/1.621 ms

adrian@adrian-desktop:~$ ping -c 4 www.megaupload.com
ping: unknown host www.megaupload.com

adrian@adrian-desktop:~$ ping -c 4  www.ubuntuforums.org
PING www.ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=46 time=185 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=46 time=184 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=46 time=185 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=46 time=184 ms

--- www.ubuntuforums.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 184.546/184.872/185.258/0.609 ms
adrian@adrian-desktop:~$ 
```

The one of megaupload take a lot of time.

---

### Post by computer13137 on 2009-07-04
Ah, that's actually just as I suspected.  The issue appears to be related to the DNS resolution.

On your Ubuntu box, please paste the results of the following commands, so I can see what DNS server you're using and more information about how your network is setup.
```
ifconfig
``````
cat /etc/resolv.conf
```If it's set to 192.168.1.1 (or your router's internal IP address) you may consider changing to 4.2.2.1 (verizon I think) or 208.67.222.222 (opendns) which are free DNS services that I haven't had a problem with.

If you want to try changing your DNS server, I can help you do that too.

Also, on your Windows Vista box, you might try flushing the DNS cache.

To do this:
1) Open a command prompt as administrator.  (Right click it and hit Run As Administrator, if you have UAC enabled and need admin rights).
2) Run the command "ipconfig /flushdns" without the quotation marks.
3) It should say something like "dns cache flushed successfully" or something.  If it complains about needing elevated rights, you didn't run it as an administrator.

-Kirk

---

### Post by Drianos on 2009-07-04
ok, I did the vista thing(dont even know what for, lol) and then run your commands in my computer:
```
adrian@adrian-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:25:0a:69:ca  
          inet addr:170.168.1.3  Bcast:170.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:25ff:fe0a:69ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:46980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50083487 (50.0 MB)  TX bytes:4975288 (4.9 MB)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.11.1  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.44.1  Bcast:172.16.44.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:282 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

adrian@adrian-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 170.168.1.1
adrian@adrian-desktop:~$ 
```

If you can explain me the steps to change the DNS server will be great, since you are good explaining.

---

### Post by computer13137 on 2009-07-05
I was hoping the Vista commands would fix the problem on the Vista box, but I guess not.  It looks like your DNS is set to the local router IP, so that indicates to me that my original assumption is still correct.  Your router's DNS cache is probably the problem.

So I'm going to have you try changing your DNS server.

There are a lot of different ways to change your DNS server.  Since you're using a local area network with a DHCP server, I'm going to suggest changing the DNS server on your dhclient.conf for the Ubuntu boxes.  (If this works and fixes it, I can also explain how to do it on Windows Vista).

You'll need to open that file in your favorite editor.  I like 'pico' so I'm going to provide instructions for pico.  The following can be done in the command prompt. 

```
sudo pico /etc/dhcp3/dhclient.conf
```

Use the CTRL+W (find) hotkey in Pico.  Type "prepend" and press enter.  This should take you to a line that looks something like this.  Change that line.  We need to remove the # symbol (makes it a comment so it's skipped over) and change the DNS server to 208.67.222.222.  This is the free DNS server provided by [www.opendns.com](www.opendns.com) and is my personal preference.

```

[OLD LINE]
#prepend domain-name-servers 127.0.0.1;
[NEW LINE]
prepend domain-name-servers 208.67.222.222;

```

Press CTRL+X to exit Pico.  It will ask if you want to save the file, press Y and hit Enter.

Now either restart the PC or reset networking.

```
sudo /etc/init.d/networking restart
```

Then attempt to visit the website again.  That should work, and should prevent future DNS problems.  Once again, if this fixes it for you, reply to this and ask and I'll post a quick tutorial for changing your DNS server on Windows.  It's actually easier, but I don't want to confuse you by giving specific instructions for 2 different operating systems, here and now, lol.

And yeah, thanks. :)  I try my best, I know it's much easier for beginners to understand stuff when it's explained clearly.  That's why I hang out here... I kind of wish people had explained some stuff to me better.  Maybe wouldn't have taken me so many years on Linux to figure stuff out, lol.

Cheers,
Kirk

---

### Post by Drianos on 2009-07-05
It works!!! thx a lot.And yeah it is great when ppl explain you the problem as you do because you learn what each command do and what is the problem, some ppl just give you the commands and you dont know what have you just done lol.

Restarting the network didn't function, I had to restart my pc. The pages [www.ubuntuforums.org](www.ubuntuforums.org) and [www.ubuntu-es.org](www.ubuntu-es.org) didn't work but i think that it is a some problem with the page since sometimes it loaded and sometimes no before doing this. 
```

adrian@adrian-desktop:~$ ping -c 4 www.ubuntu-es.org
PING www.ubuntu-es.org (150.128.97.33) 56(84) bytes of data.
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=1 ttl=48 time=237 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=2 ttl=48 time=235 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=3 ttl=48 time=241 ms
64 bytes from barrabash.aco.uji.es (150.128.97.33): icmp_seq=4 ttl=48 time=237 ms

--- www.ubuntu-es.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 235.776/237.923/241.291/2.044 ms

adrian@adrian-desktop:~$ ping -c 4 www.megaupload.com
PING www.megaupload.com (69.5.88.214) 56(84) bytes of data.
64 bytes from hosted.by.cirn.net (69.5.88.214): icmp_seq=1 ttl=53 time=113 ms
64 bytes from hosted.by.cirn.net (69.5.88.214): icmp_seq=2 ttl=53 time=113 ms
64 bytes from hosted.by.cirn.net (69.5.88.214): icmp_seq=3 ttl=53 time=112 ms
64 bytes from hosted.by.cirn.net (69.5.88.214): icmp_seq=4 ttl=53 time=114 ms

--- www.megaupload.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 112.670/113.300/114.058/0.661 ms

adrian@adrian-desktop:~$ ping -c 4  www.ubuntuforums.org
PING www.ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=46 time=184 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=46 time=192 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=46 time=183 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=4 ttl=46 time=184 ms

--- www.ubuntuforums.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3002ms
rtt min/avg/max/mdev = 183.995/186.442/192.527/3.529 ms
adrian@adrian-desktop:~$ 
```

And dont worry about doing it in Vista, i don't really need it. Thx a lot for your help.

---

### Post by computer13137 on 2009-07-05
> **Drianos said:**
> It works!!! thx a lot.And yeah it is great when ppl explain you the problem as you do because you learn what each command do and what is the problem, some ppl just give you the commands and you dont know what have you just done lol.
Yeah, that's the general idea.  Glad I could help. :)

> **Drianos said:**
> Restarting the network didn't function, I had to restart my pc. The pages [www.ubuntuforums.org]("http://www.ubuntuforums.org") and [www.ubuntu-es.org]("http://www.ubuntu-es.org") didn't work but i think that it is a some problem with the page since sometimes it loaded and sometimes no before doing this. 
Ah, yeah.  I wasn't sure if restarting networking cleared the DNS cache or not.  I've actually never encountered any DNS issues on Ubuntu, so my fix was just based on past experiences with Windows DNS problems, lol.

Cheers,
Kirk

---

