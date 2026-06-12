---
title: "S-video to TV Problems"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Rileymd on 2007-11-29
Okay so I want to know if it's possible to set up my TV as a clone via an svideo cable in Linux...It works fine whenever I boot into Windows but not Linux, could someone guide me through how to get it working? I'm using Ubuntu 7.10 with an nVidia Geforce 7600gt Video Card connected to a tv via an svideo cable. Thanks!

---

### Post by Ripfox on 2007-11-29
+1

---

### Post by Rileymd on 2007-11-29
What does that mean?

---

### Post by Ripfox on 2007-12-13
It means I need the answer to that too!

---

### Post by Ripfox on 2007-12-13
I used nvidia-settings from the terminal and it worked in my case.

---

### Post by fenian on 2007-12-13
First install the Nvidia driver.You  can do that from the menu System>Administration>Restricted Drivers Manager.
Restart the computer and in a terminal type...
> 
sudo nvidia-settings

Under  X Server Display configuration click the TV icon then click the configure button.You will have 3 oprtions...
1-Disable=disables display
2-Seperate X screen=sets TV up as independent screen(you can perform different tasks on each screen,i.e:watch video on TV while surfing the web on the main monitor.
3-Twinview=either clones the desktop on the TV or stretches the desktop across both screens.
After you choose the option you want click the Save X Configuration File button.Restart X for changes to take effect (ctrl+alt+backspace).

---

### Post by Greenskycity on 2007-12-13
I was having the same problem and found this in another thread.  here is my xorg.conf file and I added all the lines with the option ahead of them and it worked for me.  hopefully it'll work for you too.  Don't forget to backup you original just in case.

```
Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7300 GT]"
	Driver		"nvidia"
	Busid		"PCI:5:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
[COLOR="Yellow"][COLOR="Blue"]Option "TwinView" "true"
Option "TwinViewOrientation" "Clone"
Option "TVOutFormat" "S-VIDEO"
Option "TVStandard" "NTSC-M"
Option "SecondMonitorHorizSync" "30-50"
Option "SecondMonitorVertRefresh" "60"
Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;  512x384,512x384"[/COLOR][/COLOR]
EndSection
```

---

### Post by mocha on 2007-12-13
Does clone mode only work with the Gutsy version of the proprietary nvidia drivers?  I tried to do clone mode before with the Fiesty version and never got it to work.

---

### Post by gumpontheweb on 2007-12-14
First let me say how I don't understand most of this. I just switched from vista after getting fed up with blue screens! So Far I think this is faster, but I dont know how to do anything!
My Newer digital widescreen TV just pugged & played in the s-video of my compaq. I Think my graphics card is an intel 945. 
When I first plugged it in it was a duplicate of the LCD (theLaptop). 
Now it's one or the other? I would like that back, HOW?
I just tried connecting it to my Old School 3:4 tube television's s-video. All I got was a rolling flickering picture. I thought it had something to do with the refresh rate so i googled and found a line to put in the terminal. I only know how to do that from watching my buddy set this up.
I set up the "compiz config setting manager" and changed the refresh rate to 60 with no effect.. I couldn't believe I got that far!
When I boot with the S-video cable connected to the old TV, it starts the LCD but it doesn't fill the screen. The laptop screen is 16:9, like the New TV. When the old tv is connected it seems like it wants to go 3:4 and JUST WORK, but it doesn't! I really think it is the refresh rate but I have NO Clue on what else to do.
1.  Can I watch movies on the old TV?    
2.  Can I have the laptop screen be on and be a duplicate(or its own) on the new TV, the way it worked the first time ?:confused:

---

### Post by lowebb on 2007-12-14
[http://ubuntuforums.org/showthread.php?t=98456](http://ubuntuforums.org/showthread.php?t=98456)

P.S. My experience of S-video (not restricted to Ubuntu) is pathetic. I think the quality is awful. I'm buying a 25" monitor rather than outting to a TV

---

### Post by sfielder on 2007-12-19
I am having a big problem with my svideo connection. My hardware thinks the svideo cable is plugged in all the time. gutsy on dell e1405 laptop w/ intel 945gm card. very weird. I have also posted  with a long description on this thread: [ http://ubuntuforums.org/showthread.php?t=64291]("http://ubuntuforums.org/showthread.php?t=642913") I can't find any info in this so any help would be greatly appreciated.

thanks

sam

---

