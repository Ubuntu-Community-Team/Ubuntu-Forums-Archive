---
title: "disable imon internal  IR receiver"
date: 2008-02-07
forum: Mythbuntu
---

### Post by madman100 on 2008-02-07
hi all can any one tell me how to disable imon internal  IR receiver i have a mce remote with external   IR receiver witch i use but on boot up the remote does not work the reason for this is the system is picking two  IR  receiver but if i unplug then plug the usb   IR receiver back in the usb port and restart the system then the remote works i do not want to use the imon remote only the mce remote or does any one know how to get the imon   internal  IR receiver to work with mce remote or how to make the mce IR receiver my default receiver 

Thanks

---

### Post by Dubstar_04 on 2008-02-09
I am currently doing a fresh install and i'm having the same problem. 

I use to have the imon vfd and the mce remote working I just can't remember how!!

---

### Post by Dubstar_04 on 2008-02-09
I think I may have found the solution:-

I'm no expert however I have managed to get this to work as follows. 
Please note this may not be the correct way to solve the problem however it has worked for me. If this problem persists the only other solution will be to name the hardware and load it with udev. I will look into this at a later date if needed.

My hardware -
Silverstone LC16m - Imon VFD
Microsoft MCE remote (Philips)


How to:

```

sudo gedit /etc/lirc/hardware.conf

      Modify LIRCD_ARGS="" to match

      LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"
      LIRCD2_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"


```

```

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



```

```

Restart LIRC:
	sudo /etc/init.d/lirc stop
	sudo /etc/init.d/lirc start

```


Now comes the testing:

       		```
ls /dev/lirc*
```

You should have something similar to:
```

sandal@MediaBox:~$ ls /dev/lirc*
/dev/lirc0  /dev/lirc1  /dev/lircd  /dev/lircd1

```

Now test lircd and lircd1 (press a few buttons on each and see if your remote will work:

```

		irw /dev/lircd
		irw /dev/lircd1

```

You will more than likely find that your remote works on lircd1 if that is the case then:

```

sudo gedit /etc/lirc/hardware.conf

     	 Modify:
      	LIRCD_ARGS="-d /dev/lirc0 --output=/dev/lircd --listen"
      	LIRCD2_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"

	To match:
        LIRCD_ARGS="-d /dev/lirc1 --output=/dev/lircd1 --listen"
  	LIRCD2_ARGS="-d /dev/lirc0 --output=/dev/lircd --connect=localhost:8765 --pidfile=/var/run/lircd2.pid"



```

Restart LIRC:
```

	sudo /etc/init.d/lirc stop
	sudo /etc/init.d/lirc start

```

Hopefully you now have remote that works straight from boot!!

Regards,

Dubstar_04

---

### Post by madman100 on 2008-03-29
Hi Dubstar_04 many thanks for the code just got round to doing it and it now load at  boot and the remote now works every time i boot up the machine and log in too myth \\:D/

Thanks 
Madman100

---

