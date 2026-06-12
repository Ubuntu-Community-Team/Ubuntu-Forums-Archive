---
title: "How to enable bluetooth under 11.04"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by raunhar on 2011-05-25
I upgraded from 10.10 yesterday.
The Bluetooth is disabled. Even when I click on Blue Tooth on, it doesnot get highlighted or detects the nearby devices.

In 10.10 , it worked just fine.

---

### Post by matt_symes on 2011-05-25
Hi

Open a terminal and type

```
sudo apt-get install rfkill
```

to install rfkill if it's not installed. Then type

```
rfkill list
```

Post back results.

Kind regards

---

### Post by raunhar on 2011-05-25
$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by matt_symes on 2011-05-25
Hi

> **raunhar said:**
> $ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

That looks fine. Open a terminal and type

```
sudo service bluetooth status
```

Post back results.

Kind regards

---

### Post by raunhar on 2011-05-26
$ sudo service bluetooth status
[sudo] password for yyyy: 
 * bluetooth is running

If i use
sudo killall bluetoothd
sudo bluetoothd

The bluetooth gets enabled, but on restart, the same situation

---

### Post by matt_symes on 2011-05-26
Hi

> **raunhar said:**
> $ sudo service bluetooth status
[sudo] password for yyyy: 
 * bluetooth is running

If i use
sudo killall bluetoothd
sudo bluetoothd

The bluetooth gets enabled, but on restart, the same situation

Restart your machine so bluetooth is not connecting and type

```
lsmod | grep bluetooth
```Post back the results of that. Then type

```
ps aux | grep bluetooth
```Post back the results of that.

Then try restarting the bluetooth service.

```
sudo service bluetooth restart
```Run this command again

```
ps aux | grep bluetooth
```Post back the results of that. 

If it does not automatically connect type

```

sudo killall bluetoothd
sudo bluetoothd
ps aux | grep bluetooth
```and post back the results of that that last ps aux | grep command.

Hopefully that will give us some idea of what is going in.

Kind regards

---

### Post by raunhar on 2011-05-26
~$ lsmod | grep bluetooth
bluetooth              65565  9 rfcomm,sco,bnep,l2cap,btusb

$ ps aux | grep bluetooth
root       769  0.0  0.1   4176  1632 ?        Ss   10:35   0:00 /usr/sbin/bluetoothd --udev
user    1553  0.0  0.9 104876  9424 ?        Sl   10:35   0:00 bluetooth-applet
user    2740  0.0  0.0   4160   868 pts/0    S+   10:47   0:00 grep --color=auto bluetooth
$ sudo service bluetooth restart
[sudo] password for user: 
 * Stopping bluetooth                                                                                                                                  [ OK ] 
 * Starting bluetooth                                                                                                                                  [ OK ] 
$ ps aux | grep bluetooth
user    1553  0.0  0.9 104876  9424 ?        Sl   10:35   0:00 bluetooth-applet
root      2901  0.0  0.1   4176  1936 ?        Ss   10:47   0:00 /usr/sbin/bluetoothd --udev
user   2950  0.0  0.0   4160   864 pts/0    S+   10:48   0:00 grep --color=auto bluetooth

---

### Post by matt_symes on 2011-05-26
Hi

After that last command you ran (restarting the service) did it connect ?

If not type
```

sudo killall bluetoothd 
sudo bluetoothd 
ps aux | grep bluetooth
```

and post back that last command

Kind regards

---

### Post by raunhar on 2011-05-26
Yes, it started, but on reboot no.

---

### Post by matt_symes on 2011-05-26
Hi

> **raunhar said:**
> Yes, it started, but on reboot no.

That's interesting. I think the next thing to look at is your configuration files. Can you post the output of 

```
cat /etc/bluetooth/main.conf
```Please post the results between code tags like this

[noparse]```
text from file
```[/noparse]

It makes it easier to read :)

You will get output like the code block in this post.

Kind regards

---

### Post by raunhar on 2011-05-27
$ cat /etc/bluetooth/main.conf


[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler.
DiscoverSchedulerInterval = 0

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false

# Enable Low Energy support if the dongle supports. Default is false.
# Enable/Disable interleave discovery and attribute server over LE.
EnableLE = false

# Enable the GATT Attribute Server. Default is false, because it is only
# useful for testing. Attribute server is not enabled over LE if EnableLE
# is false.
AttributeServer = false

---

### Post by steviejay on 2011-05-27
I'm having exactly the same problem but with Linux Mint 11 which is based on Ubuntu 11.04.

Bluetooth icons reports that bluetooth is on but preferences show it as disabled and when I click the turn bluetooth on button it just greys out.

The only way I can get it to work is by typing commands in the terminal but back to square one after reboot or even after just removing the adapter and plugging it in again, major PITA.

Didn't have this problem with U10.10 or LM10 which Ive reverted back to using until this issue is fixed.

---

### Post by rvchari on 2011-05-27
> **steviejay said:**
> I'm having exactly the same problem but with Linux Mint 11 which is based on Ubuntu 11.04.

Bluetooth icons reports that bluetooth is on but preferences show it as disabled and when I click the turn bluetooth on button it just greys out.

The only way I can get it to work is by typing commands in the terminal but back to square one after reboot or even after just removing the adapter and plugging it in again, major PITA.

Didn't have this problem with U10.10 or LM10 which Ive reverted back to using until this issue is fixed.

i am using ubuntu natty 64 bit from the live usb stick (till i am fully confirmed that all my apps and services will run without any hitch, i ll stick to this mode) and i ve been having the same problem. i am following this thred and will now boot onto my usb live and check out if things work out....
i ll post my comments after i ve tried these steps....

---

### Post by rvchari on 2011-05-27
i am now on my ubuntu live natty 64 bit usbstick. 
bluetooth starts but cant identify my nokia n70 !!! it seems to keep spinning in searching for devices !!!
here i am posting my outputs as mentioned in the earlier posts...

[B]ubuntu@ubuntu:~$ lsmod | grep bluetooth
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
ubuntu@ubuntu:~$ ps aux | grep bluetooth
ubuntu   14823  0.0  0.2 252860  8640 ?        Sl   22:11   0:00 bluetooth-applet
root     15491  0.0  0.0  23236  2132 ?        Ss   22:46   0:00 bluetoothd
ubuntu   15501  0.0  0.0  13128  1060 pts/0    S+   22:56   0:00 grep --color=auto bluetooth


ubuntu@ubuntu:~$ sudo killall bluetoothd
ubuntu@ubuntu:~$ sudo bluetoothd
ubuntu@ubuntu:~$ sudo service bluetooth restart
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
ubuntu@ubuntu:~$ cat /etc/bluetooth/main.conf
[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler.
DiscoverSchedulerInterval = 0

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false

# Enable Low Energy support if the dongle supports. Default is false.
# Enable/Disable interleave discovery and attribute server over LE.
EnableLE = false

# Enable the GATT Attribute Server. Default is false, because it is only
# useful for testing. Attribute server is not enabled over LE if EnableLE
# is false.
AttributeServer = false[/B]

---

### Post by steviejay on 2011-05-27
OK this is what I've discovered so far.

Bluetooth adapter fires up automatically with Ubuntu 10.10 & Linux Mint 10. Also with Linux Mint 10 KDE & Xfce.

The same problem uccurrs with Ubuntu 11.04, Mint 11 & Fedora 15 although on all three I can get the Bluetooth service working by entering commands in the terminal. I think all of these latest releases use Gnome 3 *(maybe someone can correct me if I'm wrong)* whereas the earlier versions used Gmome 2. So my guess is the problem lies there.

---

### Post by rvchari on 2011-05-27
atlast i could connect my device. gnome-bluetooth could not identify my nokia, so i used another way to pair it. i chose to send a file to my laptop over blue tooth and it asked for paitring before i sent it, i did it at that point.
it remains to be seen if bluetooth starts on its own after a reboot or i have to go thru the process all over again !!!

natty needs to be straightenend up !!!

---

### Post by rvchari on 2011-05-27
> **steviejay said:**
> OK this is what I've discovered so far.

Bluetooth adapter fires up automatically with Ubuntu 10.10 & Linux Mint 10. Also with Linux Mint 10 KDE & Xfce.

The same problem uccurrs with Ubuntu 11.04, Mint 11 & Fedora 15 although on all three I can get the Bluetooth service working by entering commands in the terminal. I think all of these latest releases use Gnome 3 *(maybe someone can correct me if I'm wrong)* whereas the earlier versions used Gmome 2. So my guess is the problem lies there.

cant say exactly if g3 is the cause, earlier i had complied gnome 3 to test and have a feel and was using that under ubuntu 10.10 (which i removed after i found it not so pleasing). i used to fire up g3 issuing a command and even tried it to set it up on start up.

during those days my bluetooth was functioning well so my hunch is natty has to be tweaked to identify and run bluetooth and certain other services that may have bugs.... i may be wrong but this is my observation.

---

### Post by matt_symes on 2011-05-27
Hi

Please boot into 11.04 so the bluetooth does not work.

Open a terminal and type

```
hciconfig
```Please post the output of this command back here. I want to see it. @[raunhar]("http://ubuntuforums.org/member.php?u=699728"), i especially want to see the output of this command on your machine.

If you get output like this (notice the [COLOR=Blue]DOWN[/COLOR]).....

```
matthew@matthew-Aspire-7540:~$ hciconfig
[COLOR=Red]hci0[/COLOR]:    Type: BR/EDR  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    [COLOR=Blue]DOWN [/COLOR]
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:0 acl:0 sco:0 commands:0 errors:0

matthew@matthew-Aspire-7540:~$
```....type

```
sudo hciconfig [COLOR=Red]hci0[/COLOR] up
```Replace hci0 if required. 

Does this restart the applet and enable bluetooth ? 

After that, reboot your PC again into 11.04. Open a terminal and type

```
rfkill list
```Post the results back here. This last rfkill step is important as i need to see if it is being soft blocked after rebooting so please post it.

If it does it means the hci0 interface is down when booting up and on rebooting it is being softblocked.

And for once, i can replicate this on my machine.
 I need to see if the behaviour on your machines is _exactly_ the same as mine.

Kind regards

---

### Post by EdTheUniqueGeek on 2011-05-27
I am having the exact same problem in the new release of Mint 11 and have been following along.
Here is my output:

```
ed@ed-Vostro-Mint11 ~ $ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by trukker on 2011-05-28
Having the same problem on my machine when upgrading to 11.04

Following the posts here, and restarting the daemon did the trick!

sudo service bluetooth restart
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 


cat /etc/bluetooth/main.conf
[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 0 to use controller scheduler.
DiscoverSchedulerInterval = 0

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false

# Enable Low Energy support if the dongle supports. Default is false.
# Enable/Disable interleave discovery and attribute server over LE.
EnableLE = false

# Enable the GATT Attribute Server. Default is false, because it is only
# useful for testing. Attribute server is not enabled over LE if EnableLE
# is false.
AttributeServer = false

---

### Post by steviejay on 2011-05-28
> **trukker said:**
> Having the same problem on my machine when upgrading to 11.04

Following the posts here, and restarting the daemon did the trick!




You mean permanently or just for that session?

I am able to get the bluetooth working by running the stop/restart command but it only works temporarily. Take the adapter out or re-boot and it's back to square one.

---

### Post by trukker on 2011-05-29
I've rebooted the machine, and the Bluetooth icon is still on... so seems permanent!

---

### Post by trukker on 2011-05-29
I've rebooted again, and the Bluetooth panel icon is greyed out.... running 
sudo service bluetooth restart restarted it, and bluetooth is usable...

---

### Post by EdTheUniqueGeek on 2011-05-29
For me, doing a service restart doesn't fix it, the adapter still doesn't appear.

---

### Post by trukker on 2011-05-30
Seems a problem in Natty... Have a look at:

[http://askubuntu.com/questions/45871/bluetooth-doesnt-start-up-properly-when-i-start-up](http://askubuntu.com/questions/45871/bluetooth-doesnt-start-up-properly-when-i-start-up)

and related questions on the right hand side of the page...

---

### Post by EdTheUniqueGeek on 2011-05-30
Yeah, none of that helped me.

---

### Post by trukker on 2011-05-30
Restarting the bluetooth service works on my laptop.... I had thought that it was a bug in the upgrade path, so I did a full reinstall, with the same results... seems like a problem in natty.... grrrrrr....

---

### Post by matt_symes on 2011-05-31
Hi

Did anybody try post 18 to  see if the interface is down at startup ?

If it is has anybody tried to re-enable it in one of the configuration files ? I am currently in Lucid so i can't test it but i would try to bring the interface up in rc.local or one of the other files.

Kind regards

---

### Post by EdTheUniqueGeek on 2011-05-31
Yes, it is DOWN at startup.
Unfortunately, I do not know Linux well enough to know how to re-enable in the config files.

---

### Post by matt_symes on 2011-05-31
Hi

Try this. I don't know if it will work as i cant find my Bluetooth dongle. Still, it's worth a try.

Open a terminal and type

```
sudo nano /etc/rc.local
```

Enter your password. It will not be echoed to the screen. This is normal.

Add this line before exit 0

```
sudo service bluetooth restart
```

Press ctrl + o to save and ctrl + x to exit.

Make the file exectuable if it is not already by typing

```
sudo chmod 755 /etc/rc.local
```

Plug your Bluetooth adaptor in if required and restart your PC.

Kind regards

---

### Post by EdTheUniqueGeek on 2011-05-31
Thank you.
I have completed these steps and when I restart the machine and do a hciconfig I still get a DOWN.

```
ed@ed-Vostro-Mint11 ~ $ hciconfig
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
	DOWN 
	RX bytes:0 acl:0 sco:0 events:0 errors:0
	TX bytes:6 acl:0 sco:0 commands:2 errors:0
```

Also, just an F.Y.I.: This is an internal bluetooth adapter that came with my Dell Vostro v130.

---

### Post by ratatouille on 2011-06-04
Thanks Mat_Symes,
Your solution worked for me.
It's working...

---

### Post by NightTiger2 on 2011-06-06
I'm having the same problem too , made a new installation on a new laptop and my bluetooth mouse didn't worked since the beginning, tried the terminal commands and none did anything.  this ubuntu version is disappointing

---

### Post by matt_symes on 2011-06-08
Hi

I still can't find my Bluetooth dongle anywhere so i cannot test any of this. I might have to buy another.

To summarise so far. Try these steps.

Try 

To list any blocks...

```
rfkill list
```Make sure it's not hard blocked by a hardware switch.

If it's soft blocked.

```
sudo rfkill unblock all
```This should remove any softblocks.

```
service bluetooth status
```to check the bluetooth status. If it's not running check it's added as a start application. If it is running, restart it.

```
sudo service bluetooth restart
```This will restart the bluetooth daemon.

Check to see if the interface is down.

```
hciconfig
```

If it is down try to raise it. You may need to change hci0. You can get that from the above command.

```
sudo hciconfig hci0 up
```This will try to raise the interface. If any of these steps do not fix it, you are looking at a different issue.

You can put then all in a script so you only need to run it at start up.

Kind regards

---

### Post by ccsureshbabu on 2011-08-10
I am very new to ubuntu. recently i have changed my OS to 11.04 version  by completly uninstalling windows 7.. everything work fine except bluetooth. i use Dell N4010 lap. I can see a blue tooth icon at the panel, but clicking on it shows only three options

Bluetooth: On (this is faded and not able to click)
Turn Off Bluetooth
and Preferences.

clicking on preferences menu will open a box, where it shows a message "blue tooth disabled" at the top. it has a big command button at the center of the box with a caption of "Turn On Bluetooth". But clicking on the button will not make any changes. the button will fade out and stays as such.

I am not able to send or receive files through my blue tooth.

I would be so greateful if someone help me out..

Thanks
Suresh

---

### Post by raunhar on 2011-08-10
Its good that you are switching to Open Source.
11.04 has certain bugs which create problems with Bluetooth and certain old USB printers.
If you get 10.10, get it and install it. Your bluetooth and all other hardware will work fine. 11.10 will be free from these bugs (hope).

---

### Post by EdTheUniqueGeek on 2011-08-10
> **ccsureshbabu said:**
> I am very new to ubuntu. recently i have changed my OS to 11.04 version  by completly uninstalling windows 7.. everything work fine except bluetooth. i use Dell N4010 lap. I can see a blue tooth icon at the panel, but clicking on it shows only three options

Bluetooth: On (this is faded and not able to click)
Turn Off Bluetooth
and Preferences.

clicking on preferences menu will open a box, where it shows a message "blue tooth disabled" at the top. it has a big command button at the center of the box with a caption of "Turn On Bluetooth". But clicking on the button will not make any changes. the button will fade out and stays as such.

I am not able to send or receive files through my blue tooth.

I would be so greateful if someone help me out..

Thanks
Suresh

I was actually able to get Bluetooth working in Linux Mint 11 on my Dell Vostro V130 using the following bug fix from comment #10:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/714862)

First you will need to determine what Bluetooth hardware you have in your Dell to see if that fix applies as the drivers from that fix, I believe, only apply to a specific hardware. Complete the following from terminal to see if you have Atheros bluetooth chipset:

lspci

It may say something like Network controller to list the type of bluetooth device. I have the AR9285 and the driver from that bug fix worked for me.

---

### Post by eltntawy on 2012-01-16
Hi, 

I have the same problem but its not work by doing above steps and its output of the last post


lsmod | grep bluetooth
bluetooth             148839  10 bnep,rfcomm
user:~$ ps aux | grep bluetooth
user  1543  0.0  0.3 127348 10408 ?        Sl   15:14   0:00 bluetooth-applet
root      7222  0.0  0.0   4496  1556 ?        Ss   18:58   0:00 /usr/sbin/bluetoothd
user 10461  0.0  0.0   4448   804 pts/0    S+   19:12   0:00 grep --color=auto bluetooth
user:~$ sudo service bluetooth restart
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
user:~$ ps aux | grep bluetooth
user  1543  0.0  0.3 127348 10408 ?        Sl   15:14   0:00 bluetooth-applet
root     10527  0.0  0.0   4496  1556 ?        Ss   19:12   0:00 /usr/sbin/bluetoothd
user 10549  0.0  0.0   4448   800 pts/0    S+   19:12   0:00 grep --color=auto bluetooth
user:~$ sudo killall bluetoothd
user:~$ sudo bluetoothd
user:~$ ps aux | grep bluetooth
user  1543  0.0  0.3 127348 10408 ?        Sl   15:14   0:00 bluetooth-applet
root     10596  0.0  0.0   4496  1556 ?        Ss   19:13   0:00 bluetoothd
user 10609  0.0  0.0   4448   800 pts/0    S+   19:13   0:00 grep --color=auto bluetooth
user:~$ cat /etc/bluetooth/main.conf
[General]

# List of plugins that should not be loaded on bluetoothd startup
#DisablePlugins = network,input

# Default adaper name
# %h - substituted for hostname
# %d - substituted for adapter id
Name = %h-%d

# Default device class. Only the major and minor device class bits are
# considered.
Class = 0x000100

# How long to stay in discoverable mode before going back to non-discoverable
# The value is in seconds. Default is 180, i.e. 3 minutes.
# 0 = disable timer, i.e. stay discoverable forever
DiscoverableTimeout = 0

# How long to stay in pairable mode before going back to non-discoverable
# The value is in seconds. Default is 0.
# 0 = disable timer, i.e. stay pairable forever
PairableTimeout = 0

# Use some other page timeout than the controller default one
# which is 16384 (10 seconds).
PageTimeout = 8192

# Discover scheduler interval used in Adapter.DiscoverDevices
# The value is in seconds. Defaults is 30.
DiscoverSchedulerInterval = 30

# What value should be assumed for the adapter Powered property when
# SetProperty(Powered, ...) hasn't been called yet. Defaults to true
InitiallyPowered = true

# Remember the previously stored Powered state when initializing adapters
RememberPowered = true

# Use vendor, product and version information for DID profile support.
# The values are separated by ":" and VID, PID and version.
#DeviceID = 1234:5678:abcd

# Do reverse service discovery for previously unknown devices that connect to
# us. This option is really only needed for qualification since the BITE tester
# doesn't like us doing reverse SDP for some test cases (though there could in
# theory be other useful purposes for this too). Defaults to true.
ReverseServiceDiscovery = true

# Enable name resolving after inquiry. Set it to 'false' if you don't need
# remote devices name and want shorter discovery cycle. Defaults to 'true'.
NameResolving = true

# Enable runtime persistency of debug link keys. Default is false which
# makes debug link keys valid only for the duration of the connection
# that they were created for.
DebugKeys = false

# Enable Low Energy support if the dongle supports. Default is false.
# Enable/Disable interleave discovery and attribute server over LE.
EnableLE = false

# Enable the GATT Attribute Server. Default is false, because it is only
# useful for testing. Attribute server is not enabled over LE if EnableLE
# is false.
AttributeServer = false

Thanks,

---

### Post by yvsong on 2012-02-24
```
hciconfig
``` shows nothing and ```
hciconfig version
``` shows "Can't get device info: No such device" on my Toshiba Satellite Pro laptop.

---

