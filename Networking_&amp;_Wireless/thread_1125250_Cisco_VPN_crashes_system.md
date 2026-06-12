---
title: "Cisco VPN crashes system"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by dkinfl on 2009-04-14
I have a Dell Latitude E6500 with the Intel Centrino vPro 2 chipset.  I am running the Cisco VPN client.  After I connect to the VPN, and I start to send traffic through the tunnel, the laptop freezes, and the Caps and Scroll lock flash.  My only recovery at this point is to power off the computer.  I have seen this issue on other forums but I have yet to find a solution.

I am running Ubuntu 8.10.  Any help is appreciated.  It appears to work fine over an Ethernet connection.  It only does this on WiFi.

---

### Post by Mordac85 on 2009-04-14
Have you enabled logging or checked your system logs?  Normally the Cisco client gives you some good indicators of any issues, but if it locks up, maybe not.

Personnally, I didn't like their interface and switched to kvpnc (I'm on kubuntu).  I just pointed to my profiles and it works like a champ w/o any major changes.  Since that's just a GUI interface for vpnc maybe you could try using that as an alternative?

---

### Post by jerryarn on 2009-09-28
I am having the same issue with the same hardware.  Did you ever figure this out?

---

### Post by agmonzon on 2009-10-05
Hi all

I've found the same problem.
I have a Dell vostro 1500 with INtel PRO/Wireless 3945ABG network card, Ubuntu 9 (kernel 2.6.28) and Cisco VPN cliente 4.8.02
The system crash sometimes, and the Caps and Scroll lock flash
I've read some posts about this issue, but nobody has written the definitive solution
The log file (/var/log/messages) doesn't say something about wifi card error
Please, is there anybody who has resoved this problem ??

Many Thanks

---

### Post by skinnejay on 2009-10-09
Running Karmic 2.6.31-12 and having the same problems on wifi (linksys wireless g usb adapter). Computer freezes immediately when I enter the command in the terminal and the caps lock and scroll key light up. hoping for a solution soon. curious about vpnc through the network manager but does it allow certificates?

---

### Post by lavadisco on 2009-10-15
I also have this problem. Everything is fine, I can tunnel into my work machine and exchange files without issue, but as soon as I use any browser (Firefox and Seamonkey), the entire computer freezes and I get the caps/scroll lock flashing lights.

---

### Post by jonobr on 2009-10-15
Hello

Im using VPNC with the KVPNC gui,

I import my cisco PCF file that I got from my IT group and it works ok.


If you have a pcf file Im wondering if you could try that to rule out application problems

---

### Post by domkle on 2009-11-18
I am having same problem here, Dell Inspiron 1525 using Ethernet
Affected me before Karmic, but only when using Wifi, thought about a driver (Broadcom) problem.
Now it happens even on Ethernet, not good

Going nowhere I tried the vpnc workaround advocated before in the strip
I have to say, it is working for me
For my job I rely quite heavily on VPNs, and have to switch between severals.
no problems
Many thanks to the authors of pcf2vpnc and cisco-decrypt!

---

### Post by Schlummi on 2009-11-22
> **agmonzon said:**
> Hi all

I've found the same problem.
I have a Dell vostro 1500 with INtel PRO/Wireless 3945ABG network card, Ubuntu 9 (kernel 2.6.28) and Cisco VPN cliente 4.8.02
The system crash sometimes, and the Caps and Scroll lock flash
I've read some posts about this issue, but nobody has written the definitive solution
The log file (/var/log/messages) doesn't say something about wifi card error
Please, is there anybody who has resoved this problem ??

Many Thanks
Hello all out there
same troubles here. My system is a HP dv3-2030ez running xubuntu 9.10.
the wlan chip seems to an Intel PRO/Wireless 5100 AGN and i also use cisco vpnclient 4.8.02.0030. the effect is the same, the caps lock led starts flashing and everyting stops working.

I know the vpnc, but I don't like this opportunity. The connection is not realy stable.

other question, has anybody with that problem ever tried the 'cisco anyconnect vpn client' instead of the 'cisco vpn client'?

Regards Florian

---

### Post by corydd on 2009-11-22
I ran across a workaround claiming the problem occurs when running WIFI with a multi-core CPU.  The workaround was to disable all but core 0 while running vpnclient, and re-enable the cores after finished with vpn.  It seems to be working for me on a dual core laptop.

sudo -i
[I]echo 0 > /sys/devices/system/cpu/cpu1/online
#  start vpnclient
# do stuff
# exit vpnclient
[/I]*echo 1 > /sys/devices/system/cpu/cpu1/online*

[http://www.lamnk.com/blog/computer/cisco-vpn-client-freezes-system-with-dual-core-cpu/](http://www.lamnk.com/blog/computer/cisco-vpn-client-freezes-system-with-dual-core-cpu/)

---

### Post by ncubede on 2009-12-11
I have a Dell Latitude E6500 with 8G RAM, Karmic, and lots of VPN usage - on 24h.  I had real issues with Ubuntu freezing the computer, killing USB, sound, until I updated the BIOS to E6500 A18 a few days ago.  It seems there was an overheating issue in the BIOS, and the USB hardware was not always properly initialized.

Then suddenly all stability issues with and without vpn went away.  I almost exclusively switched from cisco vpn to vpnc, even if the re-keying fails after 24h (so vpnc needs to be reconnected), as it is really stable otherwise and does allow me to accept or decline the request from the vpn concentrator to route all traffic through the corporate network. I don't want my youtube traffic to be routed across the ocean ;-)  The biggest downside of vpnc is that it can not tunnel through tcp, you have to use udp.

---

### Post by mdm_sd on 2009-12-30
Updating the BIOS (on a DELL E6500, w/8gb memory, w/ latest karmic (64 bit 2.6.31-16-generic) to the A18 BIOS patch from DELL still causes the cisco VPN to crash using the wireless network adapter when evolution MAPI tries to synchronize.  There is no information in the logs to detect what module is causing the crash.  Suspicion may be in a interaction with the structure change required to compile the cisco VPN client (4.8.02) and the ia32-libs package required to have the vpn client work.  Seems to be some type of memory boundary issue with large amounts of data.  Also noticed crash with SVN synchronization on checkout of large projects.  Any fix for this is greatly appreciated. :!:

---

### Post by crazysexycool on 2010-01-11
Hi all i am having a very similar issue every time i start my cisco VPN 

sudo /usr/local/bin/vpnclient connect company name

this freezes my entire pc on solution is to reboot by holding the power button down.

can anyone help 

running ubuntu 9.10

---

### Post by ncubede on 2010-01-22
> **mdm_sd said:**
> Updating the BIOS (on a DELL E6500, w/8gb memory, w/ latest karmic (64 bit 2.6.31-16-generic) to the A18 BIOS patch from DELL still causes the cisco VPN to crash using the wireless network adapter when evolution MAPI tries to synchronize.  There is no information in the logs to detect what module is causing the crash.  Suspicion may be in a interaction with the structure change required to compile the cisco VPN client (4.8.02) and the ia32-libs package required to have the vpn client work.  Seems to be some type of memory boundary issue with large amounts of data.  Also noticed crash with SVN synchronization on checkout of large projects.  Any fix for this is greatly appreciated. :!:

In the end MY instability was caused by 2 x 4g elpida memory so dimms, which were used in the manufacturing of E6500 with 8gb for a while.  Then Dell used Samsung, instead, which no longer causes instability.  Apparently there was also a certain randomness or dependency on the exact environment, see this link (last post) [Dell Support Forum Link]("http://en.community.dell.com/forums/t/19256129.aspx?c=us&l=en&cs=04&s=gen&PageIndex=2")

For me it pretty much castrated usb, made vpn erratic. and caused intermittent freeze. you may want to use dmidecode to check your ram type, just in case.  I did NOT have a repeatable test case when a start of cisco vpn would always freeze immediately, it froze after a while.  Dell exchanged my memory without giving me any issues, but my laptop is still under warranty.

For completeness' sake: while I was experimenting what might help, I did add a few boot parameters trying to make DMA more stable, which may or may not have had any impact. I use (from /proc/cmdline):
> 
BOOT_IMAGE=/boot/vmlinuz-2.6.31-18-server root=UUID=02fc386a-75b5-4a61-8872-7aa73727a923 ro debug reboot=bios acpi_osi=Linux pci=nommconf swiotlb=32768


---

### Post by jamaj on 2010-04-10
Today i was using my DELL inspiron 1525 at University Campus.

My kernel is Linux KAOS 2.6.27-17-generic #1 SMP Fri Mar 12 03:09:00 UTC 2010 i686 GNU/Linux

This was the first time this problem raised in this machine. Now i'm home, and using my wireless router this never happened, and the problem did not happen again.

So, i think something occurs only with my University wireless network. I already read that this simptom (caps and scroll lock leds blinking) means that kernel panic occurred.

But why only with some wireless networks? Do someone knows which program causes this kernel panic?

Note: when i use univesity campus wireless networks, the network led on my inspiron 1525 blinks much more than when i connect to others. So, maybe something is wrong with university compus router that causes kernel panic.

---

### Post by Cato2 on 2010-04-14
> **jamaj said:**
> So, i think something occurs only with my University wireless network. I already read that this simptom (caps and scroll lock leds blinking) means that kernel panic occurred.

But why only with some wireless networks? Do someone knows which program causes this kernel panic?

This might be the wireless driver - worth trying the same activities via Ethernet to see if you get the crash, or trying a different wireless card (maybe a USB stick).  I have had kernel panics on a specific wireless card (Ralink RT2500?) that were solved in a later kernel that had a fixed driver.

> Note: when i use univesity campus wireless networks, the network led on my inspiron 1525 blinks much more than when i connect to others. So, maybe something is wrong with university compus router that causes kernel panic.

That may be because there's just a lot more traffic on the wireless access point (WAP) you are using at the university.  It's unlikely that the university router could cause your crash, but the panic that I had was traffic dependent - it only happened during a very large file transfer lasting some hours.  Even though much of the traffic on the shared WAP is not for you, it still affects the driver I would think.

---

### Post by schnupfy on 2010-05-11
Got the same problem here. Running Thinkpad T510 with lucid 64bit. I can connect to my company VPN fine, but as soon as I access the internet the system freezes and I have to reset it.

When I disable my wireless it seems to be stable, BUT I also have KVM in use with a couple of Domains. When I now activate a client domain, the system gets slower and slower and I can't even issue commands from the terminal even more.

Cheers,
Marcus

---

### Post by SagarDoke on 2010-05-20
I'm having the same problem with my Dell Latitude D630.
And it happens with both WiFi and Ethernet.
I tried above solution also (shutting down 1 core...), but no success.
In my case no CAP/Scroll lock flashing, whole system gets freeze and only solution is to reboot the PC by holding the power button. :(

Also I cant use VPNC, I have to import Cisco VPN certificate and it wont work with VPNC.

Thanks
Sagar

---

### Post by clrg on 2010-07-26
I have the same problem. Every time I initiate a VPN connection, the kernel panics. It doesn't matter whether I am using wireless or ethernet. 

Has anyone found a solution to this problem yet? Any help is greatly appreciated. I can't connect to my corporate network without the VPN client, and I'd rather not install faildows because of this issue.

---

### Post by Cato2 on 2010-07-27
You need to find out more about the crash - look at the error messages leading up to the time of the crash (make sure your PC clock is accurate) - ```
less /var/log/kern.log
``` is the most useful one probably.  This should give a clue as to where and why the kernel is crashing (e.g. driver or elsewhere).  Also, Google for 'diagnose linux crash'.  Often there are useful threads in non-Ubuntu forums for less common problems like this.

Once you have some of the error messages around the crash, Google for those and see if there are solutions - possibly some boot-time command line options (applicable via Grub's /boot/grub/menu.lst on Ubuntu <= 9.10, different config in Grub 2 in 10.04 onwards if a new install).

Have you tried using a different network connection?  It could be your WiFi driver at fault, so temporarily try an Ethernet connection and also a USB WiFi dongle not the built-in one.  If it doesn't recur, you need to see if the specific bug has been reported already against the wireless driver.

Have you tried this suggest to disable multi-cores during the VPN session? [http://ubuntuforums.org/showpost.php?p=8368160&postcount=10](http://ubuntuforums.org/showpost.php?p=8368160&postcount=10)   - or simply use vpnc instead of the Cisco VPN Client.

I've had the VPN Client on Windows cause Firefox crashes, but of course it should not lead to Linux crashes.

---

