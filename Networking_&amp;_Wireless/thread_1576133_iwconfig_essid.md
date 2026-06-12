---
title: "iwconfig essid"
date: 2010-09-16
forum: Networking &amp; Wireless
---

### Post by IQRules on 2010-09-16
> root@sony:~# iwconfig wlan0 essid NPPL
root@sony:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:**[COLOR="Red"]"\x0D\xA7\xFAZ\xD8\xB0\xB5\xDBP\xC2\xFD]\x09Z*\xA5\xE2\xA3\xFB\xB7\x13GT\x9A1c2#N\xCEv[" [/COLOR]** 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr : off   Fragment thr : off
          Encryption key : off
          Power Management : off
          

Is this a bug here in iwconfig?

---

### Post by jlanza on 2010-09-17
i'm also getting that sometimes but still doesn't know the reason.

---

### Post by MaindotC on 2010-09-17
Are you having problems connecting?

---

### Post by onnob on 2010-09-23
> 
root@sony:~# iwconfig wlan0 essid NPPL
root@sony:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:**[COLOR=Red]"\x0D\xA7\xFAZ\xD8\xB0\xB5\xDBP\xC2\xFD]\x09Z*\xA5\xE2\xA3\xFB\xB7\x13GT\x9A1c2#N\xCEv[" [/COLOR]** 
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr : off   Fragment thr : off
          Encryption key : off
          Power Management : off                      
Having the exact same problem in 10.04. Recently installed FVWM and tried connecting to my regular access point using iwconfig instead of gnome network manager when I encountered it. No idea what causes it...

---

### Post by IQRules on 2010-09-26
> **strAlan said:**
> Are you having problems connecting?

Of course, I can't connect.
Not sure this bug is related to upper case essid here.
At home, my essid is in lower cases, no issue.

Thanks

---

### Post by MaindotC on 2010-09-26
Well iwconfig certainly shouldn't be doing that but until the problem is resolved you may want to try using NetworkManager or Wicd if you have access to the desktop.

If you think it is a bug be sure to file a [bug report on Launchpad]("https://launchpad.net/ubuntu/+source/wireless-tools") so the developers can address it.

---

