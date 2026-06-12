---
title: "Tv-out with gutsy + ati driver using only TV"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by vemon on 2007-10-19
Hi!

Is there a way to use tv-out with the ati open source driver without a monitor attached (TV as the only output device)? I know the xrandr commands I would use (while X running) to enable the TV-out are:

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600

.. but I cannot run them since X doesn't even start with the "ati" driver when only TV is connected to my radeon9000. And running the commands under vesa "accelerated" bulletproof X is probably not helping anyone :). 

So is there a way to get the same functionality as the xrandr commands by editing xorg.conf? I have tried using this guide: [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12) but with no success. I only get no suitable screens found in xorg log.

Maybe this could be fixed with "xrandr --addmode" equivalent in xorg.conf?

I'll attach my xorg.conf to this message as soon as I get home but please reply if you have any ideas or a working xorg.conf for ati tv-out in Gutsy!

- Jaakko

---

### Post by mostrovoi on 2007-10-19
I have exactly the same problem. My graphic card is a radeon 9250 and it was working perfectly with feisty, open-source driver + patch provided by gatos for enabling tv-out. The problems started when I upgraded to gutsy, after that I get the error that no suitable modes were found. 
I am using the same xorg.conf file which was working in feisty, 
I even tried to map all the outputs to different monitor configurations but I always end up with the vesa driver loaded.

---

### Post by vemon on 2007-10-20
I still haven't gotten X to start with TV as the only output device using the ati driver but I tried the xrand commands with both monitor and tv attached. The result was a "picture" that was so out of sync that I couldn't make anything of it. I don't even know how to debug that problem since the modeline xrandr shows for the 800x600 mode (xrandr -q --verbose) seems like a correct PAL modeline. And of course adding any other modeline for tv-out (S-video output) just gives an error since only 800x600 is promised to work with this release. I wonder if compiling the newest xorg ati driver would make it work...

At the moment I'm using the fglrx driver (version 8.28.8 which is the last to work with radeon 9000) and it can enable tv out with overscan (without a monitor attached) but it has other problems. Xv overlay is broken for the second head (tv-out) and crops out 1/3 from the bottom of the picture when running mplayer with "-vo xv". I could use opengl overlay for mplayer but I haven't been able to install the fglrx 8.28.8 kernel module in gutsy so I have no working 3d/opengl. Mplayer's xvidix driver almost works but it has some strange tearing effects when there is movement in the picture and the picture shows only after pressing f (fullscreen) button for a couple of times.

There seems to be no fully working tv-out (w/ overscan & xv overlay) solution for my configuration with Gutsy and Radeon 9000 even though my only need at the moment is to be able to play movies (& dvb) with mplayer. The next thing I'm probably going to try is the VGA-SCART adapter which should give a beautiful tv picture with radeon based cards and the ati driver when using a proper modeline for X.

---

### Post by vemon on 2007-10-20
Here is the config for my setup with the ati driver (which doesn't work):

------------------------------------------------------------------------

Section "Device"
	Identifier "radeon9k"
	Driver     "ati"
	BusID      "PCI:1:0:0"
	Option     "MonitorLayout" "TVMonitor"
EndSection

Section "Monitor"
        Identifier   "S-video"
EndSection

Section "Screen"
	Identifier "TVScreen"
	Device     "radeon9k"
	Monitor    "S-video"
	DefaultDepth     24
	SubSection "Display"
		Modes    "800x600"
	EndSubSection
EndSection

------------------------------------------------------------------------

Here is the config for my almost working (tvout w/ overscan but no working xv overlay) fglrx setup:

------------------------------------------------------------------------

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option      "UseInternalAGPGART" "no"
	Option      "TexturedVideo" "off"
	Option      "VideoOverlay" "off"
	Option      "OpenGLOverlay" "on"
	Option      "MonitorLayout" "tv"
	BusID       "PCI:1:0:0"
	Option	    "TVOverscan" "on"
	Option	    "ForceMonitors" "tv"
	Option	    "TVFormat" "PAL-B"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "720x576"
	EndSubSection
EndSection

------------------------------------------------------------------------

---

### Post by vemon on 2007-10-20
Finally got xv overlay (mplayer -vo xv) working with tv-out using fglrx 8.28.8 driver! The trick is to use mirror mode where the same overlay is used for both heads (crt1 & tv). Only thing that doesn't work now is overscan but it doesn't bother me that much because the image overlaps the screen horizontally (no black borders in left and right side of the screen) and most stuff I watch is widescreen anyway.

Found the answer from this thread: [http://ubuntuforums.org/archive/index.php/t-249846.html](http://ubuntuforums.org/archive/index.php/t-249846.html)

Here are the display related parts of my xorg.conf:

Section "Monitor"
        Identifier  "Default Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ati-fglrx"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"

        Option      "VideoOverlay" "on"

# crt1 has to be enabled like this for the mirror mode & overlay
# to work even though I dont have a monitor attached
        Option      "ForceMonitors" "crt1,tv"
        Option      "DesktopSetup" "mirror"
        Option      "TVFormat" "PAL-B"

# Sadly the TVOverscan option doesn't seem have an effect in the mirror mode
#       Option      "TVOverscan" "on"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ati-fglrx"
        Monitor    "Default Monitor"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "720x576"
        EndSubSection
EndSection

---

### Post by mostrovoi on 2007-10-21
Finally it works for me :) Thank you so much!
I followed your instructions from this and other thread and finally I managed to get it working .
Kiitos!

---

### Post by vemon on 2007-10-22
Just out of curiosity: Did you use fglrx or the open source ati driver?

And how on earth did you know I'm Finnish? :D

---

### Post by Lil on 2007-10-22
There is a bug in the 'radeon' driver as far as I'm aware that scrambles the display when you specify a PAL setting; I believe they are working on sorting it. Thus Svideo output is presently locked to NTSC; which not all PAL devices can sync up to (50 vs 60Hz), some PAL devices will only show it in black and white and others (more modern devices) will work. My JVC LT23D50 with SVideo input can show an NTSC signal fine.

Your solution here is about as good as it gets for TV output on an ATI card when booting.

---

### Post by vemon on 2007-10-22
I'll have to try the radeon driver using NTSC mode like you described. If it would work the two remaining questions for the open source radeon/ati driver would be:

- How to enable tv-out in xorg.conf (no xrandr commands) with no monitor attached?
- How to enable overscan (could be done with xrandr commands after x has started)?

I would prefer the open source driver over fglrx since it "works out of the box" with Gutsy. I even don't have any 3d benefits from fglrx atm since the version 8.28.8 kernel module doesn't compile in gutsy :(

---

### Post by BungaMan on 2007-10-22
> **vemon said:**
> ...Maybe this could be fixed with "xrandr --addmode" equivalent in xorg.conf?...

Have a look at my attached xorg.conf.  It should give you an idea on how it works.

And if you would need more help then let me know.  But do give it a try first :)

BTW, anyone know how to explicitly tell the driver which output (PAL or NTSC) to set?  Or is it not needed and auto detected (does a bad job on my stuff)

---

### Post by vemon on 2007-10-24
BungaMan: I tried with your xorg.conf and was able to modify it so that the only output used was the S-video output. The key seemd to be putting the "Enable" "true" line in the monitor section. Even though the X started I still coudn't get a stable image. I guess my TV just can't sync to NTSC signal :(

Does anyone know if there already is a version of the radeon driver that supports PAL? In the mean time I'm happily stuck using the fglrx tv-out solution which is working nicely at the moment. I still feel a bit naucious not to be using the open source driver :D

To your question (setting PAL/NTSC): The answer can be found from this Wiki page: [http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12). The command to enable PAL would be "xrandr --output S-video --set tv_standard pal" and it's stated that currently there is no way to set output properties in xorg.conf.

---

### Post by BungaMan on 2007-10-24
Thanks for the tv_standard tip.  I'm using a script for my s-video so those settings are not much of a problem.

---

### Post by vemon on 2007-10-24
So were you using PAL or NTSC mode? I'm just asking because earliler in this thread 'Lil' said that the PAL mode just produces an out of sync image to the TV and that's also what's happening when I try to use it.

---

### Post by BungaMan on 2007-10-24
For me as well, default I get the out of sync image.  So what I do is set it to ntsc because my beamer supports it.  That provides a good image.  Pal is not yet properly supported so we'll have to wait for an updated driver.

---

### Post by steve0921 on 2007-10-29
Hello,

I am in the same situation as vemon (oldish ati card, want output on only a TV), and have found this thread very helpful. Thanks.

My one remaining problem is that the picture is black and white. I've done some experimenting with different tv_standards, and only ntsc gives me a stable picture (all others have given out of sync, still black and white garbage). After some reading, I've seen older X.org configurations use both the "TVStandard" option, but also "TVOutFormat". Is there some way to set the latter with xrandr? If I use the xorg.conf option, will it do anything? (I was thinking I could change to COMPOSITE, since I'm using an S-video -> composite converter).

---

### Post by vemon on 2007-10-30
If I've understood correctly there is no way to use PAL tv-out with the ati driver at the moment. And some PAL tv's display ntsc signal as black and white. So with the ati driver and your current tv you're stuck with b&w picture. 

The only way I have gotten tv-out (with colors :D) to work in Gutsy was to use the fglrx driver and mirror desktop. I've posted my working xorg.conf to this thread already. The driver can be installed using the install-fglrx-debian.sh ([http://kanotix.com/files/install-fglrx-debian.sh](http://kanotix.com/files/install-fglrx-debian.sh)) script which is able to patch older fglrx versions to work with Gutsy's rather new version of X. I still had to hack the script a little bit since it tries to download the driver from the wrong place. I can post my hacked installation script here if you are (or would be) using the version 8.28.8 of fglrx.

---

### Post by steve0921 on 2007-10-30
I would appreciate a copy of your hacked script (there's no sense in rehacking the same thing).

I wasn't aware that there was any way to use versions of fglrx that support old cards in new versions of X. This is interesting and probably worth a try.

---

### Post by vemon on 2007-10-30
The script and my xorg.conf can be found from: [http://www.cs.helsinki.fi/u/jjsipari/public/](http://www.cs.helsinki.fi/u/jjsipari/public/)

Run the script like this:
sudo sh ./install-fglrx-debian.sh -y

The script downloads and does it's things in /usr/src directory so if the download fails for some reason that's the place to put the fglrx installer binary. It doesn't try to re-download the driver if it's already there. Good luck with your tv-out!

---

### Post by steve0921 on 2007-10-31
Thanks. I haven't decided yet when I'll give this a try, but if I do I'll update this thread on how it went.

Also, I'm not great at deciphering bash scripts so do you know if this installs the driver as a package? (ie. will it be easy to remove everything it did in case it doesn't work?)

---

### Post by vemon on 2007-11-01
Yep. It first creates a .deb package and then installs it. You can see the package name from /usr/src for possible removal.

---

### Post by seanf on 2007-11-05
gah, wish I had found this thread earlier! I've been hashing out tv-out problems over here:

[http://ubuntuforums.org/showthread.php?t=600091](http://ubuntuforums.org/showthread.php?t=600091)

and finally got a working setup (s-video 800x600 ntsc with the open source ati driver) here: 

[http://ubuntuforums.org/showthread.php?p=3708537#post3708537](http://ubuntuforums.org/showthread.php?p=3708537#post3708537)

The only remaining issue for me is that I can't get fullscreen video on the TV. Any ideas? :-)

---

### Post by Malvin on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/161893](https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/161893) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				whey!

another try! (I think I've spend at least 40 hours of my life with tv-out problems... an the thing is, you always think that the solution is just 5 minutes ahead,,,, ;-)

I really liked this thread, thanks a lot to all.

I have a thinkpad t40p with an radeon 9000 and my problem ist the garbled image when using pal-output... I found the bug in here:
[http://bugs.freedesktop.org/show_bug.cgi?id=12007](http://bugs.freedesktop.org/show_bug.cgi?id=12007)

but didn't find it in lauchpad, so i tried to gain some attention:
[https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/161893](https://bugs.launchpad.net/ubuntu/+source/xrandr/+bug/161893)

if you have similiar problems and an launcpad-account, please confirm or vote for those bugs ;-)
have a nice day,
malvin

ps@vemon: maybe I'll give your script a try, if it really gets the 8.28.8 drive working on current gutsy kernel....

---

### Post by vemon on 2007-11-10
Malvin:
It did successfully install the xorg portion of fglrx 8.28.8 in Gutsy at least for me. I'm still using it without any problems :). As already mentioned the drawbacks are that you're stuck with mirror mode (which doesn't bother me since I only use tv-out) and there is no working kernel module/3D acceleration (which again is not a problem for my media center pc). It may be possible to patch the kernel module to get 3d though...

The install script is originally made by the Kanotix distribution author 'Kano'. I only updated the download location for the ati driver.

BTW It's nice to hear that someone has actually filed bug(s) about the issue with the radeon os driver :)

---

### Post by Malvin on 2007-11-11
I tried the script this night and I'm really impressed... But as you wrote there is no 3D-Accerlation Module included which would load into the new gutsy-kernel ... That was the main thing why I was so interested in the script as I also would like to play Age of Empires, WoW, etc. without having to reboot...
I didn't try the TV-Out with the ati-drive, maybe I'll have a look later this week.
Thank you very much so far,
Malvin

---

### Post by akaihola on 2007-11-11
I remember having perfect XVideo-accelerated PAL TV-out from my Radeon 9200 back in my Mandrake 10 days, perhaps even with Ubuntu Breezy. So maybe an older version of fglrx than 8.28.8 might work better? But how to make them work with the current Xorg version?

---

### Post by Dr.Suave on 2007-11-12
This is what happens when I try and run Vemon/Kano's script:
```

wilf@ubuntu-laptop:~/Downloads$ sudo sh ./install-fglrx-debian.sh -y
[sudo] password for wilf:
Error: No KANOTIX found. Do not ask for support!
Error: No ATI RADEON/FIREGL adapter found.
wilf@ubuntu-laptop:~/Downloads$ 
```
So close and yet so far! Help!:)

---

### Post by vemon on 2007-11-13
Dr.Suave:

What Radeon card do you have? It seems that it's not listed as a compatible card in the script. The compatibility list has been extracted from the actual fglrx xorg drivers so chances to get your card to work using fglrx are not very good.

What do you get when you run these commands (separately):

1. show pci devices with names:

sudo lspci

2. show pci devices with just id's:

sudo lspci -n

3. just show the id's (extracted from the install script):

sudo lspci -n|perl -e 'while(<>){(push(@cards,$_)) if (s/^.+?\s*0300\:\s+(.+?)\s+.*$/$1/)} print join(" ",@cards);'

---

### Post by Dr.Suave on 2007-11-13
I think mine's a Radeon Mobility 9000 - here are the results of your commands:

```
wilf@ubuntu-laptop:~$ sudo lspci
[sudo] password for wilf:
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:01.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
07:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
wilf@ubuntu-laptop:~$ 
```


```
wilf@ubuntu-laptop:~$ sudo lspci -n
00:00.0 0600: 8086:3575 (rev 02)
00:01.0 0604: 8086:3576 (rev 02)
00:1d.0 0c03: 8086:2482 (rev 01)
00:1e.0 0604: 8086:2448 (rev 41)
00:1f.0 0601: 8086:248c (rev 01)
00:1f.1 0101: 8086:248a (rev 01)
00:1f.5 0401: 8086:2485 (rev 01)
00:1f.6 0703: 8086:2486 (rev 01)
01:00.0 0300: 1002:4c59
02:00.0 0200: 10b7:9200 (rev 78)
02:01.0 0607: 104c:ac51
02:01.1 0607: 104c:ac51
07:00.0 0280: 14e4:4320 (rev 03)
wilf@ubuntu-laptop:~$ 
```


```
wilf@ubuntu-laptop:~$ sudo lspci -n|perl -e 'while(<>){(push(@cards,$_)) if (s/^.+?\s*0300\:\s+(.+?)\s+.*$/$1/)} print join(" ",@cards);'
1002:4c59wilf@ubuntu-laptop:~$ 
```

Don't think I did that last one right - sorry

There is a driver on the ATI site for a Radeon 9000, but not a Radeon Mobility 9000 - I've been wondering whether it would be a good idea to install the Radeon 9000 driver (even though mine's a mobility)?

---

### Post by Malvin on 2007-11-13
according to [http://wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx](http://wiki.ubuntuusers.de/ATI-Grafikkarten/fglrx) the fglrx-driver only supports the following cards:

# ATI Radeon 8500, 9000, 9100, 9200, 9250 (R2xx)
# ATI Radeon 9500, 9550, 9600, 9700, 9800, X300, X400, X600 (R3xx)
# ATI Radeon X700, X800 (R4xx)
# ATI Mobility 9000, 9600, 9800
# ATI FireGL 8700, 8800, E1, E2, X1, X2, X3, Z1, T2, 5100, 7100, 7200
# ATI Mobility FireGL 9000, T2, T2e

I don't think "ATI Technologies Inc Radeon Mobility M6" is one of those but too old...
In my previous laptop I had somewhat like an  "ATI Rage M2" and I remember that there was no official linux driver for those old ATI-Cards...
if I'm right, I'm sorry to disappoint you...

---

### Post by vemon on 2007-11-13
I did a google search with the PCI ID gotten from the listing and according to this page your card is actually a Mobility Radeon 7000. It is not supported at all by the proprietary (fglrx) driver, sorry: 

[http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000)

Only driver for that card would be the open source radeon driver which is already shipped with Ubuntu.

---

### Post by Geertjanneman on 2008-01-05
Hi guys,

I've been wrestling with fglrx drivers for 6 weeks now, with the ultimate goal to have TV-out working. I'm running Gutsy on an Acer Aspire 3020 laptop, which has an ATI Radeon Mobility X700 on AGP.
I got the fglrx driver to work quite easily, but was stuck with a garbled image on the TV. The image was vaguely recognisable (colors) but the horizontal sync seemed to be out of order. My desktop seemed horizontally smeared.

ANYWAY.... I made some progress tonight!

After completely purging the xorg-driver-fglrx package yesterday, in an attempt to start from scratch - but now with the open-source driver, I couldn't get latter driver to work at all. So... today I decided to give fglrx one last try. So I put my last working xorg.conf (calling fglrx) back in place and tried to restart gdm. Of course this didn't work, for the xorg-driver-fglrx package needed to be reinstalled first. So next I did a 'sudo apt-get install xorg-driver-fglrx', and restarted gdm again.

What the....???? The TV-out was working suddenly! On a PAL system!

So the big question is: what changed? :confused:
The only thing I can find so far, is that glxinfo now reports MESA instead of fglrx. Of course this is bad news if you want to have fancy 3D stuff, but the sole purpose of my laptop-project is to get it working on a TV so I can watch movies, and to be able to control it with my WiiMote (which i have already up and running by the way, but that's a totally different topic) :)

The only thing I have to get working now is: overlay. At this point I prefer using Totem as the video-player, but with that, the overlay doesn't work. But I'm going to try and look into that right now. As far as xorg.conf is concerned: nothing special there. If I have overlay running, I'll post my configs here.

Hope this gives some hope to all of you who are still stuck out there...

---

### Post by vemon on 2008-01-09
Just a FYI:

Now there should be working PAL (in addition to NTSC) tv-out support in the latest version of the open source ati/radeon driver. The PAL code in xorg-ati was previously broken but has been fixed by mimicing the workings of the old Gatos TV-OUT drivers.

This is probably going to be included in ubuntu Hardy and it's possible someone has already made packages of the newest version for use in Gutsy also. I actually remember that someone hosts an archive of the bleeding edge xorg packages for ubuntu...

Anyways, this was just a FYI for those who are still trying to get the PAL output to work with an old Radeon card. I haven't tried it myself yet since I have a working (but slightly hacked..) fglrx tv-out setup with my Radeon 9000 in Ubuntu Gutsy.

- Jaakko

---

### Post by angels on 2008-01-13
Hello,
Please, can someone tell me what am I doing wrong... I'm trying for so long time to get my tv-out, but without any success. I have the second monitor, I can see it on the tv (black) and I can see the cursor as well. But how to see the video there? If I try to drag my video to the second screen, it is not possible...or I should do in another way? Here is my xorg.conf ...
> Section "Device"
	Identifier	"Device[0]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen 0
EndSection

Section "Device" 
   	Driver          "fglrx" 
   	Identifier      "Device[1]" 
       Screen 1 
       Option          "TVOutFormat" "SVIDEO"
       Option          "TVStandard" "PAL-G"
       Option          "ConnectedMonitor" "Monitor[1]" 
   	BusID           "PCI:1:0:0" #adjust using 'lspci' or cat /proc/pci 

EndSection

Section "Monitor"
	Identifier	"Monitor[0]" #CRT
	Option		"DPMS"
	Horizsync	28-206
	Vertrefresh	43-75
EndSection

Section "Monitor"
	Identifier	"Monitor[1]" #TV
	Horizsync	30-50
	Vertrefresh	50
EndSection

Section "Screen"
	Identifier	"Screen[0]"
	Device		"Device[0]"
	Monitor		"Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "Screen" 
   	Device "Device[1]" 
   	Identifier "Screen[1]" 
   	Monitor "Monitor[1]" 
   	DefaultDepth 24 
         SubSection "Display" 
               Depth 24 
               Modes "800x600" 
       	EndSubSection    
EndSection

Section "ServerLayout"
	Identifier	"Simple Layout"
  		Screen 0 "Screen[0]"
		Screen 1 "Screen[1]" RightOf "Screen[0]"
	Inputdevice	"Generic Keyboard" "CoreKeyboard"
	Inputdevice	"Configured Mouse" "CorePointer"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
    #Mode    0666
EndSection

Section "Extensions"
	Option		"Composite"	"disable"
EndSection

I would really appreciate your help,
Angels

---

