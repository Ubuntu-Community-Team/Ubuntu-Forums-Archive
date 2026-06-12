---
title: "Samba via Linksys Wireless G router"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by absolutezero1287 on 2009-03-02
I made an illustration showing how my wireless network is set up. My goals are to enable file and printer sharing with samba. I'm on Ubuntu 8.04 and the other computer is using Windows XP home edition.

For printer sharing I was wondering if my router would have to forward port 631 for CUPS or is all this taken care of by Samba? I have already installed Samba.

[IMG]http://i469.photobucket.com/albums/rr54/absolutezero1287/My_setup.jpg[/IMG]

---

### Post by dmizer on 2009-03-02
Your brother's XP computer is not on a "magical interwebs connection". An "interwebs" connection is the WAN or ethernet connection between your router and the modem (your connection to the "interwebs"). Your brother is on your local network (LAN), exactly the same as if his computer was connected with an ethernet cable to port 2 in your router. So, you do not need to do any configuration on your router at all.

All you need to do is correctly configure a samba server on your Ubuntu box (please see the first link in my sig), then configure file an printer sharing via the CUPS interfaces (under System > Administration > Printing).

---

### Post by absolutezero1287 on 2009-03-02
> **dmizer said:**
> Your brother's XP computer is not on a "magical interwebs connection".

That was meant to be a joke....

---

### Post by dmizer on 2009-03-02
> **absolutezero1287 said:**
> That was meant to be a joke....

I understand that. Problem is though, that "interwebs" is a common slang term for internet. I just wanted to make sure we were both on the same page.

---

### Post by absolutezero1287 on 2009-03-02
> **dmizer said:**
> I understand that. Problem is though, that "interwebs" is a common slang term for internet. I just wanted to make sure we were both on the same page.

Oh yea, I'm definitely following what you're saying. The magical interwebs connection thing was just a joke about how my brother's computer is on wireless, hence it being "magical". Anyways, I'll check out the how-to and if I run into any problems then I'll post here.

---

### Post by x1101 on 2009-03-02
I personally suggest using webmin to config samba (and everything else)
Sadly last I checked it was not in any repo, but is provided in a .deb package [here]("http://www.webmin.com/download.html"). I have found this makes setting up ANYTHING easy. And if you want to understand the config files, it modifies them, so you can look them after and get a better feel for what does what.

---

### Post by dmizer on 2009-03-02
> **x1101 said:**
> I personally suggest using webmin to config samba (and everything else)
Sadly last I checked it was not in any repo, but is provided in a .deb package [here]("http://www.webmin.com/download.html"). I have found this makes setting up ANYTHING easy. And if you want to understand the config files, it modifies them, so you can look them after and get a better feel for what does what.

It's no longer in the repositories because of security concerns. It also requires you to have a properly configured web server. This is overkill, and overly complex for simple peer to peer file sharing.

More information on Webmin and Ubuntu here: [https://answers.launchpad.net/ubuntu/+question/2873](https://answers.launchpad.net/ubuntu/+question/2873)

---

### Post by x1101 on 2009-03-03
Actually from what I remember of my own setup it doesnt require you to have a working websever setup. It runs a mini one on its own. I never said that i was the most secure, but as far as admining anything, its much easier. I spent like 4 hours hacking around with Samab.conf, then spent 45 minutes installing webmin and getting it working that way...

---

### Post by absolutezero1287 on 2009-03-03
Ok, so I followed the instructions on the link that was posted. I'm not sure where to go from here. How would someone print something from Windows and get the request sent to my machine? Do I have to make any changes to CUPS for this? Also, I have shared my Music folder, how do you access it from the Windows box?

---

### Post by dmizer on 2009-03-03
Perhaps this is a better howto for printing with CUPS: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

If you've shared your music folder, you should be able to access it from Windows through my network places.

---

### Post by absolutezero1287 on 2009-03-03
Actually I just put a link to my music folder in the shared folder. I really haven't made any progress at all. 

[HOWTO: Setup Samba Peer-To-Peer With Windows]("http://ubuntuforums.org/showthread.php?t=202605")

I'm not sure what the problem is but I suspect it has something to do with the "wins support" part of the smb.conf. I'm using DHCP but I'm fairly certain that I have a fixed IP address.

I don't really understand how to set up windows. I tried to add a network printer and it just says that it can't find it. I don't really now what I'm doing wrong.

---

### Post by dmizer on 2009-03-03
> **absolutezero1287 said:**
> Actually I just put a link to my music folder in the shared folder. I really haven't made any progress at all. 

[HOWTO: Setup Samba Peer-To-Peer With Windows]("http://ubuntuforums.org/showthread.php?t=202605")

I'm not sure what the problem is but I suspect it has something to do with the "wins support" part of the smb.conf. I'm using DHCP but I'm fairly certain that I have a fixed IP address.

I don't really understand how to set up windows. I tried to add a network printer and it just says that it can't find it. I don't really now what I'm doing wrong.

For printing, please read this link carefully: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP) it includes directions both on how to share your printer, and how to configure Windows to connect to it.

For file sharing:
Please post your current smb.conf

Also, install "smbfs" with the following command:
```
sudo aptitude install smbfs
```

Then post the output of
```
smbtree
```

---

### Post by absolutezero1287 on 2009-03-03
smbfs is already installed
smbtree returns no output
As for the how-to guide I read it very carefully and XP still won't pick up my printer nor will XP find any shared folders. It might have something to do with the LAN. The XP computer has two connections. One is the wireless and the other calls itself a LAN and is trying to use an ethernet card that isn't connected to anything. The computer uses a wireless G usb adapter to pick up the wifi.

here's the smb.conf
```
[global]
    ; General server settings
    netbios name = SATORI
    server string =
    workgroup = COMP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/chowder/shared_files/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = chowder
    force group = chowder
```

---

### Post by dmizer on 2009-03-03
On the Ubuntu computer, please post the output of this command:
```
sudo iptables -L
```

Try temporarily disabling any firewalls on the Windows machine.

---

### Post by absolutezero1287 on 2009-03-03
```
Satori~$>sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

firewall disabled :)

---

### Post by dmizer on 2009-03-03
Double check your XP computer to make sure it's a part of the "COMP" workgroup.

For testing purposes, try this smb.conf:
```
[global]
    ; General server settings
    netbios name = SATORI
    workgroup = COMP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    interfaces = lo, eth0
    bind interfaces only = true
    passdb backend = tdbsam
    security = share
    null passwords = true
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

[MyFiles]
    path = /home/chowder/shared_files/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = chowder
```

Also, please post ->
From the Ubuntu computer:
```
ifconfig
```

From the Windows computer:
```
ipconfig
```

---

### Post by absolutezero1287 on 2009-03-03
```
Satori~$>ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:7f:2b:70  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe7f:2b70/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59080 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85727466 (81.7 MB)  TX bytes:10245122 (9.7 MB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:160253 (156.4 KB)  TX bytes:160253 (156.4 KB)

```

```

ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : LEO
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : hsd1.fl.comcast.net.

Ethernet adapter Local Area Connection:

        Media State . . . . . . . . . . . : Media disconnected
        Description . . . . . . . . . . . : GVC-REALTEK Ethernet 10/100 PCI Adap
ter
        Physical Address. . . . . . . . . : 00-C0-A8-88-8D-57

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : hsd1.fl.comcast.net.
        Description . . . . . . . . . . . : Compact Wireless-G USB Adapter
        Physical Address. . . . . . . . . : 00-16-B6-53-47-C1
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 68.87.74.162
                                            68.87.68.162
                                            68.87.73.242
        Lease Obtained. . . . . . . . . . : Wednesday, March 04, 2009 3:10:37 AM

        Lease Expires . . . . . . . . . . : Thursday, March 05, 2009 3:10:37 AM

```

---

### Post by dmizer on 2009-03-04
In Windows, click: start > run

And enter this command:
\\SATORI

If Satroi's share appears in the explorer window, right click on "MyFiles" and select "Map network drive". Make sure "Reconnect at Logon" is selected, and click "Finish".

If SATORI's share does NOT appear, try the same with satori's IP address instead:
\\192.168.1.101

That should give you access to your share from Windows.

---

### Post by dmizer on 2009-03-04
For printing:

On your Ubuntu box. Open a browser window and go to this url:
[http://localhost:631/printers/](http://localhost:631/printers/)

Post the results here, either in a screenshot or in text form.

---

### Post by absolutezero1287 on 2009-03-04
[IMG]http://i469.photobucket.com/albums/rr54/absolutezero1287/CUPS.png[/IMG]

---

### Post by absolutezero1287 on 2009-03-04
On the windows box I got an error message saying:

"No network provider accepted the given network path"

---

### Post by dmizer on 2009-03-04
On Windows, go to:
Start > printers and faxes > add a printer

Click:
Next

Select:
A network printer, or printer attached to another computer

Select:
Connect to a printer on the internet or on a home or office network.

Enter this URL in the blank:
[noparse]http://192.168.0.101/printers/Deskjet_F4200_series[/noparse]

Click:
Next

You'll have to add the printer drivers at this point.

---

### Post by dmizer on 2009-03-04
> **absolutezero1287 said:**
> On the windows box I got an error message saying:

"No network provider accepted the given network path"

Either your Windows computer has a firewall in the way, or your Windows computer is not a member of the same workgroup.

Check this by going to:
Start > control panel > system > computer name.

Is the workgroup listed as "COMP"? If it's not the same, change it and reboot. Then try directions from [post 18](http://ubuntuforums.org/showpost.php?p=6834276&postcount=18) again.

If you still have problems, please post the output of (on the Ubuntu computer):
```
sudo /etc/init.d/samba restart
```

Edit:
Also, please post the output of:
```
testparm
```

---

### Post by absolutezero1287 on 2009-03-04
```
Satori~$>testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[print$]"
Processing section "[printers]"
Processing section "[MyFiles]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = COMP
	interfaces = lo, eth0
	bind interfaces only = Yes
	security = SHARE
	null passwords = Yes
	passdb backend = tdbsam
	syslog only = Yes
	announce version = 5.0
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = CUPS

[print$]
	path = /var/lib/samba/printers
	write list = root
	create mask = 0664
	directory mask = 0775
	guest ok = Yes

[printers]
	path = /tmp
	guest ok = Yes
	printable = Yes
	browseable = No

[MyFiles]
	path = /home/chowder/shared_files/
	force user = chowder
	read only = No
	create mask = 0644
	guest ok = Yes
```

I actually turned off the firewall. I will get on this tomorrow. Unfortunately its 0033 over here and the computer is in my brother's room. He's got class tomorrow.

Thank you for the help, I'll keep you posted.

---

### Post by absolutezero1287 on 2009-03-04
The name of the computer is LEO and the workgroup is MSHOME. Windows won't let me change it. It says that I can only change it until networking is installed, which I don't understand why it isn't installed. Everything would be so much easier if my brother just used Ubuntu.

For now this is what I've done.
```

sudo /etc/init.d/samba stop

```

Changing parameters of the smb.conf to match that of the windows PC.
All I changed was one line and here it is:
```

workgroup = MSHOME

```

```

sudo /etc/init.d/samba restart

```

And now following the steps in [post 18]("http://ubuntuforums.org/showpost.php?p=6834276&postcount=18") I get the same error in Windows.
```

No network provider accepted the given network path.

```

---

### Post by dmizer on 2009-03-04
On Windows:

Go to:
Start > Control panel > network connections

Right click on the wireless connection and select "properties"

Under "This connection uses the following items:", is there an entry for "File and Printer sharing for Microsoft networks"?

If not, you'll have to install it. To install it, I beleive you'll need the Windows install CD.

Also:
From Windows, can you ping Ubuntu?
From Ubuntu, can you ping Windows?

---

### Post by absolutezero1287 on 2009-03-04
> **dmizer said:**
> On Windows:

Under "This connection uses the following items:", is there an entry for "File and Printer sharing for Microsoft networks"?

Yes, and it is enabled

> **dmizer said:**
> 
Also:
From Windows, can you ping Ubuntu?
From Ubuntu, can you ping Windows?
How would I do that?

---

### Post by dmizer on 2009-03-04
> **absolutezero1287 said:**
> How would I do that?

In Windows:
Start > run
Type -> cmd
and hit enter

Type -> ping SATORI

In Ubuntu:
Open a terminal and type -> ping LEO

Do the same on both Ubuntu and Windows with IP as well:
On Windows:
ping satori.ip.address.here

On Ubuntu:
ping leo.ip.address.here

---

### Post by absolutezero1287 on 2009-03-04
Both give me an unknown host error

---

### Post by dmizer on 2009-03-04
Did you also get an "unknown host" error when pinging by IP address as well?

In Ubuntu you can run ifconfig. The IP address is labeled as "inet addr"
In Windows you can run ipconfig.

---

### Post by absolutezero1287 on 2009-03-09
Now I have a new problem...my printer won't print at all. :(

---

### Post by dmizer on 2009-03-09
Are you absolutely positve that your brother's computer is connected to your wireless network and not a neighbor's?

> **absolutezero1287 said:**
> Now I have a new problem...my printer won't print at all. :(
You should probably post a new thread for this.

---

### Post by absolutezero1287 on 2009-03-10
I'm 100% positive. Its definitely connected to my wireless network.

---

### Post by absolutezero1287 on 2009-03-23
I actually tried to upgrade to 8.10 and ran into a lot of problems so I had to do a fresh install. I got the printer working now all I have to do is get samba. I'll post again once I'm up to speed.

---

