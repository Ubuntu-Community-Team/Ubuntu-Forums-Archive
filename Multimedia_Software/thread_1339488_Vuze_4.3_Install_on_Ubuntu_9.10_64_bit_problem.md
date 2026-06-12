---
title: "Vuze 4.3 Install on Ubuntu 9.10 64 bit problem"
date: 2009-11-27
forum: Multimedia Software
---

### Post by techguy615 on 2009-11-27
I had some trouble installing Vuze 4.3 on Ubuntu 9.10 64 bit. Apparently the version in repositories is NOT supported by Vuze and when you open the client it tells you that your running an unsupported version. It seemed like I did the install and launched vuze again, but the site still said it was still an unsupported version.

Here is what I had to do correct the issue:

1) Uninstall the version from repository.
2) Download the latest version from the Vuze site.
3) Make sure you have the newest version of Java installed (64bit).
4) Extract the install files from the Vuze site to your home directory or another easily accessible folder.
5) open a terminal and go to the extracted files.
6) Copy the "swt.jar" file from this folder "/etc/alternatives/swt.jar" and replace the one found in the vuze folder. (if you can't fine it just search the file system for "swt.jar" to find it).

NOTE: If you do not perform step #6 you will probably get an error that says something like this when you try to do the install using the instructions:

*Browser check failed with: Cannot load 32*-*bit SWT libraries on 64*-*bit JVM Auto*-*scanning for GRE*/*XULRunner*. [I]You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.

This error above is what almost drove me crazy. 

[I]7) Open the terminal in the vuze install folder and execute the script "./azureus".

The install should work just fine, and if I recall correctly it should automatically launch from there. :)

This whole problem is caused by the version of "swt.jar" in the vuze install files is 32 bit and not 64 bit.

Launching the application from there is a little more tricky. This site taught me a great deal about all of this: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

Personally, I just copied the vuze folder to my home directory and created a launcher to run "azureus" from /<homedir>/vuze"

 So thanks to this guy for his contribution. I couldn't have worked through it with out the added info.

Cheers! 
:D
[/I][/I]

---

### Post by d0ti5 on 2009-11-29
Thanks, brother!  It also worked with the 32bit version.  What a pain that the update is anything but automatic, but your instructions made it easy.  Cheers!
****

---

### Post by cforceleritas on 2009-12-01
Ahhh!  Fixed me up too... I was banging my head over the ```
Cannot load 32-bit SWT libraries on 64-bit JVM
``` error as well.

Finally I stumbled upon this post and all was saved!  Thanks a bunch techguy615

---

### Post by Vignesh S on 2009-12-08
Thanks HEAPS!!! That saved my sanity there. I had absolutely no idea how to install it there, but when I came across these, it just worked!! :-D :-D :-D

---

### Post by Spiljka on 2010-01-03
Hi everybody!

Iam pretty new in this and I just want an explanation about 7. point of tech post



7) Open the terminal in the vuze install folder and execute the script "./azureus".

The install should work just fine, and if I recall correctly it should automatically launch from there.

This whole problem is caused by the version of "swt.jar" in the vuze install files is 32 bit and not 64 bit.

Launching the application from there is a little more tricky. This site taught me a great deal about all of this: [http://forlong.blogage.de/en/entries...us-4-on-Ubuntu](http://forlong.blogage.de/en/entries...us-4-on-Ubuntu)

Personally, I just copied the vuze folder to my home directory and created a launcher to run "azureus" from /<homedir>/vuze"


Or please can u give me some more easier instruction or maybe Iam just DUMB:)

I copied swt.jar in /etc/ folder but what do U mean to run terminal in Vuze folder and execute the script???:confused:
How to do that?

Thanks anyone who help me:guitar:

---

### Post by Shrekster on 2010-01-15
Spiljka:

At 4) --> Extract the install files from the Vuze site to your home directory or another easily accessible folder. **(this is the "Vuze install folder", can be anything as you name it while extracting)**

You should first remove that swt.jar you copied into /etc/.

> what do U mean to run terminal in Vuze folder and execute the script???It means Applications->Accessories->Terminal (GNOME)
and navigating(like using CD command. If you want, find some good HOWTO about CD: [http://is.gd/6iiN4](http://is.gd/6iiN4)) to the "Vuze install folder" location then copy using CP, for example:
```
cp /etc/alternatives/swt.jar ./
```And finally, on the same terminal(same "Vuze install folder" location), execute:
```
./azureus
```Hope that helps!;)

---

### Post by guanucoluis on 2010-02-02
Hi,
I would like to ask a question. I have trouble finding swt.jar file in the / etc / alternative. If you can help them would be very grateful. Greetings to all and thank you for your cooperation. Luis Guanuco


> **techguy615 said:**
> I had some trouble installing Vuze 4.3 on Ubuntu 9.10 64 bit. Apparently the version in repositories is NOT supported by Vuze and when you open the client it tells you that your running an unsupported version. It seemed like I did the install and launched vuze again, but the site still said it was still an unsupported version.

Here is what I had to do correct the issue:

1) Uninstall the version from repository.
2) Download the latest version from the Vuze site.
3) Make sure you have the newest version of Java installed (64bit).
4) Extract the install files from the Vuze site to your home directory or another easily accessible folder.
5) open a terminal and go to the extracted files.
6) Copy the "swt.jar" file from this folder "/etc/alternatives/swt.jar" and replace the one found in the vuze folder. (if you can't fine it just search the file system for "swt.jar" to find it).

NOTE: If you do not perform step #6 you will probably get an error that says something like this when you try to do the install using the instructions:

*Browser check failed with: Cannot load 32*-*bit SWT libraries on 64*-*bit JVM Auto*-*scanning for GRE*/*XULRunner*. [I]You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.

This error above is what almost drove me crazy. 

[I]7) Open the terminal in the vuze install folder and execute the script "./azureus".

The install should work just fine, and if I recall correctly it should automatically launch from there. :)

This whole problem is caused by the version of "swt.jar" in the vuze install files is 32 bit and not 64 bit.

Launching the application from there is a little more tricky. This site taught me a great deal about all of this: [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

Personally, I just copied the vuze folder to my home directory and created a launcher to run "azureus" from /<homedir>/vuze"

 So thanks to this guy for his contribution. I couldn't have worked through it with out the added info.

Cheers! 
:D
[/I][/I]

---

### Post by MissCocoGold on 2010-02-08
Hey there. I'm a bit of a n00b but my husband and I found a bit of a work around for the new Vuze update. I uninstalled the old version of Vuze and although techguy found a solution, I have another. After I extracted the file from the Vuze_Installer.tar.bz2, I moved the new "vuze" folder to my home folder. From there, I opened "azureus" or "./azureus" file and saw that Vuze does indeed work. Then, I right-clicked on "Applications" in my top left corner and selected "Edit Menus". I chose "+ New Item", put "Vuze" in the Name field, for the Command field, I clicked Browse and went to my home folder, opened the extracted Vuze folder and selected the "azureus" file from before. You can even add the Icon. After clicking OK, Vuze should show up in your Applications. Tada! But not done yet. You want to make sure when you download a Torrent file, it opens with Vuze itself. Test it out by finding a Torrent. It should then open a box asking what Firefox should do with it. Click the arrow in the drop down menu and select Other. From there, browse for your extracted Vuze folder and again, choose the "azureus" file that we've been using. Don't forget to check the "Do this automatically for files like this from now on" box so you don't have to reselect Azureus. 

Like I said. I'm a huge FEMALE n00b who found somewhat of a loop hole, mainly for other n00bs who still don't understand Ubuntu yet (like me). Thanks for bearing with me and good luck! Hope this helps. And let me know if there are any problems with doing it this way. Thanks!

---

### Post by Camaguey on 2010-02-24
glad you guys got it working but the (hidden?) 64 bit version is right here:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

---

### Post by snakeman21 on 2010-03-11
> **camaguey said:**
> glad you guys got it working but the (hidden?) 64 bit version is right here:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

thaaaaaank yoooouuuuu!

---

### Post by volatilepyro on 2010-03-29
> **MissCocoGold said:**
> Hey there. I'm a bit of a n00b but my husband and I found a bit of a work around for the new Vuze update. I uninstalled the old version of Vuze and although techguy found a solution, I have another. After I extracted the file from the Vuze_Installer.tar.bz2, I moved the new "vuze" folder to my home folder. From there, I opened "azureus" or "./azureus" file and saw that Vuze does indeed work. Then, I right-clicked on "Applications" in my top left corner and selected "Edit Menus". I chose "+ New Item", put "Vuze" in the Name field, for the Command field, I clicked Browse and went to my home folder, opened the extracted Vuze folder and selected the "azureus" file from before. You can even add the Icon. After clicking OK, Vuze should show up in your Applications. Tada! But not done yet. You want to make sure when you download a Torrent file, it opens with Vuze itself. Test it out by finding a Torrent. It should then open a box asking what Firefox should do with it. Click the arrow in the drop down menu and select Other. From there, browse for your extracted Vuze folder and again, choose the "azureus" file that we've been using. Don't forget to check the "Do this automatically for files like this from now on" box so you don't have to reselect Azureus. 

Like I said. I'm a huge FEMALE n00b who found somewhat of a loop hole, mainly for other n00bs who still don't understand Ubuntu yet (like me). Thanks for bearing with me and good luck! Hope this helps. And let me know if there are any problems with doing it this way. Thanks!

All right one question. How do I get the frog as the icon??? I can't seem to find it when I look for it using the browse option and I can't seem to find anyway to convert it to .svg format.

---

### Post by ddtpoison on 2010-04-06
Found this link on a Vuze forum: [http://sourceforge.net/projects/azureus/files/vuze/vuze-4.3.0.6/Vuze_4.3.0.6_linux-x86_64.tar.bz2/download]("http://sourceforge.net/projects/azureus/files/vuze/vuze-4.3.0.6/Vuze_4.3.0.6_linux-x86_64.tar.bz2/download")

I downloaded it, extracted, moved the vuze folder to my home directory, cd's into the vuze folder and ran './azureus' from command line. works like a bomb so far.

Hope it helps

---

### Post by rifter on 2010-04-22
> **volatilepyro said:**
> All right one question. How do I get the frog as the icon??? I can't seem to find it when I look for it using the browse option and I can't seem to find anyway to convert it to .svg format.

You don't need to convert it.

First off for anyone who finds this later the link to the original howto seems to be dead, but I am sure it is _[color=blue][this one](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)[/color]_.

As for how to add the frog, it depends on whether you put Vuze under opt like the howto says or if you moved it to your home directory.  If you're following the howto they have you edit the menu item file and just put in the locations there.  But you can do the same thing in the gui if you click on the icon for choosing an icon (when editing the properties of the menu item) and then navigate to where the picture lives.  What you are looking for is vuze.png which will be under the vuze directory, wherever you put that (/opt/vuze or ~/vuze or wherever).

---

