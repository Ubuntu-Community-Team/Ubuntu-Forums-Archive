---
title: "Fiesty Firefox .wmv streaming (embedded) totem issues"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by alexvd on 2007-05-11
Hi I have an issue that when I want to play a .wmv that plays from Firefox it downloads starts playing for 1 second then stops and goes black screen.  

I have tracked this down to totem-mozilla plugin issue.  
I have w32 codecs installed and I have gstreamer and totem mozilla installed and totem-xine completely removed.     

I dont want to bother installing vlc or mplayer. Yes I know they work but I had this working fine in dapper drake.  I also dont want to install the media player connectivity add-on.

I just want to try and fix because it simplifies upgrades and changes.  If I need to delete old plugins like totem  xine or gxine or anything else where do i delete those?  

Here are my plugins from about:plugins in firefox......

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Totem Web Browser Plugin 2.18.1

    File name: libtotem-basic-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes

QuickTime Plug-in 7.1.3

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.18.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
MozPlugger 1.7.3 handles QuickTime Windows Media Player Plugin

    File name: mozplugger.so
    MozPlugger version 1.7.3, written by Fredrik Hübinette <hubbe@hubbe.net> and Louis Bavoil <bavoil@cs.utah.edu>.
    For documentation on how to configure mozplugger, check the man page. (type man mozplugger)
    Configuration file:	/etc/mozpluggerrc
    Helper binary:	mozplugger-helper
    Controller binary:	mozplugger-controller
video/mpeg 	MPEG animation 	mpeg,mpg,mpe 	Yes
video/x-mpeg 	MPEG animation 	mpeg,mpg,mpe 	Yes
video/x-mpeg2 	MPEG2 animation 	mpv2,mp2ve 	Yes
video/mp4 	MPEG4 animation 	mp4 	Yes
video/msvideo 	AVI animation 	avi 	Yes
video/x-msvideo 	AVI animation 	avi 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
application/x-mplayer2 	Windows Media 	wmv,asf,mov 	Yes
video/x-ms-asf 	Windows Media 	asf,asx,wma,wax,wmv,wvx 	Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-quicktimeplayer 	Quicktime animation 	mov 	Yes
image/x-macpaint 	Quicktime animation 	pntg,mov 	Yes
video/quicktime 	Quicktime animation 	mov,qt 	Yes
video/x-quicktime 	Quicktime animation 	mov,qt 	Yes
video/x-theora 	OGG stream with video 	ogg 	Yes
video/theora 	OGG stream with video 	ogg 	Yes
video/ogg 	OGG stream with video 	ogg 	Yes
video/x-ogg 	OGG stream with video 	ogm,ogv 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
audio/x-mp3 	MPEG audio 	mp3 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/mpeg 	MPEG audio 	mpa,abs,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mpa,abs,mpega 	Yes
audio/x-ogg 	OGG audio 	ogg 	Yes
application/x-ogg 	OGG audio 	ogg 	Yes
application/ogg 	OGG audio 	ogg 	Yes
audio/basic 	Basic audio file 	au,snd 	Yes
audio/x-basic 	Basic audio file 	au,snd 	Yes
audio/wav 	Microsoft wave file 	wav 	Yes
audio/x-wav 	Microsoft wave file 	wav 	Yes
audio/x-pn-wav 	Microsoft wave file 	wav 	Yes
audio/x-pn-windows-acm 	Microsoft wave file 	wav 	Yes
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
audio/x-pn-realaudio 	Realaudio-plugin resource locator 	ra,rm,ram 	Yes
audio/x-realaudio 	RealAudio file 	ra,rm,ram 	Yes
application/vnd.rn-realmedia 	RealMedia file 	rm 	Yes
application/smil 	RealPlayer 	smi 	Yes
audio/vnd.rn-realaudio 	RealAudio file 	ra,ram 	Yes
audio/vnd.rn-realvideo 	RealVideo file 	rv 	Yes
audio/x-ms-wax 	Windows Media 	wax,wma 	Yes
image/sun-raster 	SUN raster image 	rs 	Yes
image/x-sun-raster 	SUN raster image 	rs 	Yes
image/x-rgb 	RGB Image 	rgb 	Yes
image/x-portable-pixmap 	PPM Image 	ppm 	Yes
image/x-portable-graymap 	PGM Image 	pgm 	Yes
image/x-portable-bitmap 	PBM Image 	pbm 	Yes
image/x-portable-anymap 	PBM Image 	pnm 	Yes
image/tiff 	TIFF image 	tiff,tif 	Yes
image/x-tiff 	TIFF image 	tiff,tif 	Yes
application/pdf 	PDF file 	pdf 	Yes
application/x-pdf 	PDF file 	pdf 	Yes
text/pdf 	PDF file 	pdf 	Yes
text/x-pdf 	PDF file 	pdf 	Yes
application/x-postscript 	PostScript file 	ps 	Yes
application/postscript 	PostScript file 	ps 	Yes
application/x-rtf 	Rich Text Format 	rtf 	Yes
application/rtf 	Rich Text Format 	rtf 	Yes
text/rtf 	Rich Text Format 	rtf 	Yes
application/x-msword 	Microsoft Word Document 	doc,dot 	Yes
application/msword 	Microsoft Word Document 	doc,dot 	Yes
application/vnd.ms-excel 	Microsoft Excel Document 	xls,xlb 	Yes
application/vnd.sun.xml.writer 	OpenOffice Writer 6.0 documents 	sxw 	Yes
application/so7_vnd.sun.xml.writer 	OpenOffice Writer 7.0 documents 	sxw 	Yes
application/vnd.sun.xml.writer.template 	OpenOffice Writer 6.0 templates 	stw 	Yes
application/vnd.sun.xml.writer.global 	OpenOffice Writer 6.0 global documents 	sxg 	Yes
application/vnd.stardivision.writer 	StarWriter 5.x documents 	sdw 	Yes
application/vnd.stardivision.writer-global 	StarWriter 5.x global documents 	sgl 	Yes
application/x-starwriter 	StarWriter 4.x documents 	sdw 	Yes
application/vnd.sun.xml.calc 	OpenOffice Calc 6.0 spreadsheets 	sxc 	Yes
application/so7_vnd.sun.xml.calc 	OpenOffice Calc 7.0 spreadsheets 	sxc 	Yes
application/vnd.sun.xml.calc.template 	OpenOffice Calc 6.0 templates 	stc 	Yes
application/vnd.stardivision.calc 	StarCalc 5.x spreadsheets 	sdc 	Yes
application/x-starcalc 	StarCalc 4.x spreadsheets 	sdc 	Yes
application/vnd.sun.xml.draw 	OpenOffice Draw 6.0 documents 	sxd 	Yes
application/so7_vnd.sun.xml.draw 	StarOffice Draw 7.0 documents 	sxc 	Yes
application/vnd.sun.xml.draw.template 	OpenOffice Draw 6.0 templates 	std 	Yes
application/vnd.stardivision.draw 	StarDraw 5.x documents 	sda 	Yes
application/x-stardraw 	StarDraw 4.x documents 	sda 	Yes
application/vnd.sun.xml.impress 	OpenOffice Impress 6.0 presentations 	sxi 	Yes
application/so7_vnd.sun.xml.impress 	StarOffice 7.0 Impress presentations 	sxi 	Yes
application/vnd.sun.xml.impress.template 	OpenOffice Impress 6.0 templates 	sti 	Yes
application/vnd.stardivision.impress 	StarImpress 5.x presentations 	sdd 	Yes
application/vnd.stardivision.impress-packed 	StarImpress Packed 5.x files 	sdp 	Yes
application/x-starimpress 	StarImpress 4.x presentations 	sdd 	Yes
application/vnd.ms-powerpoint 	PowerPoint Slideshow 	ppt 	Yes
application/mspowerpoint 	PowerPoint Slideshow 	ppt,ppz,pps,pot 	Yes
application/vnd.sun.xml.math 	OpenOffice Math 6.0 documents 	sxm 	Yes
application/so7_vnd.sun.xml.math 	StarOffice 7.0 Math documents 	sxm 	Yes
application/vnd.stardivision.math 	StarMath 5.x documents 	smf 	Yes
application/x-starmath 	StarMath 4.x documents 	smf 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.3.5 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes
Shockwave Flash

    File name: libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes
Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r68

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by spamking2000 on 2007-05-11
What you posted is pretty much how I have my Fedora machine setup, and it works just fine there. On the other hand, when I first got Ubuntu, I installed the mplayer-plugin through Automatix as one of the first things I did... so I don't have any experience with Totem-gstreamer or Totem-xine on Ubuntu.

My experience with it on Feodra was that once I used Mozplugger, things started working that weren't working before.... ie totem was picking up mms streams.

If you're getting a second of stream and then it stops, to me that almost sounds like more of a network issue than a plugin issue. To me, once it reaches the plug in, if it starts playing, I've never had it stop because of the application.

You might try this with you DNS settings... it definately sped up my response time to my internet connection. Go to System -> Administration -> Network, type in your password, select your ethernet NIC (assuming you're not using a modem or token ring) and go to the DNS tab. The top section will be a couple of IP addresses, probably for your internet service provider. Delete those and put in the address on your router. If you haven't customized it, the default will be either 192.168.1.1 or 192.168.1.0. Put which ever of those is right for you in (you can test by opening up those addresses in a browser window... the one that works and asks you for a password is your router) and hit close. 

Restart Firefox and try a stream... if it doesn't work, it may be quicker to just install MediaPlayerConnectivity and not futz with it.

Hope it works!
D

---

### Post by spamking2000 on 2007-05-11
Oh... just another thought... might be stupid, but check in your /usr/lib/firefox/plugins directory and make sure you have your libtotem-****.so and .xpt files in there that you have listed from mozplugger. I can't imaging mozplugger would write that if you didn't, but its worth checking... might as well make sure the microwave is plugged in before you try to turn it on.

---

### Post by alexvd on 2007-05-12
Hi thanks for the replies.  I should have specified that other streams work fine.  I can even stream what I think are probably different versions of wmv files. ie wmv9 or 10.  I am also using FIOS with a big fat Pipe so no problems with that.  One thing to note is that I couldn't get a bunch of avi,mpeg working so I used automatix and then everything worked but I started getting the issue with some wmv streaming files as described above.  

Are you sure I should change the DNS setting to my router gateway address?  I have never done that on any OS and I wonder if that would break browsing?

One question I had is it possible the plugin could be not pointing to the right player or something.  I did an upgrade from dapper to edgy to fiesty.  My machine is def a bit slower and has some crashes now so I wouldn't be suprised if somehow its misconfigured.

All the plugins seem to be in the right folder for Firefox.

---

### Post by alexvd on 2007-05-25
Hi anyone help with this?

---

### Post by erlingwl on 2007-05-27
I have the same problem. I can't find a solution anywhere either..

---

### Post by alexvd on 2007-05-27
So your issue is just embedded .wmv right.  I can download and play .wmv with totem or xine but not via the mozilla plugin via firefox.  Its odd because I can play embedded mpeg with no issues.  

Is it possible to open a terminal and tail firefox to see what is causing the problem.  

I didnt have this issue on Edgy.

---

### Post by alexvd on 2007-05-29
Any help with this is greatly appreciated.  

To further specify the behavior.  I see the totem movie player icon flash then for 1 second i get audio and video then black screen typically.    Somehow the plugin is conflicting or not installed properly.

---

### Post by alexvd on 2007-05-30
bump

---

### Post by alexvd on 2007-05-30
Can anyone suggest steps to troubleshoot???  Should I remove other plugines or players?

---

### Post by alexvd on 2007-05-30
I removed xine and vlc and the problem still exists.  Now whenever I have a wmv which used to open with xine firerfox gives me a open with dialog.  I select totem and check the box for do this from now on.  It plays no problem in totem but then i keep getting the open with dialog box.  I went into firefox, content and edit the wmv to open with totem however it does not stay.

This is driving me nuts

---

### Post by alexvd on 2007-05-31
This is really annoying can someone please post thier download actions from Firefox.  WMV is now pretty screwed up.

Please post if you are using totem

---

### Post by parimels on 2007-05-31
I have the exact same issue.

I subscribe to a streaming web site that does not allow URL access to the stream in a stand alone player.

I have been seriously evaluating to switching to Ubuntu as my primary OS. But this seems to be a show stopper (the wife will not live without windows video media)

I tried totem, gxine, mplayer but none of them work to replace the Windows experience.

All I use Ubuntu is to burn iso images to CD/DVD :)

---

