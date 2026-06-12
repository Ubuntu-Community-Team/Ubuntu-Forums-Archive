---
title: "kvpnc vpnclient not found"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by kaizo2560 on 2011-08-19
Hi I have installed kvpnc and loaded my profile using a .pcf file but seems not to be able to connect.

the error I get is:

error:The required daemon (vpnclient) is not available, connect will be disabled.

I tried looking for vpnclient in the repo and over the internet but seems to be unavailable.

Has anyone else has a similar problem?

I use Kubuntu Natty 

thanks in advanced

---

### Post by praseodym on 2011-08-21
Try reinstalling the network-manager with all components:

```
sudo apt-get install --reinstall network-manager plasma-widget-networkmanagement network-manager-vpnc network-manager-vpnc-kde
sudo service network-manager restart
```

---

### Post by kaizo2560 on 2011-08-21
Thank you for your response :)

I've tried it just now but it spits back the same error I've installed vpnc and assumed that will do the job but did not...

How do you get vpnclient?

Again thanks in advance

---

### Post by praseodym on 2011-08-22
Try

```
sudo apt-get install --reinstall network-manager plasma-widget-networkmanagement network-manager-vpnc network-manager-vpnc-kde network-manager-openvpn network-manager-openvpn-kde network-manager-vpnc network-manager-vpnc-kde network-manager-pptp network-manager-pptp-kde
sudo service network-manager restart
```

---

### Post by kaizo2560 on 2011-08-22
Hmm didn't work... I just got the same error

Does the pcf file commute with all platforms?(i.e. for windows and linux)

I got the one for windows and since kvpnc said the profile was made successfully I have dismissed it but do you think that may be the reason?

I mean I know where to put the file now in /usr/local/bin/vpnclient but don't have the file vpnclient 

Do you know where to get this from?

thanks for your help

---

### Post by praseodym on 2011-08-22
You may have a look at [this]("http://translate.google.de/translate?js=n&prev=_t&hl=de&ie=UTF-8&layout=2&eotf=1&sl=de&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2Fkvpnc") translated website. I translated the final part of the site manually by google translator. It reads:

> Finally, save the file. A connection can now be in the terminal [5] using

```
sudo vpnc-connect /etc/vpnc/mops.conf
```

be made&#8203;&#8203;. Separately, the connection is simply using

```
sudo vpnc-disconnect
```

It may happen that happens after you call vpnc nothing for a while and after a few minutes the message "no response from target" appears. Here it may be helpful vpnc with - disable-natt start.
problems

**Import Cisco PCF files**

If profiles do not work from imported PCF files, it can help in the box under "Preferences -> Enable advanced settings> Profiles -> General - -> Advanced" to disable.

If the group password in the PCF file to be stored coded (a long hexadecimal number), so if they manually decipher [http://www.unix-ag.uni-kl.de/](http://www.unix-ag.uni-kl.de/) ~ massar/bin/cisco- {S} and decode transmitted in plain text.

---

### Post by kaizo2560 on 2011-08-22
Hi I tried that but when running:

sudo vpnc-connect /etc/vpnc/mops.conf
the file was not found but vpnc-connect was available as an option so vpnc is definitely there.

As for the pcf file since it manages to create a profile it probably is working.

Any ideas?

Thank you for your help

---

### Post by praseodym on 2011-08-22
"mops.conf" ist just a random name. The name.conf is the name of your vpn connection. Show:

```
cd /etc/vpnc/
ls -l
```

---

### Post by kaizo2560 on 2011-08-22
Hi I tried that and I got:


aaa@bbb:~$ sudo vpnc-connect /etc/vpnc/example.conf
Enter IPSec gateway address: 000.00.000.00
Enter IPSec ID for 000.00.000.00: XXXXX
Enter IPSec secret for XXXXX@000.00.000.00: 
Enter username for 000.00.000.00: [email]xxx@xx.xx[/email]
Enter password for [email]xxx@xx.xx[/email]@000.00.000.00: 
vpnc-connect: no response from target

not sure why it is not responding...

---

