---
title: "[need help] modem driver for haier D1200P"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by freakyjohn101 on 2008-12-22
hello everyone,
i have a problem installing modem driver from haier D1200P in my xubuntu OS, can anyone help me?

* My OS is XUBUNTU 7.10 and most of it have been upgraded to xubuntu 8.04, the kernel is still using 2.6.22-generic from xubuntu 7.10.

* My modem is a mobile phone from haier D1200P, it's vendor and product id is: vendor=0x15eb product=0x0001. On windows it detected as VIA Telecom Modem.

* I already tried some of the suggestion that exist in this forum, modem device is working properly in windows, in linux it's already detected when i used modprobe usbserial vendor=0x15eb product=0x0001, i always see this in my dmesg:
[  159.217122] usbcore: registered new interface driver usbserial
[  159.217157] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  159.217178] usbcore: registered new interface driver usbserial_generic
[  159.217183] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/serial/usb-serial.c: USB Serial Driver core
[  179.683612] usb 1-1: new full speed USB device using ohci_hcd and address 2
[  179.896563] usb 1-1: configuration #1 chosen from 1 choice
[  179.902502] usbserial_generic 1-1:1.0: generic converter detected
[  179.902870] usb 1-1: generic converter now attached to ttyUSB0
[  179.905631] usbserial_generic 1-1:1.1: generic converter detected
[  179.905986] usb 1-1: generic converter now attached to ttyUSB1

but when i use wvdial, it cannot detect the modem. sometime wvdialconf can detect the modem but most of the time it cannot detected it.

* Some of the people that using mandriva 2008.1 can easily install it, but people using ubuntu variant having trouble detecting it.

* So.. my question is, how to fix it? why the modem is working in windows but not in xubuntu? (i can't using mandriva 2008.1 now because there's so many work i've done in my xubuntu and i really hate to reinstall the whole thing), what were the programs that directly control the modem and can i just upgraded them or i have to install the new kernel version?

---

### Post by freakyjohn101 on 2008-12-22
here's the logfile that generated in windows when i checked the modem connection:
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\tapisrv.dll, Version 5.1.2600   
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\unimdm.tsp, Version 5.1.2600   
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\unimdmat.dll, Version 5.1.2600   
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\uniplat.dll, Version 5.1.2600   
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\drivers\modem.sys, Version 5.1.2600   
12-22-2008 09:55:35.020 - File: C:\WINDOWS\System32\modemui.dll, Version 5.1.2600   
12-22-2008 09:55:35.030 - File: C:\WINDOWS\System32\mdminst.dll, Version 5.1.2600   
12-22-2008 09:55:35.030 - Modem type: VIA Telecom CBP USB Modem
12-22-2008 09:55:35.030 - Modem inf path: oem3.inf
12-22-2008 09:55:35.030 - Modem inf section: ViaUsbModem
12-22-2008 09:55:35.030 - Matching hardware ID: usb\vid_15eb&pid_0001&mi_00
12-22-2008 09:55:36.032 - 230400,8,N,1, ctsfl=0, rtsctl=1
12-22-2008 09:55:37.033 - Initializing modem.
12-22-2008 09:55:37.344 - Send: ATZE0Q0V1<cr>
12-22-2008 09:55:37.354 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:37.354 - Interpreted response: OK
12-22-2008 09:55:37.364 - Send: ATE0Q0V1<cr>
12-22-2008 09:55:37.364 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:37.364 - Interpreted response: OK
12-22-2008 09:55:37.374 - Send: AT<cr>
12-22-2008 09:55:37.374 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:37.374 - Interpreted response: OK
12-22-2008 09:55:37.374 - Sending user initialization commands.
12-22-2008 09:55:37.384 - Send: at+crm=1;+cmux=1;+cps=33;+cta=0<cr>
12-22-2008 09:55:37.394 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:37.394 - Interpreted response: OK
12-22-2008 09:55:37.394 - Waiting for a call.
12-22-2008 09:55:37.404 - Send: ATS0=0<cr>
12-22-2008 09:55:37.404 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:37.404 - Interpreted response: OK
12-22-2008 09:55:37.404 - 230400,8,N,1, ctsfl=0, rtsctl=1
12-22-2008 09:55:38.405 - Initializing modem.
12-22-2008 09:55:39.347 - Send: ATZE0Q0V1<cr>
12-22-2008 09:55:39.347 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:39.357 - Interpreted response: OK
12-22-2008 09:55:39.367 - Send: ATE0Q0V1<cr>
12-22-2008 09:55:39.367 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:39.367 - Interpreted response: OK
12-22-2008 09:55:39.377 - Send: AT<cr>
12-22-2008 09:55:39.377 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:39.377 - Interpreted response: OK
12-22-2008 09:55:39.377 - Sending user initialization commands.
12-22-2008 09:55:39.387 - Send: at+crm=1;+cmux=1;+cps=33;+cta=0<cr>
12-22-2008 09:55:39.397 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 09:55:39.397 - Interpreted response: OK
12-22-2008 09:55:39.397 - Dialing.
12-22-2008 09:55:39.407 - Send: ATDT####<cr>
12-22-2008 09:55:41.490 - Recv: <cr><lf>CONNECT<cr><lf>
12-22-2008 09:55:41.490 - Interpreted response: Connect
12-22-2008 09:55:42.341 - Receive Connect but CD was low, Waiting for signal to go high
12-22-2008 09:55:43.342 - CD has been raised
12-22-2008 09:55:43.342 - Connection established at 230400bps.
12-22-2008 09:55:43.342 - Error-control off or unknown.
12-22-2008 09:55:43.342 - Data compression off or unknown.
12-22-2008 09:56:13.345 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 09:58:13.347 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:00:13.350 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:02:13.353 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:04:13.355 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:06:13.358 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:08:13.360 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:10:13.363 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:12:13.365 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:14:13.368 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:16:13.370 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:18:13.373 - Read: Total: 0, Per/Sec: 0, Written: Total: 0, Per/Sec: 0
12-22-2008 10:18:23.658 - Hanging up the modem.
12-22-2008 10:18:24.298 - Hardware hangup by lowering DTR.
12-22-2008 10:18:26.301 - Detected CD dropped from lowering DTR
12-22-2008 10:18:27.303 - Timed out waiting for response from modem
12-22-2008 10:18:27.313 - Send: ATH<cr>
12-22-2008 10:18:27.313 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:27.313 - Interpreted response: OK
12-22-2008 10:18:27.313 - 230400,8,N,1, ctsfl=0, rtsctl=1
12-22-2008 10:18:28.314 - Initializing modem.
12-22-2008 10:18:29.316 - Send: ATZE0Q0V1<cr>
12-22-2008 10:18:29.316 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:29.316 - Interpreted response: OK
12-22-2008 10:18:29.326 - Send: ATE0Q0V1<cr>
12-22-2008 10:18:29.326 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:29.326 - Interpreted response: OK
12-22-2008 10:18:29.336 - Send: AT<cr>
12-22-2008 10:18:29.336 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:29.336 - Interpreted response: OK
12-22-2008 10:18:29.336 - Sending user initialization commands.
12-22-2008 10:18:29.346 - Send: at+crm=1;+cmux=1;+cps=33;+cta=0<cr>
12-22-2008 10:18:29.356 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:29.356 - Interpreted response: OK
12-22-2008 10:18:29.356 - Waiting for a call.
12-22-2008 10:18:29.366 - Send: ATS0=0<cr>
12-22-2008 10:18:29.366 - Recv: <cr><lf>OK<cr><lf>
12-22-2008 10:18:29.366 - Interpreted response: OK
12-22-2008 10:18:29.376 - Session Statistics:
12-22-2008 10:18:29.376 -                Reads : 0 bytes
12-22-2008 10:18:29.376 -                Writes: 0 bytes
ATQ0V1E0 - OK
AT+GMM - +GMM: "CBP4PLUS"
AT+FCLASS=? - +FCLASS: 0,2.0
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - COMMAND NOT SUPPORTED
AT+GCI=? - COMMAND NOT SUPPORTED
ATI1 - COMMAND NOT SUPPORTED
ATI2 - COMMAND NOT SUPPORTED
ATI3 - COMMAND NOT SUPPORTED
ATI4 - COMMAND NOT SUPPORTED
ATI5 - COMMAND NOT SUPPORTED
ATI6 - COMMAND NOT SUPPORTED
ATI7 - COMMAND NOT SUPPORTED
ATQ0V1E0 - OK
AT+GMM - +GMM: "CBP4PLUS"
AT+FCLASS=? - +FCLASS: 0,2.0
AT#CLS=? - COMMAND NOT SUPPORTED
AT+GCI? - COMMAND NOT SUPPORTED
AT+GCI=? - COMMAND NOT SUPPORTED
ATI1 - COMMAND NOT SUPPORTED
ATI2 - COMMAND NOT SUPPORTED
ATI3 - COMMAND NOT SUPPORTED
ATI4 - COMMAND NOT SUPPORTED
ATI5 - COMMAND NOT SUPPORTED
ATI6 - COMMAND NOT SUPPORTED
ATI7 - COMMAND NOT SUPPORTED

---

### Post by ieee488 on 2008-12-22
Whether a modem works in Windows or not is completely irrelvant to this discussion except to prove that the modem is not broken.

[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

---

### Post by freakyjohn101 on 2008-12-22
yup, i know it's irrelevant and yup i just show that log to prove that the modem is not broken, so if wvdialconf can't detect my modem (by the way in the cellphone there's qualcomm 3g cdma sign) what other modem detection tool that i can use?

---

### Post by annoe_yk on 2009-01-04
does anyone know the solution please? i'm having the same problem here..
thanks..

---

