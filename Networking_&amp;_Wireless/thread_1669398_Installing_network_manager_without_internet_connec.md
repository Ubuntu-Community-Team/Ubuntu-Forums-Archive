---
title: "Installing network manager without internet connection!"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by dannyspanish on 2011-01-17
I've read a lot on the internet about various ways of doing this but i've been unsuccessful each time.

Basically what i've done is accidently un-installed network-manager because I was having trouble staying connected on my WPA network. 

The easiest way of reinstalling it I know of is using the CD but I don't have a CD ROM drive and the pen drive I used to install it I no longer have.

I tried using a program called Keryx but you need python installed and from some reason this doesn't come with ubuntu 10.10. I've also downloaded the .deb packages but I still need to download 200kb which is a killer. I've also downloaded it from here too [http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.8/]("http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.8/")

but the install file makes no sense to me as i'm not a massive linux user. 

If someone could please help me find a way of installing network-manager again I would really appreciate it. 
Oh I would be able to connect to the internet if I could get ubuntu to select my ethernet as my default connection.


One last thing reinstalling isn't really an option as i've already put a lot of time into setting up this computer.

By the way i'm using a dell optiplex GL 60 intel processor.

Thanks for any help.

---

### Post by khamil8686 on 2011-01-17
i uninstalled network manager by accident before too, i just reinstalled though. i figured you can download a .deb file from somewhere and load it onto usb and googled it and found
[http://packages.ubuntu.com/maverick/i386/network-manager-pptp/download](http://packages.ubuntu.com/maverick/i386/network-manager-pptp/download)
that is the link to download a .deb file for ubuntu 10.10 maverick meerkat (change the url depending on which version you have), if you only uninstalled the network manager package and didnt uninstall others by accident that should just replace that file, just open the usb stick and double click the file to install. course you have to have a connection to the internet somewhere, like a friend's or something, that link you posted i believe is the source code for the network manager file that you would have to compile, .deb files are automatic install files
you can also install ubuntu to a usb stick if you dont have a friend's machine you can burn a ubuntu live cd to just goto this link
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
and scroll to the bottom for how to install to a usb stick manually, that page might have some other information that will help you out as well, hope this helps!

---

### Post by dannyspanish on 2011-01-18
Thanks for getting back in touch. It said that I already had this installed however the addon "KDE network management infrastructure (PPTP Plugin)" is not installed. Is this what I need?

I think my best bet is just to grab a memory stick from work (if I remember) and create a usb boot disk. 

Such a pain though, I don't think the user should be able to remove this so easily.

---

### Post by khamil8686 on 2011-01-18
yes if thats what it says is missing id try to find download that deb from the earlier link and install it, grabbing a memory stick from work does sound to be the easiest option though, because if you accidentally uninstalled the whole network system like i did once somehow... :) then theres no telling which other necessary ones are missing as well, you might install that one and then it would pop up and say you need x and x to install before you install the PPTP plugin! yes it can be a pain for the user to accidentally remove a file but thats also part of the beauty of linux, freedom to do what you want with your operating system how you want to do it (as long as you allow the same rights to others) and the system is getting a lot more user friendly, every release im impressed by the changes they make to make it more user friendly, its not there yet but its taking strides :) anyways, just post back if you have some more trouble!

---

### Post by grahammechanical on 2011-01-18
Did you really uninstall or did you only remove it from the top panel? To uninstall it you would have to do it through synaptic or the software centre. I would say that it is possible to uninstall through ignorance but not accidentally.

If it is still installed then make sure that network manager is in the list of Startup Applications. System>Preferences>Startup Applications.

Also you may need to add the Notification Area to the top panel It may be that you removed that and not network manager. Right click the top panel. Select Add to Panel and select Notification Area.

Regards.

---

### Post by dannyspanish on 2011-01-19
I thought that was it then grahammechanical, but when I right click on the top notification bar and select add a new item, I search for network-manager but it doesn't find it, although it is under the start up applications. 

Just wondered how I can go about installing it through a live usb pen drive?

Thanks.

---

### Post by khamil8686 on 2011-01-19
boot into ubuntu and then open up system>administration>sources :) (check [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) for documentation on adding sources) and then add the usb stick to your repository directory 
(possibly 'deb file://*absolute path to mounted usb stick*'
'deb file:///absolute/path/to/mounted/stick' is an example of the absolute path minus the quotes), then refresh the package list and search for network-manager and it should show up for installation. the file:// part of the repo im not 100% sure of, i did some googling and came across a few examples where people put file:// into their sources file for a local repo

also im not sure if a bootable ubuntu memory stick has all the debs uncompressed on the memory stick or not, you might give a try to mounting the usb stick and browsing the stick for a network-manager deb so you could just double click the file to install it

just post back if you run into more troubles!

---

### Post by dannyspanish on 2011-01-27
all sorted now thanks. In the end I managed to get wicd to discover my ethernet connection and I just downloaded it using apt-get install. I then had a few troubles getting it to discover my wireless usb adapter but i found a helpful post on how to go about installing the device (I was gonna link this post but I cannot find it AT ALL) then it was disconnecting me after 30 seconds of been connected, restarting my router sorted that out.

So finally after 3 weeks hard work I have a working music server that runs banshee music player and is controllable by my android phone :D just about...

Couple of things to iron out, it says it's connected to the network and it is however when i click connect to server on my app it says unreachable host and the only solution at the moment is to restart my phone, hopefully I just have to restart my wireless connection. playback can be a bit jumpy now and then but it's a fairly old computer so hopefully a ram upgrade will sort that out.

Lastly, is they anyway I can make ubuntu boot faster? like I don't need a gui really, I just need banshee music player and wireless to work. 

Thanks a lot for your all your help though guys.

---

### Post by khamil8686 on 2011-01-27
glad you got it figured out! the music server controlled by your android phone sounds pretty cool, i have a droid 2 and love it so far :) anyways could you mark the thread solved so if anyone else has a similar problem and they search the forums they can identify which threads might help them easier? and to make ubuntu boot faster i found something the other day about that, theres many tricks people have used to get it to boot faster just do some googling :) but i found this site
[http://ubuntuforums.org/showthread.php?t=987244]("http://ubuntuforums.org/showthread.php?t=987244")
about changing the concurrency value to shell in /etc/init.d/rc so that processes could run simultaneously in different processor cores is what i gathered about it, everyone gets different mileage with this but it saved me about 25 seconds in boot time, others have gotten it to boot 2x as fast as normal, the bootchart program is a good program to use for seeing how long your boot time is and how much you gain from this change, so far i havent had any problems by changing the value either :)

---

