---
title: "Installing ATI Radeon x1100 driver on 9.04"
date: 2009-05-31
forum: Multimedia Software
---

### Post by Shadyboy on 2009-05-31
Well, after some time now trying to do this on my own, I am near brink of destruction.

I have downloaded the driver for my ATI Radeon x1100 card.
Found it here : [http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English]("http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English")

and when I try to install it I get the following message :

> shadyboy@hacky:~/Desktop$ sh ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.CCUppT
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.CCUppT
shadyboy@hacky:~/Desktop$

And when I have searched on Google, all help is kinda given for the "older" versions of Ubuntu. 

I have even tried EnvyNG... My system kinda "hung up" when I used it.

---

### Post by Melcar on 2009-05-31
Catalyst 9.3 was the last version to support your particular chip.  Jaunty comes with 9.4, and because of the new kernel and xserver in Jaunty, drivers earlier than 9.4 won't work.  If you want to use Jaunty you need to move to the open source driver (either radeon or radeonhd).  If you prefer to use the proprietary driver, you will need to go back to Hardy.

---

### Post by Humans_Are on 2009-05-31
word is that there is no "restricted driver" support for the those "older" ati cards... 

I'm sure someone with have a more in depth reply.

awesome huh?

edit:
Does anybody know if there's anything going on to fix this...a place to find updates on this issue? even if it's a better open source driver..

---

### Post by Shadyboy on 2009-05-31
Well, want to do that as a last resort.

Is it possible to remove the 9.4 driver and install the 9.3 driver?
Or is my only option to use Hardy?

---

### Post by Humans_Are on 2009-05-31
From what i've read hardy is our only choice for real 3d. #%*$!

---

### Post by Shadyboy on 2009-05-31
My main reason for wanting the drivers, is to keep on playing Wow :P

---

### Post by regala on 2009-05-31
> **Humans_Are said:**
> 
Does anybody know if there's anything going on to fix this...a place to find updates on this issue? even if it's a better open source driver..

there's only one open source driver...

---

### Post by usergentoo on 2009-06-01
You can compile an older xserver version and use the 9.3 drivers on Jaunty it takes a bit of work but its worth it. They should port the older version to Jaunty for people like us so you dont have to jump thru crap to get this working.

---

### Post by usergentoo on 2009-06-02
Ill see if I can build a deb package for you guys that need it later this week(Ill try anyway) and see how well that works.

---

### Post by bernash on 2009-06-10
I have ATI Radeon x1100 too. The same problem.
I cant find proprietary driver & radeonhd do not have my card in list ((

---

### Post by raakken on 2009-06-14
> **usergentoo said:**
> Ill see if I can build a deb package for you guys that need it later this week(Ill try anyway) and see how well that works.

I would be forever grateful:)

---

### Post by CheeRees on 2009-06-18
Any news? I have same Radeon x1100 on my laptop :icon_frown: 
HELP PLEASE

---

### Post by nekisia on 2009-06-18
hi there.i 've x1200 ,i think we tried to install the driver package,from the official site.
and i have the same problem.My version is 32bit not 64

---

### Post by ndo on 2009-06-28
> **nekisia said:**
> hi there.i 've x1200 ,i think we tried to install the driver package,from the official site.
and i have the same problem.My version is 32bit not 64

It seems the 1200 is supported by something called the fglrx driver, found the information here:
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

**** out of luck on the 1100, though...I'll be honest, I'm starting to think the most effective way bind a person's loyalty to Windows is to make them use Linux...

---

### Post by mcduck on 2009-06-29
Just use the "ati"-driver, not "radeonhd" or "fglrx".

---

### Post by Deiutzu on 2009-07-17
I also have an Acer Aspire 5100 with an ATI Radeon Xpress 1100 card. The only thing that makes me still use Windows is the fact that I cannot install the correct video drivers in Ubuntu. Also, I cannot revert to Ubuntu 8.10 or older because of an load cycle error that my hdd gives in older Ubuntu versions. 

**Usergentoo** you gave me hope when you said that you can recompile an older xserver version that we can use with Catalyst 9.3 but we still have no news from you.

A fix for this problem would be much appreciated.

Best regards,

       Andrei C.

---

### Post by steefjeqv on 2009-07-17
Hi,

Stay away from fglrx (closed source ATI/AMD) driver.

Use the open-source xorg-ati driver (ati) which is default on Jaunty.
It runs fine on my T-60 laptop with X1400 ATI graphics (3D, Compiz, Video...).

Greetings,
Steven

---

### Post by ssri on 2009-07-17
> **Deiutzu said:**
> I cannot revert to Ubuntu 8.10 or older because of an **load cycle error** that my hdd gives in older Ubuntu versions...

Best regards,

       Andrei C.

I doubt the recompile could be done since Catalyst 9.3 will absolutely not work with xserver 1.6.x and above (installed on Jaunty by default).  

As for your load_cycle problem, try "sudo hdparm -B 254"

You can check which power management settings are set via:

"sudo hdparm -I /dev/sda"

Then monitor the load_cycles using smartctl

That fixed the problem for me way back in 12/2008.  My load_cycles stop dead in its tracks.

[http://ubuntuforums.org/showthread.php?t=1180286](http://ubuntuforums.org/showthread.php?t=1180286)

---

### Post by Deiutzu on 2009-07-18
Thank you very much for your answer! So, if I understand well, if I want to have hardware acceleration on my ATI Radeon Xpress the only option is to revert to Ubuntu 8.10 and fix my Load Cycle error... I will try also that.

---

### Post by aj_the_first on 2009-07-19
So, I have an x1300 card, and I have bad screen flicker with Jaunty.  I did realize that the old ATI proprietary driver won't work when I tried to install it, but I like Jaunty...
Of course I dont like the less than 1MB/sec USB and SATA transfer rates, and the screen flicker is pissing me off, but I figured I could fix those problems...
Is it just not worth it?  Is backdating to Intrepid or Hardy the only way to run smoothly?
Are there any other options?

---

### Post by aj_the_first on 2009-07-19
> **steefjeqv said:**
> Hi,
 
Stay away from fglrx (closed source ATI/AMD) driver.
 
Use the open-source xorg-ati driver (ati) which is default on Jaunty.
It runs fine on my T-60 laptop with X1400 ATI graphics (3D, Compiz, Video...).
 
Greetings,
Steven
 
Is this the same as the RaedonHD 1.2.2 and 1.2.3 drivers? Because the default Jaunty driver is not working for me (screen flicker with ATI x1300 card) or my wife (800x600 resolution is the only option, even though she has a 16" wide screen on her laptop with an ATI Mobility Raedon HD4670 vid card)
I really want to fix Jaunty and keep it working, but between the the screen flicker and resolution issues, combined with the SLOOOOWWW USB and SATA transfer rates, I'm not sure how much longer I care to work on it.
She has already reverted back to Vista... It was sad to see her go...
 
EDIT: I have an x1200 card

---

### Post by steefjeqv on 2009-07-19
Hi,

The xserver-xorg-video-ati is closely related to radeonhd. The "ati" driver is default when installing Jaunty.

When installing Jaunty on my T60 laptop (X1400), I was a bit concerned about the graphics (I'd heard about the flickering too). It seems that my X1400 isn't affected, but X1100-1200-1300 are.

Anyway, this error has already been filed as a bug, and there is a solution :

Type this command in your terminal :

sudo gedit /etc/X11/xorg.conf

Now add the following line under the Section "Device" :

Option "AccelMethod"  "XAA"

Save and reboot.

This should work if your system uses the open "ati" driver.
I've attached an xorg.conf as an example.

Greetings,
Steven

---

### Post by aj_the_first on 2009-07-20
Awesome!  works perfectly!
I'll spread this around on some other similar threads I have been watching.  Thanks.

---

### Post by aj_the_first on 2009-07-20
Okay not perfect.  The screen flicker is greatly reduced, though there is still some minor flickering, but skype video no longer works.  It doesn't display anything, and neithe did cheese.  in fact, cheese just closed as soon as it opened.  I reverted back to the original file configuration and I am dealing with the screen flicker so I can use skype and cheese and such.
I am going to try again and see if any other video is affected such as youtube.

---

### Post by steefjeqv on 2009-07-20
Hi,


This may be worth a try : updating the ati driver.

Tormod Volden provides updated versions of this driver for Jaunty :

[https://launchpad.net/~tormodvolden/+archive/ppa]("https://launchpad.net/~tormodvolden/+archive/ppa")

Just click on the xserver-xorg-video-ati - 1:6.12.99+git20090710.43db263d-0ubuntu0tormod package and choose your architecture (i386 or amd64).

Download all Files produced from build, and double-click to install.

If this doesn't help then you can try upgrading your X-server by using this repo :
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")
Be careful because this option can break your x-server.


Greetings,
Steven

---

### Post by aj_the_first on 2009-07-21
> **steefjeqv said:**
> Hi,
 
 
This may be worth a try : updating the ati driver.
 
Tormod Volden provides updated versions of this driver for Jaunty :
 
[https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa)
 
Just click on the xserver-xorg-video-ati - 1:6.12.99+git20090710.43db263d-0ubuntu0tormod package and choose your architecture (i386 or amd64).
 
Download all Files produced from build, and double-click to install.
 
If this doesn't help then you can try upgrading your X-server by using this repo :
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
Be careful because this option can break your x-server.
 
 
Greetings,
Steven
 
 
So just to clarify, I need to download and install **all four** .deb files from this site? (amd64 architechture): 
[https://launchpad.net/~tormodvolden/+archive/ppa/+build/1113482](https://launchpad.net/~tormodvolden/+archive/ppa/+build/1113482)
 
If it doesn't work, and for some reason I end up with more problems, how do I fix it/uninstall?
Let's just hope it doesn't for now....

---

### Post by steefjeqv on 2009-07-21
Hi,

You don't really need the dbg packages.
The other two (ati and radeon) are needed.

If something isn't good you can remove these deb files using Synaptic and after removal you can install the original ones again.

Greetings,
Steven

---

### Post by zetanuxi on 2009-07-21
I have a x1600Pro and the fglrx drivers killed my install. During boot, the screen distorted and froze. I couldn't uninstall it from the terminal in recovery mode either. I gave me a permissions error, even though I was root. The ATI drivers from the site give me an error when I unpack and try to install them. It says my distribution is not supported.

I've tried the ATI drivers that come stock with Jaunty, but they wont let me use my 52" Projection TV as the main monitor. I try to put the resolution to 1920x1080 and the screen distorts and goes blank. Any one have an answer? Are the ATI drivers in the repositories the only option?

---

### Post by ssri on 2009-07-21
> **zetanuxi said:**
> I have a x1600Pro and the fglrx drivers killed my install. During boot, the screen distorted and froze. I couldn't uninstall it from the terminal in recovery mode either. I gave me a permissions error, even though I was root. The ATI drivers from the site give me an error when I unpack and try to install them. It says my distribution is not supported.

I've tried the ATI drivers that come stock with Jaunty, but they wont let me use my 52" Projection TV as the main monitor. I try to put the resolution to 1920x1080 and the screen distorts and goes blank. Any one have an answer? Are the ATI drivers in the repositories the only option?

Stick with Catalyst 9.3 on Intrepid?

---

### Post by aj_the_first on 2009-07-22
> **steefjeqv said:**
> Hi,
 
You don't really need the dbg packages.
The other two (ati and radeon) are needed.
 
If something isn't good you can remove these deb files using Synaptic and after removal you can install the original ones again.
 
Greetings,
Steven
 
 
Well, I loaded that driver and it booted up at a very fuzzy 600x800 resolution.  I went back to the default drivers...  anything else I can try?

---

### Post by steefjeqv on 2009-07-23
Hi,

@ aj_the_first :

I've noticed you're helping debugging this problem :
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/351291")

I think the ati drivers from Tormod Volden are your best chance to resolve these problems.

I suppose that you aren't able to change the resolution from 800x600 to something else when using these ppa drivers.

What you can try : Give the Tormod Volden drivers another try, and when you end up with the 800x600 resolution type the following in terminal :

sudo dpkg-reconfigure -phigh xserver-xorg

This command will reconfigure your X (keyboard layout, mouse control...) so be carefull when following this procedure. Hopefully, after a reboot your screen resolution will now be detected correctly. 

Greetings,
Steven

---

### Post by steefjeqv on 2009-07-25
Hi,

I've just installed Tormod Volden's packages on my laptop. 
The screen resolution was detected correctly but I'd lost all desktop effects.

So I decided to use "the xorg on the edge" ppa. This can break your X, but in my case everything went well.

[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")

A small howto :

Add the ppa to your software sources by using Synaptic>Settings>Sources>third parties>Add.

Add the signing key to Synaptic (click the link at xorg on the edge, then copy/paste into gedit) :
Synaptic>Settings>Sources>Authentication>Add.

Now use your terminal :

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

That should be everything.

Greetings,
Steven

---

### Post by photographerHU on 2009-07-27
Hi,

I have Ati 1150 with the same problem. Im still new so its not clear, that how can I add in here:
Add the signing key to Synaptic (click the link at xorg on the edge, then copy/paste into gedit) :
Synaptic>Settings>Sources>Authentication>Add.
How and where can I save the key? Can you write it down again with a little bit more deatails? I cant understand this part.
Please

---

### Post by martinbaselier on 2009-07-27
You can save it where you want. Just choose save, give it a name and remember the location.

---

### Post by steefjeqv on 2009-07-27
Hi,

@ photographerHU :

After clicking on the signing key link, click on 8844C542, then copy everything between -----BEGIN PGP PUBLIC KEY BLOCK----- and -----END PGP PUBLIC KEY BLOCK-----

Paste to gedit (text editor) and save.

Then point Synaptic to the location where you saved the file.

That's it.

Greetings,
Steven

---

### Post by photographerHU on 2009-07-28
Its working

Thank you steefjeqv

---

### Post by kammpler on 2009-08-03
> **Shadyboy said:**
> My main reason for wanting the drivers, is to keep on playing Wow :P

same problems, same reason here, it sems that the only solution for us is to downgrade to hardy

---

### Post by smsmith on 2009-08-04
> **aj_the_first said:**
> Well, I loaded that driver and it booted up at a very fuzzy 600x800 resolution.  I went back to the default drivers...  anything else I can try?
I too was having the horrible flicker with my ATI x1200 and had tried installing the updated drivers from Tormod's PPA.  I then got the wrong resolution like you described with no way to fix it.  Until I found this little tidbit:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/379856/comments/2](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/379856/comments/2)

Now the resolution is correct and I can use desktop effects without any flicker.

Hope that helps, though I don't know if it will solve your Skype and Cheese problems.

---

### Post by martinbaselier on 2009-08-04
You can also downgrade your xorg:
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by yogaman69 on 2009-08-04
HI Guys,

I've been trying to install Mythbuntu 9.04 but had a lot of problems which I traced to my ATI X1300 card. it seems the Tormod Volden drivers solve a lot of the problemes with Jaunty. Does anyone know if they work with MythTV?

thanks a lot

---

### Post by photographerHU on 2009-08-27
Hi,
I did not try it, because I cant believe, that something will work with my ati radeon xpress 1150 / 200M, but anyone tryed this? Is it working with my card too?? Is this the solution for us?
Im writeing, asking, because today I found this article:
 [http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html#more-1805](http://www.ubuntugeek.com/ati-linux-video-driver-9-8-now-supports-ubuntu-9-04-jaunty.html#more-1805)
 [http://www.theinquirer.net/inquirer/news/1529490/ati-updates-linux-graphics-display-drivers](http://www.theinquirer.net/inquirer/news/1529490/ati-updates-linux-graphics-display-drivers)

---

### Post by photographerHU on 2009-08-27
OK sorry. I  think is still not the right one, but maybe for someone else is helpful....

---

### Post by del_diablo on 2009-08-27
Ain't the free drivers already doing their job? And ain't somebody suppose to read the news?
[http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards](http://www.linux-magazine.com/Online/News/AMD-Provides-Legacy-Driver-for-Old-ATI-Cards)
[http://forums.amd.com/game/messageview.cfm?catid=260&threadid=115857](http://forums.amd.com/game/messageview.cfm?catid=260&threadid=115857)

---

### Post by photographerHU on 2009-08-29
Hi (again),
Im new in ubuntu, so Im just interest, that is the following is possible:
[http://ubuntuforums.org/showthread.php?t=1009502](http://ubuntuforums.org/showthread.php?t=1009502)
because (I saw this on the ati`s homepage) ATI Catalyst&#8482; Display Driver support openSUSE....!!!!! (NO ubuntu, just "Red Hat Enterprise Linux suite, Novell/SuSE product suite"
So my question is: is it possible to make an "ubuntu SUSE mixture"? Get the xorg, driver and support from SUSE and still use ubuntu. Like this, get the ati card work?

---

