---
title: "WPA  Supplicant and Network Manager"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by jsym12 on 2009-02-12
Hi-
I am (very) new to Ubuntu. I have an XPS1330 with a dual boot of windows and Ubuntu 8.1 it has a broadband wireless (i don't know which one) . Everything works fantastically well  except for connecting to my University's restricted wireless.

I think in theory, this should be easy. The instructions online are:

# Download the certificate file. You can even connect to the guest.utexas.edu wireless network and get it without logging on.

    *
      [https://management.pna.utexas.edu/static/faqs/dot1x/cacerts.pem](https://management.pna.utexas.edu/static/faqs/dot1x/cacerts.pem) 

# Left click on your network manager icon and select the restricted.utexas.edu wireless network.
#

Fill in the WPA Enterprise information required and leave the other boxes blank (see screenshot).

    * EAP Method: TTLS
    * Key Type: TKIP
    * Identity: YourUTEID
    * Password: ******** (Your UTEID Password)
    * CA Certificate File: cacerts.pem (the file you downloaded) 

# Click Connect. You're done! 
(taken from here: [https://wiki.kubuntu.org/AustinTeam/](https://wiki.kubuntu.org/AustinTeam/)) 


The problem with this is that in my version of network manager, there is no place to specify the key type, and I think this is causing an issue because if I set it up as above, my computer freezes.  My input is the following:
Security: WPA &WPA2 Enterprise
Authentication: Tunneled TLS
CACertificate: cacerts.pem
InnerAuthentication: MSCHAPv2
UserName : myidentity
Password : mypassword

The entire screen looks different, so I think that maybe this advice is outdated.

The other option is to manually configure wpa supplicant. My old laptop (which I am writing this one) uses scientific linux 5 and this manual method works fine here. "Old" computer has an atheros wireless card.

SO
changing the wireless driver from "madwifi" to "wext", i copied the configuration files from my old computer and into my new computer and perform the command


sudo wpa_supplicant -Dwext -ieth1 -c/etc/wpa/config

The output of which is something like:

ioctl[SIOCGIWSCAN]:Resource temporarily unavailable


and then it freezes.

config (the same on both computers):

network={
        ssid="restricted.utexas.edu"
        key_mgmt=WPA-EAP
        eap=TTLS
        ca_cert="/etc/wpa/certs/cacerts.pem"
 subject_match="CN=restricted.utexas.edu"
        anonymous_identity="anonymous"
        identity="myidentity"
        password="mypassword"
        phase2="auth=MSCHAPV2"
}

I think this ioctl has something to do with a bad driver?  I dont really want to fool around with ndiswrapper - which i was doing when I was trying to install scientific linux onto the new computer. Is there a way I can get this to work or should I give up and use ndiswrapper??

---

### Post by Reiger on 2009-02-12
As far as I have seen ioctl is involved in the interaction between kernel (the Linux bit in Ubuntu) and the driver itself. What you see here is an error message from that 'thing' which says it could not do what it is supposed to do because <error message>.

Anyways, you may find wicd very useful because it *does* have the GUI bells and whistles for certificate-based authentication.

---

### Post by jsym12 on 2009-02-13
Thank you!! that worked, though I had to make a modified template based on "PEAP with TKIP" (fyi)

---

### Post by aviator79 on 2009-02-20
Can you be specific about how you set up your template? I'm also trying to get connected to the UT restricted network.

edit: more info: I have a similar problem. Using network manager or manually configuring wpa_supplicant causes my system to freeze. Unfortunately, so does using wicd the way I've configured my template, so I'd be interested to know what you did that got it working.

---

### Post by anachronist on 2009-09-10
I was able to get wicd working with the UT restricted network using this template:

name = TTLS - TKIP
version = 1
require identity *Identity password *Password ca_cert *Path_to_CA_Cert
-----
ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="$_ESSID"
        scan_ssid=$_SCAN
        proto=WPA
        key_mgmt=WPA-EAP
        pairwise=TKIP
        group=TKIP
        eap=TTLS
        identity="$_IDENTITY"
        password="$_PASSWORD"
        ca_cert="$_CA_CERT"
        phase2="auth=MSCHAPV2"
}

The problem is that KNetworkManager (which I would prefer to use) doesn't have the option to set the key type and restricted.utexas.edu requires either TKIP or AES keys. This template allows it, thankfully.

---

