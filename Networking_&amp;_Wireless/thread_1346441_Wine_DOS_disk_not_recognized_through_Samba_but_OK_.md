---
title: "Wine DOS disk not recognized through Samba but OK through NFS"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by spectralx on 2009-12-05
Hello,

I have some job applications written in VisualFoxPro, and I want to make them running through Wine, in order to turn off all the M$ machines. I've managed that succesfully, except a single one. 

This application is a client-server model. The clients are installed on all the workstations, and is working with thei resources that are shared over the network through a Samba share on my Linux server. While working under Windows, there are no problems...

... *but* when I am trying to run the client under Wine, I am receiving an error message that is saying that the application cannot find the path of the files on the server.

To run the applications under Wine, I've mounted the server resources with smbmount and then I've mapped the local resource as disk S: in Wine configuration tool. Of course, I've checked if the S: disk is accessible, and it is (for example, running the cmd.exe under Wine and then changing to the S: disk). 

Also, I've tried to change the owner of all my files on the Linux server, to the owner of the user that I am mounting on the Linux client. Also tried to use "security = user" in smb.cfg, then mount the volume with the appropriate UID/GID . 

However, despite of my efforts, nothing good happened. 

Finnaly, I've give up on Samba and I've installed a NFS server. After 5 minutes of work, I've end up succesfully. The Windows application is running through Wine without any problem. Of course, I've mounted the NFS export under the same folder on my Linux client (that is an Ubuntu, hi). 

I would like to ask if somebody could help me with some ideeas to make the same thing work over Samba. 

In the hope of an answer, thank  you very much and have a nice week-end all !

Regards,
SpectralX

---

