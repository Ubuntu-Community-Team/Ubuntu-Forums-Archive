---
title: "Hardy: HOWTO: MobilePre (or Sonica/Ozone/Transit/Audiophile USB) with firmware loader"
date: 2008-07-01
forum: Multimedia Software
---

### Post by paulg on 2008-07-01
To use Madfuload in Fiesty/Gutsy, see the old howto [here]("http://ubuntuforums.org/showthread.php?t=466667").

***Update***
Upgraded to Intrepid a few days ago and I can confirm it didn't break anything so these instructions are good for 8.04 and 8.10. Pulse Audio is another matter for another thread...
************

First of all, the newer MobilePre's apparently work out of a box in which case you will not need to do anything. I have a MobilePre circa. 2003 which requires the firmware loader to work. If you follow these steps you should be able to  replace MobilePre with Sonica/Ozone/Transit/Audiophile USB if you have one of the other devices. The older devices require firmware and loader available here:
[http://usb-midi-fw.sourceforge.net/]("http://usb-midi-fw.sourceforge.net/")

This had been working for me for sometime and seemed to be set-off by Dapper (?) to some degree and now definitely would not work with Fiesty/Gutsy without intervention and broke again when upgrading from gutsy to hardy. Below is basically the same information to modify the UDEV loader fix from the Fiesty/Gutsy mod with an additional change to make it compatible with Hardy. Special thanks to HaightsW who posted the fix in the [Ozone thread]("http://ubuntuforums.org/showthread.php?t=148467"). His post can be seen [here]("http://ubuntuforums.org/showpost.php?p=4791301&postcount=72"). It appears there was an additional change to UDEV where subsystem was 'usb_device' and now should be 'usb'. Full instructions for Hardy and Intrepid below if you need them. Again, see the [old howto for]("http://ubuntuforums.org/showthread.php?t=466667") Fiesty/Gutsy instructions. I've seen rumblings that they are working on rolling Madfuload (and appropriate fix) into the next release so this may be the last time we need to do this.

[LIST=1]
[*]Install the [firware]("http://http://usb-midi-fw.sourceforge.net/") from the link above. Install directions are given on the site and view the README in the tarball for more help on compiling.
[*]The installer will create a udev rule in /etc/udev/rules.d/42-madfuload.rules
You will need to open the file with your favourite editor. I suggest the following command in terminal:
```
~$ sudo nano /etc/udev/rules.d/42-madfuload.rules
```
[*]Basically all of the lines are incorrect so you may as well comment all of them with a '#'. You could delete them but you may want to keep the one for the MobilePre so you can copy the product ID and firmware.
[*]Find the entry for MobilePre (or Sonica/Ozone/Transit/Audiophile) create a new line and paste the following
```
ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2804", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin -D $env{DEVNAME}"
```
[*]Replace the product ID and the firmware (file name ending with '.bin') in the above line with your device ID. Summary is below but you should be able to verify this in the original udev rule file.

[LIST]
[*]MobilePre
Product ID == 2804
firmware == ma004103.bin

[*]Sonica
Product ID == 2805
firmware == ma005101.bin

[*]Ozone
Product ID == 2808
firmware == ma008100.bin

[*]Transit
Product ID == 2806
firmware == ma006100.bin

[*]Audiophile USB
Product ID == 2803
firmware == ma003101.bin[/list]
[*]Just need to restart the udev listening engine:
```
 $ sudo /etc/init.d/udev restart
```
[/list]

As before, post successes and problems below. I'll help if I am able.

~pAul.

---

### Post by isaacj87 on 2008-07-10
Once again, thanks man!

I remember you helped me with this quite some time ago...Would be interesting to see this in the next release. :)

---

### Post by wolpert on 2008-08-16
I'm trying to get MobilePre USB working on my 8.04 box. (The one without midi ports) It worked fine on the 7.10 one, but doesn't run with the upgraded Ubuntu.

Basically, followed instructions to no avail. But interesting enough the 'lsusb' gives this: Bus 003 Device 002: ID 0763:200f Midiman 
And the details are here: 

Bus 003 Device 002: ID 0763:200f Midiman 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0         8
  idVendor           0x0763 Midiman
  idProduct          0x200f 
  bcdDevice            1.03
  iManufacturer           1 M Audio
  iProduct                2 MobilePre
  iSerial                 0 
  bNumConfigurations      1

Any ideas?  (I installed the "DFU" firmware from the site linked above)

Thanks!

---

### Post by wolpert on 2008-08-16
Okay, so the 200f version is the 'works out of the box' variant. The problem I had was audacity wasn't working with the device. The fix was to rebuild audacity and then it worked fine.

---

### Post by bbvdd on 2008-09-25
Thank you so much!

:cool:

---

### Post by kingbuzzo on 2008-11-13
I've noticed that sometimes my m-audio transit simply wont give any output.

I'll see that the soundcard is detected by xmms and playing media, but I wont actually hear anything from the line out.

This happened right after I attempted to have foobar2000 (through wine) access the card through OSS. Reinstalling the firmware doesn't seem to work unless I reformat first.

any idea?

---

### Post by bschultzjames on 2008-11-13
I can't even get ubuntu 8.1 to recognize the mobilepre is even connected.  I can record with ardour and jack through the built-in soundcard and mic on my laptop, but nothing shows up anywhere when I connect the mobilepre.


I tried a few terminal commands to see the installed firmware and nothing comes up that even looks relevant to audio.


Is there some software control I need to install to use the MobilePre in ardour?

---

### Post by paulg on 2008-11-13
Is it a pulseaudio issue? It's totally borked the audio on my system so I just kill it (system mainly used for recording and some light browsing) and rely on my programs interfacing with ALSA instead.

```
sudo killall pulseaudio
```

Then select ALSA as you've described.

If this works then it's a pulseaudio issue. There are many posts about 'fixing' it. Usually by uninstalling or disabling pulseaudio.

---

### Post by paulg on 2008-11-13
bschultzjames, with the MobilePre plugged into a working USB port and the power on, what does the following command return?

```
lsusb
```

Edit: by power on, confirm you have power to the unit with either the main LED on or the phantom power LED on when the button is depressed.

---

### Post by gerlach1025 on 2008-11-23
This may be the wrong thread to post in but I figured I would try here before starting a new thread, especially since the title did say ozone. I am having trouble getting my m-audio ozone working correctly with ubuntu. If I boot up ubuntu with the ozone turned on, lsusb only shows midiman and the device is not detected by any audio programs. If I then reboot into the windows xp partition the ozone works fine. I reboot back into ubuntu and now lsusb shows the ozone in the list and it is detected and works with all the audio software. Then if I turn off the ozone and turn it back on, or if I shutdown and turn the unit off and back on, I'm back to square one. :confused: I've followed the tips in all the various threads but I continue to have this issue. Right now I'm running Intrepid and I installed madfuload using the repos. Does anyone have any ideas on what I'm doing wrong. If I'm lacking details let me know what info I should supply.

Thanks

---

### Post by paulg on 2008-11-23
Have you modified the madfuload udev rules as described in this thread?

What you are seeing is normal. When you boot into Windows the firmware is being loaded and by rebooting without powering down the unit it's retaining the firmware and allowing you to use it in Linux. It sounds like you don't have udev configured to take advantage of the firmware in madfuload. See the first post in this thread and modify the values for the Ozone (given in the list). The example given is for the MobilePre because that's what I have, but it should also work for the Ozone if you replace the values. Let us know how it goes.

---

### Post by gerlach1025 on 2008-11-23
> **paulg said:**
> Have you modified the madfuload udev rules as described in this thread?


I will take a look at my settings again. I've modified them before but I have also uninstalled and reinstalled a couple times so I may have missed something. I'll let you know how I make out. You did reassure me that I'm wasting my time. Thanks.

---

### Post by gerlach1025 on 2008-11-24
@paulg

Ok, I looked at the udev rules and realized that I had the wrong path for the ma008100.bin file. Instead of /usr/local/share/usb/maudio it should have been /usr/share/usb/maudio. Pure sloppiness on my part. Everything is working great now. :guitar: Thanks again for the help.

---

### Post by paulg on 2008-11-24
No problem. Better user error than something worse!

How is the midi (e.g. the keyboard) on the Ozone being handled? It's been a while since I've checked any of the Ozone threads. Last I checked some people were *just* starting to get it to work. Any howto's you followed I should link to in the first post?

---

### Post by gerlach1025 on 2008-11-25
All you need to do is install madfuload from the repos using either apt or synaptic and then modify the udev rules as per your instructions. The only difference in my case was the files were installed in /usr/sbin and usr/share/maudio instead of /usr/local/sbin and /usr/local/share/maudio as listed in step 4 of your instructions. 
The audio and midi are working great with alsa. As long as the program supports midi from alsa the keyboard is fine. I am having issues getting jack to work correctly with the unit. Every time I start jack with the ozone set as the default hardware, jack crashes. I can live with out jack but it would be nice to have it working correctly. When I have more time I will look into it a bit more.

---

### Post by Monona on 2009-01-09
After having followed the directions here, I got my M-Audio Ozone working just fine as a MIDI controller.  I even got audio through the mic input for the first time last night.  This morning, nothing.  No Ozone when I run "asoundconf list", no Ozone in jack, no MIDI input for anything. 

I've spent the better part of the day trying to figure this out, and I've come up blank.  

When I run lsusb, it shows up:

Bus 003 Device 002: ID 0763:2008 Midiman

dmesg gives me this:

[   34.319697] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/acore/init.c:174: cannot find the slot for index 0 (range 0-0), error: -16
[   34.319707] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usbaudio.c:3477: cannot create card instance 0
[   34.319716] snd-usb-audio: probe of 3-2:1.0 failed with error -5
[   34.319735] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/acore/init.c:174: cannot find the slot for index 0 (range 0-0), error: -16
[   34.319741] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-rt/sound/alsa-driver/usb/usbaudio.c:3477: cannot create card instance 0
[   34.319747] snd-usb-audio: probe of 3-2:1.3 failed with error -5

I can tell there's something wrong with how snd-usb-audio is working but I don't know what.  I can't find any information about that particular error message, except that other people have had it.

I'm way over my head technically, and I'm pretty frustrated.  Any help?

Edit: I also upgraded my kernel last night, to 2.6.24-23-rt, but it was running fine even after I restarted my computer.  I'm running Ubuntu 8.04 on an Acer TravelMate 4010 with a 1.6 Ghz Pentium M.  If that's important.

---

### Post by Concussion on 2009-04-05
I am about to pull my hair out...well what is left of it. 

I've been working on getting my Ozone working for 3 days now. 
I've followed all of the instructions, I've gone from Intrepid to Hardy just to make sure it wasn't intrepid, and I've done the boot from Windows with the Ozone loaded back into Studio with no luck. 

Here is what I have as far as readouts. 

lsusb
```
concussion@Portable:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0763:2808 Midiman 
Bus 001 Device 001: ID 0000:0000  

```

asoundconf list
```
concussion@Portable:~$ asoundconf list
Names of available sound cards:
Intel

```

With this I get zero output
```
concussion@Portable:~$ sudo modprobe snd-seq-midi
concussion@Portable:~$ 

```

and then my madfuload rule which I changed the directories on to match directories on my system.
```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2808", RUN+="/usr/sbin/madfuload -l -3 -f /usr/share/usb/maudio/ma008100.bin -D $env###{DEVNAME}"
```

I used to run linux about 4 years ago but I couldn't get done what I needed to so I went back to Windows. I'm hoping to make the switch permanently this time, but if I cannot get my Ozone working then I'll be switching back again. I want to use Studio because of the visual and audio direction that it's heading towards.

Please help me figure this out.

---

### Post by muhkayoh on 2009-05-05
Well, I now have that sinking feeling that comes sometimes when I've followed all of the instructions and the darn thing still doesn't work.  

I've got a Mobile Pre, so I followed those instructions, then I tried uninstalling and reinstalling Audacity, but still no signal from the microphone.  This same Mobile Pre works on my Windows desktop, so the unit itself is fine.

my lsusb reads:

Bus 005 Device 002: ID 0763:200f Midiman M-Audio MobilePre
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


I'm still on Hardy.

Any suggestions?

Thanks,

Matt

---

### Post by paulg on 2009-05-06
muhkayoh, You appear to have the correct USB device ID so I think the device has been installed properly. 

What's the  output of aplay -l? If the MobilePre is listed there then it's a valid audio device on your system and the good news is it's installed. The bad news is if you're not getting audio then something else is wrong. My first guess would be that you are currently experiencing pulseaudio problems so I suggest you seek out a howto on that for Hardy. There was quite a useful one that was stickied in the media forum.

Concussion,Haven't been back to this thread for a while. Unfortunately the directions I have only apply to the audio side of the Ozone. I have no idea how to get the midi working and only have a very small idea on how to use midi on linux, sorry.

You do appear to not have the audio working either? The last bit in your rule, $env[COLOR="Red"]###[/COLOR]{DEVNAME}, has '###' in it. You don't need that, take it out. The midi module you are loading I suppose could be handling the midi side of things. I am not certain how to detect if it is working for you or not. The fact that it's not giving any output means the module has been loaded successfully although doesn't mean anything about whether or not the module is detecting the hardware. Try 'lsmod | grep snd' and looking for something called snd_usb_audio (or something like that). I believe that module will be operating the firmware on the Ozone for the audio side but maybe getting audio working will help you out with the midi as well. Can't hurt anyway.

---

### Post by muhkayoh on 2009-05-06
paulg,

Thanks, the pusleaudio clean-up fixed it.

Matt

---

### Post by mrche on 2009-06-13
I downloaded the firmware but couldn't get it to install.  When I double click on the "Configure" file nothing happen.  It doesn't create the /etc/udev/ rules there.

So i went to package manager and install the madfuload there.

However, it still doesn't create the /etc/udev rules.

I am totally stuck now as both my AC97 built-in nor the Sonica works so I have no audio.

I should also mention that I am a total newbie and using the 9.04 version.

This is what lsusb gives:
Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0763:2805 Midiman 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

asoundconf list give me nothing

Please help.

---

### Post by lhbecker on 2009-06-14
Hi

I am also struggling to get my MobilePre going on my Lenovo Thinkpad T61. Like most laptop computers, it has built-in sound. An Intel Chipset. I have installed madfuload using Synaptic Package Manager. If I run "lsusb", I get the following:

...
Bus 005 Device 002: ID 0582:0009 Roland Corp. Edirol UM-1SX MIDI Adapter
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0763:2804 Midiman M-Audio MobilePre DFU
...

The UM-1SX is a usb midi device.

If I run "aplay -l" I get the following:

card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

To me it looks like the MobilePre drivers are loaded, hence being visible through lsusb-command, but it is not visible to/configured in ALSA. I have searched all the ubuntu forums and many site beyond, but I am still not able to get it going.

Someone, please help.
Louis

---

### Post by mrche on 2009-07-13
I GOT MINE working! I have never been this happy : )
 
I have decided to share what I did (in red) so anyone with Ubuntu 9.04 Jaunty Jackalope can try it out.
 
 
Install the [firware]("http://http//usb-midi-fw.sourceforge.net/") from the link above. Install directions are given on the site and view the README in the tarball for more help on compiling. [COLOR=red]*EDIT : Install madfuload using Synaptic Package Manager instead.*[/COLOR]
[COLOR=red]*Goto System --> Administration --> Synaptic Package Manager --> Search madfuload --> highlight madfuload and right click to select &#8220;Mark for installation&#8221; --> Apply*[/COLOR]
 
1. The installer will create a udev rule in /etc/udev/rules.d/42-madfuload.rules [COLOR=red]*EDIT : After installation. The 42-madfuload.rules was found under /lib/udev/rules.d/42-madfuload.rules. Use the &#8220;Search for Files&#8221; function under &#8220;Places&#8221; if you have trouble finding this file.*[/COLOR]
 
2. You will need to open the file with your favourite editor. I suggest the following command in terminal:
 
Code: ~$ sudo nano /etc/udev/rules.d/42-madfuload.rules 
*[COLOR=red]EDIT : Open the file with the correct path of the 42-madfuload.rules. [/COLOR]*
*[COLOR=red]In my case, it will be [/COLOR]*
[COLOR=red]*Code: ~$ sudo nano /lib/udev/rules.d/42.madfuload.rules*[/COLOR]
 
3. Basically all of the lines are incorrect so you may as well comment all of them with a '#'. You could delete them but you may want to keep the one for the MobilePre so you can copy the product ID and firmware.
 
*[COLOR=red]EDIT : No change here.[/COLOR]*
 
4. Find the entry for MobilePre (or Sonica/Ozone/Transit/Audiophile) create a new line and paste the following
 
Code:
 
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2804", RUN+="/usr/local/sbin/madfuload -l -3 -f /usr/local/share/usb/maudio/ma004103.bin -D $env{DEVNAME}" 
 
[COLOR=red]*EDIT : Removed /local from both path. Again, use the "Search for files" function to make sure the path for both madfuload and ma00xxxx.bin are correct. *[/COLOR]
 
5. Replace the product ID and the firmware (file name ending with '.bin') in the above line with your device ID. Summary is below but you should be able to verify this in the original udev rule file.

[LIST=1]
[*]
[LIST]
[*]MobilePre
Product ID == 2804
firmware == ma004103.bin
[*]Sonica
Product ID == 2805
firmware == ma005101.bin
[*]Ozone
Product ID == 2808
firmware == ma008100.bin
[*]Transit
Product ID == 2806
firmware == ma006100.bin
[*]Audiophile USB
Product ID == 2803
firmware == ma003101.bin
[/LIST]
[/LIST][COLOR=red]EDIT : After this step. This is what I have for my Sonica[/COLOR]
[COLOR=red]ACTION=="add", SUBSYSTEM=="usb", SYSFS{idVendor}=="0763", SYSFS{idProduct}=="2805", RUN+="/usr/sbin/madfuload -l -3 -f /usr/share/usb/maudio/ma005101.bin -D $env{DEVNAME}"[/COLOR]
  
Just need to restart the udev listening engine:
 
Code
$ sudo /etc/init.d/udev restart 
[COLOR=red]EDIT : RESTART COMPUTER.[/COLOR]
 
I am a total newbie and by chance I got mine working. Wrote this so that I can share this with everyone who might have trouble as well. At first, I was so frustrated neither of my build-in AC97 audio or my Sonica USB audio work that I was about to give up. Now I am a happy camper again : ) Hope this help.
 
[COLOR=red]EDIT : Also, I had to disable onboard audio for this to work consistantly.[/COLOR]

---

### Post by jy_moustache on 2010-06-24
Hi

Did anyone experience some trouble when upgrading from Karmic Koala to Lucid Lynx ?

My mobilePre worked just fine on Karmic but since the upgrade to Lucid, I've been experiencing some troubles. The soundcard seems to be recognised but I only get a low level of output (extremely low as a matter of fact).

I'm wondering if it's madfuload or ALSA related.

Thanks

jy

Here are some logs from "cat /proc/asound/cards" :
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0400000 irq 22
 1 [MobilePre      ]: USB-Audio - MobilePre
                      M Audio MobilePre at usb-0000:00:1d.2-2, full speed

```
Seems to be fine, right ?


**EDIT** finally alsamixer did the trick

---

