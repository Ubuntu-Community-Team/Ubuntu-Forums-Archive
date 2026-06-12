---
title: "No wired internet connection"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by drilltotheheavens on 2012-12-17
Hello, Complete linux noob here. I just built a pc and successfully  installed ubuntu 12.10. However, my  computer is not detecting the ethernet cable I plugged in.

> **Cheesehead said:**
> In a terminal, try 'lspci -v' to see if the ethernet port has a driver assigned.

03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
Subsystem: Giga-byte Technology Device e000
Flags: bus master, fast devsel, latency 0, IRQ 11
Memory at f7d00000 (64-bit, non-prefetchable) [size=256K]
I/O ports at d000 [size=128]
Capabilities: <access denied>

> **Cheesehead said:**
> Then try 'dmesg | grep eth' to see if the  kernel detected the hardware and assigned an eth port to it.

Nothing displayed in terminal.

> **Cheesehead said:**
> Finally, try 'ifconfig -a' to see of the eth* port is configured at all.

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:224 errors:0 dropped:0 overruns:0 frame:0
TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:18400 (18.4 KB) TX bytes:18400 (18.4 KB)

> **Cheesehead said:**
> It means that the hardware is recognized and a driver is assigned (good).
It means that no eth* interface is created (not good). Only the loopback interface was created.

What's telling me that the driver was successfully installed?

> **Cheesehead said:**
> Unplug the network cable, wait about 10  seconds, then plug in the  network cable. Then run the command 'dmesg |  tail -n10' and post the  result here.

[    3.246843] type=1400 audit(1355396781.949:7): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper"  pid=832 comm="apparmor_parser"
[    3.246957] type=1400 audit(1355396781.949:8): apparmor="STATUS"  operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script"  pid=833 comm="apparmor_parser"
[    3.247008] type=1400 audit(1355396781.949:9): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser"  pid=830 comm="apparmor_parser"
[    3.247018] type=1400 audit(1355396781.949:10): apparmor="STATUS"  operation="profile_load"  name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrappe  r//chromium_browser" pid=832 comm="apparmor_parser"
[    3.479620] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[    3.479729] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[    3.479807] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[    3.479858] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[    3.479944] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[    3.479988] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14

> **Cheesehead said:**
> Also, take a look at  /etc/udev/rules.d/70-persistent-net.rules (yours  might not be '70-').  If there is anything in that file, please post  it.

Don't know how to do that.

> **dannyboy79 said:**
> check to see if the module is loaded for that chipset

sudo lsmod | grep e1000e

Nothing displayed in terminal.

I have seen advice elsewhere for similar problems, however please keep in mind that I do not have any computer that has Linux and is connected to the internet.

Thanks in advance for your help.

---

### Post by chili555 on 2012-12-17
> What's telling me that the driver was successfully installed?
Everything we see tells us the driver was *NOT* successfully installed. It wasn't because the Atheros AR8161 is a relatively new device for which there is no driver built in to the kernel. We'll have to compile one from scratch. Fun!

We need a bit more information. Please post:```
lspci -nn | grep 0200
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by drilltotheheavens on 2012-12-17
```
lspci -nn | grep 0200
```
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)

---

### Post by chili555 on 2012-12-17
> Atheros Communications Inc. AR8161 Gigabit Ethernet [[COLOR="Red"]1969:1091[/COLOR]]Your device requires the driver alx. This post describes how to get the prerequisites without internet access: [http://ubuntuforums.org/showpost.php?p=12206899&postcount=6](http://ubuntuforums.org/showpost.php?p=12206899&postcount=6)

Then download the compat wireless package here: [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.6/compat-wireless-3.6.8-1-snpc.tar.bz2)

Drag and drop the file to the desktop of the Ubuntu machine. Open a terminal and do:```
cd Desktop
tar -xf compat-wireless-3.6.8-1-snpc.tar.bz2
cd compat-wireless-3.5.1-1-snpc
./scripts/driver-select alx
make
sudo make install
sudo modprobe alx
```Your ethernet should now be working. If you get stuck, please post back and I'll be happy to help.

---

### Post by drilltotheheavens on 2012-12-21
[Following your instructions]("http://ubuntuforums.org/showpost.php?p=12206899&postcount=6") to install the build essentials, I came across this error.

```

dpkg: error processing gcc (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libc6-dev:amd64:
 libc6-dev:amd64 depends on libc6 (= 2.15-0ubuntu10.2); however:
  Version of libc6:amd64 on system is 2.15-0ubuntu20.
 libc6-dev:amd64 depends on libc-dev-bin (= 2.15-0ubuntu10.2); however:
  Version of libc-dev-bin on system is 2.15-0ubuntu20.

```

It seems that the current system on my computer is more up-to-date than the ones you are suggesting I download. Will downgrading certain packages create any compatibility issues?

---

### Post by chili555 on 2012-12-21
In Linux-land, August is a while ago an there have been several rounds up updates since then. I would install the later versions of the packages in question. Post back if you need more exact instructions.

---

