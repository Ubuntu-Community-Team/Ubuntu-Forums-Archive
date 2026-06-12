---
title: "Adventures in making this thing work"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by Dr.Gonzo on 2007-12-20
Hehe i'm enjoying the Ubutnu experience. Totally different feel from a windoze system, and I can still use winamp. [dx 10 on ubuntu sounds cool, give it that extra kick, but back to reality here...]

I don't know what happend, I installed the Nvidia restricted driver and everything went blank. Now I don't know what buttons I hit to get to a terminal, but dag-nabit I finally was able to run "sudo dpkg-reconfigure xserver-xorg and get a decent resolution. 

The fun came in switching over to Component Video, hehe looks way better on a 32 inch flat panel. I managed to reconfigure my xorg.conf to 720p, but my choices in resolution are kinda limited. Over in windoze land [dual boot] I can get a resolution of 1366x768 with no drama and a killer picture.

I've read all over the Nvidia driver help page, but since my monitor isn't natively supported in Ubuntu. I'm left with having to I guess; write a driver [probably just configure the xorg.conf somewhere] all of the places I've tried hasn't done me any good. Either the screen is a little square in the center of my display or the entire desktop over-laps the screen and the corners are cut out.

I'm running an Nvidia GeFarce 6600GT [hehe gefarce]
The Monitor is a Sceptre X32GV Komodo

Here's a chunk of my xorg.conf:
> 
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	# 
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Boardname	"nv"
	Busid		"PCI:1:0:0" # uh... it's an agp card, not sure if this is a problem
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	# 
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"NvAGP"	"3"
	Option		"NoLogo"	"1"
	Option		"RenderAccel"	"1"
	Option		"TVStandard"	"HD720p" # It's capable of 1080i, but it don't like that mode
	Option		"TVOverScan"	"1.0"
	Option		"UseDisplayDevice"	"DFP"
	Option		"FlatPanelProperties"	"Scaling = native, Dithering = enabled" # thought this would help adding it in hehe guess not :P
	Option		"AddARGBGLXVisuals"	"1" # same with this one
	SubSection "Display"
		Depth	24
		Virtual	1280	768 # changing this didnt help Tried switching this to atleast 1024x768... nothing 
		Modes		"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection
#now it's just mocking me, I get a new one each time I boot up
Section "device" # 
	Identifier	"device2"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection


Any info would be appreciated, thanks in advance :)

---

### Post by erfahren on 2007-12-20
the OP on this thread was having a similar issue with the monitor and the xorg.conf - [http://ubuntuforums.org/showthread.php?t=641939&page=5](http://ubuntuforums.org/showthread.php?t=641939&page=5)
he got it a little better and posted what he did.



[SIZE="1"][9/11 wasn't an inside job](http://www.loosechangeguide.com/LooseChangeGuide.html)[/SIZE]

---

### Post by Dr.Gonzo on 2007-12-20
Hehe, first Im running an Nvidiot card and you linked me to ATI related material... Totally irrelevant... I've already tried the method of popping in the different display modes, as outlined in the post I was linked to. I have already tried that method and nothing. Ubuntu says "no". By taking out things like the "modelines", the "virtual" and the "modes" and replacing the info in the manner as presented in what you linked me to. I'll  reboot and the funky nintendo glitch screen comes back, follwoed by the recovery program where ubuntu attempts to re-detect my video card and monitor. Back to square one I go. After envy does it's thing... my screen is black and blue I managed to get the color back by specifying 720p in the xorg.conf file, I access by typing "sudo gedit /etc/X11/xorg.conf" Good thing I posted my xorg in my original post, so a little copy/pasting helped me recover from the disinfo I was passed.

My manufacturer has zero support in this OS, and I am on my own in that matter. Is there any "hi-def" guides out there. I feel that my video card is as configured as it is going to get, and since my monitor has no linux support, that could be an explanation for the "modelines" and "Virtual" settings that gets inputted automatically when I am forced to go through the recovery process. So I'm back to the really small screen or the over-sized display area. Sorry bro the info didn't help and was somewhat disinforming.

Oh yea... as the old saying goes, if we do not learn from history, then we're doomed to repeat it. Only a knowledgeable and well-informed citizenship can help fight the rise of misplaced power. adolf hitler burned his own parliment building and used it as an excuse to start WWII. Try to find a "viewers guide" to the Nuremburg trials, where that stuff is admitted, also how they used propaganda to manipulate the people. The United States has based it's foreign policy on an event where over 70% of the questions asked by the victims were not addressed by the commission. I lost a friend in that incident! We have a president and vice president who refused to testify under oath in public regarding the matter. Afghani ambassadors stated to congress that if the we provide proof  The level of failure that has occured denotes a level of complicity, I am not stating that the government pulled it off alone, but whoever did it got a helping hand from inside. The same people who worked the rubble in the wake of the attacks are suffering major health problems now due to the toxic air they were told was safe to breathe, and they're not getting any help from the government who promised to help. Bottom line... many people are demanding a new investigation and the media doesn't want to talk about it. Oh yea... and Pearl Harbor was investigated MULTIPLE times with public inquiry. 

But that is not the main point of this post... hehe I did not mean to raise any arguement in that area, but to seek some guidance on getting my monitor to work correctly using Component Video. But now you mention it I will be sure to ask what "rm -rf" does if told to type something like that.

---

### Post by Dr.Gonzo on 2007-12-20
> Afghani ambassadors stated to congress that if the we provide proof

To complete that sentence, if we provided proof that Bin Landen in fact did it, they would turn him over no questions asked. Look at the FBI's website for Bin Laden, to date he still hasn't been officially charged with the crime[s] of 9/11

---

### Post by erfahren on 2007-12-20
I posted that link not because of the video card specifically, but because he was having monitor related issues, mainly that it wasn't getting configured correctly in xorg.conf. 

your problem seemed *similar*, that's all. Sometimes the fix for similar problem can give a helpful clue, in my experience at least. (and I did mention that the issue was similar).

I also posted a couple links to a couple resolution related howtos in [this post](http://ubuntuforums.org/showpost.php?p=3964430&postcount=35) that I thought might help. ... so I just linked to the whole thread.

Did you make a backup copy of the xorg.conf (that works halfway decently) so you can just restore it by the command line in recovery mode if needed? (You mentioned needing to copy & paste what you had here and needing to do the dpkg-reconfigure xserver-xorg again - I think that's what you meant by "recovery program where ubuntu attempts to re-detect my video card and monitor.) - that way you could try different things and not go through the reconfiguring everytime. -- just a thought, maybe you already started doing that.

---

### Post by erfahren on 2007-12-20
let's not get into the 9/11 thing here. the mods won't like it. thats what the "Backyard" subforum is for

---

### Post by erfahren on 2007-12-20
oh, the rm -rf thing in my signature is in regards to a problem that was going on here awhile back with rogue posters getting people to type in malicious commands into the terminal. It's kind of gone away now, but alot of members have something similar to that in their sigs to help inform people.

(in case you're wondering, I have my pc's specs there to show what I have Ubuntu Feisty working on - didn't have much luck with Gutsy, darned suspend problems with my card - lol !)

welcome to the forums, btw.

---

