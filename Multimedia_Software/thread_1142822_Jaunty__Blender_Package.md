---
title: "Jaunty / Blender Package"
date: 2009-04-29
forum: Multimedia Software
---

### Post by coilgunner on 2009-04-29
I am using the new Jaunty Jackalope Ubuntu 9.04 release and I'm having an error while trying to install Blender. It's probably a dumb error, on my part. 

My Ubuntu box has no internet, and I put the bz2 folder onto a thumb drive and moved it over. When I put it onto my desktop I extracted the archive successfully and then extracted the tar file onto my desktop. I now have a blender directory, with all of the normal stuff inside. When I open the terminal and navigate to my blender directory and run the "sudo apt-get install blender" everything seems to go fine until it reaches the end, and then it says "E: Couldn't find package blender"

I went to accessories and opened Add/Remove and then looked up blender, I told it to install that way, but since there is no internet connection it gave me a bunch of fetch errors, regarding that it could not connect to the appropriate site.

Any help would be appreciated.

---

### Post by mihai.ile on 2009-04-29
oh... you downloaded the original source files of blender.
Not that it's wrong but it's harder to get it working because you have to compile the application first.

When you want to download software for Ubuntu always try to find .deb files for it as it's much easier (double click and that's it).

Now I could say you can go to a internet and on this page:
[http://packages.ubuntu.com/jaunty/graphics/blender](http://packages.ubuntu.com/jaunty/graphics/blender)
you find at the bottom the download of blender for i386 or 64bit systems.

But this won't help because you would need to install all dependencies listed over there before as Ubuntu won't let you install the file.
Many of the dependencies are already installed on your Ubuntu but some aren't.

Maybe another user could help you in specifying which .deb files to download besides the blender .deb file

EDIT:

I found on the net some tools that say that could help in installing software on systems without internet but didn't tested them:
(a must read to understand your problem and with a solution)
[http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/](http://kmandla.wordpress.com/2007/07/24/howto-download-packages-and-dependencies-for-offline-installation/)

(this one is confusing I think)
[http://www.khattamonline.co.cc/2009/04/21/update-and-add-packages-to-your-offline-ubuntu-installation-with-ease/](http://www.khattamonline.co.cc/2009/04/21/update-and-add-packages-to-your-offline-ubuntu-installation-with-ease/)

(interesting idea, server now offline though)
[https://launchpad.net/pd](https://launchpad.net/pd)

(this seems easyer but don't know about Ubuntu support)
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by coilgunner on 2009-04-29
Ok, thanks!  I'll have to look for the debs.

---

### Post by mihai.ile on 2009-04-29
also see edit part of my post

---

### Post by coilgunner on 2009-04-29
Thanks, this was what I was looking for.  However, I think my best bet is to just move my computer to where my wired internet is and then using the packet manager to download blender via the add/remove application.  This should get me my full download, without too much trouble.  Then I'll just move it back.

---

### Post by EXCiD3 on 2009-04-29
You could use [Keryx]("http://keryxproject.org") for your offline computer.

---

