---
title: "no network connection after changing provider"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by i_karpas on 2012-01-26
pls help
I have a PC with WIN7 and Ubuntu10.04, using Grub, it is connected thru a modem+switch. There are 2 other PC connected thru the swich, all able to surf using Win and Ubuntu.=
The problem with this particular PC is that it doesn't recognize the connection (Network Manager (N-M) has a red !). The Win OS _did_ connect. 
I edited the /etc/network/interfaces file which is shown below by *adding the last 2 lines*
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
saved it, restarted, Nothing changed
I then did R-click on the N-M icon, it shows **Networking** and **Notifications** as checked
**Edit Connections --> Wired **edited by entering eth0 and then in the IPv4 tab I added the address,network and geteway + DNS server that showed up in the Win7 OS, checked available 4 all users and 4 Method I tried both Manual and Automatic. Nothig worked 2 create connection
I also tried turning off/on the modem still nothing.
I ran ifconfig and it only shows this
 
karpas@karpas-desktop:~$ ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:122 errors:0 dropped:0 overruns:0 frame:0
TX packets:122 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:11850 (11.8 KB) TX bytes:11850 (11.8 KB)
 
also looked at dhcp3.conf but except for the first 2 lines all have # and I don't know what 2 do with it.
Any help will be appreciated since the internet supplier does not support Linux
 
i_karpas:confused:

---

### Post by chili555 on 2012-01-26
If you don't have an eth0 interface in ifconfig, then it will do no good to fiddle with /etc/network/interfaces or tweak Network Manager. Let's find out where eth0 has gone. Let's find out what kind of network card you have and find out what driver it needs and evidently isn't loading.

Please run and post:```
lspci -nn | grep 0200
uname -r
dmesg | grep eth0
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Network Manager will work best without the eth0 listings in /etc/network/interfaces. You may safely remove them. Leave the lo lines untouched.

---

### Post by i_karpas on 2012-01-27
Hi Chili555
I did as u indicated and  got                                                                                                                                                                                                
                                    karpas@karpas-desktop:~$ lspci -nn | grep  0200                                                                                                                                                        

    [LEFT]02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0) [/LEFT]
            [LEFT]karpas@karpas-desktop:~$ uname -r [/LEFT]
    [LEFT]2.6.32-33-generic [/LEFT]
        [LEFT]karpas@karpas-desktop:~$ dmesg | grep eth0[/LEFT]
    [LEFT] *returned nothing*[/LEFT]
        [LEFT]karpas@karpas-desktop:~$ sudo /etc/init.d/networking restart [/LEFT]
    [LEFT] * Reconfiguring network interfaces... 
[/LEFT]
   [LEFT]
  [/LEFT]
   [LEFT]the last command i did after editing /etc/network/interfaces and commenting (#)[/LEFT]
   [LEFT]the eth0 lines (auto ....  and iface .....)[/LEFT]
   [LEFT]There is still no connection
   Thank u
[/LEFT]

---

### Post by chili555 on 2012-01-27
The driver for this device is *atl1c*; it is built in to the latest Ubuntu version but must be compiled from source code on your older version. Here is a rough outline of the process, although there are some refinements we could add since the May 2010 postings. [http://ubuntuforums.org/showthread.php?t=1476231](http://ubuntuforums.org/showthread.php?t=1476231)

Perhaps you'd rather upgrade to Ubuntu 11.10. I'll be happy to help in either case.

---

### Post by i_karpas on 2012-01-27
Hi Chili555
I am going to reinstall the 10.04 version for which i have an image CD, since the connection worked before and i  hope it will again. I am saving all my files now. If this does not work i'll try what u recomended
I'll let u know how it turns out
      Thank u    i_karpas

---

### Post by i_karpas on 2012-01-30
Hi Chili555
I'm sorry 4 the delay in answering. My attemp 2 reinstall Ubuntu  10.04 didn't work in the process i lost Win7, and finally did a clean installation of Ubuntu  10.04  from the installation CD but that  did not return the network so i am going to install the modem driver as u instructed , I will keep u informed
  Thanks 4 the help
i_karpas

---

### Post by i_karpas on 2012-01-31
:DI looked up the url in u'r  thread from May 2010, but it is inactive (404 error).  So I downloaded the Ubuntu 11.10 distro, and after some effort got it installed now the Network works fine, and I am now in the process of getting used 2 it
Thank u again
   i_karpas:)

I want 2 mark this thread as SOLVED but I dont know how

---

### Post by chili555 on 2012-01-31
> **i_karpas said:**
> :DI looked up the url in u'r  thread from May 2010, but it is inactive (404 error).  So I downloaded the Ubuntu 11.10 distro, and after some effort got it installed now the Network works fine, and I am now in the process of getting used 2 it
Thank u again
   i_karpas:)

I want 2 mark this thread as SOLVED but I dont know howI'm glad it's working by whatever means. Use Thread Tools at the top to Mark Solved.

---

