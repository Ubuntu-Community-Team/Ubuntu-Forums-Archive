---
title: "Fast Secure Way To Network Mac Windows and Linux on Wireless Network?"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by cgb223 on 2011-08-31
Hey all, i have 4 computers at the moment on my wireless network that i would like to wire together in some groovy way to allow me to access any of the other computers hard drives from any computer. I need it to be able to transfer files quickly from one to the other, and preferably have some sort of encryption. As the title mentioned, on the network is a Mac, a Windows box, an ubuntu box 11.04 if it matters, and a netbook with Backtrack 5. I menton the netbook because what ever the answer is actually has to not bog down my netbook (a challenge in fact).


Help?


Figurative beer for the best answer!

---

### Post by northd_tech on 2011-09-01
Depending upon your flavor of Windows (9X, XP, Vista, Win7), you probably already have Windows Networking installed on that machine, so you should already be "wired for sound" there and can probably ignore that for now (you can check under Networking from Control Panel- it should be listed near your TCP/IP settings).   I'm just going to arbitrarily assume Win Vista here since that's what I usually play with lately (although I prefer Win XP, 2000/NT, and 98 truth be known).  Here is where you set the **Workgroup** for Windows Networking under Vista (and that will be a pretty important thing to get everyone "talking" to each other on the network:

 File and Printer Sharing in Windows Vista 
   Published: November 08, 2006 |  Updated: May 14, 2007
[http://technet.microsoft.com/en-us/library/bb727037.aspx](http://technet.microsoft.com/en-us/library/bb727037.aspx)

see also:

**Setting up a home network**
[http://windows.microsoft.com/en-US/windows-vista/Setting-up-a-home-network](http://windows.microsoft.com/en-US/windows-vista/Setting-up-a-home-network)

Now for Ubuntu (and probably the Backtrack 5 Linux netbook), you will probably need both a Samba client (too see the other machines on the Windows Networking **Workgroup**) as well as a Samba sever (to enable the other machines to "see" your Ubuntu and Backtrack Linux boxes under Windows Networking).  See one of several recent threads here at Ubuntuforums tagged "samba" for details on that (I don't want to reinvent any wheels on what is already extensively documented here):

[http://ubuntuforums.org/tags.php?tag=samba](http://ubuntuforums.org/tags.php?tag=samba)

After [successfully] configuring Samba on the Linux boxes, I would verify that you can "see" the Windows machine at this point before proceeding (probably under Places > Network > **Windows Network** > Workgroup > [your Windows machine name] ).

As far as the Mac, I personally avoid those like the plague so I can't really walk you through a Samba setup on those (I'm allergic to single button mice among other things), but here are some articles about just that:

Printing to a Windows (Samba) shared printer from a Mac
[http://www.mac-connect.com/smb_print_mac.php](http://www.mac-connect.com/smb_print_mac.php)

Mac OS X: How to connect to Windows File Sharing (SMB)
[http://support.apple.com/kb/ht1568](http://support.apple.com/kb/ht1568)

Inside Samba: Windows Sharing for the Mac
[http://macdevcenter.com/pub/a/mac/2003/03/18/samba.html](http://macdevcenter.com/pub/a/mac/2003/03/18/samba.html)

You will probably want to bookmark and/or print out and save these pages for future reference too: 

Networking Tips: Windows, Mac, and Linux PCs on the Same Network
Enable the machines on your cross-platform network to access and share the same files and resources.
[http://www.pcworld.com/article/122932/networking_tips_windows_mac_and_linux_pcs_on_the_same_network.html](http://www.pcworld.com/article/122932/networking_tips_windows_mac_and_linux_pcs_on_the_same_network.html)

Make UNIX work with Windows XP and Mac OS X
[http://www.ibm.com/developerworks/aix/library/au-unixothers/](http://www.ibm.com/developerworks/aix/library/au-unixothers/)

OK- once you've got Samba up and running on the Mac and the 2 Linux machines (Ubuntu & Backtrack 5), then go into each and make sure that your** Workgroup** is IDENTICAL on EACH machine on the network (I often copy/paste to prevent typos).  As I recall, on Windows machines CaSe does NOT matter, on Linux it definitely does, and I don't have a clue about Mac networking and cAsE.

You may or may not need to restart the various machines to get the network settings (mainly **Workgroup**) to take "hold" and hopefully be able to browse your "Network Neighborhood" (under Windows) and set up your "shared" files/directories and/or printers.  You will probably also want to set up a "public" (or Music, or Data, or Shared Data, or Shared Documents) directory on each of the Mac and Linux machines too, and hopefully you can just "plug & play" at that point (although you might need to "mount" the Shared directories under Places > Network > Windows Network under the 2 Linux machines.

Clear as mud?  :(

EDIT:  On the Windows (Samba) "shared resources," I think you can choose either open or username/password security:

Share and User Level access
[http://www.windowsnetworking.com/articles_tutorials/shareacc.html](http://www.windowsnetworking.com/articles_tutorials/shareacc.html)

---

### Post by cgb223 on 2011-09-08
Wow possibly the most thorough answer I've ever gotten on this forum. I'm gonna go get on this, thanks!

---

