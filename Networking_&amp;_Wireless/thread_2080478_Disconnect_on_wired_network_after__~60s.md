---
title: "Disconnect on wired network after  ~60s"
date: 2012-11-04
forum: Networking &amp; Wireless
---

### Post by mnhg on 2012-11-04
Hi,  

I just installed a fresh ubuntu (ubuntu-12.10-server-amd64.iso) in a VMware vm. Beside changing the language/keylayout to German, I only disabled DHCP and assigned a static IP. Furthermore I installed openssh. (I changed nothing after installation.) Now I discovered that I get disconnect after being 60 second inactive in my SSH client. But not only the SSH connection is closed, the whole network seems down. If I ping the gateway from the server the first 7 packets get lost and afterwards the connection is reestablished and I could also reconnect via SSH.

I'm neither very familiar with ubuntu nor networking, so has anybody an idea where the problem is, and how to fix it.

Please feel free to ask if there are further informations required.

Thanks,
Martin


**/etc/networks/interfaces:**
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.115.20
        netmask 255.255.255.0
        network 192.168.115.0
        broadcast 192.168.115.255
        gateway 192.168.115.100
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.115.100
        dns-search FOOBAR

```

---

### Post by mnhg on 2012-11-04
Do you need any other information? 

Any hint would also be fine.

---

### Post by varunendra on 2012-11-05
Please provide the details of the setup. Particularly -

[LIST]
[*]versions of host and vmware,
[*]virtual network type (NAT, Bridge or Host-only?),
[*]where are you accessing the VM from,
[*]output of following from Ubuntu VM (when the connection freezes) :
[/LIST]
```
lsb_release -d
uname -mr
lshw -C network
lsmod
ifconfig
```

---

### Post by mnhg on 2012-11-06
Windows 7 Pro 64 bit
VMPlayer 4.0.3 (Bridged, access direct from host)
Ubuntu 12.10
3.5.0-17-generic x86_64

```

  *-network
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0c:29:da:dd:a2
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full ip=192.168.115.20 latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:c9020000-c903ffff memory:c9000000-c900ffff ioport:2000(size=64) memory:d8400000-d840ffff

Module                  Size  Used by
coretemp               13400  0
ghash_clmulni_intel    13180  0
aesni_intel            51037  0
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17208  1 aesni_intel
ppdev                  17073  0
vmw_balloon            12673  0
microcode              22803  0
psmouse                95552  0
serio_raw              13215  0
snd_ens1371            25302  0
gameport               15544  1 snd_ens1371
snd_rawmidi            30512  1 snd_ens1371
snd_seq_device         14497  1 snd_rawmidi
snd_ac97_codec        134272  1 snd_ens1371
ac97_bus               12766  1 snd_ac97_codec
snd_pcm                96580  2 snd_ens1371,snd_ac97_codec
vmwgfx                121398  0
snd_timer              29425  1 snd_pcm
snd                    78734  6 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm,snd_timer
soundcore              15047  1 snd
ttm                    83595  1 vmwgfx
snd_page_alloc         18484  1 snd_pcm
joydev                 17457  0
i2c_piix4              13167  0
drm                   275528  2 vmwgfx,ttm
parport_pc             32688  1ext2                   72880  1
mac_hid                13205  0
shpchp                 37108  0
lp                     17759  0
parport                46345  3 ppdev,parport_pc,lp
hid_generic            12493  0
usbhid                 46947  0
hid                   100366  2 hid_generic,usbhid
e1000                 114778  0
mptspi                 22529  2
mptscsih               40289  1 mptspi
mptbase               101919  2 mptspi,mptscsih
floppy                 69452  0


eth0      Link encap:Ethernet  HWaddr 00:0c:29:da:dd:a2
          inet addr:192.168.115.20  Bcast:192.168.115.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feda:dda2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73901 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:102610330 (102.6 MB)  TX bytes:2379899 (2.3 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:448 (448.0 B)  TX bytes:448 (448.0 B)






```

---

### Post by varunendra on 2012-11-06
Try disabling IPv6 by adding the following lines to your '/etc/sysctl.conf' file :
> # disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
Easy way to do this with a single command :
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```

Also, be aware that the [lifespan]("https://wiki.ubuntu.com/Releases") of 12.10 server is only 1.5 years (upto April 2014) while that of 12.04 is 5 years (upto April 2017) because it is an LTS (Long Term support). LTS versions are also supposed to be more stable and less buggy, while all the experimental (thus often buggy) things are done with interim releases.

So whether you are just learning or intend any serious usage, using 12.04 is recommended.

---

### Post by mnhg on 2012-11-06
Problem still exists.

Any other ideas before I reinstall the system? (with 1204 ofcourse :) )

---

### Post by varunendra on 2012-11-06
> **mnhg said:**
> Problem still exists.

Any other ideas before I reinstall the system? (with 1204 ofcourse :) )
None :(
But if we have to dig deeper, I'd prefer to do so with the one which is going to stay longer with us. :)

---

### Post by mnhg on 2012-11-06
> **varunendra said:**
>  I'd prefer to do so with the one which is going to stay longer with us. :)

Blackmail! :)

Seriously, I guess I can't contribute much to the forum, except for more problems. 

I'm a pretty good software engineer and usually like to solve problem, but an OS should simply work, especially when I try to set up a Git/CI server :)

Maybe I find some time at the weekend and I will try to reinstall my VM.

---

### Post by varunendra on 2012-11-06
> **mnhg said:**
> Blackmail! :)Oh no..! Not at all !!
In fact, if the 'down'-grading didn't fix the problem, I'd be already out of wits.

I just noticed a post in a thread I replied to, where the OP has reported that his problem (similar, but not same as yours) 'seems' to have been solved by removing VMware server (which he wasn't using anyway). So I'm wondering if it is some new compatibility bug between vmware and ubuntu. Here's the thread : [http://ubuntuforums.org/showthread.php?t=2080326](http://ubuntuforums.org/showthread.php?t=2080326)

Scratching your head? :confused: Me too ;)

But if you wanna try, I'd suggest to export the vm to an open format and try  it with VirtualBox - with vmware network removed or disabled.

Although the problem is interesting and I have Win7 Ultimate installed in my laptop, but don't remember when I last logged into it, so also don't remember if I have VMware installed in it to experiment with :)
On my Ubuntu part, I have VirtualBox installed and running happily.

---

