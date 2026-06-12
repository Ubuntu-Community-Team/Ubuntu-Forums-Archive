---
title: "Installing ATI Drivers on Ubuntu 7.04 guide"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by Gorlist on 2007-05-09
This is a small guide covering the methods I use to install latest ATI drivers on a fresh install of Ubuntu 7.04. 

The reason I have wrote this guide is ive found using the xorg-fglrx drivers through the package manager left me with screen artifacts for my ATI Radeon x800.

Firstly I am new to Linux and take **NO** responsibility if any of the methods listed below cause hardware damage or data lose!

Please read the full post before attempting to follow the guide.. 

**[COLOR="Red"]**Warning**[/COLOR]** - if driver installation fails completely you may find Ubuntu Desktop will fail to load - if this is the case it will require you to restore your xorg.conf file via a command line (found in post 2, thanks to adromidon) - or load the Ubuntu Safe Mode Kernal??

---------------------



[COLOR="Sienna"]**1)** [/COLOR]Firstly download & Install latest version of Envy  - [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32395&stc=1&d=1178956632[/IMG]

Envy when used later on in the guide will automatically download, compile & install the latests ATI drivers for you.


---------------------
[COLOR="#a0522d"]**2) **[/COLOR]For people who prefer to use a file browser rather than command line, Right Click on your desktop and select "Create Launcher...".   With the following panel leave everything as default accept enter a suitable name (e.g. Administrator - Nautilus", and for the Command tab enter "**sudo nautilus**" (without quotes)  and click OK.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32396&stc=1&d=1178956689[/IMG]

This will allow you to browse your computer and edit files as the root user.

Double click on the newly created Icon, and when terminal appears enter your password accordingly  (if you close the Terminal it will also close the sudo browser) - after entering the password Nautilus will now  open.


---------------------
[COLOR="#a0522d"]**3)**[/COLOR]  Using the admin Nautilus browser click on "File System" located on the left menu, then double click on the folder called "etc", once Nautilus has updated find and open the directory "X11".

You will then find a number of folders and files listed in the X11 directory, firstly copy and paste your xorg.conf file adjusting the name to xorg.conf_backup (if something goes wrong you can always roll back to this file). 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32397&stc=1&d=1178956732[/IMG]

Open the original "xorg.conf" file by double clicking (geEdit will then load) and find the "Device" Section (will list your graphics card name, current driver (ati) and BusID).

Firstly replace "**ati**" with "**fglrx**" and below add the following:
[B]
	Option 		"VideoOverlay" 		"on"
  	Option 		"OpenGLOverlay" 	"off"
  	Option 		"UseInternalAGPGART" 	"no"[/B]

Below is an example of my updated xorg.conf for the device section:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32398&stc=1&d=1178956732[/IMG]

Lastly add the following to the bottom of the file:

[B]Section "Extensions"
        Option  "Composite" "0" 
EndSection[/B]

Then **save** xorg.conf.


---------------------
[COLOR="#a0522d"]**4)**[/COLOR] Open Envy through your Applications/System menu and select "Install ATI Driver" - a new terminal style windows will then appear and Envy will go to work.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=32399&stc=1&d=1178956732[/IMG]

Once the driver has been successfully downloaded and installed it will ask whether you wish for Envy to update/adjust your "xorg.conf", make sure you select **NO** (it tends to cause errors in the xorg.conf file),  another popup panel will then appear asking your to either Reboot now, or Later - making sure you have all onscreen items saved select "Reboot Now". 


---------------------
[COLOR="Sienna"]**5)**[/COLOR] After rebooting hopefully your Desktop will have loaded, and Ubuntu should prompt you with a "Restricted Driver warning", double click on the icon and make sure the ATI driver is enable, and close the window. 

Open a terminal and type in "fglrxinfo",  if the driver installation was successful similar to the following should now appear:

[B]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Platinum Edition
OpenGL version string: 2.0.6458 (8.36.5)[/B]

if not the following will appear and the guide was unsuccessful:

[B]display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)[/B]


---------------------
**Other Notes*** [LIST]
[*]You may find the second time you reboot, Ubuntu will reset to the Mesa OpenGL render, this is due to the operating system automatically using a backup xorg file which is generated by Ubuntu itself; you will find this in the X11 directory and will be called, as you can guess :), xorg and have a random generated number within its name, either delete or adjust to match your primary config. 

[*]Please remember when the next major Ubuntu release takes place, use Envy to uninstall the ATI driver before upgrading.

[*]When newer drivers are made available by ATI, I believe you can simply use Envy to uninstall, then reinstall the drivers, and it simply download and compile the latest version (unconfirmed method?).
[/LIST]


Good luck!

---

### Post by adromidon on 2007-05-11
This is a great program I tried to download and install the ATI driver manaully and was presented with several errors stating that x.org is not the same version the driver was compiled for with this program i did not get the error at all and it went flawlessly as far as the install goes I am about to restart now and test the configuration.

also just to add if someone was looking for a command to paste into the terminal to backup the xorg.conf prior to editing you can use the command below

```

sudo cp /etc/X11/xorg.conf ~/xorg.conf_backup

```

that will copy the file into a new filenamed xorg.conf_backup in your home directory of the user your logged in as the "~" is a short cut that points to the home directory of the user currently logged in.

Also run the following commands after word so you can access the file if you want to be able to edit it

```

sudo chown username:username ~/xorg.conf_backup
sudo chmod 774 ~/xorg.conf_backup

```

in the above code username should be replaced with your current user name (I.E the one your logged in as) this line assigns your user ownership over the file

the second line gives your user and the group your in editable privileges over the file

You will have to enter your password for most of these tasks as they are administrative shell commands. Once you do this you will have a full copy of your xorg.conf file that is fully editable by you.

---

### Post by hedonistic.heathen on 2007-05-11
I followed your directions and everything went as you said, when I rebooted a second time, as you indicated might happen, Ubuntu reset to the Mesa OpenGL render.  I deleted the automatically generated backup and rebooted, but when I issue "fglrxinfo", the Mesa OpenGL information is there and not the ATI.  I've triple checked /etc/X11/ to make sure there isn't a hidden backup that's being used and I've rebooted several times, so I'm not sure why it isn't working.

After the first reboot it was definitely working - the restricted driver warning popped up and "fglrxinfo" was ATI.  

Any suggestions on what I might be missing?

---

### Post by Gorlist on 2007-05-12
So at the moment in the X11 directory you only have the xorg.conf file, and your xorg.conf_backup?

My Ubuntu currently does have an active backup called "xorg.conf_backup_200705091436", all ive done is edited the file to match my primary xorg.conf and rebooted and since then its work fine.

As you know the driver functions correctly (which is good) when enabled, so its certainly xorg related.

Perhaps someone else who knows more can post?

---

### Post by hedonistic.heathen on 2007-05-12
So, my problem stems from the fact that I don't really know what I'm doing when I'm making these changes...

In short the ATI driver wasn't loading because I had changed my xorg.conf file from <Options "Composite" "0"> to <Options "Composite" "Enable"> based on advice from another post.

I changed this setting because when I try to run beryl I get an error that says <"No composite extension">, and I'm guessing that's because I'm disabling it in the xorg.conf file when I set the value of "Composite" to "0".

Also, when I try to enable desktop effects via System>Prefs>DesktopEff I get an error that says "The composite extension is not available".

My ultimate goal here is to make sure my ATI driver is installed (i.e. I'm getting the most out of my video card) and to get beryl up and running.


Any suggestions would be appreciated.

---

### Post by Gorlist on 2007-05-12
The current ATI drivers don't support Composite Desktop at the moment - and thats reason why its disable in xorg.conf (and also why the error appears when you go to Desktop Effects).

How to resolve the Mesa issue I don't know at the moment, unfortunately ive just made a mistake my end and reset my xorg and now also have mesa stuck on. 

It has been suggested that its something to do with the kernels/modules not being update.

Regards,

---

### Post by adromidon on 2007-05-12
> **Gorlist said:**
> So at the moment in the X11 directory you only have the xorg.conf file, and your xorg.conf_backup?

My Ubuntu currently does have an active backup called "xorg.conf_backup_200705091436", all ive done is edited the file to match my primary xorg.conf and rebooted and since then its work fine.

As you know the driver functions correctly (which is good) when enabled, so its certainly xorg related.

Perhaps someone else who knows more can post?

I have that file as well i just like to make my own backup file prior to changing it i think it gives me extra security :) Also i find having a backup outside the folder i am working in allows for me to have the file backedup in two places and with a file that is as important as the xorg.conf file  i think that is a good idea.

---

### Post by hedonistic.heathen on 2007-05-12
So, to state the obvious (just not obvious to me), without the ATI driver installed I'm not using my graphics card to it's full potential (i.e. I couldn't run google earth), but with the driver installed I can't run beryl, b/c the current driver doesn't support compositing.

So, just to clarify, there's no way to run beryl with an ATI X800 series graphics card?  Or is there an alternative method to installing a driver?  I keep reading about the open source vs proprietary (maybe not the right word) ATI driver...anyone care to put the difference into layman's terms?


As a side note, after installing and uninstalling the driver a couple times now, it seems like the fan on my graphics card is running at 100% all the time with the new driver installed.  It seems to be much quieter without the driver installed.  I might just be paranoid though, anyone else noticed this?

---

### Post by adromidon on 2007-05-12
> **hedonistic.heathen said:**
> So, to state the obvious (just not obvious to me), without the ATI driver installed I'm not using my graphics card to it's full potential (i.e. I couldn't run google earth), but with the driver installed I can't run beryl, b/c the current driver doesn't support compositing.

So, just to clarify, there's no way to run beryl with an ATI X800 series graphics card?  Or is there an alternative method to installing a driver?  I keep reading about the open source vs proprietary (maybe not the right word) ATI driver...anyone care to put the difference into layman's terms?


As a side note, after installing and uninstalling the driver a couple times now, it seems like the fan on my graphics card is running at 100% all the time with the new driver installed.  It seems to be much quieter without the driver installed.  I might just be paranoid though, anyone else noticed this?

Not at all the driver is merely a way to get your card to work if it was not allready detected by Ubuntu

Infact in most cases if your card's native resolution is supported and your card works to your likeing with the Ubuntu default driver then I would say hold off on the ATI driver.

Also to note desktop effects are based on technowledies that the Linux version of the ATI proprietary drivers have issues with alot of the time such as Composite and AIGLX. This does not neccesarily mean you can not use these features with the ATI drivers but in most cases you will have to disable them to get your ATI driver working to its optimum.

Some reasons for installing the ATI driver may include
[LIST]
[*]Resolution can not reach levels your card can support
[*]Ubuntu does not see to have clean and clear graphics with the Ubuntu driver
[*]You just like using vendor drivers to ensure you get the right ones
[/LIST]

Truth be known Ubuntu does a reall good job of accurately detecting cards and applying the correct driver but as mentioned above you could have problems that may or maynot go away with the ATI driver

Not sure about the fan issue however never heard of that but I am takeing a shot in the dark here. maybe it is something to do with the ATI driver being able to more accurately control your Card Fan.

---

### Post by Enverex on 2007-05-12
Envy doesn't work for me:

> python pulse.py ati 
root@Cipher:/usr/share/envy# python pulse.py ati 
rm: cannot remove `*.deb': No such file or directory
Ubuntu Feisty 32bit
rm: cannot remove `/lib/linux-restricted-modules/.nvidia*': No such file or directory
Your graphic card has been detected as a ATI Mobility / Radeon 9000
Your graphic card is supported by the legacy Driver
ENVY ERROR: ATI's legacy driver does not support your operative system
root@Cipher:/usr/share/envy#

I guess I can count myself in the "screwed by ATi crowd" eh?

---

### Post by Enverex on 2007-05-12
> **adromidon said:**
> Infact in most cases if your card's native resolution is supported and your card works to your likeing with the Ubuntu default driver then I would say hold off on the ATI driver.

2D and moreso 3D performance with the official driver is exponentially better than it is with the open driver.

---

### Post by adromidon on 2007-05-12
> **Enverex said:**
> Envy doesn't work for me:



I guess I can count myself in the "screwed by ATi crowd" eh?

not neccesarily

your card may not be supported by the ATI drivers in the Envy program try going to [www.ati.com](www.ati.com) and download them directly follow their install steps

it is harder to install but may work for you

---

### Post by Enverex on 2007-05-13
> **adromidon said:**
> not neccesarily

your card may not be supported by the ATI drivers in the Envy program try going to [www.ati.com](www.ati.com) and download them directly follow their install steps

it is harder to install but may work for you

That wont work either because, as Envy pointed out, the old drivers that I'd have to use don't work with the newer versions of XOrg.

---

### Post by adromidon on 2007-05-13
Hmm well if this was a red hat distro i would recomend enabling the livna repo and get their drviers but i am not sure what an Ubuntu alternate would be

I use both distros so i have had my fair share of trying to get my card to work properly in both

---

### Post by tseliot on 2007-05-13
> **Enverex said:**
> That wont work either because, as Envy pointed out, the old drivers that I'd have to use don't work with the newer versions of XOrg.
You're right.

---

### Post by wyth on 2007-05-13
Like Enverex, I have an ATI 9000 gfx card.

I haven't updated to Feisty because of the ATI issues, so let me just get this straight:

*If* you have an ATI 9000 or older card, you *can't* use the proprietary drivers for Feisty.

Since the proprietary drivers work "exponentially better" than the open source drivers, if we want decent 2D and 3D performance, we're better off leaving Feisty behind, and might be perpetually stuck at Edgy.

Is this correct?

---

### Post by Enverex on 2007-05-13
More problems caused by that: The older the ATi drivers the more issues they had, added to the fact that you're using older versions of everything which in itself causes more issues too (no bugfixes, performance enhancements, new features, etc).

---

### Post by wyth on 2007-05-13
At least on my end, everything works great *except* that damned card.  I tried out Feisty and loved it, but the open source driver just wasn't enough, and it was affecting my work.  So I had to go back to Edgy.

The other solution would be if the open source drivers were as effective as the proprietary, but that's not the case at this point.  If so, I'd be back in Feisty finery.

---

### Post by drizzzt on 2007-05-13
Most likely those guides would help:
1. First install latest driver from ATI.com [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").
2. Then follow steps in the following one to setup Beryl [Beryl/ATI/Feisty]("https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29%7C%28ati%29").

---

### Post by Gorlist on 2007-05-14
Still, does anyone know why Ubuntu still uses Mesa even though the drivers are enabled and setup correctly in xorg.conf?

** Ive just checked my Xorg.0.log and the only area I have noticed is:

(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

---

### Post by Enverex on 2007-05-14
> **drizzzt said:**
> Most likely those guides would help:
1. First install latest driver from ATI.com [BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").
2. Then follow steps in the following one to setup Beryl [Beryl/ATI/Feisty]("https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%28beryl%29%7C%28ati%29").

Again that wont work, please people, check your facts, you'll break his system.

He has an R250 (Radeon 9000) which ISN'T supported by FGLRX and hasn't been for some time.

---

### Post by Desperado2006 on 2007-05-14
Hello! I that's the best guide of all

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

---

### Post by Gorlist on 2007-05-15
Its the reason I wrote this guide :) as that one only covers the xorg drivers via the package manager rather than the latest ATI using Envy.

Regards,

---

### Post by Canesfan2020 on 2007-05-15
Whenever I install the latest driver 8.36.5(?) I think it is it borks my video and AGP bus is stuck at 0 instead of 8x like its supposed to be.

---

### Post by adromidon on 2007-05-16
well crapola it seems that until ATI goes through on their promise to make the ATI drivers open source that some people will have a heck of a time getting their cards to work :(

---

### Post by MrTrumpets on 2007-05-20
The original instructions worked like a charm for me.  Thank you!

It may help everyone to know that I have the exact same card. ;)

---

### Post by Dropknee on 2007-05-21
This guide work great, but is sad than this driver still have the load fan, overheating bug, the ATI open source driver don't have this problem. I guess, but not sure this bug is only with the X800 series. This problem affect me very bad because I have a Shuttle XPC (Gaming small form factor) and with this overheating bug in this small case, the card is going to melt, I guess I'm going back to open source driver.

---

### Post by randoy on 2008-02-07
I'm having a tough time here... and obviously a complete newb with Ubuntu.  I'm currently running 7.04, Intel Pentium 4, 1.8ghz processor, 768mb of ram, and currently using a Nvidia MMX440, 64mb video card. 

I just got the ATI Radeon 9000 series today and put it in my computer.  First thing thing I see when I reboot is "No device detected" and it fails to load Ubuntu.  Do I have to start this guide before I physically install the card? Any help would be greatly appreciated, and please excuse my ignorance.

Dan

---

### Post by Gorlist on 2008-02-08
Im slightly out of date on the current route on graphics drivers, specially since 7.10 has been released - but yes I would assume you need to update xorg via the command line to use ATI drivers before the desktop would load - so you could try adjusting it to just "ati" so its using the opensource ones??

Also im sure you can let Ubuntu reset your Xorg? but I can't remeber the command off hand...

---

### Post by randoy on 2008-02-08
Thanks for the reply!  

I think what I may end up doing, since I kinda suck with this kind of thing, 
(read:completely useless), Is trade my ATI card for an equivalent Nvidia card.  

My current card, as I mentioned in my earlier post, is a Nvidia.... and the installation was very smooth.  Kinda sucks that it has to be that way, but what can you do?

Thanks again,

Dan

---

### Post by Shadowmeph on 2008-02-09
> **Dropknee said:**
> This guide work great, but is sad than this driver still have the load fan, overheating bug, the ATI open source driver don't have this problem. I guess, but not sure this bug is only with the X800 series. This problem affect me very bad because I have a Shuttle XPC (Gaming small form factor) and with this overheating bug in this small case, the card is going to melt, I guess I'm going back to open source driver.
ALthough this is an old post I just would like to say I have the exact same card and same issuse I read somewhere that there is a way to set the fan differently but being a noob at linux I am not sure of how it has something to do with typing in this aticonf --set-powerstate=( then a number but first you have to find out your  available settings "aticonf --lsp or something like that I am not sure of this because I tried and like I said being a noob at this I couldn't get it to work but I am hoping that some one else can figure it out because I don't want to melt my x800 card :(

---

