---
title: "ndiswrapper hardware NOT present"
date: 2005-03-16
forum: Networking &amp; Wireless
---

### Post by dannyBoy on 2005-03-16
Hi folks, Id really appreciate a hand here!

Believe me, I've spent the last two days trawling these forums before posting and am totally stuck. I should say I'm very new to Linux (and loving it so far) so go easy on me! lol

Anyway, I have a Buffalo g54 pcmcia wireless card.

lspci lists the following:

    0000:02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

I tried using ndiswrapper to use the correct WinXP driver for my card from the buffalo website.

ndiswrapper -i installed fine. However, ndis wrapper -l lists:

    Installed ndis drivers:
    netcbg54        hardware NOT present

I have manually configured /etc/network/interfaces to apend the following lines:

    # The buffalo 54g wireless - pcmcia
    auto wlan0
    iface wlan0 inet dhcp
    wireless_mode managed
    name Wireless 54g

the gnome network configuration can therefore see my wireless adapter, but obviously when I try to enable it fails.

ifconfig returns:

eth0      Link encap:Ethernet  HWaddr 00:0D:9D:84:22:2F
          inet addr:192.168.2.5  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:9dff:fe84:222f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1212672 (1.1 MiB)  TX bytes:370110 (361.4 KiB)
          Interrupt:10 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64637 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9336812 (8.9 MiB)  TX bytes:9336812 (8.9 MiB)


No mention of eth0!

I know the problem is ndiswrapper is not working correctly, but I have no idea why!

Sorry for the length of this post - I'd appreciate any help that can be given. I want to leave XP behind and this is the only thing holding me back!

dannyBoy

---

### Post by dannyBoy on 2005-03-16
Actually don't worry - I have it working now! I googled a new XP driver that let ndiswrapper find the hardware - now I'm all set!

Thanks for reading :)

---

