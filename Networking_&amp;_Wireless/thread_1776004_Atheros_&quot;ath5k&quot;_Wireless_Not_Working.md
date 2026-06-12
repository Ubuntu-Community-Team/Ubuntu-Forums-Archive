---
title: "Atheros &quot;ath5k&quot; Wireless Not Working"
date: 2011-06-05
forum: Networking &amp; Wireless
---

### Post by Naturally-Simple on 2011-06-05
Hello. I've followed a few different steps to try and solve the wireless issue, but no luck so far. I have a Compaq Presario CQ60 with Atheros 5001 "ath5k" driver and module. I use "WPA & WPA 2 Personal" security. 

I first did "rfkill list all" to see what was being blocked, and at the time, I had this:
> 
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: yes 
1: phy0: Wireless LAN
Soft blocked: no
Hard blocked: yes
Sometimes the soft options were blocked, sometimes the hard. So I did "rfkill unblock all" which sometimes unblocked, sometimes didn't. I did "rfkill unblock wifi" which worked sometimes and sometimes didn't. After a reboot, it was working, but after another reboot, "rfkill unblock all" and "rfkill unblock wifi" consistently didn't work. I also tried the physical wireless toggle switch, which seemed to help in the first attempt, but after the reboot, didn't work.

So I followed these instructions written by [chili555]("http://ubuntuforums.org/member.php?u=35909") from this thread ([11.04%20%22Natty%20wireless%20issue%20-%20Acer%20-%20Device%20not%20ready,%20rfkill%20soft%20auto%20blocked%29:"]http://ubuntuforums.org/showthread.php?p=10748476#post10748476%22]11.04%20%22Natty%20wireless%20issue%20-%20Acer%20-%20Device%20not%20ready,%20rfkill%20soft%20auto%20blocked):]("http://ubuntuforums.org/showthread.php?p=10748476#post10748476%22) >      Code:
     sudo rmmod -f acer-wmi sudo rfkill unblock all rfkill list all 
Code:     sudo su echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf gedit /etc/rc.local 
Add one line above Exit 0     Code:
     rfkill unblock all 
Instead of "acer-wmi" I put my "hp-wmi". So now my hp-wifi is gone when I type "rfkill list all" and all that shows is this:

kevin@deep-thought:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

And at the time, wireless was working, but then it disconnected after reboot, and can only search for the connection but can't connect. The other wireless networks were visible when it connected, but now they aren't. I can click "connect to hidden wireless network" and it attempts to connect to my network, but it tries and tries before asking me for my pass, which is typed correctly. It just won't connect.

I came across this thread ([http://ubuntuforums.org/showthread.php?p=10884683](http://ubuntuforums.org/showthread.php?p=10884683)), but I'm leery of messing around more with codes and commands I don't understand (I feel like I've done enough messing around as is).

Here is my output from
dmesg | grep ath
sudo iwlist wlan0 scan:

> kevin@deep-thought:~$ dmesg | grep ath
[    1.054391] device-mapper: multipath: version 1.2.0 loaded
[    1.054394] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.630426] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.630440] ath5k 0000:02:00.0: setting latency timer to 64
[   14.630494] ath5k 0000:02:00.0: registered as 'phy0'
[   15.136257] ath: EEPROM regdomain: 0x64
[   15.136260] ath: EEPROM indicates we should expect a direct regpair map
[   15.136263] ath: Country alpha2 being used: 00
[   15.136265] ath: Regpair used: 0x64
[   15.177849] Registered led device: ath5k-phy0::rx
[   15.177931] Registered led device: ath5k-phy0::tx
[   15.177942] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
> kevin@deep-thought:~$ sudo iwlist wlan0 scan
[sudo] password for kevin: 
wlan0     No scan results
Sorry for such a long post! Any help is much appreciated.

---

### Post by drpjkurian on 2011-06-05
Hi
Why cant you try Madwifi drivers?
See my blog [http://ubuntucrack.blogspot.com/2010_07_18_archive.html](http://ubuntucrack.blogspot.com/2010_07_18_archive.html)

---

### Post by chili555 on 2011-06-05
> **drpjkurian said:**
> Hi
Why cant you try Madwifi drivers?
See my blog [http://ubuntucrack.blogspot.com/2010_07_18_archive.html](http://ubuntucrack.blogspot.com/2010_07_18_archive.html)By default, in Natty, ath_pci is blacklisted. If you install madwifi, please be sure to do:```
sudo rm /etc/modprobe.d/blacklist-ath_pci.conf
```You might read the file for important information before you proceed.

You might also consider the compat-wireless suite.

---

### Post by Naturally-Simple on 2011-06-05
My friend (who's out of town) is the one I go to for Ubuntu help, but for this issue he had said a new release of Ubuntu should automatically compensate for my system's wireless problem rather than me having to install Madwifi. Unfortunately, that was since 9.04.

In any case, I can try Madwifi by following the instructions on your blog, drpjkurian, but should I do what you posted, Chili555 before or after I install Madwifi?

Also, should I undo any of the changes I already made by blacklisting hp-wmi and the rmmod command?

---

### Post by chili555 on 2011-06-05
> should I do what you posted, Chili555 before or after I install Madwifi?Before.> should I undo any of the changes I already made by blacklisting hp-wmi and the rmmod command? Nope. Please post your experience so we all, including the searchers, learn from it.

---

### Post by Naturally-Simple on 2011-06-05
I followed both of your instructions. Actually, to be honest, I forgot to do Chili555's instructions before installing MadWifi, so I started again this time doing Chili555's, then following drpjkurian's blog instructions.

I can now connect wirelessly, but only after I first start with my wired connection, then I push the wireless toggle button, and then voila, I see all the wireless networks I can connect to, plus my own, and it works to connect. But if I unplug the wired, then reboot, I have no wireless. So to get it back, I plug in the wired, press the toggle switch, then I get my wireless.

Any thoughts on this?

---

### Post by Naturally-Simple on 2011-06-05
Here's an update from when I came home this evening. It's similar to before, but now my wireless isn't working.

When I booted up tonight, I couldn't see any wireless networks. It said wireless disabled. I unplugged my wired cable and I clicked on "connect to hidden wireless network" and chose my network. It couldn't connect (eventually asked for my password). So I plugged my wired cable back in again. It continued to try to connect to my wireless, but I gave up on it and disconnected after the third time it showed me the password prompt (which, again, I know I'm typing in the right password in case you're wondering).

I pushed the wireless toggle button on my laptop, and then I saw the list of the other available networks including my own. I clicked on my network, but it just wouldn't work. I also tried connecting to one of the non-password protected networks, but no luck.

What do you think is going on here?

Also, why does my "rfkill list all" command not show me anything any more?

Here's my terminal output from iwconfig and ifconfig (I'm not sure which other outputs you'd like to see):
> kevin@deep-thought:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Heavyfoot"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:21:91:E9:44:97   
          Bit Rate:1 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=2/70  Signal level=-94 dBm  Noise level=-96 dBm
          Rx invalid nwid:9400  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kevin@deep-thought:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:24:2c:52:f9:5e  
          inet6 addr: fe80::224:2cff:fe52:f95e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:36450 (36.4 KB)  TX bytes:18225 (18.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:1f:16:d6:21:06  
          inet addr:192.168.1.137  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fed6:2106/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:827 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:533326 (533.3 KB)  TX bytes:198090 (198.0 KB)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:51760 (51.7 KB)  TX bytes:51760 (51.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-24-2C-52-F9-5E-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14254 errors:0 dropped:0 overruns:0 frame:1739
          TX packets:2356 errors:129 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:3098584 (3.0 MB)  TX bytes:179510 (179.5 KB)
          Interrupt:17 


---

### Post by chili555 on 2011-06-06
Sorry for the delay in responding. We had a power outage due to severe weather. I apologize in advance for my response. I have no desire to get into a disagreement with one of our very helpful posters, but I think your wireless is not working as well now as before you installed Madwifi. If you agree, would you like to uninstall Madwifi and try compat-wireless?

When you boot up without the cable plugged in is ath_pci loaded?```
lsmod | grep ath
```Does pressing the wireless switch have no effect? Does reloading acer-wmi make your switch effective?```
sudo modprobe acer-wmi
```

---

### Post by Naturally-Simple on 2011-06-06
I booted up without the cable, and checked lsmod | grep ath which showed this:
> 
kevin@deep-thought:~$ lsmod | grep ath
ath_rate_sample        17279  1 
ath_pci               183044  0 
wlan                  224640  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398701  3 ath_rate_sample,ath_pci

So I pressed the wireless switch, but no effect. I tried reloading the wmi, which is actually hp-wmi, not acer-wmi (My original post included the instructions that were for an acer-wmi problem, but I simply replaced that with "hp-wmi" on my own machine). But just to be sure I wasn't misunderstanding something, I first tried it with acer-wmi. Here's what I put into my terminal:
> 
kevin@deep-thought:~$ sudo modprobe acer-wmi
[sudo] password for kevin: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Error inserting acer_wmi (/lib/modules/2.6.38-8-generic/kernel/drivers/platform/x86/acer-wmi.ko): No such device
kevin@deep-thought:~$ sudo modprobe hp-wmi
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Then a notification appeared that said "wireless disconnected" which is odd considering that it never was connected.

Anyway, after this, I tried rfkill commands:
> 
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
kevin@deep-thought:~$ rfkill unblock wifi
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

By the way, that hard block went away after I pushed my wireless switch.

After this, I could see all potential wireless networks (actually, I may have seen these after re-loading hp-wmi, I can't recall), including my own. I clicked on mine, tried to connect, no dice. It kept trying and trying, then it prompted me for the password, and even though I felt that this would be futile, it tried connecting for a long time again, and then suddenly it connected!

What on earth?

I'll see if this current setup continues to work throughout the day. I'll try a reboot after this, then I'll need to leave for work and will try rebooting when I get back. If there continue to be issues, I'd be up for trying compat-wireless so long as I get really detailed instructions.

---

### Post by Naturally-Simple on 2011-06-06
Okay, after a reboot without my cable plugged in, I had the same issue as in my post above. I could see the other wireless networks, but pressing my switch did nothing. Then I repeated the steps you posted before, Chili555. After I re-loaded hp-wmi, I used rfkill to see about any blocks, saw the soft and hard blocked, pressed the wireless switch, saw the hard unblocked like last time, then did rfkill unblock wifi and both soft and hard were unblocked. I clicked on my network and hey presto, I'm here using the wireless to send you my update.

If I could make this permanent without having to manually re-load hp-wmi and unblock my hard and soft, I'd be fine with this. Is this what you think compat-wireless may do for me?

---

### Post by chili555 on 2011-06-06
Please try:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Change the hp-wmi line to:```
#blacklist hp-wmi
```The # symbol will ask the system to ignore that line. Proofread carefully, save and close gedit. Next, do:```
sudo gedit /etc/rc.local
```Add one line above exit 0```
rfkill unblock wifi
```Proofread carefully, save and close gedit.> WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.Whatever is in there needs to be in blacklist[COLOR="Red"].conf[/COLOR]. Let's have a look:```
cat /etc/modprobe.d/blacklist
```Reboot and tell us if your wireless is working.> so long as I get really detailed instructions. That's my specialty!

---

### Post by Naturally-Simple on 2011-06-06
Hallelujah! It works! I suppose a problem there was the /etc/modprobe.d/blacklist without the ".conf" at the end.

Drpjkurian, I took another look at your blog instructions, and they are also missing the ".conf" at the end of the blacklist file. Just a heads up for people in a similar situation as mine. Other than that, though, your instructions and Chili555's tweaking have helped me out tremendously!

I've rebooted three times now, two without the wired connection and my wireless automatically connected. The third time, I was wanted to see if starting it with a wired connection would make any difference, but I had both wired and wireless working. When I unplug the wired, the wireless kicks in, and vise versa. Smooth as silk.

Just in case, I'll leave this unresolved until later tonight when I check again. I don't see why another 8 hours would make a difference, but you never know. If all is still well, I'll mark this thread as solved.

Thanks again so much you two!

---

### Post by Naturally-Simple on 2011-06-06
UPDATE:

Turning my computer on poses no problems for my wireless, but it would seem as though there's an issue with the wireless when the system wakes from sleep after I shut the laptop lid. At that point I can't see any other networks (well, besides just one random one which isn't mine), and I tried connecting to mine as a hidden network, but that didn't work. Rfkill shows all is unblocked.

Any ideas on that?

---

### Post by chili555 on 2011-06-06
You might try this:```
sudo gedit /etc/pm/config.d/config
```Add one line:```
SUSPEND_MODULES=ath_pci
```Proofread carefully, save and close gedit. It may take a reboot to get all the various systems to see the change. ath_pci is the Madwifi driver, right? Please check lsmod.

DISCLAIMER: This works often, but not always.

---

### Post by Naturally-Simple on 2011-06-07
I was wondering whether you missed something at the end of "config" but I followed your instructions, Chili555, and it seems like this has fixed the issue for me. I've tested it twice now, so I'd imagine it should keep on working. I'll mark this as solved.

Thanks again so much!

---

### Post by chili555 on 2011-06-07
Happy to have helped. Glad it's all sorted. Have fun!

---

### Post by chili555 on 2011-10-02
I'm confused. Did you install madwifi? Please let me see:```
sudo updatedb
locate ath | grep .ko
```What is in /etc/modprobe.d/blacklist?```
cat /etc/modprobe.d/blacklist
```We'll transfer it all, if we need it, to blacklist**.conf**.

What does this tell us?```
sudo modprobe ath5k
dmesg | grep ath5k
```

---

### Post by Naturally-Simple on 2011-10-02
just before I saw your post, I tried "rfkill list all" to see what it shows:
> kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

so I toggled my physical button, with no luck. I tried "rfkill unblock wifi" but that gave me this:
> kevin@deep-thought:~$ rfkill unblock wifi
kevin@deep-thought:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Here's the output of the commands you asked me to try:
> kevin@deep-thought:~$ sudo updatedb
kevin@deep-thought:~$ locate ath | grep .ko
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/mathml.css
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/dtd/mathml.dtd
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/entityTables/mathml20.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfont.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfontSTIXNonUnicode.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfontSTIXSize1.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfontStandardSymbolsL.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfontSymbol.properties
/home/kevin/.wine/drive_c/windows/system32/gecko/1.0.0/wine_gecko/res/fonts/mathfontUnicode.properties
/lib/modules/2.6.32-25-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.32-25-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath3k.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath5k.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath9k.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath9k_common.ko
/lib/modules/2.6.32-25-generic/updates/compat-wireless-2.6.34/ath9k_hw.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/bluetooth/ath3k.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/bluetooth/ath3k.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/bluetooth/ath3k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/bluetooth/ath3k.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
/lib/modules/2.6.38-8-generic/net/ath_hal.ko
/lib/modules/2.6.38-8-generic/net/ath_pci.ko
/lib/modules/2.6.38-8-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.38-8-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.38-8-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.38-8-generic/net/ath_rate_sample.ko
/usr/share/gnome/help/gweather/ko
/usr/share/gnome/help/gweather/ko/figures
/usr/share/gnome/help/gweather/ko/gweather.xml
/usr/share/gnome/help/gweather/ko/figures/gweather-details.png
/usr/share/gnome/help/gweather/ko/figures/gweather-menu-prefs.png
/usr/share/gnome/help/gweather/ko/figures/gweather-prefs-general.png
/usr/share/gnome/help/gweather/ko/figures/gweather-prefs-locations.png
/usr/share/gnome/help/gweather/ko/figures/gweather_applet.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-cloudy.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-few-clouds.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-fog.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-night-clear.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-night-few-clouds.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-showers.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-snow.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-storm.png
/usr/share/gnome/help/gweather/ko/figures/stock_weather-sunny.png
/usr/share/omf/gweather/gweather-ko.omf

> 
kevin@deep-thought:~$ cat /etc/modprobe.d/blacklist
#Remove To Install MadWIFI Drivers
blacklist ath5k

#Remove To Install MadWIFI Drivers
blacklist ath9k
blacklist ath5k

> 
kevin@deep-thought:~$ sudo modprobe ath5k
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
kevin@deep-thought:~$ dmesg | grep ath5k
[ 8114.614113] ath5k 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 8114.614131] ath5k 0000:02:00.0: setting latency timer to 64
[ 8114.614212] ath5k 0000:02:00.0: registered as 'phy0'
[ 8115.143405] Registered led device: ath5k-phy0::rx
[ 8115.143449] Registered led device: ath5k-phy0::tx
[ 8115.143465] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)


---

### Post by chili555 on 2011-10-02
I see no evidence of the successful installation of madwifi; ath_pci.ko is nowhere to be found in 2.6.38-11:> /lib/modules/2.6.38-11-generic/kernel/drivers/bluetooth/ath3k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/md/multipath.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ar9170/ar9170usb.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
/lib/modules/2.6.38-11-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.koTherefor, ath5k is the only reasonable driver. Let's remove the blacklist:```
sudo rm /etc/modprobe.d/blacklist
```Now, let's try another experiment:```
sudo rmmod -f hp-wmi
sudo rfkill unblock all
rfkill list all
```If this brings your wireless to life, we'll need to blacklist hp-wmi.

---

### Post by Naturally-Simple on 2011-10-02
Ok, I followed what you asked me to do:

> 
kevin@deep-thought:~$ sudo rm /etc/modprobe.d/blacklist
kevin@deep-thought:~$ sudo rmmod -f hp-wmi
kevin@deep-thought:~$ rfkill unblock all
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

I toggled the physical switch, but nothing. When I click on my network connections, I now see something different. It now has a greyed out "Wireless Networks" and also greyed out "wireless is disabled by hardware switch" and again a repeat greyed out "Enable Wireless".

Obviously my hardware switch is blocked. I recall the last time that all I did was push the physical button to make this change, but that solution doesn't seem to be working now.

---

### Post by chili555 on 2011-10-02
Evidently not.

I worked on a case a few weeks ago where the poster found that hp-wmi mapped the Alt+F12 key to wireless on his laptop instead of Fn+F12. Would you please reload hp-wmi:```
sudo modprobe hp-wmi
```Then try some other key combinations, not just Alt but Ctrl and all the F keys. After each trial, run:```
rfkill list all
```See if we can find the magic combination.

---

### Post by Naturally-Simple on 2011-10-02
Ha, so I went through the combinations of Alt+F__ and then Ctrl+F__ and after it suspended my computer on Ctrl+F5, I logged back in, and the physical toggle switch for my wireless changed from blue (as it has been this whole time) to orange. Intrigued by this, I looked at "rfkill list all" but it showed me the same:
> 
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

The funny thing is that now when I push my wireless button, the colour stays orange, but "rfkill list all" shows me this:
> 
kevin@deep-thought:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
2: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

I've repeated it a few times, and it keeps working like this, unblocking the hp-wifi. My Networks Connections still tells me, however, that the wireless is disabled by hardware switch.

---

### Post by Djesurun1 on 2012-02-20
Chili, I've seen your name on several other posts that I have been looking into so that I can fix my problem. Hopefully you can help me here too! I have the same ath5k driver for my netgear WG311T wireless card. I can see my network but it keeps asking for my password. I am very new to linux and i have tried so many different commands that i have read in the forums but still It wont connect to my network. I have changed to network security from WPA1 and WPA 2, to every available option on my AT&T Uverse router (including no security) and still it will not work. I have a working ethernet card so i have made all of the available updates through update manager. I don't know what else to try! 

Here are some responses to the common commands Ive read. 

djesurun1@djesurunlinux:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux djesurunlinux 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 athlon i386 GNU/Linux

djesurun1@djesurunlinux:~$ lspci -nnk | grep -iA2 net
02:07.0 Ethernet controller [0200]: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
    Subsystem: Netgear WG311T 108 Mbps Wireless PCI Adapter (rev.A2) [1385:4d00]
    Kernel driver in use: ath5k
    Kernel modules: ath5k
02:08.0 Ethernet controller [0200]: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 [1317:0985] (rev 11)
    Subsystem: ADMtek Device [1317:0574]
    Kernel driver in use: tulip
--
02:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard [1458:e000]
    Kernel driver in use: 8139too

djesurun1@djesurunlinux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

djesurun1@djesurunlinux:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

djesurun1@djesurunlinux:~$ lsmod
Module                  Size  Used by
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
nvidia               7098131  24 
arc4                   12473  2 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
k8temp                 12905  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172427  3 ath5k,ath,mac80211
soundcore              12600  1 snd
i2c_ali15x3            12878  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
i2c_ali1535            12777  0 
i2c_ali1563            12850  0 
ns558                  12654  0 
binfmt_misc            17292  1 
gameport               15060  2 ns558
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
tulip                  52487  0 
sata_uli               12693  0 
pata_ali               13562  2 
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0

---

### Post by chili555 on 2012-02-20
How is your security set now? WPA2 *only* is preferred; not the tricky mixed WPA and WPA2 mode:```
sudo iwlist wlan0 scan
```Reset the router to WPA2 only if it's not already. What does Network Manager have to say about this while you are trying to connect?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by Djesurun1 on 2012-02-20
Thanks chili!

Ok, i am set on the WEP2 only. I had read that before so I made that change already.
 Here is the response to your commands

djesurun1@djesurunlinux:~$ sudo iwlist wlan0 scan
[sudo] password for djesurun1: 
wlan0     No scan results

The second command prompted a VERY long response...here you go!


djesurun1@djesurunlinux:~$ sudo iwlist wlan0 scan
[sudo] password for djesurun1: 
wlan0     No scan results

djesurun1@djesurunlinux:~$ sudo cat /var/log/syslog | grep etwork 
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) starting connection 'Jesurun'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): access point 'Jesurun' has security, but secrets are required.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 09:20:00 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Feb 20 09:21:00 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 09:21:00 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:21:00 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 09:21:00 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:21:00 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:21:04 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <warn> No agents were available for this request.
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed for access point (Jesurun)
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> Marking connection 'Jesurun' invalid.
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed.
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 09:21:08 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) starting connection 'Jesurun'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): access point 'Jesurun' has security, but secrets are required.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 09:23:34 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 09:24:34 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 09:24:34 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:24:34 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 09:24:34 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:24:34 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:24:38 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 09:24:53 djesurunlinux NetworkManager[509]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 09:24:54 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 09:25:53 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 09:25:53 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:25:53 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 09:25:53 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:25:53 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:25:57 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <warn> No agents were available for this request.
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed for access point (Jesurun)
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> Marking connection 'Jesurun' invalid.
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed.
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 09:27:53 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) starting connection 'Jesurun'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): access point 'Jesurun' has security, but secrets are required.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 09:29:33 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 09:30:33 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 09:30:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 09:30:33 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 09:30:33 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:30:33 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 09:30:37 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <warn> No agents were available for this request.
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed for access point (Jesurun)
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> Marking connection 'Jesurun' invalid.
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed.
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 09:32:33 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) starting connection 'Jesurun'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): access point 'Jesurun' has security, but secrets are required.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 10:06:09 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 10:06:10 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 10:07:09 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 10:07:09 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 10:07:09 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 10:07:09 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:07:09 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:07:13 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0/wireless): connection 'Jesurun' has security, and secrets exist.  No new secrets needed.
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'ssid' value 'Jesurun'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'scan_ssid' value '1'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> No agents were available for this request.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed for access point (Jesurun)
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Marking connection 'Jesurun' invalid.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
djesurun1@djesurunlinux:~$ sudo cat /var/log/syslog | grep etwork | tail n-20
tail: cannot open `n-20' for reading: No such file or directory
djesurun1@djesurunlinux:~$ sudo cat /var/log/syslog | grep etwork | tail -m20
tail: invalid option -- 'm'
Try `tail --help' for more information.
djesurun1@djesurunlinux:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'auth_alg' value 'OPEN'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: added 'psk' value '<omitted>'
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> Config: set interface ap_scan to 1
Feb 20 10:07:16 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: inactive -> scanning
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): association took too long.
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0/wireless): asking for new secrets
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:08:16 djesurunlinux NetworkManager[509]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: scanning -> inactive
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> No agents were available for this request.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed for access point (Jesurun)
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Marking connection 'Jesurun' invalid.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <warn> Activation (wlan0) failed.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'none') [0]
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
Feb 20 10:08:20 djesurunlinux NetworkManager[509]: <info> Policy set 'Wired connection 1' (eth1) as default for IPv4 routing and DNS.
djesurun1@djesurunlinux:~$

---

### Post by chili555 on 2012-02-20
When you add the last part, as I asked:> sudo cat /var/log/syslog | grep etwork [COLOR="Red"]| tail -n20[/COLOR]Then you limit the output to twenty lines and probably omit all the repeats.

Let's try another approach:```
sudo modprobe -r ath5k
sudo modprobe ath5k nohwcrypt=1
sudo cat /var/log/syslog | grep etwork | tail -n20
```Let's also try again:```
sudo iwlist wlan0 scan
```

---

### Post by Djesurun1 on 2012-02-20
Ok here goes. I had the tail -n20 on that last command but i must have had a mistake somewhere. This is the first set of commands:

       
    
                                                             djesurun1@djesurunlinux:~$ sudo modprobe -r ath5k
[sudo] password for djesurun1: 

djesurun1@djesurunlinux:~$ sudo modprobe ath5k nohwcrypt=1

djesurun1@djesurunlinux:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Feb 20 13:57:32 djesurunlinux NetworkManager[509]: <info> (wlan0): now unmanaged
Feb 20 13:57:32 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: disconnected -> unmanaged (reason 'removed') [30 10 36]
Feb 20 13:57:32 djesurunlinux NetworkManager[509]: <info> (wlan0): cleaning up...
Feb 20 13:57:32 djesurunlinux NetworkManager[509]: nm_system_iface_is_up: assertion `iface != NULL' failed
Feb 20 13:57:32 djesurunlinux NetworkManager[509]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/net/wlan0, iface: wlan0)
Feb 20 13:57:32 djesurunlinux NetworkManager[509]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/ieee80211/phy0/rfkill0 disappeared
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/ieee80211/phy0/rfkill1) (driver (unknown))
Feb 20 13:57:56 djesurunlinux NetworkManager[509]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/net/wlan0, iface: wlan0)
Feb 20 13:57:56 djesurunlinux NetworkManager[509]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): new 802.11 WiFi device (driver: 'ath5k' ifindex: 5)
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): now managed
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): bringing up device.
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): preparing device.
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): deactivating device (reason 'managed') [2]
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: starting -> ready
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> (wlan0): supplicant interface state: ready -> inactive


And finally the last:


djesurun1@djesurunlinux:~$ sudo iwlist wlan0 scan
wlan0     No scan results

---

### Post by Djesurun1 on 2012-02-20
Ooops i lied.....I did leave tail -n20 off lol. guess that was obvious!

---

### Post by chili555 on 2012-02-20
This is pretty wierd:> Feb 20 13:57:32 djesurunlinux NetworkManager[509]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/ieee80211/phy0/[COLOR="Red"]rfkill0 disappeared[/COLOR]
Feb 20 13:57:56 djesurunlinux NetworkManager[509]: <info> [COLOR="Red"]found WiFi radio killswitch rfkill**1**[/COLOR] (at /sys/devices/pci0000:00/0000:00:02.0/0000:02:07.0/ieee80211/phy0/rfkill1) (driver (unknown))And so is this:> djesurun1@djesurunlinux:~$ sudo iwlist wlan0 scan
wlan0 No scan results With the ethernet disconnected, please reboot and run:```
dmesg > djes_dmesg.txt
rfkill list all >> djes_dmesg.txt

```In your home directory, you will find a text document called djes_dmesg.txt. Please attach it to your reply using the paperclip tool in the reply box. Thanks.

---

### Post by Djesurun1 on 2012-02-21
I wish i knew what any of this meant! I got a good book on linux commands im about to start reading up on though =) I love to learn! Thank you again for your time...That is one thing that is so impressive about the linux community!


Ok..Ive tried so many different ways to separate this up but it is too large to upload into the forum. It is 64kb but it only lets me upload 15kb per doc. Is there another way to send it to you?

---

### Post by Djesurun1 on 2012-02-21
there...whew i got them all to fit!

---

### Post by chili555 on 2012-02-21
Try this:```
zip djes_dmesg.zip djes_dmesg.txt
```Now the zipped file will be easily within the limitations of the forum. I'm sorry I didn't suspect that from the start.

dmesg is a listing of kernel bootup messages. Since you are running it after a clean boot, it will be unaffected by any commands, key presses, the earth's magnetic resonance (just kidding), etc. A more experienced eye can look for errors or warnings and hopefully we can find out what to fix.

rfkill just tells us the state of the wireless key combination or physical switch. In some cases, there is a small module that reads the key presses and then turns the wireless and/or bluetooth on and off. These little modules mostly work perfectly; sometimes not.

Oops, I missed your reply. Thanks.

---

### Post by Djesurun1 on 2012-02-21
That makes sense...the magnetic field does all kinds of things to my network lol. Did you still want that zip file? I'm at work but I can get right on that this evening.

---

### Post by chili555 on 2012-02-21
I see some very interesting things that may or may not have much to do with wireless. First, this:> [    0.121429] ACPI: PCI Interrupt Link [LNK1] (IRQs 1 3 4 5 6 7 10 11 12 14 15) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.121592] ACPI: PCI Interrupt Link [LNK2] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
[    0.121824] ACPI: PCI Interrupt Link [LNK3] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[    0.122053] ACPI: PCI Interrupt Link [LNK4] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
[    0.122284] ACPI: PCI Interrupt Link [LNK5] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.122515] ACPI: PCI Interrupt Link [LNK6] (IRQs 1 3 4 5 6 7 10 11 *12 14 15)
[    0.122745] ACPI: PCI Interrupt Link [LNK7] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
[    0.122905] ACPI: PCI Interrupt Link [LNK8] (IRQs 1 3 4 5 6 7 10 11 12 14 15) [COLOR="Red"]*0, disabled.[/COLOR]
[    0.123070] ACPI: PCI Interrupt Link [LNK9] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)How are IRQs set up in the computer's BIOS? I have the best luck with Auto Select and not manually allocating IRQs. Next, this:> [    6.965148] ata1.00: failed command: READ DMA
[    6.965155] ata1.00: cmd c8/00:08:40:03:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[    6.965157]          res 51/84:00:47:03:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[    6.965160] ata1.00: status: { [COLOR="Red"]DRDY ERR[/COLOR] }
[    6.965163] ata1.00: error: { ICRC ABRT }
[    6.965179] ata1: soft resetting link
[    7.224442] ata1.00: configured for UDMA/66
[    7.240289] ata1.01: configured for UDMA/66
[    7.240294] ata1: EH completeThis repeats three times. This link doesn't look good: [http://www.linuxquestions.org/questions/linux-newbie-8/ata1-01-status-%7B-drdy-err-%7D-896401/](http://www.linuxquestions.org/questions/linux-newbie-8/ata1-01-status-%7B-drdy-err-%7D-896401/)> Those certainly look like drive hardware failure errors to me. I think we ought to find out if ata1:00 is your CDROM (not so bad) or your harddrive (very bad). I'm working on that now.

Next, this:> [    7.804348] Buffer I/O error on device sda, logical block 832
[    7.804351] Buffer I/O error on device sda, logical block 833
[    7.804354] Buffer I/O error on device sda, logical block 834
[    7.804357] Buffer I/O error on device sda, logical block 835
[    7.804359] Buffer I/O error on device sda, logical block 836
[    7.804362] Buffer I/O error on device sda, logical block 837
[    7.804365] Buffer I/O error on device sda, logical block 838
[    7.804368] Buffer I/O error on device sda, logical block 839
[    7.804378] ata1: EH complete
[    8.399711] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    8.399719] EXT4-fs (sda1): write access will be enabled during recovery
[    9.278829] EXT4-fs (sda1): orphan cleanup on readonly fs
[    9.278849] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1312019
[    9.278941] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1311540
[    9.278955] EXT4-fs (sda1): 2 orphan inodes deleted
[    9.278958] EXT4-fs (sda1): recovery completesda1 is a partition on your harddrive. While errors were found, the system recovered. You might see if the previous boot reported the same thing:```
sudo cat /var/log/dmesg.0 | grep -i err
```This may be helpful: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530649](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530649)> I had a physical port on my sata bus which was dying. I moved the drive to another port and I no longer receive these error notifications.

---

### Post by chili555 on 2012-02-21
> **Djesurun1 said:**
> That makes sense...the magnetic field does all kinds of things to my network lol. Did you still want that zip file? I'm at work but I can get right on that this evening.Nope. I stitched them all back together. Please see my reply above.

---

### Post by Djesurun1 on 2012-02-21
I think I have an explanation for that, one of my cd drives gets power but doesn't function. It opens closes and spins but never reads the disk. I'll try to just disconnect it and see if that gets rid if the message tonight.

---

### Post by Djesurun1 on 2012-02-23
Sorry its been a while since i logged in but heres an update. I am on the Internet wireless =) I bought a new wireless network card and it just simply connected. Guess maybe my old one is no good?  Anyways thank you SO much more the advice and time. By the way my old card was a Netgear WG311T PCI and the new one was a usb Belkin N150 $20 at walmart lol.

---

### Post by amancarlos on 2012-08-11
try installing **madwifi**, here's a guide:
[http://ubuntucrack.blogspot.in/2010_07_18_archive.html](http://ubuntucrack.blogspot.in/2010_07_18_archive.html)

---

