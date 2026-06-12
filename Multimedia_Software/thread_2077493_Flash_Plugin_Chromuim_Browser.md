---
title: "Flash Plugin Chromuim Browser"
date: 2012-10-28
forum: Multimedia Software
---

### Post by Ajay Ramaseshan on 2012-10-28
Hello,

I am trying out Lubuntu 12.04 32 bit on my machine and I was trying to see if Youtube videos work. It says on the top of the page, that Additional Plugins are required to see the content of the webpage, but the video plays perfectly, without any hanging / freezing.. however I notice that the old Youtube interface appears.

But some Youtube videos dont play at all and request me to install Flash Plugin 11.2 from the Adobe site, there I am given choices for Linux APT for Ubuntu 10.04+ I thought that this was Lubuntu lighter Ubuntu so I clicked it, but clicking it just opens a new chromium Window, that s it, no plugin gets installed, 

And the other formats like tar,gz and rpm dont work either, I tred downloading the tar.gz and in that there was a file libflashplayer.so I double clicked on it, but it says no program can open the file..

Could someone please help me out ?

---

### Post by Ajay Ramaseshan on 2012-10-28
I reloaded the page a couple of times, and now it seems to work. So I will mark this thread solved once I install Lubuntu 12.10 on my laptop i was trying from the Live Usb till now...

---

### Post by howefield on 2012-10-28
Try placing the libflashplayer.so file in your ~/.mozilla/plugins folder.

---

### Post by Ajay Ramaseshan on 2012-11-04
I did not do anything, I installed Lubuntu 12.10 on my computer and the Flash Plugin works perfectly for Chromium Web Browser. However, the new Youtube interface does not appear. I wonder if it has been removed, or it is not working with my Flash Plugin.

---

### Post by TenPlus1 on 2012-11-06
Since Google's new PepperFlash player 11.4 library works with Chromium, how about adding that to the repo and giving users the latest version of the flash library that fixes many bugs with hardware acceleration and full screen HD playback :)

---

### Post by deeinmetrodc on 2012-11-09
Ten Plus, that would be suicide for fglrx users as the pepper flash does not work in full screen mode with the fglrx drivers.  I tried for a week and gave up.

Also, if you want to use the pepper flash driver, there are instructions here:  [http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html]("http://www.webupd8.org/2012/09/how-to-make-chromium-use-flash-player.html")

Best of luck to you.

---

### Post by TenPlus1 on 2012-11-09
Latest PepperFlash 11.5 was installed on my friends Lenovo q180 with AMD Radeon 6450 HD and seems to work ok with full screen YouTube vids, still not hardware accelerated but works...

---

### Post by deeinmetrodc on 2012-11-09
It will work without the fglrx drivers.  Using the fglrx drivers you can forget it.  The free drivers are no problem.  I haven't tried the 11.5, will give it a go.

---

### Post by monkeybrain2012 on 2012-11-09
> **TenPlus1 said:**
> Since Google's new PepperFlash player 11.4 library works with Chromium, how about adding that to the repo and giving users the latest version of the flash library that fixes many bugs with hardware acceleration and full screen HD playback :)

Then why not just use Chrome?


BTW, if you have problems only with Youtube you don't need flash. I use the script ViewTube.[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011)

It also works in Chrome/Chromium if you install an addon called Tampermonkey (which is the Chrome equivalent of greasemonkey) It uses totem or gecko-mediaplayer to play videos on some supported sites and it works a lot better than flash anyway and there are no flash headaches.

---

### Post by cwsnyder on 2012-11-09
Nobody mentioned it, but you may have been seeing youtube through the HTML5 interface rather than the Flash interface, which would explain the 'older' version of the site.

---

### Post by deeinmetrodc on 2012-11-09
Well, I tried it with the new pepper flash 11.5 and fglrx drivers catalyst 12.10 specificaly and got full screen video from youtube so i guess it's ok....


There are valid reason to use chromium vs chrome.  chromium is open source and doesn't have all the tracking features enabled that chrome uses is i would reckon most people's reason though.

I downloaded chrome from the dev channel, copied libpepflash.so to /opt/pepper-flash (a directory I created then edited my chromium launcher with the following

chromium-browser --ppapi-flash-path=/opt/pepper-flash/libpepflashplayer.so --ppapi-flash-version=11.5.31.101

to see what version of pepper flash your chrome is using type in chrome://plugins in your chrome browser, click on details on the far right and then scroll down to the flash section and look for the number.

The location is where you can find it if you want to copy it to another location or edit your chromium launcher like I did

Adobe Flash Player (2 files) - **Version: 11.5.31.101**
Shockwave Flash 11.5 r31
Name:	Shockwave Flash
Description:	Shockwave Flash 11.5 r31
Version:	11.5.31.101
**Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so**
Type:	PPAPI (out-of-process)
 	 Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	
.swf
application/futuresplash	FutureSplash Player	
.spl
Name:	Shockwave Flash
Version:	11.2 r202
Location:	/opt/mint-flashplugin-11/libflashplayer.so
Type:	NPAPI
 	 Disable

---

### Post by monkeybrain2012 on 2012-11-09
> **deeinmetrodc said:**
> 

There are valid reason to use chromium vs chrome.  chromium is open source and doesn't have all the tracking features enabled that chrome uses is i would reckon most people's reason though.




Those tracking features can be disabled. One of the things that make Chromium open source and Chrome not is pepper flash and some plugins, so if you are hacking chromium to install it it kind of defeat the purpose of using chromium, isn't it?

---

### Post by deeinmetrodc on 2012-11-09
Well, except that Adobe has abandoned flash development for linux.  Otherwise, I wouldn't bother with a hack.

---

