---
title: "Advice for building a Mythbuntu box"
date: 2008-09-14
forum: Mythbuntu
---

### Post by thconsof on 2008-09-14
Hello!

i despise vista and only tolerate XP, so being that vista will soon be my only option, i have decided to finally switch over to Ubuntu fully and completely!
i am running 8.04 on my desktop when i noticed i have the option to install Mythbuntu.

I'd like to build a box specifically for Mythbuntu.
Cause i can do that, i have enough parts, albeit they are old...
if i build a new (old) box these will be the specs

**Motherboard**
CPU Type  	
Intel Celeron, 700 MHz (10.5 x 67)
Motherboard Name  	
ECS P6IWP-Fe (2 PCI, 2 DIMM, Audio, Video, LAN,)
Motherboard Chipset  	
Intel Whitney i810E
System Memory  	
512 MB (SDRAM)
OnBoard Display
Intel(R) 82810E Graphics Controller 32 MB
3D Accelerator  	
Intel i752
OnBoard Multimedia Audio Adapter  	
C-Media CMI8738 Audio Chip
OnBoard Network Adapter  	
Realtek RTL8139 Family PCI Fast Ethernet NIC
HD 
Western Digital Corporation 50GB IDE

I have a PNY GeForce FX 5200 DDR 256MB PCI card i could add.
I have 3 older PCI Creative Sound Cards as well.

There are only 2 PCI slots, and i have 2 Analog TVcard MPEG2 encoder tuners in my "junk" parts pile.

The first which i believe to be a hardware MPEG encoder.
But the specs of the card are questionable at best.
The card itself is marked Sony 1-860-696-22ENX-26 AOI on the board.
The chip is marked Conexant MPEG II A/V encoder CX23416-12.
Everest identifies it as a 
Conexant (Internext Compression) iTVC16/CX23416 MPEG Codec.
DriverAgent Windows hardware identifier for PCI\VEN_4444&DEV_0016&SUBSYS_813D104D&REV_01 identifies it as a Sony MPEG RealTime encoder board. 
It has CableTV in with both composite video and audio (R,W,Y) as well as a S-Video.

The second is what i believe to be software MPEG encoder.
The card itself is marked Hauppauge WinTV NTSC 44801 Rev D182 on the board.
The chip is marked Conexant Fusion 878A 25878-13.
Everest identifies it as a BrookTree WinTV PAL B-G.
DriverAgent Windows hardware identifier for PCI\VEN_109E&DEV_036E&SUBSYS_13EB0070&REV_11  identifies it as a WinTV PAL B-G [Hauppauge Computer Works Inc].
It has CableTV in with composite video (Y) and line in/line out for audio.

Would either of these work with Mythbuntu, and which would you recommend?

And finally, can i use my TV as a monitor?
[http://www.bestbuy.com/site/olspage.jsp?skuId=8205952&type=product&id=1165610947263]("http://www.bestbuy.com/site/olspage.jsp?skuId=8205952&type=product&id=1165610947263")

thank you in advance for any help in this matter!

---

### Post by mrand on 2008-09-15
> **thconsof said:**
> Hello!

<...>
There are only 2 PCI slots, and i have 2 Analog TVcard MPEG2 encoder tuners in my "junk" parts pile.

The first which i believe to be a hardware MPEG encoder.
But the specs of the card are questionable at best.
The card itself is marked Sony 1-860-696-22ENX-26 AOI on the board.
The chip is marked Conexant MPEG II A/V encoder CX23416-12.
Everest identifies it as a 
Conexant (Internext Compression) iTVC16/CX23416 MPEG Codec.
DriverAgent Windows hardware identifier for PCI\VEN_4444&DEV_0016&SUBSYS_813D104D&REV_01 identifies it as a Sony MPEG RealTime encoder board. 
It has CableTV in with both composite video and audio (R,W,Y) as well as a S-Video.

The second is what i believe to be software MPEG encoder.
The card itself is marked Hauppauge WinTV NTSC 44801 Rev D182 on the board.
The chip is marked Conexant Fusion 878A 25878-13.
Everest identifies it as a BrookTree WinTV PAL B-G.
DriverAgent Windows hardware identifier for PCI\VEN_109E&DEV_036E&SUBSYS_13EB0070&REV_11  identifies it as a WinTV PAL B-G [Hauppauge Computer Works Inc].
It has CableTV in with composite video (Y) and line in/line out for audio.

Would either of these work with Mythbuntu, and which would you recommend?

And finally, can i use my TV as a monitor?
[http://www.bestbuy.com/site/olspage.jsp?skuId=8205952&type=product&id=1165610947263]("http://www.bestbuy.com/site/olspage.jsp?skuId=8205952&type=product&id=1165610947263")

thank you in advance for any help in this matter!

My experience is that using a SDTV as a monitor doesn't work well.. the resolution isn't high enough to read a lot of text unless it is set to be annoyingly large.

As for your cards:

The iTVC16 / CX23416 looks to be [supported]("http://google.com/search?q=iTVC16+OR+CX23416+mythtv+OR+mythbuntu") by Linux.  In fact, the Hauppauge [website]("http://www.hauppauge.com/Pages/faq/support_faq_linux.html") says as much.

The Fusion 878A is a frame grabber.  Almost certainly not what you want with such a low horsepower CPU - it wouldn't be able to keep up with compressing the stream.

Have fun,

[INDENT]   Marc[/INDENT]

---

### Post by tgm4883 on 2008-09-15
Using your TV as a TV monitor is fine, don't plan on using it for browsing the internet though.

---

### Post by dougsnell on 2008-09-15
First, check some of your hardware against a database of known devices ([http://pvrhw.goldfish.org/tiki-pvrhwdb.php](http://pvrhw.goldfish.org/tiki-pvrhwdb.php)).  In particular, the graphics card gives me pause.  The hard drive is likely far too small ... although it will work, you won't get much in the way of storage on it.

The other two replies to this also seem valid, but I can't speak from experience on them.

As for horsepower, you don't need much.  Decent cards can off-load the vast majority of work (though framegrabbers do suck cycles).

---

### Post by thconsof on 2008-09-16
> **mrand said:**
> 
As for your cards:

The iTVC16 / CX23416 looks to be [supported]("http://google.com/search?q=iTVC16+OR+CX23416+mythtv+OR+mythbuntu") by Linux.  In fact, the Hauppauge [website]("http://www.hauppauge.com/Pages/faq/support_faq_linux.html") says as much.

[INDENT]   Marc[/INDENT]

guess this is where that card becomes a head scratcher. it clearly says sony on it. but the iTVC16/CX23416 chip keeps popping up on google as various hauppauge cards.
after googling, i managed to use it on WXP with a driver from sony and TotalMedia was the only windows-based software would recognize it easily and play decently.
i was hoping mythbuntu might recognize for what it is?

> **dougsnell said:**
> First, check some of your hardware against a database of known devices ([http://pvrhw.goldfish.org/tiki-pvrhwdb.php](http://pvrhw.goldfish.org/tiki-pvrhwdb.php)). 

i did do that. nothing for the first card under sony, iTVC16, CX23416, Conexant MPEG II or any other variation.

for the second card, there were some successful winTv-go insalations, even with the onboard video and audio.

but that seems like the least advantageous of the 2 cards...

but i'm appreciating all the feedback. i have tomorrow off and am just going to load Mythbuntu with both cards onboard and see what happens! not much to loose? right?

---

### Post by mrand on 2008-09-17
> **thconsof said:**
> guess this is where that card becomes a head scratcher. it clearly says sony on it. but the iTVC16/CX23416 chip keeps popping up on google as various hauppauge cards.
after googling, i managed to use it on WXP with a driver from sony and TotalMedia was the only windows-based software would recognize it easily and play decently.
i was hoping mythbuntu might recognize for what it is?
<...>
 i have tomorrow off and am just going to load Mythbuntu with both cards onboard and see what happens! not much to loose? right? Right!

BTW, I'm unclear what you are scratching your head about.  Linux doesn't really care that Sony made the card.  It cares about what chip(s) are on the card.

Good luck,

[INDENT]Marc[/INDENT]

---

### Post by Eric Boring on 2008-09-19
I just built a box on a similar old machine. (766 Celeron).

If you have some money to spend, I'd suggest making sure that the video encoding and decoding all happens on the card. I'm using the Hauppauge 350 for both, and it works great. 

You'll need to hunt around to get X to go out through the PVR350's TV out, but I don't think it's very hard. What I did was use a config that only used the TV out (no monitor for X). Then I enables SSH and I ssh in from cygqin or another ubuntu box when I need to work on the myth box. 

Let me know if you'd like me to post the config file I wound up using.

---

### Post by MarcG on 2008-09-27
I'd like to see that config. I've got a PVR-250. I've been able to display on the TV, but can't get anything that fits on the screen. MythTV's menus take up the entire screen, so most of the menu picks are off-screen and I have to hunt blind to get to them.

--Marc

---

### Post by Eric Boring on 2008-09-28
> **MarcG said:**
> I'd like to see that config. I've got a PVR-250. I've been able to display on the TV, but can't get anything that fits on the screen. MythTV's menus take up the entire screen, so most of the menu picks are off-screen and I have to hunt blind to get to them.

--Marc

Here is the config I'm using. I can't for the life of me findthe page where I found it. But it sends X to the TV and turns off the VGA port completely.

```
Section "Files"
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

# Specific modules needed *this is important.*
Section "Module"
	Load		"dbe"
	Load		"v4l"
	Load		"extmod"
	Load		"type1"
	Load		"freetype"
EndSection

# Almost standard keyboard 
# Note: This setup doesn't require the keyboard to be present

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

# Almost standard mouse pointer
# Note: This setup doesn't require the mouse to be present

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Hauppauge PVR 350 iTVC15 Framebuffer"
	
	# the driver we installed - in Gutsy, this is NOT "ivtvdev".
	Driver		"ivtv"
	
	# frame buffer we found above
	Option		"fbdev"	"/dev/fb0"
	Option		"TVStandard"	"NTSC-M"
	Option		"VideoOverlay"	"on"
	Option		"XVideo"	"1"
	
	# below settings are optional I've seen lots of people with them commented out.
	# I believe that pal users should just comment below line out.
	
	# Not optional setting
	# BusID we found with lspci converted as shown above
	Busid		"PCI:01:09:0"
	
	Screen	0
	
EndSection

# these settings are generic (for TVs) but are specifically for TV

Section "Monitor"
	Identifier	"TV"
	Horizsync	30-68
	Vertrefresh	50-120
	Displaysize	183	122
  Mode "720x480"
		Dotclock	34.564
		Htimings	720	752	840	928
		Vtimings	480	484	488	504
		Flags		"-HSync"	"-VSync"
  EndMode
	
	
	# for pal users:
	#Section "Monitor"
	#       Identifier  "TV"
	#       HorizSync  30-68
	#       VertRefresh 50-120
	#       Mode "720x576"
	#       D: 41.475 MHz, H: 44.693 kHz, V: 74.488 Hz
	#       DotClock 41.476
	#       HTimings 720 752 840 928
	#       VTimings 576 580 584 600
	#       Flags    "-HSync" "-VSync"
	#       EndMode
	#EndSection
	#for pal users more settings: http://www.mythtv.org/wiki/index.php/XV_on_PVR-350#PAL 
	
	# Sorry SECAM users I don't have the codes for that but I did see them on the web
	# So seek and you will find.  There are some resources at the bottom of this 
	# webpage to help out.
	
EndSection


# Our PVR-350 Driver entry
Section "Screen"
	Identifier	"TV Screen"
	Device		"Hauppauge PVR 350 iTVC15 Framebuffer"
	Monitor		"TV"
	Defaultdepth	24
	Defaultfbbpp	32
	SubSection "Display"
		Depth	24
		Fbbpp	32
		Modes		"720x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "TV Screen"
	
	# There is other ways to get rid of keyboard and mouse, but you can these settings as is.
	# This setup is designed to run without keyboard and mouse plugged in.
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666#	Not	specifically	needed	as	far	as	I	know.
	# I think it's specific to my computer's hardware
	# That said all my ubuntu boxes have this line.
	
EndSection
```

There is some info here about resizing the Myth UI to fit your TV screen better. [http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#Displaying_X_on_the_PVR-350_video_output](http://www.mythtv.org/wiki/index.php/Hauppauge_PVR-350#Displaying_X_on_the_PVR-350_video_output). This is for the 350, so it might be of limited use to you.

Finally, may I recommend this excellent posting (ahem) on getting -X to display on Windows using ssh and cygwin. [http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html](http://blog.lib.umn.edu/welsh059/blog/2008/09/x_on_windows_you_bet_1.html).

 I've found this very useful for maintaining my mythbox from my XP laptop. Of course, if you are all Ubuntu all the time, then you can just install ssh on both sides and run 
```
ssh -X [user]@[host]
```
where [user] is your user account on the mythbox and [host] is the name or ip of the box itself. Have fun. And if you find that blog useful, leave a comment (It's my first how to post)

-Josh

---

### Post by MarcG on 2008-09-28
Thanks, Josh. I'm going to give that a try. We're all Ubuntu here, so ssh works fine.

Related to that, would it make sense to just ssh in to the Myth box and play/record movies from there, in addition to maintenance? Will it play on the TV while I control from the safety and comfort of my easy-chair?

--Marc

---

### Post by Eric Boring on 2008-09-28
> **MarcG said:**
> 
Related to that, would it make sense to just ssh in to the Myth box and play/record movies from there, in addition to maintenance? Will it play on the TV while I control from the safety and comfort of my easy-chair?

--Marc
No, when you SSH in it doesn't change what happens on the TV screen. It's like you have two different user sessions going from the same machine. You could use VNC instead. When I've played around with that on other machines, I could see the mouse moving on the screen of the host machine while I controlled it from the client. Mythbuntu-control-centre has a nice option for installing VNC as well. 
I like to go with SSH because VNC seems to export the sub-optimal desktop dimensions that are sending -X to the TV out. SSH seems to size the window in such a way that it makes it sense on the client machine. When I'd use VNC, I could never see the buttons at the bottoms of the windows, which are in many respects, the most important ones ;).

For controlling the mythbox, you'll probably do fine with something like the Streamzap remote. Myth8.04 seems to just recognize it when you select in the the MCC. Very simple to get working, Are you needing to control a set-top box as well?  CommandIR mini worked great for me for that. But it's another 100 bucks. But then, as I told my brother: doing a cost-benefit analysis of a project like this is what we call "Wrong Thinking." I don't know why I wanted to built this thing, but it sure wasn't to save money.

-Josh

---

### Post by MarcG on 2008-09-29
> **Eric Boring said:**
> No, when you SSH in it doesn't change what happens on the TV screen. It's like you have two different user sessions going from the same machine. You could use VNC instead. 


But if I'm SSH'ed in to the MythTV box and run Myth from the laptop, wouldn't anything related to the tuner card, specifically RF_in and video_out, still go through the tuner card? I would set it up so that the MythTV box doesn't run MythTV on power-up, so there would be no competing sessions.

Or do I have the whole structure wrong in my mind?

--Marc

---

### Post by Eric Boring on 2008-09-29
> **MarcG said:**
> But if I'm SSH'ed in to the MythTV box and run Myth from the laptop, wouldn't anything related to the tuner card, specifically RF_in and video_out, still go through the tuner card? I would set it up so that the MythTV box doesn't run MythTV on power-up, so there would be no competing sessions.

Or do I have the whole structure wrong in my mind?

--Marc

Well, this was such an intriguing idea I had to try it! You are right. If I ssh into the mythbox and launch mythfrontend, I can select Watch TV and it plays on the TV. Same for watching recordings. The menu navigation takes place on the client machine, which sounds like just what you want. The menus responded excruciatingly slowly for me, but you may have more luck if your myth box is a little faster. Let me know how it turns out!

-Josh

---

### Post by MarcG on 2008-09-29
> **Eric Boring said:**
> Well, this was such an intriguing idea I had to try it! You are right. If I ssh into the mythbox and launch mythfrontend, I can select Watch TV and it plays on the TV. Same for watching recordings. The menu navigation takes place on the client machine, which sounds like just what you want. The menus responded excruciatingly slowly for me, but you may have more luck if your myth box is a little faster. Let me know how it turns out!

-Josh

That's cool :D That really is the way to go for me. Now I can't wait to try it! I'm going out tonight and won't have a chance, but I've gotta give it a whirl tomorrow. And if that works out, the only thing left to work on is the :popcorn:

Thanks for trying it out.

---

### Post by SoFingFrustrated on 2008-09-30
> **thconsof said:**
> Hello!

i despise vista and only tolerate XP, so being that vista will soon be my only option, i have decided to finally switch over to Ubuntu fully and completely!
i am running 8.04 on my desktop when i noticed i have the option to install Mythbuntu.

I'd like to build a box specifically for Mythbuntu.


thank you in advance for any help in this matter!

Good luck.  I built a system with everypart linux/ubuntu/myth friendly. Wasted one month  on the Piece of Sh!t. If you get it to work, go buy a lottery ticket

---

### Post by SiHa on 2008-09-30
> Good luck. I built a system with everypart linux/ubuntu/myth friendly. Wasted one month on the Piece of Sh!t. If you get it to work, go buy a lottery ticket
One month?
You give up easily don't you? Took me a month just to get the remote working.
3 months in and I'm nearly there:D

---

### Post by Eric Boring on 2008-09-30
> **SiHa said:**
> One month?
You give up easily don't you? Took me a month just to get the remote working.
3 months in and I'm nearly there:D

Ha! I think I started my myth box in April. Finally got it working at the end of August. Not that I worked on it every day. I even put it away for awhile because i was getting frustrated. But the dream kept calling me back. ...

---

### Post by DemonBob on 2008-09-30
> **SoFingFrustrated said:**
> Good luck.  I built a system with everypart linux/ubuntu/myth friendly. Wasted one month  on the Piece of Sh!t. If you get it to work, go buy a lottery ticket

Took me two days. Have you considered starting your own post in mythbuntu forums, and listing your issues.

---

### Post by tgm4883 on 2008-09-30
> Posts: 3

Ask for help if you need it.   Don't Troll

---

### Post by MarcG on 2008-10-01
> **Eric Boring said:**
> Well, this was such an intriguing idea I had to try it! You are right. If I ssh into the mythbox and launch mythfrontend, I can select Watch TV and it plays on the TV. Same for watching recordings. The menu navigation takes place on the client machine, which sounds like just what you want. The menus responded excruciatingly slowly for me, but you may have more luck if your myth box is a little faster. Let me know how it turns out!

-Josh

Well, I had mixed results. One problem is that, many moons ago when I started this project, I assumed that TV capture cards also had a TV out. Without going into the definition of "ASSUME", I was wrong. My PVR-250MCE has tons of inputs, but no output. When I first tried this I used the S-video output of the system. So I need to figure out how to redirect the output when I SSH in to the system video instead of my remote.

My other problem is the screen I get from mythtvfrontend when I SSH in is a little bigger than my physical screen. Mostly just the "BACK""NEXT" buttons are below where I can see them, but that's not too bad. I'll take a look at the link above to resize that.

--Marc

---

### Post by Eric Boring on 2008-10-01
That's a bummer. I messed around with the xorg.conf for S-video on a laptop a while back. I have to admit I was disappointed with the results. I hate to suggest throwing more money into the myth, but the 350 is a great card, which takes care of encoding and decoding. 

I've tried getting mp2 acceleration to work on another low-power box, and I threw my hands up in frustration. 

Regarding the screen size of the frontend when you SSH in, I really wish I knew what I was doing with that ssh thing. The whole reason I recommend it is that it resizes things to fit the screen so nicely (or so I thought).

Anyways, good luck. I don't know how I got so obsessed with this project. I didn't even own a tv a year ago! But I love my myth system now. It's well worth the blood sweat and tears when it's all over. 

-Josh

---

### Post by MarcG on 2008-10-02
I'm thinking the 350 is probably the best way, too. I might even be able to eBay the 250 and only be out 20 bucks or so.

Thanks.

--Marc

---

