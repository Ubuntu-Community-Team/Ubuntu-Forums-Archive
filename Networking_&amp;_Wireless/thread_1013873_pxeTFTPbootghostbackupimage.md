---
title: "pxe/TFTP/boot/ghost/backup/image"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by p.becks on 2008-12-17
Hello,

Recently i installed Amahi (fedora) on an old pc of mine. I used it for a while and found that i could backup other pc's in my network to this amahi-server with pxe/network booting (F12 on my HP-pc). That's a great feature that i would like to see in Ubuntu (my first love). Now, there are lots off "how-to's" on the internet but none off them appeal to me (i need a "how-to" for dummies...)

I understand that it involves these things:

- The (ubuntu) server must be the dhcp-server. (so the dhcp-service in my router must be disabled)
-I need to install TFTP and configure it.

Do you know a "fool-proof" install guide for dummies?

---

### Post by jonobr on 2009-01-21
HEllo


Im dissappointed no-one took a stab at this.

I had to do this myself and got the following, Im hoping its useful.
Its not fool proof, but maybe you could kick this around, and then if it works, post in tutorials , tips and howtos.......



Assuming that the dhcp is disabled and will not reply to DHCP requests, heres what I recommend (note IP addresses, subnet masks, bootfiles, macaddresses etc are all made up)
On the Ubuntu server


1- Install DHCP
2- Install TFTP
3- Configure DHCP
4- Configure TFTP
5- load config files into tftp directory.
6- start both
7- Error checking




1- install DHCP app

in a terminal window
sudo apt-get install dhcp3-server
Installs dhcp3-server

2- Install TFTP

in a terminal window
sudo apt-get install tftpd-hpa
Installs tftp server

3- Configure DHCP


go to /etc/dhcp3/dhcp.conf (vi skill would be good here.)
In my example I am using an address range of 10.10.0.0 with a class b subnet (255.255.0.0) my boot file is 'bootfile' and the address I am giving the PC will be 10.10.0.22. The mac is dummy but I use that to assign to the PC. Add more declarations for IP addresses.

Here are the important lines you need to add modify of uncomment.
(This what works for me and seperated by **********)
************************
# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative; <- I uncommented this line
***************************
# No service will be given on this subnet, but declaring it helps the
# DHCP server to understand the network topology.

subnet 10.10.0.0 netmask 255.255.0.0 {
}
******************************
# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

host pc1 {
  hardware ethernet 00:30:43:11:32:21;
  fixed-address 10.10.0.22;
  filename "bootfile";
#  server-name 10.10.0.14;
}
*****************************

4- Configure TFTP

   1.  Edit /etc/inetd.conf -  comment out the tftpd line by adding a hash (#) at the start of the config line containing tftp
   2. Edit /etc/default/tftpd-hpa : Set RUN_AS_DAEMON="yes"
   3. Edit /etc/default/tftpd-hpa : OPTIONS="-l -v -s /bootfromhere"

5- load config files into tftp directory.

Add your bootfile (name bootfile- use your own here) to the directory called /bootfromhere

6- Start both

Open one window and open a syslog

tail -f /var/log/syslog

start dhcp using
sudo /etc/init.d/dhcp3 start

start tftp
sudo /etc/init.d/tftpd-hpa start

7- errors

Watch the output of starting both services, any errors should be shown on the starting of each.

note where it complains and rectify.
watch the syslog to ensure both start ok/

When doing tftp, run wireshark to ensure correct dhcp negotiation as well as tftp transfer commencement

---

