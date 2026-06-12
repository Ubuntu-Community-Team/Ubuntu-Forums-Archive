---
title: "How to reinstall network-manager-gnome"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by ehsanoo on 2013-07-09
I have removed *dnsmasq-base* by mistake when I wanted to remove *dnsmasq*, which removed *network-manager* and also *network-manager-gnome* packages, and maybe some others, the problem is I don't have internet or even network access on my laptop anymore to try reinstalling them, I've downloaded those .deb files but I can't install them because of their dependencies, is there any way to automatically install them and all of their dependencies or I have to install any packages that is needed myself?


-------------------------------- Solved
Thank you guys for at least reading the problem!
The problem is fixed, you just need to get dependicies using Synaptic Package Manager and download them somewhere else, a tutorial is available [here]("https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection"), but if you are lazy like me, here's the brief explenation:

1. Open **Synaptic Package Manager**.
2. **Check packages** that you have removed and you want to install.
3. From the **File** menu, Choose **Generate package download script**.
4. Save the script in a portable drive like USB-flash.
5. **Run the script on another machine** using Ubuntu or any linux system, the script will download some .deb files.
6. Get back to your own computer and insert the drive, then choose **Add downloaded packages** from **File** menu and open the folder which those files are downloaded to.

You are done :) maybe you need to click on the **OK** button if there is any! :P 

If other machines are not running Ubuntu, don't worry, you just have to open the script as text and download links that are in script, those are direct links to some .deb files.

---

