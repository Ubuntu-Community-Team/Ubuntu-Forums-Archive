---
title: "NEW_Rogers Rocket stick installation detailed method for newbies"
date: 2010-07-15
forum: Networking &amp; Wireless
---

### Post by JackAbear on 2010-07-15
[SIZE=4]**Rogers Rocket stick installation on UBUNTUSTUDIO 10.04  method for newbies.**[/SIZE]
 [SIZE=4]This really is not difficult and the only Terminal Cmd needed  is: [/SIZE][SIZE=4]** lsusb**[/SIZE]
 [SIZE=4]**As understood and explained by a Ubuntu newbie with one year of experience using the Stick with windows and lots of experience fixing my own endless windows XP problems.**[/SIZE]
 [SIZE=4]Using the following method, you will not need to install & tweak Wvdial  or Modeswitch, and it  is really much less complicated in the end, plus you will have a little monitor icon similar to Window's XP that shows whether you are online or offline. [/SIZE] 
 

 [SIZE=4]The stick will work the same as with windows xp, even though you don't have the rogers hook-up Software instaled.[/SIZE]
  [SIZE=4]My Rogers rocket stick is 668 3G HSPA ONDA technologies but this would most probably apply to most USB Rocket sticks like the 627,  636, sony Erickson 400.[/SIZE]
 

 [SIZE=4]This  easy method of getting online is meant for stand alone home PC desktop or laptop & UBUNTU STUDIO 10.04  **fresh installs**, not servers or home network installs (I've not tested ) I leave that to others more knowlegeable in those areas. [/SIZE] The reason  for this method is that UBUNtU STUDIO does not default install a broadband wireless connection manager. and even though the suggested files below are from an older distribution( 9.04) their immediate purpose is just to get you online, and then the update manager will immediatelly slate a couple of these files for removal as they will have become obsolete in the this new distro and will then automatically replace them with the required updated files to allow the Rocket stick work even better than it will at first. If your distro already has default install of Broadband wireless manager, you will not need to install these 8  files , instead just  do everything else suggested here, and it  should work just fine.

 

 [SIZE=4](I  took a couple of days & proof tested this method four times over on two PC's &  it worked as good as it ever was on Wind-hose Xp each time without fail.)[/SIZE]
 [SIZE=4]Tested twice with UbuntuStudio LUCID 64 and twice with the Lucid 32 bits version, if you already have the Package files listed below on a USB stick the complete OS install and getting online via Rogers usb stick will total about two hours of your time.[/SIZE]
 [SIZE=4]**Procedure:**[/SIZE]
 [SIZE=4][SIZE=4]**Step One**[/SIZE]**:** In order to install 10.04 ubuntuStudio without having an ethernet connection, cable or any internet connection at all for that matter, you SHOULD prevent the installation from trying to hook up  automatically to find updates during the install ,since it would fail...in order to do so, [/SIZE] 
 [SIZE=4]GO into the BIOS (F1) where you **disable** anything to do with networks, anything to do with "Lan", onboard motherboard modem, remove network card if you have something like that., 1394 ZTE modem, PCI modem?... if you have either one of those shown as abled, **disable it/them**.( the USB stick is stand alone, does not require them, and this should prevent the OS installation from defaulting to non existent services and from warnings, like "check your wires" " your modem is not present or defective,... installation aborting, important files missing, cannot continue,  cannot install grub etc...(all messages I observed in my first three atempts to install LUCID on my Compaq, and even on my other older HP a500n where I finally very easily installed the 32 bit version after disabling the above. [/SIZE] 
 [SIZE=4]The Rogers  modem wireless stick is also a usb memory stick, but you only just want the modem device part to be installed , so:[/SIZE]
 

 [SIZE=4]**MOST important:** The Rocket stick** should not be plugged in either,** as the install would undoubtedly find a driver for it as a usb mass storage, which would then be a pain to get rid of ...mass storage driver could then become default & would reinstall(or try to) every time you cold start the PC...hence creating a need for modeswitch.deb, which I now understand possibly offers only temporary internal switching solution in that case, and needs to be reused over again after every shutdown and restart. At least, that is the impression I got when I tried it.[/SIZE]
 

 [SIZE=4][SIZE=4]**Step Two:**[/SIZE] I'm assuming you have an ordinary memory stick, + another PC, linux or windows or MAC that is online, or at least, can ask a friend who has one, .[/SIZE]
 
[LIST=1]
[*][SIZE=4]Go online to:      [/SIZE][SIZE=4]**packages.ubuntu.com **[/SIZE]
[/LIST]
   [SIZE=4]Click on  the  **Jaunty 9.04** distro(trust me), and, on the next page got to the bottom, center, and click "**ALL Packages**" [/SIZE] 
 [SIZE=4]depending on your connection speed, wait for the long list to complete then locate & download the following 8 deb packages in either 64bit or (386i) 32 bit versions according to your setup and save to desktop:[/SIZE]( you will see a rectangular box on the botom left of the page; that is where you chose 32 bit or 64 bit version to download, then pick a mirror on the next page)
 [SIZE=4]This will  all end up to  be much simpler than it looks, so if you've never done this kind of thing before, please &#8220;Bear&#8221; with me. (lol)[/SIZE]
 

 [SIZE=4]libnm-util1_0.7.1...deb[/SIZE]
 [FONT=Liberation Serif, serif][SIZE=4]libnm-glib0_0.7.1...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]libpolkit-dbus2_0.9-2...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]libpolkit-grant2_0.9-2...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]libpolkit2_0.9-2...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]libpolkit-gnome0_0.9-1...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]network-manager_0.7.1...deb[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]network-manager-gnome_0.7.1...deb     [/SIZE][/FONT] 
 

 [FONT=Liberation Serif, serif][SIZE=4](Be carefull not to download the same file names with &#8220;dev&#8221; in the name, as it is a developper version and is not what we want here. And do not substitute network admin.deb for network manager.deb or you will be missing the Broadband wireless section[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]______You have now installed your new OS and have just loged in.[/SIZE][/FONT]
 [SIZE=4][FONT=Liberation Serif, serif]**Now is the time to insert you Rogers stick **[/FONT][FONT=Liberation Serif, serif]in the USB port of your choice.[/FONT][/SIZE]
 [SIZE=4][FONT=Liberation Serif, serif]Next,  go to terminal and type:     [/FONT][FONT=Liberation Serif, serif]**lsusb **[/FONT][FONT=Liberation Serif, serif]        then press enter        (that's &#8220;L&#8221;susb not &#8220;i&#8221;susb)[/FONT][/SIZE]
 [FONT=Liberation Serif, serif][SIZE=4]and  if you did everything as I explained you should get something similar to the following:[/SIZE][/FONT]
 

 [FONT=Liberation Serif, serif][SIZE=4]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=4]Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=4]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub [/SIZE][/FONT] 
 [SIZE=4][FONT=Liberation Serif, serif]Bus 001 Device 003: [/FONT][FONT=Liberation Serif, serif]**ID 19d2:0017**[/FONT][FONT=Liberation Serif, serif] ONDA Communication S.p.A. [/FONT][/SIZE] 
 [FONT=Liberation Serif, serif][SIZE=4]Bus 001 Device 002: ID 05dc:a762 Lexar Media, Inc. [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=4]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=4]jack@10:~$ [/SIZE][/FONT] 
 

 [SIZE=4][FONT=Liberation Serif, serif]**0017**[/FONT][FONT=Liberation Serif, serif] tels you the stick does not have a mass storage device driver installed and you should be smilling at this point, for it [/FONT][FONT=Liberation Serif, serif]**is **[/FONT][FONT=Liberation Serif, serif]seen as a wireless modem....and the rest will be easy.[/FONT][/SIZE]
 [SIZE=4][FONT=Liberation Serif, serif](if you see a [/FONT][FONT=Liberation Serif, serif]**:2000**[/FONT][FONT=Liberation Serif, serif] instead, you have a memory stick instead of a modem, and you can assume something went wrong somewhere...remember that this method will work best with a fresh install.)[/FONT][/SIZE]
 

 [SIZE=4][FONT=Liberation Serif, serif]So, I will assume you did see  0017,  now close the terminal and  install each of the[/FONT][FONT=Liberation Serif, serif]** 8 **[/FONT][FONT=Liberation Serif, serif]DEB packages you have on a memory stick by simply transfering them to the desktop & double clicking  on each one [/FONT][FONT=Liberation Serif, serif]**in the order given**[/FONT][FONT=Liberation Serif, serif] on the list above and follow  the instructions of the instaler for each one..( if you get a prompt&#8221; dependency not satisfiable&#8221;, just go and get whatever dependency file is suggested by the instaler, at the same place you got the other ones, but I doubt this will happen on a fresh install from the 10.04 DVD which is what I used.[/FONT][/SIZE]
 

 [FONT=Liberation Serif, serif][SIZE=4]Once the 8 DEB's are installed, you are in business, shutdown your PC with the stick remaining in it...boot it up again, login,[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=4]& you will see your broadband monitor icon in the tray on the right with a red X in it, but still no connection...that is OK![/SIZE][/FONT]
 [SIZE=4][FONT=Liberation Serif, serif]Just [/FONT][FONT=Liberation Serif, serif]**restart (not shutdown) **[/FONT][FONT=Liberation Serif, serif]the PC at this point, login again. ( this step will be needed everytime you turn on the PC after shuting it off ...I suspect there is a strong security setting that shuts down the connection until you have loged-in properly then lets it connect upon restarting....for your protection...you will notice the stick does not drop out and go red at login after the restart.)[/FONT][/SIZE]
  [FONT=Liberation Serif, serif][SIZE=4]Right click on the monitor icon, enable networking, enable mobile broadband, enable notifications and click on edit connections, click on broadband, and in most cases for Rogers fill in the boxes as follows (if they have not already filled in automatically)[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]number; *99#[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]user name: wapuser1[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]password : wap[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]APN : internet.com[/SIZE][/FONT]
 

  [FONT=Liberation Serif, serif][SIZE=4]....that is all that is required.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]If you click &#8220;for all users&#8221; it will have an impact on security and you better know what you are doing before you do that...same with connect automatically....I left those unchecked until I get  time to figure that out, and it works just fine.[/SIZE][/FONT]
 [SIZE=4][FONT=Liberation Serif, serif]Now left click on the monitor icon and click one of the bold lines  [/FONT][FONT=Liberation Serif, serif]**mobile broadband  (gsm)connection **[/FONT][/SIZE] 
  [SIZE=4][FONT=Liberation Serif, serif]**Now if  your stick has a blue light to begin with and your reception is fair to good you should see the icon connecting by going around in circles five or six times**[/FONT][FONT=Liberation Serif, serif]...if it keeps turning but does not connect and times out check to see that the following are still there[/FONT][/SIZE]
  [FONT=Liberation Serif, serif][SIZE=4]*99#[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]user name: wapuser1[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]password : wap[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]APN : internet.com[/SIZE][/FONT]
  [FONT=Liberation Serif, serif][SIZE=4]if they are still there and you are not connecting, you are either too far away from the IP tower  or the tower his overloaded with traffic and your connection is too slow to engage a connection, or the stick is getting too hot and shutting down to save itself (put a fan on it, when that happens, and it will happen often with this stick, ....multitude of possibilities here, and I think this is not the place to cover those & I have to end this  guide sometime...  [/SIZE][/FONT] 
 [FONT=Liberation Serif, serif][SIZE=4]**Last step: if all went well you should be online now**, so get your updates ( go to System/Administration/ update manager )and the files you had downloaded  from jaunty 9.04 will be updated to  10.04 along with everything else.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]Got it?[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]Hope that worked for you, my two installs are fine after three days of use now! Though I had to do a service call to Rogers yesterday as their signal kept droping out and I was getting green light instead of blue, they reset the stick at their end and thing were back to normal after that...never rule out stick problems whether in Windows or in Ubuntu.[/SIZE][/FONT]
 [FONT=Liberation Serif, serif][SIZE=4]And I can honestly say, I know I will get along just fine with UBUNTU...WoW! So intuitive... I tip my hat to the developers,[/SIZE][/FONT]
 

 [SIZE=4]A bit of background: [/SIZE] 
  [SIZE=4]In order to solve anything, a solid understanding of the problem itself is a prerequisite, and I must thank forum members alexfish & mrpenguin and the references they provided in a few threads have certainly given me enough information  to be able to experiment and come up with this workable solution.[/SIZE]
 [SIZE=4]Background:  the way it was until I used this method)[/SIZE]
 [SIZE=4]During the past three weeks, I had experienced  pretty much all the problems I was reading about , at first installing the OS with the stick plugged in, only to find that the stick was showing-up as a usb mass storage device with the usual Rogers red icon( cmd lsusb ...resulting in 019d2 2000 instead of the desired 019d2 0017)...so I went through the wvdial and modeswitch procedures trying to hook it up and even though I did ,after two weeks of trying every which way, end up with somewhat of a connection, it would be gone the next time I booted up,..sometimes the  universal pass word WAP would dissapear, sometimes not, but the stick would have reverted to mass storage, and I would have to repeat the procedures, then updates would finally come in, and I would think " great, that's it, it works now"...then the next day I would put the stick back into my windows PC for a day, but when it  came back to Ubuntu, the stick wasn't even seen at all...and so on!...[FONT=Liberation Serif, serif]Sound familiar?[/FONT] [/SIZE] 
 [SIZE=4]That is why I kept looking for a better way, and posted the results[/SIZE]
 [FONT=Liberation Serif, serif][SIZE=4]Enjoy!, ...any problems just ask[/SIZE][/FONT].
 [FONT=Liberation Serif, serif][SIZE=4]Jacques Hebert
Still working fine after three weeks, as long as my reception from  the tower permits ; I live on the outskirts, in the mountains, and reception is often unstable whether I'm using the stick with Windows XP or UBuntu, makes no difference. Some days it's great ,some days very poor...that's life!
[/SIZE][/FONT]

---

