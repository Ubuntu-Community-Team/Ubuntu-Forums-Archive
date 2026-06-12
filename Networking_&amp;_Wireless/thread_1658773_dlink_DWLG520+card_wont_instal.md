---
title: "dlink DWLG520+card wont instal"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by Owndu on 2011-01-03
I have just installed unbuntu 10.10 on an old AMD seperon 3000+ pc and can run it ok on a wired network but cant get wireless to run at all 
i have downloaded ndisgtk and the other stuff which it suggested in the synaptic manager
and applied them
when i go to wireless drivers in admin it allowed me to select an xp driver from cdrom and instaled new driver netrt61g but theres a note underneath the driver, "hardware present : NO" i restarted but it still wont pick it up
i have to say im a complete noob to ubuntu and linux and ive spent lots of time to get this far though have been using open office for a while on windows
if any one can help i be very grateful:confused:
oh i also down loaded drivers for the card from Dlink website but could not find an INF. file at all in the files

---

### Post by chili555 on 2011-01-03
This suggests that the correct driver is gplus.inf. Did you try that?

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G520%2B](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=D-Link_DWL-G520%2B)

---

### Post by Owndu on 2011-01-03
Thanks for the Reply

No I have not tried this, I have downloaded it, But i am again at a loss because this file like the one I got from D link contains no INF.file so I dont Know how to use it to get it installed?

---

### Post by chili555 on 2011-01-03
I could attach it, but the searchers will never learn. You need a package called unshield. If you can temporarily get a wired ethernet connection, do:```
sudo apt-get install unshield
```If you must transfer files on a USB key or similar, you can download this: [http://packages.ubuntu.com/maverick/unshield](http://packages.ubuntu.com/maverick/unshield)

Be sure to select your version if it's not Maverick (10.10) and either the 32- or 64-bit version. Install with:```
sudo dpkg -i unshield*
```You can right-click the downloaded driver file and then do:```
cd Downloads/dwl-g520+_rev_bx_driver_v3-00
unshield x data1.cab
```Substitute the location your downloaded driver file went to, if not Downloads. Many folders will be extracted; one is InfMe2KXP. It contains GPLUS.INF. Install it with ndiswrapper and enjoy.

---

### Post by Owndu on 2011-01-09
Hi I installed unshield using the synaptic manager and have the zipp file for the drivers in downloads, are you suggesting I use terminal to carry out the commands you suggest? where does unshield go when its installed I cant see it in programs!, can i open unshield and then use it on the desktop?

---

### Post by chili555 on 2011-01-09
> are you suggesting I use terminal to carry out the commands you suggest?Yes, exactly. unshield is a terminal only program.

---

### Post by Owndu on 2011-01-10
Ok i have file "DWL-G520+_Driver_v3.10b19 in my downloads directory

when I type your last step ( im not sure what you mean about the right clicking bit) it tells me there is no such file or directory!??

I changed the path to /home/ian/downloads but still no joy any suggestions please

---

### Post by chili555 on 2011-01-10
> Ok i have file "DWL-G520+_Driver_v3.10b19 in my downloads directory
Have you unzipped it? You can do so easily by opening Places > Home Folder > Downloads And select the DWL zip file. Right-click it and select 'Extract Here.' Now your commands should work perfectly.

---

### Post by Owndu on 2011-01-10
yea i have, Look im sorry im being such a pain the file i mention is the unzipped file perhaps im being a complete noob but i thought this ubuntu was supposed to be the " works out of the box" seems real hard to get this thing working!!!

---

### Post by chili555 on 2011-01-10
> i thought this ubuntu was supposed to be the " works out of the box"Who said that? It isn't "works out of the box" any more than Windows or Mac with any and every hardware ever invented. It's also famous for not being "works out of the box" for equipment that is introduced *after* the latest installation. A large number of devices from webcams, printers, etc., and even wireless cards do work perfectly well out of the box. Almost no-one comes on this forum to post that everything works perfectly. 

I am not sure how to explain it more clearly. If you have the unzipped folder in your downloads folder, open a terminal and do:```
cd Downloads/DWL-G520+_Driver_v3.10b19
unshield x data1.cab
```Many folders will be extracted; one is InfMe2KXP. It contains GPLUS.INF. 

Now open Windows Wireless Drivers and point it at Downloads/DWL-G520+_Driver_v3.10b19/InfMe2KXP/GPLUS.INF.

You are not a pain; post back if I can help. I'm going nowhere; I'm snowed in!

---

### Post by Owndu on 2011-01-11
OK just thought it might be easy for you to see what happens so have reconnected the ubuntu pc via a wired link this is my latest effort using terminal to unshield the driver, this was copied directly from terminal


ian@ian-System-Product-Name:~$ cd Downloads/DWL-G520+_Driver_v3.10b19[COLOR=Blue] [/COLOR]
ian@ian-System-Product-Name:~/Downloads/DWL-G520+_Driver_v3.10b19$ unshield x datal.cab
Failed to open datal.cab as an InstallShield Cabinet File
ian@ian-System-Product-Name:~/Downloads/DWL-G520+_Driver_v3.10b19$

[COLOR=Blue]( I hit the Enter Key which previously I  hadnt been doing after the first [/COLOR]cd Downloads/DWL-G520+_Driver_v3.10b19[COLOR=Blue] [/COLOR][COLOR=Blue] so therefore that was why i was having problems with  it finding the file and then again after typing [/COLOR]unshield x datal.cab[COLOR=Blue])[/COLOR]

---

### Post by chili555 on 2011-01-11
> unshield x datal.cabIt is not datal.cab with an L; it is data[COLOR="Red"]1[/COLOR].cab with a one.

---

