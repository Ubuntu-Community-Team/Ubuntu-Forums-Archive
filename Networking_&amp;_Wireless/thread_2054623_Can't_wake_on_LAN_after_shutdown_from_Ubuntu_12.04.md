---
title: "Can't wake on LAN after shutdown from Ubuntu 12.04.1 Server"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by ItEndsWithTens on 2012-09-07
About a year ago I built a little home backup server from some spare parts I had lying around, and it had been working reasonably well, a few quirks notwithstanding. Earlier this week, however, in the process of replacing the hard drive with something larger, I noticed a burst capacitor on the motherboard. With a new hard drive on hand and a need to replace the other components anyway, it seemed like the perfect time to switch from Windows 2000 Pro to something that still receives security updates, and I've become rather fond of Ubuntu over the past few months. I don't want the system to be running around the clock, though, and I'd like to get Wake on LAN working, but I'm not having any luck.

My research thus far has included these pages:

[http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)
[http://ubuntuforums.org/showthread.php?t=2018218](http://ubuntuforums.org/showthread.php?t=2018218)
[http://ubuntuforums.org/showthread.php?t=1598356](http://ubuntuforums.org/showthread.php?t=1598356)
[http://ubuntuforums.org/showthread.php?t=1892570](http://ubuntuforums.org/showthread.php?t=1892570)
[http://www.linuxquestions.org/questions/linux-networking-3/howto-make-wake-on-lan-wol-work-712283/](http://www.linuxquestions.org/questions/linux-networking-3/howto-make-wake-on-lan-wol-work-712283/)
[http://confoundedtech.blogspot.com/2011/06/enable-wol-on-ubuntu-hp-microserver.html](http://confoundedtech.blogspot.com/2011/06/enable-wol-on-ubuntu-hp-microserver.html)
[http://www.htgi.ca/node/25](http://www.htgi.ca/node/25)

There have been others, but it always seems to come back to those, and I'm going around in circles trying to apply the lessons learned there to my own hardware setup. My apologies for the volume of text, but I've tried a few different things and I want to provide as much detail as possible.

Perhaps worth noting is that although that capacitor was a problem, the previous motherboard/CPU combo did work well enough to boot an operating system, and at first I installed Ubuntu 12.04 Desktop. The system was flaky thanks to the damaged hardware, but when I ran sudo shutdown -P now to poweroff the computer, I'd then be able to wake it up by Magic Packet from any computer on the network. The old motherboard had a built-in NIC, and I didn't have to do anything to the OS to get remote wakeup working.

The replacement hardware, running under 12.04.1 Server (I switched to Server when I read about Desktop's Network Manager potentially interfering with WOL; I don't need a GUI anyway, and Server is what I've been using for the tests I'll be describing), hasn't been cooperating. I'm using an MSI K7T266Pro2, R2.0, with one particular resistor removed and a beta bios (3.7B4) that allows use of an Athlon XP 2600+ that was incompatible with the board in factory condition. I'd be nervous about mods like that too, but one of the two network cards I've been testing does seem to work properly when the system is shut down from Windows, which gives me hope it's not the motherboard's fault.

This board doesn't have a network interface built in, and I've tried two PCI adapters: a CNet Pro200WL with a Davicom DM9102AF chipset, and a 3Com 3C905B-TXNM with one of their own chipsets. Ubuntu loads the dmfe driver for the former, and the 3c59x for the latter. Both can connect to the network, but neither one will let me wake on lan, despite both supporting magic packet wakeup (g in ethtool). I can't get the 3Com to wake after a Windows shutdown, though, so I'm not too worried about that one; that the CNet works after Windows powers off is what gets my attention. Whether I send the packet after only a few seconds, or wait fifteen minutes, the system wakes up.

I have the BIOS options "Wake Up On Ring/LAN" and "Wake Up On PME" enabled, and I've got "Power Management/APM" enabled, along with each listed IRQ set to Monitor instead of Ignore, just in case (the defaults only monitor a handful). I tried disabling APM, since from what I read you can't have both it and ACPI, but that didn't make a difference.

I only install one network card at a time, and I make sure to send the magic packet to the right MAC address for each test. I made that mistake a couple of times, I'm embarrassed to say, sending to the CNet address when the 3Com was installed. Now I double check. I won't be surprised to discover that my problem stems from doing something similarly braindead.

I've tried using

```
sudo ethtool -s eth0 wol g
```

to change the wakeup option. I've tried it by hand at the command line, I've tried it in /etc/network/interfaces to run it every time the network interface is brought up and every time it's brought down, I've tried it in /etc/rc.local, and I've tried directly creating scripts in /etc/rc0.d and /etc/rc6.d, to no avail. Each time it seems to correctly change the wol setting, but it never lets the system wake up. I've noticed something interesting, though: in the output of dmesg, I see that the 3Com driver reports that PME# was enabled after running the ethtool command, and the output of lspci -vv shows that the "PME-Enable" status item is changed, while the CNet card has no such luck. Running sudo ethtool eth0 after setting wol to g suggests that the option has changed, but nothing is added to dmesg. In both cases, the system won't respond to magic packets after a sudo shutdown -P now.

I've tried using acpitool, or just direct access to /proc/acpi/wakeup, to change the state of the various wakeup devices on the system, but neither network card shows up in the list. I've also got a USB 2.0 card I added (for faster testing with Live USB sticks, as the motherboard only has USB 1.1 built in), and it's not listed either. I've tried enabling PCI0, which is the bus on which the network card is located, but it hasn't helped. I also notice nothing in the list supports S5; three USB controllers support waking from S3 (suspend), while the few others that show up support S4 (hibernate). Windows brings the hardware down to S5 on shutdown, I believe, and as I say, the CNet card wakes from that, so I'm not sure what to think here. I feel like this is the big issue, and if I could figure out why none of the PCI cards I've added get listed as ACPI wakeup capable, I'd be on track to a solution.

Poking around in /etc/init.d/halt, I changed the NETDOWN variable to "no", as has been suggested elsewhere, and it didn't help either.

I've also gotten so desperate as to try messing with setpci, but that's getting into terrifyingly dangerous territory. Playing around with a virtual network card installed in an Ubuntu virtual machine, running in VirtualBox on one of my Windows computers, ended up freezing the VM on boot, and forcing me to uninstall the fake hardware from the VirtualBox settings. I know it's only a virtualized installation, but it seems to me directly accessing hardware registers is dangerous, and since I'm having such a hard time figuring out how to find the right register in the first place, I think I should leave this alone until someone more knowledgeable tells me otherwise.

Likewise, I've checked the sysfs filesystem, under /sys. In /sys/devices/pci0000:00/0000:00:08.0/power, which is my CNet card, I see that the wakeup file shows "disabled". Forcing it to enabled didn't help, and the setting was lost on the next boot anyway. The 3Com card, on the other hand, successfully changes this on its own when I run the aforementioned ethool command to turn on magic packet wakeup. I was ecstatic to discover this, but it didn't help me.

I've considered it might be a driver issue, but although the CNet driver package included C source for a Linux module, I've been unable to compile it. I have a passing familiarity with writing C/C++, and I've been doing some work in Linux over the past couple of months, but despite my increasing comfort with the process I've been unable to get this driver to compile. The file is dated 1997-98, so I'm not surprised; the structure of the Linux headers, and which files are included, have no doubt changed significantly in the past fifteen years, and my best efforts at creating symbolic links to point the compiler in the right direction have been unsuccessful. 

I'm terribly sorry to rehash a topic I've seen discussed so many times before, but I haven't managed to get other people's advice to work for me, and I'd appreciate any insight people have into my particular configuration of hardware and operating system. The simplest solution (that doesn't require spending any more money) is to just reinstall Windows 2000 and use that, but I'd really rather not go back to running an internet-connected computer with an OS that no longer receives security patches. It wouldn't explain what's wrong, anyway. If anyone can offer advice I'll be eternally in your debt, as I have an enormous variety of trivial nonsense I'd like to conveniently back up.

---

### Post by ItEndsWithTens on 2012-09-12
Go figure. I held off of starting this thread altogether for almost a week, telling myself the answer was right around the corner, and I should exhaust all my options before asking for help. I finally reached what I thought was the end of my rope, signed up for the board and posted my question, only to stumble upon the solution about six hours afterward. I avoided updating this thread until I'd had the system up and running for a few days to test it, but I've now run several successful backup operations and I feel confident marking this one solved.

The key lay in this thread, one I somehow skipped over initially: **[http://ubuntuforums.org/showthread.php?t=951563](http://ubuntuforums.org/showthread.php?t=951563)** The second post, describing the use of pci-config, is what sorted the whole mess out. From a fresh install of Ubuntu 12.04.1 Server, I followed these steps:

1.) **sudo apt-get install nictools-pci**
This installs a few tools, I believe, but pci-config is the one I needed.

2.) **sudo lspci -nn**
I found the network card's line, and made note of two things: the PCI bus number (the first two digits, at the head of the line, in my case 00) and the vendor and model information (at the end, between the square brackets, for me [1282:9102]).

3.) **sudo pci-config -B 00**
Running pci-config with -B provides a list of devices on the specified bus. Looking at the hexadecimal at the end of each line, and remembering that the two numbers are reversed ([1282:9102] from lspci appears as 91021282), I saw that my network card was Device #3.

4.) **sudo nano /etc/init.d/halt**
I modified the halt script to include the series of commands described in the other thread, placing them just before the actual call to halt:

```
...

[color=blue][b]sudo rmmod dmfe
sudo sleep 0.5                     
sudo modprobe dmfe
sudo sleep 0.5                             
sudo pci-config -B 00 -#3 -S
sudo sleep 0.5[/b][/color]

log_action_msg "Will now halt"
halt -d -f $netdown $poweroff $hddown

...
```

I went with the CNet card, so the dmfe module is the one I need to play with, whereas the 3Com would have used the 3c59x module. I use pci-config's -B option to target Bus 00, the -#3 to specify Device #3, and the -S to put it to sleep (ACPI state D3). I might have been able to achieve the same thing with setpci if I knew what I was doing, but as I mentioned before I'm a little out of my league with that. Bus and device numbers are one thing, hardware registers are another.

I tried using only the pci-config line, to no effect. Removing and reinserting the module, then putting the card to sleep, seems to be the only way to get this working. I didn't test this without the half-second pause after each command, though, so I don't know if those are strictly necessary.

The 'sudo' in each line turned out to be important for what I'm doing; since this is an automated backup system, I have a variety of user accounts that need to be able to shutdown the machine without requiring a password. Adding them to the sudoers list with the "NOPASSWD" option lets them execute certain commands without needing a sudo password, but the 'sudo' still needs to be there in the script. Without it, users can shut the machine off, but it then fails to respond to magic packets, since the rmmod/modprobe/pci-config stuff I added isn't properly executed.

And that's it! None of the other things mentioned in that thread turned out to be necessary in my case. I left NETDOWN set to "yes" in the halt script, didn't have to bother with module options (dmfe doesn't recognize enable_wol or global_enable_wol, anyway), and I didn't need to run update-initramfs.

There are two issues with this approach that I haven't been able to solve: first, the procedure enabled all the Wake on LAN modes that my card supports. Luckily for me, that's only physical activity and magic packet (p and g, respectively, as shown by ethtool). Others might not be so fortunate; if your card supports waking on broadcast activity, for example, I imagine this could be a real pain. I tried adding a call to ethtool at various places in the halt script, but had no luck setting only magic packet wakeup.

The other problem is that, if I'm not mistaken, the halt script might be automatically replaced in future Ubuntu updates/releases, undoing the changes I've made. I briefly tried writing a standalone script that would run at certain runlevels, but didn't get very far before I decided to stop looking a gift horse in the mouth and just go with what I've got so far. If I ever figure out how to do it I'll add the info here, but until then I certainly welcome input from others.

I'm sorry I ended up posting a request for help when the answer was already out there, and on these boards no less; with any luck someone else will find this thread helpful and it won't have been a total waste. Good luck waking up your Ubuntu server, whoever you are!

---

### Post by daigidan on 2012-10-03
Greetings!

I'm writing to let you know that your post proved incredibly useful to someone else by solving a very similar problem for me. Oddly enough, I was also working to setup a backup server. Just for kicks I'll share my story.

I have a machine which had been running MythTV on Ubuntu 7.04 since 2006. I never upgraded due to all the work involved in getting some particular kernel modules working correctly (read: laziness). At any rate, I got FiOS and wanted to start capturing HD, so I setup a new box and decided to reuse the old one as a RAID1 backup server.

I disassembled the box, cleaned it, then put it back together minus a few odds and ends. Both integrated Ethernet controllers have only given me a link light when the machine is powered off since then, so clearly I've done something wrong there, but I worked around it by slotting in an old 3COM card I've had since the turn of the millennium (see above: lazy). I had never really used the network on this machine, except to download schedules for MythTV, but I needed to backup a number of files and this exposed an ACPI problem of some sort which caused kernel panics. I worked around this by passing 'noacpi noapic nolapic' to the kernel at boot and was then able to back the machine up. I did all of this under 7.04 and hoped that the (much) newer kernel in 12.04 would solve my issue as some reports online had suggested it would.

After a fresh install of 12.04, during which the network was fine, I shut down the machine. The next day eth0 was present, ifconfig was showing increasing packet counts with no errors, but I couldn't even ping the gateway. After checking /etc/network/interfaces, trying both static and DHCP addresses, rmmod'ing 3c59x, restarting, changing BIOS options, etc. I tried swapping Ethernet cables. In the process I cut power completely to the motherboard out of habit by flipping the power switch on the PSU, and when the machine came up eth0 was working like a champ.

Then I found your post and started to make the connection with the wol setting. Like you, I only made the changes to the halt script, and now I'm tens of GBs into a file transfer with no errors. My sincere thanks.

---

