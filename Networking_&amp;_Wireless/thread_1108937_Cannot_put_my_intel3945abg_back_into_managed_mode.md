---
title: "Cannot put my intel3945abg back into managed mode??"
date: 2009-03-28
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-28
I have just patched my Intel3945 pro/wireless Network card,

From the iwl3945 Drier 
(mark@ubuntu:~$ lsmod | grep iwl)
mark@ubuntu:~$ 

To the mark@ubuntu:~$ lsmod | grep ipwraw
ipwraw                125848  0 

 Also managed to put it in Monitor Mode.

Here is my iwconfid output Now:

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

BUT I should be getting this: (From iwconfig command):

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11abg ESSID:"ROUTER"
Mode:Managed Frequency:2.437 GHz Access Point: 00:1E:74:6C:22:96
Bit Rate=54 Mb/s Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Encryption key:2387-BFEE-4C96-8850-5522-9F08-8314-43B8-3BD9-D7A9-1E56-0F13-0ACF-1D8B-4869-2D6C [2] Security modepen
Power Managementff
Link Quality=98/100 Signal level:-26 dBm Noise level=-62 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

pan0 no wireless extensions.

BUT I am getting this output:

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

I also cannot put my wireless card back into Managed Mode to serf the net?

Can anyone suggest what I can do to fix this please?

Thank-you in advance

---

### Post by scrypt on 2009-03-28
Im not sure, but i think it is becuse I cannot enable my wireless card?

Is this correct?

How do i enable it?

---

### Post by scrypt on 2009-03-28
there is NO wireless icons in network configuration?

---

