---
title: "Disable bluetooth"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Tobywuk on 2009-11-08
Hello,

On 9.04 I disabled bluetooth by removing the startup deamon with rc-update.

This method does not seem to work with 9.10. How do i go about disabling the bluetooth deamon with the new ubuntu 9.10?

Thanks.

---

### Post by TKoorn on 2009-11-09
I would like to know this too.
Disabling it manually everytime I boot is a pain.

---

### Post by Tobywuk on 2009-11-11
someone out there must know :)

---

### Post by GoofYas007 on 2009-11-11
I also would like to know...

Any bright souls out there who can share the solution with us...

---

### Post by zorkerz on 2009-11-11
Same here. There has never been an easy way to disable bluetooth on ubuntu. Every release the situation changes a bit but no good solutions arise. I have never actually used my computer with a bluetooth device and yet it is constantly sucking down my battery power.

---

### Post by koex on 2009-11-11
System->Preferences->Startup apss->Disable Bluetooth manager

---

### Post by zorkerz on 2009-11-11
This is were part of the confusion comes with bluetooth. I do not believe that actually disables bluetooth, rather it simply prevents the bluetooth applet from loading in the system tray. For people with a hardware bluetooth light they will see that it does not go off and power is still going to the bluetooth antenna. 

If you use powertop it will still recommend disabling bluetooth.

---

### Post by Tobywuk on 2009-11-12
As above.

> How do i go about disabling the bluetooth deamon
Kernel module will also do. :)

---

### Post by jollysnowman on 2009-11-12
You could just go to synaptic and remove the bluetooth packages.

---

### Post by foxmulder881 on 2009-11-12
In addition to the above, also System > Administration > Services and disable the bluetooth service.

---

### Post by TKoorn on 2009-11-12
I installed blueman to replace bluetooth manager and blueman remembers my settings. So if it is off it stays off. I can't find a services under System > Administration

---

### Post by TKoorn on 2009-11-12
BTW there is no 

System > Administration > Services

in Karmic Koala

---

### Post by walmis on 2009-11-12
In karmic bluetoothd is on demand, so if there is an active bluetooth adapter bluetoothd will start with udev rules, if there's none, bluetoothd will not start.

---

### Post by zorkerz on 2009-11-12
I am still a little bit confused by all of this. 

by default in system->prefereneces->startup applications the bluetooth-applet starts with the computer. However even when this is set not to start up my bluetooth light comes on at every start up. The only way I know to turn it off is to either right click on the bluetooth-applet icon in the notification aread and select "Turn Off Bluetooth" or via my built in hardware key combination (fn+F5). This needs to be done every time the computer starts (if somebody knows a way to not have it turn on pleas let me know).

So if i set the bluetooth-applet not to turn on with the computer and everytime the computer starts I manually turn off the bluetooth light am I still wasting power, memory, or processor time on bluetooth?

Finally why does the bluetooth light not operate in a similar fashion to the wifi light?
i.e. it is off unless I am actually connected to a wifi network and it flashes when info is being transfered.

thanks

---

### Post by foxmulder881 on 2009-11-12
> **TKoorn said:**
> BTW there is no 

System > Administration > Services

in Karmic Koala

Ok, sorry about that. I guess it was there when I was running Intrepid and it's there in my current Fedora 11 system. I just assumed it would have been there in Karmic too.

---

### Post by wired98 on 2009-11-12
> **Tobywuk said:**
> someone out there must know :)

That's right! :)

I solved this like on all other versions of ubuntu. You can issue the command 

```
sudo echo "disable" > /proc/acpi/ibm/bluetooth
```

in the commandline to disable bluetooth. Respectively 

```
sudo echo "enable" > /proc/acpi/ibm/bluetooth
```

turns it back on. 

This mechanism can be used to disable bluetooth during startup. You only have to put in a script that is executed during the boot process. I put it in the file

/etc/rc.local

that is executed each time the runlevel is changed. That works for me. I am sure though, that there probably is a more elegant solution...

I hope that helps!

Best,

Marc

---

### Post by zorkerz on 2009-11-13
Does this mean that as part of the startup process bluetooth is first enabled and then with your command disabled?

---

### Post by GoofYas007 on 2009-11-15
plz, for the people mentioning use this to turn this or that bluetooth module off... I don't have any bluetooth module in my computer. Nevertheless, Ubuntu loads some bluetooth stuff, see below...


root  43  0.0  0.0 0     0 ? S<   Nov11   0:00 [bluetooth]

So what's loading & how do I disable it?

---

### Post by invenit on 2009-11-16
Check out guvnr's website for an easy way to disable services in karmic [http://guvnr.com/pc/ubuntu-disable-services/](http://guvnr.com/pc/ubuntu-disable-services/)

---

### Post by fstonedahl on 2009-12-28
> **wired98 said:**
> You can issue the command 

```
sudo echo "disable" > /proc/acpi/ibm/bluetooth
```

in the commandline to disable bluetooth. Respectively 

```
sudo echo "enable" > /proc/acpi/ibm/bluetooth
```

turns it back on. 


Thanks, Marc, this is great!  This thread may be mostly dead, but here are a couple further remarks:

1) As discussed more fully in [_this other post_]("http://ubuntuforums.org/showthread.php?t=412329"), you can't just issue "sudo echo XXX > YYY", from the terminal and get it to work, if the YYY file needs root access to be modified.  Instead, you can do:

```
echo "disable" | sudo tee /proc/acpi/ibm/bluetooth
```


> **wired98 said:**
> 

This mechanism can be used to disable bluetooth during startup. You only have to put in a script that is executed during the boot process. I put it in the file

/etc/rc.local

that is executed each time the runlevel is changed. That works for me. I am sure though, that there probably is a more elegant solution...


Since the rc.local file is being run with root permissions, it works just fine to add the following line (before the "exit 0" line):

```
echo "disable" > /proc/acpi/ibm/bluetooth
```

---

### Post by sliketymo on 2009-12-28
System>Preferences>Startup Applications,uncheck it,then delete it if you want.

---

### Post by guvnr on 2010-01-10
> **invenit said:**
> Check out guvnr's website for an easy way to disable services in karmic [http://guvnr.com/pc/ubuntu-disable-services/](http://guvnr.com/pc/ubuntu-disable-services/)

big cheers Invenit .. shout much appreciated.

---

### Post by lgjsheron on 2010-01-11
When i click the blue tooth icon and i disable it after that i'm unable to enable it. How to activate my blue tooth again

---

### Post by psrivats on 2010-01-11
> **fstonedahl said:**
> Thanks, Marc, this is great!  This thread may be mostly dead, but here are a couple further remarks:

1) As discussed more fully in [_this other post_]("http://ubuntuforums.org/showthread.php?t=412329"), you can't just issue "sudo echo XXX > YYY", from the terminal and get it to work, if the YYY file needs root access to be modified.  Instead, you can do:

```
echo "disable" | sudo tee /proc/acpi/ibm/bluetooth
```




Since the rc.local file is being run with root permissions, it works just fine to add the following line (before the "exit 0" line):

```
echo "disable" > /proc/acpi/ibm/bluetooth
```

Thank you!

Works on my thinkpad T60 running ubuntu 9.10

---

### Post by clevertomato on 2010-01-11
I need to turn off my bluetooth, too, when I'm not using it. I want to use the method "echo "disable" | /proc/acpi/ibm/bluetooth" but I guess I need a little help. I have no /proc directory.

If it matters, I have a Dell Studio 1555.

---

