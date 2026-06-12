---
title: "Problem with HVR4000"
date: 2009-07-08
forum: Multimedia Software
---

### Post by sperwer on 2009-07-08
Hi
I have problem making HVR4000 functioning i ubuntu 9.04.
I can see im not the only one with the problem.

I have tried to follow the guide at:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000)
Still without succes.

Result of dmesg | grep DVB:
```
tv@tv-desktop:~$ dmesg | grep DVB
[    9.493069] cx88[0]: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68,autodetected], frontend(s): 2
[    9.674861] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xf4)
[    9.736646] cx88[0]/2: subsystem: 0070:6902, board: Hauppauge WinTV-HVR4000 DVB-S/S2/T/Hybrid [card=68]
[    9.736649] cx88[0]/2: cx2388x based DVB/ATSC card
[    9.809549] DVB: registering new adapter (cx88[0])
[    9.809553] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
[    9.809782] DVB: registering adapter 0 frontend 1 (Conexant CX22702 DVB-T)...
tv@tv-desktop:~$ 

```
Result of dmesg | grep dvb:
```
tv@tv-desktop:~$ dmesg | grep dvb
[    9.736639] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    9.736643] cx88/2: registering cx8802 driver, type: dvb access: shared
[  152.595298] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  152.595304] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  160.128680] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  160.128685] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  176.804189] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  176.804195] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  180.780719] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  180.780723] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  185.743443] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  185.743449] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  189.720034] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  189.720040] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  194.185788] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  194.185794] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  199.155712] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  199.155717] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  203.641213] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  203.641218] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
[  223.728687] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[  223.728694] cx8800 0000:01:05.0: firmware: requesting dvb-fe-cx24116.fw
tv@tv-desktop:~$ 

```

Result of dmesg | grep CX24116:
```
tv@tv-desktop:~$ dmesg | grep CX24116
[    9.809553] DVB: registering adapter 0 frontend 0 (Conexant CX24116/CX24118)...
tv@tv-desktop:~$ 

```

It looks like the firmware isn't loading.
What am i doing wrong.

Sperwer

---

