---
title: "Want to use USB tape converter but no /dev/video0"
date: 2011-07-07
forum: Multimedia Software
---

### Post by hydrox24 on 2011-07-07
Ok, So I have searched the great internetz high and low and cannot find a solution to this issue.
Ihave a 'Gadget Geek VHS to DVD maker' USB device that takes analogue video in (composite) and plugs into the computer via USB.
Here is the output of lsuss (it's the eMPIA one):

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID eb1a:2863 eMPIA Technology, Inc. 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 07ca:a815 AVerMedia Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Now this is essentially as far as I get, DBUS just says the following when I plug it in:

```
[ 5009.390267] usb 2-2.4: new high speed USB device using ehci_hcd and address 7
[ 5009.500477] usb 2-2.4: configuration #1 chosen from 1 choice

```

What I want to be able to do is open the (theoretical) output stream it produces in vlc and record it from there. Then I run into my next issue. There is no video* folder or link or file in my /dev directory and I can't stream video directly from the appropriate 'special file' inside /dev/bus/usb/00*/00*

Notes:
[LIST]
[*]My machine is ubuntu 10.4 64-bit
[/LIST]

Thanks for all the help, I am happy to do some more detective work if you can just point me in the right direction with some helpful tools or installations. I will update this post (or post a reply) if I get any closer to a solution.

Thanks a ton in advance :)

---

### Post by prshah on 2011-07-07
> **hydrox24 said:**
> 
Bus 002 Device 006: ID eb1a:2863 eMPIA Technology, Inc. 


Try loading the device driver manually, then check the dmesg log ```
sudo modprobe em28xx
sleep 5 && dmesg|tail
```

You should now have a video device (usually /dev/video0) created.

Please post back with results.

---

### Post by hydrox24 on 2011-08-14
I'm sorry that it took me so long to get back to this thread, for some reason it didn't alert me to your answer by e-mail..
Anyway, The modprobe command worked successfully and here is the dmesg output from running your two commands:
```

[   27.910772]   domain 1: span 0-3 level MC
[   27.910773]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[   27.910777] CPU3 attaching sched-domain:
[   27.910778]  domain 0: span 2-3 level SIBLING
[   27.910780]   groups: 3 (cpu_power = 589) 2 (cpu_power = 589)
[   27.910783]   domain 1: span 0-3 level MC
[   27.910785]    groups: 2-3 (cpu_power = 1178) 0-1 (cpu_power = 1178)
[   31.230089] eth1: no IPv6 routers present
[  163.689421] usbcore: registered new interface driver em28xx
[  163.689427] em28xx driver loaded

```

So I opened up /dev/video0 with VLC using the 'capture device' option in the file menu and it opened up my laptops webcam, which is alright, but I thought that you should know :)
Thanks for helping me with this and I am sorry it took me so long to get back to you.

---

### Post by hydrox24 on 2011-09-29
I know this is a long shot at this stage... but BUMP?

---

