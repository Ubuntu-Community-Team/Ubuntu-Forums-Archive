---
title: "howto disable imon internal IR receiver in mythbuntu 8.10"
date: 2009-03-09
forum: Multimedia Software
---

### Post by madman100 on 2009-03-09
hi all can any one tell me how to disable imon internal IR receiver in mythbuntu 8.10  i have a mce remote with external IR receiver witch i use but on boot up the remote does not work the reason for this is the system is picking two IR receiver but if i unplug then plug the usb IR receiver back in the usb port and restart the system then the remote works i do not want to use the imon remote only the mce remote or does any one know how to get the imon internal IR receiver to work with mce remote or how to make the mce IR receiver my default receiver the 
sudo gedit /etc/lirc/hardware.conf

      Modify LIRCD_ARGS="" to match

      LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"
      LIRCD2_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

sudo gedit /etc/init.d/lirc

Change this block:
   
	LIRCD_ARGS=`build_args $LIRCD_ARGS`
        start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
        < /dev/null


To be:
         LIRCD_ARGS=`build_args $LIRCD_ARGS`
         LIRCD2_ARGS=`build_args $LIRCD2_ARGS`
         start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
         < /dev/null
         /usr/sbin/lircd $LIRCD2_ARGS \
         < /dev/null
code was  working  in mythubuntu 7.10 but it does not work in mythbuntu 8.10

Thanks
madman100

---

