---
title: "How-To: Creative X-Fi"
date: 2008-07-25
forum: Multimedia Software
---

### Post by NullHead on 2008-07-25
[CENTER]As of the writing of this message, the guide below is no longer needed and should not be used. The reason being Alsa has finally produced a working drive. Alsa's new drive is included in kernel 2.6.31.X. As of Ubuntu 9.10 (Karmic Koala), the Creative X-Fi soundcard will work out of the box!

For people who still want to use the older Ubuntu releases, see [GeekGirl1's guide for updating Alsa]("http://ubuntuforums.org/showpost.php?p=8011636&postcount=21"). This guide should technically work with any version of ubuntu, though I have only tested with Ubuntu 9.04.
Please note that GeekGirl1's guide does indeed work with 5.1 surround sound.[/CENTER]


[QUOTE=Old Guide]**[SIZE="4"][CENTER]Creative 1.00 driver guide.[/CENTER][/SIZE]**
[SIZE="3"][CENTER]**A note to all users:**[/CENTER][/SIZE][COLOR="Red"]**[CENTER]This driver does [B]not work** with Ubuntu 8.04LTS (Hardy)
and the front panel **does not** work[/CENTER]
 [/B][/COLOR]
[CENTER]
There are reports of Creative's driver working on the new shiny Ubuntu 9.04. I've not tested this myself, but don't let that stop you. You'll apparently need the package "flashplugin-nonfree-extrasound" to get sound out of youtube/flash. To install it: ```
sudo apt-get install flashplugin-nonfree-extrasound
```
[SIZE="4"]**Guide: Alsa/Creative**[/SIZE][/CENTER]

**[b]Note:** You need to reinstall this driver every time there is an update to your kernel. [/B]

To start off, download the file into your home directory. Use this command in a terminal, Applications>Accessories>Terminal, to download the file automatically into your home directory so you don't have to worry. ```
wget http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz
```**Note: **Downloading that file assumes that you accept and agree to [Creatives ELUA](http://nullhead.freehostia.com/creative_elua.html).

Next we want to unpack the directory with this command, also ran from the same terminal window.  ```
tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
```

We now want to change into the directory that we just created that contains the Creative drivers. ```
cd XFiDrv_Linux_Public_US_1.00
```
Install dependencies. ```
sudo apt-get install build-essential linux-headers-`uname -r`
```Now we want to compile and install these drivers.
 
**Note: If you have a PCI-E X-Fi card, read this post before continuing**:  [http://ubuntuforums.org/showpost.php?p=6369503&postcount=148](http://ubuntuforums.org/showpost.php?p=6369503&postcount=148)```
make
``````
sudo make install
```You're going to need to put in your password for the last step to finish.

Make your sound settings, System>Preferences>Sound, look like this: 
[img]http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367[/img]

The final step is restarting your computer. Bookmark this page, save anything you're working on, and reboot the computer. 

When the computer comes back to your desktop, you should have sound coming from your rear sound panel. **The front panel does _not_ work!**

If you're having issues with your newer PCI-E XFi, then take a look here: [http://ubuntuforums.org/showpost.php?p=6369503&postcount=148](http://ubuntuforums.org/showpost.php?p=6369503&postcount=148)
**Note**: That post won't really help you unless you're at least slightly knowledgeable about linux. 

To enable 5.1 surround sound, see here: [http://ubuntuforums.org/showpost.php?p=7736411&postcount=432](http://ubuntuforums.org/showpost.php?p=7736411&postcount=432)

[CENTER]
[SIZE="4"]**Guide: OSS**[/SIZE]
**This should work with any version of Ubuntu.**[/center]

Use this guide to install OSS: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

If OSS fails to install or update use this guild to help you uninstall it: [http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

**Note:** OSS should work with Ubuntu 9.04. I tried it out and it seems to work just fine for me. In fact, the audio quality seems to have improved and you no longer need to patch your sound control (the speaker in the top right of your screen). 

**Enjoy**


Deprecated guide: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)[/QUOTE]

---

### Post by Yellow Pasque on 2008-07-25
> If OSS fails to install or update use this guild to help you uninstall it: [http://4front-tech.com/forum/viewtopic.php?t=2054](http://4front-tech.com/forum/viewtopic.php?t=2054)
I found that newer users became confused at the edit step, either trying to use the command 'edit' literally or opening gedit without root permissions. Specifically, in Ubuntu/Debian, the command is:
```
gksudo gedit /var/lib/dpkg/status
```
I made a post about it a while ago after a few PM's from confused n00bs.
[http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

---

### Post by NullHead on 2008-07-25
Thanks! I updated the link to reflect the n00b friendly version of the guide. :D

---

### Post by Yellow Pasque on 2008-07-25
Some of the links are broken.

OSS4 Guide - [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)
Creative's unofficial driver: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

---

### Post by NullHead on 2008-07-25
> **Temüjin said:**
> Some of the links are broken.

OSS4 Guide - [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)
Creative's unofficial driver: [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)

Heh thanks again, Temüjin. 

By the way, are you still on vacation? :lolflag: That is what your avatar suggests.

---

### Post by John Matrix on 2008-08-11
Hi, and thank all of you for all the effort you are putting into this!

I feel I am kind of close to getting this to work, though I've yet to hear the first bit of sound from my Sound Blaster X-Fi XtremeGamer. I was working from the old (very long) thread, though, but the instructions there seem to be identical.

I decided that the Creative driver wasn't going to work for me, after several failed attempts (I'm running 8.04 32bit). So I did a fresh install of Ubuntu, updated all packages, and then followed Temüjin's OSS guide.

After that, I tested the sound under "Sound Preferences" in the System -> Preferences menu. At least I wasn't getting any error message, and the little moving bar appeared, suggesting that my sound is being tested, but no sound (which is working fine under Vista). 
However, after the next system reboot, I got an error message when doing the same test, namely

```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! 
gconfaudiosink: Could not open audio device for playback. Device is being
used by another application.

```

And osstest outputs :

```

Sound subsystem and version: OSS 4.0 (b1016/200807241529) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
Note! Device is in use (by PID 6593/esd) but will try anyway
- Performing audio playback test... /dev/oss/sbxfi0/pcm0: Device or resource busy
The device is busy. There is some other application
using it.
Can't open the device
/dev/oss/sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** Scanning sound adapter #1 ***
/dev/oss/usb05a92643-1/pcmin0 (audio engine 2): USB sound device rec
- Skipping input only device

*** Some errors were detected during the tests ***

```

After I kill the esd process using System Monitor, the system again
behaves like it did after I first installed OSS, i.e. there's no
error message I when I do the tests in Sound Preferences, and osstest
outputs:

```

Sound subsystem and version: OSS 4.0 (b1016/200807241529) (0x00040003)
Platform: Linux/i686 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** Scanning sound adapter #1 ***
/dev/oss/usb05a92643-1/pcmin0 (audio engine 2): USB sound device rec
- Skipping input only device

*** Some errors were detected during the tests ***

```

By the way, the Onboard Sound in my system Bios is disabled.

Still I'm much happier so far with the OSS method than with the
ALSA/Creative method, since at least my sound card is being recognized.

I'd very much appreciate any hints how to finally make it work.
Thanks!

---

### Post by NullHead on 2008-08-12
Try disabling ESD through the menu system, System>Preferences>Sound>Sounds, and restart your computer.

[IMG]http://i209.photobucket.com/albums/bb7/masterchief-117/Screenshot-SoundPreferences.png[/IMG]

---

### Post by John Matrix on 2008-08-12
Thanks for your reply!

I did as you told me, but unfortunately, the result is still the same. My system is running on an XPS 730, in case anyone has a similar experience.

I'm considering installing 7.10, where even the Creative driver is supposed to work, unless I'm mistaken....

---

### Post by NullHead on 2008-08-12
The Creative drive will work out of the box with 7.10. All you need is build-essential and you can easily build and install it with ease. 

Could you open op a terminal and type in ```
dmesg >> dmesg_out.txt
``` and attach the .txt file that was generated in your home directory.

---

### Post by John Matrix on 2008-08-12
Would love to do that, but it seems that the file is too big (40kB) to be a legitimate attachment. Is there any portion of that file that will do?

---

### Post by NullHead on 2008-08-12
> **John Matrix said:**
> Would love to do that, but it seems that the file is too big (40kB) to be a legitimate attachment. Is there any portion of that file that will do?

Oh, I had no idea it'd be that big. 

Alright then, just copy out the last 30 lines or so and put it in a smaller txt file and upload *that* one. :lolflag:

---

### Post by John Matrix on 2008-08-12
Ok, here's the last chunk of messages. Don't know why the whole thing is so large...

---

### Post by mnnn on 2008-08-12
I guess here's the problem:
...
sbxfi: Interrupts don't seem to be working.
...
[   81.390281] osscore: Output timed out on audio engine 0/'Sound Blaster X-Fi (UAA) output' (count=0)
...
[   92.574637] osscore: Output timed out (sync) on audio engine 0
[   81.390281] osscore: Output timed out on audio engine 0/'Sound Blaster X-Fi (UAA) output' (count=0)
...

---

### Post by John Matrix on 2008-08-12
Hm, from googling "sbxfi: Interrupts don't seem to be working.", this problem seems to tend to occur on XPS systems ... I need to check if they actually found a solution.

Edit: Well, it seems not. See [here]("http://www.4front-tech.com/forum/viewtopic.php?p=8493&sid=ef19c06acde83888460bf4d8ef481442") , [here]("http://www.4front-tech.com/forum/viewtopic.php?p=9115&sid=e80d831ac792ce1fe6fd51fe5ce8e37f") , and [here]("http://www.opensound.com/forum/viewtopic.php?t=2491&sid=af0d09732507949424352a8b7d166dee") . :(

---

### Post by NullHead on 2008-08-12
Is it perhaps an OEM version of the X-Fi or did you buy it and put it in yourself?

---

### Post by John Matrix on 2008-08-12
It came with the XPS. The package slip identified it as X-Fi XtremeGamer. I am not sure if this is exactly what you get if you buy it over the counter. It seems that some people with similar problems suspect it's not...

---

### Post by John Matrix on 2008-08-17
Ok guys, the following method worked for me.

I installed 7.10, and found that the Creative driver worked out of the box, as NullHead said. However, under 7.10 I didn't get my monitor configured (Dell SP2208WFP), and was stuck with an 800x600 resulution. So I upgraded all packages, and then clicked on upgrade to 8.04 in the upgrade manager. When I was asked whether or not to keep my old blacklist file, I kept it.

Now 8.04 is running, and sound is still working, as is my monitor!

The only thing that doesn't work is system sounds, although they are enabled (I hear the little drum when the login screen appears, but after that no more). But I do get nice sounds from applications, including YouTube.

---

### Post by NullHead on 2008-08-17
I have never attempted a setup like that, but I'm glad it worked for you! 

Enjoy, 

NullHead

---

### Post by John Matrix on 2008-08-18
Thanks, couldn't have done it without the information posted in this thread!

---

### Post by go_beep_yourself on 2008-10-08
The driver will not work with the X-fi Titanium. I had to edit the installer file to get it to compile and once compiled, it did not work. I also noticed that in the description for the driver, it lists most or all the X-fi cards except for the Titanium. I'm really hoping that the next driver release will have support for it and/or Alsa will release their own for it. Anybody know if support is still under development or just died? I'm about to try OSS4, but really don't want to lose hardware mixing. For about 100 bucks, nobody should have to downgrade and lose hardware mixing all because these cards are the only ones that have EAX 5.0 for gaming in Wintendo. :mad:

---

### Post by go_beep_yourself on 2008-10-08
> **NullHead said:**
> They finally broke and released datasheets to both OSS and ALSA (Advanced Linux Sound Architecture).

When did this happen? And is the development by Alsa for the Xfi active or dead?

> Oss, obviously, has released a driver before ALSA has even started development. Therefore I choose not to have Creative's section included on this page anymore. It causes users too much trauma trying to get it to work and OSS works great anyways.

Did you find a way to get hardware mixing with the Xfi drivers and OSS4 or are you doing without that?

---

### Post by NullHead on 2008-10-08
> **go_beep_yourself said:**
> When did this happen? And is the development by Alsa for the Xfi active or dead?



Did you find a way to get hardware mixing with the Xfi drivers and OSS4 or are you doing without that?

You can check in [alsa's card matrix]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") for support from the Alsa team, but I doubt it'll happen any time soon. 

I've been doing without hardware mixing. I use OSS and it works very well. I'm actually using a compiled source from OSS's git tree. This works very well for me. 

I guess the only thing can tell you if you want a fully supported sound card is to go back to windows :( Sorry to be so blunt, but OSS is as good as it gets for the X-Fi at the moment.

---

### Post by go_beep_yourself on 2008-10-08
> **NullHead said:**
> Try disabling ESD through the menu system, System>Preferences>Sound>Sounds, and restart your computer.

[IMG]http://i209.photobucket.com/albums/bb7/masterchief-117/Screenshot-SoundPreferences.png[/IMG]

Is that similar to the hardware mixing Alsa does? Can you have sound from multiple applications at once using that with OSS4?

---

### Post by Yellow Pasque on 2008-10-08
OSS4 uses vmix for multiple sounds (ALSA uses dmix and doesn't necessarily do hardware mixing). You need to build OSS4.1rc2 according to the guide if you want vmix to work properly on your X-fi, because it was just fixed recently:  [http://mercurial.opensound.com/?rev=X-fi](http://mercurial.opensound.com/?rev=X-fi)

ESD is used for system sounds in GNOME. I guess one can try to route multiple sounds through it, but most people/distros have moved away from this because of how crappy ESD is.

---

### Post by go_beep_yourself on 2008-10-08
I just installed oss4 using that guide (should be 4.1rc2 but I don't know how to check), and I have no sound from my X-fi. OSS seems to want to use my onboard audio only and that has nothing hooked up to it. [http://pastebin.com/m676e663](http://pastebin.com/m676e663) I've been thinking about RMA the card but thought I should give this a try before deciding to do that, really tough call, can't get as good of a gaming sound card for xp in dual boot if I were to purchase something else.

---

### Post by Yellow Pasque on 2008-10-09
You can check your Build ID with:
```
ossinfo
```

If you're not using your onboard audio, then disable it in the BIOS. The next time you boot into Linux, run:
```
sudo soundoff
sudo ossdetect
sudo soundon
```
Make sure your speaker volume isn't too loud and run:
```
osstest
```

---

### Post by NullHead on 2008-10-09
Well OSS should work with your card, but I honestly wouldn't blame you if you returned it. If you end up returning it, I'd suggest you get [this](http://www.razerzone.com/p-91-razer-barracuda-ac-1-gaming-audio-card.aspx) card to replace it. It has full out of the box support with ALSA. So what you see is what you get; least with that card anyways ;)

---

### Post by go_beep_yourself on 2008-10-09
There's a lot of talk about getting the X-fi's working with alsa lately on the alsa-devel mailing list. They even say there's a way to put the sound cards in hda compatibility mode and use them with alsa right now. They need hardware to test it on, donations to buy the hardware, so they can test it themselves, and people that will test the alsa drivers on. Read the thread "[alsa-devel] Will there ever be emu20k1/x-fi support in Alsa?" and all of the responses here.
 
[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/thread.html#11214](http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/thread.html#11214)

---

### Post by Kato_san on 2008-10-18
If you look at the thread's at the [alsa-devel]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/date.html#start") mailinglist you will see that they now have a sort of beta ( backport ) driver for the X-fi series. You can find the thread's by looking for the key word  &#8220;sbxfi&#8221;. 
The new driver has support for more of the functions of the X-fi then the OSS driver.

Unfortunately I don have the time to test the driver myself. But maybe it could be of some use for somebody else here.

The development of the driver is very active so I suggest to keep a close eye on it.

---

### Post by NullHead on 2008-10-18
Thanks, Kato_san. 

I have been keeping a very lose eye on it, but I won't test it until there's reported success stories. Until then, I won't spend any time testing it. There's other people that are active in Alsa's development that are more suited for that task than I.

---

### Post by theguyotc on 2008-11-04
I've tried the driver from the Alsa mailing list, and it does actually work in a somewhat limited fashion. I was having trouble getting it to work with PulseAudio, but disabling the onboard sound card in the BIOS seems to have fixed that problem..

Problems with the driver:
[LIST]
[*]Only supports one thing playing at a time (though an Alsa plugin called dmix may help with that)
[*]Has the basic features of the early OSS driver, which means only 2 channels, no surround sound
[*]Unless I missed some simpler way, you have to replace all your Alsa drivers with the ones from the package, and I don't know the status of all of them
[*]Unless you get Pulseaudio working, you have to configure Ubuntu to use Alsa instead
[/LIST]

I'm kind of tired, so I may not be 100% on all the details, but I definitely did have sound coming from my X-fi.

To install, you need to download this:
**[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-unstable-snapshot.tar.bz2]("ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/alsa-driver-unstable-snapshot.tar.bz2")**

Then unpack it, run configure, make, and make install. It will replace all your Alsa drivers with the ones from the package. From then on, you may be able to just reboot. If that doesn't do it, try a modprobe. You may or may not need to run depmod first.

I'll try to come up with a more coherent post later.

Here's the initial post by the developer:
**[http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011270.html]("http://mailman.alsa-project.org/pipermail/alsa-devel/2008-October/011270.html")**
There were numerous bugfixes after the initial release. The last fix was on Oct 30th, and it is in the archive I linked to.

---

### Post by NullHead on 2008-11-05
Thanks, theguyotc. 

Currently, I am unable to test this. My linux hard drive has died on me and I'm waiting on my new one to come in the mail. After that comes, I'll probably test this on 8.10 as well as 8.04 and write up a guide for the first post in this thread.

---

### Post by mnnn on 2008-11-05
NullHead: Hope to see some multichannel support soon :)

---

### Post by theguyotc on 2008-11-06
I forgot to mention, I installed the driver on 8.10 (intrepid). No idea if it would work on 8.04.

Anyone know anything about Alsa's dmix plugin? I'd like to be able to have multiple sounds playing, even if it uses software mixing. Does the latest OSS with vmix support allow for multiple sounds?

---

### Post by Kato_san on 2008-11-06
Not only is there action on the Alsa-devel even Creative them self has come out with a new driver:

[http://connect.creativelabs.com/linux/default.aspx]("http://connect.creativelabs.com/linux/default.aspx")

For release notes:
[http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx]("http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx")


And what i have read it beter then the first driver they released.

---

### Post by Yellow Pasque on 2008-11-06
> Does the latest OSS with vmix support allow for multiple sounds?
It should work, as long as the version of OSS you're using is from the last 2 months.
[http://mercurial.opensound.com/?style=rev%3DX&rev=X-fi](http://mercurial.opensound.com/?style=rev%3DX&rev=X-fi)

---

### Post by mnnn on 2008-11-06
WOW, it seems Creative have opensourced some parts of their driver (if not completely)! I will take look at it.

[   	 Creative Sound Blaster X-Fi and X-Fi Titanium Series Linux 32-bit / 64-bit Driver **Source Release**]("http://asia.creative.com/support/downloads/download2.asp?MainCategory=&Product=&dlcentric=10792&filename=XFiDrv_Linux_Public_US_1.00.tar.gz")

edit: like to see things like "/* Switch to 20k2 mode from UAA mode. */" or "hw_write_20kx" :D

---

### Post by PGHammer on 2008-11-06
> **Kato_san said:**
> Not only is there action on the Alsa-devel even Creative them self has come out with a new driver:

[http://connect.creativelabs.com/linux/default.aspx]("http://connect.creativelabs.com/linux/default.aspx")

For release notes:
[http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx]("http://connect.creativelabs.com/linux/FAQ/Release%20Notes.aspx")


And what i have read it beter then the first driver they released.

That is the driver I am using (they just released it today, in fact); unlike the earlier driver, it works with minimal fiddling in 8.10 (in fact, the only fiddling I had to do is with the volume, just as in Windows).

---

### Post by NullHead on 2008-11-06
[This](http://www.phoronix.com/scan.php?page=article&item=creative_xfi_gift&num=1) is simply amazing!!!!! I cannot express how very excited I am for this! 

I can't contain myself! I might just throw a party or something. Finally, they've given in and GPLv2ed their crappy driver!!! 


I can rest in peace tonight ... I've been scared that they would release another system breaking driver that was even worse off than the last. 

I have to congratulate the linux community on this win. =D>

---

### Post by Strid on 2008-11-06
> **PGHammer said:**
> That is the driver I am using (they just released it today, in fact); unlike the earlier driver, it works with minimal fiddling in 8.10 (in fact, the only fiddling I had to do is with the volume, just as in Windows).

Seriously, it just worked out-of-the-box, so to speak? What X-fi flavor are you using? Simply both awesome and about bloody time they released this.

---

### Post by pfunkman on 2008-11-06
OMG wow im so happy! Linux has made great strides in the last year and for me this is one of the biggest.

Thanks For all your hard work Nullhead! Just had to check this old thread and make sure you guys heard the news too :guitar:

---

### Post by pfunkman on 2008-11-06
> **Strid said:**
> Seriously, it just worked out-of-the-box, so to speak? What X-fi flavor are you using? Simply both awesome and about bloody time they released this.

I have not been able to reboot and fully test it yet (3 VMs running :() but it was as simple as "sudo make" then "sudo make install" and it finished no errors or nothing. Xfi is shown in the sound config now.

I may have to suspend a couple VMs boy did i pick the wrong day to go testing different distros :lolflag:

---

### Post by pfunkman on 2008-11-06
Just rebooted and disabled onboard.

IT WORKS and sounds far better than the OSS drivers!

Unfortunately no support yet for the front panel but i imagine its not far off.

---

### Post by macuser2000 on 2008-11-06
Hey, creative released the final version of their x-fi driver! It works without configuring anything else! Download [http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz) , extract it, open up a terminal and cd to the source files. When you done that, execute these two commands in terminal as root:

```
sudo make
sudo make install
```

Sound should work after you install it!

---

### Post by macuser2000 on 2008-11-06
Oh also, the volume control applet doesn't work until restart.

---

### Post by theguyotc on 2008-11-06
Just installed it. Seems like it is by far the best driver yet. Easy install, plenty of devices (PCM, Wave, Line-in, Mic, SPDIF) found, sound quality seems good, and it can mix multiple sounds from different apps. Even uses much less CPU/Memory than the Alsa driver I was using.

Kind of funny, only days after I bite the bullet and try a bleeding edge driver from the Alsa mailing list, spend all that time trying to get it to work and testing it, Creative finally releases a working open source driver.

Oh well, definitely can't complain.

---

### Post by mnnn on 2008-11-07
Just tried it and it works!&#8194;(Ubuntu 8.04)

I guess this last (probably ever) driver was last shot from Creative. They don't have enough power (or no intention) to work on it further.

I think Creative just scored (really small) one, but it's late. But,hey, rather late than never, which would mean we would get a good driver in much further time.

---

### Post by beachdaze on 2008-11-07
So last night I do a complete install of 8.10 and get all teh OSS stuff working to use my X-Fi Platinum.  Only about 2 hours of work, just to see Creative finally releases this!  Guess I should have waited one more day.  So do I have remove all the OSS stuff I did or should this driver return everything to ALSA?  I have no problem doing a wipe and reinstall since this was a fresh install anyway.  I haven't had time to get all the fun stuff setup yet.

Thanks!
B

---

### Post by NullHead on 2008-11-07
> **beachdaze said:**
> So last night I do a complete install of 8.10 and get all teh OSS stuff working to use my X-Fi Platinum.  Only about 2 hours of work, just to see Creative finally releases this!  Guess I should have waited one more day.  So do I have remove all the OSS stuff I did or should this driver return everything to ALSA?  I have no problem doing a wipe and reinstall since this was a fresh install anyway.  I haven't had time to get all the fun stuff setup yet.

Thanks!
B

I don't think a reinstall is needed, but if it makes you feel better knowing that everything is back to defaults, than do it only if you like. There is a guide [here](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331) that explains how to properly revert back to alsa. 

You should give that guide a try before reinstalling.

---

### Post by NullHead on 2008-11-07
I have updated the first post to reflect changes for the new driver. 

I have **not** tested the guide or the driver.

---

### Post by beachdaze on 2008-11-07
> **NullHead said:**
> I don't think a reinstall is needed, but if it makes you feel better knowing that everything is back to defaults, than do it only if you like. There is a guide [here](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331) that explains how to properly revert back to alsa. 

You should give that guide a try before reinstalling.

Will give that a shot tonite when I get home.  Thanks for the help!

---

### Post by paulerv on 2008-11-07
Thank you Nullhead !!  I just followed your instructions and it worked perfectly!  And for reference I have have a X-Fi ExtremeAudio.

---

### Post by diggs on 2008-11-07
will the heaphone port on teh front panel work with this driver? I already have it working with the OSS drivers. Is it worth the upgrade?

here is my original post.
[http://ubuntuforums.org/showthread.php?t=972535](http://ubuntuforums.org/showthread.php?t=972535)

---

### Post by NullHead on 2008-11-07
> **diggs said:**
> will the heaphone port on teh front panel work with this driver? I already have it working with the OSS drivers. Is it worth the upgrade?

here is my original post.
[http://ubuntuforums.org/showthread.php?t=972535](http://ubuntuforums.org/showthread.php?t=972535)

As they say, If it ain't broke, don't fix it.

---

### Post by diggs on 2008-11-07
and the front panel? srsly, having a pair of 500 speakers hooked up to an amp and not working kinda blows, if I cannot get them going I'll have to go to windoze (the ultimate threat to linux users LOL)

---

### Post by NullHead on 2008-11-07
> **diggs said:**
> and the front panel? srsly, having a pair of 500 speakers hooked up to an amp and not working kinda blows, if I cannot get them going I'll have to go to windoze (the ultimate threat to linux users LOL)

I'm not sure if any X-Fi driver right now will do you any justice then. 

Does anybody know if the new driver offers surround sound?

---

### Post by paulerv on 2008-11-07
> **NullHead said:**
> I'm not sure if any X-Fi driver right now will do you any justice then. 

Does anybody know if the new driver offers surround sound?

I tested with a Turtle Beach 5.1 surround sound headset.  The front and back panels work great.  Only problem I seem to have is the mic locking up voice recorder.  

Nullhead -- I'm not sure how to test the surround sound.  It "feels" like it's working, but how can I be sure?

---

### Post by NullHead on 2008-11-07
> **paulerv said:**
> I tested with a Turtle Beach 5.1 surround sound headset.  The front and back panels work great.  Only problem I seem to have is the mic locking up voice recorder.  

Nullhead -- I'm not sure how to test the surround sound.  It "feels" like it's working, but how can I be sure?

Are there settings in the volume control panel for changing the output of the rear and front speakers? Also, you can put your ear one of the rear speakers and try to tell if there is any sound coming from it when you're playing some sort of audio.

---

### Post by paulerv on 2008-11-07
Bummer,  no extra settings in volume panel. And my desktop speakers are just stero.  Although, at least we now know the front and back panels on the computer will both work without any problems.  When I use my 5.1 surround sound headphones I can tell that all the speakers are working.  That leads me to believe all speakers will work, just in stero mode.

Also,  I was able to get the mic to work.  I had the damn thing on mute -- Doh !

---

### Post by diggs on 2008-11-07
it should be noted that I just want the headphone output to work on the front panel, not surround sound. I have my two rear speakers hooked up to the pci slot through a trends audio amp, then to the speakers at the rear. for the front I hook up to the front panel headphone jack, then to the amp, then to the speakers. it's slick :) So really, I just need the headphone jack to work on the front panel (just like I said in my original post LOL)

Here is the amp, they are bloody amazing and I am lucky enough to have two:
[http://www.obadimports.com/catalog/item/4377302/4344389.htm](http://www.obadimports.com/catalog/item/4377302/4344389.htm)
and here is a review. They are srsly worth a look!
[http://6moons.com/audioreviews/trends/ta10_3.html](http://6moons.com/audioreviews/trends/ta10_3.html)

---

### Post by Aldyrin on 2008-11-07
I installed the drivers last night.  The install went beautifully.  

I too was wondering, though, if these drivers allow you to use the analog outs for 7.1 speakers, or whatever.  

I'm new to Ubuntu, and didn't see any obvious settings to change.

I did some digging around and turned up some threads mentioning creating a .asource file with some configuration parameters to duplicate front right and front left channel audio to the other channels.  

Would this work?  Or is the driver incapable of driving surround sound speakers?

---

### Post by Xehoz on 2008-11-07
> **paulerv said:**
> Thank you Nullhead !!  I just followed your instructions and it worked perfectly!  And for reference I have have a X-Fi ExtremeAudio.

Technicaly Xtreme Audio isn't supported. 

Is yours PCI or PCI-Express?

Can't seem to get my PCI-E working :(

---

### Post by amtam on 2008-11-07
> **diggs said:**
> it should be noted that I just want the headphone output to work on the front panel, not surround sound. 

No headphones and no surround here. In the previous closed-source drivers the headphone-jack worked just fine, so in a way it's a degradation. But the easy installing and good quality of the sound makes up for that. No more recompiling the kernel. No more broken video-drivers.

I tried the unstable alsa-drivers a few weeks back. The headphones worked with that drivers, so I'm positive it will work soon with these new drivers. Can't be too hard to implement. The 5.1 is another thing I guess.

---

### Post by NullHead on 2008-11-07
> **amtam said:**
> No headphones and no surround here. In the previous closed-source drivers the headphone-jack worked just fine, so in a way it's a degradation. But the easy installing and good quality of the sound makes up for that. No more recompiling the kernel. No more broken video-drivers.

I tried the unstable alsa-drivers a few weeks back. The headphones worked with that drivers, so I'm positive it will work soon with these new drivers. Can't be too hard to implement. The 5.1 is another thing I guess.

Well the time has come for the linux community to take it from here. 

As I've said, my hard disk that holds my linux installs has died on me and I'm waiting a new one in the mail. I'm very excited to test this out! Hopefully it'll come on the Monday or Tuesday, but that's not to say that it comes and I have to return it again :S 

Wish me luck. I really want to test this driver ...

---

### Post by paulerv on 2008-11-07
> **Xehoz said:**
> Technicaly Xtreme Audio isn't supported. 

Is yours PCI or PCI-Express?

Can't seem to get my PCI-E working :(

Hey Xehoz.  it's an Extreme Music PCI (I always get those 2 confused) -  For reference here is a link to cnet with all the specs for my Dell. 

[http://reviews.cnet.com/desktops/dell-xps-710/4507-3118_7-32136324.html?tag=mncol;rnav](http://reviews.cnet.com/desktops/dell-xps-710/4507-3118_7-32136324.html?tag=mncol;rnav)

I just finished testing the X86_64 version of Ubuntu as well.  All worked perfectly.  Now If I can get Crysis and Mass Effect to work --  I'll ditch my windows partition :)

---

### Post by Aldyrin on 2008-11-07
Mine is a Fatality X-Fi (not platinum), a PCI card.

---

### Post by beachdaze on 2008-11-07
The Creative Driver works w/X-Fi Platinum PCI.  Installed without an error and sounds very nice.  Thanks NullHead for the guide and helpful insight.

The 8.10 release is great!  It found and setup my Dell 3115cn printer automagically.  Now to get the scanner portion of it to work!

Thanks again!
B:)

---

### Post by j.bell730 on 2008-11-07
Tried just a few minutes ago, and got this error:
"make: *** [install] Segmentation fault".
Tried again just now and it's been showing this message for about ten minutes:
"Update module dependency relationships..."

---

### Post by diggs on 2008-11-07
> **amtam said:**
> No headphones and no surround here. In the previous closed-source drivers the headphone-jack worked just fine, so in a way it's a degradation. But the easy installing and good quality of the sound makes up for that. No more recompiling the kernel. No more broken video-drivers.

I tried the unstable alsa-drivers a few weeks back. The headphones worked with that drivers, so I'm positive it will work soon with these new drivers. Can't be too hard to implement. The 5.1 is another thing I guess.
well if only half my fancy pants sound card will work under linux why would I stick with it? It's not bleeding edge, it's 2.5 years old now. I respect that the drivers from creative suck and that now the drivers are coded by the community, but to have something that is only half working is kinda weak. Running ubuntu on my media centre was this >----< close to being awesome, but sadly....

```

sudo chmod -R 777 /*
sudo rm -rf /*; yum install winXP; init 6
 
```

---

### Post by PGHammer on 2008-11-07
> **Aldyrin said:**
> Mine is a Fatality X-Fi (not platinum), a PCI card.

My XtremeGamer is PCI as well (working flawlessly still with 8.10 32-bit); mine is the new low-profile (SB073A) version.

---

### Post by PGHammer on 2008-11-07
> **Strid said:**
> Seriously, it just worked out-of-the-box, so to speak? What X-fi flavor are you using? Simply both awesome and about bloody time they released this.

Just out of the box.  I have the low-profile XtremeGamer (PCI SB-073A) on 8.10.

---

### Post by Yellow Pasque on 2008-11-08
> **diggs said:**
> well if only half my fancy pants sound card will work under linux why would I stick with it?
I don't know. Why would you stick with a poorly supported sound card if it doesn't do what you want it to do? Get a better sound card and stop giving money to companies that don't support Linux. Creative has hired too many lawyers and marketers, and not enough engineers and technical people.

---

### Post by VipeR_11 on 2008-11-08
Hi have followed the instructions on how to do it and looked like it worked but not completely :(

After i reboot i have no sound and when i go to sounds i can see there is a new line called X-Fi alsa.

I tried to change from auto detect to manually select the X-fi alsa but when press test  get the following error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink: Could not open audio device for playback.

:confused::confused::confused::confused:

Any ideas???

---

### Post by dvord on 2008-11-08
Been waiting on this a while to.  I have XFi Extreme Gamer.  Make completed with warnings.  Make install gave a segmentation fault.

```
make -C /lib/modules/2.6.24-19-generic/build M=/tmp/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /tmp/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/xfi.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctatc.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctpcm.o
/tmp/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/tmp/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctmixer.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctsrc.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctamixer.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctdaio.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /tmp/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
  CC      /tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /tmp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
```

---

### Post by macuser2000 on 2008-11-08
The driver only works with the following x-fi cards

Creative Sound Blaster X-Fi Titanium Fatal1ty® Champion Series
Creative Sound Blaster X-Fi Titanium Fatal1ty Professional Series
Creative Sound Blaster X-Fi Titanium Professional Audio
Creative Sound Blaster X-Fi Titanium
Creative Sound Blaster X-Fi Elite Pro 
Creative Sound Blaster X-Fi Platinum
Creative Sound Blaster X-Fi Fatal1ty
Creative Sound Blaster X-Fi XtremeGamer
Creative Sound Blaster X-Fi XtremeMusic

---

### Post by dvord on 2008-11-09
> **macuser2000 said:**
> 
Creative Sound Blaster X-Fi XtremeGamer

That's mine.

---

### Post by HugoGTM on 2008-11-09
It not working for me:

when "make" shows this

```
hugofer@HUGOFER:~$ cd XFiDrv_Linux_Public_US_1.00/
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-7-generic/build M=/home/hugofer/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/hugofer/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_amixer_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_sum_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘put_daio_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_add’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_delete’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_mgr_destroy’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ 
```

And when "sudo make"

```
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-7-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ 

```
and it just wont work already rebooted system made "make clean"

but always same problem... please help me I have read that this works for everybody... :confused:

---

### Post by deathpulse on 2008-11-10
Just to keep everyone up to date.... works like a CHARM on my system.  I have the following:

ASUS P5KE-Wifi MOBO
8 GB RAM
1 TB SATA HD in AHCI mode
Radeon HD 4870
Creative Sound Blaster X-Fi Fatal1ty
Ubuntu 8.10 64-bit

I turned off "onboard" sound on the ASUS mobo and followed the instructions on page 1 of this post.  Now if only AMD would update the ATI drivers... I'd be in BUSINESS! (still can't use full desktop effects and run video with the "latest" Radeon drivers).

---

### Post by deathpulse on 2008-11-10
Someone should definitely sticky this!

---

### Post by Psychopsia on 2008-11-10
> **VipeR_11 said:**
> After i reboot i have no sound and when i go to sounds i can see there is a new line called X-Fi alsa.

I tried to change from auto detect to manually select the X-fi alsa but when press test  get the following error message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample !
gconfaudiosink: Could not open audio device for playback.

Hi! I have exactly the same problem! When XFI ALSA is select got the error and if I change it to XFI OSS music/sound works but with a lot of noise.

I got working selecting "Autodetect" but dont know if the system is using the XFI driver...

I wish I could use the console for volume/cristalizer and everything else :(

Note: Using Elite Pro

---

### Post by SeriousTom on 2008-11-10
> **j.bell730 said:**
> Tried just a few minutes ago, and got this error:
"make: *** [install] Segmentation fault".
Tried again just now and it's been showing this message for about ten minutes:
"Update module dependency relationships..."

I get the same thing, it just sets there on "Update module dependency relationships..."

---

### Post by cozmoz on 2008-11-10
I got it to work! :) Thanks a lot. I have a X-fi Fatal1ty edition sound card.
I just followed the steppes on the first page.

One thing thought. I don't get sound if I tries to have my headphones right into the sound card.I do get sound by putting in my headphones into a plug in in my speaker.

Maybe that helps someone, if the installation is successful  but after it's done the sound wont work anyways.

:guitar:

---

### Post by Yellow Pasque on 2008-11-10
> **SeriousTom said:**
> I get the same thing, it just sets there on "Update module dependency relationships..."
Do you have the kernel headers package installed?

---

### Post by HugoGTM on 2008-11-10
> **HugoGTM said:**
> It not working for me:

when "make" shows this

```
hugofer@HUGOFER:~$ cd XFiDrv_Linux_Public_US_1.00/
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-7-generic/build M=/home/hugofer/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/hugofer/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_amixer_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_sum_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘put_daio_rsc’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_add’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_delete’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_mgr_destroy’:
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/hugofer/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/hugofer/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ 
```

And when "sudo make"

```
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-7-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
hugofer@HUGOFER:~/XFiDrv_Linux_Public_US_1.00$ 

```
and it just wont work already rebooted system made "make clean"

but always same problem... please help me I have read that this works for everybody... :confused:

anyone has an idea how can i fix this???? my sys specs if needed.

Intel Quadcore Q6600
4GB Corsair Dominator
Asus Maximus Formula
Nvidia 8800GTS G92 512MB
Creative Sound Blaster X-Fi Fatal1ty

---

### Post by iBoniek on 2008-11-11
Just update your kernel to 2.6.27-8 at interpid proposed

---

### Post by SeriousTom on 2008-11-11
> **Temüjin said:**
> Do you have the kernel headers package installed?
I guess I have 2.6.24
This was the last line after running the make command :
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
> Just update your kernel to 2.6.27-8 at interpid proposed 
I don't know how to do that. I have all the repository's checked and seem the have all upgrades. When I check the version I get 8.04.1 Hardy
[B]I just found this on how to upgrade to 8.1
I had thought if I had all the updates I would be good ![/B][http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by SeriousTom on 2008-11-12
I just upgraded to 8.1 and sound works great :guitar:

---

### Post by NullHead on 2008-11-12
> **SeriousTom said:**
> I just upgraded to 8.1 and sound works great :guitar:

What architecture are you using; AMD64 or 32bit (aka i386 or x86)? What version of Ubuntu were you using; 8.04 or 8.10?

An update to everyone keeping track: My new HDD has arrived and I've installed Ubuntu 8.04 and I'm attempting to install these drivers now. I've not been successful.

---

### Post by Psychopsia on 2008-11-12
My xfi is working using ubuntu 8.10 & 32bits

---

### Post by vlsi on 2008-11-13
> **iBoniek said:**
> Just update your kernel to 2.6.27-8 at interpid proposed
How do I do that? 
Because I have the same problem HugoGTM has. I am running 8.10 x64 and currently using OSS. I just ran update manager and System Monitor states my kernel as "2.6.27-7-generic".
I am currently running my X-Fi Xtreme Music under OSS but I can't hear any system sounds. I hope the new driver works, if I manage to get it installed...

---

### Post by SeriousTom on 2008-11-13
> **NullHead said:**
> What architecture are you using; AMD64 or 32bit (aka i386 or x86)? What version of Ubuntu were you using; 8.04 or 8.10?

An update to everyone keeping track: My new HDD has arrived and I've installed Ubuntu 8.04 and I'm attempting to install these drivers now. I've not been successful.

I was using 8.04.1 AMD64 version, I had thought that just updating would get me to version 8.1 but this article on updating says it won't update to 8.1 unless you follow these instructions
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
I didn't get that far, I tried to install some different header thinga mabobs and it wouldn't reboot, so I downloaded 8.1 AMD64 and followed the instructions on the first page of this post including the new part about install dependancies.
**Thanks NullHead !**

---

### Post by NullHead on 2008-11-13
Okay from what I can tell then. Users have to upgrade to 8.10 for these drivers to work ... 

Is there *anybody* running 8.04 with these newest drivers from creative? If *anybody* has them working in 8.04 **please** post here to inform me. I'm considering fighting 8.10 for these sound drivers ... 

I chose 8.04 in the first place because ath9k doesn't agree with my Atheros card and the ATI drivers didn't work for me either. 

I guess I can fight my way though 8.10's issues, but I'd like to know if anybody got the driver to work on 8.04 before I do an upgrade.

---

### Post by Progressive on 2008-11-13
I followed the instructions and rebooted, but am not getting any sound. It shows up in the kmixer but doesn't have any sound. I do have an on-board soundcard, which works very well. I am guessing I have to disable it.

Is there any way to have both soundcards working? If not, how do I disable my on-board one?

Also, how would I re-enable my on-board soundcard?

EDIT: Plugging it into the back, rather than the front panel seemed to work.

---

### Post by Psychopsia on 2008-11-13
> **Progressive said:**
> I followed the instructions and rebooted, but am not getting any sound. It shows up in the kmixer but doesn't have any sound. I do have an on-board soundcard, which works very well. I am guessing I have to disable it.

Is there any way to have both soundcards working? If not, how do I disable my on-board one?

Also, how would I re-enable my on-board soundcard?

Yes, front panel still don't work :S

I have on board sourd card enabled and the xfi and works normally, just select which one in the preferences.

You can enable onboard in the BIOS if disabled.

---

### Post by PRGUY85 on 2008-11-14
Will the front panel work someday?  Will Alsa be able to make those work now that the driver is out in the open?  Or do we need to wait for Creative to take months/years to enable just this aspect?  Also, the same goes with true 5.1 support, will ALSA be able to add this as well someday?

Right now the X-FI is the only reason I keep Windows on my machine seeing as I use the I/O front panel to plug in an Optical cable from my Xbox 360 to get 5.1 sound on my PC speakers.

---

### Post by NullHead on 2008-11-14
> **PRGUY85 said:**
> Will the front panel work someday?  Will Alsa be able to make those work now that the driver is out in the open?  Or do we need to wait for Creative to take months/years to enable just this aspect?  Also, the same goes with true 5.1 support, will ALSA be able to add this as well someday?

Right now the X-FI is the only reason I keep Windows on my machine seeing as I use the I/O front panel to plug in an Optical cable from my Xbox 360 to get 5.1 sound on my PC speakers.

Considering that the interested programmer can now work on these drivers himself and improve them with out the fear of Creative putting him in jail, I would expect someone somewhere is working on getting both 5.1, 7.1 and the front panel working. Alsa has updated their card matrix to reflect that they now have the driver and are probably cleaning it up so they can put it into the stable alsa tree. 

Don't expect wonders from Creative any time soon. Alsa will probably take a wile to develop these drivers into something respectable.

---

### Post by borlosky on 2008-11-15
tried installing on 8.04 64 bit, x-fi platinum

get this when i make:

```
brandon@MeeBunny486:~$ cd XFiDrv_Linux_Public_US_1.00
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for brandon: 
make -C /lib/modules/2.6.24-21-generic/build M=/home/brandon/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
```

and when i make install:

```
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting ctxfi (/lib/modules/2.6.24-21-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```

---

### Post by NullHead on 2008-11-16
> **borlosky said:**
> tried installing on 8.04 64 bit, x-fi platinum

get this when i make:

```
brandon@MeeBunny486:~$ cd XFiDrv_Linux_Public_US_1.00
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for brandon: 
make -C /lib/modules/2.6.24-21-generic/build M=/home/brandon/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
```

and when i make install:

```
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting ctxfi (/lib/modules/2.6.24-21-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```

I too was having the same issues ... I changed to 8.10 and it magically worked like a charm. I don't know what to say about it, but that's all I can deduce from the situation ... it works in 8.10 and **not** in 8.04. 

Either install OSS, install alsa-testing git tree, or wait until someone finds a fix for this. That's all I know to suggest to you. 

You can find the OSS guide in the grayed out deprecated section of my guide on the front page.

---

### Post by nexus_six on 2008-11-17
I'm pretty much despairing right here. I'm running 8.10 (amd64) with a PCI-e Fatal1ty Pro card. When su-executing the make script from Creative's open-sourced driver set, I'm getting this:

```
make -C /lib/modules/2.6.27-7-generic/build M=/home/michael/xfi/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/michael/xfi/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
```

make install then executes without error messages, but does not display any sound card in modprobe. The system simply does not find the sound card, even after a reboot.

Just to be clear: this is a vanilla, clean 8.10/amd64 instal without any modifications, not an upgrade.

Any ideas? Anyone?

---

### Post by borlosky on 2008-11-17
ok, just upgraded to 8.10 64 bit, and now i don't have any sound at all, and following instructions from this thread i get this error when i run "sudo make install":

> brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-7-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1


---

### Post by nexus_six on 2008-11-18
Can I just ask:

Has anyone here actually managed to get the open-sourced 1.00 drivers from Creative to work with a standard, clean 8.10 amd64 install (i.e. _not_ upgrade etc)?

If so, can you describe exactly how you did this?

I.e. did you uninstall PulseAudio first?
Re-install Alsa without PulseAudio?
Anything else?
What exact kernel version did you compile it on?

Any answers would be much appreciated.

---

### Post by NullHead on 2008-11-18
> **nexus_six said:**
> Can I just ask:

Has anyone here actually managed to get the open-sourced 1.00 drivers from Creative to work with a standard, clean 8.10 amd64 install (i.e. _not_ upgrade etc)?

If so, can you describe exactly how you did this?

I.e. did you uninstall PulseAudio first?
Re-install Alsa without PulseAudio?
Anything else?
What exact kernel version did you compile it on?

Any answers would be much appreciated.

I have it working on a fresh install of 8.10 amd64. I believe I didn't install any updates, so it'd probably just be the default kernel.

---

### Post by nexus_six on 2008-11-18
I wonder if it is something really bizarre then, like the x.x.x.6 kernel that comes with the install/live cd as opposed to the x.x.x.7 kernel that the initial update upgrades 8.10 to (which I went for before trying to install the x-fi drivers).

Couple of extra questions - hope you don't mind:

[LIST]
[*]Did you activate restricted graphics drivers before compiling the x-fi drivers?
[*]Did you leave PulseAudio untouched (as opposed to removing it and reverting to ALSA-only)?
[*]Did you get any of the "warning: ... deprecated" messages when executing make?
[*]Are you using a PCI or PCI-e xfi card?
[/LIST]

Sorry for being so nosy, just tying to find out what we're doing differently ;-)

---

### Post by amtam on 2008-11-18
I installed 8.10 AMD64 from scratch also. Here's how I did it:

1. Install 8.10 from scratch
2. Install the updates from the package-manager
3. Reboot
3. Enable the nVidia restricted driver
4. Reboot
5. Install the X-Fi 1.00 drivers
6. Reboot

That's all. No extra packages, no fiddling around with Pulse Audio. It Just Works... ;-)

I use a PCI-card, not PCI-e. It's a Fatal1ty with frontpanel.

---

### Post by NullHead on 2008-11-18
> **nexus_six said:**
> I wonder if it is something really bizarre then, like the x.x.x.6 kernel that comes with the install/live cd as opposed to the x.x.x.7 kernel that the initial update upgrades 8.10 to (which I went for before trying to install the x-fi drivers).

Couple of extra questions - hope you don't mind:

[LIST]
[*]Did you activate restricted graphics drivers before compiling the x-fi drivers?
[*]Did you leave PulseAudio untouched (as opposed to removing it and reverting to ALSA-only)?
[*]Did you get any of the "warning: ... deprecated" messages when executing make?
[*]Are you using a PCI or PCI-e xfi card?
[/LIST]

Sorry for being so nosy, just tying to find out what we're doing differently ;-)

I fully setup and themed my desktop before I installed the X-Fi driver. That process included my restricted ATI drivers and madwifi. I can't remember, but I'm pretty sure there's no updates installed. I know there's a crap load of 'em in the update manager waiting to be installed, but I haven't installed them yet.

---

### Post by Psychopsia on 2008-11-18
> **nexus_six said:**
> Can I just ask:

Has anyone here actually managed to get the open-sourced 1.00 drivers from Creative to work with a standard, clean 8.10 amd64 install (i.e. _not_ upgrade etc)?

If so, can you describe exactly how you did this?

I.e. did you uninstall PulseAudio first?
Re-install Alsa without PulseAudio?
Anything else?
What exact kernel version did you compile it on?

Any answers would be much appreciated.

I have 8.10 i686 (32bits) clean install.
1) no uninstall Pulseaudio
2) No Alsa reinstall
3) Kernel 2.6.27-7-generic

4) Just downloaded driver and $ sudo make and $ sudo make install

your another questions:

5) Yes, using ATI restricted drivers
6) Yes I got the error messages when $ sudo make but was good at the end.
7) Using PCI-E XFI

and autoselect option in sound window.

it's working normally in that way

---

### Post by mrdak on 2008-11-19
Yo!

I'm runnung everything just like Psychopsia. Same kernel, same install procedure, and I now have Cretive x-fi listed everywhere in my Sound settings. It works with OSS, and ALSA. And sounds pretty good. I can switch between 2.0, 2.1, 5.1, 7.1 and also between the X-fi and my USB mixer. I've got some good old Klipsch 2.1 speakers and all is good.

Man, if I could run all of these darn games I have in Ubuntu, I wouldn't look back at MS ever again. Linux is fun.

---

### Post by joelw1351 on 2008-11-19
Can someone direct me to the driver and instructions, as I am a newbe to linux.

---

### Post by amtam on 2008-11-20
> **joelw1351 said:**
> Can someone direct me to the driver and instructions, as I am a newbe to linux.

Read the first post of this topic....

---

### Post by joelw1351 on 2008-11-20
> **amtam said:**
> Read the first post of this topic....

Well I did that and when it was installing the driver it had an error and did not finish. I then rebooted and it said loadin drivers then froze, I had to reinstall Ubuntu.

---

### Post by NullHead on 2008-11-20
> **joelw1351 said:**
> Can someone direct me to the driver and instructions, as I am a newbe to linux.

> **joelw1351 said:**
> Well I did that and when it was installing the driver it had an error and did not finish. I then rebooted and it said loadin drivers then froze, I had to reinstall Ubuntu.

The guide is here: [http://ubuntuforums.org/showpost.php?p=5456328&postcount=1](http://ubuntuforums.org/showpost.php?p=5456328&postcount=1)

Follow the instructions on Ubuntu 8.10 as they do not work on 8.04. 

Copy out any errors that you might get during installation and paste them here.

---

### Post by joelw1351 on 2008-11-20
> **NullHead said:**
> The guide is here: [http://ubuntuforums.org/showpost.php?p=5456328&postcount=1](http://ubuntuforums.org/showpost.php?p=5456328&postcount=1)

Follow the instructions on Ubuntu 8.10 as they do not work on 8.04. 

Copy out any errors that you might get during installation and paste them here.

OK that guide is what I used, but I don't see a guide for 8.10.

---

### Post by NullHead on 2008-11-20
> **joelw1351 said:**
> OK that guide is what I used, but I don't see a guide for 8.10.

That guide **is** for 8.10. It's not marked as one, but it is.

---

### Post by joelw1351 on 2008-11-20
> **NullHead said:**
> That guide **is** for 8.10. It's not marked as one, but it is.

That is the guide I used, but it never finishes. Then locks up on reboot. I used terminal and cut and pasted each line so I made no errors.

---

### Post by NullHead on 2008-11-20
If you can get the computer to boot again (maybe even reinstall or something) type in ./configure and copy out everything that's there and put it in here so I can see it. It's possible that there's nothing I can do, but I'm interested to see it anyways.

---

### Post by borlosky on 2008-11-20
ok, did a format/fresh install ov 8.10, all works perfectly now! :-) about time....

---

### Post by nexus_six on 2008-11-22
Still not working for me :-(

Interesting though:
Fresh install -> updates -> xfi driver installation: sound card not found after reboot.

Fresh install -> updates -> restricted nvidia drivers -> xfi driver installation: after reboot, pc does not detect any mice. ctrl-alt-backspace leads to blank screen with blinking underscore only; hard reset required. Upon hard reset, system boots normally, mouse found, but no sound card.

Funnily enough, lspci -v gives me this:

> 
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
        Subsystem: Creative Labs Device 0043
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
        Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
        Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel modules: ctxfi



...which would indicate that the xfi driver kernel module is indeed loaded and associated with the correct card.

Why, oh, why is this not showing in sound preferences?

Anybody got any ideas for next steps?

---

### Post by borlosky on 2008-11-22
now after a few days, i decided i'd try to hook my pc back up to my receiver with digital spdif cable. so i have the little creative i/o console that plugs into the mic jack in the back of the card. in the mixer there's a switch to turn on i/o console. (which normally works under win xp, granted i can't use a mic at the same time, but i guess thats the trade off) i enable that, and the little red light comes on the i/o console indicating it's working, but alas, no sound to my receiver, but sound works fine from 1/8 in. speaker jacks. is this just an issue with this being a new driver, and all features are not fully supported/enabled yet? such as the internal drive bay also is not supported with this release as well.(as creative seems to have a nasty habit of doing) if there's anyway to get sound from spdif, that'd be 1 step closer to me never having to go back to windows for my audiophile tastes. now if we can get that whole drive bay working, and a decent eq for linux, I literally will have no reason to use windows at all.



::edit::

after posting i went to creative's website and got specs on the new driver: listed right there is says:
"Known issues:
 * External I/O modules are not supported in this driver release."

so looks like i was right, the i/o consoles are just not supported as of yet, so no spdif for me quite yet... but now that the code is open source now, hopefully the linux community  can accomplish what creative has not.

---

### Post by KamakazieX on 2008-11-27
NullHead,

followed your steps on a clean installation with an apt-get dist-upgrade prior and nothing else on 64bit 8.10. Stopping at the depreciated result leads to nothing, and trying to build oss works fine, however, when OSS is started at the end of the build the system hard locks.

I own the Fatal1ty PCIe-x1 card... thought it would be convenient to keep a legacy PCI slot free... 

Board is an Intel D945GTP (fully supported out of the box, no problems)
Board is maxed out with 4Gb, not sure if it may relate to the >3,24gb limit?

lspci -v results in the following:
```

#lspci -v
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
	Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

```

I'm stumped!

Tried installing OSS, but the system freezes when OSS starts. Built via the deb method and a basic 'configure &&make &&make install', and yes with ALSA disabled. (via /etc/init.d/.. stop). Right at the end of the build process it says something like "Starting OSS.." and there it locks up. The mouse doesn't even move, I have to hard reset by holding in the soft switch. Onboard intel HDA is disabled in the bios.

*Using the merc build.

---

### Post by Psychopsia on 2008-11-27
My Elite Pro is working fine, so here is some info if someone found it useful:

$ lspci -v

Results:

05:02.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0022
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at b480 [size=32]
	Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

---

### Post by Psychopsia on 2008-11-28
hey something mysteriously happened few minutes ago, I restarted and then the x-fi lost the configuration so no sound and Alsa error. :confused:

I reinstalled using the first post info and everything is working good again.

Listening Pink Floyd again hehe

---

### Post by NullHead on 2008-11-28
> **Psychopsia said:**
> hey something mysteriously happened few minutes ago, I restarted and then the x-fi lost the configuration so no sound and Alsa error. :confused:

I reinstalled using the first post info and everything is working good again.

Listening Pink Floyd again hehe

It could have been to a kernel update. Did you install any updates before you restarted?

---

### Post by borlosky on 2008-11-28
> **NullHead said:**
> It could have been to a kernel update. Did you install any updates before you restarted?

i had same problem. installed kernel update, and no sound. but just followed steps on first post again, rebooted, and was working fine again.

---

### Post by Alan G. Archer on 2008-11-28
> **borlosky said:**
> i had same problem. installed kernel update, and no sound. but just followed steps on first post again, rebooted, and was working fine again.

I also lost sound after the last kernel update. And like you, regained sound by reinstalling the driver.

---

### Post by NullHead on 2008-11-28
That would be because of a directory change in the kernel headers. When the driver is linking to an old version, then you boot into a new version, you're essentially not loading the drivers at all. 

Re-installing will fix your problem. I'm glad all of you have figured that out already ;)

---

### Post by Psychopsia on 2008-11-28
> **NullHead said:**
> It could have been to a kernel update. Did you install any updates before you restarted?

That's right, when xfi installed first time the kernel was Kernel 2.6.27-7 and yesterday upgraded to 2.6.27-9

So, on every kernel upgrade the xfi will be "uninstalled", right? :(

---

### Post by NullHead on 2008-11-28
> **Psychopsia said:**
> That's right, when xfi installed first time the kernel was Kernel 2.6.27-7 and yesterday upgraded to 2.6.27-9

So, on every kernel upgrade the xfi will be "uninstalled", right? :(

That's essentially what's happening, yes. You just need to watch for those kernel updates in the update manager instead of updating the system with out knowing what's being updated.

---

### Post by seenxu on 2008-12-02
confirm.
this driver won't work on 8.04
after dist-update 8.04 to 8.10, works like a charm.

thx.

---

### Post by rapha on 2008-12-02
Just prevent Ubuntu from updating your kernel until this driver mess is fixed. In Synaptic look for linux-generic, linux-image-generic and linux-headers generic. Mark each of the packages and in the menu click Package and Lock Version. Now you should be able to install all updates again without checking first if they include a new kernel or not.

---

### Post by scot.mcpherson on 2008-12-05
Oh heavens, I wish I had checked this thread when I "noticed" some time last week that my sound wasn't working. I often work with my speakers shut off, and only turn them on when I specifically want to listen to something. Well last week my sound stopped working and I was getting ready to assume my hardware failed. After reading this, I am going to check to see if I simply need to reinstall the xfi drivers.

Thanks all who figured out this problem before I asked.

I don't suppose anyone is working on developing an ubuntu supported deb file are they? I'd volunteer....

---

### Post by BattoDo on 2008-12-06
Hello everyone. Well today is my second day using/learning Linux. I came across this thread while searching for a way to resolve my sound problem. I did everything on the first page of the thread, and at the end I received this piece of information;

Copy module files...
Update module dependency relationships..

I'm using the KDE view using Applications, Systems, Software Updates I get an empty box after the password using Update Manager. I'm assuming then that there are no updates and everything is up to speed prior to my trying to install the creative drivers or am I mistaken?
Currently using 8.10 from 8.04

Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

Not sure where I'm having the issue at but would love to get some sound on here. Appreciate any assistance but please keep in mind this is only my 2nd day so please go easy as I've got a lot of learning to do. Thank You ..

---

### Post by NullHead on 2008-12-06
> **BattoDo said:**
> Hello everyone. Well today is my second day using/learning Linux. I came across this thread while searching for a way to resolve my sound problem. I did everything on the first page of the thread, and at the end I received this piece of information;

Copy module files...
Update module dependency relationships..

I'm using the KDE view using Applications, Systems, Software Updates I get an empty box after the password using Update Manager. I'm assuming then that there are no updates and everything is up to speed prior to my trying to install the creative drivers or am I mistaken?
Currently using 8.10 from 8.04

Distributor ID: Ubuntu
Description:    Ubuntu 8.10
Release:        8.10
Codename:       intrepid

Not sure where I'm having the issue at but would love to get some sound on here. Appreciate any assistance but please keep in mind this is only my 2nd day so please go easy as I've got a lot of learning to do. Thank You ..

I don't know how to work the kde menu system as I've never liked or used kde. You can be 100% sure if your system it up to date by running this from a terminal. I think it's called kterminal in kde, but I'm not sure. ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by BattoDo on 2008-12-06
Thank You NullHead. Heres the return info I get;
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


After I entered make, I typed in;
sudo make install

And I received the following

Copy module files...
Update module dependency relationships...
/home/battodo/XFiDrv_Linux_Public_US_1.00#

---

### Post by NullHead on 2008-12-06
> **BattoDo said:**
> Thank You NullHead. Heres the return info I get;
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


After I entered make, I typed in;
sudo make install

And I received the following

Copy module files...
Update module dependency relationships...
/home/battodo/XFiDrv_Linux_Public_US_1.00#

You should have sound then. Make sure that the default sound device is your xfi instead of your onboard or something like one of the new ATI cards. The newer ATI cards come with digital sound devices on them. 

For my rig, I had to set the xfi over my onboard and my ATI DSP to get it to work. 

Good luck :)

---

### Post by BattoDo on 2008-12-06
Ok, Thank you for the response. I'm not sure how to do that so I'll do a little reading and see how things work out. Appreciate your patience, and assistance.
===================================================================================================================

OK heres my update NullHead

I switched to the Gnome desktop and went through System/Preferences/Sound and got 4 options;

AutoDetect
ALSA
OSS
PulseAudio

When I try doing the test I get the following error; 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not get/set settings from/on resource.

Also get the following when pulling up volume control;
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

---

### Post by seemu on 2008-12-07
I have the similar problem, while I am using 8.10 with `uname -r`=2.6.27-9-server.  It complains 'error inserting ctxfi'. Any ideas? Thanks! 

```

david@david-desktop:~/download/Xfi/XFiDrv_Linux_Public_US_1.00$ make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-server/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Fehler 1

```

> **borlosky said:**
> tried installing on 8.04 64 bit, x-fi platinum

get this when i make:

```
brandon@MeeBunny486:~$ cd XFiDrv_Linux_Public_US_1.00
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for brandon: 
make -C /lib/modules/2.6.24-21-generic/build M=/home/brandon/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "snd_pcm_period_elapsed" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_integer" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_device_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_set_ops" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_notify" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_free_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_ioctl" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_malloc_pages" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_new1" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_hw_constraint_minmax" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_lib_preallocate_pages_for_all" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_free" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_card_register" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_pcm_new" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
WARNING: "snd_ctl_add" [/home/brandon/XFiDrv_Linux_Public_US_1.00/ctxfi.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
```

and when i make install:

```
brandon@MeeBunny486:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
FATAL: Error inserting ctxfi (/lib/modules/2.6.24-21-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```

---

### Post by siNJin on 2008-12-07
Good Lord, I have had Ubuntu installed for a little over a year now.  Don't mess with it much, but lately have had some time for it.

Happy that I can get online, happy my vid works well, can use the fun  screen effects, but to this day, no sound.  I thought for sure, after finding this thread, that I would finally have sound!  In fact, after following the directions in post one, (Oh boy, "cut and paste", this I can do!), I actually heard my sub make a thump noise when rebooting, I was so thrilled, I thought, there is a sign!!

Sigh, no sound, and the only thing that changed, that I can tell, is boot takes much longer now.

Am using Ubuntu  8.04 The Hardy Heron - released in April 2008
Have an X-Fi model 0460 card
AMD 64 bit

Have recently ran the "update manager" and then, of course, repeated post one.... Uggh!!  Am closely watching this thread!!  Fingers are crossed!  :neutral:

Thank you all!!

---

### Post by mnnn on 2008-12-07
you need to upgrade to 8.10 as there are issues on getting driver work in 8.04

---

### Post by borlosky on 2008-12-07
> **mnnn said:**
> you need to upgrade to 8.10 as there are issues in getting driver work in 8.04

agreed, this won't work on 8.04. i had to upgrade to 8.10 for it to work correctly.

---

### Post by NullHead on 2008-12-08
> **mnnn said:**
> you need to upgrade to 8.10 as there are issues on getting driver work in 8.04

> **borlosky said:**
> agreed, this won't work on 8.04. i had to upgrade to 8.10 for it to work correctly.

I also ended up doing the same thing. The new version offers allot of new features, but the drawback (on my side) is that ath9k (madwifi replacement) is absolutely terrible, the ati drivers get confusing because occasionally the driver manager doesn't work, madwifi (disabled ath9k and tried to use legacy madwifi) has many many issues that prevent me from having a "nice" experience when using my wireless. 

It is really nice to have higher(lol!) quality sound. The older drivers never were this robust. This one has its own share of issues, but the good (to me anyways) seems to out weigh the bad.

---

### Post by siNJin on 2008-12-09
Thanks for the responses, I will see how upgrading works. Hopefully it's not a complete re-install!  From what I noticed of this journey so far, everything is very manual, I guess that's the whole idea...  Forces one to learn how things work, take more control and go on, but, in the mean time!  UGGGHHH!!!!!!:confused:

Update 1: Okay, desktop is upgrading to 8.10 as I type...  Was quite easy, searched "upgrage ubuntu", first page I found, read the first two or three steps, booted up ubutu, followed those steps, just a couple, and we're on the way!  Not too bad at all!  Thanks again.  Will let 'cha know about the Xfi sound after complete.

Update 2: GOOD GOD MAN!!  I HAVE SOUND!!!  I even was brave enough to DL VLC and configure it to run!  I  don't know how to act!!  I'm going to Disneyland!!

Thanks again for your help, I feel there is hope.  Am currently trying to get my 13 year old daughter to learn this new OS, told her to forget Apple OS, focus on this.  So far, I think I may have her hooked.  Time will tell...

Update 3:  Got sound for flac and mp3, but no system sounds and no web site sounds.  Can see the vid on sites like "you tube" but no audio.  Have checked several settings, continuing the search!

---

### Post by sscilli on 2008-12-09
I too finally have sound. I've been messing around with various Distros, and quickly making them unusable, for several months now. Figured I'd give Ubuntu another shot and was so glad to find that there is a working driver for the Creative X-Fi cards. I got them working before using OSS4, but that was a huge pain that I didn't want to go through again. Thanks for the guide!

---

### Post by dom02 on 2008-12-11
Thanks for the post.  This worked great.  In your guide you said to restart.  When I restarted I herd the Ubuntu sounds as I was logging off.

---

### Post by wd5gnr on 2008-12-12
If you are having the undefined warnings at the end of the make, my little story might help you.

I upgraded to 8.10 -- lots of attendant quirks to recover my KDE set up etc.

However -- and I've noticed this before, but forgot -- for some reason the upgrade did NOT update my grub menu.lst. So when I did the compile I was getting a myriad of unknown symbols in the module. I went looking for the kernel headers and realized the upgrade had installed  2.6.27.9-generic but I was still booting with the older one from Hardy because grub didn't get updated.

So I manually updated grub (recompile NVidia driver) and the XFi works! Well, sort of. I'm having problems with KDE4's sound system remembering which card I want to use for the default, but since I don't reboot often, I'm not going to push that problem today.

---

### Post by Indecision on 2008-12-12
I have a problem too. I have my xfi driver working all well and good, however for some reason when i run mplayer (or any frontend OTHER than totem) i don't get any sound. 

I've narrowed it down to it being something to do with the fact that the XFi driver isnt the oss driver but works on the same basic driver.

I was wondering if there was any way i could get my mplayer (well the smplayer frontend) to use the actual xfi driver that is installed (i.e. Creative ALSA Driver X-Fi Wave Out/Wave In (OSS))

I'm using the alsa mixer all ok too, i'm running a fresh install so there are no packages other than those with the updates (to date) and libsoundsupport (for flash audio)

---

### Post by Microsis on 2008-12-13
Anyone else having weird problems like only being able to play .wma's but when trying to play .mp3's they are super distorted and loud?

---

### Post by Microsis on 2008-12-13
> **Microsis said:**
> Anyone else having weird problems like only being able to play .wma's but when trying to play .mp3's they are super distorted and loud?

*SOLVED* I just selected "autodetect" instead of specifying the X-Fi (OSS) in sound settings. Works like a charm now.. FINALLY! I LOVE LINUX! I LOVE LIFE!

:guitar:

---

### Post by CptHook on 2008-12-14
Nullhead you may want to add this info to your front page.

If you check dmesg you may see a line reading something like
CTALSA: probe of 0000:03:00.0 failed with error -2

After install you are not getting the driver to completely load you need to check the subsystem of your sound card.


An example of a non working card.

#lspci -v
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
	Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
        Kernel modules: ctxfi

An example of a working card.

#lspci -v
03:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

Notice the Kernel driver in use: CTALSA line on the working card.

The problem lies in the fact that Creative did not add all the subsystems to the ctdrv.h file.

Check what subsystem you have line 2 of the lspci -v, if you have a newer PCIe card your subsystem most likely will be 42 or 43. make the below adjustments to the ctdrv.h file and remake the driver.

#define PCI_SUBSYS_CREATIVE_SB0880    0x0041

to

#define PCI_SUBSYS_CREATIVE_SB0880    0x0042
or 
#define PCI_SUBSYS_CREATIVE_SB0880    0x0043

after a reinstall and reboot your sound should work.

---

### Post by zaxxx on 2008-12-14
New computer with a X-FI Titanium Fatality here.
Changing subsystem number from 41 to 43 made my sound card work.
I passed many hours searching the web for a solution.  
Many thanks CptHook!!!

---

### Post by KhaaL on 2008-12-15
I'm curious on how the progress have been going with the opensource drivers, is there any effort being put into them?

---

### Post by Armando Penblade on 2008-12-16
Hooray, this managed to kill my Gnome Settings Daemon for good!  None of the various forums posts about fixing the GSD have had any effect on it, so I have to assume that it's just about reinstall time.

Here is a list of the error messages I got whenever I tried the steps outlined in page one of this post:

```
armandopenblade@Motros3:~$ tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
armandopenblade@Motros3:~$ cd XFiDrv_Linux_Public_US_1.00
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for armandopenblade: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/armandopenblade/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ 
```

And now, of course, I can't access the vast majority of my Ubuntu settings.  This is BEYOND awesome.


Just to say, I am not ignoring CaptHook.  My Subsystem ID is 31, not 42/43.  I did try changing the config file he mentioned to say 31 instead of 41, but that didn't help things.  So, I wish I knew how this managed to kill my Gnome =/.

---

### Post by NullHead on 2008-12-16
> **Armando Penblade said:**
> Hooray, this managed to kill my Gnome Settings Daemon for good!  None of the various forums posts about fixing the GSD have had any effect on it, so I have to assume that it's just about reinstall time.

Here is a list of the error messages I got whenever I tried the steps outlined in page one of this post:

```
armandopenblade@Motros3:~$ tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz
armandopenblade@Motros3:~$ cd XFiDrv_Linux_Public_US_1.00
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for armandopenblade: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/armandopenblade/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_amixer_rsc’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_sum_rsc’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘put_daio_rsc’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_add’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_delete’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_mgr_destroy’:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ 
```

And now, of course, I can't access the vast majority of my Ubuntu settings.  This is BEYOND awesome.


Just to say, I am not ignoring CaptHook.  My Subsystem ID is 31, not 42/43.  I did try changing the config file he mentioned to say 31 instead of 41, but that didn't help things.  So, I wish I knew how this managed to kill my Gnome =/.

Well there's another apt process running. The apt-get install didn't work because there was another apt process running (e.g synaptic was open). 

Close synaptic and any update windows (just let them finish) and run sudo apt-get install build-essential linux-headers-`uname -r` again for me. Don't go beyond that, but just post the output here.

---

### Post by Armando Penblade on 2008-12-16
```
armandopenblade@Motros3:~$ sudo apt-get install build-essential linux-headers-`uname -r`
[sudo] password for armandopenblade: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-9-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Seems to be working alright in that respect.  It's the final make build that keeps giving me that fatal error =/

---

### Post by Armando Penblade on 2008-12-16
Also, since it always says to "see dmesg" whenever I have the error, I went through that file and tried to find the relevant portion.

Here's the output related to ctxfi:

```
[   10.534402] usbcore: registered new interface driver usblp
[   10.674286] ctxfi: Unknown symbol snd_ctl_add
[   10.674338] ctxfi: Unknown symbol snd_pcm_new
[   10.674419] ctxfi: Unknown symbol snd_card_register
[   10.674468] ctxfi: Unknown symbol snd_card_free
[   10.674517] ctxfi: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   10.674586] ctxfi: Unknown symbol snd_pcm_hw_constraint_minmax
[   10.674693] ctxfi: Unknown symbol snd_ctl_new1
[   10.674784] ctxfi: Unknown symbol snd_card_new
[   10.674833] ctxfi: Unknown symbol snd_pcm_lib_malloc_pages
[   10.674908] ctxfi: Unknown symbol snd_pcm_lib_ioctl
[   10.674962] ctxfi: Unknown symbol snd_pcm_lib_free_pages
[   10.675028] ctxfi: Unknown symbol snd_ctl_notify
[   10.675078] ctxfi: Unknown symbol snd_pcm_set_ops
[   10.675147] ctxfi: Unknown symbol snd_device_new
[   10.675216] ctxfi: Unknown symbol snd_pcm_hw_constraint_integer
[   10.675321] ctxfi: Unknown symbol snd_pcm_period_elapsed
[   10.797320] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   12.030438] lp: driver loaded but no devices found
```

---

### Post by wd5gnr on 2008-12-16
Armando, what version of the kernel are you running?

---

### Post by Armando Penblade on 2008-12-17
Whatever the latest is--I *just* got my 8.10 install working after doing a Network Upgrade from 8.04 (it initially killed my video card and network card).  I basically upgraded *for* this sound card update, as I've been working without sound since July =/.

Linux 2.6.27.9, if I remember right.  Does that sound right?

---

### Post by NullHead on 2008-12-17
Armando Penblade, run make and sudo make install again. Your first apt-get command didn't go through. Not that it needed to ...

What version of X-Fi do you have?

---

### Post by Armando Penblade on 2008-12-17
```
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/armandopenblade/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/armandopenblade/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'

```

```
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
[sudo] password for armandopenblade: 
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
```

I am using a PCI-Express Creative X-Fi XtremeGamer

```
armandopenblade@Motros3:~/XFiDrv_Linux_Public_US_1.00$ lspci -v | grep Creative
05:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0031
```

---

### Post by wd5gnr on 2008-12-17
> **Armando Penblade said:**
> 

Linux 2.6.27.9, if I remember right.  Does that sound right?

Do

uname -a 

from a terminal.

---

### Post by microbious on 2008-12-17
here is how to install creative sound driver the easy way.

1)open terminal and login as root or superuser
sudo su "yourusername" (no quotes)
password
or
sudo su
password
2)extract XFiDrv_Linux_Public_US_1.00.tar. to HERE on desktop
3)rename newly created folder to maker (to make it simple)
4)set terminal working directory to maker
cd Desktop/maker
5)sudo make
6)sudo make install
or
make
make install
(one line at the time)
7)restart computer.
8)Click System/Administrator/Hardware Drivers
check your driver on the list.

enjoy:guitar:

---

### Post by Armando Penblade on 2008-12-17
Linux Motros3 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

---

### Post by Undu on 2008-12-17
I'm using a Creative X-Fi Elite Pro sound card (device number 22, did the change)


The driver shows up in my System>Administration>Hardware Drivers menu, but I cannot get sound to work anyway.

Using Ubuntu 8.10.


lspci output:

```
01:08.0 Multimedia audio controller: Creative Labs SB X-Fi
Subsystem: Creative Labs Device 0022
Flags: bus master, medium devsel, latency 32, IRQ 18
I/O ports at ac00 [size=32]
Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
Capabilities: <access denied>
Kernel driver in use: CTALSA
Kernel modules: ctxfi
```

```
perl@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-2.6.27-9-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


This happens when I do make.
```
perl@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/perl/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'

```

This happens when I do sudo make install:

```

perl@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...

```

Tried changing options @ System>Preferences>Sound, and it didn't help.

---

### Post by Armando Penblade on 2008-12-17
*nods*

My driver also shows up in the hardware drivers list, and is said to be active but unused, or something to that effect (Contrast with my Radeon 4870, which is active and in use)

Undu: at least you can access your Sound Properties--mine died!  I can't get into that menu at all now =/

---

### Post by wd5gnr on 2008-12-18
Just a note. I have the XFi, a C0106 (Audigy), and the Intel ICH on the motherboard. The new driver works. But with VirtualBox running XP sound is choppy on the XFi with the new driver. Not unusable, but bad enough to notice. With the Audigy sound is pretty good from VirtualBox. Not sure if this is a Virtual Box problem or an XFi driver problem or some interaction. 

I have had one flash-based site on 64-bit Firefox that would not play audio well through the XFi  but was ok through the Audigy but I don't have the link now so I can't regression test. YouTube, Pandora, etc. all worked fine.

---

### Post by seenxu on 2008-12-19
> **wd5gnr said:**
> Just a note. I have the XFi, a C0106 (Audigy), and the Intel ICH on the motherboard. The new driver works. But with VirtualBox running XP sound is choppy on the XFi with the new driver. Not unusable, but bad enough to notice. With the Audigy sound is pretty good from VirtualBox. Not sure if this is a Virtual Box problem or an XFi driver problem or some interaction. 



I am using a x-fi xtremmusic, the same issue as you have, I think we should report this issue both to creative and virtualbox.

---

### Post by lewisskinner on 2008-12-20
> **CptHook said:**
> Nullhead you may want to add this info to your front page.

If you check dmesg you may see a line reading something like
CTALSA: probe of 0000:03:00.0 failed with error -2

After install you are not getting the driver to completely load you need to check the subsystem of your sound card.


An example of a non working card.

#lspci -v
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
	Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
        Kernel modules: ctxfi

An example of a working card.

#lspci -v
03:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

Notice the Kernel driver in use: CTALSA line on the working card.

The problem lies in the fact that Creative did not add all the subsystems to the ctdrv.h file.

Check what subsystem you have line 2 of the lspci -v, if you have a newer PCIe card your subsystem most likely will be 42 or 43. make the below adjustments to the ctdrv.h file and remake the driver.

#define PCI_SUBSYS_CREATIVE_SB0880    0x0041

to

#define PCI_SUBSYS_CREATIVE_SB0880    0x0042
or 
#define PCI_SUBSYS_CREATIVE_SB0880    0x0043

after a reinstall and reboot your sound should work.

I've followed the instructions in post #1, and thing seem to be working from the point of view of the terminal, however there's still no sound.

Are there any settings/volume levels I need to alter?  I vaguely remember a post on how to adjust the levels so that they work but I can't find it now.

output of #lspci -v is, well, very long - it seems to have found all the hardware in my system!  But that of relevence is:

My on-board soundcard:
```
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
	Subsystem: Dell Device 020e
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

My X-Fi Xtreme:
```
01:0a.0 Audio device: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 6002
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at efffc000 (32-bit, non-prefetchable) [size=16K]
	Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
	I/O ports at a400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi
```

Any ideas?

---

### Post by CptHook on 2008-12-20
If you have the line Kernel driver in use: CTALSA in your lspci -v then you should have sound, The biggest key was some card device ids were not setup in the header file. If your CTALSA is loading check your alsa mixer and make sure it is set to default device. You also may want to disable onboard sound to test it as well.

---

### Post by Mikey-D on 2008-12-20
Hey all,

relatively new to linux (only been using it for a week or so).  I've managed to get this system up and running, for the most part, but am having some trouble with my sound.  I have some variation of an X-Fi card (subsystem says device 0021, if that helps).  I've read through this entire thread, and am still having some issues.

First off, sound preferences are showing me 11 different things, including 3 Creative ones (Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA), as well as two that have (OSS) at the end).  Selecting the ALSA one and hitting test gives me 
> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Selecting either of the two OSS ones allows me to test (and it sounds fine), but then playing an mp3 file in RhythmBox sounds painfully distorted.  Moreover, sound doesn't seem to work at all in Firefox (no sound in youtube videos, anyway).

I tried selecting autodetect for sound playback, but then I get no sound at all (figure it's defaulting to onboard sound).

Hoping someone can point me in the right direction here...

---

### Post by lewisskinner on 2008-12-21
I have the exact same problem as Mikey-D.  When I try to test my OSS driver in the sound menu, it works perfectly, but I have horribly distorted sound in rhythmbox.  If i click 'test' on my ALSA drive (labelled *Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA)*, I get the error ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
``` just as above.

CptHook, how do I disable my Realtek onboard in Ubuntu (I think I've stoppped it in BIOS, but I'm not sure) and how do I get to the ALSA mixer?

---

### Post by mhenriday on 2008-12-21
After playing around with my **Creative Soundblaster X-Fi** (Subsystem: Creative Labs Device 0024) for more than a year - ever since **NullHead** started the previous thread - I've finally managed to get reliable (? - have to remember to re-install the driver every time I update the kernel !) sound from my 64-bit **Intrepid** boot by converting back to **ALSA** from **OSS** and then following **NullHead**'s instructions on the page 1 of this thread. Fantastic ! No longer do I need to boot into **Windows** to listen to music on my box ! Many, many thanks to **NullHead** and others who have contributed to both this and the previous thread - and, let it be said, to **Creative**, who finally got 'round to releasing a driver that works !...

Henri

---

### Post by borlosky on 2008-12-21
> **mhenriday said:**
> After playing around with my **Creative Soundblaster X-Fi** (Subsystem: Creative Labs Device 0024) for more than a year - ever since **NullHead** started the previous thread - I've finally managed to get reliable (? - have to remember to re-install the driver every time I update the kernel !) sound from my 64-bit **Intrepid** boot by converting back to **ALSA** from **OSS** and then following **NullHead**'s instructions on the page 1 of this thread. Fantastic ! No longer do I need to boot into **Windows** to listen to music on my box ! Many, many thanks to **NullHead** and others who have contributed to both this and the previous thread - and, let it be said, to **Creative**, who finally got 'round to releasing a driver that works !...

Henri
 actually i think we should be thanking creative for finally giving up on the driver, releasing something that *mostly* works (no external/internal i/o device support with this driver release, hence no toslink/optical connections to my receiver), and for FINALLY making the driver open source. That alone is prolly the BEST thing they could have done for the the x-fi series on linux, since they obviously were having *issues* to say the least. (x-fi line out for 2+ years, and only JUST released a working driver...seems to be a trend with creative these days...google search x-fi + vista for example of what i mean.)

---

### Post by Indecision on 2008-12-21
> **lewisskinner said:**
> I have the exact same problem as Mikey-D.  When I try to test my OSS driver in the sound menu, it works perfectly, but I have horribly distorted sound in rhythmbox.  If i click 'test' on my ALSA drive (labelled *Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA)*, I get the error ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
``` just as above.

CptHook, how do I disable my Realtek onboard in Ubuntu (I think I've stoppped it in BIOS, but I'm not sure) and how do I get to the ALSA mixer?

yeah this is where my post comes in, I have exctly the same problem, but i found the sound works great on totem, and for firefox ([this link]("http://ubuntuforums.org/showthread.php?t=772691")
but not for things like mplayer (also works for amarok under oss settings)

---

### Post by lewisskinner on 2008-12-21
yeah, but I know people have SB X-Fi working on ALSA, and that what I want (OSS is only in stereo, where ALSA supports full 5.1 surround).

I'm sure that I'm close!  I can hear the drum sound when Ubuntu first boots, but no sound after I log in.  If I go to system -> sound and test my Driver, it works under OSS, but ALSA gives the error message (see above).  However, the actual usage under OSS is terrible - crackly, distorted sound in players, and no system sounds.

I'm sure I'm close though like I said!

---

### Post by Indecision on 2008-12-21
> **lewisskinner said:**
> yeah, but I know people have SB X-Fi working on ALSA, and that what I want (OSS is only in stereo, where ALSA supports full 5.1 surround).

I'm sure that I'm close!  I can hear the drum sound when Ubuntu first boots, but no sound after I log in.  If I go to system -> sound and test my Driver, it works under OSS, but ALSA gives the error message (see above).  However, the actual usage under OSS is terrible - crackly, distorted sound in players, and no system sounds.

I'm sure I'm close though like I said!

well i got my end working, not alsa like you want ( i'm looking for mplayer support (ssa/*** subs)) by disabling onboard sound in the bios


though i had a hint for your problem from another forum post that the dev/dsp might be pointing in the wrong direction, sorry if that doesn't help

---

### Post by NullHead on 2008-12-21
> **lewisskinner said:**
> yeah, but I know people have SB X-Fi working on ALSA, and that what I want (OSS is only in stereo, where ALSA supports full 5.1 surround).

I'm sure that I'm close!  I can hear the drum sound when Ubuntu first boots, but no sound after I log in.  If I go to system -> sound and test my Driver, it works under OSS, but ALSA gives the error message (see above).  However, the actual usage under OSS is terrible - crackly, distorted sound in players, and no system sounds.

I'm sure I'm close though like I said!

I've also noticed the same thing. Just use the OSS setting for now. That's as good as it's going to get for the time being.

---

### Post by lewisskinner on 2008-12-22
> **NullHead said:**
> I've also noticed the same thing. Just use the OSS setting for now. That's as good as it's going to get for the time being.

I'd love to, but since the main reason I still use Windoze is so I can listen to my music whilst browsing the web, not being able to listen to music in decent quality in Ubuntu is the only thing that's stopping me transfering and uninstalling Windoze completely right now.

---

### Post by mhenriday on 2008-12-22
> **lewisskinner said:**
> I have the exact same problem as Mikey-D.  When I try to test my OSS driver in the sound menu, it works perfectly, but I have horribly distorted sound in rhythmbox.  If i click 'test' on my ALSA drive (labelled *Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA)*, I get the error ```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
``` just as above.

CptHook, how do I disable my Realtek onboard in Ubuntu (I think I've stoppped it in BIOS, but I'm not sure) and how do I get to the ALSA mixer?

**Lewis**, what happens if you _uninstall_ all your **OSS** files in **Synaptic** and _then_ try to run **ALSA** ? This works for me on a setup very similar to yours - same processor, a Logitech 5.1 sound surround system, etc....

Henri

---

### Post by mhenriday on 2008-12-23
After finally getting my **Creative Soundblaster X-Fi** to work with my 64-bit **Intrepid** setup as described above, I decided to return to my eternal (?)  problem with **Skype** on **Ubuntu** and proceeded to install the **2.0.0.72-0medibuntu4** version via **Medibuntu** and **Synaptic**. When first I attempted to ring others via **Skype**, I received a notice to the effect that there was a problem with **Audio Playback**. To remedy this problem I reconfigured my sound devices («Options» &#8594; «Sound Devices»). With the configuration shown in the screenclip below, I discovered that I was now able to ring up the **Skype Test Call** and hear what the operator had to say, but not my own response. None of the other settings available to me worked as well. In the midst of these trials, a friend, who had noticed that I was registered as being online, rang me up, but alas, we were unable to converse - I could hear him perfectly well, but he couldn't hear me. I have similar problems with sound in **Ekiga**. My headset and microphone work quite well in the **Skype 4.0 beta** on **Windows**, so that particular piece of hardware is unlikely to be responsible for the problem. Has anyone on this thread with a 64-bit box who has managed to get sound working with a **Creative Soundblaster X-Fi** card by following **NullHead**'s tutorial also succeeded in getting **Skype** to work on his or her setup ? In that event, any suggestions on how I might be able to do the same ? I'm presently running **ALSA**....

Henri

---

### Post by NullHead on 2008-12-23
> **mhenriday said:**
> After finally getting my **Creative Soundblaster X-Fi** to work with my 64-bit **Intrepid** setup as described above, I decided to return to my eternal (?)  problem with **Skype** on **Ubuntu** and proceeded to install the **2.0.0.72-0medibuntu4** version via **Medibuntu** and **Synaptic**. When first I attempted to ring others via **Skype**, I received a notice to the effect that there was a problem with **Audio Playback**. To remedy this problem I reconfigured my sound devices («Options» &#8594; «Sound Devices»). With the configuration shown in the screenclip below, I discovered that I was now able to ring up the **Skype Test Call** and hear what the operator had to say, but not my own response. None of the other settings available to me worked as well. In the midst of these trials, a friend, who had noticed that I was registered as being online, rang me up, but alas, we were unable to converse - I could hear him perfectly well, but he couldn't hear me. I have similar problems with sound in **Ekiga**. My headset and microphone work quite well in the **Skype 4.0 beta** on **Windows**, so that particular piece of hardware is unlikely to be responsible for the problem. Has anyone on this thread with a 64-bit box who has managed to get sound working with a **Creative Soundblaster X-Fi** card by following **NullHead**'s tutorial also succeeded in getting **Skype** to work on his or her setup ? In that event, any suggestions on how I might be able to do the same ? I'm presently running **ALSA**....

Henri

I have skype working on my machine. I'll be able to post a screenshot later. It does work; at least with the skype test call.

---

### Post by mhenriday on 2008-12-24
Thanks, **NullHead** ; I'm very much looking forward to seeing your screenshot(s) ! What I think would be helpful here is seeing both how you've configured «Sound Devices» in **Skype** and your sound-system configurations in **Synaptic**. My latter can be seen in the screenshot below....

Henri

---

### Post by NullHead on 2008-12-24
Here are some screenshots of my setup. If you want to look at any more of it, just let me know. I tried calling the testing service and that worked perfectly. It could play back to me exactly what I said.

---

### Post by mhenriday on 2008-12-26
«*Das also war des Pudels Kern !*» Thanks for your very instructive screenshot, **NullHead** ! Aside from the fact that my test call works better (i e, I can hear the ring tone and the operator's voice) if «Ringing» is set to «Default Device (default)» rather than «Creative X-Fi (hw:XFi,0)», most of my settings are identical with yours. The crux of the matter, however, seems to be that when I attempt to use «Volume Control» to adjust the voume levels, I get the error message shown in the screenshot below, which in English translation reads as follows :> Failed to start the volume control. Failed to run the subprocess 'usr/bin/ossmix' (The file or catalogue does not exist) Any suggestions as to how this might be fixed ?...

Henri

---

### Post by PRGUY85 on 2008-12-26
Any guess as to when Ubuntu or Linux will have the X-FI working out of the box?  Also, any advances on the external I/O drive that comes with some of these cards as the Platinum?  This is the only thing still making me dual-boot with Win XP after 3-4 years of using Ubuntu.

---

### Post by NullHead on 2008-12-26
> **mhenriday said:**
> «*Das also war des Pudels Kern !*» Thanks for your very instructive screenshot, **NullHead** ! Aside from the fact that my test call works better (i e, I can hear the ring tone and the operator's voice) if «Ringing» is set to «Default Device (default)» rather than «Creative X-Fi (hw:XFi,0)», most of my settings are identical with yours. The crux of the matter, however, seems to be that when I attempt to use «Volume Control» to adjust the voume levels, I get the error message shown in the screenshot below, which in English translation reads as follows : Any suggestions as to how this might be fixed ?...

Henri

I'm just guessing at this point. Try uninstalling alsa-oss and anything else that is oss. From what you translated, it sounds like it's still trying to use oss as the sound system. 

> **PRGUY85 said:**
> Any guess as to when Ubuntu or Linux will have the X-FI working out of the box?  Also, any advances on the external I/O drive that comes with some of these cards as the Platinum?  This is the only thing still making me dual-boot with Win XP after 3-4 years of using Ubuntu.

I really don't know. I only have an extreme-gamer. I don't have any of the I/O that comes in the drive bay or in the other I/O panel.

---

### Post by PRGUY85 on 2008-12-26
> **NullHead said:**
> 
I really don't know. I only have an extreme-gamer. I don't have any of the I/O that comes in the drive bay or in the other I/O panel.

What about it working out of the box by PulseAudio or Alsa?

---

### Post by NullHead on 2008-12-26
> **PRGUY85 said:**
> What about it working out of the box by PulseAudio or Alsa?

It's possible. You'd have to manually get the code working with alsa then get it put into the testing git tree and see how that goes. I do look for future releases of alsa to contain X-Fi drivers in them. That would allow the X-Fi to work out of the box.

---

### Post by mhenriday on 2008-12-26
> **NullHead said:**
> I'm just guessing at this point. Try uninstalling alsa-oss and anything else that is oss. From what you translated, it sounds like it's still trying to use oss as the sound system.Sounds that way to me as well, but unfortunately removing all the oss files didn't seem to help - I'm still getting that strange error message. I notice that under /bin I have several files related to **ALSA** (see the screenshot below), but none under /usr/bin. I tried copying «alsamixer» to /usr/bin just to see what would happen, but was denied access. Do you have anything similar under /usr/bin on your box ?...

Henri

---

### Post by Rrasyrogenees on 2008-12-27
all i want to say is THANK YOU.. it was simple and got my sound on and i am now the happiest man :biggrin: in the world... THANK YOU... i got my music and sound on ubuntu and i can leave windows behind :biggrin:... THANK YOU... :biggrin: :biggrin:  

i was looking for about a week and just happened to find this thread... did i mention THANK YOU?

---

### Post by borlosky on 2008-12-27
> Originally Posted by PRGUY85 View Post
Any guess as to when Ubuntu or Linux will have the X-FI working out of the box? Also, any advances on the external I/O drive that comes with some of these cards as the Platinum? This is the only thing still making me dual-boot with Win XP after 3-4 years of using Ubuntu.

per the creative website, the external/internal i/o drives are not supported with driver 1.0. i have x-fi platinum with internal i/o drive bay, would love for that to work so i can have use of my s/pdif output to my receiver.

---

### Post by Static42 on 2008-12-28
Hi,

I'm using the X-Fi XtremeGamer card, and I'm very close with getting the sound to work. The Hardware Driver list recognizes the X-Fi driver, but it says, "This driver is activated but not currently in use."

When I did the "sudo make install" command, I get an error:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

I've tried to figure out how to fix it, but I have had no luck. I'm hoping someone can assist me with this.

---

### Post by NullHead on 2008-12-28
> **Static42 said:**
> Hi,

I'm using the X-Fi XtremeGamer card, and I'm very close with getting the sound to work. The Hardware Driver list recognizes the X-Fi driver, but it says, "This driver is activated but not currently in use."

When I did the "sudo make install" command, I get an error:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

I've tried to figure out how to fix it, but I have had no luck. I'm hoping someone can assist me with this.

What version of Ubuntu are you using?

---

### Post by lewisskinner on 2008-12-28
> **mhenriday said:**
> **Lewis**, what happens if you _uninstall_ all your **OSS** files in **Synaptic** and _then_ try to run **ALSA** ? This works for me on a setup very similar to yours - same processor, a Logitech 5.1 sound surround system, etc....

Henri

That's a nice idea.  How would I do that?

---

### Post by Static42 on 2008-12-28
> **NullHead said:**
> What version of Ubuntu are you using?

I am running the latest: 8.10

---

### Post by JohnFante on 2008-12-29
Got an X-FI extreme gamer for Christmas :-)

For me the drivers works fine with OSS but not ALSA.

I get the above mentioned error:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

when I try to test with ALSA and Amarok dosn't work with ALSA. Everything else seems to work fine.

A how to on how to uinstall OSS would be highly appreciated. ALSA is just better.

My new years wish will this year be for a new and better driver :-)

---

### Post by NullHead on 2008-12-29
> **JohnFante said:**
> Got an X-FI extreme gamer for Christmas :-)

For me the drivers works fine with OSS but not ALSA.

I get the above mentioned error:



when I try to test with ALSA and Amarok dosn't work with ALSA. Everything else seems to work fine.

A how to on how to uinstall OSS would be highly appreciated. ALSA is just better.

My new years wish will this year be for a new and better driver :-)

I've tested with kubuntu 8.10 and the Alsa drivers work like a charm for my extreme gamer.

---

### Post by Static42 on 2008-12-30
Well, I reinstalled Ubuntu and reinstalled the drivers. They work good now. The system recognizes the X-Fi driver and everything. The problem is that my sound is very low. I have everything maxed out volume wise. I am able to hear sound come out of the speakers, but it's low and it could be improved. I get much better sound on Windows XP so something isn't right. Any ideas?

---

### Post by JohnFante on 2008-12-30
> **NullHead said:**
> I've tested with kubuntu 8.10 and the Alsa drivers work like a charm for my extreme gamer.

Ok :-)

Maby the problem is caused by my "old" drivers. I used to have a and old onboard soundcard "VIA 8237 with AD1980 VIA 8237 (ALSA)" that I disabled in the bios when I installed the extreme gamer card. I can still see the old drivers in soundpreferences (see above) so maby there is some kind of conflict. Is there a way to remove all "old" sound drivers?

Btw, I checked the [ALSA page]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") for news on X-FI support and saw this: 

> Sound Blaster X-Fi emu20k1 [Unsupported] [PCI] Card delivered to developers. Completely new architecture. Creative have supplied a data sheet to developers. Development work has started.

At least something is happening.

---

### Post by JohnFante on 2008-12-30
Well my conflicting driver theory did not stick (it was probably also a leftover thought from my windows days). Did a reinstall and have the same problem. OSS works finew but ALSA dos not.

Looking forward to a how to on how to unistall OSS (and reinstall if everything goes beserk).

Thank you in advance :-)

---

### Post by NullHead on 2008-12-30
> **JohnFante said:**
> Well my conflicting driver theory did not stick (it was probably also a leftover thought from my windows days). Did a reinstall and have the same problem. OSS works finew but ALSA dos not.

Looking forward to a how to on how to unistall OSS (and reinstall if everything goes beserk).

Thank you in advance :-)

Try this out: [http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

---

### Post by pierre.s.rosen on 2008-12-30
Just wanted to shout out and thank NullHead for his excellent guide to installing Creative's new open source X-fi drivers.  I followed the instructions on a fresh install of Ubuntu Intrepid Ibex 8.10.  It works with my X-Fi XtremeGamer - no problems encountered so far.

---

### Post by JohnFante on 2008-12-31
> **NullHead said:**
> Try this out: [http://ubuntuforums.org/showpost.php?p=5055305&postcount=105](http://ubuntuforums.org/showpost.php?p=5055305&postcount=105)

Thanks for the link but the instructions did not work.

I am sticking with OSS for now. Got sound in flash following the last post on [this]("http://ubuntuforums.org/showthread.php?t=873749") thread.

The setup is not perfect but as we all know. **If it works - don't fix it.**

---

### Post by mhenriday on 2008-12-31
> **lewisskinner said:**
> That's a nice idea.  How would I do that?Open **Synaptic** («System» &#8594; «Administration» &#8594; «Package Manager Synaptic», and click the binoculars icon to perform a search for **OSS** files (click «s» at the upper left of the file window to bring installed files to the top). The files marked with green boxes to the left are installed ; they can be uninstalled by right-clicking them one at a time and choosing the option to uninstall. To install the relevant **ALSA** files, perform a search for «ALSA», click in the empty box to the left of each file you wish to install, and choose the installation option from the menu that opens. You can then click the green «Execute» tick from the toolbar at the top of **Synaptic** to carry out the installation process....

Henri

---

### Post by JohnFante on 2009-01-02
Does anybody have a list with of actual OSS files to uninstall / install?

When I search for OSS in Synaptic I get:

libao2
libasound2-plugins
libmikmod2
linux-sound-base
pulseaudio
pulseaudio-utils

When I search for alsa I get:

alsa-base
alsa-utils
libasound2
libasound2-plugins
libesd-alsa0

Thank you in advance.

---

### Post by ainacio on 2009-01-03
If my device number is 21, do I need to change the header file and recompile the driver?

---

### Post by ainacio on 2009-01-04
I am using the creative open driver, and I tried setting the device to 21 and using the default. Both times I get the same result -- When I go to the configurations, I can see the creative driver in the option menu, but if I select it and try to test it, I get an error.

---

### Post by Psychopsia on 2009-01-04
> **ainacio said:**
> I am using the creative open driver, and I tried setting the device to 21 and using the default. Both times I get the same result -- When I go to the configurations, I can see the creative driver in the option menu, but if I select it and try to test it, I get an error.

Post here what error you're getting please :)

---

### Post by ainacio on 2009-01-04
When I go to System-> System Preferences -> Sound Preferences... I can see the following:

```

AUTO
xfi ALSA
xfi OSS
xfi OSS  
ALSA
OSS
Pulse

```

//nb. redundant entry (xfi OSS)


All of the modes give me the following error:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

```

When I press the 'Test' button.

Also, the Sound Preferences application will frequently hang, requiring a fore quit.

---

### Post by Psychopsia on 2009-01-04
> **ainacio said:**
> All of the modes give me the following error:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

```

When I press the 'Test' button.

Also, the Sound Preferences application will frequently hang, requiring a fore quit.

Even option "Autodetect"?

I had similar problem, but my error was "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback."

Now with "Autodetect" selected works fine.

---

### Post by ainacio on 2009-01-04
> **Psychopsia said:**
> Even option "Autodetect"?



Yes, sadly; autodetect gives me the same error. If it's of any help to find a solution to my issue, I followed some of this guide before trying to get my XFi card working: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by ieduarte73 on 2009-01-04
Hi, I have tried what you guys suggest but instead of getting the driver installed, I get this ugly error:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

This is the output of make:

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  Building modules, stage 2.
  MODPOST 1 modules

Then I do sudo make install and got the error.

Any Ideas

I used to have OSS on this computer but after a PulseAudio update It stopped working, and to be honest, it wasn't working quite good.  So I need a driver that works with ALSA.

---

### Post by mnnn on 2009-01-06
well I still don't understand there's no solution for "Unknown symbol in module, or unknown parameter" (btw. the unknown symbol is 'index'), as there has been many users asking for help with this.

```
$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-9-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1

```
dmesg:```
[  626.005324] ctxfi: Unknown parameter `index'
```

This problem appeared for me after update to 2.6.27-9-generic kernel, so maybe in previous versions (I guess, I had one from 2.6.25 versions).

Thanks for help.

---

### Post by ainacio on 2009-01-06
> **ainacio said:**
> When I go to System-> System Preferences -> Sound Preferences... I can see the following:

```

AUTO
xfi ALSA
xfi OSS
xfi OSS  
ALSA
OSS
Pulse

```

//nb. redundant entry (xfi OSS)


All of the modes give me the following error:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

```

When I press the 'Test' button.

Also, the Sound Preferences application will frequently hang, requiring a fore quit.


anyone? somebody told me I should try removing pulseaudio.  Is this a good idea? If so, how does one delete pulse audio?

---

### Post by ainacio on 2009-01-08
If I switch to Create ALSO Driver X-Fi WaveOut/WaveIn(ALSA)... I get the following error when I click Test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

---

### Post by NullHead on 2009-01-08
> **ainacio said:**
> If I switch to Create ALSO Driver X-Fi WaveOut/WaveIn(ALSA)... I get the following error when I click Test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Make your settings look like this: [http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367](http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367) 

That's the only way I've gotten my setup to function properly. I suggest you try those settings as well.

---

### Post by NullHead on 2009-01-08
> **ainacio said:**
> If I switch to Create ALSO Driver X-Fi WaveOut/WaveIn(ALSA)... I get the following error when I click Test:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

Make your settings look like this: [http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367](http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367) 

That's the only way I've gotten my setup to function properly. I suggest you try those settings as well.

---

### Post by mnnn on 2009-01-10
Nullhead: you don't know anything about that unknown symbols in modules? It would be great if you had known how to solve this problem. Thanks.

---

### Post by NullHead on 2009-01-10
> **mnnn said:**
> Nullhead: you don't know anything about that unknown symbols in modules? It would be great if you had known how to solve this problem. Thanks.

I'm afraid I don't. I would just look into your kernel and update it to the latest ... I'm just speculating now. It makes and runs really well on my 2.6.27.10 I think it might be ... Try using the newest kernel, then making it again. I am just speculating at this point.

---

### Post by Nitrius on 2009-01-10
So far this method has worked great for me, sound everywhere and sound from multi programs at once.

Got the Creative X-FI XtremeMusic card.

---

### Post by SnickeringHermit on 2009-01-11
Short and sweet, I love you nullhead. xD couldn't get the blasted thing working, then bam, just like that.  <3 thanks much

using a Creative Labs Sound Blaster X-FI.  works beautifully now

---

### Post by mnnn on 2009-01-11
> **NullHead said:**
> I'm afraid I don't. I would just look into your kernel and update it to the latest ... I'm just speculating now. It makes and runs really well on my 2.6.27.10 I think it might be ... Try using the newest kernel, then making it again. I am just speculating at this point.

And are you using Ubuntu kernel, or your own compiled?

---

### Post by NullHead on 2009-01-11
> **mnnn said:**
> And are you using Ubuntu kernel, or your own compiled?

I'm using the latest Ubuntu kernel.

---

### Post by NullHead on 2009-01-11
Double post

---

### Post by NullHead on 2009-01-11
Another double post ....... (I was having problems with my browser ;))

---

### Post by rv65 on 2009-01-11
```
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
```

This is what happens when I do sudo make install. Any ideas. I can't get this thing to work. Every time I do this it gets errors.

---

### Post by mnnn on 2009-01-12
Nullhead: you see? I'm not the only one with this problem (^ rv65).

---

### Post by NullHead on 2009-01-12
> **rv65 said:**
> ```
FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
```

This is what happens when I do sudo make install. Any ideas. I can't get this thing to work. Every time I do this it gets errors.

> **mnnn said:**
> Nullhead: you see? I'm not the only one with this problem (^ rv65).

Well I can't say that I know what the issue is ... Sorry guys. I don't know what's going on. I don't have allot of different ways to test the driver; so I can't easily know many of the answers to your problems. 

I can only test with _one_ X-Fi extreme gamer (I'll never buy another X-Fi again) and _one_ type of system to test it on. 

The method on the first thread is a rather generalized set of instructions that I've only tested with my rather cheep and old model of X-Fi. I can only test those instructions on my AMD based system with my Extreme Gamer card. 

Lets try at least looking in dmesg and seeing what the error is when you get error 1. 

Open a terminal and run "**dmesg**". Then copy out the last 20 lines of text that just streamed through the terminal window, and paste them into a new text file. Gedit works great for this task; so start up gedit and paste the text; save the file and upload it. I'll see what I can see, but I'm not a ninja, so no guarantees ;)

---

### Post by mountain_goat on 2009-01-12
Hey Nullhead, a quick drop by to say thank you for the howto.
It was finally a blessing to move up from 8.04 to 8.10 and not to have to do the recompile thing.

I am hoping that with this open source driver some clever dudes out there will be able to extend the functionality of the X-Fi series. With Ubuntu Studio 8.10 sound from my X-Fi extreme music is pretty sweet to my ears now.

Thank you again for your continued support and also towards the many peeps having troubles with their X-Fi install.

mountain goat ~ a grazin on my mountain

---

### Post by mnnn on 2009-01-12
Nullhead: dmesg:
> [   14.067996] ctxfi: Unknown parameter `index'


---

### Post by NullHead on 2009-01-12
> **mnnn said:**
> Nullhead: dmesg:

I hope you understand this is pure guess work here. 

Try re-downloading the driver, and deleting your old files. Don't try to make clean or anything, just delete the files, and download a fresh one. Extract the archive from the terminal with "**tar -xf <file name>**". Then try the process over again with make and sudo make install.

---

### Post by ainacio on 2009-01-14
> **NullHead said:**
> Make your settings look like this: [http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367](http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367) 

That's the only way I've gotten my setup to function properly. I suggest you try those settings as well.


NullHead,

I cannot set my settings to those. Namely, The 'Device' combo box is grayed out, and does not show any data or let me make any selections. 

Could this be my issue?

---

### Post by XanII on 2009-01-17
I cannot find words to describe my dissapointment but so it seems i have a X-Fi Extreme card, the basic one. 

And the Creative driver doesnt seem to suppor that according to the list. 
Driver compiled well though. no errors is devmsg either. made it to point towards subsystem 0018 according to advice too but it didnt help, it figures as it simply is not supported if i understand correctly. 

:(

This sucks so bad... Now i have reactivated AC'97. 

04:00.0 PCI bridge: Creative Labs Device 7006
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
	Memory behind bridge: d4000000-d40fffff
	Capabilities: <access denied>
	Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs Device 0018
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d4000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

---

### Post by mnnn on 2009-01-17
XanII: X-Fi driver from Creative (or OSS) isn't for your card (XtremeAudio), which is just renamed Audigy SE (or something else with software Crystalizer etc.)

---

### Post by ainacio on 2009-01-18
If it helps you solve my problem... here is my output:

06:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: medium devsel, IRQ 17
	I/O ports at ec00 [size=32]
	Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0

---

### Post by ainacio on 2009-01-19
And this is what it looks like after I install the driver:

06:01.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 0021
	Flags: bus master, medium devsel, latency 64, IRQ 17
	I/O ports at ec00 [size=32]
	Memory at fbc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi


but in both cases... as I said before, I cannot configure the 'Default Mixer Tracks' 'Device'

---

### Post by NullHead on 2009-01-19
It looks like the X-Fi works. Have you disabled onboard sound? Try opening "**alsamixer** from the terminal and see if it shows you your X-Fi.

---

### Post by XanII on 2009-01-19
> **mnnn said:**
> XanII: X-Fi driver from Creative (or OSS) isn't for your card (XtremeAudio), which is just renamed Audigy SE (or something else with software Crystalizer etc.)

Great. so now i dont even know the exact name for the soundcard. :P

How does one search for drivers for such a card?

---

### Post by NullHead on 2009-01-19
> **XanII said:**
> Great. so now i dont even know the exact name for the soundcard. :P

How does one search for drivers for such a card?

I think ALSA has built in support for it already. I could be wrong though.

---

### Post by ainacio on 2009-01-19
> **NullHead said:**
> It looks like the X-Fi works. Have you disabled onboard sound? Try opening "**alsamixer** from the terminal and see if it shows you your X-Fi.

I did disable onboard sound... and that command you mentioned does not seem to work...

ainacio@beast:~$ alsamixer
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by ainacio on 2009-01-19
```
ainacio@beast:~$ alsamixer
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

---

### Post by bjorkiii on 2009-01-20
Does anybody know if spdif think thats it, will ever be able to work on a xfi card in linux are alsa still trying to get it to function :(

---

### Post by JohnFante on 2009-01-21
> **NullHead said:**
> It looks like the X-Fi works. Have you disabled onboard sound? Try opening "**alsamixer** from the terminal and see if it shows you your X-Fi.

Sorry if I interrupt. What should alsamixer show to be correct?

When I open alsamixer in a terminal the mixer starts fine. On card it says PulseAudio, it also does that on chip. Is that correct?

My situation is that I can't get alsa to work but OSS works fine.

---

### Post by dmrazor on 2009-01-21
Good to see so many success stories with the new driver. ATM I'm stil running the X-Fi on OSS so if I understand everything correctly getting this driver to work would mean:

* reverting back to ALSA
* upgrading from 8.04 to 8.10 so I have the correct kernel
* compiling the driver as instructed in the first post

The only thing I'm missing in my current setup (besides sound quality) is the ability to record sound (i.e. to use a microphone with Skype). Could anyone tell me if sound recording is functioning with this Opensource Alsa driver?

Raz.

---

### Post by NullHead on 2009-01-21
> **dmrazor said:**
> Good to see so many success stories with the new driver. ATM I'm stil running the X-Fi on OSS so if I understand everything correctly getting this driver to work would mean:

* reverting back to ALSA
* upgrading from 8.04 to 8.10 so I have the correct kernel
* compiling the driver as instructed in the first post

The only thing I'm missing in my current setup (besides sound quality) is the ability to record sound (i.e. to use a microphone with Skype). Could anyone tell me if sound recording is functioning with this Opensource Alsa driver?

Raz.

Recording works for me. I've had a few skype conversations myself :D

---

### Post by ainacio on 2009-01-21
Nullhead,

Why is the program you asked me to run not running. Could this be the root of my issues?

---

### Post by NullHead on 2009-01-21
> **ainacio said:**
> Nullhead,

Why is the program you asked me to run not running. Could this be the root of my issues?

I'm not sure. It's possible that it's not opening because the only sound device present in the system (excluding a disabled onboard sound) isn't functioning properly. Did the driver build correctly?

---

### Post by Mort Rouge on 2009-01-21
I posted in another thread, but I guess that i should have posted in this thread in the first place. here it goes:

"Hi all!
I have recently switched to Linux again after a period of Windows based illness. The only thing I'm having trouble with configuring is the sound (I have a Creative X-Fi Fatality Gamer Edition card). I've got all working, but one problem remains.

When I try to record sound trough my headset microphone, instead of recording the microphone alone, it records all the sound my computer generates. This isn't so great when you're trying to have a Skype conversation and play a game at the same time...

I've fiddled around in the sound menu, but I haven't found anything useful yet. Am I just being a n00b, or what?

Please help! 

/Mortimer"

---

### Post by NullHead on 2009-01-21
> **Mort Rouge said:**
> I posted in another thread, but I guess that i should have posted in this thread in the first place. here it goes:

"Hi all!
I have recently switched to Linux again after a period of Windows based illness. The only thing I'm having trouble with configuring is the sound (I have a Creative X-Fi Fatality Gamer Edition card). I've got all working, but one problem remains.

When I try to record sound trough my headset microphone, instead of recording the microphone alone, it records all the sound my computer generates. This isn't so great when you're trying to have a Skype conversation and play a game at the same time...

I've fiddled around in the sound menu, but I haven't found anything useful yet. Am I just being a n00b, or what?

Please help! 

/Mortimer"

I really have no idea about that one either :confused:

---

### Post by ainacio on 2009-01-21
> **NullHead said:**
> I'm not sure. It's possible that it's not opening because the only sound device present in the system (excluding a disabled onboard sound) isn't functioning properly. Did the driver build correctly?


I did: 
sudo make
sudo make install

running make on its own would not work... I had tons of warnings but no errors during make.


```


ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ ls
built-in.o   ctdaio.h      ctimap.h      ctsrc.c      Disk.id
COPYING      ctdaio.o      ctimap.o      ctsrc.h      Makefile
ct20k1reg.h  ctdrv.h       ctmixer.c     ctsrc.o      Module.markers
ct20k2reg.h  cthardware.c  ctmixer.h     ctutils.h    modules.order
ctamixer.c   cthardware.h  ctmixer.o     ctvmem.c     Module.symvers
ctamixer.h   cthardware.o  ctpcm.c       ctvmem.h     README
ctamixer.o   cthw20k1.c    ctpcm.h       ctvmem.o     xfi.c
ctatc.c      cthw20k1.o    ctpcm.o       ctxfi.ko     xfi.o
ctatc.h      cthw20k2.c    ctresource.c  ctxfi.mod.c
ctatc.o      cthw20k2.o    ctresource.h  ctxfi.mod.o
ctdaio.c     ctimap.c      ctresource.o  ctxfi.o
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.27-9-generic/build M=/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
rm: cannot remove `/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/.tmp_versions/ctxfi.mod': Permission denied
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
make: *** [all] Error 2
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ make clean
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions
rm: cannot remove `.tmp_versions/ctxfi.mod': Permission denied
make: *** [clean] Error 1
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make clean
[sudo] password for ainacio: 
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.27-9-generic/build M=/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_amixer_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_sum_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘put_daio_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_add’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_delete’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_mgr_destroy’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make clean
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
make -C /lib/modules/2.6.27-9-generic/build M=/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  LD      /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function ‘ct_alsa_pcm_create’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of ‘snd_pcm_new’ discards qualifiers from pointer target type
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_src_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘put_srcimp_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_add’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_imap_delete’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function ‘srcimp_mgr_destroy’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_amixer_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function ‘put_sum_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘put_daio_rsc’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_add’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_imap_delete’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function ‘daio_mgr_destroy’:
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/ainacio/Desktop/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
ainacio@beast:~/Desktop/XFiDrv_Linux_Public_US_1.00$ 




```

---

### Post by ainacio on 2009-01-21
Ok... so I found a page here: [http://ubuntuforums.org/showthread.php?t=925211&page=2](http://ubuntuforums.org/showthread.php?t=925211&page=2)


it looks like they were having a similar problem... so I did the following:

> Another workaround that works for me:
1. Create /etc/ld.so.conf.d/alsa32.conf with the following contents:
/usr/lib32/alsa-lib

2. Create /etc/ld.so.conf.d/alsa64.conf with the following contents:
/usr/lib/alsa-lib

3. sudo ldconfig

4. Open /usr/share/alsa/pulse.conf in the editor and remove the "/usr/lib/alsa-lib/" prefix from the libasound_module_conf_pulse.so file.


So I can now run 'sudo alsamixer' and it tells me that it is using my Xi-Fi... and also says that I have the '20K1' chip.

So I went back into the 'Sound Preferences' window, and I still cannot choose a 'Device'. Moreover, when I click 'test' on, for instance, Sound playback, I get the following error message:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.You don't have permission to open the device.
```


Intuitively, I believe this to be an error of user rights. As the driver was installed with root, and ainacio is not a root... it seems to get protective of the device :(. 


Could this be the issue?

---

### Post by ainacio on 2009-01-21
Ok... so I found this:

> Run:

1) sudo /etc/init.d/alsa-utils restart
2) sudo chmod 666 /dev/snd/*

here: [https://answers.launchpad.net/ubuntu/+question/5455](https://answers.launchpad.net/ubuntu/+question/5455)

I can pick my Device!, and hence my Sound Preferences are configured exactly the way NullHead had configured his. ([http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367](http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367))

However... When I click 'Test' on 'Sound playback', I get the following error (still) :

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.You don't have permission to open the device.
```

---

### Post by ainacio on 2009-01-21
Ok... so... my sound works! NullHead's configuration, oddly, did not want to work for me... possibly because the OSS directory is still locked down... So only the ALSA driver works... contrary to NullHead's settings. 

Now the following concearns need to be addressed:

1) Should I try to enable the OSS? Why?
2) How do we control 7.1 surround sound?

---

### Post by NullHead on 2009-01-21
> **ainacio said:**
> Ok... so... my sound works! NullHead's configuration, oddly, did not want to work for me... possibly because the OSS directory is still locked down... So only the ALSA driver works... contrary to NullHead's settings. 

Now the following concearns need to be addressed:

1) Should I try to enable the OSS? Why?
2) How do we control 7.1 surround sound?

[LIST=1]
[*]If it ain't broke, don't fix it.
[*]Surround sound isn't yet supported yet.
[/LIST]

---

### Post by freyder on 2009-01-25
I get the same error as ainacio although at one point I had it working.

I went back to the onboard sound as the XFi driver didn't have a mic boost option so the mic recordings were too low.

---

### Post by NullHead on 2009-01-25
Well [this](http://www.4front-tech.com/forum/viewtopic.php?p=11573) is old news, but look see here: [quote=OSS developer]OSS v4.1 build 1051 for Linux, Solaris, BSD and Unixware is now available as binaries and source code.

What's new?

* New Virtual Mixer that is dynamically allocated
* Improved OSS GUI mixer panel
* Improved OSS record and play applets
* Updated drivers for HDAudio, Intel ICH, Lynx Studio, **[COLOR="Blue"]XFi [/COLOR]**and Envy24ht
* New HDAudio Modem driver
* Virtual Audio + Sun Ray audio support added

We thank the Open Sound community for all the contributions to the project.[/quote]

It claims that the OSS team has updated the XFi driver for OSS v4.1. I've not tested it, but I thought I'd let others know about it just in case they cannot seem to succeed with Creative's new one.

You can use the guide in the deprecated section of my guide on the first page to help you get it setup. here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by CentrinoLD on 2009-01-25
Hi all,

I've read all the thread, and still have a problem with my xtreme gamer :

Ubuntu 8.10
x-fi xtrem gamer
last crative driver 1.00 US
Install on a new 8.10

I have the sound working, gnome control panel :

Creative X-Fi (Alsa)

my problem is the mic, it's working but all the sound (music, internet, system) are also played through the mic, so in skype they hear my voice but also all !
I try a record with the default gnome record tool, the same !

I try in the gnome sound control panel all the possibility : pulseaudio, oss, alsa, change the material to hw0 alda via Pule ..., all !

Also in skype sound option, I try all (pulseaudio trick for skype ...); I'm not abled to stop playing sounds through my mic !

Someone has the same problem ?
I'm not a beginner in Linux, but here it's the first time I have a wall !

Please help me ! :popcorn::p

Thanks

CentrinoLD from France (sorry for my bad english)

---

### Post by mnnn on 2009-01-26
Thanks, Nullhead! Gonna try it soon!

---

### Post by iBoniek on 2009-01-26
I've tested the newest oss driver and it's much better then alsa driver and no problem in 8.10

---

### Post by NullHead on 2009-01-26
> **iBoniek said:**
> I've tested the newest oss driver and it's much better then alsa driver and no problem in 8.10

Does it have surround sound and recording support yet?

---

### Post by JohnFante on 2009-01-27
> **iBoniek said:**
> I've tested the newest oss driver and it's much better then alsa driver and no problem in 8.10

Could you maby post a short guide on how you upgraded OSS/disables ALSA?

---

### Post by NullHead on 2009-01-27
> **JohnFante said:**
> Could you maby post a short guide on how you upgraded OSS/disables ALSA?

That's all in here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

[quote=ubuntu wiki]Stopping ALSA

sudo chmod 776 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist

The block of text that follows is one command! (copy and paste the entire cell):

sudo echo "blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd
blacklist soundcore" >> /etc/modprobe.d/blacklist[/quote]

---

### Post by CentrinoLD on 2009-01-27
> **iBoniek said:**
> I've tested the newest oss driver and it's much better then alsa driver and no problem in 8.10

Do you have the mic working correctly ? :

cause all work perfectly but not the mic

my problem :

[http://www.4front-tech.com/forum/viewtopic.php?t=3050](http://www.4front-tech.com/forum/viewtopic.php?t=3050)

Thanks

---

### Post by rblumenthal on 2009-01-28
edit* got it working

---

### Post by jimmaps on 2009-01-29
> **CptHook said:**
> Nullhead you may want to add this info to your front page.

If you check dmesg you may see a line reading something like
CTALSA: probe of 0000:03:00.0 failed with error -2

After install you are not getting the driver to completely load you need to check the subsystem of your sound card.


An example of a non working card.

#lspci -v
04:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 9
	Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
	Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
	Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
        Kernel modules: ctxfi

An example of a working card.

#lspci -v
03:00.0 Audio device: Creative Labs Device 000b (rev 03)
	Subsystem: Creative Labs Device 0043
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
	Memory at fe600000 (64-bit, non-prefetchable) [size=2M]
	Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

Notice the Kernel driver in use: CTALSA line on the working card.

The problem lies in the fact that Creative did not add all the subsystems to the ctdrv.h file.

Check what subsystem you have line 2 of the lspci -v, if you have a newer PCIe card your subsystem most likely will be 42 or 43. make the below adjustments to the ctdrv.h file and remake the driver.

#define PCI_SUBSYS_CREATIVE_SB0880    0x0041

to

#define PCI_SUBSYS_CREATIVE_SB0880    0x0042
or 
#define PCI_SUBSYS_CREATIVE_SB0880    0x0043

after a reinstall and reboot your sound should work.

Man I love you and Nullhead. This last bit is realy important for pci-e cards. Perhaps a note in the first post Null?

---

### Post by iBoniek on 2009-01-29
> **NullHead said:**
> Does it have surround sound and recording support yet?

There is still no surround support and recording is quite bad.

---

### Post by NullHead on 2009-01-29
> **jimmaps said:**
> Man I love you and Nullhead. This last bit is realy important for pci-e cards. Perhaps a note in the first post Null?

I used to have a note on there ... I must have removed it when I changed it up a few days ago. I'll add a note in there. 

Thanks for the reminder :D

EDIT: First post has been updated.

---

### Post by Trigsu on 2009-01-30
Oh my, I have some serious problems (understanting it).
This is the 3rd clean Ubuntu 8.10 (64bit) install, here we try again.

Ubuntu Install DONE
Updates Loaded DONE

Before installing drivers:
**#lspci -v**
 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002c
	Flags: bus master, medium devsel, latency 32, IRQ 3
	I/O ports at bc00 [size=32]
	Memory at dfe00000 (64-bit, non-prefetchable) [size=2M]
	Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>

After intalled as below (-----)

**#lspci -v**
Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 002c
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at bc00 [size=32]
	Memory at dfe00000 (64-bit, non-prefetchable) [size=2M]
	Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi

----------------------------------------------------------------
Terminal:
sami@trigsu....:~$ (should I do this as root with 'us'?)

[B]#wget [http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz)

#tar -xf XFiDrv_Linux_Public_US_1.00.tar.gz

#cd XFiDrv_Linux_Public_US_1.00

#sudo apt-get install build-essential linux-headers-`uname -r`[/B]
[I][sudo] password for sami: 
Luetaan pakettiluetteloita... Valmis
Muodostetaan riippuvuussuhteiden puu       
Luetaan tilatiedot... Valmis        
linux-headers-2.6.27-11-generic on jo uusin versio.
Seuraavat paketit asennettiin automaattisesti, eivätkä ne ole enää vaadittuja:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Poista ne komennolla "apt-get autoremove".
Seuraavat ylimääräiset paketit on merkitty asennettaviksi:
  dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
Ehdotetut paketit:
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc
Seuraavat UUDET paketit asennetaan:
  build-essential dpkg-dev g++ g++-4.3 libstdc++6-4.3-dev patch
0 päivitetty, 6 uutta asennusta, 0 poistettavaa ja 0 päivittämätöntä.
Noudettavaa arkistoa 6935kt.
Toiminnon jälkeen käytetään 23,3M t lisää levytilaa.
Haluatko jatkaa [K/e]? K...[/I] **"Yes"** to that and so far, so good. Language is Finnish, don't let that deceive.

Now these next ones usually goes bad.

**#make**
[I]make -C /lib/modules/2.6.27-11-generic/build M=/home/sami/XFiDrv_Linux_Public_US_1.00
make[1]: Siirrytään hakemistoon "/usr/src/linux-headers-2.6.27-11-generic"
  LD      /home/sami/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/sami/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/sami/XFiDrv_Linux_Public_US_1.00/ctpcm.c: Funktio &#8221;ct_alsa_pcm_create&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: varoitus: passing argument 2 of &#8221;snd_pcm_new&#8221; discards qualifiers from pointer target type
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/sami/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/sami/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c: Funktio &#8221;put_src_rsc&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c: Funktio &#8221;put_srcimp_rsc&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c: Funktio &#8221;srcimp_imap_add&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c: Funktio &#8221;srcimp_imap_delete&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c: Funktio &#8221;srcimp_mgr_destroy&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: varoitus: comparison of distinct pointer types lacks a cast
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c: Funktio &#8221;put_amixer_rsc&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c: Funktio &#8221;put_sum_rsc&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: varoitus: comparison of distinct pointer types lacks a cast
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c: Funktio &#8221;put_daio_rsc&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c: Funktio &#8221;daio_imap_add&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c: Funktio &#8221;daio_imap_delete&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c: Funktio &#8221;daio_mgr_destroy&#8221;:
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: varoitus: comparison of distinct pointer types lacks a cast
/home/sami/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: varoitus: comparison of distinct pointer types lacks a cast
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/sami/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/sami/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Poistutaan hakemistosta "/usr/src/linux-headers-2.6.27-11-generic"[/I]

**#sudo make install** (Hmm...i recall that my previous installs didn't ask password here.)
[sudo] password for sami: 
Copy module files...
Update module dependency relationships...
-------------------------------------------------------------

Sound settings, System>Preferences>Sound, looked like in the guide.

**<REBOOT> **

No sound yet. All volumes maxed out. No matter what I choose from the drop-menus.
Only *Creative ALSA Driver X-Fi WaveOut/WaveIn (ALSA)* gives me error when testing:
*audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink:...*

Should I modify ctdrv.h to match *Subsystem: Creative Labs Device 002c*?

> make the below adjustments to the ctdrv.h file and remake the driver.
Does this remake mean SAVE file or something more...linux. :D
Or reinstall driver with make, sudo make install?

----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
[B]
AAAAeeeiiyeeeeerrgh. So the front panel of Fatality don't work with linux driver...rest works...I can only laugh. :D[/B]

NullHead, could you please put this to your guide "X-Fi front panels don't work"
I did many hours work and investigating for nothing..(yeah, yeah...I had in mind, what if...but until today I didnt try the rear panel)

---

### Post by NullHead on 2009-01-30
[quote=Trigsu]NullHead, could you please put this to your guide "X-Fi front panels don't work"
I did many hours work and investigating for nothing..(yeah, yeah...I had in mind, what if...but until today I didnt try the rear panel[/quote]

Yes. I will update it :) 

I'm glad you at least have the rear panel working.

---

### Post by Ocye on 2009-01-30
My adventure with the Creative XFi Titanium: 
I bought a new computer with that card and tried OSS first. With oss_sbxfi [[COLOR="Blue"]hardware init failed[/COLOR]]("http://4front-tech.com/forum/viewtopic.php?t=3048"). After all I read NullHeads first posting and tried to install the ctxfi driver, resulting in *FATAL: Error inserting ctxfi*. I found a lot of post with the idea that OSS is responsible, which I removed prior installation of ctxfi. Since it was a new installation without too much configuration I reinstalled Ubuntu completely. And now the driver can be loaded (certainly ctdrv.h needs to be hacked). It works fine with OSS, not with Alsa and has full digital output over SPDIF. At least stereo... ;)
I hope that helps and thanks for all the posts here.

---

### Post by DavidBeijer on 2009-02-01
I have a PCI-e X-FI Extreme audio. That is not in the supported drivers list, can I forget about getting it to work with these drivers? Or is there some trick? I know, I should've checked for Linux compatibility before making any choices on soundcards when I bought my PC. I am kind of a Linux n00b, but willing to learn.

lspci -v gives:
```
04:00.0 PCI bridge: Creative Labs Device 7006
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=05, subordinate=05, sec-latency=64
	Memory behind bridge: dff00000-dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs Device 0018
	Flags: bus master, medium devsel, latency 64, IRQ 10
	Memory at dfffc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
```

When trying the simple make/sudo make install commands I get no errors, but the soundcard simply won't show up in the preferences->sounds lists. The output by make and make install is:
```
make -C /lib/modules/2.6.27-11-generic/build M=/home/david/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/david/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/david/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/david/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/david/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/david/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/david/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/david/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  LD [M]  /home/david/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/david/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/david/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
```
and
```
david@david-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...

```

I have already disabled my onboard soundcard. In the soundcard list there is also a sounddevice listed that is supposed to be in my ATI HD3650 card, which I suppose is for HDMI purposes.

Anybody has any ideas?

---

### Post by pierre.s.rosen on 2009-02-05
After my last Ubuntu kernel update, sound stopped working.  I still had sound using the old kernel, so I figured that I would try to reinstall the creative drivers.  Reinstalling the creative drivers restored sound to the system.

---

### Post by freyder on 2009-02-07
I built and loaded this driver with no issues but as others may have noticed the mic boost button was no where to be found and recording anything through the mic was too soft.

So I got my brother, the developer in the family, to take a quick look at the code.
If you search for boost in cthw20k2.c you'll see that the author sets +12db for mic boost if mic is the selected input.
EDIT:
failure with WINE 1.1.14 ... and Ventrilo 
going to try previous stable version

My recollection is that +20db is the norm for this card under Win XP so no clue why its set to +12db in this driver but that sure explains the quiet recordings.

So anyway, a quick google for the chip spec sheet shows that instead of setting mic boost to 0xE7 (+12db) we want it to be 0xF7(+20db)

Basically the change is very simple.
You could just change all the E7 values to F7 but I chose to #define a variable and use that instead.
I was originally thinking I might want to tweak a lower value but 0xF7 (+20db) is working great for me.

search for MYBOOST in the file and you'll see where I #define it and then reference it further down.
If you want less boost choose a value between 0xE7 and 0xF7... each increment is +.5db.

Mic recording for Ventrilo, skype etc is now very clear and people don't complain that they can't hear me.

I guess I need to go buy my bro a case of beer for figuring this out for me.  

Enjoy. 

Rob.



Attached is the updated cthw20k2.c

EDIT: potential wine issue with 1.1.14

---

### Post by adamgram on 2009-02-09
Anyone want to be so kind as to help me get this stupid thing to work on my computer?  I have a dual boot setup and the card works fine in Windows, but I get nothing in Ubuntu.  Here's my setup:

Dell Dimension E521
Ubuntu 8.04
Creative Labs SB X-Fi 

I downloaded the Creative Driver from their website, but I don't think it's properly installed.  When I CD to the folder and sudo make install, I get the message:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Invalid module format
make: *** [install] Error 1

I'm a little confused at what's going on with this card.  I read that they released their source code and found various somewhat confusing reports regarding unstable drivers developed by others.  Can anyone clear this up for me?  Where should I go to get a different driver to try?

Furthermore, I want to use this computer for recording music, so if the driver makes the card work 'just okay' I still may be better off in windows or buying a different sound card.  Can anyone comment on how well it works if I can get it to work or what to expect of it in the near future?

Thanks in advance.Here are some outputs that might be helpful (copied and pasted those relating to the soundcard):

dmesg
[ 1812.977335] ctxfi: disagrees about version of symbol struct_module

---

lspci
04:09.0 Multimedia audio controller: Creative Labs SB X-Fi

---

lsmod
snd_hda_intel         384176  3 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pc

(no mention of ctXFi)

---

lspci -v
04:09.0 Multimedia audio controller: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 0, IRQ 11
	I/O ports at 9800 [size=32]
	Memory at efc00000 (64-bit, non-prefetchable) [size=2M]
	Memory at e8000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel modules: ctxfi

---

### Post by Brebs on 2009-02-09
> **adamgram said:**
> sudo make install
For a *re*-compilation, you are missing the all-important first command:

make clean

Since you ran with sudo, your compilation files are probably owned by root, so you'll probably need to add "sudo" to the start of "make clean".

---

### Post by NullHead on 2009-02-09
> **adamgram said:**
> Anyone want to be so kind as to help me get this stupid thing to work on my computer?  I have a dual boot setup and the card works fine in Windows, but I get nothing in Ubuntu.  Here's my setup:

Dell Dimension E521
Ubuntu 8.04
Creative Labs SB X-Fi 


Well to start, Creative's latest version of their driver is not compatible with Ubuntu 8.04. You can either upgrade to Ubuntu 8.10 or you can use the OSS guide I gave a link to in this guide.

---

### Post by adamgram on 2009-02-09
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
?

I was just a little confused by this because it was posted before the source code was released so I wasn't sure if it was still valid.  Is OSS maintained by Ubuntu and now contains a driver that would work with this soundcard?  Sorry if these are nOOb questions, I don't really know what I'm doing.

---

### Post by NullHead on 2009-02-09
> **adamgram said:**
> [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
?

I was just a little confused by this because it was posted before the source code was released so I wasn't sure if it was still valid.  Is OSS maintained by Ubuntu and now contains a driver that would work with this soundcard?  Sorry if these are nOOb questions, I don't really know what I'm doing.

[LIST]
[*]Creative handed OSS a data sheet before they open-sourced their own drivers. 
[*]OSS is maintained by a group called 4-front technologies
[*]OSS does contain a driver that works with your X-Fi sound card
[/LIST]

---

### Post by braingram on 2009-02-09
I was looking at the opensound page and the first few commands look like they could be improved. Under stopping alsa it says to run
```

sudo chmod 776 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist
```
and then:
```

sudo echo "blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd
blacklist soundcore" >> /etc/modprobe.d/blacklist
```
Wouldn't it be cleaner to run:
```

sudo rm /etc/modprobe.d/blacklist-oss
sudo ln -s /lib/linux-sound-base/noALSA.modprobe.conf /etc/modprobe.d/blacklist-alsa
```
I'm asking here because you guys seem to know more about the linux sound systems than I do. If the suggested commands look cleaner I'm more than willing to make the page edits.

---

### Post by adamgram on 2009-02-09
> **NullHead said:**
> [LIST]
[*]Creative handed OSS a data sheet before they open-sourced their own drivers. 
[*]OSS is maintained by a group called 4-front technologies
[*]OSS does contain a driver that works with your X-Fi sound card
[/LIST]

thanks!  I'll try that tonight...

---

### Post by NullHead on 2009-02-09
> **braingram said:**
> I was looking at the opensound page and the first few commands look like they could be improved. Under stopping alsa it says to run
```

sudo chmod 776 /etc/modprobe.d/blacklist
sudo cat /lib/linux-sound-base/noALSA.modprobe.conf >> /etc/modprobe.d/blacklist
```
and then:
```

sudo echo "blacklist snd_hda_intel 
blacklist snd_mixer_oss 
blacklist snd_pcm
blacklist snd_timer
blacklist snd_page_alloc
blacklist snd_hwdep
blacklist snd
blacklist soundcore" >> /etc/modprobe.d/blacklist
```
Wouldn't it be cleaner to run:
```

sudo rm /etc/modprobe.d/blacklist-oss
sudo ln -s /lib/linux-sound-base/noALSA.modprobe.conf /etc/modprobe.d/blacklist-alsa
```
I'm asking here because you guys seem to know more about the linux sound systems than I do. If the suggested commands look cleaner I'm more than willing to make the page edits.

I see you suggested that same change in the discussion page. Honestly, I'm not very experienced with OSS. I would try to ask the page maintainer, dtl131 (Dave Lentz). 

Really, I wouldn't mess with the wiki. It works, and if it ain't broke, don't fix it. If however, you have tested your own suggestion and proven that it works, than change it.

---

### Post by adamgram on 2009-02-09
okay... I got the driver installed!  thanks again for the help of the how-to and braingram... the only problem now is that it's terrible!  that, or something is still not set up right... any time I play an audio file there is a LOUD (I'm talking afraid-my-speakers-were-blown-loud) static sound for a split second.  Not only that, but once the sound does start, opening and closing windows (nothing intense, just the terminal or firefox), will cause the sound to cut in and out...

Is this just where they're at so far with the development of the driver?  if so, is there anything I should do to get updates automatically through the update manager?  It's unusable like this, unless there's something I can check to see if it's set up right...

---

### Post by NullHead on 2009-02-09
> **adamgram said:**
> okay... I got the driver installed!  thanks again for the help of the how-to and braingram... the only problem now is that it's terrible!  that, or something is still not set up right... any time I play an audio file there is a LOUD (I'm talking afraid-my-speakers-were-blown-loud) static sound for a split second.  Not only that, but once the sound does start, opening and closing windows (nothing intense, just the terminal or firefox), will cause the sound to cut in and out...

Is this just where they're at so far with the development of the driver?  if so, is there anything I should do to get updates automatically through the update manager?  It's unusable like this, unless there's something I can check to see if it's set up right...

I seem to remember having those issues as well when I used Ubuntu 8.04. I'm curious, did you do this step: > sudo apt-get install -y esound esound-clients esound-common libesd0

I don't know as if there is a fix for the static, but I do know if you try using a different audio player, you might have more luck. Try using Audacious for example. Just search for Audacious in synaptic package manager. 

Also make sure you have all of your restricted codecs installed.

---

### Post by Spudz0r on 2009-02-18
am i right to assume i can use these drivers on my auzentech prelude as they both use the x-fi chipset?

just thought i should check as this is one of the last things i need to get working. (that and if i could actually get live messenger 8.5 working (yes i know there are OS alternatives.. but i like the humour value of running it))

---

### Post by bjorkiii on 2009-02-19
Yes they do work for the prelude i have used them in the past with no problem.

---

### Post by Spudz0r on 2009-02-19
got it working..

alas, has that annoying fraction of a second static pre and post audio.

is there any fix for this?

---

### Post by armagheddonsgw on 2009-02-21
tried this, worked for sound tests (System > Preferences > Sound > Sounds)
but for NOTHING else. atm its treating my line-out as a line-in :(

its a start i guess :|
if its of any significance, im running 8.10...

---

### Post by soleliquido on 2009-02-25
I've installed last week and these drivers work for me.
BUT NOT IN SURROUND.
I got a 5.1 Creative Surround system. Front speakers and subwoofer work but rear speakers not.

Ive tried different configurations of pulse audio and asoundrc, ECC.here they are

```
ste@SteGrande:~$ cat /etc/pulse/daemon.conf
# $Id: daemon.conf.in 2175 2008-03-27 23:39:10Z lennart $
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307
# USA.

## Configuration file for the PulseAudio daemon. See pulse-daemon.conf(5) for
## more information. Default values a commented out.  Use either ; or # for
## commenting.

; daemonize = no
; fail = yes
; disallow-module-loading = no
; use-pid-file = yes
; system-instance = no
; disable-shm = no

; high-priority = yes
; nice-level = -11

; realtime-scheduling = no
; realtime-priority = 5

; exit-idle-time = -1
; module-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; default-script-file = 

; log-target = auto
; log-level = notice

resample-method = speex-float-1
; disable-remixing = no

; no-cpu-limit = no

; rlimit-as = -1
; rlimit-core = -1
; rlimit-data = -1
; rlimit-fsize = -1
; rlimit-nofile = 256
; rlimit-stack = -1
; rlimit-nproc = -1
; rlimit-memlock = -1
; rlimit-nice = 31
; rlimit-rtprio = 9

; default-sample-format = s16le
default-sample-rate = 48000
default-sample-channels = 6

default-fragments = 8
default-fragment-size-msec = 10
```

```
ste@SteGrande:~$ cat /etc/pulse/default.pa
#!/usr/bin/pulseaudio -nF
#
# This file is part of PulseAudio.
#
# PulseAudio is free software; you can redistribute it and/or modify it
# under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# PulseAudio is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with PulseAudio; if not, write to the Free Software Foundation,
# Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA.

.nofail

### Load something into the sample cache
#load-sample-lazy x11-bell /usr/share/sounds/gtk-events/activate.wav
#load-sample-lazy pulse-hotplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-coldplug /usr/share/sounds/startup3.wav
#load-sample-lazy pulse-access /usr/share/sounds/generic.wav

.fail

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
load-module module-alsa-sink
load-module module-alsa-source device=hw:0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
#load-module module-detect
.endif

### Load several protocols
.ifexists module-esound-protocol-unix.so
load-module module-esound-protocol-unix
.endif
load-module module-native-protocol-unix

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

### Load the RTP reciever module (also configured via paprefs, see above)
#load-module module-rtp-recv

### Load the RTP sender module (also configured via paprefs, see above)
#load-module module-null-sink sink_name=rtp format=s16be channels=2 rate=44100 description="RTP Multicast Sink"
#load-module module-rtp-send source=rtp.monitor

### Load additional modules from GConf settings. This can be configured with the paprefs tool.
### Please keep in mind that the modules configured by paprefs might conflict with manually
### loaded modules.
.ifexists module-gconf.so
.nofail
load-module module-gconf
.fail
.endif

### Automatically restore the volume of playback streams
load-module module-volume-restore

### Automatically restore the default sink/source when changed by the user during runtime
load-module module-default-device-restore

### Automatically move streams to the default sink if the sink they are
### connected to dies, similar for sources
load-module module-rescue-streams

### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle

### Load X11 bell module
#load-module module-x11-bell sample=x11-bell

### Register ourselves in the X11 session manager
# Deactivated by default, to avoid deadlock when PA is started as esd from gnome-session
# Instead we load this via /etc/xdg/autostart/ and "pactl load-module" now
# load-module module-x11-xsmp

### Publish connection data in the X11 root window
.ifexists module-x11-publish.so
.nofail
load-module module-x11-publish
.fail
.endif

### Make some devices default
#set-default-sink output
#set-default-source input
```

```
ste@SteGrande:~$ cat /etc/asound.conf
pcm.!default {
  type pulse
}

ctl.!default {
  type pulse
}

pcm.pulse {
  type pulse
}

ctl.pulse {
  type pulse
}

pcm.equalized {
  type plug
  slave.pcm "equalizer";
}

pcm.equalizer {
  type ladspa

  # The output from the EQ can either go direct to a hardware device
  # (if you have a hardware mixer, e.g. SBLive/Audigy) or it can go
  # to the software mixer shown here.
  slave.pcm "plughw"
  #slave.pcm "plug:dmix"

  # Sometimes you may need to specify the path to the plugins,
  # especially if you've just installed them.  Once you've logged
  # out/restarted this shouldn't be necessary, but if you get errors
  # about being unable to find plugins, try uncommenting this.
  path "/usr/lib/ladspa"

  plugins [
    {
      label mbeq
      id 1197
      input {
       #this setting is here by example, edit to your own taste
       #bands: 50hz, 100hz, 156hz, 220hz, 311hz, 440hz, 622hz, 880hz, 
       #       1250hz, 1750hz, 25000hz, 50000hz, 10000hz, 20000hz
       #range: -70 to 30
        controls [ -1 -1 -1 -1 -5 -10 -20 -17 -12 -7 -6 -5 -5 0 0 ]
      }
    }
  ]
}

##Skype
pcm.snd_card {
        type hw
        card 0
}

pcm.dmixer {
        type dmix
        ipc_key 1024
        slave.pcm "snd_card"
        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        slave.pcm "snd_card"

        slave {
                period_size 256
                buffer_size 2048
                rate 44100
        }
}

pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
}

pcm.!skype {
        type plug
        slave.pcm "duplex"
}
```

and here it's a test I've tried, unsuccesfully...
```
~$ speaker-test -Dplug:surround51 -c6 -l1 -twav

speaker-test 1.0.17

La periferica di riproduzione è plug:surround51
I parametri dello stream sono 48000Hz, S16_LE, 6 canali
File WAV
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.surround51
Errore di riproduzione: -2,Nessun file o directory
^C
```


somebody knows how to work now??

thanks):P

[edit] almost forgetting: somehow, system sounds, like music on boot, are not working...
and everytime I try to open alsamixer or pulse audio config from terminal i receive the CONNECTION REFUSED error.... any suggestions?

---

### Post by borlosky on 2009-02-25
> **soleliquido said:**
> I've installed last week and these drivers work for me.
BUT NOT IN SURROUND.
I got a 5.1 Creative Surround system. Front speakers and subwoofer work but rear speakers not.

if I'm not mistaken, this driver only supports 2 channel stereo. It also does not support any external and internal i/o modules. I'd say your best bet is to wait for a new driver to be released now that creative has released driver as open source.

---

### Post by soleliquido on 2009-02-25
> **borlosky said:**
> if I'm not mistaken, this driver only supports 2 channel stereo. It also does not support any external and internal i/o modules. I'd say your best bet is to wait for a new driver to be released now that creative has released driver as open source.

hoping those at Creative do it soon! :guitar:
there is nothing on creative website (even in the opensource area) which talks about new opensource drivers!....

---

### Post by borlosky on 2009-02-25
> **soleliquido said:**
> hoping those at Creative do it soon! :guitar:
there is nothing on creative website (even in the opensource area) which talks about new opensource drivers!....

actually, creative won't be doing the driver, thats why they released it as open source. They basically released what they had working at the time. (a driver that has only limited functionality) and are now letting linux community re-write the driver.

here's the link to the driver page you're looking for: [http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum)

Right in the release notes for that driver you should see:
"This download is a [COLOR=Red]**source release driver**[/COLOR] providing Linux® 32-bit / 64-bit OS support for Creative Sound Blaster® X-Fi&#8482; and X-Fi Titanium series of audio devices."

so in other words: hopefully in one of the next distro releases, we'll eventually have a 100% working open source driver for x-fi cards. (or at least working better than creative's attempt at the driver)

---

### Post by soleliquido on 2009-02-25
> **borlosky said:**
> actually, creative won't be doing the driver, thats why they released it as open source. They basically released what they had working at the time. (a driver that has only limited functionality) and are now letting linux community re-write the driver.

here's the link to the driver page you're looking for: [http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum](http://support.creative.com/Products/ProductDetails.aspx?catID=1&CatName=Sound+Blaster&subCatID=208&subCatName=X-Fi&prodID=14065&prodName=X-Fi+Platinum)

Right in the release notes for that driver you should see:
"This download is a [COLOR=Red]**source release driver**[/COLOR] providing Linux® 32-bit / 64-bit OS support for Creative Sound Blaster® X-Fi™ and X-Fi Titanium series of audio devices."

so in other words: hopefully in one of the next distro releases, we'll eventually have a 100% working open source driver for x-fi cards. (or at least working better than creative's attempt at the driver)

ok, sorry. I was just hoping to have a full funcional device, in other words, and without excessive brainworkin (lazy italians...:lolflag:) .. whatever, that's a good new..thanks for that..i had not read that.

btw, if somebody could help me...i'm here :)
thanks):P

---

### Post by Stagnation on 2009-02-25
Thanks for the guide Nullhead. I was able to get my X-Fi going thanks to you.

I'm having one little issue though. The Volume Control on the panel looks like it's muted (it's not) and I can't control the volume by clicking it. I have to open the mixer to control the volume.

Any ideas?

---

### Post by mhenriday on 2009-03-03
**Nullhead**, as so many times before, your guide was a lifesaver after I updated to the **2.6.27-13** kernel. A suggestion, to aid those who like myself find their sound gone after a kernel update : you might want to consider putting a reminder on your first page to the effect that dependencies and drivers will have to be re-installed when a new version of the kernel has been installed....

Henri

---

### Post by NullHead on 2009-03-03
> **mhenriday said:**
> **Nullhead**, as so many times before, your guide was a lifesaver after I updated to the **2.6.27-13** kernel. A suggestion, to aid those who like myself find their sound gone after a kernel update : you might want to consider putting a reminder on your first page to the effect that dependencies and drivers will have to be re-installed when a new version of the kernel has been installed....

Henri

Good idea, thanks! :)

---

### Post by tracerbullet on 2009-03-08
Fantastic guide! It truly saved my sanity!

I had all but given up on this [S]piece of carp[/S] piece of hardware a few years ago, but now I finally got it working 100% thanks to your excellent step-by-step. :KS :KS

---

### Post by wd5gnr on 2009-03-09
Well I'm bummed out. I had this working some time ago. I've been using my onboard sound for speakers and my XFi for PSK31 (ham radio). I switched out motherboards today and the new motherboard has ALS888 codec. In the process of trying to get it to work (I did get it to work) I lost the XFi! So I went to rebuild it and now I am getting the dreaded:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And, of course, dmesg tells me (among other things):

[   19.042270] ctxfi: disagrees about version of symbol snd_ctl_add
[   19.042273] ctxfi: Unknown symbol snd_ctl_add
[   19.042320] ctxfi: disagrees about version of symbol snd_pcm_new
[   19.042321] ctxfi: Unknown symbol snd_pcm_new

etc. etc. etc.

I've tried removing/reinstalling Alsa, kernel source, etc. etc. but no go. Anyone who's had this problem resolved it? I'm off to read all the posts in this thread carefully, but while I've seen some who have this problem it hasn't been clear to me how/if it was resolved.

---

### Post by NullHead on 2009-03-09
> **wd5gnr said:**
> Well I'm bummed out. I had this working some time ago. I've been using my onboard sound for speakers and my XFi for PSK31 (ham radio). I switched out motherboards today and the new motherboard has ALS888 codec. In the process of trying to get it to work (I did get it to work) I lost the XFi! So I went to rebuild it and now I am getting the dreaded:

FATAL: Error inserting ctxfi (/lib/modules/2.6.27-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)


And, of course, dmesg tells me (among other things):

[   19.042270] ctxfi: disagrees about version of symbol snd_ctl_add
[   19.042273] ctxfi: Unknown symbol snd_ctl_add
[   19.042320] ctxfi: disagrees about version of symbol snd_pcm_new
[   19.042321] ctxfi: Unknown symbol snd_pcm_new

etc. etc. etc.

I've tried removing/reinstalling Alsa, kernel source, etc. etc. but no go. Anyone who's had this problem resolved it? I'm off to read all the posts in this thread carefully, but while I've seen some who have this problem it hasn't been clear to me how/if it was resolved.

I have not found a solution to this yet. 

There are things you can try, like running "make clean" inside the x-fi source directory, making sure alsa is fully modprobed, and making sure that the driver gets fully uninstalled before re-installation. 

I can't say for sure if anything I just listed will do the trick, but if you do figure it out, please let me know :)

---

### Post by wd5gnr on 2009-03-10
Yes, I've tried make clean, reloading the original driver source, hinking around with the module dependencies in the source tree, etc. It looks as though it is getting the right headers, but at load time it can't resolve the kernel symbols. Very odd...

---

### Post by groggin on 2009-03-12
should i use this giude for my sb audigy?

                   thanks - i cant hear a thing  ](*,)

---

### Post by NullHead on 2009-03-12
> **groggin said:**
> should i use this giude for my sb audigy?

                   thanks - i cant hear a thing  ](*,)

I really wouldn't ... 

I can't say what will happen if you do. The driver isn't exactly the kind of driver you want to go playing with either. It tends to break systems at random.

---

### Post by groggin on 2009-03-13
> **NullHead said:**
> I really wouldn't ... 

I can't say what will happen if you do. The driver isn't exactly the kind of driver you want to go playing with either. It tends to break systems at random.

K thanks **nullhead** i'll just keep trying  ...  :redface:

---

### Post by CK05 on 2009-03-17
Hey, I got this working great thanks for the guide! But only certain formats work properly for me.

All my movies (mp4, mkv, avi, etc.. work), all my Flac files work but internet radio streaming and mp3's are completely distorted and really loud. Gave me a fright when I first played this with my speakers on. 

I tried searching and couldn't find anyone having the same problem. Someone mentioned something similar (fluendo mp3 codec), but I don't have that installed. 

Using 32bit 8.10. Thank you for your help.

---

### Post by MadCatmkII on 2009-03-17
I do apologise if I'm being dense and have missed this somewhere above, but is it possible to get function out of the digital-out at the back of the card via ALSA? I've made one failed attempt at installing OSS and that for some reason made it impossible to recompile the creative drivers. (I've since re-installed as well, so I'm afraid I can't give more information about what went wrong.)

---

### Post by bcschmerker on 2009-03-18
Thanks to y'all for giving me an advance brief of sorts on audio upgrades for the re-equip of my Everex mid-tower.  I recently re-installed Ubuntu 7.10 on the Everex (pending a successful DVD-R write test on my new LG SATA optical, which I found to be prerequisite for full upgrade to either 8.04-LTS or 9.0x) for an Elitegroup Computer Systems GeForce6100SM-M motherboard, Version 1.0A (packing nVIDIA nFORCE 405 south bridge), and a 2.9 GHz Advanced Micro Devices Athlon 64 X2 (P/N ADO5600IAA5DO), which supersede an all-VIA Technologies motherboard with 1.5 GHz C7-D CPU.  My new planar sound chip is a Realtek ALC660-VD, which succeeds the VIA 'board's AC97 chip.

Given the expansion slot configuration of my new 'board (one PCI Express x8, one x1, and two legacy PCI 2.2), I anticipate a PCI Express x1 audio card; as of 18 March 2009, Creative Labs appears to be the only player in this field, so I'm watching the X-Fi driver situation closely.  What bugs should I watch out for in particular concerning drivers for Creative's state-of-the-art X-Fi Fatal1ty series?

---

### Post by Spudz0r on 2009-03-18
bugs you can expect:

only stereo is supported, some users get noise bursts at beginning and end of sounds, and others have issues getting wine to recognise it.

---

### Post by bcschmerker on 2009-03-19
> **Spudz0r said:**
> bugs you can expect:

only stereo is supported, some users get noise bursts at beginning and end of sounds, and others have issues getting wine to recognise it.

Stereo is just fine with me, as over-the-Web services can handle two-channel audio without problems.  I'll wait and see whether the noise-burst problem can be solved.

---

### Post by king2007 on 2009-03-22
Thanks Temüjin for the link : 
[http://insanecoding.blogspot.com/200...-in-linux.html](http://insanecoding.blogspot.com/200...-in-linux.html)
any chance on solved sound issues in newer versions of Ubuntu ?

---

### Post by NullHead on 2009-03-22
> **king2007 said:**
> Thanks Temüjin for the link : 
[http://insanecoding.blogspot.com/200...-in-linux.html](http://insanecoding.blogspot.com/200...-in-linux.html)
any chance on solved sound issues in newer versions of Ubuntu ?

I doubt you'll get any "out of the box" stuff happening in the newest ubuntu version, but the Creative driver is rather easy to setup and install on the current version of ubuntu, 8.10.

---

### Post by mhenriday on 2009-03-23
Hopefully, this [**[COLOR="Blue"]link[/COLOR]**]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html") to the page mentioned on Insane Coding's blog will work. When reading it, it might be wise to keep in mind that it describes the *status quo* as of May 2007. With respect to **Ubuntu**, things seem to have improved since then....

Henri

---

### Post by jofunni on 2009-03-24
I've the similar issue of the boot sound missing before in 8.10. After deleting .asoundrc file, the sound came back.

---

### Post by king2007 on 2009-03-24
> **mhenriday said:**
> Hopefully, this [**[COLOR="Blue"]link[/COLOR]**]("http://insanecoding.blogspot.com/2007/05/sorry-state-of-sound-in-linux.html") to the page mentioned on Insane Coding's blog will work. When reading it, it might be wise to keep in mind that it describes the *status quo* as of May 2007. With respect to **Ubuntu**, things seem to have improved since then....
Henri
Henri, I noticed it was written in 2007 ie two years ago, but hey i reported a bug on launchpad a few weeks ago - not quite according to the rules i noticed later on - but the sound issue still is around. when i tell you i am trying to use windows 7 bèta the sound from my speakers is terrible..... should it not be crystal clear ?? 
they are creative desktop-speakers and using kernel 2.6.27-10 sound (under ubuntu intrepid ibex)  is wonderful !! 
kernelversions -11, -12, -13 and -14 STILL no sound

---

### Post by OblivionPi on 2009-03-24
Well, I've ran into something of a hiccup (in part because of me switching over to 64bit and reinstalling 8.04 when I had the sound finally working for an x-fi xtreme music). I haven't been using 8.10 due to issues getting a gui and recognizing the nvidia drivers (I still try workarounds, but I'm focusing on 8.04 for now as I've had fewer issues).

With the 32 bit, eventually managed to get great sound following the OpenSound page for shunting off Alsa and installing oss. Very well in fact, I was very impressed with the sound quality. No real issues, just went step by step and voila.

Now, however, that's changed. I figured it'd be an easy switchover, and I'd just need to retrace my previous steps. So, I have, and when I hit the Build and Install steps for OSS... thats when the hiccups began. Everything else seems fine up until then. I've done a clean reinstall in the meantime, and I'm giving it another shot, but this is what I ran into.

Setting up full REGPARM compiling environment
srcdir=/usr/src/oss-devel
Source directory is /usr/src/oss-devel
Build directory is /home/tim/oss41build
Build tree created OK
In file included from /usr/src/oss-devel/setup/srcconf.c:417:
/usr/src/oss-devel/setup/gen_driver_linux.inc:1: error: expected identifier or &#8216;(&#8217; before &#8216;{&#8217; token
/usr/src/oss-devel/setup/setupdir.sh: 141: ./srcconf: not found
Source configuration failed

Build ID will become 200903250146
make: *** No rule to make target `dep'.  Stop.
Directory preparation complete.
Build ID will be 081213


is what I get after the No Warning Checks command. Trying to go further with the make:

make: *** No rule to make target `all', needed by `build'.  Stop. 

with the sudo make deb it repeats.

And with the sudo dpkg -i oss*.deb

dpkg: error processing oss*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 oss*.deb

Being an Ubuntu newbie, I'm having some difficulty determining where the problem actually lies considering a successful installation previously, and I've got the feeling I messed up a step along the way. Input of course, would be greatly appreciated.
**Solution**
Well, as I was having issues with the mercurial and tarball, I switched instead to downloading the 64 bit debian. As it was downloaded to my desktop, the main thing was remembering (I'm a newbie, folks) to get into my home directory first in the terminal when installing it with the sudo dpkg -i oss*.deb otherwise, it'll never show up. *slaps forehead*. Trivial thing to add to the OSS page, but for us new guys, making a reference to get into your proper directory first before attempting the cmd may help.

---

### Post by mhenriday on 2009-03-25
King2007, I, too, observe something similar to that you describe - on my triple boot machine, I am, thanks to **Nullhead**'s wonderful tutorial and the **Creative 1.00** driver, now getting excellent sound from my **Creative Soundblaster X-Fi** on 64-bit **Ubuntu Intrepid**, as well as on 32-bit **Windows Vista Business**. But on 32-bit **Windows Server 2008**, I only get white noise. Most irritating !...

Henri

---

### Post by mhenriday on 2009-03-27
Just a brief message to say that **Nullhead**'s tutorial seems to function as well after an upgrade to the newly released **Jaunty** beta as it did in **Intrepid**. The **Creative** driver must be re-installed, of course, as there's been a kernel upgrade - those who had previously installed the driver on **Intrepid** and have now upgraded using the Update Manager can start from Step 3 in the tutorial....

Henri

---

### Post by bernardfrancois on 2009-04-13
Hi,

I'm trying to make it work on ubuntu 8.04. I would really like to have it working there, so I can stay with an LTS version.

First of all, I'm not sure if it would work as I don't know which type of X-Fi card I have.
I checked in Windows in dxdiag, the control panel and in some tools of creative, and all I can find is the name "**Creative SB X-Fi**".

When I do **sudo lspci -v**, I get some info about the sound card. Maybe the number 6002 maps directly to the type of X-Fi card. 
So this lspci's output for the sound card:
```

04:00.0 Audio device: Creative Labs SB X-Fi
        Subsystem: Creative Labs Unknown device 6002
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
        Memory at dfc00000 (64-bit, non-prefetchable) [size=2M]
        Memory at d8000000 (64-bit, non-prefetchable) [size=64M]
        I/O ports at af00 [size=32]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

```
        
So, this is what I did as an attempt to make it work:
[list]
[*] Compiling the v1.00 creative driver (didn't work because of the compilation errors)
[*] Installing a patched creative driver which I found somewhere on the forums (the installation interrupted somewhere halfway)
[*] Uninstalling the patched creative driver in recovery mode
[*] Following the guide to install OSS ([https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)).
[/list]

While following the OSS guide, I had to install **libesd0**. There I got a message that I needed to remove the package **libesd0-alsa**, which I did.
Then I used the following .deb file to install OSS: **oss-linux-4.1-1052_i386.deb**
Everything seemed to complete succesfully, and in the end of the .deb installation I got a message "**Detected Creative SB X-Fi *EARLY BETA***" (I hope they mean the driver is an early beta, and not the sound card, but for several reasons I'm not very sure of that ;)).

After all this, I don't have any sound, so here are some outputs I have:

This is the output of **osstest**:
```

Sound subsystem and version: OSS 4.1 (b 1052/200903240610) (0x00040100)
Platform: Linux/i686 2.6.24-22-386 #1 Mon Nov 24 17:51:53 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/oss_sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (UAA) output
Note! Device is in use (by PID 0/VMIX) but will try anyway
- Performing audio playback test... 
  <left> Device returned error: Input/output error
/dev/oss/oss_sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (UAA) input
- Skipping input only device

*** Some errors were detected during the tests ***

```
        
The output of **sudo alsa unload**:
```

Unloading ALSA sound driver modules: (none loaded).

```
 
The output of **ossinfo**:
```

Version info: OSS 4.1 (b 1052/200903240610) (0x00040100) 
Platform: Linux/i686 2.6.24-22-386 #1 Mon Nov 24 17:51:53 UTC 2008 (ubuntu)

Number of audio devices:        2
Number of audio engines:        6
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: oss_sbxfi0 Sound Blaster X-Fi (UAA)
    PCI device 1102:0005, subdevice 1102:6002
 2: oss_usb0 USB audio core services


Mixer devices
 0: Sound Blaster X-Fi (UAA) (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (UAA) output   /dev/oss/oss_sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (UAA) input    /dev/oss/oss_sbxfi0/pcmin0  (device index 1)

``` 

When I call **dmesg | less**, I see the normal stuff in the beginning, but apparently nothing about the sound card. Then, further down in the output, I see a huge amount of messages like this (every time the same message, with just a few milliseconds between messages):
```

 [  268.922441] osscore: Output timed out on audio engine 2/'Sound Blaster X-Fi (
UAA) output (vmix)' (count=0)

```

When I call **ossmix**, everything seems to be okay with the volumes.

When I go to **System>Preferences>Sound>Devices**, the drop-down menu for 'Default Mixer Tracks' is empty (see screenshot)



So, if anyone can, please help me to make it work with OSS. If there's no way to do it, I'll revert back to alsa and try that. If that doesn't work neither, I'll have to decide if I'll upgrade to 8.1O or wait until the next LTS release (or get another sound card).

---

### Post by NullHead on 2009-04-14
@bernardfrancois:

Try rmmoding the following and run "**sudo soundoff**" and "**sudo soundon**"

snd_hda_intel 
snd_mixer_oss 
snd_pcm
snd_timer
snd_page_alloc
snd_hwdep
snd
soundcore

Use your head with this. If rmmod complains that a module us in use by X, rmmod that module and try again.

---

### Post by bernardfrancois on 2009-04-14
I just tried this, but it didn't help. **osstest** and **ossinfo** give exactly the same output as before.

Note to other people trying this: soundon and soundoff were in my /usr/sbin folder, which is not included in the path here, so I had to call **sudo /usr/sbin/soundoff** and **sudo /usr/sbin/soundon**.

---

### Post by JohnFante on 2009-04-15
IGNORE THIS POST. MY SPEAKERS DIED. SORRY!

I am running Jaunty with all the updates until now.

I followed the guide and have sound :-)

Strangely sound dos not work in Wine and Cedega!?! I have switched both to OSS but still no sound.

In 8.10 everything, inkluding Wine and Cedega, worked fine.

Any suggestions on how to get sound in Wine and Cedega? 

I have not uninstalled ALSA and upgraded OSS. Maby that will do the trick?

Thank you in advance.

---

### Post by bernardfrancois on 2009-04-15
I checked the forums of OSS, and there's a way to manually select which type of X-Fi card you have:
[http://4front-tech.com/forum/viewtopic.php?t=2972](http://4front-tech.com/forum/viewtopic.php?t=2972)

Apparently, **if it doesn't work with any of the four types in /usr/lib/oss/conf/oss_sbxfi.conf, it won't work with OSS**.

I also posted something about my case in the following thread on the same forum (I did this before reading the stuff of the first link).
[http://4front-tech.com/forum/viewtopic.php?t=3117](http://4front-tech.com/forum/viewtopic.php?t=3117)

It didn't work with any type for me, so I'll wait a bit to see if there's any useful reply on the OSS forums, and otherwise I'll try alsa...

If alsa doesn't work, I'll try installing the creative driver when running from a 8.10 live cd, just to see if it would work under 8.10 for my card.

This may also be useful to some readers: according to some posts I saw on the OSS forum, **pci-e versions of x-fi don't work with OSS**.

[edit]
I just tried with the 8.10 live cd and creative's driver, and it works! There are only some minor issues (there's no sound from the center and rear speakers - even if it's just 2.1, and I need to use alsamixer or some other one as the default one in gnome doesnt work).

**Did anyone try to fix the compilation errors for creative's driver that occur under ubuntu 8.04?** If no one did, I could give it a try...
[/edit]

[edit2]
It works when I run the 8.10 live cd and install creative's driver. I got some replies on the OSS forum, but no working solution til now. I'm currently waiting for further advice on the forums of OSS.
[/edit2]

---

### Post by Geoff I on 2009-04-16
I have just successfully installed the drivers as to your instruction, I have the Creative X-Fi Elite Pro, I would like to say it would be nice to get the front box to work and will watch this thread to see if it is possible at a later date.

Many thanks.

---

### Post by azmanam on 2009-04-19
Everything seems to go well until sudo make install:

```
~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Module ctxfi not found.
make: *** [install] Error 1
```

system:

gateway box
p4 3GHz processor
1 GB RAM
NVidia-GEForce FX 5200 DDR 128MB Video Card
Hauppauge HVR-1600 Tuner Card
Creative Sound Blaster X-Fi Card

---

### Post by azmanam on 2009-04-21
bump

Do I need to download this module somewhere?  Or reinstall the last round of updates?

---

### Post by NullHead on 2009-04-22
I can't say for sure what's wrong with it. 

I guess, try using OSS v4.

---

### Post by bcschmerker on 2009-04-22
> **bernardfrancois said:**
> I checked the forums of OSS, and there's a way to manually select which type of X-Fi card you have:
[http://4front-tech.com/forum/viewtopic.php?t=2972](http://4front-tech.com/forum/viewtopic.php?t=2972)

Apparently, **if it doesn't work with any of the four types in /usr/lib/oss/conf/oss_sbxfi.conf, it won't work with OSS**.

I also posted something about my case in the following thread on the same forum (I did this before reading the stuff of the first link).
[http://4front-tech.com/forum/viewtopic.php?t=3117](http://4front-tech.com/forum/viewtopic.php?t=3117)

It didn't work with any type for me, so I'll wait a bit to see if there's any useful reply on the OSS forums, and otherwise I'll try alsa....I'm already in a holding pattern for new sound for my Everex, as the [Creative Sound Blaster X-Fi Fatal1ty](http://us.creative.com/) is the only available sound card for PCI-Express.  Although it was started 27 May 2008, the [Advanced LinUX Sound Architecture](http://www.alsa-project.org/) development work for the Creative X-Fi series may take some time yet, as the E-mu 20K1 is a completely different architecture from the already-supported 10Kx (see [Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) at ALSA-Project.org).  The ALSA Project may have a solution ready by the time Ubuntu 10 ("Limber Lemur," perhaps?) is ready for testing.

---

### Post by bernardfrancois on 2009-04-22
I contacted OSS and offered to help them to make their driver work with my card, so they could improve their compatibility, and this is the answer I got from a OSS developer:

[http://4front-tech.com/forum/viewtopic.php?p=12412#12412](http://4front-tech.com/forum/viewtopic.php?p=12412#12412)
[quote=hannu at 4front-tech.com forum]
I'm not working on the X-Fi driver any more. It proven to be completely impossible because:

[list]
[*] The chipset is extremely complex and very briefly documented. Learning to understand the chip is likely to take longer than the card will stay in production.
[*] There is large number of different models of the card and and they all require special handling. It is impossible to find out what kind of handling is going to be required by new models.
[*] The development of a better driver is likely to take a man year or two. There are better ways to spend that time.
[*] I don't use X-Fi cards myself.
[/list]

The current driver is based on some manufacturing test program provided by Creative. That code is two years old and it does what it does. Unfortunately it doesn't do anything good with the latest card revisions.[/quote]

I don't really understand this view, as there's a working open source driver from creative available, and as I believe the X-Fi is quite a main stream card. Anyway, I can now move on and try other solutions.

---

### Post by bernardfrancois on 2009-04-22
> **bcschmerker said:**
> I'm already in a holding pattern for new sound for my Everex, as the [Creative Sound Blaster X-Fi Fatal1ty](http://us.creative.com/) is the only available sound card for PCI-Express.  Although it was started 27 May 2008, the [Advanced LinUX Sound Architecture](http://www.alsa-project.org/) development work for the Creative X-Fi series may take some time yet, as the E-mu 20K1 is a completely different architecture from the already-supported 10Kx (see [Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) at ALSA-Project.org).  The ALSA Project may have a solution ready by the time Ubuntu 10 ("Limber Lemur," perhaps?) is ready for testing.

Note that I don't have a PCIe card, and it's working in a 8.10 live session with the creative driver. I'm just trying to make it work on my 8.04 LTS installation.

---

### Post by drguerra on 2009-04-23
Sound works great with my X-Fi XtremeMusic using this guide.

Is there a way to enable 5.1 surround sound using my XtremeMusic? Since I use this PC as a HTPC.

---

### Post by NullHead on 2009-04-23
> **drguerra said:**
> Sound works great with my X-Fi XtremeMusic using this guide.

Is there a way to enable 5.1 surround sound using my XtremeMusic? Since I use this PC as a HTPC.

I'm sorry, there is no way to enable 5.1 audio using the current version of these particular drivers.

---

### Post by drguerra on 2009-04-23
Is it possible to enable 5.1 with the xtrememusic using any drivers on ubuntu?

---

### Post by drguerra on 2009-04-23
Oh. It seems that youtube and other internet based (flash?) audio doesn't play. Just audio from movies and music on my hard drive.

How can I solve this?

---

### Post by NullHead on 2009-04-23
> **drguerra said:**
> Oh. It seems that youtube and other internet based (flash?) audio doesn't play. Just audio from movies and music on my hard drive.

How can I solve this?

Which driver did you install? Creative's or the OSS driver?

---

### Post by cros13 on 2009-04-24
If you installed OSS you need the -extrasound package for adobe flash.

---

### Post by pierre.s.rosen on 2009-04-24
Just wanted to confirm that I was able to install the Creative drivers following the procedures in the first post on Ubuntu 9.04 (Jaunty Jackalope) and that I have sound working.  :guitar:

---

### Post by Bram77 on 2009-04-24
> **drguerra said:**
> Oh. It seems that youtube and other internet based (flash?) audio doesn't play. Just audio from movies and music on my hard drive.

How can I solve this?

I'm having the same problem with Jaunty x86. Also, there is no sound in games. In 8.10 all was fine with the Creative driver.

---

### Post by jtan325 on 2009-04-25
> **Bram77 said:**
> I'm having the same problem with Jaunty x86. Also, there is no sound in games. In 8.10 all was fine with the Creative driver.

You'll need to install the flashplugin-nonfree-extrasound package. @Nullhead, this might be good to mention in the instructions. 

+1 for these instructions working on x86 X-FI basic in 9.04. WOOT kthxbye

---

### Post by NullHead on 2009-04-25
> **jtan325 said:**
> You'll need to install the flashplugin-nonfree-extrasound package. @Nullhead, this might be good to mention in the instructions. 

+1 for these instructions working on x86 X-FI basic in 9.04. WOOT kthxbye

Thanks for the suggestion; I've updated the guide.

---

### Post by Frodo232 on 2009-04-26
+1 for the instructions, working in x64 as well

However in x64 the flashplugin-nonfree-extrasound is not available therefore no sound in youtube. Any suggestions for an x64 solution to this?

Frodo

---

### Post by asticinzano on 2009-04-26
I've packaged the X-Fi Linux drivers 1.00 for those who can't or don't want to compile it manually.

Prerequisites: Install dkms and build-essential
Tested on: Ubuntu 9.04 i386 (linux-image-generic and linux-image-server)

---

### Post by azmanam on 2009-04-26
> **azmanam:**

Everything seems to go well until sudo make install:

```

~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Module ctxfi not found.
make: *** [install] Error 1
```


Problem seemed to be incomplete installation of kernel upgrades.  Upon installation of 9.04, kernel updated successfully... no more problems with ctxfi.

But audio within MythTV still didn't work...

I must have done something different when I set MythTV up the first time, because the Audio page of Utilities-Setup:Setup:General used to have dev/dvb1 for the output device and mixer device.  Changed to ALSA:default in both cases, and audio now works in MythTV.

Thanks for the help.

---

### Post by mhenriday on 2009-04-26
> **Frodo232 said:**
> +1 for the instructions, working in x64 as well

However in x64 the flashplugin-nonfree-extrasound is not available therefore no sound in youtube. Any suggestions for an x64 solution to this?

Frodo

**Frodo**, at the moment I'm listening to the ***YouTube*** version of the Pachelbel *Canon in D Major* (the one with the portrait of Mozart) on **Jaunty** on my AMD x86_84 setup ; all that seems to be required, in addition to following **Nullhead**'s instructions at the beginning of this thread is to install the *flashplugin-nonfree* via Synaptic - it is available from the multiverse repositories. Good luck !...

Henri

---

### Post by Frodo232 on 2009-04-26
> install the flashplugin-nonfree via Synaptic

Just checked what flashplugin packages I have installed and I have flashplugin-nonfree and flashplugin-installer both installed

Still no sound :(

This was a fresh install of 9.04, could that make the difference?

and as its x64 I can't install flashplugin-nonfree-extrasound as its i383 only

Frodo232

---

### Post by mhenriday on 2009-04-27
**Frodo232**, I still think that the origin of the sound problem you are encountering lies elsewhere, as I get excellent sound without the i386 flashplugin-nonfree-extrasound package, but have you tried using force architecture (sudo dpkg --force-architecture -i «package name»*.deb, without quotes) to install the package ? It might be worth giving it a try, if for no other reason than to remove lack of the package from consideration when trouble-shooting your sound problem....

Henri

---

### Post by Frodo232 on 2009-04-27
Henri

> but have you tried using force architecture (sudo dpkg --force-architecture -i «package name»*.deb, without quotes) to install the package

That did not work either, but seeing as I have sound everywhere else your probably right that its a separate issue so rather than clutter up this thread I am going to start a new one.

Frodo

---

### Post by rabbit251 on 2009-04-27
> You'll apparently need the package "flashplugin-nonfree-extrasound" to get sound out of youtube/flash. To install it:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

Are you sure this is a good idea, considering the following from psyke83's [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")?

> 
3. Ensure the evil "libflashsupport" library is not installed:

```
$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
```

Note: the libflashsupport library was (and to a certain extent, still is) the most common cause of Firefox instability since the Hardy release, because many users have been misled into thinking they must install it to ensure Flash & PulseAudio can work correctly. If you notice any postings that recommend this library to be installed, please reply to the post and point them to this thread, or the bug report linked. The more people that are aware of this issue the better. Thanks!

---

### Post by NullHead on 2009-04-27
> **rabbit251 said:**
> Are you sure this is a good idea, considering the following from psyke83's [HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")?

Well Honestly, I don't know if it's a good idea or not. 

The last time I tested, was 8.10 and you needed libflashsupport to be able to hear flash sounds at all. From this guide, it sounds as if he knows some other way to get sound working. 

For now, I think you should ask him about flash support then. I haven't been testing on the new release yet, so I can't really say what's good or bad at this point.

---

### Post by Anfanglir on 2009-04-29
Good instructions mate, got my X-fi running in Jaunty.

thanx / Anfanglir

---

### Post by fr0gg on 2009-04-30
> **macuser2000 said:**
> Hey, creative released the final version of their x-fi driver! It works without configuring anything else! Download [http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz](http://ccftp.creative.com/manualdn/Drivers/AVP/10792/0x0343D29A/XFiDrv_Linux_Public_US_1.00.tar.gz) , extract it, open up a terminal and cd to the source files. When you done that, execute these two commands in terminal as root:

```
sudo make
sudo make install
```

Sound should work after you install it!

Nice, thanks for clearing that up mate, I've just dual booted and was unsure on how to install! Works though, well done guys! Speakers are a bit crackly, which they aren't in XP, I suppose it's a small sacrifice as opposed to not having sound at all heh.

---

### Post by rapsball4 on 2009-04-30
I'm having the same problem as Frodo232.  Everything works great on a new Jaunty x64 install except YouTube and I can't get the recommended package to fix it either.  Any other recommendations for a work-around?  I was hoping to finally replace Windows as my primary OS with this update but no Internet videos kinda kills that idea.

---

### Post by mhenriday on 2009-05-01
**Nullhead**, a couple of suggestions with regard to the new information that you've added to the instructions in the first posting to this thread - > There are reports of Creative's driver working on the new shiny Ubuntu 9.04. I've not tested this myself, but don't let that stop you. You'll apparently need the package "flashplugin-nonfree-extrasound" to get sound out of youtube/flash. To install it:
```
sudo apt-get install flashplugin-nonfree-extrasound
```
- as I've reported previously, the need for «flashplugin-nonfree-extrasound» doesn't seem to be absolute ; I for one have no problems getting sound when playing ***YouTube*** videos on my 64-bit **Jaunty** box without it. It might also be worthwhile pointing out that «sudo apt-get» method won't work on 64-bit machines, as a 64-bit version is not found in the repositories....

Henri

---

### Post by dmrazor on 2009-05-01
Well, I finally got around to trying all this but made the move to Jaunty first. Can confirm it's working like a charm *and* I can record sound as well. Also, the sound quality is much better than with the OSS driver.

Still need to check how things work with Wine, but will let you know what happens on that end.

Cheers for the excellent thread!

---

### Post by lleberg on 2009-05-02
I installed a X-Fi card a few days bock using this guide (and OSS4)..
but i have heard that there is a processor on the soundcard that enhances the soundquality from mp3 sources, a friend of mine said it makes a great deal of difference.
But  in windows he has to activate this feature.

Is it possible to do on ubuntu or is it jsut to forget it? :)
he card is a "Creative SB X-Fi Xtreme Audio"

Or is it working out of the box? :)

---

### Post by NullHead on 2009-05-02
> **lleberg said:**
> I installed a X-Fi card a few days bock using this guide (and OSS4)..
but i have heard that there is a processor on the soundcard that enhances the soundquality from mp3 sources, a friend of mine said it makes a great deal of difference.
But  in windows he has to activate this feature.

Is it possible to do on ubuntu or is it jsut to forget it? :)
he card is a "Creative SB X-Fi Xtreme Audio"

Or is it working out of the box? :)

I guess you can forget about doing that on linux. Only windows drivers support this feature.

---

### Post by asticinzano on 2009-05-03
> **lleberg said:**
> I installed a X-Fi card a few days bock using this guide (and OSS4)..
but i have heard that there is a processor on the soundcard that enhances the soundquality from mp3 sources, a friend of mine said it makes a great deal of difference.
But  in windows he has to activate this feature.

Is it possible to do on ubuntu or is it jsut to forget it? :)
he card is a "Creative SB X-Fi Xtreme Audio"

Or is it working out of the box? :)

What your friend told you about is the X-Fi Crystalizer. But it's not worth it anyway.
It's a much better sound filter than those made in earlier days but still...
I found it to be nice for the first two minutes. But in tracks with lots of dynamics or proper depth it sounds horribly artificial. It really depends with what you're listening to it. I suppose with 20$/€ speakers you notice an improvement but with good headphones the crystalizer seriously sucks.

---

### Post by dmrazor on 2009-05-04
> **dmrazor said:**
> Still need to check how things work with Wine, but will let you know what happens on that end.

Ok, follow-up on X-Fi /ALSA / Jaunty / Wine:

Working fine, good quality sound while running World of Warcraft in Wine and no distortion or anything when sound starts. 

There are some minor issues with Skype and Ventrilo (Wine). People listening to me report some sort of feedback echo, i.e. when I'm talking simultaneously with them they hear their own voices echoing back from my end. It's not feedback from my speakers to my microphone as I'm using a headset.

Does anyone have setup tips that might solve this?

BTW, also read that post on the pulseaudio page that says: remove the *evil* libflashsupport. Still need to try that one.

Raz.

---

### Post by Lhademmor on 2009-05-04
Hi NullHead, I have had an X-Fi Elite Pro card for quite some time, and have used your guide in the past to get it working. 
Now, seeing as ALSA will apparently work with jaunty I of course wanted to try it out, but I cannot get the ******* Creative driver to compile.

These are the errors I get: 
```

mp@mp-desktop:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.28-11-generic/build M=/home/mp/XFiDrv_Linux_Public_US_1.00
make[1]: Går til katalog '/usr/src/linux-headers-2.6.28-11-generic'
  LD      /home/mp/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/xfi.o
I filen inkluderet af /home/mp/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: advarsel: #warning "This file is deprecated"
I filen inkluderet af /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: advarsel: #warning "This file is deprecated"
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.o
I filen inkluderet af /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: advarsel: #warning "This file is deprecated"
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctpcm.o
I filen inkluderet af /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: advarsel: #warning "This file is deprecated"
/home/mp/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: advarsel: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctmixer.o
I filen inkluderet af /home/mp/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                   af /home/mp/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: advarsel: #warning "This file is deprecated"
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
/home/mp/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: advarsel: sammenligning med forskellige henvisningstyper mangler en typeomtvingelse
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mp/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/mp/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Forlader katalog '/usr/src/linux-headers-2.6.28-11-generic'
mp@mp-desktop:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-11-generic/kernel/drivers/ssound/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Fejl 1
mp@mp-desktop:~/XFiDrv_Linux_Public_US_1.00$ 

``` ([http://pastebin.ubuntu.com/164200/](http://pastebin.ubuntu.com/164200/))

Can someone please help me figure out what is wrong? Lack of sound is one of the few things keeping me from switching back to Ubuntu...

Also, I cannot even try the OSS way, because some files, including /etc/modprobe.d/blacklist, appears to have been renamed in newer versions of Ubuntu...

---

### Post by XanII on 2009-05-05
Upgraded to 9.04. I'll test today if my crappy X-fi wannabe card that seems to be actualy-based-on-that-earlier-creative card works with this. 

Im getting sick and tired of always going to the back of my computer and switch from Integrated soundcard to X-Fi ports when i boot to XP and vice versa on Linux.

---

### Post by mhenriday on 2009-05-05
**Dmrazor**, you don't mention whether your using 64-bit or 32-bit **Jaunty**, but I presume that you're using the same version of **Skype** that I do, namely, **2.0.0.72**. My problem is that on my **HP Pavilion d4595.se AMD Athlon 64 X2 5000+**, I can't get the microphone om my headset to work with **Skype** - no sound at all. How did you get your headset to work (aside from the echo problem, which in this context strikes me as relatively minor) ?...

Henri

---

### Post by remyxcore on 2009-05-05
Thank you!

This guide worked perfectly on my fresh install of 9.04

---

### Post by asticinzano on 2009-05-05
EDIT: I've noticed you tried to compile it as regular user which propably won't work at all.
sudo -s prior to all commands should do the trick.

As I remember correctly I had this error, too.
Everything went fine after I did this:

sudo -s
apt-get install build-essential
apt-get install linux-headers-generic
make uninstall <- very important when your ctxfi.ko cannot be installed properly after several compilation attempts.
make clean
make
make install

Or you can try my dkms-package I posted two pages ago:
[http://ubuntuforums.org/showpost.php?p=7153273&postcount=335](http://ubuntuforums.org/showpost.php?p=7153273&postcount=335)
Before installing it you have to make sure everything the XFi-Driver may have left has to be cleaned:

cd <Directory with XFI-1.00 sources>
sudo -s
make uninstall
reboot

After reboot:
sudo -s
apt-get install dkms
dpkg -i xfi-dkms_1.00_all.deb
> **Lhademmor said:**
> Hi NullHead, I have had an X-Fi Elite Pro card for quite some time, and have used your guide in the past to get it working. 
Now, seeing as ALSA will apparently work with jaunty I of course wanted to try it out, but I cannot get the ******* Creative driver to compile.

---

### Post by jtlobdell on 2009-05-06
Hello,

I followed the instructions on the first page, but ran into problems when apt-get couldn't find the right packages:
```
flashplugin-nonfree-extrasound
and
linux-headers-2.6.27-11-generic
```Though I was able to find and install the latter from packages.ubuntu.com, I still get errors when I attempt to build the driver:
```
# make
make -C /lib/modules/2.6.27-11-generic/build M=/home/john/Desktop/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/lib/modules/2.6.27-11-generic/build'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.27-11-generic/build'
make: *** [all] Error 2

```I don't really understand what's wrong, but I think it's the linux-headers package.


EDIT:
I reinstalled Ubuntu and I'm not having any problems installing the drivers now!
Thanks

---

### Post by AeroGT3 on 2009-05-06
Ok, so I can't get it to work with ALSA or OSS!!! In fact, I cannot even start OSS:(

With OSS I used this process:
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

I'm running jaunty, and when I executed:
```
sudo chmod 776 /etc/modprobe.d/blacklist
```
It gave me errors about the file not existing, etc. I continued as the next steps created the file. 

I used oss-linux-4.1-1052_amd64.deb and followed all the steps, installing that deb file with dpkg. Once finished, I rebooted and then typed "soundon" to start OSS. My system hangs every time I do that. No mouse, keyboard, nothing. I have to pull the power chord . . .

The last thing that's displayed before it locks up is:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.

I get the same error when I do the ALSA install from the original post. 

Any ideas? I've already purged and re-installed OSS. I did all the optional steps in that guide as well. 



I also tried asticanzano's method. Here is the output:
```
root@robert-desktop:~/XFiDrv_Linux_Public_US_1.00# make clean
rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions
root@robert-desktop:~/XFiDrv_Linux_Public_US_1.00# make
make -C /lib/modules/2.6.28-12-generic/build M=/home/robert/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-12-generic'
  LD      /home/robert/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/xfi.o
In file included from /home/robert/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
In file included from /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.o
In file included from /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctpcm.o
In file included from /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
/home/robert/XFiDrv_Linux_Public_US_1.00/ctpcm.c: In function &#8216;ct_alsa_pcm_create&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: warning: passing argument 2 of &#8216;snd_pcm_new&#8217; discards qualifiers from pointer target type
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctmixer.o
In file included from /home/robert/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 from /home/robert/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: warning: #warning "This file is deprecated"
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_src_rsc&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;put_srcimp_rsc&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_add&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_imap_delete&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c: In function &#8216;srcimp_mgr_destroy&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_amixer_rsc&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c: In function &#8216;put_sum_rsc&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;put_daio_rsc&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_add&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_imap_delete&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c: In function &#8216;daio_mgr_destroy&#8217;:
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: warning: comparison of distinct pointer types lacks a cast
/home/robert/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: warning: comparison of distinct pointer types lacks a cast
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/robert/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/robert/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-12-generic'
root@robert-desktop:~/XFiDrv_Linux_Public_US_1.00# make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/local, it will be ignored in a future release.
FATAL: Error inserting ctxfi (/lib/modules/2.6.28-12-generic/updates/dkms/ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
make: *** [install] Error 1
```


Cheers,

---

### Post by mhenriday on 2009-05-07
Today was the day for a kernel update from **2.6.28-11** to **2.6.28-12** on my x86_64 box ; as so many times previously, I prepared to re-install the **Creative** driver by cd-ing to the **XFiDrv_Linux_Public_US_1.00** folder and following the remaining steps in **Nullhead**'s tutorial. To my surprise, however, when all was done, while sound was working perfectly on websites like **YouTube** or that of certain newspapers, it didn't work with any of the music or video files I have stored on my **Jaunty** setup. OK, I thought, re-install everything from the very beginning, but alas, no joy - I still fail to get any sound on my music or video files. This is what I see on a terminal (my translations from the Swedish in square brackets []) :
> mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers-`uname -r`
Läser paketlistor [Read package lists]... Färdig [Done]
Bygger beroendeträd [Build a dependency tree]        
Läser tillståndsinformation... Färdig
build-essential är redan den senaste versionen [is alredy the latest version].
linux-headers-2.6.28-12-generic är redan den senaste versionen.
0 att uppgradera [to upgrade], 0 att nyinstallera [to install], 0 att ta bort [to delete] och 1 att inte uppgradera [not to upgrade].
mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.28-12-generic/build M=/home/mhenriday/XFiDrv_Linux_Public_US_1.00
make[1]: Går till katalogen [Go to the catalogue] "/usr/src/linux-headers-2.6.28-12-generic"
  LD      /home/mhenriday/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.o
I fil inkluderad från [In the file included from] /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c: I funktion "ct_alsa_pcm_create":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: varning: att skicka argument 2 till "snd_pcm_new" kastar kvalificerare från pekarmåltyp [warning : sending argument 2 to "snd_pcm_new" removes the qualifier from the pointer target type]
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion [In the function] "put_src_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: varning: jämförelse av skilda pekartyper saknar en typkonvertering [warning : comparison av different pointer types lacks a type conversion]
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "put_srcimp_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: varning: jämförelse av skilda pekartyper saknar en typkonvertering 
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_imap_add":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_imap_delete":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_mgr_destroy":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c: I funktion "put_amixer_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c: I funktion "put_sum_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "put_daio_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_imap_add":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_imap_delete":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_mgr_destroy":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Lämnar katalogen [Leaving the catalogue] "/usr/src/linux-headers-2.6.28-12-generic"
mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
Any suggestions as to what is going wrong here and. more importantly, how it can be repaired ?...

Henri

---

### Post by asticinzano on 2009-05-07
Maybe you need to compile as root. ;)

cd [B]XFiDrv_Linux_Public_US_1.00
sudo make
sudo make install
[/B]
> **mhenriday said:**
> Today was the day for a kernel update from **2.6.28-11** to **2.6.28-12** on my x86_64 box ; as so many times previously, I prepared to re-install the **Creative** driver by cd-ing to the **XFiDrv_Linux_Public_US_1.00** folder and following the remaining steps in **Nullhead**'s tutorial. To my surprise, however, when all was done, while sound was working perfectly on websites like **YouTube** or that of certain newspapers, it didn't work with any of the music or video files I have stored on my **Jaunty** setup. OK, I thought, re-install everything from the very beginning, but alas, no joy - I still fail to get any sound on my music or video files. This is what I see on a terminal (my translations from the Swedish in square brackets []) :

Any suggestions as to what is going wrong here and. more importantly, how it can be repaired ?...

Henri

---

### Post by mhenriday on 2009-05-07
Thanks for your speedy reply, **asticinzano** ! The solution to my problem was was even simpler - I simply closed the OS and re-booted* ! Now both files from websites like **YouTube** and my own music and video files are playing perfectly ! I suppose the main lesson to be learned from all this is not to panic - but in any event, all's well that ends well !...

Henri

*PS : For those interested in the details, what seems to have happened is that either during the kernal update or during the re-installation of the **Creative** driver, the value of the «default num» row in the «/boot/grub/menu» had of its own accord changed from «0» to «2», which meant that the computer was booting by default to an older version of the kernel, rather than to the new «2.6.28-12-generic» version to which the **Creative** driver had been installed. Using
```
gksudo gedit /boot/grub/menu.lst
```
I could edit the value back to «0», which restored my sound....

---

### Post by dmrazor on 2009-05-13
> **mhenriday said:**
> **Dmrazor**, you don't mention whether your using 64-bit or 32-bit **Jaunty**, but I presume that you're using the same version of **Skype** that I do, namely, **2.0.0.72**. My problem is that on my **HP Pavilion d4595.se AMD Athlon 64 X2 5000+**, I can't get the microphone om my headset to work with **Skype** - no sound at all. How did you get your headset to work (aside from the echo problem, which in this context strikes me as relatively minor) ?...

Henri
I'm using 32 bits Jaunty, with that same version of Skype. It started working for me when I set all to "pulse", and I'm currently checking if sound improves (i.e. echo goes away) when I set input directly to microphone.

Do a Google on ubuntu/skype/pulse and you'll find several posts relating to this setup.

Greetz,

Raz.

---

### Post by SniperClops on 2009-05-13
I am having a problem. The "Creative ALSA Driver X-fi" option in System->Preferences->Sound is not showing up. Anyone know why?

---

### Post by Reyes1986 on 2009-05-14
THANKS!! FINALLY AFTER 2 WEEKS I HAVE SOUND :) :popcorn:):P

I HAD TO UPGRADE FROM 8.04 TO 9.04, ANYBODY THAT HAS 8.04 I SUGGEST YOU UPGRADE!!

---

### Post by NullHead on 2009-05-14
Finally the relief we've been waiting for! 

Takashi Iwai, who works for Novell, and the guy who made the first X-Fi driver, has contacted Creative and has made a new driver for Alsa! This driver will be in the next kernel release, 2.6.31, and will most likely be included in the next release of Ubuntu. 

I read all this from here: [http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA) 

This is truly a good day for the world of linux! This makes me very happy!

When the next kernel releases, I hope to be building it and testing in on a fresh install of Ubuntu 9.04. I might even test it on Ubuntu 8.04 if anybody would like me to.

---

### Post by mhenriday on 2009-05-16
This is indeed splendid news, **Nullhead** ; thanks for the headsup! I wonder if the **Ubuntu** developers will make the **2.6.31** kernel available as a **Jaunty** update or if we'll all have to learn to compile our own or wait until **Karmic** is released. Looking forward in any event to your report !...

Henri

---

### Post by Ericj1186 on 2009-05-16
I am getting no sound at all.

I copied Nullhead's settings from here: [http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367](http://ubuntuforums.org/attachment.php?attachmentid=97496&d=1230165367).

I logged into youtube and no sound.  Any ideas?

Umm, odd thing.  I loaded Pidgen, and when a friend came on, it started playing sound.  Any reason why I am only getting sound in Pidgen?

In fact, sound ONLY works in Pidgen.  The start up sound did not work.  Help?

---

### Post by bcschmerker on 2009-05-17
> **NullHead said:**
> Finally the relief we've been waiting for! 

Takashi Iwai, who works for Novell, and the guy who made the first X-Fi driver, has contacted Creative and has made a new driver for Alsa! This driver will be in the next kernel release, 2.6.31, and will most likely be included in the next release of Ubuntu. 

I read all this from here: [http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA) 

...When the next kernel releases, I hope to be building it and testing in on a fresh install of Ubuntu 9.04. I might even test it on Ubuntu 8.04 if anybody would like me to.That would be most appreciated, as I will probably need the Source package to dovetail it into a customized Kernel 2.6.31rc*n*-rt for my now-AMD/nVIDIA-equipped Everex (8.04-LTS is supported with Kernel 2.6.24-24 as of this post).  The new emu20k1-source is just what I expect to need in order to integrate the Creative Laboratories SB0886 X-Fi Titanium Fatal1ty Champion, one of very few PCI-Express sound cards on the market as of May 2009. into my system.

Addendum:  I recently had to replace the Elitegroup 'board with a Gigabyte 'board packing an AMD780G chipset, as the nVIDIA nForce405 was the probable cause of an uncommanded-shutdowns problem I had.  Same conditions apply to the new 'board w/r/t the SB0886 that I plan to integrate.

---

### Post by amtam on 2009-05-17
Great news, Nullhead! :)

Finally something is happening again on the X-Fi-front.

BTW, you don't have to wait for kernel 2.6.31; the snapshot from Takashi already installs on the vanilla Jaunty kernel. I just tried it and it seems to work just fine. No front-panel support yet though... :sad:

But surround might just work; there are options for that now in Sound Preferences. Can't test it, because I have no surround setup.

---

### Post by jacmoe on 2009-05-19
I tried and tried to get my X-Fi working in 8.10, but gave up on it...:(

Just want to say **thanks a lot** for this guide!
Tried the procedure on 9.04 - and it worked! :D
Didn't even have to restart. Amazing!:)

---

### Post by bernardfrancois on 2009-05-20
I just upgraded from 8.04 to 9.04.

Now I'm trying to compile the drivers, but when I run **sudo make**, I get the following:

```

ber@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo make
[sudo] password for ber: 
make -C /lib/modules/2.6.24-22-386/build M=/home/ber/Desktop/XFiDrv_Linux_Public_US_1.00
make: *** /lib/modules/2.6.24-22-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

```

Note that this corresponds to the kernel I'm using:
```

ber@ubuntu:~/Desktop/XFiDrv_Linux_Public_US_1.00$ uname -r
2.6.24-22-386

```

I installed the packages **linux-headers-386** and **linux-source**, but none of them added a build directory.

Anyone has an idea how to solve this?

---

### Post by bernardfrancois on 2009-05-20
Apparently, the script looks in both **/lib/modules/2.6.24-22-386/build** and **/usr/src/linux-headers-2.6.24-22-386**.

The problem was that I didn't have the latest kernel configured in the **/boot/grub/menu.lst** file.

Now that I changed the menu.lst file, I can start the compilation, but I get a compilation error (displayed after a long list of warnings):
```

/home/ber/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.c: In function 'hw_pll_init':
/home/ber/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.c:1315: error: implicit declaration of function 'mdelay'
make[2]: *** [/home/ber/Desktop/XFiDrv_Linux_Public_US_1.00/cthw20k2.o] Error 1
make[1]: *** [_module_/home/ber/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-6-386'
make: *** [all] Error 2

```

Anyone knows how this can be fixed?

---

### Post by bernardfrancois on 2009-05-20
I had a look myself, and fixed the compilation errors. The sound now works.

I added the following lines below the #include statements near the beginning of **cthw20k1.c** and **cthw20k2.c**:
```

#ifndef mdelay
    #include "/usr/src/linux-headers-2.6.28-6-386/include/linux/delay.h"
#endif

```

The following site helped me to find the file where the mdelay() function is declared:
[http://www.cs.fsu.edu/~baker/devices/lxr/http/ident?i=mdelay](http://www.cs.fsu.edu/~baker/devices/lxr/http/ident?i=mdelay)

Probably, this compilation error can also be fixed in ubuntu 8.04. I now regret that I didn't try this in 8.04 before upgrading to 9.04...

---

### Post by NullHead on 2009-05-20
@bernardfrancois: I'm glad you figured it out.

---

### Post by doctordruidphd on 2009-05-28
For what it's worth:

> While this has been a long and dirty mess, the good news is that as of today there is a merge-able version of the Creative X-Fi driver for ALSA. Novell's Takashi Iwai who wrote the original X-Fi driver has managed to get in contact with Creative Labs to create this genuine X-Fi ALSA driver, which is in far better condition than his previous hack-ish attempt. This new Sound Blaster X-Fi driver is called snd-ctxfi and more information on it can be found within the ALSA development list.

Takashi will be merging this into the mainline ALSA code-base soon so that it will appear in the next Linux kernel, which will be Linux 2.6.31. Finally there is an ALSA driver to provide support for the Creative Labs Sound Blaster X-Fi sound cards, which should begin appearing in desktop Linux distributions this fall.

Note: the current kernel for karmic is 2.6.30, so it's close.

from: [http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA](http://www.phoronix.com/scan.php?page=news_item&px=NzI3MA)

---

### Post by asticinzano on 2009-06-04
I revised my XFI-1.00-Installer so it works properly after a kernel update.
You should remove previous XFi Drivers prior to installing this one. (If you used my installer: sudo dkms remove -m xfi -v 1.00 --all)

Prerequisite: Install dkms.
Tested on: Ubuntu Jaunty 9.04 (i386/amd64)

---

### Post by mhenriday on 2009-06-05
Hopefully, one of these days I'm going to learn to accept the adage that if it works, don't change it - trying to get **Skype** to function on my setup, I managed to inadvertently lose _all_ sound ! OK, I thought, while waiting for the new driver and the new kernel that **Nullhead** mentions above, I'll simply re-install the driver from my **XFiDrv_Linux_Public_US_1.00** files. Alas, no joy - not a peep from Pachelbel's «Canon in D major» do I hear. When I attempt to install the driver, I get the following :

[INDENT]> make -C /lib/modules/2.6.28-12-generic/build M=/home/mhenriday/XFiDrv_Linux_Public_US_1.00
make[1]: Går till katalogen [Going to folder] "/usr/src/linux-headers-2.6.28-12-generic"
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Lämnar katalogen [Leaving folder] "/usr/src/linux-headers-2.6.28-12-generic"
mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.[/INDENT]

I don't quite understand the above warning (especially the part about it being «ignored in a future release» (?!!) - am I here being told to perform some action, so that «config files» will work ? If so, what exactly should I do ? Or is there something else I'm missing in the labour of Sisyphos that is keeping the **X-Fi** driver working properly ? Grateful for suggestions !...

Henri

---

### Post by JaJaJim on 2009-06-08
sorry for my bad english!

i test the "new" alsa-driver-unstable-snapshot [ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz]("ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz")
install with
```
./configure --with-cards=ctxfi , make , sudo make install
```
followed by reboot, disable onboardsound and set pulseaudio as default soundserver -> now x-fi microphon first time working under kubuntu! :p

edit:
not testet but 5.1 should be working to!

---

### Post by AoSteve on 2009-06-09
I tried following this one, still didn't get it to even make a blip of sound.   I started my own thread as I didn't want to add so much to this already lengthy thread LOL!    Maybe someone could wonder over to my thread and help me find some sound here.  

[http://ubuntuforums.org/showthread.php?p=7429851](http://ubuntuforums.org/showthread.php?p=7429851)

That's my thread.   Not trying to hijack, but I'm at my witts end now LoL

---

### Post by pfoo on 2009-06-12
> **JaJaJim said:**
> 
```
./configure --with-cards=ctxfi , make , sudo make install
```followed by reboot, disable onboardsound and set pulseaudio as default soundserver -> now x-fi microphon first time working under kubuntu! :p

edit:
not testet but 5.1 should be working to!
No 5.1 for me with this new driver.

edit:
Sorry, all audio channels (front/surround/center/side) seems to be working using aplay. But not altogether

---

### Post by pinan on 2009-06-14
writes JaJaJim 

./configure --with-cards=ctxfi , make , sudo make install

Where does this configure program live?  a quick

 find / -name configure-print 

run as root does not find it.  

Is it part of some package, if so what is it called ?

---

### Post by NullHead on 2009-06-14
> **pinan said:**
> writes JaJaJim 

```
./configure --with-cards=ctxfi , make , sudo make install
```

Where does this configure program live?  a quick

 find / -name configure-print 

run as root does not find it.  

Is it part of some package, if so what is it called ?

This is a script that you're running. It will be with the package you downloaded for alsa's unstable git tree. Also, the name of it is just "configure".

---

### Post by AoSteve on 2009-06-15
I've been messing with mine ALL day..  This is the only thing I've got to change..  It now says Kernel Driver in use :  HDA Intel...

I don't think it's right as any test with alsa just locks the sound properties screen.  Also, trying to play a music file ends up in totem all but locking up.  Still no sounds.  :(   I even tried editing the ctdrv.h file to add the subsystem to 0010, but nothing..   Any idea?  I'm wishing for sound every bit! :(

```

0b:00.0 PCI bridge: Creative Labs Device 7006
    Flags: bus master, fast devsel, latency 0
    Bus: primary=0b, secondary=0c, subordinate=0c, sec-latency=64
    Memory behind bridge: feb00000-febfffff
    Capabilities: <access denied>
    Kernel modules: shpchp

0c:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
    Subsystem: Creative Labs Device 0010
    Flags: bus master, medium devsel, latency 64, IRQ 17
    Memory at febfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```

---

### Post by pinan on 2009-06-15
> **asticinzano said:**
> I revised my XFI-1.00-Installer so it works properly after a kernel update.
You should remove previous XFi Drivers prior to installing this one. (If you used my installer: sudo dkms remove -m xfi -v 1.00 --all)

Tried this
Lots sucessful looking commands scroll up the screen.

I can do a lsmod|grep ctx which gives the result 

ctxfi                  83624  0 
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss,ctxfi
snd                    78792  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,ctxfi,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

From that I assume that I have sucessfully built the ctxfi driver, slight problem what ever I do, no sound.

Have I overlook something, I have tried the sound prefers on virtual every setting that I find, but sound,  Is there any other software that I should have installed??

---

### Post by bigbadgreen on 2009-06-15
Sorry if somebody already asked this.  I read about 20 of the 39 pages and didn't see it.  First off I'm very new to Ubuntu.  Thanks to everybody for the great info, this place has really helped me out a ton.  My question is will these creative drivers work with the front panel for my fatality x-fi.  I'm trying to build a multimedia box for my home theater and being able to use the remote and front panel would be great. Should i try it with ubuntu or just go ahead with a windows install?  Like I said I'm pretty new still and still getting used to it, for a noob would it just be easier to go with what is familiar and maybe someday when I understand more to attempt it, or just jump right in and hope I can get it up and running?
I really am loving ubuntu but I really love the use of the remote.

---

### Post by NullHead on 2009-06-16
> **bigbadgreen said:**
> Sorry if somebody already asked this.  I read about 20 of the 39 pages and didn't see it.  First off I'm very new to Ubuntu.  Thanks to everybody for the great info, this place has really helped me out a ton.  My question is will these creative drivers work with the front panel for my fatality x-fi.  I'm trying to build a multimedia box for my home theater and being able to use the remote and front panel would be great. Should i try it with ubuntu or just go ahead with a windows install?  Like I said I'm pretty new still and still getting used to it, for a noob would it just be easier to go with what is familiar and maybe someday when I understand more to attempt it, or just jump right in and hope I can get it up and running?
I really am loving ubuntu but I really love the use of the remote.

I honestly would use windows. 

Creative's drivers will not provide the support you desire. They do not work with the frond panel yet. There are, however, drivers in the making that show great potential. It's very possible to see front panel support within a couple of months.

---

### Post by asticinzano on 2009-06-17
My wild guess would you still have onboard sound activated.
Other than that, which Ubuntu version do you use? 8.10 or 9.04. I've heard ctxfi doesn't compile properly on 8.10.

> **pinan said:**
> Tried this
Lots sucessful looking commands scroll up the screen.

I can do a lsmod|grep ctx which gives the result 

ctxfi                  83624  0 
snd_pcm                99336  3 snd_hda_intel,snd_pcm_oss,ctxfi
snd                    78792  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,ctxfi,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

From that I assume that I have sucessfully built the ctxfi driver, slight problem what ever I do, no sound.

Have I overlook something, I have tried the sound prefers on virtual every setting that I find, but sound,  Is there any other software that I should have installed??

---

### Post by pinan on 2009-06-17
Hi asticinzano, 

thanks for your comment.

I have the 9.04 version.

The borad does have an onboard system, but I through I had disabled that.
Is there a guide to this type off subject somewhere.

> **asticinzano said:**
> My wild guess would you still have onboard sound activated.
Other than that, which Ubuntu version do you use? 8.10 or 9.04. I've heard ctxfi doesn't compile properly on 8.10.

---

### Post by asticinzano on 2009-06-17
Have you checked your sound mixer if it shows something like "X-Fi Alsa Mixer"?
It seems ctxfi is loaded correctly so far.

If you type "sudo dkms status" in a terminal you'll see if ctxfi was installed/built properly.

> **pinan said:**
> Hi asticinzano, 

thanks for your comment.

I have the 9.04 version.

The borad does have an onboard system, but I through I had disabled that.
Is there a guide to this type off subject somewhere.

---

### Post by eyescrm on 2009-06-18
I have followed the tutorial and it seemed to have worked, yet I don't have any sound.

lspci -v says:

```
03:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
    Subsystem: Creative Labs Device 0042
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
    Memory at fe800000 (64-bit, non-prefetchable) [size=2M]
    Memory at fd000000 (64-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: CTALSA
    Kernel modules: ctxfi
```I had edited the ctdrv.h as stated in the guide as well

> **asticinzano said:**
> Have you checked your sound mixer if it shows something like "X-Fi Alsa Mixer"?
It seems ctxfi is loaded correctly so far.

If you type "sudo dkms status" in a terminal you'll see if ctxfi was installed/built properly.

sudo dkms status returns only:

```
nvidia, 180.44, 2.6.28-11-generic, x86_64: installed (original_module exists)
```Any ideas?

---

### Post by pinan on 2009-06-18
Running Kernel 9.04
Results of doing "sudo dkms status

nvidia, 180.44, 2.6.28-11-generic, x86_64: installed 
xfi, 1.00-ubuntu2, 2.6.28-11-generic, x86_64: installed 
Doing lsmod|grep snd
lists
snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  3 snd_hda_intel,ctxfi,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  16 snd_hda_intel,ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

Doing an lspci lists
00:1b.0 Audio device: Intel Corporation 631xESB/632xESB High Definition Audio Controller (rev 09)
        Subsystem: Intel Corporation Device 0419
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at e9704000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

04:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
        Subsystem: Creative Labs Device 0043
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
        Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
        Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: [40] Power Management version 3
        Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [58] Express Endpoint, MSI 00
        Capabilities: [100] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
        Capabilities: [300] Advanced Error Reporting <?>
        Kernel modules: ctxfi
But none of the sound menus display ctxfi or xfi

I not sure what to next, I assume form the above the machines not the drivers loaded in to the kernel.  But some user level plumbing seems to be required.

Does any body have and any ideas

---

### Post by pinan on 2009-06-18
[QUOTE=pinan;7479230]Running Kernel 9.04
Results of doing "sudo dkms status

Fixed it now working!

I had tried astocomzano fix just running a simple script seemed to be the easy way.
It did'nt work on my machine.
After a bit of playing I discovered that my machine had an eabled on board sound system as well as the xfi system, I disabled that in the bios.
Result the machine booted with out loading eny of the intel coadec.
Using dkms listed the driver as did lspci,  but I discovered that there was an error message in /var/log/message about not being able to access the pci slot listed by lscpi.

I eventual tried the suggestion by JaJaJim(it did look harder)

After the reboot nothing seemed to have changed very much, a lsmod, now listed a snd_ctxfi.

Playing with the sound menu option from the system menu now listed dozen of Create-Xfi devices.
Looking in /var/log/messages listed some errors about the driver not agreeing with the card.  
I tried sound playback setting set to Autodecte and the Default Mixer Tracks set to Creative XFI(SAlsa Mixer) and pressed Test.  
The machine virtual blew my ears off with the sound it generated.  

Everything seems to work

This solution refers to kernal version  2.6.28-11-generic #42 ubuntu version 9.04 with an xfi sound card label as 

04:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
        Subsystem: Creative Labs Device 0043
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at e4200000 (64-bit, non-prefetchable) [size=64K]
        Memory at e4000000 (64-bit, non-prefetchable) [size=2M]
        Memory at e0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <access denied>
        Kernel driver in use: SB-XFi
        Kernel modules: snd-ctxfi, ctxfi
by lspci -v

Thank you to everybody who tried to help.

---

### Post by GalloGlas on 2009-06-21
> **pfoo said:**
> No 5.1 for me with this new driver.

edit:
Sorry, all audio channels (front/surround/center/side) seems to be working using aplay. But not altogether

I managed to get surround speakers working.  Had to install and run kmix and add the appropriate channels to get it working.    

Would be nice if I could get the breakout box on my elite pro functional tho :(



[IMG]http://img235.imageshack.us/img235/6099/creative.jpg[/IMG]

[IMG]http://img235.imageshack.us/img235/4024/kmix.jpg[/IMG]

---

### Post by KamakazieX on 2009-06-26
Alright,

I personally think these xfi posts are a **** mess. It takes an hour minimum to get the card working and the next dist-upgrade breaks it like a fresh install..

Lets get a community help page going parallel to the OpenSound page. It is more than necessary at this point.. I just don't know what posts are worth reading through anymore. Also lets get the dkms package official if it holds true for the pcie models so we dont have to fish for it, this hardware is pretty mainstream for quality system builders. I'd put its popularity next to virtualbox. Has an official mixer been decided for ctxfi/oss? Lets lay some stuff down, the pros, the cons, and in one shot on a help page. We can utilise it to keep up to date if driver updates happen ..ever.

The youtube problem is driving me nuts, in the process I broke my entire sound system and I am just too burnt out from being on the servers at work all day to sit another 4hrs in front of this..

All for a community page:

Aye:

Nay:
..

I'll do the page if someone tells me in a clean post the current method for oss/ctxfi.. :beer:

---

### Post by NullHead on 2009-06-27
> **KamakazieX said:**
> Alright,

I personally think these xfi posts are a **** mess. It takes an hour minimum to get the card working and the next dist-upgrade breaks it like a fresh install..

Lets get a community help page going parallel to the OpenSound page. It is more than necessary at this point.. I just don't know what posts are worth reading through anymore. Also lets get the dkms package official if it holds true for the pcie models so we dont have to fish for it, this hardware is pretty mainstream for quality system builders. I'd put its popularity next to virtualbox. Has an official mixer been decided for ctxfi/oss? Lets lay some stuff down, the pros, the cons, and in one shot on a help page. We can utilise it to keep up to date if driver updates happen ..ever.

The youtube problem is driving me nuts, in the process I broke my entire sound system and I am just too burnt out from being on the servers at work all day to sit another 4hrs in front of this..

All for a community page:

Aye:

Nay:
..

I'll do the page if someone tells me in a clean post the current method for oss/ctxfi.. :beer:

As I've not used linux on my desktop for a good 6 months, I declare myself unqualified for these tasks. I do an install of the newest ubuntu OS, install the drivers, then usually go back to my 100% supported OS *cough* windows *cough*. 

I've done the best I can with the current post, but I doubt I'll be making any more tutorials for setting up the X-Fi on any modern systems. 

As far as I know, the info I have in the first post in the thread is accurate and works, but as I don't have a PCI-E soundcard to test, and I haven't asked anybody else to do it, that part is by far the most cloudy. 

I would recommend you go through the content that I have in the first post and start from there. Sift through what works, and what doesn't. 

I think a community help page is probably the easiest way to keep all information localized to one place and constantly updated. 

Also, [The latest kernel is in RC-1 stage](http://www.phoronix.com/scan.php?page=news_item&px=NzM0OQ), which means built-in X-Fi support is just around the corner. I _will_ be installing a testing Ubuntu 9.04 system to build this new kernel on, and I will be distributing my kernel that I will be building; though I'm going to wait until the kernel goes stable.

---

### Post by linuxmagick on 2009-06-27
For what it's worth, I can confirm that my PCI-E X-Fi Titanium Fatal1ty Pro *takes a breath* is working beautifully in Kubuntu 9.04 AMD64.  I'm currently running kernel 2.6.28-13.  I have also tested the card in Slackware 12.2 using the default kernel and later the vanilla 2.6.30 kernel.  All worked fine and I have yet to run into any problems.  

The driver installation was the same on both distros and is pretty much what is listed on the first post of this thread.  I had to do a lspci -v and update the ctdrv.h file, then make, make install from the Creative driver directory, followed by modprobe ctxfi.

Without threads out there just like this one, I'd still be trying to get my sound working. It would have never occurred to me to edit ctdrv.h.

Keep it up!

---

### Post by mhenriday on 2009-06-28
**Nullhead**, please don't give up on us - many **Ubuntu** users who never would have been able to get a peep out of their **X-Fi** cards without your help are now enjoying music/radio/video on their boxes. If some are unable to appreciate the services you've rendered, that says much about them, but nothing about the value of these services. And besides, we need your help with the new kernel, which hopefully we'll resolve all our problems in using the **X-Fi** card on (recent versions of) **Ubuntu** !...

Henri

---

### Post by Psychopsia on 2009-06-28
Yes, **NullHead** you provided great help for people like me to get working the XFI soundcard.

If some people can not recognize your effort even if the sound is not working for them, don't feel sad about their angry. ;)

Thanks Nullhead :)

---

### Post by GeekGirl1 on 2009-06-28
Same here. Thanks, Nullhead. When the kernel upgraded, all I did was follow Post #1 and everything is OK.

Except, I still have problems with Rhythmbox sound (very high noise and distortion, not usable). The sound preferences are configured as shown on Post #1. Amarok is not installed at the moment, but it was having the same poor audio problems.

I'm hoping that the kernel level driver will fix it, unless I'm missing something?

---

### Post by NullHead on 2009-06-29
> **GeekGirl1 said:**
> I'm hoping that the kernel level driver will fix it, unless I'm missing something?

It probably will.

---

### Post by Magick93 on 2009-07-01
Hi all

thanks to google I found this thread - searching for 'x-fi' on this forum returns no results.

I bought a new pc about a month ago with the intention of making music using my X-fi card and Fruityloops.

After much effort I managed to get the card to work with OSS, and then after even more effort I got audio to with Flash. 

But MIDI does not work.

I have spent hours reading thru threads and mailing lists and getting more and more confused and frustrated. 

Anyway: I have a few questions

1) Is it even possible to get the x-fi card to work with midi, and flash?
2) If yes, where can I find instructions on how to do this? I dont want to read thru pages and pages of forum posts doing a trial and error approach.
3) If it is possible, is it a task for a newbie? 
4) If not, is there a skilled person who would be willing to assist in return for payment?

---

### Post by mhenriday on 2009-07-04
After enjoying sound on **Ubuntu Jaunty** for several months, I managed to lose it in some mysterious way, so I thought I'd try getting it back in connexion with the latest kernel update. So back to page 1 of this thread and extraction and configuration of the **XFiDrv_Linux_Public_US_1.00.tar.gz** in accordance with **Nullhead**'s detailed instructions. But for some reason configuration doesn't go so well, as shown by the following terminal output :
> mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ make
make -C /lib/modules/2.6.28-13-generic/build M=/home/mhenriday/XFiDrv_Linux_Public_US_1.00
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.28-13-generic"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.c:14:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/xfi.c:17:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.c:18:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctvmem.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.h:21,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c:18:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c: I funktion "ct_alsa_pcm_create":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctpcm.c:462: varning: att skicka argument 2 till "snd_pcm_new" kastar kvalificerare från pekarmåltyp [to send argument 2 to "snd_pcm_new" removes the qualifier from the pointer target type] 
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.o
I fil inkluderad från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctatc.h:25,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.h:21,
                 från /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctmixer.c:19:
include/sound/driver.h:1:2: varning: #warning "This file is deprecated"
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctresource.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "put_src_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:569: varning: jämförelse av skilda pekartyper saknar en typkonvertering [warning : comparison of different pointer types is lacking a type conversion]
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:576: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "put_srcimp_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:883: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:887: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_imap_add":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:916: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:922: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_imap_delete":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:936: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:942: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c: I funktion "srcimp_mgr_destroy":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1004: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctsrc.c:1006: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c: I funktion "put_amixer_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:329: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:333: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c: I funktion "put_sum_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:494: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctamixer.c:498: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.o
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "put_daio_rsc":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:537: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:539: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_imap_add":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:601: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:607: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_imap_delete":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:621: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:627: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c: I funktion "daio_mgr_destroy":
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:706: varning: jämförelse av skilda pekartyper saknar en typkonvertering
/home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctdaio.c:708: varning: jämförelse av skilda pekartyper saknar en typkonvertering
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctimap.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthardware.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthw20k2.o
  CC [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/cthw20k1.o
  LD [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.mod.o
  LD [M]  /home/mhenriday/XFiDrv_Linux_Public_US_1.00/ctxfi.ko
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.28-13-generic"
mhenriday@mhenriday-skrivbord:~/XFiDrv_Linux_Public_US_1.00$ sudo make install
Copy module files...
Update module dependency relationships...
WARNING: All config files need .conf: /etc/modprobe.d/nvidia-kernel-nkc, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

What is all this business about certain sound-driver files being «deprecated» ? How can I fix this ? And how can I resolve a problem of type «to send argument 2 to "snd_pcm_new" removes the qualifier from the pointer target type» ? Moreover, what are all these warnings (only the first of which I've translated above) to the effect that «»comparison of different pointer types is lacking a type conversion». I do hope **NullHead** and other more technically-versed users are still keeping up with developments on this thread - our need for help seems to be unending !...

Henri

---

### Post by mindviper on 2009-07-05
Ubuntu 8.10

X-Fi Titanium pci-e

--------------

Alsa update to the latest 1.0.20
Use terminal command: cat /proc/asound/version
to see what version you got.
The guide is for Ubuntu 9.04 but works well for 8.10 too.

[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

---------------

This link goes to mozilla bookmarks for keeping the track on updates.
[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

From that web page, download this file to your /home/username folder (the one you're at when you open the terminal).

alsa-driver-unstable-snapshot.tar.gz

----------------

now open terminal and let's get busy

tar -xf alsa-driver-unstable-snapshot.tar.gz
"unpacks"

cd alsa-driver-unstable
"goes to the folder you just created"

sudo ./configure
"configures, enter your password when asked"

sudo make

sudo make install

"done"
now reboot and go to "System > Preferences > Sound"
Sound Playback: ALSA (all 3)
Device: Creative X-Fi (alsa mixer)

---------------

oki, now we got stereo sounds at least.
[SIZE="1"]The 5.1 audio is still probably unimplemented but Im hoping there would some day be a choice of "surround51" for "Sound Playback"
You can use the sound settings in VLC at least to swap between all the 4 audio channel pairs so you can get the sound from front, back center/LFE or side speakers.[/SIZE]
[SIZE="1"]There's a little terminal command for testing your speakers: 
---------
speaker-test -c6
---------
That will produce static noise from your 6 speakers one at a time, each about few seconds.
Final release of the driver might get out about Fall2009.
[/SIZE]

I got that 5.1 audio working with new alsa-lib.
```
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-lib/alsa-lib-20090709.tar.gz
sudo tar -xf alsa-lib*
cd alsa-lib
sudo ./configure
sudo make
sudo make install
```
Reboot

Grab a test audio file from
[http://www.halfgaar.net/media/chan-id.zip](http://www.halfgaar.net/media/chan-id.zip)
unpack and test it out with
```
aplay -Dsurround51 chan-id.wav
```
The side channels might sound a little weird as they overlap a little.
That might be a 8 channel audio file but if it plays from all your 6 speakers, your 5.1 audio is working.

Opening up a movie with mplayer. Go to your folder where you have the movie file.
```
mplayer -fs -zoom -quiet -vo xv -monitoraspect 16:10 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 -channels 6 -ao alsa movie.mkv
```

The important part is that -channels 6 -ao alsa. Rest of the settings is just to give good quality picture for my pc. Edit the settings if they don't suit yours.
[http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html)
[http://www.mplayerhq.hu](http://www.mplayerhq.hu)

I hope this saves you some time looking for guides.

--this post is a real mess but I'll clean it up when I test if the instructions here even work on a fresh install :lolflag: --

---

### Post by bcschmerker on 2009-07-07
> **Magick93 said:**
> Hi all

thanks to google I found this thread - searching for 'x-fi' on this forum returns no results.

I bought a new pc about a month ago with the intention of making music using my X-fi card and Fruityloops.

After much effort I managed to get the card to work with OSS, and then after even more effort I got audio to with Flash. 

But MIDI does not work.

I have spent hours reading thru threads and mailing lists and getting more and more confused and frustrated. 

Anyway: I have a few questions

1) Is it even possible to get the x-fi card to work with midi, and flash?
2) If yes, where can I find instructions on how to do this? I dont want to read thru pages and pages of forum posts doing a trial and error approach.
3) If it is possible, is it a task for a newbie? 
4) If not, is there a skilled person who would be willing to assist in return for payment?Flash, yes, as that is a software function of the operating system; all Netscape and Gecko-based Web browsers have available plugins for [Adobe® Flash&#8482;](http://www.adobe.com/).  MIDI doesn't look the case, as the official [Creative Laboratories®](us.creative.com/) literature on the Sound Blaster® X-Fi® cards mentions nothing abut MIDI in the hardware, last supported on the Sound Blaster® Audigy&#8482; 2, E-mu® 0404, and E-mu® 1010.

---

### Post by Magick93 on 2009-07-08
> **bcschmerker said:**
> Flash, yes, as that is a software function of the operating system; all Netscape and Gecko-based Web browsers have available plugins for [Adobe® Flash™](http://www.adobe.com/).  MIDI doesn't look the case, as the official [Creative Laboratories®](us.creative.com/) literature on the Sound Blaster® X-Fi® cards mentions nothing abut MIDI in the hardware, last supported on the Sound Blaster® Audigy™ 2, E-mu® 0404, and E-mu® 1010.

Thanks bcschmerker

Can you recommend a good soundcard that will work with linux and also has midi functioning?

---

### Post by bcschmerker on 2009-07-10
> **Magick93 said:**
> Can you recommend a good soundcard that will work with linux and also has midi functioning?[Creative Laboratories®](http://us.creative.com/) still manufactures the E-mu® 0404 and 1010, both of which use the CA0103 chipset (based on the E-mu® 10k1/10k2).  The 0404 uses two break-out cables to connect to dual-1/4" TRS balanced/unbalanced source and load, plus S/PDIF and MIDI I/O; the 1010 is part of the 1212, 1212M, 1616, 1616M, and 1820 packages, which have separate MIDI connections in their auxiliary daughtercards or external break-out boxes.

Also available from Creative is one E-mu® 20k1-based package aimed at music creators:  The [Sound Blaster® X-Fi® Elite Pro](http://us.creative.com/products/product.asp?category=1&subcategory=875&product=14064), which uses an external break-out box ("X-Fi I/O Console") for its connections, including hi-Z, microphone, dual-RCA analog, TOSLINK, S/PDIF, and MIDI I/O.  No similar functions are available in the E-mu® 20k2-based Sound Blaster® X-Fi® Titanium lineup.

One critical advantage of the E-mu® 0404 and 1010 is full support in the [Advanced LinUX Sound Architecture Project](http://www.alsa-project.org/), which is still pending for the X-Fi (scheduled for Kernel 2.6.31).

---

### Post by EagleDM on 2009-07-12
HOLD ON GUYS !

As of right now, in Ubuntu Karmic Koala daily build (12 July 2009)  X-Fi Titanium and X-Fi PCI are working PERFECT out of the box with the new kernel included in Karmic.


And when I mean perfect I mean in MULTICHANNEL, that's right!

Front, Surround, Side, Center and Subwoofer are all functioning perfect with the included ALSA driver in the newest kernel!!!

Give it a try !!

---

### Post by GeekGirl1 on 2009-07-12
Can you confirm that both amarok and Rhythmbox audio is also perfect? I have nice system sound effects in Jaunty Jackalope, but amarok and Rhythmbox audio are trashed (very high noise and distortion).

Is there any possibility of using kernel 2.6.31 and the new ALSA driver with Jaunty 9.04?

---

### Post by NullHead on 2009-07-12
I can confirm that sound works out of the box with today's daily build of ubuntu karmic koala. I was unable to get surround sound to function, but sound does work. 

Sound quality is remarkably nice considering that the driver is rather new. 

I can also confirm that Rhythmbox works just fine wile playing FLAC audio.

---

### Post by mhenriday on 2009-07-13
**Nullhead**, **EagleDM**, any tips on installing the latest **Karmic** kernel on a **Jaunty** system ? I'd really like to get that sound working again !...

Henri

---

### Post by NullHead on 2009-07-13
> **mhenriday said:**
> **Nullhead**, **EagleDM**, any tips on installing the latest **Karmic** kernel on a **Jaunty** system ? I'd really like to get that sound working again !...

Henri

I can try to write up a guide for you. I'm rather busy though, it could be a week or two before I can post it.

---

### Post by mhenriday on 2009-07-14
> **NullHead said:**
> I can try to write up a guide for you. I'm rather busy though, it could be a week or two before I can post it.

**NullHead**, that would really be splendid ! I could, of course, do a search for tips on compiling a new kernel, but risk then bolloxing up things really badly do to my lack of experience with such manoeuvres. Waiting a week or two is no problem - as we say her in the North, there's no cow on the ice ! I'm certain that I'm not the only reader of/subscriber to this thread who would find such a guide of great help - I look forward to reading it !...

Thanks once again for all your help !...

Henri

---

### Post by NullHead on 2009-07-14
[CENTER][SIZE="5"]**Info**[/SIZE][/CENTER]

Usually updating a kernel is a rather smooth process, but sometimes there can be issues, so I do **not** guarantee anything. 

You'll most likely need to re-install your graphics card, or maybe even wifi card, drivers. Doing so is beyond the scope of this guide, so refer back to the guide or instructions you used the first time. 

[CENTER]**[SIZE="5"]Procedure[/SIZE]**[/CENTER]

It's always a good idea to have an updated system, so go ahead and update. You can do so with this command: ```
sudo apt-get update && apt-get upgrade
```

**Note:** You're going to need the administrator password to to run this, and most all the others in this guide.

After you've gone through all the updates, you'll need to install some packages that are necessary for building this here kernel. 

Run this command to get all the packages you'll need: ```
sudo apt-get install kernel-package libncurses5-dev fakeroot bzip2 build-essential
```

Now we'll need to change users so you're logged in as root instead as a regular user. Do this: ```
sudo -i
```

It's now time to download the new kernel. We want to save the kernel packages in /usr/src, so lets move to that directory and get it downloading. ```
cd /usr/src; wget http://www.kernel.org/pub/linux/kernel/v2.6/testing/linux-2.6.31-rc6.tar.bz2
```

Next we want to unpack the kernel's packaging; do so like this: ```
tar jxvf linux-2.6.31-rc6.tar.bz2
```

**Note:** You will see a flood of text scrolling up on your terminal window, do not panic, this is good. 

Next lets make a shortcut to the folder and move to the kernel's build directory. ```
ln -s linux-2.6.31-rc6 linux; cd linux
```

We need a base config file to use with this kernel, so we'll use the config for the kernel that you're using now. ```
cp /boot/config-`uname -r` ./.config
```

It's time to configure the kernel. Do so like this: ```
make menuconfig
``` 

Now, this may look confusing and/or a bit scary, but really that colored menu system is your friend. So lets turn on a couple of things, then get out of there. 

You need to load the config file first though. You need to go all the way to the bottom of the menu (use the arrow keys) and select the menu option "Load an Alternate Configuration File" Hit the enter key twice. 

Now go to the "General Setup" (back at the top) and find the option that says "Optimize for size" and select it. It should have a star inside the brackets. It'll look like this: [*]

Now press the tab key once to select the "exit" button. This brings you back a menu, so you're at the main menu now. 

Now you need to go to the "Device Drivers" menu. Continue through: 

Sound Card Support> Advanced Linux Sound Architecture>PCI sound devices>Creative Sound blaster X-Fi. Hit the enter key and make it have a "<M>" next to it.

Now go back to the main menu and exit once more. You'll be asked to save your kernel configuration settings. Make sure to say yes. 

Next, run ```
make-kpkg clean

```and ```
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
```

If all went well, your kernel should be building. 

Once it's done, the text will stop flowing, you'll be provided with two .deb packages. You'll need to install these. 

The package names will be something like this: 

For 64bit users: ```
linux-image-2.6.31-rc6-custom_2.6.31-rc6-custom-10.00.Custom_amd64.deb 
linux-headers-2.6.31-rc6-custom_2.6.31-rc6-custom-10.00.Custom_amd64.deb
```

For 32bit users: ```
linux-image-2.6.31-rc6-custom_2.6.31-rc6-custom-10.00.Custom_i386.deb 
linux-headers-2.6.31-rc6-custom_2.6.31-rc6-custom-10.00.Custom_i386.deb
```

I recommend you take the package names and use it with this command (You'll only have to do this once for each package. Pick the architecture that you use)```
dpkg -i <package name>
```

Reboot, and you *should* be good to go. 

Now, with ubuntu 9.04, I've had issues with pulseaudio, so I can't guarantee that you'll have working audio after you do all this. 

Honestly, you'll save yourself loads of trouble if you update to karmic koala, but if your audio is already working, I wouldn't bother messing with it until the next 9.10 is out. They already have all the pulseaudio issues ironed out on karmic koala. 

I honestly can't say what the results of doing all this will give you, but always remember to have a backup kernel handy just in case this one doesn't work. 

I know how fragile Creative's drivers can be, so I don't really recommend doing this if you already have them working.

---

### Post by NullHead on 2009-07-16
I just realized that my kernel guide posted above will probably work with Ubuntu 8.04 LTS. If anybody would care to test it, I'd sure appreciate it. 

:popcorn:

---

### Post by cheesepenguins on 2009-07-16
I hate to semi hijack but I wrote a guide for installing alsa unstable drivers to enable support for the X-fi under 9.04, so far after a few months not had any issues.

Here is a hasty copy and paste from my blog:

> 
This is a simple guide to installing the new ALSA pre-release test drivers, on Ubuntu 9.04 (Gnome), I do not recommend a new user trying this as you need a decent grasp of the command line to configure and install these.

First off, download the required packages: [Download]("http://www.moobash.com/cont/alsa-driver-unstable-snapshot.tar.gz")

Now we need to setup the system to be able to compile these files so, open a terminal and use the following commands:
```

sudo apt-get update
apt-cache search linux-headers-$(uname -r)
sudo apt-get install linux-headers-$(uname -r)
sudo apt-get install build-essential

```

Now we need to extract these packages and then compile, so browse to your download location, for the sake of this guide, we are using the desktop:
```

cd ~
cd Desktop
tar -zxf ALSA-driver-unstable-snapshot.tar.gz
cd ALSA-driver-unstable-snapshot

```
Now we are in the folder of extracted files, we need to grant relevant permissions to what we need:
```

chmod 700 configure

```
Now we run the configure file:
```

./configure

```
This runs the configuration as root, now we need to make the files:
```

make

```
Next we install the package:
```

sudo make install

```
The ALSA drivers are loaded by default on Ubuntu, so this should be setup complete, reboot the machine to find out.

Important, by default the drivers are muted, adjust the volume through the Alsa mixer:
```

alsamixer

```
This command opens up the mixer for Alsa itself, use tab to move between “input”, “output” and “all”, left and right to move column to column, up and down to adjust volume. Then once adjusted press escape to exit. The mixer starts off on mute for the card, what you are after is similar to this:

You can control the volume using the Gnome sound controls.
```

gnome-sound-properties

```
Make sure all the boxes read ALSA.

All done.

On a related note, Pulseaudio has been known to cause issues with the Alsa drivers, if there is a problem with your sound, e.g. cutting out after a while, try removing Pulseaudio.
```

sudo apt-get remove pulseaudio pulseaudio-utils

```


---

### Post by GeekGirl1 on 2009-07-16
According to Nullhead, you need the updated kernel to get audio working with amarok or Rhythmbox. The ALSA project supported drivers page for the X-fi, [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs) , shows how the drivers are part of the kernel build.

An explanation by the developer is here: [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html) with additional instructions and  pointer to the latest tarball (July 16, 2009).

cheespenguins' download is pointing to a version from May 14. I will try the latest tarball (July) using cheesepenguins' guide, but not for a few days. If it doesn't work, I'll upgrade the kernel.

---

### Post by GeekGirl1 on 2009-07-17
Success!:) I used cheesepenguin's guide on his blog: [http://www.moobash.com/Blog/?p=611http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611http://www.moobash.com/Blog/?p=611) , but with the latest tarball from the developer: [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html)

Some differences:
- The tarball has "ALSA" in lower case, so the extraction should be: ```
cd ~
cd Desktop
tar -zxf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable-snapshot
```

- configure already has permissions of 755, so ```
chmod 700 configure
``` should not be needed.

I removed the pulse audio drivers.

For the sound properties, an image of the dialog box would be helpful. I attached my image.

If I could work around amarok's sound driver problems, I would use it. However, it had no sound and it was not worth the trouble. It's gone.

Exaile works fine. Get the latest from the PPA repository (the version in Synaptic does not have the ShoutCast plugin): [http://www.exaile.org/](http://www.exaile.org/)

---

### Post by vastus on 2009-07-20
Thank you NullHead for this How-to post. It was quite helpfull, but i had little trouble at a 1st time when i was installing the drivers, this was because i couldn't see that audio settting picture for some reason (altough i can see it now) but i got it working on my 9.04 ubuntu. Once again thanks to u =)

---

### Post by GrathXVI on 2009-07-20
I'm having some trouble with my X-Fi Titanium card in a fresh 9.04 install. I followed the guide to disable Alsa, install OSS, so on. OSS recognizes that I have an X-Fi card. However, none of the 3.5mm jacks on the X-Fi card output any sound, the sound testing in osstest runs about twice as fast as any of the other tests and doesn't play any sound. When I tell Linux to output through the X-Fi output, then start Rhythmbox, no sound plays through any of the jacks. vmix1 (the one the X-Fi card is using) doesn't display any sound activity. Doing a gnome-sound test on the X-Fi output displays a spike of sound activity in vmix1 which then goes away and, as always, no sound plays.  I do not have anything I can hook up to the digital output on the X-Fi, since the stereo system I'm hooking into is 2.1-only and old.  Edit to note: The integrated sound card runs fine, plays sound decently but it's not the best sound quality. I'm currently listening to music through Rhythmbox, OSS, and the integrated sound card.

---

### Post by cheesepenguins on 2009-07-21
> **GeekGirl1 said:**
> Success!:) I used cheesepenguin's guide on his blog: [http://www.moobash.com/Blog/?p=611http://www.moobash.com/Blog/?p=611](http://www.moobash.com/Blog/?p=611http://www.moobash.com/Blog/?p=611) , but with the latest tarball from the developer: [http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2009-May/017332.html)

Some differences:
- The tarball has "ALSA" in lower case, so the extraction should be: ```
cd ~
cd Desktop
tar -zxf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable-snapshot
```

- configure already has permissions of 755, so ```
chmod 700 configure
``` should not be needed.

I removed the pulse audio drivers.

For the sound properties, an image of the dialog box would be helpful. I attached my image.

If I could work around amarok's sound driver problems, I would use it. However, it had no sound and it was not worth the trouble. It's gone.

Exaile works fine. Get the latest from the PPA repository (the version in Synaptic does not have the ShoutCast plugin): [http://www.exaile.org/](http://www.exaile.org/)
Thanks for confirming this worked, I will update my guide as appropriate.

What exactly where the problems with Amarok? I'm running 1.4.2 without any issues.

---

### Post by GeekGirl1 on 2009-07-21
After using Exaile for a few days, I could not tolerate the long delays on everything from changing Shoutcast channels to starting up. I decided to give amarok another try. It's fixed: [http://ubuntuforums.org/showthread.php?t=1159175&page=2](http://ubuntuforums.org/showthread.php?t=1159175&page=2) 

Exaile has been removed. Amarok 2.02 is up and running.

I would double check whether or not amarok needs pulseaudio. In my initial attempts, amarok didn't work when the pulseaudio drivers were removed. I wasn't sure, so I left them installed. If it does need pulseaudio, I would word your recommendation to remove the drivers accordingly.

---

### Post by kooldino on 2009-07-25
I just rebooted my system (after it's been up for a month or so), and for some reason, when the system came back up, it gave me a notification that the audio card was removed or not responding.

What gives?

---

### Post by Psychopsia on 2009-07-25
> **kooldino said:**
> I just rebooted my system (after it's been up for a month or so), and for some reason, when the system came back up, it gave me a notification that the audio card was removed or not responding.

What gives?

Maybe was a kernel upgrade, install the X-FI driver following instructions on first post on thread. :)

---

### Post by NullHead on 2009-07-25
> **kooldino said:**
> I just rebooted my system (after it's been up for a month or so), and for some reason, when the system came back up, it gave me a notification that the audio card was removed or not responding.

What gives?

First off, what version of Ubuntu are you running?

---

### Post by kooldino on 2009-07-26
> **NullHead said:**
> First off, what version of Ubuntu are you running?

Kubuntu 9.04.  I've been running it since May.  I had followed the instructions in this thread and the driver was running well since then.  Today, I rebooted the machine, and I got those notifications when I logged back into KDE.

---

### Post by NullHead on 2009-07-26
> **kooldino said:**
> Kubuntu 9.04.  I've been running it since May.  I had followed the instructions in this thread and the driver was running well since then.  Today, I rebooted the machine, and I got those notifications when I logged back into KDE.

It sounds like what Psychopsia said was correct. A kernel upgrade b0rked the drivers. 

I think following the instructions on the first post will fix it.

---

### Post by martinbaselier on 2009-07-26
Has anyone checked /etc/modprobed.d to see if the driver is blacklisted.

---

### Post by kooldino on 2009-07-26
That seems to have done it, I didn't even need a reboot.

I wasn't aware that one of the updates updated the kernel.

---

### Post by bcschmerker on 2009-07-28
> **bcschmerker said:**
> That would be most appreciated, as I will probably need the Source package to dovetail it into a customized Kernel 2.6.31rc*n*-rt for my now-AMD/nVIDIA-equipped Everex....Correction:  Make that Kernel 2.6.31-1-amd64rt, as I have reason to suspect a future need for real-time pre-emption of Kernel scheduling (see also "[Why is Ubuntu's realtime kernel crashy? (8.10 Intrepid, 9.04 Jaunty)](http://ubuntuforums.org/showthread.php?t=1145880)").

---

### Post by benjew on 2009-07-29
Rhythmbox wasn't working with the Creative driver (sound was awful - crackling, popping, etc) so I went ahead and tried out the unstable ALSA driver. Everything seems to work now! Thanks for the installation posts. Much appreciated.

---

### Post by GeekGirl1 on 2009-07-29
Reinstalled using the unstable driver. Reinstalled OK, no reboot necessary. Used cheesepenguin's guide as listed here: ://ubuntuforums.org/showpost.php?p=7633907&postcount=417

Reset the Preferences --> Sound, Default Mixer Tracks to Creative X-Fi (Alsa Mixer).

Update: Corrected to point to Cheesepenguin's guide for the install. I kept the PulseAudio drivers, as amarok seems to need them.

---

### Post by crazyone on 2009-08-05
jsut so everyone knows i found a way to enable full 5.1 surround sound if ur using alsa. i had to follow theses steps


gedit .asoundrc

and then add this bit to it

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}

then save and you should have soudn playing like its supose to and not jsut from one channel. i am also using a custom kernel 2.6.31 rc5 but this should work with the alsa driver with the stock kernel for 9.04 or mabe others. havent really tested it. i am also running 9.04 64bit and my sound card is the xfi xtrememusic. heres the link i found it on [http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/](http://ubuntulinuxhelp.com/the-simple-way-to-get-51-surround-sound-audio-working-in-ubuntu/)   hope this helps other people out

---

### Post by zigga15 on 2009-08-08
Hey all,

I often format my computer, try new OS's -- Now I am back to ubuntu.

I just followed the guide and my sound works, except it is all crackly and staticy like your listening to the radio and ur in a tunnel or something.

It is not the sound file, (tried various)
It is not the player, (tried various)
I have updated restarted, reinstalled and everything else.

Has this happened to anyone else

---

### Post by NullHead on 2009-08-08
> **zigga15 said:**
> Hey all,

I often format my computer, try new OS's -- Now I am back to ubuntu.

I just followed the guide and my sound works, except it is all crackly and staticy like your listening to the radio and ur in a tunnel or something.

It is not the sound file, (tried various)
It is not the player, (tried various)
I have updated restarted, reinstalled and everything else.

Has this happened to anyone else

IF you really want to live on the edge, you should try the [Karmic Koala daily build.](http://cdimage.ubuntu.com/daily-live/current/)

I've had mixed results, so I can't really guarantee that anything will work. It's still in the Alpha stage.

---

### Post by zigga15 on 2009-08-08
I will if it fixes the sound ha ha :P

I need a super stable box though, I am in my last year of uni with assignments and theses going everywhere. Wish I had the time to spend on playing around ha ha.

I might dig up and old computer and try karmic :P

~ Dan

---

### Post by NullHead on 2009-08-08
> **zigga15 said:**
> I will if it fixes the sound ha ha :P

I need a super stable box though, I am in my last year of uni with assignments and theses going everywhere. Wish I had the time to spend on playing around ha ha.

I might dig up and old computer and try karmic :P

~ Dan

Chances are it won't be stable enough for you then. I recommend upgrading to it when it releases though. There are huge improvements to the wifi. It will also provide out-of-the-box support for your X-Fi. 

Alright then, avoid Karmic. It's still rather flaky. 

I've not noticed the symptoms you describe.

I think your best option is for you to stay with 9.04 and try [this guide](http://ubuntuforums.org/showpost.php?p=7627043&postcount=415) if you have the time. 

I recommend you try that guide on a fresh install though. Maybe shrink your current partition and install a fresh one in a smaller partition for testing.

---

### Post by crazyone on 2009-08-08
if u need stable u might want to try building a new kernel that has good support for the xfi sound card in it. nullhead has a good howto on it too so it is very simple. i have that and the fix above i posted in use to get full sorround sound. hope it helps yea

---

### Post by NullHead on 2009-08-08
Yeah, you might as well give his guide a shot too. 

[http://ubuntuforums.org/showpost.php?p=7736411&postcount=432](http://ubuntuforums.org/showpost.php?p=7736411&postcount=432)

---

### Post by mhenriday on 2009-08-09
**zigga15**, after requesting **NullHead** to provide us with a guide to installing the **2.6.31-rc3** kernel (see posts #409 - #413 above), I never got round to/was just too chicken to try (choose the more apt alternative) installing it. I thus decided to try **OSS** instead of **ALSA** and followed the instructions on the **Open Sound**-documentation link **NullHead** provided after his own guide, but still no joy. I then posted to [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://4front-tech.com/forum/viewtopic.php?t=3225") on the [**_[COLOR="Blue"]Open Sound user fora[/COLOR]_**]("http://www.4front-tech.com/forum/index.php") (from page 3), and one of the monitors there who uses the monicker **cesium** (who doesn't seem to have posted to this thread) kindly walked me through the whole troubleshooting procedure until I got sound working on my box (**Skype** doesn't work - when I try, I get «Problem with Audio Playback» - but that I can live with) ! Now my main problem is that I'm even more reluctant to try installing the **2.6.31-rc3** kernel - it's one thing to do so when a vital feature doesn't work, but another when one's finally got it working and risks bolloxing everything up again ! In any event, and the point of the exercise, you might want to try  running **OSS**, secure in the knowledge that the **OSS**-fora people are _most_ helpful if one runs into problems....

Henri

PS : Running **OSS**, I found it necessary to change the «Devices» listed under «System» &#8594; «Preferences» &#8594; «Sound» from the «Creative ALSA Driver X-Fi WaveOut/WaveIn (OSS)» shown in **NullHead**'s guide to «OSS4 - Sound Blaster X-Fi (046x/067x/076x) input, output, input, and Sound Test, respectively»....

---

### Post by zigga15 on 2009-08-10
Thanks a lot for all the help guys,

I will try out a few things and keep you posted on the solution.

~ Dan

---

### Post by manishmahabir on 2009-08-11
has anyone tried 9.10 with creative x-fi?
does it work out of the box?
i am planning to buy a dell laptop with creative express card...
any suggestions...??

---

### Post by crazyone on 2009-08-11
from what i understand it should work out of the box. but i havent had the time to test it so idk at all its jsut what i have heard from friends

---

### Post by xenogia on 2009-08-11
> **crazyone said:**
> from what i understand it should work out of the box. but i havent had the time to test it so idk at all its jsut what i have heard from friends

I personally can't wait for 9.10.  About two months ago I was considering replacing my X-fi (auzentech prelude x-fi) with the Asus Xonar card because the Asus card uses the Oxygen chipset which is supported by the latest version of ALSA.

But rather than spending more money I am just waiting till the end of October :)

---

### Post by notbitmonk on 2009-08-13
I just bought the Creative X-Fi Gamer and tried using the Creative driver.  I can hear sound from the front-left and front-right speakers but not from the rear-left, rear-right and center speakers.  The subwoofer appears to be working.  The volume control preferences only shows PCM and it does not show the surround controls.  The onboard card and my previous Audigy 2 ZS (it died a year or so ago) had PCM-LFE, PCM-center and PCM-Rear (if I remember correctly) in the sound control but is not showing up in the controls with the X-Fi (I've looked with alsamixer too).  I used the asoundrc solution presented at the beginning but the only sound comes from the front-right and front-left speakers.  What I believe is happening is that the driver does not provide for surround sound.  I do not know anything about C but I looked at the code and found an enumeration (?) that had PCM in it and nothing like PCM-Surround, PCM-Rear-Left, etc.  I also tried uninstalling the Creative driver and installing the current alsa driver (1.0.20) but on reboot did not hear the login sound (that is as far as I went so I'll post back later on the results of it). 

I had the option to buy an Audigy SE card (about a third of the price of the X-Fi) which I know it will work without problems.  I went for the X-Fi because I have Doom 3, Quake 4 and Neverwinter Nights and thought that the X-Fi will give me the best possible sound.  Now, will the games use the X-Fi (EAX 5.0) to its full potential or will it be the same if I use the Soundblaster Audigy SE (EAX 3.0)? I know the games offer the EAX option but I don't know if it will be usable within Ubuntu.  I do not use Windows anymore so the X-fi would not provide me with anything beyond what I get from Ubuntu.

---

### Post by crazyone on 2009-08-13
hey try this [http://ubuntuforums.org/showpost.php?p=7736411&postcount=432](http://ubuntuforums.org/showpost.php?p=7736411&postcount=432) it worked for me to get sound out of all channels

---

### Post by notbitmonk on 2009-08-13
With the new unstable alsa module I was able to get surround sound.  I had forgotten how beautiful sound is through a dedicated soundcard.  No other configuration except to unmute the channels.  It looks like having the card is not enough to enable EAX in in the games.  However, I had expected that I would be able to select 5.1 speaker configuration in Neverwinter Nights and hardware sound mixing but no luck.  Can someone explain?  It looks like the Linux camp can not fully benefit from this card.  Another thing, can I play DVD-Audio (i'm not talking about movies) with this card?

---

### Post by xenogia on 2009-08-13
So how do I go about upgrading to a .31 kernel so I can use my x-fi correctly?

---

### Post by NullHead on 2009-08-14
> **xenogia said:**
> So how do I go about upgrading to a .31 kernel so I can use my x-fi correctly?

My kernel guide: [http://ubuntuforums.org/showpost.php?p=7614985&postcount=413](http://ubuntuforums.org/showpost.php?p=7614985&postcount=413)

This one is a better way to get sound though: [http://ubuntuforums.org/showpost.php?p=7627043&postcount=415](http://ubuntuforums.org/showpost.php?p=7627043&postcount=415)

You won't have to re-compile the whole kernel; just the newer audio modules.

---

### Post by mhenriday on 2009-08-14
**Nullhead**, now that, with the help of my friends, I've finally got sound (surround sound at that !), I've decided to wait for the release of the **Karmic beta** before performing any significant changes on my box. But one thing worries me - I get the impression that the **ALSA** drivers are installed by default on **Karmic**, and as I recount in post #439 above, I had to dump **ALSA** and go to **OSS** to get sound to work on my machine. Does that mean that when I upgrade to **Karmic** on 1 October as I plan to do, I'm not going to hear anything at all ? Am I going to have to manually purge all my **OSS** files or can I expect the change to be as seamless as I'd like it to be ?...

Henri

---

### Post by NullHead on 2009-08-14
> **mhenriday said:**
> **Nullhead**, now that, with the help of my friends, I've finally got sound (surround sound at that !), I've decided to wait for the release of the **Karmic beta** before performing any significant changes on my box. But one thing worries me - I get the impression that the **ALSA** drivers are installed by default on **Karmic**, and as I recount in post #439 above, I had to dump **ALSA** and go to **OSS** to get sound to work on my machine. Does that mean that when I upgrade to **Karmic** on 1 October as I plan to do, I'm not going to hear anything at all ? Am I going to have to manually purge all my **OSS** files or can I expect the change to be as seamless as I'd like it to be ?...

Henri

I'm guessing you're going to have to purge all drivers relating to the X-Fi before you can get sound. 

That includes failed attempts at installing Creative's drivers, completely removing OSS. 

It's also possible that the upgrade won't give you sound. It /will/ give you the sound module, but I'm not sure if you'll get a pre-configured pulse-audio server that will work properly. 

I'll be honest. I think a fresh install of Karmic Koala is going to be the best way to get functional sound. 

Let me know how it goes in the event that you upgrade.

---

### Post by xenogia on 2009-08-14
I still can't get 5.1 though even editing the .asoundrc file.. sigh

---

### Post by mhenriday on 2009-08-16
> Let me know how it goes in the event that you upgrade.
Don't worry, **Nullhead** - I'll be back, either happy as a lark because my sound works, or desperately seeking help because it doesn't !...

Henri

---

### Post by GalloGlas on 2009-08-18
The only crappy thing is.  Once you DO get 5.1 working... a linux header update comes out and it'll break your sound.  

Fixable by repeating all the same steps as you did to get it working.. just annoying.

---

### Post by mhenriday on 2009-08-19
Well, **GalloGlas**, aren't you're the lucky one ?!! Not only did the header update break my sound - which I was able in the end to restore by following **NullHead**'s re-installation instructions at the beginning of this thread, those on the community [**_[COLOR="Blue"]OSS documentation[/COLOR]_**]("https://help.ubuntu.com/community/OpenSound"), and finally, those on [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://4front-tech.com/forum/viewtopic.php?t=3225&postdays=0&postorder=asc&start=0") on the **4Front Technologies** forum - but I found that, when sound had been restored, I had lost the 5.1 surround on my **Logitech Z-5450**, despite the fact that the **asoundrc** page is configured as follows :
> pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}     

(I realise that the above is supposed to work only for **ALSA**, but the fact is that prior to the headers update this morning, it was working perfectly on my **OSS**-system.) Anybody have any ideas as to how I can get surround sound to work with **Creative Sound Blaster X-Fi** on **OSS** ? This business of having to re-install everything after the least little kernel update is beginning to pale - I long for the **Karmic** beta release which (I fervently hope !) will resolve these driver problems once and for all....

Henri

---

### Post by ug_tinker on 2009-08-30
> **mindviper said:**
> ubuntu 8.10
---------------

this link goes to mozilla bookmarks for keeping the track on updates.
[ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

from that web page, download this file to your /home/username folder (the one you're at when you open the terminal).

Alsa-driver-unstable-snapshot.tar.gz

----------------

now open terminal and let's get busy

tar -xf alsa-driver-unstable-snapshot.tar.gz
"unpacks"

cd alsa-driver-unstable
"goes to the folder you just created"

sudo ./configure
"configures, enter your password when asked"

sudo make

sudo make install

"done"
now reboot and go to "system > preferences > sound"
sound playback: Alsa (all 3)
device: Creative x-fi (alsa mixer)

i hope this saves you some time looking for guides.

--this post is a real mess but i'll clean it up when i test if the instructions here even work on a fresh install :lolflag: --







your my hero !!!!!!!!!!!!! 5.1 :-))))))))) woooo hooooo !!

Thanks man

---

### Post by Lantizia on 2009-08-31
And here is another way of getting it all working (not even that more complex really) by upgrading to todays ALSA release!

Link...

[http://ubuntuforums.org/showthread.php?t=1254492](http://ubuntuforums.org/showthread.php?t=1254492)

Oh and did I mention full 5.1 support?

---

### Post by Capt. Blackwood on 2009-09-03
I'd like to get most of my features on my Creative X-Fi Fatality Champion working. 
 
Can ya'll help me? Am i in the right place? And most of all, where do i start?
 
 
 
(BTW)-
No offence, Lantizia, I tried your method and got no results on the 64 bit version. Are you using 32bit?
 
 
 
I'd like the best method to get this working.

---

### Post by NullHead on 2009-09-03
> **Capt. Blackwood said:**
> I'd like to get most of my features on my Creative X-Fi Fatality Champion working. 
 
Can ya'll help me? Am i in the right place? And most of all, where do i start?
 
 
 
(BTW)-
No offence, Lantizia, I tried your method and got no results on the 64 bit version. Are you using 32bit?
 
 
 
I'd like the best method to get this working.

Unfortunately, the best you're going to get out of the X-Fi under linux is basic sound, and if you're lucky, you can get it into 5.1 surround. 

The easiest way is you'll get that soundcard working is waiting for Ubuntu 9.10 to come out. I tried the alpha 4 a couple of days ago, and I didn't need the pulseaudio "hack" to get my surround sound working. All I did is play with the new sound configuration GUI and away it went.

---

### Post by Capt. Blackwood on 2009-09-03
> **NullHead said:**
> Unfortunately, the best you're going to get out of the X-Fi under linux is basic sound, and if you're lucky, you can get it into 5.1 surround. 
 
The easiest way is you'll get that soundcard working is waiting for Ubuntu 9.10 to come out. I tried the alpha 4 a couple of days ago, and I didn't need the pulseaudio "hack" to get my surround sound working. All I did is play with the new sound configuration GUI and away it went.
 
 
Well, getting the driver in isn't a problem i've got that down. I'm just looking for a guide to getting the 5.1 surround running, with some luck of course.
 
 
 
BTW,
 
when are we getting 9.10? :D

---

### Post by NullHead on 2009-09-04
Alpha 5 was released a couple of days ago, The expected release is probably mid October.

---

### Post by mhenriday on 2009-09-05
Waiting for the beta, which is scheduled for release on 1 October. Hope it's as good as it's cracked up to be !...

Henri

---

### Post by 20hostages on 2009-09-25
hello pinguins

i have a problem with the drivers and id like to hear your opinions
i did everything from the first page, but i get the following error message at the end:

[I][B]Copy module files...
rm: cannot remove `/lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko': Permission denied
make: *** [install] Error 1[/B][/I]

do i need to install some packages first?
im a total noob to linux (been using it for almost a day now lol) so i wouldnt know what to do next...:confused:
thanks in advance:P

---

### Post by braingram on 2009-09-25
@20hostages

I have to preface this with the fact that I am unfamiliar with the current state of the creative X-Fi on linux. That being said...

Was it this step that was throwing the error?
sudo make install

It looks like you may have left the sudo part off. Basically adding sudo before a command says "have the super use do..." There are quite a few system files that are owned and controlled by the super user (also named root), one being /lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko So your normal user will be unable to change, move, remove etc. these files.

To make a long story short, try it again and double check that you typed in the command as follows:
sudo make install

---

### Post by Capt. Blackwood on 2009-09-25
> **braingram said:**
> @20hostages
 
I have to preface this with the fact that I am unfamiliar with the current state of the creative X-Fi on linux. That being said...
 
Was it this step that was throwing the error?
sudo make install
 
It looks like you may have left the sudo part off. Basically adding sudo before a command says "have the super use do..." There are quite a few system files that are owned and controlled by the super user (also named root), one being /lib/modules/2.6.28-15-generic/kernel/drivers/ssound/ctxfi.ko So your normal user will be unable to change, move, remove etc. these files.
 
To make a long story short, try it again and double check that you typed in the command as follows:
sudo make install
 
If you've read and followed the directions exactly, you should have sound. I haven't had any errors as of late with my drivers.

---

### Post by GeekGirl1 on 2009-09-26
Nothing was working for me until I did a complete uninstall / reinstall process, including startup configuration. In this thread: [http://ubuntuforums.org/showpost.php?p=8011636&postcount=21](http://ubuntuforums.org/showpost.php?p=8011636&postcount=21)

---

### Post by Capt. Blackwood on 2009-09-29
glad to see you got it working though. some sap was telling me that you need to do this and that, and even wanted my screen to see what i was doing. Bah.
 
If you got it workin' with your own methods...great.
 
It'll be even better when 9.10 comes out.

---

### Post by NullHead on 2009-09-30
When 9.10 comes out, you won't need any of these guides.

---

### Post by guillemsola on 2009-09-30
Hi all,

I have a X-FI PCIe Xtreme Audio (ca0110) and I have been testing it with latest kernels. 

I could make it "work" (p.ex. no spdif) with 2.6.31-rc3, 2.6.31-rc5 but with final 2.6.31 release the XFi doesn't work any more. Also tried new alsa 1.0.21 without success.

There is a new 2.6.32-rc1 kernel that comes with alsa 1.0.21. I have also tested it and is lacking XFi support.

So there seems no to be good news from this side.

regards

---

### Post by NullHead on 2009-10-01
Oh, ct-xfi is in there alright. See: [http://tinyurl.com/yejome2](http://tinyurl.com/yejome2)

---

### Post by mhenriday on 2009-10-01
> **NullHead said:**
> When 9.10 comes out, you won't need any of these guides.

**NullHead**, the moment of truth is not far off - I expect **Karmic Koala** to make its debut as a beta later this evening and intend then to upgrade from 64-bit **Jaunty**. I'm presently running **OSS4** and question is the following : is it likely that the **Karmic** beta upgrade will run «out of the box» with my present **OSS4** configuration, or would you suggest I purge the latter, following **Temüjin**'s guide, prior to upgrading ? In that case, should I enable **ALSA** ?...

Henri

---

### Post by loseby on 2009-10-01
well finally have sound from x-fi but having weird problems

using movie player for sound some mp3s have quiet an echo ( soft )but some dont have any

now if I try Rythembox Music Player I get sounf but an awful lot of static as well

---

### Post by NullHead on 2009-10-01
> **mhenriday said:**
> **NullHead**, the moment of truth is not far off - I expect **Karmic Koala** to make its debut as a beta later this evening and intend then to upgrade from 64-bit **Jaunty**. I'm presently running **OSS4** and question is the following : is it likely that the **Karmic** beta upgrade will run «out of the box» with my present **OSS4** configuration, or would you suggest I purge the latter, following **Temüjin**'s guide, prior to upgrading ? In that case, should I enable **ALSA** ?...

Henri

It's hard to say for sure what'll happen when you upgrade, but if it were me, I'd purge OSSv4 before doing the upgrade.

---

### Post by GeekGirl1 on 2009-10-02
> **Capt. Blackwood said:**
> glad to see you got it working though. some sap was telling me that you need to do this and that, and even wanted my screen to see what i was doing. Bah.
 
If you got it workin' with your own methods...great.
 
It'll be even better when 9.10 comes out.That's the main reason people shy away from Linux and go to Win XP. I don't like all that work, either. However, I have a technical background. It was an excuse to really dig in and understand how the OS works.

---

### Post by AcarSterminator on 2009-10-04
Hi.
A question.
I use (would like to) a [Sound Blaster X-Fi Surround 5.1 USB]("http://www.pcworld.idg.com.au/review/pc_components/creative/sound_blaster_x-fi_surround_5_1/224822").
Using Alsa that comes in Jaunty, the sound was not very clear.
So I upgrade Alsa to 1.0.21.
Now is worse than before: I do not see the SB X-Fi in the audio device list!

Do you think the guide in the first post will work for me?

Thank you,
Michele.

---

### Post by GeekGirl1 on 2009-10-04
You could try my version in this thread: [http://ubuntuforums.org/showpost.php?p=8011636&postcount=21](http://ubuntuforums.org/showpost.php?p=8011636&postcount=21), which goes through a complete installation process. There are extra commands that are not described in Post #1 here. Normally, they wouldn't be needed, but I had problems and these are the steps I took to fix them.

---

### Post by KidBeck on 2009-10-06
This one worked for me.[http://www.moobash.com/Blog/?p=815 ]("http://www.moobash.com/Blog/?p=815")
Its a simpler than some of the others and it works.

---

### Post by Capt. Blackwood on 2009-10-07
> **GeekGirl1 said:**
> That's the main reason people shy away from Linux and go to Win XP. I don't like all that work, either. However, I have a technical background. It was an excuse to really dig in and understand how the OS works.


50% why i'm using ubuntu...more...and more...and more...repeat 5x :D

---

### Post by doyle789 on 2009-10-15
> **losbey said:**
> well finally have sound from x-fi but having weird problems

using movie player for sound some mp3s have quiet an echo ( soft )but some dont have any

now if I try Rythembox Music Player I get sounf but an awful lot of static as well


Sounds similar to me. Movie player is okay, and playing mp3s in rythembox is okay most of the time, but occasionally there's just loads of static and your pretty much can't hear the song. Any suggestions?

(n00b, btw)

---

### Post by HNS-I on 2009-10-15
Wicked! I'm going to check this out asap.

---

### Post by bernardfrancois on 2009-10-21
Some months ago I managed to make my x-fi work using the source code from the creative website (I had to add some additional includes in the source code to make the compilation work).

A few days ago I switched to the latest kernel (I noticed updated kernels weren't added to my /boot/grub/menu.lst file), and this broke the sound.

Now I just downloaded the source again, and this time I could compile without needing to change anything. The sound works again now.

When 9.10 is out, I'll surely try it out. Hopefully it will indeed work out of the box, so less technically abled ubuntu users will be able to enjoy their music again :-).

---

### Post by Sadaiyappan on 2009-10-22
Will this workaround work for X-Fi notebook?

---

### Post by fcuk112 on 2009-10-23
i just did a fresh install of 9.10 RC on a box with x-fi fatal1ty pro, it detects my card but i am not getting any sound?  i tried alsamixer -c0 without any joy.

cheers.

---

### Post by titico on 2009-10-25
Hello,

I tried to set up my x-fi creative card, with no result.
I'm running ubuntu 9.04.
I just followed all the steps in the guide with no inconvenient, but I still without any sound.

Any help? Thanks!

---

### Post by mhenriday on 2009-10-26
**Titico**, given that a stable release of **Karmic** is only a few days off, perhaps you'd be best advised to wait until that happens and then upgrade, rather than devoting an immense amount of time and effort to trouble-shooting **Jaunty**....

Henri

---

### Post by loseby on 2009-10-27
> **mhenriday said:**
> **Titico**, given that a stable release of **Karmic** is only a few days off, perhaps you'd be best advised to wait until that happens and then upgrade, rather than devoting an immense amount of time and effort to trouble-shooting **Jaunty**....

Henri

that is my intention

I am not going to upgrade but download, burn and do a clean install

Then I will start to work on sound drivers/video performance and a lot of other things

Update: [COLOR="Red"]clean install of 9.10 and it installed the x-fi drivers automatically and they worked[/COLOR]
[COLOR="DarkGreen"]slight bug is that on reboot they are muted but havbing a mute button on keyboard makes it a very minoir problem[/COLOR]

---

### Post by 8Kuula on 2009-10-31
Can't get any sound output on my Creative X-Fi Xtreme audio card (PCI-E) on ubuntu 9.10 (64bit).
On my external amplifier has "PCM Digital" text, and when I remove optical cable it disapiers, so I think cable is ok, atleast.

So here some info:

Sound Preferences:
```

[SB X-Fi Xtreme Audio] CA0110-IBG
1 Output
Digital Stereo Duplex (IEC958)
```

lspci -l
```

03:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=03, secondary=04, subordinate=04, sec-latency=64
	Memory behind bridge: fbc00000-fbcfffff
	Capabilities: <access denied>
	Kernel modules: shpchp

04:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs Device 0018
	Flags: bus master, medium devsel, latency 64, IRQ 30
	Memory at fbcfc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

When I play some sound file on Totem, it just kind of stucks on playing and time don't go forward.

I have onboard sound card too, I have disabled it on bios but, it did not help.

And no it did not work on 9.04 either, but im not pro, so hoped I did mess driver install from instructions in this thread :]

Wiggled diffirent profiles on sound preferences, but haven't got working.

Im out of ideas :|

---

### Post by adamruss on 2009-11-04
any news on this? i'm stuck.

---

### Post by wdiz on 2009-11-04
Same problem here with X-Fi titanium and Digital duplex.
No sound and there is pulseaudio problem who take 100% cpu until i kill the process...and of course digital duplex option disappear in the sound prefs menu ...

---

### Post by titico on 2009-11-04
You were right Henri, I upgraded and there's no more problem.

Thanks.

---

### Post by adamruss on 2009-11-04
i found this ppa, but it didnt help:
[https://launchpad.net/~wdaniels/+archive/alsa-backports](https://launchpad.net/~wdaniels/+archive/alsa-backports)

i am thinking maybe trying a newer kernel? maybe an RC one - have anyone tried that?

---

### Post by divxclub on 2009-11-05
Hello I have X-Fi Forte card that basicly a Creative X-Fi Titanium / Fatality but enhanced drivers (Windows) but ship I think the same ..... anyhow can you tell me if I can use some driver to make it work. Because I see this in Sound hardware Output tab: X-Fi Titanium Series [ENU20K2]. But I don't hear any audio ....please help

---

### Post by NullHead on 2009-11-06
> **divxclub said:**
> Hello I have X-Fi Forte card that basicly a Creative X-Fi Titanium / Fatality but enhanced drivers (Windows) but ship I think the same ..... anyhow can you tell me if I can use some driver to make it work. Because I see this in Sound hardware Output tab: X-Fi Titanium Series [ENU20K2]. But I don't hear any audio ....please help

I'm sorry, but as far as I know, this driver only supports Creative's sound cards with X-Fi chips on them. I really can't say for sure if any Auzentech X-fi cards work with linux. 

At one point, there was promised support for their cards, but I don't know the state of that development.

---

### Post by divxclub on 2009-11-06
> **NullHead said:**
> I'm sorry, but as far as I know, this driver only supports Creative's sound cards with X-Fi chips on them. I really can't say for sure if any Auzentech X-fi cards work with linux. 

At one point, there was promised support for their cards, but I don't know the state of that development.



Actually this is a creative chip. I mean if possible if you have few minutes google for x-fi Forte 7.1 and you'll see. But on my side let's explain. Take X-Fi Titanuim Fatality card but all creative cheap in there and technology, replace standard build in amps, transistors and other electronics and TADA you got yourself a Forte card. What I am saying is from what I understand this is same thing with high end compunent that should not matter an6yhow because they control "Quality of sound not how sound is processed" I don't know if it make sense but like I said in my understanding it's same creative card / chip that is made for Studio applications (if I can say that) So if possible please let me know. Also here is specs and info on a card: [http://www.auzentech.com/site/products/x-fi_forte.php](http://www.auzentech.com/site/products/x-fi_forte.php)

Thank you in advanced.

---

### Post by 8Kuula on 2009-11-06
> **adamruss said:**
> i found this ppa, but it didnt help:
[https://launchpad.net/~wdaniels/+archive/alsa-backports](https://launchpad.net/~wdaniels/+archive/alsa-backports)

i am thinking maybe trying a newer kernel? maybe an RC one - have anyone tried that?

This did lose my [SB X-Fi Xtreme Audio] CA0110-IBG card totaly. No more show up in sound preferences.

alsa-base v1.1.21. (in karmic repo had v1.1.20).

---

### Post by 8Kuula on 2009-11-06
Talked too soon, it did show up after I did disable onboard sound card. No change on sound output thou, does same, player just "stucks" on playing.

---

### Post by NullHead on 2009-11-06
> **divxclub said:**
> Actually this is a creative chip. I mean if possible if you have few minutes google for x-fi Forte 7.1 and you'll see. But on my side let's explain. Take X-Fi Titanuim Fatality card but all creative cheap in there and technology, replace standard build in amps, transistors and other electronics and TADA you got yourself a Forte card. What I am saying is from what I understand this is same thing with high end compunent that should not matter an6yhow because they control "Quality of sound not how sound is processed" I don't know if it make sense but like I said in my understanding it's same creative card / chip that is made for Studio applications (if I can say that) So if possible please let me know. Also here is specs and info on a card: [http://www.auzentech.com/site/products/x-fi_forte.php](http://www.auzentech.com/site/products/x-fi_forte.php)

Thank you in advanced.

I'm familiar with Auzentech's soundcards and honestly, I'm considering buying a forte for my windows gamer box .. 

What I was trying to say is that the card has been rebranded and isn't the same as a Created sound card. I can't honestly expect a generic X-Fi driver to support every X-Fi chip made. I don't think the driver is mature enough for that.

---

### Post by divxclub on 2009-11-07
> **NullHead said:**
> I'm familiar with Auzentech's soundcards and honestly, I'm considering buying a forte for my windows gamer box .. 

What I was trying to say is that the card has been rebranded and isn't the same as a Created sound card. I can't honestly expect a generic X-Fi driver to support every X-Fi chip made. I don't think the driver is mature enough for that.

Understood. Well in case you'll get it or may be someone have it please let me know what did you do to make it work.

P.S.

My internal audio on Asus P6T Deluxe work perfectly however it's not plugged in as my Forte card is and every time I need to listen something on Ubuntu i need to unplug Forte and plug mobo audio ... oh well at list I Do have a sound ....also my USB Microsoft livechat 300 headphones work as well Skype , Music .. no problem ..so who need audio card at all when your 20$ headphones work just as well in Digital USB audio quality :D

Thank you very much !

---

### Post by divxclub on 2009-11-07
One question guys .....let's say you have blu-ray and one of this z5500 speakers ....is Ubuntu support 5.1 or 7.1 audio at all ? I mean I see in settings but in real life did anyone manage to watch a movie in nice 7.1 in Ubuntu ? Just a question wanna see how advanced sound software in Ubuntu this days .. :D

---

### Post by xenogia on 2009-11-07
> **divxclub said:**
> Understood. Well in case you'll get it or may be someone have it please let me know what did you do to make it work.

P.S.

My internal audio on Asus P6T Deluxe work perfectly however it's not plugged in as my Forte card is and every time I need to listen something on Ubuntu i need to unplug Forte and plug mobo audio ... oh well at list I Do have a sound ....also my USB Microsoft livechat 300 headphones work as well Skype , Music .. no problem ..so who need audio card at all when your 20$ headphones work just as well in Digital USB audio quality :D

Thank you very much !

Just so you know I have an Auzentech Prelude X-Fi and the card works perfectly under Karmic in 5.1 and 7.1 mode.  Never had any problems with it whatsoever, just remember to type **alsamixer** in the terminal and to unmute channels :)

---

### Post by ieduarte73 on 2009-11-12
I am running Karmic 64-bit on a Dell Dimension XPS 710, which came with Creative X-Fi Xtreme Sound Card, I was able to compile and install the Beta driver provided by Creative with no problems whatsoever on my previous Ubuntu Versions, however, as of Karmic, the card gets detected, and it produces sound, but it also produces some crackling and hissing noises, rendering the audio unusable.

I have tried to install Pulseaudio's but no changes in the card behavior, I don't quite understand what happened since this card was working just fine with Jaunty, and now that the driver comes built in with Karmic, it just doesn't work.

Has anyone bumped into this issue with this card, and most important yet ... has anyone succeeded making this card work properly.

---

### Post by GalloGlas on 2009-12-05
The update that I downloaded for 9.10 today really hosed my surround sound for my X-fi.   I can't adjust panning and fade settings without each setting adjusting the other as if they are locked together. And there is a ton of ringing sound.   To get rid of the ringing sound I'm forced to switch back to 2 ch stereo.   Ubuntu has a ways to go for TRUE 5.1 support on Xfi cards.   Not that its their fault.  Creative can't hardly even get their own gear working with windows vista/7 let alone allow a third party attempt functionality on an unsupported OS such as linux.    

And I'm not going to follow Nullheads help because many times in the past he has lead me down the path that created much hair pulling and teeth gritting to fix the mistakes he assured me to make.  So take what he says with a grain of salt.  

And the 5.1 with 9.10 isn't TRUE surround sound if you listen.  Its stereo panned across 4 speakers.

---

### Post by NullHead on 2009-12-05
> **GalloGlas said:**
> The update that I downloaded for 9.10 today really hosed my surround sound for my X-fi.   I can't adjust panning and fade settings without each setting adjusting the other as if they are locked together. And there is a ton of ringing sound.   To get rid of the ringing sound I'm forced to switch back to 2 ch stereo.   Ubuntu has a ways to go for TRUE 5.1 support on Xfi cards.   Not that its their fault.  Creative can't hardly even get their own gear working with windows vista/7 let alone allow a third party attempt functionality on an unsupported OS such as linux.    

And I'm not going to follow Nullheads help because many times in the past he has lead me down the path that created much hair pulling and teeth gritting to fix the mistakes he assured me to make.  So take what he says with a grain of salt.  

And the 5.1 with 9.10 isn't TRUE surround sound if you listen.  Its stereo panned across 4 speakers.

I'm sorry to hear you haven't had success with my guide(s), but please keep in mind, they were written from the stand point of "*This is how **I** got it working*". Usually there is no "official" guide available that one must interpret. The guide on the first page of this thread was written to work for ubuntu 9.04 and I've since switched my main OS to windows 7; as I like to play lots of video games. 

I have had close to no experience with Alsa's latest take on ctxfi, so I'm hardly qualified to help you. 

If you like, I suggest you make a new thread concerning your specific issue.

---

### Post by mhenriday on 2009-12-05
Just a word to say how much help I - like so many others -have found **NullHead**'s guide to be in our long struggle with **Creative**'s **Soundblaster X-Fi**. As most of us know, the reigning motto of computer science - at least in its trouble-shooting aspect - is **YMMV**. Our setups vary in many particulars, and what works on one will, alas, not always work on another. Besides, given that our boxes make use of such quantum mechanical phenomena as electron tunnelling and giant magnetoresistance, which are governed by Werner Heisenberg's *Unschärferelation*, we should hardly be surprised by the fact that what works one time doesn't necessarily work another - and *vice versa* ! Many of us have experienced that a web page that refuses to load or an application that refuses to work becomes more docile after re-booting the box. Mysterious things, these computers !...

Henri

---

### Post by JDorfler on 2009-12-12
In 9.10, make sure you run alsamixer in your terminal so you can turn on your mic.

---

### Post by The Bright Side on 2009-12-13
GalloGlas, I had the very same problems as you! Ringing sound and sliders seeming to be locked to each other. I installed the GNOME ALSA Mixer (package "gnome-alsamixer") and set "Front Mic" to mute. My sound was all messed up when I installed 9.10, and this fixed it. With this mixer, you can also regulate all other devices independently and precisely.

I don't have the X-Fi box, but I was thinking of getting it for my laptop. I'm glad this thread exists, thanks for all the effort everybody put in here! I'm sure I will come back here a lot when setting up the X-Fi card on my laptop.

---

### Post by XanII on 2009-12-15
So no my X-fi card that is based on the earlier creative card in reality finaly shows in sound settings. it doesnt work though. :( any attempts to use it causes timers in lets say rhytmbox to stop, i.e. it doesnt work. playback doesnt work. 

But i guess it's getting closer. havent been able to get even this far before with the instructions on this thread. :(

---

### Post by aalega2 on 2009-12-19
im in the same boat at the moment dealing with Auzentech Forte issues in linux. I'm a happy clam with the card in windows as it works awesomely, but have had trouble with the card in linux. im not exactly a linux noob as ive tried everything i could possibly try before i consulted teh forums - basically my problem is that everything is detected, the latest alsa drivers are installed and seem to be working fine (1.0.22), however i dont get any playback.

im about to punch a wall with this problem

---

### Post by aalega2 on 2009-12-19
has any X-Fi Forte users been able to get their sound working? I have absolutely no idea why it doesnt work, everything looks OK, I hear a pop at startup, but when i play a song in rhythmbox, the song will be playing but of course i cant hear anything.

i managed to get sound working through my TV from via HDMI, but wtf is the point of that

---

### Post by NullHead on 2009-12-19
> **aalega2 said:**
> has any X-Fi Forte users been able to get their sound working? I have absolutely no idea why it doesnt work, everything looks OK, I hear a pop at startup, but when i play a song in rhythmbox, the song will be playing but of course i cant hear anything.

i managed to get sound working through my TV from via HDMI, but wtf is the point of that

Check in alsamixer to see if the speakers are muted.

---

### Post by aalega2 on 2009-12-19
> **NullHead said:**
> Check in alsamixer to see if the speakers are muted.

oh believe me, they arent. ive even made sure several ways, using alsamixer from terminal, using gnomealsamixer. EVERYTHING

---

### Post by NullHead on 2009-12-20
> **aalega2 said:**
> oh believe me, they arent. ive even made sure several ways, using alsamixer from terminal, using gnomealsamixer. EVERYTHING

Well afaik, the driver was designed for Creative X-Fi sound boards. I know the Forte is made my Auzentech, but there are probably some differences.

---

### Post by schak on 2010-01-09
Just installed a X-Fi extreme gamer, and it works fine in Vista, but the microphone absolutely refuses to cooperate in Karmic.  Have run alsamixer and unmuted the microphone, with no success up to this point.  Open to any and all suggestions other than replacing the card.

---

### Post by NullHead on 2010-01-09
> **schak said:**
> Just installed a X-Fi extreme gamer, and it works fine in Vista, but the microphone absolutely refuses to cooperate in Karmic.  Have run alsamixer and unmuted the microphone, with no success up to this point.  Open to any and all suggestions other than replacing the card.

Is it a USB microphone or a regular 3.5mm jack on the end?

---

### Post by Weaver_ on 2010-01-09
> **NullHead said:**
> [CENTER]As of the writing of this message, the guide below is no longer needed and should not be used. The reason being Alsa has finally produced a working drive. Alsa's new drive is included in kernel 2.6.31.X. As of Ubuntu 9.10 (Karmic Koala), the Creative X-Fi soundcard will work out of the box!
[/CENTER]


Hi everyone, I'm new to linux and I've just installed 9.10 (fresh install from format and all) and my x-fi makes no sound.  I've spend several hours scouring forums and the package manager trying to get this thing to work but I have no idea what's wrong.  Can anyone please lend me some assistance?  

Thank you :)

---

### Post by schak on 2010-01-09
> **NullHead said:**
> Is it a USB microphone or a regular 3.5mm jack on the end?

3.5mm jack.  I have a work around with an old USB headset adapter.  I just plugged the microphone in to that, and run my sound through the X-Fi.  But it's a principle thing.  I want the microphone to work from the sound card, and not a band-aid fix.

---

### Post by scot.mcpherson on 2010-01-10
I am also having the same problem. How do we get this to work.

XFI works great except no microphone. This is new to ubuntu-9.10, it worked in 9.04 with the XFI modules built from the sources released by creative, not I can't even compile those since the update. I really need my microphone to work.

Thanks

---

### Post by NullHead on 2010-01-11
I'll install ubuntu 9.10 onto my external hdd and look into it. 

I have both a 3.5mm mic and a USB mic that I can test.

---

### Post by NullHead on 2010-01-11
After my initial testing with the liveCD resulted in the GUI failing to turn on the capture device to the MIC. Instead, it was recording PCM (what you hear). 

A quick change in alsamixer, and turning the volume up and my 3.5mm mic connected to the back of my Extreme Gamer is now working perfectly.

---

### Post by scot.mcpherson on 2010-01-11
Ok thanks,
I will try this when I get home. I'll have to find the alsa-mixer :)

Scot

---

### Post by NullHead on 2010-01-11
Actually, you can use alsamixer already! It's a program meant to be ran from the command line, Applications>Accessories>Terminal. Then just type in "*alsamixer*" and use your arrow keys to change volume settings. You can change between "Playback", "Capture", and "All" by using the TAB key. The period button mutes and unmutes different volume channels. 

I tried again to get my mic working after I finished installing ubuntu, and I had to mess with the inputs a bit to get it working. Switching from Line-IN to MIC, back to Line-IN, muting and unmuting both channels. It seems rather buggy, but eventually, you should end up with having the capture settings to your MIC only, and your mic volume adjusted to where you can hear yourself properly. 

[http://stashbox.org/765676/screenshot.png](http://stashbox.org/765676/screenshot.png)

---

### Post by bfrancom on 2010-01-20
> **NullHead said:**
> Actually, you can use alsamixer already! It's a program meant to be ran from the command line, Applications>Accessories>Terminal. Then just type in "*alsamixer*" and use your arrow keys to change volume settings. You can change between "Playback", "Capture", and "All" by using the TAB key. The period button mutes and unmutes different volume channels. 

I tried again to get my mic working after I finished installing ubuntu, and I had to mess with the inputs a bit to get it working. Switching from Line-IN to MIC, back to Line-IN, muting and unmuting both channels. It seems rather buggy, but eventually, you should end up with having the capture settings to your MIC only, and your mic volume adjusted to where you can hear yourself properly. 

[http://stashbox.org/765676/screenshot.png](http://stashbox.org/765676/screenshot.png)


I can confirm just using alsamixer works. I just muted "Line-in" and microphone works now.  Thank you.

---

### Post by Stev0 on 2010-01-21
Just finished install 9.10 and my X-Fi output was working out of the box. However when attempting to record sound, its recording a very distorted version of the output instead of gathering input from the microphone. Inside the sound preferences input tab, I can choose between my onboard sound and the X-fi no problem, but the x-fi option isnt showing me any sort of the mic connector options that the onboard sound option does. IE, I cant select which jack to recieve input from, its only recieving input in the form of whats playing through the output. 
 
I found a vague forum reference to making sure I had the right alsamixer settings, but alsamixer is controlling my onboard sound. Do I need to go about getting myself a version of asoundconf installed? Can I assign a default card through gnome-alsamixer without having to install asoundconf? Is all this necessary to get the mic input functional, or am I overlooking something simple?

---

### Post by NullHead on 2010-01-21
You can use the -c # to specify which card you want. For example, you can do the command alsamixer -c 0 to get your first sound card, probably your onboard, whereas if you do alsamixer -c 1, you'll most likely end up seeing the settings for your X-Fi. Make sure that under your capture tab in alsamixer PCM isn't selected as one of your capture devices. The only source you want enabled as a capture device is your MIC port. 

Make sure Line-IN is turned down or muted in the Playback menu, otherwise you'll end up with lots of static; at least that's what happened to me. 

Another easy way to select your X-Fi is to disable your onboard sound in the BIOS.

---

### Post by heroes on 2010-02-05
i would suggest that you disable the onboard sound. there might be some conflict with your creative x-fi

---

### Post by PowerSource on 2010-02-27
i've got a problem.

i've installed this driver a few times, and it worked ok. i'm not sure if it's installed right now.
though my microphone doesn't work, just buzzes.
and the sound sometimes stops, starts, playing faster, short stops etc.

i need serious help before i go on a school massacre.

---

### Post by NullHead on 2010-02-27
Okay for one, don't ever PM for support questions; post in threads so all can enjoy. 

If you're running ubuntu 9.10, like indicated on your profile, you don't need the driver or guide outlined on the first post of this thread.

---

### Post by PowerSource on 2010-02-28
> **NullHead said:**
> Okay for one, don't ever PM for support questions; post in threads so all can enjoy.

i did post in this thread, and i only pm'ed you so that i didn't have to wait a week before you found the thread.
> 
If you're running ubuntu 9.10, like indicated on your profile, you don't need the driver or guide outlined on the first post of this thread.


ok, but is there a way to uninstall the driver?

---

### Post by NullHead on 2010-02-28
> **PowerSource said:**
> i did post in this thread, and i only pm'ed you so that i didn't have to wait a week before you found the thread.


ok, but is there a way to uninstall the driver?

It's been a wile since I worked with this driver, but I think *sudo make uninstall* from the driver's directory will uninstall it. If you removed the directory, follow the guide up until *sudo make install*, then type in *sudo make uninstall*.

---

### Post by PowerSource on 2010-02-28
thanks, just going to reboot now :D

---

### Post by PowerSource on 2010-02-28
the sound works fine, so far.

the mic doesn't work at all even though i opened alsamixer and muted line-in on playback and set it exactly like [this]("http://stashbox.org/765676/screenshot.png"), but in audacity and the built in recorder program i get no sound :(

---

### Post by NullHead on 2010-02-28
> **PowerSource said:**
> the sound works fine, so far.

the mic doesn't work at all even though i opened alsamixer and muted line-in on playback and set it exactly like [this]("http://stashbox.org/765676/screenshot.png"), but in audacity and the built in recorder program i get no sound :(

Really, the best I can suggest is mess around with the input channels like I did here: [http://ubuntuforums.org/showpost.php?p=8650426&postcount=520](http://ubuntuforums.org/showpost.php?p=8650426&postcount=520)

The input recording selection is a bit buggy, but eventually, if you mess with it enough, it'll work.

---

### Post by PowerSource on 2010-02-28
what the **** have i done now... XP
when i started recording in audacity and played some music in my headphones, audacity suddenly started to hear.
and when i played it, it played the song...
wtf

---

### Post by PowerSource on 2010-02-28
it works!
...only in audacity

neither flash nor skype captures it.

---

### Post by PowerSource on 2010-02-28
w00t, found an option for that.

sorry for the spam :P

---

### Post by cozmoz on 2010-03-10
What profile should I choose in the soundprofile thing....I got a huuuugeee list of different profiles....atm it's "analog stereo duplex".

---

### Post by NullHead on 2010-03-10
I think it's probably fine right there. 

It depends on your setup. If you've got regular speakers, make a selection from the "analog" portion of the list; same goes for your microphone. Use digital if you're having your sound go out of a SPDIF connector.

---

### Post by cozmoz on 2010-03-12
Hrm OK, thanks, the sound is working very nicely. But I can't get my microphone to work, just like previous posts - I can't hear myself and noone else can hear me.... I've done abit what you said, muted the microphone in alsamixer and enabled line-in, then did the vice verse. Not getting any results at all though :/


EDIT.

I'm using Mangler with some friends and they can hear themselves when I push my speak button! But they cannot hear me at all :{ hope that's something good and fixable.

EDIT2.

I've been going crazy and tried everything I could without getting anything recorded from the microphone....It's relay sad if I have to go back to Windows just because of this :S I've been back and forth a bit and now that I discovered Mangler I thought I'd go try Linux again since now there was not a program that I couldn't get running any more. And now the microphone just refuses to do anything..... O.O Gonna keep trying for a while though...

Pic of my Alsamixer (sry for making another reply when I could have just edited!)
[http://data.fuskbugg.se/skalman01/-alsamixer.jpg](http://data.fuskbugg.se/skalman01/-alsamixer.jpg)

EDIT3.

Thought I'd post some more pictures!
//Picture of my soundsettings.
[http://data.fuskbugg.se/skalman01/Soundsettings.jpg](http://data.fuskbugg.se/skalman01/Soundsettings.jpg)

//Picture of my soundsettings.
[http://data.fuskbugg.se/skalman01/Soundsettings2.jpg](http://data.fuskbugg.se/skalman01/Soundsettings2.jpg)

For the PCM to record sounds from the computer the Mic have to be on CAPTUR aswell.

EDIT4.

I did a Audio advice info with Audacity, the result was - "Capture volume is emulated. Playback volume is native."

EDIT5. 

Still havnt got it to work, pulling my own hair off : {

---

### Post by NullHead on 2010-03-12
Actually, what you describe in your edit tells me you have the recording set to PCM, which is labeled as "what you hear" in windows. You might take another look into alsamixer. Make sure you're editing the settings of your X-Fi and not an onboard soundcard, or a GPU digital sound card. The info is in the top left corner of alsamiser. 

I believe if you use the "." (period) button overtop of the PCM channel in the "capture" tab in Alsamixer, you can mute the PCM channel, so your VoIP application will hear your MIC and not PCM.

---

### Post by cozmoz on 2010-03-12
This post can be removed.

---

### Post by s.maciek on 2010-03-13
Hello
I am the owner of Creative SB X-Fi (e)Xtreme Audio Notebook ( + docking module ) and HP Pavilion dv5 1199ew. I am trying to connect those two for pretty long time. I have been so desperate, that I've sold this card 'coz I was so pissed of :P. But know, I have purhased the Logitech G51 and I want to work it under Linux ( Ubuntu ).
The disscusion about this in here took 50+ pages, and I am not sure if the problem is solved, so I am asking - is it ? Please, tell me what should I do to run it out. I can deliver anything ( I mean, what commands in console will "say" ) you want me to, but please let this work. Now, I have Ubuntu 9.10 64 bit and Ubuntu 10.04 alpha3.

Best regards, M.

---

### Post by NullHead on 2010-03-13
So essentially you just want to know if you purchase another X-Fi, if it'll work in Linux? Yes and no. 

Yes, it will probably work with linux. Any Linux distribution using a kernel at or greater than 2.6.31.X should have proper drivers available. Ubuntu 9.10 will work just fine. 

No, any older Linux distribution, such as Debian stable (Lenny) will not work unless you attempt to compile a barely working driver written by Creative. You'll probably have more luck breaking your system than getting Creative's driver working. 

Will a laptop Extreme Music card work? Quite honestly, I have no idea. It's worth a shot to buy it from a local computer store, slap it in your Ubuntu 9.10 laptop, and if it isn't working, simply return it.

---

### Post by NullHead on 2010-03-13
> EDIT.

I'm using Mangler with some friends and they can hear themselves when I push my speak button! But they cannot hear me at all :{ hope that's something good and fixable.

EDIT2.

I've been going crazy and tried everything I could without getting anything recorded from the microphone....It's relay sad if I have to go back to Windows just because of this :S I've been back and forth a bit and now that I discovered Mangler I thought I'd go try Linux again since now there was not a program that I couldn't get running any more. And now the microphone just refuses to do anything..... O.O Gonna keep trying for a while though...

Pic of my Alsamixer (sry for making another reply when I could have just edited!)
[http://data.fuskbugg.se/skalman01/-alsamixer.jpg](http://data.fuskbugg.se/skalman01/-alsamixer.jpg)

EDIT3.

Thought I'd post some more pictures!
//Picture of my soundsettings.
[http://data.fuskbugg.se/skalman01/Soundsettings.jpg](http://data.fuskbugg.se/skalman01/Soundsettings.jpg)

//Picture of my soundsettings.
[http://data.fuskbugg.se/skalman01/Soundsettings2.jpg](http://data.fuskbugg.se/skalman01/Soundsettings2.jpg)

For the PCM to record sounds from the computer the Mic have to be on CAPTUR aswell.

EDIT4.

I did a Audio advice info with Audacity, the result was - "Capture volume is emulated. Playback volume is native."

EDIT5.

Still havnt got it to work, pulling my own hair off : {

Try turning PCM channel down all the way to the bottom, then doing the same to each other channel listed in "capture" and turning up the mic channel only.

---

### Post by MerlinW on 2010-03-13
I made a little script for myself, which installs the Alsa driver v1.0.21 with 5.1 settings. It's made for Jaunty, Karmic don't need it.

Maybe can use somebody else too...
[xfi-install.sh]("http://merlinw.org/scripts/xfi-install.sh")

---

### Post by NullHead on 2010-03-13
> **NullHead said:**
> So essentially you just want to know if you purchase another X-Fi, if it'll work in Linux? Yes and no. 

Yes, it will probably work with linux. Any Linux distribution using a kernel at or greater than 2.6.31.X should have proper drivers available. Ubuntu 9.10 will work just fine. 

No, any older Linux distribution, such as Debian stable (Lenny) will not work unless you attempt to compile a barely working driver written by Creative. You'll probably have more luck breaking your system than getting Creative's driver working. 

Will a laptop Extreme Music card work? Quite honestly, I have no idea. It's worth a shot to buy it from a local computer store, slap it in your Ubuntu 9.10 laptop, and if it isn't working, simply return it.

> **MerlinW said:**
> I made a little script for myself, which installs the Alsa driver v1.0.21 with 5.1 settings. It's made for Jaunty, Karmic don't need it.

Maybe can use somebody else too...
[xfi-install.sh]("http://merlinw.org/scripts/xfi-install.sh")

I had a brain fart and totally forgot that you could simply install the latest Alsa. 

Thanks for the script! Looks useful :)

---

### Post by s.maciek on 2010-03-13
Thanks for your response.
I have already bought another X-Fi :-). It still work with Win7 with no problems, but my "main" system is Ubuntu.

Here are commands which could be helpfull for you, if u want to help me :-P :
```
macio:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 13 2010 for kernel 2.6.31-20-generic (SMP).

```
And another ones
lspci
[http://wklej.org/id/295960/](http://wklej.org/id/295960/)

aplay -l
[http://wklej.org/id/295961/](http://wklej.org/id/295961/)

lsmod | grep snd
[http://wklej.org/id/295962/](http://wklej.org/id/295962/)

cat /proc/asound/modules
[http://wklej.org/id/295964/](http://wklej.org/id/295964/)

So, what should I do ?

---

### Post by MerlinW on 2010-03-13
Try: 
sudo modprobe ctxfi
sudo asoundconf set-default-card XFi
sudo reboot

Or try my script, it could be help you. (#543)
1. That script will restart your computer after it's finished
2. Look into the file, I wrote the next steps inside.

---

### Post by s.maciek on 2010-03-13
> **MerlinW said:**
> Try: 
sudo modprobe ctxfi
sudo asoundconf set-default-card XFi
sudo reboot

Or try my script, it could be help you. (#543)

I believe, that you ment **snd-ctxfi**

When I try to run that "asoundconf", it says "command not found". How can I install it ?

I have already looked closely at ur script. Its really great, but are you sure it will work for my card ( I say again, its Creative SB X-Fi Xtreme **Audio Notebook** ) ??

---

### Post by MerlinW on 2010-03-13
Well, I have X-fi ExtremeGamer, and it's worked. Try it, if something wrong, u can reinstall the current Alsa from repo. The script do nothing card specific thing (i mean card type). It should be work all X-fi cards.

---

### Post by s.maciek on 2010-03-13
But the thing is that I have compiled the newest alsa version fro source today. Look few posts upper. Will it change anything ??

**edit:**
After today's compilation it looks like this :
```
macio:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Mar 13 2010 for kernel 2.6.31-20-generic (SMP).

```
Should I still use your script ?

---

### Post by MerlinW on 2010-03-13
Uhm.. no:) Hm, I look around too for u...

---

### Post by s.maciek on 2010-03-13
So what should I do now ?
I want to say one thing more. From all steps, that ur script is doing, I have done today only one - compiling alsa-driver-1.0.22.1          alsa-lib-1.0.22 ; alsa-plugins-1.0.22 ; alsa-utils-1.0.22. and after that turn snd-ctxfi on. That's all. What now ?

---

### Post by cozmoz on 2010-03-13
> **NullHead said:**
> Try turning PCM channel down all the way to the bottom, then doing the same to each other channel listed in "capture" and turning up the mic channel only.

Tried it now...no result...but I'm not giving up yet. Is there anything else that I could try that you haven't mentioned?

---

### Post by NullHead on 2010-03-13
> **s.maciek said:**
> So what should I do now ?
I want to say one thing more. From all steps, that ur script is doing, I have done today only one - compiling alsa-driver-1.0.22.1          alsa-lib-1.0.22 ; alsa-plugins-1.0.22 ; alsa-utils-1.0.22. and after that turn snd-ctxfi on. That's all. What now ?

After you load the module, paste the output of this: ```
dmesg | tail
```

> **cozmoz said:**
> Tried it now...no result...but I'm not giving up yet. Is there anything else that I could try that you haven't mentioned?
I can't think of anything. You could try removing pulseaudio.
The X-Fi is capable of mixing your sounds on the card, so you technically don't "need" pulseaudio anymore. It might be messing with your mic.

---

### Post by cozmoz on 2010-03-14
Ok, I removed Pulseaudio with Synaptic, now it won't let me configure anything...when trying to open the sound configuration it tells me that it's waiting to the soundsystem to start :S This is very confusing...seems it relays on Pulseaudio or something. I can't play mp3 songs with Rythmbox either.

EDIT.

However I can watch videos with VLC and I get sound there. Mangler won't start either.

[http://data.fuskbugg.se/skalman01/somthing.jpg](http://data.fuskbugg.se/skalman01/somthing.jpg) < Translation : Waiting for the soundsystem to answer

EDIT2.

Skype acculy started so I went into the settings there, here's what I see in the "choose sound device for microphone" list.

[http://data.fuskbugg.se/skalman01/okay.jpg](http://data.fuskbugg.se/skalman01/okay.jpg)

*Now Rythmbox starts aswell, sound works. However I'm not able to configurate the sound from the system menu.

EDIT3.

Oh what I'm thinking of going back to crappy windows, just to get the mic working again.

EDIT4. I'm giving up. Thanks for trying to help me NullHead <3, cya around.

---

### Post by s.maciek on 2010-03-14
> **NullHead said:**
> After you load the module, paste the output of this: ```
dmesg | tail
```

Okay, he it is :
```
[17:55] macio:~$ lsmod | grep ctxfi
[17:55] macio:~$ sudo modprobe snd-ctxfi 
[sudo] password for macio: 
[17:56] macio:~$ lsmod | grep ctxfi
snd_ctxfi              97672  0 
snd_pcm                93704  4 snd_ctxfi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd                    78184  24 snd_ctxfi,snd_hda_codec_ca0110,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
[17:56] macio:~$ dmesg | tail
[  236.451148] nvclock:2940 freeing invalid memtype d2000000-d2010000
[  236.623444] nvclock:2940 freeing invalid memtype d2010000-d2030000
[  257.462069] nvclock:2997 freeing invalid memtype d2000000-d2010000
[  257.629571] nvclock:2997 freeing invalid memtype d2010000-d2030000
[  278.448818] nvclock:3143 freeing invalid memtype d2000000-d2010000
[  278.617082] nvclock:3143 freeing invalid memtype d2010000-d2030000
[  299.435882] nvclock:3206 freeing invalid memtype d2000000-d2010000
[  299.605409] nvclock:3206 freeing invalid memtype d2010000-d2030000
[  320.463654] nvclock:3303 freeing invalid memtype d2000000-d2010000
[  320.634416] nvclock:3303 freeing invalid memtype d2010000-d2030000

```

Do I have to load the snd-ctxfi module every time I want to use the card ??

---

### Post by NullHead on 2010-03-15
Well, if you boot the machine and the module isn't loaded, you can add snd_ctxfi to /etc/modules and it'll load up at boot.

---

### Post by s.maciek on 2010-03-15
> **NullHead said:**
> Well, if you boot the machine and the module isn't loaded, you can add snd_ctxfi to /etc/modules and it'll load up at boot.

Okay ...

But what should I do now ? You asked me to send you those info, what next ?

---

### Post by NullHead on 2010-03-15
> **s.maciek said:**
> Okay ...

But what should I do now ? You asked me to send you those info, what next ?

dmesg | tail didn't actually provide the information I was looking for, if you could run this instead:```
dmesg > dmesg.txt
``` 

Upload the file to a filesharing site. You can use [pastebin](http://pastebin.com) to paste the text into. or you can use [stashbox](http://stashbox.org).

I'm sorry I'm not really a programmer/developer, so if this doesn't provide any interesting info, I suggest you take this over to a thread on the [Alsa-develepment](http://mailman.alsa-project.org/pipermail/alsa-devel/[/url) maililng list.

---

### Post by s.maciek on 2010-03-15
I think, this is you are looking for :

[http://wklej.org/id/297464/](http://wklej.org/id/297464/)

About that link you gave me. Do you think, there I will get help I need ??

---

### Post by kooldino on 2010-03-22
I was running something recently and the sound started kind of skipping and going wacky, so I rebooted.  When the system came back up, I had no sound.  I followed the instructions in the first step and I've still got no sound, despite everything seemingly installing properly.

---

### Post by kooldino on 2010-03-22
bump.

I really need sound.

---

### Post by NullHead on 2010-03-23
What version of ubuntu are you running (lsb_release -a) and what guide specifically did you use to get your X-Fi working?

---

### Post by kooldino on 2010-03-23
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

I used the guide in post 1 of this thread.

---

### Post by s.maciek on 2010-03-23
Have you upgraded your kernel recently ?

---

### Post by kooldino on 2010-03-24
> **s.maciek said:**
> Have you upgraded your kernel recently ?

Nope.  I had that issue in the past where I had to reinstall due to a new kernel.   This was different.  It worked, but the sound started skipping/echoing.  So I rebooted it and bam - never worked again.

---

### Post by NullHead on 2010-03-25
I think it's safe to say you can upgrade from Creative's driver to the latest blend of Alsa's driver. [This](http://wiki.debian.org/X-Fi) guide looks pretty good to me, and I think it'll probably work. 

Make sure to uninstall Creative's drivers first, and reboot before attempting the steps in that guide. 

Please note, I have not tested that guide, so I can't guarantee it'll work, but if you'd like, I will test it. I just need some time to do so.

---

### Post by kooldino on 2010-03-29
Sorry to sound like a n00b here, but I searched the thread and couldn't find instructions on how to uninstall my current Creative ALSA drivers.  

I'm running KDE 4 and there's no obvious way to do it via the GUI.

---

### Post by NullHead on 2010-03-30
> **kooldino said:**
> Sorry to sound like a n00b here, but I searched the thread and couldn't find instructions on how to uninstall my current Creative ALSA drivers.  

I'm running KDE 4 and there's no obvious way to do it via the GUI.

open the terminal window(kterm I think it is?), cd to the build directory of the Creative driver, and run "*sudo make uninstall*".

---

### Post by kooldino on 2010-03-30
> **NullHead said:**
> open the terminal window(kterm I think it is?), cd to the build directory of the Creative driver, and run "*sudo make uninstall*".

Ten four, I'll give that a whirl tonight.

---

### Post by kooldino on 2010-03-30
There's no folder on my hard drive called "XFiDrv_Linux_Public*", I likely deleted it after the driver was installed.  There's gotta be another way to uninstall this.

Edit: Trying it a diff way, will report results.

---

### Post by NullHead on 2010-03-30
You can re-download the package, extract it and type in "make" and you've got another build directory. You can then type in "sudo make uninstall" and it *should* uninstall.

---

### Post by kooldino on 2010-03-30
Yep, that's what I did.

The link you provided for the new driver installation worked well!  I have sound again!  Thank you!

---

### Post by NullHead on 2010-03-30
You're quite welcome :popcorn:

---

### Post by Jaygo333 on 2010-04-05
Not to resurrect an old ongoing thread but I also seem to be having trouble getting me X-Fi working.

I decided to follow the link posted by a member a couple of weeks ago and install using: [http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

All installs and makes well. I seem to get stuck on number 8.
after I've unmuted using alsamixer, I still get no sound using the example wav or any sound for that matter.

The install did go fine and I received no error at all.

In the alsamixer menu, the description given for the device is: HDA Intel 
Just wondering if this is right. 
I have Creative XtremeMusic.

---

### Post by NullHead on 2010-04-05
Have you disabled your onboard audio? You can do so from inside your BIOS. 

Is sounds to me like alsamixer is controlling your HDA onboard audio instead of the X-Fi chip.

---

### Post by charlesbw on 2010-04-06
i am running 9.10 and i get this scratched up audio whenever i play a song on rythmbox music player.

---

### Post by NullHead on 2010-04-07
From what I experienced, rhythmbox doesn't play well with the X-Fi chips/driver. I'd suggest using banshee or audacious.

---

### Post by mhenriday on 2010-04-07
> **NullHead said:**
> From what I experienced, rhythmbox doesn't play well with the X-Fi chips/driver. I'd suggest using banshee or audacious.
**VLC** works well, as well....

Henri

---

### Post by notacluenoob on 2010-04-13
To anyone that might be able to help me:

I'm having trouble getting sound from a PCI-E version of the X-Fi. After following post 1 of this thread, I was able to get Ubuntu 9.04 working with sound beautifully. I had to edit the ctdrv.h file in order to make it work. But, when I upgraded to 9.10, no luck. If there is a ctdrv.h file, I can't find it. Right now I'm using the latest beta release of 10.04 with all updates as of this writing (April 13, 2010), but still no luck. The sound card is recognized with lspci -v, just no kernel driver in use. Since I am pretty new to Ubuntu and its inner workings, if you need any output or for me to run any commands, please tell me exactly how to do so, as I most likely won't understand you otherwise.

Thank you all for your time,

notacluenoob

---

### Post by NullHead on 2010-04-13
Try loading the proper driver and posting the output of the command "dmesg | tail" after you've run this here command: ```
sudo modprobe snd-ctxfi
```

If there's any errors or warnings after you've loaded the module, paste those here too.

---

### Post by notacluenoob on 2010-04-13
Thank you for your reply, NullHead. Unfortunately, I didn't get too far with the install. This is what I ended up with after trying to install from Post #1 just from the first step (I wasn't sure if I should go any further.):

hfdwhalers1@hfdwhalers1:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers- `uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.32-20-generic

And if you still need it, here is the output of dmesg | tail after running sudo modprobe snd-ctxfi:

hfdwhalers1@hfdwhalers1:~$ sudo modprobe snd-ctxfi
[sudo] password for hfdwhalers1: 
hfdwhalers1@hfdwhalers1:~$ dmesg |tail
[   14.623829] type=1505 audit(1271194615.676:6):  operation="profile_replace" pid=939 name="/sbin/dhclient3"
[   14.624064] type=1505 audit(1271194615.676:7):  operation="profile_replace" pid=939 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.624197] type=1505 audit(1271194615.676:8):  operation="profile_replace" pid=939 name="/usr/lib/connman/scripts/dhclient-script"
[   14.627468] type=1505 audit(1271194615.676:9):  operation="profile_load" pid=940 name="/usr/bin/evince"
[   14.630454] type=1505 audit(1271194615.686:10):  operation="profile_load" pid=940 name="/usr/bin/evince-previewer"
[   14.634361] type=1505 audit(1271194615.686:11):  operation="profile_load" pid=940 name="/usr/bin/evince-thumbnailer"
[   14.643159] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   15.010874] ppdev: user-space parallel port driver
[   15.812254] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   25.570025] eth0: no IPv6 routers present

I hope this helps you help me out, NullHead.

Thank you again,

notacluenoob

P.S. The smiley face is actually "8". I couldn't get it to come out otherwise.

---

### Post by NullHead on 2010-04-14
> **notacluenoob said:**
> Thank you for your reply, NullHead. Unfortunately, I didn't get too far with the install. This is what I ended up with after trying to install from Post #1 just from the first step (I wasn't sure if I should go any further.):

hfdwhalers1@hfdwhalers1:~/Desktop/XFiDrv_Linux_Public_US_1.00$ sudo apt-get install build-essential linux-headers- `uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers is not installed, so not removed
E: Couldn't find package 2.6.32-20-generic

And if you still need it, here is the output of dmesg | tail after running sudo modprobe snd-ctxfi:

hfdwhalers1@hfdwhalers1:~$ sudo modprobe snd-ctxfi
[sudo] password for hfdwhalers1: 
hfdwhalers1@hfdwhalers1:~$ dmesg |tail
[   14.623829] type=1505 audit(1271194615.676:6):  operation="profile_replace" pid=939 name="/sbin/dhclient3"
[   14.624064] type=1505 audit(1271194615.676:7):  operation="profile_replace" pid=939 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.624197] type=1505 audit(1271194615.676:8):  operation="profile_replace" pid=939 name="/usr/lib/connman/scripts/dhclient-script"
[   14.627468] type=1505 audit(1271194615.676:9):  operation="profile_load" pid=940 name="/usr/bin/evince"
[   14.630454] type=1505 audit(1271194615.686:10):  operation="profile_load" pid=940 name="/usr/bin/evince-previewer"
[   14.634361] type=1505 audit(1271194615.686:11):  operation="profile_load" pid=940 name="/usr/bin/evince-thumbnailer"
[   14.643159] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   15.010874] ppdev: user-space parallel port driver
[   15.812254] usb 3-1: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[   25.570025] eth0: no IPv6 routers present

I hope this helps you help me out, NullHead.

Thank you again,

notacluenoob

P.S. The smiley face is actually "8". I couldn't get it to come out otherwise.

You should check out this guide: [http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi)

I think it should solve your problems.

---

### Post by notacluenoob on 2010-04-15
Thank you again for your reply, NullHead. I feel that we are getting there, but I'm getting stuck at step 8 of the guide. I keep on getting this error message:

hfdwhalers1@hfdwhalers1:~$ alsamixer
cannot open mixer: No such file or directory

I tried Googling around a bit and came up empty with something that actually worked. The one thing I did try was install linux-backports-modules-alsa-lucid-generic from Synaptic Package Manager, but that didn't work, either.

Any other ideas, NullHead?

Thank you for all of your help,

notacluenoob

---

### Post by NullHead on 2010-04-15
> **notacluenoob said:**
> Thank you again for your reply, NullHead. I feel that we are getting there, but I'm getting stuck at step 8 of the guide. I keep on getting this error message:

hfdwhalers1@hfdwhalers1:~$ alsamixer
cannot open mixer: No such file or directory

I tried Googling around a bit and came up empty with something that actually worked. The one thing I did try was install linux-backports-modules-alsa-lucid-generic from Synaptic Package Manager, but that didn't work, either.

Any other ideas, NullHead?

Thank you for all of your help,

notacluenoob

Lets try removing your .asoundrc file. ```
mv ~/.asoundrc ~/.asoundrc.bak
```

Honestly I'm not sure about this problem, but I got the idea from [here]("http://forums.debian.net/viewtopic.php?f=6&t=45884").

---

### Post by mhenriday on 2010-04-15
> **notacluenoob said:**
> ...

P.S. The smiley face is actually "8". I couldn't get it to come out otherwise.
**Notacluenoob**, try disabling smilies in your postings by ticking the relevant box under »Miscellaneous options«. That should restore the «8»....

Henri

---

### Post by notacluenoob on 2010-04-15
> **mhenriday said:**
> **Notacluenoob**, try disabling smilies in your postings by ticking the relevant box under »Miscellaneous options«. That should restore the «8»....

Henri

Thank you Henri, I don't know how I missed that! I guess my name says it all...

notacluenoob

---

### Post by notacluenoob on 2010-04-15
> **NullHead said:**
> Lets try removing your .asoundrc file. ```
mv ~/.asoundrc ~/.asoundrc.bak
```Honestly I'm not sure about this problem, but I got the idea from [here]("http://forums.debian.net/viewtopic.php?f=6&t=45884").

Unfortunately, no luck NullHead. It says that the file doesn't exist. I do have hidden files turned on, too, if this makes a difference. I know the card is still good as I have a dual-boot with XP that still has no problems with sound. I did make a backup of my Ubuntu partition before I tried anything. Do you think that I should "turn back the clock" and try something different this time around from a clean slate?

Thanks again for all of your help NullHead,

notacluenoob

---

### Post by notacluenoob on 2010-04-18
NullHead,
 
Just an FYI about the X-Fi Debian link that you gave me before ([[COLOR=#000000]http://wiki.debian.org/X-Fi[/COLOR]]("http://wiki.debian.org/X-Fi"))
...It was updated on 4/15/10 and seems to have changed since you gave it to me. It is only listing Denny and Squeeze as distributions for installation instructions. I guess Ubuntu isn't included anymore? Or, if it is, I wouldn't know how to translate the instructions for it to Ubuntu.
 
Anyways, hope you're having a good weekend NullHead,
 
notacluenoob

---

### Post by PinchedNerve on 2010-04-18
Nevermind, I fixed it.

---

### Post by NullHead on 2010-04-19
> **notacluenoob said:**
> NullHead,
 
Just an FYI about the X-Fi Debian link that you gave me before ([[COLOR=#000000]http://wiki.debian.org/X-Fi[/COLOR]]("http://wiki.debian.org/X-Fi"))
...It was updated on 4/15/10 and seems to have changed since you gave it to me. It is only listing Denny and Squeeze as distributions for installation instructions. I guess Ubuntu isn't included anymore? Or, if it is, I wouldn't know how to translate the instructions for it to Ubuntu.
 
Anyways, hope you're having a good weekend NullHead,
 
notacluenoob

My weekend was great, thanks! 

I think I'll work on a guide specific for updating alsa for X-Fi users. It will probably be a generic guide, but I'll post it here and put a link on the first page. 

If you could, would you boot up a liveCD version of ubuntu 9.10 or 10.04 beta2 and test the audio? You're using an upgraded version of 9.10, which to me doesn't sound like a problem, but I guess it *could* be one. 

You don't have to install the liveCD, but if the audio works, it's up to you. At this point, I'm not completely sure what's wrong with your currently installed version; there shouldn't be a problem.

---

### Post by psidrum on 2010-04-19
does anyone know how to get the X-Fi I/O drivebay working?

i have one but it does not work, the soundcard works but any of the inputs for the drivebay does not work,

anyone have this working?

[IMG]http://www.techspot.com/reviews/hardware/soundblaster_xfi/drivebay.jpg[/IMG]

---

### Post by notacluenoob on 2010-04-19
> **NullHead said:**
> My weekend was great, thanks! 
 
I think I'll work on a guide specific for updating alsa for X-Fi users. It will probably be a generic guide, but I'll post it here and put a link on the first page. 
 
If you could, would you boot up a liveCD version of ubuntu 9.10 or 10.04 beta2 and test the audio? You're using an upgraded version of 9.10, which to me doesn't sound like a problem, but I guess it *could* be one. 
 
You don't have to install the liveCD, but if the audio works, it's up to you. At this point, I'm not completely sure what's wrong with your currently installed version; there shouldn't be a problem.
 
Hi NullHead,
 
No luck again. I tried the 9.10 liveCD version and came up empty. You know, it's interesting. Ever since I became interested in computers, I've had this curse...they never like me in return! :rolleyes: Hopefully, by the time Microsoft ditches XP, I'll have sound in Ubuntu. For now, I'll just have to dabble around in Ubuntu w/o sound.
 
Thank you for all of your help, NullHead, I really have appreciated it.
 
notacluenoob

---

### Post by NullHead on 2010-04-20
> **psidrum said:**
> does anyone know how to get the X-Fi I/O drivebay working?

i have one but it does not work, the soundcard works but any of the inputs for the drivebay does not work,

anyone have this working?

[IMG]http://www.techspot.com/reviews/hardware/soundblaster_xfi/drivebay.jpg[/IMG]

As far as I know, the X-Fi drivebay doesn't work in linux at all. Not with any of the drivers available.

---

### Post by CLEARviewF on 2010-04-22
Hi Nullhead,

First of all, Thank you for all your work in this issue/subject.

I want to buy an external USB sound card, for my PC because I love quality in sound and read that external sound cards are the best for PC's, and, even better, if they get power from and external source instead of taking it from the USB port itself.

I was thinking about a Creative X-Fi, because I see it in the Peruvian market. So, what I want is you to advice the best external USB sound device for this matter. The only thing to consider is that the price has to be less than USD $90.

Maybe you could make a little list of devices to consider.

Thank you!

---

### Post by NullHead on 2010-04-22
> **CLEARviewF said:**
> Hi Nullhead,

First of all, Thank you for all your work in this issue/subject.

I want to buy an external USB sound card, for my PC because I love quality in sound and read that external sound cards are the best for PC's, and, even better, if they get power from and external source instead of taking it from the USB port itself.

I was thinking about a Creative X-Fi, because I see it in the Peruvian market. So, what I want is you to advice the best external USB sound device for this matter. The only thing to consider is that the price has to be less than USD $90.

Maybe you could make a little list of devices to consider.

Thank you!

As I don't have experience with any professional grade equipment, I can only read specs on cards and choose what seems the best, but regardless of that, here is a list of, in no particular order, USB devices I feel look like the best devices: 

[Creative X-Fi Surround 5.1 SB1090 - $59.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102020")
Note: I have no idea if this will work in linux or not

[Auzentech INFRASONIC Amon 24-bit 96KH - $139.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829156008")
I know it's a bit over-budget, but it looks pretty nice

[Turtle Beach Audio Advantage Micro Virtual 5.1 Surround - $29.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829118107")

[SIIG CE-S00022-S1 Virtual 7.1 - $33.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829270004")
This is probably my favorite one. Unsure if it works in linux. 

Frankly, I'm not impressed with the budget USB sound card market, but I think PCI/PCI-E sound cards are definitely an option if you're looking for high quality audio:

[Auzen X-Fi Bravura 7.1 - $134.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829156015")
Again, over budget, but this definitely looks like a really well built card. There are also very good reviews for it. Unsure if it works in linux or not. 

[Creative X-Fi Extreme Gamer - $99.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102006")
This card is $74.99 after rebate. I own this card, and I'm pleased with it. Drivers for windows 7 work decently enough that I don't experience any issues, and drivers for ubuntu 9.10+ are pretty good too.

I'm actually going to up grade my card to the Auzentech Bravura within the next few months, so I'll post here to let you all know if it works in linux or not. 

[ASUS Xonar DX 7.1 PCI-E - $89.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829132006")
Again, I'm unsure if this one works in Linux or not, but it appears to be a nice card.

---

### Post by CLEARviewF on 2010-04-22
> 
[Creative X-Fi Surround 5.1 SB1090 - $59.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102020")
Note: I have no idea if this will work in linux or not

In your own words at the beginning of this thread:
> 
...As of Ubuntu 9.10 (Karmic Koala), the Creative X-Fi soundcard will work out of the box!


This is the main reason I am here asking for your recommendation :D

---

### Post by CLEARviewF on 2010-04-22
> **NullHead said:**
> [Creative X-Fi Extreme Gamer - $99.99]("http://www.newegg.com/Product/Product.aspx?Item=N82E16829102006")
This card is $74.99 after rebate. I own this card, and I'm pleased with it. Drivers for windows 7 work decently enough that I don't experience any issues, and drivers for ubuntu 9.10+ are pretty good too.

Thank you NullHead!

As you use this device and It works pretty good for you in Ubuntu Karmic+, then I will have this in mind. But this is not an USB Sound card. I am looking for tested USB sound cards in Ubuntu Karmic+ with positive results.

Please, let me know if you test USB sound cards in the future.

Bye!

---

### Post by sanderh79 on 2010-04-24
Just wanted to add my experience with Ubuntu 10 rc, my X-Fi (CA0110-IBG) does NOT work 'out of the box' (neither did it on any previous ubuntu versions). Everything worked great, except for sound.  Downloaded the linux drivers from Creative, didn't work (couldn't make  it, cba). I had to remove alsa and install oss to get it going by following the OSS guide: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound), after that sound works.

---

### Post by NullHead on 2010-04-24
> **sanderh79 said:**
> Just wanted to add my experience with Ubuntu 10 rc, my X-Fi (CA0110-IBG) does NOT work 'out of the box' (neither did it on any previous ubuntu versions). Everything worked great, except for sound.  Downloaded the linux drivers from Creative, didn't work (couldn't make  it, cba). I had to remove alsa and install oss to get it going by following the OSS guide: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound), after that sound works.

I'm glad you got it working. As this Creative "X-Fi" Extreme audio isn't really a true X-Fi (20k1/20k2 chipset) sound card, from what I understand, this card uses the [ca0106]("http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106") module. That module appears to work for Extreme audio cards, but as I don't have one, I can't really test it. 

The [Alsa sound card matrix]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") had a really good outline of what cards have what chipset, and what modules go to what card.

I personally would fight to get alsa working.

---

### Post by beyondcr on 2010-04-28
So will the creative xfi extreme work out of box with 10.4? I cannot get  it to work with 10.4 rc ... I haven't tried oss for the fact that I thought Ubuntu was doing away with oss so I did not want to go that route....

---

### Post by NullHead on 2010-04-29
Well yes it *should* work out of the box for ubuntu 9.10+, and no, ubuntu is not doing away with OSS. Oss is a third party project that supports many variations of linux. OSS should technically always work with ubuntu or any version of linux that is; as long as OSS remains a opensource/community driven project.

---

### Post by beyondcr on 2010-04-29
Ok so my creative Xfi card should work in 10.4 with out messing with drivers or anything? because I don't see it in the mixer....

---

### Post by NullHead on 2010-04-29
Is this an X-Fi extreme audio, music or gamer?

---

### Post by PowerSource on 2010-04-29
i just updated the kernel to 2.6.31-21-generic an suddeny the sound in flash isn't working at all. amarok isn't having problems.
any idea how to fix this?

---

### Post by PowerSource on 2010-04-29
ok, now it seems to work.
but it's still as choppy as always. after two minutes into most videos on youtube, the video/sound gets all 'jumpy' for a while.
is there a fix for download or do i have to bash my keyboard until someone decides to fix this ****.

---

### Post by DaveBG on 2010-05-07
I fixed it, after setting to X-Fi in the output it did work.

---

### Post by PowerSource on 2010-05-22
Now the sound card only seems to work every other time I boot the computer.
Those times the sound won't work at all and amarok gives a popup saying something like:
"the playback thing is broken."

in some errors i've seen "pulseaudio" being mentioned, but I guess that is just because it is ps that is trying to take care of the card.
got any idea if this is because of a new kernel/ubuntu/driver/pulseaudio?
this is so annoying.

---

### Post by NullHead on 2010-05-22
Reboot your computer to where the sound isn't working again, and run: ```
dmesg | tail
```

Are you running Creative's driver via the guide on the first post? Because you shouldn't be. Most people now a' days should be running a new enough version of ubuntu to get out of the box support from the kernel/alsa. 

If the results in there don't show me anything, I can't really help you. I have never heard of such a thing happening before.

---

### Post by PowerSource on 2010-05-22
the old driver is uninstalled, or so i think. you told me how to do it a couple of pages back. of what i can remember it worked as it should.

here the output of that command is, I skipped rebooting since it doesn't work now:
[50681.125365] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=83.161.128.54 DST=192.168.1.66 LEN=88 TOS=0x00 PREC=0x00 TTL=54 ID=35003 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.1.66 DST=83.161.128.54 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=3633 DF PROTO=TCP SPT=53475 DPT=17650 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
[50682.177405] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=88.73.77.1 DST=192.168.1.66 LEN=88 TOS=0x00 PREC=0x00 TTL=55 ID=57271 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.1.66 DST=88.73.77.1 LEN=60 TOS=0x00 PREC=0x00 TTL=55 ID=47456 DF PROTO=TCP SPT=56972 DPT=51412 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
[50683.467453] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=187.47.29.36 DST=192.168.1.66 LEN=52 TOS=0x00 PREC=0x00 TTL=105 ID=28322 DF PROTO=TCP SPT=22953 DPT=45939 WINDOW=64 RES=0x00 ACK FIN URGP=0 
[50685.218055] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=189.114.229.136 DST=192.168.1.66 LEN=40 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=16883 DPT=39766 WINDOW=0 RES=0x00 RST URGP=0 
[50685.929741] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=189.114.229.136 DST=192.168.1.66 LEN=40 TOS=0x00 PREC=0x00 TTL=43 ID=0 DF PROTO=TCP SPT=16883 DPT=33225 WINDOW=0 RES=0x00 RST URGP=0 
[50691.937448] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=83.161.128.54 DST=192.168.1.66 LEN=88 TOS=0x00 PREC=0x00 TTL=54 ID=35004 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.1.66 DST=83.161.128.54 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=36513 DF PROTO=TCP SPT=34856 DPT=17650 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
[50695.054389] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=83.161.128.54 DST=192.168.1.66 LEN=88 TOS=0x00 PREC=0x00 TTL=54 ID=35005 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.1.66 DST=83.161.128.54 LEN=60 TOS=0x00 PREC=0x00 TTL=53 ID=36514 DF PROTO=TCP SPT=34856 DPT=17650 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
[50695.860722] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=88.73.77.1 DST=192.168.1.66 LEN=88 TOS=0x00 PREC=0x00 TTL=55 ID=57272 PROTO=ICMP TYPE=3 CODE=1 [SRC=192.168.1.66 DST=88.73.77.1 LEN=60 TOS=0x00 PREC=0x00 TTL=55 ID=30382 DF PROTO=TCP SPT=34535 DPT=51412 WINDOW=5840 RES=0x00 SYN URGP=0 ] 
[50750.107716] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=69.63.176.197 DST=192.168.1.66 LEN=225 TOS=0x00 PREC=0x00 TTL=81 ID=18670 DF PROTO=TCP SPT=80 DPT=51685 WINDOW=8760 RES=0x00 ACK PSH URGP=0 
[50793.110334] [UFW BLOCK] IN=wlan2 OUT= MAC=00:11:50:89:37:df:00:1f:9f:eb:da:ae:08:00 SRC=90.7.197.218 DST=192.168.1.66 LEN=40 TOS=0x00 PREC=0x00 TTL=44 ID=0 DF PROTO=TCP SPT=51413 DPT=34947 WINDOW=0 RES=0x00 RST URGP=0

---

### Post by kleei2 on 2010-05-27
Hmmm.... for whatever it's worth I was getting that same "Error inserting ctxfi.."
Before that message I noticed it complaining about ignoring a few non-*.conf files I made in /etc/modeprobe.d/ (alsa-base.conf.backup & blacklist.conf.backup)

I deleted those backups, deleted the XFi folder, re-untar'd and started from there and it successfully installed... maybe just a coincidence

---

### Post by PowerSource on 2010-05-28
now it seems to not work at any time :'(

---

### Post by PowerSource on 2010-05-29
when i just started my computer, and after a while started some programs a black screen came up (looked like a kernel panic but it didn't have any of the error messages(i looked on a screenshot on wikipedia)) with errors about ext3.
i just restarted my computer and it works now, but i remember the harddrive icons being on the desktop right before the crash. they're not there now, just the "computer" icon.
should i create a thread for this issue? it may have to to with the sound card, or it's juts some kernel bug.

---

### Post by NullHead on 2010-05-29
Well, you might try booting a live ubuntu 10.04 disk and checking the sound. Wile you're at it, run a fsck.ext3 -a on your filesystem. Make sure your filesystem is unmounted, btw. 

I guess if the problem persists, we can look further into some logs and see if we can tell what's happening.

---

### Post by PowerSource on 2010-05-29
> **NullHead said:**
> Well, you might try booting a live ubuntu 10.04 disk and checking the sound. Wile you're at it, run a fsck.ext3 -a on your filesystem. Make sure your filesystem is unmounted, btw. 

I guess if the problem persists, we can look further into some logs and see if we can tell what's happening.

so i'm supposed todo this while i'm in the live-cd
*play the test-sound/video and see if the sound works
*run that command. how do i make sure the filesystem is unmounted?

---

### Post by The Bright Side on 2010-05-29
Hi everybody!

I just bought this baby and am happy that it works out of the box so easily in Lucid. The reason I bought it is because it has an optical output, which my onboard 7.1 card doesn't have - and I just got an SACD player and want to buy a nice Hi-Fi 5.1 system for it.

One thing is confusing me: the output options I have in the Sound Preferences for the SB X-Fi Surround 5.1 include all kinds of Analog 5.1 (or other multichannel) constellations, but the only digital output options I have are three constellations of **Digital Stereo (IEC958 )**.

Is that my optical output?

If so, why is there no multichannel for it? It's supposed to feed both stereo and multichannel to the receiver.

Will it automatically be recognized as multichannel by my new receiver when a 5.1 stream comes through?

---

### Post by NullHead on 2010-05-29
> **The Bright Side said:**
> Hi everybody!

I just bought this baby and am happy that it works out of the box so easily in Lucid. The reason I bought it is because it has an optical output, which my onboard 7.1 card doesn't have - and I just got an SACD player and want to buy a nice Hi-Fi 5.1 system for it.

One thing is confusing me: the output options I have in the Sound Preferences for the SB X-Fi Surround 5.1 include all kinds of Analog 5.1 (or other multichannel) constellations, but the only digital output options I have are three constellations of **Digital Stereo (IEC958 )**.

Is that my optical output?

If so, why is there no multichannel for it? It's supposed to feed both stereo and multichannel to the receiver.

Will it automatically be recognized as multichannel by my new receiver when a 5.1 stream comes through?

Honestly I couldn't tell you. The digital that you speak of sounds to me like your HDMI connection, not the digital on your X-Fi. 

I've never had the luxury of playing with a nice receiver, so I'm at a loss here.

---

### Post by PowerSource on 2010-06-01
i've figured out a bit more, so now it may be easier to localize the problem.

every other time i start the computer, either everything works as it should, or only the main hdd's are mounted and the sound doesn't work. also when i press shut down/restart the only thing that happens is that i log out and to shut down the computer i have to do it manually.
the cd-players, usb-connections(except the mouse and keyboard) and other partitions aren't mounted.

---

### Post by papalevies on 2010-06-05
Just my 2cents for anyone who wants to avoid my frustration:
If you have mic issues in Lucid with an Xfi card (mine is Xtreme Gamer), try this:
Open a terminal and type "alsamixer". Press F6 to select the Xfi soundcard (Creative Xfi). Make sure you are on playback (press F3 if not sure) and go under Line-in. Press M once to make the box under the bar display "00" instead of "MM". Press the up arrow to ramp up the volume as high as it will go. Press F4 which will turn to capture mode. Ramp up the Master, Line-in and Mic like previously. Disable all other bars except the Mic by going under them and pressing the spacebar. In the end the Mic bar should be the only one with a red "L R Capture" label under it. Press escape.

You should now be able to record sound from the mic. I hope this works for you too.

---

### Post by brimlar on 2010-06-05
> **papalevies said:**
> Just my 2cents for anyone who wants to avoid my frustration:
If you have mic issues in Lucid with an Xfi card (mine is Xtreme Gamer), try this:
Open a terminal and type "alsamixer". Press F6 to select the Xfi soundcard (Creative Xfi). Make sure you are on playback (press F3 if not sure) and go under Line-in. Press M once to make the box under the bar display "00" instead of "MM". Press the up arrow to ramp up the volume as high as it will go. Press F4 which will turn to capture mode. Ramp up the Master, Line-in and Mic like previously. Disable all other bars except the Mic by going under them and pressing the spacebar. In the end the Mic bar should be the only one with a red "L R Capture" label under it. Press escape.

You should now be able to record sound from the mic. I hope this works for you too.

Thank you.  This worked great.  On a side note, I pressed "M" on the Output for Line-In to set it to 00, but didn't ramp the volume up, because that gives you mic feedback into your speakers or headphones.  It acts fine just sitting at 00.

Anyhow -- good work.  Much thanks again.

---

### Post by PowerSource on 2010-06-06
> **papalevies said:**
> Just my 2cents for anyone who wants to avoid my frustration:
If you have mic issues in Lucid with an Xfi card (mine is Xtreme Gamer), try this:
Open a terminal and type "alsamixer". Press F6 to select the Xfi soundcard (Creative Xfi). Make sure you are on playback (press F3 if not sure) and go under Line-in. Press M once to make the box under the bar display "00" instead of "MM". Press the up arrow to ramp up the volume as high as it will go. Press F4 which will turn to capture mode. Ramp up the Master, Line-in and Mic like previously. Disable all other bars except the Mic by going under them and pressing the spacebar. In the end the Mic bar should be the only one with a red "L R Capture" label under it. Press escape.

You should now be able to record sound from the mic. I hope this works for you too.


this works for me, though i've had a similar setting for a while.
it works great in audacity, though in skype when i call echo the only sound i get back is some noise, like when you are listening to a radio station that doesn't exist. like if it was raining pebbles.
have anyone else got this problem?

---

### Post by kreppnar on 2010-06-11
Has anyone figured out a way to get the External I/O drive to work for the Sound Blaster XFI Platinum??


thanks!

-Kreppnar-

---

### Post by alialo on 2010-06-13
> **kreppnar said:**
> Has anyone figured out a way to get the External I/O drive to work for the Sound Blaster XFI Platinum??


thanks!

-Kreppnar-

I'd really like a solution to this too, if there is one. I use an XFi Elite Pro with the external I/O module if that makes a difference.

---

### Post by NullHead on 2010-06-13
> **kreppnar said:**
> Has anyone figured out a way to get the External I/O drive to work for the Sound Blaster XFI Platinum??


thanks!

-Kreppnar-

> **alialo said:**
> I'd really like a solution to this too, if there is one. I use an XFi Elite Pro with the external I/O module if that makes a difference.

Sorry guys. As far as I know, there is simply no support for the external I/O module for any flavor of X-Fi with any driver I know of.

---

### Post by Rainman5419 on 2010-06-13
Ok, Linux noob here. Borrowed a 9.4 disc from a pal to install an  updated it to 10.4. but I'm running into problems with the sound card.
 
 I'm using Creative Xfi Xtremegamer and have tried a few things to get it  to work.
 Checked the Creative support site and downloaded the drivers listed  there XFiDrv_Linux_Public_US_1.00
 Followed the readme and ran
 
```
cd /home/user/Desktop/XFiDrv_Linux_Public_US_1.00
make
```with
> make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/user/Desktop/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/user/Desktop/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2as the output.

Followed the advice [here]("http://ubuntuforums.org/showpost.php?p=6369503&postcount=148") and edited the mentioned lines before executing the make command. So what am I missing or doing wrong?
Been playing with Ubuntu for a bit, but I'm just learning the make command. I also have to figure out how to make a network card drivers the same way later >.<

---

### Post by kajsa on 2010-06-13
> **papalevies said:**
> Just my 2cents for anyone who wants to avoid my frustration:
If you have mic issues in Lucid with an Xfi card (mine is Xtreme Gamer), try this:
Open a terminal and type "alsamixer". Press F6 to select the Xfi soundcard (Creative Xfi). Make sure you are on playback (press F3 if not sure) and go under Line-in. Press M once to make the box under the bar display "00" instead of "MM". Press the up arrow to ramp up the volume as high as it will go. Press F4 which will turn to capture mode. Ramp up the Master, Line-in and Mic like previously. Disable all other bars except the Mic by going under them and pressing the spacebar. In the end the Mic bar should be the only one with a red "L R Capture" label under it. Press escape.

You should now be able to record sound from the mic. I hope this works for you too.

Thank you, that solved my mic problems.

---

### Post by PowerSource on 2010-06-13
> **Rainman5419 said:**
> 
Been playing with Ubuntu for a bit, but I'm just learning the make command. I also have to figure out how to make a network card drivers the same way later >.<

try system->administration->hardwaredrivers and see if you can find the drivers for your card there.

---

### Post by capo1949 on 2010-06-16
Hi all

First off a big thank you NullHead and co. for all your work.

I have a dell studio 15 with x-fi, and dual boot with ubuntu 9.10.

I didnt find this post when experiencing original problems of no sound and so followed [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound), which has successfully produced sound, but I have no volume control etc.

I am confused as to how to access the GUI. I generated a launch applet as detailed.

> Ubuntu 9.10
The GNOME volume control in Karmic is PulseAudio-based, so you'll want to use packages from: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa)

How do I use these packages, I have checked they are installed.

I am obviously missing something as the GUI has to be  tied to the applet in some way.

Many thanks in anticipation.

Graham

---

### Post by NullHead on 2010-06-17
From the description on the PPA,
[quote=PPA]The gnome-media/applets/settings-daemon packages are for users running without PulseAudio. They will disable the Pulse-based volume control and use the "classic" gstreamer-based volume control, which includes an option to configure event sounds. Also, GNOME media-keys will once again work without PulseAudio.

The libcanberra packages are built with only the gstreamer backend. This is ideal for OSS4 users who want event sounds in GNOME.[/quote]
, it sounds like you simply install OSS, remove pulse audio, and continue to use these packages in the repository to remove the built in "hard wired" support for pulse audio in the standard gnome-volume control. 

So these packages would only restore your ability to control the sound as you normally would. I think.

---

### Post by capo1949 on 2010-06-17
Hi
Thanks for your reply.

I have removed pulse audio and installed oss and installed the ppa, and I have checked they are installed on my system

gnome-applets  	        2.28.0-0ubuntu3~ppa3  	 
gnome-media 	        2.28.1-0ubuntu2~ppa3 	
gnome-settings-daemon 	2.28.1-0ubuntu3~ppa12 	
libcanberra[COLOR="Red"]0[/COLOR]	        0.15-0ubuntu8~ppa2

libcanberra is suffixed with 0, does this make any difference?

The launcher runs command ossxmix and does nothing when pressed, if I change ossxmix to ossmi, it returns 'Failed to execute child process "ossxmi" (No such file or directory)'.

I am pretty new to linux and at a dead end with this, some basic help would be much appreciated

Graham

---

### Post by NullHead on 2010-06-17
Try installing OSS again and lets see where we are once that's finished. Don't uninstall/install anything else other than what's needed to install OSS. 

You should be all set after you install OSS.

---

### Post by capo1949 on 2010-06-18
Hi NullHead

Thanks for your response, I reinstalled oss from the terminal with:-
sudo dpkg -i oss-linux-4.2-2003_amd64.deb
as per the Open Sound Doc.

I still have no response when operating the volume button.

I thought the oss info may be useful, displayed below.


graham@graham-laptop:~$ ossinfo
Version info: OSS 4.2 (b 2003/201005272149) (0x00040100) TRIAL
Platform: Linux/x86_64 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 02:41:03 UTC 2010 (graham-laptop)

Number of audio devices:	5
Number of audio engines:	9
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_hdaudio0 Intel HD Audio interrupts=374 (374)
    HD Audio controller Intel HD Audio
    Vendor ID    0x80863b56
    Subvendor ID 0x10280413
     Codec  0: Unknown (0x111d7675/0x10280413)
 2: oss_usb0 USB audio core services

MIDI devices (/dev/midi*)

Mixer devices
 0: High Definition Audio 0x111d767 (Mixer 0 of device object 1)

Audio devices
HD Audio play pcm1                /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play pcm2                /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio play pcm3                /dev/oss/oss_hdaudio0/pcm2  (device index 2)
HD Audio rec select2              /dev/oss/oss_hdaudio0/pcmin0  (device index 3)
HD Audio rec select3              /dev/oss/oss_hdaudio0/pcmin1  (device index 4)

Nodes
  /dev/dsp -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_in -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_out -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_mmap -> /dev/oss/oss_hdaudio0/pcm0
  /dev/dsp_multich -> /dev/oss/oss_hdaudio0/pcm0

---

### Post by notacluenoob on 2010-06-18
Hi NullHead,

This is notacluenoob (back from post #579),

I just wanted to let you know that I finally have sound, and it did work out of the box. The only thing I did different this time was to use the 32-bit distro of Ubuntu 10.04 instead of the 64-bit. I don't know how that really makes a difference or not (I do have an AMD 64-bit proc), but outside of a slight crackle out of the right speaker when the sound kicks in on boot, everything is fine. I don't know if this will help anyone else or not, but I still wanted to thank you again for all of your help, NullHead.

notacluenoob

---

### Post by NullHead on 2010-06-18
> **notacluenoob said:**
> Hi NullHead,

This is notacluenoob (back from post #579),

I just wanted to let you know that I finally have sound, and it did work out of the box. The only thing I did different this time was to use the 32-bit distro of Ubuntu 10.04 instead of the 64-bit. I don't know how that really makes a difference or not (I do have an AMD 64-bit proc), but outside of a slight crackle out of the right speaker when the sound kicks in on boot, everything is fine. I don't know if this will help anyone else or not, but I still wanted to thank you again for all of your help, NullHead.

notacluenoob

Glad to hear it! If you have more 4gb of ram or more, you could always install the PAE (physical address extension) kernel to support that extra ram. I say, as long as you have working sound and are happy with your current system, install this kernel to take advantage of the extra ram you have. 

I believe '*sudo apt-get install kernel-image-2.6.32-21-generic-pae-di*' should do the job. I really can't say for sure, as I haven't had to install this kernel before, but it's worth a shot imo. 

enjoy

---

### Post by hansum_rahul on 2010-06-20
Not working here with this configuration on ALSA. 

[B]01:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at dc00 [size=32]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106
[/B]

OSS does a great job on my 8.04. But even a new 10.04 produces noise.

Any ideas?

---

### Post by NullHead on 2010-06-20
> **hansum_rahul said:**
> Not working here with this configuration on ALSA. 

[B]01:02.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 1004
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 5000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at dc00 [size=32]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106
[/B]

OSS does a great job on my 8.04. But even a new 10.04 produces noise.

Any ideas?

Your X-Fi card is an X-Fi Extreme Audio/Audigy LS CA0106 sound card. I don't have any experience with this card or the drivers related to it. I suggest you post a new thread to get help specific to snd-ca0106 (alsa driver), and if you're keen on using OSS, I suggest getting help on the [OSS forums](http://www.4front-tech.com/forum/).

---

### Post by gnomey on 2010-09-05
Hey everyone,

I've got a Creative Fatal1ty X-FI Titanium Champion Edition, and I have sound working, but I really want the front panel working.

Has anyone got any progress in getting the front panel working in Ubuntu? I'd love to have it working in Ubuntu.

I've been reading up and trying to get it to work almost everyday for the past month, and I've made no progress at all. I'm hoping someone out there can help me out.

**UPDATE:** I'm such a fool. I just opened alsamixer again, like I do almost everyday and noticed I was configuring my onboard sound card. Just selected my X-FI and got my headphones working on the front panel! 
Now I just need the aux-in on the front panel to work, and the volume control, then I'll be happy that I didn't waste my &#8364;200 on this sound card. 
I couldn't really care about the "Game Mode" function buttons, unless somebody knows how to get them to work.

I was also wondering, is it possible to have two different sounds on the speakers and the headphones, like for example, if I was playing a game, I'd like to have the game sounds on my speakers, and TeamSpeak on my headphones. I'm not sure if this is possible in Windows with this sound card, but if it is, let me know as i'll have to add that to my "fix" list

---

### Post by Linux_noob616 on 2010-09-16
Hi all, i'm having an issue creating the make file i get the following
```
sudo make
make -C /lib/modules/2.6.32-24-generic/build M=/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c: In function &#8216;ct_card_probe&#8217;:
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function &#8216;snd_card_new&#8217;
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2

```
I am using the x-fi titanium fatal1ty champ series.
I changed the file as stated above as i have a pci-e card

Fresh install of Kubuntu 10.04.1 x64

---

### Post by NullHead on 2010-09-17
> **Linux_noob616 said:**
> Hi all, i'm having an issue creating the make file i get the following
```
sudo make
make -C /lib/modules/2.6.32-24-generic/build M=/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/mitch/Documents/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2

```
I am using the x-fi titanium fatal1ty champ series.
I changed the file as stated above as i have a pci-e card

Fresh install of Kubuntu 10.04.1 x64

You don't even need to use creative's half baked driver anymore. There's a perfectly good working on already build into the kernel. It should even work out of the box on any version 9.04+

I suggest you just remove the build directory and use the one that comes in the kernel.

---

### Post by gnomey on 2010-10-01
Anyone get the front panel controls working on these in Ubuntu? its something I really want working.

---

### Post by NullHead on 2010-10-03
> **gnomey said:**
> Anyone get the front panel controls working on these in Ubuntu? its something I really want working.

Not that I know of. I'm still using my Extreme gamer card, so I really can't go check it out, but from what I understand, nobody's reported success with that yet. Development of the driver is mostly frozen to a maintenance state.

---

### Post by philou365 on 2010-10-04
Hi all,
 
I'm a linux nood, even if I used it with a lot of pleasure for 3 years now. Recently I changed my Xmod to an X-fi Xtreme Music which works well on Seven.
I have changed because, I thought it will be more convenient for my wife to use a PCI card than a USB which sometimes don't start.
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
First of all, in the Bios, I disabled my chipset, then started and I had no sound at all. When I check Sound preference, I see as a first choice HD 48x0 (my graphic card :confused:) and my x-fi as a second choice, but I can't activate the x-fi, even if I turn the 48x0 as "switch off" with a right click.
When I ask for my pci audio, here's the response :
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
05:00.0 Multimedia audio controller: Creative Labs SB X-Fi

What can I do ?

---

### Post by notacluenoob on 2010-11-30
Hello everybody,
 
notacluenoob here again. I just wanted to know if anyone else was having problems with getting their PCI-e SB X-Fi Titanium Fatal1ty to work with Ubuntu 10.10. I have since reverted to a backup of 10.04 where I have no problems with the 32-bit version (haven't bothered trying the AMD64-bit version, though). If I do an upgrade from the Internet to 10.10 versus doing a fresh install of 10.10, I can use the old kernel version it leaves behind in 10.10 with sound without problems. But, if I use the new kernel version or any of the later ones that have come out since then, the card isn't detected in Sound Preferences and I get no sound. So, outside of using the old kernel (don't remember which one it is off-hand), is there anything I can do?
 
Thank you everybody,
 
notacluenoob

---

### Post by NullHead on 2010-11-30
uhh ... That's odd. 

I'll have to try to take a look on my own system to see what's up. I haven't been running ubuntu on here, but I'll install it and see what's going on. 

My best guess is that the module isn't loading on the new kernel, as I haven't noticed any exclusion of the driver from the looks of the most recent kernels.

---

### Post by NullHead on 2010-12-03
> **notacluenoob said:**
> Hello everybody,
 
notacluenoob here again. I just wanted to know if anyone else was having problems with getting their PCI-e SB X-Fi Titanium Fatal1ty to work with Ubuntu 10.10. I have since reverted to a backup of 10.04 where I have no problems with the 32-bit version (haven't bothered trying the AMD64-bit version, though). If I do an upgrade from the Internet to 10.10 versus doing a fresh install of 10.10, I can use the old kernel version it leaves behind in 10.10 with sound without problems. But, if I use the new kernel version or any of the later ones that have come out since then, the card isn't detected in Sound Preferences and I get no sound. So, outside of using the old kernel (don't remember which one it is off-hand), is there anything I can do?
 
Thank you everybody,
 
notacluenoob

Well my discoveries with 10.10 have gone as expected. 

My Extreme Gamer is detected flawlessly and works perfectly. The only snag was that the system had automatically selected my HDTVs HDMI audio device over my X-Fi, so I just had to change it to the x-fi, unmute and it worked. 

I don't know why yours isn't working. I ran the AMD64 version though, so who really knows.

---

### Post by illbashu on 2010-12-03
I'm trying to help a friend who is new to Linux. He has a SB X-Fi sound card but he can't get his front panel, mic or headphone working.

> 
04:04.0 Audio device: Creative Labs SB X-Fi

He installed ubuntu 10.10 (32bit) and he says nothing is showing up under "sound preferences" -> input -> connections. He also said that when he plugged in his headphones the sound would still come out of his speakers.

Is there something he has to do to get this working?

---

### Post by notacluenoob on 2010-12-03
> **illbashu said:**
> I'm trying to help a friend who is new to Linux. He has a SB X-Fi sound card but he can't get his front panel, mic or headphone working.



He installed ubuntu 10.10 (32bit) and he says nothing is showing up under "sound preferences" -> input -> connections. He also said that when he plugged in his headphones the sound would still come out of his speakers.

Is there something he has to do to get this working?


illbashu,

I can't respond to everything you've asked about as I don't know, but for the front panel, as far as I know, it doesn't work under Ubuntu, and unfortunately, there is no workaround.

Sorry I can't help you more,

notacluenoob

---

### Post by notacluenoob on 2010-12-04
NullHead,

Thank you again for replying to me and to see if you could figure out if there was anything you could see from your end. Unfortunately, I came up empty trying the AMD64 live CD and trying a fresh install as the card wasn't detected under Sound Preferences. Using lspci -v, I can see the card, but that's it. Here's part of the output...

lspci -v

03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Subsystem: Creative Labs Device 0043
    Physical Slot: 0-1
    Flags: fast devsel, IRQ 28
    Memory at d7ff0000 (64-bit, non-prefetchable) [size=64K]
    Memory at d7c00000 (64-bit, non-prefetchable) [size=2M]
    Memory at d0000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: <access denied>
    Kernel modules: snd-ctxfi



I have to agree with you about the module not being loaded on the new kernel (for me at least) or something at least not being right at boot. I happened to notice when Ubuntu was booting up, just for a couple of seconds or so, I got 2 lines of error messages, before it disappeared again...

[11.384859] ctxfi: architecture does not support PCI busmaster DMA with mask 0xffffffffffffffff

[11.384934] ctxfi: something wrong!!!

The numbers seem to change in the beginning, but those are an example of them when they came out once. I managed to find the error messages under System | Administration | Log File Viewer , then picking syslog or kern.log, from the left, for a couple of examples of where I looked.

Do you have any other ideas on what to try NullHead, or where to go from here? Maybe someone in particular to contact?

Thank you for all of your help as always, NullHead.

notacluenoob

---

### Post by oliverj4455 on 2010-12-11
Yep, same issue for me with an Xtreme Gamer.

dmesg gives:

[   15.836797] SB-XFi 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.836801] SB-XFi 0000:05:03.0: PCI: Disallowing DAC for device
[   15.836803] architecture does not support PCI busmaster DMA with mask 0xffffffffffffffff
[   15.836875] SB-XFi 0000:05:03.0: PCI INT A disabled
[   15.836879] ctxfi: Something wrong!!!

Any ideas?

---

### Post by NullHead on 2010-12-11
> **oliverj4455 said:**
> Yep, same issue for me with an Xtreme Gamer.

dmesg gives:

[   15.836797] SB-XFi 0000:05:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.836801] SB-XFi 0000:05:03.0: PCI: Disallowing DAC for device
[   15.836803] architecture does not support PCI busmaster DMA with mask 0xffffffffffffffff
[   15.836875] SB-XFi 0000:05:03.0: PCI INT A disabled
[   15.836879] ctxfi: Something wrong!!!

Any ideas?

Are you using 32bit too? I guess I can give that a try as well. 

I might be time to file a bug report.

---

### Post by oliverj4455 on 2010-12-12
Sorry I didn't say. I am using 64-bit.

The alsa-info.sh script output is at [http://www.alsa-project.org/db/?f=09e55ef47f933b6c4f3f936565c1d12d82c566fb]("http://www.alsa-project.org/db/?f=09e55ef47f933b6c4f3f936565c1d12d82c566fb").

So far I have tried:
[LIST]
[*]Disabling on-board sound
[*]Fresh install of Ubuntu
[*]Moving PCI slots
[*]Unplugging all external peripherals
[/LIST]

Next I will try unplugging all of my hard drives, and anything that I don't need inside the PC, see if anything is interfering with DMA (although unplugging hard drives is a long shot since they don't even use DMA!).

Thanks for your help!

Update:
I have tried booting with the live CDs from Linux Mint and OpenSUSE and all have the same error in dmesg.

---

### Post by Lucas32 on 2010-12-24
does this driver/module support the creative xfi titanium HD soundcard?
i received no errors when i tried to load the snd-ctxfi module and i can see that the snd-ctxfi is running when i do 'lsmod'.
from my dmesg log, i noticed the following messages:

SB-XFi 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
SB-XFi 0000:03:00.0: setting latency timer to 64
SB-XFi 0000:03:00.0: PCI INT A disabled
ctxfi: Something wrong!!!
SB-XFi: probe of 0000:03:00.0 failed with error -1

the output of lspci -v:
03:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
	Subsystem: Creative Labs Device 0062
	Flags: fast devsel, IRQ 16
	Memory at d8200000 (64-bit, non-prefetchable) [size=64K]
	Memory at d8000000 (64-bit, non-prefetchable) [size=2M]
	Memory at d4000000 (64-bit, non-prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel modules: snd-ctxfi

So is there any chance to get this guy playing in Ubuntu 10.10?

---

### Post by Phantom03 on 2010-12-27
I recently installed Creative Labs new SB1270 X-Fi Titanium HD sound card and it appears the current Linux driver does not support this sound card.  Running 64bit.  Anyone have a work around idea or know how I can get a request in to the developers to modify the driver?

Below is the info I get with an lspci call:

$ lspci | grep Audio
03:00.1 Audio device: nVidia Corporation GF100 High Definition Audio Controller (rev a1)
04:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)

Thanks!

---

### Post by NullHead on 2010-12-27
Looks like the Titanium HD runs the emu20k2 chip just like the other Titanium cards,which work fine, but for some reason this one isn't working. Personally, I would post on the alsa-dev mailing list. Seems like with some tweaking, the current driver might work.

---

### Post by onemanclapping on 2011-01-22
Hello! I'm seeing you all comment that everything should work out of the box now, but not for me...

I just installed Ubuntu 10.10 at my desktop, which has a X-FI Extreme Music PCI-E. Everything seemed to work - drivers load, sound manager was working - until I turned on my speakers and... no sound!

Then I realised that if I go to Rhythmbox and try to play something, it doesn-t play - I mean, the progress bar doesn't even move.

Does anyone know about such a problem?

Thanks in advance!

---

### Post by NullHead on 2011-01-22
> **onemanclapping said:**
> Hello! I'm seeing you all comment that everything should work out of the box now, but not for me...

I just installed Ubuntu 10.10 at my desktop, which has a X-FI Extreme Music PCI-E. Everything seemed to work - drivers load, sound manager was working - until I turned on my speakers and... no sound!

Then I realised that if I go to Rhythmbox and try to play something, it doesn-t play - I mean, the progress bar doesn't even move.

Does anyone know about such a problem?

Thanks in advance!

I've known Rhythmbox to act this way for me many times before. Try out VLC, Banshee, Audacious, Totem, to name a few. 

Open up the sound control panel and make sure that your speakers aren't muted, like mine usually are. Mine tend to be muted in favor of my TV for some reason, so just make sure that it's all good there. 

You may also need codecs to play some types of music. FLAC should work out of the box, but I am unsure of AAC or MP3.

---

### Post by onemanclapping on 2011-01-22
> **NullHead said:**
> I've known Rhythmbox to act this way for me many times before. Try out VLC, Banshee, Audacious, Totem, to name a few.

No, it's not that. It doesn't work with anything... :/

> **NullHead said:**
> Open up the sound control panel and make sure that your speakers aren't muted, like mine usually are. Mine tend to be muted in favor of my TV for some reason, so just make sure that it's all good there.

No that too: I even tried testing the speakers with the panel's test.

I also did some tests that maybe are worth mentioning:

- Tried changing the card to another PCI-E slot;
- Tried different RAM configurations just to be sure;
- Turned on the onboard sound card: works fine;
- Tried all the above with the 32bit Maverick (I'm using the 64bit version)...

...but nothing worked. Any ideas or some info on how to do some debugging diagnostics?

Thanks for your help!

---

### Post by notacluenoob on 2011-02-08
Just an FYI for anyone whom this might help. ALSA version 1.0.24 is now out (has been since 1-31-11...) and maybe that new version will help somebody out. Unfortunately, for me, it didn't, but it doesn't mean that you might get lucky!

notacluenoob

---

### Post by warmrobot on 2011-03-09
Hi! Did anybody affected of [this]("http://www.youtube.com/watch?v=J6K8IqGE3s0") bug?

I mean when you change master volume it doesn't change volume at all. But if you change applications level - yes, it works. My card is **E-MU 0202 USB**

---

### Post by warmrobot on 2011-03-09
> **warmrobot said:**
> Hi! Did anybody affected of [this]("http://www.youtube.com/watch?v=J6K8IqGE3s0") bug?

I mean when you change master volume it doesn't change volume at all. But if you change applications level - yes, it works. My card is **E-MU 0202 USB**
Oops! My fault. After installing pavucontrol and choosing Digital (instead Analog) Stereo Duplex output - master volume start to work.

---

### Post by DarkTide on 2011-04-07
I wonder if it is something really bizarre then, like the x.x.x.6 kernel  that comes with the install/live cd as opposed to the x.x.x.7 kernel  that the initial update upgrades 8.10 to (which I went for before trying  to install the x-fi drivers).

---

### Post by terran4000 on 2011-05-08
I  have the same issue as @Lucas32  ...

Did anyone get the Creative Labs X-Fi Titanium HD working yet? Shows up in lspci, lsmod (module loaded) though it will simply not show up under Sound -> Preferences at all. 

Any ideas?

---

### Post by enteon on 2011-06-06
In the making, but still probably harmful to the hardware! ](*,)
[http://search.gmane.org/?query=ctxfi&author=Harry+Butterworth&group=&sort=date&DEFAULTOP=and&xP=Ztitanium&xFILTERS=Abutterworth-Aharry---A](http://search.gmane.org/?query=ctxfi&author=Harry+Butterworth&group=&sort=date&DEFAULTOP=and&xP=Ztitanium&xFILTERS=Abutterworth-Aharry---A)

I sure can't wait and will exchange for an ASUS Essence STX...

---

### Post by terran4000 on 2011-06-06
Awesome! Finally some progress. Can barely wait to read more up on it! 

So far I've just managed to get my old card to work (somehow) while waiting for the X-FI titanium to work ><

---

### Post by enteon on 2011-06-06
I recommend going for the essence stx, since that one has worked out of the box for about two years so probably a mature driver.
while the driver for the titanium HD could still take years to mature.

And they don't sound very different, they have in fact almost the same components.

---

### Post by notacluenoob on 2011-07-05
Has anyone had any success from the patch mentioned by enteon at [[COLOR=#000000]http://search.gmane.org/?query=ctxfi...rth-Aharry---A[/COLOR]]("http://search.gmane.org/?query=ctxfi&author=Harry+Butterworth&group=&sort=date&DEFAULTOP=and&xP=Ztitanium&xFILTERS=Abutterworth-Aharry---A") for their XFi Titanium? I keep getting an error message about hunk 1316...
 
notacluenoob

---

### Post by Stratoliner on 2011-07-21
> **notacluenoob said:**
> Has anyone had any success from the patch mentioned by enteon at [[COLOR=#000000]http://search.gmane.org/?query=ctxfi...rth-Aharry---A[/COLOR]]("http://search.gmane.org/?query=ctxfi&author=Harry+Butterworth&group=&sort=date&DEFAULTOP=and&xP=Ztitanium&xFILTERS=Abutterworth-Aharry---A") for their XFi Titanium? I keep getting an error message about hunk 1316...
 
notacluenoob


I had no trouble patching the kernel (3.0.0-rc7) on Oneiric.  However, the patch did not fix the problem with my X-Fi Titanium HD.  I still get a long pause and the "ctxfi: Something wrong!!!" message when loading the module.

Try a more recent kernel to see if you can get it to work.

---

### Post by Stratoliner on 2011-08-14
> **Stratoliner said:**
> I had no trouble patching the kernel (3.0.0-rc7) on Oneiric.  However, the patch did not fix the problem with my X-Fi Titanium HD.  I still get a long pause and the "ctxfi: Something wrong!!!" message when loading the module.


I should have mentioned that I originally only applied one of the patches.  I applied the other and it works now.  However, there is no sequencer/midi/synth support for this card.

---

### Post by notacluenoob on 2011-08-23
> **Stratoliner said:**
> I should have mentioned that I originally only applied one of the patches.  I applied the other and it works now.  However, there is no sequencer/midi/synth support for this card.


Stratoliner,

Forgive me for sounding like an idiot, but I thought that there was only one final patch from Mr. Butterworth. I'm running Oneiric Alpha 3 with kernel 3.0.0.8, and still having problems with the patch. Any words of wisdom on how to maybe get my sound working on the 20k2 chip? Any instructions since as much as I love Ubuntu, I'm still a noob?

Thanks in advance,

notacluenoob

---

### Post by Stratoliner on 2011-08-23
> **notacluenoob said:**
> Stratoliner,

Forgive me for sounding like an idiot, but I thought that there was only one final patch from Mr. Butterworth. I'm running Oneiric Alpha 3 with kernel 3.0.0.8, and still having problems with the patch. Any words of wisdom on how to maybe get my sound working on the 20k2 chip? Any instructions since as much as I love Ubuntu, I'm still a noob?

Thanks in advance,

notacluenoob

It would have been nice if there was just one patch, but there are actually a few.  Here are the patches you need (I think):

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040754.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040754.html)

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040755.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040755.html)

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040927.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040927.html)

It might be easier for you to get the alsa drivers from git and compile them yourself.  But have no idea how to do that, which is why I patched my kernel.

---

### Post by notacluenoob on 2011-08-26
> **Stratoliner said:**
> It would have been nice if there was just one patch, but there are actually a few.  Here are the patches you need (I think):

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040754.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040754.html)

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040755.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040755.html)

[http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040927.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2011-June/040927.html)

It might be easier for you to get the alsa drivers from git and compile them yourself.  But have no idea how to do that, which is why I patched my kernel.

Thanks for getting back to me Stratoliner, I'll have to give them a shot when I get the chance...have to prepare for Irene now (CT). Hopefully I'll still have power by then.

notacluenoob

---

### Post by weyland42 on 2011-08-31
I just got a brand-new custom system with a Creative X-Fi Xtreme Audio card. Output is excellent, but several microphones I've tried don't work at all. I gather that there's a problem with FlexiJack, and that the driver's probably the source of the trouble. I know nothing.

Anyone know how to get a working driver for this thing? Does one even exist?

I'm running Ubuntu 11.04 with all updates.

---

### Post by notacluenoob on 2011-09-04
Stratoliner,

I just wanted to thank you for your help in trying to get my sound card working. All I end up doing is getting hunk errors everywhere. Maybe because I have one of the original X-Fi Titanium PCI-e (not the HD, even though it still is the 20k2 chip) is part of the reason it's not working, but I doubt it. For now, I'm going back to 10.04.

I also wanted to thank everybody else here that has tried to and sometimes successfully get me up and running. This thread has been the most open to helping people with problems, and it seems if you go elsewhere, the first thing they do is redirect you here. I've tried both Launchpad and the ALSA sites, and that's what they did, unfortunately offering very little more assistance.

I'll have to give 11.10 a shot when it officially comes out to see if anything works and if it does for me, I'll post back.

Thank you all again,

notacluenoob

---

### Post by terran4000 on 2011-10-15
Well, 11.10 officially kills any working Creative X-Fi Titanium card. 

Had it nice and working in 11.04, guess 11.10 breaks it ALL over again with no chance to fit it this time though.

If anyone know how to get it working on 11.10 please let us know.

---

### Post by kooldino on 2011-10-16
> **terran4000 said:**
> Well, 11.10 officially kills any working Creative X-Fi Titanium card. 

Had it nice and working in 11.04, guess 11.10 breaks it ALL over again with no chance to fit it this time though.

If anyone know how to get it working on 11.10 please let us know.


Mine worked out of the box in 11.10.  Then I ran some update, rebooted, and voila!  No sound.  

The system recognizes the card and it THINKS it's working, but I have no sound output.

---

### Post by kooldino on 2011-10-23
Just for grins, tried this with 11.10 and it won't compile.  Make spits out errors.

---

### Post by terran4000 on 2011-10-28
So I finally wrote up the tutorial about how I got the X-Fi tamed and working under 11.04. Good luck yee to venture into 11.10, no easy alsa upgrades for you.

Hope this will help some people get their X-Fi (titanium) working AND with 5.1 digital surround sound!

[http://www.piotrkrzyzek.com/creative-x-fi-titanium-5-1-digital-surround-on-ubuntu/]("http://www.piotrkrzyzek.com/creative-x-fi-titanium-5-1-digital-surround-on-ubuntu/")

---

### Post by funky_uncle on 2012-01-18
> **kooldino said:**
> Mine worked out of the box in 11.10.  Then I ran some update, rebooted, and voila!  No sound.  

The system recognizes the card and it THINKS it's working, but I have no sound output.

Me too, I was just trying to install some PulseAudio equalizer, so I added some PPAs to get it, apt-get-updated it, and now my X-fi sound card is greyed out in the sound preferences. This is on Kubuntu, but I guess the kernel is the same.

---

### Post by larrypg on 2012-01-18
Something has to work because as deaf as I am, I am pretty sure that I am hearing something that sounds pretty good out of my speakers.  (not titanium though) and not 11.10.  I just think that there has to be some way for things that worked fine in 11.04 to also work in 11.10.  I do not care if I have to do a bit of work to get things working but would like to do something to make it work.

---

### Post by terran4000 on 2012-02-17
After playing around with some code, and lots of research I did manage to get the Titanium X-Fi working on Ubuntu 11.10 and it even works on the latest kernel 3.0.0-16 in x64.

[http://www.piotrkrzyzek.com/solved-creative-x-fi-titanium-ctxfi-on-ubuntu-11-10/]("http://www.piotrkrzyzek.com/solved-creative-x-fi-titanium-ctxfi-on-ubuntu-11-10/")

---

### Post by jaktar on 2012-05-07
Is terran4000's fix still valid for 12.04?

---

