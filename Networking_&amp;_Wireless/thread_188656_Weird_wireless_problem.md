---
title: "Weird wireless problem"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by ipaidforthisname on 2006-06-04
I posted my original thread in the wrong section :-( I am posting it here now. Sorry for the double post. 

I just upgraded from Breezy Badger to Dapper Drake, and love it, but I've had a few odd issues that I haven't been able to solve on my own. One of the most perplexing is my wireless problem. My wireless card was detected during the installation, and I just had to extract the firmware from the .sys using the fwcutter program. 

The wireless card works fine now, but everytime I boot, it doesn't work until I do these three things:

```
 
$sudo ifconfig eth1 down
$sudo ifconfig eth1 up
$sudo /etc/init.d/networking restart

```

After that, it works without a hitch until I reboot again, and I have to keep doing that. 

Does anyone have any ideas as to how I can avoid doing that each boot?

Thanks!

---

### Post by lukew on 2006-06-09
[QUOTE=ipaidforthisname]I posted my original thread in the wrong section :-( I am posting it here now. Sorry for the double post. 

I just upgraded from Breezy Badger to Dapper Drake, and love it, but I've had a few odd issues that I haven't been able to solve on my own. One of the most perplexing is my wireless problem. My wireless card was detected during the installation, and I just had to extract the firmware from the .sys using the fwcutter program. 

The wireless card works fine now, but everytime I boot, it doesn't work until I do these three things:

```
 
$sudo ifconfig eth1 down
$sudo ifconfig eth1 up
$sudo /etc/init.d/networking restart

```

After that, it works without a hitch until I reboot again, and I have to keep doing that. 

Does anyone have any ideas as to how I can avoid doing that each boot?

Thanks![/QUOTE]
Hay,

I am having the exact same problem using a linksys wusbv11v4. I presume you are using the ndiswrapper? Did you see the section near the bottom of thr wikki mentioning to add ndiswrapper as a module to be booted up in /etc/modules?

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)


Like I said I ma having the exact same problem but this does not seem to fix it..... let me know how you get on and sorry I can not be of any more help.

Thanks

Luke

---

### Post by lukew on 2006-06-09
[QUOTE=ipaidforthisname]I posted my original thread in the wrong section :-( I am posting it here now. Sorry for the double post. 

I just upgraded from Breezy Badger to Dapper Drake, and love it, but I've had a few odd issues that I haven't been able to solve on my own. One of the most perplexing is my wireless problem. My wireless card was detected during the installation, and I just had to extract the firmware from the .sys using the fwcutter program. 

The wireless card works fine now, but everytime I boot, it doesn't work until I do these three things:

```
 
$sudo ifconfig eth1 down
$sudo ifconfig eth1 up
$sudo /etc/init.d/networking restart

```

After that, it works without a hitch until I reboot again, and I have to keep doing that. 

Does anyone have any ideas as to how I can avoid doing that each boot?

Thanks![/QUOTE]
I have also seen this mentioned on the offical ndis wikki, with regards to my advise previously.

If this does not work, instead add a line

modprobe ndiswrapper

in /etc/rc.d/rc.local.

I can not find this file but I can see a /etc/rc.local. 

Is this the same?  I supose there is only one way to find out.....

If I dont reply soon dont do it! ;)

I will let you know how I get on.....

Regards

Luke

---

### Post by lukew on 2006-06-09
Bummer....

I added it into /etc/rc.local and /etc/init.d/rc.local and still no joy.

I better stop wasting so much valuable paper and come back when I have a correct solution. ;)

Sorry I can not be of any more help but I will keep on trying.

Luke

---

### Post by TomH on 2006-06-10
Any luck with this guys i have the same problem here, except mine works sometimes :confused:

---

### Post by lukew on 2006-06-24
Hay,

No luck so far but i have been on holiday in Spain. Got a few other things I want to fix/break first. If I find the fix I will post. I think the solution, if there is one, is to compile the latest stable version from source and not use the slightly dated package in the ubuntu repository.

Luke

---

