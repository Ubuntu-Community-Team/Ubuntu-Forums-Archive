---
title: "Ati Radeon 9000 + Ubuntu 10.10 = Brightness Issues"
date: 2011-01-23
forum: Multimedia Software
---

### Post by OrangeChrome on 2011-01-23
Hello all. 

I have been just pretty much having fun with Ubuntu and a couple other distros for a couple years and have not yet ran into a problem like this.  I'm pretty good in a command line environment although I end up googling syntax a lot b/c of that wonderful memory I have! Anyways.. 

I am running an older machine: P4P800 ASUS Mobo, P4 2 Ghz, 3G RAM and an ATI Radeon 9000.
OS: Ubuntu 10.10 Maverick Meerkat

Issues: Seems that anything that Compiz has to render the brightness is really low.  CairoDock (w/ OpenGL) does not render like it does on other machines that I have, looks like garbage. I've come to the conclusion that I need to get a better video driver (Hope I'm correct here otherwise I've been going the wrong direction for awhile now).  

Things I've tried through research around the net:  

I've attempted installing fglrx(command line style) from several tutorials I've found here and there.  Most of them for older versions of Ubuntu and if I'm remembering right there have been a few significant changes lately, which may be causing my issues?

Of course I've tried the easy ways: 

[LIST]
[*]Installed all fglrx/ati/radeon related packages in Synaptics Package Manager
[/LIST]

[LIST]
[*]Checked System > Admin. > Additional Drivers before and after package installations
[/LIST]

[LIST]
[*]Ati Website - the drivers that they have are for XFree86.  I don't think they can run on XOrg - it's a completely different setup? Again, I don't have a great understanding on how the back end of all this works, so bear with em.
[/LIST]

I ran: echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
To disable KMS. 
Rebooted - Video was much worse
I then ran:  echo options radeon modeset=1 > /etc/modprobe.d/radeon-kms.conf
To re-enable KMS
Rebooted again. Everything ran fine but I didn't have my Cairo Dock > which I can deal with, that's not why I'm posting.. 


Well, that's a good chunk of it - there's more but I don't remember most of it as I've been working at this on and off for weeks.  Again, a lot of this was tried upon researching anything and everything I could find on the net - so some of it might sound ridiculous, I was just trying anything that would work!!

Any help would be [SIZE=3]**GREATLY**[/SIZE] appreciated.

---

### Post by OrangeChrome on 2011-02-17
BUMP

No one is able to help out?

Even a link with some decent syntax/directions would be appreciated.  Even if it's another thread that I may not have come across yet.  

Again, any help would be awesome!

---

### Post by Mark Phelps on 2011-02-17
Just to clear up one concern you had regarding drivers ... the open-source drivers you already have installed are the only ones that will work with your card and Ubuntu versions newer than 8.10.

There are no drivers on the ATI/AMD website (or anywhere else, for that matter) that you can download that will give you fglrx support -- as AMD dropped such support for your card years ago.

If you want to do some searching, suggest you go over to the Phoronix forums.  They do a LOT of work with the open-source drivers.  You might find some tips there on things you can do.

---

