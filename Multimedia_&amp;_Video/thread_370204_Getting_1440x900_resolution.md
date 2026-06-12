---
title: "Getting 1440x900 resolution"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by Tadpole on 2007-02-25
I noticed that Ubuntu (gnome) does not come with out-of-box support for my 1440x900 widescreen monitor like my mac does, so my screen is stretched and painful to look at. I heard that you have to do something in the "/etc/X11/xorg.conf file" (I don't know where that is). Could anyone let me know how to do this - or preferably, what little utility will do it for me?

Thanks so much.

---

### Post by taurus on 2007-02-25
You need to install a driver for your graphic card first and what is it anyway?

---

### Post by Tadpole on 2007-02-25
I do not have a graphics card,,,I'm on a mac mini core solo, which has integrated intel graphics. I can get that resolution on Mac OSX, so I don't see why I can't with Ubuntu...

---

### Post by Aliarse on 2007-03-01
Sorry for the bump, but i too am having problems getting 1440x900 on my ubuntu.

I've already tried reconfiguring xserver (sudo dpkg-reconfigure xserver-xorg) to no avail. Then tried manually adding them to my xorg.conf, and still i dont get the option of 1440x900.

Im currently stuck using 1280x1024 and it doesnt look all that good, so any help would be appreciated. Im using a brand new LG Flatron 19" Widescreen and an old TNT2m64 (which supports resolutions up to 2000x something, well above what i need...

---

### Post by Aliarse on 2007-03-01
Anyone? Would really like to get this setup on its native res... :(

---

### Post by Aliarse on 2007-03-01
Well, after a couple of hours of searching via google, i found my fix. Posting this here for the guy/girl above, and for myself if i ever need it again.

In a terminal, type...

```
gtf 1440 900 75
``` Adjust these settings for the max your monitor can do.

You will get an output like this.
```
  # 1440x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 136.49 MHz
  Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync
```

Copy all of that, and paste it into your xorg.conf file (sudo gedit /etc/X11/xorg.conf), in the monitor section, save the file. Then Alt+F1, type ```
sudo /etc/init.d/gdm stop
``` then ```
sudo /etc/init.d/gdm start
``` and look in the screen resolution GUI for your new res. ;)

---

### Post by andou on 2007-03-03
I can't seem to get it to work for mine at 2560x1600 resolution with my 30" monitor.

I tried ```
gtf 2560 1600 60 
```

I'm wondering if you only need to put in the "modeline" line, or if the commented segment should be included.

---

### Post by ununtunewb on 2007-06-05
I am having trouble getting this to work also.  I am not sure that I am editing my xorg.conf file correctly. I modify the monitor section to :

Section "Monitor"
	Identifier	"L194WT"
	Option		"DPMS"
	 # 1400x900 @ 75.00 Hz (GTF) hsync: 70.50 kHz; pclk: 132.54 MHz
  Modeline "1400x900_75.00"  132.54  1400 1488 1640 1880  900 901 904 940  -HSync +Vsync
EndSection

Is that correct?
Also when I press Alt + F1, it just opens up my 'Applications' menu, but when I press Shift + Alt + F1, I get a dos screen where I type the stop & start command where it says shutting down gnome and then I log back in, but I am still in the same resolution.

Any more help would be greatly appreciated.
Thanks

---

### Post by Baka no Kami on 2007-06-05
You might want to try setting the 'HorizSync' and 'VertRefresh' settings in the monitor section of the conf file. Some resolutions didn't display right on my monitor. This info can be found in the tech specs for the monitor.  I also removed all resolution from the screen section except my desired res, 1024x768, and 800x600 as fallbacks incase the main resolution failed.

---

### Post by stillingen on 2007-06-06
I have the same issue with my Samsung Syncmaster 940BW, adding the output of gtf 1440 900 75 does not change anything. I running ATI X1300 using fglrx driver.

---

### Post by jonlink on 2007-06-17
That how-to doesn't really make things very clear, there is no place to just paste the output, also the "#" in front of it means it would be commented out.  But reading the comments I noticed you can regenerate that file using this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It will ask you to pick a video card and the resolutions you'd like to use.  I did have to reboot to make the new resolutions available, but I am now at 1440x900.  

However, there isn't any option to change the refresh rate.  I think for that you need to edit the xorg.conf file by hand.

I'm using the LG L196W, the LG website has it's h-resh & v-refresh on the website, so I edited the "monitor" section to read like this:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
EndSection
```

I'm about to reboot again and we'll see what happens.[-o<

EDIT:  no good, didn't do anything **also** it turns out if you edit "Generic Monitor" the computer goes crazy-bananas so don't do that.  It wasn't hard to fix, but it was scary at first.  (if bad things happen just boot up in recovery mode and either edit the file by hand or use the auto reconfigure thingy above)

EDIT 2:  Okay, first the computer only goes crazy if you don't change the identifier in both the "monitor" and "screen" sections.  Also, the line that you cut and paste goes into the "monitor" section.  I still can't get a 60Mhz refresh, but it's up to 56Mhz now.  Close enough I guess. I'm taking my ball and going home now

---

### Post by Tadpole on 2007-06-25
> **jonlink said:**
> That how-to doesn't really make things very clear, there is no place to just paste the output, also the "#" in front of it means it would be commented out.  But reading the comments I noticed you can regenerate that file using this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It will ask you to pick a video card and the resolutions you'd like to use.  I did have to reboot to make the new resolutions available, but I am now at 1440x900.  
Do you know what video card I should pick in the list of choices? I'm on an intel mac mini so I have Integrated Intel GMA 950 graphics.

Already tried manually adding Modeline to xorg.conf and restarted but that didn't work.

---

### Post by Killtown on 2007-06-27
> **Aliarse said:**
> 

Copy all of that, and paste it into your xorg.conf file (sudo gedit /etc/X11/xorg.conf), in the monitor section, save the file. Then Alt+F1
Alt+**F2**, not F1.

---

### Post by vgrisham on 2007-08-15
In case anyone is still hunting an answer to this, here it is (worked for me): [http://www.spickles.org/archives/2006/10/31/95/](http://www.spickles.org/archives/2006/10/31/95/)

---

### Post by crgee on 2007-09-05
> **Aliarse said:**
> ```
gtf 1440 900 75
```

Works fine with Ati Radeon 9100 and BenQ FP92Wa, using "ati" in xorg. Excellent. 
I spent 3 days trying to get it to work with no results before I found this. Thanks a lot :)

---

### Post by woodyk on 2007-09-21
I was having an issue like this with my mac mini and a Dell 2407WFP 24" monitor.  Ubuntu will try its best to determine the right settings for your monitor but is not alway correct.  Here is a simple set of instructions on getting the res you want, assuming that your hardware supports it and that the video card is already configured properly... :)
[U][I]
Note: The bold sections should be replaced with the settings for your monitor.[/I][/U]

**1) **Find the specifications for your monitors model number.  In my case I did a little bit of googling to find out the detailed specs on my monitor.  If you're lucky enough to have the manual then life will get a little bit easier.  There are three sections in particular that you want.
[LIST]
[*]Horizontal Scan Frequency (ex: **30** kHz to **81** kHz )
[*]Vertical Scan Frequency (ex: **56** Hz to **76** Hz )
[*]Optimal Resolution (ex: **1920** x **1200** @ **60** Hz)
[/LIST]
The spec sheet may contain other useful information so make sure you keep a copy of the info.

**2) **We now know that the optimal setting is **1920** x **1200** @ **60** Hz.  Simply run the following to obtain the "Modeline" for your xorg.conf.
[INDENT]gtf **1920** **1200** **60**[/INDENT]
The output should resemble this:
[INDENT]# 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz
Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync[/INDENT]

**3) **Now edit you're /etc/X11/xorg.conf.  Under the "Monitor" section modify the "HorizSync" and "VertRefresh" to match the specs that you obtained on your monitor.  Also add the "Modline" string you have from your gtf output.  Ex:
[INDENT]
Section "Monitor"
    Identifier        "Generic Monitor"
    Option            "DPMS"
    **HorizSync      30-81**
    **VertRefresh   56-76**
    **# 1920x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 193.16 MHz**
    **Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync**
EndSection
[/INDENT]
Under you're "Screen" section you will now need to add your specified "Modeline" res setting. Ex:
[INDENT]
Section "Screen"
    Identifier      "Default Screen"
    Device          "ATI Technologies, Inc. RV280 [Radeon 9200]"
    Monitor         "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes           **"1920x1200_60.00"** "1280x1024"
    EndSubSection
EndSection
[/INDENT]

I hope this helps...  Its a shame to loose so much desktop real estate to a bad monitor config. :)

---

### Post by gowger on 2007-09-25
Hi All,

I've used the previous posts to get my resolution set to better that what it was, thanks to all posters. I have a dell lcd monitor that follows the following spec:
 Section "Monitor"
    Identifier     "DELL E198WFP"
    Option "DPMS" "CalcAlgorithm"
    #Option         "DPMS"
    Option "CheckDesktopGeometry"
    HorizSync 30.0-83.0
    VertRefresh 56.0-76.0
    Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync
    DisplaySize     1440 900
EndSection

but unfortunately the resultant desktop is clipped on the top and bottom edge. It looks like the display is native resolution but the desktop area is bigger than 1440x900. It scrolls up and down when you push to the clipped edges.

Any ideas?

---

### Post by gowger on 2007-09-25
Actually I tried one last thing that did it.

The modes in Display are listedin order of preference. It looks like having a resolution after the wide one set the vertical to 1024, the largest vertical available. So all resolutions after the default must have BOTH dimensions smaller than the ones before. Not intuitive IMHO!

was:
SubSection     "Display"
        Depth       24
        Modes      "1440x900_60.00" "1280x1024" "800x600"
EndSubSection

now is:
SubSection     "Display"
        Depth       24
        Modes      "1440x900_60.00"
EndSubSection

---

### Post by speedup on 2007-10-04
Guyz,

I was able to make my Nvidia 8800 GTS and Samsung 940BW work with 1440x900 resoultion.

(Make sure you backup the xorg.conf before doing the following steps.

Steps:

1.  Make sure you've installed the latest driver for Nvidia drivers (I recommend use Envy to install your drivers)
2. After installing the drivers through Envy,  Go to Applications->system Tools->Nvidia XServer Settings
3. Go to Xserver Display Configuration option, select Auto for Resolution then click on Apply
4. Click on Save to X Configuration File then a pop-out window will come up
5. Click on Show preview button. It will show all the details for the X Configuration
6. Select all and copy the content.
7. open the terminal window, type sudo /etc/X11/xorg.conf
8. Highlight all the content and replaced it with the details copied from the Show preview of the Nvidia X Configuration.
9. Save it and reboot. It should be ok.

---

### Post by uncleclinto on 2007-10-08
> **woodyk said:**
> 

**1) **Find the specifications for your monitors model number.  In my case I did a little bit of googling to find out the detailed specs on my monitor.  If you're lucky enough to have the manual then life will get a little bit easier.  There are three sections in particular that you want.
[LIST]
[*]Horizontal Scan Frequency (ex: **30** kHz to **81** kHz )
[*]Vertical Scan Frequency (ex: **56** Hz to **76** Hz )
[*]Optimal Resolution (ex: **1920** x **1200** @ **60** Hz)
[/LIST]
The spec sheet may contain other useful information so make sure you keep a copy of the info.



woodyk,

Your post seems like it may be the answer to my two week connundrum.  I have a problem though.  The only spec sheet available for my Acer x191w monitor doesn't seem to have the above mentioned info.  Attached is the spec sheet that came with the monitor and that I keep finding online.

Is there a way to interpret what I need from page 11.  It has a resolution but nothing about Horizontal or Vertical Scan Frequency, not to mention @ ??Hz after the resolution.  Maybe because it's a European monitor?? Do they spec it differently? 

Any help would be much appreciated,
Clint

---

### Post by vgrisham on 2007-10-08
This past weekend, I installed Gutsy, and I thought I'd let everyone in this thread know that it automatically detected my widescreen monitor and set my resolution at 1440 x 900 without my having to do anything. It just worked; no configuration needed. :guitar:

---

### Post by tubasoldier on 2007-10-08
> **Killtown said:**
> Alt+**F2**, not F1.

Alt+F1 works. As does Alt-F2. So does Alt-F3. If your feeling like you need more command line logins you can go as far as Alt-F6. Crazy isnt it? Only when you reach Alt-F7 do you start making more graphical logins.

---

### Post by uncleclinto on 2007-10-09
> **vgrisham said:**
> This past weekend, I installed Gutsy, and I thought I'd let everyone in this thread know that it automatically detected my widescreen monitor and set my resolution at 1440 x 900 without my having to do anything. It just worked; no configuration needed. :guitar:

Awesome, when does Gutsy Studio come out??

---

### Post by zainka on 2007-10-09
HI

Got it work almost instantly... Youst had to recon that there is to many different version on how to press alt+f1 in this therad. For me, Pressing CL+ALT+F1 got me out of graphic mode and into etxt mode. Since command "sudo /etc/init.d/gdm stop" actually stops the GUI, running the command inside a normal terminal window will turn everything black. 

Also, as many has pointed out, one also need to edit the screen section as well. In despite of all this, the authors receipt for adding better resolution works youst fine.

Here is my relevant part of xorg.conf and how i got my wanted 1280x1024@75Hz resolution. Bold are the changes made by me, and saved, before i entered text mode (still ctrl+alt+F1 (or f1, f2, f3.... up to f6)). Youst one notification more, I had a bit hard time finding my xorg.conf file until it hit me that foldernames etcetra in linux is case sensitive, so folder /etc/**x**11 for example does not exist, but /etc/**X**11 does. This for the newbies arround here looking into this thread, as myself is.

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-**81**
	VertRefresh	43-**80**
[B]  	# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
  	Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV370 [Sapphire X550 Silent]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		**"1280x1024" **"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
[B]	SubSection "Display"
		Depth		32
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection[/B]
EndSection
```


breg
Vidar (Z)

---

### Post by vgrisham on 2007-10-09
> **uncleclinto said:**
> Awesome, when does Gutsy Studio come out??

It [looks]("https://wiki.ubuntu.com/UbuntuStudio") to be on the same schedule as Ubuntu/Kubuntu/Xubuntu, October 18th.

---

### Post by ATrentino on 2007-10-09
> **vgrisham said:**
> In case anyone is still hunting an answer to this, here it is (worked for me): [http://www.spickles.org/archives/2006/10/31/95/](http://www.spickles.org/archives/2006/10/31/95/)

Thanks, it worked for my HP dv9408nr with nVidia Geforce 6150 Go running Gutsy

---

### Post by lord_jagganath on 2007-10-09
HELP... I must have done something stupid to my /etc/X11/xorg.conf file... as now it just boots to a terminal ( as if using an old dos interface), and no gui in sight...  gui error...or some thing like that

---

### Post by zainka on 2007-10-10
I guess you could use pico editor to edit the xorg file from the terminal and to see if you have by accident deleted some lines etc. Atleast you should be able to delete the lines you have put into the xorg file to see if this helps. Remember to use sudo...

**sudo pico /etc/X11/xorg.conf**

PRIOR to this, why not try to start up the graphical interface manually by 

**sudo /etc/init.d/gdm start**

See if that helps

---

### Post by lord_jagganath on 2007-10-10
> 
PRIOR to this, why not try to start up the graphical interface manually by 

**sudo /etc/init.d/gdm start**

See if that helps

i have tried that and it says that there is an error starting the GUI... i will try to edit it some how... ( i have created another thread for it [HERE]("http://ubuntuforums.org/showthread.php?t=572088"))

---

### Post by jesnev on 2007-10-10
Sounds nice, but how?
I installed 7.04 and tried all hints described on the forum. Nothing works, still 1280*1024 on Samsung SyncMaster with 1440*900. hp dc7200 standard box. 

I upgraded to Gutsy, the problem still remains. 
In "System>Preferences>Screen resolution" I do not get the option 1440*900. 
 Has anyone any suggestion? The new screen works perfectly in Vista, but would distaste that solution.
/jesnev

---

### Post by jesnev on 2007-10-10
(Question to post #21)
Sounds nice, but how?
I installed 7.04 and tried all hints described on the forum. Nothing works, still 1280*1024 on Samsung SyncMaster with 1440*900. hp dc7200 standard box. 

I upgraded to Gutsy, the problem still remains. 
In "System>Preferences>Screen resolution" I do not get the option 1440*900. 
 Has anyone any suggestion? The new screen works perfectly in Vista, but would distaste that solution.
/jesnev

---

### Post by vgrisham on 2007-10-10
> **lord_jagganath said:**
> HELP... I must have done something stupid to my /etc/X11/xorg.conf file... as now it just boots to a terminal ( as if using an old dos interface), and no gui in sight...  gui error...or some thing like that

at your terminal prompt, code:
sudo dpkg-reconfigure -phigh xserver-xorg

That command command will allow you to reset the contents of the xorg.conf file.

---

### Post by vgrisham on 2007-10-10
> **jesnev said:**
> (Question to post #21)
Sounds nice, but how?
I installed 7.04 and tried all hints described on the forum. Nothing works, still 1280*1024 on Samsung SyncMaster with 1440*900. hp dc7200 standard box. 

I upgraded to Gutsy, the problem still remains. 
In "System>Preferences>Screen resolution" I do not get the option 1440*900. 
 Has anyone any suggestion? The new screen works perfectly in Vista, but would distaste that solution.
/jesnev

Logoff and choose a terminal session. At your terminal prompt, code:

sudo dpkg-reconfigure -phigh xserver-xorg 

Tell it what kind of graphics card you have and choose defaults for everything. Choose your screen resolution. This has never let me down.

---

### Post by jesnev on 2007-10-18
I upgraded to 7.10.
The problem remains, it is impossible to get 1440*900. 
I kicked out my 7 year old 1024*768 monitor, I really miss it now. 
WHY is so &#*------*+&%¤#" hard to fix it? 

Vista had no problem whatsoever. Widescreen and 1440*900 is quite common now, isn't it?

Added after some frustrating moments
ctr-alt-f1 and gdm stop
sudo dpkg-reconfigure xserver-xorg
...
...
after quite many screens I had the only option 1440*900 @100Hz

save and gdm start
hear the drums,... and wait for the screen to burn

heureka! It works! 100Hz never was any option before, strange. 

Now its time to start using 7.10

---

### Post by kevingillan on 2008-02-06
Hi

Thanks for the various tips. I've followed all the instructions that make sense and still can't get the monitor working properly. I can get and select the 1440x900 option but when I do, although the actual resolution and ratio look fine, the colours have darkened and become inconsistent and there's a fuzzy, flickering bar at the left side of the screen, and the whole screen is shifted to the right so, e.g., you can't see the log out icon in the top right corner.

Any hints gratefully experimented with. System details following...

Relevant bits of /etc/X11/xorg.conf
```

Section "Device"
	Identifier	"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL193W"
	Horizsync	30-81
	Vertrefresh	55-76
	# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82946GZ/GL Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
	Depth	24
	Modes "1440x900_60.00" "1280x768"	
	EndSubSection
EndSection

```

I'm running Gutsy AMD_64 version on a home built computer including:
Asus P5B-MX motherboard with integrated intel graphics - 946GZ with GMA X3000
Core 2 Duo E4500  CPU
Acer 193W widescreen monitor

Cheers

---

