---
title: "Connect to FTP with Login &quot;The file is not a directory&quot;"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by LinuxLars on 2008-12-18
Using 8.04 on Lenovo X61s.

Using Nautilus Connect to server, and choosing FTP (with login), entering our company server's IP address (which does not have a domain name), user, and hitting "Connect".

Prompts for password, and then displays: 
"The folder contents could not be displayed"
"Sorry, couldn't display all the contents of "/ 
on <ipaddress>.21": The file is not a directory"

Yet, in a terminal session, everything works fine:

$ ftp
ftp> open
(to) <ipaddress>
Connected to <ipaddress>
220 ---------------
Name (<ipaddress>:<mylaptoplogin>): <ftpusername>
331 User name okay, need password.
Password:
230 User logged in, proceed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT Command successful.

and on and on. Works fine.

Is this a bug? Or am I missing something with Nautilus? (I can successfully connect to a drive on our windows server, so I think I know how it works).

---

### Post by jonobr on 2008-12-18
I tested this on intrepid 8:10 and its working ok,
When I follow the step you mentioned, I dont enter port number and directory (accept the default associated with login)
it gets me to an ftp  server.

If you did the same sounds like it might be a bug, I would recommend doing a tcpdump or wireshark trace to see whats going on.
You could compare the two.
Im also wondering if its something to do with PASV mode,
your trace , if you run it should confirm that....

---

### Post by LinuxLars on 2008-12-19
I've repeated the tests again today. Nautilus will not connect (maybe it's because it's an IP address and not a domain?).

However gFTP works fine.

---

### Post by jonobr on 2008-12-19
nah... IP/domain shouldn't matter

I recommend you do a tcpdump on the port to see why its not connecting and post the results here

---

### Post by LinuxLars on 2008-12-19
I understand it "shouldn't" matter. But it's just not working through Nautilus.

I've attached the results of the tcpdump monitoring port 21.

Cheers!

---

### Post by jonobr on 2008-12-19
[https://launchpad.net/ubuntu/+source/nautilus/+bug/35943](https://launchpad.net/ubuntu/+source/nautilus/+bug/35943)


what version of nautilus are you on?

---

### Post by LinuxLars on 2008-12-20
Looks like 1:2.22.5.-1-0ubuntu.

Just a normal 8.04 install and using Update Manager.

---

### Post by phiphi on 2008-12-31
I've got the same Problem.

What I can say, is that it's not a problem of IP/domain. I use domain.

To me it seems to be a problem with the directory on the server. the folder for the user is not the root / folder of the server it is: "/d:/www/edvl/badi-event.ch/html" when i connect with FireFTP or other clients.

So Nautilus tries to connect to badi-event.ch**/** where it has no permission!

When connecting with the ftp> (Terminal) to "badi-event.ch**/**" there is also an error "ftp: badi-event.ch**/**: Unknown host
Opening "badi-event.ch" leads to prompting the Username and afterwards the pw

Perhaps Nautilus automatically adds the / at the end of the URL and this causes problems.

Connecting directly to badi-event.ch/d:/www/edvl/badi-event.ch/html does not work either.

---

### Post by phiphi on 2008-12-31
Bug reported on launchpad
[https://bugs.launchpad.net/nautilus/+bug/312722](https://bugs.launchpad.net/nautilus/+bug/312722)

---

### Post by RealG187 on 2009-09-25
[http://forums.fedoraforum.org/showthread.php?t=230743](http://forums.fedoraforum.org/showthread.php?t=230743)

I have the same problem in Ubuntu on Nautilus. I cannot connect to my FTP. (See screenshot)

The FTP Server is: [COLOR="Red"]ftp.operation420.net[/COLOR]
The FTP Account is: [COLOR="Red"]test@operation420.net[/COLOR]

I have given these credentials for users to test and see if they can get it working, please do not abuse this.

---

### Post by LinuxLars on 2009-09-26
You can also just use gFTP....

---

### Post by RealG187 on 2009-09-27
> **LinuxLars said:**
> You can also just use gFTP....Using gFTP will never match up to just usibg a stanard file manager.

Nautilus is a million times easier and faster...

---

