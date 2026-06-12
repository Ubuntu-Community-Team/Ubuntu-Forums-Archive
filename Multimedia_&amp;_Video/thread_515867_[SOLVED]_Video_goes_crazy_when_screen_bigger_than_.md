---
title: "[SOLVED] Video goes crazy when screen bigger than 1024x768"
date: 2007-08-02
forum: Multimedia &amp; Video
---

### Post by parameter on 2007-08-02
Hi.  I have a IBM Thinkpad T30 and I recently installed Ubuntu 7.04.  After the install my screen came up in 1024x768 which is smaller than the screen's native resolution.  I used the screen resolution preference program to switch to the native resolution of 1400x1050.  When I did that, the screen went a bit crazy.  It's a bit hard to explain.  I can still read things, but now there is some random garbage on the screen.  When I move a window, half or part of it will appear on the left side of the screen as well as the right.  Windows that were open before I changed resolution don't redraw properly, and only appear as I drag another window over them.

Here's a screenshot of what happens:
[[IMG]http://img392.imageshack.us/img392/5079/screenshotiy9.th.png[/IMG]](http://img392.imageshack.us/my.php?image=screenshotiy9.png)

Any ideas?  I don't know much about linux desktops so I don't even know where to begin to investigate the problem.  I'll also add that I have the same problem with the LiveCD, but I did not have this problem with the previous version of Ubuntu (6.10) when using it from a CD.

---

### Post by wolfen69 on 2007-08-02
have you tried 7.10? i know it's beta, but alot of people are using it without problems. or go back to 6.10.

---

### Post by parameter on 2007-08-02
I want to stick with the current stable release.  7.04 is the first Ubuntu I have tried that seems to have a chance of working for me most of the time.  The only problems that I've experience are this video problem and the inability to get my built-in wireless to work.  if I can fix those then I have a chance to start migrating away from Windows.  6.10 wouldn't allow me to play music from a Windows file share, so I can't use it since 100% of my music files are on my file server.

---

### Post by parameter on 2007-08-05
Anyone have any suggestions?  I don't know what I'm doing and I don't know where to start looking for answers.  I've searched on Google and other search engines and I've searched the forums, but I haven't come up with a solution.

---

### Post by buzzmandt on 2007-08-05
check defaultdept 24 in xorg.conf
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by parameter on 2007-08-06
I looked in the file and there was an entry that said DefaultDepth 24.  Is that what I should be looking for?  It was part of a larger section that said:

```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
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

```

---

### Post by parameter on 2007-08-09
What should I do next?

---

### Post by parameter on 2007-08-10
Buzzmandt, can you tell me what I need to do next?  Do I need to change a setting in /etc/X11/xorg.conf?

---

### Post by buzzmandt on 2007-08-12
sorry, i'm a truck driver and only get to surf every few days
and again sorry, i'm not sure what to check next

anyone else?

---

### Post by rhinst on 2007-08-22
Not sure if you're still having the problem, but I also have a ThinkPad T30 with the same video card and was having the same exact issue. After much googling, the solution turned out to be very simple.  Just add "1400x1050" as the first listed resolution under the 24-bit depth section.

So basically, where you had this in your config above:

```
 SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
 EndSubSection
```
```
 SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
 EndSubSection
```

Change it to this:

```
 SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1024x768" "800x600" "640x480"
 EndSubSection
```


Then you just need to restart your xserver (the quickest and easiest way is just by hitting CTRL+ALT+BACKSPACE)

Hope that helps

---

### Post by parameter on 2007-08-23
Thanks, rhinst.  That definitely fixed it! :)

---

