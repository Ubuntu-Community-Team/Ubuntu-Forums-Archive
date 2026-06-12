---
title: "Installing jperf to test network speed"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by cbonilla on 2009-02-11
I'm trying to figure out why file transfers are so slow to my ubuntu server so I want to see if the bottleneck is in the network portion of the installation. Trying to get jperf to work. Easy part was setting up and making it work on a pair of windows boxes. I have a couple of questions if anyone has time

How do I install it in ubuntu?
Will 8.10 use a GUI like windows?


Many thanks for your help

Carlos

---

### Post by FishRCynic on 2009-02-11
never used jperf however

if you are using samba

goto /etc/samba/smb.conf

add or change

socket options = TCP_NODELAY 

or

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

there are other options as well i find these normally work

- if you want the desktop type sudo apt-get install ubuntu-desktop 
from there you can synaptic all you want

the desktop really does not help with server management 

webadmin over http does wonders though

note:you will have to set your user to autologon if you intend to work from the desktop 
(it works can even enable compiz emerald )

---

### Post by cbonilla on 2009-02-17
Thanks for your help. Socket Option was already set to no delay. I added the changes to RCVBUF and SNDBUF with no effect

Any other thought gladly welcomed

Carlos

---

### Post by netztier on 2009-02-17
> **cbonilla said:**
>  Will 8.10 use a GUI like windows?


Ubuntu Server can have a GUI installed, but it's been a design decision by the Ubuntu makers not to include one by default.

Before you now go ahead and install a GUI on the server just to run jperf, you're better off running iperf on it, which is the classical non-GUI version that was there before jPerf was. Since they're actually the same thing, you can perfectly well use jPerf on a Windows system to measure against an iPerf running on a server.

```
apt-get install iperf
```

should do the trick.

regards

Marc

---

### Post by cbonilla on 2009-02-18
Thank you, I'll try that

---

### Post by cbonilla on 2009-02-18
Thanks for your help in getting iperf running on the ubuntu server.

Here is the jperf/iperf result from a slow XP box with a gigabit adapter to the poweredge server. This is a wired gigabit network

[1912] local 192.168.1.3 port 2222 connected with 192.168.1.252 port 5001
[ ID] Interval       Transfer     Bandwidth
[1912]  0.0- 1.0 sec  47088 KBytes  385745 Kbits/sec
[1912]  1.0- 2.0 sec  55288 KBytes  452919 Kbits/sec
[1912]  2.0- 3.0 sec  55024 KBytes  450757 Kbits/sec
[1912]  3.0- 4.0 sec  54896 KBytes  449708 Kbits/sec
[1912]  4.0- 5.0 sec  54976 KBytes  450363 Kbits/sec
[1912]  5.0- 6.0 sec  55192 KBytes  452133 Kbits/sec
[1912]  6.0- 7.0 sec  54840 KBytes  449249 Kbits/sec
[1912]  7.0- 8.0 sec  54936 KBytes  450036 Kbits/sec
[1912]  8.0- 9.0 sec  55040 KBytes  450888 Kbits/sec
[1912]  9.0-10.0 sec  55400 KBytes  453837 Kbits/sec
[1912]  0.0-10.0 sec  542688 KBytes  443876 Kbits/sec

and here is the result from a Vista box to the samer PowerEdge Server

108] local 192.168.1.2 port 52646 connected with 192.168.1.252 port 5001
[ ID] Interval       Transfer     Bandwidth
[108]  0.0- 1.0 sec  30688 KBytes  251396 Kbits/sec
[108]  1.0- 2.0 sec  32096 KBytes  262930 Kbits/sec
[108]  2.0- 3.0 sec  33344 KBytes  273154 Kbits/sec
[108]  3.0- 4.0 sec  32528 KBytes  266469 Kbits/sec
[108]  4.0- 5.0 sec  33200 KBytes  271974 Kbits/sec
[108]  5.0- 6.0 sec  33040 KBytes  270664 Kbits/sec
[108]  6.0- 7.0 sec  32752 KBytes  268304 Kbits/sec
[108]  7.0- 8.0 sec  33968 KBytes  278266 Kbits/sec
[108]  8.0- 9.0 sec  32872 KBytes  269287 Kbits/sec
[108]  9.0-10.0 sec  32464 KBytes  265945 Kbits/sec
[108]  0.0-10.0 sec  326960 KBytes  267712 Kbits/sec

What I'm trying to close in on is whether my slow file transfer times are a network bottleneck or a disk I/O problem on the PowerEdge server.

Are you able to provide guidance given these results?

thanks,

Carlos

---

### Post by netztier on 2009-02-18
> **cbonilla said:**
> Thanks for your help in getting iperf running on the ubuntu server.

Here is the jperf/iperf result from a slow XP box with a gigabit adapter to the poweredge server. This is a wired gigabit network
...


These are numbers in the ~250 Mbps and 450Mbps range, not quite blazing fast. I suspect you ran **iperf -s** on the Dell server, and then ran the "client" part on the workstations, right?

Well, that's a bit unlucky for a test result, because iPerf (and I assume that jPerf as well) has an "inverted" terminology of "Server" and "Client": the system where you run **iperf -s** acts as the *receiver*, while the one with **iperf -c <client ip>** is the *sender*. So if you want to test your server, here's what you should do:

On the *receiving* system (your Windows workstations)
```
user@client:/~$ iperf -s
```

On the *sending* system (your Dell server):

```
user@server:/~$ iperf -c <client's IP> -t 30 -i 5
```
[SIZE="1"]**-t 30 ** send for 30 seconds
**-i 5 ** report stats every 5 seconds
[/SIZE]

This way, iPerf just generates some data pattern and sends it out onto the wire as raw TCP, without any protocol overhead from Samba, NFS or sshfs.

Let's first see how good your disks are:

```
sudo hdparm -tT /dev/sdX
```

...where sdX is the hard disk on the server where the files/directories are that the server should .. well "serve". On my Server, this is how it looks for a software RAID1 array:

```
marc@blaze:~$ **sudo hdparm -tT /dev/md2**

/dev/md2:
 Timing cached reads:   266 MB in  2.01 seconds = 132.19 MB/sec
 Timing buffered disk reads:  128 MB in  3.04 seconds =  42.05 MB/sec

```

So we have the rough estimate that this RAID array can deliver around 40MBytes/s.

Now instead of letting iPerf generate the data, let's have it read them from a file. Prepare a large file, for example a .iso CD or DVD image file, and then send a certain amount of data from that file like this:

```
user@server:/~$ iperf -c <client's IP> -n 600M -F /path/to/samplefile -i 5
```
[SIZE="1"]**-n 600M** read 600MBytes ... 
**-F /path/to/samplefile** ... from the file samplefile in the /path/to directory[/SIZE]

Now the values you get show as a "grand total" how fast the server can read from a file, push the data onto the wire and transfer it to another system (but: *without* writing it to disk on the remote system!). 

Now compare these numbers against the ones with generated data. 

On my old server for example, the single PCI bus is the bottleneck: Gigabit NIC and two SATA controllers (one for each disk) share a single PCI bus - this isn't going to get real fast, never.

regards

Marc

---

### Post by cbonilla on 2009-02-18
Marc -- thank you very much for your help and insight. You're absolutely right, I ran iperf in server mode on the PowerEdge ubuntu box. I will run your suggestions and get back to you.

FYI, the server is a Poweredge 2650 with twin xeon processors and 2GB of memory. It has two 750GB Seagate Baracuda sata drives set up as RAID1 with a silicon image controller. Raid is configured with MDADM as Linux raid. I made sure to put the SI controller in the fastest slot on the Poeredge and did remove the drive jumper so that they run as SATA II. The system has built in gigabit controllers so I dont know if they share the PCI bus with the SI controller. Ubuntu is loaded on a pair of small scsi drives as raid1 set up by the adaptec Perc contoller and used only for the OS.

Again, thanks for your help.

Carlos

---

### Post by netztier on 2009-02-19
> **cbonilla said:**
> 

FYI, the server is a Poweredge 2650 with twin xeon processors and 2GB of memory. It has two 750GB Seagate Baracuda sata drives set up as RAID1 with a silicon image controller. Raid is configured with MDADM as Linux raid. I made sure to put the SI controller in the fastest slot on the Poeredge and did remove the drive jumper so that they run as SATA II. 

So does this mean that although there is a RAID controller in the system, you are not using it's hardware RAID feature (that would probably expose a single virtual disk to the OS), but you are running Linux software RAID1 across two "normal" disks, right? 

I'm all in favour of such a decision - you gain a lot of flexibility in case of disk or controller failure because you can easily migrate a disk to another system. There might be a slight performance impact, but I don't think that these two Xeons bother a lot about that.

> **cbonilla said:**
> The system has built in gigabit controllers so I dont know if they share the PCI bus with the SI controller. Ubuntu is loaded on a pair of small scsi drives as raid1 set up by the adaptec Perc contoller and used only for the OS.

Onboard ethernet controllers are most often connected to the System Bus or PCI Express, so you should be "safe" there. Check the output of **lspci** to see all PCI devices and their bus numbers. My old server shows that only the AGP slot is seen as it's own PCI bus, while all other compontents are competing for bus bandwith on bus 00. But then again, this is a very old desktop mainboard I have there. Server mainboards have multiple PCI buses, for obvious reasons.

```
marc@blaze:~$ **lspci**
[COLOR="Blue"]00[/COLOR]:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
[COLOR="Blue"]00[/COLOR]:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
[COLOR="Blue"]00[/COLOR]:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
[COLOR="Blue"]00[/COLOR]:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
[COLOR="Blue"]00[/COLOR]:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
[COLOR="Blue"]00[/COLOR]:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
[COLOR="Blue"]00[/COLOR]:09.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
[COLOR="Blue"]00[/COLOR]:0a.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
[COLOR="Blue"]00[/COLOR]:0b.0 Mass storage controller: Promise Technology, Inc. PDC40718 (SATA 300 TX4) (rev 02)
[COLOR="Blue"]00[/COLOR]:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
[COLOR="Green"]01[/COLOR]:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)

```

regards

Marc

---

### Post by cbonilla on 2009-02-19
Marc &#8211; here are the answers to your most recent questions and the output from the runs you suggested before that.

There are two controllers in the system, the onboard adaptec raid controller built into the PowerEdge which runs two small scsi devices as a RAID 1 and a Silicon Image add-in card running two esata drives which are configured as linux raid using mdadm. The raid feature on the SI controller is not enabled.

**Here is the lspci output**

carlos@PowerEdge:~$ sudo lspci
sudo: unable to resolve host PowerEdge
[sudo] password for carlos: 
00:00.0 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset) (rev 13)
00:00.1 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset)
00:00.2 Host bridge: Broadcom CMIC-LE
00:04.0 Class ff00: Dell Embedded Remote Access or ERA/O
00:04.1 Class ff00: Dell Remote Access Card III
00:04.2 IPMI SMIC interface: Dell Embedded Remote Access: BMC/SMIC device
00:0e.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 Host bridge: Broadcom CSB5 South Bridge (rev 93)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 93)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 ISA bridge: Broadcom CSB5 LPC bridge
00:10.0 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:10.2 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:11.0 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:11.2 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
02:06.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
03:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
04:08.0 PCI bridge: Intel Corporation 80303 I/O Processor PCI-to-PCI Bridge (rev 01)
04:08.1 RAID bus controller: Dell PowerEdge Expandable RAID Controller 3/Di (rev 01)

**The iperf output:**

(the windows box was put into server mode using jperf)

carlos@PowerEdge:~$ sudo iperf -c 192.168.1.2 -t 30 -i 5
sudo: unable to resolve host PowerEdge
[sudo] password for carlos: 
------------------------------------------------------------
Client connecting to 192.168.1.2, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.252 port 34138 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 5.0 sec  68.1 MBytes    114 Mbits/sec
[  3]  5.0-10.0 sec  68.0 MBytes    114 Mbits/sec
[  3] 10.0-15.0 sec  68.0 MBytes    114 Mbits/sec
[  3] 15.0-20.0 sec  68.4 MBytes    115 Mbits/sec
[  3] 20.0-25.0 sec  68.4 MBytes    115 Mbits/sec
[  3] 25.0-30.0 sec  68.3 MBytes    115 Mbits/sec
[  3]  0.0-30.0 sec    409 MBytes    114 Mbits/sec

**HDPARM on the drives:**

One of the two drives in the md0 raid
carlos@PowerEdge:~$ sudo hdparm -tT /dev/sdb
sudo: unable to resolve host PowerEdge

/dev/sdb:
 Timing cached reads:   894 MB in  2.00 seconds = 446.78 MB/sec
 Timing buffered disk reads:  220 MB in  3.00 seconds =  73.30 MB/sec


The other drive in the md0 raid
carlos@PowerEdge:~$ sudo hdparm -tT /dev/sdc
sudo: unable to resolve host PowerEdge

/dev/sdc:
 Timing cached reads:   880 MB in  2.00 seconds = 440.07 MB/sec
 Timing buffered disk reads:  222 MB in  3.01 seconds =  73.68 MB/sec


The raid itself
carlos@PowerEdge:~$ sudo hdparm -tT /dev/md0
sudo: unable to resolve host PowerEdge

/dev/md0:
 Timing cached reads:   892 MB in  2.00 seconds = 446.15 MB/sec
 Timing buffered disk reads:  208 MB in  3.02 seconds =  68.89 MB/sec

**And the large file test**
FYI, I dragged and dropped a 6.5GB file from the windows box to the ubuntu server and it took 10-12 minutes to copy

carlos@PowerEdge:~$ sudo iperf -c 192.168.1.2 -n 600M -f /dev/mdo/video1.mpg
sudo: unable to resolve host PowerEdge
[sudo] password for carlos: 
------------------------------------------------------------
Client connecting to 192.168.1.2, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.1.252 port 58497 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-43.8 sec  5.03 Gbits    115 Mbits/sec

Thanks again for your time.

Carlos

---

### Post by netztier on 2009-02-19
> **cbonilla said:**
> 

**Here is the lspci output**


Please add "Code" marks to text output that you copy from the console - it is more comfortable to read. Just copy/paste the text from the console to here, highlight it with the mouse and click the "#" button in the small toolbar above the editing window.


> **cbonilla said:**
> 
```
carlos@PowerEdge:~$ sudo lspci
sudo: unable to resolve host PowerEdge
[sudo] password for carlos: 
00:00.0 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset) (rev 13)
00:00.1 Host bridge: Broadcom CMIC-WS Host Bridge (GC-LE chipset)
00:00.2 Host bridge: Broadcom CMIC-LE
00:04.0 Class ff00: Dell Embedded Remote Access or ERA/O
00:04.1 Class ff00: Dell Remote Access Card III
00:04.2 IPMI SMIC interface: Dell Embedded Remote Access: BMC/SMIC device
00:0e.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
00:0f.0 Host bridge: Broadcom CSB5 South Bridge (rev 93)
00:0f.1 IDE interface: Broadcom CSB5 IDE Controller (rev 93)
00:0f.2 USB Controller: Broadcom OSB4/CSB5 OHCI USB Controller (rev 05)
00:0f.3 ISA bridge: Broadcom CSB5 LPC bridge
00:10.0 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:10.2 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:11.0 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
00:11.2 Host bridge: Broadcom CIOB-X2 PCI-X I/O Bridge (rev 03)
02:06.0 RAID bus controller: Silicon Image, Inc. SiI 3124 PCI-X Serial ATA Controller (rev 02)
[COLOR="Red"]03:06.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5701 Gigabit Ethernet (rev 15)
[/COLOR]04:08.0 PCI bridge: Intel Corporation 80303 I/O Processor PCI-to-PCI Bridge (rev 01)
04:08.1 RAID bus controller: Dell PowerEdge Expandable RAID Controller 3/Di (rev 01)

```


ok, we see that NICs and the RAID Controllers are not on the same PCI bus, so there's probably no congestion there.

> 
/dev/md0:
 Timing cached reads:   892 MB in  2.00 seconds = 446.15 MB/sec
 Timing buffered disk reads:  208 MB in  3.02 seconds =  68.89 MB/sec


See? That should be good for way over 700Mbit/s

> 
**And the large file test**

```
carlos@PowerEdge:~$ sudo iperf -c 192.168.1.2 -n 600M -f /dev/mdo/video1.mpg
sudo: unable to resolve host PowerEdge
[sudo] password for carlos: 
------------------------------------------------------------
Client connecting to 192.168.1.2, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.1.252 port 58497 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-43.8 sec  5.03 Gbits    115 Mbits/sec
```


That's way too slow. Does it get any faster if you repeat the sending of the 600MBytes? With 2GBytes of RAM, the second time, the whole 600Megs  should come from cache, not from disk - and should be noticeably faster.


Hmm... Broadcom 5700 series onboard NICs... there are some stories around of them performing badly in some products, also on Dell PowerEdge 2650. If I remember correctly, HP even swapped out Mainboards on DL38x systems, taking back the Broadcom equipped ones and replacing them with Intel-NICced boards.

[2650 Problem with Broadcom Dual Onboard NIC's with Red Hat 7.2]("http://lists.us.dell.com/pipermail/linux-poweredge/2002-July/003272.html")

And then I found something very interesting. This is from a guy that had Broadcom NICs in an IBM server:

[Troubleshooting VMware ESX network perform...]("http://http://www.tuxyturvy.com/blog/index.php?/archives/37-Troubleshooting-VMware-ESX-network-performance.html")

In a nutshell: looking at /proc/interrupts, he found out that the Broadcom NIC was sharing the Interrupt with the USB subsystem. Upon removing the USB kernel module, his Broadcom NIC started to fly!

Can you show us /proc/interrupts from your server?

```
user@server $ **cat /proc/interrupts**
```

regards

Marc

---

### Post by cbonilla on 2009-02-19
Thanks for the confirmation that I'm not imagining it

Here's the output 

carlos@PowerEdge:~$ sudo cat /proc/interrupts
[sudo] password for carlos: 
```
           CPU0       CPU1       CPU2       CPU3       
  0:         92          0          0          0   IO-APIC-edge      timer
  1:        450          0          0          0   IO-APIC-edge      i8042
  3:          4          0          0          0   IO-APIC-edge    
  4:          4          0          0          0   IO-APIC-edge    
  8:          2          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 11:          0          0          0          0   IO-APIC-fasteoi   ohci_hcd:usb1
 12:      17640          0          0          0   IO-APIC-edge      i8042
 14:      22935          0          0          0   IO-APIC-edge      pata_serverworks
 15:          0          0          0          0   IO-APIC-edge      pata_serverworks
 24:       6078          0          0          0   IO-APIC-fasteoi   sata_sil24
 28:     299146          0          0          0   IO-APIC-fasteoi   eth0
 29:          1          0          0          0   IO-APIC-fasteoi   eth1
 30:      16112          0          0          0   IO-APIC-fasteoi   aacraid
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      85345     218076     127022     221991   Local timer interrupts
RES:       9126       8280      21755       9145   Rescheduling interrupts
CAL:        404        830        499        835   function call interrupts
TLB:        586        682       1362       1511   TLB shootdowns
SPU:          0          0          0          0   Spurious interrupts
ERR:          0
MIS:          0

```

Nice trick for marking as code, wasn't aware of that. As I said, I'm new to Ubuntu. FyI, my network connection is via eth0.

Not sure if its relevant but at boot I'm getting the following error : MP-BIOS BUG 8254 Timer not connected to IO-APIC. I think that error only started when I upgraded from Hardy to Itrepid although the speed was unaffected.

---

### Post by netztier on 2009-02-19
> **netztier said:**
> 

In a nutshell: looking at /proc/interrupts, he found out that the Broadcom NIC was sharing the Interrupt with the USB subsystem. Upon removing the USB kernel module, his Broadcom NIC started to fly!


Guess what! It's sensational! I always felt a bit stumped by low transfer rates on my AMD based desktop (Shuttle SN95Gv3 barebone and an AMD64 Venice 3000+). And I was p*ssed off by stuttering sound output during iPerf tests, that would barely ever go beyond 40 MByte/s on a good day.

Then I looked an my own /proc/interrupts:

```
           CPU0       
  0:        127    XT-PIC-XT        timer
  1:          2    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:    1918827    XT-PIC-XT        ohci_hcd:usb2, ohci_hcd:usb5, eth0
  4:          3    XT-PIC-XT      
  5:    9551333    XT-PIC-XT        hhci_hcd:usb3, ehci_hcd:usb4, [COLOR="Red"]eth1_rename, NVidia CK8S[/COLOR]
  7:         35    XT-PIC-XT        parport0
  8:          2    XT-PIC-XT        rtc0
  9:          0    XT-PIC-XT        acpi
 11:    1038651    XT-PIC-XT        ehci_hcd:usb1, ohci_hcd:usb6, ohci1394, sata_nv, nvidia
 14:          0    XT-PIC-XT        pata_amd
 15:     120846    XT-PIC-XT        pata_amd
NMI:          0   Non-maskable interrupts
LOC:    2300376   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          1
MIS:          0
```

 D'OH! eth1_rename (the device name the somewhat strange Marvell Chip sometimes appears as) shares the interrupt with the CK8S sound device! 

I went into the BIOS and started to deactivate unneeded devices like the parallel port, floppy controller, first IDE ( the hardisk is on SATA and DVD drive on second IDE). Apparently, this freed up some interrupt allocation space and no we have this:

```
marc@cube:/tmp$ more /proc/interrupts 
           CPU0       
  0:        127    XT-PIC-XT        timer
  1:          2    XT-PIC-XT        i8042
  2:          0    XT-PIC-XT        cascade
  3:     240024    XT-PIC-XT        ehci_hcd:usb1, [COLOR="SeaGreen"]NVidia CK8S[/COLOR]
  4:          2    XT-PIC-XT      
  5:   17347530    XT-PIC-XT        ehci_hcd:usb4, [COLOR="SeaGreen"]eth0[/COLOR]
  7:     135470    XT-PIC-XT        ohci_hcd:usb5, nvidia
  8:          2    XT-PIC-XT        rtc0
  9:          0    XT-PIC-XT        acpi
 10:       3290    XT-PIC-XT        ohci_hcd:usb2, ohci_hcd:usb6, ohci1394
 11:      65870    XT-PIC-XT        ohci_hcd:usb3, sata_nv
 14:          0    XT-PIC-XT        pata_amd
 15:      20677    XT-PIC-XT        pata_amd
NMI:          0   Non-maskable interrupts
LOC:     399179   Local timer interrupts
RES:          0   Rescheduling interrupts
CAL:          0   function call interrupts
TLB:          0   TLB shootdowns
SPU:          0   Spurious interrupts
ERR:          1
MIS:          0

```

The Marvell chip is now eth0 again, has almost it's own interrupt, and we have **70-75MByte/s** in and out of the interface with no sound stutter at all!

Let's call THAT a day! :-)

Marc

---

### Post by cbonilla on 2009-02-19
I'll go give that a try and let you know

Carlos

---

### Post by cbonilla on 2009-02-19
OK, went into the BIOS and flagged the floopy as not present and disabled the floppy and USB controler. Here's the output from

```
carlos@PowerEdge:~$ sudo cat /proc/interrupts
[sudo] password for carlos: 
           CPU0       CPU1       CPU2       CPU3       
  0:         92          0          0          0   IO-APIC-edge      timer
  1:         65          0          0          0   IO-APIC-edge      i8042
  3:          4          0          0          0   IO-APIC-edge    
  4:          4          0          0          0   IO-APIC-edge    
  8:          2          0          0          0   IO-APIC-edge      rtc0
  9:          0          0          0          0   IO-APIC-fasteoi   acpi
 12:       7194          0          0          0   IO-APIC-edge      i8042
 14:       1013          0          0          0   IO-APIC-edge      pata_serverworks
 15:          0          0          0          0   IO-APIC-edge      pata_serverworks
 24:       1227          0          0          0   IO-APIC-fasteoi   sata_sil24
 28:       8622          0          0          0   IO-APIC-fasteoi   eth0
 29:          1          0          0          0   IO-APIC-fasteoi   eth1
 30:      11759          0          0          0   IO-APIC-fasteoi   aacraid
NMI:          0          0          0          0   Non-maskable interrupts
LOC:      14525      11449      10258      13279   Local timer interrupts
RES:       4883       6844       8481       6877   Rescheduling interrupts
CAL:        454        750        446        726   function call interrupts
TLB:        523        606       1211       1404   TLB shootdowns
SPU:          0          0          0          0   Spurious interrupts
```
ERR:          0

I'll try a file transfer in a moment

---

### Post by cbonilla on 2009-02-19
I ran iperf again. All I can say is WOW. Throughput leapt from 115Mbits sec to over 700. Truly amazing. Its too late or I'd offer to name my first born after you

```
carlos@PowerEdge:~$ sudo iperf -c 192.168.1.2 -n 600M -f /dev/md0/video1.mpg
------------------------------------------------------------
Client connecting to 192.168.1.2, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.1.252 port 48840 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 7.1 sec  5.03 Gbits    705 Mbits/sec
```


and then ran it a second time

```
carlos@PowerEdge:~$ sudo iperf -c 192.168.1.2 -n 600M -f /dev/md0/video1.mpg
------------------------------------------------------------
Client connecting to 192.168.1.2, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.1.252 port 58683 connected with 192.168.1.2 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 7.1 sec  5.03 Gbits    706 Mbits/sec
```

---

### Post by netztier on 2009-02-20
> **cbonilla said:**
> I ran iperf again. All I can say is WOW. Throughput leapt from 115Mbits sec to over 700. Truly amazing. Its too late or I'd offer to name my first born after you

:-D

Congrats for fixing it. From the outputs of /proc/interrupts alone, I couldn't tell where the difference is and what actually happened that unleashed your NIC.

So - now we know that iPerf/jPerf show decent throughput rates, but that's nothing but raw TCP. What about Samba/CIFS or NFS performance? 

regards

Marc

---

### Post by cbonilla on 2009-02-20
No, the congrats on fixing it belong to you, not me. I just followed directions

Carlos

---

### Post by cbonilla on 2009-02-21
Marc -In trying to understand what you accomplished, I came across this. Thought it might be of interest in case similar problems arise.

Carlos

Local APICs

LAPICs manage all external interrupts for the processor that it is part of. In addition, it is able to accept and generate inter-processor interrupts (IPIs) between LAPICs. LAPICs may support up to 224 usable IRQ vectors from an I/O APIC. Vectors numbers 0 to 31, out of 0 to 255, are reserved for exception handling by x86 processors.

[edit] I/O APICs

I/O APICs contain a redirection table, which is used to route the interrupts it receives from peripheral buses to one or more Local APICs.

[edit] Considerations

[edit] Hardware Bugs

There are a number of known bugs in implementations of APIC systems, especially with concern to how the 8259 is connected.

There are defective BIOSes which do not set up interrupt routing properly. This includes the errors in the implementation of ACPI tables and Intel Multiprocessor Specification tables.

[edit] Operating System Issues

It can be a cause of system failure, as some versions of some operating systems do not support it properly. If this is the case, disabling I/O APIC may cure the problem. For Linux, try the 'noapic nolapic' kernel parameters; for FreeBSD, the 'hint.apic.0.disabled' kernel environment variable; For NetBSD, drop into userconf ("boot -c" from the boot prompt), then use "disable ioapic" and "exit" to continue the boot process.

In NetBSD with nforce chipsets from Nvidia, having IOAPIC support enabled in the kernel can cause "nfe0: watchdog timeout" errors.[1]

[COLOR="Red"]In Linux, problems with I/O APIC are one of several causes of error messages concerning "spurious 8259A interrupt: IRQ7.". It is also possible that I/O APIC causes problems with network interfaces based on via-rhine driver, causing a transmission time out. Uniprocessor kernels with APIC enabled can cause spurious interrupts to be generated.[/COLOR]

---

