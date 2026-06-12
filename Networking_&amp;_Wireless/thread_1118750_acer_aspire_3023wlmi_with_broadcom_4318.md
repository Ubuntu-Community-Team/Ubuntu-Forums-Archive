---
title: "acer aspire 3023wlmi with broadcom 4318"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by SpikeyMike on 2009-04-07
I just got wireless working on my pc after trying for a while and am now trying to get it working on my laptop, I installed intrepid and first installed wicd, then I tried this procedure by alex_kent_18, after the procedure if I go to system > administration > network tools my wireless card shows up there but when I open wicd it doesn't show any wireless networks, I tried uninstalling wicd and installing network manager instead but this doesn't connect to my network either, I filled in all the necessary info, ssid, encryption etc but it tries to connect but eventually fails. The problem is I am not sure if my wireless is enabled properly because the light no longer works, the light doesn't work in windows either but I am able to connect wirelessly in windows, any advice greatly appreciated.

Spikey

---

### Post by SpikeyMike on 2009-04-07
sorry I forgot to include the procedure from alex_kent_18 I followed, it's here:

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by superprash2003 on 2009-04-07
in your terminal type the following commands and post output
1)iwlist scanning
2)iwconfig

---

### Post by SpikeyMike on 2009-04-07
> **superprash2003 said:**
> in your terminal type the following commands and post output
1)iwlist scanning
2)iwconfig

here is the output from iwlist scanning:

[COLOR="Red"]mikey@mikeys-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan1     No scan results

pan0      Interface doesn't support scanning.[/COLOR]


and from iwconfig:

[COLOR="Red"]mikey@mikeys-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:Off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:0ff
          Power Management:0ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.[/COLOR]


cheers

Spikey

---

### Post by superprash2003 on 2009-04-08
did you have wifi networks around at the time you posted these outputs? cause wlan1 says NO SCAN RESULTS.. which means it did attempt to scan..
 have you tried the drivers at system->admin->hardware drivers

---

### Post by SpikeyMike on 2009-04-09
> **superprash2003 said:**
> did you have wifi networks around at the time you posted these outputs? cause wlan1 says NO SCAN RESULTS.. which means it did attempt to scan..
 have you tried the drivers at system->admin->hardware drivers

hi, yes my wifi network is on all the time and there are alot of other networks around so it should have found something. I originally activated the restricted broadcom bc43xx driver using system > admin > hardware drivers but that didn't work so I tried using ndiswrapper. 

I take it nidswrapper works with wicd?

also if I try another driver using ndiswrapper -r to remove the old driver and then ndiswrapper -i to install a different one do I need to go through the whole procedure again as described in the link in my original post?

thanks in advance

Spikey

---

### Post by Ayuthia on 2009-04-09
You might check out this thread:
[http://ubuntuforums.org/showthread.php?t=995780](http://ubuntuforums.org/showthread.php?t=995780)

I am not for sure if you are able to do this with ndiswrapper or not, but I would think that it should be the same.  It looks like there is a wireless switch that is not getting activated for your card.

---

### Post by SpikeyMike on 2009-04-10
> **Ayuthia said:**
> You might check out this thread:
[http://ubuntuforums.org/showthread.php?t=995780](http://ubuntuforums.org/showthread.php?t=995780)

I am not for sure if you are able to do this with ndiswrapper or not, but I would think that it should be the same.  It looks like there is a wireless switch that is not getting activated for your card.


hi, great thanks for your message, that was the problem, I had to enable the wireless adaptor, did it by running the command:

echo 1 > /sys/devices/platform/acer-wmi/wireless

the only thing is I need to do that every time I boot the laptop, do you know how I can get that command to run automatically on startup?

Spikey

---

### Post by Ayuthia on 2009-04-10
> **SpikeyMike said:**
> hi, great thanks for your message, that was the problem, I had to enable the wireless adaptor, did it by running the command:

echo 1 > /sys/devices/platform/acer-wmi/wireless

the only thing is I need to do that every time I boot the laptop, do you know how I can get that command to run automatically on startup?

Spikey

You can try and add the command in /etc/rc.local.  Just put the command above the exit 0 line.

---

### Post by SpikeyMike on 2009-04-11
> **Ayuthia said:**
> You can try and add the command in /etc/rc.local.  Just put the command above the exit 0 line.

hi, thanks that worked perfectly.....

Spikey

---

