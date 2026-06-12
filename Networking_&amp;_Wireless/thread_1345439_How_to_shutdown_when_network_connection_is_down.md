---
title: "How to shutdown when network connection is down?"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by praveensripati on 2009-12-04
Hi,

I have Ubuntu 9.10 installed on a Desktop. Is there a way to shutdown the computer when the power supply goes down?

Once in a while I download huge files and I want to shutdown the computer when the power supply goes off. The UPS powers the desktop for about 10 min and then desktop suddenly turns off.

I was thinking. One way is to check if the network connection is up or down and then shutdown the computer accordingly.

Thanks,
Praveen

---

### Post by Some Penguin on 2009-12-04
Might be in luck if your UPS is from APC.

[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)


Or, perhaps more generally,

[http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

---

### Post by praveensripati on 2009-12-04
>>Might be in luck if your UPS is from APC.
>>[https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd)
>>Or, perhaps more generally,
>>[http://blog.shadypixel.com/monitorin...-ubuntu-linux/](http://blog.shadypixel.com/monitorin...-ubuntu-linux/)

The above solution requires UPS from APC or USB based UPS. My UPS doesn't follow under one of these categories.

Can we have some script or daemon process check the network connection let's say once a minute and shutdown the desktop when the network connection goes down?

My DSL Modem is not connected to the UPS, so when the power goes off the network connection to the desktop is lost.

Thanks&Regards,
Praveen

---

### Post by Grenage on 2009-12-04
From [here]("http://www.unix.com/shell-programming-scripting/104820-how-call-if-not-test-then.html"):


```
ping -c 2 -s 100 -w 1 8.8.8.8 >/dev/null
if [ $? -eq 1 ] ; then
   shutdown -h -P now
else
echo "pinging"
fi
```

Something like that on a 2 min schedule via crontab?

---

### Post by Lars Noodén on 2009-12-04
What model of UPS is it?  There may be the possibility of getting a signal directly from the UPS as to the status of the grid.

Another way, besides ping, is to see if the network cable is attached to something live.  This script could be polled every few minutes and will shutdown if there is no response from the net after a few tries.  

```

#!/bin/sh

# try six times
for i in 1 2 3 4 5 6; do

  # wait a bit before trying again
  **sleep** 10;

  # if the network has power, exit
  **ifconfig** eth0 | **grep** RUNNING && exit;

done;

# oh, my, no network for a period, so we'll shut down
**sudo** /sbin/**shutdown** -k now "Power is probably out"

```

You'll have to substitute **-k** for something useful.

---

### Post by praveensripati on 2009-12-05
@Lars Noodén

I have got a Frontech UPS (Model JIL 2513). I am not sure if it supports getting a signal directly from the UPS as to the status of the grid.

Thanks for all the suggestions.

---

