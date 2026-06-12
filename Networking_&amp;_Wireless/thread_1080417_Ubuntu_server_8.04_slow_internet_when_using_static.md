---
title: "Ubuntu server 8.04 slow internet when using static ip"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by jch2os on 2009-02-25
I have a really strange problem.  I have a machine directly connected to a route provided by Comcast.  I have 5 static IPs.  Say they are 2.2.2.1-5, with a gateway of .6 and netmask of 255.255.255.248.   

If I use DHCP in my interfaces file the router gives me a 10.1.10.0 address.  I can then download about 1.5mb/second.  

If I set my static ip in my interfaces file I get about 300k/second. 

I'm downloading the same file.  I'm pretty sure it can't be hardware since I get the full speed when I use DHCP.  I'm not getting errors or dropped packets.  I have IPV6 disabled.  If I plug my windows laptop and do the same thing I get 1.5mb/second with static and dhcp.  So I think that rules out the Comcast hardware.  I'm also using the same DNS each time.

Here is my /etc/network/interfaces file when I'm using static.  With my "temp" IP that is :)

auto eth1
iface eth1 inet static
address 2.2.2.1
netmask 255.255.255.248
gateway 2.2.2.6

I also tried IP's 1-5 to see if that made a difference...it didn't.

I'm going crazy...does anyone have any other ideas?  Thanks!

---

### Post by terazen on 2009-02-25
I'm assuming you are moving cables around somehow?  Can you describe your network?  I'm not gathering how your router lets 2.2.2.x and 10.1.10.x work on the same lan port.

Have you tried a 10.1.10.x static ip address?  I'd guess the problem has something to do with the 2.2.2.x subnet and less to do with the fact it's static vs dhcp.

---

### Post by jch2os on 2009-02-25
I'm not moving any cables around.  For testing I really just have the cable modem plugged directly into this machine, nothing else.  I tried setting the static IP to 10.1.10.170(what I got from dhcp) and it still got 1.5mb down, so it is something with that IP but it works in windows.  What is odd is that I tried two different cable modems and each have totally different IP blocks.  Any other ideas?

---

### Post by terazen on 2009-02-25
Oh comcast must have 2 subnets on the vlan you're on...

One thing you can do is to copy the mac address of your windows box to your ubuntu server temporarily and use the same 2.2.2.x ip your windows server uses (of course disconnect your windows box).  If the ubuntu server goes faster after that then comcast is throttling by mac somehow.  If not then I'm out of ideas.

In either case, the ubuntu server has proven it can get 1.5mb with dhcp and static using the same ethernet cable and modem, only changing ip's.  You will probably need to call comcast.  Good luck!

---

### Post by jch2os on 2009-02-25
I did call comcast.  Since it works in Windows it isn't there problem.  And I'm pretty sure it isn't.  I think I'm going to try 8.10 and see if it does it there.  This is a pain.

---

### Post by jch2os on 2009-02-27
So I think I have it figured out.  I disabled acpi and now it is so much faster.  I read about ubuntu with 8139too having issues with acpi.  Man that was a pain.  I disabled it by editing my /boot/grub/menu.lst file

before:

# kopt=root=UUID=b59f2c4c-7dd1-4fdf-be1e-21e9492cf9a3 ro

after:

# kopt=root=UUID=b59f2c4c-7dd1-4fdf-be1e-21e9492cf9a3 ro acpi=off


Make sure you keep the '#' in the front.

Then I ran update-grub and rebooted.  All is good now!

---

