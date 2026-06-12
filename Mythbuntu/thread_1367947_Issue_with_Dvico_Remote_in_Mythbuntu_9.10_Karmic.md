---
title: "Issue with Dvico Remote in Mythbuntu 9.10 Karmic"
date: 2009-12-30
forum: Mythbuntu
---

### Post by mozz66 on 2009-12-30
Hi there 

I am a linux / mythbuntu newbie and have built myself a Mythbuntu 9.10 Media Center PC. Installed are two identical Dvico Fusion Plus HDTV cards with a single Dvico USB IR receiver and Fusion MCE Remote. I only have one issue that I cant seem to work out - every time I push a button on the remote, it registers twice e.g. push the button 3 and it will register channel 33.

The remote initially was not working at all, and I found a posting on the web to change the /etc/lirc/hardware.conf file from REMOTE_DEVICE="/dev/lirc0" to be REMOTE_DEVICE="/dev/usb/hiddev0". This got the remote working with this issue 

But now if I use irw in a terminal window and press the 1,2 & 3 buttons I get the following results 
$ irw
0001004600000bfe 00 1 DVICO_MCE
0001004600000bfe 01 1 DVICO_MCE
00010046000017fe 00 2 DVICO_MCE
00010046000017fe 01 2 DVICO_MCE
0001004600001bfe 00 3 DVICO_MCE
0001004600001bfe 01 3 DVICO_MCE

OK my guess here is that the 00 and 01 following the code for each button press are because the two Dvico HDTV Cards both seeing the USB IR device received signal ?
As a note if I use the arrows on the keyboard to change channels everything works fine.

I have searched the web for an answer but couldn't find any, and now need some help please. 

Thanks


 		
 		  		  		  		  		  		  	   	 [[IMG]http://www.xpmediacentre.com.au/community/imagize/buttons/reputation.gif[/IMG]]("http://www.xpmediacentre.com.au/community/reputation.php?p=283170") 		 		[[IMG]http://www.xpmediacentre.com.au/community/imagize/buttons/report.gif[/IMG]]("http://www.xpmediacentre.com.au/community/report.php?p=283170") 		 		  	 	 	 	 		 		 			[IMG]http://www.xpmediacentre.com.au/community/imagize/misc/progress.gif[/IMG] 			[[IMG]http://www.xpmediacentre.com.au/community/imagize/buttons/edit.gif[/IMG]]("http://www.xpmediacentre.com.au/community/editpost.php?do=editpost&p=283170")

---

