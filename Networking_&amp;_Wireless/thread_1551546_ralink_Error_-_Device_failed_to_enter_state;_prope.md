---
title: "ralink Error - Device failed to enter state; proper workaround?"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by wayover13 on 2010-08-12
I've experienced a glitch with my ralink rt2500 wireless card. I've found a workaround for the glitch but want to ask about the best way to implement it. Find below a description of the problem and a request for help in applying the workaround.

My ralink rt2500 wireless card works fine under Lucid. But I've discovered that it keeps broadcasting error messages: > rt2500pci_set_device_state: Error - Device failed to enter state 1 (-16) This appears to be a problem related to the module for this card and it afflicts certain kernels, including the stock Lucid kernel. I think the volume of error messages the card broadcasts may be related to some system instability I've seen lately.

There's a fairly simple workaround for the problem: simply issue "sudo iwconfig ra0 power off" (my card ends up being ra0, but your ralink card may get a different identifier). This disables some sort of power-saving feature on the card and causes the error messages to stop. But I'm so far at a loss for how to make that command run automatically when the card is brought up. That's the main thing I want to inquire about in this thread - how do I incorporate this command into the card's initialization, so that don't have to run it from the CLI each time the card is brought up?

A cron job is the wrong approach since, once the card is up and the command has been run there's no sense in running it again unless the network goes down or is manually stopped and needs to brought up again (something that does happen from time to time with this machine). Perhaps, then, the workaround should be incorporated into the ifup command? I'm unsure how to do that, though. Also, I have the system bringing up the card on every boot and I'm unsure whether ifup is invoked in that case: anyone know about that? 

So what's the best way to make sure the command "iwconfig ra0 power off" gets run (with root privileges) every time the interface is brought up?

This problem is supposed to be fixed in a future kernel, by the way. But for now those of us with ralink hardware who use Lucid need an automated workaround. Ideas?

Thanks,
James

PS Relevant links that discuss the problem and workaround: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6076](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6076) ; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456977](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/456977) ; [https://bbs.archlinux.org/viewtopic.php?id=82589](https://bbs.archlinux.org/viewtopic.php?id=82589) ; [http://forums.debian.net/viewtopic.php?f=5&t=51895](http://forums.debian.net/viewtopic.php?f=5&t=51895)

---

### Post by wayover13 on 2010-08-12
Rooting around the system it begins to seem to me that something in /etc/network, /etc/init, or /etc/init.d might be edited to make the iwconfig ra0 power off command run each time the ralink interface is brought up. Does that make sense to anyone else? If so, what to edit and how?

Another possibility could be editing /etc/rc.local. But that seems less likely.

Input, anyone?

Thanks,
James

---

### Post by wayover13 on 2010-08-13
Ok. Here's what I'm trying, lifted from [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/) (I think the stanza I'm excerpting comes from a sample /etc/network/interfaces file which, though I do not find on my current system, I'm sure I've looked at before somewhere): > # A more complicated ethernet setup, with a less common netmask, and a downright
# weird broadcast address: (the "up" lines are executed verbatim when the
# interface is brought up, the "down" lines when it's brought down)
#
# auto eth0
# iface eth0 inet static
#     address 192.168.1.42
#     network 192.168.1.0
#     netmask 255.255.255.128
#     broadcast 192.168.1.0
#     up route add -net 192.168.1.128 netmask 255.255.255.128 gw 192.168.1.2
#     up route add default gw 192.168.1.200
#     down route del default gw 192.168.1.200
#     down route del -net 192.168.1.128 netmask 255.255.255.128 gw 192.168.1.2
I gather from this that inserting a line in the /etc/network/interfaces file that reads > up iwconfig ra0 power off will cause to happen what I'm asking about (I inserted that line *after* the line "iface ra0 inet dhcp" in my /etc/network/interfaces file, btw). That is to say that the "up" option in this files causes the specified command to run whenever the interface is brought up. And I want the iwconfig ra0 power off command to run each time the interface is brought up, so this seems to offer me a solution.

I entered that line in the file, issued ifdown, then ifup, and did not get the continuous stream of error messages I was previously seeing. This initial test, then, indicates that this may be a good way to implement the workaround.

Any further input on this matter? Hopefully my solution will continue working, and hopefully a new kernel and/or modules for this NIC will soon be released so that this workaround becomes unnecessary. I'll post to this thread again if I come to realize that I've not resolved my problems with this approach.

James

---

### Post by wayover13 on 2010-08-14
I've discovered that entering the line > up iwconfig ra0 power off into the /etc/network/interfaces file does NOT cause the ralink card's power management feature to be turned off upon rebooting. It apparently only disables it when you issue ifup ra0 on an already-running system. So I had to find a different solution, since I want the card initialized when the computer boot up.

Here's what I did for the next step in this workaround. I made a primitive script called "ra0-powoff" that has only 2 lines: > #!/bin/sh
iwconfig ra0 power off I then made that script executable (chmod +x ra0-powoff). I then put a symlink to that script in the directory /etc/network/if-up.d . After rebooting the computer I found that no error messages were being broadcast in relation to my ralink card, so I assume this has resolved the problem of the card coming up with power management on (when it should be off) upon reboot.

There's gotta be a more elegant solution. But if no one here is willing to offer help I'll have to make due with my two kludges until the new kernel with working power management code comes out.

James

---

