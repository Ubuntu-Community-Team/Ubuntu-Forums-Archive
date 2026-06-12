---
title: "Landisk mounting trouble -- please help!"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by mikey_likesit on 2009-07-20
I'm going absolutely bonkers here trying to get my fresh Jaunty install to mount (or even acknowledge the existence of) my network hard drive (an I-O Data Landisk). I've looked through a ton of forums and found various similar threads with various solutions, but none of them have worked for me. Here are examples of what I've tried, with no success:

sudo mount -t cifs //192.168.0.200/disk /mnt/networkdisk
(according to the hard drive's manual it automatically takes the address 192.168.0.200/disk, I created the directory /mnt/networkdisk myself)

sudo smbmount /192.168.0.200/disk /mnt/networkdisk

sudo mount 192.168.0.200:/disk /mnt/networkdisk

sudo mount ntfs 192.168.0.200:/disk /mnt/networkdisk
(I formatted the drive myself, so I'm sure about the NTFS format)

sudo mount 192.168.0.200:/disk /mnt/networkdisk cifs rw,user,noauto, exec  0   0

su
smbmount //192.168.0.200/disk /mnt/networkdisk -o uid=mike,gid=1000  0   0

I even tried to scan the network for devices using "nmap 192.168.0-255,1-255" but got no result.

Many of these commands, when executed just hung a while and timed out after about 5 minutes, like the computer was waiting for the drive to respond. I've got this drive plugged in to a network hub through its built-in LAN plug, and on my other computer running XP there's no problem at all.

I am admittedly not that up on my linux, but I would've thought one of the above would work... can I ask also, should I be looking for 
//192.168.0.200/disk
or
/192.168.0.200/disk
or
192.168.0.200:/disk
? what's the difference between them, if any?

I really hope someone can help me out here, I'm at my wits end and about to go postal on my computer!

---

### Post by komputes on 2009-07-20
Have you tried putting this in a nautilus address bar?
smb://192.168.0.200/SHARE_NAME_HERE

---

### Post by mikey_likesit on 2009-07-20
yes, I tried that as well, Nautilus just sits there for a while like it's thinking, then gives me this error:

Could not display "smb://192.168.0.200/disk/".
Error: Failed to mount Windows share
Please select another viewer and try again.

what other viewer could I use? Is this likely to make a difference?

---

### Post by jamest09 on 2009-07-20
Firstly, can you ping the device?

---

### Post by mikey_likesit on 2009-07-20
actually no, here's what I get:

mike@mike-laptop:~$ ping 192.168.0.200
PING 192.168.0.200 (192.168.0.200) 56(84) bytes of data.
From 219.103.128.97 icmp_seq=5 Destination Host Unreachable

---

### Post by jamest09 on 2009-07-20
Output of 'ifconfig' please

And the output of 'route' too

---

### Post by mikey_likesit on 2009-07-20
mike@mike-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:cf:9d:d9  
          inet6 addr: 2001:c90:949:5a8b:215:c5ff:fecf:9dd9/64 Scope:Global
          inet6 addr: fe80::215:c5ff:fecf:9dd9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:34517147 (34.5 MB)  TX bytes:2303820 (2.3 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5556 (5.5 KB)  TX bytes:5556 (5.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:61.115.87.19  P-t-P:219.103.128.113  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:25745 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15051 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:33643786 (33.6 MB)  TX bytes:1884905 (1.8 MB)


mike@mike-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
fce043.nw.wakwa *               255.255.255.255 UH    0      0        0 ppp0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         fce043.nw.wakwa 0.0.0.0         UG    0      0        0 ppp0

---

### Post by jamest09 on 2009-07-20
Ok, you PC does not have a connection to the 192.168.0.0 network.

How is everything connected together?

---

### Post by mikey_likesit on 2009-07-20
my main internet connection goes to a hub, my 2 laptops are also plugged in to the same hub via the wall outlets (my apartment came wired for network access).

---

### Post by irv on 2009-07-20
Are you running this through a router, and if so what kind of router? If you can't ping it, your system will never see it. Have you ever had this working before? Or is it new?

---

### Post by mikey_likesit on 2009-07-20
> **irv said:**
> Are you running this through a router, and if so what kind of router? If you can't ping it, your system will never see it. Have you ever had this working before? Or is it new?

my xp machine, plugged in to the same network sees the drive no problem. Actually, i've got a 2nd drive plugged into that 1st one's usb port and I can connect to that one too.

no router, just a buffalo 4-port hub

---

### Post by jamest09 on 2009-07-20
What IP does you XP system have?

---

### Post by mikey_likesit on 2009-07-20
I should note there's only 1 network card, so I'm not sure why there are 2 Local Area Connections listed...

*****************
ipconfig in xp gives:

Ethernet adapter Local Area Connection
Connection-specific DNS Suffix:
Autoconfig IP address : 169.254.190.145
Subnet mask : 255.255.0.0

Ethernet adapter Local Area Connection 2
Media State : Media Disconnected

PPP Adapter My ISP
IP: xxx.45.161.31
Subnet Mask : 255.255.255.255
Default Gateway: xxx.45.161.31

when I mapped the drive in windows the manual said to look for //landisk, though for MacOS X I'm meant to use 192.168.0.200. I figured that what with OS X and linux having some common DNA, I should be using the ip address rather than the device name. I have tried using that too though with the commands I initially posted here, with no success either

---

### Post by jamest09 on 2009-07-20
ping landisk from xp, what IP does it return?

---

### Post by mikey_likesit on 2009-07-20
i get 169.254.157.241

tried pinging that from ubuntu but after waiting a few minutes with no response I had to ^C out of it

tried smb://169.254.157.241 in nautilus as well, just in case, but no response there either.

---

### Post by jamest09 on 2009-07-20
Can you ping 169.254.157.241 from XP?

---

### Post by mikey_likesit on 2009-07-20
yes, with no loss

---

### Post by jamest09 on 2009-07-20
Ok you are using automatic private IP's

Try 'sudo ifconfig eth0 169.254.9.9'  on your Ubuntu box and see if you can ping it.

If so, you need to set some proper IP's on your devices.

---

### Post by mikey_likesit on 2009-07-20
eureka! I got a response from the drive and am able to browse the files on both drives (the network one and the usb one connected to it)!

do I need to add something to /etc/fstab to get this to work from boot? you said something about setting proper IP's for the devices... you mean get admin access to the drive and manually define its IP?

---

### Post by irv on 2009-07-20
> Actually, i've got a 2nd drive plugged into that 1st one's usb port and I can connect to that one too.

no router, just a buffalo 4-port hub
I take it you are connecting the via a network port on the first one and the second via USB? If this is the case you should be able to ping the drive. If not, they is your network port alive. Check that first.

---

### Post by mikey_likesit on 2009-07-20
actually, by assigning eth0 an ip in the same range as the network drive I was able to ping the drive successfully. now I just need to get that to stick whenever I reboot...

---

### Post by irv on 2009-07-20
> **mikey_likesit said:**
> actually, by assigning eth0 an ip in the same range as the network drive I was able to ping the drive successfully. now I just need to get that to stick whenever I reboot...
I think that can be done in the network manager. I don't use the gnome network manager so I can't check that out. I use wicd network manager. Some say they don't like it, but I like it better.
Here is a couple of screen shots:
[ATTACH]121761[/ATTACH]

[ATTACH]121762[/ATTACH]

---

### Post by mikey_likesit on 2009-07-20
i've been fooling around with the gnome network manager but no dice yet. I was sure there was something to do with /etc/fstab though... don't I need to set it to automatically mount the network drives on boot?

---

### Post by mikey_likesit on 2009-07-21
for anyone experiencing a similar problem, here's the contents of a script I wrote to get the two network disks to mount on startup. not the most elegant solution, I suspect there may be something I could have written in /etc/fstab, but this does the trick as well:

```
sudo mkdir /mnt/networkdisk
sudo mkdir /mnt/networkdisk2
sudo gedit networkmount.sh
``````
#!/bin/bash

sudo ifconfig eth0 169.254.9.9
sudo smbmount //169.254.157.241/disk /mnt/networkdisk
sudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
``````
sudo chmod 755 networkmount.sh
```I then added /networkmnt.sh to the list of startup applications thru System>Preferences

Thanks so much to Jamest09 and Irv for helping me out on this, you guys are life savers and undoubtedly prevented a violent outburst aimed at my laptop!

---

### Post by irv on 2009-07-21
> **mikey_likesit said:**
> for anyone experiencing a similar problem, here's the contents of a script I wrote to get the two network disks to mount on startup. not the most elegant solution, I suspect there may be something I could have written in /etc/fstab, but this does the trick as well:

```
sudo mkdir /mnt/networkdisk
sudo mkdir /mnt/networkdisk2
sudo gedit networkmount.sh
``````
#!/bin/bash

sudo ifconfig eth0 169.254.9.9
sudo smbmount //169.254.157.241/disk /mnt/networkdisk
sudo smbmount //169.254.157.241/usbdisk2 /mnt/networkdisk2
``````
sudo chmod 755 networkmount.sh
```I then added /networkmnt.sh to the list of startup applications thru System>Preferences

Thanks so much to Jamest09 and Irv for helping me out on this, you guys are life savers and undoubtedly prevented a violent outburst aimed at my laptop!

I just happen to notice that your first post used the ip address of //192.168.0.200, and now you are using 169.254.157.241? Did you change the ip address to this static ip?

---

### Post by mikey_likesit on 2009-07-21
192.168.0.200 is what the drive manual said would be the default ip, but when I pinged the drive by name using my xp box it gave me the other ip. not entirely sure why it worked out that way, but I'm not one to look a gift horse in the mouth.

---

### Post by irv on 2009-07-21
I forgot to ask what format is the Drive? NTFS? The reason I am asking is make sure you have The ntfs-3g driver loaded. You can install it from the Synaptic Pakage Manager. 
You might be able to go to Places>Connect to Server> and set it up there. I would try the window share and then bookmark it so all you would have to do is selected from the Places menu and you would have access to it. I am not sure if this will work, but you could try it. I have my server setup on a FTP with login. Here is a screen shot. I just use the static ip to set it up.
[ATTACH]121861[/ATTACH]

---

### Post by mikey_likesit on 2009-07-21
thanks, but I already got it all figured out and working fine. After spending as much time as I did on this, I'll be happy to just let this drop and not think about it for a while...

---

