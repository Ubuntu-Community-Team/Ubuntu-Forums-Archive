---
title: "Wake on Lan with e100 on 9.10 Server"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by MMistro on 2009-11-01
So I was trying to get wake on lan working on 9.10 server with my Sun LX50 which has two onboard Intel 82557/8/9/0/1 Ethernet Pro 100 ports. I'm using only the eth0 port.

I've gone through this thread, but to no avail: [http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)

I've managed to narrow the problem down to be something with the way ubuntu shuts down the machine. When I wait for grub to load and turn off the machine using the power at that stage, I can WOL just fine. However, once I shut down properly using "halt" or "shutdown -h", I cannot turn it on using WOL.

The Ethernet light is on, and it flickers on par with the sending of my WOL signals, so it does seem to have power after a proper shut down.

Here is the output of ethtool:
```

Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        **Supports Wake-on: g**
        **Wake-on: g**
        Current message level: 0x00000007 (7)
        Link detected: yes

```in the file in /etc/init.d/halt, I've taken out the -i from the halt command.

here is the contents of /proc/acpi/wakeup:
```

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S4     disabled  no-bus:pci0000:00
PS2K      S1     disabled  pnp:00:06
UAR1      S4     disabled  pnp:00:08
UAR2      S4     disabled  pnp:00:09
USB       S1     disabled  pci:0000:00:0f.2
PCI1      S4     disabled  no-bus:pci0000:01

```The NIC's don't seem to be listed... here is an output of lspci:
```

$lspci
00:00.0 Host bridge: Broadcom CNB20HE Host Bridge (rev 23)
00:00.1 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.2 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
00:00.3 Host bridge: Broadcom CNB20HE Host Bridge (rev 01)
[B]00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)[/B]
00:0c.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 ISA bridge: Broadcom CSB5 South Bridge (rev 92)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 92)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 Host bridge: Broadcom CSB5 LPC bridge
01:07.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
01:07.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)

```In the grub boot options, if i set acpi=off (by default there's no acpi setting), I can get the machine to "shut down", however this does not go into the same power state as a normal shut down. In fact, the only thing that seems to turn off is the hard drive. Everything else seems to remain on. Even in sleep mode, the fans turn off, but not with acpi off :(

However, with this setting, I can restart the machine using WOL. However, it's not really "off".

Here is the output of /proc/acpi/sleep
```

$ cat /proc/acpi/sleep
S0 S1 S4 S5

```So basically, I want the machine to be in the shutdown mode it is when i turn off power at grub (which is the same power state windows left it in), AND be able to WOL it. So leaving acpi=off is not an option.

Any ideas?

---

### Post by MMistro on 2009-11-05
Here's a possible solution in case someone searches up this thread:

Seems like I can get it to do what I somewhat want it to do, but it involves putting it into hibernate (I think?)

I was googleling some more and stumbled upon this:
[http://lists.pdxlinux.org/pipermail/plug/2007-May/054264.html](http://lists.pdxlinux.org/pipermail/plug/2007-May/054264.html)

and so I tried
```

# echo mem > /sys/power/state

```

which didn't work, but upon outputting the contents of /sys/power/state, there was only standby and disk.

So I then tried 
```

 # echo disk> /sys/power/state
 
```

and it seems like it successfully shut's down the machine, most likely hibernating it. I don't have the server hooked up to any monitor right now, and I'm too lazy to disconnect it and pull it out for that purpose, and my serial cables haven't arrived yet.... so there's no way for me to verify what exactly is happening.

Either way, the power state is low enough that the system and cpu fans shut off, but high enough that it still wakes up.

I still need to test to see if it wakes up after extended periods of hibernating though.

---

### Post by MMistro on 2009-11-05
[SIZE=3]**Full "Solution"**[/SIZE]

Ok so for reference, here are the full steps I followed to get it "working". Once again, I have an old Sun LX50 with dual Intel Pro 10/100 NIC's using the e100 driver.

I managed to get it to "work" by, instead of shutting it down, suspending the system to disk. This may not be what you're looking for, but for me it is an adequate solution as it turns off the system to a lower state then suspend to memory.

Instructions:

Create a script to run at startup which makes sure that ethtool sets wol to g, and also to make sure the appropriate entries in /proc/acpi/wakeup are set to enabled. This can be done by modifying the script mentioned in the start of the tutorial to be like this:

```

$ cat /etc/init.d/wakeonlanconfig

#!/bin/bash
ethtool -s eth0 wol g;
ethtool -s eth1 wol g;

grep 'PCI0.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI0  > /proc/acpi/wakeup;

grep 'PCI1.*enabled' < /proc/acpi/wakeup >/dev/null || \
    echo PCI1  > /proc/acpi/wakeup;

exit;

```I did both pci0/eth0 and 1 to get both my NIC's enabled, even though I'm only using one right now.

So this needs to be included in some file, and be invoked at startup. Refer to the great tutorial on the original post for details. Basically you just throw the script in the /etc/init.d folder, make it executable, and invoke 
```
update-rc.d -f [scriptname] defaults
```to make sure it runs at startup.


Once this is done, try rebooting your machine and running
```

$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
PCI0      S4     [COLOR=Red]**enabled **[/COLOR]no-bus:pci0000:00
PS2K      S1     disabled  pnp:00:06
UAR1      S4     disabled  pnp:00:08
UAR2      S4     disabled  pnp:00:09
USB       S1     disabled  pci:0000:00:0f.2
PCI1      S4     [COLOR=Red]**enabled **[/COLOR]no-bus:pci0000:01

```Make sure that they are automatically enabled on startup by the script you just created. This just makes your life easier, and it's one less thing to remember when "shutting down".

Now, the reason I did a suspend to disk is because it seems to be the lowest state where the NIC is set properly to receive wol signals and act on them.

Your computer may (if not will) be different. You can check the supported states by running
```

$ cat /sys/power/state
standby disk

```As you can see, in my case, there is only standby and disk. Standby kept the chassis/cpu fans running. Since it's a 1U rackmounted chassis, I'd rather have the tiny fans off when the computer is supposed to be shut down since it sounds like a vacuum cleaner when running :biggrin: The disk state seems to bring the system down into that level.

Now to suspend the system to the disk, run:
```

# echo disk > /sys/power/state

```You can always throw this into a script called "hibernate" or something and put it in some directory on your classpath to make things easier.

And all that's left to do is to test it!

Again, I havn't tested this for periods longer than 15 minutes. There could still be that issue where the mobo cuts power to the NIC's after a certain period of time. I'm going to leave the machine like that overnight and I'll report on the results in this post in the morning.

Hopefully all this ends up helping someone with an older system like mine ;)

---

### Post by koszta on 2010-02-24
Hey I have the very same NIC and the very same problem. Can you post some more info on how you got it solved and how it worked out for you? It seems to me that the NIC is just incapable of waking up the computer which is SUPER annoying... 

I tried forcing the older eepro100 driver but it didnt work out. I just think that e100 still lacks wol capability in general...sad ...

I mean I really want to turn the machine off and then wake it completely... THIS IS JUST FREAKING annoying...oh well... (I've got a Dell server and it astonishes me that such companies like Sun or Dell would dare to not test their machines in working conditions with linux... My complain also goes to Intel since their driver is barely good enough for establishing the basic connection...)

---

### Post by koszta on 2010-02-24
Here we go with a very probable solution but it seems that you need to recompile the driver yourself 

[http://www.mail-archive.com/netdev@v.../msg29552.html](http://www.mail-archive.com/netdev@v.../msg29552.html)

Dont have time for it but will try to compile the new driver version from intel with this fix tmrw and will let you know

---

### Post by MMistro on 2010-05-15
Thanks for looking into this! Hopefully your post will help other's in the future who stumble upon this.

As for my specific problem, that server is no more... I threw it off my balcony...




Actually I donated it to someone since it was no longer needed :)

---

