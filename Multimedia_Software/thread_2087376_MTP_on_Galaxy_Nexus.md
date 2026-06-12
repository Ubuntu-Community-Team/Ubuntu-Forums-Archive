---
title: "MTP on Galaxy Nexus"
date: 2012-11-23
forum: Multimedia Software
---

### Post by alecjw on 2012-11-23
Hi, I'm trying to transfer music over to my galaxy nexus in rhythmbox under ubuntu 12.10. I get this error every time:
"Unable to send file to MTP device: PTP Layer error 02fe: get_storage_freespace(): could not get storage info."

It didn't work under 12.04 either.

Does anyone know the solution to this?

Thanks,
Alec

---

### Post by cwsnyder on 2012-11-23
I have a Samsung Galaxy Tab 2 7.0", and the best way I have found to transfer files does not work through USB, but by way of a wireless router, Filezilla on the host computer and Rapfox FTP Server app on the Galaxy.  The procedure is outlined on this thread: [http://ubuntuforums.org/showthread.php?t=2082437](http://ubuntuforums.org/showthread.php?t=2082437) bottom of page 2

---

### Post by cwsnyder on 2012-11-26
An alternative method, outlined here: [http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)

---

### Post by alecjw on 2012-11-26
I'm not sure this is a solution for the same problem that I'm having. I can mount the device just fine via MTP, and list files. I just can't write to or read from it. Installing an FTP server on my phone sounds like a very contrived way of doing it, and not very secure. Do you know of any other solutions?

Thanks

---

### Post by cwsnyder on 2012-11-27
Security:  Your router must block the FTP port from outside access while allowing access from other users on the same network.

The only other method I have found which works for general files, like ebooks, was to transfer them to a microSD card which was then plugged in to my Samsung Galaxy Tab.  This won't work if you have no microSD expansion slot.

---

