---
title: "samba/swat connect to server 2008 domain"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by DCalabrese on 2010-07-30
Hi: I'm new, totally confused - on adding Ubuntu 10.04 web server to a windows server domain [static IP's] . I created a main user and installed gnome/samba/swat etc. I then created an administrator user but did not install samba/swat. Followed Ubuntu forums Mount Windows Share Permanently up to part where it says:
 
***Note:** Regretfully as from version 3.3.2-1ubuntu3.2 (October 2009) this approach is no longer possible . . . *
 
Is this referring to the steps I've just taken?. . . the steps below that I've not taken? How do I get just a simple share between ubuntu and a windows server 2008 server? Really need help. 
 
Thank you in advance, Chris

---

### Post by redmk2 on 2010-07-30
> **DCalabrese said:**
> Hi: I'm new, totally confused - on adding Ubuntu 10.04 web server to a windows server domain [static IP's] . I created a main user and installed gnome/samba/swat etc. I then created an administrator user but did not install samba/swat. Followed Ubuntu forums Mount Windows Share Permanently up to part where it says:
 
***Note:** Regretfully as from version 3.3.2-1ubuntu3.2 (October 2009) this approach is no longer possible . . . *
 
Is this referring to the steps I've just taken?. . . the steps below that I've not taken? How do I get just a simple share between ubuntu and a windows server 2008 server? Really need help. 
 
Thank you in advance, Chris

See were it says *[COLOR="Blue"]**"A security fix prevents reading the credentials file..."**[/COLOR]*.  It is referring to the credentials files above.

Be aware there are several ambiguous sections and even some errors in that howto.  What are you trying to mount from a remote host?  How much integration into the Windows domain do you really need?  

The web server will server web pages without needing to be part of the AD domain.

---

### Post by DCalabrese on 2010-07-30
Thank you for such a timely reply. I can ping the gateway, but none of the windows servers.  Seems like it must be a Linux firewall issue.  . .will dig deeper.
 
Any help is greatly appreciated. Chris

---

### Post by redmk2 on 2010-07-30
> **DCalabrese said:**
> Thank you for such a timely reply.  Do I need to undo what I just did [directions above warning] and how do i undo it?  
The simple answer is: Delete the file and remove the reference to it in the /etc/fstab file.  That's really not a satisfactory answer though; is it?  I would look for another way of doing this while accomplishing the same end result.> 
Just getting a single shared folder between one server 2008 and ubuntu is all we need to move the website files to the new web server.  
And so...thinking outside the box; Are you doing this one time only?  Do you really need to share the directory?  Most of the web servers (actually all) I have maintained have used FTP to move files to the production site, or a place where the webmaster can move them to their permanent location.> 
I can ping the Ubuntu from the server 2008.  Can't ping the windows server from Ubuntu.  Any help is greatly appreciated.  Chris
Are you telling me that you **do not **have TCP/IP connectivity (in both directions)?  If this is so then no amount of fiddling with Samba or any other sharing will work.  I'll bet you meant ping by name; am I right?

So the questions seem to be:[LIST]
[*]Do we need to do this one time only?
[*]Do we really need this to be shared using smbfs/CIFS?
[*]Can we use FTP (or even sFTP)?
[/LIST]

---

### Post by redmk2 on 2010-07-30
> **DCalabrese said:**
> Thank you for such a timely reply. I can ping the gateway, but none of the windows servers.  Seems like it must be a Linux firewall issue.  . .will dig deeper.
 
Any help is greatly appreciated. Chris

Why do you think it is a FW issue?  If you can ping one host, why would you net be able to ping another.  Anything that has an IP address is a host and unless you have made very specific rules all should be reachable.  What error do you get back?

**Edit:**When you delete items from a post using edit we loose our train of thought.  Try and just add to the post rather than deleting everything and starting over.  :D

---

### Post by DCalabrese on 2010-07-31
1. Need permanent windows share - should this be so hard to do???
2.  firewall not the issue 
Thanks for the reply and tip on posting. 
Newbie Chris

---

### Post by redmk2 on 2010-07-31
> **DCalabrese said:**
> 1. Need permanent windows share
Explain why.> 
 - should this be so hard to do???
Easy to do, but hard to explain.  How are you sharing the directory on the W2008 host?  Are all users allowed to access the share? > 

2.  firewall not the issue 
Does this man that you can ping (by name) in both directions?> 
Thanks for the reply and tip on posting. 
Newbie Chris

Without knowing more details about your needs I'm not sure what to advise you.

---

### Post by DCalabrese on 2010-07-31
Hi: Can ping both ways between Ubuntu and Windows. 
 
What I need is to be pointed to instructions on how to set up a single share between Ubuntu 10.04 server & windows 2008 server, preferably using samba. 
 
Thanks Chris

---

### Post by redmk2 on 2010-07-31
> **DCalabrese said:**
> Hi: Can ping both ways between Ubuntu and Windows. 
 
What I need is to be pointed to instructions on how to set up a single share between Ubuntu 10.04 server & windows 2008 server, preferably using samba. 
 
Thanks Chris

Try [**_here_**]("http://www.google.com/search?hl=en&q=cifs+mount&aq=f&aqi=&aql=&oq=&gs_rfai=").

---

### Post by DCalabrese on 2010-07-31
[SIZE=3][FONT=Calibri]Hi: Thank you for the link. Shouldn't this simple method for windows 7 also work on server 2008?     It goes smoothly until I get to [/FONT][/SIZE][FONT=Calibri][SIZE=3]step 9 where it accepts the psswd and looks for share but is unable to mount.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]smb://username@IPAddress/share [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]user name is Administrator[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]sharename is "home" on c: drive of server 2008[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]caps issue, syntax issue? no experience with Ubuntu Thanks Chris[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]+++++++++++++++++++++++++++. [/FONT][/SIZE]
[FONT=Calibri][SIZE=3]INSTRUCTIONS[/SIZE][/FONT]
[SIZE=3][FONT=Calibri]1. On your Windows 7, create a new folder to be shared.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]2. Right click the folder and choose &#8220;Share With&#8221; &#8220;Specific People&#8230;&#8221;.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]3. Type the user account of a user that has local rights on the Windows 7 [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]4. Change the permissions level on the right accordingly.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]5. Click the &#8220;Share&#8221; button then click &#8220;Done&#8221;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]6. On Ubuntu 10.04, right click desktop and choose "Create Launcher.&#8221;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]7. In the &#8220;Type&#8221; field, choose "Location"[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]8. In the "Name" field, type a name for your share.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]9. In the "Location" filed, type &#8220;smb://username@IPAddress/share&#8221;[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Example= smb://dave@192.85.45.2/pictures[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]10. Click the "OK" button, enter the password of your Windows 7 user [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]11. At that point the shared folder should be mounted on your Ubuntu 10.04 desktop and should show up under &#8220;Places&#8221;[/FONT][/SIZE]

---

### Post by DCalabrese on 2010-07-31
[http://www.itsolutionskb.com/2009/04/adding-ubuntu-to-a-windows-server-2008-active-directory/](http://www.itsolutionskb.com/2009/04/adding-ubuntu-to-a-windows-server-2008-active-directory/)
 
THIS APPROACH WORKED FINE.  THANK YOU FOR YOUR HELP.  PLEASE CLOSE THE POST
 
Chris

---

