---
title: "Can't get home networking going"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by mamboze on 2011-06-13
Hi,

I'm attempting to get a home network setup with a laptop and desktop, both running 10.04.  I followed the procedure set out in 
[http://ubuntuforums.org/showthread.php?t=1476875](http://ubuntuforums.org/showthread.php?t=1476875)   post 7
I've installed ssh server and client on each of the two computers and filled in the Places>Connect to Server dialog box with info for the other computer. 

But when I hit the connect button, there is a delay and then this message

"Cannot display location "sftp://roy@192.168.1.5//" " on one machine and "....."sftp://roy@192.168.1.4//" " on the other.

What to do? Any help much welcomed.

---

### Post by doas777 on 2011-06-13
while logged in as roy, try opening nautilus. hit Ctrl + L to put the address bar in location mode, and enter:
```
ssh://192.168.1.5
``` (note, drop the final slash from your addresses. is not right.) 

does this work correctly?

if not, open a terminal, and from 192.168.1.5, run this command:
```
ssh 192.168.1.4
```
can you login? do you recieve an error, and if so what is it?

---

### Post by mamboze on 2011-06-13
With nautilus, got the error message   

Could not display "sftp://192.168.1.4/"
Error: ssh program unexpectedly exited

192.168.1.4 being the IP address of the other machine.

in the terminal,

ssh 192.168.1.5   returned

ssh: connect to host 192.168.1.4 port 22: Connection timed out

---

### Post by doas777 on 2011-06-13
ok, lets make sure ssh is running. run this and post back the output:
```
netstat -ntlup
```

---

### Post by mamboze on 2011-06-13
~$ netstat -ntlup
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 0.0.0.0:46115           0.0.0.0:*

---

### Post by doas777 on 2011-06-13
ok looks like ssh is running. 
do you have UFW/GUFW configured to block ports?
you can check with this command:
```
sudo ufw status
```

---

### Post by mamboze on 2011-06-13
~$ sudo ufw status
[sudo] password for roy: 
Status: active

---

### Post by doas777 on 2011-06-13
ok, looks like ufw is blocking connections. try running this command on both boxes. it will allow hosts on your local lan (192.168.1.XXX) to connect to SSH:
```
sudo ufw allow from 192.168.1.0/24 to any port 22
```

then try connecting through nautilus again, and see if its working.

---

### Post by mamboze on 2011-06-13
OK, it's working going from the 192.168.1.4 box, but not from the 192.168.1.5 box, going this way give a 
Could not display "sftp://192.168.1.4/" message

Actually, I made a mistake by typing in ssh://192.168.1.5 on the 192.168.1.5 box 

but ssh://192.168.1.4 gave the error message

---

### Post by doas777 on 2011-06-13
from the .4 box, run the netstat command and make sure you have a listener on port 22. then run sudo ufw status again and confirm that it allows port 22 traffic. post back the output if both appear to be true.

---

### Post by mamboze on 2011-06-14
Sorry for the delay in replying, work and sleep intervened.

Here are the requested outputs:

~$ netstat -ntlup
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:56929           0.0.0.0:*               LISTEN      3057/skype      
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -               
tcp6       0      0 :::80                   :::*                    LISTEN      -               
tcp6       0      0 :::22                   :::*                    LISTEN      -               
tcp6       0      0 ::1:631                 :::*                    LISTEN      -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:68              0.0.0.0:*                           -               
udp        0      0 0.0.0.0:56929           0.0.0.0:*                           3057/skype      
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           -               
udp        0      0 127.0.0.1:56302         0.0.0.0:*                           3057/skype      
udp        0      0 0.0.0.0:49191           0.0.0.0:*                           -               

~$ sudo ufw allow from 192.168.1.0/24 to any port 22
[sudo] password for roy: 
Skipping adding existing rule

tcp6       0      0 :::22                   :::*                    LISTEN      -
To my limited understanding the above line in the netstat output indicates port 22 is being listened to, right?


Thanks for your help

---

### Post by doas777 on 2011-06-15
> **mamboze said:**
> 

tcp6       0      0 :::22                   :::*                    LISTEN      -
To my limited understanding the above line in the netstat output indicates port 22 is being listened to, right?


Thanks for your help

your right, that is the IPv6 listener, but in this case we are interested in this one (the IPv4 listener):
```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -               
```

well, it seems like everything should work, so I think the problem is elsewhere.

from .5, are you able to connect to ssh over the commandline? open a terminal and enter:
```
ssh 192.168.1.5
```?

---

### Post by mamboze on 2011-06-15
Hi doas777

output from .5 for ssh 192.168.1.5

ssh 192.168.1.5
roy@192.168.1.5's password: 
Linux medea 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

2 packages can be updated.
0 updates are security updates.

Last login: Thu Jun 16 08:54:25 2011 from 192.168.1.5

I tried ssh 192.168.1.4 on .4 and got this output

ssh: connect to host 192.168.1.4 port 22: Connection timed out

This seems strange. I expected a similar output to .5

---

### Post by doas777 on 2011-06-16
> **mamboze said:**
> Hi doas777

output from .5 for ssh 192.168.1.5

ssh 192.168.1.5
roy@192.168.1.5's password: 
Linux medea 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

2 packages can be updated.
0 updates are security updates.

Last login: Thu Jun 16 08:54:25 2011 from 192.168.1.5

I tried ssh 192.168.1.4 on .4 and got this output

ssh: connect to host 192.168.1.4 port 22: Connection timed out

This seems strange. I expected a similar output to .5

why are you trying to login to the localhost?

from .4, connect to .5, and vice versa. 
connecting to localhost should work, but I'm at a loss as to why you would want to. 

from .4, what is teh output of:
```
sudo service ssh status
```?

if you run;
```
sudo service ssh restart
dmesg | tail
``` what is the output?

from .5, what is the ouput of:
```
telnet 192.168.1.4 22
```
?
if all is working correctly, you should see this:
```
Trying 192.168.1.4...
Connected to 192.168.1.4.
Escape character is '^]'.
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu6
```(hit ctrl + C to exit telnet. )
that will tell us from a client perspective whether 22 is accessible to .5

---

### Post by mamboze on 2011-06-16
about connecting to localhost, I was basically just exploring, as is obvious, I'm at the very beginning of a learning curve here. 

from .4

sudo service ssh status 
gives
ssh start/running, process 21169

sudo service ssh restart dmesg | tail
gives
restart: Env must be KEY=VALUE pairs

from .5

~$ telnet 192.168.1.4 22
Trying 192.168.1.4...
telnet: Unable to connect to remote host: Connection timed out

---

### Post by doas777 on 2011-06-17
ok, from the telnet command, your ssh service on .4 is either broken or is being blocked.

from .4, please run these commands again. they are seperate commands so enter the top one, press enter, and then enter the second one. that is what cause the "ENV: " error you saw.

```
sudo service ssh restart



dmesg | tail
```

also on .4, please post back the output of 
```
sudo ufw status
```

---

### Post by mamboze on 2011-06-17
these are the outputs requested

~> sudo service ssh restart
ssh start/running, process 3248
~> dmesg | tail
[ 1966.972129] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29285 DF PROTO=TCP SPT=34060 DPT=80 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 1968.974337] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29286 DF PROTO=TCP SPT=34061 DPT=8080 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2035.049435] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29391 DF PROTO=TCP SPT=34064 DPT=80 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2037.051674] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29392 DF PROTO=TCP SPT=34065 DPT=8080 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2103.128839] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29497 DF PROTO=TCP SPT=34068 DPT=80 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2105.131039] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29498 DF PROTO=TCP SPT=34069 DPT=8080 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2171.210152] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29597 DF PROTO=TCP SPT=34072 DPT=80 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2173.212394] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29598 DF PROTO=TCP SPT=34073 DPT=8080 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2239.289475] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29698 DF PROTO=TCP SPT=34076 DPT=80 WINDOW=20480 RES=0x00 SYN URGP=0 
[ 2241.291720] Inbound IN=eth0 OUT= MAC=00:01:80:3a:1b:d3:90:e6:ba:be:71:ce:08:00 SRC=192.168.1.1 DST=192.168.1.2 LEN=44 TOS=0x00 PREC=0x00 TTL=64 ID=29699 DF PROTO=TCP SPT=34077 DPT=8080 WINDOW=20480 RES=0x00 SYN URGP=0 
~> sudo ufw status
Status: inactive
~> 

This is curious!!  the output for ifconfig  on .4 is now:

~> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:80:3a:1b:d3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe3a:1bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7721 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8336908 (8.3 MB)  TX bytes:1495226 (1.4 MB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20872 (20.8 KB)  TX bytes:20872 (20.8 KB)

and for .5 

roy@medea:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:11:32:15:7f:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 4c:ed:de:f5:6f:56  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::4eed:deff:fef5:6f56/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3439 errors:0 dropped:0 overruns:0 frame:573
          TX packets:2665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3937028 (3.9 MB)  TX bytes:363313 (363.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3888 (3.8 KB)  TX bytes:3888 (3.8 KB)

Could these changes be due to my moving the Dlink network hub yesterday and moving the Ethernet connectors to different positions in the hub?

---

### Post by MondoTofu on 2011-06-17
Hello --
 just checked your ifconfig outputs.
Let's recap
This is curious!! the output for ifconfig on .4 is now:

~> ifconfig
eth0 Link encap:Ethernet HWaddr 00:01:80:3a:1b:d3 
inet addr:**192.168.1.2** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::201:80ff:fe3a:1bd3/64 Scope:Link
UP BROADCAST [COLOR="Green"]RUNNING[/COLOR] MULTICAST MTU:1500 Metric:1
...
...
and for .5 

roy@medea:~$ ifconfig
eth0 Link encap:Ethernet HWaddr e8:11:32:15:7f:9f 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:26 Base address:0x8000 

eth1 Link encap:Ethernet HWaddr 4c:ed:de:f5:6f:56 
inet addr:**192.168.1.8** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::4eed:deff:fef5:6f56/64 Scope:Link
UP BROADCAST [COLOR="green"]RUNNING[/COLOR] MULTICAST MTU:1500 Metric:1
....

Recapping, those two IP addresses are actually 

**192.168.1.2**
and
**192.168.1.8**

try connectivity with each other now with these commands.

From the ".4" box,  use ssh 192.168.1.8

and 
From the ".5" box, use ssh 192.168.1.2

I expect you'll be able to connect as roy between the two, but let us know how you get on.

---

### Post by mamboze on 2011-06-17
output from ".4" desktop

~> ssh 192.168.1.8
The authenticity of host '192.168.1.8 (192.168.1.8)' can't be established.   
RSA key fingerprint is dd:1c:71:2e:47:37:10:e7:77:57:58:68:3e:f8:89:31.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.8' (RSA) to the list of known hosts.
roy@192.168.1.8's password: 
Permission denied, please try again.
roy@192.168.1.8's password: 
Linux medea 2.6.32-31-generic #61-Ubuntu SMP Fri Apr 8 18:24:35 UTC 2011 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Last login: Thu Jun 16 10:53:01 2011 from 192.168.1.4


**NOTE: 192.168.1.8  in brackets gives a smilie >> (192.168.1.8)**

output from ".5" laptop

roy@medea:~$ ssh 192.168.1.2
ssh: connect to host 192.168.1.2 port 22: Connection timed out

Thank you

---

### Post by MondoTofu on 2011-06-18
On both desktop and laptop, please try the following command:

 ps -ef | grep -i ssh  

I would expect something like this on medea,

```
root       796     1  0 Jun16 ?        00:00:00 /usr/sbin/sshd -D
root      6989   796  0 00:07 ?        00:00:00 sshd: medea [priv]   
medea      7063  6989  0 00:07 ?        00:00:00 sshd: medea@pts/0   

``` 
but there wouldn't be any lines with "sshd" on the desktop machine.

If there are no sshd lines then you will want to try to restart the service ( I wouldn't assume that the services are set to start automatically at boot-time ) if it was installed using previously given commands, else

you may need to run the following commands:

sudo apt-get remove openssh-server 
sudo apt-get install openssh-server

---

### Post by mamboze on 2011-06-18
output from desktop 

~> ps -ef | grep -i ssh 
roy       2351  2317  0 05:55 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
root      3248     1  0 06:29 ?        00:00:00 /usr/sbin/sshd -D
roy       6365  6340  0 13:20 pts/0    00:00:00 grep --color=auto -i ssh

the second line contains  sshd -D

so I should run the 2 openssh commands?

output from laptop

roy@medea:~$ ps -ef | grep -i ssh
root      1178     1  0 05:52 ?        00:00:00 /usr/sbin/sshd -D
roy       1818  1784  0 05:55 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session gnome-session
roy       3374  2469  0 13:22 pts/0    00:00:00 grep --color=auto -i ssh

Well, it seems the first line of the medea output is OK. And the ssh setup on the laptop is OK? But the ssh server needs to be reinstalled on the desktop, right?

---

### Post by mamboze on 2011-06-18
My many thanks to doas777 and MondoTofu for their help in trying to get a ssh network up and running on my two computer network. Despite their thorough efforts and my very limited contribution to solving this problem, the network is still not working fully. 

This situation is this. I have two computers, a desktop 192.168.1.2 and a laptop 192.168.1.8  The desktop is running 10.04 and the laptop 10.04.2.

I can connect from the desktop to the laptop but not from laptop to desktop, the connection times out. 

I have ufw disabled (inactive) on both machines. And I've reinstalled the ssh server on the desktop. But to no avail.

Any help would be most gratefully received. I'm at my wits end on this.

Perhaps an alternative to ssh might be advisable. Any suggestions? All I want to do is to network two computers, the methodology doesn't matter to me.

---

### Post by mamboze on 2011-06-18
Success!! The network is working

I found that I had firestarter running on the desktop machine. I thought that I had removed it when I installed ufw, but apparently not. Immediately, I uninstalled firestarter, the two machines could communicate. 
Many thanks to doas777 for your patient help in guiding me thru this troubleshooting (and, for me, educational) exercise, I'm most appreciative to you, and to MondoTofu too.
The Ubuntu forums are superb sources of support and information, IMO, unmatched by any other forums online.

Thanks guys. :D :D

---

### Post by doas777 on 2011-06-19
You're welcome. Glad you got it worked out!

Happy ubuntuing!

---

