---
title: "working microphone on hda-intel. does it exist?"
date: 2006-10-05
forum: Multimedia &amp; Video
---

### Post by ryu kun on 2006-10-05
I really wonder, is there any hda-intel sound card owner who can use their microphone for capturing or audio conversations without any problem?

If yes, can you state its chipset and your alsa driver version?

Mine is Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller. No mic capture on dapper. I'm trying to fix it for weeks. No avail. ](*,)

To get info about your card and chipset use this code:
```

lspci -v
```

---

### Post by onemanwaking on 2006-10-11
I'm in the exact same boat as you are.

I've had this laptop (Gateway MX6920) for about a week and this is the only thing that doesn't work. Same setup - HDA Intel/ICH7.

One weird thing that I found was that if you plugged the EARphones into the mic input, you could speak into them and it would register! Weird that it would recognize a stereo input source through the earpieces, but not the proper mic.

Still looking for answers. Anyone???](*,)

---

### Post by JayTee on 2006-10-11
I have the same Intel HDA chipset on my Intel motherboard. I can get the mic to capture sound but even with the capture volume set to max the sound level on playback is very low. One of the posts I read here earlier talked about setting the 20db gain on the switches tab of the Volume control settings but I don't have that tick box available. Looks like we are all in the same boat.](*,)

---

### Post by spaceturnip on 2006-10-14
After playing around with it a little bit it seems to be working for me. The volume control prefs are a little confusing, the capture icon underneath the Microphone sliders shows that capture is enabled, but the speaker next to had a red x through it so it was muted, if you click the speaker and unmute the mic it should be working.  If you need more volume, there isn't a switch, but there is a mic boost slider you can activate in the preferences, it will show up in the playback tab.  The only test I've done so far is calling the echo service in gizmo, but I can hear myself there so it should be working.

---

### Post by GliderMike on 2006-10-14
I have several laptops at work where we use a line in to the mic jack to take audio input and then stream audio out, using dapper.  I had to play with alsamixer on the command line to enable capture, then save my settings with "alsactl store"

---

### Post by 4thHeaven^!^ on 2006-10-19
Hi,

I'm using a Dell Latitude D520 with Dapper 6.06. I've been fiddling with front panel headphone and mic for sometime. My sound card is Intel HDA 82801G and alsa version is 1.0.10.

I noticed my /etc/asound.names is missing. After executing
```

sudo alsactl names
sudo alsactl store

```
to generate /etc/asound.names and /var/lib/alsa/asound.state seems to fix front panel sound problems.

After a restart I noticed volume controller has set input source (Under Options tab) to *line*, which I set to *mic* to use it.

^!^

---

### Post by LogicalDash on 2006-10-26
4thHeaven, could you be a little more specific about which Options tab you're talking about, so I can find the equivalent in Kubuntu?

---

### Post by pefdus on 2006-10-27
Okay, 4thHeaven this has worked. 

I will detail what I have done. 
These were my synptoms
- IBM ThinkPad Z61m
- lspci : Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
- Microphone was not working, but you could "hear" yourself in the headphones. So the mic actually worked okay

I ran the 
sudo alsactl names
sudo alsactl store
and then when into the Sound preferences. 
(Dbl Click on the speaker Icon to get Volume Control)
In here I see two tabs.

Playback and Capture
--------------------
The playback tab is as it's name suggests. If you modify the volume
of the mic here, it will just control the level to which you "hear" yourself in the speakers.

Go to the Capture tab.
I see 
CD / Microphone / Capture All three levels are set at around 75%

The trick was to toggle the buttom on the bottom.
Firstly, the Microphone is is not Muted (the speaker icon)
          the Microphone audio capture (the mictophone) is enabled
Second, and I think this is what made it work,
the "capture" is the same, not muted and enabled.

After running the alsactl commands above and changing the capture
This seemed to fix "whatever" was the problem.

I then used Audacity (which shows a nice sound wave displaying that it is in
fact recording something).

Hope that helps.
ramon

---

### Post by JayTee on 2006-11-03
I have the same hardware. My mic works but even though I've set the capture level to maximum I can hardly hear the recording when I play it back.

[Edit] I finally got it working. It now records perfectly. I went into terminal, typed alsamixer and I noticed the Mux level was all the way off at 0. I moved it up to 100% and tested. I got great volume on playback of a test recording but there was a bit of noise. I played around and found that with the mux set at 75% I get great quality playback. I also had to set the Capture source to Front Mic but I'd already done that prior to messing with the alsamixer settings and that gave me only barely audible output. It was the mux setting at 0 that was reducing the gain of my mic.

---

### Post by Fraz on 2006-11-05
Yes, it does exist!

Here is my hardware, same as the original posters:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The laptop in question is an Asus S96J.

Okay here is how you "fix" this, it's not a 100% great solution but it gives you the functionality you need.

I noticed two problems with snd-hda-intel after installing Ubuntu 6.10 (Edgy).

1) Microphone refused to work. The internal one was always garbage and never worked, even in Windows, but my external headset microphone refused to work whatever amxier settings I used.

2) The volume control would change the "Headphone" volume which does nothing.

How to fix:

1) You need the latest ALSA driver. Do this:

1. Get build-essential and linux-headers packages.
2. Get alsa-driver package from alsa-project.org
3. Unpack it.
4. Run "./configure --with-cards=hda-intel"
5. Run "sudo make"
6. Run "sudo make install"
7. Edit /etc/modules and add "snd-hda-intel"
8. Reboot.

You will now notice new options in the Gnome Volume Manager. For me the front microphone input is labeled "Microphone" (Not FRONT microphone, that is the busted internal mic). It now works.

If you don't see it, add "options snd-hda-intel model=ref position_fix=0"
to /etc/modprobe.d/alsa-base and reboot again.

Now, for problem number 2, the Volume Control keys.

Basically unless we can either hardcode gnome-volume-manager to adjust FRONT instead of HEADPHONE or merge the two in ALSA we have to use the following work around:

1) Edit /etc/acpi/mutebtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_MUTE
amixer sset Front toggle

2) Edit /etc/acpi/volupbtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEUP
amixer sset Front 1+ unmute;

3) Edit /etc/acpi/voldown.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEDOWN
amixer sset Front 1-;


Done!!

The only drawback is you lose the visual notification gnome-volume-manager gives you.

If there is a way to merge headphone & front please tell me!

Thanks.

---

### Post by dejitarob on 2006-11-05
I have an Asus Z70v laptop with an Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller. Thanks to some of the suggestions on this thread, I got my mic working by doing the following:

Make sure /etc/asound.names is correct
```

sudo alsactl names
sudo alsactl store
```

Then
```

alsamixer
```
and bump up "Mic" to 100%, change "Input source" to "Mic", set "Channel Mode" to "2ch", hit tab to change to the Capture page, and make sure Capture is all the way up.

And lastly ```
sudo alsactl store
``` for good measure.

---

### Post by ryu kun on 2006-11-11
> **Fraz said:**
> Yes, it does exist!

Here is my hardware, same as the original posters:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The laptop in question is an Asus S96J.

(...)

Thank you Fraz, for your reply and detailed information. I'll try all of them as soon as I get my laptop back from HP repair service. I unfortunately had a keyboard problem with my laptop which seems not very rare in Pavilion dv5000 and dv8000 series. :(

By the way, you can check  [this]("http://www.linuxquestions.org/questions/showthread.php?t=473668") thread for additional information about our low output problem.

---

### Post by mexlinux on 2006-11-13
Where is that "Channel Mode" to set to "2ch"... in alsamixer???? (not there)

---

### Post by SamJonesUS on 2006-11-27
Hello People ! 
I desperately need to find [affordable web hosting](http://hometown.aol.com/webhbest/affordable-web-hosting.html) 
but I also need it to be a [cheap web hosting](http://hometown.aol.com/webhbest/cheap-web-hosting.html) because 
I don't want to spend a lot of money on my personal site. So if anyone knows about a reliable and [cheap web site hosting service](http://hometown.aol.com/webhbest/cheap-web-site-hosting-service.html) please respond. 
I'll appreciate any information I can get. 
Thanks.

---

### Post by birchwood on 2006-11-29
Fraz, your solution worked wonderfully on this Asus A96F. Skype works well. I'm grateful for your help!

---

### Post by atte on 2006-12-01
Do you get the internal mic to work as well? External mic works for me but not internal... I'm using Edgy and the same Intel chipset.

In the alsa mixer I have Capture, Capture 1 and Capture 2. None of them enables the internal mic :-(

---

### Post by vicnov on 2006-12-01
Good news for those who have hda intel card with conexant 5045/5047 codec:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

---

### Post by Charles Hand on 2006-12-03
I have 82801G (ICH7 Family) and alsamixer has a Mic and Line label, but no thermometer over either one. Up/down arrow keys don't do anything. Capture has a thermometer, and up/dow keys work. There is only an external Mic on this computer, no internal. GUI volume applets don't show any Mic at all. I've done sudo alsactl names and sudo alsactl store.  I've followed the procedures of Fraz, also. 

One think about downloading building and installing the alsa driver, do I have to do anything to remove whatever alsa driver came with the Ubuntu disto, or does Fraz's procedure take care of that? Because sound playback works with the Ubuntu distro. It's just the microphone that doesn't work.

---

### Post by zachflanders on 2006-12-03
I have a hp pavilion dv6000 with an  Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller, and I am running edgy.  I was having trouble with my internal microphone, line in, and headphones, and I was getting a little frustrated. But after I followed the directions under fraz's post everything works great!  Way to go Fraz!  Now everything in my laptop is working fine.  :D

---

### Post by pokeyflan on 2006-12-08
Actually, I seem to be in the same boat as Charles Hand: the playback works fine, but I can'tget the micropphone to work; I also have an 82801G (ICH7 Family) and my alsamixer controls are also *short* of see. veralcontrols, i.e. no thermometers over 'LINE' or 'MIC'.

Suggestions please?

---

### Post by bro on 2006-12-11
Unfortunately none of this is working for me. I've got the same intell soundcard but I don't have a working mic. I plug it in the side of my laptop. 
There is a build in mic as well. When in volume control > edit > preferences I enable everything I got 3 capture devices. One unnumbered en nummber 1 and 2. 
If I test it there is some scrumbling coming out of the boxes when I mess around with the unnumbererd one.
But I cannot change any of the 3 capture devices to 'Line' for example. It's just mic mic mic. 
Anybody? I did all of the above (new drivers installed).

---

### Post by brazzmonkey on 2006-12-15
i've got 2 input source selectors. both needed to be changed to "Mic"

---

### Post by mikewhatever on 2006-12-20
> 
Make sure /etc/asound.names is correct
Code:

sudo alsactl names 
sudo alsactl store

Then
Code:

alsamixer

Typed in these on HP Pavilion 5269ea. The fist two produced no outcome. What is supposed to happen? I checked the file 'asound.names' is in etc. Is that it?

' alsamixer' command opened a window with two volume controls, master and PCM. What channels are people talking about?

I should mention, that there is no built in microphone.

---

### Post by ryu kun on 2007-01-03
I have followed Fraz's and dejitarob's instructions, installed ALSA driver 1.0.14rc1. My overall volume has dramatically increased, which is very nice. But my microphone is still not working. 

After ugrading my drivers, I have a new option in my Alsa mixer, "Mic Bypass", and a new tab as "Switches" and a checkbox "IEC958" but they apparently have no effect to my microphone.

---

### Post by eduardo_barros on 2007-01-25
hello.
i want to thank pefdus for his solution. it works perfect on my laptop.
i'm using Dapper and i have a IBM Thinkpad R60. both mics working (internal and external).
thank you.

---

### Post by chinthaka on 2007-02-03
> **ryu kun said:**
> I have followed Fraz's and dejitarob's instructions, installed ALSA driver 1.0.14rc1. My overall volume has dramatically increased, which is very nice. But my microphone is still not working. 

After ugrading my drivers, I have a new option in my Alsa mixer, "Mic Bypass", and a new tab as "Switches" and a checkbox "IEC958" but they apparently have no effect to my microphone.

I also have the same problem, having followed all the instructions. Please help.

---

### Post by jpjunge on 2007-02-05
I am lost on what to do next... I am having the same problem as this guy:

[http://ubuntuforums.org/showthread.php?t=275355&highlight=MX6920](http://ubuntuforums.org/showthread.php?t=275355&highlight=MX6920)

I have a Gateway MX6912 and the only way I can get the mic to work is plug my headphones in to the mic jack and speak through the ear piece. In sound recorder there is no input device and when I check the volume controller properties there is no tab for capture devices or anything. The only tab is playback.

Anyone have any advice on where to look next??

---

### Post by ryu kun on 2007-02-10
If you get this error 
```

checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).
```

when you try to compile alsa drivers after a kernel upgrade, try this command first:

```
sudo aptitude install linux-headers-`uname -r`
```

---

### Post by ryu kun on 2007-02-10
> **vicnov said:**
> Good news for those who have hda intel card with conexant 5045/5047 codec:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2401)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2485)

This is a very good news!

Vicnov, I applied [your instructions]("http://ubuntuforums.org/showpost.php?p=1914583&postcount=16") and my microphone is FINALLY working!! Thank you very much!

I'll celebrate this: :guitar:

---

### Post by likwidsnj on 2007-02-14
All-
  I have an HP dv6025 with the hda-intel chipset. i followed Franz's doc to get the headphone output working, and you are the man, Franz! However i ran into the same problem with the ACPI buttons controlling the headphone fader instead of the master fader, and the speakers were not getting muted when plugging in the headphones. i just installed the newest ALSA driver thats in testing, but did not run the ./configure --with-intel-support or whatever line Franz stated. Now, my ACPI buttons work great and the headphones work off the same volume controls, as well as mute the speakers when plugged in. You guys rock, and after booting up this machine with its stock Vista install just once, one can see how far superior Ubuntu is. :P

---

### Post by mahy on 2007-03-21
Wow, it finally works for me! I've got the ICH6 chipset. First i tried to install newest ALSA drivers, but they completely hosed my sound system (bad gcc version -- my fault). I managed to revert to older drivers and kept searching for some solution. Then i found gnome-alsamixer which did it!! (I've got Xfce, so it wasn't obvious.) All i had to do was to slide the "capture" slider all the way to the top AND check the "Rec." box. (Something that alsamixer isn't capable of) That's it! I love you, Tux the penguin.

---

### Post by joey111 on 2007-04-11
hey man, you are a legend after having tried virtually anything it now works!
quite silent though, but it works. any idea how to make it louder if all settings in the alsamixer are already 100%?
thanks anyway, tried it on a amilo si1520 with the 2.6.17-11 kernel and the alsa driver 1.0.13 (1.0.11 refused to work)

---

### Post by kissg1988 on 2007-11-06
This issue had been solved, you just need to update to alsa drivers version 1.0.15.

Download, compile and install these source packages:

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2)

More information in the INSTALL file.

This solved me the problem with no mic boost on alsa mixer.

---

### Post by Soglad on 2007-11-07
> **Fraz said:**
> Yes, it does exist!

Here is my hardware, same as the original posters:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The laptop in question is an Asus S96J.

Okay here is how you "fix" this, it's not a 100% great solution but it gives you the functionality you need.

I noticed two problems with snd-hda-intel after installing Ubuntu 6.10 (Edgy).

1) Microphone refused to work. The internal one was always garbage and never worked, even in Windows, but my external headset microphone refused to work whatever amxier settings I used.

2) The volume control would change the "Headphone" volume which does nothing.

How to fix:

1) You need the latest ALSA driver. Do this:

1. Get build-essential and linux-headers packages.
2. Get alsa-driver package from alsa-project.org
3. Unpack it.
4. Run "./configure --with-cards=hda-intel"
5. Run "sudo make"
6. Run "sudo make install"
7. Edit /etc/modules and add "snd-hda-intel"
8. Reboot.

You will now notice new options in the Gnome Volume Manager. For me the front microphone input is labeled "Microphone" (Not FRONT microphone, that is the busted internal mic). It now works.

If you don't see it, add "options snd-hda-intel model=ref position_fix=0"
to /etc/modprobe.d/alsa-base and reboot again.

Now, for problem number 2, the Volume Control keys.

Basically unless we can either hardcode gnome-volume-manager to adjust FRONT instead of HEADPHONE or merge the two in ALSA we have to use the following work around:

1) Edit /etc/acpi/mutebtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_MUTE
amixer sset Front toggle

2) Edit /etc/acpi/volupbtn.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEUP
amixer sset Front 1+ unmute;

3) Edit /etc/acpi/voldown.sh to read:

#!/bin/bash
. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_VOLUMEDOWN
amixer sset Front 1-;


Done!!

The only drawback is you lose the visual notification gnome-volume-manager gives you.

If there is a way to merge headphone & front please tell me!

Thanks.

Arrrgh!!! I did this and now I have NO access to my volume control manager AND I don't have any sound!!

Holy ****! I can't seem to get it working again!

What the hell's up here!!!! Please help!

---

### Post by kissg1988 on 2007-11-08
I think, your sound card uses a different driver. Try to build the alsa-driver package without any parameters (use a simple "./configure" command without any parameters).
Then, do a "make".
And finally, Install the freshly built drivers with "sudo make install".

Following these instructions, you'll have a full set of alsa drivers and all of the config files will be overwritten.
It's a good idea to install the alsa-lib package from the same version, after the drivers had been installed.

If this doesn't help you, try to reinstall the original alsa-drivers shipped with Ubuntu.
On a terminal, type "sudo aptitude".
Search for a package named "alsa-base". Press the Shift + L keys to mark the package for reinstallation. This will replace the config files with ones having default settings.

I hope this helps you.

---

### Post by lacabra on 2008-02-12
Following this thread, I also got this one working:
```

Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

under Debian Lenny/Sid with kernel 2.6.24 and alsa drivers 1.0.15. I could hear my mic through the speakers, but I was unable to record. My problem was that using XFCE as the window manager, the  volume sound applet cannot control all the parameters, thus I could fix it using alsamixer. Make sure you change the capture controls not only the playback (there's also a mic in playback that controls the mic directly through the speakers but not the recording).

What made the difference for me was to toggle the Capture and Capture 1 settings through alsamixer, which I was unable to do from anywhere else (yes I also played with /var/lib/alsa/asound.state with no luck).

So get the newest kernel, and newest drivers, and play around with alsamixer!

---

