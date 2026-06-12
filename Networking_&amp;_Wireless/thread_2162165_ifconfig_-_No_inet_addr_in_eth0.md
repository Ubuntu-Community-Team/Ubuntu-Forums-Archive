---
title: "ifconfig - No inet addr in eth0"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by Razor2803 on 2013-07-13
eth0      Link encap:Ethernet  HWaddr 00:0c:29:cb:1f:64  
          inet6 addr: fe80::20c:29ff:fecb:1f64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2669 (2.6 KB)  TX bytes:32197 (32.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19504 (19.5 KB)  TX bytes:19504 (19.5 KB)

---

### Post by TheFu on 2013-07-13
Is this a new system or just a new issue with a formerly working NIC?  Did it break after an update?

**sudo lshw -C network** will show the network hardware that Linux sees.
Is the correct driver loaded?  **lsmod** should show that.  

Which version of Ubuntu?  desktop, server,  or some other special version?  Also, which release?

---

### Post by Razor2803 on 2013-07-13
Its ubuntu-11.04-desktop-amd64 and I am running it on VMware 8.0.1

Here is the output of **lsmod**
```
Module                  Size  Used by
vmhgfs                 63016  0 
vsock                  47686  0 
binfmt_misc            17565  1 
vesafb                 13761  1 
rfcomm                 47694  8 
sco                    18131  2 
bnep                   18308  2 
snd_ens1371            25634  2 
gameport               19652  1 snd_ens1371
l2cap                  53570  16 rfcomm,bnep
snd_ac97_codec        134270  1 snd_ens1371
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96625  2 snd_ens1371,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17113  0 
btusb                  18600  2 
vmw_balloon            12841  0 
psmouse                73535  0 
snd                    67382  11 snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
serio_raw              13166  0 
joydev                 17606  0 
soundcore              12680  1 snd
snd_page_alloc         18529  1 snd_pcm
parport_pc             36959  1 
i2c_piix4              13303  0 
vmci                   77740  2 vmhgfs,vsock
shpchp                 37297  0 
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
mptspi                 22738  2 
usbhid                 46956  0 
mptscsih               44457  1 mptspi
e1000                 111862  0 
hid                    91020  1 usbhid
floppy                 74120  0 
mptbase               102904  2 mptspi,mptscsih
scsi_transport_spi     30630  1 mptspi
vmxnet                 20808  0 
vmw_pvscsi             22699  0 
vmxnet3                45260  0
``` 
and here is the output of **sudo lshw -C network**
```
*-network               
       description: Ethernet interface
       product: 82545EM Gigabit Ethernet Controller (Copper)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 01
       serial: 00:0c:29:cb:1f:64
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list rom ethernet physical logical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k8-NAPI duplex=full firmware=N/A latency=0 link=yes mingnt=255 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:19 memory:c9020000-c903ffff memory:c9000000-c900ffff ioport:2000(size=64) memory:d8400000-d840ffff
```

---

### Post by TheFu on 2013-07-13
I am not an expert on YOUR hardware.  Is that NIC a PRO/1000?  The module is loaded for that - the e1000 line, but it isn't being used for some reason.  Could be that the NIC is failing or starting to fail?  Perhaps reseating it inside the case would help?  

VMware makes 6+ different virtualization products. While it might not matter, being more specific could be helpful. The most current releases will support newer Linux releases better.

Ubuntu 11.04 has been non-supported for over a year.  If you don't plan to update to a new release every April and October, then it would be best to always run an LTS release - 12.04 is the current one.  14.04 will be the next.  Upgrades directly between LTS releases are fairly well supported - no need to load the intermediate releases.  No way would I put a non-supported Linux on the internet. NO WAY.  Just sayin'.

BTW, I'm an LTS release guy - haven't looked at any non-LTS releases since 11.04 burned me with Unity.  8.04, 10.04, 12.04 and 14.04 for me. Most of my VMs run 12.04, but a few servers are on 10.04 still - servers get 5 yrs of support.  It is only since 12.04 that desktops got 5 yrs of patching.

---

### Post by varunendra on 2013-07-14
> **Razor2803 said:**
> Its ubuntu-11.04-desktop-amd64 and I am running it on VMware 8.0.1

Your issue has nothing to do with "Networking". The (virtual) adapter is a generic one and correct driver is loaded, so everything from the 'inside' of the VM is absolutely normal and okay.

Are the "Connect at Power on" and "Connected" checkboxes checked when you turn the VM on? (in VM Network Adapter settings)

What kind of network you are using in the VM ? (NAT, Bridge, Custom,...)

If it is NAT (which I think is default), which virtual adapter it is connected to? Does it exist in /dev directory? If not, you can go to "Edit > Virtual Network Editor" in VMware main window to fix this setting (and much more).

---

