---
title: "WNDA3100v2 on Ubuntu 12.10 not working"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by bruti on 2013-01-08
I post now after having many issues, and after trying many of the posted solutions on this website and off of it.
Some include:
[http://ubuntuforums.org/showthread.php?t=1383708](http://ubuntuforums.org/showthread.php?t=1383708)
[http://ubuntuforums.org/showthread.php?t=1797795](http://ubuntuforums.org/showthread.php?t=1797795)
[http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)

lsusb indicates that the ID for NeatGear, Inc. WNDA3100v2 is 0846:9011

I am currently bridging a connection from my laptop to my PC (PC is what needs the wireless adapter to work).

I need Ubuntu to work on my PC for school, otherwise I would remain on Windows there and just use ubuntu on my laptop.

Edited to add:
I already have ndiswrapper installed.  When I type ndiswrapper -l, I get:

bcmn43xx64 : driver installed
device (0846:9011) present

sudo modprobe ndiswrapper never does anything.  I type it in, and then it goes to a new line and sits there.  I can't even enter more commands after that.

---

### Post by chili555 on 2013-01-08
>  I type it in, and then it goes to a new line and sits there. I can't even enter more commands after that.That can't be good. What does this tell us?```
dmesg | grep ndis
cat /var/log/syslog | grep ndis
```I suspect your ndiswrapper version and 64-bit are at war.

---

### Post by bruti on 2013-01-08
It might be worth noting that I am new to Linux.

dmesg | grep ndis
```

[   34.892262] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[   35.544331] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   35.544398] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   35.544463] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   35.544530] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   35.544596] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[   35.544661] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   35.544727] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   35.544794] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   35.544861] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   35.544930] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[   35.544997] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   35.545076] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[   35.545166] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   35.545260] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[   35.545352] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   35.545442] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[   35.545535] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   35.545626] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[   35.545717] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[   35.545809] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[   35.545903] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   35.545995] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   35.546091] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   35.546183] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   35.546275] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   35.546370] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   35.546461] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   35.546542] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   35.546635] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   35.546737] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[   35.546829] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[   35.546920] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[   35.547012] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[   35.547103] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh6'
[   35.547247] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh6'
[   35.547364] usbcore: registered new interface driver ndiswrapper
[ 1547.824671] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[ 1547.824680] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[ 1547.824686] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[ 1547.824694] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[ 1547.824700] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[ 1547.824706] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[ 1547.824712] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[ 1547.824718] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[ 1547.824723] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[ 1547.824732] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[ 1547.824741] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[ 1547.824746] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[ 1547.824752] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[ 1547.824760] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMPauseComplete'
[ 1547.824765] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[ 1547.824771] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisCancelTimerObject'
[ 1547.824777] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[ 1547.824782] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisSetTimerObject'
[ 1547.824788] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeTimerObject'
[ 1547.824795] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateTimerObject'
[ 1547.824801] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[ 1547.824806] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[ 1547.824820] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[ 1547.824826] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[ 1547.824832] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[ 1547.824837] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[ 1547.824843] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[ 1547.824853] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[ 1547.824859] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[ 1547.824871] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[ 1547.824876] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[ 1547.824881] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[ 1547.824885] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[ 1547.824887] ndiswrapper (load_sys_files:199): couldn't prepare driver 'bcmwlhigh6'
[ 1547.824978] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh6'
[ 1623.003160] usbcore: deregistering interface driver ndiswrapper
[ 1623.007323] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[ 1623.009513] usbcore: registered new interface driver ndiswrapper
[ 1634.081616] usbcore: deregistering interface driver ndiswrapper
[ 1634.084836] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
[ 1798.751658]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 1798.751680]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 1798.751707]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 1798.751771]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 1798.751783]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 1918.607658]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 1918.607682]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 1918.607712]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 1918.607780]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 1918.607793]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2038.463594]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2038.463617]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2038.463646]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2038.463714]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2038.463726]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2158.319588]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2158.319612]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2158.319641]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2158.319709]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2158.319721]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2278.175541]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2278.175565]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2278.175593]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2278.175659]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2278.175671]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2398.031506]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2398.031530]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2398.031559]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2398.031627]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2398.031639]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2517.887479]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2517.887503]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2517.887532]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2517.887599]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2517.887611]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2637.743446]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2637.743470]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2637.743499]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2637.743566]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2637.743579]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2757.599431]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2757.599455]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2757.599484]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2757.599553]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2757.599565]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 2877.455425]  [<ffffffffa0d9ed79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 2877.455449]  [<ffffffffa0dae48b>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 2877.455480]  [<ffffffffa0daef83>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 2877.455548]  [<ffffffffa0da0282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 2877.455560]  [<ffffffffa0e2f0a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]

```

cat var/log/syslog | grep ndis
```
cat: var/log/syslog: No such file or directory
```

---

### Post by chili555 on 2013-01-08
> cat: var/log/syslog: No such file or directoryIt is actually:```
cat [COLOR="Red"]/[/COLOR]var/log/syslog
```However, we see all we regrettably need to see above. I only mentioned it because all the slashes, etc. are crucial. When you see a no such thing error, it means one of us made a typo and double-check your and my work.

> [COLOR="Red"]ndiswrapper version 1.58rc1[/COLOR] loaded (smp=yes, preempt=no)
[   35.544331] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   35.544398] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   35.544463] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   35.544530] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMResetComplete'You are not too much of a beginner if you compiled 1.58rc1 then. Did you get a lot of warnings when you compiled it? I just now compiled 1.58rc1 on my 64-bit system and it went perfectly. I haven't the wireless device, so I can test no further. 

You might try recompiling:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
```Post back your errors, warnings, etc. and we'll try to troubleshoot them.

---

### Post by bruti on 2013-01-08
> **chili555 said:**
> 
You are not too much of a beginner if you compiled 1.58rc1 then. Did you get a lot of warnings when you compiled it? I just now compiled 1.58rc1 on my 64-bit system and it went perfectly. I haven't the wireless device, so I can test no further. 

You might try recompiling:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
```Post back your errors, warnings, etc. and we'll try to troubleshoot them.

I was following someone's instructions on compiling it.  I did the code you suggested, and everything installed without errors.  The sudo modprobe ndiswrapper is still yielding the same results.

---

### Post by chili555 on 2013-01-08
Your dmesg says:> ndiswrapper (load_sys_files:199): couldn't prepare driver '[COLOR="Red"]bcmwlhigh6[/COLOR]'
[ 1547.824978] ndiswrapper (load_wrap_driver:121): couldn't load driver 'bcmwlhigh6'However, ndiswrapper -l says:> [COLOR="Red"]bcmn43xx64[/COLOR] : driver installed
device (0846:9011) presentI wonder if you have two conflicting .inf and .sys files loaded. Let's see:```
ls /etc/ndiswrapper
```Since it complains about bcmwlhigh6, if there is a file in the above called bcmwlhigh6, then I suggest you do:```
sudo ndiswrapper -e bcmwlhigh6
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```Any improvement?

---

### Post by bruti on 2013-01-08
```
ls /etc/ndiswrapper
bcmn43xx64

```The high6 doesn't seem to be there.

Edit:  The adapter is working out of the blue.  I am using it right now for my internet source.  I had to unplug my power source because the Shut Down and Restart options on Ubuntu simply sent me to the login screen, rather than shutting down or restarting the computer (any idea what caused that?).

Anyway, I am going to give this a day or two before I mark the thread as solved -- simply because it started working for reasons I can't figure out.

I see you posting in a lot of threads helping users out.  Thank you for being so diligent in your efforts, the ubuntu community is better for it.

---

### Post by chili555 on 2013-01-09
> Thank you for being so diligent in your efforts, the ubuntu community is better for it.Thank you so much for your kind words. I enjoy what I do and this makes it even more so.

Glad it's working and post back if we can help you further.

---

### Post by bruti on 2013-01-13
After a couple days of testing, I have found some issues.  The issues are mostly in my windows partition, however.  Everytime I log into my windows account, my wireless adapter switches its security type from WPA2 to WPA.  I have to manually switch this and enter the password multiple times before I can connect.  I'm not sure why this is happening.

---

### Post by chili555 on 2013-01-14
Is your home network set up in WPA and WPA2 mixed mode as many are? You will probably have better luck with it set to WPA2 only. Here, for example, is a scan at my location with some names redacted;> Wireless Access Points (* = current AP)
    piper:       Infra, xx:1B:5E:EE:0C:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    mahb:            Infra, xx:1D:D4:73:FF:xx, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Home:            Infra, xx:86:3B:38:D4:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 [COLOR="Red"]WPA WPA2[/COLOR]
    dlink:           Infra, xx:18:E7:D1:C8:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 30
    *GBR1:           Infra, xx:13:10:62:8D:xx, Freq 2462 MHz, Rate 54 Mb/s, Strength 51 WPA2
    ATT9999:         Infra, xx:44:01:07:21:xx, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    2WIRE:        Infra, xx:22:A4:53:31:xx, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WEP

---

### Post by bruti on 2013-01-19
It is not.  It is set up exclusively in WPA2 only.  However, that problem is unrelated to Ubuntu it seems.  I'm going to mark this as solved.  Thank you for your help.

---

### Post by bruti on 2013-01-21
It was set to WPA2 online when I logged into the router.  However, it has stopped working.
Recently, I have:

- installed updates
- suspended the desktop and resumed later
- switched from WPA2 to WPA/WPA2 back to WPA2 (was testing)

Can't seem to make the USB wifi adapter work anymore.

---

### Post by chili555 on 2013-01-21
> **bruti said:**
> It was set to WPA2 online when I logged into the router.  However, it has stopped working.
Recently, I have:

- installed updates
- suspended the desktop and resumed later
- switched from WPA2 to WPA/WPA2 back to WPA2 (was testing)

Can't seem to make the USB wifi adapter work anymore.Was one of the updates a later linux-image version? If so, please re-compile ndiswrapper:```
cd Desktop/ndiswrapper-1.58rc1
sudo su
make clean
make
make install
modprobe ndiswrapper
exit
```Now does it work? If not, please post:```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by bruti on 2013-01-22
After posting, I had the idea of re-compiling.  I typed that exact string of commands (as you suggested prior), and also dide the sudo modprobe command.  It was working after that.  I'll do a bit more testing before I post next time.

Thanks again, chili555.

If anyone happens on this thread by a search and has a similar issue with the adapter working, and then not working (if it seems random or not) -- try to recompile the driver!

---

