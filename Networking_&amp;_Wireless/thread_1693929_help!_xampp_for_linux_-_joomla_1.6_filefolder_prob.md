---
title: "help! xampp for linux - joomla 1.6 file/folder problems"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by joopie18 on 2011-02-23
Hi folks,

I have been using **lampp** (= xampp for linux) for a while now to test my **joomla** sites. I set my website folders in my home folder and then link them to the lampp folder. 

I have a difficulty though. Any time I want to **install an extension or template**, I get some _error_. Sometimes the folder cannot be found, other times it cannot be written, other times the tmp folder is unusable... Is there anyone that has _set xampp for linux and joomla 1.6 up_ so that it works and are you interested in sharing that with the larger community?

thanks in advance
Wc


Edit: Example:
	
[LIST]
[*]JFile: :write(tmp/install_4d65715746963/Joom!Fish 2.1  development/admin/assets/css/help.css):  fopen(/home/user/websites/one/tmp/install_4d65715746963/Joom!Fish 2.1  development/admin/assets/css/help.css) [[function.fopen]("http://localhost/trouw/administrator/function.fopen")]: failed to open stream: No such file or directory
[*]Unable to write entry
[/LIST]

---

### Post by joopie18 on 2011-02-26
BUMP!!

this is getting frustrated. lost hours on it.

I have read
[http://forum.joomla.org/viewtopic.php?f=429&t=351463](http://forum.joomla.org/viewtopic.php?f=429&t=351463)
[http://forum.joomla.org/viewtopic.php?f=431&t=508627&view=next](http://forum.joomla.org/viewtopic.php?f=431&t=508627&view=next)
[http://www.joomlatutorials.com/joomla-tips-and-tricks/40-miscellaneous-joomla-tips/113-joomla-and-unix-file-permissions-explanation.html](http://www.joomlatutorials.com/joomla-tips-and-tricks/40-miscellaneous-joomla-tips/113-joomla-and-unix-file-permissions-explanation.html)
and many others...

I have tried to change to the users of my files to
root:root
www-data:www-data
nobody:nogroup

I set the file and folder permissions to 777

I have checked my htdocs folder (/opt/lampp/htdocs) with a test file

all with **no effect**...

finally I found a solution :( 
migrate back to w$
[no need to criticise me for that; the work just has to be done!]


PS: Is this ubuntu? Or Xampp? Or Joomla? Who knows!

---

