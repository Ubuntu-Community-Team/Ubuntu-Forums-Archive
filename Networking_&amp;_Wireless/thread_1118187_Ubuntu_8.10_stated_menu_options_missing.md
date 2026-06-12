---
title: "Ubuntu 8.10 stated menu options missing"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by drrdf on 2009-04-06
In the Help attached to Ubunutu 8.10 it states that there is an option in the menu path: System/Administration/Windows Wireless Drivers. this does not appear on my installation of Ubuntu 8.10. It also states that ndisgtk is included in Ubuntu 8.10 and may be accessed in the Synoptic Package Manager, but this is not present in my installation of Ubuntu 8.10. I have attempted to install ndisgkt from a CD but the package manager greys out and will not recognise it. I cannot thus get Ubuntu to recognise my wireless card (which is a Dynamode with Windows drivers). I have checked in the terminal and the PCI card is recognised as unclaimed. 

Can someone please inform me what the problem is and what I have to do to install the windows driver?

---

### Post by drrdf on 2009-04-13
Hi all you guys out there with Ubuntu knowledge. Is there no one that can explain to me why these stated options are not present in Ubuntu 8.10. Is it perhaps that the developers are working on adding these options, but they were not actually included in 8.10, although the associated Help assumed that they were there, and had wrongly anticipated the addition? 

Please tell me if you now the answer to this. Thanks.

---

### Post by drrdf2 on 2009-06-23
[CENTER][FONT=AlBattar][SIZE=4]_**Installing a wireless card in Ubuntu 9.04**_[/SIZE][/FONT][/CENTER]
 

 [FONT=AlBattar]Installing a wireless card in Ubuntu seems to be much more difficult than with many other Linux distros. It seems this is due to two reasons. Firstly the developers of Ubuntu, whilst being very clever to be able to develop such a good OS are not good at communicating, and also do not think logistically operationally, in terms of the chronological sequence, when one is installing the OS from scratch, with no internet connection on a PC because the wireless card is not working at initial installation.  They thus seem to think or imply that you need to download ndistgk from the internet using the Synaptic Package Manager or other means. They completely fail to mention that in fact it is included on the distro CD, nor how you are supposed to access that and install it, so as to be able to use the MS Windows drivers, which are almost always the only ones supplied with all available devices. What most novices to Linux (even those who may be very experienced with MS and other OSs ) need is clear instructions for what you actually have to do. So far such do not seem to have existed, (I have certainly not been able to find them) and even those users who have managed to work out by hard experience what to do, and have succeeded, where they have attempted to help others by posting in forums, do not seem to fully understand what they have done, or are unable to clearly communicate this to others. Indeed some seem to have made things even worse by what they have posted in forums, supposedly to help, since what they suggest does not work, either because it is downright wrong, or because it does not include all the elements of the necessary action! Additionally the stuff in the Ubuntu &#8220;Help&#8221; is inaccurate, most of the time supposed &#8220;options&#8221; in the Ubuntu menus and Help  do not exist, and/or do not work. [/FONT] 
 

 [FONT=AlBattar]After much suffering as a direct result, I venture here to offer a clear guide, for novice Ubuntu users as I was. Although I posted on the Ubuntu forum here about these problems I did not get even one response![/FONT]
 

 [FONT=AlBattar]It is unlikely that if you try to use the menu routes existing in Ubuntu to install a wireless card and try to get your wireless connection going that it will work, unless you are extremely lucky and happen to have one of a few specific cards which may work almost instantly with Ubuntu. You will therefore have to use a more difficult process. However, if it is explained clearly it is not really very difficult, and it should work with all Ubuntu-compatible wireless cards.  [/FONT] 
 

 [FONT=AlBattar]First fit your wireless card in the PC.  It is best to do this before you install Ubuntu. When the OS installation is completed and you have re-booted replace the Ubuntu distro cd in the cd drive. Then you must select the menu path (from the top tool bar): &#8220;System/Administration/Software Sources&#8221;. You will then have to enter your user password to authorise a Root authority change. You will then have the &#8220;Software Sources&#8221; dialogue box open. Make sure the first tab &#8220;Ubuntu Software&#8221; is selected. At the bottom of this dialogue box there should be two similar options with tick boxes &#8220;Cdrom with Ubuntu XX.X `Version name' Officially supported Restricted copyright&#8221;. Click to put a tick in the top one of these two option boxes. Then click the &#8220;Revert&#8221; button at the bottom. Close this dialogue box. This has then set the system default to point to CD ROM as the SW source.[/FONT]
 

 [FONT=AlBattar]Open a Terminal window: select the menu path &#8220;Applications/Accessories/Terminal&#8221; (from the top tool bar). Enter into the terminal &#8220;sudo apt-get install ndisgtk&#8221;. You should then see a dialogue in the Terminal window similar to the following, (you will have to enter your user password again herein):[/FONT]
 

 [FONT=AlBattar]**xxxx@XXXXX:~$ sudo apt-get install ndisgtk**[/FONT]
 

 [FONT=AlBattar]**[sudo] password for xxxx: **[/FONT] 
 

 [FONT=AlBattar]**Reading package lists... Done**[/FONT]
 

 [FONT=AlBattar]**Building dependency tree       **[/FONT] 
 

 [FONT=AlBattar]**Reading state information... Done**[/FONT]
 

 [FONT=AlBattar]**The following extra packages will be installed:**[/FONT]
 

   [FONT=AlBattar]**ndiswrapper-common ndiswrapper-utils-1.9**[/FONT]
 

 [FONT=AlBattar]**Suggested packages:**[/FONT]
 

   [FONT=AlBattar]**ndiswrapper-source**[/FONT]
 

 [FONT=AlBattar]**The following NEW packages will be installed**[/FONT]
 

   [FONT=AlBattar]**ndisgtk ndiswrapper-common ndiswrapper-utils-1.9**[/FONT]
 

 [FONT=AlBattar]**0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.**[/FONT]
 

 [FONT=AlBattar]**Need to get 0B/79.1kB of archives.**[/FONT]
 

 [FONT=AlBattar]**After this operation, 676kB of additional disk space will be used.**[/FONT]
 

 [FONT=AlBattar]**Do you want to continue [Y/n]? y**[/FONT]
 

 [FONT=AlBattar]**Selecting previously deselected package ndiswrapper-common.**[/FONT]
 

 [FONT=AlBattar]**(Reading database ... 101998 files and directories currently installed.)**[/FONT]
 

 [FONT=AlBattar]**Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.53-2ubuntu1_all.deb) ...**[/FONT]
 

 [FONT=AlBattar]**Selecting previously deselected package ndiswrapper-utils-1.9.**[/FONT]
 

 [FONT=AlBattar]**Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.53-2ubuntu1_i386.deb) ...**[/FONT]
 

 [FONT=AlBattar]**Selecting previously deselected package ndisgtk.**[/FONT]
 

 [FONT=AlBattar]**Unpacking ndisgtk (from .../ndisgtk_0.8.4-1_i386.deb) ...**[/FONT]
 

 [FONT=AlBattar]**Processing triggers for man-db ...**[/FONT]
 

 [FONT=AlBattar]**Setting up ndiswrapper-common (1.53-2ubuntu1) ...**[/FONT]
 

 [FONT=AlBattar]**Setting up ndiswrapper-utils-1.9 (1.53-2ubuntu1) ...**[/FONT]
 

 [FONT=AlBattar]**Setting up ndisgtk (0.8.4-1) ...**[/FONT]
 

 

 

 [FONT=AlBattar]**xxxx@XXXXX:~$ **[/FONT] 
 

 

 [FONT=AlBattar]The wrapper package ndisgtk should now be installed in your system. Remove the Ubuntu distro cd from your drive and put the cd with the MS Windows drivers (supplied with your wireless card) into the cd drive. Now select the menu path (from the top tool bar) &#8220;System/Administration/Windows Wireless Drivers&#8221;. (It seems very strangely that this menu option is not always displayed? It seems to be displayed only once you have successfully installed the ndisgtk package into Ubuntu?) A dialogue box for you to enter your user password will then be displayed. Enter your password and you will probably then get an error  message &#8220;Unable to see if hardware is present&#8221;. If you receive this message ignore it and click on the &#8220;OK&#8221; button. You will then see a dialogue box &#8220;Wireless Network Drivers &#8230;.    Currently Installed Windows Drivers&#8221;.  Click on the button &#8220;+ Install New Driver&#8221;. You will then see a dialogue box &#8220;Install Driver&#8221;. Click on the &#8220;Location&#8221; field, then a &#8220;Select inf File" box will be displayed. Click on the appropriate folder on your driver cd and select the appropriate info file for your card chip set. Click on the &#8220;Open&#8221; button. When you have selected the appropriate info file the &#8220;Select inf File&#8221; box will close and you should see the &#8220;Wireless Network Drivers &#8230;.    Currently Installed Windows Drivers&#8221; box again with the required info file entered in the &#8220;Location&#8221; field. Click on the &#8220;Install&#8221; button.  You should then see your required info file displayed in the field at the left-hand side of the &#8220;Wireless Network Drivers &#8230;.    Currently Installed Windows Drivers&#8221; box, with &#8220;Hardware present: Yes&#8221;. Success &#8211; your wireless card is working. [/FONT] 
 

 [FONT=AlBattar]If you have a secure wireless connection you will then have to enter the required code (such as WEP) etc. Click on the network icon at the right-hand of the top tool bar, and then click on the network shown; you will then be able to set-up the security elements and you should then have your internet connectivity established. Congratulations &#8211; that was not too difficult, when it was explained properly, was it? [/FONT]

---

### Post by sandjkirkland on 2009-06-30
Okay now how do I black list a native driver that is trying to load?

---

