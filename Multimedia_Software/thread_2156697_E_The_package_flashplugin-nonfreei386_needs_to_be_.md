---
title: "????E: The package flashplugin-nonfree:i386 needs to be reinstalled, but????"
date: 2013-06-22
forum: Multimedia Software
---

### Post by H15 on 2013-06-22
OK i searched the web and found a few sites that talk about this problem and the all seem to have the same problem but they either dont post the solution or the posted solution dosnt work for me...When I try to install adobe flash player (Witch is suposed to come with crome) it soped mid install i had searched the web for a .deb pakage and found a bad one i guess so I tryed to reinstall it to no avail, so I tryed uninstalling software update and this is the problem:::

me@noneofyourbiz:/home/me$ sudo apt-get remove software update
[sudo] password for me: 
Sorry, try again.
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.
:::

I need help i cant use softwarecenter at all and i cant perg or even force perg it says there is no file by that name when i look up the logs there is an .postinst and a .premp log but i at best can only read them when I try to delet even as admin i am told i dont have rights. Do i need to unlock Root ?

FYI am useing ubuntu 12.04 LTS 64bit

---

### Post by newbie-user on 2013-06-23
You need to install adobe-flashplugin:
```
sudo apt-get install adobe-flashplugin
```
It is available in the partner repository.

To my knowledge, flashplugin-nonfree was retired a few releases ago. Also, Chrome has its own flash player, which is not the same as Adobe Flash.

---

### Post by H15 on 2013-06-27
1st thanx for the help but everything I have tryed has had this same problem....
*****************************************************************************************
H152@minenoturz:~$ su -- H15
Password: 
H15@minenoturz:/home/H152$ sudo apt-get install adobe-flashplugin
[sudo] password for H15: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR][COLOR=#ffff00]****[/COLOR]
H15@minenoturz:/home/H152$
******************************************************************************************
I am useing Ubuntu 12.04 I was as up to date as of the time of the issue but now when I try to update I get....
********************************************************************************************
H15@minenoturz:/home/H152$ yum update
[COLOR=#ff0000]The program 'yum' is currently not installed.  You can install it by typing:[/COLOR]
[COLOR=#ff0000]sudo apt-get install yum[/COLOR]
H15@minenoturz:/home/H152$ update
No command 'update' found, did you mean:
 Command 'xupdate' from package 'libxml-xupdate-libxml-perl' (universe)
 Command 'uupdate' from package 'devscripts' (main)
 Command 'lupdate' from package 'qt4-linguist-tools' (main)
 Command 'lupdate' from package 'qt3-dev-tools' (main)
update: command not found
H15@minenoturz:/home/H152$ sudo apt-get install yum
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR][COLOR=#ffff00]****[/COLOR]
H15@minenoturz:/home/H152$ uupdate
[COLOR=#ff0000]The program 'uupdate' is currently not installed.  You can install it by typing:[/COLOR]
[COLOR=#ff0000]sudo apt-get install devscripts[/COLOR]
H15@minenoturz:/home/H152$ sudo apt-get install devscripts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR][COLOR=#ffff00]****[/COLOR]
H15@minenoturz:/home/H152$
*****************************************************************************************
I cant install update or remove anything without getting this reply.

---

### Post by Bashing-om on 2013-06-27
H15; Hey ...

I will try and help you.
To understand what is going on, do in terminal:
```
apt-cache search flashplugin-nonfree
```
out put shows "flashplugin-installer" as well as "adobe-flashplugin" that only tells us what packages need to be installed.
do:
```
apt-cache depends adobe-flashplugin
``` That tells us both what we need to have installed as well as what we do not need to have installed.

So, let us see what you do have installed:
```
dpkg -l flashplugin-installer
dpkg -l adobe-flashplugin
```

once these are known we can remove and/or (re-)install that package the package manager is unhappy with.

We are working with 'buntu's package manager within 'buntu's software repositories; between what is installed, what is available. what you want installed, what it takes in get that package installed when there now exist conflicts and/or broken packages.

All can be fixed ...But I make no promises about the continued usage of adobe-flash. I have given up on flash usage in respect to FaceBooK , YouTube and other sites requiring the latest versions of flash in order to display video !

[INDENT][INDENT]what ya want to do ?[/INDENT][/INDENT]

---

### Post by H15 on 2013-06-27
1st thanx I am still super noobish, ok heres what happend......
**************************************************************************************************
**************************************************************************************************
[COLOR=#000000]H152@minenoturz:/home/$[/COLOR] su -- H15
Password: 
[COLOR=#ff0000]H15@minenoturz:/home/H152$ sudo apt-cache search flashplugin-nonfree[/COLOR]
[COLOR=#ff0000][sudo] password for H15: [/COLOR]
[COLOR=#ff0000]Sorry, try again.[/COLOR]
[COLOR=#ff0000][sudo] password for H15: [/COLOR]
[COLOR=#ff0000]flashplugin-installer - Adobe Flash Player plugin installer[/COLOR]
[COLOR=#ff0000]flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS[/COLOR]
[COLOR=#ff0000]adobe-flashplugin - Adobe Flash Player plugin version 11[/COLOR]
[COLOR=#ff0000]flashplugin-nonfree - Adobe Flash Player plugin installer[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$[/COLOR] apt-cache depends adobe-flashplugin
adobe-flashplugin
  Depends: wget
    wget:i386
  Depends: fontconfig
    fontconfig:i386
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libfontconfig1
  Depends: libfreetype6
  Depends: libgdk-pixbuf2.0-0
  Depends: libglib2.0-0
  Depends: libgtk2.0-0
  Depends: libpango1.0-0
  Depends: libx11-6
  Depends: libxcursor1
  Depends: libxext6
  Depends: libxrender1
  Depends: libxt6
  Suggests: firefox
  Suggests: konqueror-nsplugins
  Suggests: x-ttcidfont-conf
  Suggests: <msttcorefonts>
    ttf-mscorefonts-installer
 |Suggests: ttf-bitstream-vera
  Suggests: ttf-dejavu
  Suggests: ttf-xfree86-nonfree
  Suggests: xfs
  Suggests: libnspr4-0d
  Suggests: libnss3-1d
 |Recommends: adobe-flash-properties-gtk
  Recommends: adobe-flash-properties-kde
  Conflicts: <flashplayer-mozilla>[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: <flashplayer-mozilla:i386>[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: <flashplugin>[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: <flashplugin:i386>[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: <flashplugin-downloader>[COLOR=#FF8C00]<--[/COLOR]
    flashplugin-downloader:i386[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: flashplugin-downloader:i386[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: flashplugin-installer[COLOR=#FF8C00]<--[/COLOR]
    flashplugin-installer:i386
  Conflicts: flashplugin-installer:i386[COLOR=#FF8C00]<--[/COLOR]
    flashplugin-installer
  Conflicts: xfs[COLOR=#FF8C00]<--[/COLOR]
  Conflicts: xfs:i386[COLOR=#ff8c00]<--[/COLOR]
  Replaces: <flashplugin>
  Replaces: <flashplugin:i386>
  Conflicts: adobe-flashplugin:i386[COLOR=#FF8C00]<--[/COLOR]
[COLOR=#ff0000]H15@minenoturz:/home/H152$ dpkg -l flashplugin-installer[/COLOR]
[COLOR=#ff0000]Desired=Unknown/Install/Remove/Purge/Hold[/COLOR]
[COLOR=#ff0000]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/COLOR]
[COLOR=#ff0000]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/COLOR]
[COLOR=#ff0000]||/ Name           Version        Description[/COLOR]
[COLOR=#ff0000]+++-==============-==============-============================================[/COLOR]
[COLOR=#ff0000]un  flashplugin-in <none>         (no description available)[/COLOR]
[COLOR=#ff0000]H15@minenoturz:/home/H152$ dpkg -l adobe-flashplugin[/COLOR]
[COLOR=#ff0000]Desired=Unknown/Install/Remove/Purge/Hold[/COLOR]
[COLOR=#ff0000]| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend[/COLOR]
[COLOR=#ff0000]|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)[/COLOR]
[COLOR=#ff0000]||/ Name           Version        Description[/COLOR]
[COLOR=#ff0000]+++-==============-==============-============================================[/COLOR]
[COLOR=#ff0000]un  adobe-flashplu <none>         (no description available)[/COLOR]
[COLOR=#000000]H15@minenoturz:/home/H152$
*************************************************************************************************************
**************************************************************************************************************
Now I assume that the parts that are cusing the problem are the conflicts and if so then just spit-balling here but did I find my self a Firefox only .deb install ??? is that even a thing I need to look for next time ??? //I use Crome 
and one more I also assume --[/COLOR]Depends:-- are installd and --Suggests:--are optional pakeges and --Recommends:-- are pakeges that I need???

---

### Post by deadflowr on 2013-06-27
Are you having troubles getting the pepperflash plugin for chrome working?
Try looking in the chrome plugins menu
Open a blank tab and enter this
```
chrome://plugins
```
Sometimes you have to click the details button at the top right area, and then scroll down the list till you find the shockwave flash stuff.
Make sure it says disable, that means it's running.

As far as getting other flash variants installed
Flashplugin-nonfree is no longer available.
Adobe-flashplugin needs the partner repository enabled.
The easy solution is to install flashplugin-installer
```
sudo apt-get install flashplugin-installer
```
Flashplugin installer downloads the files directly from adobe, where as adobe-flashplugin is pulled from Ubuntu's maintained partner repos.

Best practice is to run an update on a system before doing any installs
```
sudo apt-get update
```

---

### Post by H15 on 2013-06-28
[COLOR=#ff0000]apt-get update[/COLOR] works so i guess I am updating but it still _***failed***_ and I _***still***_ ***_cant_*** watch youtube there is still _***no***_ flash/shockwave anything in crome.... and I am still getting the same reply to [COLOR=#ff0000][FONT=Ubuntu Mono]sudo apt-get install flashplugin-installer
:::[/FONT][/COLOR][COLOR=#ff0000]E: The package flashplugin-nonfree:i386 needs to be reinstalled, but I can't find an archive for it.[/COLOR][COLOR=#ffff00]****[/COLOR]

---

### Post by Bashing-om on 2013-06-28
H15; Hey, Mornin'n to ya ..

Ok... What is your browser.
If not FireFox or another derivative on that base, then you do not need to install any flash components.
1. Chromium: ...flash is built into it .. only requiring -if not on by default - ..typing "chrome://plugins" in the adress bar will indicate what plugins (flash) are enabled.

2. Google-Chrome: uses it's own application "pepper" for flash ,,,and is enabled by default. No action on your part should be required to enable that compenent.

My experience with flash: 
Adobe no longer supports linux with any updates to flash, only security fixes, thus FireFox is lacking;
Chromium also uses adobe flash and is lacking.
In order to view ALL flash content on the web, I installed Google-Chrome, on this system I am in reference to, is an old Nvidia graphics card with little onboard ram (512 MB)... and Chrome crashes in intense situations.

What it boils down to in my opinion is that if you are not running high end hardware and with ubuntu you are not running Google-Chrome as your web browser you will not as a "home" user have a good experience on the web in today's political situation with adobe's support structure and the requirement of high end hardware to meet peoples' demand for great graphics, that is presently a part of the web.

There are other browsers out there, many as a matter of fact ... most requiring a high level of knowledge and experience to install and operate in today's world.

That all said ... do we need to "remove" all traces of adobe flash ... and (re-)install Chromium ? OR maybe see about installing Google-Chrome.... beyond version 12.04 is a bit of a challenge, as Google's browser still depends on an old library and must be installed via Google's ppa. In order to do so one has to obtain the proper security keys from the server.


To the situation at hand; To remove adobe flash; We do not know how deeply embedded it is into the system, What I suggest we do in order to proceed to remove it, is use the utility "synaptic" to see and remove components.

Else we can resort to terminal commands and try it as a "shotgun" approach to get rid of it... what effect that would have on chromium I do not know ... requiring most likely a (re-)installation of Chromium.....


It is your system, what do you want on it? What methods are you the more comfortable with in resolving this situation ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2013-06-28
Since there is no flashplugin-nonfree packages from the Ubuntu repos, as far as I can tell, did you try installing it through other means?
If so, you might need to use the dpkg tool to remove whatever is there.
Try
```
sudo dpkg --purge flashplugin-nonfree:i386
```
or variants of this, and see if it can clear out the problem app.

You can also look at former forum admin's bodhizazen's method for fixing very broken packages, which ironically in his example is the flashplugin-nonfree package
[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by H15 on 2013-06-28
Ok thx [COLOR=#000000]deadflowr

[/COLOR][COLOR=#000000][http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)
[http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)
[/COLOR][http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)[COLOR=#000000]
[/COLOR]
Thats the fix I need so thx deadflower and a big thx to [COLOR=#000000]bodhizazen for the instructions on fixing it... now only if i can get the stupid youtube working

[http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)
[http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)
[/COLOR][http://blog.bodhizazen.net/linux/apt...oken-packages/](http://blog.bodhizazen.net/linux/apt...oken-packages/)

---

