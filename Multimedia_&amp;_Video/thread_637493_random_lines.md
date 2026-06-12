---
title: "random lines"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by darkreaction on 2007-12-11
I dont know whats up with this but at seemingly random times 8 lines appear at the bottom right hand corner of my screen and theydont go away till i reboot. Its not really that big of a deal its just kinda annoying can anyone shed some light on this situation? I have an ATI radeon 1300 pro and the drivers are installed.  

a screen shot is attached.

---

### Post by darkreaction on 2007-12-11
Never mind the screen shot the lines don't show up on it thats weird.

---

### Post by Schalken on 2007-12-11
Perhaps it is because the lines are being drawn on the screen somewhere further down in the stack, like by the xorg server or by your graphics drivers or the graphics card itself, somwhere where the screenshot program wont be able to see it.

---

### Post by darkreaction on 2007-12-11
I don't think its the video card this has never happed on any other os's I use. Any suggestions on how to fix?

---

### Post by Bloged on 2007-12-11
I've got an almost identical problem on an ATI X1250 with the latest drivers from ATI.

I think I got it narrowed down to gFTP. They only appear when I have this program running. 

The bars itself change depending on the screen below it... Furthermore everything is drawn underneath them, except for the mousepointer.

Restarting the X-server removes the bars (4 in my case).

---

### Post by darkreaction on 2007-12-11
Ya the same thing except mine come up seemingly at random. also i get either four big lines or eight thinner lines either way its really irritating.

---

### Post by Bloged on 2007-12-12
I've installed FileZilla... to check if it's gFTP will post back the result ASAP.

I'm using XFCE by the way... maybe we can narrow it down just bij looking at the same programs running!

---

### Post by acoustibop on 2007-12-12
I've seen it as well.  Seems to happen when the card gets hot; maybe it's a warning built into the driver?

---

### Post by darkreaction on 2007-12-12
Hmm that might be true although wouldn't it just stay on after u restart the x server? cuz mine go away for a while after that. 
I am pretty sure mine just appear at random, whether I'm surfing the web or i start up Amarok it just happens whenever.

---

### Post by willie_wang on 2007-12-20
try adding the following line to your xorg.conf in the Device section, it worked for me:

```
	Option		"XAANoOffscreenPixmaps"	"true"
```

my Device section now looks like this:

```
Section "Device"
	Identifier	"aticonfig-Device[0]"
	Boardname	"ati"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"XAANoOffscreenPixmaps"	"true"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection
```

and ever since adding that line, i've had no more of those strange black bars :)

---

### Post by JayBachatero on 2007-12-24
Thanks for the fix.  I was getting ready to whipe out Ubuntu and reinstall everything and you saved me some time :).

---

