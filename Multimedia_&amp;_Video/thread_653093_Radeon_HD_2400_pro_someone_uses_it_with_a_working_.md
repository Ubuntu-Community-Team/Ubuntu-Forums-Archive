---
title: "Radeon HD 2400 pro: someone uses it with a working ati driver?"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by sloboda on 2007-12-29
Hi! This afternoon I tried to configure the video card (Ati Radeon HD 2400 pro) on a pc with ubuntu. I've read many documents, but doesn't work.
Has someone of you a driver that works on your ubuntu, for this video card?
If yes, please give me some links, that I'm not able to find any solution :-(

Thanks, and greetings from Italy.

Sergej

---

### Post by sandman772 on 2008-01-28
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Go there and download Envy. Works great.

---

### Post by forrestcupp on 2008-01-28
I have an HD 2600 and Envy didn't work for me for some reason.  I had to manually install the latest drivers from ATI.  [Here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) is a great How-to that explains how to install the latest binary drivers.

A word of warning.  Don't do the part that explains how to use the Restricted Drivers Manager.  The drivers it installs don't work with the HD series.  Go half way down the page to where it says "Install from ati.com."  The only thing about it, is you need to change the name of the driver to whatever the newest driver is called.  They have an old version in this how-to.

---

### Post by deegs on 2008-01-28
follow that link to envy. i have the exact same card (ati radeon hd2400 pro) and the only thing that worked was envy. incredibly easy for a noob like me.

---

### Post by aardfark on 2008-01-29
I'm really screwed here...  (not surprising as I'm new to Ubuntu)

I'm on a brand-new install of Gutsy trying to install an ATI 2400 Pro, and nothing has been working.

I've tried installing the .run package from ATI's site, installing via terminal from ati.com, I've even tried a total re-install then loading Envy, and I still get a black screen after reboot.

I just got a new widescreen monitor, and the best I can get is the default settings (1280x1024 with crap for colors).

Anybody got any ideas?

(please?)

---

### Post by forrestcupp on 2008-01-29
> **aardfark said:**
> 

Anybody got any ideas?

(please?)

Did you try installing ATI's drivers according to the instructions in the link in my previous post?  I had the same trouble you are having with Envy and the Restricted Drivers manager, but when I followed the instructions in that link, it worked.  Make sure you do everything I said in my previous post.

---

### Post by aardfark on 2008-01-29
> **forrestcupp said:**
> Did you try installing ATI's drivers according to the instructions in the link in my previous post?  I had the same trouble you are having with Envy and the Restricted Drivers manager, but when I followed the instructions in that link, it worked.  Make sure you do everything I said in my previous post.

Yeah, I used the instructions on that page (specifically [these instructions]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-117effcb5f0fbe8e10f40881bff1dbf7824a77b0"))

However, I'm now realizing that was probably after I had followed the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way")


I've since performed a full system re-install, so I'll give that another shot when I get home. 

Any idea if the recent catalyst 8.1 drivers are what may be causing the problem?  I was hoping that maybe a previous version might help, so I've downloaded the 8.42.3 driver, and I was planning on trying that version out when I get home tonight.

---

### Post by aardfark on 2008-01-30
So I finally got the 8.42 driver working, but movement on the screen is incredibly jittery - even just scrolling up and down on a page in Firefox, or moving a window.

Any recommendations?

---

### Post by terminal on 2008-01-30
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

+1 for above link .

Scrolling with firefox is a know problem with current ATI drivers ( i own hd2600 ) . Moving windows and all are quite ok for me . You also get flickering while watching movies in window mode :( .

Type fglrxinfo and see what is rendering graphics .

---

### Post by ScottLind on 2008-02-09
> **forrestcupp said:**
> I have an HD 2600 and Envy didn't work for me for some reason.  I had to manually install the latest drivers from ATI.  [Here](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) is a great How-to that explains how to install the latest binary drivers.

A word of warning.  Don't do the part that explains how to use the Restricted Drivers Manager.  The drivers it installs don't work with the HD series.  Go half way down the page to where it says "Install from ati.com."  The only thing about it, is you need to change the name of the driver to whatever the newest driver is called.  They have an old version in this how-to.

Hi. When I get to this point of the 'tutorial' it says: "No such file of directory."

> 
Then install the binary drivers:

[QUOTE]sudo dpkg -i fglrx-kernel-source_<version>.deb

Run the following command to install the Xorg driver

> sudo dpkg -i xorg-driver-fglrx_<version>.deb[/QUOTE]

Can you help me?

---

### Post by steefjeqv on 2008-02-10
Hi,

Why not try the open source driver ? It's still in development, but improvements are made due to the support of AMD.
Before you install it, first remove the ATI binary driver. 

It's in the Ubuntu repositories.

You can install it using Synaptic or just type in terminal :

sudo apt-get install xserver-xorg-video-radeonhd

Greetings,
Steven

---

### Post by inphektion on 2008-02-15
I have an optiplex 755 from dell.  It has an ATI HD 2400 Pro card. 
I've tried every link in this thread.  
I've installed the driver from the repo's, I've installed it from ati's site, I've followed a few different ways each time starting clean.  I've just now tried envy.
Every time I get zero errors during the build or install but on boot instead of seeing my login screen, the waiting circle freezes just as the login screen is sort of trying to come up and the background stays all white.  At this point it either freezes there or reboots.  I have to boot into rescue mode every time and restore my xorg.conf file that has vesa in it to boot again.
Speaking of which, that is painful since my bootloader is LILO.  Is there any way to switch my bootloader to grub so I can boot to command line without the rescue disk everytime?

---

### Post by grifoxx on 2008-02-19
> **ScottLind said:**
> Hi. When I get to this point of the 'tutorial' it says: "No such file of directory."



Can you help me?

I have got the same problem No such file or directory.

I also download the driver form the ATI site and tried to access it but it did not work either.

Does any body else have another suggestion?

Thanks a lot

---

### Post by kokotero on 2008-02-19
> **terminal said:**
> Scrolling with firefox is a know problem with current ATI drivers ( i own hd2600 ) .

Which drivers do you use? I have HD2600 too and have not obtaing to use fglrx properly, only vesa. Do you have direct rendering?

Thanks a lot

Eneko

---

### Post by MiniZiper on 2008-03-08
Me too.
I installed the ATI drivers with envy. but compiz is very jittery.
thanks to that... im still using windows >.<

---

### Post by Warmask on 2008-03-18
has anyone gotten the 2400 or 2600 to work properly yet??  This is annoying the piss out of me.

---

### Post by dootzky on 2008-03-19
damnit, I just bought brand new MSI Megabook EX610X-007EU, and it has HD2400, and I can't get it to work, I've tried default drivers, Envy (which crashes my Ubuntu on boot: gives only black screen, for ever.., and then I have to do dpgk-reconfigure xserver and get back stupid VESA drivers just to get back to graphic mode..), and it's still not working.

but i'm pretty sure this is DOABLE, i know a guy which did this with all MSI Megabooks he encountered, so I'm not quiting  on this one.

I'll hit you back here as soon as (if?) I get it working...

---

### Post by ykpaiha on 2008-03-19
I am ashamed of my answer:
I found the right way to have a proper ATI card working under Linux:
5 Months after a hard battle against 8.1, 8.2, 8.3..issues and a dead monitor (pushing some resolutions in xorg)
I killed my radeon 3850 for 100 Euro and bought a 8800gt
and guess what:!!
IT WORKS§§:lolflag:

---

### Post by dootzky on 2008-03-27
ok, after 4 days of torture, I made it!!

I've setup the latest stable ATI drivers with Envy, or by compiling them from ATI unofficial Wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way))

but now, even if I have great resolution, and everything looks perfect, I have no direct rendering. :( it's horrible!! it's very slow on ocassion, Gnome is working so-so, but KDE is literally choking to death. 

on fglrxinfo i still get fckin' MESA, instead of ATI, and I can't get it to work.

I've tried everything. RadeonHD open drivers, binary drivers, free drivers, Vesa, nothing works.

in restricted drivers my Ubuntu Gutsy Gibbon (7.10) doesn't see any ATI graphic card. on lspci I was getting "Unknown ATI card", but after:

**update-pciids**

I get normal result on LSPCI command: 

```

dootzky@freedom:~$lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 2400

```

but still - even if I made it through, and I have cool screen resolution on my MSI Megabook EX610X, my ATI Radeon HD 2400 is not working properly. 

please, can anyone give me a HINT or at least some hope that I'll be able to use it normally? or should I wait for 30 more days for Hardy Heron.. :P (8.04...)

cheers, hope this helped someone, and i hope someone will help me :)

---

### Post by dootzky on 2008-03-28
SUCCESS!!! I've got it to work, with fresh install of Gutsy Gibbon! :)
here's the forum link of my full post with all explanations!! 

[http://ubuntuforums.org/showthread.php?t=738592](http://ubuntuforums.org/showthread.php?t=738592)

Hope it helps someone!! :)
cheers,
dootzky
Serbian Ubuntu LoCo Administrator

---

