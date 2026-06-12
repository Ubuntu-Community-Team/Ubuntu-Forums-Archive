---
title: "Mobile Broadband Connections"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by alexfish on 2010-04-30
**[SIZE=2]USB Mobile broadband Ubuntu [  10.04  : 9.10 : 9.04][/SIZE]**[SIZE=2]

[/SIZE]         	 	 	 	 	 	  [FONT=Verdana][SIZE=2]**Most modems will work out of the box:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Boot up the computer without the modem give time for the system to settle then connect the modem

Click on the Network Manager you may see something like " Make Connection" , click on it and follow the Wizard

[http://en.wikipedia.org/wiki/NetworkManager#User_interfaces](http://en.wikipedia.org/wiki/NetworkManager#User_interfaces)[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]Network manager failed to connect : Double check the Information

Device is Recognised and have double checked the information try the below methods of dial up

Device not recognised in the Network Manager : follow the below[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]If 	it is not recognised and an icon appears and the desktop try right 	click with mouse and eject tor safely remove the device then see if 	will configure [/SIZE][/FONT] 	
[*][FONT=Verdana][SIZE=2]if nothing happens , open 	up the terminal and enter this command [/SIZE][/FONT] 	
[/LIST]
 [FONT=Verdana][SIZE=2]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

dmesg | grep -e "modem" -e "tty"

this will show if the modem has been identify and the lines { ttyx } and possible the driver

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Example :**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

[/SIZE][/FONT][COLOR=#0000ff][FONT=Verdana][SIZE=2][ 0.000000] console [tty0] enabled
[ 0.262809] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/SIZE][/FONT][/COLOR][FONT=Verdana][SIZE=2]
[/SIZE][/FONT][COLOR=#483d8b][FONT=Verdana][SIZE=2][ 0.263080] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A[/SIZE][/FONT][/COLOR][FONT=Verdana][SIZE=2]
[ 21.950573] USB Serial support registered for GSM modem (1-port)
[ 21.950756] option 1-10:1.0: GSM modem (1-port) converter detected
[ 21.950893] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ttyUSB0**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.950911] option 1-10:1.1: GSM modem (1-port) converter detected
[ 21.951003] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ttyUSB1**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.951025] option 1-10:1.3: GSM modem (1-port) converter detected
[ 21.951130] usb 1-10: GSM modem (1-port) converter now attached to [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ttyUSB2**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[ 21.951157] option: v0.7.2:USB Driver for GSM modems

[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]for serial legacy devices

[/B][/SIZE][/FONT][17179575.588000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.588000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179575.592000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179575.592000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[FONT=Verdana][SIZE=2]
if only shows the lines highlighted in blue then there is a problem

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**If the the output look similar to the above then the Problem is a configuration one /**[/SIZE][/FONT][FONT=Verdana][SIZE=2] make a note of the ttyx as this will help to configure wvdial or Gnomeppp

Some modems have more than one control line and could be any two of the above so if in wvdial or Gnome ppp detects the modem on port 1 , then fails to connect then force them to use another port , you will have to try them ..

as for The [/SIZE][/FONT][FONT=Verdana][SIZE=2]**Network Manager **[/SIZE][/FONT][FONT=Verdana][SIZE=2]if it is Failing to connect as regards the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**TTYx**[/SIZE][/FONT][FONT=Verdana][SIZE=2] then use alternate methods of [/SIZE][/FONT][FONT=Verdana][SIZE=2]**dialup **[/SIZE][/FONT][FONT=Verdana][SIZE=2]

One thing is for sure : [/SIZE][/FONT][FONT=Verdana][SIZE=2]**if the modem is recognised then there is no reason a connection can't be made**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Verdana][SIZE=2]For USB Devices ;If nothing 	shows enter this command from the terminal[/SIZE][/FONT]
[/LIST]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Code :**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

lsusb

this will give the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ID's**[/SIZE][/FONT][FONT=Verdana][SIZE=2] of the device

Look to see if your device is listed in the latest [/SIZE][/FONT][[COLOR=#000000][FONT=Verdana][SIZE=2]_**usb_modeswitch.setup**_[/SIZE][/FONT][/COLOR]]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup")[FONT=Verdana][SIZE=2]

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Check**[/SIZE][/FONT]
 
[LIST]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**DefaultVendor 	= 0xN**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] 	where n is the number in hex[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**DefaultProduct 	= 0xN**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] 	where n is the number in hex[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Verdana][SIZE=2]If 	the device is listed then there is a good chance it will work[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Verdana][SIZE=2]use 	a [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]**computer**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] 	with [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]**internet**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] 	access for any downloads and save to usb stick , also you will 	always have the necceccary tools to get connected ; if you are a 	novice use links to the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]**Debian 	sites **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]as 	the files will self install when in [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]**Ubuntu**[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Verdana][SIZE=2]if 	you install the latest package then the device should work without 	any further cofiguration of the usb modeswitch[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**read 	all** the info at the **Draisbergho.de site** thoroughly and 	note any areas of problems and the fixes and links [/SIZE][/FONT][/COLOR] 	
[/LIST]
 


 
[LIST]
[*][[COLOR=#000000][FONT=Verdana][SIZE=2]_**usb_modeswitch.setup**_[/SIZE][/FONT][/COLOR]]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup") 		
[*][[FONT=Verdana][SIZE=2]http://www.draisberghof.de/usb_modeswitch/[/SIZE][/FONT]]("http://www.draisberghof.de/usb_modeswitch/") 		
[*][FONT=Verdana][SIZE=2]Starting 	from version 1.1.2, usb_modeswitch will add a symbolic link to the 	correct port with interrupt transfer if the device provides standard 	serial ports. The link will have the name [/SIZE][/FONT][FONT=Verdana][SIZE=2]**/dev/gsmmodem**[/SIZE][/FONT][FONT=Verdana][SIZE=2], 	with a number appended if more than one device is attached.[/SIZE][/FONT] 		
[*][FONT=Verdana][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package 	]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE][/FONT] 	
[/LIST]
 [FONT=Verdana][SIZE=2]
[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Dial up Methods:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[/SIZE][/FONT]


 
[LIST]
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**Gnome 	Network Manager **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]{ 	Should already be installed } Also has a list of predefined 	connections[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**Gnomeppp**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] 	this is a front end tool to wvdial so both need to be down loaded[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**Sakis3g 	**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]{ 	please refer to the site below }[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Verdana][SIZE=2]**PPP** 	{ should already be installed. **set up** use the terminal and 	enter the command : **sudo pppconfig **[/SIZE][/FONT][/COLOR] 	
[/LIST]
 [COLOR=#000000][FONT=Verdana][SIZE=2]**Downloads**[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][http://packages.debian.org/sid/wvdial](http://packages.debian.org/sid/wvdial)
[*]
[*][[COLOR=#000000][FONT=Verdana][SIZE=2]http://packages.debian.org/unstable/net/gnome-ppp[/SIZE][/FONT][/COLOR]]("http://packages.debian.org/unstable/net/gnome-ppp")
[/LIST]
 [COLOR=#000000][FONT=Verdana][SIZE=2]**Sakis3G **
This Method is also worth trying . (Will also detect if you are KDE so may be of use if experiencing problems here ) ......{ Read the Two Links thoroughly before hand } { Also has usb_modeswitch and will implement if the modem has not switched from storage mode.a + couple of fixes for zte devices ,also probes the modem ports so may be a better tool if you have problematic devices IE : multiple ports registering on the system which makes life hard for the Network Manager. Check out the script file , its is easy to enter your provider info},Will work with WVDIAL OR Direct with PPPd, Read the script file as not all providers are in the database and also as to its usage[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][[COLOR=#000000][FONT=Verdana][SIZE=2]http://sakis.tel4u.gr/blog/sakis3g/#features[/SIZE][/FONT][/COLOR]]("http://sakis.tel4u.gr/blog/sakis3g/#features") 		
[*][COLOR=#000000][FONT=Verdana][SIZE=2]Check 	it out at Sakis' blog [ToDo 	Forever]("http://sakis.tel4u.gr/blog/sakis3g/").[/SIZE][/FONT][/COLOR]
[/LIST]
 [COLOR=#000000][FONT=Verdana][SIZE=2]**Reminder**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2] " Read the script file "

If done with Ubuntu the " sakis3g " script should be in the " usr/bin " it is easy to add to the menu go to edit menu's and add new item , then locate the script , also give it a name[/SIZE][/FONT][/COLOR][FONT=Verdana][SIZE=2]


[/SIZE][/FONT][COLOR=#000000][FONT=Verdana][SIZE=2]**A site worth reading**[/SIZE][/FONT][/COLOR][[COLOR=#000000] [/COLOR][COLOR=#000000][FONT=Verdana][SIZE=2]http://www.pcurtis.com/ubuntu-mobile.htm[/SIZE][/FONT][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm")[FONT=Verdana][SIZE=2]


Network Manager failing to return the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS1**[/SIZE][/FONT][FONT=Verdana][SIZE=2] and [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS2**[/SIZE][/FONT][FONT=Verdana][SIZE=2] IE :the modem connects but the Browser and updates etc fail to connect

From the terminal try these

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

sudo gedit /etc/ppp/options

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Add this line and save:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

replacedefaultroute


[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Or**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Here I have change the IPCP configure-NAKs returned before starting , remove the # and set the number to 30 ( or any thing above the default value till there is a constant connection ) Tip try 30 then work down

[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Code:**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

sudo gedit /etc/ppp/options


[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Place a # in front of the replacedefaultroute so it looks like **[/SIZE][/FONT][FONT=Verdana][SIZE=2]


# replacedefaultroute


[/SIZE][/FONT][FONT=Verdana][SIZE=2]**Then look for the lines**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
# ipcp-max-failure <n>

[/SIZE][/FONT][FONT=Verdana][SIZE=2][B]to look like
[/B][/SIZE][/FONT][FONT=Verdana][SIZE=2]
# Set the maximum number of IPCP configure-NAKs returned before starting
# to send configure-Rejects instead to <n> (default 10).
ipcp-max-failure 30

Hopefully I can now leave the NM IPv4 settings to Automatic (PPP) instead of Setting the NM to IPv4 settings to Automatic (PPP) address only and having to enter the numerical addresses in the DNS servers text box.

the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**replacedefaultroute**[/SIZE][/FONT][FONT=Verdana][SIZE=2] has failed a few times after a fresh boot , but has proved quite successful

alternatively you can use the Network Manager to use the address of you [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP **[/SIZE][/FONT][FONT=Verdana][SIZE=2]

get the Numerical address or addresses from your [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP**[/SIZE][/FONT][FONT=Verdana][SIZE=2] commonly known as [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS1**[/SIZE][/FONT][FONT=Verdana][SIZE=2] and [/SIZE][/FONT][FONT=Verdana][SIZE=2]**NS2**[/SIZE][/FONT][FONT=Verdana][SIZE=2]

Open up the connection via the Network Manager . Select Mobile Broadband . Select Edit Connection .Select Ipv4 settings select the Automatic(PPP) address only then enter the addresses of your [/SIZE][/FONT][FONT=Verdana][SIZE=2]**ISP**[/SIZE][/FONT][FONT=Verdana][SIZE=2] in the [/SIZE][/FONT][FONT=Verdana][SIZE=2]**DNS servers box**[/SIZE][/FONT][FONT=Verdana][SIZE=2] separated by a &#8220; [/SIZE][/FONT][FONT=Verdana][SIZE=2]**, **[/SIZE][/FONT][FONT=Verdana][SIZE=2]&#8220; comma without the quotes so it will look something like

149.254.201.126,149.254.192.126


This is a small update to HSOconnect that allows it to work with the iCon 515 as sold by Orange. or 5X5 May work with other Icon HSO devices please refer to Pharescape Site

Tested On Ubuntu 9.10 may work on other versions

[/SIZE][/FONT][[FONT=Verdana][SIZE=2]**Re: Option iCON 515m wireless USB modem (Orange)**[/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1351612") [FONT=Verdana][SIZE=2]

[http://www.pharscape.org/](http://www.pharscape.org/)[/SIZE][/FONT]
 [FONT=Verdana][SIZE=2]
[http://www.pharscape.org/forum/index.php](http://www.pharscape.org/forum/index.php)[/SIZE][/FONT]
 
[FONT=Verdana][SIZE=2]PS: I am not Skinny , Just Slim When there is no Free Beer[/SIZE][/FONT]

  
 

[SIZE=2]
[/SIZE]

---

