---
title: "Trendnet TEW 644-UB"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by L0VEL1NUX on 2009-01-11
I've been trying to get my Trendnet 644-UB adapter working on my x64 desktop. I've installed ndiswrapper and used the WinXP x64 drivers that were on the CD. The adapter is listed as present in the Wireless Network Drivers. But when I enter the WPA Encryption key, it searches for about 1 minute then says the adapter is disconnected. The key I entered is correct because it's working on my XP laptop. I would appreciate any help.

---

### Post by Smith.. on 2010-04-10
I came across your post and thought I'd shoot a reply. I have the exact same make and model adapter your talking about. The TEW-644UB. I was able to goto here:

```
http://www.ralinktech.com/support.php?s=2
```And I found the linux version of the drivers. Ok so what did I get off that list?

```
 [RT2870USB(RT2870/RT2770)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1EQTVMekV5THpFMUwyUnZkMjVzYjJGa05UYzBNVFExTkRNNU5TNWllakk5UFQxU1ZESTROekJmVEdsdWRYaFRWRUZmVmpJdU15NHdMakF1ZEdGeUxuUmhjZz09Qw%3D%3D") 
```Once you download the package. You extract it somewhere. I choose my home folder. Then open a terminal and type this in. 

```

cd "name of the folder"
make 
sudo make install 

```So what that did for me was compile the source code driver. From what I understand. I'm fairly new to all this myself as well. And it installs. If you get a permission error you can type sudo make install and it'll give you root permissions. 

After that I plug the deal in and it still doesn't work right. So I'm at my terminal again and I type in: 

```
sudo modprobe rt2870sta
```That command works cause there's no error message after it. So I got the driver down. I've told the ubuntu load this module/driver for it. What next? Bring up the device like this:

```
sudo ifconfig ra0 up
```Ok awesome the device starts blinking now. Why can't I still use this deal? After searching around here. I lost the page where it had the guide. But this is what I found out. Because I'm posting here on these forums using a wireless G adapter. That there are two modules/drivers working at the same time. I'm looking at them now and they're both blinking crazy like. If the make commands don't work out there. Then you'll need to get the packages to compile source code. 

```

https://help.ubuntu.com/community/CompilingEasyHowTo

```Oh in order to get the drivers to stop battling it out on your pc. You need to blacklist the older ones. 

```
sudo gedit /etc/modprobe.d/blacklist.conf 
```The ones I had to blacklist were:

```
rt2x00usb
rt2x00lib
```I found out those were the ones by doing these commands: 

```
sudo modprobe rt2x00usb
sudo modprobe rt2x00lib 
```They loaded and since I'm here typing this out. I'm thinking these are the ones. I tried:

```
sudo modprobe -r rt2x00lib 
```After reading the pages here:

```
man modprobe 
```I couldn't remove the modules cause it said they were already in use. I think if I reboot this though it'll do it. Cause I blacklisted the ones above. All this time though I've been doing the upgrade though so I may have to do this over again. I hope this helps someone out. 

I subscribed to this thread and I'll get an email if you post something here. Let me know.

---

### Post by WindowsIsBad on 2010-05-06
Hey, Seems like you went through lots of hoops to get to this point. I could not tell if you actually got it to work at the end. 

I have the TEW-644UB wireless N adapter as well and having a hard time getting it to work.

I installed the windows wirless drivers package and chose the .INF file for the windowsXP version. It says the hardware is present, but I dont see it at the tray on the top...

If you got it to work, your solution would be great!

---

### Post by Smith.. on 2010-05-06
> **WindowsIsBad said:**
> Hey, Seems like you went through lots of hoops to get to this point. I could not tell if you actually got it to work at the end. 

I have the TEW-644UB wireless N adapter as well and having a hard time getting it to work.

I installed the windows wirless drivers package and chose the .INF file for the windowsXP version. It says the hardware is present, but I dont see it at the tray on the top...

If you got it to work, your solution would be great!

To this day I'm still having issues with it. I've installed all the drivers I can. I can check out what drivers are currently loaded or "live" by using this command:

```
less proc/modules
```If I check that out on my pc I'll see other drivers on there that are wifi related. I have two adapters. Thankfully one of them worked right off. THANK YOU UBUNTU DEVELOPERS! As for the this new better adapter. I'm guessing this one is still back on the drawing board. But anyways, back with my discovery. The modules listed by the above command are what's loaded. To exit the list press q to quit. 

You can blacklist or prevent them from even loading to begin with. By using this command. 
```

sudo gedit /etc/modprobe.d/blacklist.conf
```Here is an example of what I got on the bottom of mine. 

```
# Custom blacklist by the Smyth~
blacklist snd_hda_intel
blacklist rt2870sta
```The snd_hda_intel is blacklisted because I've had issues with sound and I didn't want to mess with pulseaudio anymore. You talk about hoops that's like it's own circus there man. The other one is the driver that I installed earlier. It doesn't seem to work to well. I can find networks with this. But I can not login. 

I've installed the other driver for windows xp 64 as well. By first installing ndiswrapper like so: 

```
sudo apt-get install ndiswrapper-utils-1.9
```Then once installed what you do is you take your drivers off the cd that came with it. I placed mine here:

```
/home/smyth/Documents/Backup/WinXP64
```Then what you do is you install the driver using the inf file you got. Keep in mind you need all three files in that folder. If your using a 32 bit os don't use the 64bit drivers. When your ready to install point ndiswrapper to the driver package: 

```
sudo ndiswrapper -i /home/smith/Documents/Backup/WinXP64/rt2870.inf
```To verify that you have the driver loaded. Try: 

```
ndiswrapper -l 
```You should see this: 

```
smyth@ubuntu:~$ ndiswrapper -l 
rt2870 : driver installed
    device (148F:2770) present (alternate driver: rt2800usb)
smyth@ubuntu:~$ 

```Hope this helps. Let me know.

---

### Post by WindowsIsBad on 2010-05-07
Thanks for the reply Smith, 

I can get to this point:

rt2870 : driver installed
    device (148F:2770) present (alternate driver: rt2800usb)

But thats it. When I run dmesg | grep -e ndis -e wlan

I get:

[   13.444702] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.117924] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   14.118503] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   14.119690] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   14.120277] usbcore: registered new interface driver ndiswrapper

And I have been stuck from here...

---

### Post by Smith.. on 2010-05-07
> **WindowsIsBad said:**
> Thanks for the reply Smith, 

I can get to this point:

rt2870 : driver installed
    device (148F:2770) present (alternate driver: rt2800usb)

But thats it. When I run dmesg | grep -e ndis -e wlan

I get:

```
[   13.444702] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   14.117924] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   14.118503] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   14.119690] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   14.120277] usbcore: registered new interface driver ndiswrapper

And I have been stuck from here...
```

hmmm, 

When I do the same command I get this as my output:
```

[29169.488825] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29169.490558] wlan1: authenticated
[29169.490580] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29169.493200] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29169.493203] wlan1: associated
[29173.648493] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29175.254441] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29175.257989] wlan1: direct probe responded
[29175.257997] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29175.261197] wlan1: authenticated
[29175.261226] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29175.273222] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29175.273227] wlan1: associated
[29179.281198] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29180.947264] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29180.950846] wlan1: direct probe responded
[29180.950853] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29180.952689] wlan1: authenticated
[29180.952712] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29180.955312] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29180.955315] wlan1: associated
[29185.015457] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29186.719659] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29186.727234] wlan1: direct probe responded
[29186.727242] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29186.729471] wlan1: authenticated
[29186.729500] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29186.729517] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29186.729517] wlan1: associated
[29190.750470] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29192.436862] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29192.439846] wlan1: direct probe responded
[29192.439849] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29192.441569] wlan1: authenticated
[29192.441595] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29192.444206] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29192.444210] wlan1: associated
[29196.484448] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29198.116065] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29198.315371] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[29198.512535] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[29198.517845] wlan1: direct probe responded
[29198.517851] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29198.519720] wlan1: authenticated
[29198.519747] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29198.522227] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29198.522232] wlan1: associated
[29202.526485] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29204.194320] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29204.197874] wlan1: direct probe responded
[29204.197881] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29204.203334] wlan1: authenticated
[29204.203361] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29204.206707] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29204.206711] wlan1: associated
[29208.269889] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29209.894829] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29209.898500] wlan1: direct probe responded
[29209.898508] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29209.901113] wlan1: authenticated
[29209.901147] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29209.903860] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29209.903866] wlan1: associated
[29213.895885] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29215.593859] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29215.596983] wlan1: direct probe responded
[29215.596990] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29215.600850] wlan1: authenticated
[29215.600877] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29215.603462] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29215.603466] wlan1: associated
[29219.628462] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29221.356270] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29221.360473] wlan1: direct probe responded
[29221.360480] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29221.365956] wlan1: authenticated
[29221.365981] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29221.369921] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29221.369927] wlan1: associated
[29225.362485] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[29226.987329] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[29227.182561] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[29227.187868] wlan1: direct probe responded
[29227.187875] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[29227.189857] wlan1: authenticated
[29227.189889] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[29227.192490] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=1)
[29227.192529] wlan1: associated
[29229.012556] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32856.142936] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32856.384311] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32856.393474] wlan1: direct probe responded
[32856.393481] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32856.395211] wlan1: authenticated
[32856.395242] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32856.400691] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32856.400696] wlan1: associated
[32860.420945] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32862.204431] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32862.402630] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32862.409353] wlan1: direct probe responded
[32862.409370] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32862.411085] wlan1: authenticated
[32862.411116] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32862.415970] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32862.415976] wlan1: associated
[32866.462955] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32868.224557] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32868.228340] wlan1: direct probe responded
[32868.228348] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32868.230075] wlan1: authenticated
[32868.230101] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32868.233082] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32868.233086] wlan1: associated
[32872.305371] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32873.987100] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32874.182566] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32874.382559] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[32874.389343] wlan1: direct probe responded
[32874.389349] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32874.391200] wlan1: authenticated
[32874.391229] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32874.393726] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32874.393731] wlan1: associated
[32878.444086] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32880.173326] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32880.177204] wlan1: direct probe responded
[32880.177209] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32880.178945] wlan1: authenticated
[32880.178969] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32880.183244] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32880.183249] wlan1: associated
[32884.179020] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32885.884317] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32885.887361] wlan1: direct probe responded
[32885.887369] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32885.889148] wlan1: authenticated
[32885.889179] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32885.896975] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32885.896980] wlan1: associated
[32889.914955] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32891.526853] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32891.722542] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32891.922550] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[32892.124794] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 timed out
[32903.014328] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32903.019838] wlan1: direct probe responded
[32903.019846] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32903.022349] wlan1: authenticated
[32903.022383] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32903.024981] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32903.024986] wlan1: associated
[32907.014987] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32908.715850] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32908.912537] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32908.918367] wlan1: direct probe responded
[32908.918374] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32908.920465] wlan1: authenticated
[32908.920493] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32908.923742] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32908.923747] wlan1: associated
[32912.890132] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32914.537715] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32914.541365] wlan1: direct probe responded
[32914.541372] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32914.543120] wlan1: authenticated
[32914.543149] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32914.548377] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32914.548381] wlan1: associated
[32914.992656] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32915.202916] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32915.434344] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32915.441367] wlan1: direct probe responded
[32915.441375] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32915.443110] wlan1: authenticated
[32915.443143] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32915.447029] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32915.447034] wlan1: associated
[32919.507969] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32921.228834] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32921.232376] wlan1: direct probe responded
[32921.232380] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32921.234096] wlan1: authenticated
[32921.234121] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32921.236846] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32921.236849] wlan1: associated
[32925.242964] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32926.907339] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32926.910374] wlan1: direct probe responded
[32926.910381] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32926.912241] wlan1: authenticated
[32926.912273] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32926.917879] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32926.917885] wlan1: associated
[32930.977017] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32932.634337] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32932.832611] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32933.032537] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[32933.038937] wlan1: direct probe responded
[32933.038944] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32933.040601] wlan1: authenticated
[32933.040626] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32933.043218] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32933.043221] wlan1: associated
[32937.018967] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32938.685194] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32938.688351] wlan1: direct probe responded
[32938.688357] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32938.690720] wlan1: authenticated
[32938.690746] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32938.693373] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32938.693379] wlan1: associated
[32942.761015] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32944.419141] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32944.422378] wlan1: direct probe responded
[32944.422385] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32944.424221] wlan1: authenticated
[32944.424246] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32944.426717] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32944.426720] wlan1: associated
[32948.489011] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32950.131853] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32950.135354] wlan1: direct probe responded
[32950.135359] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32950.137228] wlan1: authenticated
[32950.137253] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32950.141863] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32950.141867] wlan1: associated
[32954.120996] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32955.804972] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32955.808365] wlan1: direct probe responded
[32955.808373] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32955.810731] wlan1: authenticated
[32955.810759] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32955.813258] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32955.813263] wlan1: associated
[32959.958255] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32961.608122] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32961.611377] wlan1: direct probe responded
[32961.611383] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32961.613104] wlan1: authenticated
[32961.613129] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32961.615743] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32961.615748] wlan1: associated
[32965.589982] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32967.250949] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32967.452544] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32967.457369] wlan1: direct probe responded
[32967.457373] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32967.459350] wlan1: authenticated
[32967.459370] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32967.461978] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32967.461981] wlan1: associated
[32971.529976] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32973.195600] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32973.392559] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32973.592534] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[32973.597416] wlan1: direct probe responded
[32973.597419] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32973.599268] wlan1: authenticated
[32973.599300] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32973.602892] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32973.602897] wlan1: associated
[32975.002560] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32975.232945] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[32975.474361] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32975.479363] wlan1: direct probe responded
[32975.479367] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32975.481108] wlan1: authenticated
[32975.481128] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32975.484124] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32975.484128] wlan1: associated
[32979.517010] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32981.179721] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32981.183468] wlan1: direct probe responded
[32981.183475] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32981.185155] wlan1: authenticated
[32981.185188] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32981.187752] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32981.187757] wlan1: associated
[32985.251991] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32986.865356] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32986.868400] wlan1: direct probe responded
[32986.868408] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32986.870613] wlan1: authenticated
[32986.870649] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32986.873145] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32986.873149] wlan1: associated
[32990.884035] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32992.537857] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32992.732531] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32992.737362] wlan1: direct probe responded
[32992.737366] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32992.739105] wlan1: authenticated
[32992.739126] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32992.743100] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32992.743105] wlan1: associated
[32996.721531] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[32998.376447] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[32998.572551] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[32998.577420] wlan1: direct probe responded
[32998.577428] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[32998.579117] wlan1: authenticated
[32998.579139] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[32998.582876] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[32998.582879] wlan1: associated
[33002.558028] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33004.216307] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33004.219402] wlan1: direct probe responded
[33004.219409] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33004.221979] wlan1: authenticated
[33004.222001] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33004.224662] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33004.224667] wlan1: associated
[33008.293274] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33009.995553] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33009.998656] wlan1: direct probe responded
[33009.998663] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33010.000265] wlan1: authenticated
[33010.000292] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33010.005162] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33010.005168] wlan1: associated
[33014.028010] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33015.734621] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33015.932542] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[33015.937420] wlan1: direct probe responded
[33015.937427] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33015.939454] wlan1: authenticated
[33015.939493] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33015.942029] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33015.942033] wlan1: associated
[33019.967031] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33021.606140] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33021.609665] wlan1: direct probe responded
[33021.609674] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33021.612727] wlan1: authenticated
[33021.612778] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33021.615251] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33021.615254] wlan1: associated
[33025.599031] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33027.245000] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33027.248410] wlan1: direct probe responded
[33027.248418] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33027.250767] wlan1: authenticated
[33027.250819] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33027.263155] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33027.263160] wlan1: associated
[33031.232512] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33032.951493] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33033.152560] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[33033.360046] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 3)
[33033.365408] wlan1: direct probe responded
[33033.365415] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33033.369878] wlan1: authenticated
[33033.369900] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33033.372537] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33033.372540] wlan1: associated
[33034.992591] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[33035.242838] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
[33035.484892] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33035.489388] wlan1: direct probe responded
[33035.489393] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33035.491126] wlan1: authenticated
[33035.491147] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33035.493779] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33035.493784] wlan1: associated
[33039.526071] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33041.154134] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33041.157420] wlan1: direct probe responded
[33041.157427] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33041.161886] wlan1: authenticated
[33041.161915] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33041.165155] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33041.165160] wlan1: associated
[33045.159033] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33046.802537] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33047.002549] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[33047.007432] wlan1: direct probe responded
[33047.007439] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33047.009287] wlan1: authenticated
[33047.009318] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33047.011849] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33047.011854] wlan1: associated
[33050.996228] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33052.658924] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33052.860042] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 2)
[33052.865430] wlan1: direct probe responded
[33052.865438] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33052.867172] wlan1: authenticated
[33052.867208] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33052.870796] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33052.870801] wlan1: associated
[33056.938129] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33058.605013] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33058.608430] wlan1: direct probe responded
[33058.608438] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33058.610213] wlan1: authenticated
[33058.610243] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33058.612807] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33058.612812] wlan1: associated
[33062.670555] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33064.306148] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33064.309413] wlan1: direct probe responded
[33064.309420] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33064.311179] wlan1: authenticated
[33064.311214] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33064.315052] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33064.315057] wlan1: associated
[33068.302592] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33069.955018] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33069.958430] wlan1: direct probe responded
[33069.958437] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33069.960168] wlan1: authenticated
[33069.960200] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33069.962802] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33069.962807] wlan1: associated
[33073.936387] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33075.594395] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33075.597440] wlan1: direct probe responded
[33075.597447] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33075.599268] wlan1: authenticated
[33075.599290] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33075.602934] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33075.602940] wlan1: associated
[33079.670049] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33081.356549] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33081.359424] wlan1: direct probe responded
[33081.359431] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33081.361145] wlan1: authenticated
[33081.361167] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33081.363812] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33081.363815] wlan1: associated
[33085.404039] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33087.016904] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33087.020433] wlan1: direct probe responded
[33087.020440] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33087.022150] wlan1: authenticated
[33087.022172] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33087.026042] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33087.026047] wlan1: associated
[33091.036052] wlan1: deauthenticated from 00:1e:2a:5a:a6:26 (Reason: 15)
[33092.677688] wlan1: direct probe to AP 00:1e:2a:5a:a6:26 (try 1)
[33092.681421] wlan1: direct probe responded
[33092.681428] wlan1: authenticate with AP 00:1e:2a:5a:a6:26 (try 1)
[33092.683157] wlan1: authenticated
[33092.683180] wlan1: associate with AP 00:1e:2a:5a:a6:26 (try 1)
[33092.685780] wlan1: RX AssocResp from 00:1e:2a:5a:a6:26 (capab=0x411 status=0 aid=2)
[33092.685783] wlan1: associated
[33095.002578] wlan1: deauthenticating from 00:1e:2a:5a:a6:26 by local choice (reason=3)
```I have no idea why it's not making the connection there. I imagine it has something to do with reason 15. What is reason 15 exactly? I have no idea. 

When I type in this command: 

```
ifconfig
```I can confirm that both my wifi adapters are running. That one works and allows me to reply here. That the other don't and it's name being wlan1. I hope someone can figure this one out. Would be nice to pull of dual wifi connections.

---

### Post by espressobeanie on 2010-08-08
Try:  "sudo apt-get install linux-backports-modules-wireless-lucid-generic"        Works for me and I can use aircrack-ng.    [http://ubuntuforums.org/showthread.php?t=1483410](http://ubuntuforums.org/showthread.php?t=1483410)

---

### Post by moe458 on 2010-10-19
I can't get this thing to work for everything that I have tried.
I tried with wicd and it's unable to get it to pickup IP. ( I can see the adapter in wicd.)
[[IMG]http://img821.imageshack.us/img821/8865/wicd.png[/IMG]](http://img821.imageshack.us/i/wicd.png/)

I can bring the wlan0 down and bring it up but unable to make a connect.  Would love to know what's the problem with it..


```
moe@ubuntu:~$ lsmod | grep rt
rt2870sta             525366  1 
rt2x00usb              11260  0 
rt2x00lib              32133  1 rt2x00usb
led_class               3764  1 rt2x00lib
mac80211              238864  2 rt2x00usb,rt2x00lib
cfg80211              148725  2 rt2x00lib,mac80211
parport_pc             29958  1 
parport                37160  3 ppdev,parport_pc,lp

```

```
moe@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:11:3c:16:c1  
          inet addr:192.168.1.147  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:xx5c:xxc1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3231730 (3.2 MB)  TX bytes:599637 (599.6 KB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33081 (33.0 KB)  TX bytes:33081 (33.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:14:d1:5c:39:fe  
          inet6 addr: fe80::214:d1ff:fe5c:39fe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:917740 (917.7 KB)  TX bytes:86360 (86.3 KB)

moe@ubuntu:~$ 

```

---

