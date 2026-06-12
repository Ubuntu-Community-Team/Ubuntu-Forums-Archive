---
title: "Problems Connecting to the Internet (ADSL Ethernet)"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by Eudoxia on 2009-08-22
[First, I'll appreciate every tip you can provide. This is probably an error caused by n00bish first time users. Second, I don't know much about hardware, specially modems and routers :( ]

I installed Ubuntu Linux, 9.04 through WUBI yesterday.  I logged in with my account, while the wire from the computer to the modem was connected and the lights flashing. 

However, the internet connection was down.  I tried rebooting and shutting down the modem, then switching it on again.  In the connections, I have eth0. I try to connect. Nope, it tells me i'm disconnected.  

I tried the docs, the man pages, and all of that.  Also, I typed:  

> sudo pppoeconf  

Yes, I got the menu. I copied the file to y /root (In the process, I learned how to get root privileges. Go me), and proceeded.  Nope.

 I used
 > sudo pon dsl-provider  
But that simply prompted the file and the last compilation date.  Finally, when using 

> plog

, between the sevral lines on the Terminal, it prompted:

>  PAP identification failed  

Ideas?

Thanks in advance,

~~Eudoxia

---

### Post by Charly85551 on 2009-08-24
Before you try to manipulate any software you need to be sure about your hardware. Is your ADSL-connection via a router (which is normally with DHCP- and Firewall-Server and pretty straight forward to program) or are you talking about a naked ADSL-modem.
Second you need to know the setup of your computer's ethernet interface. With Ubuntu 9.04 your interface is expecting DHCP and all the information related to gateway, DNS and subnet is coming from the DHCP server inside the router.:confused:
May be you could give us some more details on your ADSL-hardware! May be you are lucky and have already a router.[IMG]http://ubuntuforums.org/images/icons/icon11.gif[/IMG]
cheers

---

### Post by superprash2003 on 2009-08-24
also post output of **ifconfig** from the terminal

---

### Post by Eudoxia on 2009-08-27
Output of ifconfig -a (Ubuntu, duh) and ipconfig -all (WindowsXP-SP2)


[NOTE: MS-DOS here is in spanish, so i translated the names of stuff. It should be quit eaccurate]

[NOTE 2: IP addresses censored]

Windows IP Configuration



        Nombre del host / Host Name. . . . . . . . . : usuario-7732293

        Sufijo DNS principal  / Main DNS Suffix (?). . . . . . : 

        Tipo de nodo / Node Type. . . . . . . . . .  : desconocido / unknown

        Enrutamiento habilitado / Routing Enabled. . . . . .: No

        Proxy WINS habilitado / WINS Proxy. . . . .    : No



Adaptador Ethernet Conexión de área local / Ethernet Adapter Local Area Connection          :



        Sufijo de conexión específica DNS / Specific DNS Connection Suffix : 

        Descripción / Description. . . . . . . . . . .  : Adaptador Fast Ethernet compatible VIA / Fast Ethernet Adapter compatible VIA

        Dirección física /MAC Address. . . . . . . . . : 00-13-8F-81-0D-F4

        DHCP habilitado / DHCP Enabled. . . . . . . . .  : No

        Autoconfiguración habilitada / Autoconfig enabled. . . : Sí / Yes

        Dirección IP de autoconfiguración / Auto config IP Address : XXX.XXX.XXX.XXX

        Máscara de subred / Subnet Mask . . . . . . . . : XXX.XXX.X.X

        Puerta de enlace predeterminada   : 



Adaptador PPP adsl 2 / PPP ADSL 2 Adapter              :



        Sufijo de conexión específica DNS / Specific DNS Connection Suffix : 

        Descripción / Description. . . . . . . . . . .  : WAN (PPP/SLIP) Interface

        Dirección física / MAC Address. . . . . . . . . : 00-53-45-00-00-00

        DHCP habilitado / DHCP Enabled. . . . . . . . .  : No

        Dirección IP / IP Address . . . . . . . . . . . : XXX.XXX.XXX.XX

        Máscara de subred / Subnet Mask. . . . . . . . : XXX.XXX.XXX.XXX

        Puerta de enlace predeterminada / Pre-determined Gateway (?)   : 190.135.142.56

        Servidores DNS / DNS servers. . . . . . . . . .: XXX.XX.XXX.XXX

                                            XXX.XX.XXX.XXX

        NetBios sobre TCPIP / NetBIOS over TCP-IP. . . . . . .  : Deshabilitado / No

        
        
        
        
Results of IFCONFIG -A

sysadmin@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  direcciónHW 00:13:8f:81:0d:f4  
          dirección inet6: fe80::213:8fff:fe81:df4/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:4800 (4.8 KB)  TX bytes:3610 (3.6 KB)
          Interrupción:23 Dirección base: 0x4c00 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

pan0      Link encap:Ethernet  direcciónHW 4e:76:97:3c:ec:14  
          DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

sysadmin@ubuntu:~$ 



sysadmin@ubuntu:~$ plog
Aug 27 11:34:09 ubuntu pppd[2063]: Connection terminated.
Aug 27 11:34:40 ubuntu pppd[2063]: PPP session is 6934
Aug 27 11:34:40 ubuntu pppd[2063]: Connected to 00:30:88:10:e5:e0 via interface eth0
Aug 27 11:34:40 ubuntu pppd[2063]: Using interface ppp0
Aug 27 11:34:40 ubuntu pppd[2063]: Connect: ppp0 <--> eth0
Aug 27 11:34:40 ubuntu pppd[2063]: PAP authentication failed [<<< THIS IS IMPORTANT---]
Aug 27 11:34:40 ubuntu pppd[2063]: Connection terminated.
Aug 27 11:34:40 ubuntu pppd[2063]: Exit.
sysadmin@ubuntu:~$

---

### Post by Eudoxia on 2009-08-28
Also, here is a crappy diagram of my internet connection:

[EDIT: error]

[EDIT2: nevamind]

[IMG]http://i26.tinypic.com/2vcu69s.png[/IMG]

---

### Post by Eudoxia on 2009-08-29
Note 1: Running sudo ppoeconf deletes the Auto eth0 connection after rebooting.

When it asks you for your username, is it:

username

OR:

username@adsl04

???

Note 2: When I try to set up a connection, and type in the MAC address (Or fill in any other variable) the "Apply" button goes inactive. :confused:

My Ethernet card is:

Fast Ethernet Adapter VIA Compatible

Can I connect to the internet in Linux with this? Or do I need a special driver?

---

### Post by Eudoxia on 2009-08-30
Possibilities:

1 - Ethernet card not supported

2 - Driver missing

3 - DNS cache blew up

4 - Auto config issues

---

### Post by Eudoxia on 2009-09-02
sysadmin@ubuntu:~$ lshw
WARNING: you should run this program as super-user.
ubuntu                    
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 511MiB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.40GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc up pebs bts pni dtes64 monitor ds_cpl cid xtpr
          configuration: id=0
     *-pci:0
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: driver=agpgart-via latency=8 module=via_agp
        *-pci
             description: PCI bridge
             product: VT8237/VX700 PCI Bridge
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV44A [GeForce 6200]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 maxlatency=1 mingnt=5
        *-storage
             description: RAID bus controller
             product: VIA VT6420 SATA RAID Controller
             vendor: VIA Technologies, Inc.
             physical id: f
             bus info: pci@0000:00:0f.0
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: storage bus_master cap_list
             configuration: driver=sata_via latency=32
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: f.1
             bus info: pci@0000:00:0f.1
             version: 06
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=pata_via latency=32
        *-usb:0
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10
             bus info: pci@0000:00:10.0
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.1
             bus info: pci@0000:00:10.1
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.2
             bus info: pci@0000:00:10.2
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:3
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 10.3
             bus info: pci@0000:00:10.3
             version: 81
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=uhci_hcd latency=32 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: USB 2.0
             vendor: VIA Technologies, Inc.
             physical id: 10.4
             bus info: pci@0000:00:10.4
             version: 86
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ehci_hcd latency=32 module=ehci_hcd
        *-isa
             description: ISA bridge
             product: VT8237 ISA bridge [KT600/K8T800/K8T890 South]
             vendor: VIA Technologies, Inc.
             physical id: 11
             bus info: pci@0000:00:11.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-multimedia
             description: Multimedia audio controller
             product: VT8233/A/8235/8237 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.5
             bus info: pci@0000:00:11.5
             version: 60
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Audio latency=0 module=snd_via82xx
        *-communication
             description: Communication controller
             product: AC'97 Modem Controller
             vendor: VIA Technologies, Inc.
             physical id: 11.6
             bus info: pci@0000:00:11.6
             version: 80
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=VIA 82xx Modem latency=0 module=snd_via82xx_modem
        *-network
             description: Ethernet interface
             product: VT6102 [Rhine-II]
             vendor: VIA Technologies, Inc.
             physical id: 12
             bus info: pci@0000:00:12.0
             logical name: eth0
             version: 78
             serial: 00:13:8f:81:0d:f4
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical
             configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
     *-pci:1
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 101
          bus info: pci@0000:00:00.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 102
          bus info: pci@0000:00:00.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: PT890 Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 103
          bus info: pci@0000:00:00.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 104
          bus info: pci@0000:00:00.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: CN700/VN800/P4M800CE/Pro Host Bridge
          vendor: VIA Technologies, Inc.
          physical id: 105
          bus info: pci@0000:00:00.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:a6:20:22:39:0a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
sysadmin@ubuntu:~$ 



[All the info I could get]

---

### Post by Eudoxia on 2009-09-03
Problem solved

---

### Post by Nuller on 2010-07-29
how did you solve this? i have same problem? 
thanks

---

