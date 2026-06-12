---
title: "Peculiar wireless problem"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by groovedspines on 2013-06-03
Hi folks! I've been searching and trying multiple fixes for my wifi problems, but I still haven't found a solution.

Here's the funny part, though: This problem only occurs at one wifi location, and only since I replaced windows with linux.

I'm typing this post from the local library, it has a WPA password, as does my wifi at home, as well as at my father's house.
My initial conclusion was that the wireless must have some issue with the fact that the cafe has no password required, yet I can use pretty much any other password-less hotspot *except* [I]this location. 

[/I]The behavior is as follows: I turn on the laptop at the cafe (or resume from suspend if it was on earlier), do some browsing for 10-15 minutes, and then the connection stops working. The laptop is convinced that it is connected to the router, but has no result. Later, there's the usual endless reconnecting I'm sure plenty of you have experienced with wifi issues. 

Restarting will allow me to use the net for another 10-15 minutes before it disconnects me yet again. 

Does anyone have an idea as to what exactly is going on? I'm pretty lost as to what's going on specifically with this router at my study spot.

---

### Post by chili555 on 2013-06-03
Do I *know* what's going on? Nope. Do I have a hunch? You betcha. Let's look for clues. Let it run for a while and die and then run:```
dmesg | grep 80211
```Does either cfg80211 or mac80211 have any complaints about probe response? If so, we can write a fix. If not, what is the complaint and let's see what we can do.

-----

Reference:```
chili@Think410:~$ modinfo mac80211
filename:       /lib/modules/3.8.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D743988E247C2BAE9F32AA
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-23-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
[COLOR="#FF0000"]parm:           probe_wait_ms[/COLOR]:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

```

---

### Post by groovedspines on 2013-06-04
Hello! Here are the results of running those commands:

```
[   12.382131] cfg80211: Calling CRDA to update world regulatory domain
[   12.798643] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.457372] cfg80211: World regulatory domain updated:
[   13.457377] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.457379] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.457381] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.457383] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.457385] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.457387] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.458814] cfg80211: Calling CRDA for country: EC
[   13.463221] cfg80211: Regulatory domain changed to country: EC
[   13.463225] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.463228] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.463230] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   13.463232] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   13.463234] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   14.580211] [drm] fb mappable at 0x80142000
[   18.426481] cfg80211: Calling CRDA for country: US
[   18.441440] cfg80211: Regulatory domain changed to country: US
[   18.441446] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.441448] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   18.441451] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   18.441453] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.441454] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.441456] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.441458] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)

```

```

daniel@meridian:~$ modinfo mac80211
filename:       /lib/modules/3.8.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D743988E247C2BAE9F32AA
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-23-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


```

thank you for your help! I'll do some non-internet stuff for school while I'm here.

EDIT: I did a quick search at one of the lines (calling CRDA...etc) and possibly I have the same issue as another google search has presented me. With any luck I'll load enough pages to fix it before my connection drops! One can only hope.

---

### Post by groovedspines on 2013-06-04
I can temporarily get access to the wifi for another 5-10 minutes by running the following commands from your post in [Problem with World Regulatory domain]("http://ubuntuforums.org/showthread.php?t=2045604") :

```


sudo modprobe -r <wireless_driver> 
sudo modprobe -r cfg80211 
sudo modprobe cfg80211 ieee80211_regdom=US 
sudo modprobe <wireless_driver>

```

Sometimes I wish I had a linux command line survival guide so I'd know what commands to use instead of throwing up my hands and restarting.

EDIT: the first time I ran these commands it only worked for 5-10 minutes. Currently, I'm still connected to the net after trying the commands again at the problematic hotspot. Will check back in an hour to see if it's still working.

---

### Post by groovedspines on 2013-06-04
Well, I just had to run those commands again to get the net back, but it had been working for over an hour or so this time, so it was certainly an improvement!

I redid your two commands to see what the system says is going on. It's significantly longer this time for some reason:

```
daniel@meridian:~$ dmesg | grep 80211
[   12.709207] cfg80211: Calling CRDA to update world regulatory domain
[   13.438283] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.608768] cfg80211: World regulatory domain updated:
[   13.608773] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.608776] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.608778] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.608780] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.608781] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.608783] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.608796] cfg80211: Calling CRDA for country: EC
[   13.658603] cfg80211: Regulatory domain changed to country: EC
[   13.658607] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.658610] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   13.658612] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   13.658614] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   13.658616] cfg80211:   (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   18.787220] cfg80211: Calling CRDA for country: US
[   18.791758] cfg80211: Regulatory domain changed to country: US
[   18.791763] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.791765] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   18.791767] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   18.791769] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.791771] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.791773] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.791775] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  638.176991] cfg80211: Calling CRDA to update world regulatory domain
[  638.187640] cfg80211: World regulatory domain updated:
[  638.187646] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  638.187648] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  638.187651] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  638.187653] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  638.187654] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  638.187656] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.049684] cfg80211: Calling CRDA to update world regulatory domain
[  667.057681] cfg80211: World regulatory domain updated:
[  667.057686] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  667.057689] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.057691] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  667.057693] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  667.057694] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.057696] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.057717] cfg80211: Calling CRDA for country: US
[  667.067638] cfg80211: Regulatory domain changed to country: US
[  667.067643] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  667.067645] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  667.067648] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  667.067650] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.067651] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.067653] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  667.067655] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[  675.979153] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  678.487885] cfg80211: Calling CRDA for country: US
[  678.503996] cfg80211: Regulatory domain changed to country: US
[  678.504001] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  678.504004] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[  678.504006] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[  678.504008] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  678.504009] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  678.504011] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  678.504013] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1017.129594] cfg80211: Calling CRDA to update world regulatory domain
[ 1017.135989] cfg80211: World regulatory domain updated:
[ 1017.135994] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1017.135996] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.135999] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1017.136001] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1017.136002] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.136004] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.136025] cfg80211: Calling CRDA for country: US
[ 1017.146725] cfg80211: Regulatory domain changed to country: US
[ 1017.146729] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1017.146732] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1017.146734] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1017.146736] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.146738] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.146739] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.146741] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1017.301555] cfg80211: Calling CRDA to update world regulatory domain
[ 1017.308405] cfg80211: World regulatory domain updated:
[ 1017.308409] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1017.308412] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.308414] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1017.308416] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1017.308418] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.308420] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.308458] cfg80211: Calling CRDA for country: US
[ 1017.330276] cfg80211: Regulatory domain changed to country: US
[ 1017.330281] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1017.330284] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1017.330286] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1017.330287] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.330289] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.330291] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1017.330293] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[ 1829.992062] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1853.212382] cfg80211: Calling CRDA for country: US
[ 1853.218223] cfg80211: Regulatory domain changed to country: US
[ 1853.218228] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1853.218230] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[ 1853.218233] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[ 1853.218235] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1853.218236] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1853.218238] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1853.218240] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)


```

and also 

```
daniel@meridian:~$ modinfo mac80211
filename:       /lib/modules/3.8.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     0D743988E247C2BAE9F32AA
depends:        cfg80211
intree:         Y
vermagic:       3.8.0-23-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


```

So...if I'm understanding the above messages correctly..my region keeps being set to EC, which is Ecuador, if I'm not mistaken. That makes some sort of sense since the owners of the cafe all speak spanish, though it's kinda cool that they might've brought a router from home when they set up shop. So, when they call for this to be updated to Ecuador or the US, it's not updating and instead remaining blank?

I apologize if my logic is flawed. This is certainly a rather interesting problem!

Edit: the net is back to being unstable once again at this hotspot. How perplexing! alright, I believe I've collected enough data here and need to do some online class things so I'll be leaving here. Is there anything else I should search for, beyond the CRDA thing?

---

### Post by chili555 on 2013-06-04
We don't really see any evidence of the wireless dropping and reconnecting. You might look a bit deeper, after it drops:```
cat /var/log/syslog | grep wlan | tail -n20
```We can also set the regulatory domain explicitly by an edit:```
gksudo gedit /etc/rc.local
```Right above exit 0, add one line:```
iw reg set US
```Proofread carefully, save and close gedit. Upon reboot, the new parameter will be set automatically.

Get the parameter to have immediate effect without a reboot:```
sudo iw reg set US
```As they say, the plot thickens!

---

### Post by groovedspines on 2013-06-06
Hi again, I'm here and ready to test this once the net goes down!

Just leaving this message to let you know that I haven't forgotten this thread! Just couldn't get to the cafe till today!

---

### Post by chili555 on 2013-06-06
> **groovedspines said:**
> Hi again, I'm here and ready to test this once the net goes down!

Just leaving this message to let you know that I haven't forgotten this thread! Just couldn't get to the cafe till today!I'm looking forward to your report. Mrs. Chili says 'peculiar' is my middle name.

---

### Post by groovedspines on 2013-06-07
Alrighty! Here's a paste of the result from the cat command you had me do:

```
Jun  6 21:55:03 meridian kernel: [ 5398.320755] wlan0: associate with 06:25:bc:8c:1e:27 (try 1/3)
Jun  6 21:55:03 meridian kernel: [ 5398.323697] wlan0: RX AssocResp from 06:25:bc:8c:1e:27 (capab=0x1421 status=0 aid=6)
Jun  6 21:55:03 meridian kernel: [ 5398.324711] wlan0: associated
Jun  6 21:55:03 meridian wpa_supplicant[1133]: wlan0: Associated with 06:25:bc:8c:1e:27
Jun  6 21:55:03 meridian wpa_supplicant[1133]: wlan0: CTRL-EVENT-CONNECTED - Connection to 06:25:bc:8c:1e:27 completed (reauth) [id=0 id_str=]
Jun  6 21:55:03 meridian NetworkManager[896]: <info> (wlan0): supplicant interface state: associating -> completed
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'berkeleyespresso'.
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun  6 21:55:03 meridian NetworkManager[896]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jun  6 21:55:03 meridian avahi-daemon[841]: Withdrawing address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.
Jun  6 21:55:03 meridian avahi-daemon[841]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun  6 21:55:03 meridian avahi-daemon[841]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun  6 21:55:03 meridian NetworkManager[896]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun  6 21:55:03 meridian NetworkManager[896]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun  6 21:55:03 meridian dhclient: Listening on LPF/wlan0/70:f1:a1:c1:6e:b1
Jun  6 21:55:03 meridian dhclient: Sending on   LPF/wlan0/70:f1:a1:c1:6e:b1
Jun  6 21:55:03 meridian dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x7983aaad)

```

---

### Post by chili555 on 2013-06-07
It looks like it connected perfectly; yes?

---

### Post by groovedspines on 2013-06-07
> **chili555 said:**
> It looks like it connected perfectly; yes?

In a world where technology worked consistently and made perfect sense to the average user it might!

Here's what actually happens at the cafe 99% of the time:

1. Use internet for a while, asymptomatic.
2. After 5-10 min usually, the top right of the screen will indicate that I am by all means connected to the router (berkeleyespresso)
3. Symptoms begin: Internet stops working (pages will remain stuck on "loading..." and never resolve)
4. At first, all indications on the GUI will say that I'm connected to the router. Sometimes, after a while, it will disconnect and try to reconnect indefinitely, being unable to for some unexplainable reason. 
5. I can also force #4 to happen after the internet stops working by manually telling the computer to reconnect to the router. 

When I ran the cat command, that was after it was disconnecting and reconnecting indefinitely. 

for the record, I'm running Xubuntu 13.04, but I've had the same issue with Ubuntu 12.04 LTS/13.04.

It could just be a quirk of my hardware, perhaps? I have a Compaq Presario CQ62-231NR laptop. I'm not going to pretend that technology always makes sense, I've had too many weird problems to try to fix to believe that. I was considering installing Lubuntu 13.04 since it claims to be the one made for older/lower hardware, I hadn't known about it when I installed xubuntu. I could attempt that to see if there was any difference, though since it's also an ubuntu variant, i'd probably just get better battery life. 

Ah, what a strange problem indeed!


EDIT: There is also apparently a password-protected router in the same building with the same name. This could perhaps lead to conflict?

I'm more than happy to try the commands you gave me earlier again after forcing a disconnect to see if I can get different results, if you've got nothing to work with.

Have a wonderful day!

---

### Post by chili555 on 2013-06-07
> EDIT: There is also apparently a password-protected router in the same building with the same name. This could perhaps lead to conflict?It is, as they say in the movies, a usual suspect. Network Manager often tries to roam to an apparently 'better' access point often resulting in a drop and failuah to commun'cate. If you grep the syslog for network (i.e. Network Manager) you can often see the process unfolding as the MAC address changes; something roughly like:

wlan0: Trying to associate with xx:d7:19:41:54:[COLOR="#FF0000"]ef[/COLOR] (SSID='myrouter' freq=5745 MHz)
wlan0: Trying to associate with xx:d7:19:41:54:[COLOR="#FF0000"]ab[/COLOR] (SSID='myrouter' freq=5745 MHz)

Do you see anything like that?

You can ask Network Manager to stick to the desired access point by specifying its MAC in the BSSID box as in the attached. Find out the MAC with a scan:```
sudo iwlist wlan0 scan
```> wlan0     Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]xx:D7:19:41:54:EF[/COLOR]
                    Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"myrouter"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
          <snip>


---

### Post by groovedspines on 2013-06-09
> **chili555 said:**
> It is, as they say in the movies, a usual suspect. Network Manager often tries to roam to an apparently 'better' access point often resulting in a drop and failuah to commun'cate. If you grep the syslog for network (i.e. Network Manager) you can often see the process unfolding as the MAC address changes; something roughly like:

wlan0: Trying to associate with xx:d7:19:41:54:[COLOR=#FF0000]ef[/COLOR] (SSID='myrouter' freq=5745 MHz)
wlan0: Trying to associate with xx:d7:19:41:54:[COLOR=#FF0000]ab[/COLOR] (SSID='myrouter' freq=5745 MHz)

Do you see anything like that?

Apparently it says the same MAC address?

Here's the relevant results from the scan command!

This is the desired router to connect to (the one without a required password)

```
wlan0     Scan completed :
          Cell 01 - Address: 06:25:BC:8C:1E:27
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"berkeleyespresso"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000030c468f1
                    Extra: Last beacon: 249880ms ago
                    IE: Unknown: 00106265726B656C6579657370726573736F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0208
                    IE: Unknown: DD0E0017F207000101060025BC8C1E28
         
```

 This is the undesired one, the one that requires a password. Apparently, I already had put the MAC address in my network settings to connect to it, but the MAC address is the same!
```

Cell 02 - Address: 00:25:BC:8C:1E:27
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"berkespresso's Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000003fa5f81d
                    Extra: Last beacon: 272ms ago
                    IE: Unknown: 00166265726B657370726573736F2773204E6574776F726B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 33027E9D
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016C0320
                    IE: Unknown: DD0E0017F207000101060025BC8C1E28
                    IE: Unknown: DD0B0017F20100010100000007

```

---

### Post by chili555 on 2013-06-09
> but the MAC address is the same!Not quite, but maybe there's a typo here. Didn't you do a straight copy and paste?> wlan0     Scan completed :
          Cell 01 - Address: [COLOR="#FF0000"]06[/COLOR]:25:BC:8C:1E:27
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    [COLOR="#FF0000"]Encryption key:off[/COLOR]
                    ESSID:"berkeleyespresso"...and then:> Cell 02 - Address: [COLOR="#FF0000"]00[/COLOR]:25:BC:8C:1E:27
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    [COLOR="#FF0000"]Encryption key:on[/COLOR]
                    ESSID:"berkespresso's Network"Also, it appears the SSID is different.

---

### Post by groovedspines on 2013-06-10
My apologies for not noticing that!

I had entered the MAC address of the desired access point (SSID berkeleyespresso BSSID [COLOR=#FF0000]06[/COLOR]:25:BC:8C:1E:27), though sadly to no change. 

Other settings I have:
General: Automatically connect. All users can connect to this network.
Wifi: Mode: infrastructure. Entered the BSSID and SSID. MTU set to automatic
Wifi security: none.
IPv4: Method Automatic(DHCP)
IPv6: Method Automatic (DHCP only) <-- This was a recent change just to see if it would make a difference. Was originally set to automatic(DHCP).

---

### Post by chili555 on 2013-06-10
> IPv6: Method Automatic (DHCP only) <-- This was a recent change just to see if it would make a difference. Was originally set to automatic(DHCP). You might also try 'Ignore.'

Let's see what the logs say about this peculiar problem:```
cat /var/log/syslog | grep wlan | tail -n20
```Obviously, as it tries to connect to berkeleyespresso and either fails or drops.

---

### Post by groovedspines on 2013-06-12
Hi again, reporting in at the cafe thus far - 

At first, I lost  my connection rather quickly, but after disconnecting, changing the ipv6  setting to 'ignore', I am still on the net after 10 minutes! This may  have been all that was required, but I'll keep trying for a couple hours  while I'm here to see if it's consistent.

---

### Post by groovedspines on 2013-06-12
Sadly, it was not to last. I have run your command multiple times from different states:

When the net has gone down, but the system reports no problem (other than that you can't connect to anything). 
```

Jun 12 19:31:05 meridian dhclient: DHCPREQUEST of 172.16.42.133 on wlan0 to 172.16.42.1 port 67 (xid=0x6a2fbfc8)
Jun 12 19:31:05 meridian NetworkManager[893]: <info> (wlan0): DHCPv4 state changed reboot -> renew

```

When I force the issue to happen by trying to reconnect to what i'm supposedly connected to. 
```

daniel@meridian:~$ cat /var/log/syslog | grep wlan | tail -n20
Jun 12 19:45:57 meridian NetworkManager[893]: <info> (wlan0): deactivating device (reason 'none') [0]
Jun 12 19:45:57 meridian NetworkManager[893]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 4563
Jun 12 19:45:57 meridian avahi-daemon[809]: Withdrawing address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.
Jun 12 19:45:57 meridian avahi-daemon[809]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:45:57 meridian avahi-daemon[809]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 12 19:45:57 meridian avahi-daemon[809]: Withdrawing address record for 172.16.42.133 on wlan0.
Jun 12 19:45:57 meridian avahi-daemon[809]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 172.16.42.133.
Jun 12 19:45:57 meridian avahi-daemon[809]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jun 12 19:45:57 meridian kernel: [ 7129.260598] wlan0: deauthenticating from 06:25:bc:8c:1e:27 by local choice (reason=3)
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) starting connection 'berkeleyespresso'
Jun 12 19:45:57 meridian NetworkManager[893]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 12 19:45:57 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 12 19:45:57 meridian NetworkManager[893]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 12 19:45:58 meridian avahi-daemon[809]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:45:58 meridian avahi-daemon[809]: New relevant interface wlan0.IPv6 for mDNS.
Jun 12 19:45:58 meridian avahi-daemon[809]: Registering new address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.*.
daniel@meridian:~$ cat /var/log/syslog | grep wlan | tail -n20
Jun 12 19:46:24 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 12 19:46:24 meridian NetworkManager[893]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 12 19:46:24 meridian NetworkManager[893]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 12 19:46:24 meridian avahi-daemon[809]: Withdrawing address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.
Jun 12 19:46:24 meridian avahi-daemon[809]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:46:24 meridian avahi-daemon[809]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 12 19:46:24 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 12 19:46:24 meridian NetworkManager[893]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 12 19:46:24 meridian dhclient: Listening on LPF/wlan0/70:f1:a1:c1:6e:b1
Jun 12 19:46:24 meridian dhclient: Sending on   LPF/wlan0/70:f1:a1:c1:6e:b1
Jun 12 19:46:24 meridian dhclient: DHCPREQUEST of 172.16.42.133 on wlan0 to 255.255.255.255 port 67 (xid=0x3baab1fa)
Jun 12 19:46:25 meridian avahi-daemon[809]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:46:25 meridian avahi-daemon[809]: New relevant interface wlan0.IPv6 for mDNS.
Jun 12 19:46:25 meridian avahi-daemon[809]: Registering new address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.*.
Jun 12 19:46:27 meridian dhclient: DHCPREQUEST of 172.16.42.133 on wlan0 to 255.255.255.255 port 67 (xid=0x3baab1fa)
Jun 12 19:46:34 meridian dhclient: DHCPREQUEST of 172.16.42.133 on wlan0 to 255.255.255.255 port 67 (xid=0x3baab1fa)
Jun 12 19:46:44 meridian dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x77f43d00)
Jun 12 19:46:47 meridian dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6 (xid=0x77f43d00)
Jun 12 19:46:53 meridian dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8 (xid=0x77f43d00)
Jun 12 19:47:01 meridian dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18 (xid=0x77f43d00)
daniel@meridian:~$ cat /var/log/syslog | grep wlan | tail -n20
Jun 12 19:47:09 meridian avahi-daemon[809]: Withdrawing address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.
Jun 12 19:47:09 meridian avahi-daemon[809]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:47:09 meridian avahi-daemon[809]: Interface wlan0.IPv6 no longer relevant for mDNS.
Jun 12 19:47:09 meridian kernel: [ 7201.537027] wlan0: deauthenticating from 06:25:bc:8c:1e:27 by local choice (reason=3)
Jun 12 19:47:09 meridian NetworkManager[893]: <info> (wlan0): supplicant interface state: completed -> disconnected
Jun 12 19:47:09 meridian wpa_supplicant[985]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Jun 12 19:47:11 meridian avahi-daemon[809]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::72f1:a1ff:fec1:6eb1.
Jun 12 19:47:11 meridian avahi-daemon[809]: New relevant interface wlan0.IPv6 for mDNS.
Jun 12 19:47:11 meridian avahi-daemon[809]: Registering new address record for fe80::72f1:a1ff:fec1:6eb1 on wlan0.*.
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) starting connection 'berkeleyespresso'
Jun 12 19:47:12 meridian NetworkManager[893]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 12 19:47:12 meridian NetworkManager[893]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0/wireless): connection 'berkeleyespresso' requires no security.  No secrets needed.
Jun 12 19:47:12 meridian NetworkManager[893]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 12 19:47:15 meridian NetworkManager[893]: <info> (wlan0): supplicant interface state: disconnected -> scanning

```

---

