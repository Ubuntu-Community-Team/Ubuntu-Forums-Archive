---
title: "Losing connection sometimes!"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by R3cKL3SS_aM on 2011-06-24
Sometimes the connection works perfect no problems and runs for a good solid day and other times it just drops out on me after 5-20mins of use.

I have no connecting problems when I restart my computer, but sometimes it just quits out on me while browsing the internet then I have to restart my computer to reconnect to the internet unless I were to plugin directly hardwire. The only program i am typically running that has to do with the internet other than my browser is Pidgin chat client, would that have anything to do with it crashing or dropping the signal? Not sure why this is happening but, if anyone has any solutions that would be great! 

I am running a dual boot, Ubuntu 11.04 along side Windows 7 and I never have my wireless connection drop while using windows.

Thanks for the help.

---

### Post by doas777 on 2011-06-24
right after it dies, make note of the exact time, and check your log file viewer. look at kernel, messages, syslog, and dmesg to see if there are any messages regarding the failure. post any you find.

when it fails, run these commands and save their output to post back:
```

sudo iwconfig
sudo ifconfig -a
nslookup ubuntuforums.org
route
cat /etc/network/interfaces
cat /etc/resolv.conf

```

that will give us a pretty good look at the state of your network stack.

---

