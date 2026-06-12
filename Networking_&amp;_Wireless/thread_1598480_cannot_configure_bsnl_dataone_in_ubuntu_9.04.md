---
title: "cannot configure bsnl dataone in ubuntu 9.04"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by ch_suresh on 2010-10-16
i have tried several methods to connect to internet but nothing has worked .........can anyone help me 

details 

ifconfig

eth0      Link encap:Ethernet  
HWaddr 00:04:61:5e:ab:9c
         
 UP BROADCAST MULTICAST  MTU:1500  Metric:1
 
         RX packets:0 errors:0 dropped:0 overruns:0 
frame:0
         
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
   
       collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
        Interrupt:22 Base address:0xa000 

lo    
    Link encap:Local Loopback  
     
     inet addr:127.0.0.1 
 Mask:255.0.0.0
      
    inet6 addr: ::1/128 Scope:Host
      
    UP LOOPBACK RUNNING  MTU:16436  Metric:1
 
         RX packets:4 errors:0 dropped:0 overruns:0 frame:0
     
     TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
        collisions:0 txqueuelen:0 
    
      RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by dineshs on 2010-10-17
please try this
Right-click on the NM icon(on top right of the panel) and then click on Edit Connections. 
Select the tab, wired 
select the ethernet connection  and click edit
select ipv4 
method-manual 
address 192.168.1.200
mask 255.255.255.0 
gateway 192.168.1.1
then [COLOR="Red"]hit enter [/COLOR]
give DNS as  [COLOR="Blue"]4.2.2.1[/COLOR]
(You can use any working  DNS)
then click apply
See if the connection is working after a restart.If not post the results of```
sudo lshw -C network
```
by the way what is the model name of your modem.How do you connect in windows?Do you have a PPPoE dialler

---

### Post by ch_suresh on 2010-10-18
thanx 4 ur reply .......i have tried it .but still it is not working 
the output for 
sudo lshw -C network

*-network           
    
       description: Ethernet interface
 
      product: nForce2 Ethernet Controller
    
   vendor: nVidia Corporation
   
    physical id: 4
    
   bus info: pci@0000:00:04.0
    
   logical name: eth0
      
 version: a1
       
serial: 00:04:61:5e:ab:9c
 
      capacity: 100MB/s
   
    width: 32 bits
       
clock: 66MHz
     
  capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       
configuration: autonegotiation=on broadcast=yes driver=forcedeth 
driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
 
 *-network DISABLED
       
description: Ethernet interface
   
    physical id: 1
      
 logical name: pan0
    
   serial: a2:93:f2:6c:14:37
      
 capabilities: ethernet physical
     
  configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes.



my modem model
**[*UT-300R2U* ADSL *MODEM -*]("http://www.google.co.in/url?sa=t&source=web&cd=2&ved=0CBkQFjAB&url=http%3A%2F%2Fwww.calcutta.bsnl.co.in%2Fdataoneinstall%2Fmdm04.html&rct=j&q=bsnl%20modem%20model%20ut300r2u&ei=72W8TO7ZC8mecPbK0eUM&usg=AFQjCNFB6Qzba5CCRy_PcBKEHC1K71OS1g&cad=rja")**


connectivity : usb

i will use a pppoe dialler to connect to internet in windows xp

---

### Post by dineshs on 2010-10-19
> connectivity : usbYour modem has ethernet port.Why dont you connect via ethernet port and post the output of```
 ifconfig -a
```?
> i will use a pppoe dialler to connect to internet in windows xp After connecting modem via ethernet try [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")

---

### Post by ch_suresh on 2010-10-19
i dont know how to connect my usb modem to ethernet port ................
i'll try ur method if possible . if u know any other method please let me know .
thanx for ur reply .

---

### Post by dineshs on 2010-10-19
> i dont know how to connect my usb modem to ethernet port
UT300R2U modem has ethernet port.use an ethernet cable to connect it to your PC

---

