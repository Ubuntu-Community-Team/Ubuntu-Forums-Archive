---
title: "Connecting to eduroam with Ubunty 9.04"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by gbajra on 2009-07-29
I am trying to connect to the eduroam with Ubuntu 9.04. My university have a ubuntu setup but the setup is different in 9.04 and it does not work. Here is the link to the guide:
[http://luchthaven.tudelft.nl/content/manuals/TTLS-Ubuntu7_10.pdf](http://luchthaven.tudelft.nl/content/manuals/TTLS-Ubuntu7_10.pdf)

Has anyone tried eduroam for 9.04. Would appreciate if you can tell me how?

---

### Post by tomBorgia on 2009-09-01
Bit late reply but spent ages getting this to work so glad to share and hope it helps!

I have eduroam working with wicd (as opposed to network manager) - You'll need to install wicd (sudo apt-get install wicd) and create a custom encryption file in /etc/wicd/encryption/templates/ (I called mine eduroam)

```
name = eduroam
author = Tom Borgia  
version = 1
require identity *Identity anonymous_identity *Anonymous_identity password *Password
-----
ctrl_interface=/var/run/wpa_supplicant

eapol_version=1
ap_scan=1
update_config=1

network={
        ssid="eduroam"
        key_mgmt=WPA-EAP
        eap=TTLS
        identity="$_IDENTITY"
        anonymous_identity="$_ANONYMOUS_IDENTITY"
        password="$_PASSWORD"
        ca_cert="/etc/ssl/certs/Equifax_Secure_CA.pem"
        phase2="auth=PAP"
}
```

the ca_cert may be different for your university... and you'll also need to add the line "eduroam" (or whatever you called the file with those details in) to /etc/wicd/templates/active to enable it. Load up the wicd manager, select "use encryption" and you should have eduroam in the drop down box... enter your username and password (anon id is usually anon@your-university-domain) and connect! You'll need to set "use these aettings for all connections with this ssid" so you don't need to set it up each time.

Hope that works.

[Got most of the info above from here!]("http://wicd.sourceforge.net/templates.php")

---

### Post by atom heart on 2009-09-02
Wow 
thank you so much!
followed your instructions and worked perfectly!

btw do you have a link for specifying commands like 
eapol_version=1
ap_scan=1
update_config=1
 
or any tutorial on creating wicd templates?

---

### Post by tomBorgia on 2009-09-02
> **atom heart said:**
> Wow 
thank you so much!
followed your instructions and worked perfectly!

btw do you have a link for specifying commands like 
eapol_version=1
ap_scan=1
update_config=1
 
or any tutorial on creating wicd templates?

[http://wicd.sourceforge.net/templates.php]("http://wicd.sourceforge.net/templates.php")

To be honest can't remember what ap_scan / eapol_version do... have a google!

Tom.

---

### Post by atom heart on 2009-09-02
> **tomBorgia said:**
> [http://wicd.sourceforge.net/templates.php]("http://wicd.sourceforge.net/templates.php")

To be honest can't remember what ap_scan / eapol_version do... have a google!

Tom.

yes I actually read this tut but couldn't match with the options for eduroam!

That's why I'm asking for these declarations

---

### Post by tomBorgia on 2009-09-02
I think -

update_config=1 allows wicd to update wpa_supplicant.conf.

From [http://www.fmepnet.org/debian_wpa.html]("http://www.fmepnet.org/debian_wpa.html") -

> #ap_scan=1
#eapol_version=2

These are a few useful global options. These just restate default settings, but are worth mentioning.

Modern access points (like those my employer has deployed) are able to broadcast more than one network ID (SSID), and potentially respond to several more. To find these alternate SSIDs, the supplicant must poll access points. ap_scan=1 turns on this capability, and indicates that wpa_supplicant (not the driver) should handle AP scanning. eapol_version indicates which version of the polling protocol should be used. Version 2 exists (and is defined in the 802.1x spec), but not many access points support it yet - hence using version 1.

If you operate in an environment with many hidden SSIDs, you'll probably want to set ap_scan=2. With that, when a new access point is detected the supplicant will iterate through every network defined in the config file to see if a proper network connection can be made (rather than just relying on broadcasted SSIDs). 

So not sure if you'll need them... I did a lot of messing around to get this to work so may have seen them somewhere and put them in to test if they were needed... and not removed them when I finally got it working!

---

### Post by RudderDuck on 2009-09-05
Another option to connect wireless, although not through eduroam, is to use Wnet1 and VPN. I found the required information at:

[https://wiki.ubuntu.com/NlTUDelft](https://wiki.ubuntu.com/NlTUDelft)

First you need to install 'network-manager-vpnc' as follows:

```
sudo apt-get install network-manager-vpnc
```

This allows you to configure a new vpn connection:

Click the network applet icon.
Click VPN Connections.
Click Configure VPN...

A 'Network connections' window pops up.

Click the VPN tab, if it isn't already selected.
Click the Add button.

A new window appears.

Click the Create... button.

A new window appears.

Fill in the required info:

Gateway: luchtbrug.tudelft.nl
Group name: public
User password (saved): your_netid_password
Group password (saved): wireless
User name: your_netid_user_name

Click the apply button and your almost done.

Whenever you have Wnet1 listed as an access point connect to it (it's unsecure so you can connect without problem). Then click the network applet icon. Click VPN Connections. Finally click the VPN connection you created above.

This works for me with the Ubuntu netbook remix.

I will also try and get eduroam working though. And finally, webprint, a real pain...

---

### Post by atom heart on 2009-09-09
> **tomBorgia said:**
> I think -

update_config=1 allows wicd to update wpa_supplicant.conf.

From [http://www.fmepnet.org/debian_wpa.html]("http://www.fmepnet.org/debian_wpa.html") -



So not sure if you'll need them... I did a lot of messing around to get this to work so may have seen them somewhere and put them in to test if they were needed... and not removed them when I finally got it working!

thank you again

---

### Post by RudderDuck on 2009-09-22
> **atom heart said:**
> Wow 
thank you so much!
followed your instructions and worked perfectly!

btw do you have a link for specifying commands like 
eapol_version=1
ap_scan=1
update_config=1
 
or any tutorial on creating wicd templates?

Hi Atom Heart,

Could you post the template you are using to connect to eduroam at Delft?

Somehow it doesn't want to connect to eduroam here.

Thanks.

---

### Post by humphreybc on 2009-09-25
Does anyone know how to connect to a university wireless network with the following properties?

WPA and WPA2 Enterprise
PEAP Authentication
No CA certificate
MSCHAPv2 Inner Authentication
username + password

And then a proxy too, although I have that sorted.


It will connect... but often takes about 20 minutes and several retries, and then it drops the connection every 5 minutes or so, sometimes never reconnecting for ages... ie, it's severely unreliable.

Do you think it's Ubuntu's fault, or the University network?

---

### Post by tomBorgia on 2009-09-25
Have you tried Wicd or just using the default network manager?

Have a word with your universities' support people for the correct details - I'm sure they'll have some linux monkeys there!!!

---

### Post by tomBorgia on 2009-09-25
Have you tried Wicd or just using the default network manager?

Have a word with your Universities' support people for the correct details - I'm sure they'll have some Linux monkeys there!!!

---

### Post by atom heart on 2009-09-25
follow the instructions provided by tomborgia!

cheers

---

### Post by RudderDuck on 2009-09-26
> **tomBorgia said:**
> Have you tried Wicd or just using the default network manager?

Could you explain why to use Wicd instead of the default network manager? I tried Wicd but had no luck using it, would connect but is unable to find any names. Something with it disabling name resolving. Had to go back to the default network manager.

Is Wicd really necessary for eduroam?

Thanks!

---

### Post by atom heart on 2009-09-26
I choosed wicd for eduroa because of the disconecting issues.

for wicd follow the instructions by tomborgia !!!
this works!


for creating a new wicd template google :wicd template






Bit late reply but spent ages getting this to work so glad to share and hope it helps!

I have eduroam working with wicd (as opposed to network manager) - You'll need to install wicd (sudo apt-get install wicd) and create a custom encryption file in /etc/wicd/encryption/templates/ (I called mine eduroam)

Code:

name = eduroam
author = Tom Borgia  
version = 1
require identity *Identity anonymous_identity *Anonymous_identity password *Password
-----
ctrl_interface=/var/run/wpa_supplicant

eapol_version=1
ap_scan=1
update_config=1

network={
        ssid="eduroam"
        key_mgmt=WPA-EAP
        eap=TTLS
        identity="$_IDENTITY"
        anonymous_identity="$_ANONYMOUS_IDENTITY"
        password="$_PASSWORD"
        ca_cert="/etc/ssl/certs/Equifax_Secure_CA.pem"
        phase2="auth=PAP"
}

the ca_cert may be different for your university... and you'll also need to add the line "eduroam" (or whatever you called the file with those details in) to /etc/wicd/templates/active to enable it. Load up the wicd manager, select "use encryption" and you should have eduroam in the drop down box... enter your username and password (anon id is usually anon@your-university-domain) and connect! You'll need to set "use these aettings for all connections with this ssid" so you don't need to set it up each time.

Hope that works.

---

### Post by tomBorgia on 2009-09-28
> **RudderDuck said:**
> Could you explain why to use Wicd instead of the default network manager? I tried Wicd but had no luck using it, would connect but is unable to find any names. Something with it disabling name resolving. Had to go back to the default network manager.

Is Wicd really necessary for eduroam?

Thanks!

Using network manager the wireless would connect, authenticate and then be fine for 5 - 10 mins... then drop and fail to reconnect - for some reason wicd is a lot more robust on the Samsung NC10 I'm using so may be hardware related...

---

### Post by TKoorn on 2009-11-29
Is anybody able to connect to eduroam at the TU Delft with Ubuntu 9.10? I can't get it to do anything. I followed the instructions on luchthaven.tudelft.nl but nothing happens.
It used to work fine but since the changes of 3 november I can't get in anymore.

---

