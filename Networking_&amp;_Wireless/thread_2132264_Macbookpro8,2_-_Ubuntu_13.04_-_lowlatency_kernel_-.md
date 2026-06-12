---
title: "Macbookpro8,2 - Ubuntu 13.04 - lowlatency kernel - problem installing wireless driver"
date: 2013-04-04
forum: Networking &amp; Wireless
---

### Post by miguelnegrao on 2013-04-04
Hi

I'm running ubuntu 13.04. When I installed it on my MacBookpro8,2 I was able to install the drivers by doing "sudo apt-get install linux-firmware-nonfree".  After I installed the lowlatency kernel the wireless driver stopped working:

```

miguel@miguel-MacBookPro:~$ uname -a
Linux miguel-MacBookPro 3.8.0-14-lowlatency #9-Ubuntu SMP PREEMPT Mon Mar 25 10:49:31 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I've attemped re-installing it for the new kernel but if fails. I was running the command "sudo apt-get install--reinstall linux-firmware-nonfree"

```
Após esta operação, serão utilizados 0 B adicionais de espaço em disco.

AVISO: Os seguintes pacotes não podem ser autenticados!

  bcmwl-kernel-source

Instalar estes pacotes sem verificação [y/N]? y



(A ler a base de dados ... 
(A ler a base de dados ... 5%
(A ler a base de dados ... 10%
(A ler a base de dados ... 15%
(A ler a base de dados ... 20%
(A ler a base de dados ... 25%
(A ler a base de dados ... 30%
(A ler a base de dados ... 35%
(A ler a base de dados ... 40%
(A ler a base de dados ... 45%
(A ler a base de dados ... 50%
(A ler a base de dados ... 55%
(A ler a base de dados ... 60%
(A ler a base de dados ... 65%
(A ler a base de dados ... 70%
(A ler a base de dados ... 75%
(A ler a base de dados ... 80%
(A ler a base de dados ... 85%
(A ler a base de dados ... 90%
(A ler a base de dados ... 95%
(A ler a base de dados ... 100%
(A ler a base de dados ... 215298 ficheiros e directórios actualmente instalados.)

A preparar para substituir bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6 (a usar .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...

Removing all DKMS Modules

Done.

A descompactar substituto bcmwl-kernel-source ...

A instalar bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...

Loading new bcmwl-6.20.155.1+bdcom DKMS files...

Building for 3.8.0-14-lowlatency and 3.8.0-15-generic

Building for architecture x86_64

Building initial module for 3.8.0-14-lowlatency

Error! Bad return status for module build on kernel: 3.8.0-14-lowlatency (x86_64)

Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.

FATAL: Module wl not found.

update-initramfs: deferring update (trigger activated)

A processar 'triggers' para initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-3.8.0-15-generic
```

I attach also the log file mentioned above. 

Does anyone know how get this installed ?

thank you,
Miguel Negrão

---

### Post by chili555 on 2013-04-04
linux-firmware-nonfree accompanies the driver b43. However, your install seems to be, instead for bcmwl-kernel-source which provides the driver wl. These are not interchangeable. Some devices work with one and not at all with the other. Some devices may work with either driver but certainly work much better with one or the other. Before you struggle to install what may be the wrong driver, let's see which one you actually need. Please run and post:```
lspci -nn | grep 0280
```By the way, once the firmware package is installed, it's there forever until you reinstall.

---

### Post by miguelnegrao on 2013-04-04
> **chili555 said:**
> linux-firmware-nonfree accompanies the driver b43. However, your install seems to be, instead for bcmwl-kernel-source which provides the driver wl. These are not interchangeable. Some devices work with one and not at all with the other. Some devices may work with either driver but certainly work much better with one or the other. Before you struggle to install what may be the wrong driver, let's see which one you actually need. Please run and post:```
lspci -nn | grep 0280
```By the way, once the firmware package is installed, it's there forever until you reinstall.

Yes, indeed I made a confusion, the command whose output I posted was "sudo apt-get install --reinstall bcmwl-kernel-source", I had read on some forum this could solve my problem. I have also tried "sudo apt-get install --reinstall linux-kernel-nonfree" but didn't seem to help.

Here is the output asked for:
```

miguel@miguel-MacBookPro:~$ lspci -nn | grep 0280
03:00.0 Network controller [0280]: Broadcom Corporation BCM4331 802.11a/b/g/n [14e4:4331] (rev 02

```

Miguel

---

### Post by chili555 on 2013-04-04
> Broadcom Corporation BCM4331 802.11a/b/g/n [[COLOR="#FF0000"]14e4:4331[/COLOR]]There is a bit of controversy about the proper way to get this device going. We may have to try a few things before it's solved. First, let's verify that you have the nedded firmware for the first method:```
ls /lib/firmware/b43
```We don't need to see the whole output, we just need to know that there are quite a few .fw files there. If so, please proceed:```
sudo modprobe bcma
iwconfig
sudo iwlist wlan0 scan
```If this helps, we'll make a few changes to make it persistent.

---

### Post by miguelnegrao on 2013-04-04
Hi

> **chili555 said:**
> There is a bit of controversy about the proper way to get this device going. We may have to try a few things before it's solved. First, let's verify that you have the nedded firmware for the first method:```
ls /lib/firmware/b43
```We don't need to see the whole output, we just need to know that there are quite a few .fw files there. 

Yes, there are many files in that folder.

> 
If so, please proceed:```
sudo modprobe bcma
iwconfig
sudo iwlist wlan0 scan
```If this helps, we'll make a few changes to make it persistent.


"sudo modprobe bcma" runs without any output or errors.
```

miguel@miguel-MacBookPro:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

miguel@miguel-MacBookPro:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

```

So, it seems something more needs to be done,

best,
Miguel

---

### Post by chili555 on 2013-04-04
Before we give up on *bcma* forever, let's see if there is any message in the log:```
dmesg | grep -e bcma -e b43
```

---

### Post by miguelnegrao on 2013-04-04
```

miguel@miguel-MacBookPro:~$ dmesg | grep -e bcma -e b43
[  114.137785] bcma: bus0: Found chip with id 0x4331, rev 0x02 and package 0x09
[  114.137824] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x25, class 0x0)
[  114.137849] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x1D, class 0x0)
[  114.137893] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x13, class 0x0)
[  114.149093] bcma: bus0: Bus registered

```

Btw, I wonder why the wireless driver was working fine with the generic kernel but doesn't work on the lowlatency kernel ?

best,
Miguel

---

### Post by chili555 on 2013-04-04
I'm not at all convinced that lowlatency is a factor. Let's try the other method. Please get a temporary ethernet connection and do:```
sudo modprobe -r bcma
sudo apt-get install linux-headers-generic
sudo apt-get install linux-headers-`uname -r`
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Is it working now?

---

### Post by miguelnegrao on 2013-04-05
> **chili555 said:**
> Is it working now?

Ok, I tried that without success: 
```

miguel@miguel-MacBookPro:/var/cache/apt/archives/partial$ sudo modprobe
-r bcma
miguel@miguel-MacBookPro:/var/cache/apt/archives/partial$ sudo apt-get
install linux-headers-generic
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
Os seguintes pacotes extra serão instalados:
 linux-headers-3.8.0-16 linux-headers-3.8.0-16-generic
Serão instalados os seguintes NOVOS pacotes:
 linux-headers-3.8.0-16 linux-headers-3.8.0-16-generic
Serão actualizados os seguintes pacotes:
 linux-headers-generic
1 pacotes actualizados, 2 pacotes novos instalados, 0 a remover e 2 não
actualizados.
É necessário obter 13.2 MB de arquivos.
Após esta operação, serão utilizados 72.0 MB adicionais de espaço em
disco.
Deseja continuar [Y/n]? y
Obter:1 http://gb.archive.ubuntu.com/ubuntu/ raring/main
linux-headers-3.8.0-16 all 3.8.0-16.26 [12.2 MB]
Obter:2 http://gb.archive.ubuntu.com/ubuntu/ raring/main
linux-headers-3.8.0-16-generic amd64 3.8.0-16.26 [998 kB]
Obter:3 http://gb.archive.ubuntu.com/ubuntu/ raring/main
linux-headers-generic amd64 3.8.0.16.31 [2,354 B]
Obtidos 13.2 MB em 2s (6,097 kB/s)                 
A seleccionar pacote anteriormente não seleccionado
linux-headers-3.8.0-16.
(A ler a base de dados ... 212986 ficheiros e directórios actualmente
instalados.)
A descompactar linux-headers-3.8.0-16
(desde .../linux-headers-3.8.0-16_3.8.0-16.26_all.deb) ...
A seleccionar pacote anteriormente não seleccionado
linux-headers-3.8.0-16-generic.
A descompactar linux-headers-3.8.0-16-generic
(desde .../linux-headers-3.8.0-16-generic_3.8.0-16.26_amd64.deb) ...
A preparar para substituir linux-headers-generic 3.8.0.15.30 (a
usar .../linux-headers-generic_3.8.0.16.31_amd64.deb) ...
A descompactar substituto linux-headers-generic ...
A instalar linux-headers-3.8.0-16 (3.8.0-16.26) ...
A instalar linux-headers-3.8.0-16-generic (3.8.0-16.26) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
3.8.0-16-generic /boot/vmlinuz-3.8.0-16-generic
A instalar linux-headers-generic (3.8.0.16.31) ...
miguel@miguel-MacBookPro:/var/cache/apt/archives/partial$ sudo apt-get
install --reinstall bcmwl-kernel-source
A ler as listas de pacotes... Pronto
A construir árvore de dependências       
A ler a informação de estado... Pronto
0 pacotes actualizados, 0 pacotes novos instalados, 1 reinstalados, 0 a
remover e 2 não actualizados.
É necessário obter 1,346 kB de arquivos.
Após esta operação, serão utilizados 0 B adicionais de espaço em disco.
Obter:1 http://gb.archive.ubuntu.com/ubuntu/ raring/restricted
bcmwl-kernel-source amd64 6.20.155.1+bdcom-0ubuntu6 [1,346 kB]
Obtidos 1,346 kB em 0s (2,520 kB/s)           
(A ler a base de dados ... 236646 ficheiros e directórios actualmente
instalados.)
A preparar para substituir bcmwl-kernel-source 6.20.155.1+bdcom-0ubuntu6
(a usar .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu6_amd64.deb) ...
Removing all DKMS Modules
Done.
A descompactar substituto bcmwl-kernel-source ...
A instalar bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu6) ...
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
Building for 3.8.0-14-lowlatency and 3.8.0-15-generic
Building for architecture x86_64
Building initial module for 3.8.0-14-lowlatency
Error! Bad return status for module build on kernel: 3.8.0-14-lowlatency
(x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more
information.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
A processar 'triggers' para initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-15-generic
miguel@miguel-MacBookPro:/var/cache/apt/archives/partial$ sudo modprobe
wl
FATAL: Module wl not found.

```

But then I tried again "sudo modprobe b43" and the wireless started working for some misterious reason. I have no idea what caused that, had done before 
```

sudo apt-get update
 sudo apt-get upgrade
sudo apt-get install --reinstall linux-firmware-nonfree

```
might be related.

The wireless was not starting automatically on boot so I then I added "b43" to the end of the file '/etc/modules' and now the wireless works on boot. 

Thank you very much for the help, in any case !!

best,
Miguel Negrão

ps:How do I set this thread to solved ?

---

### Post by slickymaster on 2013-04-05
Boas, Miguel.

Vê na minha assinatura como marcar as threads como SOLVED. Basta clicares no link e és redireccionado para um breve tutorial de como o fazer.

---

