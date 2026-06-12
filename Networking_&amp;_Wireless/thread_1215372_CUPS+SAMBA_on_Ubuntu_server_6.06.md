---
title: "CUPS+SAMBA on Ubuntu server 6.06"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by mathewfer on 2009-07-17
Hi 

I am trying to setup network printer on Ubuntu server 6.06 LTS with CUPS & SAMBA for Samsung CLP-315 printer. I want to setup this Ubuntu server as my print server.

So far, I managed to install the drivers (from Samsung site) & get the CUPS setup to some extent. I can access https:/server:631 from another Windows PC & print the test page very successfully - very good quality colours. I think the printer drivers are correct.

Now the issue is that I can not get other Windows PCs to print to that printer. I have setup the SAMBA file & printer shares & I can see the printer from all the windows PC. I can send the printouts from windows PC without any errors but NOTHING is printed on printer.

CUPS admin webpage does not show the print JOB unlike test page print that shows the print job in the queue.

When I checked error logs in error_log (in /var/log/cups/), I do not see any specific errors except for the below;

cupsdAuthorize: No authentication data provided.

root@U-SRV:/etc/samba# smbtree
Password:
HOMEXP
        \\U-SRV                         U-SRV server (Samba, Ubuntu)
                \\U-SRV\CLP-310splc     CLP-310splc
                \\U-SRV\print$          Printer Drivers
                \\U-SRV\MyFiles
                \\U-SRV\IPC$            IPC Service (U-SRV server (Samba, Ubuntu))
                \\U-SRV\ADMIN$          IPC Service (U-SRV server (Samba, Ubuntu))
        \\WINDOWS-PC                    Mathew Fernando
root@U-SRV:/etc/samba#

Thanks to let me know a working smb.conf & cupsd.conf files that is working for networking printing on Ubuntu 6.06 LTS server.

Mathew

---

