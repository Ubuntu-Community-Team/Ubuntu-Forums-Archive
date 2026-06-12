---
title: "Ubuntu, ndiswrapper,D-Link DWL G630 AirplusG and Icewm, static IP"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by ncmncm on 2009-07-18
Hello, 

I have tried to summarize the list of steps required for running IceWM on Ubuntu with the DWL G630 PCI card wireless enables at startup. 
**Please let me know if there are some steps where corrections can be made **



On my old laptop running at 1.2 GhZ and 512MB RAM (Dell C640 Series) , I prefer IceWM. Sleek and  a palpable performance appreciation over Gnome.
For wireless,  I have a D-Link DWL G630 PCI card. The  Windows drivers come with the CD when you purchase it.

Naturally, for such a system, the requirements would be to have wireless enabled at startup. Here are the broad steps. 


----------------------------------------------------------
**0. Firstly, update your packages**

 ```
    sudo apt-get update
```


**1. Install the ndiswrapper tools.**

    ```
   sudo apt-get install ndisgtk 
```

**2. Launch ndisgtk GUI and install the DWL-G630 drivers**.
  


( Note: ensure that the ***lspci*** command lists  RaLink RT2561/RT61)
```
ndisgtk
```
 All you need to  do in this case is to point to the .INF file (netrt61g) that comes with the CD. If you do not have the CD, search  for the drivers online.  The windows drivers are automagically installed for Ubuntu.
The drivers are usually installed in the *** /etc/ndiswrapper/***  folder

If your PCI card is inserted, ndisgtk should say "Hardware present".

After this stage, you should check your wireless card with Gnome. You should be able to connect to you router with the right settings.

Continue reading further for startup settings.

[B] 
3. Install wpasupplicant package[/B]
```

       sudo apt-get install wpasupplicant
```


**4. Run wpa_passphrase**

```
      sudo wpa_passphrase your_ssid your_password > /etc/wpa_supplicant/wpa_supplicant.conf

```

You will end up with the contents:

>     network={
            ssid="qi"
            #psk="DharmicKarma"
            psk=d9fa4c5cc20b4c94b50cf021ddf67e31c9ddd63429c85ddd3fff5ddaa85c4eb65142c00
    }


**5. Edit /etc/wpa_supplicant/wpa_supplicant.conf**

You need to add protocol details for your wireless connection. Post editing, mine looks like this for WPA-PSK settings

>     network={
            ssid="qi"
            #psk="DharmicKarma"
            psk=d9fa4c5cc20b4c94b50cf021f67e31c9563429c853fff5ddaa85c4eb65142c00
            proto=WPA
            key_mgmt=WPA-PSK
            group=TKIP    
            pairwise=TKIP
    }


**6. Edit /etc/network/interfaces file**

Mine looks like this for the static IP I am using.
> 
    auto lo
    iface lo inet loopback


    auto wlan0
    iface wlan0 inet static
    address 192.168.0.3
    netmask 255.255.255.0
    gateway 192.168.0.1
    wpa-driver wext
    wpa_conf /etc/wpa_supplicant/wpa_supplicantconf




Adapt it to your needs for dhcp. You are done with the wireless settings. All that needs to be done is ensuring that the driver loads at startup and  your  PC knows the DNS servers.

**7. Ensure ndiswrapper in startup**

Edit** /etc/modules** and add the line **ndiswrapper** at the end
[B]
8. Edit resolv.conf / make it non-editable[/B]
Add your DNS server to /etc/resolv.conf - A line like 

> ** nameserver 192.168.0.1** 
   should usually do.


Prevent network manager from editing the the resolv.conf like so 

>  chmod u-w /etc/resolv.conf

-------------------------------------------------

---

