---
title: "WiFi problem"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by LinLou on 2009-08-05
Hello,

I am having a problem on activating my wireless since the button that turns on/off the wireless is a touch button and not a normal one + it does not work if i try to push it. My PC is a HP pavilion dv5-1012ea and my wireless card is an Intel PRO/Wireless 4965AGN Network Connection. Also i have not set up any drivers for the wireless card. Any suggestions on how can i make my wireless work? 

Thanks!

P.S. I also do not have the ability to enable the wireless from the connections. I can enable and disable only the wired network.
[B][SIZE=1]
[/SIZE][/B]

---

### Post by Crafty Kisses on 2009-08-05
Now from what I understand, these cards should work if you're using an up to date kernel, but I think the **compat-wireless **package should work. Alright so first you want to grab compat-wireless, so run the following:
```
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Once you have grabbed that package, you should untar it, you can do this by running:
```
tar xvjf compat-wireless-2.6-stable/v2.6.30/compat-wireless-2.6.30.tar.bz2
```
Now in order to actually successfully build this package and compile it from source, you may need the "build-essential" package, so you can grab that by running as root:
```
apt-get install build-essential
```
Now you need to navigate to the compat-wireless folder by running:
```
cd /home/username/Desktop/compat-wireless-*
```
Remember replace **"username"** with your actual username, it is case sensitive. Now once you're in the directory, you need to type:
```
ls
```
Make sure everything is in the folder that you need, now you can actually go with the initial compile, you can run the following in order:
```
make
sudo make install
```
Now, if you have a existing compat-wireless driver, you may want to unload the driver, so you can run:
```
sudo make unload
```
Now if there is an actual problem with compat-wireless, you can remove it by running in the compat-wireless directory:
```
make uninstall
```
That should get your wireless card up and running.

---

### Post by LinLou on 2009-08-06
Sorry i forgot to tell you that i am using Ubuntu 9.04 

:P

---

### Post by LinLou on 2009-08-06
Ok i did what u told me.. and i think that the installation was successful. But i see no difference in the wireless. I still cant enable it. 

If i use iwconfig i get 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

Any Ideas??? :)

---

### Post by superprash2003 on 2009-08-06
also post output of **sudo iwlist scanning**

---

### Post by LinLou on 2009-08-06
Here it is.. 

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

---

### Post by LewRockwell on 2009-08-06
multiple threads, same issue...

[http://ubuntuforums.org/showthread.php?t=1232070](http://ubuntuforums.org/showthread.php?t=1232070)

would ask moderators to combine thread...

so we don't end up with two sets of people working on the same trouble-call...

.

---

### Post by martinbaselier on 2009-08-06
@Linlou
FYI: 
The output from iwconfig shows your card is on. It's just not associated to a wireless network. (when it would be off, it would show Tx-Power=off)

iwscanning shows it can't find any networks. The problem might be driver related. I'm wondering what kind of driver you have installed. 

Please post the output of:
**sudo lshw -c network**

---

### Post by LinLou on 2009-08-06
Sorry for the mixing up in the threads.. i saw later that there was a specific part for Wireless problems.

&

The output is 

 *-network               
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:c7:c4:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:c4:4c:6b
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.133 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 36:1b:e2:31:4a:e4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

