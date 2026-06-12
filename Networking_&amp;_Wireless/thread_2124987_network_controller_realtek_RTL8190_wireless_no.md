---
title: "network controller realtek RTL8190 wireless no"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by betaniaho on 2013-03-12
hola he actualizado mi ubuntu a la versión 12.10 y no detecta la red inalambrica, tengo el controlador RTL8190, me pueden ayudar con este espantoso error por favor...saludos

---

### Post by chili555 on 2013-03-12
You will probably have better luck here: [http://www.ubuntu-es.org/forum/37#.UT-WzVGUx0w](http://www.ubuntu-es.org/forum/37#.UT-WzVGUx0w) However, if you'd like to proceed notwithstanding the language barrier, please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by stans on 2013-04-26
Chili555 - May I join this thread and request your assistance with getting my RTL8190 working ?

stan@stan-DX4300:~$ lspci -nn | grep 0280
05:05.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN [10ec:8190]

Ndiswrapper recognizes the driver, but the card cannot 'see' my network.

Thanks for your assistance.

---

### Post by chili555 on 2013-04-26
> **stans said:**
> Chili555 - May I join this thread and request your assistance with getting my RTL8190 working ?

stan@stan-DX4300:~$ lspci -nn | grep 0280
05:05.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8190 802.11n Wireless LAN [10ec:8190]

Ndiswrapper recognizes the driver, but the card cannot 'see' my network.

Thanks for your assistance.What does this tell us?```
ndiswrapper -l
sudo modprobe ndiswrapper
dmesg | grep ndis
```

---

### Post by stans on 2013-04-26
stan@stan-DX4300:~$ ndiswrapper -l
net819xp : driver installed
	device (10EC:8190) present
stan@stan-DX4300:~$ sudo modprobe ndiswrapper
stan@stan-DX4300:~$ dmesg | grep ndis
[   15.410301] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   15.763407] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   15.763415] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   15.763420] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   15.763425] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   15.763433] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   15.763437] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   15.763442] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   15.763455] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   15.763459] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   15.763464] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   15.763475] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   15.763482] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   15.763487] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   15.763491] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   15.763498] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   15.763509] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   15.763513] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   15.763518] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   15.763524] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   15.763529] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   15.763534] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   15.763541] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   15.763545] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   15.763553] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   15.763558] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   15.763563] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   15.763567] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   15.763572] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   15.763577] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   15.763582] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   15.763584] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net819xp'
[   15.763654] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net819xp'
[   15.763752] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2013-04-27
That doesn't look at all happy, does it? I recommend you install ndiswrapper-1.58. Please check here: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981)

---

### Post by stans on 2013-04-27
I've downloaded and installed the 'essentials' then downloaded and installed the new verson of ndiswrapper however the old version keeps coming up. I have rebooted but it doesn't help.


Thank you for your assistance.

---

### Post by chili555 on 2013-04-27
> **stans said:**
> I've downloaded and installed the 'essentials' then downloaded and installed the new verson of ndiswrapper however the old version keeps coming up. I have rebooted but it doesn't help.

Do I need to delete the old version with pkg mgr ?

Thank you for your assistance.When you 'sudo make install' the 1.58 version, it should overwrite the old 1.57 version. You might then try a reboot and then do:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Look for 1.58 and not 1.57.

---

### Post by stans on 2013-04-27
Yes - I rebooted and re-issued those commands and got the screenful of bad msgs - and it was the 1.57 version that loaded.

---

### Post by chili555 on 2013-04-27
We shouldn't have to do this, but, hey, nothing succeeds like brute force:```
sudo apt-get remove --purge ndiswrapper*
sudo rm -rf /etc/ndiswrapper/*
cd Desktop/ndiswrapper-1.58
sudo su
make clean
make
make install
ndiswrapper -i [COLOR="#FF0000"]wherever[/COLOR]/net819xp.inf  [COLOR="#FF0000"]<--wherever the inf and sys files are on your system[/COLOR]
modprobe ndiswrapper
exit
dmesg | grep ndis
```*NOW* is it 1.58??

---

### Post by stans on 2013-04-27
This is where I get frustrated.

root@stan-DX4300:/etc/ndiswrapper# ndiswrapper -i Desktop/net819xp.inf
couldn't open Desktop/net819xp.inf: No such file or directory at /usr/sbin/ndiswrapper line 219.

On the plus side - 

stan@stan-DX4300:~$ dmesg | grep ndis
[   15.146550] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.316612] usbcore: registered new interface driver ndiswrapper
stan@stan-DX4300:~$

---

### Post by chili555 on 2013-04-27
> root@stan-DX4300:[COLOR="#FF0000"]/etc/ndiswrapper[/COLOR]# ndiswrapper -i [COLOR="#FF0000"]Desktop/net819xp.inf[/COLOR]That asks for the system to install from /etc/ndiswrapper/Desktop/net819xp.inf. Desktop isn't there; it is in /home/stan or some such. Change directories back to /home/stan from root which you are:```
[COLOR="#FF0000"]root[/COLOR]@stan-DX4300:/etc/ndiswrapper[COLOR="#FF0000"]#[/COLOR] 
```Use this command:```
cd /home/stan 
```Your prompt should now read:> root@stan-DX4300:/home/stan#List the contents of the directory:```
ls
```Is Desktop one of the directories listed? Good! Now proceed:```
ndiswrapper -i Desktop/net819xp.inf
```And continue.

---

### Post by stans on 2013-04-27
So far so good. I am very fortunate to have your assistance... and am a bit frustrated cause there is still so much to learn. Now I'll see if a reboot gets my wifi up and running. This is a dual boot Gateway with W7 as the 'other' boot. I bought this a few years ago and never cared about the wifi card that was in it. Now that I have W7 wireless thought it would be cool to get Ubuntu also wireless, and just unplug the 10BaseT cable.

---

### Post by stans on 2013-04-27
OK - guess there are still things to do.

---

### Post by chili555 on 2013-04-27
> **stans said:**
> OK - guess there are still things to do.Did ndiswrapper load on boot?```
lsmod | grep ndis
```If not load it:```
sudo modprobe ndiswrapper
```And get it to load automagically:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```After it's loaded, do you get a wireless interface, ideally wlan0?```
iwconfig
```Does it scan?```
sudo iwlist wlan0 scan
```Let me know your results and we'll proceed.

---

### Post by stans on 2013-04-27
stan@stan-DX4300:~$ lsmod | grep ndis
ndiswrapper           283384  0 
stan@stan-DX4300:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

stan@stan-DX4300:~$ sudo iwlist wlan0 scan
[sudo] password for stan: 
wlan0     Interface doesn't support scanning.

stan@stan-DX4300:~$

---

### Post by chili555 on 2013-04-27
As always, let's check the message log for clues:```
dmesg | grep ndis
ndiswrapper -l
```

---

### Post by stans on 2013-04-27
stan@stan-DX4300:~$ dmesg | grep ndis
[   15.178625] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   15.348570] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   15.348578] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   15.348584] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   15.348589] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   15.348597] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   15.348602] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   15.348606] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   15.348620] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   15.348625] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   15.348629] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   15.348641] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   15.348648] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   15.348653] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   15.348658] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   15.348665] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   15.348676] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   15.348680] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   15.348685] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   15.348692] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   15.348697] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   15.348701] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   15.348709] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   15.348713] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   15.348722] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   15.348727] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   15.348732] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   15.348736] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   15.348741] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   15.348746] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   15.348751] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   15.348753] ndiswrapper (load_sys_files:199): couldn't prepare driver 'net819xp'
[   15.348818] ndiswrapper (load_wrap_driver:121): couldn't load driver 'net819xp'
[   15.348928] usbcore: registered new interface driver ndiswrapper
stan@stan-DX4300:~$

stan@stan-DX4300:~$ ndiswrapper -l
net819xp : driver installed
	device (10EC:8190) present
stan@stan-DX4300:~$

---

### Post by chili555 on 2013-04-27
Is your a 32- or 64-bit systm?```
arch
```Where did you get the .inf and, I assume, .sys files? Windows XP, I hope and matching your architecture??

---

### Post by stans on 2013-04-27
Both files came from my Windows 7 system. (Dual boot system - and the same wifi card works when windows 7 is up).

There are a variety of .sys and .inf files of different lengths on the Windows 7 system which makes me now wonder if that is the problem. 

Where is a good place to get them from ? The realtek site ?

---

### Post by chili555 on 2013-04-28
ndiswrapper is designed to use the XP files, and rarely W2k, but not 7 or 8 or any other.> Where is a good place to get them from ? The realtek site ? That's what I'd suggest. Post back if you get stuck.

---

### Post by stans on 2013-04-28
Thank you very much for your assistance.

---

### Post by stans on 2013-04-28
I've downloaded both .inf and .sys files from the realtek site and it doesn't make a difference. Isn't the .inf file a text file that can be read with either more or gedit ?

---

### Post by chili555 on 2013-04-28
> Isn't the .inf file a text file that can be read with either more or gedit ? Yes. Does it says it's for x86 or is it x86_64 and XP?

---

### Post by stans on 2013-04-28
It does NOT state which architecture on the realtek site. With gedit the .inf file looks like garbage.

---

### Post by stans on 2013-04-28
Any suggestion on where I can find the 64 bit downloads ? Have been chasing forum threads, just downloaded Samsung items... and still garbarge in the .inf file. Am I missing something obvious here ?

Just copied another set from the Windows 7 system - with 'AMD64' comments in the .inf file and still garbage trying to read with gedit. Perhaps I am not copying it correctly while in Windows ?

---

### Post by stans on 2013-04-28
(deleted).

---

### Post by chili555 on 2013-04-28
You can read the inf files with vim, which you may need to install:```
sudo apt-get install vim
vim Desktop/some_folder/net819xp.inf
```Look for any declarations of x86 or x64.> Any suggestion on where I can find the 64 bit downloads ? How about the manufacturers (of the wireless card) website? We can probably extract any exe files. Do you have a link?

---

### Post by stans on 2013-04-28
You missed where I said I was at the realtek site and had no way of knowing what the correct driver was. The don't identify 32 or 64 bit. 


[www.realtek.com](www.realtek.com) - correct ?

---

### Post by chili555 on 2013-04-28
I guess I misunderstood this:> and still garbarge in the .inf file. I thought that meant you didn't know if you had a 32- or 64-bit file. No?

Try this.

---

### Post by stans on 2013-04-28
Thanks... but now I have a new problem in that the system won't shut down. 

Ah well... the joy of it all.

stan@stan-DX4300:~$ sudo su
[sudo] password for stan: 
root@stan-DX4300:/home/stan# ndiswrapper -i Desktop/net819xp.inf
driver net819xp is already installed
root@stan-DX4300:/home/stan# dmesg | grep ndis
[   16.241582] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  241.096092]  [<ffffffffa0358d48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  241.096106]  [<ffffffffa0368487>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  241.096119]  [<ffffffffa0368db0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  241.096270]  [<ffffffffa035a28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  241.096279]  [<ffffffffa03e2073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  361.096094]  [<ffffffffa0358d48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  361.096108]  [<ffffffffa0368487>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  361.096121]  [<ffffffffa0368db0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  361.096271]  [<ffffffffa035a28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  361.096279]  [<ffffffffa03e2073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  481.096086]  [<ffffffffa0358d48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  481.096100]  [<ffffffffa0368487>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  481.096113]  [<ffffffffa0368db0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]
[  481.096263]  [<ffffffffa035a28d>] loader_init+0x9d/0x150 [ndiswrapper]
[  481.096271]  [<ffffffffa03e2073>] wrapper_init+0x73/0x1000 [ndiswrapper]
[  601.096108]  [<ffffffffa0358d48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  601.096122]  [<ffffffffa0368487>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  601.096136]  [<ffffffffa0368db0>] wrap_pnp_start_pci_device+0x60/0x90 [ndiswrapper]

root@stan-DX4300:/home/stan# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@stan-DX4300:/home/stan# sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

root@stan-DX4300:/home/stan#

---

### Post by chili555 on 2013-04-29
> root@stan-DX4300:/home/stan# ndiswrapper -i Desktop/net819xp.inf
driver net819xp is already installedI gave you a new 64-bit net819xp above. Before we install it, we need to erase the old one:```
sudo ndiswrapper -e net819xp
sudo rm -rf /etc/ndiswrapper/*
```Next, if you have two different .inf and .sys files on your desktop, how is ndiswrapper going to tell the old, not working files from the new 64-bit files? When I uploaded the file, it was compressed in a folder called 64bit. I hope you right-clicked it to extract it. Then, you need to do:```
sudo ndiswrapper -i Desktop/64bit/net819xp.inf
```Any complaints or errors? How does the message log look now?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by stans on 2013-04-29
stan@stan-DX4300:~$ sudo ndiswrapper -e net819xp
[sudo] password for stan: 
stan@stan-DX4300:~$ sudo rm -rf /etc/ndiswrapper/*
stan@stan-DX4300:~$ sudo ndiswrapper -i Desktop/64bit/net819xp.inf
installing net819xp ...
stan@stan-DX4300:~$ ndiswrapper -l
net819xp : driver installed
	device (10EC:8190) present
stan@stan-DX4300:~$ dmesg | grep ndis
[   15.961533] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
stan@stan-DX4300:~$ 

Yes, right clicked what you sent. I guess you do deal with all types in this forum...  

EDIT: I rebooted after this - then a few moments later got a cleared screen, several lines appeared with hex values then too quickly to read much more the screen turned into 'snow'. I rebooted using an older kernel but at this point with all due apologies will bail out of the project mainly cause I already have a running Ubuntu system (no wireless) sitting next to this one. No real need to have two. Will format the drive and redirect primary boot to the Windows 7 system. I was originally going to load another distro but realized that I have more than enough to keep me busy. I will add a wireless 'card' later to the other system - and selection will be based on what I know will work out of the box. Thank you so very much for all the time and effort you put into helping me. I did learn a lot about ndiswrapper...

---

### Post by chili555 on 2013-04-30
I am sorry the project didn't work out. The RTL8190 is a pretty rare device and we have no control here over the drivers that may be available, either native or ndiswrapper. 

There are many threads here about devices that work out of the box and I suggest you search carefully before you buy.

---

### Post by stans on 2013-04-30
A final note about buying unsupported devices - way back early in this thread I mentioned that the wireless card was in the Gateway machine that I got on sale. I did NOT buy it and install it. I full well realize one of the main weaknesses of linux (if you want to call it a weakness) is lack of support by manufacturers. As my boss stated - "the world is windows" and this is unfortunate. I know that TPLINK makes a wireless that works on Mint and should work on Ubuntu so I will eventually get to that. 

Thanks again for your kind support. Hopefully someday I can return the favor. If you need any mainframe support let me know !

---

