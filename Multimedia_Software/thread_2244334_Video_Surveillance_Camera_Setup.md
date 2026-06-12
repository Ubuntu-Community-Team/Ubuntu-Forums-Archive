---
title: "Video Surveillance Camera Setup?"
date: 2014-09-15
forum: Multimedia Software
---

### Post by johnsmoke on 2014-09-15
So I've been noticing some odd things out back of my house, and I'd like to setup a cheap surveillance setup so that I can see who is going back there. I'd like to use my Ubuntu machine along with maybe a wireless camera that can interface w/ my 802.11.... motion sensor cam, w/ night-vision preferably. Does anyone know the simplest method of setting up a system such as this? Ubuntu machine upstairs, I'd like to monitor the back yard area which is basement-level. Any help would be appreciated.

---

### Post by dave131 on 2014-09-15
I don't know anything about doing this, but I did do a google search using 'ubuntu simple home surveillance' as the search string and some options did show up. While it was in an older thread, here is what sounds like a good place to start:

> 
 		                                                                                                                                                    August 3rd, 2009                                                                                                                                                                                                     [#4]("http://ubuntuforums.org/showthread.php?t=1230307&p=7725991#post7725991")                                                                                                                                                                                      		
  		 			 				 				 					 						 	[**[COLOR=#000000]lswb[/COLOR]**]("http://ubuntuforums.org/member.php?u=210286") 	 
 						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG]  					 					 						Dark Roasted Ubuntu 					 					 						[IMG]http://ubuntuforums.org/images/rank_17.png[/IMG] 					                                           					 					 						 							     						
 					 				
 			
 			 				 					Join DateDec 2006Beans1,133DistroUbuntu 10.04 Lucid Lynx 					 					 				
 			 		
 	
  	 		 		 		 		[h=2]Re: DIY home surveillance with a Webcam[/h] 		 				 				 		 			 				[INDENT] 					Try these:

[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)
[http://www.linux.com/archive/articles/114118](http://www.linux.com/archive/articles/114118)
[http://www.zoneminder.com/](http://www.zoneminder.com/)
[http://tech.shantanugoel.com/2008/05...d-twitter.html]("http://tech.shantanugoel.com/2008/05/14/keep-tab-on-home-security-with-a-webcam-and-twitter.html")

BTW, a google search for "linux webcam motion detector" returned all these on the 1st page.


Hope that helps in some way.
[/INDENT]

---

### Post by yancek on 2014-09-15
Motion and Zoneminder should work as expected.  You will need to do some configuring.  I'm not sure they are both in the repositories bu should be.

---

### Post by johnsmoke on 2014-09-15
Thanks for the replies folks. I did find some great tutorials on both online, especially a couple youtube vids. I did see that Motion seems to be the more stable interface, so I'll probably go with that.

Can anyone recommend a good IP, network-based cam that works with Ubuntu that also is night-vision capable that I can use with Motion? Just trying to set up my surveillance asap.

Thanks.

---

### Post by dave131 on 2014-09-15
I just checked and both Motion and Zoneminder are in the repositories and show in Synaptic Package Manager.  With that in mind, I would think they both should be fairly stable.  There is a brief description of both, and just going by those descriptions, I'd probably try either one - though Motion appears to be command-line oriented and I don't know if there is GUI'd front end to it or not.

If you don't already have the package manager installed:

- open a terminal window (ctrl/alt/t)
- type:

sudo apt-get install synaptic <press enter>.  It will ask for your password - just type it and press enter as it isn't echoed to the screen.

Once you have it installed, you can start it then put motion in the search string and it will take you to the package and its description.  Same thing with Zoneminder.  Of course, you can always install BOTH and see which one does what you need in the easiest way for you.

Sorry - can't answer the "which camera" question.

---

