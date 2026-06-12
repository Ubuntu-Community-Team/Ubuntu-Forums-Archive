---
title: "Printing to Ubunto CUPS from OS X"
date: 2005-01-14
forum: Networking &amp; Wireless
---

### Post by Jæd on 2005-01-14
Hi, 
 
 I'm having problems printing from OS X to CUPS on my Ubuntu box... I've set up my HP Photosmart as a CUPS printer and this works fine from Ubuntu. Looking at the CUPS web interface the location of it is [http://localhost:631/printers/PhotoSmart-P1115](http://localhost:631/printers/PhotoSmart-P1115).
 
 I've selected IPP Printing on OS X and have set the printers location. (192.168.0.4). OS X verifies that this is correct. I then set the printer queue as "PhotoSmart-P1115". But when I print I get the following error in the error log file:
 
 get_printer_attrs: resource name '/ipp/PhotoSmart-P1115' no good!
 
 I'm guessing I could make a sym link somewhere from  printers -> ipp but I'm not sure where...? 
 
 Can anyone give me any pointers?

---

### Post by JsPr on 2005-01-14
IIRC you might try using a postscript driver on the OS X computer. I seem to remember getting this error when using a non PS printer driver on the client.

Hope this helps.

---

### Post by Jæd on 2005-01-14
Solved by making the changes described [here]("http://www.cups.org/faq.php?16") and then modifying the printers detail in the cups web interface. And then ducking as it printed off lots of pages. (My printer is above my computer...)

---

### Post by jeffjj on 2005-01-23
Oh Jæd I wish you would have entered in more detail :).

I am trying to get my wife's mac working with cups and not having any luck. If you could post your complete fix that would be great!!

With the help of these forums I was able to get my client Ubuntu machine talking to my printer running on my Ubuntu server machine.

-Jeff

---

### Post by Jæd on 2005-01-24
Oops I think the link I gave is broken... Some more detail:
 
 Problem: I couldn't enter the correct ipp url when setting up a printer under os x
 
 Solution: Use cups to manually change the print queue
 
 Detailed Solution:
 
 First I setup the printer using the "Setup Printer" app on OS X. I planned to alter it via the cups interface later. Cups on OS X requires a password but giving the root password doesn't work. Apple changed the way passwords are used recently. I removed password protection for cups on OS X. This is very non-secure! 
 
 So... In the /etc/cups/cupsd.conf add a '#' in front of the lines.
 
 <Limit GET>
   AuthType Basic
   AuthClass System
  </Limit>
 
 Then restart cups with:
 
  sudo killall -HUP cupsd
 
 If you go the cups inteface [http://localhost:631/]("http://localhost:631/sam.html")  you won't be asked for a password and can edit the os x cups set up. To solve my problem I then manually edited the print queue for the printer in question. 
 
 Hope this helps!

---

### Post by snovak on 2007-10-10
Hmm.. I did have problems logging into CUPS but I just went to the log viewer. (Applications>Utilities>Console) then click "Logs" and browse down to cups> access_log after a couple of lines, I noticed that my user name had a capitol letter that I omitted.  When I used the right user name, it worked.  Go figure.  I didn't have to comment out any config lines on the mac side.  You DO however, have to enable printer sharing on the Ubuntu side.  I think it's in System>Administration>Printing.  And then reboot CUPS.  

But, I also found that I needed to add the printer through the CUPS web interface, which is weird.  So, again, that can be found at [http://localhost:631]("http://localhost:631").  Choose add printer.  And,, well,, add the printer.  WORKS NOW!  After an entire morning of finagling.  

Oh, right,, the path.  I found the path to my Ubuntu printer like this:
Log into the CUPS interface on your linux box. (My path was [http://192.168.0.101:631/printers/](http://192.168.0.101:631/printers/))
Right click the "Print test page" button and "Copy Link Location"
I did that and this is what I have now: [http://192.168.0.101:631/printers/DeskJet-970C?op=print-test-page](http://192.168.0.101:631/printers/DeskJet-970C?op=print-test-page)
Get rid of this part [http://192.168.0.101:631/printers/DeskJet-970C](http://192.168.0.101:631/printers/DeskJet-970C)**?op=print-test-page**
and now you have your path to use.  **[http://192.168.0.101:631/printers/DeskJet-970C](http://192.168.0.101:631/printers/DeskJet-970C)**

Back to work.

I hope this helps someone.

---

