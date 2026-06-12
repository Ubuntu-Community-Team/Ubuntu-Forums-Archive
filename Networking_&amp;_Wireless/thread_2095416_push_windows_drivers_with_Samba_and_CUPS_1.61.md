---
title: "push windows drivers with Samba and CUPS 1.61"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by markosjal on 2012-12-16
I am trying to get cups to push out Postscript drivers to windows machines. I have found a number of tutorials and most of them are clearly older and many with no dates nor references to versions. This is XbmcBuntu (ubuntu 12.04) with CUPS updated to 1.61 via Ubuntu 12.10 packages 


I have the following in smb.conf, but have tried many variations
[print$]
  comment = Printer Driver Download
  path = /var/lib/samba/printers
  browseable = yes
  guest ok = yes
  read only = yes
  write list = @samba-printers, root

when I run 
cupsaddsmb  -U root -v -a

I get 
Password for root required to access localhost via SAMBA:  ****
No Windows printer drivers are installed.


Clearly the drivers are correctly indicated in smb.conf, and installed there . Do they need to be references somewhere in CUPS config? Maybe CUPS is looking for the windows drivers elsewhere?

I found this line commented and modified it accordingly
# Location of Samba configuration file...
SMBConfigFile /etc/samba/smb.conf

So the result is when I try to connect to the printer from Windows it is not finding the drivers from 

/var/lib/samba/printers/W32X86

nor from 

/var/lib/samba/printers/w32x86

Windows 7 32 bit client reports
No Driver Found
Can not find driver on the network.....

from another linux Machine I can see the print$ share so I know it is there but CUPS does not see it

---

### Post by markosjal on 2012-12-19
Answering my own post for archival purposes

Here is the magic cups smb command
(as root) 

cupsaddsmb -H localhost -U root -h localhost -a -v

Make sure that root is defined with write permissions in the print$ share in smb.conf and that you conform the smb.conf as defined in the ink below

Also if you want cups to be able to connect to a printer that is shared via Windows or SMB or a NAS like one of mine with native windoze sharing for printers
(as root) 

apt-get install samba-client



if you have issues you can test your username and password with
(as root) 

smbclient //localhost/<sharename> -U root

Obviously with the localhost references above it all assumes it is done on the local machine or via ssh

Now my remaining issue is that I now have an error in windows that it can not find the share when connecting the printer but no longer complains about the drivers at least 

I want to be clear that this is CUPS 1.61 . There is a lot of documentation around with the wrong syntax for cupsaddsmb command. Those posts lack dates and versions. I think it is imperative that people date posts and specify versions.  There is more useful information at 

[http://www.cups.org/documentation.php/doc-1.6/man-cupsaddsmb.html](http://www.cups.org/documentation.php/doc-1.6/man-cupsaddsmb.html) 

however far from complete in my opinion.

---

