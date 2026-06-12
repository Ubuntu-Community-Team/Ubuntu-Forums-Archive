---
title: "Windows wireless drivers crashes?"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by 805g on 2008-12-31
I am a NEWBBBBB to Ubuntu.  I am very capable of troubleshooting windows and felt i should learn some linux.

I installed the wireless driver for my linksys wusb11 ver. 2.6 driver and it accepted it as a valid driver.  I have not been able to see any wireless networks.  And if i attempt to open the 'windows wireless driver' thing it crashes  and goes dark.

Any help?  THANKS ALL!

---

### Post by 805g on 2008-12-31
I use 8.10

---

### Post by MattBD on 2008-12-31
Just to clarify - are you using Ndiswrapper to get the Windows driver to work with Ubuntu?

---

### Post by 805g on 2008-12-31
i believe that installed ndiswrapper and ndisgtk and then i was able to go system->Admin->windows wirelesss drivers.  but now that crashes and i have no wireless connections....thank you for the quick reply!

---

### Post by MattBD on 2008-12-31
OK then. I'm assuming here that your wireless device wasn't detected at all, as if it was detected but didn't work well then that involves an extra step.
You need to get the driver files (which are often contained within a Windows .exe file) and extract them to get the .sys and .inf files.
The best way to do this is with unzip from the terminal, like this:
```
unzip drivers.exe
```
This should work OK, so let me know when you have done this. You'll have to replace drivers.exe with whatever your file is called.

---

### Post by MattBD on 2008-12-31
If you're having problems with ndisgtk, I'd just use ndiswrapper from the command line.
What you need to do is as follows:
1) Save the extracted .sys and .inf files from the Windows drivers somewhere in your Ubuntu install. There might also be one or more .bin files, which you will also need if they are present. I would set up a new folder in /opt, as that's traditionally where new software is installed in Linux, call it something easy to remember like drivers, and put the driver in that folder. You'll need root access to do this, so start Nautilus from the terminal as root like this:
```
gksudo nautilus
```

2) Change into the directory you have the drivers in from the command line using cd, like this:
```
cd /opt/drivers
```

3) To actually install the driver, type the following:
```
sudo ndiswrapper -i filename.inf
```
Replace filename.inf with the filename of your driver.

4) Now to add ndiswrapper to the list of modules Ubuntu automatically runs, enter this:
```
sudo ndiswrapper -m
```
Followed by this:
```
sudo nano /etc/modules
```
This will open /etc/modules in the nano text editor (hopefully you shouldn't have a problem using this, once you want to leave it it's Ctrl and X, and press Y when it asks if you want to save). If ndiswrapper isn't showing already, you'll need to add it on a new line at the bottom.

Once all this is done, if you exit nano and reboot your system, the Windows drivers should work fine (hopefully!)

---

### Post by 805g on 2008-12-31
thank you guys for your help.

I can not copy anything into /opt

it says i don't have permissions.  And i don't know how to relinquish the permissions in ubuntu...

again thanks for the help!

---

### Post by MattBD on 2009-01-01
You should be able to do this if you run Nautilus using gksudo. Or you can do it from the command line:
```
sudo cp -r driverfolder /opt
```
Basically, to be able to write to a folder outside your /home directory, you need to use sudo to give you root powers - this is the equivalent of administrative access in Windows.

---

### Post by 805g on 2009-01-01
Matt I'm sorry but i'm not sure what I need to do here.  

Should i use the terminal to enter

sudo cp -r driverfolder /opt

what does this do?  

and is there a way to just sign in as the root user?

THANK YOU SO MUCH
and happy new year!!!!!!

---

### Post by MattBD on 2009-01-01
Yes, you'd need to use the terminal for this.

cp is copy - for instance you could create a text folder called example.txt, then enter the following to create a copy of it:
```
cp example.txt copy.txt
```
That would create a copy of example.txt called copy.txt. The -r means it's recursive, so if you use it on a folder anything inside that folder will be copied as well.

The /opt is the destination folder.

If you prefer to use the GUI, you can start Nautilus (the file manager) with root powers as follows:
```
gksudo nautilus &
```
Gksudo is just a graphical version of sudo.

As for the root user, it is possible to activate the root account in Ubuntu but I don't really recommend it - sudo is generally safer to use.

What you can do is either run whatever graphical app you want to have root access using gksudo as above, or on the terminal you can enter the following:
```
sudo -i
```
This will mean that while that session is open, you will automatically be root.

Stick with it, getting ndiswrapper working was a real stumbling block for me too when I first got started using Ubuntu:). Now my wireless card has worked out of the box for the last three versions.

---

### Post by 805g on 2009-01-01
OK.  So i was able to copy the drivers into opt using the sudo command you gave me.

I then ran nautilus.  It stated that i should enable user sharing...?

I then cd /opt/drivers
then 
sudo ndiswrapper -i driver.inf

It stated that the driver was already installed.

Then i did 
sudo ndiswrapper -m 

and it said some type of error and repeated it five times

then i entered
sudo nano /etc/modules 

and it opened some special thing... but i have no idea how to navigate it or what it is for....

matt thank you for putting up with me

---

### Post by MattBD on 2009-01-01
Can you run this and post the result here?
```
ndiswrapper -l
```

---

### Post by 805g on 2009-01-01
when i did 

ndiswrapper -l (the letter L)  it listed nothing

When i did

ndiswrapper -1 (the number 1) it listed the command options for ndiswrapper

---

### Post by MattBD on 2009-01-01
Hmmm - that seems to mean that the driver isn't supported. If you check out [this link]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing Windows driver using command line"), that seems to suggest that the driver may not work with ndiswrapper (not all of them do, unfortunately). You may want to have a look through there to see what can be done.

If you have a fairly new wireless device it's quite common for them not to work in Ubuntu, whereas older devices are well supported, so it may be that a future version will support it out of the box. Also, some vendors (in particular Broadcom) are notorious for producing cards that are a pain to get working in Linux.

If you want to learn to use Linux and don't have plans to use it as your main system, you could try running Ubuntu in [Virtualbox]("http://www.virtualbox.org/") on a Windows system. That would give you the chance to get Ubuntu working because VirtualBox is set up to make the guest operating system think it's connected via Ethernet even if the computer is using a wireless connection, so you wouldn't have that issue. Not ideal, but if all else fails...

Sorry I couldn't be more help!

---

### Post by 805g on 2009-01-03
ok, so i am going to look into using virtual box for a while.

is there an easy way to delete teh partitions on my drive.  I partitioned my drive 30 gigs for windows and the rest of the 220 gigs for ubuntu. can i easily delete that and have the space available from teh windows side?

THANKS!

---

### Post by MattBD on 2009-01-03
There are tools available that can resize a partition. If you have a copy of Knoppix, you could use that as it includes QtParted, which is very good, or download a free trial of [Partition Magic for Windows]("http://www.soft32.com/download_151.html"). Unfortunately I don't think Ubuntu comes with a nice easy graphical partitioning tool on the CD.

---

