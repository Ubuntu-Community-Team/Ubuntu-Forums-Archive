---
title: "wireless problem on eeepc 1000h with rt2860"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by szend on 2010-10-03
hello,
i have struggled to set up the wireless connection with RT2860. I read a lot in different forums and i see everywhere different solutions.
I couldn't install the new drivers, because i have got always errors during the installation process.

My problem that i sew always this:
i@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless  **ESSID:""**  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:21:91:EE:E8:C6   
     **     Bit Rate=1 Mb/s   **
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-35 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I thought it cannot find my ssid, so did:
root@ubuntu:/etc/Wireless/RT2860STA# vi RT2860STA.dat

and i changed this:
SSID=dlink

instead of the original line, which is:
SSID=

Now i see:

i@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RT2860 Wireless **[COLOR=black] ESSID:"dlink" [/COLOR]** Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:21:91:EE:E8:C6   
          **Bit Rate=65 Mb/s   **
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-35 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I don't know if because of my change but now it is workin **only sometimes **and sometimes if i want to connect in wicd, i get an error message: "bad password"

Somebody could explain me, how it works? I'm very new on linux and ubuntu and it is driving me crazy, that i cannot figure out why it works only sometimes.

thanks
szend

---

