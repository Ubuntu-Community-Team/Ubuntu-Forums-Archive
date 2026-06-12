---
title: "Wireless connection fixed ubuntu"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by Extract_Here on 2009-12-19
[FONT=Lucida Sans Unicode][SIZE=4]I hate this problem the same thing happened to me when i first installed 9.04. Your going to need to achieve a direct connect from the router so you can get the correct software to install your wireless driver. 
 The things you will need to download 
1. ndiswrapper you can get this from the synaptic package manager 
(system>administrator>synaptic) 
2. You will need to find the driver for your wireless card(google search its brand name along with driver. eg. ("Belkin" Driver) download it even if its a Windows Exe. file 
3. Browse the windows exe. file and find the file with .inf on the end eg. (belkin.inf)
4. once you have found that file open up Ndiswrapper It has a different name in the menu its called windows wireless drivers. (system>admin>windows wireless drivers)
5. drag the .inf file into the NDiswrapper and your wireless should connect.

if your still having problems message me and we can talk further.

-may the source be with you[/SIZE][/FONT]  
 		                   		  		  		 		 			[FONT=Lucida Sans Unicode][SIZE=4] 				__________________
				-May the Source be with you:KS [/SIZE][/FONT]

---

### Post by wah fun on 2009-12-19
Did this and still no joy. Next steps?

thx

---

### Post by bkratz on 2009-12-19
> **wah fun said:**
> Did this and still no joy. Next steps?

thx

Do you know what type of wireless card you have?  Ndiswrapper is only used if no inherent support exists.  Many current wireless cards are natively supported. Go to the terminal

Applications..Accessories...terminal and type in 

lspci if it is a pci card  (LSPCI in lowercase)

or 
lsusb if it is a usb dongle.  Look at the outputs or post here the results, and someone can help determine what the proper course of action is.

---

