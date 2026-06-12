---
title: "Netgear WPN111 connection drops"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by itsjareds on 2009-06-20
Hi, I have a wireless adapter, the Netgear WPN111, that connects to my local network. It has been buggy every step of the way trying to get it to connect. Well, I've finally gotten it connecting, and it works perfectly except for random disconnects. I don't know why, but just out of the blue, my Internet will be cut off.

The wireless card's light is still blinking (meaning it's not off) and I can still scan and see results for nearby networks. However, I can't seem to be able to reconnect to the Internet. The only way I can get the adapter to stop blinking is to physically pull the thing from the USB slot, then re-plug it and re-scan. Does anybody know of a way to turn off the wireless card and turn it back on from the terminal?

I have already tried:

```
rmmod ndiswrapper
modprobe ndiswrapper
```

Then try to reconnect, but no dice.

See [this thread]("http://ubuntuforums.org/showthread.php?p=5670733") for my tutorial on how to connect the WPN111 to a WPA2-secured network.

Thanks for any support.

---

### Post by itsjareds on 2009-06-20
Bump

---

### Post by markthecarp on 2009-06-20
Hi itsjareds,

```

sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

```

Should bring the wireless device down and up. When this happens do other machines on your LAN also lose their connection to the internet?

-mark

---

### Post by itsjareds on 2009-06-21
Nope, my other computer using Windows 7 runs fine -- as does this computer on my other Windows XP partition. My connection very rarely drops out on Windows, but it seems that it disconnects every few hours on Ubuntu.

I'll try those commands.. I was thinking about doing that but I couldn't for the life of me remember what the command was -- and I was offline so I couldn't search it.

I believe the major part of my symptoms is that ndiswrapper is freezing. When I try to run a command from the terminal or open ndisgtk, I get an unresponsive application which I have to force kill. I restarted once when I lost connection and while Ubuntu was in the process of shutting down before the reboot, it got stuck at "Disabling Bluetooth". I don't use Bluetooth and don't predict ever using it in the future. I tried disabling the bluetooth service, but that just made it so I couldn't connect at all. Is bluetooth a more general term for wireless?

---

### Post by itsjareds on 2009-06-21
Ok, my connection crashed again and I got the chance to debug once again. Taking off wlan0 and putting it back up didn't seem to do anything. My wireless driver still blinks and is still able to scan for local networks. Just can't get any Internet connection for whatever reason.

I tried:
```
sudo ifconfig wlan0 down
sudo /etc/init.d/networking stop
sudo /etc/init.d/wicd stop
sudo rmmod ndiswrapper
```

Yet, my adapter keeps blinking. That last line, removing the ndiswrapper module, returns an error that says the resource is busy. Reading further on the rmmod command says that I can force kill a module, but I'd have to boot with that option set in the kernel. I don't think that is the right approach.

---

### Post by aimwin on 2009-06-25
Use WEB 128 bit share key

It stable like a rock.

[http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111](http://ubuntuforums.org/showthread.php?t=844856&highlight=wpn111)

---

### Post by itsjareds on 2009-06-25
Is this another form of security? And do you mean WEP not WEB? I don't have the power to change my local network from WPA2 to anything else and I'm not the only user of the network.

I think I may submit a bug report.

---

### Post by pytheas22 on 2009-06-27
> Is this another form of security? And do you mean WEP not WEB? I don't have the power to change my local network from WPA2 to anything else and I'm not the only user of the network.

I think I may submit a bug report. 

I think the poster indeed meant to say WEP.  As I recall, the WPN111 works fine with WEP, just not with WPA.  On the other hand, WEP is not very secure at all anymore, since it can be cracked in a few minutes using a tool like aircrack.

Some questions:

Have you looked at the dmesg output after your connection crashes?  That may provide a clue as to why it's crashing (although I recall going through all that last summer and not really getting much of a clue).

If you unplug the device physically and plug it back into your computer, can you connect again?  Save your work before unplugging as I suspect this may freeze your machine, but it's worth a try.

Does removing and reinserting the usb_storage module by typing:
```

sudo rmmod usb_storage
sudo modprobe usb_storage
```

help?  I believe this is the module that drives the USB bus, so removing it should cause all USB devices to refresh.  (Also note that usb_storage only applies to Ubuntu 9.04 and later; if you're using an older version of Ubuntu, try removing and reinserting ehci_hcd instead.)

---

### Post by itsjareds on 2009-06-27
First of all, thanks for looking back at my topic. I know it's not too easy to solve and I thank you for your dedication. :D

> **pytheas22 said:**
> Have you looked at the dmesg output after your connection crashes?  That may provide a clue as to why it's crashing (although I recall going through all that last summer and not really getting much of a clue).

Nope, I forgot about that one. I'll run it the next time I lose connection.

> **pytheas22 said:**
> If you unplug the device physically and plug it back into your computer, can you connect again?  Save your work before unplugging as I suspect this may freeze your machine, but it's worth a try.

I've done that and also tried leaving the adapter disconnected and stopping/starting the ndiswrapper module. It stays frozen permanently it seems. If I take out my adapter, nothing works and I end up restarting. While Ubuntu is restarting, it gets stuck during the booting down phase and eventually goes to the non-graphical spot where it's hanging. It gets stuck on "Stopping Bluetooth...". If you know a way to remove Bluetooth permanently that'd be great. This doesn't happen unless I unplug my adapter after it's frozen.

> **pytheas22 said:**
> Does removing and reinserting the usb_storage module by typing:
```

sudo rmmod usb_storage
sudo modprobe usb_storage
```

help?  I believe this is the module that drives the USB bus, so removing it should cause all USB devices to refresh.

Nope, and that intrigues me. Sounds like exactly what I need to virtually unplug my adapter. If it doesn't get me to reconnect, at the very least I might be able to run that on shutdown so I can make my adapter stop blinking.

Thanks, I'll try these commands as soon as I get disconnected.

---

### Post by ratcheer on 2009-06-27
I know this won't be any help, but before I converted my spare machine from Win to Linux, I tested wireless with a WN111 in Win XP. It dropped the connection frequently, too. So I just ended up running an Ethernet cable to the box before I converted it to Linux.

Tim

---

### Post by itsjareds on 2009-06-27
Ah, ok, thanks. It never hurts to confirm that it's not "just me".

---

### Post by itsjareds on 2009-06-27
I just lost connection and did the commands you said. [Here's my terminal output]("http://download203.mediafire.com/tyinmjc9tb8g/zqnkoyznma5/dmesg.txt") for dmesg and rmmod usb_storage.

I didn't read through dmesg, but usb_storage gave me an error that there was no such module. I am running 9.04 Jaunty, so I'm not sure why it's not working.

Unplugging/replugging the device does not crash my computer, but I can't get the adapter blinking again once I replug. I also can't successfully scan for networks as I could when it was blinking but disconnected.

What do you think?

Edit: Ugh, the terminal must have only copied up to so many characters when I selected all. The beginning of the output got cut off. The only command you can't see is dmesg, but part of the output of that is still visible.

Edit2: Running dmesg again when I restarted and can connect, I get the same last lines as I did when I couldn't connect.

Edit3: Shouldn't have that problem with the terminal output getting cut off, changed some preferences to allow more lines.

---

### Post by pytheas22 on 2009-06-28
hmmm, the dmesg.txt file seems to be empty when I try to download it.  Could you check on this and let me know.

As for rmmod usb_storage, it turns out that usb_storage is only used for USB storage devices (surprise), not all USB devices.  So it doesn't affect your USB wireless card.  I'm not sure if there is a separate driver for USB wireless cards in Jaunty and Google doesn't seem to have an answer.  (There were major changes to the USB driver scheme for Jaunty and I still don't understand how it works now.)

It's interesting that you mention the issues with bluetooth, and I'm wondering if that might have to do with the wireless device crashing.  You can disable bluetooth permanently by adding all the bluetooth modules to your /etc/modprobe.d/blacklist.conf file.  You can get a list of all the bluetooth modules by typing:
```

ls /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
```

You can also stop the bluetooth service and tell the system not to auto-start it at boot by typting:
```

sudo /etc/init.d/bluetooth stop
sudo update-rc.d bluetooth remove
```

Also, what happens if, after a crash, you unplug the wireless card, then rmmod ndiswrapper; modprobe ndiswrapper, then plug it back in?

And have you tried to uninstall the Windows driver from ndiswrapper (ndiswrapper -r driver_name) and then reinstall it?  I've seen situations where people report having to do this.

---

### Post by itsjareds on 2009-06-28
> **pytheas22 said:**
> hmmm, the dmesg.txt file seems to be empty when I try to download it.  Could you check on this and let me know.

Yeah, I'm not sure what happened but the first 100 or so lines are blank. If you scroll down a bit you'll see it. Something strange happened.

I disabled bluetooth through sysv-rc-conf. I'll have to see if that stops the freezing on shutdown. I did lose connection once after I disabled bluetooth and restarted, though.

> **pytheas22 said:**
> Also, what happens if, after a crash, you unplug the wireless card, then rmmod ndiswrapper; modprobe ndiswrapper, then plug it back in?

I still get no response after I type either of those commands in. Seems like it's frozen.

> **pytheas22 said:**
> And have you tried to uninstall the Windows driver from ndiswrapper (ndiswrapper -r driver_name) and then reinstall it?  I've seen situations where people report having to do this.

Yeah, that was the first thing I tried last summer. Typing anything that deals with my already installed driver seems to be unresponsive in the terminal. And opening ndisgtk also freezes.

==

I ran those commands to disable bluetooth already because I don't have to be disconnected. Here's my output:
```
jared@jared-desktop:~$ ls /lib/modules/$(uname -r)/kernel/drivers/bluetooth/
bcm203x.ko  bluecard_cs.ko  bt3c_cs.ko  btuart_cs.ko  dtl1_cs.ko   hci_vhci.ko
bfusb.ko    bpa10x.ko       btsdio.ko   btusb.ko      hci_uart.ko
jared@jared-desktop:~$ sudo /etc/init.d/bluetooth stop
 * Stopping bluetooth                                                    [ OK ] 
jared@jared-desktop:~$ sudo update-rc.d bluetooth remove
update-rc.d: /etc/init.d/bluetooth exists during rc.d purge (use -f to force)

```

I'm not sure if the last line about rc.d purge means that the module didn't get removed, or if it's just a warning.

==

Edit: I just disconnected, ran those rmmod ndiswrapper; modprobe ndiswrapper and the terminal got nothing as usual. I blacklisted all of the bluetooth modules in /etc/modprobe.d/blacklist.conf, disabled bluetooth in sysv-rc-conf, and disabled bluetooth through sudo update-rc.d -f bluetooth remove. I already had bluetooth disabled in sysv-rc-conf, and unplugging the adapter and restarting seemed to not hang on "Stopping bluetooth...". That's one problem fixed.

---

### Post by deankovell on 2009-06-28
"When I try to run a command from the terminal or open ndisgtk, I get an unresponsive application which I have to force kill. I restarted once when I lost connection and while Ubuntu was in the process of shutting down before the reboot, it got stuck at "Disabling Bluetooth"."

I'm not sure if this is even relevant, but I tried installing my wpn111 on jaunty from the instructions on one of your other threads, and the same thing happened to me. however, after I shut it down I rebooted into windows. The weird thing was that the adapter was still blinking the whole time I was booting into windows. *it doesn't normally do that *until vista's up and running. also I still had to physically remove it and plug it in while in vista to get it to work.  

anyway, Thanks to everybody who's trying to figure this out.

---

### Post by itsjareds on 2009-06-28
I've had the same issue. It's definitely relevant, for some reason Ubuntu is not turning the adapter off. My solution for the longest time was to just unplug after my computer restarted, and before Ubuntu or Windows tried to start up the adapter. I found out recently that I could also shut down the computer instead of restart, and the adapter stops blinking. It's easier to press the computer's On button than to unplug/replug the adapter.

Windows seems to turn off the adapter fine when it's shutting down or restarting. Ubuntu doesn't turn it off, then whenever you boot into either Windows or Ubuntu, the systems seem to notice it's busy. That's what I was hoping removing the usb_storage module would fix.

Do you need to have Bluetooth enabled? If not, do what Pytheas posted above and disable all of your Bluetooth modules. That way Ubuntu won't even start it on boot -- so there's nothing to get stuck on while you're shutting down.

---

### Post by itsjareds on 2009-06-29
Now that I've used Ubuntu quite a bit more, I'm starting to notice a trend. It seems that most of the time, my adapter will freeze while I'm downloading continuously for things such as installing software. It's annoying but thankfully Ubuntu keeps temporary files and continues where it left off.

But my adapter also freezes if I leave the computer alone for a while -- maybe an hour. Maybe it's because the adapter is working too hard? This confuses me because it works fine with WEP.

---

### Post by deankovell on 2009-06-29
try pointing a fan at it. mine does the same thing in vista with large downloads or  after about 45 minutes of streaming fairly high quality video. the adapter always seems to be pretty hot when I disconnect/reconnect it.

---

### Post by itsjareds on 2009-06-29
The thing is, mine *doesn't* do that in Windows XP or Windows 7. Not sure where I'll get or place the fan.. I don't have that much desk real estate.

---

### Post by carcar1 on 2009-06-29
This little usb dongle is poorly made.  All there is to say, its a physical problem, I had mine for like 1 week with no problems in xp then it started freaking out when I went to download things.  Netgear does not make solid card, try encore.

---

### Post by itsjareds on 2009-06-29
> **carcar1 said:**
> This little usb dongle is poorly made.  All there is to say, its a physical problem, I had mine for like 1 week with no problems in xp then it started freaking out when I went to download things.  Netgear does not make solid card, try encore.

How could it be physical if it's working fine in XP? Sounds like a software issue to me. I don't have any money to buy a wireless adapter - my parents give me what works and I have to make use of it.

And as far as how my connection is doing now: It hasn't disconnected for a good 6 hours, even when I left the computer for two 2-hour periods.

---

### Post by itsjareds on 2009-07-01
Bump

---

### Post by john1911 on 2009-07-03
I have same problems like u. On XP works fine, no dropout, never crash, never freeze. But on ubuntu difrent story, it's work all the time but when i start download something it's always goes off and I need to restart-unplugged-pluged and than works again.

---

### Post by itsjareds on 2009-07-12
Thanks for that info. I think I will submit this as a bug report on Launchpad because [so many people]("https://answers.launchpad.net/ubuntu/+source/ndiswrapper/+question/67884") are having this issue, even aside from this thread. Should I do it? I think it is bug-worthy but I'm not sure of how important the bug must be before I submit it.

edit: I believe the connection problem IS activity related. My connection goes out almost every time I try to stream a Youtube video, or a while after streaming music from Grooveshark.

edit2: I just suicide tested my connection by running 7 youtube videos, one HD video (House MD) and then streamed some music. Connection went fine during the test, but I don't think I did it long enough. A few minutes after the test, the connection went out.

---

### Post by itsjareds on 2009-07-14
I actually have kept up a fairly stable connection by not keeping prolonged downloads or streams. Only viewing regular HTML pages and downloading small files here and there, and I haven't had any disconnects.

It kind of ruins the experience though, being limited to half of the Internet..

---

### Post by itsjareds on 2009-07-14
I found out how to reconnect!! :guitar:

I compiled ndiswrapper 1.55 from the source with a few debug parameters. Since I've used v1.55, I have been able to run the command ndiswrapper -l even when my connection has dropped. This is important, ndiswrapper does not freeze anymore when the connection drops. The issue must lie somewhere else other than "ndiswrapper freezes". I was able to reconnect after reinstalling the driver through:

```
sudo ndiswrapper -r netwpn11
(unplug WPN111 from USB port)
sudo ndiswrapper -i <inf file>
(plug WPN111 back into USB port)
```

After this, I was able to reconnect through Wicd and I pinged google.com and received feedback! This makes me happy, we're finally seeing some progress. :p In a few minutes I'll write up a script to run to reconnect. I hope this can be enabled automatically upon disconnect.

Of course, I might be getting too excited. Maybe something else happened this time. Thanks for all the support through this forum that I've gotten, and hopefully we will be able to find a complete fix instead of a workaround.

---

### Post by itsjareds on 2009-07-16
So far it has been successful after a second disconnect.

I attached a shell script to run after you disconnect, it should get you back and up after a little while (the actual connection might take a minute to reconnect, but it'll do it).

---

### Post by itsjareds on 2009-07-19
That last workaround only works after the first time.


I've also discovered something else. Windows will drop the connection exactly the same if you use Windows Wireless Zero Configuration connection service, then while you are connected, end the WPN111.exe process (the Netgear software). You will stay connected to the Internet, but my connection eventually dropped and I could not reconnect. I ended up having to unplug my adapter, start the WPN111.exe program, then plug in my adapter and reconnect.

I think the answer lies in the Netgear software. Netgear users have complained about dropouts in Windows for a long time, then Netgear released version 2.0 of their software. This probably holds the fix for our trouble, the only problem is finding it :(

If anybody would like to help or has experience with hacking Windows executables.. post here :)

---

### Post by pytheas22 on 2009-07-19
It's interesting that you mention the drop outs in Windows.  ndiswrapper could well be experiencing the same problem, since it's essentially just a wrapper around the same WPN111.exe process that you have in Windows.

Do you have a .exe file for version 2.0 of the software and are looking for a way to get the .inf and .sys files out?  Or are you unable to find the version 2.0 driver anywhere?

---

### Post by itsjareds on 2009-07-19
Nope, I have the 2.0 software installed on Windows, and luckily Netgear provides a separate "Driver" folder inside their Program Files that contains the .inf file. I just copied this folder over and installed it into ndiswrapper. I have the 2.0 driver and it's fine, but my thought is that the WPN111.exe software (this includes a GUI for connecting) does something to keep the connection alive when it usually would go out on Linux. I can also get the driver from installing the software through WINE.

I tested my adapter by installing my adapter's software through Windows's Wireless Zero Configuration service. It lets you connect wirelessly without having to configure many things, and the alternate option was to use Netgear's software -- WPN111.exe. Connecting through Zero Configuration worked fine, and then I checked the task manager and WPN111.exe was running. I ended this process and I was still connected, so I didn't think anything of it. I kept it stopped and maybe 10 hours later, I disconnected and could not reconnect, almost exactly the same way as in Ubuntu.

I had to unplug my adapter, run WPN111.exe, then replug my adapter to reconnect.

---

### Post by pytheas22 on 2009-07-22
That's very interesting.  Unfortunately, I doubt there's a way to figure out how Netgear's configuration manager manages the WPN111.exe process.  But what you might try doing is writing a script to periodically reinstall the driver in ndiswrapper automatically, which would hopefully keep it from crashing.  You could probably figure out a way to have the script run only when your computer is idle so that it wouldn't affect your work flow.  So you would write a script that looks like this:
```

#!/bin/bash

...test to figure out if system is idle...

ifconfig wlan0 down
modprobe -r ndiswrapper
ndiswrapper -r wpn111
ndiswrapper -i wpn111
modprobe ndiswrapper
ifconfig wlan0 up
```

and run it as a cron job.

I'm not sure exactly how to determine measure whether the computer is idle, but there are various approaches discussed on [this page]("http://stackoverflow.com/questions/622367/scheduling-in-linux-run-a-task-when-computer-is-idle-no-user-input").  I'm sure there are other ways to do it as well if you do a more extensive Google search.

---

### Post by itsjareds on 2009-07-23
Ok, thanks, I configured my script to run whenever my screensaver appears. Here's my Perl script ([ripped from here]("http://ubuntuforums.org/showthread.php?p=6197571#post6197571")):

idle.pl (Run on startup, waits in background for screensaver)
```
#!/usr/bin/perl
my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='SessionIdleChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
	if (m/^\s+boolean true/) {
		system("gnome-terminal -e \"/home/jared/Desktop/network.sh\"");
	}
}
```

network.sh
```
#!/bin/bash
echo " - Putting wireless interface down"
sudo ifconfig wlan0 down
echo " - Removing ndiswrapper module"
sudo modprobe -r ndiswrapper
echo " - Uninstalling driver for ndiswrapper"
sudo ndiswrapper -r netwpn11
read -p " - Unplug adapter then press enter..."
echo " - Installing driver for ndiswrapper"
sudo ndiswrapper -i "/media/winxp/Program Files/NETGEAR/WPN111/Driver/netwpn11.inf"
read -p " - Replug adapter..."
echo " - Adding ndiswrapper module"
sudo modprobe ndiswrapper
echo " - Putting wireless interface up"
sudo ifconfig wlan0 up
echo " - Done. You may close the window."
```

My only problem now is that I need to run most of those commands as a superuser, and I won't be there to type in my password when the script runs.

Any ideas?

---

### Post by itsjareds on 2009-07-23
At the very least, your script helped my script in that it will work EVERY time, not just after the first disconnect. Now I don't have to restart at all :D, and can keep connected for the most part. I think I'd rather have my script run every hour or so. This is a job for cron, right? I'll still have the same problem with needing to type in my password for sudo, though.

I don't mind the disconnects too much, it's a fair trade-off to use Ubuntu instead of Windows. It would be nice to solve this thing, though.

---

### Post by itsjareds on 2009-07-23
Argh.. didn't work again after keeping it up with the script for about 15 hours. The only problem is that the ndiswrapper driver is busy. I'll check the module for dependencies next time it happens with lsmod | grep ndiswrapper. Usually it shows with "0" (this means none, right?). If I can't stop any dependencies, then I'm thinking about compiling a kernel with CONFIG_MODULE_FORCE_UNLOAD set.

---

### Post by itsjareds on 2009-07-23
This is frustrating. My dad changed the network to unsecured for a while (I guess he's doing something to it..), and I still get the dropouts! My brother's computer's connection is fine while I've lost connection. The exact same thing happens with the dropout. I did a restart also and still got the dropout.

I guess I'll have to take a look at some of those WPN111 tutorials again..

edit: I think I may have been wrong about the WPN111.exe process, I tried testing it a few more times and I could just unplug/replug the second time it happened. Hadn't happened after that for about 2 days.

---

### Post by pytheas22 on 2009-07-23
Sorry to hear that things aren't going as well as you originally expected.

As for running the script with superuser privileges, all you have to do is tell cron to run it as root.  In other words, edit the file /etc/crontab, add a line for your script and make sure the user for running it is root.  This way you won't need to be there to type in your password.

But I guess this isn't actually a solution after all?  It's strange that the connection drops even with security disabled.  Did this used to be the case?  I thought we determined last summer that things were fine with no security or with WEP; it was just WPA that was the problem.

---

### Post by itsjareds on 2009-07-23
Yeah it's confused me too. My dad's messing with the connection now and he changed it back to WPA2. I'm not sure if it's relevant because I didn't get enough time to test it, but I tried connecting to the unsecured network through the atmel driver instead of wext, and for an hour or two I didn't reach a dropout, but I honestly didn't get enough time to test it.

Anyways, I compiled another kernel that allows CONFIG_FORCE_MODULE_UNLOAD, so hopefully if ndiswrapper hangs again, I can force unload it and modprobe it again.

---

### Post by Black_Wolf_92 on 2009-07-24
just confirming the same problem. I posted a few threads about this about 6 months ago, while on intrepid, and recieved no solution. Works fine on Windows. Eventually I just picked up a cheap built in card, and its working fine. Not sure if there will ever be a solution to this problem, which is a shame, because in the brief period before the disconnection, I used to get pretty crazy speeds...

---

### Post by frozen.toast on 2009-08-08
Hey just created an account to say thanks to itsjareds for the reconnecting script. I've just started using Ubuntu in the last few weeks and this is the only problem I'm having although my connection drops out exactly the same as yours and I use a WEP key. Anyway I was wondering If someone could help me edit itsjareds script so it runs every hour or so.

---

### Post by pytheas22 on 2009-08-09
frozen.toast: you can write a cron job to make the script run every hour.  You can find instructions on how to write a cron job [here]("https://help.ubuntu.com/community/CronHowto").  Please give that a try.  If you have trouble understanding how to write a cron job, or it doesn't seem to work after you've written it, let us know.

---

### Post by itsjareds on 2009-08-18
Thanks for replying frozen.toast. I haven't heard of the problem in WEP connections but I suppose anything's possible (a faulty shipment of devices?). I had the same issues even on an unsecured connection, albeit a very short testing period (3 hours). My suggestion is the same; try making a cron job. I preferred the screensaver script so that I didn't get disconnected all the time.

I'm also reposting to give an update on the CONFIG_MODULE_FORCE_UNLOAD enabled kernel: no luck. Didn't get an error about the option not being unabled, but the task just hung when I entered rmmod into the terminal.

---

