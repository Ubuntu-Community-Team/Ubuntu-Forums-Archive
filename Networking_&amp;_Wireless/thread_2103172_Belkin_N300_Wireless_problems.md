---
title: "Belkin N300 Wireless problems"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by lightsaberlesbian on 2013-01-09
I have a belkin F7D2102 N300  that I've been trying to get working on my Ubuntu and Fedora machine for a few days now without much luck. I tried the fix here ([http://ubuntuforums.org/showthread.php?t=2053044&highlight=Belkin+N300+F7D2102&page=2](http://ubuntuforums.org/showthread.php?t=2053044&highlight=Belkin+N300+F7D2102&page=2)) without much luck.

> Hook up the ethernet and let's compile the latest from Realtek. Please open a terminal and do:
Code:
sudo apt-get remove --purge ndiswrapper*
sudo apt-get install linux-headers-generic build-essential
Now grap the file here: [http://www.realtek.com.tw/downloads/...Downloads=true](http://www.realtek.com.tw/downloads/...Downloads=true) 

Download it to your desktop and right-click it and select Extract Here. Now back to the terminal:
Code:
cd Desktop/RTL81
Press the Tab key and the remiander will fill in automatically. Press Enter.
Code:
sudo su
chmod +x install.sh
./install.sh
modprobe -r rtl8192cu
modprobe 8192cu
exit
If it works correctly, we'll need to amend the blacklist file.

I guess while on the topic do any fedora users here know how I'd input this code into a fedora machine?  I'm not very familiar with yum.

---

### Post by kurt18947 on 2013-01-09
I didn't have much luck with that download link.  Here is what I came up with:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

I don't have that particular adapter but the install procedure looks very similar to my RTL8188CUs.  The download contains an install script.  Here is a link to a thread I started for the 8188CUs.  

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188CUs)

Your adapter is not identical but I bet the installation is similar.  You may need to blacklist the 'native' drivers appearing from an 'lsusb' command.  I blacklisted the 'native' driver, ran the installer script then rebooted.  Does this help any?

---

### Post by lightsaberlesbian on 2013-01-09
Weird.  The instructions said to do the exact same thing I think.

[http://ubuntuforums.org/showthread.php?t=2053044&highlight=Belkin+N300+F7D2102&page=2](http://ubuntuforums.org/showthread.php?t=2053044&highlight=Belkin+N300+F7D2102&page=2)

i already blacklisted ndiswrapper.  i'm not sure what "lsusb" is supposed to do.  I know "lsmod" has been thrown around in other threads but I have no idea what to find in that returned text to blacklist.

---

### Post by Hadaka on 2013-01-09
Hi here is a thread with a Belkin N300 fix.
[http://ubuntuforums.org/showthread.php?t=2051808&highlight=N300](http://ubuntuforums.org/showthread.php?t=2051808&highlight=N300)

lsmod= list modules that load at boot...aka what divers are being loaded
lsusb = list usb devices

read the thread, if you need help, perhaps i can give some assist, or 
better still chili555 will see your post and get you going.

---

### Post by lightsaberlesbian on 2013-01-09
I'm still confused as to why I should run lsusb.  Well I ran both lsusb and lsmod.

lsusb
> Bus 001 Device 006: ID 050d:2103 Belkin Components F7D2102 802.11n N300 Micro Wireless Adapter v3000 [Realtek RTL8192CU]

lsmod
> 

lsmod
Module                  Size  Used by
arc4                   12473  2 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20061  1 rt73usb
rt2x00lib              48836  2 rt73usb,rt2x00usb
ppp_async              17307  0 
crc_ccitt              12595  1 ppp_async
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
dcdbas                 14098  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
k8temp                 12905  0 
psmouse                86486  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17292  1 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
radeon                737926  3 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197599  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
mac_hid                13077  0 
rtl8192cu              97722  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95804  1 rtl8192cu
nv_tco                 13399  0 
i2c_nforce2            12906  0 
mac80211              436455  5 rt2x00usb,rt2x00lib,rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              178679  3 rt2x00lib,rtlwifi,mac80211
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
b44                    31364  0 
hid                    77392  1 usbhid
uas                    17828  0 
usb_storage            39646  0 
ssb                    50691  1 b44
sata_nv                23360  2 



I'm not really sure which modules I should blacklist honestly.

---

### Post by Hadaka on 2013-01-09
hi, the wireless adapter belkin n300 is a usb...no?

hence running lsusb.

looks to me from your lsmod output...you are attempting to load 2
wireless drivers...one for the internal wireless card
and one for your usb wireless belkin n300

rt73usb 27029 0 rtl8192cu 97722 0 

USB..........................                        Internal card

so,if you want to use the usb wireless blacklikst the internal....

or....uncheck "CONNECT AUTOMATICLY"  when you edit connections
then...under the wireless icon...click which one you want to connect.
usb....or......internal

---

### Post by Hadaka on 2013-01-09
Hi, after re reading the post i sent you, i am not giving you correct
advise, the rtl driver is for the belkin, however i am also seeing the rt73usb
driver in lsmod. I dont know if blacklisting the rt73usb driver would work or
not,you could try and then unblacklist it if there is no change. I know very little
about rtl drivers other than they seem to be a pain. sorry if i have led you down
a more confusing path.

---

### Post by lightsaberlesbian on 2013-01-09
No your post was helpful.  I'll have to try it out later when I'm on the comp.  I think the rt73 might be for my linksys g-wireless though i'm not quite sure.  I've also tried to get this belkin usb wireless adapter to work on my other fedora computer with the same issues...asking for authentication again and again for every network.

---

### Post by chili555 on 2013-01-09
Do you want to get the Belkin working or the Linksys? They will conflict, so choose one and we'll proceed by blacklisting the other. What is not working with the Linksys?

If the Belkin, I think you'll get a better result with the Ubuntu compat-wireless backports package. In order to recommend the correct version, we need to know your Ubuntu version:```
lsb_release -d
```

---

### Post by lightsaberlesbian on 2013-01-09
I'm trying to get it working on Ubuntu 12.10 (Gnome) and my other comp w/ Fedora 17 eventually.  I'm siding with the Belkin b/c my dad just got it for me and i'm just trying to get it to work.  I'd think it'd run faster than the Linksys g-wireless i simply found but that hasbn't been the case w/ linux so far.

---

### Post by chili555 on 2013-01-10
>  I'd think it'd run faster than the Linksys g-wireless i simply found but that hasbn't been the case w/ linux so far.Do you mean to achieve N speeds? I doubt it ever will. N is touch and go these days in Linux; sometimes it works perfectly and for some other card/driver/router combinations not at all. 

If you'd like to get the Belkin going because you love pain, then I think your best chance will be with linux-backports-modules-cw.```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Reboot and give us your report.

---

### Post by lightsaberlesbian on 2013-01-10
> sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
[sudo] password for sushi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-cw-3.6-quantal-generic
E: Couldn't find any package by regex 'linux-backports-modules-cw-3.6-quantal-generic'


Honestly, if this is as much trouble as you make it out to be I might have to give up.  Do you think the further updates in Linux kernels will correct this issue in the future?

---

### Post by chili555 on 2013-01-10
> **lightsaberlesbian said:**
> Honestly, if this is as much trouble as you make it out to be I might have to give up.  Do you think the further updates in Linux kernels will correct this issue in the future?Give up? *Give up????* Unless the coroner is on the way, I don't give up ever. > E: Unable to locate package linux-backports-modules-cw-3.6-quantal-genericYou are booted into Ubuntu 12.10, correct?> I'm trying to get it working on Ubuntu 12.10 (Gnome) The package certainly exists, please see attached. Do you have all the usual software sources enabled?```
sudo sudo software-properties-gtk
```Please see attached.

If you make any changes; i.e. add any sources, please do:```
sudo apt-get update
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```

---

### Post by lightsaberlesbian on 2013-01-10
shoot.  I'm sorry at the time I answered I didn't have access to the comp.  It's Ubuntu 12.04.1 LTS.

I don't know how to find the respective backport on my own sadly.

ps.  Is there a respective backport for fedora as well?

---

### Post by chili555 on 2013-01-10
Shoot, indeed...```
sudo apt-get install linux-backports-modules-cw-3.6-[COLOR="Red"]precise[/COLOR]-generic
```Shall I assume we are fixing 12.04 aka Precise now?> ps. Is there a respective backport for fedora as well? I haven't any idea. Sorry.

---

### Post by lightsaberlesbian on 2013-01-10
Unfortunately that didn't change much.  It can still find networks.  But it still can't connect to them.  I may call it quits since I technically have a Linksys-G working and everyone is making it out to be a huge fuss to get to work.  Any chance that this problem will resolve w/ the next kernel update?

---

### Post by chili555 on 2013-01-10
The next kernel update is in 12.10. I suggest you try the live CD and, if not, the backports package that matches.

---

### Post by lightsaberlesbian on 2013-01-23
Hi! I found some time in my work schedule to try and resolve this issue again.  If I wanted another crack at it what should I do next?
 
1) attempt to upgrade to 12.10?
2) install additional backports? i'm not sure which ones to install. also if i did install additional bacports would i have to blacklist anything?

---

### Post by chili555 on 2013-01-23
I'd download 12.10 and run the live CD to see if it helps before you install.

---

### Post by Slixt on 2013-04-13
Dead thread? Gah.. I had issues with the rtl8192ce randomly slowing down after troubleshooting everything I can only conclude the issue is my wifi hardware since every other laptop in the house worked fine. My solution.. was buying this belkin n300 which apprently has.... realtek in it. Why must everything be difficult. Any suggestions on an alternative I can just plug in when I want a stable connection?

---

### Post by kurt18947 on 2013-04-14
> **Slixt said:**
> Dead thread? Gah.. I had issues with the rtl8192ce randomly slowing down after troubleshooting everything I can only conclude the issue is my wifi hardware since every other laptop in the house worked fine. My solution.. was buying this belkin n300 which apprently has.... realtek in it. Why must everything be difficult. Any suggestions on an alternative I can just plug in when I want a stable connection?

Not all RealTek chips are problems in my experience.  My best performing WiFi USB adapters are RealTek 8192SU based adapters.  My post from a previous thread:


> I use N150 devices, they're reasonable cost and adequate for my  purposes.  My preferred adapters are RealTek 8192SU based.  I have a  Dlink DWA-131 v1 and a TrendNet TEW-649UB - they're twins.  I'd have  concerns about buying a new Dlink DWA-131.  There is a thread that  mentions a DWA-131 v.B or v.2 which uses a different chipset which is  not plug 'n' play.  I also have a generic Ralink RT-5370, bought off  Ebay for about $6.  It is plug 'n' play but signal strength appears to be about  half of the 8192SU based adapters.  Netgear WNA1100 uses an Atheros 9271  chipset and is plug 'n' play.                 


All the adapters mentioned above provide me stable connection with no disconnects.  I did disable hardware encryption on the Netgear WNA1100 as recommended on a few threads.  It seems like WiFi adapters, especially N speed (greater than 54 Mb./sec) are the biggest hardware pains in linux.

---

### Post by Slixt on 2013-04-14
Glad to hear it's not all bad. I did find that it's listed as working out of the box in 13.04 but, I have 12.10. I did however update the kernel to the latest stable I think. the one not listed as 'rc'. I'm using 3.8.6-030806-generic. Installed it hoping to alleviate these errors with the system. Didn't fix it but, that's another issue. I did try plugging it in and rebooting with it in and neither worked. I did however notice in dmesg it says :
```
[ 1359.625968] usb 1-1.1: new high-speed USB device number 4 using ehci-pci
[ 1359.720959] usb 1-1.1: New USB device found, idVendor=050d, idProduct=845a
[ 1359.720971] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1359.720978] usb 1-1.1: Product: Belkin USB Wireless Adaptor
[ 1359.720983] usb 1-1.1: Manufacturer: Manufacturer Realtek 
[ 1359.720988] usb 1-1.1: SerialNumber: 00e04c000001
[ 1359.838859] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[ 1359.839896] r8712u: Staging version
[ 1359.839914] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1359.839916] r8712u: USB_SPEED_HIGH with 4 endpoints
[ 1359.840443] r8712u: Boot from EFUSE: Autoload OK
[ 1360.433755] r8712u: CustomerID = 0x0000
[ 1360.433766] r8712u: MAC Address from efuse = ec:1a:59:4d:26:90
[ 1360.433770] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1360.433963] usbcore: registered new interface driver r8712u
[ 1360.439588] r8712u: Firmware request failed


```

I am guessing this means that I'm missing the drivers? Which if that's the case brings me to ask whether or not I'll end up having to ditch my current wifi drivers. Which do work just unreliably as i'm getting periodic slowdowns which seem to get worse lately. Like, vicious lags that sadly make it worse than poor dialup connections.

---

### Post by chili555 on 2013-04-14
> r8712u: Firmware request failedDo you have the required firmware?```
ls /lib/firmware/rtlwifi
```

---

### Post by Slixt on 2013-04-15
```
slixt@slixt-comet-L755:~$ ls /lib/firmware/rtlwifi
Realtek-Firmware-License.txt  rtl8192cfwU.bin     rtl8192sefw.old.bin
rtl8188efw.bin                rtl8192defw_12.bin  rtl8723fw_B.bin
rtl8192cfw.bin                rtl8192defw.bin     rtl8723fw.bin
rtl8192cfwU_B.bin      

```

I don't see anything with r8712u in there. So maybe I don't.

---

### Post by zrdc28 on 2013-04-15
**Drivers for the usb **
rt73usb 27029 0
crc_itu_t 12627 1 rt73usb
rt2x00usb 20061 1 rt73usb
rt2x00lib 48836 2 rt73usb,rt2x00usb

**Drivers for the internal radio**
rtl8192cu 97722 0
rtl8192c_common 69519 1 rtl8192cu
rtlwifi 95804 1 rtl8192cu

You do not need any drivers, you are trying to load 2 different drivers to do the same thing, you will never get it to work
with two different drivers.  The first thing you need to do is just unplug the usb, the internal is far superior to the usb
because it has a very effective antenna system and besides that it is a n type modem. When you reboot it will be ready
to use that 1 and then all you will have to do is when the message comes up at the top right about the network tell it
the name & password.

---

### Post by Slixt on 2013-04-15
Hmm, if the internal is superior then I may have to admit defeat and accept this as is. The internal does work, the issue with the internal is that it's not very stable. I was hoping that with the usb I can get a more stable connection. It doesn't seem to drop wifi on this kernel version (It did with one I tried) but, I constantly get these lags when playing games online or surfing that last upto a couple minutes it seems. I recently just had to kill my wifi and reconnect to get it going solid again. I originally gave in believing it's just wifi connection but, I've been monitoring the connection and the fact the reconnecting makes it run perfect again make me think it's something else. I've been checking it with wavemon and during points of lag my signal isn't typically lower. It fluctuates as to be expected but, nothing severe it generally stays in the same range and last time it hung up on me it was actually at a better signal rate.

Edit: Another reason I wanted to try this was the hangs are becoming more and more frequent and worst in severity. It started with minor ones.. couple seconds tops lately it's been a few minutes even. While browsing it's not a HUGE deal since it's not typically time important but, for playing games a couple minutes of it is gameover.

---

### Post by chili555 on 2013-04-15
> **zrdc28 said:**
> **Drivers for the usb **
rt73usb 27029 0
crc_itu_t 12627 1 rt73usb
rt2x00usb 20061 1 rt73usb
rt2x00lib 48836 2 rt73usb,rt2x00usb

**Drivers for the internal radio**
rtl8192cu 97722 0
rtl8192c_common 69519 1 rtl8192cu
rtlwifi 95804 1 rtl8192cu

Where did you see this? In lightsaberlesbian's post or in Slixt's? I believe Slixt has an rtl8192**ce**. Any assertion that an rtl8192xx is superior to an external USB is, in my humble opinion, quite questionable. 80% of the difficult problems on this forum, the ones that can't be solved by firmware or compiling a driver, are rtl8192xx related.

---

### Post by chili555 on 2013-04-15
> **Slixt said:**
> Hmm, if the internal is superior then I may have to admit defeat and accept this as is. The internal does work, the issue with the internal is that it's not very stable. I was hoping that with the usb I can get a more stable connection. It doesn't seem to drop wifi on this kernel version (It did with one I tried) but, I constantly get these lags when playing games online or surfing that last upto a couple minutes it seems. I recently just had to kill my wifi and reconnect to get it going solid again. I originally gave in believing it's just wifi connection but, I've been monitoring the connection and the fact the reconnecting makes it run perfect again make me think it's something else. I've been checking it with wavemon and during points of lag my signal isn't typically lower. It fluctuates as to be expected but, nothing severe it generally stays in the same range and last time it hung up on me it was actually at a better signal rate.

Edit: Another reason I wanted to try this was the hangs are becoming more and more frequent and worst in severity. It started with minor ones.. couple seconds tops lately it's been a few minutes even. While browsing it's not a HUGE deal since it's not typically time important but, for playing games a couple minutes of it is gameover.I suggest you find and correct the reason for the hangs first. It may not be related to wireless. Is there a behavior that provokes the hangs? If so, I'd open a terminal and run:```
top
```Provoke the hang and watch some process or another go to 100% CPU usage, or more, if you have a multi-core machine. Then troubleshoot the runaway process here:```
cat /var/log/syslog | grep <some_process> 
dmesg | grep <some_process>
```Google the result and see what can be done to fix it.

Then, I'd try to tweak the internal. Keep the USB detached. I'd get the firmware installed first. Here is a package with the file in it. Download it to your desktop. Right-click it and select 'Extract Here.' Now open a terminal and do:```
sudo cp Desktop/rtlwifi/rtl8712u.bin  /lib/firmware/rtlwifi
```Now unload and reload the driver so it sees the firmware:```
sudo modprobe -r r8712u
sudo modprobe r8712u
```Check the message log:```
dmesg | grep rtl
```Look for timestamps after the previous:> [ [COLOR="#FF0000"]1360.439588[/COLOR]] r8712u: Firmware request failedIf all that doesn't help, I'd blacklist the internal and start troubleshooting the USB.

---

### Post by Slixt on 2013-04-15
Thanks, Chili. I'll start with monitoring top. I'll just keep it on top and watch for something using up cpu when i'm experiencing it. I didn't really think about this being a cause since it seems to open/close everything fine during it just the wifi suffers. I'll get back to you on this and go from there.

---

### Post by Slixt on 2013-04-15
okay, I can rule out otherthings being the cause, wifi seemed to freeze for a long time there and nothing was even close 50% cpu.

---

### Post by Slixt on 2013-04-15
I'm a little bit confused with some of the directions here. Mostly just because I don't know what it's doing. I followed the steps by downloading the package, exracting and doing the modprobe stuff. My internet stopped which seemed like it probably should after. So, I plugged in the usb device and reset my internet connection. Am I using the usb now? or is this still the internal? The indicator light on the usb is off, so I'd think that means it's off. Dmesg shows no failure to load firmware now though.

Nevermind, through network manager I see i'm still using the rtl8192ce.

---

### Post by chili555 on 2013-04-15
> **Slixt said:**
> okay, I can rule out otherthings being the cause, wifi seemed to freeze for a long time there and nothing was even close 50% cpu.Any clues here?```
cat /var/log/syslog | grep -e r8712 -e wlan | tail -n20
```What exactly is frozen? Your whole desktop, mouse, etc. or just networking, downloading, etc.?

---

### Post by Slixt on 2013-04-15
Hey, just my network. The desktop has it's own issue which seems to be unrelated though. I'll post the log of cat.
```
Apr 15 21:25:49 slixt-comet-L755 wpa_supplicant[966]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:1a:2b:3c:ff:02 completed (auth) [id=0 id_str=]
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'ASUS'.
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 15 21:25:49 slixt-comet-L755 NetworkManager[837]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 15 21:25:49 slixt-comet-L755 dhclient: Listening on LPF/wlan0/68:a3:c4:d4:f2:b4
Apr 15 21:25:49 slixt-comet-L755 dhclient: Sending on   LPF/wlan0/68:a3:c4:d4:f2:b4
Apr 15 21:25:49 slixt-comet-L755 dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
Apr 15 21:25:52 slixt-comet-L755 dhclient: DHCPREQUEST of 192.168.1.2 on wlan0 to 255.255.255.255 port 67
Apr 15 21:25:52 slixt-comet-L755 NetworkManager[837]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 15 21:25:52 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 15 21:25:52 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 15 21:25:53 slixt-comet-L755 NetworkManager[837]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Apr 15 21:25:53 slixt-comet-L755 NetworkManager[837]: <info> Policy set 'ASUS' (wlan0) as default for IPv4 routing and DNS.
Apr 15 21:25:53 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) successful, device activated.
Apr 15 21:25:53 slixt-comet-L755 NetworkManager[837]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.


```

 Just making sure we're on the same page, 8712 is the usb and 8192ce is the built in I think. So, I looked at dmesg after downloading the usb firmware you gave and it loads it with no issues according to that. How would I get it to actually use the usb instead of the internal set though? I had a little trouble following which one we're going to sort out. :P

---

### Post by chili555 on 2013-04-16
I am unsure, as well, which one you want to sort out and use. Whichever you want, we will attempt to get going. From your logs, it appears that whichever is wlan0 connects just perfectly!

r8712u is a driver for USB devices. Please run and post:```
sudo lshw -C network
lsusb
lspci -nn | grep 0280
```Of course, I suggest you detach the USB and try to connect. Does it? What are its symptoms? Faults? Once we find out the driver for the internal, let's blacklist it and try only the USB and see if conditions improve.

---

### Post by Slixt on 2013-04-16
Okay, I'd love for the one that's connecting to work properly. It's the rtl8192. It'll connect perfectly but, the problem is it doesn't stay perfect. I've been replying from the laptop using it but, it's fault is that it'll go fine for a while, work perfectly even then just suddenly stall for a while and once it starts it's usually pretty frequent. I've had it become impossible to even play a mud because it's so bad. I've monitored the signal from wavemon and I really don't think it's the signal quality as I thought originally. I'd have better than normal signals during some of the episodes. I'll post the terminal info requested for you here.

Lshw -C network:
```
 *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:d4:f2:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.8.6-030806-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:3000(size=256) memory:c0500000-c0503fff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:36:67:85
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.1-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:44 memory:c0400000-c043ffff ioport:2000(size=128)


```

lsusb: 
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., Ltd 


```

and lspci -nn | grep 0280
```
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)


```

---

### Post by chili555 on 2013-04-16
> description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: [COLOR="#FF0000"]wlan0[/COLOR]
       version: 01
       serial: 68:a3:c4:d4:f2:b4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="#FF0000"]driver=rtl8192ce[/COLOR] driverversion=3.8.6-030806-generic firmware=N/A ip=192.168.1.2 latency=0 link=yesSo we see that the internal is wlan0 and is connected and does connect easily. We also see that the USB wasn't inserted when you ran the diagnostics...> Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b289 Chicony Electronics Co., LtdLet's leave it that way for now and try to get the internal working smoothly. If and only if we are unable to do so, we'll blacklist the internal and work on the USB. Tuck the USB in the desk drawer for now so we can concentrate on the internal.

There are a variety of driver parameters available for rtl8192ce and let's try one at a time until we hit the magic combination.```
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
```We probably don't want debug. First, let's try:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```Is it better? If so, and for any of these parameters that works, we can write a conf file to make it persistent. Also, these go away at reboot.

If it does not help, try the next one:```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce ips=0
```Try each, except debug, using the opposite of default, and tell us if one helps your problem.

Either Chili or Realtek doesn't understand boolean.

---

### Post by Slixt on 2013-04-16
Okay, I've been through a bunch of stuff trying to get the internal to work properly. I know I have the swenc=0 one. Wildeman helped me there and I believe i found and applied the ips=0. :(
I'll double check that one.

the content of my rlt8192ce.conf file is 
options rtl8192ce swenc=1
options rtl8192ce ips=0 fwlps=0 debug=2

I've been trying to troubleshoot this one for a while and followed a thread which lead me to those configurations. Like most everything I tried, I've gotten a false sense of hope as the hangs are so random I can go a short while believing it's fixed then blam hit with it. Currently though, it's getting pretty bad.

I've taken that info out for now, and working with you from here. I'd really love to get it working.

---

### Post by chili555 on 2013-04-16
I think the answer will be, with all respect to my good friend the Wild Man, one single parameter and I recommend you try each once at a time.

---

### Post by Slixt on 2013-04-16
Yeah, wildeman gave me the swenc=1 line, I found the others later on, he ran out of ideas with me on this. Ips=0 didn't seem to help, so, I'll do the next in line now. So far so good on the swlps=1.
An interesting note is when I disconnect and reconnect the connection gets back to good for a short time, it could be for seconds or a couple minutes before getting crappy again. So, something must be happening after being connected for a while. :(

---

### Post by Slixt on 2013-04-16
Nevermind, I spoke too soon. I can feel it starting to slow back down. It's so damn weird..

---

### Post by Slixt on 2013-04-16
Okay, I've now tried all of them listed above individually, and still nothing helps. :(

---

### Post by chili555 on 2013-04-17
> **Slixt said:**
> Okay, I've now tried all of them listed above individually, and still nothing helps. :(Normally, I'd suggest linux-backports-modules-cw, but I'm not sure it exists for your 3.8.0-something kernel. We could compile compat-wireless from scratch and see if that gets the internal working or we could blacklist the internal and proceed to the USB. What do you prefer?

Frankly, rt2800pci is always a bit twitchy, so if I were pressed for a recommendation, I'd start on the USB.

---

### Post by Slixt on 2013-04-17
Okay, we can start on the usb. I'm kind of sick of messing with the internal one at this point. I've tried to compile the realtek sites driver but, came back with errors on make. It's saying the file is not right I think. So, where do I start with getting the usb to work. I wish it would just work by plugging it in and tada wifi.

---

### Post by chili555 on 2013-04-17
With our fingers crossed, let's blacklist the internal, insert the USB, reboot and see if it starts:```
sudo su
echo "blacklist rtl8192ce" >> /etc/modprobe.d/blacklist.conf
echo r8712u >> /etc/modules
exit
```Insert the USB, reboot and let us see:```
iwconfig
ifconfig
```Thanks.

---

### Post by Slixt on 2013-04-17
Okay, I tried this and wifi didn't come up. I'll post the results of the commands you gave me along with dmesg which seems to indicate the firmware is failing to load.
```
   slixt@slixt-comet-L755:~$ iwconfig  
 lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 slixt@slixt-comet-L755:~$ ifconfig  
 eth0      Link encap:Ethernet  HWaddr e8:9a:8f:36:67:85   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:65536  Metric:1  
           RX packets:400 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:400 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:31904 (31.9 KB)  TX bytes:31904 (31.9 KB)  
 

 

 slixt@slixt-comet-L755:~$ dmesg | grep r8712u  
 [   18.196634] r8712u: module is from the staging directory, the quality is unknown, you have been warned.  
 [   18.197372] r8712u: Staging version  
 [   18.197386] r8712u: register rtl8712_netdev_ops to netdev_ops  
 [   18.197388] r8712u: USB_SPEED_HIGH with 4 endpoints  
 [   18.202005] r8712u: Boot from EFUSE: Autoload OK  
 [   18.750419] r8712u: CustomerID = 0x0000  
 [   18.750429] r8712u: MAC Address from efuse = ec:1a:59:4d:26:90  
 [   18.750433] r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"  
 [   18.750669] usbcore: registered new interface driver r8712u  
 [   18.752862] r8712u: Firmware request failed


```

---

### Post by chili555 on 2013-04-18
Can you confirm the firmware is actually there and readable?```
ls -al /lib/firmware/rtlwifi
```If it isn't there, please retrace your steps from post #28 above. If it isn't readable:> 
<snip>
-[COLOR="#FF0000"]r[/COLOR]w-[COLOR="#FF0000"]r[/COLOR]--[COLOR="#FF0000"]r[/COLOR]--  1 root root 122328 Nov  8 12:24 rtl8712u.bin
<snip>...then make it so, Mr. Data:```
sudo chmod +r  /lib/firmware/rtlwifi/*
```Then unload and reload the driver:```
sudo modprobe -r r8712u
sudo modprobe r8712u
```Now check for messages *after* the timestamp 18.752862 you posted:```
dmesg | grep 8712
```

---

### Post by Slixt on 2013-04-18
Okay, files are now there. I somehow managed to skip the copy step last time. I'll blacklist the driver and try this again with the firmware. :D

---

### Post by Slixt on 2013-04-18
Okay, THANK YOU CHILI!!! It's working now. Little lights blinking and all. Now, when I looked at Wavemon with this working it made me realize something. Signal level is way different. It used to be in the red with a negative symbol in front of it while link quality was in the green. Now both are in the green. I wonder what the deal with the internal was?

---

### Post by Slixt on 2013-04-18
Okay, the output of iwconfig and ifconfig.

```
slixt@slixt-comet-L755:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"ASUS"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1A:2B:3C:FF:02   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=56/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

slixt@slixt-comet-L755:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:9a:8f:36:67:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:782 errors:0 dropped:0 overruns:0 frame:0
          TX packets:782 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65120 (65.1 KB)  TX bytes:65120 (65.1 KB)

wlan1     Link encap:Ethernet  HWaddr ec:1a:59:4d:26:90  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ee1a:59ff:fe4d:2690/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3675 errors:0 dropped:357 overruns:0 frame:0
          TX packets:2522 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3059384 (3.0 MB)  TX bytes:524526 (524.5 KB)


```

Okay, it looks like i'm dropping some packets for some reason which I think could explain why I'm getting a bit of a hang when playing but, honestly I think this is still the better route to go than the internal. I think it's issues were probably far more complicated.

---

### Post by Slixt on 2013-04-18
The connection definitely feels better though. On the internal it was hanging a lot worse. I've had like 2 mild hangs on this but, I'm pretty sure it's the packets dropping as the number dropped increases each time it happens and I don't remember seeing any dropped packets on the internal one. So, a clue at least aswell

---

### Post by chili555 on 2013-04-18
> wlan1     Link encap:Ethernet  HWaddr ec:1a:59:4d:26:90  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ee1a:59ff:fe4d:2690/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3675 errors:0 dropped:357 overruns:0 frame:0
          TX packets:2522 errors:0 [COLOR="#FF0000"]dropped:1[/COLOR] overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3059384 (3.0 MB)  TX bytes:524526 (524.5 KB)Glad it's working! I wouldn't worry at all about one drop.

---

### Post by Slixt on 2013-04-18
Yeah, it's just the rx packet drops I was looking at that steadily increase. Had over 1000 drops on that before going into suspend and walking away for a bit. Small hangs but, I think it's just from that. Every hang = drop increases in ifconfig. So, I'll look into possibilities that cause drops on rx packets. The 1 tx packet drop never increases. I guess I should start with what rx and tx are. Recieve and Transmit I think. 

Thanks again, Chili. This is significantly better so far, minor hangs are doable. I was catching sets of like 10+second hangs repeatedly for like an hour until I give up and reset my connection with the internal wifi. I'll deal with this and try to slowly sort it out on my own unless you feel like hanging around to help troubleshoot it. I'd hate to bug you though.

---

### Post by chili555 on 2013-04-18
> Recieve and Transmit I think. Correct.

---

