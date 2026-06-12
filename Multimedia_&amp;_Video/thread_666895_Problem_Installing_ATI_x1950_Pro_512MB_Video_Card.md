---
title: "Problem Installing ATI x1950 Pro 512MB Video Card"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by flipovich on 2008-01-13
Well, I've been googling, searching the Ubuntu forums, trying everything I could find to get this to work.  Now, after all these tries, I think I may have jacked things up, but not certain.  I'm not a COMPLETE n00b to Linux, but I'm more familiar with Windows and Unix than I am with Linux, so things are a little bit testing for me.

First, let me give you my system setup, then I'll get into the details of what I'm trying to accomplish and such.  Thanks.

Intel C2D E6600
HIS ATI X1950 Pro Extreme 512MB PCI-E
2GB OCZ DDR2 800 RAM (will be 6GB once I resolve the driver issue, as I don't want to cross more than 1 hurdle at a time ;) )
MSI 975X Platinum Power-up Edition Motherboard
Hanns-G JW199DPB 19" Widescreen Monitor
Ubuntu 7.10 64-Bit OS

Ok, here's what I'm trying to do.  I was initially able to get 3D rendering working with installing the latest ATI drivers.  The problem was that I had zero widescreen support, which I need/prefer for some of my applications.  So, I started researching things a bit more and found that the latest ATI drivers have problems with widescreen, but the prior version doesn't (7.11).  No biggie, I just uninstalled those then installed the 7.11 drivers from the ATI website.  Well, that gave me widescreen, but no 3D support.  Now I can even run any of my applications that require 3D rendering as I have no 3D rendering capabilities.

I've tried completely removing all FGLRX packages installed and then trying to reinstall the generic Ubuntu ones, but that isn't even working right anymore.  I think something is lingering around and I don't know exactly how to clear everything away that has been previously installed so that I can start from scratch, again (without reinstalling Ubuntu, ofcourse).

Now, I'd like to avoid an OS reinstall as I like troubleshooting rather than just reformatting, so anything you need, just let me know.  I've gone into Synaptic and tried removing the packages that way as well, and I don't think that removes everything either.  Please let me know any suggestions ya'll have for getting my system back to scratch when it comes to the ATI drivers so that I can install the 7.11 drivers from scratch (with no traces of any other drivers) and get Widescreen AND 3D rendering capabilities at the same time.   

Thanks in advance for any assistance you are able to provide me.

---

### Post by flipovich on 2008-01-13
Oh yeah...I also forgot that when I go to the terminal and try to run fglrxinfo it now just resets the XServer and brings me back to the log-in screen; whereas it used to give me the graphics info (was ati while I had the 7.12 drivers installed, but wouldn't change from Mesa when I installed the 7.11 drivers, and now won't even display at all).  Doesn't even display anything in the terminal.  This is why i'm at a stuck point and need some assistance.  Let me know what ya'll think.  Thanks.

---

### Post by Rubruquis on 2008-01-14
I have an X1900 series ATI card, which has the same chipset as yours. I've tried enabling 3D & Widescreen at the same time, installed all the ATI drivers I could have found and none of them did work. Then I've installed a fresh copy of Ubuntu and used the drivers that came with Ubuntu and did not make any update. Miracle! Everything worked fine. 
So I'd suggest installing a fresh copy of Ubuntu and see if it helps.

---

### Post by flipovich on 2008-01-14
hmmm....if I remember right, when I first installed the OS I had the ones that came with ubuntu installed and I tried widescreen AND 3D rendering and it was a no-go, but I'll give it a try this afternoon after work and let ya'll know if I'm successful or not.  Thankfully I created a seperate /home partition ;)

---

### Post by KeeperOS on 2008-01-15
I've been postponing installing Ubuntu (or Linux in general for that matter) exactly because of that.
I too have a (Sapphire) ATI x1950 Pro 512MB PCI-e and no matter how many (Debian based and not) distros I tried under live cd 
environment none worked with either the fglrx, ati or radeon drivers.
Only thing that kinda worked were the vesa drivers and those were murder with video playback...

Anyway, after a lot of searching I found out that many **mistakenly** think the x1950 and x1900 have the same chips. **THEY DO NOT**!

The 1950 has a chip that was developed AFTER the x1900 (both chronologically and from a design standpoint, aimed at lower power consumption) and as thus the drivers for one will not work correctly for the other.

The latest ATI drivers were supposed to also support the x1950 series but that was done in haste and didn't really bothered to fix all the problems...

I've asked around many times and in different places but no-one has been able to provide any real help...

---

### Post by flipovich on 2008-01-15
> **KeeperOS said:**
> I've been postponing installing Ubuntu (or Linux in general for that matter) exactly because of that.
I too have a (Sapphire) ATI x1950 Pro 512MB PCI-e and no matter how many (Debian based and not) distros I tried under live cd 
environment none worked with either the fglrx, ati or radeon drivers.
Only thing that kinda worked were the vesa drivers and those were murder with video playback...

Anyway, after a lot of searching I found out that many **mistakenly** think the x1950 and x1900 have the same chips. **THEY DO NOT**!

The 1950 has a chip that was developed AFTER the x1900 (both chronologically and from a design standpoint, aimed at lower power consumption) and as thus the drivers for one will not work correctly for the other.

The latest ATI drivers were supposed to also support the x1950 series but that was done in haste and didn't really bothered to fix all the problems...

I've asked around many times and in different places but no-one has been able to provide any real help...



Yeah, I'm kinda in the same boat.  The 7.12 drivers from ATI fully support the x1950, with the exclusion of widescreen support.  Widescreen support is currently a "global" problem with the 7.12 drivers.  I had zero problems with those when it came down to 3D rendering.  They ran movies, games, etc flawlessly.  The problem came when I didn't have the capability to enable widescreen, even manually by modifying the xorg.conf.  If you don't mind NOT running widescreen til the next revision of drivers, then install the 7.12 drivers.  Like I said, they ran 3D rendering and DVD/AVI playback wonderfully.

If I can get the regular driver version working well, then I'll post back here with my findings.  As I've said before, I've researched quite a bit and haven't been able to find any reason as to why the x1950 won't do both 3D Rendering AND widescreen at the same time.  As for the 1900 and 1950 being different chips, yes I know ;)  Alot of people have the misconception that the 1950 is just a souped up version of the 1900, which it isn't.  Thanks for the response :)

---

### Post by KeeperOS on 2008-01-15
Thanks man, I've been a little behind myself, my monitor is a 4x3 CRT so no need for widescreen support here.

HOWEVER, I DO remember reading somewhere (found it, [HERE]("http://www.phoronix.com/scan.php?page=article&item=601&num=3")) that if you were to manually modify the  *ChipID* argument in */etc/X11/xorg.conf* to fake the Chipset as  a Radeon X1900, it'd work but will lack 3D acceleration support... dunno if/how that helps though...

---

### Post by flipovich on 2008-01-15
eh, I saw that as well, didn't bother trying as soon as I read that 3D support will be jacked up quite a bit.  Considering I didn't have a problem getting 3D rendering working, I didn't even bother with it.  My problem was getting 3D rendering AND widescreen working at the same time.  I could do 1, but then couldn't do the other :(

---

### Post by flipovich on 2008-01-15
well, well, well...from what I can tell so far, the ones that Ubuntu installs by itself are working for 3D rendering AND widescreen support.  I did things a tad bit different during this install, however.  

After reformatting/repartitioning and installing, I did NOTHING but the Restricted Drivers Manager on the first boot-up.  Enable the ATI Restricted driver and then let it do it's thing and rebooted.  After this I did ALL of the updates listed and did a reboot.  Then I did the next set of updates that came up (didn't require a reboot this time) and installed Wine.  Installed all the other applications I wanted installed and got the move on.

I basically did things in a specific order, video first, then OS, then personal preference, instead of how I did it before--video last.  :(  Goes to show ya how doing things in a smart order can actually benefit ya.  Looks like Ubuntu wins again with great default drivers :)  Good job.  Thanks all for your assistance.  Much appreciated.

---

### Post by KeeperOS on 2008-01-16
PERFECT! Now perhaps it's time to buy a new HD and get the buntu experience rolling :D

---

### Post by chmavr on 2008-04-01
and everything is ok now???i have the agp version and i cant make anything wrong.

---

