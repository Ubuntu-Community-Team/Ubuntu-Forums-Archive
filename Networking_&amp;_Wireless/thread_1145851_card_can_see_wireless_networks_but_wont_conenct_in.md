---
title: "card can see wireless networks but wont conenct in jaunty, but did worlk in hardy"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by Yondergod22 on 2009-05-02
I just updated to Jaunty and my wireless doesn't work anymore. It is a trendnet TEW-424UB usb adpater with a rtl8187B driver installed with ndiswrapper. In hardy I had to manually connect with these commands to get it to work (network manager didn't work)
```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "(essid)"
sudo iwconfig wlan0 key (wep key)
sudo iwconfig wlan0 key open
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```
but now it doesn't work, DHCPDiscover always fails. When I try to connenct with network manager nothing (that I can see) happens, and when I try to connect with the network icon thing in the top right corner of the screen, it keeps asking me for my wep key over and over again until I cancel it.

Thanks for your help :)

---

### Post by Yondergod22 on 2009-05-02
bump. I might just have to go back to 8.04 :'(

---

### Post by Maethoriel on 2009-05-02
Have you tried connecting to any other networks?  My home network uses 128-bit WEP, and I can't connect to that (so far), but it connected to the wireless at school just fine.  You could try connecting to wireless at a library or cafe to see if the problem is the wireless in general or just in dealing with WEP.  (Sorry I don't have more useful advice, I'm no expert, but if I do find a solution to getting mine to work I'll post back here to see if it helps you too!)

---

### Post by bkratz on 2009-05-02
I tried unsuccessfully to connect to my wep network for several weeks  (since the beta version) , I never was able to access the wep version (it just seemed to lock up)  so I changed my router to no encryption which worked.  Yesterday I switched to WPA/WPA2 and it worked perfectly.  Have you tried to remove encryption?

---

### Post by Yondergod22 on 2009-05-02
thanks for the suggestions, but there is no other wireless networks around here, and I don't have access to my router to change the encryption  (it's in my parents room and they wont let me touch their computers or give me the password for the router)

---

### Post by Yondergod22 on 2009-05-03
ok I confirmed, it does work with no encryption, but I have to turn it back on, so I need to make it work with a wep key.

---

