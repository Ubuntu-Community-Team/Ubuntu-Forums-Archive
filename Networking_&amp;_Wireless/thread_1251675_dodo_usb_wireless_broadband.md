---
title: "dodo usb wireless broadband"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by albert5 on 2009-08-27
1

---

### Post by reddingo90 on 2009-08-29
Hi [albert5]("http://ubuntuforums.org/member.php?u=901638"), I don't know if this will help but after searching and trying heaps of things I finally got my telstra usb modem to work by using this guys instructions. Hopefully you can adept it for dodo and if you're using ubuntu 9.04 ignore the 1st  part about modeprobe usbserial. Adrian
  	 	 	 	 	 	  [COLOR=#000080]_[w0lv3n]("http://ubuntuforums.org/member.php?u=805795")_[/COLOR] 
  	5 Cups of Ubuntu
 	[IMG]http://ubuntuforums.org/images/rank_2.png[/IMG] 		
 	 
[IMG]http://ubuntuforums.org/customavatars/avatar805795_1.gif[/IMG] 	  	
 	 
 	Join Date: Apr 2009
 	Location: Rockingham, Western Aus
 	Beans: 29  	
 	Ubuntu 8.10 Intrepid Ibex  	
 	 	[IMG]http://ubuntuforums.org/images/misc/im_msn.gif[/IMG] 	 **[AU] Bigpond 7.2 MF636 Mobile 	Broadband :: HowTo**  	
 	 
  	 	[I]Not sure if this should 	be in another area if there is a dedicated 'articles' 	board.

Writing this after pissfarting around trying to get my 	own mobile broadband to work.[/I]

This is a quick and simple 	'How-To' for using a **Bigpond MF636 Mobile Broadband Card** with 	**Ubuntu 8.10 Intrepid Ibex**

[SIZE=4]**Step 1**[/SIZE]
*We 	need to disable the autorun feature of the USB Modem. Basically it 	has three functions: Modem, Mini-SD Reader and Mountable ISO. When 	you plug it into Linux, the ISO is the only thing it sees. This is a 	problem because we dont want the ISO we want the Modem.*

**Load** 	up Windows - If you havent already installed your mobile card, then 	do so.
**Run** "Bigpond Wireless Broadband 2.0" - 	This is the mobile connection manager.
**Connect** to the 	internet.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Main.jpg[/IMG] 	

*At this point, you are connected to the internet, the 	modem is working. Now we need to send a command to the modem in 	order to disable the ISO function*

**Shift+Click** 	'Options' - This will load a slightly extended version of the normal 	options window.
**Click** the 'Diagnosis' tab.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Options.jpg[/IMG] 	

**Click** 'Modem Terminal' - This will open a direct 	terminal to the modem. Usually to do this you must have 	Hyperterminal or something similar - which is not standard in 	Vista.
**Type** 'AT' press 'Send' - This should return 	'OK'
**Type** 'AT+ZCDRUN=8' press send - This should return a 	message saying whether it failed or succeeded.

[IMG]http://i6.photobucket.com/albums/y249/w0lv3n/MF636_Terminal.jpg[/IMG] 	

*You can now disconnect, quit the manager , unplug the 	modem and load Ubuntu*

[SIZE=4]**Step 2**[/SIZE]
*Now 	that you have loaded Ubuntu, plug in the usb.*

**Open** 	terminal.
**Enter** the command 'lsusb'.
 	 	Code:
 	Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 004: ID 19d2:0031   Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 	[I]Something similar to this should result. The important part here 	is the 'ID 19d2:0031' . If this isnt in your results, but 'ID 	19d2:2000' is, then we havent disabled the ISO so try step one 	again.

Now that we have the correct function being 	recognised, we need to tell Linux what it is.[/I]

**Enter** 	the following code into terminal:
 	[INDENT] 	Code:[/INDENT] 	sudo modprobe -r usbserial sudo modprobe usbserial vendor=0x19d2 product=0x0031 	*This has told Linux that the device at ID 19d2:0031 is a 	USBserial device (I think! =P)*

**Unplug** the 	modem.
**Enter** the following into terminal:
 	[INDENT] 	Code:[/INDENT] 	sudo /etc/init.d/hal restart 	*This should restart the hardware detection. Hopefully after this 	point, Network Manager will notice the device and prompt for a new 	connection.*

[SIZE=4]**Step 3**[/SIZE]
*Now 	that we have the device recognised, we need to setup the connection. 	Provided Network Manager plays nice, this is very easy*

**Click** 	the 'Mobile Broadband' tab.
**Click** 'Add'
**Select** 	'Telstra' - Accept the settings.
**Click** 'Edit'
**Enter** 	your username and password
**Change** the APN to 	'telstra.bigpond.
**Accept** the settings

*Now that 	the connection is set up, attempt to connect to the internet. 	Hopefully you should now have internet access! All thats left to do 	now is make the modem recognition automatic*

[SIZE=4]**Step 	4**[/SIZE]
*By editing a few lines, we will enable the device 	automatically upon startup.*

**Open** terminal.
**Enter** 	the following code:
 	[INDENT] 	Code:[/INDENT] 	sudo gedit /etc/init.d/rc.local 	**Add** the following lines to the bottom of the file:
 	[INDENT] 	Code:[/INDENT] 	modprobe -r usbserial modprobe usbserial vendor=0x19d2 product=0x0031 	*Restart Linux and you should be able to connect straight after 	plugging in the USB*
- - - - - - - - - - 

I think thats 	about it. Im in vista atm and had to use other links and what not to 	remember it all. Will edit this later with any changes.

**Please** 	post any issues, feedback or variations. I dont know if the terminal 	is available in other versions of the connection manager software or 	for different model ZTE MF6xx modems.

**Hope this helps 	people!**

[I]Original posts and 	information:
[/I][COLOR=#000080]_[*http://ubuntuforums.org/showthread.php?t=1005910*]("http://ubuntuforums.org/showthread.php?t=1005910")_[/COLOR]
 
  .

---

