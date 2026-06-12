---
title: "How do I disable bluetooth on boot up?"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by clevertomato on 2010-01-15
I have a Dell Studio 1555 and want to have bluetooth turned off at startup but still be able to turn it on when I need it. I've read several suggested methods, but they all seem to be specific to other brand notebooks.

Can anyone give me a push in the right direction, please?

BTW, disabling the bluetooth applet in Startup Applications does not accomplish what I desire. I want the bluetooth/network manager applet to run at startup, I just want the bluetooth turned OFF at startup.

---

### Post by konqueror7 on 2010-01-15
go to System > Administration > Bluetooth option? what ubuntu version are you using? if your are not using 9.10/karmic, you may want to try System > Administration > Services to uncheck bluetooth or ```
sudo service bluetooth stop
```..or you may want to insta [BootUp Manager]("apt:bum") in karmic to disable them...

---

### Post by clevertomato on 2010-01-15
I'm running Karmic amd64. If you mean System/Preferences/Bluetooth, that only controls when the icon is displayed in the panel, not whether bluetooth is on or off. I can uncheck bluetooth service in System/Administration/Services, but I'm not certain if that will actually turn my bluetooth hardware OFF or simply turn off the software that manages it.

**I want my bluetooth hardware itself to be turned off when I'm not using it so it won't be draining my battery.** Unfortunately I do not have a physical switch to control it and the Fn key that controls it controls BOTH my wireless adapter AND the bluetooth. I use wireless all the time but bluetooth only sometimes.

---

### Post by konqueror7 on 2010-01-15
> **shawnboy said:**
> I'm running Karmic amd64. If you mean System/Preferences/Bluetooth, that only controls when the icon is displayed in the panel, not whether bluetooth is on or off. I can uncheck bluetooth service in System/Administration/Services, but I'm not certain if that will actually turn my bluetooth hardware OFF or simply turn off the software that manages it.

**I want my bluetooth hardware itself to be turned off when I'm not using it so it won't be draining my battery.** Unfortunately I do not have a physical switch to control it and the Fn key that controls it controls BOTH my wireless adapter AND the bluetooth. I use wireless all the time but bluetooth only sometimes.

mmm...i don't know any,,,because in windows, its pretty much the same, you disable the interface/service...so disabling the service it self will prevent bt from using at all, thus like turning it off...

mmm,,,the fn button should really have functioned in windows if you have one...disable it in windows (because there functions the fn combo), then return to ubuntu,,,but this is only assuming you are in dual boot...

have you tried going in the bios if the bluetooth option is available? some do have options in it to disable them...

---

### Post by gradinaruvasile on 2010-01-15
Use rfkill if you use ubuntu 9.10.
to stop it:

sudo rfkill block bluetooth

unblock:
sudo rfkill unblock bluetooth

The settings are remembered on reboot. This is soft blocking, anytime you want just unblock it. I made a script that toggles it on/off (and the same with wireless).

rfkill list 

shows the available options.

---

### Post by gradinaruvasile on 2010-01-15
I could modify the scripts for you if you send me the output of 

rfkill list

in a terminal.

---

### Post by konqueror7 on 2010-01-15
> **gradinaruvasile said:**
> I could modify the scripts for you if you send me the output of 

rfkill list

in a terminal.

oh, does this kill the process/service, or disable the whole interface? thanks, didn't know there is one,,,learned something new...:D

sorry i couldn't be of help....:(

---

### Post by gradinaruvasile on 2010-01-15
> **konqueror7 said:**
> oh, does this kill the process/service, or disable the whole interface? thanks, didn't know there is one,,,learned something new...:D

sorry i couldn't be of help....:(

This disables (soft blocks) the interface.
The toggler script disables it if enabled/enables it if disabled.

I need the output because i dont know if the output order is the same. The script uses "rfkill list" output parsing by line numbers to keep it simple (and to my knowledge :) ). If you send me that output i can modify the script to suit your laptop. Then you can make a launcher on menu or taskbar on which when you click, it toggles the device on/off.

---

### Post by konqueror7 on 2010-01-15
> **gradinaruvasile said:**
> This disables (soft blocks) the interface.
The toggler script disables it if enabled/enables it if disabled.

I need the output because i dont know if the output order is the same. The script uses "rfkill list" output parsing by line numbers to keep it simple (and to my knowledge :) ). If you send me that output i can modify the script to suit your laptop. Then you can make a launcher on menu or taskbar on which when you click, it toggles the device on/off.

i'm not the one who got the problem,,,:o

but good thing to know that a better solution is available...

---

### Post by clevertomato on 2010-01-15
konqueror7, changing bluetooth settings in the bios wouldn't accomplish what I want. I'd have to reboot and change back in the bios when I needed bluetooth and I don't want to have to do that.

 				 				gradinaruvasile: I'm on a dif machine right now, but I will get that info to you. I would appreciate your helping me out with that script. Thanks in advance.

Shawn

---

### Post by clevertomato on 2010-01-15
Here ya go:```
user@ubuntu:~$rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Script will be very helpful. How did you learn about this useful little command?

-- until I hear from you with the script, I tried ```
sudo rfkill block bluetooth
``` and it turned off bluetooth, BUT when I rebooted, bluetooth was back on. Isn't this supposed to be remembered after a reboot?

---

### Post by gradinaruvasile on 2010-01-15
> **shawnboy said:**
> Here ya go:```
user@ubuntu:~$rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Script will be very helpful. How did you learn about this useful little command?

Here you go. Remember, you MUST launch these scripts with administrator (root) privileges. If you plan to make a menu item for them the command is in the following format:

```
gksudo bash /path/scriptname
```

---

### Post by gradinaruvasile on 2010-01-15
> **shawnboy said:**
> Here ya go:```
user@ubuntu:~$rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Script will be very helpful. How did you learn about this useful little command?

-- until I hear from you with the script, I tried ```
sudo rfkill block bluetooth
``` and it turned off bluetooth, BUT when I rebooted, bluetooth was back on. Isn't this supposed to be remembered after a reboot?
 
It may not remember on reboot. Sorry, i wanted to say hibernate. I rarely reboot my laptop, i use hibernate/suspend. Also, my laptop (Dell D630) has 2 wireless/2 bluetooth (virtual) devices: dell-wifi/phy0 and del-bluetooth/hci0. I control the dell devices, but it works all the same on the others also.

I kinda stumbled upon the command messing around.

---

### Post by clevertomato on 2010-01-15
Thanks! Those scripts will come in handy.

I took it one step further for my use. I added ```
rfkill block bluetooth
``` to my /etc/rc.local file just before the last line (exit 0). Now my bluetooth is turned off at every boot, but the bluetooth applet and dimmed icon is still in the panel (like I wanted) so I can turn it back on anytime I want.

Thanks for the help!

---

### Post by prostar on 2010-03-01
Nice! An easy solution to turn off the bluetooth hardware using cli.

---

### Post by aaron.lwe on 2010-05-03
run this:
sudo echo "options rfkill master_switch_mode=0" > /etc/modprobe.d/rfkill.conf
this will stop bluetooth being activated during boot.

See: [http://comments.gmane.org/gmane.linux.acpi.ibm-acpi.devel/1955](http://comments.gmane.org/gmane.linux.acpi.ibm-acpi.devel/1955)

---

### Post by Lokesh123 on 2010-05-03
> **aaron.lwe said:**
> run this:
sudo echo "options rfkill master_switch_mode=0" > /etc/modprobe.d/rfkill.conf

this returns a: bash: /etc/modprobe.d/rfkill.conf: Permission denied

How to do it?

Thanks,
Lokesh

---

### Post by aaron.lwe on 2010-05-04
> **Lokesh123 said:**
> this returns a: bash: /etc/modprobe.d/rfkill.conf: Permission denied

How to do it?

Thanks,
Lokesh

Make sure you are allowed to sudo, or you just run this command as root, as creating a new file named rfkill.conf under /etc/modprobe.d requires root privilege.

---

### Post by deepclutch on 2010-05-11
I wanted bluetooth device(On the PC) disabled when booted.
```
sudo su -
``````
hciconfig hci0 down 
```^ will make bluetooth device disabled.


I don't remember how exactly..But ,I made a script with above syntax and put it in /etc/init.d/somefilename and some link made to /etc/rcS.d/filename .(I forgot all this :( ...will try to find the proper way to add a script to be ran on boot up.)
  [SIZE=3]**UPDATE**[/SIZE]:
Here is how:

[LIST]
[*]Make a file inside /etc/init.d/ as "nobluetooth" with below content :
[/LIST]
```
#!/bin/bash
echo "Disabling hci0 bluetooth usb dongle"

/usr/sbin/hciconfig hci0 down &
```

and give it execution right(sudo chmod +x /etc/init.d/nobluetooth)


[LIST]
[*] Run update-rc.d to wire all the symlinks needed for boot
[/LIST]
```
update-rc.d nobluetooth start 26 2 3 4 5  **.**
```


[LIST]
[*]On next boot ,open a terminal and check "hciconfig" output to confirm hci0 is "down"
[/LIST]

[LIST]
[*] later,if You want to enable bluetooth :
[/LIST]
 ```
sudo hciconfig hci0 up
``` OR Even a Launcher on Desktop/Panel with:
```
gksudo  hciconfig hci0 up
```

--
But ,Another Easy way is to blacklist kernel module bluetooth by adding into /etc/modprobe.d/blacklist.conf with a new line:
```
blacklist bluetooth
```^^^ This way ,bluetooth is permanently disabled in the PC.
^/etc/modprobe.d/00.local file was used in earlier distros when blacklisting some modules never worked with blacklist.conf entry.

Thanks

---

### Post by SINternet on 2010-05-12
gradinaruvasile suggestion worked for me! Backed up rc.local when updates wipe out my tweaking.

SIN

---

### Post by qhoore on 2010-05-14
Here the easiest way, i ve try it on lucid.

go to System > preference > startup application

Add New

Fill the command with :

rfkill block bluetooth

the other field can be fill as you want..

---

### Post by youbuntu on 2010-10-14
This is absolutely ridiculous! Which moron made the decision to leave BT *on* by default?

I thought Linux was designed by intelligent people...

---

### Post by btindie on 2010-10-17
> **Lokesh123 said:**
> 
[QUOTE=aaron.lwe;9223483]run this:
sudo echo "options rfkill master_switch_mode=0" > /etc/modprobe.d/rfkill.conf


this returns a: bash: /etc/modprobe.d/rfkill.conf: Permission denied

How to do it?

Thanks,
Lokesh[/QUOTE]

That command will run *echo* with root privileges and the redirect will have normal user privileges hence the message you got. For it to work correctly you need to use *tee*
```
echo "options rfkill master_switch_mode=0" | sudo tee /etc/modprobe.d/rfkill.conf
```

---

### Post by plj on 2010-10-20
> **btindie said:**
> That command will run *echo* with root privileges and the redirect will have normal user privileges hence the message you got. For it to work correctly you need to use *tee*
```
echo "options rfkill master_switch_mode=0" | sudo tee /etc/modprobe.d/rfkill.conf
```

Setting “options rfkill master_switch_mode=0” in /etc/modprobe.d/rfkill.conf did **not** fix this on HP Mini 5101; the only thing that did was to execute “rfkill block bluetooth” in /etc/rc.local.

(That HP Mini is still running Lucid.)

---

### Post by btindie on 2010-10-20
I was telling you how to correctly run the command the previous poster gave to update rfkill.conf ....
 
I think the command does work, if you only boot into terminal mode. I think the problem is when X starts along with all the other programs which ignore the current status of the bluetooth radio turning it on. When the command is run in rc.local, that is one of the last things that's run on startup and thus turns it off. So bluetooth is loaded as Off -> On -> Off via rc.local, not great I know. It would be good if it remembered the previous setting as it does under Windows. FYI, hciconfig hci0 down does the same thing I think. That's one of my main irritations having Bluetooth turned on at startup when it's not needed - I'd rather it was just left off when the module was loaded.

---

### Post by ferdez on 2010-10-22
In 10.10 the command "rfkill block bluetooth" seems to work.

---

### Post by mahy on 2010-11-04
> **glossywhite said:**
> This is absolutely ridiculous! Which moron made the decision to leave BT *on* by default?

I thought Linux was designed by intelligent people...

I second that, unfortunately Ubuntu desktops (both KDE and Gnome) have been painstakingly designed to be as idiot-friendly as possible, giving way to errors such as this one...

---

### Post by Bage2010 on 2012-01-06
> **qhoore said:**
> Here the easiest way, i ve try it on lucid.

go to System > preference > startup application

Add New

Fill the command with :

rfkill block bluetooth

the other field can be fill as you want..

Just set this up on 11.10 x64 works a treat - simple is often then best :D

---

