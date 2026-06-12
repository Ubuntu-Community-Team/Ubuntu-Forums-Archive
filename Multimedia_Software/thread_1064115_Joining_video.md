---
title: "Joining video"
date: 2009-02-08
forum: Multimedia Software
---

### Post by Revenged on 2009-02-08
If I have two movie files, like cd1 and cd2, is there any way to just join them together into one file?

---

### Post by howefield on 2009-02-08
Avidemux will do this, you'll be able to install it with Synaptic Package Manager.

---

### Post by devilliers123 on 2012-01-18
**Re: Stitching videos together** 			
 			 			 		   		 		 		I tried the same thing.

What I found worked was using that code with .mpeg file suffix but NOT .mp4

So what worked was   >>>>>    cat aaa.mpeg bbb.mpeg > nnn.mpeg

also I used    >>>>>                  mencoder -oac copy -ovc copy -idx -o nnn.mpeg aaa.mpeg bbb.mpeg

I found that the  -idx   whether entered or absent had no effect whatsoever.

What was strange was that the output made DOUBLE  clips i.e nnn.mpeg + nnn.mpeg in both cases

Otherwise the quality of video and sound was excellent in Movieplayer.

Anyone any ideas about that DUPLICATION?  It is like an ECHO?
 		                   		  		  		  		  		 		 			 				 				* 					 						[Last edited by devilliers123]("http://ubuntuforums.org/posthistory.php?p=11622028"); 1 Minute Ago at 09:54 PM.. 					 					 						Reason: clarification 					 				* 			
 		 		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=11622028") 		 		  	 	 	 	 		  		 			 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=11622028")

---

