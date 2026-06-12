---
title: "Can't install nvidia drivers on Feisty"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by cris on 2007-04-19
I want to install the nvidia drivers that i downloaded from nvidia.com.
This is how :
sudo apt-get install linux-headers-generic build-essential gcc xserver-xorg-dev pkg-config
sudo sh NVIDIA...
(this is how i was installing the drivers on 6.10 and worked perfect). But now , it says that it can not find build-essential , xserver-xorg-dev and neither pkg-config.  And when i try to run the installer , it says that i need some libc libraries or something. 
Can someone guide through the installation of the driver om Feisty 7.04 ? 
I have an nvidia geforce 6600. Thanks

---

### Post by ntetreau on 2007-04-19
How about trying the brand new restricted driver gui System > Admnistration > Restricted drivers.  It should be as easy as enabling the nvidia driver in there, at least that's how it worked for me!  Godd luck!

Nic

---

### Post by cris on 2007-04-19
thanks , but i've done it. i followed a tutorial found on this forum and all went fine.happy me .
thanks for the help

---

### Post by tonygod on 2007-04-19
I can't get the nvidia restricted drive to enable.

1. I had to install from the Live CD using Safe VGA mode because the mouse cursor doesn't appear otherwise.
          1a. Even if I get through the install, after the ubuntu logo, the desktop puts the monitor (Dell W1900) into some resolution (probably wrong refresh rate) that the monitor doesn't understand so i can't see anything.  So I finally just decided to install in Safe VGA mode.
2. After I got everything installed, every time I tried to enable the restricted driver, it gave me the confirmation dialog asking if i wanted to enable it.  I click enable, then it tells me i need to reboot.  after rebooting, it still isn't enabled.

Am I just hosed?

---

### Post by iggdawg on 2007-04-19
I'm having similar issues.   I open the restricted manager thingy and clicky "enable".   some popup comes up and yells at me, and I click the "enable" button.   then the popup disappears, and I'm back to the driver manager GUI with the enable box unchecked.   I haven't done it an infinite number of times yet, but I've done it a number of times and it continues to not work at all.   seems to just summon the popup.  I'm a BSD guy so I'm used to command-lining everything.   maybe I just don't get it =(

---

### Post by eyelessfade on 2007-04-19
then apt-get install nvidia-glx is the thing for you :)
just remember that nvidia-glx comes in three packages:
nvidia-glx-legacy, nvidia-glx and nvidia-glx-new. This is because nvidia don't support old cards in new releases.
So find out which you need first.

---

### Post by iggdawg on 2007-04-19
I tried installing nvidia-glx from the command line but it protested initially.  after doing "sudo apt-get update" from the command line, it seems to be doing its thing just fine.  it was a command-line thing after all =P (I know I could have just hit a button somewhere, but let me have my moment).  I guess I thought after a fresh install I wouldn't have to do an update right away.

EDIT - after restarting, the screen goes black.  like, off-black not "displaying black"-black.    I had to go back to the nv driver.

---

### Post by eyelessfade on 2007-04-19
it was a problem before. its fixed for me. but...

if you still have nvidia in xorg. try sudo rmmod nvidia and then restart gdm/kdm

somehow xorg refused to start if it didn't inject the module itself. weird but that was how it was

---

### Post by zachwlewis on 2007-04-19
I'm not a Linux guy at all, but I am having the same "won't check 'NVIDIA accelerated graphics driver' box."

Anyone want to give a newbie a step-by-step on how to get this stuff enabled?

---

### Post by aleska on 2007-04-19
> **ntetreau said:**
> How about trying the brand new restricted driver gui System > Admnistration > Restricted drivers.  It should be as easy as enabling the nvidia driver in there, at least that's how it worked for me!  Godd luck!

Nic

What is the equivalent of System > Administration > Restricted Drivers in kubuntu?

---

### Post by Ram Crammer on 2007-04-19
For the last two months, I've been running Feisty beta, and my system is fully in sync with the new 7.04 released today (19-APR-07), thanks to automatic updates.  Everything had been working great till last night.  My nephew has been after me to get accelerated  3D going with my ancient GeForce3-TI200 AGP card, so I decided to have a go.  I enabled the accelerated 3D driver from "desktop effects" in "Control Center", and after the system installed the new driver, I rebooted as instructed.  I then returned to "desktop effects" to "enable driver".  I got the slinky wobbly effects going but discovered that the windowing "max", "min", and "close" buttons were wonky, and other unsettling behavior, so I decided to undo the driver change.  

Well, I discovered it's pretty much a one way street.  No easy way back :-(   I used Synaptic to uninstall the newly installed nvidia-glx driver, then I rebooted.  Gotcha!  White screen after login.  I ended up having to edit /etc/X11/xorg.conf, changing the driver section from "nvidia" to "nv".  Now I have the generic open-source driver working, but performance is reduced, and 3D screen savers no longer work.  I've tried installing the other drivers in the depos, but no matter what I do, I can't get graphics back to their previous state.  It seems like my original proprietary binary driver and/or kernel was totally wiped and I'm not sure how to get it/them back onto the system, configured, and enabled.   I tried Automatix and it said it was unable to fetch nvidia-glx from the Ubuntu website, and to "try later".  The nvidia-glx driver is not what I want to restore to, anyway.  Envy doesn't support Feisty, yet, either.

I really don't know much about how to set this stuff up, and there are so many conflicting suggestions on the forums that I'm just unsure what to try.  Presently, at least the system is usable.  I just want to install and enable the proprietary nvidia driver that was enabled during the original Feisty installation.  This doesn't appear trivial, and I'm afraid of borking it and losing X service altogether.  Editing archane config files with vi in terminal mode does not make for a pleasant day, in my book.  

Consider this post a warning to those who may be thinking of enabling the accelerated 3D driver.  If it doesn't work for you, there's no easy way back for those of us who were originally running the proprietary drivers.  Definitely not nice for something this experimental.  I'd say someone dropped the ball.

Satelite AK31A, AMD XP 1700+, 350 Watt Antec PSU, 512MB, 2 X Maxtor 60Gig 7200 , NEC NIC, Nvidia GeForce3-TI200, ViewSonic E90fb,

---

### Post by Ram Crammer on 2007-04-19
> **aleska said:**
> What is the equivalent of System > Administration > Restricted Drivers in kubuntu?

The easy answer is SYSTEM-->ADMINISTRATION-->RESTRICTED_DRIVERS_MANAGER.  But I don't think it will do what you want.  It's pretty lame.  Mine only lists "NVIDIA accelerated graphics driver" and has a check box to enable, and an indicator to show "in use" or "not..."  It seems more like a stubbed feature to me.  In fact, read my earlier post.  The whole restricted driver issue seems like an afterthought.  Anyway, hope this helps.

EDIT:  Opps!  Just noticed you're asking about K-ubuntu.  My answer is for Ubuntu (Gnome) and probably isn't right for you.  I need to be more careful of these different flavors of Ubuntu.  Sorry.

---

### Post by craigsharp on 2007-04-19
I'm in the process of installing my drivers with Envy,  The website said it was compatible,   It's done now, so i guess it's time to restart,  I'll post a new reply to let you know how it worked.

---

### Post by Ram Crammer on 2007-04-19
> **craigsharp said:**
> I'm in the process of installing my drivers with Envy,  The website said it was compatible,   It's done now, so i guess it's time to restart,  I'll post a new reply to let you know how it worked.

I checked the Envy homepage this morning and a fresh post stated that Envy would refuse to install Nvidia driver to Feisty.  Are you trying to run Envy on Feisty or an earlier release?  If Envy has already been updated and it works, that's great news.  Please post results asap.  Thanks!

---

### Post by bodean on 2007-04-19
Just put 7.04 ubuntu on, how do I grab the latest NVidia drivers for my Geforce GO 7400 card and whats the method to get them installed?

---

### Post by craigsharp on 2007-04-20
Sorry for the late reply,  YES! envy works, great!  check out the site again,  I'm so pleased with this release of ubuntu,  so far so good for me.  having nvidia drivers is sweet!

---

### Post by Ram Crammer on 2007-04-20
> **craigsharp said:**
> Sorry for the late reply,  YES! envy works, great!  check out the site again,  I'm so pleased with this release of ubuntu,  so far so good for me.  having nvidia drivers is sweet!

Thanks Craigsharp, I'm off to try it myself.  Will post results.

---

### Post by tonygod on 2007-04-20
> **tonygod said:**
> I can't get the nvidia restricted drive to enable.

1. I had to install from the Live CD using Safe VGA mode because the mouse cursor doesn't appear otherwise.
          1a. Even if I get through the install, after the ubuntu logo, the desktop puts the monitor (Dell W1900) into some resolution (probably wrong refresh rate) that the monitor doesn't understand so i can't see anything.  So I finally just decided to install in Safe VGA mode.
2. After I got everything installed, every time I tried to enable the restricted driver, it gave me the confirmation dialog asking if i wanted to enable it.  I click enable, then it tells me i need to reboot.  after rebooting, it still isn't enabled.

Am I just hosed?

Well I re-installed again and this time after I booted the Live CD (Safe VGA) and before I installed I set my internet proxy up by going into System->Preferences->Network Proxy.  After doing this and getting through the install, I was then able to enable the nVidia Accelerated Driver and all seems to be working.  Now if I can only figure out how to get it to do 1280x768 @60hz so my desktop isn't stretched horizontally.

---

### Post by craigsharp on 2007-04-20
Have you tried to download and install Envy?  Works like a charm!

---

### Post by JohnnyTarr on 2007-04-20
> **zachwlewis said:**
> I'm not a Linux guy at all, but I am having the same "won't check 'NVIDIA accelerated graphics driver' box."

Anyone want to give a newbie a step-by-step on how to get this stuff enabled?

I'm having the exact same problem. 

I tried the command line ideas provided but it didn't seem to work!

Help! :confused: 

thx

---

### Post by Erlander on 2007-04-20
> **JohnnyTarr said:**
> I'm having the exact same problem. 

I tried the command line ideas provided but it didn't seem to work!

Help! :confused: 

thx

I think that the repositories are so busy at the moment that the restricted driver manager cannot always work.

I also had some trouble on my second pc that has an ATI card but got them in the end.

Check that restricted drivers is enabled in Software Sources.

Rob

---

### Post by Ram Crammer on 2007-04-20
Hi Craig

I'm back.   I Installed Envy, and ran it.  It did a whole lot of stuff, downloading source, headers, compiled, installed stuff (common kernel, and who knows what else) and I just accepted all defaults and suggested actions.  Envy correctly identified my card and chose the nvidia-glx-96xx driver as correct for my system.  Okay, so what do I know?  It looked like it was completely overhauling my system.  On and on it went, pages and pages of text scrolling off my screen as it chugged away.  It reported a number of errors along the way, but always seemed to resolve them, and then it announced that it was finished and offered to reboot my system.   I selected yes (it was recommended).  

Alas, it was all in vain.  :-(  The X server crashed on startup.  :confused:  I retrieved the Xorg.0.log file and re-edited xorg.conf, again, for about the 12th time today, editing the line:   Device:  "nvidia"  to "nv", so as to at least be able to run the default Xorg open-source driver.  And that's where I am now, back to plain vanilla nv.  

According to the log file, X  could not find the "device" (driver) "nvidia", as always, since my mishap.  I'm really disappointed.  I was so confident that Envy would just work for me, after your successful experience with it.   Considering that I haven't changed anything except that single line in the Xorg.conf, I just can't understand how my  graphics drivers/kernel could be so broken.   And brother, nv is a pretty rough running clunker, next to the proprietary driver.  

Anyway, it was fun while it lasted.  It looks like I may have to re-install from the live-CD in order to get my nice smooth system back. :cry:  I don't think I should file a bug report to Alberto, yet, since this was posted as an unstable release of Envy.  I may wait a few days and try downloading Envy again and see if it works any better for me.

---

### Post by craigsharp on 2007-04-20
Sorry to hear about your misfortune,  What graphics card do you have?   Well, nevermind,  Envy is supposed to  detect it and such,  Other then that, i'm at a loss.  I had my x-server crash on me after i installed nvidia drivers on 6.10 and eventually said i'd had enough,  Man am i glad i came back though,   I would try reinstalling Feisty and immediately system update,  then Try envy with a fresh install.

I'm no linux expert, just an expert in my own mishaps,  I was reading somewhere there is a snippet of code that allows xorg to be reconfigured with the correct nvidia tags,  i just forgot where i found it,  I'll check reall quick and i'll get back to ya.

Craig

---

### Post by craigsharp on 2007-04-20
Here,  I think this will repair your x-server.  This is what I did after beryl caused my xserver to crash when i was using Edgy.  It should work with Feisty.  When it says x-server has crashed  press ctrl-alt-F1 and log in, and then make sure GDM is shutdown by typing
```
sudo /etc/init.d/gdm start
```

after it is shutdown, then type

```
sudo rmmod nvidia && sudo modprobe nvidia
```

That unloads and reloads the nvidia kernel module.   Then restart 
gdm by typing

```
sudo /etc/init.d/gdm start
```


Try that out,  it should work.

Craig

---

### Post by Erlander on 2007-04-20
I think you mean:

```
sudo /etc/init.d/gdm stop
```

for the first command.

Rob

---

### Post by Ram Crammer on 2007-04-20
> **craigsharp said:**
> 
```
sudo /etc/init.d/gdm start
```
after it is shutdown, then type
```
sudo rmmod nvidia && sudo modprobe nvidia
```
That unloads and reloads the nvidia kernel module.   Then restart 
gdm by typing```
sudo /etc/init.d/gdm start
```
Try that out,  it should work.

Craig

Hi again Craig,
I gave your suggestion a try.   rmmod reported no such module nvidia in /proc/modules.  So, I looked in the /proc directory.  Lots of zero-byte directories, including ./modules.  I got the brainy idea that maybe I had better try running Envy again, as root, so it would have permission to create any directories it might need to store its output files to.  This time, I was in terminal mode and was able to read the output messages more easily.  It was too fast for me to see everything, but it was plain enough that there were a number of errors due to files not being present, and in effect, Envy sometimes simply ignored the errors returned by its build scripts.  As one might expect, Envy isn't the most robust program.

Envy isn't the only program that could use more work.  It looks to me like Synaptic did a real good job of removing the nvidia-glx-9631 driver, when I had it uninstall the driver package, at the outset of this adventure into the land of no return.  The package manager no doubt removed much that is needed by Envy to rebuild the driver module.  I also tried letting Symantic re-install glx-9631, thinking it might correct its previous changes.  Ran Envy again.  No sir; it didn't help at all.  Still no module.  Heh, no wonder X won't start .   These graphics drivers are a nightmare for developers and users alike.   

Anyway, thanks a lot for your help.  It wasn't in vain.  I learned something, even if it's just not to be too quick to uninstall something.  I'm a pretty cautious guy around my Linux box, but I got a bit carried away this time.  :)

---

### Post by QwertyManiac on 2007-04-20
> **iggdawg said:**
> I tried installing nvidia-glx from the command line but it protested initially.  after doing "sudo apt-get update" from the command line, it seems to be doing its thing just fine.  it was a command-line thing after all =P (I know I could have just hit a button somewhere, but let me have my moment).  I guess I thought after a fresh install I wouldn't have to do an update right away.

EDIT - after restarting, the screen goes black.  like, off-black not "displaying black"-black.    I had to go back to the nv driver.

Ditto trouble here :( Black screen.

---

### Post by kahuuna on 2007-04-20
> **iggdawg said:**
> EDIT - after restarting, the screen goes black.  like, off-black not "displaying black"-black.    I had to go back to the nv driver.

I think this is due to the monitor refresh rates not being set correctly by default - ie it's probably trying to display a higher refresh rate than your monitor allows in /etc/X11/xorg.conf

You could try fiddling with the refresh rates under your monitor settings to suit your own monitor and make sure your graphics card can support them. Worth a try?

---

### Post by bodean on 2007-04-20
Any solutions?  I, unlike others, haven't installed envy.

---

### Post by Huffalump on 2007-04-20
> **craigsharp said:**
> Here,  I think this will repair your x-server.  This is what I did after beryl caused my xserver to crash when i was using Edgy.  It should work with Feisty.  When it says x-server has crashed  press ctrl-alt-F1 and log in, and then make sure GDM is shutdown by typing
```
sudo /etc/init.d/gdm start
```

after it is shutdown, then type

```
sudo rmmod nvidia && sudo modprobe nvidia
```

That unloads and reloads the nvidia kernel module.   Then restart 
gdm by typing

```
sudo /etc/init.d/gdm start
```


Try that out,  it should work.

Craig


Just some feedback.  I tried this to solve a Failed to load module wfb after upgrading to Feisty, but this solution did not work.  Thanks for leaving some ideas, however!

---

### Post by bg1256 on 2007-04-20
In response to those whom Envy has worked for...

It did not work for me on Kubuntu 7.04 with an Nvidia 7600 GeForce card.

Installing through the command line does not work either.

All it gives me is a blank screen on startup.

---

### Post by Huffalump on 2007-04-20
> **ntetreau said:**
> the brand new restricted driver gui System > Admnistration > Restricted drivers.  It should be as easy as enabling the nvidia driver in there, at least that's how it worked for me! 

I must be both thick-headed and blind.  I have upgraded to Feisty, had problems with X not using nvidia drivers (which worked fine before), and am currently limping by with "nv" BUT in my menus under System > Administration there is no item for Restricted Drivers. 

How now?

---

### Post by marklid on 2007-04-20
> **Huffalump said:**
> I must be both thick-headed and blind.  I have upgraded to Feisty, had problems with X not using nvidia drivers (which worked fine before), and am currently limping by with "nv" BUT in my menus under System > Administration there is no item for Restricted Drivers.

I don't have that option either :confused:

---

### Post by craigsharp on 2007-04-20
I'm at a loss of words,  Sorry i couldn't help anyone out.  If this is your main OS and you have to have it to work 100 percent,  perhaps you could go buy a newer NVIDIA Card and do a clean install of Feisty...  Just a thought.  The older cards, from what i am learning. use an old nvidia driver.  The newer ones, use the newest driver.

I am using a 7600GS and it worked first time,  I think you can pick up a 7300 for less then $100.

---

### Post by marklid on 2007-04-20
Your help is appreciated !

I might do a clean install anyway as there seems to be a few inconsistencies between what I'm seeing and what I *should* see.

The only thing putting me off is the fact that certain things seem to take ages to get working correctly ! Oh well that's how you learn I suppose...

---

### Post by angryoaf on 2007-04-20
The restricted drivers don't work well for my system (or dont seem to anyway).

Could I have an answer to the OP's question?

---

### Post by etherealremnant on 2007-04-20
ARGH!

I'm 5 seconds away from switching distributions permanently!

I swear to god if someone doesn't figure out how to get my 8800GTS working with full accel under Feisty, I'm going to Sabayon and never looking back.

This is ridiculous. WHO CARES that its proprietary software!? Ubuntu's "just works" theme doesn't bode well with absolutely no support for the latest video cards!

Both nVidia AND ATi users are pissed right now and its just going to get worse!

---

### Post by sKiz on 2007-04-20
Just followed somebodies advice and after not being able to install Fiesty 7.04 on my Dell E1505 Radeon X1400, I entered a simple string and am happy to announce I am typing from ubuntu :D
[B]
sudo X -configure
sudo cp /home/ubuntu/xorg.conf.new /etc/X11/xorg.conf
start x[/B]

(CASE SENS)

I don't remember who wrote this so sorry for lack of credit.

---

### Post by Huffalump on 2007-04-20
> **marklid said:**
> I don't have that option either :confused:

I did finally get an answer on this particular detail.  While Ubuntu claims that the Final FF is the same as the last beta (available a few days before the final, or --in my case-- just an hour before releasing final), the fact is  that is not true.  The menus are different.  We have neither the navigation item for Restricted Driver Manager nor for Desktop Effects.  Those are both present in the Final, so there is a (small) difference.

I don't, at this time, see any way to get those menu items (or call their objects from the terminal, either).  There's no way to upgrade from beta to Final.  Weird.

---

### Post by marklid on 2007-04-20
> **marklid said:**
> Your help is appreciated !

I might do a clean install anyway as there seems to be a few inconsistencies between what I'm seeing and what I *should* see.

The only thing putting me off is the fact that certain things seem to take ages to get working correctly ! Oh well that's how you learn I suppose...

WELL did a clean install, luckily kept my /home on a separate partition, and all the 'new' menus are there. Selected the restricted nvidia driver and so far the desktop effects seem ok...

---

### Post by atf487 on 2007-04-20
OK, I had the same problem as you guys were having, and here is how I fixed it.

Step 1: Remove all instances of the nvidia drivers on your system
Step 2: sudo apt-get install nvidia-glx-new . And wait until it installs
Step 3: sudo gedit /etc/X11/xorg.conf
Step 4: Under section "module" remove the string Load "dri"
Step 5: Under section "Device" change Driver "nv" to Driver "nvidia"

Here is my xorg.conf for those interested. 

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation C51G [GeForce 6100]"
	Driver		"nvidia"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"ENVISION"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51G [GeForce 6100]"
	Monitor		"ENVISION"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by etherealremnant on 2007-04-20
I just got my 8800GTS working by following: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by EnterDaMatrix on 2007-04-20
[B]How to Fix:
[I][U]
In Gnome:[/U][/I]
```
sudo gedit /etc/X11/xorg.conf
```
Remove this line in the "Module" section:
```
	Load	"dri"
```
Save and ctrl-alt-backspace.

[I][U]
In single user mode:[/U][/I]
```
sudo nano /etc/X11/xorg.conf
```
Remove this line in the "Module" section:
```
	Load	"dri"
```
Save
Test configuration:
```
startx
```

If it works reboot

[/B]

Insure that your driver is nvidia and not nv.

---

### Post by moollar on 2007-04-20
I had the problem with clicking on the Enable check mark for the Nvidia drivers and nothing happening. After running updates, it finally worked. Desktop effects are pretty cool! :)

---

### Post by Bobcatben on 2007-04-21
my problem sounds similer to the ones in this post, i have a geforce6800 ultra, and if i do the restricted driver, its just black, no login sound or anything, if i download from the nvidia site, and install manualy, xserver crashes with lotsa garbled text. im gonna try some of this stuff in this thread and see if it works.

Edit: i installed the 32bit version and the restricted driver works now, guess ill have to wait till the bugs are outa the 64bit version.

---

