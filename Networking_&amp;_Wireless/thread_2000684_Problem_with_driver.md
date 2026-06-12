---
title: "Problem with driver"
date: 2012-06-09
forum: Networking &amp; Wireless
---

### Post by nobody914 on 2012-06-09
Hello Everyone. I have a problem installing my realtek 8188se driver for my backtrack 5r1 system. When i run make i get these errors:

root@bt:~/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011# make
make -C /lib/modules/2.6.39.4/build M=/root/Desktop/rtl_92ce_92se_92de_linux_mac80211_0005.1230.2011 modules
make: *** /lib/modules/2.6.39.4/build: No such file or directory.  Stop.
make: *** [all] Error 2

Can anyone tell me what the fix might be?
Thank you in advance.

---

### Post by chili555 on 2012-06-10
Do you have *linux-headers-generic* and *build-essential* installed? Please do so and try again.

---

### Post by nobody914 on 2012-06-10
> **chili555 said:**
> Do you have *linux-headers-generic* and *build-essential* installed? Please do so and try again.

 I have build essential 4.0 but I do not have Linux-headers and it looks like there are several versions of headers in synaptic. I am running backtrack 5r1 so which version should i install. Also the driver that is installed is called wext and it does recognize my realtek 8188ce but it losses connection after a short period. I had the same problem with ubuntu 10 and used the 8192se driver and it worked perfect. How do i uninstall the wireless drivers so that when i get the 8192se driver installed there will not be any conflict?:) Thanks. I will wait for your reply.

---

### Post by chili555 on 2012-06-10
I'm not at all familiar with Backtrack. I understood it's based on Ubuntu. Ubuntu has a package called linux-headers-generic that removes the guesswork. It could be renamed 'linux-headers-whateverIneed.' 

If Backtrack doesn't have a similar package, then you should install headers matching your running kernel version. The Linux shorthand for that is *uname -r*. So you could do:```
sudo apt-get install linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.> Also the driver that is installed is called wext and it does recognize my realtek 8188ce but it losses connection after a short period.Are you sure? Please check:```
lsmod | grep wext
```I believe wext is a helper for wpa_supplicant; not a wireless driver. Let's check again:```
lsmod | grep 8192
```

---

### Post by nobody914 on 2012-06-10
> **chili555 said:**
> I'm not at all familiar with Backtrack. I understood it's based on Ubuntu. Ubuntu has a package called linux-headers-generic that removes the guesswork. It could be renamed 'linux-headers-whateverIneed.' 

If Backtrack doesn't have a similar package, then you should install headers matching your running kernel version. The Linux shorthand for that is *uname -r*. So you could do:```
sudo apt-get install linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.Are you sure? Please check:```
lsmod | grep wext
```I believe wext is a helper for wpa_supplicant; not a wireless driver. Let's check again:```
lsmod | grep 8192
```

Yes you are right about wext being a WPA supplicant. There must be a driver installed however because it does pick up my wireless network. Anyhow I will install headers and see what happens then. Thanks.

---

### Post by nobody914 on 2012-06-10
> **nobody914 said:**
> Yes you are right about wext being a WPA supplicant. There must be a driver installed however because it does pick up my wireless network. Anyhow I will install headers and see what happens then. Thanks.


Ok, I decided to remove Backtrack for various other reasons. I have it on USB as well as virtual box
 I downloaded Ubuntu 12.04 LTS and I have it on USB right now. IT does see my wireless network but it will not connect. It tries over and over but it does'nt seem to make the connection. I have it wired right now. What i want to do is install it on my computer as a duel boot with my Win 7 OS but I want to make sure I can get everything working first. Can you help me figure out the wireless issue?  Also how do i open up a terminal in 12.4. Sorry for the change in venue but Backtrack 5 has issues and I can play with that in vbox. Thank you for your help.

---

### Post by chili555 on 2012-06-10
> Also how do i open up a terminal in 12.4.Click the Dash in the upper left and type in 'term.' It will offer several terminals and you can safely just use 'terminal.' Please see attached.

When you open it, let's see what driver is loaded:```
lsmod | grep 819
```Now let's see if there are any errors associated with the driver:```
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by nobody914 on 2012-06-10
> **chili555 said:**
> Click the Dash in the upper left and type in 'term.' It will offer several terminals and you can safely just use 'terminal.' Please see attached.

When you open it, let's see what driver is loaded:```
lsmod | grep 819
```Now let's see if there are any errors associated with the driver:```
dmesg | grep 819
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Ok, here is the driver info,

ubuntu@ubuntu:~$ lsmod | grep 819
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash

Here is the info from the second command i typed dmesg | grep 819
ubuntu@ubuntu:~$ dmesg | grep 819
[    3.997819] system 00:04: [io  0x1000-0x1003] has been reserved
[   46.376789] rtl8192ce 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   46.376800] rtl8192ce 0000:06:00.0: setting latency timer to 64
[   46.936987] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   47.391466] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   67.353508] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[   98.660864] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  150.248714] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  156.921231] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  209.159631] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  261.084534] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  336.936166] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  376.877623] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  426.797086] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  486.704075] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  492.610103] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  498.664469] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  504.718307] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  510.775836] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  516.835852] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  522.902724] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  528.957941] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  535.022295] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  541.077342] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  547.136931] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  562.999080] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  569.055661] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  575.113768] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  581.171081] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  587.225449] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  593.284077] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  599.348899] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  605.406909] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  611.471901] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  617.526924] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  625.930662] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  631.989015] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  638.039698] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  644.098819] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  650.155328] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  656.216017] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  662.270486] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  668.329253] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  674.387831] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  680.448634] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  689.341830] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  695.399320] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  701.452514] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  707.507625] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  713.571287] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  719.627156] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  725.686918] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  731.753625] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  737.809101] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  743.876233] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  756.422961] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  762.482011] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  768.534293] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  774.595208] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  780.649731] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  786.717890] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  792.772547] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  798.827813] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  804.892369] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  810.951022] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  840.272504] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  846.333566] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  852.388371] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  858.455165] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  864.510902] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  870.570417] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  876.626686] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  882.685316] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  888.736527] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  894.797131] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  912.109312] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  918.162428] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  924.224972] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  930.279007] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  936.332738] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  942.400541] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  948.451657] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  954.514325] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  960.575176] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  966.637113] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  976.218753] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  982.277616] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  988.330003] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[  994.388813] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1000.453233] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1006.512090] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1012.566749] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1018.639207] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1024.695876] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1030.763142] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1036.826626] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1040.181213] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1046.238583] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1052.302561] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1058.357452] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1064.414442] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1070.468783] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1076.527642] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1082.587701] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1088.654727] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1094.709004] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1145.683540] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1205.590077] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1265.496902] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1325.404764] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1385.311776] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1445.218205] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1505.126031] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1565.033490] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1624.939952] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1684.847398] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1744.754203] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1804.662241] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1864.568873] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1924.476643] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 1984.383902] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2044.291066] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2104.198355] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2164.105570] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2224.012886] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2283.919595] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2343.826959] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2403.734435] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2463.641706] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2523.549253] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2583.455758] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2643.363435] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2703.270251] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2763.177395] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2823.085218] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2882.992204] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 2942.899565] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3002.806504] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3062.714114] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3122.620343] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3182.528507] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3242.434837] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3302.342629] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3362.250178] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3422.156465] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3482.064372] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3541.971846] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3601.878231] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3661.785905] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3721.693254] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3781.600486] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3841.507418] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3901.415000] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 3961.322040] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4021.229358] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4081.136592] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4141.043687] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4200.950888] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4260.858195] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4320.765595] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4380.672457] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4440.579319] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4500.486806] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4560.394318] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4620.301502] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4680.208204] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4740.115971] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4800.023192] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4859.930374] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4919.837184] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 4979.744776] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5039.652117] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5099.559259] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5159.466522] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5219.373759] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5279.281008] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5339.188226] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5399.095432] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5459.001896] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5518.909869] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5578.816962] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5638.724131] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5698.631474] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5758.538567] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5818.445525] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5878.352588] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5938.260257] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 5998.167570] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6058.074884] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6117.982209] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6177.889223] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6237.796415] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6297.703718] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6357.611003] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6417.517963] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6477.425317] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6537.332543] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6597.239129] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6657.146524] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6717.054171] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6776.961408] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6836.868633] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6896.775902] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 6956.682558] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7016.590388] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7076.496955] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7136.404804] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7196.311650] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7256.219263] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7316.125661] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7376.033509] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7435.940450] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7495.848019] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7555.755163] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7615.662061] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7675.569036] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7735.476193] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7795.383052] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7855.291398] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7915.198784] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 7975.105961] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8035.012713] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8094.919777] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8154.826897] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8214.734224] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8274.642008] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8334.549302] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8394.456476] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8454.363577] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8514.270702] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8574.178163] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8634.084649] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8693.992558] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8753.899730] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8813.806797] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8873.714137] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8933.621318] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 8993.527753] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9053.435314] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9113.342810] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9173.249730] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9233.156676] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9293.064418] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9352.971403] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9412.879024] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9472.785908] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9532.693833] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9587.805123] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9652.530290] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9712.432989] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9772.339966] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9832.246680] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9892.154625] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[ 9952.062130] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10011.966234] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10071.876176] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10131.783665] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10191.690641] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10251.597859] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10311.505228] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10371.412438] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10431.319502] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10491.226421] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10551.134016] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10611.041336] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10670.948474] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10730.855705] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10790.762873] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10850.670043] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10910.577310] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[10970.484503] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11030.391330] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11090.299014] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11150.206132] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11210.113408] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11270.020669] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11329.927505] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11389.835125] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11449.742491] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11509.649448] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11569.556721] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11629.463707] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
[11689.371377] rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.bin
ubuntu@ubuntu:~$

---

### Post by chili555 on 2012-06-10
> rtl8192c_common: Loading firmware file rtlwifi/rtl8192cfw.binDoes the file exist?```
ls /lib/firmware/rtlwifi
```I will be away for the evening; see you tomorrow.

---

### Post by nobody914 on 2012-06-10
> **chili555 said:**
> Does the file exist?```
ls /lib/firmware/rtlwifi
```I will be away for the evening; see you tomorrow.

Here are the results i got after typing in the last command you gave:

ubuntu@ubuntu:~$ ls /lib/firmware/rtlwifi
rtl8192cfw.bin  rtl8192cufw.bin  rtl8192defw.bin  rtl8192sefw.bin  rtl8712u.bin

We'll finish this another time then. Have a good evening.:popcorn:

---

### Post by chili555 on 2012-06-11
Please try a temporary parameter. If it helps, we'll write one file and make it persistent.```
sudo modprobe -r rtl8192ce
sudo modprobe rtl8192ce swenc=1
```May I see:```
iwconfig
```Thanks.

---

### Post by nobody914 on 2012-06-11
> **nobody914 said:**
> Here are the results i got after typing in the last command you gave:

ubuntu@ubuntu:~$ ls /lib/firmware/rtlwifi
rtl8192cfw.bin  rtl8192cufw.bin  rtl8192defw.bin  rtl8192sefw.bin  rtl8712u.bin

We'll finish this another time then. Have a good evening.:popcorn:
After rebooting moden and router everything works fine. Connection made. Thanks for your input with this matter.):P

---

