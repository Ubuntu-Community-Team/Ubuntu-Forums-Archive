---
title: "How to install Realplayer"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by DGentry on 2007-09-08
Hey Guys, I've reloaded Ubuntu a couple times now and I've found one thing that's really frustrating.

I always run into an issue when I want to make real player work.
Ive searched on here and done google searches with not much luck.

I had a person named linuxwizard from this forum that led me in the right direction.
I'll copy the exact text from the site here and also the link to the directions on how.

Thank you LinuxWizard for the link to this.

[https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods?action=show&redirect=RealPlayerInstallationMethods)

Install RealPlayer for Linux from the RealNetworks web site

   1.

      Go to the [WWW] RealPlayer for Linux web page and download the installer to your Desktop.

    *

      A PowerPC version is avaliable from the [WWW] Helix Player Download page.

   1.

      Open the terminal and navigate to the file "RealPlayer10GOLD.bin". Type

       $ cd ~/Desktop

   2.

      Verify that the file is executable. If it isn't, type

       $ chmod a+x RealPlayer10GOLD.bin

   3.

      Run the installer by typing

       $ sudo ./RealPlayer10GOLD.bin

      and enter your password.
   4.

      Follow the prompts provided to finish installation.
   5.

      When you launch the player for the first time, a set-up assistant will take you through configuring your player. You can run the set-up assistant again at any time by choosing Reset RealPlayer from the Help men

---

### Post by Pumm4 on 2007-09-08
Did you tried to install with Synpatic Package Manager ?

[COLOR=Navy][I][B](Edit)
[/B][/I][COLOR=Black]If you're new, the path is as follows:
System > Administration > [/COLOR][/COLOR]Synpatic Package Manager > Click search and select the package you seek ...

---

### Post by Uncle_Grombor on 2007-09-09
It cannot be found through Synaptic unless you have a multimedia repo that is not common to ubuntu installs.  The first package to install is debian-multimedia-keyring.  In terminal type...

sudo apt-get install debian-multimedia-keyring

In Synaptic-Settings-Repositories-Third Party Software click the add button and type in [http://www.debian-multimedia.org](http://www.debian-multimedia.org)

Close the add console and click the reaload button on the top left corner of Synaptic.  Now do a search for Realplayer in synaptic.  It should be there.  Also, does anyone know of any other good repos of this nature that have more stuff?  I like games and I'm a dork!  :lolflag:

---

### Post by Uncle_Grombor on 2007-09-09
Maybe some of these other third party repos are overkill, but here is a link to them if anyone is interested.  Havn't done enough research on them yet to know if they have keys.

---

### Post by Uncle_Grombor on 2007-09-09
> **Uncle_Grombor said:**
> Maybe some of these other third party repos are overkill, but here is a link to them if anyone is interested.  Havn't done enough research on them yet to know if they have keys.

forgot the link.  oops  [http://blog.kovyrin.net/2006/03/27/unofficial-debian-reposotories-overview/](http://blog.kovyrin.net/2006/03/27/unofficial-debian-reposotories-overview/)

---

