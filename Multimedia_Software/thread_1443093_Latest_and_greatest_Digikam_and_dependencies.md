---
title: "Latest and greatest Digikam and dependencies"
date: 2010-03-30
forum: Multimedia Software
---

### Post by philip5 on 2010-03-30
Just thought I should start a thread about the latest and greatest for Digikam and dependencies.

For starters I maintain a rolling release PPA on Launchpad and more info about that is found in my signature.

I just updated my PPA with Digikam 1.2.0 for Karmic. You can read more about what's new in 1.2.0 here: [http://www.digikam.org/drupal/node/511](http://www.digikam.org/drupal/node/511)

I also updated kipi-plugins to 1.2.0 also just for Karmic. You can read more about what's new in it here: [http://www.digikam.org/drupal/node/512](http://www.digikam.org/drupal/node/512)

My repository also include an updated version of libgphoto2-2 to 2.4.8 for Karmic which vill make some cameras work better that use libgphoto2 for transfering and camera photo handling.

If you use kde 4.4.x with Karmic from the Kubunt teams PPA then you should also use my PPA called kde44. If you only use standard Ubuntu repositories (including backports) then use my standard extra PPA.

Any feedback on these packages or discussions about Digikam usage are welcome in this thread.

Here is just a little screenshot teaser but more of them at the digikam site ([http://www.digikam.org](http://www.digikam.org))

[[img]http://www.ubuntu-pics.de/thumb/49695/screenshot_042_5KSid3.png[/img]](http://www.ubuntu-pics.de/bild/49695/screenshot_042_5KSid3.png)

Have fun with these awesome piece of software! :)

---

### Post by rerx on 2010-04-02
Thanks! I was just looking for 4.4 builds of the new digikam and you saved me the trouble of compiling them on my own.

---

### Post by philip5 on 2010-04-02
> **rerx said:**
> Thanks! I was just looking for 4.4 builds of the new digikam and you saved me the trouble of compiling them on my own.

You are welcome. Hope the packages work as fine for you as they should... :)

One of the pros with using especially kipi-plugins with KDE 4.4.x is that you also get the ExpoBlend tool. The reason you don't find it in the package of kipi-plugins in the "extra" repository is because it needs KDE 4.4.x to be built and the standard version of KDE in Ubuntu 9.10 backports is 4.3.5 (at the moment).

More feedback are always welcome.

---

### Post by jessel on 2010-04-18
Thanks. I am finally able to use the image blending tool in Digikam. I had to upgrade (and switch to Kubuntu...) but your ppa made it happen!

Now I'm really liking Digikam, and may switch (from gimp + fspot).

---

### Post by philip5 on 2010-04-19
> **jessel said:**
> Thanks. I am finally able to use the image blending tool in Digikam. I had to upgrade (and switch to Kubuntu...) but your ppa made it happen!

Now I'm really liking Digikam, and may switch (from gimp + fspot).

Yes I really like Digikam (with kipi-plugins) too and I would almost go as far as saying it could be a killer app more many people using Linux who are into photography. I really like KDE too so for me it's win-win as it blends into my desktop so smoothly compared to using Digikam from i.e Gnome. :)

---

### Post by philip5 on 2010-04-22
Just thought I should let you all know that I updated libgphoto2 in my PPA for Karmic to version 2.4.9.1. That would help in many cases for you guys who use cameras that don't function as a usb-memory/stick and also is a library that Digikam use for this functionality. Have fun!

Here is the complete changelog of libgphoto2 since version 2.4.6 that comes with official Ubuntu Karmic. If you find any fixes or new features regarding your camera then you should get the update:

```
libgphoto2 2.4.9
This is a 2.4 release branch update. 
ptp2 driver
•Fixed EOS viewfinder capture speed (2 images/s -> 20 i/s) 
•EOS event handling cleaned up, so that we can also have dual image capture (RAW+JPEG). 
•New Canon EOS properties: autoexposuremode, cameraoutput, evfmode, uilock. 
•New Nikon property: exposuredelaymode 
•Fixed a Canon Powershot configuration bug that caused hangs. 
•Fixed a Nikon Coolpix configuration bug that caused hangs. 
•Fixed shutterspeed setting to be more generic. 
•New IDs added: 
&#9702;Nikon Coolpix 8800, P6000, L20, L19 
&#9702;Panasonic FS62 
&#9702;Olympus FE4000/X920/X925, 
&#9702;Canon EOS 550D 
&#9702;Canon Powershot A2100IS, SD970IS, SX20IS, IXUS 120IS 
&#9702;Fuji FinePix S1500, Z35, S2500HD 
&#9702;Apple iPhone 3GS 
•Some bugs fixed, some memory leaks closed. 
•music-players.h merged from libmtp, bringing new MTP devices. 
ST2205 Driver
New Pictureframe driver from Hans de Goede. st2205 based frames present themselves as a regular usb mass storage device, but cannot be used as a normal disk! Communication with the device happens by a special protocol which consist of reading / writing sectors of the disk at certain magic offsets. Also included is a "usbdiskdirect" port driver, which allows the direct sector access the camlib for these devices needs. 
AX203 Driver
New Pictureframe driver from Hans de Goede. ax203 based frames present themselves as a usb mass storage cdrom, which contains the windows software. Communication with the device happens by issuing special (custom) scsi commands. Also included is a "usbscsi" port driver, which allows sending the custom scsi commands. Note that if your ax203 frame has a usb-id of 1908:1315, you need to tell Linux not to touch the HID device this version also presents in its USB descriptor. To do this add the following on the linux kernel cmdline: "usbhid.quirks=0x1908:0x1315:0x4" 
digita
Made to work again hopefully after breakage due to filesystem changes. 

--------------------------------------------------------------------------------

libgphoto2 2.4.8
This is a 2.4 release branch update. 
libgphoto2
•Updated translations. 
•Added read-only flag for Widgets. gp_widget_set_readonly / gp_widget_get_readonly. 
•GP_EVENT_CAPTURE_COMPLETE event added from trunk. 
•Some bugfixes. 
ptp2
•New USB IDs for cameras: 
&#9702;Kodak Z915 
&#9702;Nikon CoolPix S220, S225, 
&#9702;Nikon DSLR D5000, D3000, D300s 
&#9702;Canon PowerShot SD770 IS, A580, SD1200, IXUS 95 IS, G11, IXY 220IS, SD940IS 
&#9702;Canon EOS 7D 
&#9702;Fuji S5 Pro 
&#9702;Sea & Sea 2G 
&#9702;Also merged new libmtp deviceids. 
•Fuji S5 Pro capture support. 
•Bugfixes in Canon EOS preview code. 
•Fixed NIKON DSLR shutterspeed not able to set bug. 
•Nikon error decoding. 
•Several Canon EOS configuration and capture additions and fixes, focus pulling. 
•PTP protocol stability improvements. 
•Lots of bugfixes. 
sierra
•restrict list of choices for Nikon Coolpix 4300 
directory
•Merged from TRUNK to gain the good stuff. 
libgphoto2_port/usb
•Updated translations. 
•Check for MTP devices by string descriptor first and by OSD later. 

--------------------------------------------------------------------------------

libgphoto2 2.4.7
This is a 2.4 release branch update. 
libgphoto2
•Translation updates from translationproject.org. 
•Widget and choice lists now dynamic, to be able to create longer ones. 
•3rd generation UDEV rules emission, now able to emit "post HAL" UDEV rules. 
print-camera-list udev-rules version 136 > /lib/udev/rules.d/40-libgphoto2.rules 
•Dsabled LRU of images. Not really useful in times of USB 2.0, aso disabled by at least Debian und Ubuntu already. 
libgphoto2_port / USB
•If we detached a USB driver, reattach it on close. This allows using e.g. cheap camera as both webcam with in-kernel driver and still camera with libgphoto2. 
PTP2 driver:
•Renamed various configuration options and changed values to match a unified model. Some common names have changed: 
&#9702;owner->ownername 
&#9702;exptime->shutterspeed 
&#9702;eos-* -> non-eos prefixed variants 
&#9702;etc. 
You will need to review configuration setting code if you have any. 
•Create config submenus /actions for action triggers and /status for read-only values, moved stuff there. 
•New IDs: 
&#9702;Kodak M863 
&#9702;Canon Digital IXUS 110IS, IXUS 100IS, Powershot SX200IS, SD780 IS, A1100IS 
&#9702;Canon EOS 500D 
&#9702;Fuji Finepix F200 EXR 
&#9702;Apple iPod Touch first generation 
•Lots of Canon EOS capture improvements, for card capture, for LiveView, and for property setting. More properties are now possible. 
•Canon EOS Bulb mode support (available in newer canons). --set-config bulb=(0|1) 
•Fixed Nikon DSC shutterspeed setting (also for times < 1/1000) 
•Enable Viewfinder on demand for Canon Powershot, not for all capture things. 
•Generic PTP Property Get/Set in the configuration handling. 
•Decode more Nikon DSC properties (for D90 now nearly complete). 
•Turned several PTP generic commands to macros to reduce number of functions. 
•MTP player list synced with libmtp 1.0. 
•Lots of bugfixes. 
Canon driver:
•Renamed various configuration options and changed values to match a unified model. 
```

---

### Post by babarosa on 2010-04-22
philip5,

once again thank you very much for your addiction.

I am on xfce (Xubuntu) - do you know if gtkam is equal featurewise to digikam (I try to avoid installing kde stuff ;-) ?

I am using a canon eos 450d for astrophotography ([www.harpoint-observatory.com](www.harpoint-observatory.com)) and try to replace the windows based eos utility with gphoto2 et al. 
Does anybody know if gphoto2 et al also provide a "live view"-transmitting feature?

Greetings,
Michael

---

### Post by philip5 on 2010-04-22
> **babarosa said:**
> philip5,
once again thank you very much for your addiction.


> ad·dic·tion&#8194; &#8194;/&#601;&#712;d&#618;k&#643;&#601;n/  Show Spelled[uh-dik-shuhn]  
–noun
the state of being enslaved to a habit or practice or to something that is psychologically or physically habit-forming, as narcotics, to such an extent that its cessation causes severe trauma. 

I couldn't help pointing out (with a big smile) that I hope that I don't have that effect on anyone. If I'm usefull then I'm happy but if you get addicted to me then you might seek help professional help... :D


> **babarosa said:**
> I am on xfce (Xubuntu) - do you know if gtkam is equal featurewise to digikam (I try to avoid installing kde stuff ;-) ?

I am using a canon eos 450d for astrophotography ([www.harpoint-observatory.com](www.harpoint-observatory.com)) and try to replace the windows based eos utility with gphoto2 et al. 
Does anybody know if gphoto2 et al also provide a "live view"-transmitting feature?

Greetings,
Michael

But now to your question. You can't even start to compare gtkam and Digikam as Digikam is so much more and better in every aspect besides having a small fingerprint on your system. gtkam is just a basic little application that let you browse photos on your camera and select, delete and transfer them. Digikam is more like i.e F-spot (or Adobe Lightroom) and also handles, sorts and organizes all your photos on your harddisk and other media. In my oppinion Digikam is much better than F-spot but have the disadvantage for some users that it's tightly integrated with kde4 and needs a bunch of kde4 and qt4 dependencies.

I can understand that you don't want to use Digikam if you don't use kde4 but in my world Digikam is almost worth going over to kde4 (I use kde4 anyway) as it's a real killer app if you are into digital photographing and Linux.

---

### Post by babarosa on 2010-04-22
> If I'm usefull then I'm happy but if you get addicted to me then you might seek help professional help...
:) I am no native english speaker and got the word "addiction" by typing the german word "Hingabe" into my dictonary.
"Hingabe" is also translated as "abandonment, addiction, application, commitment, dedication, devotedness, devotion, indulgence, surrender". Please take any word you prefer \\:D/   

Concerning gtkam - you confirmed my impression that gtkam can not be compared with eos utility's features.

Greetings,
Michael

---

