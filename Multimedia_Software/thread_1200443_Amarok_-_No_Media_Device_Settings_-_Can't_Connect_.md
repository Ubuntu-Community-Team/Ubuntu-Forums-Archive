---
title: "Amarok - No Media Device Settings - Can't Connect Device"
date: 2009-06-30
forum: Multimedia Software
---

### Post by rowp on 2009-06-30
I just bought a Create Zen Mozaic 4GB.

I have mpt-tools installed and i can connect with both mtp-detect, lsusb which both detect the device connected via usb.

Amarok 2:2.1.1** package installed, however when i go to:

tools -> configure amarok 

There is no 'devices' tab under the settings window.


--

The 'Media Devices' applet does not give any options to add a media device - just a blank gray screen, when right clicked gives me 'shortcut settings'.

--

From what i understand there should be a tab in the settings window to add a media device? Am i missing any packages?

---

### Post by trickstyhobbit on 2009-07-09
I'm in no way an expert but I was having the same problem with my ipod. But after looking around for the media devices menu I clicked on the collection tab on the left hand side of the main amarok screen and my ipod was already there. It's worth taking a look if you havn't already.

---

### Post by clickwir on 2009-08-02
Yea, is the "Devices" widget thingy broken? It shows nothing. At least tell me something. 

I get nothing. Normal click button, I get a grey area. That grey area accepts no input.  Alternate (right) clicking the button gives nothing.

Current track widget works. Lyrics... works. But tells me the website is having some BS from corporations. But the DEVICES.... nothing. 

It's just a thumb drive really, but I get the same issue with a Sansa. 

At least with Amarok 1.4 I could tell it what to do and how to handle it. It was a bit of trial and error, but it worked. This... big blank nothing.

---

### Post by fozzytbear on 2009-10-08
Did you ever manage to figure this out?  I am having the same problem.

I think it might have something to with the amarok package not being built with mtp or any media devices support.  Did you install amarok before installing MTP?  I did this and I think now no matter how many times I remove and reinstall amarok, it isn't configured with support for media devices.

I'm going to try building amarok from source, and see what happens.

---

### Post by itlarson on 2009-10-12
I have the same problem with my sansa fuze. In the past I have gotten a sansa view to work in mtp mode with amarok 1.4. and it would be convenient to use the fuze in mtp mode, so I could browse by id3 tag.  The "media devices" thing does nothing, though, and on line documentation is unhelpful at best.  Fortunately the fuze has the option to be set up as a standard usb storage device so I can access it through my file browser.    
    I just have to take a minute to rant about amarok and kde4 in general.  The amarok 2 interface is a mess compared to 1.4.  The middle pane is particularly anoying- it should be a side tab.  Like most of the kde4 apps it has lost features and usability.  I used to use kde 3.5  across the board, except for firefox and grip, but now I'm using a mix-mash of gnome, kde3 and kde4 apps on top of xfce.  Hopefully the kde folks will eventually clean up the mess they made.

---

### Post by vinutux on 2009-10-13
not sure,,,but make atry to banshee or songbird

---

### Post by LucasDavenport on 2010-12-09
I was having the same problem with v2.3.0 and my ipod. Under Settings -> Configure Amarok there wasn't a media devices option available. Finally, I looked under Local Music and I saw my ipod listed with all my music

---

### Post by jamov on 2011-02-02
I have the same issue, no devices tab (kubuntu).
I did not see the ipod in local music as others had until I went back and added the package aptly called "ipod".  After a reboot, this package gave me access to the ipod in Amarok under the local music as suggested. However as an added bonus the OS itself gained access to the ipod such file browsing, basically it was now mounting the disk which it was not before. Basic I know, but hope that helps someone.

Oh, should note that I still do not have the media device tab in settings, so original problem not solved, but end result is a working ipod in Amarok.  I would say getting a working ipod in Amarok is what drove most of us here ;)

---

