---
title: "Localhost error with printer"
date: 2009-12-11
forum: Networking &amp; Wireless
---

### Post by atentik on 2009-12-11
I have a network printer that connects several printer to the main computer. After upgrading to ubuntu 9.10, the printer wont print anymore. Whenever, I tried to setup the printer by System->Admi->Printing, I get the following error
> **[SIZE="2"]CUPS server error[/SIZE]**
There was an error during the CUPS operation: 'client-error-bad-request'.
. I was able to go through localhost:631 and setup the printer from there but only the computers that have Ubuntu Operation system was able to see the printer and print. That is all the other computer with different operation system, Windows, were not able to see the printer. In addition, I am unable to even print from the main server. The main server is not seeing the printer. 

Then I did
>  tail /var/log/cups/error_log and got the following error. 
> Request from "localhost" using invalid Host: field "".

I suspect, this has something to do with the host field but not sure how to change it. Any help would greatly be appreciated.

---

