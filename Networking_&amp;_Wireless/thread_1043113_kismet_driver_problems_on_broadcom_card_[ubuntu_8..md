---
title: "kismet driver problems on broadcom card [ubuntu 8.04]"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by neverone on 2009-01-18
i managed to install kismet with make suidinstall by following the instrucions from here:
[http://wirelessdefence.org/Contents/Installingkismet.htm](http://wirelessdefence.org/Contents/Installingkismet.htm)

and now i'm having problems with drivers, and since i have broadcom card in my laptop, i read the kismet readme file ([http://www.kismetwireless.net/documentation.shtml#readme](http://www.kismetwireless.net/documentation.shtml#readme)), and it states there that there are three supported broadcom drivers: **bcm43xx, b43 and b43legacy,** and that one of them should be installed during the configuration of kismet package. so, what i did during the installation was:

```
neverone@n1_:~/kismet-2008-05-R1$ ./configure --enable-b43

```

and afterwards it was necessary to edit data in the kismet.conf file, which i did here (only the part about drivers source is pasted):

```
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=b43,eth0,broadcomSource
```

but when i tried to run it, i got error:
```
neverone@n1_:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to neverone (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'b43' in source 'b43,eth0,broadcomSource'
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
Waiting for server to start before starting UI...

```


i tried the same thing with the other driver - "b43legacy", and i got the same error. i tried to **change the eth0 interface into eth0, wlan0, and even into eth1**, and it didn't do anything. i still recieved the same error

but when i tried to install it with the driver "**bcm43xx**"then i got a different error:

```
neverone@n1_:~/kismet-2008-05-R1$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Will drop privs to neverone (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
FATAL: Support for capture source type 'bcm43xx' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```


during the decompiling and installation process i typed ./configure --help, and there it states that i should type it this way: ```
./configure --enable-FEATURE=yes
```
but there was absoultely no difference when i tried to run it :'(

... any ideas? please? i really need kismet up and running, and functional! i have a **broadcom BCM4312 802.11b/g (rev 01) card**, and i don't know what to do else to make it run

---

