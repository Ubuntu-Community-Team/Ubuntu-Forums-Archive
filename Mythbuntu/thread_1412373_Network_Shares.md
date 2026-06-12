---
title: "Network Shares"
date: 2010-02-21
forum: Mythbuntu
---

### Post by Keith2065 on 2010-02-21
Hi Folks,
Apologies if this is a REALLY noob question, but I have little or no experience with Linux whatsoever.  I have recently install Mythbuntu on my laptop, with the plan to install it as my dedicated operating system on my Media PC.

Problem is I cant work out how to access Windows shares.  So far I have gathered I need Samba (which is installed, I believe).  Everywhere I look on the internet tells me to go to "Places" on the top bar.  And I don't have places on my top bar!  :confused:

Can anyone point me in the right direction?

Thanks,

Keith

---

### Post by kja999 on 2010-02-21
Hi,
The answers you are getting are dependent on your linux distribution (try to mention which flavour you are using in forums to get the most accurate help). With a Gnome desktop the places should have Network in which allows you to browse the windows network.

As you are setting up a media centre you (most likely?!) need proper shares setup though as opposed to occasional browsing.
This will involve adding entries to fstab:  [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I use autofs to dynamically mount windows shares when I need them from myth.. keeps things tidy.

Hope this helps a little.

---

### Post by williammanda on 2010-02-21
If you setup mythtv by mythbuntu or on top of gnome you have a very simple solution. Goto mythbuntu control center and select services > samba service and enabled it then apply. This will setup the three media directories ie pictures, videos, recordings so that you can access them through network on a windows computer.
Now if your trying to access files on the windows computer from ubuntu, you will need to select the windows drive, file, etc... and and enable share for that item. Once you do that goto places > networking and you should see the name of the windows computer. Select it and your windows shares should show up.

---

