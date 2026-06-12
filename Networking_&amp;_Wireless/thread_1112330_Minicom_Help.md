---
title: "Minicom Help"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by NvrBst on 2009-03-31
I'm using VMware (Ubuntu 8.10), fully updated.  I'm having a problem typing in Minicom.

I'm trying to connect a modem to ttyS0, and the tutorial I'm reading says I should be able to type "at" and see an OK.  Tutorial is using Minicom 1.83.0, and I'm using 2.3.

I set up the "/dev/modem" to point to "/dev/ttyS0" (my computer only has 1 Serial Port).  I get the following when I type "minicom".
```
Welcome to minicom 2.3

OPTIONS: I18n
Compiled on Oct 24 2008, 06:37:44.
Port /dev/modem

               Press CTRL-A Z for help on special keys

AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK


```

I think it can see the modem fine because if I unplug the modem and restart minicom I don't get the automatic "AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0" message.

Problem:  I can't type anything.  Could I have the "9600 8N1" wrong?  If I connect Hyperterminal using "9600 8N1" to COM1 then I'm able to type things like "at" and see an "OK".  Is this normal in Minicom v2.3?  Is there a setting I need to make sure I have enabled to type manually?

Something else I should try?

Thanks in Advance.

PS:  I'm not trying to get internet, VMWare set up NAT/Bridged connection's fine automatically for me, however, I have a wireless modem that I wanted to test/work on using a desktop PC, and I'll eventually use it in an embedded device.

EDIT: I also thought it might be mod on ttyS0 so I set it to 777 and tried restarting minicom but it didn't work.  I also noticed that if I restart the virtual machine ttyS0 gets reset to 660; probably normal.
```
administrator@administrator-desktop:~/Desktop$ l /dev/ttyS*
crwxrwxrwx 1 root dialout 4, 64 2009-03-31 13:18 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-03-31 12:41 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-03-31 12:13 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-03-31 12:13 /dev/ttyS3

administrator@administrator-desktop:~/Desktop$ l /dev/modem
lrwxrwxrwx 1 root root 5 2009-03-31 12:46 /dev/modem -> ttyS0

```

---

### Post by NvrBst on 2009-03-31
I was able to fix the problem by changing flow control.

Orig: "Hardware: Yes, Software: No"
Works: "Hardware: No, Software: No"
Works: "Hardware: No, Software: Yes"


Weird that Hyperterminal works with Flow Control is set to "Hardware" but minicom doesn't let me type anything.  Tutorial shows "Hardware: Yes" as well.  Is there any implications to turning flow controll off?  Should I switch it to Software or just keep both as "No"?

Thanks

---

### Post by mierdin on 2010-11-04
W00T!!! Thanks for this, there's not a lot of info on this, and this was my problem.

In reference to your question, I haven't run into any problems with both off.

---

### Post by dargaud on 2011-05-03
Woah, thanks a lot, I'd been having this problem on several computers for a year !

---

### Post by Bluelotus256 on 2011-07-13
[FONT=monospace]Hi,
  I am using a pl2303x USB-serial converter cable and running Ubuntu 10.0.4 on my PC. I am trying to perform a loop back test.  I shorted out the pins 2,3 and changed the  baud rate in Minicom to 19200 with 8N1 with no flow control and also changed the  serial device to /dev/ttyUSB0. I saved this configuration. When I opened minicom with this configuration I got this output:
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
Then a flashing cursor which allowed me to type but did not echo back anything.

When I typed lsusb at the terminal I got:
Bus 005 Device 010: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port. 

When I typed in dmesg | grep tty I got this:
[28210.332573] usb 5-1: pl2303 converter now attached to ttyUSB0.

Earlier I associated ttyS0 to ttyUSB0 using the ln command then removed the ttySO from the /dev/ folder. I don't know if I am missing a driver or something else. I checked and confirmed that the cable is good using Hyper terminal with the same serial port settings. Any help on this one would be greatly appreciated.
                 Regards,
                 JM[/FONT]

---

### Post by ravidborse on 2013-03-20
I also got the same problem with my /dev/ttyUSB0.
I resolved it with[**[COLOR=#000000] NvrBst[/COLOR]**]("http://ubuntuforums.org/member.php?u=802311") provided solution.

Orig: "Hardware: Yes, Software: No"
Works: "Hardware: No, Software: No"
Works: "Hardware: No, Software: Yes"

Following is the procedure for Loopback test with Minicom:

```
root@ravidborse:/home/ravidborse# minicom -s
            +-----[configuration]------+
            | Filenames and paths      |
            | File transfer protocols  |
            | Serial port setup        |
            | Modem and dialing        |
            | Screen and keyboard      |
            | Save setup as dfl        |
            | Save setup as..          |
            | Exit                     |
            | Exit from Minicom        |
            +--------------------------+

   +-----------------------------------------------------------------------+
    | A -    Serial Device      : /dev/ttyUSB0                              |
    | B - Lockfile Location     : /var/lock                                 |
    | C -   Callin Program      :                                           |
    | D -  Callout Program      :                                           |
    | E -    Bps/Par/Bits       : 115200 8N1                                |
    | F - Hardware Flow Control : No                                        |
    | G - Software Flow Control : Yes                                       |
    |                                                                       |
    |    Change which setting?                                              |
    +-----------------------------------------------------------------------+
            | Screen and keyboard      |
            | Save setup as dfl        |
            | Save setup as..          |
            | Exit                     |
            | Exit from Minicom        |
            +--------------------------+

root@ravidborse:/home/ravidborse# minicom dfl

Welcome to minicom 2.6.1

OPTIONS: I18n 
Compiled on May  1 2012, 13:36:18.
Port /dev/ttyUSB0

Press CTRL-A Z for help on special keys

						
```

Just Please Dont Forget to Use CTRL+A then Z to get the Serial Port Setting
Its interesting to learn, it takes time but its ok

Thanks to Linux

---

