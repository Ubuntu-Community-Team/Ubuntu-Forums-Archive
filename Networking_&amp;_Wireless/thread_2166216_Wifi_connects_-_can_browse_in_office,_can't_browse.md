---
title: "Wifi connects - can browse in office, can't browse at home"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by moyeen2 on 2013-08-08
Hi,
I'm new to the group. My problem can be described as follows.
1. I use Ubuntu 12.04 LTS. I can connect to my home router but I can't browse. The wired connection doesn't work either.
2. I can connect and browse when I'm using my office wi-fi.
3. At home, If I switch to win7 , then I can browse using the same laptop. 

I tried to follow the post, didn't work : 
[http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2125952&highlight=11n_disable) (my router is set to g & b mode)
[http://ubuntuforums.org/showthread.php?t=1985079](http://ubuntuforums.org/showthread.php?t=1985079) (disable power saving mode)

4. I'm posting some basic info. like ifconfig , route -n. I'll try to post the detail specs of the comp and network later in the afternoon.
Looking forward to your suggestion,
Thanks in advance.

```

eth0      Link encap:Ethernet  HWaddr 00:23:5a:c4:ae:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eth2      Link encap:Ethernet  HWaddr 00:26:82:0a:f4:d7  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:82ff:fe0a:f4d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115211 errors:194 dropped:0 overruns:0 frame:2801617
          TX packets:98838 errors:166 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97864782 (97.8 MB)  TX bytes:19725569 (19.7 MB)
          Interrupt:18 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:104853 (104.8 KB)  TX bytes:104853 (104.8 KB)



```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth2
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth2
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth2

```

---

### Post by wildmanne39 on 2013-08-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by moyeen2 on 2013-08-08
Here is the file. 
Thanks

---

### Post by wildmanne39 on 2013-08-08
Let's try a few things, please make your wireless settings match the screenshots.

Go into your routers settings and change wep encryption to just wpa2 if you have that option.

Change the channel in your router to 1 or 11.

Change the security setting for wireless in network manager at the top right of your screen to wpa/wpa2.

You said that wireless works correctly at your office correct?

---

### Post by moyeen2 on 2013-08-09
1. I tried changing the channel to 11. Didn't help with browsing. ( I can connect to my wireless setup page using wireless)
2. my netgear doesn't have wpa2. it has wpa-psk. I tried that. Couldn't browse either. 
3. yes, when I go to office, I can browse. I'm attaching the script result for office, if it helps. Also, adding a screenshot for the wireless security options. I want to remind, I can't even browse using wired connection at home.

Thanks

---

### Post by wildmanne39 on 2013-08-09
Leave the encryption on wpa if that is the best option you have.

To change router settings you need to do it with an ehternet connection.

Did you change your wireless settings in network manager to match the screenshots I posted? Is so please run the script again and let's see if the changes took effect because I believe the dns server is an issue.
Thanks

---

### Post by moyeen2 on 2013-08-09
Yes. I changed the DNS address and it is reflected in the script result.

---

### Post by wildmanne39 on 2013-08-09
Please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo modprobe b43
```
watch for errors, if you are at home with no internet connection then:

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
instead of the second command.
Thanks

---

### Post by moyeen2 on 2013-08-09
I'm home now. So, I tried by downloading.
 I got the following error msg. 

```

moyeen@moyeen-PC:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
moyeen@moyeen-PC:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
moyeen@moyeen-PC:~$ sudo modprobe b43



```

---

### Post by wildmanne39 on 2013-08-09
Still will  not connect? Please post the file again and let's see if the new driver is loaded and how everything else looks with it.
Thanks

---

### Post by moyeen2 on 2013-08-10
Still, I can't browse ! Wondering if I should re-install ubuntu... I wanted to avoid that because I have to re-install a lot of stuff :(

---

### Post by steeldriver on 2013-08-10
Your resolv.conf

```

***** resolv.conf *****

nameserver 152.1.14.14
nameserver 152.1.14.69
search Belkin

```

doesn't seem to be consistent with the nm-tool output / NetworkManager.conf 

```

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

[B]    DNS:             8.8.8.8
    DNS:             8.8.4.4
[/B]
```

```

[main]
plugins=ifupdown,keyfile
[B]dns=dnsmasq
[/B]
```

in other words it looks like something is stomping on your dnsmasq / google DNS and putting a fixed /etc/resolv.conf file in its place containing the 152.14.x.x DNS servers (NCSU?)

If that's not something that you set up or intended (maybe it's required for your office/school network?), then you might want to run

```

sudo dpkg-reconfigure resolvconf

```

and then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question and  'No' to the one about temporarily appending your existing config to the  dynamic one, then reboot - but Wild Man knows more about this stuff than me, so you might want to wait for him to post back before doing anything.

---

### Post by moyeen2 on 2013-08-10
Thanks a lot [COLOR=#000000]steeldriver. It worked. Since I'm new in Linux/Ubuntu world, I have no clue how the settings got messed up ! Anyways, now, I need to take it to office and make sure it keeps working there :)

Thanks to both of you for the support.
-Moyeen[/COLOR]

---

### Post by wildmanne39 on 2013-08-10
That is what I thought as well, but right when I was going to have you change it these errors popped up with the wl driver.
> ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  396.826112] ERROR @wl_cfg80211_get_station : Could not get rate (-1)so I wanted to take care of that first.
Thanks steeldriver.

---

### Post by The Cog on 2013-08-10
I don't think it's that the wireless can't connect. I see that eth2 has been given an IP address, and it has a good-looking default gateway. So I wonder if dns is the problem.
Please try these commands and post the output:
```
ping -c 3 192.168.0.1
ping -c 3 91.189.94.12
ping -c 3 ubuntuforums.org
dig ubuntuforums.org
```
I am guessing that ping by IP will work but ping by name will not.

---

### Post by moyeen2 on 2013-08-10
@[COLOR=#000000]The Cog : Right now, I can ping both by name and ip. I have no problem browsing in home. I only need to check what happens when I take it to office on Monday.
Thanks [/COLOR]

---

### Post by The Cog on 2013-08-10
Ah, I thought it was at home you had trouble. You may find that you need to use a proxy at work. If the proxy requires windows account authentication before it lets you through, then I think you are probably out of luck.

---

