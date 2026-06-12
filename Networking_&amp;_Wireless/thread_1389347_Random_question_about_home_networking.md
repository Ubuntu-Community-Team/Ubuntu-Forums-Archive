---
title: "Random question about home networking"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by blueshiftoverwatch on 2010-01-24
I was going to assign static IP addresses to the computers in my house instead of using DHCP and had a few questions about networking.

1. I have multiple computers with multiple OS's multi-booted. Should I assign 1 IP address per computer or per OS?

2. On all my computers the default gateway is the IP address of my router, which makes sense. But the default gateway on my router is a number that is different from my public IP address. Why is this?

3. While in my router settings I also noticed that the Internet and LAN have different subnet mask settings. LAN is the standard 255.255.255.0 but the Internet is different, why?

4. I'm assuming it won't mess anything up to leave DHCP enabled on my router after setting up static IP addresses, right? It seems like that's something I'd want to leave enabled in case someone brought over an Internet capable device like a laptop. So they could quickly connect to the Internet without having to manually set anything up.

5. Does assigning static IP addresses require that I do anything special in my router's settings?

---

### Post by chili555 on 2010-01-24
> I have multiple computers with multiple OS's multi-booted. Should I assign 1 IP address per computer or per OS?Makes no difference. It it were me, I'd do one per computer.> On all my computers the default gateway is the IP address of my router, which makes sense. But the default gateway on my router is a number that is different from my public IP address. Why is this?Your ISP delivers IP addresses to your router, your neighbor's router, his neighbor, etc. All feed through one gateway, sort of like a super-router.> I'm assuming it won't mess anything up to leave DHCP enabled on my router after setting up static IP addresses, right?Correct.> Does assigning static IP addresses require that I do anything special in my router's settings?None. Just be sure the addresses you assign are outside the DHCP range. For example, I have my router set to allow DHCP addresses in the range from 192.168.1.100 to x.104; that is, five addresses. I then use static addresses from x.105 on up.

You will probably have better luck with Network Manager completely removed from the static machines.

---

### Post by blueshiftoverwatch on 2010-01-24
> **chili555 said:**
> Just be sure the addresses you assign are outside the DHCP range. For example, I have my router set to allow DHCP addresses in the range from 192.168.1.100 to x.104; that is, five addresses. I then use static addresses from x.105 on up.
I actually hadn't thought of that.
> **chili555 said:**
> You will probably have better luck with Network Manager completely removed from the static machines.
I only have 1 machine running Linux. But why would I want it removed as long as the static IP address is set as the default connection type?

---

### Post by chili555 on 2010-01-24
> why would I want it removed as long as the static IP address is set as the default connection type?A lot of people seem to have difficulty with it and no-one, including me, has any difficulty with a correctly set purely manual configuration. Try it and if NM works well for you, then you are all set!

---

### Post by tgalati4 on 2010-01-24
You also want one IP per OS because you may set up ssh keys and shared mounts with one machine but under different OS's.  That way your /etc/hosts table on each machine reflects each machine/OS combination.  It's a little more work, but ultimately less confusing when you try to attach to a remote directory and you find it's not there because the machine is booted into a different OS.

---

### Post by Iowan on 2010-01-24
I prefer to let the DHCP server (router) hand out static leases (based on MAC address) and let the clients stay set for DHCP... but nothing says that's the only (or even best) way to do it.

---

### Post by blueshiftoverwatch on 2010-01-24
I got static IP addresses setup under Windows and Mac OSX. But I can't seem to get it setup with Network Manager Applet for Linux. I'll enter in all the relevant information but when I click on the applet icon I don't see the connection I just created listed under either of my networking cards. All that exists is Auto Ethernet, which uses DHCP. So I must be doing something wrong.

More questions:
1. Are multiple DNS's added by putting a comma followed by a space between them, as is the case with OSX?

2. What is the "Routes" button underneath the blanked out "DHCP Client ID" textbox used for?

3. Do I have to fill out the MAC address on the "Wired" page/tab? Seems like something it would automatically detect. I didn't notice it being filled out under my Auto Ethernet settings. So I'm assuming it's something I can leave blank, right?

4. This isn't really relevant. But why isn't 4.2.2.1 added by default as a backup DNS?

---

### Post by blueshiftoverwatch on 2010-01-24
After deleting NewtworkManager because apparently you can't use it to set static IP addresses I tried the following commands. I'm currently typing this from a virtual machine:

sudo ifconfig eth1 192.168.1.XXX netmark 255.255.255.0 up
-and-
sudo route add default gw 192.168.1.X

---

### Post by chili555 on 2010-01-25
To make it permanent, amend */etc/network/interfaces* to:```
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.1.XXX
netmask 255.255.255.0
gateway 192.168.1.X
```

---

### Post by blueshiftoverwatch on 2010-01-25
> **chili555 said:**
> To make it permanent, amend */etc/network/interfaces* to
That's basically what I had before, only without the first two lines of code and I had a broadcast setting in there. It worked after saving, but after I rebooted it didn't.  Yours didn't work at all.

---

### Post by chili555 on 2010-01-25
eth1 is the relevant interface? Is it wireless? Any encryption, WEP, WPA, etc.??

---

### Post by blueshiftoverwatch on 2010-01-25
> **chili555 said:**
> eth1 is the relevant interface? Is it wireless? Any encryption, WEP, WPA, etc.??
Eth1 is the slot I have my ethernet cable plugged into. I haven't moved it since this began. I copied the text you posted (which is what a lot of other sites said to do as well) exactly. Except for obviously replacing the X's with the relevant numbers. Which are the exact same numbers (except the static IP address, obviously) that I successfully used to setup static IP's on both Windows and OSX.

Just for good measure I changed it to eth0 and restarted the system, but to no avail. I also tried pinging my upstairs computer just to see if it would at least recognize my local network. But as soon as I entered the command it said that no network was found.

---

### Post by chili555 on 2010-01-26
Please post:```
ifconfig
sudo lshw -C network
```Thanks.

---

### Post by blueshiftoverwatch on 2010-01-26
Here are my two networking cards with the MAC addresses edited out.
```
*-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: XX:XX:XX:XX:XX:XX
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:a800(size=256) memory:f8eff000-f8efffff(prefetchable) memory:f8ef8000-f8efbfff(prefetchable) memory:fe8e0000-fe8fffff(prefetchable)
```
  
```
*-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: XX:XX:XX:XX:XX:XX
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:31 ioport:b800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8ff8000-f8ffbfff(prefetchable) memory:fe9e0000-fe9fffff(prefetchable)
```

---

### Post by chili555 on 2010-01-26
> *-network DISABLEDDisabled? I wonder why they are both disabled. Are they enabled in the BIOS? Are you dual-booting with Windows?

---

### Post by blueshiftoverwatch on 2010-01-26
> **chili555 said:**
> Disabled? I wonder why they are both disabled. Are they enabled in the BIOS? Are you dual-booting with Windows?
I didn't touch anything in the BIOS relating to my networking cards. I'm triple-booting with Windows XP and Windows 7. I can access the Internet on both versions of Windows perfectly fine.

I also run XP and Server 2003 on Ubuntu by means of Virtualbox. Up until I accidentally broke the VM's by turning off my computer without properly shutting down the VM's I could access the Internet from within both VM's. Even though I couldn't access it from Ubuntu at the exact same time.

---

### Post by chili555 on 2010-01-26
The plot thickens...May we please see:```
dmesg | grep eth
dmesg | grep r8169
```This is a very strange problem.

---

### Post by ant2ne on 2010-01-26
what is your /etc/network/interfaces? Post the results of```
cat /etc/network/interfaces
```and then post the results of ```
ifconfig
```

---

### Post by blueshiftoverwatch on 2010-01-26
> **chili555 said:**
> The plot thickens...May we please see
Here is the code I got for "eth". I edited out the hex numbers that came before my MAC address because I didn't know what they stood for and didn't want to risk posting anything personally identifiable on a public forum.
```
[    3.990842] eth0: RTL8168d/8111d at XXXXXXXXXXXXXXXXXX, XX:XX:XX:XX:XX:XX, XID 281000c0 IRQ 30
[    3.995421] eth1: RTL8168d/8111d at XXXXXXXXXXXXXXXXXX, XX:XX:XX:XX:XX:XX, XID 281000c0 IRQ 31
```

r8169:
```
[    3.990393] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.990409] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.990453] r8169 0000:02:00.0: setting latency timer to 64
[    3.990495] r8169 0000:02:00.0: irq 30 for MSI/MSI-X
[    3.995020] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.995031] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.995054] r8169 0000:03:00.0: setting latency timer to 64
[    3.995093] r8169 0000:03:00.0: irq 31 for MSI/MSI-X
```

cat /etc/network/interfaces:

EDIT: It says "eth0" instead of "eth1" because it's still there from when I changed it over to eth0 just to see if it would work. Which it didn't. So, I know that eth0 isn't the correct networking card and will change it back when someone else posts a possible solution.
```
auto lo
auto lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```

Just typing "ifconfig" doesn't actually do anything. I assume you meant ifconfig -a.
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 Base address:0x4000 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

---

### Post by blueshiftoverwatch on 2010-01-27
Bump.

I tried to get Network Manager re-installed so at least I could use DHCP to connect to the Internet. But ran into dependency hell issues and now I have a broken package that in order to fix, a lot of other packages must be uninstalled. I'd like to just get my static IP address assigned by modifying text files so I can put this mess behind me.

---

### Post by chili555 on 2010-01-27
> Just typing "ifconfig" doesn't actually do anything.It certainly does on all four of my Ubuntu computers. I hope this is not a symptom of a larger issue!

I am stunned that, although *interfaces* forces an IP address on either eth0 or eth1, it does not show up in *ifconfig*!! I am also stunned that *lshw* shows ***both*** interfaces with link=yes. You don't have two ethernet cables connected, do you? Please do:```
sudo /etc/init.d/networking restart
ifconfig -a
```Does one of the interfaces now have an IP address? If so, can you ping the router?```
ping -c3 192.168.1.1
```If not, please post:```
dmesg | grep eth
```You have a very mysterious problem and it's my favorite kind: everything looks perfect but it just doesn't work!

---

### Post by ant2ne on 2010-01-27
yeah something isn't right. Have we verified that the hardware is good? That the wires are good? The NIC in computer (eth0 and or eth1) is good? That the port on the switch/router is good?

---

### Post by blueshiftoverwatch on 2010-01-27
> **chili555 said:**
> You don't have two ethernet cables connected, do you?
No, just one.
[B]sudo /etc/init.d/networking restart
ifconfig -a[/B]
```
Reconfiguring network interfaces...                                          /etc/network/interfaces:2: interface lo declared allow-auto twice
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: interface lo declared allow-auto twice
ifup: couldn't read interfaces file "/etc/network/interfaces"
```
**ping -c3 192.168.1.1**
Nope.
```
connect: Network is unreachable
```
**dmesg | grep eth**
```
[    3.987764] eth0: RTL8168d/8111d at XXXXXXXXXXXXXXXXXX, XX:XX:XX:XX:XX:XX, XID 281000c0 IRQ 30
[    4.000805] eth1: RTL8168d/8111d at XXXXXXXXXXXXXXXXXX, XX:XX:XX:XX:XX:XX, XID 281000c0 IRQ 31
[   14.141973] r8169: eth1: link up
[   14.141978] r8169: eth1: link up
[   14.213330] r8169: eth0: link down
[   14.213921] ADDRCONF(NETDEV_UP): eth0: link is not ready
```
> **ant2ne said:**
> yeah something isn't right. Have we verified that the hardware is good? That the wires are good? The NIC in computer (eth0 and or eth1) is good? That the port on the switch/router is good?
I can connect to the Internet on Windows XP and Windows 7 which I triple boot with Ubuntu. Also, I can access the internet through Windows XP and Windows Server 2003 running in Virtualbox when at the same time Ubuntu couldn't connect at all. Or, at least I could until I restarted the computer before the VM's were properly powered down and something broke. But I'll figure out that problem if I manage to get my Internet back up again.

---

### Post by chili555 on 2010-01-27
> ifdown: couldn't read interfaces file "/etc/network/interfaces"
This is not happy. Please post the file.

---

### Post by blueshiftoverwatch on 2010-01-27
> **chili555 said:**
> This is not happy. Please post the file.
The configurations in this file were still set to eth0 when I tried to ping my router. So I went back and changed them back to eth1 (the networking card that's actually plugged in) and tried to ping it again. But it didn't work either.

Here's my file. Although I don't see anything abnormal about it.
```
auto lo
auto lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1
```

---

### Post by chili555 on 2010-01-27
> auto lo
auto lo inet loopbackThis should read:```
auto lo
[COLOR="Red"]iface[/COLOR] lo inet loopback


```Please amend. I am also puzzled that the system seems unable to read the file. Please do:```
ls -al /etc/network/interfaces
```It should be readable by all:> -rw-r--r-- 1 root root 228 2009-10-12 12:38 /etc/network/interfacesIf not, please do:```
sudo chmod +r  /etc/network/interfaces
```Then restart networking again and see if we have any complaints:```
sudo /etc/init.d/networking restart
```If none, let's see what we see here:```
ifconfig
```Thanks.

---

### Post by blueshiftoverwatch on 2010-01-27
> **chili555 said:**
> This should read:[CODE]auto lo
[COLOR="Red"]iface[/COLOR] lo inet loopback
That managed to do it. I have no idea how I managed to overlook something like that. Thanks for all of the help.

---

### Post by ant2ne on 2010-01-28
weird.. back on post 9 it was right.

---

### Post by blueshiftoverwatch on 2010-01-28
> **ant2ne said:**
> weird.. back on post 9 it was right.
I compared his post in [#9]("http://ubuntuforums.org/showpost.php?p=8721233&postcount=9") to mine in[#19]("http://ubuntuforums.org/showpost.php?p=8729453&postcount=19") and it looks like instead of copying and pasting what he said to write I compared our two blocks of text, didn't notice that "auto" was supposed to be "iface", and therefore didn't change anything in mine. I wish I had notice that in the first place and not wasted everyone's time.

I still want to know what those weird hex numbers you get when you type in "eth" represent. Not the ones with the colons, I know those are MAC addresses. But the ones without any colons that come before the MAC addresses. I blacked mine out with X's out of paranoia.

---

### Post by ant2ne on 2010-01-29
> **blueshiftoverwatch said:**
> I still want to know what those weird hex numbers you get when you type in "eth" represent. Not the ones with the colons, I know those are MAC addresses. But the ones without any colons that come before the MAC addresses. I blacked mine out with X's out of paranoia.not sure what you are talking about. Typing eth into a terminal doesn't do anything of value

---

### Post by chili555 on 2010-01-29
> **ant2ne said:**
> not sure what you are talking about. Typing eth into a terminal doesn't do anything of valueHe means here: [http://ubuntuforums.org/showpost.php?p=8729453&postcount=19](http://ubuntuforums.org/showpost.php?p=8729453&postcount=19)

---

