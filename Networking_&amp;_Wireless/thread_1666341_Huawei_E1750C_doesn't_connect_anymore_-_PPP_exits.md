---
title: "Huawei E1750C doesn't connect anymore - PPP exits?"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by saepia on 2011-01-13
I use, or try to use, ubuntu 10.10 and Huawei E1750C 3G USB modem.

It was working on my PC very well but suddenly had stopped connecting. It is not damaged - I am using it now on my laptop (also ubuntu 10.10). Both computers use the same version of kernel (2.6.35-24-generic), pppd and network-manager (0.8.1+git.20100810t184654.ab580f4-0ubuntu2).

The only difference is that my PC is 64-bit.

Both systems are updated.

I don't know why this modem had stopped working on my PC as I nothing changed (no hardware changes, no updates).

I submit log files, please compare the last lines of modem-manager's logs that on laptop it sends next AT commands while on the PC it just terminates PPP.

What could be the cause?

Thank you in advance,

---

### Post by alexfish on 2011-01-13
Looks like modem-manager is trying to connect to different port / IE trying to connect ttyUSB2 = failure
Normal shows ttyUSB0

not sure if it is a switching problem

can post details of


Code:

[COLOR=Blue]ls -al /dev/serial/by-id[/COLOR]

do so for both systems for comparison

and

Code:

[COLOR=Blue]usb-devices[/COLOR]

locate the lines which indicate the device and post only those lines

 try to configure ppp direct , and select to use ttyUSB0:

call up the ppp

Code:

[COLOR=Blue]sudo pppconfig[/COLOR]

may be met with failure if the device is incorrectly switched (try other ports) from the listings

other problem could exist if incorrectly switch , in that the control lines are not presented by the modem

and may need a means of force the control lines internally to the modem

wvdial does this as a matter of course (but may not be present in ubuntu 10.10)

can also suggest trying Sakis3g

[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&sqi=2&ved=0CBcQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=uGYvTejeEoW7hAfYhYTnCg&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")

#can also check the status lines with this script

#!/bin/sh
# the next line restarts using tclsh\
exec tclsh "$0" "$@"
set serial [open "[COLOR=Blue]/dev/ttyUSB0[/COLOR]" "r+"]
fconfigure $serial -mode "115200,n,8,1"
fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1}
after 300
set stat [fconfigure $serial -ttystatus]
puts $stat
close $serial
# edit the [COLOR=Blue]'/dev/tty*[/COLOR]' to suite and check all. the modem lines will show CTS 1 DSR 1 RING 0 DCD 0 or CTS 1 DSR 1 RING 0 DCD 1
# END

---

### Post by alexfish on 2011-01-13
done some testing of how modem-manager is accessing and testing the ports

this is what can occur

if certain commands are sent to a modem line (possible cd mass-storage) is set to tty* port
then if a command is sent to this port , then it sets the modem into a loop ,and presents data on that port
. Not intended. A consequence of this can be : the modem control lines get set to OFF (common on some huawie devices) the looping can sometimes be stopped by sending " ATZ " to the correct port
then as mentioned setting the control lines (sending the correct AT commands to the modem "[FONT=Times New Roman, serif][SIZE=2]ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/SIZE][/FONT]")
possible cause is incorrect switching as mentioned . leading modem-manager trying to access other ports
and or the modem has been hacked or reset back to factory defaults

although as said it works in 32 bit , 

also check pppd is not running / when not intended

check the system before trying to connect with NM

also do these commands prior to (To be sure)

Codes:

[COLOR=Blue]sudo poff[/COLOR]

[COLOR=Blue]sudo killall modem-manager[/COLOR]

---

