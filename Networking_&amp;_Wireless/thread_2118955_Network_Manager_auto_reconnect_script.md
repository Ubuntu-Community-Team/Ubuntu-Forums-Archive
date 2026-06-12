---
title: "Network Manager auto reconnect script"
date: 2013-02-22
forum: Networking &amp; Wireless
---

### Post by jsmanian on 2013-02-22
I am using internet through my GSM mobile in Xubuntu 12.04.1. It disconnects many times after one or two hours. I am looking for some scripts that will reconnect network connection automatically when internet is disconnected.

   I searched and found one script. But it is not working fine. Could you please let me know anything is not correct.

[HTML]start on started network-manager
stop on runlevel [016]

script
  while true; do
    if ifconfig ppp0 | grep -q "inet addr:"; then
       # echo "all ok!"
    else
       restart network-manager
    fi
    sleep 5
  done
end script[/HTML]

As I am connecting through GSM mobile, I changed eth0 to ppp0 in the above script. But script is not working for me.

[HTML]subramanian@jsm:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:39:62:55  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:b3380000-b33a0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:215167 (215.1 KB)  TX bytes:215167 (215.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:14.194.82.147  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:949037 (949.0 KB)  TX bytes:267669 (267.6 KB)[/HTML]
output for nm-tool
[HTML]subramanian@jsm:~/Desktop$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [Tata Docomo Internet] --------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         14.194.82.147
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             121.242.190.210
    DNS:             121.242.190.181


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1C:C0:39:62:55

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
[/HTML]

---

### Post by jsmanian on 2013-02-25
Anyone can help me? I tried wicd networkmanager also. But I could not able to connect to internet through GSM mobile. 
I don't know that it will work with GSM mobiles or not.

---

