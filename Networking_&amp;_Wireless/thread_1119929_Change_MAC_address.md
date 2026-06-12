---
title: "Change MAC address"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by Radio Zaza on 2009-04-08
Dear all

i am a new user or ubuntu "hardy heron".
i want to spoof the mac address of my wireless card (intel 3945abg)
when using 
ifconfig wlan0 down
ifconfig wlan0 hw ether ....
ifconfig wlan0 up

the mac does change. however i am unable to connect to the wireless network. it just tries to connect and nothing happens.
when looking at connection information in nm-applet i can see that the mac address is changed. but all other ino is set to 0000

same issue when using macchanger.

is it a problem in nm-applet !

any help plzzzz

---

### Post by compiledkernel on 2009-04-08
You have the command structure correct. 

What does /var/log/messages and /var/log/syslog say when you try to use that connection?

---

### Post by lensman3 on 2009-04-08
I think this can only be done when the Ethernet driver is loaded.   You will have to use modprobe with flags set so that  you can change the number.   By the time an IP stack is installed it is too late.  These numbers are arp and run at a level just above the wire.

---

### Post by Radio Zaza on 2009-04-09
thanks for the fast reply compiledkernel and lensman3...

the output of the syslog file is:

Apr  9 15:55:11 stalin NetworkManager: <info>  Old device 'wlan0' activating, won't change.

Apr  9 15:55:18 stalin kernel: [  138.517820] wlan0: Initial auth_alg=0

Apr  9 15:55:18 stalin kernel: [  138.517831] wlan0: authenticate with AP 00:60:b3:22:e3:f0

Apr  9 15:55:18 stalin kernel: [  138.518815] wlan0: Initial auth_alg=0

Apr  9 15:55:18 stalin kernel: [  138.518823] wlan0: authenticate with AP 00:60:b3:22:e3:f0

Apr  9 15:55:18 stalin kernel: [  138.551611] wlan0: authenticate with AP 00:60:b3:22:e3:f0

Apr  9 15:55:19 stalin kernel: [  138.581264] wlan0: authenticate with AP 00:60:b3:22:e3:f0

Apr  9 15:55:19 stalin kernel: [  138.604959] wlan0: authentication with AP 00:60:b3:22:e3:f0 timed out

Apr  9 15:55:23 stalin NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
Apr  9 15:55:27 stalin NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation.

Apr  9 15:55:27 stalin NetworkManager: <info>  Activation (wlan0) failure scheduled... 

Apr  9 15:55:27 stalin NetworkManager: <info>  Activation (wlan0) failed for access point (ggg3) 

Apr  9 15:55:27 stalin NetworkManager: <info>  Activation (wlan0) failed. 

Apr  9 15:55:27 stalin NetworkManager: <info>  Deactivating device wlan0.



the output of the messages file is:


Apr  9 15:49:56 stalin kernel: [   39.505601] ADDRCONF(NETDEV_UP): eth0: link is not ready

Apr  9 15:49:56 stalin kernel: [   39.506896] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Apr  9 15:50:34 stalin kernel: [   59.549845] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Apr  9 15:51:21 stalin kernel: [   70.608399] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Apr  9 15:51:36 stalin kernel: [   74.195037] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Apr  9 15:51:36 stalin kernel: [   74.215038] ADDRCONF(NETDEV_UP): eth0: link is not ready

Apr  9 15:53:25 stalin dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

Apr  9 15:53:27 stalin kernel: [  106.448058] NET: Registered protocol family 17





i must say that under mandriva spring 2008 i can do the trick by
booting with network manager off (i dnt remember the name of their network manager !!) and wlan0 off or down.
after booting i use the same commands as above and connect with 
no problems.
in ubuntu i tried to boot without networkmanager and with wlan0 down. and did the same but without success...

lensman3 i didn't get the modprobe thing. is a command or a file you edit.
if it can be done plz post the methode.

thanks.

---

