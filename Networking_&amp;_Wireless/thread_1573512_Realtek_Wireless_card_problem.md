---
title: "Realtek Wireless card problem"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by juseus on 2010-09-12
I have a Toshiba Satellite series laptop, i get ubuntu on it, all works well but there's a problem, my wireless card doesn't work, it doesn't show me the aviable wireless network, my Wireless Card is an Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) but it works in windows. I used  Ubuntu 8.04.4 LTS.
 

When i run these codes that's what it shows:

-ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1d:60:f5:10:b6  
          inet dirección:192.168.2.8  Difusión:192.168.2.255  Máscara:255.255.255.0
          dirección inet6: fe80::21d:60ff:fef5:10b6/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:57795 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46095 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          RX bytes:74634487 (71.1 MB)  TX bytes:5812643 (5.5 MB)
          Interrupción:16 Dirección base: 0xc800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          Paquetes RX:1338 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1338 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          RX bytes:66900 (65.3 KB)  TX bytes:66900 (65.3 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:16:44:6f:98:67  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  direcciónHW 00:16:44:6f:98:67  
          inet dirección:169.254.6.79  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1

-iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=67  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

Thanks if anybody could help me.

---

### Post by MaindotC on 2010-09-12
Please post any shell output in ```
 tags:[code]It should look like this
```

Please consult the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide) and let us know if you have any difficulty and precisely where so we can better help you.

Your card is detected (which is why you see wlan0) but this seems to be a driver issue.  Find your driver and make sure that is the one that should be used with your network card.

---

### Post by bkratz on 2010-09-12
> **juseus said:**
> I have a Toshiba Satellite series laptop, i get ubuntu on it, all works well but there's a problem, my wireless card doesn't work, it doesn't show me the aviable wireless network, my Wireless Card is an Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) but it works in windows. I used  Ubuntu 8.04.4 LTS.
 

When i run these codes that's what it shows:

-ifconfig

eth0      Link encap:Ethernet  direcciónHW 00:1d:60:f5:10:b6  
          inet dirección:192.168.2.8  Difusión:192.168.2.255  Máscara:255.255.255.0
          dirección inet6: fe80::21d:60ff:fef5:10b6/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:57795 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:46095 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          RX bytes:74634487 (71.1 MB)  TX bytes:5812643 (5.5 MB)
          Interrupción:16 Dirección base: 0xc800 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          Paquetes RX:1338 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1338 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          RX bytes:66900 (65.3 KB)  TX bytes:66900 (65.3 KB)

wlan0     Link encap:Ethernet  direcciónHW 00:16:44:6f:98:67  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:0 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:0 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  direcciónHW 00:16:44:6f:98:67  
          inet dirección:169.254.6.79  Difusión:169.254.255.255  Máscara:255.255.0.0
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1

-iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=67  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

Thanks if anybody could help me.

I believe the part number above is actually the ethernet controller not your wireless card.  RTL-8139/8139C/8139C+ is the same controller I have. Please post the output of 

```
lspci | grep Wireless
```

or just lspci if you get nothing from the above. By the way that is LSPCI in lowercase;

---

### Post by MaindotC on 2010-09-12
> **bkratz said:**
> I believe the part number above is actually the ethernet controller not your wireless card.  RTL-8139/8139C/8139C+ is the same controller I have. Please post the output of 

```
lspci | grep Wireless
```

or just lspci if you get nothing from the above. By the way that is LSPCI in lowercase;

These directions are already included in the official troubleshooting guide I listed.  Please do not reiterate directions.

---

### Post by bkratz on 2010-09-12
> **strAlan said:**
> These directions are already included in the official troubleshooting guide I listed.  Please do not reiterate directions.


Since you obviously did not look, we posted at about the same time. Sorry to have intruded on your thread.

---

