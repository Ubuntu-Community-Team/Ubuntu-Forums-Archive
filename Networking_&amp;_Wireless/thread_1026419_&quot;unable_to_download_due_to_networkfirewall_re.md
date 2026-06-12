---
title: "&quot;unable to download due to network/firewall restrictions&quot;"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Arunomi on 2008-12-31
Hi I got this wheather Station for x-mas.
And it gets its information form internet.

But for that i got to install a program on my comp and is a windows
program so im trying to get it to work in wine.

But the problem is that the install program wants to downloade stuff from internet and i cant..

I just gets this error message "unable to download the .exe file for installation due to network/firewall restrictions".

The wheather station is a Ventus V203 and my gateway is at Thomson tg787.

Is there any one that can help me?

---

### Post by oygle on 2008-12-31
Look in your syslog, it will tell you what port is being blocked.

---

### Post by Arunomi on 2008-12-31
```
Dec 31 13:07:38 arunomi-desktop dhclient: DHCPREQUEST of <null address> on eth2 to 192.168.1.254 port 67
Dec 31 13:07:38 arunomi-desktop dhclient: DHCPACK of 192.168.1.66 from 192.168.1.254
Dec 31 13:07:38 arunomi-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth2 
Dec 31 13:07:38 arunomi-desktop dhclient: bound to 192.168.1.66 -- renewal in 539 seconds.
```

This is what i get.

Is it port 67 on my gateway or may comp thats looked?

---

### Post by oygle on 2008-12-31
Doesn't seem to be an error though. Can you try the download/install under WINE, and then see in syslog ?

Here is a syslog entry from my computer, where a port is being blocked by firewall 

> Dec 31 23:06:06 ******** kernel: [10455.544259] Inbound IN=ppp0 OUT= MAC= SRC=86.134.147.123 DST=220.***.***.*** LEN=48 TOS=0x00 PREC=0x00 TTL=99 ID=41794 DF PROTO=TCP SPT=4415 DPT=139 WINDOW=64240 RES=0x00 SYN URGP=0 

I'm using a ppp0 connection, and the port in the logs is 139

Oygle

---

### Post by Arunomi on 2008-12-31
But its a windows program, and im runing it under wine?

---

### Post by oygle on 2008-12-31
> **Arunomi said:**
> But its a windows program, and im runing it under wine?

You are still running WINE under Ubuntu, so because of this ..

> But the problem is that the install program wants to downloade stuff from internet and i cant..


then, try the install program under WINE, and then check syslog

Oygle

---

### Post by Arunomi on 2008-12-31
This is what i get if run it thru wine in the terminal.


```
arunomi@arunomi-desktop:/media/cdrom0:$ wine install_1940.exe
fixme:wininet:InternetSetFilePointer stub
fixme:wininet:InternetSetFilePointer stub
fixme:wininet:InternetSetFilePointer stub
fixme:wininet:InternetSetFilePointer stub
wine: Unhandled page fault on write access to 0x00005600 at address 0x5649a9 (thread 0019), starting debugger...
Unhandled exception: page fault on write access to 0x00005600 in 32-bit code (0x005649a9).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:005649a9 ESP:7df948a8 EBP:7df99ea8 EFLAGS:00010206(   - 00      - RIP1)
 EAX:00005600 EBX:7df9a978 ECX:005649a0 EDX:005600c8
 ESI:00000000 EDI:7df9a9a0
Stack dump:
0x7df948a8:  00000000 00000000 00000000 00000000
0x7df948b8:  00000000 00000000 00000000 00000000
0x7df948c8:  00000000 00000000 00000000 00000000
0x7df948d8:  00000000 00000000 7e758014 00000000
0x7df948e8:  7df951d0 00000000 00000000 00000110
0x7df948f8:  7e759ff4 00000000 0000000a 7df94d40
Backtrace:
=>1 0x005649a9 (0x7df99ea8)
  2 0x00402a33 in install_1940 (+0x2a33) (0x7df9a984)
  3 0x0041c18b in install_1940 (+0x1c18b) (0x7df9aa04)
  4 0x0040df5d in install_1940 (+0xdf5d) (0x7df9aa38)
  5 0x7bc6dbee call_thread_entry_point+0xe() in ntdll (0x7df9aa48)
  6 0x7bc6e2c2 in ntdll (+0x5e2c2) (0x7df9aae8)
  7 0x7bc6e4f2 in ntdll (+0x5e4f2) (0x7df9b3d8)
  8 0xb7e064fb start_thread+0xcb() in libpthread.so.0 (0x7df9b4c8)
0x005649a9: addb	%al,0x0(%eax)
Modules:
Module	Address			Debug info	Name (89 modules)
PE	  400000-  447000	Export          install_1940
ELF	7b800000-7b93c000	Deferred        kernel32<elf>
  \-PE	7b820000-7b93c000	\               kernel32
ELF	7bc00000-7bca9000	Export          ntdll<elf>
  \-PE	7bc10000-7bca9000	\               ntdll
ELF	7bf00000-7bf03000	Deferred        <wine-loader>
ELF	7de70000-7de7b000	Deferred        libgcc_s.so.1
ELF	7dfe0000-7dfe4000	Deferred        libgpg-error.so.0
ELF	7dfe4000-7e031000	Deferred        libgcrypt.so.11
ELF	7e031000-7e041000	Deferred        libtasn1.so.3
ELF	7e041000-7e044000	Deferred        libkeyutils.so.1
ELF	7e044000-7e04c000	Deferred        libkrb5support.so.0
ELF	7e04c000-7e07e000	Deferred        libcrypt.so.1
ELF	7e07e000-7e0f4000	Deferred        libgnutls.so.13
ELF	7e0f4000-7e117000	Deferred        libk5crypto.so.3
ELF	7e117000-7e1a4000	Deferred        libkrb5.so.3
ELF	7e1a4000-7e1cd000	Deferred        libgssapi_krb5.so.2
ELF	7e1cd000-7e200000	Deferred        libcups.so.2
ELF	7e206000-7e20c000	Deferred        libnss_dns.so.2
ELF	7e20c000-7e20f000	Deferred        libnss_mdns4_minimal.so.2
ELF	7e25c000-7e28f000	Deferred        uxtheme<elf>
  \-PE	7e260000-7e28f000	\               uxtheme
ELF	7e28f000-7e298000	Deferred        libxcursor.so.1
ELF	7e298000-7e29d000	Deferred        libxfixes.so.3
ELF	7e29d000-7e2a0000	Deferred        libxcomposite.so.1
ELF	7e2a0000-7e2a6000	Deferred        libxrandr.so.2
ELF	7e2a6000-7e2ae000	Deferred        libxrender.so.1
ELF	7e2ae000-7e2b3000	Deferred        libxxf86vm.so.1
ELF	7e2b3000-7e2b6000	Deferred        libxinerama.so.1
ELF	7e2b6000-7e2d6000	Deferred        imm32<elf>
  \-PE	7e2c0000-7e2d6000	\               imm32
ELF	7e2d6000-7e2db000	Deferred        libxdmcp.so.6
ELF	7e2db000-7e2f3000	Deferred        libxcb.so.1
ELF	7e2f3000-7e2f5000	Deferred        libxcb-xlib.so.0
ELF	7e2f5000-7e2f8000	Deferred        libxau.so.6
ELF	7e2f8000-7e3df000	Deferred        libx11.so.6
ELF	7e3df000-7e3ed000	Deferred        libxext.so.6
ELF	7e3ed000-7e405000	Deferred        libice.so.6
ELF	7e405000-7e40d000	Deferred        libsm.so.6
ELF	7e418000-7e41b000	Deferred        libcom_err.so.2
ELF	7e41d000-7e4b5000	Deferred        winex11<elf>
  \-PE	7e430000-7e4b5000	\               winex11
ELF	7e4ea000-7e50b000	Deferred        libexpat.so.1
ELF	7e50b000-7e535000	Deferred        libfontconfig.so.1
ELF	7e545000-7e55a000	Deferred        libz.so.1
ELF	7e55a000-7e5c7000	Deferred        libfreetype.so.6
ELF	7e5c7000-7e5e9000	Deferred        mpr<elf>
  \-PE	7e5d0000-7e5e9000	\               mpr
ELF	7e5e9000-7e638000	Deferred        wininet<elf>
  \-PE	7e5f0000-7e638000	\               wininet
ELF	7e638000-7e664000	Deferred        ws2_32<elf>
  \-PE	7e640000-7e664000	\               ws2_32
ELF	7e664000-7e74a000	Deferred        oleaut32<elf>
  \-PE	7e680000-7e74a000	\               oleaut32
ELF	7e74a000-7e75d000	Deferred        libresolv.so.2
ELF	7e76d000-7e78c000	Deferred        iphlpapi<elf>
  \-PE	7e770000-7e78c000	\               iphlpapi
ELF	7e78c000-7e7f1000	Deferred        rpcrt4<elf>
  \-PE	7e7a0000-7e7f1000	\               rpcrt4
ELF	7e7f1000-7e8fd000	Deferred        ole32<elf>
  \-PE	7e810000-7e8fd000	\               ole32
ELF	7e8fd000-7e925000	Deferred        oledlg<elf>
  \-PE	7e900000-7e925000	\               oledlg
ELF	7e925000-7e95a000	Deferred        winspool<elf>
  \-PE	7e930000-7e95a000	\               winspool
ELF	7e95a000-7ea1b000	Deferred        comctl32<elf>
  \-PE	7e960000-7ea1b000	\               comctl32
ELF	7ea1b000-7ea76000	Deferred        shlwapi<elf>
  \-PE	7ea30000-7ea76000	\               shlwapi
ELF	7ea76000-7eba0000	Deferred        shell32<elf>
  \-PE	7ea90000-7eba0000	\               shell32
ELF	7eba0000-7ec4c000	Deferred        comdlg32<elf>
  \-PE	7ebb0000-7ec4c000	\               comdlg32
ELF	7ec4c000-7eca0000	Deferred        advapi32<elf>
  \-PE	7ec60000-7eca0000	\               advapi32
ELF	7eca0000-7ed3e000	Deferred        gdi32<elf>
  \-PE	7ecb0000-7ed3e000	\               gdi32
ELF	7ed3e000-7ee88000	Deferred        user32<elf>
  \-PE	7ed60000-7ee88000	\               user32
ELF	7efa8000-7efb3000	Deferred        libnss_files.so.2
ELF	7efb3000-7efcb000	Deferred        libnsl.so.1
ELF	7efcb000-7eff0000	Deferred        libm.so.6
ELF	7eff6000-7f000000	Deferred        libnss_nis.so.2
ELF	b7ca4000-b7cad000	Deferred        libnss_compat.so.2
ELF	b7cae000-b7cb2000	Deferred        libdl.so.2
ELF	b7cb2000-b7e01000	Deferred        libc.so.6
ELF	b7e01000-b7e19000	Export          libpthread.so.0
ELF	b7e29000-b7f5f000	Deferred        libwine.so.1
ELF	b7f61000-b7f7d000	Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\install_1940.exe
	00000019    0 <==
	00000009    0
0000000c 
	00000013    0
	00000012    0
	0000000e    0
	0000000d    0
0000000f 
	00000015    0
	00000014    0
	00000011    0
	00000010    0
00000016 
	00000017    0
Backtrace:
=>1 0x005649a9 (0x7df99ea8)
  2 0x00402a33 in install_1940 (+0x2a33) (0x7df9a984)
  3 0x0041c18b in install_1940 (+0x1c18b) (0x7df9aa04)
  4 0x0040df5d in install_1940 (+0xdf5d) (0x7df9aa38)
  5 0x7bc6dbee call_thread_entry_point+0xe() in ntdll (0x7df9aa48)
  6 0x7bc6e2c2 in ntdll (+0x5e2c2) (0x7df9aae8)
  7 0x7bc6e4f2 in ntdll (+0x5e4f2) (0x7df9b3d8)
  8 0xb7e064fb start_thread+0xcb() in libpthread.so.0 (0x7df9b4c8)

```

And this is what i get in syslog

```
Dec 31 13:24:14 arunomi-desktop dhclient: DHCPREQUEST of <null address> on eth2 to 192.168.1.254 port 67
Dec 31 13:24:14 arunomi-desktop dhclient: DHCPACK of 192.168.1.66 from 192.168.1.254
Dec 31 13:24:14 arunomi-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth2 
Dec 31 13:24:14 arunomi-desktop dhclient: bound to 192.168.1.66 -- renewal in 543 seconds.
```

---

### Post by oygle on 2008-12-31
Looks like a WINE problem to me. However, if you beleive it is firewall, then install 'Firetsrater', and it will tell you if there is a firewall problem.


Hmm, installing from the CD may be causing WINE problems. Try to change paths to where you want it installed, and then install from the CD, something like

> $ wine /media/cdrom0/install_1940.exe


---

### Post by Arunomi on 2008-12-31
How do i log all network traffic?

I tryed firestarter but i works fin and i cant install the program.

I tryed to run it under wine with full path name.

But same problem.

---

### Post by oygle on 2008-12-31
> **Arunomi said:**
> How do i log all network traffic?


If you have Firestarter installed, and it has started, then look under the 'events' tab, to see if there are any network problems

> **Arunomi said:**
> 
I tryed to run it under wine with full path name.

But same problem.

Then, it does sound like a WINE problem. There is a sub-forum here just for WINE problems - see [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

Oygle

---

