---
title: "Broadcom STA wireless driver"
date: 2010-07-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ve3tru on 2010-07-21
I cant get the Broadcom STA wireless driver to Activate (no mater what I try) I have no WFI...... anyone?
TNX

---

### Post by cariboo on 2010-07-21
The driver is on the Live CD if you don't have a wired network connection. it is in the /pool directory, look for bcmwl.

---

### Post by ranch hand on 2010-07-21
I do not have wireless so am no help there at all.

I would highly recommend reading the stickies at the top of our index page, alt least to first post of all of them.  This will save you and the rest of us a lot of hassle.

As to your problem, I think there has been discussion of that here so going to the top right of the index page, right above the listings, is Search this Forum.   I would try broadcom as your search.

Edit;
Or, of coarse, just listen to caraboo907

---

### Post by Jordanwb on 2010-07-21
I bought an Atheros chip on ebay that works great on Linux. Perhaps that would work?

---

### Post by ve3tru on 2010-07-21
"The driver is on the Live CD if you don't have a wired network connection. it is in the /pool directory, look for bcmwl."
'I have the driver installed cant get it to Activate.
I did a search before posting came up 0, though Im sure this issue came out with earlier versions of ubuntu.

---

### Post by cariboo on 2010-07-21
If you have the proper packages installed, can you manually install the modle?

```
sudo modprobe wl
```

---

### Post by ve3tru on 2010-07-21
peter@peter-laptop:~$ sudo modprobe wl
WARNING: /etc/modprobe.d/i915-disable-powersave.conf line 1: ignoring bad line starting with 'i915.powersave=0'
WARNING: /etc/modprobe.d/i915-enable-powersave.conf line 1: ignoring bad line starting with 'i915.powersave=1'
WARNING: /etc/modprobe.d/i915-disable-powersave.conf line 1: ignoring bad line starting with 'i915.powersave=0'
WARNING: /etc/modprobe.d/i915-enable-powersave.conf line 1: ignoring bad line starting with 'i915.powersave=1'
FATAL: Module wl not found.
FATAL: Error running install command for wl
peter@peter-laptop:~$ 

tried it doesn't seem to work
tnx

---

### Post by Jordanwb on 2010-07-21
The broadcom STA driver is proprietary and is not included in Live CD's because of licensing issues.

---

### Post by ve3tru on 2010-07-21
every time I try to Activate it I get this

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

what ever that is.

---

### Post by cariboo on 2010-07-21
> **Jordanwb said:**
> The broadcom STA driver is proprietary and is not included in Live CD's because of licensing issues.

See the screen shot of yesterdays kubuntu daily.

---

### Post by cariboo on 2010-07-21
> **ve3tru said:**
> every time I try to Activate it I get this

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

what ever that is.

That's the log file located in /var/log, to get to it, open nautiluis and click File System, then in the right pane click var->log.

---

### Post by ve3tru on 2010-07-21
I don't get it, because I already have it lol
Its in my package manager its already intalled ive installed like 5 times, I have wired internet now. it just wont Activate in my hardware drivers.
Maybe the package manager one has problems but its the the same one Ive always used
back to 8.04 with no problems.

---

### Post by ve3tru on 2010-07-21
found this if it helps


133 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0x28f7128>
2010-07-21 12:35:12,135 DEBUG: reading modalias file /lib/modules/2.6.35-9-generic/modules.alias
2010-07-21 12:35:12,269 DEBUG: reading modalias file /usr/share/jockey/modaliases/bcmwl
2010-07-21 12:35:12,269 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2010-07-21 12:35:12,300 DEBUG: reading modalias file /usr/share/jockey/modaliases/fglrx-modules.alias.override
2010-07-21 12:35:12,302 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-173
2010-07-21 12:35:12,304 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-96
2010-07-21 12:35:12,306 DEBUG: reading modalias file /usr/share/jockey/modaliases/nvidia-current
2010-07-21 12:35:12,309 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2010-07-21 12:35:12,560 DEBUG: loading custom handler /usr/share/jockey/handlers/nvidia.py
2010-07-21 12:35:12,567 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96

---

### Post by cariboo on 2010-07-21
It looks like you have problems with your video driver. Which one are you using?

---

### Post by ve3tru on 2010-07-21
Your right I think I do have problems with my video driver
By the way I got my wifi working yahoo.. I used this

On Ubuntu, you will need headers and tools.  Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

To check to see if you have this directory do this:

# ls /lib/modules/`uname -r`/build

Didn't have them this fixed the WIFI

As for my video problem I get this wierd blue screen on the top half, on boot up but after boot its ok.
Here's what I got
peter@peter-laptop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
peter@peter-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
peter@peter-laptop:~$ sudo apt-get install xserver-xorg-video-intel
[sudo] password for peter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  emacs diffstat quilt semi apel flim
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
peter@peter-laptop:~$ 

P.S.
Thanks for the help maybe this stuff can help others too.

---

### Post by cariboo on 2010-07-21
The error message is for nvidia drivers, you can remove them if you don't need them, just run a search in synaptic using the word **nvidia**, and remove everything nvidia that is installed.

---

### Post by ve3tru on 2010-07-22
I removed a bunch of them but not sure if I can remove these ones

X.Org X server -- Nouveau display driver (experimental)

X.Org X server -- NV display driver

smartdimmer
Change LCD brightness on Geforce cards

jockey-gtk
GNOME user interface and desktop integration for driver management

jockey-common
user interface and desktop integration for driver management

they seem to be for other cards not sure
Tnx

---

### Post by ve3tru on 2010-07-22
blue screen still there so maybe those have to go to?

---

### Post by ve3tru on 2010-07-22
Just a thought maybe I'm wrong but if these files are not included with the final installation or upgrade.
Then anyone trying to install Broadcom STA drivers will have the same problem.
Why not include, a two second blurb like.
On Ubuntu, you will need headers and tools.  Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux
This is strait from Broadcom's website.

---

### Post by cariboo on 2010-07-22
When installing the STA or any driver, from the repositories build essential is installed as a dependency.

I installed ndiswrapper in Kubuntu yesterday, build essential and dkms where installed too.

---

### Post by ve3tru on 2010-07-23
OK very cool.....but.. I still see blue on start up, well more like purple I'm colour blind.

---

### Post by ve3tru on 2010-07-23
Never mind I think they just fixed it in the latest update.
Thanks for all the help and putting up with a newbe, well not that new anymore
Id buy you a beer anytime.

---

### Post by ve3tru on 2010-07-23
"Very stable, very nice"
can we say beta.....

---

### Post by ve3tru on 2010-07-23
OH Ya just a thought, but why does the plug-ins have to be next the scroll down button.
I keep hitting it by accident?.

---

### Post by artshark on 2010-07-23
> **cariboo907 said:**
> See the screen shot of yesterdays kubuntu daily.
Can someone host this deb? that way i can throw it on a thumb drive and then upgrade, as I don't have easy access to an ethernet port.

---

### Post by cariboo on 2010-07-23
If you have an iso, you can mount it, and transfer the file from the mounted iso to your usb drive.

```
sudo mount -o loop maverick-desktop-i386.iso /mnt
```

Substitute your iso for the one in the example above.

---

### Post by ve3tru on 2010-07-23
Dam blue screen's back
It looks like the splash screen, but its all distorted and wacked (get it only on bootup)
even though I have the splash off by using Startup-Manager. Im not one of those computer geeks with pens in my pocket.
so any Ideas?

---

### Post by cariboo on 2010-07-23
I have the same problem on my netbook, it is plymouth. I can barely tell what it is, but it is intermittent, some times the logo works, and other times it's distorted.

---

### Post by ve3tru on 2010-07-23
I thought it might be video problems, nice to know I'm not the only one.
Tnx...
I think I like this OS its a keeper

---

### Post by ranch hand on 2010-07-23
Wrong thread

---

### Post by artshark on 2010-07-23
> **cariboo907 said:**
> If you have an iso, you can mount it, and transfer the file from the mounted iso to your usb drive.

```
sudo mount -o loop maverick-desktop-i386.iso /mnt
```Substitute your iso for the one in the example above.
thanks, definetely one option.
what if i do an in-place upgrade on my 10.04 install? will that break the broadcom driver i have now that works well?

---

### Post by cariboo on 2010-07-24
I can't see that as being a problem, I'll have to check my lucid install to see if the driver is the same version.

---

