---
title: "Wireless wont show on 8.10 upgrade"
date: 2009-02-13
forum: Networking &amp; Wireless
---

### Post by jsacks on 2009-02-13
Hi, I recently upgraded to Ubuntu 8.10 and my wireless doesnt seem to show at all.  I can't detect any wireless points.

I've got Dell 1330 which is and Intel 3945 wireless card.  Online it suggests i install linux-backports-modules-intrepid through the package manager - i did that but still nothing works. 

Someone told me to try these key combinations: *Normally FN plus something will enable / disable wireless. For me it's FN + F5. * Didnt help.

I also tried the wireless switch on the right side of my computer.  That doesnt work.

this is what i got after running the command:
jared@dell-desktop:~$ lsmod | grep iwl
iwl3945                96920  0
rfkill                 17176  2 iwl3945
lbm_cw_mac80211       215856  1 iwl3945
lib80211               15236  1 iwl3945
lbm_cw_cfg80211        46744  2 iwl3945,lbm_cw_mac80211
led_class              12164  1 iwl3945

Then I ran:
jared@dell-desktop:~$ sudo iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.


Does anyone have suggestions on how to debug?  I never had a problem with wireless until the upgrade.

Thanks

---

### Post by ilioscio on 2009-02-13
try running ```
sudo ifconfig -a
``` and post the output please?

---

### Post by _noob_ on 2009-02-13
Do you have the proper drivers? 
This compiles and installs the drivers. It also supports packet injection for wardriving.
[U][I]tar -xjf ipwraw-ng*
cd ipwraw-ng*
make
sudo make install
sudo make install_ucode
 echo blacklist ipwraw | sudo tee /etc/modprobe.d/ipwraw
 modprobe -r iwl3945
sudo modprobe -r iwl3945
sudo modprobe ipwraw
iwconfig[/I][/U]
Also. Did you restart your computer after you turned on your wireless? I have the Intel PRO/Wireless 3945 and I have to restart everytime.

---

### Post by jsacks on 2009-02-13
jared@dell-desktop:~$ sudo ifconfig -a
[sudo] password for jared: 
eth1      Link encap:Ethernet  HWaddr 00:1f:3c:43:3f:14  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:23:ae:01:b8:01  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe01:b801/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20017 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13608190 (13.6 MB)  TX bytes:4456027 (4.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3271 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94901 (94.9 KB)  TX bytes:94901 (94.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-43-3F-14-30-30-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by jsacks on 2009-02-13
@Noob, I should have drivers I think.  But how would I know if I do or do not?

---

### Post by binarypill on 2009-02-13
Hey, jsacks. We have the same problem. I also have problems with my wifi. I have a similar model as yours (but my laptop is an Acer Aspire 5570).

Best that I can figure, the problem is with the kill-switch not being detected when it is deactivated after being activated. Turn your wifi kill-switch off (meaning, enable your wifi) before you boot to Ubuntu and you'll notice that you will have wifi enabled. However, if you activate your kill-switch while you are using Ubuntu (thus turning off your wifi), you won't be able to turn it on again. 

There are two solutions suggested for this. Follow this URL: [>>>]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/193970") for the solutions and for some more information.

For me, the "modprobe" solution works (intermittently). I've resigned to waiting for the Jaunty release for this to be fixed (don't use wifi regularly, anyway). It's stated their that they won't be fixing this for Intrepid just yet, though I guess they will backport it. 

Good luck!

---

### Post by jsacks on 2009-02-14
The good news is it is fixed. The bad news is I am stupid because i thought the one switch was for the bluetooth when actually both my switches are related to the wireless.  So just flicked the switch and now it works

---

### Post by jediknight64 on 2009-03-23
> **binarypill said:**
> Hey, jsacks. We have the same problem. I also have problems with my wifi. I have a similar model as yours (but my laptop is an Acer Aspire 5570).

Best that I can figure, the problem is with the kill-switch not being detected when it is deactivated after being activated. Turn your wifi kill-switch off (meaning, enable your wifi) before you boot to Ubuntu and you'll notice that you will have wifi enabled. However, if you activate your kill-switch while you are using Ubuntu (thus turning off your wifi), you won't be able to turn it on again. 

There are two solutions suggested for this. Follow this URL: [>>>]("https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/193970") for the solutions and for some more information.

For me, the "modprobe" solution works (intermittently). I've resigned to waiting for the Jaunty release for this to be fixed (don't use wifi regularly, anyway). It's stated their that they won't be fixing this for Intrepid just yet, though I guess they will backport it. 

Good luck!

I have an Acer aspire 5335-2238 and I recently installed 8.10 and I am having the same problem. In windows my wireless works fine, but no internet in Ubuntu. It's very frustrating. When I left click on the NM , it shows wired networks but not wireless networks.

---

### Post by harish4linux on 2009-04-22
> **jediknight64 said:**
> I have an Acer aspire 5335-2238 and I recently installed 8.10 and I am having the same problem. In windows my wireless works fine, but no internet in Ubuntu. It's very frustrating. When I left click on the NM , it shows wired networks but not wireless networks.

Mee too facing the same problem but my model number is ACER Aspire 4715z please some one help me in solving the problem...

---

### Post by bb_454 on 2009-04-22
I'm a total linux noob.  I just got my old HP Pavilion ze5470us back up and running after my sister cooked my hdd.  I decided not to reinstall XP and go with ubuntu.  I'm using 8.10 Jaunty Jackalope.  I had some issues getting everything to work, the BIOS wouldnt recognize 250GB so I partitioned the drive, everythings good there.  My problem now is I cant find any wireless networks around me.  I can connect through my router with a cable but not wirelessly.  Maybe I'm just spoiled to windows telling me its found networks around me?  I did try going into some network settings to try to configure things manually, but obviously it didnt work.  I hate to sound like a pain, but for anyone thats willing to help (if anyone), please go slow and explain things in some detail, like I said before, I'm a beginner with Linux.  Look forward to having a good experience this time around!

Mike

---

### Post by poolem on 2009-07-06
> **bb_454 said:**
> I'm a total linux noob. I just got my old HP Pavilion ze5470us back up and running after my sister cooked my hdd. I decided not to reinstall XP and go with ubuntu. I'm using 8.10 Jaunty Jackalope. I had some issues getting everything to work, the BIOS wouldnt recognize 250GB so I partitioned the drive, everythings good there. My problem now is I cant find any wireless networks around me. I can connect through my router with a cable but not wirelessly. Maybe I'm just spoiled to windows telling me its found networks around me? I did try going into some network settings to try to configure things manually, but obviously it didnt work. I hate to sound like a pain, but for anyone thats willing to help (if anyone), please go slow and explain things in some detail, like I said before, I'm a beginner with Linux. Look forward to having a good experience this time around!
 
Mike
 
this is probably too little too late...
I have my ze5470us back from my son - he killed XP again. I installed Kububtu 9.04 last night and am impressed. Over the past few years I have tried differing flavors of Linux on this same laptop and wow, the media controls work (volume up and down on the right-hand side) except for mute and the wireless button has no affect but display is acceptable, wireless broadcom (built-in) works too.
 
I did a few things to get the wireless running and I think the important step was to connect wired to my router, rebooted Jaunty Jackalope, selected System->Hardware Drivers, it scanned and found the proprietory b43legacy driver, I activated it, rebooted, disconnected ethernet. I was presented with a clean applet in the system tray to configure my newly acquired wireless networks. If only I knew it would have been this easy I would have not gone the ndiswrapper approach and loose two hours.
;-)
 
My son doesn't know it yet, but he is getting WinXP virtualized in VirtualBox when this laptop goes home. ;)

---

