---
title: "Device problems in Ubuntu 11.04?"
date: 2011-04-03
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Twakso on 2011-04-03
Hello everyone!

I tell what is my problem. I tried Ubuntu 11.04 Beta 1 two days ago, when it was released. I burnt the ISO on a USB through UNetbootin and through LinuxLiveUSB. When I had do it, I boot the PC and I chose the "USBLive". Then, the desktop appeared and I realized I could not access the partitions. So I reboot and while Ubuntu was starting I pressed 'Esc' key and I watch the next one: "can't mount /dev/sr0: no mount found" (although no partition was mounted). In addiction, the same thing happened with the Alpha 3 and I tried install it but all partitions disappeared.

How I can solve it? Or do I have to report as a bug?

*Sorry if my English level is bad. English is not my native language.*

---

### Post by cariboo on 2011-04-03
The error is telling you it can't find anything in you CD/DVD drive. What do you mean you could access the partitions? What is the output of:

```
sudo fdisk -l
```

---

### Post by Twakso on 2011-04-04
The point is I can't access to any partition, and therefore it won't let me install it on the HDD. Maybe, I'm not sure, it also appears that there is an error to recognize the others devices, since I'm not able to go into those.

(Now I haven't time for check these errors.)

Thanks for replying.

---

### Post by cariboo on 2011-04-04
> **Twakso said:**
> The point is I can't access to any partition, and therefore it won't let me install it on the HDD. Maybe, I'm not sure, it also appears that there is an error to recognize the others devices, since I'm not able to go into those.

(Now I haven't time for check these errors.)

Thanks for replying.

So you are saying that when you run:

```
sudo fdisk -l
```

you don't get any output?

---

### Post by Twakso on 2011-04-04
Yes. If I use the command you said, I can see in the Terminal all the partitions that I have. So why can I not access them?

I'm not an expert using the Terminal, but if I write "ubuntu@ubuntu:~$ /dev/sda1", it outputs "bash: /dev/sda1: Permission denied".

Thank you again!

---

### Post by cariboo on 2011-04-04
You have to mount the partitions in order to access them. You shoul;d be able to mount them by opening nautilus and just clicking on what the file manager calls them, or on an empty workspace click Places->Computer in the panel, and double click one of the drive icons.

---

### Post by Twakso on 2011-04-06
But there appears none partition. In fact, when I'm trying install, the installer only recognize 'sda' but don't sda1, sda2, etc. So I cannot install it in the partition I want, since I cannot edit them or do anything.

I don't know if I understood you.

---

### Post by cariboo on 2011-04-06
Can you open a terminal and type:

```
sudo fdisk -l
```

and 

```
df -h
```

and paste the output of both commands in you next post.

---

### Post by Twakso on 2011-04-07
Here are the outputs. (But it's in Spanish.)

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitiendo la partición vacía (5)

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x00015c31

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        6079    48827392    7  HPFS/NTFS
/dev/sda2            6079        8146    16601088   83  Linux
/dev/sda3            8146       19458    90859521    5  Extendida
/dev/sda4           19093       19458     2928640   82  Linux swap / Solaris
/dev/sda5            8146       10578    19529728   83  Linux
/dev/sda6           10578       19092    68393984    b  W95 FAT32

Disco /dev/sdb: 8015 MB, 8015314944 bytes
255 cabezas, 63 sectores/pista, 974 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x01a6a62e

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1         975     7827424+   b  W95 FAT32
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(973, 254, 63) lógicos=(974, 120, 42)

``````
ubuntu@ubuntu:~$ df -h
S.ficheros            Tam.  Usado Disp. % Uso Montado en
aufs                  438M   43M  395M  10% /
none                  431M  660K  430M   1% /dev
/dev/sdb1             7,5G  699M  6,8G  10% /cdrom
/dev/loop0            671M  671M     0 100% /rofs
none                  438M  100K  438M   1% /dev/shm
tmpfs                 438M   20K  438M   1% /tmp
none                  438M   96K  438M   1% /var/run
none                  438M     0  438M   0% /var/lock

```

---

### Post by VMC on 2011-04-07
> **Twakso said:**
> Hello everyone!

... So I reboot and while Ubuntu was starting I pressed 'Esc' key and I watch the next one: "can't mount /dev/sr0: no mount found" (although no partition was mounted). In addiction, the same thing happened with the Alpha 3 and I tried install it but all partitions disappeared.

How I can solve it? Or do I have to report as a bug?

*Sorry if my English level is bad. English is not my native language.*

That sr0 is your cdrom drive. Your booting from usb drive. 
Also, I'm not sure what you mean by pressing 'Esc' key and watching the next one. Does that refer to watching the test messages?

If you click on the install is that when it says no partitions available?

---

### Post by Twakso on 2011-04-07
> **VMC said:**
> That sr0 is your cdrom drive. Your booting from usb drive. 
Also, I'm not sure what you mean by pressing 'Esc' key and watching the next one. Does that refer to watching the test messages?

If you click on the install is that when it says no partitions available?

I refer by that when the loading screen (usplash?) is, then I press ESC. Thus I see that 'sr0 error'.

It's only available sda. sda1, sda2, sda3, etc. don't appears.

Am I clear?

---

