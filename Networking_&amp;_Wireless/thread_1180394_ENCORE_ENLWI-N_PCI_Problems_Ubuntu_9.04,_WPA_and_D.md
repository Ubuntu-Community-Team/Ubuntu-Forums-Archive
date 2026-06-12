---
title: "ENCORE ENLWI-N PCI Problems: Ubuntu 9.04, WPA and Drivers"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by Matt_Rapp on 2009-06-06
Hi all,

I recently picked up an Encore ENLWI-N Wi-Fi card from [**_Newegg _**]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052")when it was on sale because it was cheap and was recommended in reviews as working well in Linux.

However, as I've been trying to replace my old eHome EH 102 wireless g card without much success. 

The ENLWI-N is based on the Ralink RT2860 chipset, and while there is no official support for Linux, both [**_Encore _**]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=2&pid=269")and [**_Ralink_**]("http://www.ralinktech.com/ralink/Home/Support/Linux.html") have Linux drivers that you can compile on your own.

I downloaded the driver supplied by Ralink and installed it following directions in a [**_Linux Mint forum post _**]("http://forums.linuxmint.com/viewtopic.php?f=53&t=15156"). 

After I restarted, the card was recognized and network manager showed the correct available networks, but I could not log into my home WPA2-PSK AES network. I found this weird because network manager should have saved the passphrase from my old card. I went into the wireless settings and changed the passphrase back, it was a strange string of numbers and letters originally. The card still could not connect and times out. I also tried connecting to a neighborhood open network and that failed too.

I knew that when I compiled the driver it installed as a new model but I figured I would give ndiswrapper a chance. The provided CD only had a .exe file, so I installed it on a Windows machine and then copied the entire driver's folder```
"C:\Program Files\None\802.11n PCI Wireless LAN Card\Driver"
``` over to Ubuntu. It has both the .inf and .sys files. I found the .inf file in ndiswrapper, installed it and got a pop up error saying ```
Unable to see if hardware is present.
``` but then once I hit okay the driver had Hardware present:Yes underneath its listing. Network manager did not recognize the card or show any networks. 

I decided to try and go back to my old EH 102 card, which I had previously installed with ndiswrapper. The same "Unable to see if hardware is present" thing happened again with similar results. 

I thought that the ENLWI-N driver I had previously compiled was screwing ndiswrapper up in both cases, but when I ran ```
lshw -C Network
``` as instructed [**_here_**]("http://ubuntuforums.org/showthread.php?t=885847") it correctly listed ndiswrapper for both driver= and module=

I would rather use my new card but also would like to be able to fall back on the EH102 if I have to.

Did I screw up when compiling the driver the first time? I'm pretty sure I followed the Linux mint directions exactly. What new module was created and how should I go about removing it before I try again? I think if I can remove the current module I'll start again with the driver supplied by Encore, all thought its included readme instructions are a bit more complicated.

My current installed modules and other system information is below. This is with the EH102 card in my system; see below for the ENLWI-N.
```
matt@Matt-Ubuntu:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12032  1  
nls_cp437              13696  1  
vfat                   18816  1  
fat                    58272  1 vfat 
ndiswrapper           193436  0  
isofs                  39844  1  
udf                    87716  0  
crc_itu_t              10112  1 udf 
binfmt_misc            16776  1  
video                  25360  0  
output                 11008  1 video 
input_polldev          11912  0  
sbp2                   30476  0  
lp                     17156  0  
ppdev                  15620  0  
snd_intel8x0           37532  3  
snd_ac97_codec        112292  1 snd_intel8x0 
ac97_bus                9856  1 snd_ac97_codec 
snd_pcm_oss            46336  0  
snd_mixer_oss          22656  1 snd_pcm_oss 
snd_pcm                82948  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
snd_seq_dummy          10756  0  
snd_seq_oss            37760  0  
snd_seq_midi           14336  0  
snd_rawmidi            29696  1 snd_seq_midi 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              29704  2 snd_pcm,snd_seq 
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
k8temp                 12416  0  
pcspkr                 10496  0  
snd                    62628  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore              15200  1 snd 
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm 
nvidia               4712596  32  
i2c_nforce2            14980  0  
agpgart                42696  1 nvidia 
parport_pc             40100  1  
parport                42220  3 lp,ppdev,parport_pc 
usbhid                 42336  0  
forcedeth              61712  0  
ohci1394               38576  0  
ieee1394               94660  2 sbp2,ohci1394 
usb_storage            82880  1  
floppy                 64324  0  
fbcon                  46112  0  
tileblit               10752  1 fbcon 
font                   16384  1 fbcon 
bitblit                13824  1 fbcon 
softcursor              9984  1 bitblit 

matt@Matt-Ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:off/any   
          Mode:Managed  Channel:0  Access Point: Not-Associated    
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm   
          RTS thr=2346 B   Fragment thr=2346 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0  

matt@Matt-Ubuntu:~$ sudo lshw -c network 
  *-network                
       description: Wireless interface 
       product: 88w8335 [Libertas] 802.11b/g Wireless 
       vendor: Marvell Technology Group Ltd. 
       physical id: 6 
       bus info: pci@0000:04:06.0 
       logical name: wlan0 
       version: 03 
       serial: 00:19:5b:04:88:27 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.53+eHome,08/22/2005,3.2.1.3 latency=64 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

ENLWI-N Results
```
matt@Matt-Ubuntu:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
ra0       RT2860 Wireless  ESSID:""  Nickname:"RT2860STA" 
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated    
          Bit Rate:1 Mb/s    
          RTS thr:off   Fragment thr:off 
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

matt@Matt-Ubuntu:~$ sudo lshw -c network 
[sudo] password for matt:  
  *-network                
       description: Wireless interface 
       product: RT2800 802.11n PCI 
       vendor: RaLink 
       physical id: 6 
       bus info: pci@0000:04:06.0 
       logical name: ra0 
       version: 00 
       serial: 00:08:54:8b:ca:d2 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 module=rt2860sta multicast=yes wireless=RT2860 Wireless
```

---

### Post by Matt_Rapp on 2009-06-08
Anyone?

---

### Post by nate.s on 2009-06-09
Hey,I don't know the answer but do have the same card and situation. I have not done anything yet because I don't understand any of the programming I keep finding. Any help would be great.
Good luck
nate

---

### Post by Matt_Rapp on 2009-06-09
I don't know how to back track and start over either. I think that once I have sometime on my hands again I'll run a live CD and test out ndiswrapper with the driver I extracted from the .exe CD and then try compiling the driver supplied on Encores website. If one works I may have to just deal with it ant reinstall Ubuntu, but hopefully someone will have an idea before I have to.

Could someone decipher the readme file in [Encores driver package]("http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=2&pid=269#DOWNLOAD"), I can follow some of it but get lost only a third of the way in.

---

### Post by Matt_Rapp on 2009-06-10
I&#8217;ve done some work on a live CD and this is what I got,
9.04 recognizes the Encore card by default but cannot connect to WPA2 on its own, can connect to open networks though.
When installing the windows driver with ndiswrapper I still got the hardware not present error message, but nsdiswrapper &#8211;l  output ```

ubuntu@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netr28 : driver installed
	device (1814:0601) present (alternate driver: rt2860sta)
ubuntu@ubuntu:~$ 
```
WPA2 does not work with the ndiswrapper driver.

I tried figuring out how to compile the driver from Encore but I keep getting errors and don't really know how to do it, I am starting a new tread asking for help on how to compile the driver [**_here_**]("http://ubuntuforums.org/showthread.php?p=7433883#post7433883").

---

### Post by carcar1 on 2009-06-10
I don't know in 9.04 but in 8.10 ndiswrapper for me worked fine on my WPA2-personal.  I use this card naively from ubuntu 9.04 flawlessly.  Even gets better reception then windows on the same system.

I'll make a video since so many people are having problems with this wireless card.

---

### Post by carcar1 on 2009-06-10
Here you go hope this helps!

---

### Post by Matt_Rapp on 2009-06-10
I just tried it again with your .inf file and the same errors are showing up, and it still can't connect to WPA2 networks. See attached screen shots from the live version, so I don't have to worry about the old cards software. The readme does say that the driver was tested in Red Hat 7.3, but it should work for Linux kernel 2.6, which 9.04 is built on.

---

### Post by carcar1 on 2009-06-10
You see the live cd is different.  I have no clue why my card was picked up might be the mobo.  I'll have to fiddle around a bit to figure this out.

Did you make sure you installed the wpa2 supplicant?  Some chipsets are picked up wrong in ubuntu and wpa2 & wpa1 don't work.  Try this guide [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

---

### Post by Matt_Rapp on 2009-06-11
I found an old hard drive lying around and installed 9.04 clean on it. I tried your windows driver and mine, they didn’t work. Then checked to see if the WPA supplicant was installed, it was. I then took of WPA from my network and updated Ubuntu, installing everything. Both drivers still do not work with the encryption and now when they are installed the card is not even finding the secure networks, there isn’t even a wireless option under network manager. I also tried to follow the directions of [**_this _**]("http://ubuntuforums.org/showthread.php?t=966185")post under a different install and that failed as well. I may just have to go back to the old card until there is an update I guess, which really bums me out because I saw hundreds of reviews about how the card works great in Linux.

---

### Post by carcar1 on 2009-06-11
Do you have this card specifically? [http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180052")  I am currently trying new methods on Backtrack 3 & 4 and if I figure a way out that way I'll let you know.  I'll go check for madwifi drivers for you as well.

Try this guide might be long but might work.  [http://ubuntuforums.org/showpost.php?p=5062485&postcount=36]("http://ubuntuforums.org/showpost.php?p=5062485&postcount=36")

Can you tell me your hardware mobo etc?

---

### Post by Matt_Rapp on 2009-06-11
I have an older system, but it was pretty much free:

Motherboard:  ECS Elitegroup C51G-M754
Processor: AMD Sempron 3000+
Memory: 2GB DDR400

Here are some pictures of the card with its ID number and revision:

37NB-W40300+411
REV: 1.1

---

### Post by carcar1 on 2009-06-11
I really am stumped do you have skype?  So this way I can can help you when I actually do it with you.

---

### Post by Matt_Rapp on 2009-06-11
Okay I'll try the package, the only way I know how to completely get rid of everything is to do a reinstall, so that will take like 10 min. 

What driver should I use in ndiswrapper if the package doesn't work? I already got one from you, and extracted one from my CD and neither worked remember.


I don't think it is the PCI slot, I had my old adapter in that slot for 5 months and it worked fine, plus the new card can connect to open networks just fine.

---

### Post by kirby9 on 2009-10-11
I have the same exact problem and was wondering if you ever came across the solution?

Thanks

---

### Post by Matt_Rapp on 2009-10-11
Unfortunately no,

After trying everything listed in this thread and [this]("http://ubuntuforums.org/showthread.php?t=1183801") forked one, I eventually coincided defeat and reinstalled my old 802.11g card. I also fried that motherboard installing some bad ram a few months later, so I can't really try again. If I were you I'd do a clean install of Ubuntu on an old blank hard drive, plug into a wired network and follow the steps listed in both threads. That way you can easily restart if you mess up without losing any of the settings in your normal installation. There is at least 3 different ways of going about it, using the windows driver and ndiswrapper, compiling your own driver from the manufactures page, and then using the random package written by someone else. I think compiling the driver has the best chance of success if you know what your doing. Hope you have better luck than I did. :)

---

