---
title: "Belkin Wireless refuses to connect with Lynx"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Nailbunny on 2010-06-15
I was dual booting with XP and Jackalope using a Belkin N wireless USB. The install on Jackalope was simple, a plug and play type situation, plugged it in and it worked. A few days ago though, i wiped the whole computer and installed Lynx. To my dismay, even though Lynx sees the wireless, sees the available signals, lets me input my password... it fails to connect. It just spins and spins and eventually asks for my password again...

I'm still pretty new to Ubuntu, and Linux in general. I updated, and pretty sure i retrieved 3rd party drivers for the video card properly (using a cable connection), but thats pretty close to where my "expertise" ends.

I'm at a total loss and would really appreciate ideas, thanks.

---

### Post by b k on 2010-06-16
> **Nailbunny said:**
> I was dual booting with XP and Jackalope using a Belkin N wireless USB. The install on Jackalope was simple, a plug and play type situation, plugged it in and it worked. A few days ago though, i wiped the whole computer and installed Lynx. To my dismay, even though Lynx sees the wireless, sees the available signals, lets me input my password... it fails to connect. It just spins and spins and eventually asks for my password again...
 
I'm still pretty new to Ubuntu, and Linux in general. I updated, and pretty sure i retrieved 3rd party drivers for the video card properly (using a cable connection), but thats pretty close to where my "expertise" ends.
 
I'm at a total loss and would really appreciate ideas, thanks.
 
Hi there, we need to first identify the exact model (device ID) of your Belkin wireless adapter.
 
Go to : *Applications, Accessories, Terminal*
 
```
lsusb
```
 
Post the output back here.
 
 
```
lsmod
```
 
Also post the output back here
 
Note that you can save the output to a text file and transfer (via usb dongle) the file to a machine with a working internet connection for posting back here.
 
Thanks
 
PS  if your model is **F5D8055v2 **, the solution is at post #2 at his link [http://ubuntuforums.org/showthread.php?t=1510801](http://ubuntuforums.org/showthread.php?t=1510801)
 
If your model is **F6D4050 v1** , the solution is at post #2 at this link [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

---

### Post by Nailbunny on 2010-06-17
excellent. 

i haven't had the time i wish i did in the past few days to finish this task. i will try either solution accordingly and get back with the information/solution as quick as i can... 

much appreciation. thanks again.

---

### Post by Nailbunny on 2010-06-21
Thanks for your patience... 

...the model number for the Belkin USB wireless i'm using is F5D8053v4.

Also...
lsusb results in

Bus 004 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:8053 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmob results in

Module                  Size  Used by
rt2870sta             461811  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
dell_wmi                1793  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7087672  24 
dcdbas                  5422  0 
vga16fb                11385  1 
psmouse                63245  0 
vgastate                8961  1 vga16fb
parport_pc             25962  1 
soundcore               6620  1 snd
serio_raw               3978  0 
intel_agp              24177  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
joydev                  8708  0 
lp                      7028  0 
shpchp                 28820  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  3 ppdev,parport_pc,lp
b44                    25542  0 
ssb                    37336  1 b44
mii                     4381  1 b44
floppy                 53016  1 
hid_sunplus             1259  0 
usbhid                 36110  0 
hid                    67032  2 hid_sunplus,usbhid

...this is with the wired connection up and running and the USB wireless plugged in.

---

### Post by b k on 2010-06-21
> **Nailbunny said:**
> Thanks for your patience... 

...the model number for the Belkin USB wireless i'm using is F5D8053v4.

Also...
lsusb results in

Bus 004 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:8053 Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmob results in

Module                  Size  Used by
rt2870sta             461811  0 
arc4                    1153  2 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
ppdev                   5259  0 
dell_wmi                1793  0 
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7087672  24 
dcdbas                  5422  0 
vga16fb                11385  1 
psmouse                63245  0 
vgastate                8961  1 vga16fb
parport_pc             25962  1 
soundcore               6620  1 snd
serio_raw               3978  0 
intel_agp              24177  1 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
joydev                  8708  0 
lp                      7028  0 
shpchp                 28820  0 
agpgart                31724  2 nvidia,intel_agp
parport                32635  3 ppdev,parport_pc,lp
b44                    25542  0 
ssb                    37336  1 b44
mii                     4381  1 b44
floppy                 53016  1 
hid_sunplus             1259  0 
usbhid                 36110  0 
hid                    67032  2 hid_sunplus,usbhid

...this is with the wired connection up and running and the USB wireless plugged in.

Hi there, please go to a Terminal window and do this:

```
sudo gedit /etc/modprobe.d/blacklist.conf

```

add this line to the end of the opened file:

blacklist rt2800usb

[COLOR=Red]save[/COLOR] and close (ensure that the opened file blacklist.conf is saved in the /etc/modprobe.d directory).

Reboot

If it still does not work, temporarily remove your wired connection and reboot again.

Keeping my fingers crossed. Hope you report back with success.

---

### Post by Nailbunny on 2010-06-23
Tried the line of terminal code and following instructions and it  seems as though nothing has changed, bummer. Hopefully i entered it  correctly, not the swiftest with terminal and not entirely sure what this means past saving and closing...

> **b k said:**
> 
[COLOR=Red]save[/COLOR] and close (ensure that the opened file blacklist.conf is saved in the /etc/modprobe.d directory).




i wonder if it's not something with the way i have the existing portion of the wireless setup. Would i need to change something in the wireless connection editing or security? Lynx recognizes the device and connections available... there are other computers in this house using the wireless connection, so i know thats there and solid.

---

### Post by b k on 2010-06-23
> **Nailbunny said:**
> Tried the line of terminal code and following instructions and it  seems as though nothing has changed, bummer. Hopefully i entered it  correctly, not the swiftest with terminal and not entirely sure what this means past saving and closing...




i wonder if it's not something with the way i have the existing portion of the wireless setup. Would i need to change something in the wireless connection editing or security? Lynx recognizes the device and connections available... there are other computers in this house using the wireless connection, so i know thats there and solid.

Hi there,

Always use copy and paste (ie copy whatever you wish to copy from here and save to a text file on a usb dongle, then transfer text file to Ubuntu machine with wireless problem, open text file and copy and paste code into Terminal window one line at a time) to execute code/commands to prevent human typo errors.
You can do the reverse ie transfer output from your Ubuntu machine with the wireless problem agiain via a text file and usb dongle to a internet enabled machine for posting back here.

If you are worried about this line :

[I][COLOR=Red]save[/COLOR] and close (ensure that the opened file  blacklist.conf is saved in the /etc/modprobe.d directory).
[/I] 
just execute from a Terminal window again this:

```
gedit /etc/modprobe.d/blacklist.conf 

```Scroll down to the bottom of the opened file and just check that the previously added line:

blacklist rt2800usb

is at the end of the file. If it is, you have nothing to worry about. Just close the file again.

If you have not previously created a connection to your router/gateway/access point, do this:

Go to S[I]ystem > Preferences > Network Connections

[/I]Select[I] Wireless > Add 

[/I]Fill in the details for *Connection name* , *SSI*D . and  *Mode*

Then select *Wireless Security* and then fill in the details for the Security and Password fields.

At the same time also **tick** Connect automatically and Available to all users.

Then click [COLOR=Red]Apply[/COLOR]

Reboot

Hopefully your wireless connection will be up and running.

Let us know if it works.

---

### Post by Nailbunny on 2010-06-24
yep, generally always do the copy/paste method in terminal, seems as though the inserted code is in the right place...

i have created and deleted connections a few times and attempted to use the "found" connections but similar results repeatedly. That said though, i am really unsure what information should be in the specific fields, have never had to tweak them before... mode, Bssid, IPv4 and IPv6 unsure about all of these. At one point in my playing around i set the security to a WEP 128-bit Passphrase with everything else at default, entered password and the connection said "connected" as i passed over the icon yet a browser couldn't connect online. Frustrating.

---

### Post by b k on 2010-06-24
> **Nailbunny said:**
> yep, generally always do the copy/paste method in terminal, seems as though the inserted code is in the right place...

i have created and deleted connections a few times and attempted to use the "found" connections but similar results repeatedly. That said though, i am really unsure what information should be in the specific fields, have never had to tweak them before... mode, Bssid, IPv4 and IPv6 unsure about all of these. At one point in my playing around i set the security to a WEP 128-bit Passphrase with everything else at default, entered password and the connection said "connected" as i passed over the icon yet a browser couldn't connect online. Frustrating.

Hi there, firstly do you see a sort of 'radio/wireless' beacon on the top line (slightly to your right of your screen)?
Hopefully if yes, left click on it and you should see a list of the available wireless networks you can connect to.

If you have not messed around the too many things, the info you need to enter in post #7 should be all that is required for you to connect.

*Connection name   *- for you to choose (can be the same name as your SSID).

*SSID*   - this is the name of the wireless network you are trying to connect to ([COLOR=Red]it is important[/COLOR] to type this correctly - note that it is case sensitive).

*Mode*   -  try infrastructure first if you are trying to connect to your router/gateway/access point

*Security - *you can access your wireless router/gateway/access point webpage to get this info (you need to have administration rights to do this).

*Password* - this is the password you have set  previously to access the configuration settings within  your wireless router/gateway/access point .

Hope the info is helpful

---

### Post by Nailbunny on 2010-06-29
Thanks again for your continued help.

I do have the wireless radio/wireless beacon, and can also see all available connections (mine, the cities, my neighbors,etc ...), SSID is set as the name of my wireless network connection, Mode set to infrastructure, Security set to WPA & WPA2 Personal (as it was set similarly in Jackalope and is currently used with another computer), and password entered correctly (double/triple/quad... checked).  Also the "available to all users" box is checked.

There is a "BSSID" and a "MAC address" field which are left blank and a "MTU" field which is set to automatic (as opposed to a specific number that counts up from "automatic") all of which i have no idea what they are or do.

I feel at this point i have tried every possible combination of combinations inside of the "edit connections" menus and the problem lies elsewhere.

---

### Post by b k on 2010-06-29
> **Nailbunny said:**
> Thanks again for your continued help.

I do have the wireless radio/wireless beacon, and can also see all available connections (mine, the cities, my neighbors,etc ...), SSID is set as the name of my wireless network connection, Mode set to infrastructure, Security set to WPA & WPA2 Personal (as it was set similarly in Jackalope and is currently used with another computer), and password entered correctly (double/triple/quad... checked).  Also the "available to all users" box is checked.

There is a "BSSID" and a "MAC address" field which are left blank and a "MTU" field which is set to automatic (as opposed to a specific number that counts up from "automatic") all of which i have no idea what they are or do.

I feel at this point i have tried every possible combination of combinations inside of the "edit connections" menus and the problem lies elsewhere.

Hi there,

I am assuming you did not previously install another  program called Wicd to manage your wireless network but is using the  default Network Manager.
Note that you should not have both running  at the same time.

Please [COLOR=Red]check[/COLOR] :

Some where within   "edit connections" > Wireless > (left click on your wireless name)  then Edit > Wireless Security ,
- the Password field has been  properly saved (it [COLOR=Red]should not be blank[/COLOR])
-  Connect automatically [COLOR=Red]has been ticked[/COLOR]
-  Within IPv4 Settings, choose [COLOR=Red]Automatic (DHCP)[/COLOR]  in the Method field - leave other fields blank
- Within IPv6  Settings, choose[COLOR=Red] Ignore[/COLOR] in the Method field -  leave other fields blank

Please post outputs of:

```
gedit /var/lib/NetworkManager/NetworkManager.state
``````
cat /etc/network/interfaces
``````
iwconfig
``````
sudo lshw -C network
``````
dmesg | tail -n20
```Hopefully  with more info, others on this forum who are more tech savvy can offer  further help.

Thanks and post back.

---

### Post by Nailbunny on 2010-07-03
i checked all of the fields under "edit connections" and they are as requested. With the Belkin wireless plugged in and the wired connection removed terminal outputs...

gedit /var/lib/NetworkManager/NetworkManager.state     results in...

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


cat /etc/network/interfaces   results in...

auto lo
iface lo inet loopback


iwconfig   results in...

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"Hood Hub"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:21:29:97:41:3B   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=98/100  Signal level:-46 dBm  Noise level:-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo lshw -C network   results in...

  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:68:e6:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:fe9fe000-fe9fffff memory:fe020000-fe023fff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:75:92:b3:0c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless


dmesg | tail -n20   results in...

[  405.325509] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 525
[  405.325998] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  405.375581] DRS: unkown mode,default use 11N 1S AP 
[  405.375591] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  420.377142] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 643
[  420.377716] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  420.430712] DRS: unkown mode,default use 11N 1S AP 
[  420.430720] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  435.434024] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 723
[  435.434482] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  435.479336] DRS: unkown mode,default use 11N 1S AP 
[  435.479344] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  450.480862] ===>rt_ioctl_giwscan. 5(5) BSS returned, data->length = 723
[  450.481312] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  450.530897] DRS: unkown mode,default use 11N 1S AP 
[  450.530905] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)
[  465.532785] ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 532
[  465.533236] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=6)
[  465.582622] DRS: unkown mode,default use 11N 1S AP 
[  465.582631] DRS: unkown mode (SupRateLen=8, ExtRateLen=4, MCSSet[0]=0x0, MCSSet[1]=0x0)

hopefully this will help someone help me turn this frown upside-down  :cry:.

---

### Post by b k on 2010-07-04
Hi there, your output seems to suggest that you are near to success.

> configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless seems to have a missing IP address.

Post the output of these Terminal commands:

```
sudo dhclient -1 wlan0
``````
ping -c2 85.190.27.2
``````
ping -c2 www.ubuntu.com
```

Is your router/gateway/AP configured to use TKIP or AES encryption?

Thanks and post back

---

### Post by Nailbunny on 2010-07-15
Sorry its been so long, but something horrible/hilarious has happened to my entire operating system. Allow my to elaborate...

Shortly after my last post, i tured on the computer and it failed to make it past BIOS. There were a few drive seek failures and other errors i don't quite understand. Regardless of what happened, either the hard drive itself failed or the install was corrupt, or something else... Lynx is gone. Sad. Every time i turn on the computer it stops at a screen with the options of F1 or F2. F1 to try again which results in a hardware beep (there are no speakers attached) and a return to the two options. F2 enters BIOS. 

Now this computer is running the newest version of Mint live (as it's what i had on hand) until i figure out what exactly is going on. I'm just glad this horribleness happened before i really had anything on the hard drive to lose. Oh wells. 

Thanks though for all of your effort b k.

---

