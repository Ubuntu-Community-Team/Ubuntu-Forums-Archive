---
title: "Unable to connect TP-Link TL-W321G wireless"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by alcohol52 on 2010-05-14
I have been trying to connect TP-Link TL-W321G USB wireless device to internet for a week now but no success. The Ubuntu wiki says that it works out of box but that may be written by someone who never used it. I have searched this forums and tried all but no success. Form the same i recently installed Lucid but without wireless it is useless. I am writing this from Windows. 

The modem uses rt73 drivers that is for sure but it also loads rt2500usb driver which i think is detrimental. Blacklisting does not help.

I tried it in Puppy linux and lo I could get the connection in 2 minutes. The network setup wizard was damn good. Lsmod showed that it wasn't using rt2500usb.

I think the network manager sucks in ubuntu.
Is there any one who is  successfully using the same chip/card in ubuntu? Please help.

PS- I asssume that there was the problem with the card since Gutsy and there is open source driver available yet the problem has not been solved till lucid. Ubuntu really sucks when wireless is concerned.

---

### Post by chili555 on 2010-05-15
> Ubuntu really sucks when wireless is concerned.Wireless drivers are a part of the kernel. Although Ubuntu contributes, they are not responsible for the final version. As well, Suse and Debian and Fedora and all their derivatives use the same 2.6.xx kernel. If you tell me that there is a distribution out there that loads rt73usb correctly and does not drag in rt2500usb and maybe rt2800usb, then I'd be fascinated to hear about it. 

I have tried about every one there is and they all have problems. Ubuntu has a community unmatched by any other to help you solve those problems.

Let's troubleshoot. May we see, in a terminal:```
lsusb
lsmod | grep -e rt2 -e rt7
```

---

### Post by Justice Bucket on 2010-05-15
May I get in on this thread? I just installed ubuntu and cannot connect wirelessly like I could with windows. My network manager is nowhere to be found. I've been combing the forums but still no solution yet.

---

### Post by chili555 on 2010-05-15
> **Justice Bucket said:**
> May I get in on this thread? I just installed ubuntu and cannot connect wirelessly like I could with windows. My network manager is nowhere to be found. I've been combing the forums but still no solution yet.Is this the exact same device you have?> TP-Link TL-W321GIf so, please post the requested data. If not, start a new thread and tell us what you have.

---

### Post by Bucky Ball on 2010-05-15
> **chili555 said:**
> Is this the exact same device you have?If so, please post the requested data. If not, start a new thread and tell us what you have.

Good advice.

Does the device show up when plugged in? Start from the basics and open a terminal and paste in:

```
lsusb
```Do you see it there? 

The TP-Link I used for a build last christmas did indeed work 'out of the box', much to my astonishment! One of the friendlier brands.

---

### Post by Justice Bucket on 2010-05-15
Sorry, still new. I have a Dell inspiron 6400/1505 and am using a linksys cisco wireless router. Is this I formation useful?

---

### Post by Bucky Ball on 2010-05-15
> **Justice Bucket said:**
> Sorry, still new. I have a Dell inspiron 6400/1505 and am using a linksys cisco wireless router. Is this I formation useful?

Unless you are using this specific TP-Link USB device you will have better luck starting a new thread detailing your own issue. ;)

---

### Post by Justice Bucket on 2010-05-15
Ok thanks.

---

### Post by alcohol52 on 2010-05-15
> If you tell me that there is a distribution out there that loads rt73usb correctly and does not drag in rt2500usb and maybe rt2800usb, then I'd be fascinated to hear about it.As i mentioned PUPPY linux 4.3 correctly used only RT73 and NOT RT2500USB (There is another one too but i forgot). I could connect the wireless in 2 minutes  which i couldn't in 1 week in Ubuntu. (As far as experience is concerned i ran PUPPY linux for the first time). The problem here lies in not kernel but the networkmanager trying to activate multiple modules for the device, probably.

My ubuntu partition is barely usable now(which i installed 5-6 days ago) so i wont be able to type the commands- lot of uninstalling and compiling and no network . However i have the output from PUPPY linux. (The command however showed rt2500usb drivers, I clearly remember in ubuntu)
OUTPUT FROM PUPPY LINUX:(no rt2500usb as you see)
[HTML]Module                  Size  Used by
lp                      9476  0 
snd_pcm_oss            37440  0 
snd_seq_dummy           2608  0 
snd_seq_oss            27648  0 
snd_seq_midi_event      6892  1 snd_seq_oss
snd_seq                48464  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          6968  3 snd_seq_dummy,snd_seq_oss,snd_seq
snd_mixer_oss          15820  1 snd_pcm_oss
arc4                    1612  2 
ecb                     2508  2 
rt73usb                25584  0 
rt2x00usb              11308  1 rt73usb
rt2x00lib              29388  2 rt73usb,rt2x00usb
input_polldev           3764  1 rt2x00lib
led_class               4112  1 rt2x00lib
mac80211              166056  2 rt2x00usb,rt2x00lib
cfg80211               64972  2 rt2x00lib,mac80211
crc_itu_t               1836  1 rt73usb
serio_raw               5168  0 
pcspkr                  2284  0 
8139too                23152  0 
mii                     5004  1 8139too
i2c_i801                9504  0 
i2c_core               23776  1 i2c_i801
snd_intel8x0           29160  0 
snd_ac97_codec         98604  1 snd_intel8x0
ac97_bus                1516  1 snd_ac97_codec
snd_pcm                72496  3 snd_pcm_oss,snd_intel8x0,snd_ac97_codec
snd_timer              20340  2 snd_seq,snd_pcm
snd                    56516  9 snd_pcm_oss,snd_seq_oss,snd_seq,snd_seq_device,snd_mixer_oss,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore               6912  1 snd
snd_page_alloc          8852  2 snd_intel8x0,snd_pcm
intel_agp              25788  1 
agpgart                34188  2 intel_agp
fan                     4048  0 
parport_pc             29828  1 
parport                34508  2 lp,parport_pc
evdev                   9472  0 
thermal                12712  0 
button                  5148  0 
processor              34592  0 
fuse                   53800  2 
aufs                  137092  1 
nls_iso8859_1           3724  1 
nls_cp437               5356  1 
usb_storage            51584  0 
usbhid                 26112  0 
squashfs               22928  1 
uhci_hcd               21564  0 
ehci_hcd               32856  0 
usbcore               138160  7 rt73usb,rt2x00usb,usb_storage,usbhid,uhci_hcd,ehci_hcd[/HTML]

Ok lets solve this problem once and for all.

---

### Post by chili555 on 2010-05-15
> Ok lets solve this problem once and for all.Sounds great!

Let's see:```
iwconfig
dmesg | grep -e rt2 -e rt7
```There has to be some good reason it doesn't connect.> My ubuntu partition is barely usable nowHow so? If we can't give it terminal commands and change things, we are unlikely to fix much.

---

### Post by alcohol52 on 2010-05-15
Ok I reinstalled Ubuntu 10.04-it is so easy and fast.
Let me be very clear to you. 

1. Ubuntu detects the device- no problem.
2. It detects the networks available and tries to connect. 
3. Most of time it connects but there is no internet. Sometimes there is a connection which is in bytes per seconds and not usable. I am replying from Windows 7. (Same thing in karmic,jaunty, Sabayon 5.0). The progress in lucid is that i could get internet even then it is unusuable.

I am giving you the required details

[COLOR=Red]**1.lsusb**[/COLOR]

[HTML]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/HTML]No problem the device is detected well and good.

[COLOR=Red]**2.lsmod | grep -e rt2 -e rt7**[/COLOR]

[HTML]rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              204922  2 rt2x00usb,rt2x00lib
cfg80211              126485  2 rt2x00lib,mac80211[/HTML]As you see the ***rt2500usb*** is loaded along with ***rt73usb***. Not so in Puppy linux.

[COLOR=Red]**3.**** iwconfig**[/COLOR]
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"B....link  WIFI"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 3E:19:BE:1F:B3:98   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/HTML]So the wlan is up...........

[COLOR=Red]**4. ****dmesg | grep -e rt2 -e rt7**[/COLOR]

  [HTML] 54.626401] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   54.626409] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   54.626465] usbcore: registered new interface driver rt2500usb
[   54.951286] Registered led device: rt73usb-phy1::radio
[   54.951320] Registered led device: rt73usb-phy1::assoc
[   54.951872] usbcore: registered new interface driver rt73usb
[   55.017537] rt73usb 1-6:1.0: firmware: requesting rt73.bin [/HTML]The[COLOR=Red]** tricks**[/COLOR] i have tried: (I don't want to do it again............spare me)
1. Blacklisting rt2500usb and its allies singly and in bulk.
2. Removing network manager
3. use Ndiswrapper with XP drivers (with blacklisting all opensource drivers)
4. configuring with rutil.
5. To a some extent RAlink drivers and serialmonkey drivers.
6. Replacing rt73.bin firmware in /lib/firmware

These were all i could find in forums. None of them worked. I didn't find any solved ones mentioning clearly what to do and how to do.

Hope help will come by. At he same time i will stick with Windows( thanking Bill Gates!).

---

### Post by chili555 on 2010-05-15
Please try:```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
reboot
```Now, how is your wireless?

---

### Post by alcohol52 on 2010-05-15
I have tried it and it won't work. I have mentioned it earlier.

---

### Post by chili555 on 2010-05-15
> **alcohol52 said:**
> I have tried it and it won't work. I have mentioned it earlier.But you didn't try it on your re-install? How is it going to get fixed if you won't actually change anything? Perhaps we will get further clues after you blacklist and reboot.

---

### Post by alcohol52 on 2010-05-16
> How is it going to get fixed if you won't actually change anything?

Ok I blacklisted the driver and rebooted. The situation is same.
**lsmod** shows no rt2500usb module.

What should I do next?

---

### Post by Bucky Ball on 2010-05-16
Might sound crazy but ...

Have you plugged in an ethernet cable, gotten online, then plug in the wireless device, check it is there with lsusb in a terminal then run update?

Is there a drive disabled in System->Hardware Drivers? 

I suggest getting online with a cable and getting all updates if you haven't done that already. These things rarely work without a cable connection to get things going. A catch 22.

---

### Post by alcohol52 on 2010-05-16
> These things rarely work without a cable connection to get things going.

 A catch 22.The apparent problem is that the wireless usb device is in desktop  and I haven't  any cable network. The wireless works superb in Windows 7 and till the problem is solved I am stuck with Windows. So to update or install anything in ubuntu I have to get network in ubuntu. So apparently I am in a catch 22 situation. Ha! Ha! I am posting this from windows.

---

### Post by chili555 on 2010-05-16
Now please let us see:```
dmesg | grep -e rt7 -e wlan
iwconfig
```Thanks.

---

### Post by alcohol52 on 2010-05-16
Here are the output:

[COLOR=Red]**1. dmesg | grep -e rt7 -e wlan**[/COLOR]
[HTML][   12.668111] Registered led device: rt73usb-phy0::radio
[   12.668141] Registered led device: rt73usb-phy0::assoc
[   12.668870] usbcore: registered new interface driver rt73usb
[   12.831881] rt73usb 1-6:1.0: firmware: requesting rt73.bin
[   12.968916] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.841517] wlan0: deauthenticating from 3e:19:be:1f:b3:98 by local choice (reason=3)
[   23.843687] wlan0: direct probe to AP 3e:19:be:1f:b3:98 (try 1)
[   24.040025] wlan0: direct probe to AP 3e:19:be:1f:b3:98 (try 2)
[   24.240031] wlan0: direct probe to AP 3e:19:be:1f:b3:98 (try 3)
[   24.440040] wlan0: direct probe to AP 3e:19:be:1f:b3:98 timed out
[   31.670691] wlan0: direct probe to AP 3e:19:be:1f:b3:98 (try 1)
[   31.675318] wlan0: direct probe responded
[   31.675324] wlan0: authenticate with AP 3e:19:be:1f:b3:98 (try 1)
[   31.679814] wlan0: authenticated
[   31.679841] wlan0: associate with AP 3e:19:be:1f:b3:98 (try 1)
[   31.683307] wlan0: RX AssocResp from 3e:19:be:1f:b3:98 (capab=0x21 status=0 aid=1)
[   31.683311] wlan0: associated
[   31.688088] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   42.500513] wlan0: no IPv6 routers present
[   77.220550] wlan0: deauthenticating from 3e:19:be:1f:b3:98 by local choice (reason=3)
[   98.445207] wlan0: deauthenticating from 00:19:be:1f:b3:98 by local choice (reason=3)
[   98.646559] wlan0: direct probe to AP 00:19:be:1f:b3:98 (try 1)
[   98.670310] wlan0: direct probe responded
[   98.670314] wlan0: authenticate with AP 00:19:be:1f:b3:98 (try 1)
[   98.868041] wlan0: authenticate with AP 00:19:be:1f:b3:98 (try 2)
[   98.874806] wlan0: authenticated
[   98.874834] wlan0: associate with AP 00:19:be:1f:b3:98 (try 1)
[   98.884051] wlan0: RX AssocResp from 00:19:be:1f:b3:98 (capab=0x21 status=0 aid=1)
[   98.884055] wlan0: associated[/HTML]
I have a question. Could it be due to IPv6 not present? In windows I found using IPv6. In ubuntu the setting is ignore IPv6 setting. If kept to automatic there is no connection.

**[COLOR=Red]2. iwconfig[/COLOR]**

[HTML]wlan0     IEEE 802.11abg  ESSID:"B....link"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:BE:1F:B3:98   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/HTML]

Is there something like network connection wizard or automatic connection script in ubuntu like the one in Puppy linux? I could not find one. My plan is to compile the network connection wizard and blinky  from puppy linux source  and apt-get remove **network manager**. I read somewhere in puppy linux forum someone doing same in ubuntu and getting a connection.

---

### Post by chili555 on 2010-05-16
> [   98.868041] wlan0: authenticate with AP 00:19:be:1f:b3:98 (try 2)
[   98.874806] wlan0: authenticated
[   98.874834] wlan0: associate with AP 00:19:be:1f:b3:98 (try 1)
[   98.884051] wlan0: RX AssocResp from 00:19:be:1f:b3:98 (capab=0x21 status=0 aid=1)
[   98.884055] wlan0: associatedYou are connected.> wlan0     IEEE 802.11abg  ESSID:"B....link"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:BE:1F:B3:98   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr:off
          Power Management: on
          [COLOR="Red"]Link Quality=42/70[/COLOR]  Signal level=-68 dBm  
Although the signal strength is terrible. Is the router a long way away? Does it have an option to increase the signal strength?

We might turn off power management:```
sudo iwconfig wlan0 power off
```Any improvement? We might also try encryption in software and not hardware:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```Any improvement?

Both of these are temporary; if one or both work, we will need to tweak one file to make them effective on boot.

---

### Post by alcohol52 on 2010-05-16
Neither worked.
Connecting to the network is not a problem. The internet simply doesn't work. Tranfers rate in bytes per sec.

I think the signal strength is not a problem . I have no problem in windows. The signal strength is same.

Waiting for more input.................

---

### Post by bhaddow on 2010-05-16
Hi

I'm having a problem connecting with the same card. The card seems to be recognised
```

$ sudo lsusb | grep Ral
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```But after configuring the device and trying to connect, it just times out:
```

$ sudo dhclient wlan0
Listening on LPF/wlan0/00:27:19:b9:a8:da
Sending on   LPF/wlan0/00:27:19:b9:a8:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Here's the sequence of commands that I'm using
```

lsusb
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid annebarry
iwconfig wlan0 key 98f2c4dc5c
iwconfig wlan0 mode Managed
dhclient wlan0

```Any suggestions?

regards
Barry

---

### Post by chili555 on 2010-05-16
> **bhaddow said:**
> Hi

I'm having a problem connecting with the same card. The card seems to be recognised
```

$ sudo lsusb | grep Ral
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```But after configuring the device and trying to connect, it just times out:
```

$ sudo dhclient wlan0
Listening on LPF/wlan0/00:27:19:b9:a8:da
Sending on   LPF/wlan0/00:27:19:b9:a8:da
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```Here's the sequence of commands that I'm using
```

lsusb
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid annebarry
iwconfig wlan0 key 98f2c4dc5c
iwconfig wlan0 mode Managed
dhclient wlan0

```Any suggestions?

regards
BarryIt will never connect with manual methods if Network Manager is running on the system. Click the icon, see your network and connect.

---

### Post by chili555 on 2010-05-16
> **alcohol52 said:**
> Neither worked.
Connecting to the network is not a problem. The internet simply doesn't work. Tranfers rate in bytes per sec.

I think the signal strength is not a problem . I have no problem in windows. The signal strength is same.

Waiting for more input.................I have been googling for hours on rt73usb and slow speeds and I see complaints in Arch, Puppy, Ubuntu and virtually all distributions. For example: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180518](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.24/+bug/180518)

There are suggestions to download the *later* version from the rt2x00 project; however, since rt2500usb and rt73usb are in the mainline kernel, the external rt2x00 project has been dormant for some time.

I notice there is a newer version in *linux-backports-modules-generic* so you might install it and reboot; see if it improves things.

Beyond that, I think it's a poor driver. You could try ndiswrapper or you could bring your device over to the house and I'll run over it with my truck.

---

### Post by bhaddow on 2010-05-17
Hi

I want to run this machine as a server, so I don't log in to the gui, I just hitted ctr-alt-f1 at the login screen to drop down to a terminal. So I don't think network manager is running, but I'll check that later.

As an aside, when I did log into the gui, I didn't see any icons on the panel when I logged in. No main menu, network manager or anything. I didn't really investigate, because I don't intend running the gui.

regards
Barry

---

### Post by chili555 on 2010-05-17
> So I don't think network manager is running, but I'll check that later.Check with:```
ps aux | grep Network
```> lsusb
ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
iwconfig wlan0 essid annebarry
iwconfig wlan0 key 98f2c4dc5c
iwconfig wlan0 mode Managed
dhclient wlan0All you really need is:```
iwconfig wlan0 essid annebarry
iwconfig wlan0 key 98f2c4dc5c
dhclient wlan0
```In my attempts to overpower NM, I have had limited success if I also populated /etc/network/interfaces:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid annebarry
wireless-key 98f2c4dc5c
```If you want to run as a server, don't you want a static IP? Do we have a new can of worms?

Post back if we can help further.

---

### Post by alcohol52 on 2010-05-17
**Light of hope...............**
> **chili555 said:**
> Y
```
sudo iwconfig wlan0 power off
```Any improvement? We might also try encryption in software and not hardware:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```Any improvement?

Both of these are temporary; if one or both work, we will need to tweak one file to make them effective on boot.


*** Which files are to  tweaked*** ***to turn of power management and encryption off? ***
Here is the output from **Puppy** linux:
[COLOR=Red]**1. i****wconfig:**[/COLOR]
[HTML]wlan0     IEEE 802.11abg  ESSID:"B....link"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:19:BE:1F:B3:98   
          Bit Rate=5.5 Mb/s   Tx-Power=24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]So **you seemed to be on  right track**. Disabling them permanently may work.
[B][COLOR=Red]2.lsmod|grep rt
[/COLOR][/B][COLOR=Black]rt73usb                25584  0 
rt2x00usb              11308  1 rt73usb
rt2x00lib              29388  2 rt73usb,rt2x00usb
input_polldev           3764  1 rt2x00lib
led_class               4112  1 rt2x00lib
mac80211              166056  2 rt2x00usb,rt2x00lib
cfg80211               64972  2 rt2x00lib,mac80211
crc_itu_t               1836  1 rt73usb
agpgart                34188  2 intel_agp
parport_pc             29828  1 
parport                34508  2 lp,parport_pc
**usbcore               138160  7 rt73usb,rt2x00usb,usb_storage,usbhid,uhci_hcd,ehci_hcd**
[/COLOR][COLOR=Black]
Was Usbcore running in Ubuntu? 
I am writing this from Puppy linux and I haven't given up. If it worked in Puppy linux it will work in Ubuntu too, isn't it? I don't think the drivers are too poor as the same are being used in Puppy linux.

[/COLOR]

---

### Post by alcohol52 on 2010-05-18
Puppy linux 5.0 is just released.
Guess what?
Those suckers based  it on Ubuntu Lucid.
My modem **no longer** works in Puppy Linux now.

---

### Post by bhaddow on 2010-05-18
Hi

I've disabled network manager, and verified that it's not running, but I still get the same behaviour when I try to connect. When I run dhclient it sends out DHCPDISCOVER and gets no response.

Configuring with a static ip should be straightforward once I get a connection - I can always do this on the router,


best regards
Barry

---

### Post by alcohol52 on 2010-05-21
Update.
Finally I am able to connect to internet in ubuntu using Ndiswrapper.
I blacklisted rt2500usb and rt73usb drivers and used xp drivers in Ndiswrapper. Works fine but a not 100% as in windows.

---

### Post by alcohol52 on 2010-06-06
I got  a live cd of ubuntu intrepid. Heck! the device works out of  box. No hassle.
What is the problem in karmic and lucid? Anyone there to help me?

---

### Post by cariboo on 2010-06-06
Check and see what driver it is using when running on the Intrepid Live CD. Then load the same driver using **lsmod** in Karmic/Lucid.

---

