---
title: "cannot connect to the internet on ubuntu 11.04 LTS"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by Wizard2829 on 2011-08-15
I have installed ubtuntu 11.04 from 10.04. Everything went fine i was  surfing the net without any issues. When i turned on my laptop today to  use ubuntu It won't let me connect it keeps saying check my internet  connection.  I didn't change nothing. I just updated the stuff in the  update manager and rebooted and laptop was fine. But now i can't get the  net to work on ubuntu. I know my net work cause i have windows 7  installed on my laptop to.

 I just uninstalled ubuntu and reinstalled it  thinking it would fix my issue but it didn't.   On ubuntu 10.04 lts the  wireless worked the first day then next day only wired connection  worked. I am not sure what to do or how to fix this issue its buging me  alot i love ubuntu as much as i love windows 7. I been surfing the net  for help on how to fix this but they don't seem to help. And i am still  new to ubuntu so step by step help will be good cause i just installed  ubuntu last friday. If you need need more information let me know.

I dual boot with 7 and ubuntu. I been searching for fixes but they seem to help or i don't know what to do since i'm new to ubuntu.

---

### Post by nm_geo on 2011-08-15
Welcome to the forums Wizard.

First are you able to connect the computer to an ethernet cable?

We need more information can you open a terminal?

Copy and paste the following in terminal then paste the results back in this thread.

```
lspci -nn | grep 0280
```That command gives us wireless chipset info.
```

sudo lshw -C network
```that one gives us more network info.

```
cat /etc/lsb-release; uname -a

```version and kernel info

---

### Post by Wizard2829 on 2011-08-15
Before i do that ill answer your question. When i first installed ubuntu 10.04 wireless worked but then next day it stoped. But eitthernet worked. Now either are working. On any verison from 10.04 and 11.04 lts. I know its not my net cause it works fine on windows 7. Witch i am using right now.

---

### Post by requeth on 2011-08-15
Connect with the ethernet cable.

If you try running

sudo ifconfig down eth0
sudo ifconfig up eth0

Are any errors given?

If no errors, if you run ifconfig and check eth0 does it show in the list? Does it have an IP? What is it?

Post answers to the above back. Also try going online after bring up the device, something may be stopping it from starting on boot.

Repeat the above steps for wireless by using wlan0 instead of eth0.

---

### Post by Wizard2829 on 2011-08-16
I tried all the steps that you guys gave me to try heres some of the log from some steps i did To run a command as administrator (user "root"), use "sudo <command>". 
See "man sudo_root" for details. 

laptop@ubuntu:~$ sudo ifconfig down etho 
[sudo] password for laptop: 
Sorry, try again. 
[sudo] password for laptop: 
etho: Unknown host 
ifconfig: `--help' gives usage information. 
laptop@ubuntu:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:33:ad:4d:39   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:240 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:240 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:19176 (19.1 KB)  TX bytes:19176 (19.1 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:24:d2:3e:bc:79   
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0 
          inet6 addr: fe80::224:d2ff:fe3e:bc79/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:467 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:65505 (65.5 KB)  TX bytes:21003 (21.0 KB) 

laptop@ubuntu:~$ sudo cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS" 
Linux ubuntu 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:09:46 UTC 2011 i686 GNU/Linux 
laptop@ubuntu:~$ s 
udos: command not found 
laptop@ubuntu:~$ sudo ifconfig down joes 
joes: Unknown host 
ifconfig: `--help' gives usage information. 
laptop@ubuntu:~$ help 
GNU bash, version 4.1.5(1)-release (i486-pc-linux-gnu) 
These shell commands are defined internally.  Type `help' to see this list. 
Type `help name' to find out more about the function `name'. 
Use `info bash' to find out more about the shell in general. 
Use `man -k' or `info' to find out more about commands not in this list. 

laptop@ubuntu:~$ sudo ifconfig down eth0 sudo ifconfig up eth0 
eth0: Unknown host 

 Its weird now when i got onto ubutunt two linksys names was listed so i created my own but that didnt help at all. I hope some of the log will help you guys out help me on this issue.

---

### Post by bkratz on 2011-08-16
I believe that the previous poster actually want the format ( not really sure it matters, but this how I have always seen it)


sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

### Post by Wizard2829 on 2011-08-16
Sorry i'm new to ubuntu what does format look like so i know what hes talking about.

---

### Post by bkratz on 2011-08-16
> **Wizard2829 said:**
> Sorry i'm new to ubuntu what does format look like so i know what hes talking about.

By format I was simply referring to the order of the command. You will note that in mine eth0 is before up or down. But like I said I don't really know that it makes a difference, only that it is the way I have always seen it.

---

### Post by Wizard2829 on 2011-08-16
Is there any thing else we can try to restore the net so i can surf on ubuntu? Eithernet or wireless still ain't working.

---

### Post by pdc on 2011-08-16
read post #2 

you were asked for the result of **THREE **commands

I think you have only supplied two ..

have a read at this post

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

wireless solving usually requires some data

try this diagnostic script

[http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Schnellstart/Quickstart.html](http://www.linux-tips-and-tricks.de/index.php/collectNWData.sh/collectNWData-Schnellstart/Quickstart.html)

download it; 

copy and paste the results back

---

### Post by Wizard2829 on 2011-08-16
When i got time ill go on ubuntu and get the results. Also got a question it is whats the difference between ubuntu cd copy vs dvd copy of 11.04 on ubuntu page?

---

