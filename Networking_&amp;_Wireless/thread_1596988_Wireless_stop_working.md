---
title: "Wireless stop working"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by persapiens on 2010-10-14
Hi all,

    I've upgraded from 10.04 to 10.10 ubuntu remix and wireless worked after the upgrade.

    When I run "Hardware Drivers", two options appeared:
    - Broadcom B43 wireless driver: when I tried to activate it, results: "System error: installArquives() failed!"
    - Wireless driver Broadcom STA: when I tried to activate it, results the same: "System error: installArquives() failed!"

    When my machine were 10.04, I've installed the first option.

    How can I solve it? Should I reinstall ubuntu?

    My machine is dell inspiron mini 10

    Thanks in advance.

---

### Post by johnnytm on 2010-10-14
where u connected to the internet when u tried to install the driver?
word of advice use the sta driver only. otherwise you will have conflicts. if u were connected to the internet before but install failed try the following from terminal
 ```
 sudo apt-get install patch  
 sudo apt-get install bcmwl-kernel-source
```

---

### Post by Hakunka-Matata on 2010-10-14
> [http://ubuntuforums.org/showthread.php?t=1592544](http://ubuntuforums.org/showthread.php?t=1592544)

All about your problem

---

### Post by persapiens on 2010-10-15
When I try to run "sudo apt-get install patch", i got the error:

Configurando firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: erro processando firmware-b43-installer (--configure):
 sub-processo script post-installation instalado retornou estado de saída de erro 1
Configurando patch (2.6-2ubuntu1) ...
Erros foram encontrados durante o processamento de:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any advice?

---

### Post by persapiens on 2010-10-17
I could finally install bcmwl-kernel-source.
I don't know exactly how, but i reinstall ubuntu 10.10 and patch and bcmwl-kernel-source. After somes tries, it is working.

Now, ubuntu detects only 'Wireless driver Broadcom STA' (active). The option 'Broadcom B43 wireless driver' is not shown anymore.

---

