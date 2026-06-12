---
title: "had wireless...now i dont?"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by privatejarhead on 2009-07-27
i've had my laptop (toshiba l505) for about a week now and i've played around with vista home to where i have everything i want on it, so i decided to take the plunge into linux (after backing up my data, of course). instead of the traditional install, i instead used 9.04's wubi installer and it went flawless as far as the OS is concerned. then i try to connect to my wireless network >.<. ubuntu wouldnt connect on the first boot, so i restarted and went back to vista, where i was able to connect. searched the forums for help and i got what i was looking for and now i have a connection for ubuntu. later on today, i decided to log back into vista and at first, the connection failed then reconnected, but now im unable to surfthe net within vista, only ubuntu. can anyone help me try to get my internet connection back on vista, while keeping it on ubuntu?

if it helps, here's my iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"getoffmynetwork"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:B2:1E:5F:96   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=80/100  Signal level:-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.




my lspci -v | less:


00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
        Subsystem: Toshiba America Info Systems Device ff1e
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Toshiba America Info Systems Device ff11
        Flags: bus master, fast devsel, latency 0, IRQ 2299
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 4110 [size=8]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
        Subsystem: Toshiba America Info Systems Device ff11
        Flags: bus master, fast devsel, latency 0
        Memory at d2500000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>


also, the wireless router im using is a netgear wgr614v7. i doubt this is the problem though, considering it works fine in ubuntu and it shows up under vista, it even asks me for the password when i attempt to connect. even then, i cant get on my internet.

---

### Post by privatejarhead on 2009-07-27
nvm, i somehow solved the problem by doing nothing...

i logged in and out a few times in both OSes and now they are working with the internet....hmmmm wonder how that happened

---

### Post by pibri on 2009-07-27
I have vista and ubuntu on my lap top.

Ububtu lost its wireeless connection when i was using it and i have not been able to get it back. I was using hardy...reloaded intrepid, then jaunty...all three will not connect, they dont even see the wireless network.

After all three rebuilds, vista has picked up the network with out any trouble.

Has any one any ideas.

The lap top is an acer aspire.

:confused:

---

