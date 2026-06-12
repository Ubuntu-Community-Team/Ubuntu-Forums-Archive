---
title: "How can I configure dynamic IP address?"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by Tapas Bose, India on 2009-11-28
Hallo everybody.
Can anyone please tell me how to configure dynamic IP address in Karmic. At present my ISP, Tata Indicom Broadband, is providing static IP. I can configure it easily. In Network Connection (System->Preference) I goto Wired tab, then edit, check connect automatically option, and then I goto  IPv4 settings, choose method Manual then add my IP address, netmask address, gateway address, and DNS address and lastly I reboot my DSL router. That is the way of configuring my network. But for some reason I am going to change my current ISP, Airtel Broadband. But Airtel provide dynamic IP address. So I want to know how can I configure my network connection for dynamic IP?
Please help me...

---

### Post by Yoann Juet on 2009-11-28
Just select DHCP instead of static IP configuration.

---

### Post by Tapas Bose, India on 2009-11-28
> **Yoann Juet said:**
> Just select DHCP instead of static IP configuration.
There is no static IP configuration. The options are
1. Automatic (DHCP)
2. Automatic (DHCP) addresss only
3. Manual
4. Link-Local Only
5. Shared to others computers
If I choose Automatic (DHCP) then there is box "DHCP client ID".
If I choose Automatic (DHCP) addresss only then there are there boxes "DNS servers", "Search domain", "DHCP client ID". 
I know DNS address. But what is "DHCP client ID" and "Search domain"?

---

### Post by joshajames on 2009-11-28
Go for automatic.  In most cases DHCP Client ID is not required.

---

### Post by Tapas Bose, India on 2009-11-28
> **joshajames said:**
> Go for automatic.  In most cases DHCP Client ID is not required.
Autometic means Automatic (DHCP) or Automatic (DHCP) addresss only?

---

### Post by zey on 2009-11-28
> **Tapas Bose, India said:**
> There is no static IP configuration. The options are
1. Automatic (DHCP)
2. Automatic (DHCP) addresss only
3. Manual
4. Link-Local Only
5. Shared to others computers
If I choose Automatic (DHCP) then there is box "DHCP client ID".
If I choose Automatic (DHCP) addresss only then there are there boxes "DNS servers", "Search domain", "DHCP client ID". 
I know DNS address. But what is "DHCP client ID" and "Search domain"?


just choose Automatic (DHCP) -> number 1.
and you don't need to fill "DHCP client I", just let it empty.

---

### Post by Tapas Bose, India on 2009-11-28
Thank you very much zey.

---

### Post by xx58 on 2009-11-28
:rolleyes:I have problems to configure dynamic IP Address in Karmic.
I add Address 192.168.1.110
        Netmask 255.255.255.0
       Gateway 192.168.1.1
and  DNS Address 81.21.240.1
when I click applay, then Gateway 192.168.1.1 turn 0.0.0.0 and Web Browser Firefox don't 
open web pages.
Do anybody can give advice?

---

### Post by Iowan on 2009-11-28
Address looks more like a static definition. Is it defined in Network Manager?

---

### Post by Tapas Bose, India on 2009-11-28
> **xx58 said:**
> :rolleyes:I have problems to configure dynamic IP Address in Karmic.
I add Address 192.168.1.110
        Netmask 255.255.255.0
       Gateway 192.168.1.1
and  DNS Address 81.21.240.1
when I click applay, then Gateway 192.168.1.1 turn 0.0.0.0 and Web Browser Firefox don't 
open web pages.
Do anybody can give advice?
I have similar configuration like xx58. i.e.,
IP: 192.XXX.X.X
Netmask: 255.XXX.XXX.0
Gateway: 192.XXX.X.X
DNS: 202.XX.X.X
And I know very well that my IP is static IP. I have to provide these information in System->Preference->Network Connection. Are you sure that you have static IP? If you want then you may contact your ISP to know the nature of your IP, i.e, static or dynamic...

---

### Post by xx58 on 2009-11-29
:rolleyes:Mine is [COLOR=Red]Static[/COLOR]

---

### Post by Tapas Bose, India on 2009-11-29
> **xx58 said:**
> :rolleyes:Mine is [COLOR=Red]Static[/COLOR]
As far as I know the static IP configuration can be done in previously mentioned way.

---

### Post by Arunodaya on 2011-07-06
Try using like wise :
 
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
 
I guess you would not require DNS entry to be made. hope this works.

---

