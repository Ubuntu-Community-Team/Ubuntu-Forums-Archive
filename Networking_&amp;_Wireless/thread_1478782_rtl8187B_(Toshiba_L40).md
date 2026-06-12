---
title: "rtl8187B (Toshiba L40)"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Crio on 2010-05-10
I just want to share my experience, hope it will help someone.

I have Toshiba Satellite L40 laptop, which features **internal USB** Realtek wireless card RTL8187B. 
> $ lsusb|grep -i realtek
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
This modification is less frequent than RTL8187**L** and notice PID 8197 - it seems to be non-standard even for RTL8187B device (see later).

This card is recognized and supported by Ubuntu distributions out of the box via rtl8187 module, it works fine with Network Manager, there should be no problem with connection.

Unfortunately, there is a problem - the card has stable connection only at 11Mbs even next to AP and when I attempt to force it to higher speed (for example: sudo iwconfig wlan0 rate 54M), connection breaks. It breaks even when I use 12M rate, but it is stable at 11M. My guess is that there is something wrong with the support of 802.11g in the driver and the card only works in 802.11b mode (which is limited by 11Mbs), though I have no idea how to confirm that.

So, point #1: if your connection is unstable, try to limit connection rate to 11Mbs.
> $ sudo iwconfig wlan0 rate 11M

This is fine for browsing, but not so good for anything else, because actual transfer rates fluctuate between 50kB/s and 250kBs with median about 100. I was living with that for quite a while, but after upgrading to Lucid I've decided to try to fix it. Long story short I get success with ndiswrapper driver. It now works at 54Mbs with real transfer rates between 1 and 2 MB/s, on par with Windows.

Installation of ndiswrapper was really simple (I followed *[Ubuntu community docs]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")* with just one catch - *[official Realtek Windows driver]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B")* won't install even in Windows! The catch is "non-standard" PID 8197 I mentioned above - it is not present in the inf file from Realtek. Well, I inserted it there and everything worked!
Therefore, point 2: 
> if you have the same PID 8197, you can: 
1. download Realtek driver at the ink above, 
2. unzip, 
3. go to RTL8187/WinXP subdirectory, which contains  net8187b.inf, net8187b.cat, and net8187B.sys (all you need from ~16M archive).
4. open net8187b.onf in your favorite text editor and replace all occurences of "PID_8187" string by "PID_8197" (no qoutes, of course!).
5. Proceed with the ndiswrapper instructions.


After that everything worked like a charm; syslog shows that there is an error during the connection procedure: 
> May 10 09:42:12 NetworkManager: <info>  Config: set interface ap_scan to 1
May 10 09:42:16 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May 10 09:42:41 wpa_supplicant[880]: Trying to associate with 00:26:5a:71:d1:44 (SSID='myWiFi' freq=2427 MHz)
May 10 09:42:41 wpa_supplicant[880]: Association request to the driver failed
May 10 09:42:41 kernel: [ 2371.327026] ndiswrapper (iw_set_auth:1602): invalid cmd 12

but it does not seems to affect anything, because it proceeds to successfully associate itself with AP.

Hope that would be of use.

---

### Post by mdhurst on 2010-08-11
I spent a few hours exploring a fix for this and this finally worked. I installed ndiswrapper and the windows XP driver for rtl8187B following the steps you mention (including step 2 editing the driver).

---

### Post by ciupanezul on 2011-02-01
Thank you very much.. I have red a lot about ndis... but never tried it out. IT WORKS LIKE A CHARM ! I have the same laptop and wireless adapter so i really needed it  ! Thank you so much !

---

### Post by bradleesand on 2011-02-06
I just want to add my thanks to this. I was getting pretty frustrated with WiFi not working on my laptop. Thanks so much for this easy fix.

---

