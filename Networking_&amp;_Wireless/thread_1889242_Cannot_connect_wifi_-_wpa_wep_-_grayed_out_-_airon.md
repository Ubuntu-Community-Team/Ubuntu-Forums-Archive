---
title: "Cannot connect wifi - wpa wep - grayed out - aironet - thinkpad T41"
date: 2011-12-01
forum: Networking &amp; Wireless
---

### Post by krack3rz on 2011-12-01
So the problem is I cannot connect wo my wifi network with my laptop: thinkpad T41

Steps taken so far and info:
1. updated lubuntu, latest, installed latest updates (with a wire, and installed off a usb ~550MB image)
2. on the bottom right network manager applet, looked at the networks, many grayed out, including mine (wpa personal), some aren't grayed out, ie hpsetup (some network printer, not mine)
3. installed wicd, tried connecting, failed. Tried all the wpa options, checked the encrypt box since it complained about it, says bad password: (gets stuck at validating authentication) and then on bot. right says: connections failed: bad password
4. I changed my router wifi to wep, no changes, same msg, even though i typed it all right and checked...
5. gave up after going to the internet for answers, finding none that help or work.

I read online many things that can help, so heres some codes and outputs that may help:

```
lspci | grep -i net
```
> 02:02.0 Network controller: AIRONET Wireless Communications Cisco Aironet Wireless 802.11b

```
iwconfig
```
> 
eth1      IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/100  Signal level=-70 dBm  Noise level=-88 dBm
          Rx invalid nwid:217876  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3118565   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/100  Signal level=-70 dBm  Noise level=-88 dBm
          Rx invalid nwid:217876  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:3118565   Missed beacon:0


```
lsmod
```
> Module                  Size  Used by
dm_crypt               11331  0 
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
joydev                  8740  0 
snd_intel8x0           25652  1 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
thinkpad_acpi          68083  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  13 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  0 
nsc_ircc               18220  0 
psmouse                63677  0 
led_class               2864  1 thinkpad_acpi
ppdev                   5259  0 
soundcore               6620  1 snd
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  2 yenta_socket,rsrc_nonstatic
airo                   67901  0 
nvram                   6203  1 thinkpad_acpi
serio_raw               3978  0 
irda                  186844  1 nsc_ircc
crc_ccitt               1339  1 irda
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
parport_pc             25962  1 
shpchp                 28835  0 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
radeon                678735  3 
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
intel_agp              24375  1 
video                  17375  0 
drm                   163651  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
e1000                  97435  0 
output                  1871  1 video
agpgart                31724  3 ttm,intel_agp,drm


```
cat /etc/network/interfaces
```
> 
auto lo
iface lo inet loopback


```
rfkill list all
```
NO Output

```
sudo iwlist scan
```
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:23:69:65:5A:30
                    ESSID:"My Network"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=36/100  Signal level=-77 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

wifi0     Scan completed :
          Cell 01 - Address: 00:23:69:65:5A:30
                    ESSID:"My Network"
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality=33/100  Signal level=-79 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```
ifconfig
```
> eth0      Link encap:Ethernet  HWaddr 00:11:25:11:f8:aa  
          inet addr:1.1.1.106  Bcast:1.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:25ff:fe11:f8aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17413 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:13612352 (13.6 MB)  TX bytes:1097683 (1.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:0e:9b:91:d5:23  
          inet6 addr: fe80::20e:9bff:fe91:d523/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:178551 dropped:0 overruns:0 frame:178551
          TX packets:219 errors:209 dropped:0 overruns:0 carrier:0
          collisions:4 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:18466 (18.4 KB)
          Interrupt:11 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7104 (7.1 KB)  TX bytes:7104 (7.1 KB)


```
dmesg | grep -i 'eth1'
```
[http://pastebin.com/NXgkCDhr]("http://pastebin.com/NXgkCDhr")

This is probably a bit redundant but:
dmesg | grep -i 'airo'
ht tp://pastebin.com/u4BL66Zb

If anything else I can do let me know :)

Any takers?

---

### Post by praseodym on 2011-12-01
Hi,

maybe the driver only works with WEP encryption, your network is WPA(1). Typo in the URL of the second pastebin ;-)

---

### Post by chili555 on 2011-12-01
I doubt that's the issue. His pastebin says:>   11.196744] airo(eth1): Firmware version 5.41.00
[   11.196748] airo(eth1): [COLOR="Red"]WPA supported.[/COLOR]
[   11.196751] airo(eth1): MAC enabled 00:0e:9b:91:d5:23
[   21.796214] eth1: no IPv6 routers present
[   46.088516] airo(eth1): link lost (local choice)However, let's check:```
sudo iwlist eth1 auth
```This is troubling to me:> [   49.139808] airo(eth1): cmd:1 status:7f01 rsp0:88 rsp1:ff10 rsp2:c0f0
[   49.139817] airo(eth1): Bad MAC enable reason=88, rid=ff10, offset=49392
[   49.140582] airo(eth1): cmd:2 status:7f02 rsp0:0 rsp1:ff10 rsp2:c0f0
[   49.141698] airo(eth1): cmd:1 status:7f01 rsp0:88 rsp1:ff10 rsp2:c0f0I am Googling.

Is this a PCMCIA card? If so, please do:```
sudo modprobe airo_cs
```Any improvement?

---------------

Nota bene: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/network-managers-strange-relationship-with-wpa_supplicant-787633/page2.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/network-managers-strange-relationship-with-wpa_supplicant-787633/page2.html)

---

### Post by krack3rz on 2011-12-01
```
sudo iwlist eth1 auth
```
> eth1      unknown authentication information.

```
sudo modprobe airo_cs
```
No output...


Another piece of info, I added a connection in "Edit Connections" (wireless) accessed from the panel applet, inputted all the info correctly, then clicked apply.
It asked if I wanted to add it to keyring and I did by inputting my pass. Now every time I boot into my comp it asks for pass, I input it to unlock keyring, it prompts me to input my wireless pass and channel, but channel is grayed out and has no num. inside, and theres no box in which I can input it, so all i can do is press cancel, nothing i can press, this was before installing wicd, not sure if I can reproduce and get a screen shot.

---

### Post by chili555 on 2011-12-01
> it prompts me to input my wireless pass and channel,Channel??? We don't need no steenking channel! Please let us see a screenshot. I wonder if you have inadvertently set up an ad-hoc computer-to-computer network.

Let's try:```
sudo iwlist wifi0 auth
```

---

### Post by krack3rz on 2011-12-01
```
sudo iwlist wifi0 auth
```
> wifi0     unknown authentication information.

I'll try getting a screenshot but not sure if i can get it now.


Edit: also its not ad-hoc, since it is set to "Infrastructure"
gotta be something else :/

---

### Post by krack3rz on 2011-12-01
ok so I got a screenshot, and I was a bit off when I described it,

[IMG]http://img844.imageshack.us/img844/8601/201112011847541024x768s.png[/IMG]

---

### Post by chili555 on 2011-12-01
I have not used Wicd in a while. Is that a drop-down to select the encryption protocol, in this case WPA, or is it a fill-in box to supply the WPA password? Can you select WPA and be challenged for the password?

---

### Post by krack3rz on 2011-12-01
> **chili555 said:**
> I have not used Wicd in a while. Is that a drop-down to select the encryption protocol, in this case WPA, or is it a fill-in box to supply the WPA password? Can you select WPA and be challenged for the password?


That screenshot is not of wicd, before I installed it, this happened when I originally added my network manually.

The setup is correct, I checked.
That thing shows up after I enter my pass into the keyring unlock

In wireless tab, not of wicd, I entered my pass and wpa is chosen correctly just as I have done in the past to another laptop, running ubuntu.

---

### Post by krack3rz on 2011-12-01
Heres an image, maybe it'll help...
Its of my wireless connections

[IMG]http://img213.imageshack.us/img213/6434/201112012037251024x768s.png[/IMG]

---

### Post by chili555 on 2011-12-02
In your images, is 'wlan' actually the name of your network as verified in sudo iwlist scan? It should be.

---

### Post by krack3rz on 2011-12-02
> **chili555 said:**
> In your images, is 'wlan' actually the name of your network as verified in sudo iwlist scan? It should be.

No, my wifi network name isnt in the images, also I editted the Network name slightly in "sudo iwlist scan" (after output - changed 1 word), doesn't change anything though...


I guess u're out of ideas huh...



Also, I'm gonna try booting this laptop off a usb running ubuntu 10.04, will let u know if I can connect normally as I do off my other laptop

---

### Post by krack3rz on 2011-12-04
So I booted Ubuntu 10.04 off a CD and the result is the same, some connections are grayed out.

Also I booted openSUSE 11.4 off a CD and it doesnt even give me a choice to connect with anything other than wep.

This has gotta be a driver thing, or a kernel thing.
I do realize that the AIRONET hardware I got is crap, but I have 3 laptops exactly like this and if one cant be fixed, I might as well throw then away :(


If this helps: I read somewhere that this can be fixed if the kernel is recompiled and something that I couldnt understand is done. I didnt save the page, if I find again I will post but dont count on it.

Thanks for all ure help so far.

---

### Post by chili555 on 2011-12-05
I don't think the Cisco Aironet card is crap. It's old which is what you'd expect. The T41 in which it came is old. Features that were not yet invented couldn't have been built in to the hardware. I resolved this by replacing the card in my T40 with the expected whitelist and no1802 issues.

There are several things we can try. First, be sure your wireless router is set to WPA and not WPA2. Stick with TKIP and not AES. I realize that you scans show this, but you have also changed settings trying to connect. Be sure the default is WPA-TKIP.

Second I notice your ethernet has a (funky) IP address. Network Manager is designed to disallow a wireless connection if wired is available. Are the results the same with the ethernet detached?

Next, we can examine what the system logs say about connection (with the ethernet cable detached):```
sudo cat /var/log/syslog | grep -e etwork -e eth1 -e wifi -e airo | tail -n20
```If the output is sparse; less than 20 lines, look in:```
sudo cat /var/log/syslog**.1** | grep -e etwork -e eth1 -e wifi -e airo | tail -n20
```Last, we can compile a newer driver as outlined in this link: [http://www.linuxquestions.org/questions/linux-wireless-networking-41/network-managers-strange-relationship-with-wpa_supplicant-787633/page2.html](http://www.linuxquestions.org/questions/linux-wireless-networking-41/network-managers-strange-relationship-with-wpa_supplicant-787633/page2.html)

I will write separate instructions for the compile in a few minutes.

---

### Post by chili555 on 2011-12-05
> I will write separate instructions for the compile in a few minutes.Here you go. First, hook up an ethernet connection so we can grab some needed files. Open a terminal and do:

```
sudo apt-get install linux-headers-generic build-essential subversion
cd Desktop
svn co http://svn.gna.org/svn/airo-wpa/branches/kernel airo-wpa
cd airo-wpa/
sudo su
make
modprobe -r airo
cp -b airo.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/airo

```
Those tickmarks are on the left side of my US keyboard on the same key with ~. This process is specific to your running kernel. If you get a kernel update, repeat this process. See below.
Now finish with:

```
depmod
modprobe airo wpa_enabled=1
exit

```
Detach the ethernet. Now does it connect? If so, we'll need one more tweak to make it persistent.

-------------

Process to build module after a kernel update:```
cd Desktop/airo-wpa
sudo su
make clean
make
modprobe -r airo
cp -b airo.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless/airo
depmod
modprobe airo wpa_enabled=1
exit
```

---

