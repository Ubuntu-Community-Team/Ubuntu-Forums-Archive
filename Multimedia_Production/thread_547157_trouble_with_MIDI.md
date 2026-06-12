---
title: "trouble with MIDI"
date: 2007-09-09
forum: Multimedia Production
---

### Post by scacinto on 2007-09-09
Hi, 
     I'm having some problems with a midisport 1x1.  I'm running UbuntuStudio with all the most recent updates. 

 I've installed the midisport-firmware, udev and fxload packages as per the instructions in the midisport-firmware readme.  From what I've gathered, the firmware should be automagically installed when I plug the device in, but this does not occur.

I have not been able to find a solution in these forums so far.  All help appreciated.

Thanks,

-Scacinto

---

### Post by scacinto on 2007-09-09
ick - got it!  sorry for the post - 

~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/001/005

solved it -- I suppose the auto-load thing is a myth?

anyhow, lights on.  

Thanks

S

---

### Post by theorganloft on 2007-10-20
> **scacinto said:**
> ick - got it!  sorry for the post - 

~/usbmidi$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/001/005

solved it -- I suppose the auto-load thing is a myth?

anyhow, lights on.  

Thanks

S

I GET THIS.

theorganloft@theorganloft:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0763:1010 Midiman Midisport 1x1
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
theorganloft@theorganloft:~$ sudo fxload -I /etc/firmware/ezusbmidi1x1.ihx -D /proc/bus/usb/005/002
[sudo] password for theorganloft:
/proc/bus/usb/005/002: No such file or directory
theorganloft@theorganloft:~$

---

### Post by TorchlightJay on 2007-10-21
try installing timidity. That program tends to help

---

### Post by consam on 2008-04-25
high everyone,

know it's a little delay but i'll write it for the commons.

instead of writing fxload ... /proc/ ... etc
           write              /dev/ 
proc means procedure but it's an device isn't it?
dev  means device.

so my 4x4 works.
but udev didn't load it up at systhemstart.
after this i read at the systhemprotocol, where i recognized that :

usbdevfs_control failed cmd fxload rqt 64 rq 160 len 1 ret -108 

what this means i didn't know, but with the help of other i hope to fix it.

greetings consam

---

