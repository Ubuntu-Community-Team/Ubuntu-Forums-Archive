---
title: "Cant connect to wired network (ARGH!!!); 12.04"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by lanenem on 2013-05-14
I'm at a complete loss AND I have no idea what I'm doing.

Box and network via ethernet was fine.  Moved the box with a new ethernet connection.  Network crapped out.  Moved box back to original location -- wired network still disconnected.

Ran a bunch of scripts (see below) -- nothing worked

Edit connection -- ipv4 -- assigned manual connection, including ip address w/in the range of my router -- appears to connect to network, but cant load any pages; ping 8.8.8.8 = Destination host unreachable

PLEASE HELP!!!

Thank you. 


Scripts run:

_
sudo /etc/init.d/networking restart
__
sudo rmmod tg3
sudo modprobe broadcom
sudo modprobe tg3

sudo rm /etc/modprobe.d/tg3.conf
__
cat << EOF | sudo tee /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
EOF
	Then reboot.
__
sudo rmmod tg3
sudo modprobe broadcom
sudo modprobe tg3
__
sudo route add default gw 121.165.98.1 eth0

---

### Post by Iowan on 2013-05-14
After you added the default gateway (whose IP you may wish to mask), what are the results of **route -n**?

---

### Post by lanenem on 2013-05-15
srry the format is hosed -- im opening to notepad

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

---

### Post by lanenem on 2013-05-16
What if I just formated the drives, wiped everything, and reloaded the OS?

---

### Post by varunendra on 2013-05-16
> **lanenem said:**
> What if I just formated the drives, wiped everything, and reloaded the OS?

Well, that's the 'ultimate solution' to everything ;)

But unless you have already done that, may we take a look at outputs of -
```
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

Also, why did you need to manually create (recreate) the /etc/NetworkManager/NetworkManager.conf file? And is there a particular reason why you put "managed=true" there?
Usually it is "managed=false", although it shouldn't matter if NetworkManager is the only one controlling your network interface.

---

### Post by lanenem on 2013-05-17
> **varunendra said:**
> 
Also, why did you need to manually create (recreate) the /etc/NetworkManager/NetworkManager.conf file? And is there a particular reason why you put "managed=true" there?
Usually it is "managed=false", although it shouldn't matter if NetworkManager is the only one controlling your network interface.

Ultimately, I just copied and pasted every line of code others suggested who had similar problems (which is a PITA when I copy to a flash drive on one comp and then move it to my ubuntu box and paste).  I don't have a specific understanding of why false to true.

But, tx for the suggestion.  I'll copy and paste that ASAP.

---

### Post by praseodym on 2013-05-17
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by lanenem on 2013-05-18
result 1:

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        _

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.88
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


_-server:~$ 
_-server:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

_-server:~$ 
_-server:~$ cat /etc/NetworkManager/NetworkManager.conf

[main]

plugins=ifupdown,keyfile



[ifupdown]

managed=true

_-server:~$ 
_-server:~$ cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

--
result 2:

Destination     Gateway         Genmask         Flags     Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0              UG    0         0              0 eth0
169.254.0.0     0.0.0.0         255.255.0.0       U     1000   0           0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0             0 eth0

---

### Post by varunendra on 2013-05-18
> **lanenem said:**
> 
- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  **State:             connected**
  Default:           yes
  HW Address:        _

  Capabilities:
    Carrier Detect:  yes
    **Speed:           1000 Mb/s**

  Wired Properties
    **Carrier:         on**

  IPv4 Settings:
    Address:         **192.168.1.88**
    Prefix:          24 (255.255.255.0)
    [B]Gateway:         192.168.1.1

    DNS:             192.168.1.1[/B]
..
..
_-server:~$ cat /etc/NetworkManager/NetworkManager.conf
..
[ifupdown]

managed=**[COLOR="#B22222"]true[/COLOR]**
Everything looks good above, although the "managed=true" should by default be "managed=false", but since your /etc/network/interfaces file is not managing the ethernet interface, it doesn't matter.

Now can you ping your gateway?
```
ping -c4 192.168.1.1
```
Also, make sure the IP is not conflicting with any other machines on the network. Just change it if not sure.

And what do you mean when you say you moved it to a different location? Was it a different network or a different ethernet card or just a different location on the same network (connected to same router)?

Sometimes, the firmware of the router/NIC just gets confused, sometimes there are other logical issues like DHCP pool getting full, or IP conflict, etc. In most of such cases, it is usually sufficient to just reboot both the computer and the router (better keep them power off for two or more minutes).

If these don't help, please also post what praseodym asked above your post. The outputs of first three commands may be interesting.

---

### Post by lanenem on 2013-05-19
I moved it to another location on the same network.  Same router (actually tried directly into the router via tested/good cat6 patch).

Network says connected, but cant reach anything.

Here are the results:

ping -c4 192.168.1.1

result:

From 192.168.1.88 icmp_seq=4 Destination Host Unreachable
___
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state

result:

$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:30:67:CD:17:0C

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.88
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


-server:~$ 
server:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

-server:~$ 
-server:~$ cat /etc/NetworkManager/NetworkManager.conf

[main]

plugins=ifupdown,keyfile



[ifupdown]

managed=true

-server:~$ 
-server:~$ cat /var/lib/NetworkManager/NetworkManager.sta


____
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n

result:

ane@__-server:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:230a]
	Kernel driver in use: r8169
-server:~$ 
-server:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
usb_storage            49198  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
bluetooth             180153  10 rfcomm,bnep
ppdev                  17113  0 
snd_hda_intel          33719  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  477763  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mei                    41616  0 
serio_raw              13211  0 
snd                    79041  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lp                     17799  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mac_hid                13253  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
r8169                  62154  0 
-server:~$ 
-server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr **:17:0c  
          inet addr:192.168.1.88  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ** Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:570673 (570.6 KB)
          Interrupt:48 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12715 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1634212 (1.6 MB)  TX bytes:1634212 (1.6 MB)

-server:~$ 
-server:~$ cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 192.168.1.1

###

---

### Post by varunendra on 2013-05-19
> **lanenem said:**
> From 192.168.1.88 icmp_seq=4 **[COLOR="#FF0000"]Destination Host Unreachable[/COLOR]**
Are you sure the IP address is both correct and is not in conflict with another machine on the network?

Can you verify the router/gateway's IP on another machine (ping 192.168.1.1)?

Everything else seems okay. If you are sure the IP/gateway is not problematic, please check the firewall status in Ubuntu -
```
sudo ufw status
```
By default it is "inactive".
Then try -
```
sudo ifconfig eth0 down
sudo ifconfig eth0 up
```

As an aside, your network card is Realtek RTL8111/8168B, for which the correct driver is already included in the kernel (r8169) and is loaded. So tg3 or broadcom or any other drivers are neither required nor would work for your card. It seems you tried some random stuff without realizing what it is meant for.

Did you make any other changes to your system?

**PS:**
Please use code tags to preserve the formatting of the outputs. It makes it easy to read and follow.
If you are saving the outputs in a text file, then opening it on a windows machine, make sure to change the "Line Ending" to "windows" mode. Then while posting, click on # at the top of edit box to auto-generate 'Code' tags, and copy-paste the outputs in-between the tags. Follow the "Code tags example" link in my signature to see an example 'how to'.

---

### Post by Hadaka on 2013-05-19
Hi, please set your IPv4 settings like the screen shot below..
*After you set the correct IPv4 setting
,,power down your computer
        power down you router
next.
        power up the router
        power up the computer

---

### Post by lanenem on 2013-05-19
I can ping 192.168.1.1  And there's no conflict with other device addressed.  I checked (again) by accessing my router -- no conflicts with .88 (or .99, which I tried before).  And thanks for pointing out that the NIC drives are good -- I was considering buying a new card.

Trying the power cycle (again) now.

Thanks.

---

### Post by lanenem on 2013-05-19
No love after setting to auto DHCP and doing the power cycle.

I checked all cables with ye olde trusty network cable tester with tone generator -- cables are fine.

Load 13.04 iso?

---

### Post by varunendra on 2013-05-19
> **lanenem said:**
> I can ping 192.168.1.1  And there's no conflict with other device addressed.  I checked (again) by accessing my router -- no conflicts with .88 (or .99, which I tried before).
I believe you did it all from a different machine?
You did not tell us about ufw status. Is it inactive?

> **lanenem said:**
> Load 13.04 iso?
..or whatever Live CD/USB you may already have. Just to rule-out any possibility that the installed OS may be at fault.

Boot with the Live CD/USB, and see if it picks up an IP via DHCP. If not, try assigning an IP manually to see if it connects then. Let us know if it does or doesn't.

---

### Post by wildmanne39 on 2013-05-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by lanenem on 2013-05-19
Totally sorry peeps.  I'd hosed up the switches and cords.  It was a cable issue.  When I moved the box, i screwed up the cables fm a switch.  

THANK YOU FOR THE ASSISTANCE!!

---

### Post by lanenem on 2013-05-19
CAN i marked this "solved" Mods?

---

### Post by BlinkinCat on 2013-05-19
Hi,

Here's how to mark as solved on your first post -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by varunendra on 2013-05-19
> **lanenem said:**
> Totally sorry peeps.  I'd hosed up the switches and cords.  It was a cable issue.  When I moved the box, i screwed up the cables fm a switch.  

THANK YOU FOR THE ASSISTANCE!!

Whoops!!
No problems at all ! Glad to know that our basics were always telling us the truth. You know, reaffirmed our belief - "Never ignore the fundamentals!" :D

As for marking as [Solved], yes you should do so now. Just follow the link BlinkinCat gave you to see how.

---

