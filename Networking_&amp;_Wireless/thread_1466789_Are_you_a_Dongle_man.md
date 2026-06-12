---
title: "Are you a Dongle man?"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by AnxietyDrive on 2010-04-30
Well I'll give it a try, make this post that is, in the forlorn hope that out there, there is someone who actually knows what they are taking about and, AND, can communicate that expertise in a language that a normal lay user might have some slight hope of understanding!!

I know the above has just wound 10 zillion nerdy geek heads right off, but TBO Ive trawled the forums looking through zillions of threads pertaining to my problem and all but a handful were complete unintelligible rubbish and those that weren't, were so technical that all but a few, higher echelon nuxheads, would follow. :guitar:

My problem is now time critical. My whole expedition, that I have planned for the last two years is now in jeopardy, because Ubuntu Linux is not quite as good as it says on the tin. I need mobile broadband connection.

Now I could switch back to Windozzze on all my laptops that will be used on the trip..... I could and I know it works - out of the box - Ive tested it on other machines.! 
But Having extolled the virtues of Linux to all my friends and associates for many, many years ... I'd feel a bit of a numpty' if I did. 
However unless I can find someone who can talk and walk me through this problem - Ill have to eat humble pie and concede that Windozzzze for all its bad points, still kicks Linuxes butt in most areas.

If you really know your stuff, you know your dingles from your dongle, your ying form your lan and feel charitable enough to speak with a simple tongue, then Id very much appreciate your help. If on the on the other hand you just want to flex your geeky ego pimples on an admitted linux noob, then Id rather your went else where.

I have tried many things but I'll not mention them yet as it might influence your thoughts one way or another.

The overview of the problem is :

Plugging my shiny new ( working/tested on windozzze machine)  ZTE MF112 3MOBILE Broadband Dongle into my FS AmiloPro Lappy which runs Ubuntu Hardy 8.04 - I get nothing.

Well not nothing actually. 
No I get a new drive recognised with the folders displaying the windozze setup and software files etc.

Also when I Terminal "sudo lsusb -v"
I get data showing the system sees and identifies the device correctly.

wvdial does not see any device.

I tried the 'wine' route and have a successful installation of the windozzze software, but get an access violation when tying to run it.


Anyway if you feel your up to the challenge, Ill do my best to keep up with you and give you all the info you need to 'make my day'.

Salute all you wonderful nerdy geek heads  - :lolflag:

AD

---

### Post by pdc on 2010-04-30
so you plan to run a 2 year old version of Ubuntu?

Whilst still in civilisation, I recommend downloading the 32bit iso of lucid lynx; just released; 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

if you do not have one, buy/borrow two 1G or 2G usb sticks; 

if your 8.04 does not have a "create a usbstick" programme option, download it via synaptic; and install;

copy the iso of the new ubuntu onto a 1G or 2G stick;

plug the other stick into another USB port on your computer;

now run the programme "USB Startup disk creator" ....... *or whatever it might be called for 8.04* .............

; ie the programme will burn the iso onto the other stick, and [B]select the option to allow some MB to copy other stuff onto the stick;
[/B]
you will then have a live CD of 10.04 to try before you go; that is called permanent ......... meaning changes are remembered as you boot up each time ...

I have a similar setup for 10.04 and it is running two ZTE modems and a Huawei well;

you are likely to see an icon appear on the 10.04 desktop for your ZTE;

right-click this; select "eject" and then configure the modem as here

.... halfway down page ........... create mobile broadband ...

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

---

### Post by alexfish on 2010-04-30
Hi

Does this Help

  	 	 	 	 	 	  
[LIST]
[*][SIZE=2]For USB Devices ;If nothing shows enter this 	command from the terminal[/SIZE]  	
[/LIST]
 [SIZE=2]
[/SIZE][SIZE=2]**Code :**[/SIZE][SIZE=2]

lsusb

this will give the [/SIZE][SIZE=2]**ID's**[/SIZE][SIZE=2] of the device

Look to see if your device is listed in the latest [/SIZE][[COLOR=#000000][FONT=Verdana, Arial, sans-serif][SIZE=2]_**usb_modeswitch.setup**_[/SIZE][/FONT][/COLOR]]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup")[SIZE=2]

[/SIZE][SIZE=2]**Check**[/SIZE]
 
[LIST]
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]**DefaultVendor 	= 0xN**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2] 	where n is the number in hex[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]**DefaultProduct 	= 0xN**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2] 	where n is the number in hex[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]If 	the device is listed then there is a good chance it will work[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]use 	a [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2]**computer**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2] 	with [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2]**internet**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2] 	access for any downloads and save to usb stick , also you will 	always have the necceccary tools to get connected ; if you are a 	novice use links to the [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2]**Debian 	sites **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2]as 	the files will self install when in [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2]**Ubuntu**[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]if 	you install the latest package then the device should work without 	any further cofiguration of the usb modeswitch[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]**read 	all** the info at the **Draisbergho.de site** thoroughly and 	note any areas of problems and the fixes and links [/SIZE][/FONT][/COLOR] 	
[/LIST]
 


 
[LIST]
[*][[COLOR=#000000][FONT=Verdana, Arial, sans-serif][SIZE=2]_**usb_modeswitch.setup**_[/SIZE][/FONT][/COLOR]]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.setup") 		
[*][[SIZE=2]http://www.draisberghof.de/usb_modeswitch/[/SIZE]]("http://www.draisberghof.de/usb_modeswitch/") 		
[*]Starting from version 1.1.2, 	usb_modeswitch will add a symbolic link to the correct port with 	interrupt transfer if the device provides standard serial ports. The 	link will have the name **/dev/gsmmodem**, with a number appended 	if more than one device is attached.  	
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package 	]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE] 	
[/LIST]
 [SIZE=2]
[/SIZE][SIZE=2]**Dial up Methods:**[/SIZE][SIZE=2]
[/SIZE]


 
[LIST]
[*][COLOR=#000000][FONT=Times New Roman][SIZE=3]**Gnome 	Network Manager **[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=3]{check Versions .get updated latest version 0.8 } Also has a list of predefined 	ISP connections[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Times New Roman][SIZE=3]**Gnomeppp**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=3] 	this is a front end tool to wvdial so both need to be down loaded[/SIZE][/FONT][/COLOR] 		
[*][COLOR=#000000][FONT=Times New Roman][SIZE=3]**Sakis3g 	**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=3]{ 	please refer to the site below }[/SIZE][/FONT][/COLOR]  	
[*][COLOR=#000000][FONT=Times New Roman][SIZE=3]**PPP** 	{ should already be installed. **set up** use the terminal and 	enter the command : **sudo pppconfig **[/SIZE][/FONT][/COLOR] 	
[/LIST]
 [COLOR=#000000][FONT=Times New Roman][SIZE=2]**Downloads**[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]http://packages.debian.org/sid/wvdial[/SIZE][/FONT][/COLOR] 		
[*][[COLOR=#000000][FONT=Times New Roman][SIZE=2]http://packages.debian.org/unstable/net/gnome-ppp[/SIZE][/FONT][/COLOR]]("http://packages.debian.org/unstable/net/gnome-ppp") 		
[/LIST]
 [COLOR=#000000][FONT=Times New Roman][SIZE=2]**Sakis3G **
This Method is also worth trying . (Will also detect if you are KDE so may be of use if experiencing problems here ) ......{ Read the Two Links thoroughly before hand } { Also has usb_modeswitch and will implement if the modem has not switched from storage mode.a + couple of fixes for zte devices ,also probes the modem ports so may be a better tool if you have problematic devices IE : multiple ports registering on the system which makes life hard for the Network Manager. Check out the script file , its is easy to enter your provider info},Will work with WVDIAL OR Direct with PPPd, Read the script file as not all providers are in the database and also as to its usage[/SIZE][/FONT][/COLOR]
 
[LIST]
[*][[COLOR=#000000][FONT=Times New Roman][SIZE=2]http://sakis.tel4u.gr/blog/sakis3g/#features[/SIZE][/FONT][/COLOR]]("http://sakis.tel4u.gr/blog/sakis3g/#features") 		
[*][COLOR=#000000][FONT=Times New Roman][SIZE=2]Check 	it out at Sakis' blog [/SIZE][/FONT][/COLOR][ToDo 	Forever]("http://sakis.tel4u.gr/blog/sakis3g/")[COLOR=#000000][FONT=Times New Roman][SIZE=2].[/SIZE][/FONT][/COLOR] 		
[/LIST]
 [COLOR=#000000][FONT=Times New Roman][SIZE=2]**Reminder**[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][SIZE=2] " Read the script file "

If done with Ubuntu the " sakis3g " script should be in the " usr/bin " it is easy to add to the menu go to edit menu's and add new item , then locate the script , also give it a name[/SIZE][/FONT][/COLOR][SIZE=2]


[/SIZE][COLOR=#000000][FONT=Times New Roman][SIZE=3]**A site worth reading**[/SIZE][/FONT][/COLOR][[COLOR=#000000] [/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm")[[COLOR=#000000][FONT=Times New Roman][SIZE=3]http://www.pcurtis.com/ubuntu-mobile.htm[/SIZE][/FONT][/COLOR]]("http://www.pcurtis.com/ubuntu-mobile.htm")

---

### Post by AnxietyDrive on 2010-05-01
> so you plan to run a 2 year old version of Ubuntu?

I guess this suggests that you think I should upgrade. 

As I understand what youve said is, I should have have a copy of the new 10.04 lite on a stick which I can run as a separate OS installation when I want to connect to the internet? 

If so why dont I Install 10.04 lite as a dual boot OS - migrate data across, then when done remove the 8.04 installation?

Or have I missread your post?


PS I sit possible to upgrade 8.04 to 10.04. I think I read you cant!?

Ta muchly for your reply - I'll post how I get on.
AD

---

### Post by AnxietyDrive on 2010-05-01
Thanks gents ( though I guess there is no reason why you might not be ladies :) )

Since it was inevitable that at some point I would upgrade to 10.04, I decided to dual boot an Install of 10.04.

It went in seamlessly  in no time at all.
Just did the intuative and logical, as you described.
And bish bash bosh - running tinternet from my dongle.
Now to do like wise to all the others.... bang goes  my saturday chill out :popcorn:

They way forward for Linux ( Ubuntu) is Click and Run - Plug and Play.
99% of people do not want, nor have the time to tinker under the bonnet. 
They, like me just want to get in the car , turn the key and drive.

I know all you techi nerdy geeks are the backbone of this wonderful OS, and without you it would not exist..... but when it comes to competeing with the likes of MS ... the phrases ' use command line interface' and 'terminal' are poison to the ears of prospective lay users. 

You are the mechanics and you like to get down and dirty with the binaries, but remeber 99% of folk dont know nor want to know where the bonnet catch is!!!

Nor should they need to!

Bless you all

Thanks once again!:guitar::guitar:

AD

---

### Post by alexfish on 2010-05-01
I understand your Philosophy  ;  
 

 But if the car breaks down  Ubuntu 10.04  has the tools to fix it ; No need to take it to a garage  : all the mechanics are here

 

 So now you have  Turn the Key and Go and The Tools for tinkering under the bonnet.
 

 Enjoy

---

