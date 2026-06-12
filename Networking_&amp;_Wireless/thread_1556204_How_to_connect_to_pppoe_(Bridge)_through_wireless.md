---
title: "How to connect to pppoe (Bridge) through wireless"
date: 2010-08-19
forum: Networking &amp; Wireless
---

### Post by amirkabir on 2010-08-19
Hi :p
I had test a lot of way and read threads but..
I have a wireless modem (Asus dsl-g31), with my former ISP setting every things was ok (usr&pass inside modem and **modem as dialer**).
But my current ISP configuration became a really headache for me and it force me to use my **machine as dialer**, it work fine on $win7 but on Lucid!! (No simple way)
After reading threads:

1- I can see my modem conf through Firefox 192.168.1.1
2- Start **pppoeconf **and accept all defaults. 
3- Pon dsl-provider and poff

-- After pon, no internet access.
-- After restart Wondering!! there is no network manager icon (I can access it via shell).
-- **iwconfig**: wlan0 off.
-- **ifconfig**: wlan0 nothing send/receive. 
-- Also, i have test it with ethernet cable and dsl, through network manager, but      surprisingly my browser just browse **Google **and its sub domains!

What should i do next to get wireless connection on?
Regards.

---

### Post by amirkabir on 2010-08-19
Bump Bump

anybody, No idea?

---

### Post by grahammechanical on 2010-08-19
Have you changed ISPs? Am I correct? Did you put the information about your new ISP into the modem? If you did not then this might be your problem. A DSL or broadband modem will automatically dial the ISP and connect every time you switch it on if it has been programmed with the ISP telephone number and also your ISP username and password. This is what my modem does every day. But I had to put the correct settings into it first. Did you get an instruction leaflet with the modem?

regards

---

### Post by amirkabir on 2010-08-19
Oh yes it was the way i used for my last ISP but in my new ISP, they told me to just use bridge mode in modem configuration and enter usr&pass in OS dialer.
In win7 it works fine..
I also made new connection in my modem in former way (pppoe and usr&pass inside modem) but the connection didn't established at all.
I just wana know how dial with linux, to establish a wireless connection. 

Please, my friends, i do not want to stay in $win. ;)

---

### Post by dineshs on 2010-08-19
> After restart Wondering!! there is no network manager icon (I can access it via shell).
If you run pppoeconf,the file /etc/network/interfaces will have additional entries and Network manager will not manage your devices.If you want NM to do PPPoE dialling you must first edit /etc/network/interfaces
```
sudo gedit /etc/network/interfaces 
```
so that it contain only
```
auto lo
iface lo inet loopback
```
restart machine and configure the DSL tab in NM for PPPoE dialling.[COLOR="Purple"]But I think this will work only for wired[/COLOR].If you are using wireless it is better to configure your modem in PPPoE mode (If the modem supports)

---

### Post by amirkabir on 2010-08-19
Thanx dineshs.
I can't use pppoe on modem because of my ISP configs which force me to use bridge option of modem and usr&pass on OS dialer.
Yes i think it's true that NM dsl is just for wired connections.
IMO pppoeconf is capable for wireless connections too, but i don't know how to use it :)
```

auto lo
iface lo inet loopback

iface dsl-provider inet ppp
pre-up /sbin/ifconfig **wlan0 up** # line maintained by **pppoeconf**
provider dsl-provider

auto wlan0
iface wlan0 inet manual

```As you see **pppoeconf **tries to get **wlan0 up**, so it can use it, but for some reason wlan0 can't get up!!
It's good to mention that my wlan0 was ok before i use pppoeconf and i take advantage of wireless.
But now for better help and advice, this is what i have:
**Ping:**
```

root:ping 192.168.1.1
connect: Network is **unreachable**

```**Ifup:**
```

ifup wlan0
ifup: interface wlan0 already **configured**

```**Iwconfig:**
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

```**Ifconfig:**
```

eth0      Link encap:Ethernet  HWaddr 48:5b:39:22:f5:e6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:39 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B


```Regards.

---

### Post by amirkabir on 2010-08-19
Bump Bump

---

### Post by dineshs on 2010-08-20
Let */etc/network/interfaces*  be
```
auto lo
iface lo inet loopback

#iface dsl-provider inet ppp
#pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
#provider dsl-provider

#auto wlan0
#iface wlan0 inet manual
```
run
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 

```and set ```
managed=false
```
Restart(there will be no NM icon.Dont worry) See if *sudo pon dsl-provider* is connecting

---

### Post by amirkabir on 2010-08-21
I fixed it up :D

1- Enter usr&pass into **pppoecon**.
2- Restart, ok NM would be **disappear**.
3- gksudo gedit /etc/network/interfaces and **erase** lines under:
```

auto lo
iface lo inet loopback

```
4- Restart
5- pppoecong connection will retain.
6- sudo pon dsl-provider and wait at least 15 second for connection to establish.

[SIZE=5]We need a **wireless pppoe connection** in network manager just like **wired connections**.[/SIZE]

---

### Post by sKuarecircle on 2010-08-26
HI Guys, I have been having teh EXACT same problem, I followed teh instuctiosn in post #8, but after restart the NM Icon is back, but now it won;t pick up my netwrok at all, it sees it, but won't connect.

---

### Post by sKuarecircle on 2010-08-26
OK, after the above post I rebooted into Ubuntu and and ran pppoeconf again, it ran through and gave me teh result

 Sorry, I scanned 2 interfaces, but the Access            &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.  

Which makes sense since it isn't connected to teh netwrok so it wont pick up ant pppoe connections, I then plugge din my ethernet cable, that picked up fine all of a sudden ( it wasn't before) and then I ran pppoeconf again, this time around I was able to connect and setup my connection, however this is on a wire dconnection nowm I am still unable to run this in wireless. I would keep it wored but unfotrunatly that isn;t a possibility for me, also its worth mentioneing that windows picks up the netwrok without any hassles, so teh problem does not lie there.

Thanks so much fo ryour help!

---

### Post by dineshs on 2010-08-26
what does```
iwconfig
```say?

---

### Post by sKuarecircle on 2010-08-26
Here we go

> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

ppp1      no wireless extensions.




---

### Post by dineshs on 2010-08-26
As in post #5 edit /etc/network/interfaces so that it contains only those two lines.Save the file ,remove ethernet cable restart connect wifi(try) via NM and run
```
sudo pppoeconf wlan0
```
Also pl let me know the results of
```
ls /etc/ppp/peers
```

---

### Post by sKuarecircle on 2010-08-26
Ok I ran the first set of instructions, it ran a setup, asked me for my username password etc and then told me that it was all setup fine, and that I could run it whenevr i wanted my using pon-dsl provoder ( sorry have booted ack into windows to post this so don;t remeber exactly)

After running that though the internet still didn;t work ( ethernet disconnected as you said)

the results from the second instruction > ls: cannot open directory/etc/ppp/peers:Permission deied

---

### Post by dineshs on 2010-08-26
After running ```
sudo pon dsl-provider
```,wait for 1 minute then run ```
ping 4.2.2.1 -c3
``` and post the output
please also post the output of ```
sudo gedit /etc/network/interfaces
```

---

### Post by sKuarecircle on 2010-08-26
Kay ran pon dsl-provider, said that it was connected

then ran the ping

```
 connect:Network is unreachable
```

the output of sudo gedit /etc/netwrok/interfaces

```
 auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig wlan0 up # line maintained by pppoeconf
provider dsl-provider

auto wlan0
iface wlan0 inet manual 
```

---

### Post by dineshs on 2010-08-26
edit /etc/network/interfaces```
sudo gedit /etc/network/interfaces 
```
so that it contain only
```
auto lo
iface lo inet loopback
```
Now restart machine and try

---

### Post by sKuarecircle on 2010-08-26
Cool I did that, when the machine had finished restarting the NM icon was back on the top right, it flashes and then tells me I have been disconnected from teh network, it works though, because it is picking up  all the wireless netwroks around me, but it won't connect at all. just keeps trying, I checked the network password but that is definitly correct. Even deleted it out of the keyring thing where passwords are kept so that it forces a prompt agian when it tries...but still...nada, this is so wierd because it was working fine till I tried to connect using the pppOE bridge thing :(

---

### Post by dineshs on 2010-08-26
Before giving up,
Did you do this?
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf 

```and set ```
managed=false
```then restart(NM icon will be missing dont worry)

---

### Post by sKuarecircle on 2010-08-26
alright, I did that, the icon stays on teh top actually, and it was already changed to false... alright, doesn;t seem to be a solution here, I can do this though, I will set up my router with PPPoe with pass through so that my details are in teh router adnd I am permamanetly connected and the others in teh house, who are still running xp and macs can dial up... so how di I reset all this to how it was when I originally installed it, it was working fine then and connecting to all teh netwroks wirelessly, so lets leave the pppoe dialling stuff and just get it connected to the netwrok...could you help me reset it? Thanks so much, I ealise this is taking you rtime

---

### Post by dineshs on 2010-08-26
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and make ```
managed=true
```
```
sudo service network-manager stop
sudo service network-manager start
```
Now try to access router 
If you are not getting router page try after running
```
sudo dhclient wlan0
```

---

### Post by sKuarecircle on 2010-08-26
I did that, I have set up the router with my details so all i need to do now is reset my network setitng to back to what it was before i started playing aorund with the dial up bridging nonsense, it still won;t connecto to anything ( teh wireless)

---

### Post by dineshs on 2010-08-26
Since you have run sudo pppoeconf 
1)a file named [COLOR="Blue"]dsl-provider[/COLOR] will be created in /etc/ppp/peers.The following command 
```
gksu nautilus /etc/ppp/peers
```will show it.You need not delete it.It will not affect NM or your connection
2)Additional entries will be made in /etc/network/interfaces which we have already deleted
So there is nothing to worry.
Hope you have set wifi security in router

---

### Post by moboticdes on 2011-01-02
Just one side note, connecting in bridged mode to the modem is not the best way, usually setting the modem (where possible) to bridged + routed is better because you don't need the pon dsl-provider command and just need to set
/etc/sysctl.conf which must contain the following values (uncomment values or add where needed)  

     Code:
      net.ipv4.tcp_syncookies = 1
 net.ipv4.tcp_window_scaling = 0
 net.ipv4.tcp_ecn= 0 
This will avoid all problems.

hope it helps

---

