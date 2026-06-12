---
title: "Strange networking problem"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by simion314 on 2011-11-12
Hi all, i am having a strange problem and i need some help to make it clear what component is the problem.
I am running Kubuntu 11.10 64 bit but I also have a kubuntu 11.04 on other partition(i never upgrade so i keep a OS as a backup).
All worked fine in 11.10 until i got a wireless router,i use the router with LAN and all is fine until email application will stop working,so the application(KMail,thunderbird and gmail plasmoid) work fine and after a while will stop working,I did nmot noticerd any pathern, it seems to be late in the night and in the morrning when i boot the system.
I tried to ifconfig down/uo the eth0, run dhclient eth0 , rebooting but it will not solve the problem.
I booted in 11.04 and there it worked, and i discovered that if i reboot 11.10 will not work but if after rebooting 11.10 i boot in 11.04 then reboot and start 11.10 all will be fine.

In 11.04 i am missing network manager(I removed it) but I am not sure this is important, also the problem will happen once a day so I can't make many tests, i am laning to remove network manager and see if tomorrow the problem is fixed.

I enabled all the stuff in firewall of the router(and mail works most of the time so I think is not a closed port), when the problem is pressent browser works, torrent works fine.

I need some hints on what is gong on here, some tests to do to izolate the component with the problem.
Thx

---

### Post by praseodym on 2011-11-12
Hi,

please show

```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
ifconfig -a
lsmod
```

---

### Post by simion314 on 2011-11-12
> **praseodym said:**
> Hi,

please show

```
lspci -nnk | grep -iA2 net
cat /etc/network/interfaces
ifconfig -a
lsmod
```

Hi, thx for the reply, gere is the result when all is fine, I will try to get the output also when the problem is active

```

$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
        Kernel driver in use: r8169
simi@simi-System-Product-Name:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

simi@simi-System-Product-Name:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 20:cf:30:c1:e6:0d  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fec1:e60d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5234086 (5.2 MB)  TX bytes:481041 (481.0 KB)
          Interrupt:47 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8488 (8.4 KB)  TX bytes:8488 (8.4 KB)

simi@simi-System-Product-Name:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
dm_crypt               23199  0 
binfmt_misc            17540  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
joydev                 17693  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_via      71209  1 
ppdev                  17113  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
fglrx                2929009  39 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  0 
psmouse                73882  0 
serio_raw              13166  0 
sp5100_tco             13791  0 
k10temp                13166  0 
shpchp                 37345  0 
soundcore              12680  1 snd
parport_pc             36962  1 
edac_mce_amd           23709  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_piix4              13301  0 
asus_atk0110           18078  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
wmi                    19256  0 
r8169                  52788  0 
pata_atiixp            13164  0 
ahci                   26002  4 
libahci                26861  1 ahci


```

---

### Post by praseodym on 2011-11-12
Install the module r8168 for this card (r8169 often doesnt work properly):
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2
tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
sudo modprobe -rfv r8169
sudo ./autorun.sh
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```
If "sudo ./autorun.sh" produces errors, try it via:
```
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
```
instead.

---

### Post by simion314 on 2011-11-13
> **praseodym said:**
> Install the module r8168 for this card (r8169 often doesnt work properly):
```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
wget http://r8168.googlecode.com/files/r8168-8.026.00.tar.bz2
tar xvf r8168-8.026.00.tar.bz2
cd r8168-8.026.00/
sudo modprobe -rfv r8169
sudo ./autorun.sh
sudo modprobe -v r8168
sudo depmod -a
sudo update-initramfs -u
```
If "sudo ./autorun.sh" produces errors, try it via:
```
sudo make
sudo cp src/r8168.ko /lib/modules/$(uname -r)/kernel/drivers/net/
```
instead.

Hi, i tried but it fails to load the module, it can't find it

```

simi@simi-System-Product-Name:/lib/modules/3.0.0-12-generic/kernel/drivers/net$ ls
3c59x.ko     benet        cxgb4vf     ethoc.ko      ixgbevf        netconsole.ko   pppox.ko        sfc            sunhme.ko        vxge
8139cp.ko    bna          de600.ko    fealnx.ko     jme.ko         netxen          ppp_synctty.ko  sis190.ko      tehuti.ko        wan
8139too.ko   bnx2.ko      de620.ko    forcedeth.ko  ks8842.ko      niu.ko          pptp.ko         sis900.ko      tg3.ko           wimax
8390.ko      bnx2x        defxx.ko    hamachi.ko    ks8851.ko      ns83820.ko      qla3xxx.ko      skfp           tlan.ko          wireless
acenic.ko    bonding      dl2k.ko     hamradio      ks8851_mll.ko  pch_gbe         qlcnic          skge.ko        tokenring        xen-netback
amd8111e.ko  bsd_comp.ko  dnet.ko     hp100.ko      ksz884x.ko     pcmcia          qlge            sky2.ko        tulip            xen-netfront.ko
appletalk    caif         dummy.ko    ifb.ko        macvlan.ko     pcnet32.ko      r8168.ko        slip.ko        typhoon.ko       yellowfin.ko
arcnet       can          e1000       igb           macvtap.ko     phy             r8169.bak       smsc9420.ko    usb
atl1c        cassini.ko   e1000e      igbvf         mdio.ko        plip.ko         rionet.ko       starfire.ko    veth.ko
atl1e        chelsio      e100.ko     ipg.ko        mlx4           ppp_async.ko    rrunner.ko      stmmac         via-rhine.ko
atlx         cnic.ko      enic        irda          myri10ge       ppp_deflate.ko  s2io.ko         sundance.ko    via-velocity.ko
atp.ko       cxgb3        epic100.ko  ixgb          natsemi.ko     ppp_mppe.ko     sb1000.ko       sungem.ko      virtio_net.ko
b44.ko       cxgb4        eql.ko      ixgbe         ne2k-pci.ko    pppoe.ko        sc92031.ko      sungem_phy.ko  vmxnet3
simi@simi-System-Product-Name:/lib/modules/3.0.0-12-generic/kernel/drivers/net$ sudo modprobe -v r8168
[sudo] password for simi: 
FATAL: Module r8168 not found.


```

I reloaded the other driver from the backup and after that the email worked, so next time I will try to unload and reloading the module a few times and see if it helps with the emails

---

### Post by praseodym on 2011-11-13
Tried a reboot?

---

### Post by simion314 on 2011-11-13
> **praseodym said:**
> Tried a reboot?

Yes, after reboot I had no notwrpking at all, as I said i copied back the old .ko and load that module,make worked fine so I have no idea why it can't load that driver(i am not sure why a driver would cause the mail problem)

---

