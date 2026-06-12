---
title: "wl module has to be restarted after boot for wirless to work"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by psifunk on 2013-01-22
Hi, I have a very strange problem. I am starting a new thread since I probably tried every solution founds on forums and nothing exactly solves the problem although I am now very close. So, I did a fresh install of ubuntu 12.04 yesterday on a Dell Latitude e4300 laptop. There were problems with the wireless and I finally got it to work with the wl driver after tweaking things, blqcklisting other drivers etc as mentioned in various threads. However the connection was very slow. This was the same problem I had with another laptop (an asus eee pc) with the same network. I initially thought it was a problem of that laptop. Since I now had this problem on two different machines, I looked it up and there are actually many threads on this kind of problems that mention an option called disable_11n, presumably it also had to do with the hardware of my provider (free.fr). I tried all that and to cut a long story short i narrowed down the problem to the following:

1.after startup and logging on to unity the wireless connects automatically to my network but the connection is slow to non existent

2. after that i open a terminal and type

```
sudo rmmod  wl
```  (wireless gets disabled)
```
sudo modprobe wl
``` (wireless gets re-enabled after half a minute or so)

3. it automatically connects again to my network and works like a charm! and fast too.


I then tried to do this as a startup script. I followed instructions to make it work from init.d , add it to rc.locale and to /etc/modules, one at a time. I still had to restart it as above and only then it would work. I am not sure if i did something wrong here.

By the way the option disable_11n=1 seems irrelevant to my problem.

Note that I have this problem only for free.fr wireless boxes (my provider hardware) and on two ubuntu machines. I wouldn't know where to start to give you some useful output as I am very confused as to where the problem actually resides (driver, laptop hardware,ubuntu ,provider hardware, bad script skills). My problem then is how to make this a permanent solution.

 Some possibly relative output I can think of is (I note if there is any difference in the output before and after having disabled re-enabled wl)

```
marios@mrLap:~$ lspci | grep Wireless
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
``````
marios@mrLap:~$ iwconfig
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated  
          Link Quality:5  Signal level:214  Noise level:166
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```(similar signal and noise levels before and after, same linq quality)


This is the before ifconfig 
```
eth0      Link encap:Ethernet  HWaddr 00:26:b9:96:a3:02  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:22 Mémoire:f6ae0000-f6b00000 

eth2      Link encap:Ethernet  HWaddr 90:4c:e5:77:a8:90  
          inet adr:192.168.1.49  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: 2a01:e34:edf9:1990:a4c0:ddea:66c1:53b7/64 Scope:Global
          adr inet6: 2a01:e34:edf9:1990:924c:e5ff:fe77:a890/64 Scope:Global
          adr inet6: fe80::924c:e5ff:fe77:a890/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:263 erreurs:0 :0 overruns:0 frame:1842
          TX packets:461 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:196451 (196.4 KB) Octets transmis:69054 (69.0 KB)
          Interruption:17 Adresse de base:0xc000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:81 erreurs:0 :0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:8642 (8.6 KB) Octets transmis:8642 (8.6 KB)
```and this the after
```
marios@mrLap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:96:a3:02 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:22 Mémoire:f6ae0000-f6b00000

eth2      Link encap:Ethernet  HWaddr 90:4c:e5:77:a8:90 
          inet adr:192.168.1.49  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: 2a01:e34:edf9:1990:924c:e5ff:fe77:a890/64 Scope:Global
          adr inet6: fe80::924c:e5ff:fe77:a890/64 Scope:Lien
          adr inet6: 2a01:e34:edf9:1990:6c9c:c93b:31f5:59e/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1220 erreurs:0 :0 overruns:0 frame:12988
          TX packets:1292 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:1116056 (1.1 MB) Octets transmis:194483 (194.4 KB)
          Interruption:17 Adresse de base:0xc000

lo        Link encap:Boucle locale 
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1259 erreurs:0 :0 overruns:0 frame:0
          TX packets:1259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:93783 (93.7 KB) Octets transmis:93783 (93.7 KB)


```The output is exactly the same in both cases for lsmod |grep wl and rfkill list wifi 

```
marios@mrLap:~$ lsmod |grep wl
wl                   2646632  0
lib80211               14040  2 wl,lib80211_crypt_tkip

``````
marios@mrLap:~$ rfkill list wifi
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by chili555 on 2013-01-22
I love a mystery.

> disable_11nWhere and how did you do this? May I see:```
lspci -nn | grep 0280
```While I study your results, please try editing Network Manager to ignore IPv6 as shown attached. Then reboot and let me have your report.

---

### Post by psifunk on 2013-01-22
Hi chili555, thanks for the interest. 

The 11n_disable=1  option seems to be a solution proposed often for slow wifi connection problems relative to iwlwifi and iwlagn modules. I initialy thought this was the problem but I don't think its relative any more. In order for that option to work I had to stop and restart the modules. After tweaking around I realised that I don't need iwlwifi to be running or that option, and that what was making it work was restarting wl. I had created a configuration file in /etc/moprobe.d/ where I had only this option , namely it read

options iwlagn 11n_disable=1

I deleted this file before starting the thread here. This method is for example mentioned at

[http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards](http://askubuntu.com/questions/130499/how-do-i-fix-slow-wireless-on-intel-wireless-cards)

Here's the output you requested
```
marios@mrLap:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

```

---

### Post by chili555 on 2013-01-22
>  After tweaking around I realised that I don't need iwlwifi to be running or that option, Correct! It has nothing to do with your situation. I only mention this as a point for the searchers to learn from. Did you try ignoring IPv6? Does it help?

---

### Post by psifunk on 2013-01-22
Aha, so, the ipv6 results are again strange but maybe we are closer now: 
I set it to ignore ipv6 settings for my wireless network as in the picture you attached. I restarted the laptop and it couldn't see my network anymore. So i went and changed back to automatic the ipv6 setting and as soon as i saved it, the network appeared and it connected automatically. The wifi connection is now fine without having to do the rmmod and modprobe for wl!! What do you make of this?

---

### Post by chili555 on 2013-01-22
I'm not at all sure what to make of it! I suspect it's an anomaly and that a few days from now, the old behavior may return.

What, if anything, currently resides here?```
cat /etc/rc.local
```

---

### Post by psifunk on 2013-01-22
The problem seems to be solved! I changed again the ipv6 to ignore for my wireless network and restarted. This time it saw the network and connected automatically, internet access works, is fast and fine! I restarted a second time and everything seems fine now! So thank you chili555, it seems that I was looking on all other kinds of sources of problems but you did a good diagnosis. Do you have any idea what the issue had been all along with ipv6?

---

### Post by psifunk on 2013-01-22
>  I suspect it's an anomaly and that a few days from now, the old behavior may return.


maybe I should torture this a bit more before putting the SOLVED tag

nothing there
```
marios@mrLap:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
exit 0

```

i am restarting again to see if the fix holds

---

### Post by psifunk on 2013-01-22
well restarted again and it works fine. Since I spent several hours with no definitive result, let me make a note for other users that are trying to make the rmmod wl, modprobe wl temporary fix permanent (as mentioned in several threads for slow wifi connection) that it might suffice to ignore ipv6 for the network and forget about these commands.

---

### Post by chili555 on 2013-01-22
> Do you have any idea what the issue had been all along with ipv6?All I know is that some drivers do quite well with the relatively new IPv6 and some not at all well. When I saw that you had a valid IPv6 address from your service provider, I felt that was a likely candidate:> eth2      Link encap:Ethernet  HWaddr 90:4c:e5:77:a8:90  
          inet adr:192.168.1.49  Bcast:192.168.1.255  Masque:255.255.255.0
          [COLOR="Red"]adr inet6: 2a01:e34:edf9:1990:a4c0:ddea:66c1:53b7/64 Scope:Global[/COLOR]
          adr inet6: 2a01:e34:edf9:1990:924c:e5ff:fe77:a890/64 Scope:Global
          adr inet6: fe80::924c:e5ff:fe77:a890/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:263 erreurs:0 :0 overruns:0 frame:1842Frankly, when you said above that it didn't seem to help, I was skeptical.

I suggest you watch this for a few days and either mark it Solved or post back and we'll dig deeper.

---

### Post by psifunk on 2013-01-22
Yes well, I didn't think that it could be something that simple either considering that I spent hours researching this before posting. But I can't complain that it was that simple! 

So to summarize the fix, on the first restart after ignoring ipv6 it wouldn't see the network anymore. Setting ipv6 vack to automatic, it saw it, connected and worked fine without having to run rmmod wl and modprobe wl, something that never happened in the previous 30 or so restarts i did trying other stuff. Then i ignored ipv6 again and restarted again. This time it saw the network, connected automatically and the connection was again fast and working. 

Three more restarts later it still works. So I guess we can be sure that there was something to do with ipv6.

 I am also sceptical how long this will last but for now problem solved and a clue was uncovered although it is still a mystery as to what was happening and what restarting wl has to do with this.

I will put SOLVED in a few days i guess if it holds. Thanks for the tip chili555.

---

### Post by psifunk on 2013-01-30
So anyone having problems with **SLOW internet connection** and has a modem with **ipv6** settings should simply **try and disable it (**its easy, take a look at the screenshot chili555 sent me a few posts above) 

Specificcally it seems that it is crucial to have three text files in the **HOME** folder each **NAMED** as

[B]net.ipv6.conf.all.disable_ipv6 = 1
[/B]
[B]net.ipv6.conf.default.disable_ipv6 = 1

[/B][B]net.ipv6.conf.lo.disable_ipv6 = 1

[/B]respectively and each containing the text

#disable ipv6

I am not sure at all why these are where they are and i think the text is just a commented line (or maybe not!). BUT i had huge troubles with my wireless and all i know is that after disabling ipv6 it worked as a charm. Then i deleted the above files because they were the only thing in my home folder other than my other neatly arranged folders and the wifi went **bananas** **again** taking as before a minute to open google.com . I restored the files from the recycled bin and it snapped back to working furiously fast again. I did that a few times to be sure, restarts and everything included. (dmesg had some crazy log entries in it, cfg80211 was disabling all my frequencies one by one when i deleted the files but anyway ask if you are interested i am happy that its over)

**So there you have it, IF you have tried everything as i did to get the wireless to work and finally got it to work with the wl driver (check that with lsmod | grep wl ), BUT the connection is slow to very slow, disable ipv6 or/and make sure that the above files exist.** 

Mine works incredibly well, before i manage to type the pass for login it is already connected to my network and working fast as it should be. 

**A symptom that would tell you that the above is what you **[B]need to do (ASSUMING always that you are using the wl driver) is to try the commands "sudo rmmod wl" and then "sudo modprobe wl" (dont type the quotes) to restart the driver. In my case doing that after startup would fix the slowness problem and i was searching for a permanent solution which turned out to be the above. So if restarting makes the wireless work well, go for ipv6.

[/B]There I did my duty, i hope someone gets help from this as i did from so many posts.

BTW **chili555** if you are following this please let us know what these files are and why on earth they are in the home folder!!

---

### Post by chili555 on 2013-01-30
> BTW chili555 if you are following this please let us know what these files are and [COLOR="Red"]why on earth they are in the home folder[/COLOR]!!Why indeed? I have never heard of the files in /home/user. I always thought they were additional lines in /etc/sysctl.conf. I also thought, as I've often suggested, that disabling it in Network Manager was quite enough.

I am beginning to suspect it's router related. Some have no problems at all with IPv6, some do. Some have no problems at all with 802.11N, some do. Some have no problems at all with AES, some do. I don't understand it all yet.

---

