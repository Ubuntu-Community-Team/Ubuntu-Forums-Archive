---
title: "Asus x501a rt3970 wireless chip problem (kernel panic)"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by jonny3010 on 2013-03-02
[COLOR=#000000]i have a Asus x501a rt3970 wireless chip and i installed thier rt2860 driver as the wifi driver using rt2800pci build was not very good bad signal etc. i went though the read me and compiled it etc and now i have it installed (rt2860) and working. but when the wifi chip gets a little bit of load i get kernel panic ive tryed this with ubuntu 12.10 and linux mint 14.[/COLOR]

[COLOR=#000000]Does any know now how to fix this?[/COLOR]

[COLOR=#000000]Many Thanks[/COLOR]
[COLOR=#000000]Jonny[/COLOR]

---

### Post by chili555 on 2013-03-02
The driver rt2800pci is built in to the kernel by default in 12.10. There is no reason to compile anything. Let's do some diagnostics. Please run and post:```
lspci -nn | grep 0280
lsmod | grep rt2
```Thanks.

---

### Post by jonny3010 on 2013-03-02
> **chili555 said:**
> The driver rt2800pci is built in to the kernel by default in 12.10. There is no reason to compile anything. Let's do some diagnostics. Please run and post:```
lspci -nn | grep 0280
lsmod | grep rt2
```Thanks.

i reinstalled ubuntu as it was not use able at all. but if im near routor i get get alright wifi. i tryed the power managment trick and no luck but it did work on a linux mint live but when i installed linux mint then did it nothing happened :9

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]




rt2800pci              18528  0 
rt2800lib              58685  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14475  1 rt2800pci
rt2x00lib              54891  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              539908  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              206566  2 rt2x00lib,mac80211
eeprom_93cx6           13302  1 rt2800pci

with the rt2800pci i get this when about 2 meters away from the routor

wlan0     IEEE 802.11bgn  ESSID:"Proud"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:E2:15:55:1C:EC   
          Bit Rate=81 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:0   Missed beacon:0

but the bit rate goes down to 1 all the time

wlan0     IEEE 802.11bgn  ESSID:"Proud"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:E2:15:55:1C:EC   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:0   Missed beacon:0

wifi fine on my windows install

---

### Post by chili555 on 2013-03-02
Is there any improvement with N speeds turned off in the router?

---

### Post by jonny3010 on 2013-03-02
> **chili555 said:**
> Is there any improvement with N speeds turned off in the router?

wlan0     IEEE 802.11bgn  ESSID:"Proud"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:E2:15:55:1C:EC   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:14   Missed beacon:0

i changed the routor to G and now it get that in my room i was getting 1 MBPS. also my signal is 2 bars i get more on N becuase the range is better on N

2 meters form the routor i get 3bars and 24 or 36

so now it does not drop to 1MBPS and its faster but i should get 54 and full bars near routor

---

### Post by chili555 on 2013-03-02
Let's try a driver parameter:```
sudo modprobe -r rt2800pci
sudo modprobe rt2800pci nohwcrypt=Y 
```Any improvement?> also my signal is 2 bars i get more on N becuase the range is better on N...but with an occasional kernel panic??

---

### Post by jonny3010 on 2013-03-02
routor still on G and no change

wlan0     IEEE 802.11bgn  ESSID:"Proud"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:E2:15:55:1C:EC   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0

---

### Post by chili555 on 2013-03-02
'No change' meaning what? Meaning the number you read here seems insufficient?> wlan0 IEEE 802.11bgn ESSID:"Proud"
Mode:Managed Frequency:2.412 GHz Access Point: AC:E2:15:55:1C:EC
[COLOR="#FF0000"]Bit Rate=24 Mb/s [/COLOR]Tx-Power=20 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power ManagementffOr meaning that the connection is slow, unstable and causes kernel panics under load? How long did you try it?

---

### Post by jonny3010 on 2013-03-02
no change on anything, still the same as before

---

### Post by jonny3010 on 2013-03-02
works really well on the newer rt2860 driver but i get kernel panic when i load pages or using wget. so i reinstalled like i said

---

### Post by chili555 on 2013-03-02
If you reinstalled and *lsmod* shows that you are using rt2800pci, then what does rt2860 have to do with anything? My question for you is, after you loaded the driver parameter above, what exactly is not working? Your original question says kernel panics under load. Do you have that now? > when the wifi chip gets a little bit of load i get kernel panic ive tryed this with ubuntu 12.10 and linux mint 14.

---

### Post by jonny3010 on 2013-03-02
I when i tryed rt2860 the wifi was alot better and got really good signal  but as soon as i got some load on it i got kernel panic. so i reinstalled ubuntu to get the 2800 back. I tryed this on linux mint as well but then i though there the same thing nearly. so if there was a way to use rt2860 with out the kernel panic that would be great. that way my wifi would be good and be fast and great signal

---

### Post by chili555 on 2013-03-02
The driver rt2860sta is an old driver; development stopped when your device and many others were included in rt2800pci. I know of no way to get that antique to work in newer kernels such as 3.5.xx. 

I have been trying to help you troubleshoot the driver you *DO* have, rt2800pci. I have asked you twice about its performance with a driver parameter and twice I have gotten a reference to how your wireless device performed with rt2860sta, which won't work and isn't available. 

If you'd like to troubleshoot what you *do* have and what *does* work, at least, so far, partially, I'd be happy to help. If you want to tell me again how great rt2860sta was in the old days except for the occasional kernel panic, then I can't help you.

---

### Post by jonny3010 on 2013-03-07
sorry for late reply, but i changed my WiFi chip to a intel one and i get the same problem (is slightly better) could this be the router? thing is that it works fine in windows that what i cant get my head around.

---

### Post by chili555 on 2013-03-07
What is the problem? Slow? Unstable? Kernel panic? Is the driver iwlwifi?```
lsmod | grep iwl
```There are several driver parameters that we can try to help performance.

---

### Post by jonny3010 on 2013-03-07
sorry i should of said, its unstable the speed all over the place. signal poor as well is a lot better in windows. could it be the router like i said

Driver is iwlwifi

```
jonny@The-Doctor:~$ lsmod | grep iwliwldvm                241871  0
mac80211              549638  1 iwldvm
iwlwifi               161598  1 iwldvm
cfg80211              206741  3 iwldvm,mac80211,iwlwifi



```

---

### Post by chili555 on 2013-03-07
Let's see if a driver parameter helps:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```If it helps, we can write a file and make it persistent.

---

### Post by jonny3010 on 2013-03-07
no luck :( still the same. ive tryed this on the 3.7 kernel and 3.5

is there  away to update the driver ? (if thats worth doing)

it it make any difference moving to 12.04 LTS?

---

### Post by chili555 on 2013-03-07
> is there away to update the driver ?You could try the compat-wireless package; however...> (if thats worth doing)No, in my opinion. I have two or three Intel cards around here and I am using iwlwifi right now and it's rock solid in every respect, with or without compat-wireless. I am beginning to think this is the answer:> could this be the router? I'd set it to WPA2 only, not some mixed mode WPA and WPA2 and I'd provisionally try disabling N speeds. If I remember correctly, you've had three devices and two kernels with the same problem.

---

### Post by jonny3010 on 2013-03-08
yeah I'll try WPA2

EDIT: tryed other routor NETGEAR DGN2000 and i get same problem and tryed a 32bit os might try 12.04 now
edit: no change still got the problem
edit: looked in bois to see if there any think that messing around with the wireless.

---

### Post by jonny3010 on 2013-03-11
BUMP!! ive tryed updating the bios and no luck also tried solusos using 3.3.6 kernel (might be kernel?)

---

