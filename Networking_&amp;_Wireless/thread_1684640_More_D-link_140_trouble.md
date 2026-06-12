---
title: "More D-link 140 trouble"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by Dry Lips on 2011-02-09
[FONT=Times New Roman, serif][SIZE=3]Hey everyone![/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]I'm an *absolute* newbie when it comes to Ubuntu, I have never used it before, and installed it last week. However, I have troubles with setting up my wireless antenna: (D-Link System DWA-140 RangeBooster N Adapter (rev.B1) [Ralink RT2870]). While it works perfectly in windows (I run a dual boot system) the internet connection would disconnect itself after a few minutes. [/SIZE][/FONT] 
 [FONT=Times New Roman, serif][SIZE=3]So I decided to install a new driver. I've tried to follow the instructions in: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]- I've blacklisted: [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]bcm43xx[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3], [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]b43[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3], [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]b43legacy, and rt2870sta , rt2800usb, rt2800lib, rt2x00usb[/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]- [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]I've installed [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]ndiswrapper/ndisgtk and the windows driver for XP (32).[/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3]- Windows wireless drivers (ndisgt) says «hardware present».[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Now, this took a rookie like me an entire day, and still there's no network connection.[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]I typed <nm-tool> in the terminal window, and got this output:[/SIZE][/FONT]
 

 *[I][FONT=Times New Roman, serif][SIZE=3]NetworkManager Tool [/SIZE][/FONT]*[/I] 
  
 *[I][FONT=Times New Roman, serif][SIZE=3]State: disconnected [/SIZE][/FONT]*[/I] 
  
 *[I][FONT=Times New Roman, serif][SIZE=3]- Device: eth0 ----------------------------------------------------------------- [/SIZE][/FONT]*[/I] 
 *[I]  [FONT=Times New Roman, serif][SIZE=3]Type:              Wired [/SIZE][/FONT]*[/I] 
 *[I]  [FONT=Times New Roman, serif][SIZE=3]Driver:            forcedeth [/SIZE][/FONT]*[/I] 
 *[I]  [FONT=Times New Roman, serif][SIZE=3]State:             unavailable [/SIZE][/FONT]*[/I] 
 *[I]  [FONT=Times New Roman, serif][SIZE=3]Default:           no [/SIZE][/FONT]*[/I] 
 *[I]  [FONT=Times New Roman, serif][SIZE=3]HW Address:        BC:AE:C5:95:4B:62 [/SIZE][/FONT]*[/I] 
  
 *[I]  [FONT=Times New Roman, serif][SIZE=3]Capabilities: [/SIZE][/FONT]*[/I] 
 *[I]    [FONT=Times New Roman, serif][SIZE=3]Carrier Detect:  yes [/SIZE][/FONT]*[/I] 
  
 *[I]  [FONT=Times New Roman, serif][SIZE=3]Wired Properties [/SIZE][/FONT]*[/I] 
 *[I]    [FONT=Times New Roman, serif][SIZE=3]Carrier:         off [/SIZE][/FONT]*[/I] 
 

 [FONT=Times New Roman, serif][SIZE=3](I suppose eth0 is the network card).[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]When I type <lsusb> I get this output (among other things)[/SIZE][/FONT]*[FONT=Times New Roman, serif][SIZE=3]:[/SIZE][/FONT]*
 *[I][FONT=Times New Roman, serif][SIZE=3]Bus 001 Device 003: ID 07d1:3c09 D-Link System DWA-140 RangeBooster N Adapter(rev.B1) [Ralink RT2870] [/SIZE][/FONT]*[/I]

[FONT=Times New Roman, serif][SIZE=3]But when I try <lshw -C network> the terminal gives me this message:[/SIZE][/FONT]
 *[I][FONT=Times New Roman, serif][SIZE=3]WARNING: you should run this program as super-user.[/SIZE][/FONT]*[/I]
 

 [FONT=Times New Roman, serif][SIZE=3]Iwconfig gives:[/SIZE][/FONT]
 

 *[I][FONT=Times New Roman, serif][SIZE=3]lo        no wireless extensions. [/SIZE][/FONT]*[/I] 
  
 *[I][FONT=Times New Roman, serif][SIZE=3]eth0      no wireless extensions.[/SIZE][/FONT]*[/I]
 

 [FONT=Times New Roman, serif][SIZE=3]When I go to System>Administration>Network Tools, only «Etherface Interface» and «Loopback interface» appear under «network devises». [/SIZE][/FONT] 
 

 [FONT=Times New Roman, serif][SIZE=3]I can still go to «Edit connections» by pressing the network icon, and edit my connection. The settings appears to be the same as before, but alas, still no connection. [/SIZE][/FONT] 
 

 [FONT=Times New Roman, serif][SIZE=3]Could anyone please help out a newbie? I guess the good thing about this mess, is that I get the opportunity to learn some basics of Ubuntu[/SIZE][/FONT]*[FONT=Times New Roman, serif][SIZE=3] :)[/SIZE][/FONT]*

---

### Post by chili555 on 2011-02-09
I believe rt2870sta is correct for your device, however rt2800usb also claims it and conflicts. Please run:```
lsmod | grep rt2
```Make sure none of the rt2 drivers are loaded. If so, they also need to be blacklisted. If not, please do:```
sudo modprobe rt2870sta
```That will load rt2870sta only. Now surf the web and tell us if your connection is stable. If so, we'll fix up your installation permanently.

---

### Post by Dry Lips on 2011-02-09
[FONT=Times New Roman, serif][SIZE=3]I followed your instructions and also blacklisted rt2800pci, rt2x00lib, rt2x00pci in addition to those I previously had blacklisted. The connection came up right away after rebooting! I've surfed a bit and done some installs without any trouble, so it seems as if it's working just fine... Now, do you think that [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]n[/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]disgt [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]and the windows driver I installed [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]should [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]be removed?[/SIZE][/FONT]
 
[FONT=Times New Roman, serif][SIZE=3]Thanks alot for your help so far! [/SIZE][/FONT]

---

### Post by chili555 on 2011-02-09
> Now, do you think that ndisgt and the windows driver I installed should be removed?Yes, I do. If rt2870sta is running your device correctly, you don't need them.> I've blacklisted: bcm43xx, b43, b43legacy, and [COLOR="Red"]rt2870sta[/COLOR] , rt2800usb, rt2800lib, rt2x00usbNow you need to remove rt2870sta from the blacklist.conf file and you should be all set. Post back if we can help you further.

---

### Post by Dry Lips on 2011-02-09
> **chili555 said:**
> Yes, I do. If rt2870sta is running your device correctly, you don't need them.Now you need to remove rt2870sta from the blacklist.conf file and you should be all set. Post back if we can help you further.

  Ahem, yeah... I just pasted the blacklist commando into the terminal:  
 

 echo -e "blacklist rt2800pci\nblacklist rt2x00lib\nblacklist rt2x00pci\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf  
 

 I couldn't figure out how to edit the blacklist file directly, since it was owned by the root...

---

### Post by chili555 on 2011-02-09
> I couldn't figure out how to edit the blacklist file directly, since it was owned by the root... Got root??

Here is a chance to learn a bit more about Linux. Let's open a text editor as root:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The file will open and you can check it and change it as needed. Among other things, it must contain:```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```If rt2870sta is blacklisted, remove that line. The b43 and ssb and other Broadcom lines are needless; you don't have such a device unless you haven't told me all about your system. You can remove them if you're OCD like me, but they won't help or hurt a thing.

Proofread twice, save and close gedit. Post back if it doesn't go as smoothly as I've suggested.

---

### Post by Dry Lips on 2011-02-09
I removed ssb, bcm43xx , b43 , b43legacy, and rt2870sta... When I restarted, I had no network connection... :(
 

 I blacklisted  ssb, bcm43xx , b43 , b43legacy (but not rt2870sta) again to be sure that they weren't causing any trouble, but still no connection upon restart. I ran <lsmod | grep rt2>  and <sudo modprobe rt2870sta> and the connection came up again...
 

 My entire blacklist looks like this:
 

 

 # This file lists those modules which we don't want to be loaded by 
 # alias expansion, usually so some other driver will be loaded for the 
 # device instead. 
  
 # evbug is a debug tool that should be loaded explicitly 
 blacklist evbug 
  
 # these drivers are very simple, the HID drivers are usually preferred 
 blacklist usbmouse 
 blacklist usbkbd 
  
 # replaced by e100 
 blacklist eepro100 
  
 # replaced by tulip 
 blacklist de4x5 
  
 # causes no end of confusion by creating unexpected network interfaces 
 blacklist eth1394 
  
 # snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much 
 # hardware on its own (Ubuntu bug #2011, #6810) 
 blacklist snd_intel8x0m 
  
 # Conflicts with dvb driver (which is better for handling this device) 
 blacklist snd_aw2 
  
 # causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306) 
 blacklist i2c_i801 
  
 # replaced by p54pci 
 blacklist prism54 
  
 # replaced by b43 and ssb. 
 blacklist bcm43xx 
  
 # most apps now use garmin usb driver directly (Ubuntu: #114565) 
 blacklist garmin_gps 
  
 # replaced by asus-laptop (Ubuntu: #184721) 
 blacklist asus_acpi 
  
 # low-quality, just noise when being used for sound playback, causes 
 # hangs at desktop session start (Ubuntu: #246969) 
 blacklist snd_pcsp 
  
 # ugly and loud noise, getting on everyone's nerves; this should be done by a 
 # nice pulseaudio bing (Ubuntu: #77010) 
 blacklist pcspkr 
  
 # EDAC driver for amd76x clashes with the agp driver preventing the aperture 
 # from being initialised (Ubuntu: #297750). Blacklist so that the driver 
 # continues to build and is installable for the few cases where its 
 # really needed. 
 blacklist amd76x_edac 
 blacklist rt2800usb 
 blacklist rt2800lib 
 blacklist rt2x00usb 
 blacklist rt2800pci 
 blacklist rt2x00lib 
 blacklist rt2x00pci 
  
 blacklist bcm43xx 
 blacklist b43 
 blacklist b43legacy 
 blacklist ssb

---

### Post by chili555 on 2011-02-09
Please amend the last part to read:```
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```Also do:```
sudo gedit /etc/modules
```Add a single line:```
rt2870sta
```Proofread, save and close gedit and reboot and let us have your report.

---

### Post by bkratz on 2011-02-09
Dr. Chili is probably washing his hands again (ocd you know!). Any you might want to copy/paste the output of 

gksudo gedit /etc/modules

So we can see if the module is being loaded at boot time or not.

Ignore above
Jeez, I have to not spend so much time thinking about a remark! Apparently I wasted 7 minutes without looking at the thread!

---

### Post by Dry Lips on 2011-02-09
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc



Took me about 10 seconds to do the brainwork for this reply ;)


But that's right, rt2870sta wasn't included...

---

### Post by Dry Lips on 2011-02-09
> **chili555 said:**
> Please amend the last part to read:```
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

```Also do:```
sudo gedit /etc/modules
```Add a single line:```
rt2870sta
```Proofread, save and close gedit and reboot and let us have your report.


Hey, hey! It finally works. You guys saved my day... Thanks a lot. Now we're talking!

---

### Post by chili555 on 2011-02-09
Glad it's working! Have fun.

---

