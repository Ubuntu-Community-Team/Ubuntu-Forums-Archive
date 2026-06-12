---
title: "WPA Supplicant and PEAP with certificates"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by johneckert on 2012-12-16
Hello,

I am running a WPA2 network, it worked well with WPA2 - PEAP / MSHAPv2 and a FreeRADIUS Server, with my Debian client.

But I now need to authenticate the users with their certificates in the PEAP tunnel (instead of the login/password with MSCHAPv2)

But I can't get it working. With the IHM I can't put my client certificate when I choose PEAP...so I am trying to configure things manually with WPA_supplicant

Here is my /etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
     wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf


And my /etc/wpa_supplicant/wpa_supplicant.conf file:

network={
	     ssid="MYSSID"
	     #scan_ssid=1 (my SSID is broadcasted)
	     key_mgmt=WPA-EAP
	     eap=PEAP
	     identity="user@example.com"
	     ca_cert="/etc/cert/myca.pem"
             client_cert2="/etc/cert/myclient.pem"
	     private_key_2="/etc/cert/myclient.key"
             private_key_2_passwd="mypassword"
             phase1="peaplabel=0"
	     #phase2="auth=MSCHAPV2"
     }

When I launch /etc/init.d/networking restart, I get:
"Reconfiguring network interfaces...RTNETLINK answers: No such process RTNETLINK answers: No such process
wpa_supplicant: /sbin/wpa_daemon failed to start
run_parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1 done."

And my RADIUS server doesn't see anything coming (debug mode)...

So my question is: Will PEAP with client certificates work, and how should I configure it with wpa_supplicant?
Is there anything in the "phase2" parameter to say that I want to use certificates?

Thank you for reading my problem ! If anyone can give me some information so that this can finally work that would be fine.

J.

---

