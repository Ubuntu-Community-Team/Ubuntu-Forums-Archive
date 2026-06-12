---
title: "Having trouble with Wireless Connection"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by Kvalenti on 2009-09-20
I am new to Linux and exploring the idea of switching from Windows.  For now I have set up a Windows dual boot.  I have an unsecured wireless lan in place (lynksis) with a range expander.  I can connect all day long when I boot into Windows XP.  However, when I boot up under Linux (9.04) I am only able to connect for short periods of time.  The signal indicator usually only gives me 2 or three bars under Linux, while I get an "Excellent" connection indicator in Windows.  Once my connection drops under linux, I cannot re-establish it unless I power down the machine and reboot it.  Help!
 
Thanks

---

### Post by diafanos on 2009-09-20
I had a similar problem regarding wireless range. Try to use the following command to check if it will be fixed:

```

sudo iwconfig <wlan0> rate 5.5M

```

where in <wlan0> put the name of the wireless interface. 
If you don't know what it is, run the command:

```

iwconfig

```

and you will get a list of interfaces. The one that has frequency, mode etc info is the wireless one.

---

### Post by Kvalenti on 2009-09-20
Thank You.  I tried the command but received an error "no such device".  Did I enter this incorrecly?  See below 

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:79:E9:DC   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=67/100  Signal level:-56 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ sudo iwconfig linksys rate 5.5M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device linksys ; No such device.
kenny@Valentine-desktop:~$

---

