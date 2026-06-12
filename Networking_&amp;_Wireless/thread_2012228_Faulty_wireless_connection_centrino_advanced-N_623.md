---
title: "Faulty wireless connection centrino advanced-N 6230"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by emagar on 2012-06-28
I am somewhat new to Linux. Installed 64bit ubuntu 12.04 on a Dell XPS 13 i5core. [This other thread]("http://ubuntuforums.org/showthread.php?t=1728869") deals with a related issue on 10.04, I'm nervous about following that advice for 12.04.

Machine has no problem connecting to my home wifi router, but the network connection freezes shortly afterwards for long periods. Rebooting the machine solves the problem temporarily only. 

Based on other threads, this info should come handy:

```
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 88:53:2e:f0:90:74
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-26-generic firmware=18.168.6.1 ip=192.168.15.129 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f0500000-f0501fff
--------
sudo ifconfig -a 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:139966 (139.9 KB)  TX bytes:139966 (139.9 KB)

wlan0     Link encap:Ethernet  HWaddr 88:53:2e:f0:90:74  
          inet addr:192.168.15.129  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::8a53:2eff:fef0:9074/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27144683 (27.1 MB)  TX bytes:1902828 (1.9 MB)
---------
lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"AXTEL-f360"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 5C:D9:98:FD:F3:60   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:50  Invalid misc:582   Missed beacon:0
----------
wlan0     Scan completed :
          Cell 01 - Address: 5C:D9:98:FD:F3:60
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"AXTEL-f360"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000018b790415e
                    Extra: Last beacon: 136ms ago
                    IE: Unknown: 000A415854454C2D66333630
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406050700000000000000000000000000000000000000
-----------

``` 

Thank you in advance for your help.

---

### Post by wildmanne39 on 2012-06-28
Hi, please do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit,close.
Then:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi

```
Reboot
Thanks

---

### Post by emagar on 2012-06-28
Thanks Wildemanne!
Code appears to work. Will keep an eye on wifi performance and report in a while. 
Cheers mate.

---

### Post by wildmanne39 on 2012-06-28
Hi, if it works please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by emagar on 2012-06-28
Wifi appears to be running smoothly, thanks to Wildemann. 
For my linux culture, was the problem related to some power-saving mode?

---

### Post by wildmanne39 on 2012-06-28
Hi, part of it was a power saving issue, also that driver has issues with hardware encryption so we switched it to software encryption with the second set of commands.
Thanks

---

### Post by emagar on 2012-07-10
I've been using the machine for over a week and [[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533")'s solution still works wonders. Cheers!:guitar:

---

### Post by TheGrave on 2012-07-15
> **emagar said:**
> I've been using the machine for over a week and [[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533")'s solution still works wonders. Cheers!:guitar:
Do you manage to connect to a speed above 54Mbps? Seems I have to forget about N mode until they fix driver.

Connection is very unstable for me with the solution provided above - reconnecting every few minutes or so.

---

### Post by emagar on 2012-07-19
> **TheGrave said:**
> Do you manage to connect to a speed above 54Mbps? Seems I have to forget about N mode until they fix driver.

Connection is very unstable for me with the solution provided above - reconnecting every few minutes or so.

Signal level is never at max, even with computer facing the internet router. But my connection is stable. Don't know how to to check speed of my connection, please advice.

---

### Post by TheGrave on 2012-07-19
> **emagar said:**
> Signal level is never at max, even with computer facing the internet router. But my connection is stable. Don't know how to to check speed of my connection, please advice.

sudo iwlist wlan0 rate

It got stable with me as well. Upgrading from 11.04 to 12.04 fixed one issue for me and created 10 000 other ones. This release is FULL of bugs, I can't believe they decided to go with it at this stage, I'd call it a beta best case. Seems like the 6-month development cycle of Ubuntu is too much weight for the developers to carry.

---

### Post by emagar on 2012-07-19
> **TheGrave said:**
> Do you manage to connect to a speed above 54Mbps? Seems I have to forget about N mode until they fix driver.

```
$ sudo iwlist wlan0 rate
wlan0     unknown bit-rate information.
          Current Bit Rate:54 Mb/s

```

I'm also stuck at same speed. Has anyone managed to improve this?

---

### Post by TheGrave on 2013-02-07
I have to say I'm noticing some improvement under the following kernels: 3.7.0-030700-generic and 3.5.0-23-generic. Speed almost stable at 130-144Mbps, never falls to 1Mbps as it used to staying stuck like that forever.

---

### Post by tsbertalan on 2013-02-25
So, will this fix reduce battery life? It's already short enough in the xps 13.

---

### Post by tsbertalan on 2013-02-26
The fix appears not to be working for me (XPS 13; Ubuntu 12.04). :( I tried inserting a

date > /tmp/outfile

line in the /etc/pm/... script just to confirm that it's running, and it is.

Any other ideas here? Is there some more direct way that I can check that I applied the fix correctly?

uname -rv gives 3.2.0-38-generic #61+kamal14~DellXPS-Ubuntu

---

### Post by pQNmyG4 on 2013-09-05
Dear Wild Man,
I followed your abovementioned  instructions, und unfortunatelly I have gotten a completely opposite result, my wireless has completely disappeared, I mean in the metwork settings there is now only wired connection present. iwconfig doent even show that I have a wireless adaptor:
:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

Could please give any advice on how to get the wireless? I have just installed ubuntu 12.04 on dell xps 13 and had initially the same problem as was posted in this thread.

Thank you in advance!

---

### Post by wildmanne39 on 2013-09-05
Please tell us exactly what you did and copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by pQNmyG4 on 2013-09-05
Dear Wild Man, please here I posted the full description of my problem and what I have done:
[http://ubuntuforums.org/showthread.php?t=2172609](http://ubuntuforums.org/showthread.php?t=2172609)
the result of wireless_script I will post in couple of minutes.
Thank you for responding!

---

### Post by pQNmyG4 on 2013-09-05
here is the wireless_info:
[ATTACH]246046[/ATTACH]

---

### Post by captainrewind on 2014-03-25
I can attest that this is working for Dell XPS L502X, with Centrino Wireless-N 1000 and Ubuntu 12.04.

THANKS FOR THE HELP!!!

---

