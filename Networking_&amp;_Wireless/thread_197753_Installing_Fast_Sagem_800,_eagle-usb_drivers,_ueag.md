---
title: "Installing Fast Sagem 800, eagle-usb drivers, ueagle-atm"
date: 2006-06-16
forum: Networking &amp; Wireless
---

### Post by babis85 on 2006-06-16
Hello all,
i have a problem installing Fast Sagem 800 on my dapper-drake.
I have spent a lot of time (days) searching for solution, but i haven't got it worked yet.

I have installed eagle-usb-2.3.3.
Next i installed successfully the ueagle-atm-1.3 and then ueagle-data-1.1 following the guide at [http://ubuntuforums.org/showthread.php?t=144468&highlight=%22eagle+usb%22](http://ubuntuforums.org/showthread.php?t=144468&highlight=%22eagle+usb%22)

The problem is that while the modules ueagle_atm and eagle_usb are been loading successfully i can't get connected.
The eaglediag produces all OK, except
modem operational [KO]
ping IP [KO]
test DNS resolution [KO]

For the first i run eaglectrl -d and i got
"Unable to send CMVs to driver: Inappropriate ioctl for device"

I will go crazy, please help...
Thanks a lot.

---

### Post by suloku on 2006-06-16
[http://www.ubuntuforums.org/showthread.php?t=144468&highlight=sagem+fast+800](http://www.ubuntuforums.org/showthread.php?t=144468&highlight=sagem+fast+800)

Follow this, no problems with me (well, at first there were)

I made a nice script(my first one!) to connect, but, how can I disconnect?

Here the script
```
#!/bin/bash
#created by suloku
foo=`gksudo -u root -k -m "Introduce the password to connect" /bin/echo "Do you have root access?"`
sudo modprobe pppoatm
sudo pppd call ueagle-atm
```

hope someone tells me how to disconnect.

cya

ps: i think that connecting at boot only needs to add ```
sudo modprobe pppoatm
sudo pppd call ueagle-atm
``` to .bash_profile in home folder (to connect when our user makes loggin) or in /etc/profile (to connect when anyone makes loggin)

ps2: sry for my bad english

---

### Post by babis85 on 2006-06-16
Thanks a lot for your reply.
That link that you tell me to follow to is the one that mentioned at my post.
Any other idea?
I will ask something quite silly.
I have to install both eagle-usb driver and ueagle-atm or the second is sufficient?

Thanks again, i really appreciate that.

---

### Post by babis85 on 2006-06-17
Hello again,
i think that the problem is on a configuration file.

$ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:272 (272.0 b)  TX bytes:272 (272.0 b)

inet addr mustn't be 127.0.0.1 and mask mustn't have assigned this value in order to get connected to the internet.
What do you say?

---

### Post by suloku on 2006-06-17
You have the same problem I had before, reinstalling ubuntu erasing "/" partitione (keeping /home partition) and following the mentioned thread step by step was the solution, but maybe you don't have to do.

First of all you have to completely remove eagle-usb. 
Then, as it is said in the thread remove the ueagle-usb module with "sudo rmmod ueagle-usb"
A sudo make uninstall at sources folder of your installed version of eagle-usb will do it.

Now continue the guide, remove the .ko modules from your filesystem, unplug the modem and replug it.

EDIT: After uninstalling eagle-usb i think it's better to unplug the modem and restart the system, the plug it after copying the firmware files from ueagle-data-1.0 file(see the guide)

If you follow it the only problem you may have is finding your VI.CP, a google search will make you find it, or if you have the luck to use the same isp as the creator of the guide...^^

Only one thing left, in the char-secret(uh, was it this?), well, in the file to input your loggin and pass I removed the commented lines in the file and left only the line.

"loggin" "*" "password" "*"

Hope that helped, ill be testing to remove the connection

ps: in if config you ever get this "lo" network. It is the local networ, all computers have it in that same IP

---

### Post by babis85 on 2006-06-27
So, here i am again.

I've just formated ubuntu and the problem is the same.
Although, i have follow the how-to step by step, i noticed two differences that
might cause that problem.

In the how-to says that after running "sudo modprobe ueagle-atm"
then dmesg must show
usb 1-2: [ueagle-atm] modem operational
usb 1-2: [ueagle-atm] ATU-R firmware version : 43e2ead7

In contrast, it shows me 
usb 1-1: [ueagle-atm] modem operational
usb 1-1: [ueagle-atm] ATU-R firmware version : 40e4beq6

It seems that that firmware version is older than that of the how-to.
But, i used the files that reported: ueagle-atm-1.3 and ueagle-data-1.1.

Any idea, please?

---

### Post by aces21 on 2006-06-28
Babis,

A few things that spring to mind.

I can't figure out from your posts if you still have eagle-usb installed? If you do, you need to remove it as it doesn't work with Dapper and will conflict with ueagle-atm.

Having said that, "sudo modprobe ueagle-atm" shows "modem operational" so it appears to be working.

I am not sure you need to worry that the firmware version is different.

Which ISP do you use? Are you sure they use PPPoA? If so then the guide instructions should work, assuming the VP and VC in your /etc/ppp/peers file are right. Did you check this?

If all this is right and your chap-secrets file is right, i.e. a single line with your username and password, then try running the command:

```
pon ueagle-atm
```

This is a better way to start the connection that pppd call ueagle-atm. If that doesn't give any error, then run the command:

```
plog
```

What does this output?

---

### Post by B0rsuk on 2006-06-30
I have a question. Can I set up internet connection (neostrada/sagem 800) with ACPI and APM disabled ? I don't exactly understand what these are (some kind of packages for power management). But I need to turn them off, or else Breezy kernel freezes at boot time, even when using install cd.
Disabling ACPI and APM fixes that, but somehow the connection stopped to work after that. Is this caused by ACPI+APM being disabled ? By the way: I had problems compiling eagle-usb drivers, so I used precompiled ones.

I heard this problem (kernel freezing) persists in Dapper, so I'll probably have to disable it again. I'm about to install it on my friend's machine, so I have to be sure before I meet him. The kernel freeze problem started appearing after he exchanged cdrom drive for dvd drive.

By the way: how to use acpi=off apm=off options when booting from install CD ? I managed to get it work when it was already installed (and used to work).  I mean, I have to manually specify path to kernel, root partition etc. But I don't know the paths for install cd. Can anyone help ?

---

### Post by babis85 on 2006-06-30
[QUOTE=aces21]Babis,

A few things that spring to mind.

I can't figure out from your posts if you still have eagle-usb installed? If you do, you need to remove it as it doesn't work with Dapper and will conflict with ueagle-atm.

Having said that, "sudo modprobe ueagle-atm" shows "modem operational" so it appears to be working.

I am not sure you need to worry that the firmware version is different.

Which ISP do you use? Are you sure they use PPPoA? If so then the guide instructions should work, assuming the VP and VC in your /etc/ppp/peers file are right. Did you check this?

If all this is right and your chap-secrets file is right, i.e. a single line with your username and password, then try running the command:

```
pon ueagle-atm
```

This is a better way to start the connection that pppd call ueagle-atm. If that doesn't give any error, then run the command:

```
plog
```

What does this output?[/QUOTE]

I finally got connected with the help of plog.
I had completely uninstalled the eagle-usb drivers.
The first plog's results were :
```

Jul  1 03:09:48 ubuntu pppd[5073]: Plugin pppoatm.so loaded.
Jul  1 03:09:48 ubuntu pppd[5074]: pppd 2.4.4b1 started by root, uid 0
Jul  1 03:09:48 ubuntu pppd[5074]: Using interface ppp0
Jul  1 03:09:48 ubuntu pppd[5074]: Connect: ppp0 <--> 8.35

```

The second :
```

Jul  1 03:11:36 ubuntu pppd[5074]: Remote message: Authentication failed
Jul  1 03:11:36 ubuntu pppd[5074]: PAP authentication failed
Jul  1 03:11:36 ubuntu pppd[5074]: Connection terminated.
Jul  1 03:12:06 ubuntu pppd[5074]: Using interface ppp0
Jul  1 03:12:06 ubuntu pppd[5074]: Connect: ppp0 <--> 8.35
Jul  1 03:12:11 ubuntu pppd[5074]: Remote message: Authentication failed
Jul  1 03:12:11 ubuntu pppd[5074]: PAP authentication failed
Jul  1 03:12:11 ubuntu pppd[5074]: Connection terminated.

```

If you notice the second line from the end, you will see tha PAP authentication, which refers to the /etc/ppp/pap-secrets. I hadn't added to that file my  username and my password, because i had read that it needless. So, i added these info and finally got connected.
Thanks for the plog command.

---

### Post by babis85 on 2006-06-30
[QUOTE=B0rsuk]I have a question. Can I set up internet connection (neostrada/sagem 800) with ACPI and APM disabled ? I don't exactly understand what these are (some kind of packages for power management). But I need to turn them off, or else Breezy kernel freezes at boot time, even when using install cd.
Disabling ACPI and APM fixes that, but somehow the connection stopped to work after that. Is this caused by ACPI+APM being disabled ? By the way: I had problems compiling eagle-usb drivers, so I used precompiled ones.

I heard this problem (kernel freezing) persists in Dapper, so I'll probably have to disable it again. I'm about to install it on my friend's machine, so I have to be sure before I meet him. The kernel freeze problem started appearing after he exchanged cdrom drive for dvd drive.

By the way: how to use acpi=off apm=off options when booting from install CD ? I managed to get it work when it was already installed (and used to work).  I mean, I have to manually specify path to kernel, root partition etc. But I don't know the paths for install cd. Can anyone help ?[/QUOTE]

Hello my friend,
when i had the beta version of Dapper i had no problems with that.
Now, that i have the LTS Dapper i have this problem, but i have also changed some parameters in BIOS. That are the Power Management (it was on and it's off)
and something concerning the Plug N Play that now is off. I think that these two cause the problem to me. These might help you, too.

Furthermore, in Dapper you must install the ueagle-atm as described [here](http://ubuntuforums.org/showthread.php?t=144468&highlight=%22eagle+usb%22)  and never install the eagle-usb drivers. That is because of the kernel version that dapper uses.

For the last question :
You can select to boot with special parameters. This is an option and if not (because i don't remember) there is certainly exist a F# option for that at the bottom of the screen. Opting for them, the only thing that you have to do is to add these two paremeters as you said, meaning acpi=off apm=off.

I hope this helps you.

---

