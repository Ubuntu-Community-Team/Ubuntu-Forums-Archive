---
title: "Having a very hard time with my monitor..."
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by steve k on 2006-06-05
sigh...

hey, so i'm another person having weird display problems.

this problem occured both when i tried running the live cd and when I try to boot into my freshly installed dapper system.

I did a clean install but was using breezy before.  under breezy my monitor and everything was recognized immediately, however, swithching to dapper i found i got an error from my monitor that says that the image is 'out of range' just as GDM kicks in.

i've tried all the various 'sudo dpkg-reconfigure xserver-xorg' business, and i've been nothing but frustrated.  when i do manage to get GDM to come up it is at a very small resolution and it makes my desktop basically useless.

i'll post my xconf once i get back to the computer in question.  For the record, the monitor isa benq ff93g and when i dpkg-reconfigure the xserver it does automatically recognize it.

---

### Post by Howzit on 2006-06-05
I have similar problem, I think... I'm a total novice. 

I previously installed Ubuntu 5.10 on my wife's pc at her private practise. No problems, everything worked fine. 

I then downloaded the 386 desktop ISO and tried to install Dapper. I got some error messages and after searching for solutions found a notice in Ubuntu's wiki stating that if you allready have Breezy running you should downlaod the "alternate" ISO - but too late for me.

I then un-installed the Breezy-Dapper-mix by installing Win XP from my laptop's XP cd and deleting the previous partitions. It's the only way I could figure out to uninstall an Ubuntu OS - as I've said I'm a novice. 

Then I tried to run the 386 desktop ISO for Dapper. It loads the live cd "drivers" and then moves on to a GUI. Only problem is that as the GUI is supposed to show my screen goes bezerk and the monitor (Philips 105 S7) tells me that the "signal is out of safe range". I've tried opting for a low screen resolution on the first phaze of the live cd but that doesn't help. It seems like the install is OK up to the point that the screen goes bezerk, but I can't make out anything and thus can't get any further... I trust this is similar to the original post above... Any ideas?

---

### Post by Howzit on 2006-06-05
OK, some progress with my problem. ((please remember that I'm not the originator of this thread, pls. suggest a solution to the 1st guy above if you have!!))

I've looked around in the forums for solutions for my problem described above. Biggest problem is probably my lack of knowledge regarding Linux. However, Ubuntu is supposed to be idiot friendly... :)

Anyways, I tried a lot of things. Hit-or-miss style. As a last resort I tried something that I believed wouldn't work, simply because it looked to easy... As the GUI came up and my screen went bezerk again, saying the "signal out of safe range" thing I simply typed Ctrl+Alt combined with "+" (in my case) or "-". Whalla! The desktop of the live cd displayed. It was displaying way too large and  originally I only saw the "wallpaper" of the desktop. But by moving my mouse up and down I could scroll to the top and bottom bars. At the top bar I selected system>preferences>screen resolution and selected my prefered resolution. It automatically designated a refresh rate (if I remember the term correctly) of 61Hz and now I have a beautiful desktop! Phew, what a relief.

Question is if I will still be OK after running the install. If not, I'll be back in this thread... I can't remember in which of the various threads in the forums I found the above trick, but thanks to whoever posted that trick. Definetaly worked for me.

---

### Post by steve k on 2006-06-05
i'm glad to hear your problem rectified itself.

the same thing didn't work for me unfortunately...i think i'll try another re-install and see what happens.

i also installed from the alternate cd image because i found the Ncurses dialogues far more satisfying to look at than the live cd, which kind of confused me...

anyway, if anyone's got any ideas my next plan of attack is to re-install breezy and then almost immediately dist-upgrade and see if that works.

i usually try to do clean installs when a new os comes out, i find that it's usually more stable, but in this case this seems to be the fastest solution, hopefully, whatever autodetected display settings breezy was able to get that dapper seems to not be able to get will persist from one to the other after i upgrade.

sigh...

---

### Post by Howzit on 2006-06-06
Steve, just a quick check. I suspect that what you referred to in your first post above is the fix also listed in the "HowTo" wiki on ubuntu. The code you mentioned "sudo dpkg-reconfigure xserver-xorg", is part of that solution. However, just to be on the safe side, if you haven't done so yet, have a look at: [https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28videoresolution%29]("https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28videoresolution%29")

The above page provides two lines of code before you get to the xorg app, which may help. I didn't need any of his other suggestions, but he does discuss more options lower down on the page.

As mentioned above I was unaware of the option to upgrade directly from Breezy's upgrade manager until it was too late. I'll definetaly try it with the next upgrade. I suspect your files, settings, etc. will remain in place which will be a great  time-saver. Furthermore, I hope that because Linux is different from Windows the upgrade will be a stable and firm OS. I may be proven wrong, with Windows my experience is that you have to format disks and make a clean install if you have any hope of saving an unstable OS.

---

### Post by steve k on 2006-06-06
well,
howzit, thanks for posting that stuff, there were a few things in there that i hadn't tried, but for the most part i can't figure this out at all.  I have allowed dpkg to reconfigure the system, i have checked the results of autoconfiguration manually and found that, yes, the computer was recognizing my monitor and such...

the specs that *I KNOW* my monitor has are all appearing in the xorg.conf file and the sync rates are all exactly as both my monitor and the manual says they should be.  More frustrating is that all this worked under breezy. It worked 100% and I didn't have to do *anything*.  Which maybe took a bit of the joy out of linux but....

if anyone has any bright ideas here's what my xorg.conf looks like:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"BenQ FP93G"
	Option		"DPMS"
	HorizSync	31-83	
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"BenQ FP93G"
	DefaultDepth	16	
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

In case it's an issue, you'll notice the display for 16 bit video is only using 1024x768 res. this is because i get the above mentioned ;out of range' error whenever I use the monitor's proper, nice looking 1280 1024 resolution.

---

