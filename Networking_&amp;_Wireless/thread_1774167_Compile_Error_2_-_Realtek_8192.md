---
title: "Compile Error 2 - Realtek 8192"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Grimm Spector on 2011-06-02
I'm trying to install a wireless USB adapter to a machine so I can get it internet access, unfortunately when I try to run the provided install script I'm getting an error 2, and I've never encountered that before. In fact I'm getting another error which makes me concerned that they just failed at coding this driver...
 
```

/tmp/driver/Linux/driver/rtl8192CU_linux_v2.0.1170.20101112/core/rtw_pwrctrl.c:
In function 'LeaveAllPowerSaveMode':
/tmp/driver/Linux/driver/rtl8192CU_linux_v2.0.1170.20101112/core/rtw_pwrctrl.c:712: error 'HAL_DATA_TYPE\ has no member named 'autosuspend_disabled'
make[2]: *** [/tmp/driver/Linux/driver/rtl8192CU_linux_v2.0.1170.20101112/core/rtw_pwrctrl.o] Error 1
make[1]: *** [_module_/tmp/driver/Linux/driver/trl8192CU_linux_v2.0.1170.20101112] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-2.6.32-28-generic'
make: *** [modules] Error 2
Compile make driver error: 2, Please check error Mesg
```
 
Something is clearly broken but I am not sure what, I'm awfully new to this, and wireless didn't really exist the last time I used Linux...though this doesn't appear to be specifically related to the wireless function of the driver, it's a make compile problem, it's just mysterious, any help would be highly appreciated.

---

### Post by gray bark on 2011-07-30
My problem was the same. After a little of messing around i changed one line in sourcecode and everything's fine.

Linux: Ubuntu 10.04
Driver:
rtl8192CU_linux_v2.0.1170.20101112.tar.gz
(the one from the cd i bought with the wlan stick)
File: core/rtw_pwrctrl.c
Function: LeaveAllPowerSaveMode
Line: 712
Adapter->dvobjpriv.pusbdev->autosuspend_disabled = pHalData->autosuspend_disabled;
change to:
Adapter->dvobjpriv.pusbdev->autosuspend_disabled = 0;

cu
gray bark

---

