---
title: "Ralink RT3290 support"
date: 2013-08-08
forum: Networking &amp; Wireless
---

### Post by Binary-Synapse on 2013-08-08
Hello,

I have a problem with WLAN Combo (Wifi+Bluetooth) card.
The Combo is an Azurewave AW-NB087H-LE.
OS is Ubuntu 12.04LTS with 3.2 kernel (64bits)

I downloaded the Ralink rt3290 drivers from the ralink site (couldn't find any in Azurewave site), but after "make && sudo make install && sudo reboot" I don't see any SSIDs around me.


"[COLOR=#008000]lsmod | grep rt3290sta[/COLOR]" returns:
rt3290sta   96381       1


If I issue "[COLOR=#008000]sudo ifconfig[/COLOR]" I only get "eth0" and "lo" devices listed.
But if I issue "[COLOR=#008000]sudo ifconfig ra0 up[/COLOR]" I will get "ra0", "eth0" and "lo" devices listed. But even in this case I still cant see any SSIDs via NM icon.


"[COLOR=#008000]sudo rfkill list[/COLOR]" returns nothing.

Also Bluetooth is not working (I don't think the ralink driver includes it though).

Driver was obtained here (under **RT3290 PCIe** entrance):
[http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

What can I do to make everything work?

Thank you

---

### Post by chili555 on 2013-08-08
I am skeptical that the compiled from Ralink versions will ever work on 64-bit. Were there significant warnings at the 'make' command? Of course, you could re-install 32-bit and try again, a risky and tedious process, or install Ubuntu 13.04 where  it's covered by default.

---

### Post by Binary-Synapse on 2013-08-08
Hello chili.

"make" seems to go OK.
I didn't see any obvious error.

Is there some necessary firmware for this WLAN?
Will I also need firmware files for the Bluetooth section?

Thank you.

---

### Post by chili555 on 2013-08-08
If you had seen an error, it wouldn't have installed at all.I was asking about warnings. Please check:```
cd Desktop/rt3290files  [COLOR="#FF0000"]<--or wherever you extracted them[/COLOR]
make clean
make
```Post the result here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Firmware is not required:```
$ modinfo DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/rt3290sta.ko
filename:       /home/chili/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/rt3290sta.ko
version:        2.6.0.0_rev1
[COLOR="#FF0000"]<--firmware?? Nope.[/COLOR]
srcversion:     13F483178C6DF2E02D874C3
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
depends:        
vermagic:       3.5.0-19-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
```You might look for interesting clues here:```
dmesg | grep rt2
```

---

### Post by Binary-Synapse on 2013-08-08
Hello chili,

 Here is the output after a make clean + make
[http://paste.ubuntu.com/5964472/](http://paste.ubuntu.com/5964472/)


 Here is my full dmesg:
[http://paste.ubuntu.com/5964515/](http://paste.ubuntu.com/5964515/)

 I hope that helps you more than a "dmesg | grep rt2"

The only problem is that currently I have 2 perfectly equal machines with this same issue.
One with Ubuntu and the other one with Debian 7.0
And currently I only have access to the Debian 7.0 machine.

Can you work your magic with my Debian 7.0 logs??

 Thank you

---

### Post by chili555 on 2013-08-08
> /usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c: In function ‘RT3290_AsicTxAlcGetAutoAgcOffset’:
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:1564:25: warning: assignment discards ‘const’ qualifier from pointer target type [enabled by default]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c: In function ‘MlmeAntSelection’:
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format ‘%d’ expects argument of type ‘int’, but argument 4 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2507:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2522:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2522:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2523:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘ULONG’ [-Wformat]
/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2523:5: warning: format ‘%d’ expects argument of type ‘int’, but argument 3 has typ....
<snip>As I suspected, warnings by the dozens. Somewhere among the unused, undeclared, idunnowhat warnings are one or several flaws that prevent your device from working as expected. I repeat, you could re-install 32-bit and try again, a risky and tedious process, or install Ubuntu 13.04 where it's covered by default. I use 13.04 perfectly well on two machines here without any real issues.> [ 2038.057336] CPU0: Package power limit notification (total events = 8206)
[ 2038.057345] CPU1: Package power limit notification (total events = 8207)
[ 2038.057896] CPU0: Package power limit normal
[ 2038.057902] CPU1: Package power limit normalThat's a bit scary to me; I suggest you Google it and see if it is significant and fixable or trivial.>  Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-.. insteadLikewise, I suggest we *BOTH* Google this one.

---

### Post by Binary-Synapse on 2013-08-16
Hello chilli,


> [COLOR=#000000]*/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]*[/COLOR]
[COLOR=#000000]*/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;ULONG&#8217; [-Wformat]*[/COLOR]
[COLOR=#000000]*/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2489:4: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat]*[/COLOR]
[COLOR=#000000]*/usr/src/DPO_RT3290_LinuxSTA_V2600_20120508/os/linux/../../chips/rt3290.c:2507:5: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;ULONG&#8217; [-Wformat]*[/COLOR]


Yes, there are many type conversion problems.
I guess that's what happens when developers use too much Coercion instead of Explicit Type Conversions in C language.



> [COLOR=#000000]*[ 2038.057336] CPU0: Package power limit notification (total events = 8206)*[/COLOR]
[COLOR=#000000]*[ 2038.057345] CPU1: Package power limit notification (total events = 8207)*[/COLOR]
[COLOR=#000000]*[ 2038.057896] CPU0: Package power limit normal*[/COLOR]
[COLOR=#000000]*[ 2038.057902] CPU1: Package power limit normal*[/COLOR]
That is a known bug.
I think many people with Sandy Bridge based systems have this problem (mine is Sandy Arch. also).
If you google it you will find many cases like mine.
There are ways to suppress this error, but I will wait for a future fix.
Besides, in my case the CPU is cool and the system is only using about 4% of CPU (when idle).
The error even shows up in Clonezilla Live (overlapping it's User Interface) when I'm capturing my HDD data!


> [COLOR=#000000]*Loading kernel module for a network device with CAP_SYS_MODULE (deprecated). Use CAP_NET_ADMIN and alias netdev-.. instead*[/COLOR]
OK. So the loading method is deprecated.
But what file(s) should I change??


---------------------------------------------------------------------------


Anyway... I have good news chilli.

After a good night sleep, I reinstalled everything from scratch and voilá!
I still had some compile warnings, and the message "*Loading kernel module for a network device with CAP_SYS_MODULE (deprecated)" *still shows up in dmesg, but the Combo Card is working 100% now!

And BT is also working.
For some reason the BT driver is not included.
It seems to be developed by Zotac. So I had to download/install it separately.


Thank you for your help chilli555.

---

