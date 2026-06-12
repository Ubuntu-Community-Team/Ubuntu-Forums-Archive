---
title: "Rt2870sta wireless driver regression"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by itsjareds on 2010-09-01
Ok, I'm using a fresh install of Maverick to test it out, and I'm getting dropouts with my wireless. My wireless card, a Rosewill RNX Easy-N1 (Rt2870sta chipset), plugs into USB. The problem has been haunting me for a few days that it would randomly disconnect itself from the USB and not scan anymore as if it were completely unplugged. Finally this morning I got some relevant dmesg output:

```
[230821.365440] <--- RTMPFreeTxRxRingMemory
[230821.635869] <-- RTMPAllocTxRxRingMemory, Status=0
[230821.638881] -->RTUSBVenderReset
[230821.639005] <--RTUSBVenderReset
[230821.922919] 1. Phy Mode = 0
[230821.922923] 2. Phy Mode = 0
[230821.963424] 3. Phy Mode = 0
[230821.971553] MCS Set = 00 00 00 00 00
[230822.047682] <==== rt28xx_init, Status=0
[230822.049185] 0x1300 = 000a4200
[230832.752009] wlan0: no IPv6 routers present
[244604.375873] lo: Disabled Privacy Extensions
[244612.473572] usb 1-1: USB disconnect, address 5
[244612.473656] Bulk In Failed. Status=-108, BIIdx=0x0, BIRIdx=0x0, actual_length= 0x0
[244612.473788] rtusb_disconnect: unregister usbnet usb-0000:00:1d.7-1
[244612.473793] RtmpOSNetDevDetach(): RtmpOSNetDeviceDetach(), dev->name=wlan0!
[244612.483626] device disconnected
[244612.483630] CMDTHREAD_RESET_BULK_IN: Read Register Failed!Card must be removed!!
```

Following the last message, tons of "Disconnected" messages were output until I plugged it back in. This driver worked perfectly in Lucid. There was one change, however. When installing Maverick, I didn't have to remove module rt2800usb (conflicting wireless driver) to enable my rt2870sta driver. It was already enabled by default and I was able to connect automatically.

Not sure what else I can do, perhaps I will need to submit a bug report then compile the driver myself. Any tips?

---

### Post by Elfy on 2010-09-01
moved to maverick - please post maverick issues in it's forum

---

### Post by itsjareds on 2010-09-02
Sorry, I looked briefly for the forum but it wasn't on the main page.. didn't think to look in Development + Programming.

---

### Post by cariboo on 2010-09-02
Is the rt2800usb installed, or is it blacklisted?

---

### Post by itsjareds on 2010-09-02
Oh sorry, I forgot to mention that is installed, but I tried
```
sudo rmmod rt2800usb rt2x00usb
ERROR: Module rt2800usb does not exist in /proc/modules
ERROR: Module rt2x00usb does not exist in /proc/modules
```

So the module is not loaded, right?

---

### Post by cariboo on 2010-09-02
You can list the loaded modulues by using lsmod for example, in your case you would type:

```
lsmod | grep rt2800usb
```

If the module is inserted, will be listed in the results.

---

### Post by itsjareds on 2010-09-03
Nothing came up for that command. I haven't had this issue for a while, so hopefully with the updates that I've run, the issue has been solved already.

---

### Post by Tracy177 on 2010-09-03
i will tell you something :)

i have rt2870 and yes u need to use sta driver to make it work 


i did installed it the thing is that this card isnt supported well or something every 5 sec internet disconected or couldnt obtain ip or identification failed 


better give up it wont work properly in ubuntu i tried to make it work for a long time 

there is two drivers at the moment for this card one called rt2800usb and the other rt2970sta none is working

---

### Post by itsjareds on 2010-09-03
It's working fine for me right now, I'm using it to write this post. It's worked fine for me since Jaunty 9.04

---

### Post by ktp on 2010-09-03
> **itsjareds said:**
> It's working fine for me right now, I'm using it to write this post. It's worked fine for me since Jaunty 9.04

can you mark the thread "sloved" then...thanks.

---

### Post by itsjareds on 2010-09-04
It's not solved since I get random dropouts... I'm just currently waiting for another dropout to occur. If I don't get another dropout in 24 hours I will mark it as solved.

---

