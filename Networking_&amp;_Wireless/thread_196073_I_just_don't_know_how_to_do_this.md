---
title: "I just don't know how to do this"
date: 2006-06-13
forum: Networking &amp; Wireless
---

### Post by henkk78 on 2006-06-13
How do I setup my wireless card? (SENAO, based on Prism 2 chipset methinks)

'sudo cardctl ident' returns the following:

Socket 0:
  product info: "INTERSIL", "HFA384x/IEEE", "Version 01.02", ""
  manfid: 0x0156, 0x0002
  function: 6 (network)

(someone else told me to type in cardctl ident, the only command line thing i know in linux is 'ifconfig', which doesn't show up any wlan interface)

Is there a HOWTO perhaps on how to install my wireless network card? 

Henk

---

### Post by Imre Mehesz on 2006-06-13
first try here. it helps a lot:

[http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide)


--
eMzMiM

---

### Post by SnappyCrunch on 2006-06-13
What's your card's model number? Is it a PCI, miniPCI or Cardbus card? What are the outputs of both 'ifconfig' and 'iwconfig'?

---

### Post by henkk78 on 2006-06-14
Hi SnappyCrunch, 

Model number: SL-25511CD PLUS EXT2(E200)  

It's a PCMCIA card using a PCMCIA-to-PCI adapter. 

outputs:

henk@skybuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:85:23:8A:E3
          inet addr:10.0.0.9  Bcast:255.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::214:85ff:fe23:8ae3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1887790 (1.8 MiB)  TX bytes:338527 (330.5 KiB)
          Interrupt:209

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:780 errors:0 dropped:0 overruns:0 frame:0
          TX packets:780 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22705 (22.1 KiB)  TX bytes:22705 (22.1 KiB)

henk@skybuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by noname101 on 2006-06-14
[http://www.brunolinux.com/08+-WiFi/Configuring_Wireless_USB.html](http://www.brunolinux.com/08+-WiFi/Configuring_Wireless_USB.html)
Maybe that will help, even know its not usb it might. You'll have to install linux-wlan-ng though.
```
sudo apt-get install linux-wlan-ng
```
You might need linux-wlan-ng-firmware too.
```
sudo apt-get install linux-wlan-ng-firmware
```
You might need to modprobe prism2_pci too.
```
sudo modprobe prism2_pci
```

---

### Post by az on 2006-06-14
[QUOTE=noname101][http://www.brunolinux.com/08+-WiFi/Configuring_Wireless_USB.html](http://www.brunolinux.com/08+-WiFi/Configuring_Wireless_USB.html)
Maybe that will help, even know its not usb it might. You'll have to install linux-wlan-ng though.
```
sudo apt-get install linux-wlan-ng
```
You might need linux-wlan-ng-firmware too.
```
sudo apt-get install linux-wlan-ng-firmware
```
You might need to modprobe prism2_pci too.
```
sudo modprobe prism2_pci
```[/QUOTE]
I would think it's either orinoco.plx or hostap.plx.  For prism2, it would be prism2_plx since this is a pcmcia using a pci adapter (plx).


Try the orinoco drivers since they are the oldest and most stable.  The hostap and prism2 all also work for intersil chipsets.  But prism do not implement wireless-tools properly, hence the need for linux-wlan-ng scripts.

Just load the orinoco module and see if you can config your card.

---

### Post by henkk78 on 2006-06-19
thanks azz,

but how do I "just load the orinoco module" ? 

henk

---

### Post by az on 2006-06-19
Well, first off, boot without the thing inserted.  Then open a terminal and run

tail -f /var/log/messages

and then insert your card.  Does anything appear?  This will reveal if the pcmcia and card hardware is recognised and initialised.


Does the light go on when you plug it in?

To load a module type
sudo modprobe orinoco_plx

What output does that generate in the tail -f /var/log/messages?

---

### Post by henkk78 on 2006-06-20
hey azz,

thanks again for your reply.

It's a bit of a mission watching my card as it's at the back of my pc, but with the card inserted

'sudo cardctl ident' returns the following:

Socket 0:
product info: "INTERSIL", "HFA384x/IEEE", "Version 01.02", ""
manfid: 0x0156, 0x0002
function: 6 (network)

without the card inserted, I get nothing. The local distributor of the card verified that it uses the Prism 2.5 chipset, and that I should "just google for prism 2.5 linux drivers".

Doing that returns some links about 'hostap'.  I've installed hostap-source and hostap-utils with Synaptic.

But i'm a Linux newbie, and simply don't know the process from here! 

henk

---

### Post by henkk78 on 2006-06-20
hey azz,

i did:

sudo modprobe prism2_plx 

and tailing the message gave: 


Jun 20 11:07:29 skybuntu kernel: [17181194.924000] prism2plx_init: prism2_plx.o: 0.2.2 Loaded

henk

---

### Post by henkk78 on 2006-06-20
dmesg told me the following 

[17179590.172000] pccard: PCMCIA card inserted into slot 0
[17179590.172000] cs: memory probe 0xe7000000-0xe7ffffff: excluding 0xe7000000-0xe7ffffff
[17179590.172000] cs: memory probe 0xe5000000-0xe6ffffff: excluding 0xe6000000-0xe61fffff
[17179590.176000] pcmcia: registering new device pcmcia0.0
[17179590.264000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179590.264000] orinoco_cs 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[17179590.300000] cs: IO port probe 0x100-0x3af: excluding 0x290-0x297
[17179590.300000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179590.300000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.300000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.300000] cs: IO port probe 0xa00-0xaff:<3>eth1: failed to initialize firmware (err = -19)
[17179590.308000] orinoco_cs: register_netdev() failed
[17179590.316000]  clean.

.
.
.
.
[17181194.924000] prism2plx_init: prism2_plx.o: 0.2.2 Loaded

dunno if that helps!

---

### Post by az on 2006-06-20
So in that last dmesg, did you load the module yourself or was it loaded for you?

Did you get a wireless device to configure in the networking tool?

---

### Post by henkk78 on 2006-06-20
hi,

in the last one I loaded it myself. 

If I remove the card physically, then rmmod all drivers, then re-insert the card, it loads a bunch of orinoco stuff.

It appears the main issue has to do with the error that says:

eth1: failed to initialize firmware (err = -19)
orinoco_cs: register_netdev() failed

I get this error again if I plug the card back in, regardless whether I modprobe anything.

I suspect this has something to do with PCMCIA drivers, rather than Wi-Fi drivers, though I'm speculating. 

Any ideas?

henk

---

### Post by az on 2006-06-20
[QUOTE=henkk78]
I get this error again if I plug the card back in, regardless whether I modprobe anything.

I suspect this has something to do with PCMCIA drivers, rather than Wi-Fi drivers, though I'm speculating. 

Any ideas?

henk[/QUOTE]
Yeah, since it should use the plx drivers and not the cs drivers.  That is the difference between a pcmcia card that you stick into a laptop and one that you stick into a pcmcia-to-pci bridge.

And all this this time, you never get a wireless device running
iwconfig
(or looking in System- Administration - Networking) (same thing)
?

What I would do is to blacklist the ornioco_cs driver and reboot (Add the line
blacklist orinoco_cs
to the file  /etc/modprobe.d/blacklist)

sudo gedit

Then check to see that no drivers are loaded for your device (lsmod) and then modprobe the orninoco_plx driver.  If you then get a device to configure, file a bug report for the udev package, detailing the problem and the fix (wrong module loaded for plx wireless card)

Then, add
orinoco_plx
to /etc/modules
and it will get loaded every time you boot.  Only if it works, of course.  If not, come back with more dmesg results...

---

### Post by henkk78 on 2006-06-21
okay,

blacklisting orinoco_cs helped... somewhat! (I also blacklisted hostap. so after I insert wlan card, I have to modprobe it manually)

neither orinoco_plx or hostap_plx have any effect, except for dmesg saying they've loaded.

So I tried hostap_cs, which gives a whole bunch of errors. tailing messages shows:

wifi0: prism2_interrupt: ev=0xffff

in a seemingly infinite loop.

It also gives a bunch of other errors when it starts, including:

[17181640.472000] hostap_cs: 0.4.4-kernel (Jouni Malinen <jkmaline@cc.hut.fi>)
[17181640.472000] hostap_cs: setting Vcc=33 (constant)
[17181640.472000] hostap_cs: CS_EVENT_CARD_INSERTION
[17181640.472000] hostap_cs: setting Vcc=33 (from config)
[17181640.472000] Checking CFTABLE_ENTRY 0x01 (default 0x01)
[17181640.472000] IO window settings: cfg->io.nwin=1 dflt.io.nwin=1
[17181640.472000] io->flags = 0x0046, io.base=0x0000, len=64
[17181640.472000] hostap_cs: Registered netdevice wifi0
[17181640.480000] wifi0: Interrupt, but dev not OK
.
.
.
[17181640.520000] wifi0: Interrupt, but dev not OK
[17181640.520000] hostap_cs: index 0x01: Vcc 3.3, irq 177, io 0x9100-0x913f
[17181640.528000] wifi0: __hfa384x_cmd_no_wait(6) - timeout - reg=0xffff
[17181640.528000] hostap_cs: first command failed - assuming card does not have primary firmware
[17181640.528000] wifi0: init command completed too quickly - retrying
[17181640.532000] wifi0: prism2_interrupt: ev=0xffff
[17181640.532000] wifi0: prism2_interrupt: ev=0xffff
[17181640.540000] wifi0: __hfa384x_cmd_no_wait(6) - timeout - reg=0xffff
[17181640.540000] hostap_cs: first command failed - assuming card does not have primary firmware
[17181640.540000] prism2_hw_init: initialized in 0 ms
[17181640.540000] wifi0: prism2_interrupt: ev=0xffff
[17181640.548000] wifi0: prism2_enable_aux_port - timeout - reg=0xffff
[17181640.556000] wifi0: prism2_enable_aux_port - timeout - reg=0xffff
[17181640.556000] wifi0: valid PDA not found
[17181640.556000] SWSUPPORT0 write/read failed: FFFF != 8A32
[17181640.556000] hostap_cs: Initialization failed
[17181640.556000] prism2_config() failed
[17181640.560000] wifi0: prism2_interrupt: ev=0xffff
.
.
.
[17181640.692000] wifi0: prism2_interrupt: ev=0xffff
[17181640.692000] wifi0: prism2_interrupt: ev=0xffff
[17181640.704000] wifi0: prism2_interrupt: ev=0xffff
[17181640.708000] wifi0: prism2_interrupt: ev=0xffff
[17181640.708000] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[17181640.708000] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[17181640.708000] wifi0: hfa384x_cmd: entry still in list? (entry=e6463900, type=0, res=-1)
[17181640.708000] wifi0: hfa384x_cmd: interrupted; err=-110
[17181640.708000] wifi0: MAC port 0 enabling failed
[17181640.708000] wifi0: could not enable MAC port
[17181640.720000] wifi0: prism2_interrupt: ev=0xffff
[17181640.720000] wifi0: prism2_interrupt: ev=0xffff
[17181640.720000] wifi0: hfa384x_cmd_issue: cmd reg was busy for 5000 usec
[17181640.720000] wifi0: hfa384x_cmd_issue - timeout - reg=0xffff
[17181640.720000] wifi0: hfa384x_cmd: entry still in list? (entry=e6463900, type=0, res=-1)
[17181640.720000] wifi0: hfa384x_cmd: interrupted; err=-110
[17181640.720000] hostap_cs: Shutdown failed
[17181640.732000] wifi0: prism2_interrupt: ev=0xffff
[17181640.732000] wifi0: prism2_interrupt: ev=0xffff
[17181640.744000] wifi0: prism2_interrupt: ev=0xffff
.
.
.

I read at [http://hardware.mcse.ms/archive57-2004-5-5910.html](http://hardware.mcse.ms/archive57-2004-5-5910.html) that " The problem is that the CardBus bridge is behind a PCI-to-PCI bridge
that only forwards a limited range of IO port accesses."  (same PCI/PCMCIA bridge and SENAO adapter)

and that I should 

"Edit /etc/pcmcia/config.opts and comment out
all the "include port ..." lines, and instead add:

include port 0xc000-0xcfff"

which I did. (I also tried include port 0x0000-0xffff for good measure)

didn't seem to change anything! (though this solution did apparently work for guy at [http://hardware.mcse.ms/archive57-2004-5-5910.html](http://hardware.mcse.ms/archive57-2004-5-5910.html))

thanks,

henk

---

### Post by henkk78 on 2006-06-21
p.s. 

regarding plx vs cs

This is a normal PCMCIA card, that ordinarily runs in a laptop. 

Don't know if that explains anything.

---

### Post by az on 2006-06-21
Are you sure that your card and the adapter both work?  (Do you dual boot?)

And when you load the hostap_plx or orinoco_plx (only one of the two, not both at the same time!) you get nothing when you do iwconfig?

---

### Post by henkk78 on 2006-06-22
The card works fine in Windows (dual-boot machine)

Like I said: nothing happens with the plx drivers except the log saying that they've loaded. 

From what I can figure, the plx drivers are specifically for the PLX9052 based PCI/PCMCIA bridges.

I'm using a Ricoh RL5C475 PCI/PCMCIA bridge.

henk

*update* [http://lists.trustix.org/pipermail/tsl-discuss/2004-May/010936.html](http://lists.trustix.org/pipermail/tsl-discuss/2004-May/010936.html)   <- a discussion pointing out that the PLX drivers are not suitable for the Ricoh

---

### Post by az on 2006-06-23
I dunno.

---

