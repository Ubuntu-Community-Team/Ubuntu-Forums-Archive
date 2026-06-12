---
title: "How to enable wired (ethernet cable) internet"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by doskyis on 2010-03-05
I installed ubuntu 9.10 on my laptop a few days ago and love the OS so far. However, initially i could only get internet connection though an ethernet cord. After much internet searching, i finally figured out how to get wireless internet. Unfortunately, in setting up wireless internet, I no longer have wired internet. The system doesn't seem to recognize my wired internet anymore. I'd like a scenario where i can connect to the internet both wired and wireless.

Any suggestions? 
PS. I am not very tech savvy, so you may have to dumb it down for me a little.

Thanks.

---

### Post by yoi on 2010-03-06
Hi there,

You can find the name of your wired interface name by

$ ifconfig

They are generally something like, eth0 or eth1, etc...  Once you got the name,
you can assign, using DHCP, an IP address to your wired network interface (say, eth0) as:
 
$ sudo dhclient eth0

However, I think it is not advisable to enable a wireless interface and a wired interface at the same time.  Make sure your wireless interface is down when using the wired interface.

---

### Post by doskyis on 2010-03-06
Thanks for your response. I didn't get any eth0 or eth1, just lo and wlan0. Do I need to install something?

---

### Post by yoi on 2010-03-06
You are welcome.

That case, your wired interface is not up.  Try invoking it by

$ sudo ifconfig eth0 up

The above is eth0 case, sometimes you should try eth1, eth2, etc.  To confirm your wired interface is already up, type

$ ifconfig

If can see an entry of your wired interface in the listing, try the dhclient command onto the interface again.

Please try it and let me know the results.  Good luck.

---

### Post by yoi on 2010-03-06
Also, to explicitly disable your "wireless" interface, try

$ sudo ifconfig wlan0 down

To bring it back again,

$ sudo ifconfig wlan0 up

---

### Post by doskyis on 2010-03-06
I tried #sudo ifconfig eth0 and nothing happened. I went all the way to eth4 and still no luck. I remember that when all i had was wired internet (before i was able to setup the wlan) the wired connection showed up as eth0. I am not sure if this is useful information, but to setup the wireless internet, i had to follow some steps online that involved ndiswrapper and ndisgtk. 

Thanks again for your help

---

### Post by chili555 on 2010-03-06
If eth0 doesn't appear in ifconfig, then a driver has not attached to your ethernet card to create an interface, usually eth0. Let's see what you have and see if we can get a driver to load. Please post:```
lspci -nn
```If you can recognize your wired ethernet card, you can skip all the data except that.

---

### Post by doskyis on 2010-03-06
Here's the output:
00:00.0 "0600" "8086" "2590" -r03 "1028" "01c9"
00:02.0 "0300" "8086" "2592" -r03 "1028" "01c9"
00:02.1 "0380" "8086" "2792" -r03 "1028" "01c9"
00:1b.0 "0403" "8086" "2668" -r03 "1028" "01c9"
00:1c.0 "0604" "8086" "2660" -r03 "" ""
00:1c.3 "0604" "8086" "2666" -r03 "" ""
00:1d.0 "0c03" "8086" "2658" -r03 "1028" "01c9"
00:1d.1 "0c03" "8086" "2659" -r03 "1028" "01c9"
00:1d.2 "0c03" "8086" "265a" -r03 "1028" "01c9"
00:1d.3 "0c03" "8086" "265b" -r03 "1028" "01c9"
00:1d.7 "0c03" "8086" "265c" -r03 -p20 "1028" "01c9"
00:1e.0 "0604" "8086" "2448" -rd3 -p01 "" ""
00:1f.0 "0601" "8086" "2641" -r03 "1028" "01c9"
00:1f.1 "0101" "8086" "266f" -r03 -p8a "1028" "01c9"
02:00.0 "0200" "14e4" "170c" -r02 "1028" "01c9"
02:03.0 "0280" "14e4" "4318" -r02 "1028" "0005"
thanks

---

### Post by chili555 on 2010-03-06
Here is your Broadcom ethernet device:> 02:00.0 "0200" "14e4" "170c"It uses the modules *b44* and *ssb.* Please do:```
sudo modprobe b44 ssb
ifconfig
```Do you now have an ethernet interface? If so, we will need to amend one file to get the driver to load automagically on boot. If not, please post:```
dmesg | grep b44
```Thanks.

---

### Post by doskyis on 2010-03-06
Here's what i got from the first post: $ sudo modprobe b44 ssb
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting b44 (/lib/modules/2.6.31-20-generic/updates/cw/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I then entered the grep thing and got this: $ dmesg | grep b44
[39307.223842] b44: Unknown parameter `ssb'
[39357.029881] b44: Unknown parameter `ssb'

I still don't have a wired connection.

Thanks for all your help. I really appreciate it

---

### Post by doskyis on 2010-03-06
This info might help as well. The thing is that I don't even have the option to select a wired connection on my network-manager anymore. I lost that as soon as i set up the wireless. Maybe if there was some way of bringing back that wired connection option on networkManger the problem would be fixed.
What do you think?

---

### Post by chili555 on 2010-03-06
Let me guess: you got your Broadcom wireless going with ndiswrapper and had to blacklist a few things (ssb, maybe?) and modify a few things? And now, since ssb is used in both b44 and the native wireless driver b43, your system can't find and load ssb and b44 won't grab your ethernet card and I need a tranquilizer? Is that it?> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.What happens if you simply try to add ssb?```
sudo modprobe ssb
```Does it error out?

Network Manager is not going to show a wired option until the driver and the card attach. Until then, NM doesn't even see an ethernet interface to use; like you physically removed the card.

If you want both wired and wireless both to work, we have some surgery to do. May I please see:```
cat /etc/modprobe.d/ndiswrapper
cat /etc/modprobe.d/blacklist
```Roll up your sleeves, please.

---

### Post by doskyis on 2010-03-06
I honestly don't know exactly what i did to get the wireless working. I simply followed step by step code from a website. You're probably right about what ended up happening though. Here's results from what you asked me to code:
sudo modprobe ssb
[sudo] password for aibangbee: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
aibangbee@aibangbee-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper
aibangbee@aibangbee-laptop:~$ cat /etc/modprobe.d/blacklist
blacklist bcm43xx
blacklist bcm43xx
blacklist bcm43xx
blacklist wl
blacklist bcm43xx
blacklist wl

---

### Post by chili555 on 2010-03-06
> /lib/modules/2.6.31-20-generic/[COLOR="Red"]updates/cw[/COLOR]/b44.koI notice your b44 comes from backports. It may be broken. Let's try:```
sudo apt-get remove linux-backports-modules-*
```Afterwards, reboot.

Does your wired ethernet work now?```
ifconfig
```After we get your ethernet going, let's do some housecleaning in your /etc files.

---

### Post by doskyis on 2010-03-06
Still no ethernet. Here's the output of the ifconfig:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:226 errors:0 dropped:0 overruns:0 frame:0
          TX packets:226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23667 (23.6 KB)  TX bytes:23667 (23.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:3b:31:ef  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe3b:31ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:457235 (457.2 KB)  TX bytes:143159 (143.1 KB)
          Interrupt:17 Memory:dfbfe000-dfc00000 

It says "Link encap:Ethernet" for wlan0, but what does that mean?

---

### Post by chili555 on 2010-03-06
Do you still get an error when you:```
sudo modprobe b44
```

---

### Post by doskyis on 2010-03-06
Here's what i got
$ sudo modprobe b44
[sudo] password for aibangbee: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

---

### Post by chili555 on 2010-03-06
No error. Now do you have an ethernet interface? ```
ifconfig
```May I also see :```
cat /etc/rc.local
```Thanks.

---

### Post by doskyis on 2010-03-06
I now have an ethernet interface. I'm going run upstairs and hook it up to see it if actually works.

Thanks.

---

### Post by doskyis on 2010-03-06
You're not gonna believe this. I ran ifconfig downstairs in my house and got eth0, so I shutdown my laptop, rebooted it upstairs where i have the ethernet hookup and ran the ifconfig again, except this time it no longer shows eth0. I'm confused.
Here's what else i got:
$ cat /etc/rc.local
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

I'm just gonna stay up here so if it works again, i'll be right by the ethernet cord to test it.

Thanks

---

### Post by chili555 on 2010-03-06
Please do:```
sudo su
echo b44 >> /etc/modules
modprobe b44
exit
ifconfig
```Is it working now?

---

### Post by doskyis on 2010-03-06
It's working now!!! Thank you sooooo much. YOU ROCK!!!

Do we still need to do the cleanup you mentioned earlier?

---

### Post by chili555 on 2010-03-06
```
sudo gedit /etc/modprobe.d/blacklist
```Clean it up so it contains:```
blacklist bcm43xx
blacklist wl 
```Proofread, save and close gedit.```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```You should be all set. Enjoy.

---

### Post by doskyis on 2010-03-06
Thank you so much. Everything looks good! I am so grateful. Now I can sit back, relax and enjoy Ubuntu. :popcorn:

---

### Post by greymann on 2010-03-27
**doskyis** - thanks for asking the question (I had same exact problem)!

[SIZE=3]**chili555**[/SIZE] - you rock! Thanks for the clear dialog - you've helped another newbie!

---

