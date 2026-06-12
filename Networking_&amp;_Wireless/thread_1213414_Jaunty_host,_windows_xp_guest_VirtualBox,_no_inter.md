---
title: "Jaunty host, windows xp guest VirtualBox, no internet for guest"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by smoosh on 2009-07-14
OK, using Jaunty as host and VirtualBox 3.0.2.  Everything went smooth with the Windows XP installation, but nothing I do will get me internet in the virtual Windows environment.  I have tried changing the Network Adapter settings in VirtualBox to every possible configuration, tried diagnosing it in Windows, tried turning off firewalls in Windows, tried making a bridge manually by giving Windows a static IP, nothing works.  Whenever I open Internet Explorer it says "Internet Explorer cannot display the web page".  No matter what.  Any ideas, it's driving me cookoo....  Oh, I am using Ubuntu Server so I can see all my memory.

Thanks!

---

### Post by superprash2003 on 2009-07-15
post output of ipconfig from the windows command prompt.. is the virtual box networking option set to bridging?

---

### Post by fho on 2009-07-15
Same here. Guest is Win XP (SP2, German), tried following Network adapters:

* Intel Pro/1000 T  Server (bridge, eth0)
* Pcnet FAST III (NAT)
* Pcnet FAST III (bridged, eth0)

Fixed and dynamic IPs tested. Dynamic IP never gets assigned.

When I try a "ping 192.168.1.1" (fixed IP configured as 192.168.1.20) the (translated) error message is: "Error initializing Windows sockets interface. Error code 0".

ipconfig /all output (non-static IP configuration) is:

> 
Windows-IP-Konfiguration

        Hostname. . . . . . . . . . . . . : myhost
        Primäres DNS-Suffix . . . . . . . :
        Knotentyp . . . . . . . . . . . . : Unbekannt
        IP-Routing aktiviert. . . . . . . : Nein
        WINS-Proxy aktiviert. . . . . . . : Nein

Ethernetadapter LAN-Verbindung 3:

        Verbindungsspezifisches DNS-Suffix:
        Beschreibung. . . . . . . . . . . : Intel(R) PRO/1000 T-Serveradapter
        Physikalische Adresse . . . . . . : 08-00-27-00-E3-A2
        DHCP aktiviert. . . . . . . . . . : Ja
        Autokonfiguration aktiviert . . . : Ja
        IP-Adresse. . . . . . . . . . . . : 0.0.0.0
        Subnetzmaske. . . . . . . . . . . : 0.0.0.0
        Standardgateway . . . . . . . . . :
        DHCP-Server . . . . . . . . . . . : 0.0.0.0
On the host there is a "vboxnet0" interface that seems to be down but it is not possible to bring  it up via "ifup vboxnet0".

Any further information required that could help you?

---

### Post by smoosh on 2009-07-15
Well, this is great.  When I do on "ipconfig" in Windows, I get nothing.  It says "Windows IP Configuration" and then it's just blank.

---

### Post by smoosh on 2009-07-15
I had the Network set to "bridging" a few different times, but it didn't make a difference, and all the other threads I found seemed to point toward NAT, so it's set for that.

Thanks!

---

### Post by smoosh on 2009-07-15
Set it to bridged and still the output of "ipconfig" is blank.  Do I need to install Windows drivers?  When I first open Windows it says "new hardware found" and tells me there are ethernet adapters there (multiple since I have all 4 on, hoping one combination will work)... I know zero about Windows, but I figured since it's a virtual machine, I shouldn't need to install drivers, right?

---

### Post by DrDevice on 2009-07-15
> **smoosh said:**
> I know zero about Windows, but I figured since it's a virtual machine, I shouldn't need to install drivers, right?

Actually, as it's a VM, you NEED to install drivers, just like a physical machine. :grin:  Start your Virtual Windows, and when all booted and ready, go to "Devices->Install Guest Additions", it should act like you popped a driver CD in and ask you to install a bunch of stuff.  These are the drivers for your virtual hardware to get access to your real hardware.  Reboot the VM and it should be much smoother now.

I'd reduce your virtual network cards back down to one just to be safe and streamline your session. =)

---

### Post by smoosh on 2009-07-15
I did install them through Windows and it didn't help any, but when I try and go through VirtualBox by going to Device - Install Guest Additions, nothing happens. 

I guess I could just go online, download the driver for the specific ethernet adapter I have it set to, and install it that way...

---

### Post by smoosh on 2009-07-15
It works!  I downloaded and installed the driver and everything is Ok now, thanks for the help, ya'll!!

---

### Post by smoosh on 2009-07-15
Hmmm.... How do I change this thread to "solved"??

---

### Post by fho on 2009-07-16
So, what exactly did you do now to make it work? You just downloaded some drivers for some ethernet adapter in the guest operating system and installed them? But I thought your problem was exactly that you could not access the internet from within the guest OS? So, how did you download them?

Could you please tell me your settings regarding network adapter (Pcnet FAST III?) and  connection type (NAT?).

---

### Post by fho on 2009-07-17
Argh, I got it now. The Windows TCP/IP stack was somehow corrupted.   After entering the following commands in DOS shell and rebooting the guest OS the network adapter successfully connected.

> 
netsh winsock reset 
netsh int ip reset c:\resetlog.txt


---

### Post by fho on 2009-07-17
I guess we can consider this issue to be solved.

---

