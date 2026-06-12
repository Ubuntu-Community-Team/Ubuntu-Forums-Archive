---
title: "Can't find my print server!"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by Twizzle on 2009-06-23
I have just bought an ethernet usb print server for my home network as I would like to be able to print from my PC and my laptop. My setup is as follows:

Cable modem to Netgear wireless router to:

1) Ubuntu 8.10 Server box (file storage back up etc)
2) 5 Port Switch connected to:
      a)Ubuntu 9.04 desktop PC
      b)TP PS110 USB Ethernet print server
3) Wireles connection to Windows 7 laptop

I have tried running the install CD from a virtual XP machine on the desktop PC and from the laptop but it does not find the print server.

Is there any way I can try to access the server so I can set it up through Ubuntu?

According to the instructions it should be at 192.168.0.10. My network runs from 192.168.1.xx. I have tried the IP address but it will not connect to anything (there should be a web interface and also through adding a printer in Ubuntu comes back negative)

I hope that makes sense as this is my first trip into network printing!

Thanks

---

### Post by jonobr on 2009-06-23
Hello


If you get the results of the ifconfig from your PC, you should have a 255.255.255.0 subnet mask, 
if thats the case,
you will not be able to get to the 192.168.0 address.
Address wise its like your trying to deliver a letter to a house thats not on the same street as you,.

You can do one of two things,

If you can try, change the IP address of the printer to something like 192.168.1.222
(try pinging 192.168.1.222 before you change the address to ensure there is no device with that IP address)

Or  , remove everything from your 5 port switch except the printer and your pc.

Change your PC IP address to a 192.168.0.XXX address , again try 222.

With its address changed connect to the printer and change its IP address to a 192.168.1.222 address.

Change your PC back to 192.168.1.x address and reconnect to he switch.
Ping the new printer address, it should respond

Both ways should be relatively easy,

---

### Post by Twizzle on 2009-06-23
Thank you that made perfect sense.

I changed my settings to make my PC 192.168.0.222 and then managed to log into the print server and was given the options to change it to what I wanted. The available options were IP address, subnet mask and router.

I changed the IP to 192.168.1.222, the subnet mask to 255.255.255.0 and tried the router as both 0.0.0.0 (the apparently defaut setting) and 192.168.1.1 but neither worked and I had to press the reset switch to get back into the print server on 192.168.0.10, as resetting my PC and trying 192.168.1.222 failed!.

I am sure that it is something simple!

EDIT... No cancel that - it is now working and would appear that the old turn off and count to five trick worked again!

Thank you once more :-)

---

### Post by jonobr on 2009-06-23
Hello


Glad to hear its working,

chances are the switch needed to update its arp table,

SOoe switches have the ability to "know" which devices are on which port, and when you change IP address or port, sometimes, they take a short while to come up.


Again, good to hear its working

Cheers

---

### Post by jiex on 2009-11-01
> **jonobr said:**
> Hello


If you get the results of the ifconfig from your PC, you should have a 255.255.255.0 subnet mask, 
if thats the case,
you will not be able to get to the 192.168.0 address.
Address wise its like your trying to deliver a letter to a house thats not on the same street as you,.

You can do one of two things,

If you can try, change the IP address of the printer to something like 192.168.1.222
(try pinging 192.168.1.222 before you change the address to ensure there is no device with that IP address)

Or  , remove everything from your 5 port switch except the printer and your pc.

Change your PC IP address to a 192.168.0.XXX address , again try 222.

With its address changed connect to the printer and change its IP address to a 192.168.1.222 address.

Change your PC back to 192.168.1.x address and reconnect to he switch.
Ping the new printer address, it should respond

Both ways should be relatively easy,

Hello
I am new to Linux/Ubuntu but so far have found it a very easy system to use. Everything has worked very well - except configuring my UBUNTU machine to recognise and print to a networked printer. 
I suspect the answer given above - which I don't have the wit to follow completely - may hold the answer as my problem is similar to that if Twizzle.
Briefly, I have two computers networked and connected to a KYOCERA FS1010, via a Ethernet print server, TP-link TL-PS110U. The actual configuration is:
PC 1 [running XP Pro, up to date] to a DLink gigabit 5 port switch.
PC 2 [running UBUNTU 9.10] a second D link gigabit switch, this time 8 port. 
The printer is connected via its USB to a TP-Link TL-PS110U, which in turn is connected to the 8 port switch. 
The two switches are connected to each other. So, PC2 and the printeserver & printer connect to one switch; PC 2 connects to the other switch and the two switches are connected.  There are also sundry other devices hanging off each switch - such as networked media streamers. The windos network share folders and those on UBUNTU are visible to the other computers on the network and files are transferred between the different computers and the media streamers without any difficulty. 
This arrangement forms a sub-network, which is connected to a router (a Netgear), which then connects to the internet.
PC 1 (the XP PC) detected the print server without a hitch, after I ran the software that accompanied it. The software, alas is for Windows only.
I have been unable to get PC 2 [UBUNTU] to connect or mount the print server.
If I do the following, to add a printer, the printserva shows up, but I cannot select it:
System -> printing -> New -> Network Printer -> Windows Printer via SAMBA -> Browse -> Workgroup -> 1P_PRINTSERVAD5.
If I check the network, the printserver appears there as well:
Places -> Network -> 1P_PRINTSERVAD5. However, when I attempt to open it, I receive this popup error message: "Unable to mount location. Failed to retrieve share list from server."
Using the ADMIN software that came with the printserver, on PC 1 [the XP machine] I discovered that the IP address is: 192.168.0.10; subnet mask is: 255.255.255.0. 
Within UBUNTU, using "Network Tools" I pinged 192.168.0.10 and did other tests on it to discover that port 515 is associated with the printer and that port 631 is associated with IPP. 
I would be deeply grateful and obliged if someone could help me get my UBUNTU machine working with the printer, via the printserver. I suspect the above sulution woul work, but do not know how to implement it.
Regards
Jim.

---

### Post by jiex on 2009-11-01
OK - I had a play round in UBUNTU - add a printer - and managed to get my PC to print via the print server. Belo, is the process, in detail, for novices like me.
Interestingly, once you know what to do - it is all menu driven and EASIER than doing it for XP. The problem is that the people who made the print server, TP-Link, only put instructions on the quick start for Windows and the software only for for Windows. However, it is not really necessary, once you know that you can configure the print server for Windows via a browser aand within Windows and for UBUNTU via a browser AND from within UBUNTU. Why TP-Link do not say this - it would take a page on the quick start guide - only the muses know. 

The print server CD does have a very detailed 88 page manual with a section on configuring the print server for UNIX/Linux.
 It is mind bending, mind boggling, not for the faint hearted and usable by enthusiasts. For people like me, it was useless as it required you to play around with configutation files. I do not have all that many years left.
 Installation and configuration instructions should be simple, minimal information and expertise required. It should be a click through, one's grandmother should be able to do it. 

It's all right to get high and mighty and snide - as one person did on another thread and say "Whose grandmother would be using Linux anyway?" as a justification for retaining unnecessary complication. Everyone likes to feel special and superior and such remarks are those of the fanatic. The fact remains: if Linux is to compete widely with Windows, be installed on "ready to use machines" such as netbooks laptops and PCs like Dell, and be anything other than an enthusiast's way of wasting time,  Linux must be easy to install, use and have a wide range of software. On the whole, UBUNTU does this - but people like me should not have had to spend a day or so finding this solution to what is a straightforward question. My rant for the day.
Let me say that I think UBUNTU is a better OS for people like me than Windows: it is cheap, easy to learn, easy to use, intuitive. 


So, here goes:



UBUNTU 9.10: How to set up a network printer via Ethernet – USB print server
 

 NB1: The symbols << and >> are used like quotation marks, i.e. when reference is made to an actual menu item. They do NOT appear on the actual menu screen.
 NB2: This guide relates ONLY [but it may work for other setups, I do not know] to a set up where there is one or more computers on a home network, connected via a switch, AND the switch connects to a USB print server which then connects to  a printer.
 PC 1 &#8594;  
 [INDENT]		Switch &#8594; Print Server &#8594; USB Printer
[/INDENT] PC 2 &#8594;  
 

For the record I am using:
 
[LIST=1]
[*]PC (Intel E6300) running UBUNTU 	9.10
[*]D-Link Switch DGS1008G
[*]TP-Link TL-PS110U (the Print 	Server)
[*]Kyocera FS1010 - the printer

[/LIST]
 Method:

[LIST=1]
[*]Connect the print server as per 	instructions that come with it.
[*]If you have ONLY Linux machines on 	your network you can use a browser to see the 	configuration details for the print server. For the TP-Link the 	address is: [http://192.168.0.10:631/SYSTEM.HTM](http://192.168.0.10:631/SYSTEM.HTM)
[*]You do NOT need to change any 	settings whatsoever. The important information is the IP address 	of the print server: [http://192.168.0.10]("http://192.168.0.10/")
[*]The print server will remain on 	all the time and so will permanently reserve this IP address. If you 	have a large number of computers on the system, you may wish to set 	the IP address to a high value, ensuring that it remains within the 	sub net mask range. For instance, [http://192.168.0.155]("http://192.168.0.155/") 	would be OK. I left the IP as the default, which is: 	[http://192.168.0.10]("http://192.168.0.10/")
[*]Now, go to your UBUNTU desktop and 	select this path to install a new printer [assuming that you PC is 	already connected to the network]: System &#8594; Administration &#8594; 	Printing
[*]A splash screen will come appear, 	with the title: <<Printer configuration – localhost>>
[*]Select <<New>>  	
[*]Another splash screen appears with all of this text: 	<<Please Wait>>  <<Searching>> <<Searching 	for printers>>
[*]Another splash screen appears; 	<<New Printer>>
[*]On the left hand side, in a box, 	<<Devices>>, you will see a list.  In the list are 	entries including:
[/LIST]
 Serial Port #1
 Serial Port #2
 Other
 > Network Printer
 
[LIST=1]
[*] Click the little triangle beside 	<<Network Printer>> A new list appears.

[*]Select <<APPSocket/HP 	JetDirect>> from the list.
[*]On the right hand side you will 	see:
[/LIST]
 <<Location of network printer>>
 Host: [to the right: A box where you enter data]
 Port number: [9100] NB: This was already entered.
 
[LIST=1]
[*]NB: The port number, <<9100>> 	is the DEFAULT port number for the TP-Link and I suspect other print 	servers.  	
[*]Enter in the data box to the right 	of <<Host:>> the IP number of the print server, which in 	the case of the TP-Link is: <<192.168.0.10>> but without 	the << and >>.
[*]Click <<Forward>>, 	which is at the bottom of the page.
[*]Select your printer from the drop 	down list. Various CUPs driver options will then appear. I selected 	the default recommended options.
[*]Click through <<Forward>>. 	You will be offered a test screen: <<Would you like to print a 	test page?>>. Click OK.
[*]A test page will print. Close the 	dialogue boxes. Your are finished and have now installed a print 	server.
[/LIST]
 

 How to find the print server's open ports for printing.
 

 
[LIST=1]
[*]Go to  your UBUNTU desktop and 	select this path: System &#8594; Administration &#8594; Network Tools.
[*]A splash screen will pop up 	<<Devices – Network Tools>> and along the top is a row 	of tabs.
[*]Select <<Port Scan>>
[*]At the top is <<Network 	Address:>> and a data entry box to the right.
[*]In the data entry box type in the 	default IP for the print server. In the case of the TP-Link it is: 	192.168.0.10
[*]Click <<Scan>>
[*]After no more than 30 seconds a 	list appears. It will have entries such as:
[/LIST]
 Port	State	Service
 80	Open	WWW
 139	 Open	netbios-ssn
 525	 Open	printer
 631	 Open	ipp
 9100	 Open	unknown
 

 
[LIST=1]
[*]I suspect that 525 and 631 are 	also used for printing but I do not know how to configure them.
[/LIST]

---

### Post by Dave67 on 2009-12-09
I have a print server as well now it sees it but cannot connect to it so here is the setting minus the IP. I never tried this before on ubuntu I did see GPR in synaptic but not sure if this is what I need.

the connection is standard TCP/IP port (this is on windows and works fine) On ubuntu  I see this as a option as I am configuring the printer but I can not select the LPR setting and I do not know where to input the queue name. :roll:

port name: printer server 

protocol LPR (raw settings)

port 515 

queue name is lpt3

now I can see that once I set this is see the print server and tries to print a test page but the printer sets idle. 

I know there is a setting wrong somewhere.


dave

---

### Post by Dave67 on 2009-12-09
I got as far as the post ''what worked for me'' but I still think I am using the wrong port might try 525  I did try 9100 and 515 did not work.

---

### Post by amado738 on 2010-05-17
I'am having huge problems with my print server. it is currently connected through an ethernet connection straight through to the computer. Ubuntu does not even recognise it as even being connected. I tried using the arp command on the terminal screen with no luck.

My print server is a netgear ps110. and was given to me by a friend, he had it running well on win xp. I have tried using xp and windows 7 on different computers with no luck, the oonly platform which the server is even visible is windows 7 but I cannot make it work, the IP address that my friend changed from the default address does not work (I have no idea why) I have tried changing the ip address on win 7 but it still does not allow me to access the settings via firefox or internet explorer. 

there is no reset button to reset to the factory ip address and I'am not really sure what to try next. I'am not really an expert at computers (especially not linux) so please if you have any suggestions please explain it as if I was a 5 year old. 

Thanking you in advance :)

---

