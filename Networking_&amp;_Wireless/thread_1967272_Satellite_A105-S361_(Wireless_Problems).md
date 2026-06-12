---
title: "Satellite A105-S361 (Wireless Problems)"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by zdeuyo on 2012-04-28
Hello Forum,


The problem I am having is with my Satellite A105-S361 - Laptop. After upgrading to 12.04 everything worked great. The problem now is that I cannot connect via wireless internet. It notices that the network is there and ask for the key and I enter and it says established but then it does not work. It works on all other laptops. Also, it works fine via Ethernet connection


Specs:
n, Intel Pentium® M Processor 760, 1024MB 
DDR2 SDRAM, 120GB (5400 RPM) Serial-ATA (SATA), DVD SuperMulti (+/-R Double 
Layer), 15.4” widescreen TruBrite™ WXGA, Intel® Graphics Media Accelerator 900, 
Intel® PRO/Wireless 2200BG, CD control buttons, 5-in-1 Bridge Media Adapter, 
ExpressCard™

Please help.

---

### Post by zdeuyo on 2012-04-28
Hello Forum,


I found a solution.

```


sudo apt-get update
sudo apt-get upgrade


```

solved.

restarted, still works.

SOLVED

---

