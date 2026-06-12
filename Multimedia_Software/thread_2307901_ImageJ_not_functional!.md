---
title: "ImageJ not functional!"
date: 2015-12-29
forum: Multimedia Software
---

### Post by sadafmmm on 2015-12-29
Hi!
I recently installed ubuntu 15.10 alongside Windows 10 with dual boot. I need to use ImageJ for viewing some medical image files hence installed it using the terminal (sudo apt-get install imagej). The installation was successful but I don't understand why doesn't the app work?
I also didn't have any problems with installing ubuntu 15.10, everything went pretty smooth.

I have attached a screenshot to describe my problem. I get errors when I try to 'Open' any image or image sequence. 
Any help is appreciated. 
Thanks.

---

### Post by brian-mccumber on 2015-12-29
Have you tried this - > [COLOR=#000000][FONT=Arial]Windows are blank or stacks are not displayed correctly on Ubuntu with compiz enabled.[/FONT][/COLOR]Disable all effects in System Preferences > Appearance > Visual Effects.


---

### Post by sadafmmm on 2015-12-29
> **brian-mccumber said:**
> Have you tried this -

It states that 'Ubuntu with compiz enabled' and I did not download any app as such. Also I don't see any 'Visual Effects' option in 'Appearance'. 
I got a confirmation from my friend that ImageJ works without a hitch in his laptop also on ubuntu 15.10. :(

What seems to be wrong with mine?

---

### Post by brian-mccumber on 2015-12-29
Compiz is the open gl windows manager that comes with Ubuntu. Have you tried to start imageJ from the terminal to see if it is throwing errors or missing packages?

The quote I posted was from the imageJ documentation. Maybe you have installed an older version of it or something, it's hard to tell from where I am sitting. I am just trying to help you troubleshoot this install.

---

### Post by coldraven on 2015-12-29
This is a wild guess but did you also install "ubuntu-restricted-extras"?
Part of that package is Microsoft True Type fonts, maybe the garbage that you are seeing are font display errors.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Edit: At the beginning of the install process there is a check box for this that you may have missed. Maybe your friend did not miss it.

---

### Post by sadafmmm on 2015-12-29
Well like I said I didn't find any 'Visual Effects' option. Also didn't find 'compiz' in dash. I've tried running ImageJ from terminal and I don't see any error messages. I've attached a screenshot of that.
Interestingly I downloaded the [ImageJ bundled with java]("http://rsb.info.nih.gov/ij/download/linux/ij149-linux64-java8.zip"), extracted the folder and it actually works! I have no idea why can't I use it by downloading from terminal like everyone else does.
And I really do appreciate your help. Thanks.

[img]http://i.imgur.com/zFe8vle.png[/img]

---

### Post by brian-mccumber on 2015-12-29
That is strange, maybe java is not properly installed or configured or it was just a botched install like a packet got dropped or something while it was downloading or the wrong version was installed.

Compiz is a background process that controls the drawing of your windows. I was going to post a screen shot of the System Monitor showing compiz but everytime I try to add an attachment I get logged out of the forums.

---

### Post by sadafmmm on 2015-12-29
> **coldraven said:**
> This is a wild guess but did you also install "ubuntu-restricted-extras"?
Part of that package is Microsoft True Type fonts, maybe the garbage that you are seeing are font display errors.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Edit: At the beginning of the install process there is a check box for this that you may have missed. Maybe your friend did not miss it.

Ok I don't have ubuntu-restricted-extras installed. Should I install it and check if it works? Which check box are you talking about?

---

### Post by sadafmmm on 2015-12-29
> **brian-mccumber said:**
> That is strange, maybe java is not properly installed or configured or it was just a botched install like a packet got dropped or something while it was downloading or the wrong version was installed.

Compiz is a background process that controls the drawing of your windows. I was going to post a screen shot of the System Monitor showing compiz but everytime I try to add an attachment I get logged out of the forums.

How should I fix it then? I have very little knowledge on this. I saw compiz on System Monitor as a process running. Also, I don't think this is a font problem as I can't even use the options that I can read i.e. 'Open' an image etc.

---

### Post by brian-mccumber on 2015-12-29
It is hard to say how to fix it when we don't know what is wrong with it. At this point it could be a number of things, you could always uninstall it and try to reinstall it maybe there was an error that slipped by you when the terminal was scrolling while it was installing.

Also I found this on the imageJ docs page at [http://rsb.info.nih.gov/ij/docs/install/linux.html](http://rsb.info.nih.gov/ij/docs/install/linux.html)

it says 
> To install and run ImageJ, [download ]("http://rsb.info.nih.gov/ij/download.html")ImageJ bundled with either 32-bit or 64-bit Java, extract the ImageJ directory from the ZIP archive, change to the ImageJ directory and double click the "ImageJ" launcher.

So you may have already fixed your problem when you downloaded the correct bundle. I am thinking that the package from the software center is missing the java portion and that java would have to be installed, configured, and working before the package from the software center would work. You could just use the version that is working correctly and remove the other.

---

### Post by coldraven on 2015-12-30
> Ok I don't have ubuntu-restricted-extras installed. Should I install it  and check if it works? Which check box are you talking about?
When you originally installed Ubuntu after choosing your location etc. there is a check-box for it.

Reading the above posts I'm probably wrong about the fonts, it's most likely a java problem.
For more info on what you have installed you could install Synaptic Package Manager, think of it as Software Centre Pro! 
It will show you what version of Java etc. that you have. A good program to learn about in any case. You cannot run Synaptic at the same time as the Software Centre because they are both just front-ends for the apt package utility.

Tutorial here:
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

and here:
[http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html](http://www.ubuntugeek.com/synaptic-package-manager-beginners-guide-for-ubuntu-users.html)

---

### Post by sadafmmm on 2016-01-01
> **brian-mccumber said:**
> It is hard to say how to fix it when we don't know what is wrong with it. At this point it could be a number of things, you could always uninstall it and try to reinstall it maybe there was an error that slipped by you when the terminal was scrolling while it was installing.

Also I found this on the imageJ docs page at [http://rsb.info.nih.gov/ij/docs/install/linux.html](http://rsb.info.nih.gov/ij/docs/install/linux.html)

it says 


So you may have already fixed your problem when you downloaded the correct bundle. I am thinking that the package from the software center is missing the java portion and that java would have to be installed, configured, and working before the package from the software center would work. You could just use the version that is working correctly and remove the other.

Okay man. Did remove the one from software center and using the downloaded one. Still confused on why this happened :/
Could you please download it from terminal and try the software? It's small and you could remove it afterwards. Just wanted to see if this problem exists only in my one or not. 
Thanks a lot for your help.

---

### Post by brian-mccumber on 2016-01-01
Did you have Java installed and configured on your computer before you installed the package from the software center? If not I am pretty sure it was a problem with the required java packages missing from your computer since the package that came bundled with Java worked.

---

