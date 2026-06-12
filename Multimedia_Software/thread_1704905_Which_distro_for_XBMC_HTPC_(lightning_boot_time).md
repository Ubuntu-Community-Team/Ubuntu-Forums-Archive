---
title: "Which distro for XBMC HTPC (lightning boot time)"
date: 2011-03-11
forum: Multimedia Software
---

### Post by YfoMp5QBh2 on 2011-03-11
Hi All,
 
I have been playing about with various distro's to see which one's are the best. I have the intention of making a HTPC booting straight into XBMC.
 
I've Been thinking about using a cut down version of Linux with lightning fast boot (like Damn Small Linux or Peppermint OS) booting from solid state HDD or USB stick, but I need to have some basic requirements like access to internet to download content from youtube, access repo's, stream various types of content and codecs ect.
 
Can anyone help me out with some suggestions?

---

### Post by Grenage on 2011-03-11
I've got Ubuntu running my XBMC install, and it is ridiculously quick at booting; once the BIOS is gone, you're talking 5 seconds till the XBMC logo appears.

That said, any distro should do what you need, since you're only using it as a base.  Hell, I think there's actually an XBMC install available which is based on Ubuntu.

---

### Post by YfoMp5QBh2 on 2011-03-11
> **Grenage said:**
> I've got Ubuntu running my XBMC install, and it is ridiculously quick at booting; once the BIOS is gone, you're talking 5 seconds till the XBMC logo appears.
 
Is that the XBMC live installation your using?

---

### Post by Grenage on 2011-03-11
> **spadge_2356 said:**
> Is that the XBMC live installation your using?

Oh no, I'm using a base 10.10 install.  I use it for encoding movie files and ripping ISOs for the media centre, among other things.  While it's only used as an XBMC rig 95% of the time, I occasionally need to do things without tying up my main PCs.

---

### Post by YfoMp5QBh2 on 2011-03-11
so would you recommend a base/server install or a CLI install, then install things like XBMC on top?

---

### Post by Grenage on 2011-03-11
> **spadge_2356 said:**
> so would you recommend a base/server install or a CLI install, then install things like XBMC on top?

Well I personally opted for a standard desktop install, so I had gnome with a GUI if I wanted it.  You can still have XBMC load up as the default environment.

---

### Post by YfoMp5QBh2 on 2011-03-12
Thanks for your input so far. Currently playing with Xubuntu with XBMC Dharma, installed as part of a dual boot installation on a Dell Dimension 9150. 
 
The boot time is currently greater than **60 seconds**, but I suppose XFCE is a bit too heavy so could change to LXDE (or would this not make a difference?). I don't need compiz and all the bells and whistles just enough for XBMC and LIRC to function well, so I suppose I could terminate some of the process that begin on startup?
 
Any further recomendations as to how I can trim this down? 5 seconds would be a dream!

---

### Post by tjones00 on 2011-03-12
I believe Peppermint is based off ubuntu with lxde and cloud app integration.

As to desktops you don't need one for xbmcbuntu. Some people state that xbmc loads and operates faster without a gdm and de. No gdm or de will definitely cut down on resource usage.

[http://wiki.xbmc.org/?title=XBMCbuntu](http://wiki.xbmc.org/?title=XBMCbuntu)

For raw boot time on ubuntu look to disable as many services as possible eg. don't install cups (start with a bare cli/server install). You could also dabble with creating a custom kernel specifically for your machine/hardware or you could look into projects such as the liquorix kernel [http://liquorix.net/](http://liquorix.net/) which is an optimized kernel based on debian sid it should be compatible with ubuntu.

If want "instant on" type of speed (5 seconds) I'd look into getting suspend/hibernate and wake working properly.

---

### Post by YfoMp5QBh2 on 2011-03-17
> **tjones00 said:**
> I believe Peppermint is based off ubuntu with lxde...
 
Actually just started using Peppermint on my dell d600 laptop! I Think I'll try cutting down on the amount of processes which commence when Ubuntu loads up and see if that improves the boot time (eventually getting rid of the whole desktop interface together)
 
I will eventually go with the server install and build everything I need ontop of that, but it'll be tricky doing everything through the command line, I've done everything else through the GUI/desktop.

---

### Post by matt_symes on 2011-03-17
Hi

Funnily enough i was looking to do exactly the same thing but using Arch as a base and install just what i needed.

Has anybody else done this in Arch ? I assume it's possible as i have only just started looking into it.

Kind regards

---

### Post by YfoMp5QBh2 on 2011-03-17
Not looked at Arch-Linux, someone else has suggested Vector-Linux. I've decided to experiment first installing a lightweight distro, install everything I need XBMC ect and strip it down of everything I don't (compiz, or whatever)....and see what happens
 
Ultimately, I will start from a server CLI install as tjones00 suggested, and then see if I do that. 
 
But I'm not going straight to that as I'm not 100% comfortable with using the terminal commands to literlary setup EVERYTHING as my setup requires some customisation like skins, add-ons ect that arent in the generic repo's.

---

### Post by tkoopa on 2012-01-03
This may be a bit too late, but [http://www.openelec.tv/](http://www.openelec.tv/) seems to be what you are looking for. I'm in the process of building a new HTPC, and after years of using MythTV ( first on top of standard Ubuntu, then Mythbuntu ) I've decided to switch to XBMC because I can no longer record TV anymore as Belgian cable providers crypt all the digital content. OpenElec seems to be the best solutions for a fast booting device that is only used for XBMC

---

