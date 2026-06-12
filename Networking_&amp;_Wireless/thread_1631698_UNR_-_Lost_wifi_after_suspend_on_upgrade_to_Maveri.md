---
title: "UNR - Lost wifi after suspend on upgrade to Maverick"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by brigneld on 2010-11-27
I'm using a Asus eeePC1000HE netbook with UNR. Just upgraded to 10.10 Maverick from 10.04. Before upgrading, my wifi worked fine. On upgrade I found that wifi worked fine until I put the PC into suspend mode. On resuming from suspend, network manager failed to find the wifi device (Ralink RT2860), and wnt into an infinite wifi scan.

I tried the following solutions, none of which worked (all sourced via Google):

    * replacing the released drivers with ndiswrapper and xxx driver
    * replacing network-manager with wicd
    * upgrading to latest kernel
    * blacklisting rt drivers
    * etc....

Finally, I found a solution from [elsewhere in these forums]("http://ubuntuforums.org/archive/index.php/t-1028518.html") that fixed it:
Create a file called 'config' in /etc/pm/config.d, and insert in it the following line:

    SUSPEND_MODULES="$SUSPEND_MODULES ndiswrapper"
    (replace ndiswrapper with whatever your driver name is. Use lspci -v)

Since doing this, the wifi resumes from suspend. Only minor problem is that it takes about 5 secs.

Just thought I'd post this, as it was painful for me over 2 weeks.

---

### Post by Finnwal on 2010-12-23
I had the same problem on my Asus Eee PC 1000H with Ubuntu Maverick Desktop version. For months I could not solve the issue. I even downgraded to Lucid to get suspend and resume running.
Thank you very much for posting this solution. It worked immediately on my Eee PC. Now I have Maverick installed again.

---

### Post by antigooner on 2011-01-04
I have this same problem but as a newbie to ubuntu,. I can't follow the instructions.......please could you explain precisely how to do this in greater detail?

thanks in advance

Mel

---

### Post by nriqone on 2011-01-28
Hi there buddy!

First of all thank you very much for the info:P, it was very good. 

The second issue could be seen as an explanation in response to [antigooner]("http://www.uluga.ubuntuforums.org/member.php?u=513963"). As have been said before, you can extract your drivers name using the command "lspci -v". I have an Asus eee pc 1000h and the output (only the wifi one) is:

> 01:00.0 Network controller: RaLink RT2860
    Subsystem: RaLink Device 2790
    Physical Slot: eeepc-wifi
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fbef0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: [COLOR=Red]rt2800pci[/COLOR]
    Kernel modules: rt2860sta, rt2800pci
The red one is the driver name (at least I used that and it works).
Also and if you have an Asus eee pc 1000h, you can use this command:

> sudo echo "SUSPEND_MODULES=\"\$SUSPEND_MODULES rt2800pci\" ">>/etc/pm/config.d/configto create the file with the needed text.

I hope you can found this useful.

---

