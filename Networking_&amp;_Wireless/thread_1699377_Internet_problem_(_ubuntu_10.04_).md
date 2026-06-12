---
title: "Internet problem ( ubuntu 10.04 )?"
date: 2011-03-03
forum: Networking &amp; Wireless
---

### Post by sekaie on 2011-03-03
Hello everyone 
 
I'm kind of newbie with linux and i have a problem with the internet

the network icon is showing deffirent connections and not asingle one of them 
is working.
 and it says:
" disconnected you are now offline " 
the internet works just fine with the other people using windows so why it's just me? 
oh and the ping command says something about ( unknown host ) if you think this info might be useful for you.
 
i saw this thread while searchingbut i don't get what should i do and what exact command i'm suppose to write so help me please 
 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10140945](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10140945)
 
i'm so sorry . I know my english is pretty awful

---

### Post by drdos2006 on 2011-03-03
From the terminal, type :
ifconfig

Copy the result and paste back here.

regards

---

### Post by steaksauce on 2011-03-03
It seems to me like you need to right click the network manager icon in the top right-hand side of your screen (near the date and time) and select "enable networking" if it isn't selected already.

Then you need to run > ifconfig in your terminal, accessed by Applications > Accessories > Terminal

The user on the topic you found then ran > sudo ifconfig wlan0 up in the terminal. However, this might be different for you depending on how many network devices you have and which one you want to use to connect to your network. For example, my wireless on my laptop is eth1 and my ethernet port is eth0 so I would say > sudo ifconfig eth1 up if I'm not mistaken. I haven't tried those commands since I don't have the problem, but the should work.

and when you run a SUDO command, it will ask you for your password in the terminal. This is the password to your user account on your computer.

---

### Post by sekaie on 2011-03-03
I don't know if I understood you well,
but what I get when I tried the commands you told me is in the attachment.
 
Also I really want to understand why are we using these commands and why this problem happened in the first place becouse it was working just fine then suddenlly this problem appered?
 
thanks alot for the help

---

### Post by steaksauce on 2011-03-03
I have no clue why any problem occurs most of the time when it comes to GUIs and especially Linux, but the first command you fed into the terminal (sudo ifconfig wlan0 up) was the right one. Following the command, you enter your user password (which I assume you did since it didn't spit an incorrect password error at you). Judging from the thread that you found, the user ran the wlan0 up command and was able to connect. Are you trying to connect to a wired or wireless network?

---

### Post by drdos2006 on 2011-03-03
Your screenshot does not show an IPv4 IP address but IPv6 addresses.

This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?
From your server, type

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf
From your server, type
sudo  vi  /etc/sysctl.conf
Add the following lines.
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Write and Save with:  Esc(cape key)  :  w  !	Esc(cape key)  :  q  !

Reboot your server.
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by sekaie on 2011-03-04
I think It has something to do with the ipv6- ipv4 problem becouse when I restart the computer the connection to my wireless network was established for an instant and when I typed the ifconfig at that moment the ipv4 address was showing then the connection went offline again and the ifconfig was showing ipv6 this time 
when I typed the command cat as shown in drdos2006'replay the output is (5 zeroes )
 
so what to do now ? should I continue with the rest of commands or not ?

---

### Post by steaksauce on 2011-03-04
> **sekaie said:**
> I think It has something to do with the ipv6- ipv4 problem becouse when I restart the computer the connection to my wireless network was established for an instant and when I typed the ifconfig at that moment the ipv4 address was showing then the connection went offline again and the ifconfig was showing ipv6 this time 
when I typed the command cat as shown in drdos2006'replay the output is (5 zeroes )
 
so what to do now ? should I continue with the rest of commands or not ?

If it is the ipv4/6 problem, then I'd drop the rest of it and listen to drdos, I don't know much about that type of thing unfortunately.

I hope your problem gets fixed ;)

---

### Post by drdos2006 on 2011-03-04
From your server terminal, type

sudo vi /etc/sysctl.conf

Add the following lines at the bottom of the file.

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Write and Save with: Esc(cape key) : w ! 
Quit with Esc(cape key) : q !

Reboot your server.

regards

---

### Post by sekaie on 2011-03-05
Thanks alot for the help . 
 
I hope it gets fixed soon , I got sick using others' computers :)
 
>  
From your server terminal, type

sudo vi /etc/sysctl.conf

Add the following lines at the bottom of the file.

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

Write and Save with: Esc(cape key) : w ! 
Quit with Esc(cape key) : q !

Reboot your server.


 
I've tried the command in terminal and nothing happened 
if you mean the terminal server client then I have to say that I've never used it and have no idea of setting it up

---

### Post by drdos2006 on 2011-03-05
If that did not work then it may be that the network interface card ( NIC ) is not able to be seen by Ubuntu. If the NIC is on your motherboard, can you get another NIC and put the NIC in your PCI slot.

I have a late model ASUS motherboard with onboard NIC that Ubuntu does not talk to, so that is what I have done to get network and internet access.

regards

---

### Post by sekaie on 2011-03-06
Thanks alot drdos for your help but I can't get NIC 
 
Now that we know the reason behind the problem what other options do I have ?
 
I've tried several ways and commands spread in the internet and nothing worked..
 
About three weeks ago everything was working just fine and I loved my ubuntu alot  
but last week this problem appered and now I know the reason but cannot do anything about it.

---

### Post by steaksauce on 2011-03-09
> **sekaie said:**
> Thanks alot drdos for your help but I can't get NIC 
 
Now that we know the reason behind the problem what other options do I have ?
 
I've tried several ways and commands spread in the internet and nothing worked..
 
About three weeks ago everything was working just fine and I loved my ubuntu alot  
but last week this problem appered and now I know the reason but cannot do anything about it.

I disabled IPv6 through Firefox.
In the URL type about:config and type "IPv6" in the filter.
It'll only show one thing, and set its value to "TRUE"

I found that method and google and suggested it to someone else earlier today

---

### Post by sekaie on 2011-03-10
> **steaksauce said:**
> I disabled IPv6 through Firefox.
In the URL type about:config and type "IPv6" in the filter.
It'll only show one thing, and set its value to "TRUE"
 
I found that method and google and suggested it to someone else earlier today
 
I did that but the ifconfig still doesn't show the IPV4 address and the Internet didn't get back 
also I tried to work with fedora 12 instead but the same problem apperred and no IPV4 address in the ifconfig.
 
last year I tried fedora 12 for few days but everything was fine.

---

### Post by drdos2006 on 2011-03-10
Try this link, it might be of some help.

[http://ubuntuforums.org/showthread.php?t=1701133](http://ubuntuforums.org/showthread.php?t=1701133)

regards

---

