---
title: "/etc/bluetooth/rfcomm.conf"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by surferX on 2010-04-08
I got my modem working via bluetooth by using the rfcomm bind command manually

I have set up my /etc/bluetooth/rfcomm.conf correctly. (copied from a working distro on the same hardware)

looking through /etc/init.d/bluetooth I can not see where rfcomm command is invoked, anyone know how to achieve this?

---

### Post by arjuntank on 2010-04-08
$ service bluetooth status 

this will let you know if bluetooth is started. if not, do a service bluetooth start. if that doesnt work, you may need to check for any hardware switch if it's on. 
get the device name from your conf and do a rfcomm <dev> to start the device.

---

### Post by surferX on 2010-04-08
/etc/init.d/bluetooth is started

and the bluetoothd is running, but I can't see where it call rfcomm

I can run rfcomm manually, I just want the bluetooth script to reconize the existance of the rfcomm.conf file and run rfcomm.

Does that make sense?

---

### Post by arjuntank on 2010-04-08
i think your /etc/bluetooth/main.conf is not configured to match your rfcomm.conf.
 just check if that helps.

---

### Post by surferX on 2010-04-08
> i think your /etc/bluetooth/main.conf is not configured to match your rfcomm.conf.
 just check if that helps. 	

I think your right, but I can't find any example of what it should like as the main.conf does not have a man page and its new (replaces hcid.conf) and I have not working example.

Could you post yours?

---

### Post by arjuntank on 2010-04-08
i dont have a working example but 
this would surely help:
[http://www.linuxquestions.org/questions/debian-26/bluetooth-problems-715839/]("http://www.linuxquestions.org/questions/debian-26/bluetooth-problems-715839/")

---

### Post by digitao on 2010-05-28
I found this thread whilst trying to do the same thing... its probably a bit of a hack but.....

in /etc/init.d/bluetooth....

at the end of the start section add the line ->

rfcomm bind all

and at the start of the stop section (just before "pkill -TERM bluetoothd") add ->

rfcomm release all

this seems to do what you would expect, binds the rfcomm ports defined in rfcomm.conf on startup and releases them on service stop...

---

### Post by digitao on 2010-05-28
sorry back on the machine set up this way.... see extract from /etc/init.d/bluetooth below..[FONT=Fixedsys]

[/FONT][FONT=System]case "$1" in
     start)
    #currently this init script exists only because of what appears to be
    #an egg and chicken problem
    #  bluetoothd normally starts up by udev rules.  it needs dbus to function,
    #  but dbus doesn't start up until after udev finishes triggering
    #
    if [ ! -f /sbin/udevadm.upgrade ]; then
        udevadm trigger --subsystem-match=bluetooth
         fi
         # added to bind rfcomm channels in rfcomm.conf automatically
         rfcomm bind all
         ;;
     stop)
         rfcomm release all
    pkill -TERM bluetoothd || true
    ;;
[/FONT][FONT=Fixedsys]
[/FONT]

---

### Post by yanv on 2011-04-18
Thank you digitao, that worked for me!

---

