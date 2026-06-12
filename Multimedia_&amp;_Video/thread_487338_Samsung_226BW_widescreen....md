---
title: "Samsung 226BW widescreen..."
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by jpross81 on 2007-06-28
I just got a Samsung 226BW widescreen monitor for my ubuntu desktop.  I am having trouble getting ubuntu to use the native resolution of the monitor (1680x1050).  I know this resolution is possible with this hardware configuration b/c everything works fine when I boot into windows rather then ubuntu...

my video card is the "Intel Corporation 82915G/GV/910GL Integrated Graphics Controller" and I have installed the "915resolution fix".  I changed one of the modes to use the 1680x1050, restarted, and the new mode appeared in the resolution options, but when I select it the screen is blurry as if the resolution is not correct. (the text looks crappy) and the bottom menu bar is not displayed on the screen.  

it seams that other people are having the same type of problems I am having but I have not found any solutions to work with my setup.  

How can I fix this?

---

### Post by jpross81 on 2007-06-30
I have been searching all over the net and found this command...

```
sudo aptitude install xserver-xorg-video-intel
```

this enables 1680x1050, 1280x1024, 1280x960, 1152x864, 1024x768, 832x624, 800x600, and 1680x1680 resolutions for my setup.  However, when I apply one of the widesreen resolutions such as 1680x1050 the text that does show is not blurry but, the edges of the screen "run off the monitor" as if it is being displayed, but the  monitor screen size is too small.

---

### Post by tablanon on 2007-07-04
same exact problem here

i used the sudo aptitude install xserver-xorg-video-intel to get 1680x1050, but when i pick that resolution the image is only about 80% the width of the screen. When i move the resolution down to 1400px wide it spans the entire width of the screen though.

Any ideas?

---

### Post by speirint on 2007-07-31
Wow, same thing here, the screen resolution should be 1680:1050, but that resolution is unavailable for me as well in the screen resolution preferences.  Is there any way I can go in and make 1680:1050 a new option?

Okay, I haven't tried this out yet, but this looks like it could be the answer:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

You'll have to get into the terminal, and it is a lot of stuff to do if you're new, but if you can find a buddy you trust that's got some existing know-how, it shouldn't be too bad.  I'll give it a try soon and let you guys know what happens.

---

### Post by speirint on 2007-08-18
My computer figured it out already, I don't recall exactly what I did, I believe I typed one command in to install some additional dimensions and the computer figured out the monitor without me having to do any of the work listed on the previous post's hyperlink.

---

### Post by syphodias on 2007-08-21
You HAVE to remember!!! Same problem.... :'(

---

### Post by jpross81 on 2007-08-24
Well it is two months later and I still cannot find a solution anywhere for my problem.  I am leaning towards getting a new video card at this point.  I am starting to think that there is no one that has ever gotten this setup working.

---

### Post by jpross81 on 2007-08-24
If anyone has any suggestions, please send them this way.

---

### Post by technx on 2007-08-25
I have a samsung 226bw running on feisty, I don't remeber the steps exactly, but I think all you need to do is have you xorg.conf file correctly setup before you can properly choose the 1680x1050 setting using the System->Preferences->Screen Resolution app.

you can open the file by typing

```
sudo gedit /etc/X11/xorg.conf
```

Here is what the section involving my monitor settings look like.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
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
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

Since you are using a different video card, please disregard the ATI stuff.

Go through your xorg.conf file and try to add in any missing resolutions.. I think the area near the bottom where it says ```
SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
```
may be the key to getting it working. Hope this helps

---

### Post by jpross81 on 2007-08-26
when I put the monitor specific settings in my xorg along with the vert./horiz. refresh rates and some other information I was able to have the option for 1680x1050 but when set to that resolution I would get the sides running of the monitor, I think its called overscan.  

I finally just decided to get rid of the dell POS and use the scraps to build a new machine with a nvidia 8800 gt video card and an asus motherboard.  My problem now is to get ubuntu to recognize all the new hardware so that I dont have to do a clean install.  

p.s. thanks for the quick reply technx

---

### Post by kellemes on 2007-08-26
I got a 225BW working fine actually..

---

### Post by technx on 2007-08-26
Happy to help, its a bummer that you weren't able to get it working, if you have any issues once you get your new equipment, feel free to ask any other questions or request any other settings.

---

### Post by speirint on 2007-11-12
Hey Jpross, if you still have that monitor and got it working-and haven't upgraded to gutsy yet, don't do it. I have the same problems all over again and now there are no other posts that I know of that mention this issue.

I tried using the (which is what successfully made the initial correction for my monitor in feisty earlier):

sudo aptitude install xserver-xorg-video-intel

again and it doesn't work in Gutsy, someone must not have configured the right resolution for 
Gah!  As an aside, my sound still doesn't work right... Gah!

---

### Post by trappist on 2007-11-14
The solution here (after days and days of trying everything on the internets) was to "downgrade" to the i810 driver.  From there, I don't know if it worked out of the box or if the stuff I'd done with 915resolution and so on did it, but I definitely didn't make any progress with the "intel" driver.

---

### Post by speirint on 2007-11-14
> **trappist said:**
> The solution here (after days and days of trying everything on the internets) was to "downgrade" to the i810 driver.  From there, I don't know if it worked out of the box or if the stuff I'd done with 915resolution and so on did it, but I definitely didn't make any progress with the "intel" driver.

Alright, I'm giving it a shot. I reinserted this:

> sudo aptitude install xserver-xorg-video-intel
but replaced intel with i810 instead.

Upon hitting enter, the computer installed a bunch of stuff, but I haven't seen anything new yet in the resolutions for monitor and graphics and resolution. I'll be rebooting, and if that doesn't work, I'll treat myself to some off-the-cd mepis for the night(while the screen resolution might look wierd still, it was surprisingly very easy to use right away, and I even had streaming audio!). Thanks trappist.

Before restarting, I just referred back to technx's post and typed in the xorg conf. stuff to see my monitor stats (for lack of a better description and word). It has indeed changed from the older versions, and there are many new values that I have absolutely no idea what they mean. Here's what it shows:

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 226BW (Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1280x1024@75"	"1280x960@60"	"1152x864@75"	"1280x1024@60"	"1024x768@60"	"1280x960@75"	"1024x768@70"	"1400x1050@60"	"1024x768@75"	"1600x1200@65"	"832x624@75"	"1600x1200@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection


Lo and behold, our resolution is not on the list yet... now to figure out what everything else means as well as what's going on...

---

### Post by ZAKhan on 2007-12-04
Can somone please help, I am struggling here.... the screen resolution is not correct and then on top of it the sound comes and goes too..

Thanks

---

### Post by ken_vh on 2007-12-10
I had the same problem and after a lot of searching, I found out that I just installed the screen wrong.

I was already able to do this the standard way:
- Install the nvidia restricted driver (the one that is called "nvidia" in the graphics card driver list)
- Setting the monitor to some standard resolution (eg. 1280x768 )

This tutorial is asuming that you have managed to do this too.
This is what I had to do to make my screen get into 1680x1050 mode:

- Go to System->Adminstration->Screens and graphics
- Make sure that "graphics card" is still correct (and that it isn't "generic something"). In my case it was "nvidia"
- Click on the screen model, so you get a list of screens
- Find "Samsung" -> "SyncMaster 226" AND (this is the important part!) click on "Widescreen monitor" so you can get the 1680x1050 screen resolution later!
- Select 1280x768
- Press okay (don't use test first!)
- Reboot (don't log off!)

Now you're rebooted with the correct driver and the correct screen in 1280x768 mode.
Now open a console and type:
sudo nvidia-settings

Now go to the screen resolution settings:
- select 1680x1050
- test, and on succes:
- click the button to write the xorg.conf file.

That's it! Now reboot(don't log off first) and enjoy your screen :)

---

### Post by btmartin on 2008-01-17
another satisfied customer...

---

### Post by speirint on 2008-02-28
Thanks for the guide ken_vh, I have a question about integrated graphic cards and whether or not I should be using terminal as my console.

I've followed your suggested steps, and tried several variations of what I thought my graphics card would read as.  Looking under screens and graphics at the graphics card portion, I saw:

[IMG]http://farm4.static.flickr.com/3195/2297805419_76a4d9c455.jpg?v=0[/IMG]

and subsequently tried various ways of writing in my percieved graphic card, even tried pretending that I had an nvidia...:

___@primo:~$ sudo intel-settings
[sudo] password for ___:
sudo: intel-settings: command not found
___@primo:~$ sudo intel 865-settings
sudo: intel: command not found
___@primo:~$ sudo intel865-settings
sudo: intel865-settings: command not found
___@primo:~$ sudo nvidia-settings
sudo: nvidia-settings: command not found
___@primo:~$ sudo intel 865-settings
sudo: intel: command not found

Am I doing something wrong or not understanding what my graphic card is actually called?

---

### Post by taikonaut on 2008-05-02
I didn't succeed with the i810 driver so I installed 'Intel Experimental'.

Then I didn't use 'Samsung SyncMaster 226bw' but a simple 'LCD Panel 1680*1050 (widescreen)'.

Since then, it works!

Regards,
Taiko

---

### Post by BobSongs on 2008-05-06
[SIZE=3][COLOR=Gray]**hardware**[/COLOR][/SIZE]
[B]AMD Athlon XP Processor
512 Mb RAM[/B]
Monitor: **Samsung SyncMaster 206bw**
Graphics Card: **nVidia nforce 6800 LE 128 Mb RAM**

[COLOR=Gray]**[SIZE=3]steps to making the graphics card & monitor work together[/SIZE]**[/COLOR]

[LIST]
[*]Installed **EnvyNG** via **Synaptic Package Manager**.
[*]Installed **NVIDIA driver** through **EnvyNG**. Selected the Manual install and selected driver version number 169.12 (the driver version number for Windows XP at the time of writing is 169.21).
[/LIST]
[SIZE=3][COLOR=Gray]**result**[/COLOR][/SIZE]
The screen resolution **dropped** to a choice of two: **640x480** or **320x240**. Not exactly optimal.

[LIST]
[*] Pressing on I searched this forum and found a quote pointing to this command:
[/LIST]
 ```
sudo dpkg-reconfigure xserver-xorg
```
[LIST]
[*]I logged out of my account.
[*]I went to a full-screen command prompt by using **Ctrl**+**Alt**+**F1** and logged in.
[*] I shut down the GNOME Display Manager (**gdm**) using this command:
[/LIST]
 ```
sudo /etc/init.d/gdm stop
```
[LIST]
[*]Once **gdm** stopped I issued the **dpkg-reconfigure xserver-xorg** command.
[*]I answered many questions about keyboards. No questions were asked about screen resolutions or graphics cards.
[*]When the wizard finished its questions I was dropped to the command prompt. I noted that it saved a new copy of **/etc/X11/xorg.conf**. I had a feeling I was on the right track.
[*]I reactivated **gdm** by issuing this command:
[/LIST]
```
sudo /etc/init.d/gdm start
```
[LIST]
[*]X-Windows was **unable to start in full graphics mode**. The screen flickered a few times. Then a new wizard started. It asked what video card/monitor I was using.
[*]I selected the monitor, its resolution and made sure the **nvidia** driver (and not the **nv** driver) was selected.
[*]With the settings "accepted" and saved X-Windows started again. This time I came to a login screen with a resolution that was** greater than 1680x1050**. **One more tweak required.**
[*]I returned to the command prompt (**Ctrl+Alt+F1**) and stopped **gdm **again.
[*]I made a back-up copy of the **/etc/X11/xorg.conf** file.
[*]I then edited the file using **nano**:
[/LIST]
```
nano /etc/X11/xorg.conf
```
[LIST]
[*]I scrolled down the file and came across a long list of screen resolutions that resembled this one:
[/LIST]
> modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
[LIST]
[*]The last one was greater than 1680x1050@60 ... I knew this was causing the problem. So I removed that line and saved the file.
[*]I restarted **gdm** and the login screen's resolution was correct.
[*]I tweaked my own login's resolution up to 1680x1050 and am working with an optimized screen.
[/LIST]
Hope this helps.

---

