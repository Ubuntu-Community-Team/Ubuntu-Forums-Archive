---
title: "Adobe CS3 in Ubuntu?"
date: 2007-05-17
forum: Multimedia Production
---

### Post by elysium444 on 2007-05-17
Can Adobe CS3 products like flash and photoshop run under ubuntu?

Please send me a link of a tutorial if you know one. I have been searching for hours :(

---

### Post by thommango on 2007-05-17
Adobe doesn't build their products to run on Linux.  So, if you have a dual boot machine, you'll probably just want to run Adobe apps under windoze.  However, you can also try running the application under WINE.  WINE is a linux app that allows you to run windows apps from linux.  I think there's a freeware version available in the Ubuntu program adder thingy.  But WINE is one of the few Linux programs that actually charges, so you may find that you need to use a purchased version to make it work entirely.  

Good luck,

Thommango

---

### Post by PhatStreet on 2007-05-17
> **thommango said:**
> Adobe doesn't build their products to run on Linux.  So, if you have a dual boot machine, you'll probably just want to run Adobe apps under windoze.  However, you can also try running the application under WINE.  WINE is a linux app that allows you to run windows apps from linux.  I think there's a freeware version available in the Ubuntu program adder thingy.  **But WINE is one of the few Linux programs that actually charges, so you may find that you need to use a purchased version to make it work entirely.  **

Good luck,

Thommango
Are you thinking of Cedega? WINE is free OSS.

I wouldn't count on getting CS3 to run in WINE, though. The compatibility just isn't there yet.

---

### Post by Shay Stephens on 2007-05-18
The best you can do right now is run Photoshop 7 in wine.  The CS versions don't run or even install reliably yet.

---

### Post by Lorenz on 2007-05-18
If I install Windows XP as a guest OS on virtualbox, can I then install Photoshop on that guest Windows?

---

### Post by ffxr on 2007-05-20
yip, i do that but with vmware server, i previously done it with virtualbox as well.. so it not really a problem.. just make sure you have plenty of RAM.

---

### Post by cgbier on 2007-05-20
> **ffxr said:**
> yip, i do that but with vmware server, i previously done it with virtualbox as well.. so it not really a problem.. just make sure you have plenty of RAM.

You need more than plenty of RAM. However, to calculate filters, P/S needs a fast processor also, especially, when it is run in virtual environment.
I tried CS2 under a test version of VMware. With a 2.6 GHz machine and 1.25 gig RAM it was slow like molasses.

Flash (at least the player) runs natively under LINUX.

---

### Post by ricrac on 2007-05-21
Xen, KVM and vmware perform much better if you have a newer processor than supports virtualization extensions (Intel VT or AMD-V).

Multiboot between xp and linux is another option.  Vmware without VT processor, expect 50% of base performance.

I use 3d apps and CNC control Roland mills on xp in vmware on linux for production use.
The CNC program ties up windows, so you can't do anything else, especially while 3d scanning.
Using vmware (or other virtualization) I can just open another win client or linux client or just work in the parent linux system with no CNC errors from the windows client.  In fact it works much better  for me than a standard xp install.  Something to do with the serial ports and (I'm guessing here) buffers in the parent system.  I get stalls or lost commands with background xp housekeeping tasks in a default xp install, but a default xp install on vmware doesn't have these issues.

My wordy point is if you have an Intel VT or AMD-V enabled processor and setup opengl video drivers in vmware, performance is quite adequate.  I only use Xen (and other linux virtualizers) for linux on linux.

---

### Post by kayosiii on 2007-05-24
[http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/](http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/)

you could try these steps for CS2 and see if they work for you with CS3

---

### Post by Dylnuge on 2007-06-13
I have gotten some CS3 products to run under wine, but not with full functionality. Your best bets are either to use a dual boot or to run Windows under VMWare Server (free).

Wine is not paid software. Cedega and CrossOver Office, two projects that extend from the Wine project, are commercial. Cedega runs games primarily, so I would not try it. CrossOver does not support the CS lineups

Note: As to your original question-Flash I have gotten working, Photoshop I have not. Adobe released their Flex SDK under Linux and Solaris as OSS, and is relasing a new system called AIR as OSS under Linux and Solaris (both of those in addition to Win and Mac), so hopefully there will be a Linux version of CS4. However, note that Adobe only officially supports RedHat Enterprise 4 and SUSE 10. Not too much of a difference (RedHat uses KDE, and I don't know about SUSE), so there is something to be hopeful about.

---

### Post by tooleh on 2007-10-18
If one were to unpack the mac versions of the apps, is there any chance the binaries would work seeing as they are both combined for unix type OS?

Just a thought, seeing as CS3 is one of the few things keeping me on windows right now :\

---

### Post by Druke on 2007-10-19
I am personally curious why there isn't more work on bringing mac apps to linux, that seems much easier

---

### Post by jespdj on 2007-10-19
> **tooleh said:**
> If one were to unpack the mac versions of the apps, is there any chance the binaries would work seeing as they are both combined for unix type OS?

Just a thought, seeing as CS3 is one of the few things keeping me on windows right now :\
No, Ubuntu is not Mac OS X, even though Mac OS X is also a Unix-like OS. Trying to run Photoshop for Mac OS on Ubuntu (or any other flavour of Linux) is certainly not going to work.

Photoshop CS3 is also for me one of those apps that keep me on Windows. There simply isn't a replacement on Linux that is just as good as PS CS3 and Bridge CS3... I wish Adobe would make a Linux version of CS3!

(And no, The GIMP is unfortunately not good enough).

---

### Post by Shay Stephens on 2007-10-19
> **jespdj said:**
> Photoshop CS3 is also for me one of those apps that keep me on Windows. There simply isn't a replacement on Linux that is just as good as PS CS3 and Bridge CS3... I wish Adobe would make a Linux version of CS3!

(And no, The GIMP is unfortunately not good enough).

I am a photographer and that is what kept me enslaved to windows too, but in my case it was PS CS2.  I decided that the only way to free myself was to stop upgrading Adobe's software.  Besides, I am opposed to online activation in Windows, so I should treat Adobe's the same way.  So I did.

I downgraded to PS7, started using Bibble Pro instead of Bridge, and use Gimp for a lot of batch processing for web sized images. 

I am 100% free of windows now and can still get all my work done.  But now it is spread between three apps (PS7, bibble, gimp) instead of just 2 (ps & bridge).  It can be done, you just have to adapt a little.  I am glad I did.

---

### Post by NoSmokingBandit on 2007-10-19
I heard wine now supports cs2. Is this correct? I tried to copy files from my windows partition into the .wine folder, but i still couldnt get it to run, i always get a message along the lines of 'there has been a hardware error, this cant be fixed'....

---

### Post by Robsta83 on 2007-12-14
.

---

### Post by Robsta83 on 2007-12-14
Hmmm...  People say on WineHQ.Org that CS2 works ok, through a little activation hack (install CS2 on windows, open regedit, and get your valid cs2 key from there, then put it in the wine registry, and apparently that will get you going).

Now I am running wine via Crossover on a Mac, and CS3 requires XP SP2, but looking at this windows post on the adobe forums, you can edit the native windows registry to make SP1 appear as SP2. Can we do this within wine to get CS3 working? I could not find the key within the wine registry??

Adobe forum... [http://www.adobeforums.com/webx/.3bc3b3a9?14](http://www.adobeforums.com/webx/.3bc3b3a9?14)

Would that work?

Robsta

---

### Post by prabhanjan on 2007-12-18
Use portable versions of photoshop and other apps to run in wine

---

### Post by jrharvey on 2007-12-19
I have CS2 running fine on virtualbox with windows XP sp2. its not slow at all for me but maybe its because my machine is fairly new. The weird thing is that It will not allow for certain imports and exports such as DWG in illustrator which works fine on a native install. I am not entirely sure why this is but I can always dual boot If i need to.;

---

### Post by malty on 2007-12-20
PS7 runs OK in Gutsy for me, except, if like me you are used to  CS3 complete with 7 rucksacs full of plugins then PS7 is a pain.

I tried to install some Extensis plug ins, waste of time.

So even if someone fettles CS3 (other than Adobe) its full pontential cannot be utilized, if you use it as a working tool then this will be a problem.

I bought Crossover but the range of apps (other than the boggo Microsoft stuff) is poor, very limited , aimed at business.

So............I live with dual boot and cast the runes every full moon  
in the hope that one day...............
Regards         Malty

I am picking up Gimpshop its good but, if CS3 =100% then Gimpshop would be circa 75%, it would not pay the mortgage.

---

### Post by Vadi on 2007-12-26
This thread will be of use ([click]("http://ubuntuforums.org/showthread.php?p=4001494"))

---

### Post by dustman on 2008-01-27
haven't you heard of Pixel Image Editor ( [http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12) ) ?. As i've seen from those screenshots, it's 100% Adobe Photoshop, only that it's built for a multitude of platforms. It's not for free, but anyways, a 29$ price is better than the money you have to pay for Adobe Photoshop CS3 ;)

Cheers!

Radu

---

### Post by mmcmonster on 2008-01-27
Things are looking up with [Wine 0.9.54]("http://www.winehq.org/?announce=0.9.54"). :-)

---

### Post by factotum218 on 2008-05-26
I am in a similar situation and found my solution to work across the board with any Linux distribution I have used:

VMWARE

I found dual booting for applications a bit tedious after a while and found a virtual machine a great alternative.

I installed vmware server and set up an XP system which runs the entire CS3 suite without any problems.

Don't have to reach for the power button, just a couple clicks and I have a full screen xp system ready to go (and people still think you need a mac for graphic design, bah!). I went on to strip down the xp system. No network connection, themes shut off, everything outside of using a few specific applications is as close to gone as I feel comfortable with. I didn't go into regedit or anything that drastic. Just trim the fat a little.

---

### Post by zipperback on 2008-05-29
> **Lorenz said:**
> If I install Windows XP as a guest OS on virtualbox, can I then install Photoshop on that guest Windows?


Yes

---

### Post by factotum218 on 2008-06-01
If your running GNU/Linux on your system and need to have an Adobe application like Photoshop CS3 or Dreamweaver 8, you're wasting your time. Chances are if you yourself independently own legit copies and product keys, you are a professional that wouldn't need to be running GNU/Linux. Either stick with windows, or be a money wasting schmuck and get a new Mac every couple years.

Otherwise, let the head of your department or your friendly neighborhood torrent tracker take care of it for you and get back to work!

---

### Post by pingnak on 2008-06-03
I run Flash 8 under Linux all the time.  Works just fine.  People do in fact pay me to do it, and they don't have a clue I'm not a wimpy 'just be a slave to Gates' Windows creep.

Some people allege to have Flash CS3 running under Wine, but I wasn't able to duplicate their success.  Most likely CS4 will come out before CS3 runs acceptably.

I used to use VMware, but now use a VirtualBox session running XP to run CS3 Production Premium now.  The only real problem I've encountered is time-based funkyness.  Everything seems to run about 5~10% faster than it ought to, so any Flash content you develop in the emulator will need to be tested outside of it, too in order to make sure it doesn't run in slow motion.  I find testing under the native Linux flash player is close enough.

All in all, for applications like CS3, a virtual machine is absolutely the way to go.  Not only does it run OK, you can move it freely from machine to machine without tinkering with the 'activation'.  Rather than spend hours babysitting Adobe's bent CS3 setup on every machine you use, you can simply move a 16GB VM file and settings around, which is substantially faster, and you can do something else while it happens.

Another path to try is the Adobe Flex SDK if you program Flash.  You can develop the art in Flash 8 or CS3 (not really much new in CS3 that I personally appreciate except it handles the origins and errors better), then develop an AS3 app with development tools that don't suck.  I prefer jEdit, a Makefile and a C preprocessor.  
[http://flex2cpp.sourceforge.net/](http://flex2cpp.sourceforge.net/)

---

### Post by MystaMax on 2008-06-04
I also use the CS3 suite frequently. I run a slimmed down version of WinXP Pro on Virtualbox 1.6.

I've added a screenshot I took of Photoshop CS3 running in my Virtualbox WinXP session in seamless mode. Pretty sweet.

While my current setup is nice, I would rather run CS3 using Wine than in a virtual session. 

To get CS3 installed, I had to allot 1GB of my RAM to virtual session to correctly install CS3. No biggie, since I've got 2 gigs, and RAM is pretty cheap these days. Still, I rather have it back.

In the end, I'm impressed with the speed and responsiveness. I also like the ability to save a virtual machine. I no longer have to shut down the virtual machine. I can just save it with Photoshop and any other programs open, and it takes less than 30 seconds to save or start the Virtual machine. Very nice.

sorry for the large screenshot.

---

### Post by AndyCee on 2008-06-05
"if you yourself independently own legit copies and product keys, you are a professional that wouldn't need to be running GNU/Linux. "

WTF? Don't 'professionals' run Ubuntu?

---

