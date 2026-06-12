---
title: "Voodoo3 Problems"
date: 2005-11-26
forum: Multimedia &amp; Video
---

### Post by sopwithcamel on 2005-11-26
I am very new to linux. In fact I have only had it successfully loaded for 24 hours. I tried Ubuntu and it wouldn't load. All of the error messages pointed to my voodoo3 card. I thought by some weird chance, that Kubuntu might load and it did. Everything is working pretty well from the network to the file system with the exception of the display. I can only get 2 resolutions. 640 X 480 and 320 X 240. I am not concerned with getting the 3d gaming functionality out of this card, but I would like to use a higher resolution. I am using a ViewSonic 19" LCD monitor. I don't know where to start. Do I modify the xorg.conf file? If so, com someone with a voodoo3 card post a snapshot of a working xorg.conf file? Do I load drivers? If so which drivers? It looks like I can choose between xfree86 and glibc. Thanks in advance for any help you can provide. This forum looks like a great place for new users like myself to get some help.

---

### Post by nystire on 2005-11-26
By default the drivers for the Voodoo series of video cards are not built into X.Org. If you want to use them, you'll have to rebuild X yourself :( Not an easy option. I've been trying to get my Voodoo3 3500 to work, but it looks like I'll have to rebuild most of the OS for that. Sorry.

---

### Post by sopwithcamel on 2005-11-26
Thanks. Anyone have any suggestions for a cheap video card to buy that will work with Kubuntu/Ubuntu?

---

### Post by nystire on 2005-11-26
Go for any of the lower end NVidia or ATI cards. Just make sure you don't grab the newest and the best unless you wish to become a near-permanent denizen of these forums. If you can find an ATI Radeon 9000, 2D/3D are supported by the built-in 'radeon' driver which comes with Ubuntu. The newer cards will require you to install the proprietary driver from their web-site.
I'm not really sure about the NVidia drivers, as so far I have only had ATI cards, but from all the comments in these forums they are also supposed to be rather well supported.

You can also try looking here [http://doc.gwos.org/index.php/VideoCard](http://doc.gwos.org/index.php/VideoCard) or try searching these forums for cards to avoid.

---

### Post by Athlon2 on 2005-11-28
[QUOTE=sopwithcamel]I am very new to linux. In fact I have only had it successfully loaded for 24 hours. I tried Ubuntu and it wouldn't load. All of the error messages pointed to my voodoo3 card. I thought by some weird chance, that Kubuntu might load and it did. Everything is working pretty well from the network to the file system with the exception of the display. I can only get 2 resolutions. 640 X 480 and 320 X 240. I am not concerned with getting the 3d gaming functionality out of this card, but I would like to use a higher resolution. I am using a ViewSonic 19" LCD monitor. I don't know where to start. Do I modify the xorg.conf file? If so, com someone with a voodoo3 card post a snapshot of a working xorg.conf file? Do I load drivers? If so which drivers? It looks like I can choose between xfree86 and glibc. Thanks in advance for any help you can provide. This forum looks like a great place for new users like myself to get some help.[/QUOTE]

You will have to reconfig X
Back up your xorg.conf file  ( in /etc/X11 )
Write down info about your keyboard, mouse and especially your video card.
Voodoo3 cards come with 16MB memory I believe . Enter 16bit color if it asks.
Reconfigure x with
sudo dpkg-reconfigure xserver-xorg

---

### Post by peterx2 on 2005-11-28
[QUOTE=sopwithcamel]Thanks. Anyone have any suggestions for a cheap video card to buy that will work with Kubuntu/Ubuntu?[/QUOTE]

I have been horseing with a radeon 9200se and have pulled it because I dont want to mess with the driver fglrx.. You have to recompile some of the kernel..

The math appears to work out that a 16 meg card is sufficient for most displays.
linux.com has a list of cards/drivers, and most of the older cards will work ok.
pete

---

### Post by Ogrosticlops on 2005-11-28
Edited Post.

Original Poster, Since I got off of my lazy ass and decided to actually dig and work at things, I found that the problem was simply a question of not having the proper vert and horiz. sync ranges for the monitor I was using at that time.. I suggest you look up the stats of your current monitor, and find the correct rates. Open a terminal, sudo or su yourself with the text editor of your choice ( I prefer vi), edit /etc/X11/Xorg.conf , update the values and reboot. problem solved. do note that i'm using a Voodoo3 2000, on an HP mx70 monitor i bought years ago, but i'm up at 1024x768, 16bit color depth with no problems whatsoever. hope I at least helped.

---

### Post by IPR on 2005-12-02
Just installed U 5.1 on old system with Voodoo3 card (16MB). Was detected OK, jut needed to edit the xorg.conf to adjust the screen resolution (set at 60 originally). Now happily running at 1600 x 1200 and 106/84 hz (Mitsubishi 2070 CRT)

Note this is a PCI card, below pleas see relevant section of the .conf file:

-------------------

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-140
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---------------

Best of luck

---

### Post by qrazi on 2005-12-03
i run a voodoo5. it got recognized without problems, up till the max resolution my monitor supports (1024*768). I did use dpgk-reconfigure xserv-xorg command, but that was because i upgraded this box from hoary with a savage4 card to breezy with this voodoo5.

What doesnt work however is 3d accelleration. The voodoo line of cards should be more then enough to run the quake 1/2/3 series, but i cant even run glxgears properly. 

I tried installing DRI drivers, but that didnt work. Anyone have voodoo 3/4/5 cards with accelleration working in Breezy?

/edit: I found a gentoo guide for getting hardware acceleration with x.org. [http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)
but i dont know how to translate it to ubuntu. anyone?

---

### Post by qrazi on 2005-12-05
i am working my way through the DRI CVS building.

when i apply the buildtools.patch it asks where the file is. What file do i need to patch? i have no idea which file...

---

### Post by maritimer on 2005-12-18
Hi, I have similar problems with a Voodoo 3. I think it is a 3000.

I have edited my xorg.conf to remove all reference to resolutions below 1024X768 and yet everytime I boot I only have 2 options (640X480 & 320X???). I also commented out every bit depth except 16.

RIght now my xorg.conf file looks like this

Section "Device"
        Identifier      "3Dfx Interactive, Inc. Voodoo 3"
        Driver          "tdfx"
        BusID           "PCI:1:0:0"
EndSection

It says the card is on the PCI bus but it is an AGP card.

Section "Monitor"
        Identifier      "E771-4"
        Option          "DPMS"
#       HorizSync       30-70
        VertRefresh     50-120
EndSection

The horizontal sync did not work even though I got it straight from my monitors site.  Maybe it should be in kHz.

Section "Screen"
        Identifier      "Default Screen"
        Device          "3Dfx Interactive, Inc. Voodoo 3"
        Monitor         "E771-4"
        DefaultDepth    16
#       SubSection "Display"
#               Depth           1
#               Modes           "1280x1024" "1152x864" "1024x768" "832x624"
 "800x600" "720x400" "640x480"
#       EndSubSection
#       SubSection "Display"
#               Depth           4
#               Modes           "1280x1024" "1152x864" "1024x768" "832x624"
 "800x600" "720x400" "640x480"
#       EndSubSection
#       SubSection "Display"
#               Depth           8
#               Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
#       EndSubSection
#       SubSection "Display"
#               Depth           15
#               Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
#       EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
#       SubSection "Display"
#               Depth           24
#               Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600"
#       EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection


Any help is greatly appreciated.
Thanks,
Jason

---

