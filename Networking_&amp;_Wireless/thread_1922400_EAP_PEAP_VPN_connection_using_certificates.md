---
title: "EAP PEAP VPN connection using certificates"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by PommeVerte on 2012-02-08
Hi everyone,

I've had a look around regarding this but I'm still pretty confused, I wouldn't mind some pointers.

I'm currently trying to connect to a company network via VPN. All I've been given are a couple of certificates. A client and CA respecitvely in ".p12" and ".cer" extentions. A password for the p12 certificate installation was provided as well as instructions on how to get the connection up for windows XP and mac os. Needless to say these aren't much help for ubuntu.
I've been also given a VPN server host as well as another host for server certificate validation. 

I'm guessing I will have to convert these to .pem or such. I can use "openssl pkcs12 ..." for the .p12 but what about the .cer (CA)?

Now as far as the network manager goes I cannot find any way of providing these certificates when configuring a VPN. From reading around my first guess would be to configure wpa_supplicant. But that's where my understanding is limited. I'm not sure I understand the relationship between wpa_supplicant and network manager. Is the conf checked automatically or is wpa_cli used in ubuntu? Thus ignoring the former. Is it checked if the PPTP VPN is configured for MSCHAPSv2/EAP. Etc... It's all still unclear for me.

Anyone have any tips? Is looking into wpa_supplicant the correct direction? Any links/tips/walkthroughs would be greatly appreciated.

Thanks.

---

### Post by PommeVerte on 2012-02-10
anyone have any idea? Certainly someone must know

---

