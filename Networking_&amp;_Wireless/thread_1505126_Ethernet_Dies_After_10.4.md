---
title: "Ethernet Dies After 10.4"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by Dagonus on 2010-06-08
So I upgraded to 10.4 last night on my laptop. 

I had a couple minor things to adjust. Afterwards I closed the lid on teh laptop expecting the system to hibernate normally. 30 minutes later, I opened the lid because I could still hear the hdd spinning like mad. Screen was black but still backlit.No response from the system in regard to keyboard or mouse so I did what anyone might, held the button and forced power off figuring I'd deal with the hibernate issue today. 

Booted the system today and found the system is not recognizing the ethernet connection. Cable works fine for other systems and all other systems see the internet correctly. 

Laptop is an Acer Aspire 5050 which has a realtek ethernet controller.I had seen some reports about solving similar problems with a davicom controller from a few years ago where tulip and other controllers loaded, but I'm not seeing a problem within lsmod, but I might be wrong. lspci is showing the Realtek controller. 


Thoughts on solving it? What other information do you need?

---

### Post by Dagonus on 2010-06-08
It seems to have resolved after running ifconfig  and then leaving it there while I ate dinner. I don't know if it's just connecting slowly or if ifconfig had anything to do with it.

---

### Post by Dagonus on 2010-06-09
No. It seems that ifcongig has nothing to do with it. Which, I suppose is good because I don't think that made sense. It was either something else I did while checking things or it just takes 30minutes for the network to turn on, which is pretty bogus (Probably enough for me to reinstall 9.10...)

How do I speed that up?

---

### Post by MedianMajik on 2010-06-09
Please post the output of ```
ifconfig -a
```

Trying running ```
dmesg
``` to see what your pc is outputting for those thirty minutes.  Are you running DHCP for your wired ethernet (I'm assuming so)?  Trying running these commands

dhcpcd
dhcpcd eth0
dhcpcd --release

---

### Post by DavorC on 2010-06-09
The exact same thing happened to me on my desktop the first (and only) time I tried to hibernate: the screen was black but the system never shut down so I had to manually reboot it. Since then, my eth0 interface is shown disabled in lshw output, and Network Manager thinks it's unmanaged. I can bring it up manually by adding it to /etc/interfaces, but would like to get it back via NM so that it's integrated with the rest of the system.

---

### Post by DavorC on 2010-06-09
Apparently, the problem is that the Network Manager marks network interfaces disabled during the hibernate, and re-enables them on suspend. When hibernate fails and the user has to reboot, the second step never executes, and the interfaces remain disabled, as far as NM is concerned.

See [http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html](http://osdir.com/ml/debian-bugs-dist/2010-01/msg07864.html) (or LaunchPad bug #524565) for a fix (which worked for me): 
```

 service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start

```

---

### Post by DarkRage4 on 2010-06-09
I wouldn't re-install 9.10. If you're going to re-install try re-installing a fresh installation of 10.04, errors can happen when upgrading, compared to a fresh installation.

---

### Post by Dagonus on 2010-06-09
I'm typing this in by hand since I can't just paste it from teh term. Fingers cross, no major foulups. 
ifconfig -a
```
eth0 Link encap: Ethernet HWaddr 00:1b:24:32:a3:1e
BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base Address:0xa000

lo Link encap: Local Loopback
inet addr:127.0.0.1. Mask:255.0.0.0
inet6 addr: ::1?128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:960 (960.0 B) TX bytes:960 (960.0 B)
```

dmesg is enormous and being that I'm typing it from one system to the other(naturally I can't find a jump drive) is there a line or 10 in particular we're looking for?

Maybe?
```
[         0.659534] eth0: RealTek RTL8139 at 0Xa000,00:1b:24:32:a3:1e, IRQ 20
```If you need them all I'll find or beg/borrow a jump drive (Minutes later finding one of mine)

dhcpcd is not currently installed, though I am using dhcp and was fine until this happened. I'm a bit perplexed. 

however, I think DavorC may have hit it. I ran sudo lshw -C network and my wireless comes up unclaimed and the Ethernet interface comes up disabled. 

However when i try to run the commands in that article, I get no where. Maybe I'm misunderstanding them. Starting and stopping the network manager didn't get me anywhere. The folder couldn't be rm because it doesn't exist. and the other one tells me that dbus_send command doesn't exist. So the two solutions in that article don't re-enable the network.  Though, maybe I'm just not doing it right. 




Lastly, Dark, you probably are right. This particular install is probably more than a bit dirty, I think it's it's 2nd upgrade. may even be third, but I'm pretty sure 2nd. Next time will be clean. I'd prefer to get it to next time though rather than clean install before then in any case.


Thanks for the help so far.

---

### Post by Dagonus on 2010-06-10
I've seen some people say they can manually start it as well. I cna't for the life of me figure out how to do that. They say they right click on it and go to activate and it's good to go. Where are they right clicking? I right click on what I think they're talking about and there's no activate. So I'm obviously in the wrong boat or it thinks that it's active when it isn't.  I still can't get that bit of code to work either. I type it in the terminal and it either gets rejected or nothing happens.

---

### Post by Dagonus on 2010-06-10
Ok. I think I got it. I found that *.state file and just edited it to true. Now the real problem appears. How to get my system to hibernate properly since I tried to hibernate again last night, hoping that if I hibernated and successfully that it would open up on the way out. Failed the hibernate again. But that's a problem for another thread. 

Thanks again to everyone.

---

