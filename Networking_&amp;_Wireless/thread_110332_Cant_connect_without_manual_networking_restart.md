---
title: "Cant connect without manual networking restart"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by vulturesrow on 2005-12-30
Hardware: Dell Inspiron 8100 Laptop, Dlink DI-524 Wireless Router, Dlink DWL-G630(ver C2).

Software: Brand new, fully updated Breezy Badger install including wpasupplicant.

Problem: I followed the excellent WPA howto and it seemed to work like a charm. Upon reboot, I had no connectivity. I used the following command (from the How-To):

```

sudo invoke-rc.d networking restart
```



and immediately had full connectivity. Based on the How-To, this seems like the network is being configured before wpasupplicant is being started, but I followed the steps in the how-to to the letter which is supposed to prevent this. The only anomaly I could see in the boot messages is that wpasupplicant appears to try and start itself twice, but I havent been able to figure out why. Any help would be appreciated.

---

### Post by cwaldbieser on 2005-12-30
[QUOTE=vulturesrow]Hardware: Dell Inspiron 8100 Laptop, Dlink DI-524 Wireless Router, Dlink DWL-G630(ver C2).

Software: Brand new, fully updated Breezy Badger install including wpasupplicant.

Problem: I followed the excellent WPA howto and it seemed to work like a charm. Upon reboot, I had no connectivity. I used the following command (from the How-To):

```

sudo invoke-rc.d networking restart
```



and immediately had full connectivity. Based on the How-To, this seems like the network is being configured before wpasupplicant is being started, but I followed the steps in the how-to to the letter which is supposed to prevent this. The only anomaly I could see in the boot messages is that wpasupplicant appears to try and start itself twice, but I havent been able to figure out why. Any help would be appreciated.[/QUOTE]

Can you post the output of:
```

$ ls /etc/rc$(runlevel | cut -d ' ' -f 2).d

```

Explanation: lists the contents of one of the /etc/rc#.d folders, where # is your current runlevel (2-5).  These folders contain links to service programs in the /etc/init.d folder.  The names of the links tell what order things are run at boot time.

---

### Post by vulturesrow on 2005-12-30
Here is the output. 

```
S05vbesave   S11klogd  S14ppp     S20apmd          S20pcmcia     S20wpasupplicant  S89anacron  S98usplash       S99rmnologin
S10acpid     S12dbus   S19cupsys  S20hotkey-setup  S20powernowd  S25bluez-utils    S89atd      S99acpi-support  S99stop-bootlogd
S10sysklogd  S13gdm    S19hplip   S20makedev       S20rsync      S25mdadm          S89cron     S99fetchmail
```

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=vulturesrow]Here is the output. 

```
S05vbesave   S11klogd  S14ppp     S20apmd          S20pcmcia     S20wpasupplicant  S89anacron  S98usplash       S99rmnologin
S10acpid     S12dbus   S19cupsys  S20hotkey-setup  S20powernowd  S25bluez-utils    S89atd      S99acpi-support  S99stop-bootlogd
S10sysklogd  S13gdm    S19hplip   S20makedev       S20rsync      S25mdadm          S89cron     S99fetchmail
```[/QUOTE]
Well, it looks like wpasupplicant is only in there once.  I am not sure when the network scripts are getting initialized, since they don't seem to be using the SysV style initialization, so it is hard for me to say when networking is being initialized in relation to wpasuplicant.

Maybe someone else has some ideas?

---

### Post by vulturesrow on 2005-12-31
When I CTRL-ALT-F8 it clearly shows wpa supplicant being started twice in the messages. Part of the howto (which is the most recent WPA hotwo in the customization forum) has you create a symbolic link to wpasupplicant to get it to run at the proper time. IS there any other information IC an provide that would be helpful?

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=vulturesrow]When I CTRL-ALT-F8 it clearly shows wpa supplicant being started twice in the messages. Part of the howto (which is the most recent WPA hotwo in the customization forum) has you create a symbolic link to wpasupplicant to get it to run at the proper time. IS there any other information IC an provide that would be helpful?[/QUOTE]
I did some digging, and it looks like Ubuntu also runs the scripts in /etc/rcS.d *before* running any other services.  Can you post listing of that directory, too?

Also, if you have a link to the HOWTO you are following, it will save me the trouble of searching around for it.

---

### Post by Lambert on 2005-12-31
He cwald, He's following this howto

[http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa](http://ubuntuforums.org/showthread.php?t=90450&highlight=wpa)

If you look in his rc2.d directory you see where wpasupplicant is starting at S20. This how to adds a link in rcS.d called iwpa which is also supposed to start wpasupplicant which is why he's seeing it start twice in dmesg. (that one is set to S40, just before networking)

In rcS.d networking starts at S40

Not sure why that howto add's another start script for wpasupplicant.

Now I'm not that knowledgeable when it comes to wpa supplicant but my understanding is both of these start scripts do nothing but start the wpasupplicant daemon. In other instructions I've seen about wpa there are other steps needed so wpasupplicant is activated for a certain interface.

Such as this added to interface file in a pre-up stanza

**wpa**_supplicant -iath0 -c/etc/**wpa**_supplicant.conf -Dmadwifi

(except ath0 and madwifi would be changed to the device/driver that's being used)

or

pre-up /etc/init.d/**wpa**supplicant start
pre-up sleep 5


Maybe that second startup script isn't finishing in time before networking starts to run and it's the culprit of the problem.

---

### Post by vulturesrow on 2005-12-31
Gents, 

I have discovered, much to my chagrin, that this is not a WPA problem.  I uninstalled wpasupplicant and went back to my vanilla setup and changed my wireless encryption to WEP. I get the exact same problem, that is, I have a wireless connection, but not connectivity until using the invoke-rc.d networking restart.  I apologize for leading the discussion down the wrong path instead of leaving it opne. Does this perspective help at all?

---

### Post by cwaldbieser on 2006-01-01
[QUOTE=vulturesrow]Gents, 

I have discovered, much to my chagrin, that this is not a WPA problem.  I uninstalled wpasupplicant and went back to my vanilla setup and changed my wireless encryption to WEP. I get the exact same problem, that is, I have a wireless connection, but not connectivity until using the invoke-rc.d networking restart.  I apologize for leading the discussion down the wrong path instead of leaving it opne. Does this perspective help at all?[/QUOTE]
Seems a little weird.  I am not sure what kind of logging exists for the networking service, but you could try investigating that.

If you don't want to worry about that, you could just create a script in /etc/init.d that does the restart you manually do (and maybe sleeps a couple seconds first).  Then you could link it to runlevel 2 with
```

$ sudo update-rc.d script-name 99

```
Hopefully, that will keep you from having to run it yourself each time.

---

### Post by seaan on 2006-01-01
[QUOTE=vulturesrow]Gents, 
I have discovered, much to my chagrin, that this is not a WPA problem.  I uninstalled wpasupplicant and went back to my vanilla setup and changed my wireless encryption to WEP. 
...
[/QUOTE]

Hope this helps.
I have a DLink DWL-G650 and installed Breezy yesterday.
I put all the wireless settings in /etc/network/interfaces.
I use WEP with a shared key.
Although correct, the wireless settings were useless until I gave:
```
iwpriv ath0 authmode 2
```
which instructs the card to use a shared key.
The question was: how to configure this at boot time?
You can use the "pre-up" directive in /etc/network/interfaces.
See below the content of my file as regards wireless interface ath0:

```
iface ath0 inet dhcp
	pre-up /sbin/iwpriv ath0 authmode 2
wireless-essid home
wireless-key s:MY_ASCII_PASSWORD_IN_13_CHARS
wireless-mode managed
auto ath0
```

Now wireless interfaces starts correctly at boot time.

---

### Post by vulturesrow on 2006-01-01
SEan, 

Thanks for the input. Unfortunately that didnt seem to help. :( In fact it made the problem worse, that is I couldnt even connect to my network at all. Any other ideas?

---

### Post by vulturesrow on 2006-01-01
Anyone want to give this one last shot given my recent revelation?? (yea I am desperate) :)

---

### Post by seaan on 2006-01-02
Vulture,
what does it mean you can't connect anymore?
If it happened after the latest changes can you just roll back to the previous situation?
Can you also post the content of your /etc/network/interfaces file (you may hide sensitive information, if any)
Bye

---

### Post by vulturesrow on 2006-01-02
Seann, et al.,

Problem is solved. As is usually the case, it turned out to be something very simple. Basically a misconfigured /etc/network/interfaces file. I was using static IPs for my home network and I had my laptop statically assigning the same ip to both eth0 and ath0. I had a feeling the problem was something to do with that, but it took the help of a kind soul on  IRC to help with that. Thanks to everyone for the their input and help, you are a great bunch!!

---

