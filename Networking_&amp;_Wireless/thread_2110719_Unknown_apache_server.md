---
title: "Unknown apache server?"
date: 2013-01-31
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2013-01-31
I have a verry weird problem.  I had FreeBSD 9.1 on my server at home running apache, tomcat, and a few other services including SSH.  I was able to SSH into it and get to my web server externally.  Then I switched ISP's and put Ubuntu on my server since I've had better luck with PVR software on it.  I also have a new wireless router (belkin).  I setup my router in the DDNS section with my username and password.  I can get to my web server but can't SSH in.  I've set up all the forwarding correctly.  Here's where it gets weird.

The default page for apache says

"It works!

More info here..."

When I go to my website externally I just get a page saying "It works!"  I thought this was weird so I added some !'s on the end just to see if it updated.  It didn't.  I then removed the default page and built a new one.  I still get the same it works page.

Nothing else on my network is running apache.  I've got a Pi running XBIAN on my TV.  I checked my DHCP client list and tried going to all of the IP's just to make sure.

My work laptop runs apache, tomcat, and some other services.  So I shut that down making sure it wasn't the issue, and I get the same results.

I emailed DDNS and they verified all settings on their end are correct, at least as far as they can tell.  Now I'm starting to think my network was hijacked, maybe?

At this point I don't care about the server as much anymore as I do security.

I'd love to hear what everyone thinks about this strage problem.

---

### Post by SeijiSensei on 2013-01-31
The default DocumentRoot on Ubuntu is /var/www.  In that directory is the default index.html file with the "It Works!" code.  Either you can put your existing website in that directory, or you can change the configuration in /etc/apache2/sites-available/default to point to your existing website directory.  The directory must be readable by the "www-data" user, which is the name of the user the Apache server daemon runs as.

When you make changes to the Apache configuration, you must restart the server with "sudo server apache2 restart".

---

