---
title: "help with wireless"
date: 2012-10-01
forum: Networking &amp; Wireless
---

### Post by bjballar41 on 2012-10-01
Im new to ubuntu and am having problems connecting to wireless just keeps asking for my password. Ive done many searches on the web and cant get any solutions can anyone help?

---

### Post by Bucky Ball on 2012-10-01
Welcome.

We can try. Please open a terminal (Applications>Accessories>Terminal) and paste in these two commands:

```
sudo lshw -C network
iwconfig
```

... and copy/paste the output back here, thanks, between code tags (easiest to mark out the output code, hit the 'quote' icon then replace where it says [quote] with [code] at beginning and end)..

---

### Post by bjballar41 on 2012-10-01
should i be connected to my router by wire or no?

---

### Post by bjballar41 on 2012-10-01
*-network               
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:8b:0f:2c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:51 memory:de800000-de801fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 54:04:a6:46:5d:20
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:dd400000-dd43ffff ioport:a000(size=128)

---

### Post by bjballar41 on 2012-10-01
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

---

### Post by bjballar41 on 2012-10-02
Maybe I need an upgraded kernel?  Not sure what's going on

---

### Post by Bucky Ball on 2012-10-02
Follow this thread from post #5, ignoring references to Broadcom card. Should fix:

[http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

The gist is, run this:

```
sudo rmmod -f acer-wmi
```Restart and see if you get anything. If it works, run these three commands to make it persistent:

```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```If not, start digging here:

[http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8Qs_WpQ5V8AW0IK5gt.?p=WiMAX%206150%20ubuntu&fr=altavista&fr2=sfp]("http://au.yhs4.search.yahoo.com/yhs/search;_ylt=A7exU8Qs_WpQ5V8AW0IK5gt.?p=WiMAX%206150%20ubuntu&fr=altavista&fr2=sfp")

... as you have this wireless card: Centrino Wireless-N + WiMAX 6150

Known to be tricky but what release are you using? Looks like 12.04 and you are ready to go by the output of 'sudo lshw -C network' reporting this:
```

broadcast=yes driver=iwlwifi driverversion=3.2.0-31-generic firmware=41.28.5.1
```PS: Fix in link is for 11.04 but shouldn't make any diff. Incidentally, what is machine and model? ;)

---

### Post by bjballar41 on 2012-10-02
I'm using most recent I believe. I used the download from windows launcher 12.04.1 I believe. Ill give it a try and let u know. Asus u56e laptop

---

### Post by bjballar41 on 2012-10-02
Will this cause problems on the windows side I forgot to say I am dual booted

---

### Post by Bucky Ball on 2012-10-02
Has nothing to do with Windows.

---

### Post by bjballar41 on 2012-10-02
ok thanks ill get to work on it and report back

---

### Post by bjballar41 on 2012-10-02
ERROR: Removing 'acer_wmi': No such file or directory

that is what i keep getting

---

### Post by bjballar41 on 2012-10-02
does this mean i need to install the driver cause i check that additional driver and it doesnt have anything to install

---

### Post by bjballar41 on 2012-10-02
i think i got it fixed found another forum with different commands that fixed it not sure if i got it to work permanently tho

---

### Post by bjballar41 on 2012-10-02
it does not save it have to enter in code each time how do i save it i tried and it didnt

---

### Post by Bucky Ball on 2012-10-02
Let us know what you are doing and we might be able to figure how to make it permanent. Link to the site you're using and the code you're using to get wireless up, please.

---

### Post by bjballar41 on 2012-10-02
[http://ubuntuforums.org/showthread.php?t=1929304](http://ubuntuforums.org/showthread.php?t=1929304)

i tried the code they said to do to make it permanent but maybe im doing it wrong?

---

### Post by Bucky Ball on 2012-10-02
> That's a typo. Instead of gsku, you should use gksu, so:

gksu gedit /etc/modprobe.d/iwl.conf

From post #8 on that thread.

---

### Post by bjballar41 on 2012-10-02
after i put that one in it pops up with a new box and im not sure what to do after that

---

### Post by Bucky Ball on 2012-10-03
Well, did you follow the full fix from that thread and put that instruction in to replace the wrong one at the appropriate point? Or did you just run that command by itself?

The new box is Gedit, a text editor. You need to follow the fix to know what to do next. You are about to edit the file iwl.conf ...

---

### Post by bjballar41 on 2012-10-03
i did follow directions in full i put in the new code

gksu gedit /etc/modprobe.d/iwl.conf

after that it pops up with the box u called Gedit and i put in what they say

options iwlagn bt_coex_active=0

i save and exit but the wifi doesnt work after reboot or shutdown

---

### Post by Bucky Ball on 2012-10-03
But no errors? Odd. Well, that doesn't sound like the fix, perhaps. I'll keep thinking but no ideas for now ...

---

### Post by bjballar41 on 2012-10-03
the codes work but it just doesnt save so it does get the wifi working just cant save it im still looking also but cant find anything right now.

---

