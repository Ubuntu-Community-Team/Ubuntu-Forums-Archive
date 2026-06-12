---
title: "Wifi stopped working (I did something wrong)!"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by khaj_vah on 2013-07-04
Hello people,

I was learning stuff about linux and wanted to try messing with "run levels". I don't understand how could "telinit 1" mess things up(maybe it was a coincidence). Well, telinit didn't work too, it showed screen with "ubuntu" in the center of the screen, like when turning on. Now, after reboot, wifi does not find any network, it detects wifi card but cannot find any network.

```
khajvah@khajvah-Inspiron-5720:~$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

khajvah@khajvah-Inspiron-5720:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:8f:69:d3:be:d6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr c0:18:85:b7:d6:53  
          inet6 addr: fe80::c218:85ff:feb7:d653/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9314 (9.3 KB)  TX bytes:9314 (9.3 KB)


```

Please, explain what went wrong (not just the solution), because I am enthusiastic in learning these stuff.

[IMG]http://s18.postimg.org/kmhn8l9mx/wifiproblem.png[/IMG]

Thanks in advance :)

---

### Post by khaj_vah on 2013-07-04
Nvm, I don't know why but after free reboots, it started working

---

