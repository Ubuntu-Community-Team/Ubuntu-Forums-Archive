---
title: "tv tunner help"
date: 2009-11-23
forum: Multimedia Software
---

### Post by pokethesmot on 2009-11-23
i just got my KWORLD PlusTV Analog Lite PCI TV Tuner Capture Card w/ Remote PVR-TV 7134SE PCI Interface i read the reviews and it said it works in linux and i did everything it said in the write ups but still nothing it recognizes the card in mythtv but it dose not identify a cable input and i tried in it tvtime and it recognizes the card but it says no signal

---

### Post by pokethesmot on 2009-11-23
oh yeah and now when i use mythtv to try and watch tv through the tunner it looks like its loading then it says please wait and it closes out and goes back to the main menu here are my specs by the way 

[COLOR=Lime]CPU:[/COLOR][COLOR=Red]core 2 duo3.2ghz[/COLOR]
[COLOR=Lime]PSU:[/COLOR][COLOR=Blue]420w[/COLOR]
[COLOR=Lime]GPU:[/COLOR][COLOR=Blue]ATI radeon 2600 xt[/COLOR]
[COLOR=Lime]Mobo:[/COLOR] [COLOR=Red]Biostar tp43d2-a7[/COLOR]
[COLOR=Lime]Case:[/COLOR] [COLOR=Blue]alien ware case[/COLOR]
[COLOR=Lime]speakers:[/COLOR] [COLOR=Blue]5 surround sound speakers and 2 12inch subs[/COLOR]
[COLOR=Lime]Display:[/COLOR] [COLOR=Blue]dell flat screen[/COLOR]
[COLOR=Lime]Hard Drives:[/COLOR][COLOR=Blue] western digital 200gb[/COLOR]
[COLOR=Lime]OS:[/COLOR][COLOR=Blue]Ubuntu 9.10[/COLOR]
[COLOR=Lime]RAM[/COLOR][COLOR=Blue]5.8gigs[/COLOR] 			
 		 		  		  		  	   	 		 [IMG]http://www.computerforum.com/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://www.computerforum.com/images/buttons/report.gif[/IMG]]("http://www.computerforum.com/report.php?p=1363183") 		 		  	 	 	 	 		 		 			[IMG]http://www.computerforum.com/images/misc/progress.gif[/IMG] 			[[IMG]http://www.computerforum.com/images/buttons/edit.gif[/IMG]]("http://www.computerforum.com/editpost.php?do=editpost&p=1363183")

---

### Post by lovinglinux on 2009-11-23
This is what I did to make my Pinnacle PCTV card work:

[http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)

It is also analog, so I guess you will just have to find out your card numbers.

MythTV didn't work for me, but TVTime does. Because of this, I ended up developing [my own media center]("http://fmc.isgreat.org"), which is a Firefox extension.

---

### Post by pokethesmot on 2009-11-23
> **lovinglinux said:**
> This is what I did to make my Pinnacle PCTV card work:

[http://ubuntuforums.org/showpost.php?p=5971890&postcount=2](http://ubuntuforums.org/showpost.php?p=5971890&postcount=2)

It is also analog, so I guess you will just have to find out your card numbers.

MythTV didn't work for me, but TVTime does. Because of this, I ended up developing [my own media center]("http://fmc.isgreat.org"), which is a Firefox extension. i did what u said and my card is recognized but in tvtime is says no signal and mythtv just says please wait and then goes back to the main menu

---

### Post by lovinglinux on 2009-11-23
> **pokethesmot said:**
> i did what u said and my card is recognized but in tvtime is says no signal and mythtv just says please wait and then goes back to the main menu

Did you reboot after running the commands?

Reboot and try a new channel scan.

If that doesn't work, connect a DVD player, a video camera or a VCR in the A/V entry, change TVTime input configuration to Composite-1 and check if you get an image. If yes, then it's probably just a channel scan issue. Don't forget to change the input back to television before scanning again.

---

### Post by pokethesmot on 2009-11-23
[quote=lovinglinux;8375724]Did you reboot after running the commands?

Reboot and try a new channel scan.

yeah i rebooted and ile try using my n64 in the composite input...i hate to say this but if this dont work ima end up having to go back to windows...and i really dont wanna do that

---

### Post by lovinglinux on 2009-11-24
> **pokethesmot said:**
> yeah i rebooted and ile try using my n64 in the composite input...i hate to say this but if this dont work ima end up having to go back to windows...and i really dont wanna do that

Don't give up. I almost did the same thing because of the TV card, but I never had a problem once I was able to configure it properly. Besides, the TV image is better on Linux than when I was using Windows.

Extract the contents of the attached zip file into ~/.tvtime

See if that works.

PS: Did you use the correct card and tuner numbers for your TV card model?

---

### Post by pokethesmot on 2009-11-24
> **lovinglinux said:**
> Don't give up. I almost did the same thing because of the TV card, but I never had a problem once I was able to configure it properly. Besides, the TV image is better on Linux than when I was using Windows.

Extract the contents of the attached zip file into ~/.tvtime

See if that works.

PS: Did you use the correct card and tuner numbers for your TV card model?
thank you so much it worked i tried the n64 one more time and it came up and the problem with the cable coming up is i got digital cable i joined this sight just to get this answer but i think i might stick around

---

### Post by lovinglinux on 2009-11-24
> **pokethesmot said:**
> thank you so much it worked i tried the n64 one more time and it came up and the problem with the cable coming up is i got digital cable i joined this sight just to get this answer but i think i might stick around

Welcome to the Ubuntu forums community. The support from other users here is great. You won't regret it.

---

