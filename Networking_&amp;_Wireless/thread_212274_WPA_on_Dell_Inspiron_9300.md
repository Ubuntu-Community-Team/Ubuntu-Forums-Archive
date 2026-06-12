---
title: "WPA on Dell Inspiron 9300"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by cjnkns on 2006-07-09
I have been reading docs here and there about how to get WPA support on Dapper, but it hasn't been as easy as the docs are saying it should be for Dapper.

According to what I have read I should just install the Network Manger and the right click on it and select my wireless network info enter my WPA info and bada bing bada boom done. But this certainly is not the way it has worked so far. Are there problems with Dapper and connecting to wireless networks? I have seen does on wapsupplicant but it looks old like from Feb and I think that was due to the older version of ubuntu right?

---

### Post by eloj on 2006-07-09
Couldn't hurt to try wpasupplicant and see what happens. Will at least give you a lot of debug info.

Sample pretty minimal wpa_supplicant.conf for WPA-PSK (Pre-Shared Key, which is the common use)

```
update_config=1
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1

# Only WPA-PSK is used.
network={
	ssid="your_ssid_here" # this is the 'name' of the AP
	proto=WPA
	key_mgmt=WPA-PSK
      psk="your password key here"
}
```

Then, assuming your card is on eth1 (check iwconfig/ipconfig!) start it up with
```
sudo wpa_supplicant -Dwext -ieth1 -cYourConfigFile.conf
```

Note that using the ipw driver didn't work for me. From googling it seems the Inspiron 9200 use the ipw2000 just like my Inspiron 6000.

Make sure your hardware has been detected (ipconfig et.al), if not that's your problem right there.

---

### Post by cjnkns on 2006-07-09
I do not see a wpa_supplicant directory under /var/run I do however see it under /etc. In /etc the wpa_supplicant diretory has a ifupdown.sh file. Is this the same as the /var/run one you mention?

Or am I supposed to install wpa_supplicant from somewhere?

Thanks for your help!

---

### Post by eloj on 2006-07-09
If you have /etc/wpa_supplicant it ought already be installed.

The control interface is handled by wpa_supplicant (so the directory will be created when it runs). It's not important for you at this time. It's just for other utilities (like GUI tools) to communicate with wpa_s.

---

