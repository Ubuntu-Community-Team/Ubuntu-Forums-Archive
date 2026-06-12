---
title: "No connectivity after mobo/processor upgrade 10.04"
date: 2012-05-11
forum: Networking &amp; Wireless
---

### Post by kulturloseramerikaner on 2012-05-11
Hello all.

I recently replaced my aging GIGABYTE GA-MA790XT-UD4P / Athlon II board and processor with an Asus P8Z77V Pro and Intel 2600K; the old board had a Realtek 8111C/DL NIC while the new one has an Intel 82579 Gigabit. Since doing this, I cannot find any LAN connection. When I booted into Win 7 I also had this issue, but there was a driver on the disk that came with the board that got me running and it has been OK since. No love on the 'Nix side; I tried stopping and restarting the network manager then noticed there is a folder named "Linux Driver" on the disk, but when you open up the folder and check the readme file it contains, you are treated to a text file that essentially just says "the driver is already in the kernel since 2.6.29." Thanks Intel, fine work!  =D> :rolleyes:
I went to the Intel support site to get the linux driver here: [http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%C2%AE+82579+Gigabit+Ethernet+Controller") 
After unpacking per their destructions and running a *sudo make install* I get the error "*** No rule to make target install. Stop."
It's been a couple days now and it's getting frustrating; what are my next steps please? 

Thanks in advance.

---

### Post by Bucky Ball on 2012-05-11
Have you plugged in an ethernet cable, gotten online and gotten updates? Check 'Additional Drivers' before and after you do this.

You are better to use the driver in the kernel. Can you post the output, from a terminal, of:

```
sudo lshw -C network
iwconfig
```

Input the two commands one at a time. Cheers.

---

### Post by kulturloseramerikaner on 2012-05-12
Yes, I certainly do have the cable plugged in... I was able to get it working for Wintendo; there I can get updates and get online without troubles now, though at first the NIC was not seen by Win either.

Output for the lshw command:
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:f7700000-f771ffff memory:f7735000-f7735ff ioport:f040(size=32)

and 

iwconfig
lo           no wireless extensions.

That second one is weird to me because there *is* a wireless card on this board that came with it; I went ahead and installed it thinking "what the heck, might come in handy" though I certainly have no qualms about removing it if it's creating a conflict.

Thanks again.

---

### Post by Bucky Ball on 2012-05-12
Is this the total output of those commands? Please put terminal output between [code] tags (hit 'Go Advanced' and use the hash # icon). ;)

Anyhow, your wireless interface isn't showing up at all there and don't quite understand about the wireless card. You installed one yourself that came with the machine? From the output you have posted it is not being recognised so now it is not being seen by Ubuntu.

The wireless card may be dead or not installed properly. Perhaps have another look and make sure all is good there.

---

### Post by kulturloseramerikaner on 2012-05-12
Yepp, that is ALL the output I got from the terminal. Output for the lshw command:
```
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:f7700000-f771ffff memory:f7735000-f7735ff ioport:f040(size=32)

```
and 

iwconfig
```
lo no wireless extensions.
```

Recall that I had to type this in from another device by hand; I have zero connectivity with Ubuntu currently. Win 7 did not see the ethernet card either until I installed a particular driver; Intel copped out on me and their "driver" was just a text file saying "it's in the kernel," and I had no luck installing the tarball from their site. Like you said, I'd prefer to use the kernel module if I can just get it to work. As for wireless, this is a desktop. I just want to get the wired connection working first before I start messing with that. I'm perfectly willing to pull it back out if that is what is causing my issues, but I don't think that it is.

---

### Post by Bucky Ball on 2012-05-12
This is where I'm getting a bit confused ... pull what back out? You have installed a wireless card into the machine? If so, it is not working (the fact it is in a PCI slot or anywhere else is not recognised). 

You ethernet controller is showing no driver installed, from the kernel or anywhere else. You might want to give this a go:

[http://www.slickdev.com/2011/08/07/enable-built-in-intel-82579-based-ethernet-card-in-intel-dh61ww-motherboard-under-ubuntu-10-04-server-lts/](http://www.slickdev.com/2011/08/07/enable-built-in-intel-82579-based-ethernet-card-in-intel-dh61ww-motherboard-under-ubuntu-10-04-server-lts/)

... or:

[http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/](http://giantdorks.org/alain/fix-for-non-working-wired-ethernet-on-dell-latitude-e6520-with-intel-82579-based-adapter-running-ubuntu-10-04-lts-lucid/)

... or trawl through here:

[http://au.search.yahoo.com/search;_ylt=A0oGkmFKAa9PqgcAshwL5gt.?p=Intel%2082579%20ubuntu&fr2=sb-top&fr=altavista&rd=r1]("http://au.search.yahoo.com/search;_ylt=A0oGkmFKAa9PqgcAshwL5gt.?p=Intel%2082579%20ubuntu&fr2=sb-top&fr=altavista&rd=r1")

From what I'm reading it seems that card doesn't natively work with the 10.04 LTS kernel, but was introduced to the 10.10 kernel. I had the same problem with my wireless card so I simply upgraded the kernel in 10.04 to the 2.6.38-** kernel and no problem. I could install the driver and all was sweet. I could never get it working on the regular 10.04 kernel (2.6.32-** from memory). I did something similar to this:

[http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa)

---

### Post by kulturloseramerikaner on 2012-05-13
Yes, the wireless card came back out yesterday. Like I said, I came with the mobo and I figured "why not?" thinking that it could be handy when I move in a couple months, before I run cables, etc. It did not help. 

I came across the giantdork website myself yesterday and followed the instructions trying to figure this out. It would seem that before I was trying to run the make one folder too high while following the destructions from Intel; my mistake. But I did get it to run:```

cd /home/hirnrissigermann/Downloads/e1000e-a.11.3/src
~/Downloads?e1000e-1.11.3/src$ sudo make install
```
Then it runs the installer and shows a ton of stuff that I don't have time to type (I'm on another macine by necessity and can't copy/paste), but the last line is:
```
 man -c -P'cat > /dev/null/' e1000e || true
```
Then I run ```

sudo modprobe -r e1000e; sudo modprobe e1000e
```
to load it. I get the 
```
WARNING: All config files need .cong: /etc/modprobe.d/sound, it will be ignored in a future release.
WARNING: All config files need .cong: /etc/modprobe.d/sound, it will be ignored in a future release.
```
I've seen that before. No biggie. After this though, I get a pop-up alert from the network manager saying 
"Wired network 
Disconnected - you are now offline."
The thing I don't get is when I confirm that the module is loaded
```
lsmod | grep e1000e
```
it returns 
```
 e1000e                    187358    0
```
It seems it should be running. The kernel is not the issue, I'm running the latest:
uname -a returns
```
Linux HAL 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:10:32 UTC 2012 x86_64 GNU/Linux
```
I just can't see why I'm still having this issue; the kernel is new enough that it should work just fine, plus the install seems to have worked. Is there something that needs to be done to enable the kernel-native module to run?

---

### Post by Bucky Ball on 2012-05-13
Please post the output of:

```
sudo lshw -C network

```
please. That will show what driver is installed, if there is one. 

Have you restarted or logged out and back in since installing, incidentally?

---

### Post by kulturloseramerikaner on 2012-05-16
This is what it gives me:
```

hirnrissigermann@HAL:~$ sudo lshw -C network
[sudo] password for hirnrissigermann: 
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 04
       serial: c8:60:00:bd:27:bb
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.11.3-NAPI duplex=full firmware=0.13-4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:32 memory:f7700000-f771ffff memory:f7735000-f7735fff ioport:f040(size=32)
hirnrissigermann@HAL:~$ 

```

Thanks

---

### Post by Bucky Ball on 2012-05-16
```
driver=e1000e driverversion=1.11.3-NAPI duplex=full firmware=0.13-4
```Well, the driver seems to be loaded with firmware and theoretically you're good to go, but it ain't going.

How are you getting the IP address? Is it being served via DHCP from the router or have you set a static one on the local machine or for your machine on the router?

---

### Post by kulturloseramerikaner on 2012-05-16
> **Bucky Ball said:**
> ```
driver=e1000e driverversion=1.11.3-NAPI duplex=full firmware=0.13-4
```Well, the driver seems to be loaded with firmware and theoretically you're good to go, but it ain't going.

That is correct. I can't figure out why it's not cooperating...


> **Bucky Ball said:**
> How are you getting the IP address? Is it being served via DHCP from the router or have you set a static one on the local machine or for your machine on the router?

I've been trying to use the defaults with DHCP from the router. I quad boot this machine, and have several other devices on my network, so I let that happen dynamically; I've had issues in the past with static IP.

---

### Post by kulturloseramerikaner on 2012-05-17
Well, I came across this on another forum with regards to the e1000e module:
"Please try booting the kernel with the```

 pcie_aspm=off 
```
kernel parameter."

It worked for the guy that was having the problem and I'd like to give it a go, but I need to ask a n00b question now. I'm quad-booting Arch, Ubuntu, Win 7, and Win XP; How would I set a boot kernel parameter in GRUB2 so that it applies only to Ubuntu?

Thanks.

---

### Post by Bucky Ball on 2012-05-17
Well, which system is running the show? Are you using the grub from Ubuntu or another OS? If you want to alter the grub list of OSs when you boot, which OSs grub do you apply your changes to?

To try out the command to see it works, though, when you hit the grub list where you select the OS/kernel to boot, select your Ubuntu, hit 'e' to edit, find the line that ends in 'quiet splash' or either of those words, and add 'pcie_aspm=off' to the end of that. Hit ctl+x to continue with the boot with your changes in effect. They will be lost on the next reboot so ... 

If it works you could then make it permanent by booting into the Ubuntu install, editing /etc/default/grub, sudo update-grub, then restart and boot into the OS that is running the show and sudo update-grub there. Easy.  ;)

---

### Post by kulturloseramerikaner on 2012-06-05
OK, been out of the country for the past week or two but....

Got back, gave it a try, and no luck. Is there anything else I should try?

---

