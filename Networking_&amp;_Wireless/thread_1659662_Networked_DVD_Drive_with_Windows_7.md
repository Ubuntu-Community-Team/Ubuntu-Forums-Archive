---
title: "Networked DVD Drive with Windows 7"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by jc4orr on 2011-01-04
I recently bought an asus eee pc netbook because i have wanted a linux comp for a while. The only problem with the netbook is the lack of a dvd drive. I have a dvd drive in my desktop (windows 7), and it is shared. I can access it on my laptop (Vista) and family desktop (also windows 7). The only problem is that I cant even see it on my netbook. I have installed samba, and have looked at just about every samba configuration guide I can find and still dont have any luck. 
I have a static ip address on my desktop and on the netbook too. I have "ping"-ed the desktop with success too. Im sure this is possible, but just havent figured it out yet. any help is greatly appreciated.

---

### Post by PatchesTheCaveman on 2011-01-04
Hi jc4orr.  Happy New Year!

To access the file share, go to Places > Network.  You should see your Windows computer name listed in there, and can access the file share from there.

If not, go to Places > Connect to Server.  Switch the [i[Service type[/i] to **Windows share**.  In the *Server* box, enter the IP address of the computer the file share is on.  If you know the share name, type it into *Share*, but it is not strictly necessary.  Nautilus will show all the shares on that computer if you leave it blank.  If you don't have public sharing turned on on the Windows computer, you'll need to enter a valid username on that machine in the *Username* field.  Then click *Connect*.

You will be prompted for a password if necessary.  If you have public sharing turned on and you still get prompted for a username and password, try using **guest** as the username and leave the password blank.  If your username and password won't work, you might need to work around this bug:  [http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials](http://ubuntuforums.org/showthread.php?t=1655434&highlight=windows+live+essentials)

Let us know if you continue to have trouble.

---

### Post by jc4orr on 2011-01-04
I couldnt get the first way to work, but the second way showed me all the shared places on the computer. 
But what I want to do is to make the netbook think that the dvd drive in the desktop is a dvd drive, not a folder. and to be able to burn a disk over the network.

---

### Post by PatchesTheCaveman on 2011-01-04
> But what I want to do is to make the netbook think that the dvd drive in the desktop is a dvd drive, not a folder. and to be able to burn a disk over the network.

That is not possible.  Windows simply doesn't provide any mechanism that would allow that to take place.

---

### Post by jc4orr on 2011-01-04
Well that sucks, leave it up to windows hahaha. but thanks for the help and the quick responses.

---

### Post by jc4orr on 2011-01-05
Thought of this last night, If I am running ubuntu on the desktop could I do what I want to?

---

### Post by PatchesTheCaveman on 2011-01-05
Technically you can:  [http://ramanchennai.wordpress.com/2010/02/14/network-block-device-in-linux/](http://ramanchennai.wordpress.com/2010/02/14/network-block-device-in-linux/)

Would you want to?  Probably not.  DVD/CD burning is a rather precise process.  If for any reason the network couldn't transfer faster than the drive can burn, or if there's any hiccup during the process, your disc will be ruined.  You could work around that by burning at a slower speed than your drive's maximum.  It would require some trial and error, though.

A far better option would be to use DVD/CD burning software on Ubuntu to prepare an image (ISO) and then burn it using the desktop.  If the desktop were running Ubuntu you could do that without ever physically touching the desktop (except to put the disc in, of course).  With Windows you'd need to get on or access the screen remotely to burn the ISO to disc using Windows DVD/CD burning software.  (There is software that can burn ISO files built-in to Windows Vista and 7.)

---

### Post by jc4orr on 2011-01-06
never really thought of burning a dvd as such a delicate process. What you described with the iso is probably what I would do. thanks for all the help and quick responses.

---

