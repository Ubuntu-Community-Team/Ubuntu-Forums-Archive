---
title: "Network after hibernate doesn't work for kernel 2.6.27-12"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by Ocye on 2009-02-19
After kernel update to 2.6.27-12 this week, the network doesn't resume. I use a very simple configuration with onboard chip, wired, static ip address, and without NetworkManager. Prior the update all works fine.

sudo /etc/init.d/networking restart 

>     [15707.750666] tg3: eth1: No firmware running.
    [15719.111128] ADDRCONF(NETDEV_UP): eth1: link is not ready
    [15823.297239] tg3: tg3_abort_hw timed out for eth1, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff


Of course, I didn't change any configuration. If I reboot completely the network starts and works perfectly.

>     Feb 18 09:31:53 [ 10.168726] eth1: Tigon3 [partno(BCM95755) rev a002 PHY(5755)] (PCI Express) 10/100/1000Base-T Ethernet 00:22:64:ad:98:62
    Feb 18 09:31:53 [ 10.168729] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
    Feb 18 09:31:53 [ 10.168731] eth1: dma_rwctrl[76180000] dma_mask[64-bit]


/etc/network/interfaces

>     auto lo
    iface lo inet loopback

    auto eth1
    iface eth1 inet static
    address xxx.xxx.xxx.xxx
    netmask 255.255.255.0
    gateway xxx.xxx.xxx.xxx
    dns-nameservers xxx.xxx.xxx.xxx

/etc/resolv.conf

>     search xxxxxxxx
    nameserver xxx.xxx.xxx.xxx
    domain xxxxxxxx


I had to change and add some lines to /usr/lib/pm-utils/sleep.d/10NetworkManager (but that was working)
> case "$1" in
	hibernate|suspend)
#		suspend_nm
                /etc/init.d/networking stop
		;;
	thaw|resume)
#		resume_nm
                /etc/init.d/networking restart
		;;
	*) exit $NA
		;;
esac

Any idea?

---

### Post by superprash2003 on 2009-02-19
use the old kernel which worked :)_

---

### Post by Ocye on 2009-02-20
Thanks for pushing me :popcorn:
I'm glad you didn't recommend to use another OS or to buy a new PC. At the moment I switch it off. That works well.

But back to the topic: Does anyone has an idea what happens?

---

### Post by pukakk on 2009-03-02
> **Ocye said:**
> Thanks for pushing me :popcorn:
I'm glad you didn't recommend to use another OS or to buy a new PC. At the moment I switch it off. That works well.

But back to the topic: Does anyone has an idea what happens?

I have same question, but I think it is better to use old version kernel than finding perfect solution. There are so many hardware-supports and API, but not enough time to build perfect kernel. I guess this problem is some minor bug and will be corrected after a couple of months, not now. 

Therefore, it will be good for us to use older(but more stable) kernel. I am using 2.6.24.21 kernel long time, and it never has occurred a problem.

---

### Post by Ocye on 2009-03-03
> it will be good ... to use older(but more stable) kernelI don't agree. 
BTW, the bug is listed as #446028.

---

### Post by Ocye on 2009-03-03
Persist with 2.6.27-13

---

### Post by Ocye on 2009-03-05
The bug is related to the PCI layer ([http://lkml.org/lkml/2009/1/28/608](http://lkml.org/lkml/2009/1/28/608), [http://bugzilla.kernel.org/show_bug.cgi?id=12598](http://bugzilla.kernel.org/show_bug.cgi?id=12598)) and a patch ([http://marc.info/?l=linux-kernel&m=123365342301877&w=4](http://marc.info/?l=linux-kernel&m=123365342301877&w=4)) is available. 
I hope we will get it in the next kernel. ;)

---

