---
title: "How to install a new ACX111 driver?"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by Smaskens on 2005-12-10
Who knows how to install a new ACX111 driver on Ubuntu? I tried it but installation stopped when tried to copy firmware file to /lib/firmware (there are no such folder!). Creation of such folder is easy but probably Ubuntu has the required firmware in other location?

1. First, how to install kernel headers? Driver compilation requires them.
2. I tried to compile and install driver with following instructions, but failed. rolleyes: 

```

cd /usr/src
mkdir acx-20050916
mkdir acx-fw

cd acx-fw
wget [http://www.cmartin.tk/acx/fw.tar.bz2](http://www.cmartin.tk/acx/fw.tar.bz2) (original address in howto didnt work)
tar xjvf fw.tar.bz2
cp fw/acx111_1.2.1.34/tiacx111c* /lib/firmware (? there are no such folder?)

now do
ls /lib/firmware
you should see:
tiacx111c16 tiacx111c17 or tiacx100usb
and maybe some other files

cd ../acx-20050916
wget [http://acx100.erley.org/acx-20050916.tar.bz2](http://acx100.erley.org/acx-20050916.tar.bz2)
tar xjvf acx-20050916.tar.bz2

do: the ` is a back tick.  it's under ~ (no shift)

make -C /lib/modules/`uname -r`/build M=`pwd`

now test the module with:
insmod ./acx.ko

```

Current versions are here, as well the installation instructions:
[http://acx100.erley.org/](http://acx100.erley.org/)
[http://acx100.erley.org/howto.txt](http://acx100.erley.org/howto.txt)
[http://www.cmartin.tk/acx/](http://www.cmartin.tk/acx/)

Here are also general ACX driver installation instructions, however they are a bit too complicated for me :(. Could someone help?
[http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

---

### Post by Smaskens on 2005-12-12
Is there a solution or not? :)

---

### Post by MrCheese on 2005-12-12
Read this : [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

Hope this helps

---

### Post by hamil on 2005-12-12
Well, on the frontpage to houseofcraig.net, it states with beg red warning symbols that:
NOTICE: This guide DOES NOT APPLY to kernel version 2.6.14 or later

So can someone please let me know how to get my acx-111 with wep working flawlessy with Ubuntu?

---

### Post by cptncatholic on 2005-12-31
Any update on this?

I have an Allied Telesyn AT-WCP200G with the TI-ACX111 chipset.
Running Kernel 2.6.12-9-386
[www.houseofcraig.net](www.houseofcraig.net) didn't work because I couldn't get the card to scan or associate with the router.

Peace!
T.C.

EDIT: Scratch that... I decided to just to a fresh install of edubuntu (this is my son's computer for Christmas) and the installer seemed to pick up the wifi card and connect all on its own. So, I just need to remember that more often than not the computer knows what it's doing better than I do.

---

### Post by vasudevank on 2005-12-31
the newer kernels have a lot of pcmcia support built in

---

### Post by eodenns on 2006-01-06
Hi!

I have a DLINK G520+ wifi card, and it has a acx-111 chipset on. During the install of Ubuntu 5.10, everything was detected and installed correctly, it even works with WEP!

I did however manage to destroy the settings for my card when I used the graphic interface for network settings. It no longer worked even if I tried several changes. 

After some searches in the forums I found a correctly written /etc/network/interfaces file, and tried to add the lines missing. The file looks as this now and works: 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map wlan0

# The primary network interface

iface wlan0 inet dhcp
wireless-essid <insert accesspoint SSID here>
wireless-key open <insert wepkey here>
wireless-mode managed

auto wlan0

```
The reason for me to play around with the network settings was that every now and then, the wireless connection went down. I could not find out why or how, but it annoyed me. 

I finally found the soloution for that too, from a post here at ubuntu, and that is to do a script with the following: 
<file: netstart.sh>
```
sudo /etc/init.d/networking stop
sudo modprobe -r acx_pci
sudo modprobe acx_pci
sudo /etc/init.d/networking start
```

I also made a small script, a tcl script, that regularly checks the connection by pinging my accesspoint, and if no answer comes, it runs the above script. I'm well aware that it could be done as a cronjob, but I haven't had time to rewrite the script for such a task just yet. Here is that one: 

<file: keepalive.sh>
```
#!/usr/bin/tclsh

set loop 1
set num_ok 0
set num_fail 0
while { $loop } {
    set ret [catch {exec ping 192.168.0.1 -c 1}]
    if { $ret != 0} {
        incr num_fail
        puts "Script shows connection down after $num_ok times... Restarting network, the $num_fail time"
        set newret [catch {exec ~/netstart.sh}]
        if { $newret == 0 } {
            puts "Network restarted! Continuing script..."
        } else {
            puts "Could not restart network... Exiting..."
            exit
        }
    } else {
        incr num_ok
        puts "Script shows connection up, and all is well, $num_ok times"
    }
    exec sleep 30
}

```

It has worked as a charm for me, and even if it runs every 30 seconds, it's not something that makes my system run slowly!

---

