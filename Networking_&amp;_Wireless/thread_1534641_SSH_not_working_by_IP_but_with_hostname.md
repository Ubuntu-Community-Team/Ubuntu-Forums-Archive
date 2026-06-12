---
title: "SSH not working by IP but with hostname"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by alodhi on 2010-07-19
Hello All -

I just finished installing ubuntu server 9.10 - fairly new. I couldn't  run SSH when I use IP address of the server. I've also setup DynDNS that  returns responses when I ping. SSH works fine when I use the hostname  of my server (leopard) but SSH doesn't work when I use IP. 

My DHCP has assigned following, which is little odd for me

eth0: 169.254.169.254
lo: 127.0.0.1
virbr0: 192.168.122.1

I was expecting IP for "eth0" something starting with 192.168.x.x as are  my other computers running WIN on the same network.

Any ideas why
1) Why am I not able to run SSH from IP assigned to server by DHCP. It  works when I use machine hostname (leopard)
2) Why SSH isn't working from DynDNS web hostname when it responses back  the ping command.

Thanks in advance.

Al

---

### Post by Iowan on 2010-07-19
The 169.254.X.X address is from **avahi**. I suppose **avahi** is useful, but (for me, anyway) it usually means something (DHCP) didn't work right. If you **ping leopard**, does the response show the 169.254.X.X address?

---

### Post by alodhi on 2010-07-19
> **Iowan said:**
> The 169.254.X.X address is from **avahi**. I suppose **avahi** is useful, but (for me, anyway) it usually means something (DHCP) didn't work right. If you **ping leopard**, does the response show the 169.254.X.X address?


%From_WIN_Machine%>ping leopard

Pinging leopard [192.168.0.6] with 32 bytes of data:

Reply from 192.168.0.6: bytes=32 time=4ms TTL=64
Reply from 192.168.0.6: bytes=32 time=3ms TTL=64
Reply from 192.168.0.6: bytes=32 time=3ms TTL=64
Reply from 192.168.0.6: bytes=32 time=5ms TTL=64

Surprisingly, I am getting this IP. However, when I do ifconfig -a on ubuntu itself, I don't get that IP. 

So, now SSH works with this IP (192.168.0.6) -- how come this IP don't show up when I do ifconfig -a on ubuntu?

Thanks !

---

### Post by Iowan on 2010-07-19
:confused:  Hmmm... odd.
As a cross-check, try (on the Ubuntu machine) **ip address** and **sudo lshw -C network**.  Both should have the IP address embedded in the results.

---

### Post by alodhi on 2010-07-20
> **Iowan said:**
> :confused:  Hmmm... odd.
As a cross-check, try (on the Ubuntu machine) **ip address** and **sudo lshw -C network**.  Both should have the IP address embedded in the results.
I like ip address command - it gives me the other 192 IP address .. here is what I got:

1 lo: 
      inet 127.0.0.1

2 eth0:  
      inet 169.254.169.254/32 scope link eth0: meta data
      **inet 192.168.0.6/24  brd 192.168.0.255 scope global eth0**

3 virbr0:
      inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0

I dont understand what is /24 and /32 at the end of these IP ... I am googling avahi ... still confused what is it?

------------------------------------------------------------------------------------------------------------

sudo lshw -C network  gave following:

*-network
       description: Ethernet interfaces
       product: NetXtreme BCM5722 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@000:02:00.0
       logical name: eth0
       version: 00
       serial: ....
       size: 100 MB/s
       width: 64 bits
       clock: ......
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5722-v3.11 **ip=192.168.0.6**  latency=0 link=yes ......

---

### Post by alodhi on 2010-07-20
I figured what was the problem. :popcorn:

I'd a Vonage router sitting upstream  (ISP => Modem => Vonage Router => NetGear Router => LAN) -  which is why port forwarding was not working. I'd called comcast,  checked firewall - everything was fine - so finally the culprit was  vonage. 

Now, I need to figure out how to configure so that Vonage router works.  I've a new vonage router - it stopped working (incoming/outgoing calls)  when I put this behind my router - Vonage technician suggested I put  their router in the upstream and then put my own router behind theirs --  that worked and I started receiving/making calls. 

So, now the challenge is to figure out how all this will work together  -- obviously, I can't drop my vonage adapter. 

If anyone have any info about this ... please share.

---

### Post by Iowan on 2010-07-20
Wow, glad *you* found it...
The /24 or /32 are another (CIDR) way of specifying netmask. 
/24 is the "usual" 255.255.255.0, 
/32 would be 255.255.255.255 (which wouldn't seem to be very useful).

---

