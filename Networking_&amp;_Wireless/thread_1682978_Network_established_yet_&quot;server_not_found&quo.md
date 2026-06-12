---
title: "Network established yet &quot;server not found&quot;"
date: 2011-02-06
forum: Networking &amp; Wireless
---

### Post by littlea5h on 2011-02-06
ok so im using a wireless netgear wgt111t usb 2.0 network with a BTHomeHub2-5GT2 router and i think the IP is 192.168.1.65. with a WPA-Personal key

i have a dual boot of Windows 7 and Ubuntu 10.10

So i successfully established my connection but whenever i load up firefox it still says "server cannot be found" and i even tried pingin an ip in terminal but it says network unreachable or smethin like that. i even tried the code etc/directory/interfaces but it said permission denied even tho theres one account which only i use on ubuntu. i tried researchin so much stuff but still havent found any solution..is there something im missing? or somethin i need to enable in the netgear settings from windows? :confused:

plzzz help me solve this problem, its driving me nuts!!!:?

---

### Post by arjuntank on 2011-02-06
can you dump the output of 
*ifconfig -a*

---

### Post by robsoles on 2011-02-07
> **littlea5h said:**
> ok so im using a wireless netgear wgt111t usb 2.0 network with a BTHomeHub2-5GT2 router and i think the IP is 192.168.1.65. with a WPA-Personal key

i have a dual boot of Windows 7 and Ubuntu 10.10

So i successfully established my connection but whenever i load up firefox it still says "server cannot be found" and i even tried pingin an ip in terminal but it says network unreachable or smethin like that. i even tried the code etc/directory/interfaces but it said permission denied even tho theres one account which only i use on ubuntu. i tried researchin so much stuff but still havent found any solution..is there something im missing? or somethin i need to enable in the netgear settings from windows? :confused:

plzzz help me solve this problem, its driving me nuts!!!:?


Welcome to UF.

What arjuntank is asking you to do is to put the command in terminal and then copy and paste the terminal's response in your reply post, just in case you are not familiar with 'dump'.

---

### Post by burned sausage on 2011-02-07
I also have the same problem as Littlea5h and it is sending me crackers.It was working O.K. a couple of days ago and then it just stopped.I have looked everywhere to try to re-establish the server,but ,no luck.

---

### Post by robsoles on 2011-02-07
> **burned sausage said:**
> I also have the same problem as Littlea5h and it is sending me crackers.It was working O.K. a couple of days ago and then it just stopped.I have looked everywhere to try to re-establish the server,but ,no luck.

Can you type```
ifconfig -a
```into terminal and then copy and paste the output to a reply to this thread?

---

### Post by littlea5h on 2011-02-07
> **arjuntank said:**
> can you dump the output of 
*ifconfig -a*

Ok so here is the dump from my ifconfig -a

```
~$ ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:19:db:d4:09:3f  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:43 Base address:0x2000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:212 errors:0 dropped:0 overruns:0 frame:0
            TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:16128 (16.1 KB)  TX bytes:16128 (16.1 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b7:23:d4  
            inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Another problem i forgot to mention whenever i restart and boot my Ubuntu,if i slightly move my arrow towards the Network Signal icon in the top right hand corner the whole ubuntu crashes and either comes up with:

1:Completely black screen
2:Black Screen that says Error: firmware is missing or somethin like that
3:the Ubuntu logo with the 4 dots at the bottom

and i cant do anything but turn the computer off from the power button. Before i start ubuntu i have to take my USB dongle out then after i put it in it doesnt crash at all but its a nightmare doin that. Also when i reboot back to my Windows 7 i have to replug the dongle back in for it to recognize the connection again. Its a bit of a pain! :(

---

### Post by littlea5h on 2011-02-07
help anyone?

---

### Post by robsoles on 2011-02-07
> **littlea5h said:**
> help anyone?

24 hours is a more polite bump.

> **littlea5h said:**
> Ok so here is the dump from my ifconfig -a

```
~$ ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:19:db:d4:09:3f  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:43 Base address:0x2000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:212 errors:0 dropped:0 overruns:0 frame:0
            TX packets:212 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:16128 (16.1 KB)  TX bytes:16128 (16.1 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b7:23:d4  
            inet addr:**10.42.43.1**  Bcast:10.42.43.255  Mask:255.255.255.0
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

...

I have made the IP address your wireless device is taking bold above, please boot into Windows and find out what IP address the machine is being assigned while that is booted instead.

I am betting it is a different IP address and I am halfway betting that 10.42.43.1 is either your router or it's first three octets don't even match your LAN - change the IP address that Ubuntu is being assigned for that wireless device to the one that Windows is using (including mask and subnet) and it will probably just work.

> **littlea5h said:**
> Another problem i forgot to mention whenever i restart and boot my Ubuntu,if i slightly move my arrow towards the Network Signal icon in the top right hand corner the whole ubuntu crashes and either comes up with:

1:Completely black screen
2:Black Screen that says Error: firmware is missing or somethin like that
3:the Ubuntu logo with the 4 dots at the bottom

and i cant do anything but turn the computer off from the power button. Before i start ubuntu i have to take my USB dongle out then after i put it in it doesnt crash at all but its a nightmare doin that. Also when i reboot back to my Windows 7 i have to replug the dongle back in for it to recognize the connection again. Its a bit of a pain! :(

I can only suggest that the system tries to access something about a network driver that isn't ready yet - this doesn't happen on my systems so I can't comment too much about it.

---

### Post by littlea5h on 2011-02-07
> **robsoles said:**
> 24 hours is a more polite bump.



I have made the IP address your wireless device is taking bold above, please boot into Windows and find out what IP address the machine is being assigned while that is booted instead.

I am betting it is a different IP address and I am halfway betting that 10.42.43.1 is either your router or it's first three octets don't even match your LAN - change the IP address that Ubuntu is being assigned for that wireless device to the one that Windows is using (including mask and subnet) and it will probably just work.



I can only suggest that the system tries to access something about a network driver that isn't ready yet - this doesn't happen on my systems so I can't comment too much about it.

Thanks. the ip address for my Windows machine is 192.168.1.65 im guessing, 
Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : home
   Link-local IPv6 Address . . . . . : fe80::9dfd:8a37:85e3:a983%12
   IPv4 Address. . . . . . . . . . . : 192.168.1.65
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.home:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : home

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:8fa:219c:a95c:7119
   Link-local IPv6 Address . . . . . : fe80::8fa:219c:a95c:7119%13
   Default Gateway . . . . . . . . . : ::

how to find out the address of my router? How do i change the IP address  my Ubuntu is being assigned and how do i find out which one Windows is  using? Sorry, just new to all this stuff and dont really understand all  the technical terminology. Thanks once again.

---

### Post by littlea5h on 2011-02-07
Okay so i made a few minor changes to the way i setup my wireless connection in Ubuntu and this time the ifconfig -a results display as follows:

> ~$ ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:19:db:d4:09:3f  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:43 Base address:0x2000 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:646 errors:0 dropped:0 overruns:0 frame:0
            TX packets:646 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:51998 (51.9 KB)  TX bytes:51998 (51.9 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b7:23:d4  
            inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Its now changed to match my Windows config details, apart from the gateway which last 3 digits should be 254 not 255 although i entered 254 in the ubuntu settings. Its also made some changes to my firefox browser. this time when i try loading a page up it says its loading for like 3minutes then it goes back to the server cannot be found page. I think once i get my gateway sorted that should work? any way to fix that? also as u can see form my windows ping results its sayin i have an IPv6 ip though most of the threads in this forum said dont enable that but should i try adding that to see if it works? Thanks alot, if theres anything im missing out please let me know. Also i chose "No Proxy" for my Firefox settings.

---

### Post by robsoles on 2011-02-07
Router, usually referred to as 'gateway' by OS, address appears to be: 192.168.1.254

Boot Ubuntu and wait for everything to 'load'/settle to a point where you can access the network menu using the icon on the panel without crashing the system. Right-click the icon in the panel and choose "Edit Connections".

Under second tab, "Wireless", you should find one connection - select it and choose 'Edit' from the right side of that window. In the new window that opens select the 'IPV4' tab, you want to make 'method'="manual" and then enter

192.168.1.65 for 'Address', 255.255.255.0 for 'netmask' and 192.168.1.254 for 'gateway'.

In 'DNS' text field enter same as for gateway, 192.168.1.254, press 'OK' or 'Apply' on windows till they all close. If wireless connection doesn't "roll" to new settings then logout and log back in (or even restart altogether) and recheck.

How is that?

---

### Post by littlea5h on 2011-02-07
Thanks. Already did that in response to your previous reply, but i will try again and see if it works second time round. Fingers Crossed, Thanks!

---

### Post by littlea5h on 2011-02-07
Okay so tried again but still no luck :/ Would i need to add an IPv6 address? Also my windows uses DHCP so it should pick it up straightaway. Also do i need to change the ip and gateway for 'lo' as that doesnt match my wlan one?

---

### Post by robsoles on 2011-02-07
Don't fiddle with 'lo', it is "local loopback" and needs to be left as set by the system.

When you first went into the 'Edit connections', under Ubuntu, was the 'wireless connection' using DHCP or was it manually set already?

You can try changing it to 'method'="dhcp", again about logging out or restarting to re-try it.

After you set 'method'="dhcp", if you still don't have an operable connection, please show me the terminal's response to 'ifconfig -a' again.

---

### Post by littlea5h on 2011-02-07
> **robsoles said:**
> Don't fiddle with 'lo', it is "local loopback" and needs to be left as set by the system.

When you first went into the 'Edit connections', under Ubuntu, was the 'wireless connection' using DHCP or was it manually set already?

You can try changing it to 'method'="dhcp", again about logging out or restarting to re-try it.

After you set 'method'="dhcp", if you still don't have an operable connection, please show me the terminal's response to 'ifconfig -a' again.

I tried setting it to DHCP but this time no connection would establish, it would just keep scanning and then after a few minutes would say disconnected. This is the dump i managed to get for that method

```
~$ ifconfig -a
  eth0      Link encap:Ethernet  HWaddr 00:19:db:d4:09:3f  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
            Interrupt:43 
   
  lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:91 errors:0 dropped:0 overruns:0 frame:0
            TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
            RX bytes:7599 (7.5 KB)  TX bytes:7599 (7.5 KB)
   
  wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:b7:23:d4  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
```

And when its back to set as manual its the same results as i posted before this one. When i first set it up, the method was set to Share with other computers so i had to change it to either DHCP or Manually. I tried both DHCP methods yet still no luck. Im guessing it must be the smallest thing to solve this problem,always happens in my case. :-?

---

### Post by arjuntank on 2011-02-07
okay, first, you dont need ipv6. second, you need to follow this: 
[http://ubuntuforums.org/showpost.php?p=2361840&postcount=9]("http://ubuntuforums.org/showpost.php?p=2361840&postcount=9")
 
follow that thread. and dont check internet connectivity through firefox. you can try to ping google..like 
*~$ ping google.com*

also, you dont need to check ip settings on windows! from your initial ifconfig output, it looks like you can put any of 10.42.43.X. i think thats what your router assigned you through dhcp, unless you manually configured these ip: 10.42.43.1 

you just need to follow the thread above and it *should* work.

---

### Post by robsoles on 2011-02-08
> **arjuntank said:**
> okay, first, you dont need ipv6. second, you need to follow this: 
[http://ubuntuforums.org/showpost.php?p=2361840&postcount=9]("http://ubuntuforums.org/showpost.php?p=2361840&postcount=9")
 
follow that thread. and dont check internet connectivity through firefox. you can try to ping google..like 
*~$ ping google.com*

also, you dont need to check ip settings on windows! from your initial ifconfig output, it looks like you can put any of 10.42.43.X. i think thats what your router assigned you through dhcp, unless you manually configured these ip: 10.42.43.1 

you just need to follow the thread above and it *should* work.

fyi: 10.42.43.x is not OP's home network. try: 192.168.1.x

---

### Post by littlea5h on 2011-02-08
> **arjuntank said:**
> okay, first, you dont need ipv6. second, you need to follow this: 
[http://ubuntuforums.org/showpost.php?p=2361840&postcount=9](http://ubuntuforums.org/showpost.php?p=2361840&postcount=9)
 
follow that thread. and dont check internet connectivity through firefox. you can try to ping google..like 
*~$ ping google.com*

also, you dont need to check ip settings on windows! from your initial ifconfig output, it looks like you can put any of 10.42.43.X. i think thats what your router assigned you through dhcp, unless you manually configured these ip: 10.42.43.1 

you just need to follow the thread above and it *should* work.

Thanks...i'll try this and get back to you.

---

### Post by littlea5h on 2011-02-08
Okay i tried to follow that thread but i only got this far:

> ~$ sudo apt-get install ndiswrapper
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package ndiswrapper
  aysha@littlea5h:~$ unzip wg111t.zip
  Archive:  wg111t.zip
  replace athfmwdl.inf? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
    inflating: athfmwdl.inf            
  replace netwg11t.inf? [y]es, [n]o, [A]ll, [N]one, [r]ename: y
    inflating: netwg11t.inf            
  aysha@littlea5h:~$ cd wg111t
  bash: cd: wg111t: No such file or directory


Any thing im doing wrong?

---

### Post by robsoles on 2011-02-08
> **littlea5h said:**
> Okay i tried to follow that thread but i only got this far:



Any thing im doing wrong?

The zip archive is unpacking 'flat' - it means that it isn't unpacking to a sub-folder, you can check for the presence of the two files the zip archive has by typing 'ls', into terminal after unpacking archive, and looking for the .inf files in the listing that will be given by ls.

You could make a subfolder yourself and transfer the files there```
md wgt111t
mv *.inf wgt111t
```

After that 'cd wgt111t' will work and you can continue the steps of the instructions in that other thread.


If you could 'see' your wireless AP in the list of networks under the network icon in Ubuntu before trying this with ndiswrapper then it is less likely to me that this will work **BUT** I have been wrong before so I'm not saying this to stop/discourage you from trying it.

---

### Post by arjuntank on 2011-02-08
> **littlea5h said:**
> Okay i tried to follow that thread but i only got this far:



Any thing im doing wrong?


looks like thats an older version of guide. 
follow this:
1. ~$ sudo apt-get update

2. ~$ sudo apt-get install ndisgtk 
  (press yes[Y] if it asks for anything)

3. ~$ sudo ndisgtk 

4. Press "Install New Driver" and select the athfmwdl.inf file that you extracted from wg111t.zip. if you dont know where you extracted, its in your home directory. type:
~$ nautilus ~/
to open up your home directory. make sure you have netwg11t.inf and athfmwdl.inf there.

5. Again, press install new driver and select netwg11t.inf from the same location. (you need to install both .inf files). and reboot. should be working by now :D

---

### Post by littlea5h on 2011-02-15
> **arjuntank said:**
> looks like thats an older version of guide. 
follow this:
1. ~$ sudo apt-get update
 
2. ~$ sudo apt-get install ndisgtk 
(press yes[Y] if it asks for anything)
 
3. ~$ sudo ndisgtk 
 
4. Press "Install New Driver" and select the athfmwdl.inf file that you extracted from wg111t.zip. if you dont know where you extracted, its in your home directory. type:
~$ nautilus ~/
to open up your home directory. make sure you have netwg11t.inf and athfmwdl.inf there.
 
5. Again, press install new driver and select netwg11t.inf from the same location. (you need to install both .inf files). and reboot. should be working by now :D
 
 
Okay im trying all these things but im still getting errors. I don't think my internet will ever fix on the ubuntu :( after i do the first bit it starts installing some things. Most of it starts with Int "somethingsomething" downloaded
 
then it says an error...something wild happened and it just stops at 60% in the terminal n keeps repeating the same thing.
 
Also btw i tried installin the drivers from the .zip file and it said it was an invalid driver, so i had to install from my netgar CD n that worked. In Windows Wireless Drivers..it says Yes for detecting the netwg11t.inf  driver but no for the athfmwdl.inf . i dont know what the problem is, maybe my ubuntu didnt install correctly or maybe all the files didnt download onto the setup CD correctly..
 
The main problem is that when i set up the connection in the Network Connections setup, i set my input mask as 196.168.1.254 wheras in the terminal for ifconfig -a, the Broadcast shows as 196.168.1.25**[COLOR=red]5[/COLOR] **instead. I think once this problem is tackled it might be working? I think if we start from the beginning of my programme, i can guide you to find a way to fix this.

---

### Post by robsoles on 2011-02-15
If your IP address is 192.168.1.x, where x is between 1 and 255 then your broadcast address should become 192.168.1.255 and your (correct) network mask is likely to be 255.255.255.0

Can you just set it to take it's settings from DHCP?


I have to go to work, I looked for a good explanation of IP addresses on the internet but I didn't find a nice straightforward one in time,sorry.

---

### Post by littlea5h on 2011-02-15
> **robsoles said:**
> If your IP address is 192.168.1.x, where x is between 1 and 255 then your broadcast address should become 192.168.1.255 and your (correct) network mask is likely to be 255.255.255.0

Can you just set it to take it's settings from DHCP?


I have to go to work, I looked for a good explanation of IP addresses on the internet but I didn't find a nice straightforward one in time,sorry.

On my Windows, the gateway is 192.168.1.254 therfore i set it the same in Ubuntu but its still showing as .255 in the terminal.

How would i set it to take settings from DHCP?

Thanks

---

### Post by robsoles on 2011-02-15
Assuming you are using the GUI for it you would go to the page where you can set the IP address and look for the dropdown box that currently says something awfully similar to "assign manually" and check it for the DHCP option - select it and hit OK.

To set it manually there are three text boxes in a row that aren't obviously separated until you enter data in them and then there are two more boxes below - in the three boxes should be IP address, Network Mask and Gateway, in the top box below (DNS) repeat the IP from the Gateway box

So I think that what you want (if setting manually) is
192.168.1.254 255.255.255.0 192.168.1.1

192.168.1.1

but that is based on assuming that the router/modem is at 192.168.1.1

---

### Post by littlea5h on 2011-02-15
> **robsoles said:**
> Assuming you are using the GUI for it you would go to the page where you can set the IP address and look for the dropdown box that currently says something awfully similar to "assign manually" and check it for the DHCP option - select it and hit OK.

To set it manually there are three text boxes in a row that aren't obviously separated until you enter data in them and then there are two more boxes below - in the three boxes should be IP address, Network Mask and Gateway, in the top box below (DNS) repeat the IP from the Gateway box

So I think that what you want (if setting manually) is
192.168.1.254 255.255.255.0 192.168.1.1

192.168.1.1

but that is based on assuming that the router/modem is at 192.168.1.1


Tried that..still no luck :( its still showing the same things for ifconfig -a

---

### Post by robsoles on 2011-02-15
Sorry, just reviewed earlier in thread where you indicate the IP address that Windows gets assigned and it is actually;

```
IP Address, Subnet Mask, Gateway
192.168.1.65, 255.255.255.0, 192.168.1.254

DNS: 192.168.1.254
```

BUT when you made this post, [http://ubuntuforums.org/showpost.php?p=10437653&postcount=10](http://ubuntuforums.org/showpost.php?p=10437653&postcount=10), everything was right except that your gateway is not displayed in the information that 'ifconfig -a' returns - you believed the system was changing your gateway setting to x.x.x.255 but I think you were mistaking the subnet broadcast address for your gateway in the output (and I can't confirm or deny what your gateway setting may have been from it).



I am going to log on to an Ubuntu machine here at the office and get you a snapshot of the dialog box I am trying to get you to select DHCP in, back in a few minutes :)

---

### Post by robsoles on 2011-02-15
OK, made it to page two of the thread where you say what the result of choosing DHCP is - more lemons.

I attach the picture I offered because I offered it but I realise that it is practically an insult seeings as you must have found it already to make the post on page 2 :roll:


If Windows is using DHCP to get the settings that it is using and Ubuntu is scanning to no success, when set to DHCP, then I think that the driver(s) for the wifi device are not correctly installed or are otherwise not configured correctly.


Would you please tell me about steps you took to install the wgt111 into Ubuntu - did you follow [https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T) ???

---

### Post by littlea5h on 2011-02-15
> **robsoles said:**
> OK, made it to page two of the thread where you say what the result of choosing DHCP is - more lemons.

I attach the picture I offered because I offered it but I realise that it is practically an insult seeings as you must have found it already to make the post on page 2 :roll:


If Windows is using DHCP to get the settings that it is using and Ubuntu is scanning to no success, when set to DHCP, then I think that the driver(s) for the wifi device are not correctly installed or are otherwise not configured correctly.


Would you please tell me about steps you took to install the wgt111 into Ubuntu - did you follow [https://help.ubuntu.com/community/WifiDocs/Device/WG111T](https://help.ubuntu.com/community/WifiDocs/Device/WG111T) ???

Oh, thanks! Yes they are the steps i followed. It didnt detect the driver straightaway so when i crossed it off and went back to Windows Wireless drivers it said Yes for the driver  netwg111t.inf but No for the athfmwdl.inf driver and still says no. Also when trying to install ndiswrapper before it took a long time and i dont think it installed that package correctly tho it still shows in The Software centre its installed?

---

### Post by robsoles on 2011-02-16
Before following any of the advice below, please tell me that you followed step 7 and added the line to /etc/modules - if not and you can see how to do it lately then please do it, if you are not sure of what to do I will paint as clear a picture of it as I can...


Otherwise, from where you are it may as well be a big purge and a reinstall.

Purging may be taken care of just by asking apt to purge ndiswrapper in terminal;```
sudo apt-get purge ndiswrapper
```(Say yes to whatever it asks (unless it asks about removing 'gnome-desktop' or anything seeming not to belong to ndiswrapper), if part or all of the response from terminal is that interesting or perplexing then take note of it and let me see please :))

You may have to remove that line you added to /etc/modules you made in step 7

Now let's try you a (hopefully) completely graphically guided way, please open "System"->"Administrator"->"Synaptic Package Manager" and type 'ndis' into the search box. A bunch (about 5) of entries should remain and they should be unchecked, if anything that starts with 'ndis' is checked right now then uncheck them and apply (and approve :roll:) the removal.

Now just check ndisgtk and it should want to add ndiswrapper-common and a utils package too, I am checking this using 10.04 and 10.10 could have more (perhaps less but doubtful), 'mark' it and apply, approve (:roll: :lol:) and then look for "System"->"Administration"->"Windows Wireless Drivers" :)

Hit the "+ Install New Driver" button and about here I apologise that I don't have a USB wgt111t and my couple of wireless devices I do have work in a vanilla/plain install of Ubuntu - tell me what blocks you (or how unsuccessful it is in spite of accepting drivers etc) this way and I'll reconsider again!

I didn't check which repository I am getting ndisgtk from but I think it's in the main, if you can't see it for 'ndis' in Synaptic then please look into your software sources ("Settings"->"Repositories" in Synaptic) and enable universe and multiverse if they aren't - unless you are effected by them copyright or legal issues...

---

### Post by littlea5h on 2011-02-16
> **robsoles said:**
> Before following any of the advice below, please tell me that you followed step 7 and added the line to /etc/modules - if not and you can see how to do it lately then please do it, if you are not sure of what to do I will paint as clear a picture of it as I can...


Otherwise, from where you are it may as well be a big purge and a reinstall.

Purging may be taken care of just by asking apt to purge ndiswrapper in terminal;```
sudo apt-get purge ndiswrapper
```(Say yes to whatever it asks (unless it asks about removing 'gnome-desktop' or anything seeming not to belong to ndiswrapper), if part or all of the response from terminal is that interesting or perplexing then take note of it and let me see please :))

You may have to remove that line you added to /etc/modules you made in step 7

Now let's try you a (hopefully) completely graphically guided way, please open "System"->"Administrator"->"Synaptic Package Manager" and type 'ndis' into the search box. A bunch (about 5) of entries should remain and they should be unchecked, if anything that starts with 'ndis' is checked right now then uncheck them and apply (and approve :roll:) the removal.

Now just check ndisgtk and it should want to add ndiswrapper-common and a utils package too, I am checking this using 10.04 and 10.10 could have more (perhaps less but doubtful), 'mark' it and apply, approve (:roll: :lol:) and then look for "System"->"Administration"->"Windows Wireless Drivers" :)

Hit the "+ Install New Driver" button and about here I apologise that I don't have a USB wgt111t and my couple of wireless devices I do have work in a vanilla/plain install of Ubuntu - tell me what blocks you (or how unsuccessful it is in spite of accepting drivers etc) this way and I'll reconsider again!

I didn't check which repository I am getting ndisgtk from but I think it's in the main, if you can't see it for 'ndis' in Synaptic then please look into your software sources ("Settings"->"Repositories" in Synaptic) and enable universe and multiverse if they aren't - unless you are effected by them copyright or legal issues...

Before following this i thought i would provide some screenshots incase i missed anything out or incase u see anything which may be wrong. I hope this is helpful. Thanks

---

### Post by robsoles on 2011-02-16
I see from pictures 1 & 4 that your IP address for Ubuntu is 192.168.1.254 and the gateway you are using is 192.168.1.1

The post in which you showed the settings that Windows takes via DHCP shows that the gateway(modem/router/switch) is at 192.168.1.254 so **what is happening right now with Ubuntu is that it is trying to take the same address on the network as the modem/router**.

Please change the Ubuntu IP address to match the Windows DHCP'd one:  **192.168.1.65 **and change the gateway to 192.168.1.254 and go right to the trouble of restarting Ubuntu to try it please.

---

### Post by littlea5h on 2011-02-16
> **robsoles said:**
> I see from pictures 1 & 4 that your IP address for Ubuntu is 192.168.1.254 and the gateway you are using is 192.168.1.1

The post in which you showed the settings that Windows takes via DHCP shows that the gateway(modem/router/switch) is at 192.168.1.254 so **what is happening right now with Ubuntu is that it is trying to take the same address on the network as the modem/router**.

Please change the Ubuntu IP address to match the Windows DHCP'd one:  **192.168.1.65 **and change the gateway to 192.168.1.254 and go right to the trouble of restarting Ubuntu to try it please.

Yes this is what i had it set to as before u told me to change it. It still doesnt seem to work with these settings

---

### Post by robsoles on 2011-02-16
Can you make your settings match my edit of your picture and then reboot and then try your connection again please.

[img]http://ubuntuforums.org/attachment.php?attachmentid=183673&stc=1&d=1297904905[/img]

---

### Post by littlea5h on 2011-02-18
> **robsoles said:**
> Can you make your settings match my edit of your picture and then reboot and then try your connection again please.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=183673&stc=1&d=1297904905[/IMG]

Tried that as i had it set to that previously but still doesnt connect...i think it must be to do with the problem below. It happened when i restarted Ubuntu:

```
speech-dispatcher disabled; edit /etc/default/speed-dispatcher
    *Pulse Audio configured for per-user sessions
  saned disabled; edit /etc/default/saned
    *Enabling additional executable binary formats binfmt-support [OK]
  *checking battery state… [OK]
   
  [20.072060] tda1004x: timeout waiting for DSP ready
  [20.163283] tda1004x: no firmware upload (timeout or file not found?)
  [30.256665] ndiswrapper (NdisWriteErrorLogEntry:190) log: c0001389, count:4, return_address:fb1b4c6b
  [30.256688] ndiswrapper (NdisWriteErrorLogEntry:193):code:0xf3fc7800 
  [30.256703] ndiswrapper (NdisWriteErrorLogEntry:193):code:0x28
  [30.256716] ndiswrapper (NdisWriteErrorLogEntry:193) :code:0xf8472000
  [30.256729] ndiswrapper (NdisWriteErrorLogEntry:193) :code:0xf8472000

```

---

### Post by robsoles on 2011-02-19
> **robsoles said:**
> ..., from where you are it may as well be a big purge and a reinstall.

Purging may be taken care of just by asking apt to purge ndiswrapper in terminal;```
sudo apt-get purge ndiswrapper **ndisgtk**
```(Say yes to whatever it asks (unless it asks about removing 'gnome-desktop' or anything seeming not to belong to ndiswrapper), if part or all of the response from terminal is that interesting or perplexing then take note of it and let me see please :))

You may have to remove that line you added to /etc/modules you made in step 7

Now let's try you a (hopefully) completely graphically guided way, please open "System"->"Administrator"->"Synaptic Package Manager" and type 'ndis' into the search box. A bunch (about 5) of entries should remain and they should be unchecked, if anything that starts with 'ndis' is checked right now then uncheck them and apply (and approve :roll:) the removal.

Now just check ndisgtk and it should want to add ndiswrapper-common and a utils package too, I am checking this using 10.04 and 10.10 could have more (perhaps less but doubtful), 'mark' it and apply, approve (:roll: :lol:) and then look for "System"->"Administration"->"Windows Wireless Drivers" :)

Hit the "+ Install New Driver" button and about here I apologise that I don't have a USB wgt111t and my couple of wireless devices I do have work in a vanilla/plain install of Ubuntu - tell me what blocks you (or how unsuccessful it is in spite of accepting drivers etc) this way and I'll reconsider again!

I didn't check which repository I am getting ndisgtk from but I think it's in the main, if you can't see it for 'ndis' in Synaptic then please look into your software sources ("Settings"->"Repositories" in Synaptic) and enable universe and multiverse if they aren't - unless you are effected by them copyright or legal issues...

Purge and reinstall, don't install 'ath......' stuff just 'netwg...' stuff, (*shouldn't require modification to /etc/modules as far as I know) restart, retry and post back your (hopefully new and different) result please :)

---

### Post by littlea5h on 2011-02-19
> **robsoles said:**
> Purge and reinstall, don't install 'ath......' stuff just 'netwg...' stuff, (*shouldn't require modification to /etc/modules as far as I know) restart, retry and post back your (hopefully new and different) result please :)

Ok, so i started with the first line in the terminal but it was unable to find the package 

```
aysha@littlea5h:~$ sudo apt-get purge ndiswrapper
  [sudo] password for aysha: 
  Reading package lists... Done
  Building dependency tree       
  Reading state information... Done
  E: Unable to locate package ndiswrapper
  
```

---

### Post by robsoles on 2011-02-19
Looks like you didn't notice my edit where I added the one that is on your system.
```
apt-get purge ndisgtk
```

---

### Post by arjuntank on 2011-02-21
> **littlea5h said:**
> Before following this i thought i would provide some screenshots incase i missed anything out or incase u see anything which may be wrong. I hope this is helpful. Thanks

littlea5h, look at picture 3, wlan1.jpg. you are connecting to BT to your wireless router right? with adhoc? wifi doesnt connect though adhoc. they connect through access points. so change it to access point or wifi. it was on adhoc all this time? adhoc is for laptop-to-laptop connections. from one WNIC to another. i hope this helps.

---

