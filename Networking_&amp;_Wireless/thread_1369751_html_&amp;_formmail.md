---
title: "html &amp; formmail"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by icka69 on 2010-01-01
Hello,
I'm trying to create a 5 pages based web page.
My problem is that in one of the pages there must be the option of contact us. For that the user must fill in a form and then that form will be sent to an email account( in this case my email).
For this im trying to use the FormMail script. Here starts the problem. The main pages and the other pages will go in the folder, and i have inserted a cgi-bin folder into the main folder.In this folder I have copy the Formmail.pl(with all the permissions).
In the page where the form is i have put this header:
<form action="/cgi-bin/FormMail.pl" method="POST">
and then in the FormMail.pl i have put the mailprog like this:
$mailprog = '/usr/sbin/ -i -t';
i have also tryied with this:
$mailprog = '/www/wp/' (here i have all the pages)
the problem is that with some configurations when i fill in the form and i send it, the option of downloading the form runs...
otherwise i receive the following problem:

**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.12 (Ubuntu) Server at localhost Port 80




I dont know what can i do...If somebody can help me it could be really nice....
thanks!
 		                   		  		  		  		  		  	   	 		 [IMG]http://ohioloco.ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ohioloco.ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ohioloco.ubuntuforums.org/report.php?p=8577104") 		 		  	 	 	 	 		  		 			[IMG]http://ohioloco.ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ohioloco.ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ohioloco.ubuntuforums.org/editpost.php?do=editpost&p=8577104")

---

