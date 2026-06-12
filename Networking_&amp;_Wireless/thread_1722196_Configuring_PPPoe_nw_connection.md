---
title: "Configuring PPPoe n/w connection"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by sandy0594 on 2011-04-05
Hi all, i am new to linux..i have just now installed ubuntu 10.10 desktop edition..I am unable to configure n/w connections in linux..btw,i tried this

```



**[COLOR=#C20CB9]sudo[/COLOR]** pppoeconf

Sorry,no working ethernet card could be found.If you do have an interface card which was not autodetected so far,you probably wish to load the driver manually using the modconf utility.Run modconf now?   /usr/sbin/pppoeconf: 523: modconf: not found
 
 **Ifconfig**
  
   Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0
            inet6 addr: ::1/128 Scope:Host
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
            RX packets:20 errors:0 dropped:0 overruns:0 frame:0
            TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:0 
              RX bytes:1304 (1.3 KB)  TX bytes:1304 (1.3 KB)


  
**lspci -nn | grep Ethernet**

  01:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
    
  
  

```

I got the above error and it even said that my Lan card is not recognized..any suggestions please

---

