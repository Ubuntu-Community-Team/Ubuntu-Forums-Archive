---
title: "Wireless conencts but no internet and VPNs don't work"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by mortemdei on 2013-02-21
Hi everyone, I have the following problem. I can connect to the internet with using cable, but the wireless isn't working properly on ubuntu 12.04 (it works on windows).  It says it's connected, it gives me an ip and I can even ping webpages, but 99% of the times pages don't load in the browser. Also, if I connect to any VPN with the cabel network the VPN connects but no data is sent or received.

Thanks

```
mortemdei@morsdei:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 84:8f:69:c4:a7:a4  
          Direc. inet:192.168.1.101  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::868f:69ff:fec4:a7a4/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5226 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4680 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:4500143 (4.5 MB)  TX bytes:654627 (654.6 KB)
          Interrupción:50 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:5599 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5599 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:427093 (427.0 KB)  TX bytes:427093 (427.0 KB)

wlan0     Link encap:Ethernet  direcciónHW 4c:80:93:9d:6d:a4  
          Direc. inet:192.168.1.133  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::4e80:93ff:fe9d:6da4/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:464 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:31 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:114156 (114.1 KB)  TX bytes:6222 (6.2 KB)

```

```
mortemdei@morsdei:~$ route
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
default         DD-WRT          0.0.0.0         UG    0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
```

```
mortemdei@morsdei:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Guzman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:AD:AA:CA   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=21/70  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by MrsUser on 2013-02-21
I once had this problem because the power saving mode of the wifi card was enabled. You can try:

```
sudo iwconfig wlan0 power off
```

---

### Post by varunendra on 2013-02-21
> **MrsUser said:**
> I once had this problem because the power saving mode of the wifi card was enabled. You can try:

```
sudo iwconfig wlan0 power off
```
Apparently, the pm is already off -

> **mortemdei said:**
> 
```
mortemdei@morsdei:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Guzman"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:AD:AA:CA   
          **Bit Rate=[COLOR="Navy"]1 Mb/s[/COLOR]   Tx-Power=15 dBm**   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          **Power Management:[COLOR="Red"]off[/COLOR]**
          **Link Quality=[COLOR="Navy"]21[/COLOR]/70**  Signal level=-89 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26   Missed beacon:0

```
However, both the signal strength and negotiated speed are too bad. 1Mb/s is practically unusable.

Try getting closer to the access point to get stronger signals. Then try re-connecting wireless to see if it connects with any better speeds (Bit Rate=...)

If not, we can try to force a higher bit rate that is supported by the access point. To determine that, please post output of -
```
iwlist wlan0 scan
```


**Edit:**
Oh, almost forgot..

Welcome to Ubuntu Forums mortemdei ! :)

---

