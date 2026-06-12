---
title: "Cannot Connect Wirelessly - Dell 1764"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by metal_falsetto on 2010-10-22
Howdy. Long time lurker, first-time poster. 

I just purchased a refurbed Dell Inspiron 1764 i5 Laptop running 10.04. Having done a little research before receiving it, I knew there were a few issues with the wireless, but it seemed as though they were easily remedied. Not so in my case. 

The wireless failed to connect out of the box. I have no problem seeing wireless networks -- I see multiple both at work and at home. But when I attempt to connect, it will attempt to connect for a few minutes, then prompt me to re-enter my password. Re-entering the password does not work. 

I've attempted a couple remedies that I've found here on the forums. 

As found in this thread: 

[http://art.ubuntuforums.org/showthread.php?t=1596569#post9971492](http://art.ubuntuforums.org/showthread.php?t=1596569#post9971492)

I completely removed and reinstalled bcmwl-kernel-source. No go.

Then I found this thread: 

[http://www.uluga.ubuntuforums.org/showthread.php?p=9562713](http://www.uluga.ubuntuforums.org/showthread.php?p=9562713)

And I took some advice in there, and modified my blacklist.conf file. Again, no go.

Thinking/hoping that upgrading to 10.10 might remedy the situation, I went ahead and did that. Same problem. I tried both of the above fixes once I had upgraded; still no worky. 

Not really sure where to go at this point. Any help would be greatly appreciated!

---

### Post by P4man on 2010-10-22
it would help if you told us what network card is in there. WHile you are at it, provide output of

```
lspci -nn
lshw -C network
rfkill
```

---

### Post by metal_falsetto on 2010-10-22
> **P4man said:**
> it would help if you told us what network card is in there. WHile you are at it, provide output of

```
lspci -nn
lshw -C network
rfkill
```

Thanks for the response. 

The network card is the Dell 1520.

Here's the output:

> lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
03:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)


```> lshw -C network```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 0c:ee:e6:b5:3b:f5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.10 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:26:b9:13:95:b8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.11 latency=0 multicast=yes
       resources: irq:43 ioport:2000(size=256) memory:f0810000-f0810fff memory:f0800000-f080ffff memory:f0820000-f083ffff


```
> rfkill```
Usage:    rfkill [options] command
Options:
    --version    show version (0.4)
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm

```

---

### Post by P4man on 2010-10-22
sorry that should have been

```
rfkill list
```

---

### Post by metal_falsetto on 2010-10-22
> **P4man said:**
> sorry that should have been

```
rfkill list
```

That produces nothing -- just sends me back to the prompt.

---

### Post by metal_falsetto on 2010-10-22
Okay, it gets weirder. After two days of not being able to connect at all, I just connected out of the blue. It only lasted about a minute or so, though.

---

### Post by P4man on 2010-10-23
Have you tried the instructions here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20b43/STA%20hybrid%20drivers)

---

### Post by Bludkill on 2010-10-23
Might not be relevant, but does this help?

[http://www.uluga.ubuntuforums.org/showthread.php?t=1448215](http://www.uluga.ubuntuforums.org/showthread.php?t=1448215)

---

### Post by metal_falsetto on 2010-10-23
Okay. I checked out Bludkill's link, and it piqued my interest. One of the threads in my original post told me to blacklist "dell_laptop," but the thread he/she referenced told me to blacklist "dell-laptop." I did that, and after restarting, I was able to connect. But as soon as I started moving around the room, I lost my internet activity (despite still having a signal from my router). 

And here's where it gets *really* weird. After a little experimenting, I've come to the conclusion that I can only get an active connection when the power cable is plugged into the laptop. With the cable plugged in, I'll click a link -- the page loads. I unplug the power cable, page doesn't load and eventually times out. I click the link again, page will not load -- but if I plug in the power cable while the page is trying to load, the page will load about a second or two after plugging in the power cable.

When I first Googled the problems I had with the wireless, I found a few complaints from Windows users concerning the strength of this card in this laptop. Could it be that the power cable functions as some sort of antenna to the otherwise super-weak card? 

FWIW, I am right on top of my router -- it's mounted in my basement, on a joist just below the floorboards where I'm sitting. I also have a Dell Mini 9 running UNR 9.04, and I've never had any problems connecting with that, either on this floor, or the floor above me.

---

### Post by P4man on 2010-10-23
A very similar problem got reported here:
[http://ubuntuforums.org/showthread.php?t=1601777](http://ubuntuforums.org/showthread.php?t=1601777)

He can only connect wirelessly if he boots or logs in with the power cable connected, and its a totally different wifi card, so its not a driver issue, but probably something power management related. 

I think its time to find or file a bugreport on this.

---

### Post by metal_falsetto on 2010-10-23
Yeah, his comment #15 sounds exactly what I was experiencing earlier. And I was thinking of just replacing the card before I saw your last post.

---

### Post by P4man on 2010-10-24
now Im wondering if changing the card will help at all.. just sayin

---

### Post by P4man on 2010-10-24
Did some more digging. Can you provide the output of following command with the power cord detached:

```
cat /sys/module/pcie_aspm/parameters/policy
```

```
iwpriv -a
```

```
iwconfig
``` 

If you see powermanagement set to "on" for your wifi with the last command, you can already try

```
sudo iwconfig wlan0 power off
```

If that doesnt help, here is another thing to try:

```
 echo default | sudo tee -a /sys/module/pcie_aspm/parameters/policy 
```

---

### Post by metal_falsetto on 2010-10-24
Thanks for your help on this.

Here's what I got...

> cat /sys/module/pcie_aspm/parameters/policy


```
default performance [powersave] 
```


> iwpriv -a


```
lo        no private ioctls.

eth0      no private ioctls.

eth1      Available read-only private ioctl :

```


> iwconfig


```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:128  invalid misc:0

```

I didn't see anything in the last command that seemed to relate to power management, although there was that "powersave" result from the first one.

---

### Post by P4man on 2010-10-24
so try

```
 echo default | sudo tee -a /sys/module/pcie_aspm/parameters/policy
```

or even replace *default* with *performance*

---

### Post by metal_falsetto on 2010-10-24
```
tee: sys/module/pcie_aspm/parameters/policy: No such file or directory
```

Got this for both the "default" and "performance" variations of that code.

---

### Post by P4man on 2010-10-25
sorry I missed the leading "/"

```
 echo default | sudo tee -a [COLOR="Red"]/[/COLOR]sys/module/pcie_aspm/parameters/policy
```

---

### Post by metal_falsetto on 2010-10-25
Hrm...
```
ben@ben-Inspiron-1764:~$  echo default | sudo tee -a /sys/module/pcie_aspm/parameters/policy
default
ben@ben-Inspiron-1764:~$  echo performance | sudo tee -a /sys/module/pcie_aspm/parameters/policy
performance

```

---

### Post by P4man on 2010-10-26
I guess its not changing anything or?

---

### Post by metal_falsetto on 2010-10-26
The responses to those prompts were just "default" and "performance," respectively.

---

### Post by P4man on 2010-10-26
yes that is correct. It should. But it also changes PCI-Express power management settings, you can check that with:

```
cat /sys/module/pcie_aspm/parameters/policy 
```

so the question is: does it solve your wifi woes? I assume not?

---

### Post by metal_falsetto on 2010-10-26
Still no worky.

---

### Post by P4man on 2010-10-26
Bummer. Lets try manually setting transmit power then.
```

 sudo iwconfig eth1 txpower on
```

you can even try setting the value like this:
```
 sudo iwconfig eth1 txpower 30mW

```

Im also still curous why ```
sudo rkill list
``` doesnt produce any output. Can you upload or attach the dmesg log?

---

### Post by metal_falsetto on 2010-10-26
Neither of the transmit power commands seemed to do anything. 

I tried the rfkill list again, still back to the prompt. 

I've attached the dmesg log. (I zipped it, it was too big for the forum's .txt file max).

---

### Post by P4man on 2010-10-27
Perhaps give the windows drivers a try with ndiswrapper. See here:
[http://www.uluga.ubuntuforums.org/showpost.php?p=9289470&postcount=10](http://www.uluga.ubuntuforums.org/showpost.php?p=9289470&postcount=10)

---

### Post by metal_falsetto on 2010-10-28
Well, that really screwed me up. Now I can't see wireless networks at all.

---

### Post by metal_falsetto on 2010-10-28
Ahem. Kind of stymied... 

After installing ndiswrapper and the windows driver, I lost the ability to see any wireless. I uninstalled the driver, then Wicd, then ndisgtk. 

But it seems like the system is still defaulting to another driver, as opposed to reverting back to the Broadcom STA that ships with the OS. When I go to System > Administration > Additional Drivers, it says that the Broadcom STA driver is "activated but not currently in use." If I uninstall, then reinstall it, I can then find my wireless network, but only by looking under hidden networks,. And I have to do this uninstall/reinstall every session. Kind of a pain.

---

### Post by P4man on 2010-10-29
Unless someone has a better idea; this is where I suggest you try another distro (I give you little chance there) or another OS:

---

### Post by metal_falsetto on 2010-10-29
D'oh. Well, I thank you for your assistance regardless. I'll keep plugging away and report back here if I make any progress.

---

### Post by bkratz on 2010-10-29
Since this is about your chipset, it might be worth looking into

[https://lists.ubuntu.com/archives/kernel-team/2010-September/012675.html](https://lists.ubuntu.com/archives/kernel-team/2010-September/012675.html)

---

### Post by metal_falsetto on 2010-10-29
Thanks for the link; I'll check it out when I get home tonight.

Barring any other solutions, do you guys think that using a USB adapter would work? Not the most ideal or elegant of solutions, but I'm willing to try anything at this point.

---

### Post by P4man on 2010-10-29
If you buy one which is supported by linux, they yeah. Then you will ask which one, and I dont have the answer to that as its usually very tricky to find out what chipset is used in those dongles :(

Before that however, you could find a friend with a laptop with a different mini PCI-E card and swap cards for a test (intel ones are usually well supported), to see if its the card or something else. At this point its totally unclear to me if this is an issue specifically with the driver for your wifi card, or something with PCI-E and/or ACPI power management. If its just the driver, you would much rather buy a different mini PCI-E card than have to use an external dongle.

---

### Post by metal_falsetto on 2010-10-29
I'm so needy! Well, I pulled the trigger anyway and dropped a twenty on this hoodaddy:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156152)

As far as the comments on Newegg go, it seems like it plays nice with newer version of Ubuntu.

That sounds like a good idea, swapping out the card with a friend's. 

Unfortunately, I have no friends.

---

### Post by P4man on 2010-10-29
Wow.. did you actually read those reviews? I didnt see anything about ubuntu (but im sure its in there) but just about everyone complains about really crappy reception and constant drop outs. Well.. good luck anyway :)

---

### Post by metal_falsetto on 2010-10-29
Yeah, I did. I did a search within the reviews for "ubuntu," and there were a number of people who said it worked right out of the box with newer versions. A few people said it was buggy with Jaunty, but one person in particular said they had no problems with newer versions. We'll see, I guess.

---

### Post by metal_falsetto on 2010-11-01
This just in! I'm glad to report that I'm typing this from my Dell 1764 sans ethernet cable or power cord (or USB dongle for that matter)... 

I took your advice and went back to Lucid. It didn't connect at first, but then I went back and modified the blacklist.conf file, as per our previous conversation. Blammo! Connected. 

So apparently it's something funky with 10.10. I'm obviously going to wait to upgrade, but if anybody reads this and wants me to be a guinea pig for their attempted fix, I'll install 10.10 on a new partition and give it a whirl. 

Again, thanks everyone for your assistance... I'm looking at you P4man! C'mere you!

---

