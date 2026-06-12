---
title: "Toshiba Satilite P505-8980 and Atheros AR8132 on Ubuntu"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by RobFS1 on 2010-02-06
I was wondering if anyone could help me install an ethernet card. I have already asked this on General Help but I generally have not gotten any help yet...:( Please follow the link. Thank you. :KS

[http://ubuntuforums.org/showthread.php?t=1399601]("http://ubuntuforums.org/showthread.php?t=1399601")

---

### Post by chili555 on 2010-02-06
Please open Applications -> Accessories -> Terminal and do:```
sudo modprobe atl1c
```That's a bit confusing looking; in caps it would be: ATL1C. Now do:```
ifconfig
```Do you have an ethernet interface, eth0, perhaps? Can you connect?

---

### Post by RobFS1 on 2010-02-12
Sorry for the long wait on the reply, but thank you for your help.

When I type in 

```
sudo modprobe atl1c
```

terminal just outputs a blank:

```
user@hostname:~$
```

ifconfig:

```
lo      Link encap:Local Loopback
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436 Metric:1
        RX packets:4 errors:0 dropped:0 overruns:0 frame:0
        TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
```

note that I had to copy that from the other computer to here so tell me if anything is missing.

Thanks, hope there is something to be figured out. :)

---

### Post by chili555 on 2010-02-12
Please post:```
lspci -nn | grep Ethernet
sudo modprobe atl1c
dmesg | grep atl
```Thanks.

---

### Post by RobFS1 on 2010-02-15
```
username@hostcomputer:~$ lspci -nm | grep Ethernet
username@hostcomputer:~$ 

username@hostcomputer:~$ sudo modprobe atl1c
username@hostcomputer:~$ 

username@hostcomputer:~$ dmesg | grep atl
[    9.630408] atl1c 0000:07:00.0: enabling device (0000 -> 0002)
[    9.630417] atl1c 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.630432] atl1c 0000:07:00.0: setting latency timer to 64
[    9.630495] atl1c 0000:07:00.0: PME# disabled
[    9.630501] atl1c 0000:07:00.0: PME# disabled
[   10.120276] atl1c 0000:07:00.0: PCI INT A disabled
[   10.120315] atl1c: probe of 0000:07:00.0 failed with error -5
username@hostcomputer:~$ 


```

Hope this helps, thank you for your help

---

### Post by Sylslay on 2010-02-15
that divers:

sudo modprobe atl1c

doesn't work with your card,

and after ifocnig You have still
only:
127.0.0.1 ip addres for computer talking to itself :popcorn:

It works with backport in 9.04 and out of box in 9.10

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/415358](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/415358)

---

### Post by RobFS1 on 2010-02-18
So where do I go from here? I followed the link and made an account on Launchpad, but that didn't lead to anything apparent. Sorry for the n00bishness of the question, but yeah... sometimes...

---

### Post by jjbasken on 2010-03-05
You can try these steps, which worked for me on my Satellite P505:
- In grub, highlight the Ubuntu entry and press "e" to edit the boot options
- Find the text that says "quiet splash" and add "acpi=off" after the text
- Press control-x (I believe that is what it says to continue booting but I could be mistaken)
- Plug in the ethernet cable and hopefully it should work

I then ran update manager and updated everything and restarted and eth0 worked without adding acpi=off again.  

Thankfully I was also able to get the wireless working with a little bit of work also.

---

### Post by RobFS1 on 2010-03-06
That hasn't done the trick so far...

Maybe your P505 is a different model, or something. I still need help though if you can provide it.

---

### Post by George_SPatton on 2010-05-11
Rob.  This is your brother.  The bug suggests that on Ubuntu 9.10 works out of the box.  Have you reinstalled using Ubuntu 9.10?  What version are you trying?

---

### Post by RobFS1 on 2010-05-15
I have tried 9.10 and it did not work; but I tried 10.04, and the wired connection worked. The issue is that there is no wireless connection apparent (there is one, but it will not connect to anything, let alone show any available networks). I think what I will do as a solution is get a USB wireless card for the computer that is compatible with Linux.

---

### Post by Leijonberg on 2010-05-23
Hi guys,

I have a Toshiba T130 with an Atheros AR8132 wired ethernet card, and the exact same problem (dmesg | grep atl1c returns "failed with error -5").

I have tried with several distros (i.e. different kernels), among them Kubuntu 10.04 and Ubuntu 9.10. They all have the atl1c kernel module but still ifconfig -a is only showing the loopback interface.

Any hints? Are you working on a solution? Please keep us updated.

**EDIT>> **
My bad, I had tried Kubuntu 9.10, Ubuntu 9.04, Mint 8 & 9 and Arch 2010.05, but neither had working driver for AR8132, as previously stated in other topics. Ubuntu 10.04 froze on Live-CD boot, due to problems with wireless realtek rtl8187se driver. Temporary solution was to disable wireless. Hope this issue is resolved soon.
My wired atheros AR8132 is working fine in 10.04. Thanks a lot :)

---

