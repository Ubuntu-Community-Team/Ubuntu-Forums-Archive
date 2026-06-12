---
title: "Broadcom BCM4321 WIreless NIC not finding networks"
date: 2012-10-22
forum: Networking &amp; Wireless
---

### Post by Laize on 2012-10-22
Exactly as the title says.  Can't seem to find any networks.  I don't have access to a direct connection.  Only way I have been able to update software on my install is through loading it in a virtual machine in Windows.

Currently using the STA drivers from Broadcom.

---

### Post by chili555 on 2012-10-22
Let's just verify which exact device you have and a few other details so we can decide if STA is correct. Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsb_release -d
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Laize on 2012-10-22
$ sudo lspci -nn | grep 0280
```
04:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [14e4:4329] (rev 01)

```

$ rfkill list all
```
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

$ lsb_release -d
```
Description:	Ubuntu 12.04.1 LTS

```

---

### Post by chili555 on 2012-10-22
> Broadcom Corporation BCM4321 802.11b/g/n [[COLOR="Red"]14e4:4329[/COLOR]]So far, so good; I believe the STA driver is correct. Let's do some more diagnosis. Let's make sure no conflicting drivers are loaded:```
lsmod | grep -e b43 -e ndis
```If all is well, this should be blank.

Let's be sure Network Manager alone is in control here:```
cat /etc/network/interfaces
```The correct reading is only this:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```If more appears, edit the file:```
sudo gedit /etc/network/interfaces
```Remove extra lines pertaining to eth1, wlan0, etc. Proofread, save and close gedit. Restart NM:```
sudo service network-manager restart
```Let's see if we can provoke any interesting warnings or errors:```
sudo iwlist eth1 scan
```We don't need to see your results; just tell us if it scans and sees networks or if it gives a warning or error.

---

### Post by Laize on 2012-10-22
$ sudo lsmod | grep -e b43 -e ndis
	> blank

$ cat /etc/network/interfaces
> auto lo
iface lo inet loopback

$ sudo iwlist eth1 scan
(Is this what you meant by interesting?)
> eth1      Interface doesn't support scanning.


---

### Post by chili555 on 2012-10-22
> (Is this what you meant by interesting?)
[QUOTE]eth1 Interface doesn't support scanning. [/QUOTE]Indeed! Let's make sure your interface is eth1, the usual for the STA driver:```
iwconfig
```If it turns out to be eth2 or wlan99 or some such, see if it scans:```
sudo iwlist wlanXX scan
```Of course, substitute what you found.

Let's check for interesting kernel messages:```
dmesg | grep -e wl -e 04:00
```

---

### Post by Laize on 2012-10-22
$ iwconfig
```
lo        no wireless extensions.

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```

(For good measure I ran $ iwlist eth2 scan.  No scan results)

$ dmesg | grep -e wl -e 04:00
```
[    0.513406] pci 0000:04:00.0: [14e4:4329] type 0 class 0x000280
[    0.513433] pci 0000:04:00.0: reg 10: [mem 0xf7ff8000-0xf7ffbfff]
[   16.468369] wl: module license 'MIXED/Proprietary' taints kernel.
[   16.903088] wl 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19

```

---

### Post by chili555 on 2012-10-22
>  loading it in a virtual machine in Windows.Do you mean Ubuntu is running in a virtual machine within Windows??

Old Chili hates when he misses the essential fact. Sorry. Wireless networking is generally not available in a virtual machine. The virtual NICs bridge to the host, in your case Windows, network.

Is that the case here, or have I misinterpreted your statement above?

[https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1](https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1)

---

### Post by Laize on 2012-10-22
> **chili555 said:**
> Do you mean Ubuntu is running in a virtual machine within Windows??

Old Chili hates when he misses the essential fact. Sorry. Wireless networking is generally not available in a virtual machine. The virtual NICs bridge to the host, in your case Windows, network.

Is that the case here, or have I misinterpreted your statement above?

[https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1](https://blogs.oracle.com/fatbloke/entry/networking_in_virtualbox1)

Negative.

Ubuntu is installed on a USB drive which I CAN load into a virtual machine if necessary.  It's just running on its own for the purposes of this troubleshooting.

I was simply pointing out that a loading it into a virtual machine in Windows is the only way I can get internet access (and thus use apt-get update/upgrade) right now.  At this moment I'm staring at a terminal with no internet whatsoever :(

---

### Post by chili555 on 2012-10-22
Whew! I am glad to be mistaken in this case. So far, your readings are unremarkable. Let's see:```
dmesg | grep -i -e eth2 -e warn -e error
```Something's amiss here, but we haven't uncovered it yet.

---

### Post by Laize on 2012-10-22
I have a history with pretty much every operating system.  I routinely get errors that take ages to even find the cause of.

$ dmesg | grep -i -e eth2 -e warn -e error
```

[    0.502556] ACPI Warning: Incorrect checksum in table [TAMG] - 0x42, should be 0x41 (20110623/tbutils-314)
[    7.230412] mei: module is from the staging directory, the quality is unknown, you have been warned.
[    7.969367] EXT4-fs (sdc2): re-mounted. Opts: errors=remount-ro
[    7.989440] udevd[424]: renamed network interface eth1 to eth2

```


EDIT: Input wrong line.  That's the proper output.

---

### Post by chili555 on 2012-10-22
Wow! I feel like the more I learn, the less I know! >  I routinely get errors that take ages to even find the cause of.Indeed; and errors that have no significant effect. I see nothing significant here. We might look at this:> udevd[424]: [COLOR="Red"]renamed network interface eth1 to eth2[/COLOR]Did you have a different wireless device at one time? I wonder, but doubt, if fixing the udev rule might help. A long shot, but maybe. Please do:```
sudo gedit /etc/udev/rules.d/70-persistent-net.rules
```You should see an entry for the ethernet device and two wireless devices. I assume eth1 is no longer present. Comment it out, like this:```
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f0:de:f1:3e:b2:a4", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="58:94:6b:99:55:a0", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```Then change the Broadcom, now known as eth2 to eth1. Proofread, save and close gedit. Reboot immediately. 

Now check:```
iwconfig
```Is the wireless interface eth[COLOR="Red"]1[/COLOR]? Does it scan?```
sudo iwlist eth1 scan
```I am off to my supply of tranquilizers!

---

### Post by spandon on 2012-10-22
Hi,
I was having problems with my Dell´s Broadcom wifi card, tried a lot of workarounds from the forum nothing worked for me in Ubuntu 12.02 and 12.10 - untill I remembered someone saying the tried a usb wifi adapter and it worked.
I had a couple of adaptors from other projects so I tried them ( 1 a bg the other a bgn) both worked without any use of the terminal.
Happy as Larry now, if you can get hold of a usb wifi adapter it may work for you to?
Don

---

### Post by Laize on 2012-10-22
> **spandon said:**
> Hi,
I was having problems with my Dell´s Broadcom wifi card, tried a lot of workarounds from the forum nothing worked for me in Ubuntu 12.02 and 12.10 - untill I remembered someone saying the tried a usb wifi adapter and it worked.
I had a couple of adaptors from other projects so I tried them ( 1 a bg the other a bgn) both worked without any use of the terminal.
Happy as Larry now, if you can get hold of a usb wifi adapter it may work for you to?
Don

I'm actually 99.999% sure it would work.

The problem with that, however, is **I don't like being beaten by computers** and buying a USB NIC would be admitting defeat.

Still no scan results, chili.  Though the Wireless NIC **is** now Eth1.

---

### Post by chili555 on 2012-10-22
> **Laize said:**
> I'm actually 99.999% sure it would work.

The problem with that, however, is **I don't like being beaten by computers** and buying a USB NIC would be admitting defeat.Exactly! Off for lunch and an appointment in town; back later.

---

### Post by Laize on 2012-10-22
If anyone else has any experience setting up networking on 12.04 I'd greatly appreciate it.  Really ripping my hair out here.  This is day 3.

---

### Post by chili555 on 2012-10-22
May I please review a complete diagnostic work-up? Please reboot so we have a clean slate.```
dmesg > laize.txt
lsmod >> laize.txt
ls /var/cache/apt/archives/ | grep bcmwl >> laize.txt
iwconfig >> laize.txt
zip laize.zip laize.txt
```Find the file laize.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

Quite a mystery we have here...

---

### Post by Laize on 2012-10-22
> **chili555 said:**
> May I please review a complete diagnostic work-up? Please reboot so we have a clean slate.```
dmesg > laize.txt
lsmod >> laize.txt
ls /var/cache/apt/archives/ | grep bcmwl >> laize.txt
iwconfig >> laize.txt
zip laize.zip laize.txt
```Find the file laize.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

Quite a mystery we have here...

I know right?  I don't know what it is but I always seem to come up with real doozies of OS problems.  And they're fresh installs so I don't even know how they could be my fault lol.

Anyway, everything you asked for is attached.

---

### Post by umfunix on 2012-10-22
I was following this thread with great inerest as i have a smilar problem. My ethernet adapter is not working anymore, so I only have wireless for internet.  But, wireless is not wrking.  On "Additional Driver" scan it does reports that it wants to insatt the Broadcom STA wireless.....but have not internet connection to do that.

I've done all the greps and diagnostics and had similar results.  no wireless extensions, lo interface doesn't support scanning, and Broadcom BCM4311.

---

### Post by chili555 on 2012-10-22
Frankly, I still don't see anything to fix. I see a few minor points:> [    0.547664] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[    0.547690] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *7 9 10 11 12 14 15)
[    0.547715] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.547740] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.547764] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) [COLOR="Red"]*0, disabled[/COLOR].
[    0.547789] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) [COLOR="Red"]*0, disabled[/COLOR].
[    0.547814] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[    0.547838] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 6 7 9 10 11 12 14 15)I don't know why you might have two IRQs disabled or even if it makes the slightest difference. You might check in the BIOS and reset all IRQs to 'Auto Select.'

I notice you have in apt cache:> bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6.1_amd64.debIf you can confirm that you have a 64-bit system and there is no mis-match, you might try to reinstall the package:```
arch  [COLOR="Red"]<--64-bit will return x86_64[/COLOR]
```First, let's preserve a copy, just in case:```
sudo cp /var/cache/apt/archives/bcmwl*  ~
```That copies it to your /home/user direcory. Now do:```
sudo modprobe -r wl
sudo dpkg --purge bcmwl-kernel-source
sudo dpkg -i bcmwl-kernel-source*.deb
sudo modprobe wl
```Any improvements? 

The corrupted part may, in fact, be one of its dependencies and not bcmwl-kernel-source.

---

### Post by Laize on 2012-10-22
When you questioned whether or not the system was 64-bit I was actually afraid I'd used my 32-bit disk for the install... thankfully for my self-esteem that is not the case.  It's 64-bit.

I don't have the bcmwl-kernel-source.deb.  Should I load up the virtual machine and grab it?

---

### Post by Laize on 2012-10-22
Ok I loaded ubuntu in the VM just to download the package and I got it without installing it.

This occurred after I purged the old bcmwl.

Upon rebooting (such that linux was all that was running again) my wifi card immediately picked up the local networks.  I can't connect (It just attempts to connect ad infinitum and telling me "authentication is required by wireless network" periodically).

Unsure of what to do.  Continue reinstalling the bcmwl package?

---

### Post by Laize on 2012-10-22
Decided "screw it".  Reinstalled package anyway figuring I could just get rid of it later.

No improvement.

---

### Post by chili555 on 2012-10-22
> I don't have the bcmwl-kernel-source.deb???

Isn't it in /var/cache/apt/archives/ ? Weren't you able to copy it over to /home/laize, or whatever your user name is?> It just attempts to connect ad infinitum and telling me "authentication is required by wireless network" periodically).Did you add any settings to Network Manager? I suggest you remove them as NM usually does a good job all by itself.

Does it ask for your WPA password?

---

### Post by Laize on 2012-10-22
> **chili555 said:**
> ???

Isn't it in /var/cache/apt/archives/ ? Weren't you able to copy it over to /home/laize, or whatever your user name is?

Yes.  I've been up since 7 AM yesterday trying to get this darn thing working.  Stupid brain fart.  Either way I got the package back on and there was no discernible improvement.

> Did you add any settings to Network Manager? I suggest you remove them as NM usually does a good job all by itself.

Does it ask for your WPA password?

I added nothing to NM.  In fact, unless it put an unsolicited dialogue box in my face I haven't even clicked it except to see if it detected networks.

Without the BCMWL drivers it looked like it was working.  Broadcasting, detecting networks... even asked for my WPA2 key and detected a change in the SSID.  The only thing it refused to actually do is *connect*.

I almost feel like this is trench warfare where the enemy is making me claw tooth and nail for every inch towards success.

---

### Post by Laize on 2012-10-22
Is there any way to verify if it's the dependencies that are corrupt?

---

### Post by chili555 on 2012-10-22
> Without the BCMWL drivers it looked like it was working. Broadcasting, detecting networks... even asked for my WPA2 key and detected a change in the SSID. The only thing it refused to actually do is connect.Without?? I don't understand. Without bcmwl-kernel-source, what was driving it?

When you scan, does it say your network is WPA and WPA2 mixed mode? ```
nm-tool
```>  Wireless Access Points (* = current AP)
    *GBR1:           Infra, xx:13:10:62:8D:xx, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA2
    dlink:           Infra, xx:18:E7:D1:C8:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 [COLOR="Red"]WPA WPA2[/COLOR]You will have better luck with WPA2 only, not mixed mode.

---

### Post by Laize on 2012-10-22
> **chili555 said:**
> Without?? I don't understand. Without bcmwl-kernel-source, what was driving it?

When you scan, does it say your network is WPA and WPA2 mixed mode? ```
nm-tool
```You will have better luck with WPA2 only, not mixed mode.

Well as far as what is driving it?  I have no idea.

Perhaps I didn't uninstall them properly... but they're greyed out in the Drivers menu... and B43 is nowhere to be found on the system.. yet it scans.

Network security is WPA2 personal only, but the Network Mode is Mixed.

Dare I hope we're approaching an answer with these revelations?  I must agree that I was quite perplexed with the fact that it was doing more with (what I thought to be) no drivers than with.

Here's what nm-tool kicked back.


$ nm-tool

```
NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             unavailable
  Default:           no
  HW Address:        00:1A:70:3A:A3:F9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:C5:D8:AA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



```

---

### Post by Laize on 2012-10-22
Now that's strange.  Looking at the dump I see its driver is b43.

Would I be right in assuming that's somehow the culprit?

---

### Post by chili555 on 2012-10-22
> **Laize said:**
> Now that's strange.  Looking at the dump I see its driver is b43.

Would I be right in assuming that's somehow the culprit?Yes! Please do:```
sudo modprobe -r b43
sudo modprobe -r ssb [COLOR="Red"]<--it may already be gone[/COLOR]
sudo modprobe wl
```'-r' means remove. What changed/improved/degraded?

---

### Post by Laize on 2012-10-22
> **chili555 said:**
> Yes! Please do:```
sudo modprobe -r b43
sudo modprobe -r ssb [COLOR="Red"]<--it may already be gone[/COLOR]
sudo modprobe wl
```'-r' means remove. What changed/improved/degraded?

sudo modprobe wl kicked back

```
FATAL: Module wl not found.
```

---

### Post by chili555 on 2012-10-22
Please retrace your steps above to reinstall bcmwl-kernel-source and try again.

---

### Post by Laize on 2012-10-22
Downloaded package visa Synaptic in VB.

$ sudo dpkg -i bcmwl*

Restarting and crossing fingers.

---

### Post by Laize on 2012-10-22
Still no networks detected.

$ nm-tool
```
[sudo] password for laize: 

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:C5:D8:AA

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        00:1A:70:3A:A3:F9

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```

$ sudo modprobe wl gives no messages.

---

### Post by chili555 on 2012-10-22
> Broadcom Corporation BCM4321 802.11b/g/n [[COLOR="Red"]14e4:4329[/COLOR]]I have been Googling your device with disappointing results. I can't find *anyone* who reports it working. 

Since we are closest with b43 and not wl, let's troubleshoot from there:```
sudp apt-get remove --purge bcmwl-kernel-source
sudo modprobe b43
dmesg | grep b43
```I'm running low on mojo/talent/ideas.

---

### Post by Laize on 2012-10-22
Nothing.  I'm about to say screw it and just buy a new NIC.

---

### Post by chili555 on 2012-10-22
Let's have a nights sleep, boot up tomorrow and diagnose one more time. G'night!

---

### Post by Laize on 2012-10-23
I have one last Hail Mary.

It occurs to me that this NIC of mine is extremely old and I've simply been keeping it updated by windows update.

I've seen that it's possible to install 32-bit drivers on 64-bit Ubuntu and people have had success doing that.  I'd like to try it but I'm getting stonewalled in the process.  Can anyone help?

---

### Post by chili555 on 2012-10-23
> I've seen that it's possible to install 32-bit drivers on 64-bit Ubuntu Very doubtful in the case of wireless. My Hail Mary would be ndiswrapper if you have or can get the Windows XP .inf and .sys files.

If that doesn't work, I'd replace it. If it's a laptop, I'd check for whitelist and probably, unbelievably, look for a Broadcom. Aside from this beast and a very few others, Broadcoms are usually quite solid.

---

### Post by Laize on 2012-10-23
> **chili555 said:**
> Very doubtful in the case of wireless. My Hail Mary would be ndiswrapper if you have or can get the Windows XP .inf and .sys files.

If that doesn't work, I'd replace it. If it's a laptop, I'd check for whitelist and probably, unbelievably, look for a Broadcom. Aside from this beast and a very few others, Broadcoms are usually quite solid.

I can export the Win8 drivers.  I understand ndiswrapper produces disappointing results, if any, though.

---

### Post by Laize on 2012-10-23
Anyway it's a desktop PC.

Not sure if I should go for PCI or USB though.

---

### Post by Laize on 2012-10-23
Alright I'm gonna try ndiswrapper because not even the 32-bit version of ubuntu wants to build those drivers.

Is there a reasonable guide on using ndiswrapper?

---

### Post by chili555 on 2012-10-23
> **Laize said:**
> I can export the Win8 drivers.  I understand ndiswrapper produces disappointing results, if any, though.Usually, it produces a fine result; sometimes not. However, since your result now is less than disappointing, I'd certainly try.

Ndiswrapper requires the XP files and sometimes will use 2000. From *man ndiswrapper-1.9*:> DESCRIPTION
       ndiswrapper is two parts: user space tool that is used to install  Windows  XP drivers and kernel module to load the Windows XP drivers. Both are called ndiswrapper.

---

### Post by Laize on 2012-10-23
> **chili555 said:**
> Usually, it produces a fine result; sometimes not. However, since your result now is less than disappointing, I'd certainly try.

Ndiswrapper requires the XP files and sometimes will use 2000. From *man ndiswrapper-1.9*:

It HAS to be XP files?

Interesting... I wonder if the Broadcom All-in-one installer has them.  I'll have to dig through it.

---

### Post by chili555 on 2012-10-23
> **Laize said:**
> It HAS to be XP files?

Interesting... I wonder if the Broadcom All-in-one installer has them.  I'll have to dig through it.Here is a guide: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Laize on 2012-10-23
I appreciate it.  I'll let you know how it goes.

---

### Post by chili555 on 2012-10-23
I found this: [http://www.burnthesorbonne.com/ndiswrapper/g-l.html](http://www.burnthesorbonne.com/ndiswrapper/g-l.html)>  Card: Linksys WMP300N Wireless-N PCI Adapter

    Chipset: Broadcom Corporation BCM94321MP, 802.11b/g/Draft n
    pciid: [COLOR="Red"]14e4:4329[/COLOR], reported by lspci as Broadcom BCM43XG Rev. 1, but according to bcmwl5.inf, it should be BCM43XNG
    Driver: Linksys WMP300N_20061117_dr.exe
    Driver version: 4.100.15.5
    Fedora Core 6, x86-64, kernel 2.6.18-1.2849.fc6-x86_64
    ndiswrapper: ndiswrapper-1.31. 1.28rc2 works also
    Note: other Broadcom draft n drivers, such as the Dell and others do not work. They appear to support a device 14e4:4328 but not 4329. Only the newest Linksys driver supports 64 bit. Previous one did not. According to iwconfig, getting speeds in the 200 Mbit/s range, even with tx power turned down to 10dBm.
    As far as I can tell, draft N actually works.
    ‘This version of the driver also fixes a rootkit exploit’ see: [http://blogs.zdnet.com/Ou/?p=365](http://blogs.zdnet.com/Ou/?p=365)
    For older BCM cards, the file bcmwl5.inf does not contain the required data although I suspect the drivers themselves do. Other manufacturers such as Dell have released updated drivers fixing the vulnerability. See: [http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R140746&SystemID=INS_PNT_P4_9400&os=WXPX&osl=en&deviceid=9805&devlib=0&typecnt=1&vercnt=2&formatcnt=1&libid=5&fileid=187886](http://support.dell.com/support/downloads/download.aspx?c=us&cs=04&l=en&s=bsd&releaseid=R140746&SystemID=INS_PNT_P4_9400&os=WXPX&osl=en&deviceid=9805&devlib=0&typecnt=1&vercnt=2&formatcnt=1&libid=5&fileid=187886) *which does not include information for 14e4:4329 however.*

This may narrow the search somewhat.

---

### Post by chili555 on 2012-10-23
Assuming you have 32-bit...right?...try these.

Houdini's got nuthin' on me.

---

### Post by Laize on 2012-10-23
> **chili555 said:**
> I found this: [http://www.burnthesorbonne.com/ndiswrapper/g-l.html](http://www.burnthesorbonne.com/ndiswrapper/g-l.html)This may narrow the search somewhat.

It's like you read my mind.  I was just coming to ask about that.

One question, though.  If these are for 4329, what are the odds they'll work for 4321?

---

### Post by Laize on 2012-10-23
EDIT:  Figured out my problem with that error message.

However, using the GUI seems to produce nothing.  I select the .inf file and the button simply stays depressed.

UPDATE:  Did an install via terminal.  This came back.

$sudo ndiswrapper -i ~/4329/bcmwl5.inf
```

installing bcmwl5 ...
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete
couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incomplete

```

---

### Post by Laize on 2012-10-23
Another update.  I seem to have found the missing file, put it in the directory and ndiswrapper installed the driver.

That's the good news.

The bad news is that running $modprobe ndiswrapper seems to have gotten stuck in the terminal.

Nothing is locked up, but nothing is happening either.  I don'te ven have a prompt.  Process is just hanging.

---

### Post by chili555 on 2012-10-23
> One question, though. If these are for 4329, what are the odds they'll work for 4321?I think we want 432**9**.> 04:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11b/g/n [[COLOR="Red"]14e4:4329[/COLOR]] (rev 01)The pci.id is the identifier enumerated in the .inf file.> couldn't find "BCMWL564.SYS" in "/home/laize/4329"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/laize/4329" -
installation may be incompleteDitch the files you have and try these. I'd erase what you have:```
sudo ndiswrapper -e bcmwl5
sudo rm -rf /etc/ndiswrapper/*
```> The bad news is that running $modprobe ndiswrapper seems to have gotten stuck in the terminal.See if you can Ctrl+c and get out or just close the terminal; as Mrs. Chili says, "X it out."

---

### Post by chili555 on 2012-10-23
PS:> ;-----------------------------------------------------------------
; x86 - Win9x, Win2K, [COLOR="Red"]WinXP[/COLOR]
;
[BROADCOM]
        %BCM430B_DeviceDesc% = BCM43XZ, PCI\VEN_14E4&DEV_4303
        %BCM430G_DeviceDesc% = BCM43XG, PCI\VEN_14E4&DEV_4320
        %BCM430G_DeviceDesc% = BCM43XG, PCI\VEN_14E4&DEV_4318
        %BCM430G_DeviceDesc% = BCM43XG, PCI\VEN_14E4&DEV_4311
        %BCM430A_DeviceDesc% = BCM43XA, PCI\VEN_14E4&DEV_4321
        %BCM430A_DeviceDesc% = BCM43XA, PCI\VEN_14E4&DEV_431A
        %BCM430M_DeviceDesc% = BCM43XM, PCI\VEN_14E4&DEV_4324
        %BCM430M_DeviceDesc% = BCM43XM, PCI\VEN_14E4&DEV_4319
        %BCM430M_DeviceDesc% = BCM43XM, PCI\VEN_14E4&DEV_4312
        %BCM430G_DeviceDesc% = BCM43XG, PCI\VEN_14E4&DEV_4310
        %BCM430G_DeviceDesc% = BCM43XG, PCI\VEN_14E4&DEV_4313
        %BCM430N_DeviceDesc% = BCM43XNM, PCI\VEN_14E4&DEV_4328
        %BCM430N_DeviceDesc% = BCM43XNG, PCI\VEN_[COLOR="Red"]14E4[/COLOR]&DEV_[COLOR="Red"]4329[/COLOR]
        %BCM430N_DeviceDesc% = BCM43XA, PCI\VEN_14E4&DEV_432A

Added for illustration and the education of the curious.

---

### Post by Laize on 2012-10-23
New drivers installed fine.

ndiswrapper still hangs every time I execute $sudo modprobe ndiswrapper

---

### Post by chili555 on 2012-10-23
Any clues here?```
dmesg | grep ndis
```

---

### Post by Laize on 2012-10-23
$ dmesg | grep ndis
```
[    7.437166] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[    7.931625] usbcore: registered new interface driver ndiswrapper
[  162.825437] usbcore: deregistering interface driver ndiswrapper
[  162.831891] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  360.600329]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  360.600348]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  360.600365]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  360.600465]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  360.600478]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  480.597239]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  480.597259]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  480.597275]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  480.597376]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  480.597388]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  600.594155]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  600.594174]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  600.594191]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  600.594291]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  600.594303]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  720.591083]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  720.591103]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  720.591119]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  720.591221]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  720.591233]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  840.588005]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  840.588025]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  840.588042]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  840.588142]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  840.588154]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  960.584892]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  960.584911]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  960.584928]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  960.585028]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  960.585040]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[ 1080.581823]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[ 1080.581843]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[ 1080.581860]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[ 1080.581960]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[ 1080.581972]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[ 1200.578718]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[ 1200.578738]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[ 1200.578755]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[ 1200.578855]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[ 1200.578867]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[ 1320.575658]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[ 1320.575678]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[ 1320.575694]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[ 1320.575795]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[ 1320.575808]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[ 1440.572553]  [<ffffffffa0f1dd48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[ 1440.572573]  [<ffffffffa0f2d377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[ 1440.572589]  [<ffffffffa0f2dca0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[ 1440.572689]  [<ffffffffa0f1f28d>] loader_init+0x9d/0x150 [ndiswrapper]
[ 1440.572702]  [<ffffffffa0f60073>] wrapper_init+0x73/0x1000 [ndiswrapper]

```

---

### Post by Laize on 2012-10-23
Saw ndiswrapper requires drivers that match architecture.

got 64-bit drivers and they installed.

modprobe ndiswrapper worked

Now to figure out how to set up the wireless network with it.

---

### Post by Laize on 2012-10-23
Ok here's the story so far of what I've been doing.  (Uninstalling drivers properly after failure).

BCMWL5 32-bit (Chili's version) - terminal hangs on $modprobe ndiswrapper
BCMWL6 32-bit - terminal hangs on $modprobe ndiswrapper
BCMWL6 64-bit - ndiswrapper won't claim the wireless NIC

Looking for BCMWL5 64-bit so I can make it a whole set .

---

### Post by Laize on 2012-10-23
If there's one thing anyone should take away from this thread if they stumble across it via Google it's that you should avoid buying wireless NICs with the BCM4321 chipset.

---

### Post by Laize on 2012-10-25
Honestly, to heck with this.

Can anyone recommend me an excellent Wireless NIC that's preferably PCI, but USB will do?

My ideal card would be either PCI or PCIe with a high-gain antenna packaged with it.  Because of the location of my access point I need to place the antenna on top of the desk.

---

### Post by alex110 on 2013-10-01
Almost one year later after this last post, and I'm also stuck with this issue :-(

With b43 or wl driver my old MacBookAir with BCM4321 can't scan any wireless with Scan_results error (-22). It's a BCM4321 [14e4:4328].

Did anyone found a fix for this? I've just made a fresh installation with Ubuntu 13.04 on and old 2010 MacBookAir.

Thanks,
Alex

---

### Post by varunendra on 2013-10-02
> **alex110 said:**
> Almost one year later after this last post, and I'm also stuck with this issue :-(

With b43 or wl driver my old MacBookAir with BCM4321 can't scan any wireless with Scan_results error (-22). It's a BCM4321 [14e4:4328].

Did anyone found a fix for this? I've just made a fresh installation with Ubuntu 13.04 on and old 2010 MacBookAir.

Thanks,
Alex

Welcome to the forums Alex !

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should give us enough information to see if there are any obvious culprits. If not, we may try the latest version of the sta (wl) driver from [here]("http://archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/").

---

