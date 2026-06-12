---
title: "Issues: TFTP &amp; DHCP &amp; RARP &amp; NFS &amp; remote booting a server"
date: 2009-03-13
forum: Networking &amp; Wireless
---

### Post by Friqenstein on 2009-03-13
Hello all,

A brief rundown of what I'm trying to do is use computerA to remote boot & install OS on computerB. Simple right? ...

Desktop NIC#1 = eth0 = IP.add.re.ss
Desktop NIC#2 = eth1 = 192.168.1.50
Netra X1 (to be booted remotely) = 192.168.1.70

Well, I'm using my Ubuntu Desktop machine as my host. It has 2 NICs built on the Mobo, so I decided to use the second NIC as the TFTP/DHCP source.
I've configured the second port (eth1) as follows:```
Link encap:Ethernet  HWaddr *mac address here*  
          inet addr:192.168.1.50  Bcast:192.168.1.255  Mask:255.0.0.0
          ...
```So now I install the needed utilities to get this all underway.```
$ sudo apt-get install rarpd tftp tftpd-hpa bootparamd nfs-kernel-server dhcp3-server
```Now I make my directories```
sudo $ sudo mkdir -p /jumpstart
$ sudo mkdir /tftpboot
$ sudo mkdir /tftpboot
$ sudo chmod -R 777 /tftpboot
$ sudo chown -R nobody /tftpboot
```So I load my Solaris8 DVD in the drive and it auto-mounts with no problems. I copied the entire DVD contents to **/jumpstart**.
I added the following to my **/etc/exports**:```
/jumpstart *(ro,no_root_squash)
```Next I add the following to **/etc/ethers**:```
00:3:ba:4:d6:b8 192.168.1.70
```Next I copied the image file:```
(*the reason I used SUNW,UltraAx-i2 is because it was the suggested platform for Netra X1*)
cp /jumpstart/Solaris_8/Tools/Boot/usr/platform/SUNW,UltraAx-i2/lib/fs/nfs/inetboot /tftpboot/inetboot.sol8.sun4u
```After all of this, I go through and restart all the involved processes:rarpd, dhcp3-server, nfs-kernel-server, xinetd, bootparamd, tftpd.

Now I have my laptop connected to the console port via a console cable so I can control the Netra X1 via a terminal in ubuntu on my laptop.```
ok boot net - install
Boot device: /pci@1f,0/ethernet@c  File and args: - install
Using Onboard Tranceiver - Link Up.
TFTP Error: File not found

Boot load failed
```

Related Config Files:
/etc/ethers```
00:3:ba:4:d6:b8  192.168.1.70
```/etc/inetd.conf```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -c -s /tftpboot
```/etc/xinetd.d```
service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}
```/etc/default/nfs-kernel-server```
# Number of servers to start up
RPCNFSDCOUNT='8 --no-nfs-version 4'

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information, 
# see rpc.mountd(8) or http://wiki.debian.org/?SecuringNFS
RPCMOUNTDOPTS=

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=
```/etc/bootparams```
sparc root=192.168.1.50:/jumpstart/Solaris_8/Tools/Boot install=192.168.1.50:/jumpstart boottype=:in
```

This is all basically a watered down version of all the back and forth I've been through the past few days working with this. I've tried various methods regarding swapping out servers (software servers). I've tried just about all I can think of to get this setup running. I just cannot seem to get the remote machine to see the boot image.

Any help is greatly appreciated.
Tnx

---

### Post by Friqenstein on 2009-03-14
I tried a few more variances yesterday to no avail.
Has anybody got a clue to a possible solution here?

---

### Post by puppywhacker on 2009-03-14
First of all, Solaris 10 and OpenSolaris are available for years. why use 8.0?

Second when start the "net boot - install" at the OK prompt of your netra run an tcpdump on your network interface. It really helps to pinpoint the cause of failure.
```
tcpdump -v -i eth1
```

Thirdly, your error is
"TFTP Error: File not found"
which means that your TFTP server is not configured like you thought it would be. In ubunut you have a few different tftp packages that you can use, I always stick to the HPA version since it supports the option "SIZE". From your configs I think you are not using HPA. I wrestled with the pathname of tftp which has to be /tftpboot/file or /file depending on the tftp server I used.

Fourthly try on your ubuntu to tftp get the file.

---

### Post by Friqenstein on 2009-03-16
> **puppywhacker said:**
> First of all, Solaris 10 and OpenSolaris are available for years. why use 8.0?[/code]Because I have the solaris8 DVD and didn't want to waste time downloading 2Gigs worth of an OS I basically already had.
> Second when start the "net boot - install" at the OK prompt of your netra run an tcpdump on your network interface. It really helps to pinpoint the cause of failure.
```
tcpdump -v -i eth1
```Well, the **-e** flag doesn't appear to do anything at all. But you do need to specify the **-i** flag to secify the interface you are using the **tcpdump** on. (*i.e. -i eth1*)

[quote]Thirdly, your error is
"TFTP Error: File not found"
which means that your TFTP server is not configured like you thought it would be. In ubunut you have a few different tftp packages that you can use, I always stick to the HPA version since it supports the option "SIZE". From your configs I think you are not using HPA. I wrestled with the pathname of tftp which has to be /tftpboot/file or /file depending on the tftp server I used.Yes no doubt there is something ill configured, which is why I'm posting. Like I've stated already, I've gone through several online **Document's** detailing other people's experiences in getting this to work... NONE of those examples seem to work.
I've followed them all verbatim and it doesn't work. Period.

Most of the config edits the 'Documents' suggested are fairly identical in wording and principal.

I've already tried the HPA version of the TFTP server. It doesn't do anything that the regular tftpd server doesn't do. Other than the different file name for its config file, there are basically no differences.

here is the output of: tcpdump -e -v ie eth1```
08:14:18.894254 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 318: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 304) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 276
08:14:18.894978 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 313: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 299) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 271
08:14:18.895807 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 390: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 376) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 348
08:14:18.896656 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 382: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 368) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 340
08:14:18.897534 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 313: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 299) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 271
08:14:18.898364 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 366: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 352) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 324
08:14:18.899231 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 398: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 384) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 356
08:14:18.900132 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 313: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 299) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 271
08:14:18.901033 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 386: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 372) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 344
08:14:18.901878 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 380: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 366) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 338
08:14:18.902820 00:14:bf:1e:c0:8b (oui Unknown) > 01:00:5e:7f:ff:fa (oui Unknown), ethertype IPv4 (0x0800), length 382: (tos 0x0, ttl 4, id 0, offset 0, flags [DF], proto UDP (17), length 368) 192.168.1.1.1900 > 239.255.255.250.1900: UDP, length 340
08:14:19.011487 00:1d:60:6f:4e:8d (oui Unknown) > 01:00:5e:00:00:fb (oui Unknown), ethertype IPv4 (0x0800), length 88: (tos 0x0, ttl 255, id 0, offset 0, flags [DF], proto UDP (17), length 74) server.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 250.255.255.239.in-addr.arpa. (46)
```
> Fourthly try on your ubuntu to tftp get the file.I've already done this. Which is why I know that the tftp 'appears' to be working properly.

---

### Post by Friqenstein on 2009-03-16
I made a few modifications to some of the config files.

For starters, I went ahead and downloaded the ***Solaris10*** img from their site. I mounted the img like so:```
sudo mount -0 loop <path-to-sol10.iso> /jumpstart
```So I have full access to the boot img located now at /jumpstart. So the path to the actual boot file (*[SIZE="2"]to my understanding from all the examples[/SIZE]*) is **/jumpstart/Solaris_10/Tools/Boot/platform/sun4u**
In that directory we have 3 files:[LIST]
[*]boot_archve
[*]inetboot
[*]wanboot
[/LIST]

Ok, so I went back through ALL of my config files one at a time again. I changed my **/etc/bootparams** file to:```
sparc root=192.168.1.50:/jumpstart/Solaris_10/Tools/Boot/platform/sun4u install=192.168.1.50:/jumpstart/sol10 boottype=:in
```I also added```
192.168.1.50 server
192.168.1.70 sparc
```to my **/etc/hosts** file.192.168.1.50 server = my desktop's secondary NIC (eth1)
192.168.1.70 sparc = the remote sparc to be net-booted

My **/etc/default/tftpd-hpa** file is:```
RUN_DAEMON="yes"
OPTIONS="-c -l -s /tftpboot"
```However, I've noticed in numerous examples, people use /tftpboot and some use **/var/lib/tftpboot**. And the Ubuntu guide suggested in a thread on this forum uses the **/var/lib/tftpboot**
At any rate, I made sure my config file specified the regular /tftpboot directory so it matches everything else... config file wise.

My /etc/inetd.conf:```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -c -s /tftpboot
```

And since I added the host names to the /etc/hosts file, I changed some of the references to names rather than IPs. For example my /etc/ethers file:```
00:3:ba:4:d6:b8 sparc
```According to the examples, I'm supposed to use the MAC address from the sparc machine in conjunction with its IP address (*[SIZE="2"]or hostname if hostname is specified[/SIZE]*)

I restarted all the related processes and tried again. Same results... no boot with same error message as before.
However the output of the tcpdump has changed slightly:```
09:50:53.950993 sparc > Broadcast, ethertype Reverse ARP (0x8035), length 64: rarp who-is sparc tell sparc
09:50:53.951189 00:1d:60:6f:4e:8d (oui Unknown) > sparc, ethertype Reverse ARP (0x8035), length 42: rarp reply sparc at sparc
09:50:53.951523 sparc > 00:1d:60:6f:4e:8d (oui Unknown), ethertype IPv4 (0x0800), length 64: (tos 0x0, ttl 64, id 0, offset 0, flags [none], proto UDP (17), length 45) sparc.12589 > server.tftp:  17 RRQ "C0A80146" octet 
09:50:57.953892 sparc > Broadcast, ethertype IPv4 (0x0800), length 64: (tos 0x0, ttl 64, id 1, offset 0, flags [none], proto UDP (17), length 45) sparc.12589 > 255.255.255.255.tftp:  17 RRQ "C0A80146" octet
```
And this is where I sit now. Looking in the tcpdump, it seems that the RARP worked... at least it appears that the sparc replied to the DHCP server or the RARP.
The second line: **09:50:53.951189 00:1d:60:6f:4e:8d (oui Unknown) > sparc, ethertype Reverse ARP (0x8035), length 42: rarp reply sparc at sparc** has the MAC address of my eth1 card on my desktop. (*the TFTP server*) Which is the same MAC address in line 3 as well.

however lines #3 & #4 I don't fully understand. At the end of the line is shows **C0A80146** which is the HEX value of the IP address for the sparc... at least that is how the example had it.
IP 192.168.1.70 => HEX C0A80146 right?
That is the HEX of the IP for the sparc which was used in creating symlinks **ln -s inetboot.sol10.sun4u C0A80146** & **ln -s inetboot.sol10.sun4u C0A80146.SUN4U** inside the /tftpboot directory (as per instrutions)

EDIT
Forgot to add:
Now when I attempt to get or put any files with tftp (locally) it times out. It will create the file, but will not actually copy it. I've made sure the permissions are changed on the directories as well.

---

### Post by Friqenstein on 2009-03-16
A little bit of progress...
After all of those edits, it appears that simply restarting the process doesn't always work 100%.
I did a full reboot of the entire desktop (tftp server) and now I'm able to tftp locally and get & put files with no problem.

So then I tried the sparc boot again:```
Environment monitoring: disabled
Executing last command: boot net - install
Boot device: /pci@1f,0/ethernet@c File and args: - install
Using Onboard Transceiver - Link Up.
3a000
Server IP address: 192.168.1.50
Client IP address: 192.168.1.70
Using Onboard Tranceiver - Link Up.
panic - boot: Could not mount filesystem.
Program terminated
OK
```So now it seems that the sparc can now not only see the TFTP server, but actually obtains an IP address and actually appears to find the boot img, however now it says it cannot mount the filesystem.

---

### Post by Friqenstein on 2009-03-16
I think I may have got it finally...

I changed the /etc/bootparams file to:```
sparc root=192.168.1.50:/jumpstart/Solaris_10/Tools/Boot install=192.168.1.50:/jumpstart/inetboot boottype=:in
``` and recopied the boot img file inetboot from the Solaris10 mounted img. Basically not worrying about the specifics of the SUN4U indicators.
Now I have it pointed directly at the **inetboot** img file.

I got new hope after attempting that. Here is the output:```
Server IP address: 192.168.1.50
Client IP address: 192.168.1.70
Using Onboard Transceiver - Link Up.
ramdisk-root ufs-file-system
Loading: /platform/SUNW,UltraAX-i2/kernel/sparcv9/unix
Loading: /platform/sun4u/kernel/sparcv9/unix
SunOS Release 5.10 Version Generic_137137-09 64-bit
Copyright 1983-2008 Sun Microsystems, Inc.  All rights reserved.
Use is subject to license terms.
os-io Configuring devices.
WARNING: /pci@1f,0/ide@d/dad@0,0 (dad1):
        Corrupt label; wrong magic number

Using RPC Bootparams for network configuration information.
Attempting to configure interface dmfe1...
Skipped interface dmfe1
Attempting to configure interface dmfe0...
Configured interface dmfe0
install entry: 192.168.1.50 192.168.1.50 /jumpstart/inetboot
root entry: 192.168.1.50 192.168.1.50 /jumpstart/Solaris_10/Tools/Boot
ERROR:  Unable to NFS mount 192.168.1.50:/jumpstart/inetboot
             Exiting to shell.
```So now the TFTP server, DHCP server, and RARP server all appear to be functional and doing fine. Seems I have a problem with my NFS mount.

---

### Post by Friqenstein on 2009-03-16
Weird... after that last post, I didn't mention it dropped me to the # prompt on the sparc unit (still no OS installed).
So I typed **break** to get back to the 4th prompt, and then it started to initiate the txt console install mode for solaris10.

I thought... well that's just odd. (Nothing changed since it told me about the NFS error)
So after initiating itself when I told it to break, I get to the Language Selection option menu of the text based Solaris10 install.

So now I'm going through the text based install via the console terminal on my laptop.

WoW what a rocess... hopefully this all goes accordingly to plan then I can just make one install server and a script to do all this crap for me. To think I'd have to respecify the MAC address in the config file each time I want to net-boot a different server... and considering I have quite a few to net-boot...

---

### Post by jonobr on 2009-03-16
Hello

Its probably a bit late in the day to add this,
but in the tcpdump its difficult to get meaningful information from a tcpdump -v

I would recommend in future to see whats going on,

do a 

```
tcpdump -w tftp.pcap -s 1600 -i eth0 
```

This way you end up with a file that you can open on wireshark and get a lot more detail on the data which is a lot easier to look at.

You could run the capture from the GUI also.
You could also define a port number with the command to get only the traffic on that specifc port number eg

```
tcpdump -w tftp.pcap -s 1600 -i eth0 port XX 
```

---

### Post by Friqenstein on 2009-03-16
[SIZE="1"]> **jonobr said:**
> Hello

Its probably a bit late in the day to add this,
but in the tcpdump its difficult to get meaningful information from a tcpdump -v

I would recommend in future to see whats going on,

do a 

```
tcpdump -w tftp.pcap -s 1600 -i eth0 
```

This way you end up with a file that you can open on wireshark and get a lot more detail on the data which is a lot easier to look at.

You could run the capture from the GUI also.
You could also define a port number with the command to get only the traffic on that specifc port number eg

```
tcpdump -w tftp.pcap -s 1600 -i eth0 port XX 
```[/SIZE]
Thanks for the added info. I'll absolutely keep that in mind.

---

### Post by jonobr on 2009-03-16
You should, there is an exam when the thread is closed :P

---

### Post by sunta on 2012-08-10
heya, I got a similar problem. I want to install on a netra X1 from an ubuntu machine. machines are connected via crosscable on eth2
00:03:ba:0a:11:b2 MAC of netra
172.16.165.165 IP of netra
172.16.165.167 IP of ubuntu

I set up tftpd and teste it, rarpd seems to be working too:

Aug 10 17:12:31 andro rarpd[5257]: RARP request from 00:03:ba:0a:11:b2 on eth2
Aug 10 17:12:31 andro rarpd[5257]: RARP response to 00:03:ba:0a:11:b2 172.16.165.165 on eth2

so it gets the correct IP via rarpd.

its just not getting the tftpd-file :(
tcpdump on eth2@ubuntu tells me
 17:21:00.841351 IP (tos 0x0, ttl 64, id 57, offset 0, flags [none], proto UDP (17), length 45)
    netra.31995 > 255.255.255.255.tftp:  17 RRQ "AC10A5A5" octet
17:21:09.856314 IP (tos 0x0, ttl 64, id 58, offset 0, flags [none], proto UDP (17), length 45)
    netra.31995 > 255.255.255.255.tftp:  17 RRQ "AC10A5A5" octet

I see the request for AC10A5A5/172.16.165.165 but no traffic goes back.

tryin it from ubuntu from console works:
tftp 172.16.165.167
tftp> get AC10A5A5
Received 9486437 bytes in 0.5 seconds

the boot process itself looks this way
ok boot net - install                                                           
Boot device: /pci@1f,0/ethernet@c  File and args: - install                     
Using Onboard Transceiver - Link Up.

it stays forever in the "Using Onboard Transceiver - Link Up." state and nothin happens :(

any hints?

---

### Post by Friqenstein on 2013-02-08
I'm necroing my own thread for an informative update:

This crap is still crap.
It is still ridiculously difficult to get this working. It is absolutely stupid that at this time in our technological world we are still forced to use archaic methods to try to get a netboot install to function.

Why on earth has there not been anything built to simplify this process is beyond me.
I've gone back through my old post to attempt to do this again on a SPARC unit and it just simply will not work at all.
This is so damn annoying it is just plain retarded.

My advice is don't even bother. Either find a way to do a CD based install, or just get a different system that supports an alternate method of install because this whole netboot rarpd tftpd nonsense is just that... nonsense.

---

### Post by wildmanne39 on 2013-02-08
Old thread closed.

---

