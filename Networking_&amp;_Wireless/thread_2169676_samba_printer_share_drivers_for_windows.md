---
title: "samba printer share drivers for windows"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by corsairetc on 2013-08-23
Hi,
I set share printer via samba for windows clients. Printer work under cups this works perfect but I want to distribute windows drivers for user from my linus server. Is there any how to do it. I found some helps in google but this not work.

---

### Post by TheFu on 2013-08-23
I've done this in year past, but not recently.  As I recall, it was a mixed CUPs and Samba solution where the client told samba which OS it was running and the drivers had to be located in a very specific share within specific subdirectories by the OS for it to work.

There must be a guide at the samba.org website for this. ... [found it]("https://wiki.samba.org/index.php/Samba_as_a_print_server#Uploading_printer_drivers_for_Point.27n.27Print_driver_installation").  . Did you have specific questions about that document or [this]("https://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/classicalprinting.html#id2627627") one? 

For us to help you, please state exact versions of OS, samba, CUPS, show exact configurations, exact error messages from the logs, and extremely clear "what happened" details into the post.  A list of client types would be helpful too.

Be aware that Samba v4 is a huge, huge, huge, redesign over prior versions. It added support for AD as a domain controller - replacing completely Microsoft's version. If you are running this version, things are probably very different (I don't know since I've not run it anywhere yet).

---

### Post by corsairetc on 2013-09-03
Now I use 64bit Debian wheezy
samba version is: 3.6.6
cups version is: 1.5.3
I  share printer in samba and also make share print$ where is should be  drivers. After this I try to make same steps as in samba how to [https://wiki.samba.org/index.php/Samba_as_a_print_server#Uploading_printer_drivers_for_Point.27n.27Print_driver_installation](https://wiki.samba.org/index.php/Samba_as_a_print_server#Uploading_printer_drivers_for_Point.27n.27Print_driver_installation)
Only  problem is I cant add driver from windows client it is grey like I has  no rights for this. I am not sure where can I add this privilegies.

---

