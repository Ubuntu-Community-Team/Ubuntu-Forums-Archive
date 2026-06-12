---
title: "Nvidia driver install"
date: 2006-08-04
forum: Multimedia &amp; Video
---

### Post by cardude on 2006-08-04
When i try to install the nvidia graphics driver i get this error.

Unable to find the system utility `ld`; please make sure you have the
         package 'binutils' installed.  If you do have binutils installed,
         then please check that `ld` is in your PATH.

Yet in synaptic it says 'binutils' is installed????????

---

### Post by Dr. Nick on 2006-08-04
I looks lile you are using the nvidia file from thier site, Is this so?

You may have better luck using this howto
[http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+howto](http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+howto)

to use the .run from nvidia probably requires you to install builld-essential and your kernel sources

---

### Post by cardude on 2006-08-04
Yeah i downloaded version 1.0-8762. I downloaded binutils of my Ubuntu CD but  when i start installing i get these errors:

 You appear to be running an X server; please exit X before
         installing.  For further details, please see the section INSTALLING
         THE NVIDIA DRIVER in the README available on the Linux driver
         download page at [www.nvidia.com](www.nvidia.com).

Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find
         suggestions on fixing installation problems in the README available
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

:confused:

---

### Post by Dr. Nick on 2006-08-04
if you dont use the link above then you have to close the gui out to install them. using the link i posted will allpw you to install them and they will update automaticaly.

But to install the ones you downloaded you have to run this command

sudo init 3

 That will close down the xserver and leave you at a command line. I think 3 is the right one, init 1 should restart the entire computer, I would test it for you but cant restart right now :)
 

Also you can reboot anc choose recovery mode which will keep xorg from loading.

---

