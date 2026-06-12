---
title: "Intel Wireless 2200BG"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by LinuxforHumans on 2009-07-25
Hey all, 

I'm pretty new to Linux, and I'm having lots of trouble getting my wireless to connect. I can connect through Ethernet, but I've been trying for days to get wireless up.

I found some frequently requested outputs. Here they are and hope they help...

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
sudo lshw -C network
  *-network:0
       description: Ethernet interface
       product: NetXtreme BCM5705_2 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 03
       serial: 00:e0:b8:81:d7:b5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.97 duplex=full firmware=5705-v3.26 ip=192.168.1.10 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:d8:3d:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

```

I hope this is helpful -- Let me know what else is necessary.

---

### Post by coffeecat on 2009-07-25
For most people the Intel 2200BG wireless chipset has worked right out of the box in every version of Ubuntu for the last couple of years. But I see that you tagged this thread 'other OS'. Which Linux distro are you using? If Ubuntu, which release and which desktop, i.e. Ubuntu/gnome, Kubuntu/KDE or Xubuntu/Xfce?

What have you tried to do to connect wirelessly?

If you are running a recent version of Ubuntu (gnome), simply click on the network manager icon (on the top panel, near the right) and that should show you all the wireless networks in range. Does your network show?

---

### Post by LinuxforHumans on 2009-07-25
I am actually using BackTrack 4, which is now based on Ubuntu (formerly it was based on Slackware). It uses KDE, so no gnome.

As far as connecting wirelessly, I've tried DHCP, as well as static IP, WEP (Passphrase) and unencrypted. I was using wicd, but I was having troubles with it so I installed KNetworkManager, which didn't really fix much.

---

### Post by coffeecat on 2009-07-25
Back Track may be based on Ubuntu, but it's a specialist distribution designed for a specialised user group interested in security testing. Not your average home/SOHO desktop operating system, and clearly a very different animal from the official Ubuntu family if it doesn't come with knetworkmanager in a default install.

I doubt whether many (if any) in this forum will have any experience of BackTrack, so you may be better off asking in BackTrack's own user forum.

---

### Post by LinuxforHumans on 2009-07-25
Alright, thanks anyway, I'll check over there.

On another note, would you happen to know why a 'make' command wouldn't work?

I downloaded a driver and I'm trying to use 'make' within its directory, and this is what I get:

```
make
make -C /lib/modules/2.6.29.4/build M=/home/andrew/rtl-wifi modules
make: *** /lib/modules/2.6.29.4/build: No such file or directory.  Stop.
make: *** [modules] Error 2
```

---

### Post by LinuxforHumans on 2009-07-25
Anyone?

---

### Post by lswb on 2009-07-25
Do you really have a directoty named /lib/modules/2.6.29.4/build  ?

Usually it will be something like /lib/modules/2.6.29.4-generic/build, or whatever suffix is correct for you system instead of "-generic"

---

### Post by martinbaselier on 2009-07-26
As far as I can see, the driver version, the firmware and all other settings are equal to the version on my laptop. Except that it's not connected. 

Why don't you try an ubuntu live cd or live usb (unetbootin is a good tool for creating one), see if it works and look for differences. 

You could also download an ubuntu kernel an test with that. It's easier than compiling. To compile a kernel, or a kernel module, you would need to install the headers for the current kernel. 

Unless you want to hack the driver, there is not much use in downloading source files and hacking them.  

try:
iwlist eth1 scan

to see if it detects any networks. If so, you can reasonably presume the card is working correctly and you need to make the right settings to create a connection. 

You can create a connection with 
sudo iwconfig eth1 essid yourSSID
sudo dhclient eth1
if it's an unencrypted network.

---

### Post by LinuxforHumans on 2009-07-26
This is very strange...
I physically went into my /lib/modules/2.6.29.4 directory to see whether there was a 'build' file, and there appears to be a shortcut to a file called build -- but the filename is italicized, and it contains no information. The file size is 0 bytes, and clicking on it produces the error:

```
An error occurred while loading **file:///lib/modules/2.6.29.4/build:**

The file or folder file:///lib/modules/2.6.29.4/build does not exist.
```

There is another folder in my modules directory, 2.6.25-2-386, and within that is another directory called build. I'm guessing that's the one it wants to use, but how can I point it there? All I did was type 'make' and it chose to use the wrong folder.

martinbaselier, using **sudo iwlist eth1 scan**:
eth1    No scan results

**sudo iwlist wlan0 scan**:
wlan0   Failed to read scan data : Operation not permitted.

And that was using sudo.

---

### Post by martinbaselier on 2009-07-26
There should be a symbolic link on that location:
Here's what it shows on my laptop:
```

ls /lib/modules/`uname -r`/build -al
lrwxrwxrwx 1 root root 40 2009-06-22 18:25 /lib/modules/2.6.28-13-generic/build -> /usr/src/linux-headers-2.6.28-13-generic

```
ln -s is the command to create symbolic links.

---

### Post by LinuxforHumans on 2009-07-26
This is what I get:
ls /lib/modules/`uname -r`/build -al
```
ls: cannot access /lib/modules/uname -r/build: No such file or directory
```

---

### Post by LinuxforHumans on 2009-07-26
Any ideas?

---

### Post by martinbaselier on 2009-07-26
Did you copy my command to the terminal or did you type it yourself? Try copying it and pasting it into the terminal. You need to use the backward ` and not the normal '

in your case that would be:
ls /lib/modules/2.6.29.4/build -al

---

### Post by LinuxforHumans on 2009-07-26
Oh! Yes, that gave me an output -- I was wondering about those quote marks. This was my output:

```
ls /lib/modules/`uname -r`/build -al
lrwxrwxrwx 1 root root 14 2009-07-07 01:07 /lib/modules/2.6.29.4/build -> /usr/src/linux
```

What can I do with this then, to fix my 'make' command?

---

### Post by LinuxforHumans on 2009-07-27
I'd really like to know what's wrong with it, since I need to use 'make' to install a driver.

---

### Post by martinbaselier on 2009-07-27
And do you have a /usr/src/linux directory ?

Edit: /usr/src/linux is a link on my machine. 

It is however outdated (link shows up red, meaning the target no longer exist)

---

### Post by LinuxforHumans on 2009-07-27
No, I don't have a /usr/src/linux directory... :confused:

I have:
/usr/src/linux-headers-2.6.25-2-386
/usr/src/linux-OLDVERSION.1248555870
/usr/src/linux-ports-headers-2.6.25-2
/usr/src/linux-source-2.6.29.4
/usr/src/rpm

---

### Post by martinbaselier on 2009-07-27
You would need current headers. 
sudo apt-get install linux-headers-`uname -r`
then you can use ln to create correct symbolic link
ln -s TARGET LINKNAME

Than you can build a kernel, but I don't think it will help.

I've been looking to the ipw2200 settings today for a different problem. 
I have a feeling some settings for your driver are set incorrectly.

Does
cat /etc/modprobe.d/* | grep ipw2200
show anything?

---

### Post by LinuxforHumans on 2009-07-27
I've decided to use a USB wireless card, and I'm trying to install the Realtek RTL8185 drivers. I purchased it a while ago, and since the Broadcom was giving me problems I decided to give this a shot.

I found a great guide for it here:
[http://gajon.org/installing-realtek-rtl8185-wireless-card/](http://gajon.org/installing-realtek-rtl8185-wireless-card/)

And I get up to the part where I need to use 'make', and then I can't proceed.

> You would need current headers.
sudo apt-get install linux-headers-`uname -r`
then you can use ln to create correct symbolic link
ln -s TARGET LINKNAME

Once I do **sudo apt-get install linux-headers-`uname -r`**, what's that about setting the symbolic link? What would the target linkname be set as?

---

### Post by martinbaselier on 2009-07-27
It's the intel driver, not broadcom we're talking about. It's a strange problem of the distribution you are using. I'd advise you to try using ubuntu first and try again when you're more used to linux. Then the settings for the headers wil be correct by default. 

The target would be the location of the headers, on jaunty this is :

ls /usr/src/linux-headers-2.6.28-13/

I wish you good luck with realtek :)

---

### Post by LinuxforHumans on 2009-07-27
So the command would be something like **ln -s /usr/src/linux-headers-2.6.28-13/** ?

---

### Post by martinbaselier on 2009-07-27
You are missing the name of the link there. 

Is 28-13 your current kernel? 
I think it's 2.6.29.4 in your case (type : **uname -r**)

So it would probably be :

ln -s /usr/src/linux-headers-2.6.29.4/ /lib/modules/2.6.29.4/build

you probably need to **rm /lib/modules/2.6.29.4/build** first though

---

### Post by LinuxforHumans on 2009-07-27
Okay,

Well I followed these steps -- 

[B]rm /lib/modules/2.6.29.4/build
sudo apt-get install linux-headers-`uname -r`
ln -s /usr/src/linux-headers-2.6.29.4/ /lib/modules/2.6.29.4/build[/B]

(All of which executed successfully, thanks.)

And then I tried to 'make' inside of the driver directory, and got the following:
```
make -C /lib/modules/2.6.29.4/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.29.4'
/usr/src/linux-headers-2.6.29.4/arch/x86/Makefile:41: /usr/src/linux-headers-2.6.29.4/arch/x86/Makefile_32.cpu: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.29.4/arch/x86/Makefile_32.cpu'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.29.4'
make: *** [modules] Error 2

```

:cry:

EDIT: By the way, I've been referring to this for the actual installation process for this driver (RTL8185): [http://rtl-wifi.sourceforge.net/wiki/Installing](http://rtl-wifi.sourceforge.net/wiki/Installing)
I'm at the point where I have the folder on my desktop, but I can't use 'make' inside of it because of that error.

EDIT 2: I noticed the line **"/usr/src/linux-headers-2.6.29.4/arch/x86/Makefile:41"** ...arch? Does it think I'm using Arch Linux?

EDIT 3: Just as a test I ran these commands:
**cat /etc/modprobe.d/* | grep ipw2200**
```
cat: /etc/modprobe.d/arch: Is a directory
options ipw2200 associate=0
```

**cat /etc/modprobe.d/* | grep rtl8185**
```
cat: /etc/modprobe.d/arch: Is a directory
```

---

### Post by LinuxforHumans on 2009-07-27
Okay -- Here's something weird -- I'm connected wirelessly! :D I don't know how it happened, but here I am, browsing wirelessly, using my USB wireless card.

But only on an unencrypted network. Still can't connect to my own encrypted home network, using WEP. I'm using wicd, and it gets stuck at "Authenticating..."

What would cause it to not connect on an encrypted network? The passphrase is definitely correct.

EDIT: After reboot, I've tried the following:
**sudo iwconfig wlan0 essid *MyEssid* key s:*MyKey***

**sudo dhcpcd wlan0**

Output:
```
err, wlan0: timed out
err, wlan0: lease information file `/var/lib/dhcpcd/dhcpcd-wlan0.info` does not exist.
warn, wlan0: using IPV4LL address 169.xxx.xxx.xxx
dhcpcd.sh: interface wlan0 has been configured with new IP=169.xxx.xxx.xxx
```

And I'm not connected. :confused:

---

