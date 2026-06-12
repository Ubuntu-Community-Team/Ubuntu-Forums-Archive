---
title: "Slow HTTP Traffic"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by logiq on 2012-01-05
Hello everyone,

I'm having trouble browsing the internet quite frequently, and find myself having to keep refresing sites. Other traffic seems fine. Getting good and reliable speed while torrenting and gaming. Other users on my network have no problem at all. 

If I let a page load out while it's stuck, and using chromium, I'm getting this:
```
Error 324 (net::ERR_EMPTY_RESPONSE): The server closed the connection without sending any data.''
```

The problem started after I changed my old motherboard and harddrive, but I have kept the same NIC which a wlan Atheros card, and using the ath5k driver. 

**lspci -nnk | grep -iA2 net**
```
08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5413 802.11abg NIC [168c:001b] (rev 01)
        Subsystem: 3Com Corporation Device [a727:6803]
        Kernel driver in use: ath5k

```

**Uname -a**
```
$ uname -a
Linux linux 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:45:26 UTC 2012 i686 i686 i386 GNU/Linux

```

**Netstat while browsing these forums:**
```
$ netstat
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 linux.local:58221       arn06s02-in-f31.1:https TIME_WAIT  
tcp        0      0 linux.local:53103       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:58101       arn06s02-in-f31.1:https ESTABLISHED
tcp        0      0 linux.local:34497       gw016.lphbs.com:https   ESTABLISHED
tcp        0      0 linux.local:35024       www-11-02-ash3.face:www ESTABLISHED
tcp        0      0 linux.local:53277       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:48150       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:59024       199.66.238.71:www       TIME_WAIT  
tcp        0      0 linux.local:55018       arn06s02-in-f10.1e1:www TIME_WAIT  
tcp        0    769 linux.local:60019       feijoa.canonical.co:www ESTABLISHED
tcp        0      0 linux.local:60839       arn06s02-in-f27.1e1:www ESTABLISHED
tcp        0      0 linux.local:59573       a148-123-13-64.depl:www TIME_WAIT  
tcp        0      0 linux.local:53395       arn06s01-in-f21.1:https TIME_WAIT  
tcp        1      0 linux.local:53922       212-106.livestream.:www CLOSE_WAIT 
tcp        0      0 linux.local:58219       arn06s02-in-f31.1:https TIME_WAIT  
tcp        0      0 linux.local:46018       212-67.livestream.c:www ESTABLISHED
tcp        0      0 linux.local:58222       arn06s02-in-f31.1:https TIME_WAIT  
tcp        0      0 linux.local:53102       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:54657       arn06s02-in-f12.1e1:www ESTABLISHED
tcp        0      0 linux.local:39655       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:58220       arn06s02-in-f31.1:https TIME_WAIT  
tcp        0      0 linux.local:39665       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:57964       gw033.lphbs.com:https   ESTABLISHED
tcp        0      0 linux.local:50176       CRL.VERISIGN.NET:www    ESTABLISHED
tcp        0      0 linux.local:56023       ums07-1.ustream.tv:1935 ESTABLISHED
tcp        0      0 linux.local:46249       a148-123-13-56.depl:www ESTABLISHED
tcp        1      0 linux.local:33956       74.221.222.30:1935      CLOSE_WAIT 
tcp        0      0 linux.local:48280       a148-123-13-17.depl:www ESTABLISHED
tcp        0    514 linux.local:46042       174.37.182.114-stat:www ESTABLISHED
tcp        1      0 linux.local:54640       74.221.222.30:https     CLOSE_WAIT 
tcp        0      0 linux.local:39656       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:57989       74.114.28.200:www       ESTABLISHED
tcp        0      0 linux.local:39805       a92-123-207-139.d:https ESTABLISHED
tcp        0      0 linux.local:59156       flash91.ustream.tv:www  ESTABLISHED
tcp        0      0 linux.local:45693       212-67.livestream.:1935 ESTABLISHED
tcp        0      0 linux.local:52024       www-11-01-ash4.face:www ESTABLISHED
tcp        0      0 linux.local:36960       a148-123-13-18.depl:www ESTABLISHED
tcp        0      0 linux.local:34076       baymsg1020418.gate:msnp ESTABLISHED
tcp        0      0 linux.local:49822       arn06s01-in-f8.1e:https ESTABLISHED
tcp        0      0 linux.local:36915       a148-123-13-18.depl:www ESTABLISHED
tcp        0      0 linux.local:42013       www-11-02-ash3.fa:https ESTABLISHED
tcp        0      0 linux.local:36958       a148-123-13-18.depl:www ESTABLISHED
tcp        0      0 linux.local:43667       a92-123-205-177.d:https ESTABLISHED
tcp        0      0 linux.local:60941       lpp01m02-in-f103.:https ESTABLISHED
tcp        0      0 linux.local:47036       212-71.livestream.:1935 ESTABLISHED
tcp        0      0 linux.local:53396       arn06s01-in-f21.1:https ESTABLISHED
tcp        0      0 linux.local:39661       66.160.192.51:www       TIME_WAIT  
tcp        0    826 linux.local:53372       arn06s01-in-f21.1:https FIN_WAIT1  
tcp        1      0 linux.local:46022       212-67.livestream.c:www CLOSE_WAIT 
tcp        0    642 linux.local:53195       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:48349       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:53169       a148-123-13-58.depl:www ESTABLISHED
tcp        1      0 linux.local:55828       arn06s01-in-f5.1e10:www CLOSE_WAIT 
tcp        1      0 linux.local:51838       212-94.livestream.c:www CLOSE_WAIT 
tcp        0      0 linux.local:48154       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:52605       gw045.lphbs.com:https   ESTABLISHED
tcp        0      0 linux.local:39660       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:37623       2.16.177.55:www         ESTABLISHED
tcp        0      0 linux.local:34698       gw067.lphbs.com:https   ESTABLISHED
tcp        0    928 linux.local:60142       feijoa.canonical.co:www LAST_ACK   
tcp        0      0 linux.local:40376       a92-123-207-139.dep:www ESTABLISHED
tcp        0      0 linux.local:36247       OCSP.IAD3.VERISIGN.:www ESTABLISHED
tcp        0      0 linux.local:53168       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:39667       66.160.192.51:www       TIME_WAIT  
tcp        0    926 linux.local:60143       feijoa.canonical.co:www LAST_ACK   
tcp        0      0 linux.local:48350       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:39647       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:60847       arn06s02-in-f27.1e1:www ESTABLISHED
tcp        0      0 linux.local:39657       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:37652       2.16.177.55:www         ESTABLISHED
tcp        0      0 linux.local:39668       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:54556       arn06s02-in-f0.1e:https TIME_WAIT  
tcp        0      0 linux.local:42012       www-11-02-ash3.fa:https ESTABLISHED
tcp        1      0 linux.local:56029       212-72.livestream.c:www CLOSE_WAIT 
tcp        0      0 linux.local:56947       channel-hs-12-01-sn:www ESTABLISHED
tcp        0      0 linux.local:52293       arn06s02-in-f23.1:https ESTABLISHED
tcp        0      0 linux.local:53101       a148-123-13-58.depl:www ESTABLISHED
tcp        0      0 linux.local:39669       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:48153       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:44098       arn06s02-in-f21.1:https ESTABLISHED
tcp        0      0 linux.local:39664       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:39658       66.160.192.51:www       TIME_WAIT  
tcp        0      0 linux.local:39670       66.160.192.51:www       TIME_WAIT  
tcp        0    670 linux.local:48073       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:53398       arn06s01-in-f21.1:https TIME_WAIT  
tcp   491632      0 linux.local:33927       8.20.213.41:www         ESTABLISHED
tcp        0    672 linux.local:48074       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:60267       a148-123-13-27.depl:www ESTABLISHED
tcp        0      0 linux.local:44138       arn06s02-in-f21.1:https ESTABLISHED
tcp        0    925 linux.local:60159       feijoa.canonical.co:www ESTABLISHED
tcp        1      0 linux.local:45542       212-55.livestream.c:www CLOSE_WAIT 
tcp        0    679 linux.local:58501       social03.ustream.tv:www ESTABLISHED
tcp        0      0 linux.local:35022       www-11-02-ash3.face:www ESTABLISHED
tcp        0      0 linux.local:35960       fcds502.arn.llnw.n:1935 ESTABLISHED
tcp        0      0 linux.local:42057       www-11-02-ash3.fa:https ESTABLISHED
tcp        0    926 linux.local:60135       feijoa.canonical.co:www LAST_ACK   
tcp        0    926 linux.local:60141       feijoa.canonical.co:www LAST_ACK   
tcp        1      0 linux.local:44401       184-22-235-197.stat:www CLOSE_WAIT 
tcp        0      0 linux.local:38237       arn06s01-in-f0.1e10:www ESTABLISHED
tcp        0      0 linux.local:46976       CRL.VERISIGN.NET:www    ESTABLISHED
tcp        0      0 linux.local:48069       a148-123-13-17.depl:www ESTABLISHED
tcp        0      0 linux.local:59971       baymsg1010706.gate:msnp ESTABLISHED
tcp        0    925 linux.local:60136       feijoa.canonical.co:www FIN_WAIT1  
tcp        0      0 linux.local:35859       a148-123-13-59.depl:www ESTABLISHED
tcp        0    410 linux.local:50547       lpp01m02-in-f101.1e:www ESTABLISHED
tcp        0      0 linux.local:48279       a148-123-13-17.depl:www ESTABLISHED
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   Path
unix  12     [ ]         DGRAM                    11461    /dev/log
unix  2      [ ]         DGRAM                    6398     /var/run/wpa_supplicant/wlan0
unix  3      [ ]         STREAM     CONNECTED     53717    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     57438    
unix  3      [ ]         STREAM     CONNECTED     44971    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     57433    
unix  3      [ ]         STREAM     CONNECTED     49740    
unix  3      [ ]         STREAM     CONNECTED     49739    
unix  3      [ ]         STREAM     CONNECTED     44962    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     56926    
unix  3      [ ]         STREAM     CONNECTED     49705    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     54531    
unix  3      [ ]         STREAM     CONNECTED     56901    
unix  3      [ ]         STREAM     CONNECTED     56900    
unix  3      [ ]         SEQPACKET  CONNECTED     60064    
unix  3      [ ]         SEQPACKET  CONNECTED     60063    
unix  3      [ ]         STREAM     CONNECTED     60062    
unix  3      [ ]         STREAM     CONNECTED     60061    
unix  3      [ ]         STREAM     CONNECTED     57408    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     56755    
unix  3      [ ]         STREAM     CONNECTED     54517    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     53668    
unix  3      [ ]         STREAM     CONNECTED     57404    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     58430    
unix  3      [ ]         STREAM     CONNECTED     57403    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     58429    
unix  3      [ ]         STREAM     CONNECTED     49696    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     57400    
unix  3      [ ]         STREAM     CONNECTED     57396    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     49695    
unix  3      [ ]         STREAM     CONNECTED     56751    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     57395    
unix  3      [ ]         STREAM     CONNECTED     59946    
unix  3      [ ]         STREAM     CONNECTED     59945    
unix  3      [ ]         STREAM     CONNECTED     53664    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     57390    
unix  3      [ ]         STREAM     CONNECTED     57385    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     58421    
unix  3      [ ]         STREAM     CONNECTED     44940    /tmp/virt_1111
unix  3      [ ]         STREAM     CONNECTED     54493    
unix  3      [ ]         STREAM     CONNECTED     57377    /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     53653    
unix  3      [ ]         STREAM     CONNECTED     49691    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     56741    
unix  3      [ ]         STREAM     CONNECTED     44916    
unix  3      [ ]         STREAM     CONNECTED     44915    
unix  3      [ ]         STREAM     CONNECTED     44913    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     53605    
unix  3      [ ]         STREAM     CONNECTED     44888    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     54423    
unix  3      [ ]         STREAM     CONNECTED     55675    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     35786    
unix  3      [ ]         STREAM     CONNECTED     39895    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     54376    
unix  3      [ ]         STREAM     CONNECTED     54373    
unix  3      [ ]         STREAM     CONNECTED     54372    
unix  3      [ ]         STREAM     CONNECTED     35784    
unix  3      [ ]         STREAM     CONNECTED     35783    
unix  3      [ ]         STREAM     CONNECTED     44881    
unix  3      [ ]         STREAM     CONNECTED     44880    
unix  3      [ ]         STREAM     CONNECTED     53468    
unix  3      [ ]         STREAM     CONNECTED     53467    
unix  3      [ ]         STREAM     CONNECTED     52041    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     44730    
unix  3      [ ]         STREAM     CONNECTED     39852    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     48093    
unix  3      [ ]         STREAM     CONNECTED     49633    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     39850    
unix  3      [ ]         STREAM     CONNECTED     48089    
unix  3      [ ]         STREAM     CONNECTED     48088    
unix  3      [ ]         STREAM     CONNECTED     52930    
unix  3      [ ]         STREAM     CONNECTED     52929    
unix  3      [ ]         STREAM     CONNECTED     52927    
unix  3      [ ]         STREAM     CONNECTED     52926    
unix  3      [ ]         STREAM     CONNECTED     53450    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     52925    
unix  3      [ ]         STREAM     CONNECTED     52921    
unix  3      [ ]         STREAM     CONNECTED     52920    
unix  3      [ ]         STREAM     CONNECTED     39843    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     53449    
unix  2      [ ]         DGRAM                    52848    
unix  3      [ ]         SEQPACKET  CONNECTED     52847    
unix  3      [ ]         SEQPACKET  CONNECTED     52846    
unix  3      [ ]         SEQPACKET  CONNECTED     52844    
unix  3      [ ]         SEQPACKET  CONNECTED     52843    
unix  3      [ ]         STREAM     CONNECTED     49435    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     39714    
unix  3      [ ]         STREAM     CONNECTED     39303    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     29627    
unix  3      [ ]         STREAM     CONNECTED     44157    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     43346    
unix  3      [ ]         STREAM     CONNECTED     41618    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     42392    
unix  3      [ ]         STREAM     CONNECTED     39113    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     24512    
unix  3      [ ]         STREAM     CONNECTED     29420    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     33709    
unix  3      [ ]         STREAM     CONNECTED     42103    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     41510    
unix  3      [ ]         STREAM     CONNECTED     42060    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     39063    
unix  3      [ ]         STREAM     CONNECTED     33446    
unix  3      [ ]         STREAM     CONNECTED     33445    
unix  3      [ ]         STREAM     CONNECTED     33342    
unix  3      [ ]         STREAM     CONNECTED     33341    
unix  2      [ ]         STREAM     CONNECTED     38973    
unix  3      [ ]         STREAM     CONNECTED     38968    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     22497    
unix  3      [ ]         STREAM     CONNECTED     24397    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     37042    
unix  3      [ ]         STREAM     CONNECTED     37002    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     33230    
unix  2      [ ]         STREAM     CONNECTED     38944    /tmp/ksocket-skruf/krunnerVu1838.slave-socket
unix  3      [ ]         STREAM     CONNECTED     27902    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     17394    
unix  3      [ ]         STREAM     CONNECTED     23961    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     26150    
unix  3      [ ]         STREAM     CONNECTED     28800    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27819    
unix  3      [ ]         STREAM     CONNECTED     23923    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     27735    
unix  3      [ ]         STREAM     CONNECTED     9001     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     20453    
unix  3      [ ]         STREAM     CONNECTED     13208    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     16900    
unix  3      [ ]         STREAM     CONNECTED     13207    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     16899    
unix  3      [ ]         STREAM     CONNECTED     16898    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     19644    
unix  3      [ ]         STREAM     CONNECTED     13205    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     19643    
unix  3      [ ]         STREAM     CONNECTED     17918    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20979    
unix  3      [ ]         STREAM     CONNECTED     13073    /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     20515    
unix  3      [ ]         STREAM     CONNECTED     20514    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     18693    
unix  2      [ ]         SEQPACKET  CONNECTED     13731    
unix  3      [ ]         STREAM     CONNECTED     8152     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14481    
unix  3      [ ]         STREAM     CONNECTED     7045     /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     14477    
unix  3      [ ]         STREAM     CONNECTED     12989    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8142     
unix  3      [ ]         STREAM     CONNECTED     14476    /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     17456    
unix  3      [ ]         STREAM     CONNECTED     8731     /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     16506    
unix  3      [ ]         STREAM     CONNECTED     8730     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     8729     
unix  3      [ ]         STREAM     CONNECTED     12988    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     12987    
unix  3      [ ]         STREAM     CONNECTED     7041     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     12986    
unix  3      [ ]         STREAM     CONNECTED     7040     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8728     
unix  3      [ ]         STREAM     CONNECTED     7039     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7038     
unix  3      [ ]         STREAM     CONNECTED     8726     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8138     
unix  3      [ ]         STREAM     CONNECTED     14475    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7037     
unix  3      [ ]         STREAM     CONNECTED     14474    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8725     
unix  3      [ ]         STREAM     CONNECTED     8137     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14473    
unix  3      [ ]         STREAM     CONNECTED     12985    /tmp/virt_1111
unix  3      [ ]         STREAM     CONNECTED     8136     
unix  3      [ ]         STREAM     CONNECTED     13700    /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     8125     
unix  3      [ ]         STREAM     CONNECTED     7033     /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     7031     
unix  3      [ ]         STREAM     CONNECTED     7032     /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     7030     
unix  3      [ ]         STREAM     CONNECTED     7029     /tmp/ksocket-skruf/nepomuk-socket
unix  3      [ ]         STREAM     CONNECTED     7028     
unix  3      [ ]         STREAM     CONNECTED     8721     /var/run/xdmctl/dmctl-:0/socket
unix  3      [ ]         STREAM     CONNECTED     13697    
unix  3      [ ]         STREAM     CONNECTED     14457    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     8718     
unix  3      [ ]         STREAM     CONNECTED     12945    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     12944    
unix  3      [ ]         STREAM     CONNECTED     8114     /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     8113     
unix  3      [ ]         STREAM     CONNECTED     16361    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14415    
unix  3      [ ]         STREAM     CONNECTED     14414    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8683     
unix  3      [ ]         STREAM     CONNECTED     12838    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12026    
unix  3      [ ]         STREAM     CONNECTED     8068     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     8067     
unix  3      [ ]         STREAM     CONNECTED     11995    
unix  3      [ ]         STREAM     CONNECTED     11994    
unix  2      [ ]         DGRAM                    13671    
unix  3      [ ]         STREAM     CONNECTED     13668    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8066     
unix  3      [ ]         STREAM     CONNECTED     6980     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6979     
unix  3      [ ]         STREAM     CONNECTED     8643     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6978     
unix  3      [ ]         STREAM     CONNECTED     8060     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11979    
unix  3      [ ]         STREAM     CONNECTED     14404    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     8638     
unix  3      [ ]         STREAM     CONNECTED     12828    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     12827    
unix  3      [ ]         STREAM     CONNECTED     14389    /tmp/virt_1111
unix  3      [ ]         STREAM     CONNECTED     13657    
unix  3      [ ]         STREAM     CONNECTED     10197    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     6975     
unix  3      [ ]         STREAM     CONNECTED     6974     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     8630     
unix  3      [ ]         STREAM     CONNECTED     6973     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6972     
unix  3      [ ]         STREAM     CONNECTED     8625     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     12813    
unix  3      [ ]         STREAM     CONNECTED     8620     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8619     
unix  3      [ ]         STREAM     CONNECTED     12808    /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     6963     
unix  3      [ ]         STREAM     CONNECTED     12798    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14380    
unix  3      [ ]         STREAM     CONNECTED     12765    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12764    
unix  3      [ ]         STREAM     CONNECTED     12762    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14365    
unix  3      [ ]         STREAM     CONNECTED     8570     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13609    
unix  3      [ ]         STREAM     CONNECTED     7971     /home/skruf/.pulse/2ea1526576b5782e19c7e24600000238-runtime/native
unix  3      [ ]         STREAM     CONNECTED     14364    
unix  3      [ ]         STREAM     CONNECTED     7965     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10159    
unix  3      [ ]         STREAM     CONNECTED     11934    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10156    
unix  3      [ ]         STREAM     CONNECTED     12760    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13605    
unix  3      [ ]         STREAM     CONNECTED     10153    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12759    
unix  3      [ ]         STREAM     CONNECTED     7963     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13604    
unix  3      [ ]         STREAM     CONNECTED     11931    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     12758    
unix  3      [ ]         STREAM     CONNECTED     11928    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6924     
unix  3      [ ]         STREAM     CONNECTED     7960     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     12757    
unix  3      [ ]         STREAM     CONNECTED     10152    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12756    
unix  3      [ ]         STREAM     CONNECTED     11925    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14354    
unix  3      [ ]         STREAM     CONNECTED     12751    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13601    
unix  3      [ ]         STREAM     CONNECTED     12750    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13599    
unix  3      [ ]         STREAM     CONNECTED     11917    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14352    
unix  3      [ ]         STREAM     CONNECTED     13593    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8565     
unix  3      [ ]         STREAM     CONNECTED     8564     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7958     
unix  3      [ ]         STREAM     CONNECTED     12749    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     13590    
unix  3      [ ]         STREAM     CONNECTED     12748    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14350    
unix  3      [ ]         STREAM     CONNECTED     11908    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14347    
unix  3      [ ]         STREAM     CONNECTED     11907    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13589    
unix  3      [ ]         STREAM     CONNECTED     12747    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     14345    
unix  3      [ ]         STREAM     CONNECTED     11902    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     14342    
unix  3      [ ]         STREAM     CONNECTED     14387    /tmp/virt_1111
unix  3      [ ]         STREAM     CONNECTED     11884    
unix  3      [ ]         STREAM     CONNECTED     13576    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     13575    
unix  3      [ ]         STREAM     CONNECTED     11882    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     13574    
unix  3      [ ]         STREAM     CONNECTED     11881    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     6901     
unix  3      [ ]         STREAM     CONNECTED     11880    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     12741    
unix  3      [ ]         STREAM     CONNECTED     11879    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     12740    
unix  3      [ ]         STREAM     CONNECTED     8551     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6897     
unix  3      [ ]         STREAM     CONNECTED     11877    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     8550     
unix  3      [ ]         STREAM     CONNECTED     7944     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6896     
unix  3      [ ]         STREAM     CONNECTED     12738    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     8549     
unix  3      [ ]         STREAM     CONNECTED     12737    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     12736    
unix  3      [ ]         STREAM     CONNECTED     12733    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     6893     
unix  3      [ ]         STREAM     CONNECTED     7939     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11876    
unix  3      [ ]         STREAM     CONNECTED     12732    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8546     
unix  3      [ ]         STREAM     CONNECTED     13569    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     12730    
unix  3      [ ]         STREAM     CONNECTED     13568    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     12729    
unix  3      [ ]         STREAM     CONNECTED     12728    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     12727    
unix  3      [ ]         STREAM     CONNECTED     8543     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     7936     
unix  3      [ ]         STREAM     CONNECTED     8542     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     8541     
unix  3      [ ]         STREAM     CONNECTED     7935     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     10150    
unix  3      [ ]         STREAM     CONNECTED     7934     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     12726    
unix  3      [ ]         STREAM     CONNECTED     11869    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     12725    
unix  3      [ ]         STREAM     CONNECTED     10149    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     6844     
unix  3      [ ]         STREAM     CONNECTED     10148    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     12724    
unix  3      [ ]         STREAM     CONNECTED     13566    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     7933     
unix  3      [ ]         STREAM     CONNECTED     13564    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6843     
unix  3      [ ]         STREAM     CONNECTED     7932     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     6842     
unix  3      [ ]         STREAM     CONNECTED     7931     /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     7930     
unix  3      [ ]         STREAM     CONNECTED     11244    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     11243    
unix  3      [ ]         STREAM     CONNECTED     12723    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     11242    
unix  3      [ ]         STREAM     CONNECTED     12722    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     6841     
unix  3      [ ]         STREAM     CONNECTED     11241    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11240    
unix  3      [ ]         STREAM     CONNECTED     10147    /home/skruf/.local/share/akonadi/socket-linux/akonadiserver.socket
unix  3      [ ]         STREAM     CONNECTED     13563    
unix  3      [ ]         STREAM     CONNECTED     12721    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     10143    
unix  3      [ ]         STREAM     CONNECTED     11236    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     11235    
unix  3      [ ]         STREAM     CONNECTED     13561    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8532     
unix  3      [ ]         STREAM     CONNECTED     7926     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     8531     
unix  3      [ ]         STREAM     CONNECTED     12720    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11234    
unix  3      [ ]         STREAM     CONNECTED     7920     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7919     
unix  3      [ ]         STREAM     CONNECTED     12719    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10142    
unix  3      [ ]         STREAM     CONNECTED     11863    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13558    
unix  3      [ ]         STREAM     CONNECTED     12712    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     12711    
unix  3      [ ]         STREAM     CONNECTED     11232    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11231    
unix  3      [ ]         STREAM     CONNECTED     12709    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11230    
unix  3      [ ]         STREAM     CONNECTED     6832     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7918     
unix  3      [ ]         STREAM     CONNECTED     12708    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10141    
unix  3      [ ]         STREAM     CONNECTED     6831     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     6830     
unix  3      [ ]         STREAM     CONNECTED     7917     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     12706    
unix  3      [ ]         STREAM     CONNECTED     11861    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     7916     
unix  3      [ ]         STREAM     CONNECTED     6829     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11860    
unix  3      [ ]         STREAM     CONNECTED     11229    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10140    
unix  3      [ ]         STREAM     CONNECTED     11228    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11856    
unix  3      [ ]         STREAM     CONNECTED     12699    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7910     
unix  3      [ ]         STREAM     CONNECTED     12698    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11227    
unix  3      [ ]         STREAM     CONNECTED     12697    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12696    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10131    
unix  3      [ ]         STREAM     CONNECTED     13546    
unix  3      [ ]         STREAM     CONNECTED     11223    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     12690    
unix  3      [ ]         STREAM     CONNECTED     11222    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     11221    
unix  3      [ ]         STREAM     CONNECTED     11842    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10119    
unix  3      [ ]         STREAM     CONNECTED     11220    /home/skruf/.local/share/akonadi/socket-linux/mysql.socket
unix  3      [ ]         STREAM     CONNECTED     7896     
unix  3      [ ]         STREAM     CONNECTED     12684    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13528    
unix  3      [ ]         STREAM     CONNECTED     11219    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13521    
unix  3      [ ]         STREAM     CONNECTED     7890     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11826    
unix  3      [ ]         STREAM     CONNECTED     6813     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10109    
unix  3      [ ]         STREAM     CONNECTED     10108    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     8508     
unix  3      [ ]         STREAM     CONNECTED     8506     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     7888     
unix  3      [ ]         STREAM     CONNECTED     6812     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     8505     
unix  3      [ ]         STREAM     CONNECTED     8499     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7887     
unix  3      [ ]         STREAM     CONNECTED     11204    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11203    
unix  2      [ ]         DGRAM                    11202    
unix  3      [ ]         STREAM     CONNECTED     11196    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11195    
unix  3      [ ]         STREAM     CONNECTED     12664    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     10096    
unix  3      [ ]         STREAM     CONNECTED     11822    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6802     
unix  3      [ ]         STREAM     CONNECTED     8483     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7880     
unix  3      [ ]         STREAM     CONNECTED     8481     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10088    
unix  3      [ ]         STREAM     CONNECTED     12648    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     10085    
unix  3      [ ]         STREAM     CONNECTED     7870     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6799     
unix  3      [ ]         STREAM     CONNECTED     7868     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11805    
unix  3      [ ]         STREAM     CONNECTED     11750    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11179    
unix  3      [ ]         STREAM     CONNECTED     11749    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11178    
unix  3      [ ]         STREAM     CONNECTED     13449    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11175    
unix  3      [ ]         STREAM     CONNECTED     7865     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13438    
unix  3      [ ]         STREAM     CONNECTED     7864     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     11173    
unix  3      [ ]         STREAM     CONNECTED     7863     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11171    
unix  3      [ ]         STREAM     CONNECTED     7858     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11168    
unix  3      [ ]         STREAM     CONNECTED     7857     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12645    
unix  3      [ ]         STREAM     CONNECTED     11737    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13430    
unix  3      [ ]         STREAM     CONNECTED     11726    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11167    
unix  3      [ ]         STREAM     CONNECTED     8473     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13420    
unix  3      [ ]         STREAM     CONNECTED     12642    @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     7839     
unix  3      [ ]         STREAM     CONNECTED     11125    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7838     
unix  3      [ ]         STREAM     CONNECTED     11721    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11123    
unix  3      [ ]         STREAM     CONNECTED     7832     @/tmp/.ICE-unix/1756
unix  3      [ ]         STREAM     CONNECTED     13385    
unix  3      [ ]         STREAM     CONNECTED     7831     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13384    
unix  3      [ ]         STREAM     CONNECTED     11711    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     13381    
unix  3      [ ]         STREAM     CONNECTED     7830     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13380    
unix  3      [ ]         STREAM     CONNECTED     7828     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     13371    
unix  3      [ ]         STREAM     CONNECTED     8471     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13368    
unix  3      [ ]         STREAM     CONNECTED     11710    /tmp/ksocket-skruf/kdeinit4__0
unix  3      [ ]         STREAM     CONNECTED     13364    
unix  3      [ ]         STREAM     CONNECTED     12635    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13355    
unix  3      [ ]         STREAM     CONNECTED     12632    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11683    
unix  3      [ ]         STREAM     CONNECTED     11117    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11681    
unix  3      [ ]         STREAM     CONNECTED     13347    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11672    
unix  3      [ ]         STREAM     CONNECTED     11665    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11112    
unix  3      [ ]         STREAM     CONNECTED     11662    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     13338    
unix  3      [ ]         STREAM     CONNECTED     11656    @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11111    
unix  3      [ ]         STREAM     CONNECTED     7782     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13329    
unix  3      [ ]         STREAM     CONNECTED     13319    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11109    
unix  3      [ ]         STREAM     CONNECTED     7770     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     11106    
unix  3      [ ]         STREAM     CONNECTED     11649    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11648    
unix  3      [ ]         STREAM     CONNECTED     7766     @/tmp/dbus-bRdWLn6Z4P
unix  3      [ ]         STREAM     CONNECTED     6144     
unix  3      [ ]         STREAM     CONNECTED     6140     
unix  3      [ ]         STREAM     CONNECTED     6139     
unix  3      [ ]         STREAM     CONNECTED     6118     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6766     
unix  3      [ ]         STREAM     CONNECTED     12628    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6765     
unix  3      [ ]         STREAM     CONNECTED     6097     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     7761     
unix  3      [ ]         STREAM     CONNECTED     11093    
unix  3      [ ]         STREAM     CONNECTED     11092    
unix  3      [ ]         STREAM     CONNECTED     6095     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11623    
unix  2      [ ]         DGRAM                    6079     
unix  3      [ ]         STREAM     CONNECTED     9932     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6071     
unix  3      [ ]         STREAM     CONNECTED     9929     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6752     
unix  3      [ ]         STREAM     CONNECTED     9923     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7752     
unix  3      [ ]         STREAM     CONNECTED     9922     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6068     
unix  3      [ ]         STREAM     CONNECTED     6058     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9913     
unix  3      [ ]         STREAM     CONNECTED     7742     
unix  3      [ ]         STREAM     CONNECTED     7741     
unix  3      [ ]         STREAM     CONNECTED     7740     
unix  3      [ ]         STREAM     CONNECTED     7739     
unix  3      [ ]         STREAM     CONNECTED     7735     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6056     
unix  3      [ ]         STREAM     CONNECTED     8461     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     6700     
unix  2      [ ]         DGRAM                    6699     
unix  3      [ ]         STREAM     CONNECTED     8459     
unix  3      [ ]         STREAM     CONNECTED     8458     
unix  3      [ ]         STREAM     CONNECTED     7707     /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     6045     
unix  2      [ ]         DGRAM                    10667    
unix  2      [ ]         DGRAM                    6381     
unix  3      [ ]         STREAM     CONNECTED     12548    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9828     
unix  2      [ ]         DGRAM                    9820     
unix  3      [ ]         STREAM     CONNECTED     5851     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7603     
unix  3      [ ]         STREAM     CONNECTED     5848     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10573    
unix  2      [ ]         DGRAM                    10570    
unix  3      [ ]         STREAM     CONNECTED     10564    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11496    
unix  3      [ ]         STREAM     CONNECTED     11491    
unix  3      [ ]         STREAM     CONNECTED     11490    
unix  2      [ ]         DGRAM                    11487    
unix  3      [ ]         STREAM     CONNECTED     10563    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9799     
unix  2      [ ]         DGRAM                    9798     
unix  3      [ ]         STREAM     CONNECTED     7593     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12541    
unix  3      [ ]         STREAM     CONNECTED     10556    
unix  3      [ ]         STREAM     CONNECTED     10555    
unix  3      [ ]         STREAM     CONNECTED     10507    @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     12479    
unix  3      [ ]         DGRAM                    12418    
unix  3      [ ]         DGRAM                    12417    
unix  3      [ ]         STREAM     CONNECTED     12379    @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     5660   
```

**lsmod**
```
$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
dm_crypt               22565  0 
ppdev                  12849  0 
arc4                   12473  2 
snd_hda_codec_hdmi     31426  4 
binfmt_misc            17292  1 
ses                    17217  0 
enclosure              14744  1 ses
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
ath5k                 145100  0 
nvidia              10782577  42 
snd_hda_intel          24262  6 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ath                    19387  1 ath5k
eeepc_wmi              12722  0 
asus_wmi               19333  1 eeepc_wmi
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
sparse_keymap          13658  1 asus_wmi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393459  1 ath5k
mxm_wmi                12859  0 
cfg80211              172427  3 ath5k,ath,mac80211
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  2 asus_wmi,mxm_wmi
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
usb_storage            44173  0 
firewire_core          56937  1 firewire_ohci
vesafb                 13489  1 
usbhid                 41905  0 
hid                    77367  1 usbhid
uas                    17699  0 
crc_itu_t              12627  1 firewire_core
xhci_hcd               72982  0 
e1000e                139814  0 
ahci                   21634  2 
libahci                25727  1 ahci
```

**ifconfig**
```
$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:0f:cb:b3:19:35  
          inet addr:192.168.0.190  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:cbff:feb3:1935/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:622936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:434711 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:816849941 (816.8 MB)  TX bytes:53201555 (53.2 MB)

```

**iwconfig**
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"dlink"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1E:58:39:3F:3E   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3476  Invalid misc:3767   Missed beacon:0

```

**/etc/network/interfaces**
```
auto lo
iface lo inet loopback

# The primary network interface
auto wlan0
iface wlan0 inet static
	wpa-ssid dlink
	wpa-psk ***
	address 192.168.0.190
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
```

**/etc/resolv.conf**
```
nameserver 192.168.0.1
```

**Pinging**[www.ubuntuforums.org](www.ubuntuforums.org)
```
$ ping www.ubuntuforums.org
PING www.ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=45 time=52.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=45 time=46.3 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=45 time=46.9 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=45 time=45.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=5 ttl=45 time=45.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=6 ttl=45 time=46.8 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=7 ttl=45 time=45.9 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=8 ttl=45 time=54.4 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=9 ttl=45 time=51.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=10 ttl=45 time=56.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=11 ttl=45 time=57.0 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=12 ttl=45 time=52.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=13 ttl=45 time=52.3 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=14 ttl=45 time=46.0 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=16 ttl=45 time=48.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=17 ttl=45 time=45.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=18 ttl=45 time=45.7 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=19 ttl=45 time=46.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=20 ttl=45 time
```

Couple of things I've tried:
[LIST]
[*]Diffrent browsers, including Konqueror, Chromium and Firefox
[*]Disabling IPv6
[*]Recompiling the ath5k driver from latest git
[*]Changing between WPA, WPA2 and TKIP, AES on my router
[/LIST]

Any assistance on this problem would be greatly appreciated,

Thanks in advance!

---

### Post by KrisDouglas on 2012-01-05
Hello, this seems almost identical to what I am experiencing. Any theories that this could be a bug?

[http://ubuntuforums.org/showthread.php?t=1904264](http://ubuntuforums.org/showthread.php?t=1904264)

---

### Post by logiq on 2012-01-05
After reading your thread a little closer, disregard what I said if you read it before this last edit. Could possibly very well be a bug. 

Did you have any packages installed that might have taken effect after you rebooted, though?

---

### Post by logiq on 2012-01-05
Here's a screenshot of firebug's "Net" tab:

[http://www.bildedump.no/pics/6adc37930ae74c43ff9040cc181c1940.png]("http://www.bildedump.no/pics/6adc37930ae74c43ff9040cc181c1940.png")

Nothing is cached, and DNS lookup was fast. This was just a slow transfer, but very often it gets stuck, and wont ever load.

---

### Post by KrisDouglas on 2012-01-05
It seems that screenshot you sent is a thumbnail. There is a slight difference between our posts because I am able to get a good connection if directly referring to the server's IP. 

Do you experience this problem?

---

### Post by spacecheck on 2012-01-05
Please disregard, entry was inaccurate. Sorry.

Spacecheck
(just don't let it bounce)

---

### Post by logiq on 2012-01-05
> **KrisDouglas said:**
> It seems that screenshot you sent is a thumbnail. There is a slight difference between our posts because I am able to get a good connection if directly referring to the server's IP. 

Do you experience this problem?

Oops, I linked the thumbnail ---fixed now!

Our issues are most likely not related then, as DNS lookups are working just fine on my part.

---

