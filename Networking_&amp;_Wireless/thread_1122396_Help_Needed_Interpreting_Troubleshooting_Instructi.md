---
title: "Help Needed Interpreting Troubleshooting Instructions"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Curbside Jimmy on 2009-04-11
I am trying to get wireless and internet working on my laptop
I have been able to determing that the driver is not installed.
Below, in is the solution provided under troubleshooting in the help files.

1.) By the "Windows Driver for your system", does that mean something that applies to the entire system? Or, just the device driver?

2.) What is ndisgtk? Is that a program that needs to be downloaded and run in Ubuntu? Where do I get it?

3.) The actual Wireless adapters end in .dll. 

Ubuntu supports a system known as NDISWrapper. This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System &#9656; Administration &#9656; Synaptic Package Manager).
   3. Open ndisgtk (System &#9656; Administration &#9656; Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.

Thanks

James

---

### Post by t0mppa on 2009-04-11
1) Just the wireless device driver.

2) It's a graphical front end for ndiswrapper, as you'll find out when you open up Synaptic Package Manager (click System at the top panel and then Admininstration). Type ndisgtk in the quick search field and it'll show you the package. Then just click on the empty square in front of the program name and choose "Mark for installation" then it asks if you want to mark a few packets that are required by the packet you selected to work, select 'Mark'. And then it'll install all the necessary packages for you.

3) There should be a .inf file as well, since it's the setup info file. Windows probably just keeps it in a different place than the .dll files on your system. Try doing a search on your disc with the driver name.

---

### Post by Curbside Jimmy on 2009-04-11
(3) "try doing a search on your disk with the driver name."

This is what show up in the device manager

Network Adapters
Atheros AR5007 Wireless Driver 802.11b/g WiFi Adapter
 athr.sys

In doing a search, how do I know the name of the file I am looking for? There are hundreds of files that end in inf.

Thanks

James


> **t0mppa said:**
> 1) Just the wireless device driver.

2) It's a graphical front end for ndiswrapper, as you'll find out when you open up Synaptic Package Manager (click System at the top panel and then Admininstration). Type ndisgtk in the quick search field and it'll show you the package. Then just click on the empty square in front of the program name and choose "Mark for installation" then it asks if you want to mark a few packets that are required by the packet you selected to work, select 'Mark'. And then it'll install all the necessary packages for you.

3) There should be a .inf file as well, since it's the setup info file. Windows probably just keeps it in a different place than the .dll files on your system. Try doing a search on your disc with the driver name.

---

### Post by t0mppa on 2009-04-11
Search for Atheros for instance, since they only provide network adapters.

For instance, I searched my Windows file system for occurances of "*ath*.inf" and found that a "netathr.inf" file could be found from:

[LIST=1]
[*]C:\ACER\Preload\Autorun\DRV\Atheros\Atheros Wireless LAN 3rd Wifi BG\
[*]C:\Windows\inf
[*]C:\Windows\System32\DriverStore\FileRepository\
[/LIST]

---

### Post by Curbside Jimmy on 2009-04-11
I was able to find the driver.

ndisgtk is not on my system under Administration and then Synatic Packane Manager. It does not come up on the search and it is not on the list.

Is there another way I can get it?

Thanks

James


> **t0mppa said:**
> Search for Atheros for instance, since they only provide network adapters.

For instance, I searched my Windows file system for occurances of "*ath*.inf" and found that a "netathr.inf" file could be found from:

[LIST=1]
[*]C:\ACER\Preload\Autorun\DRV\Atheros\Atheros Wireless LAN 3rd Wifi BG\
[*]C:\Windows\inf
[*]C:\Windows\System32\DriverStore\FileRepository\
[/LIST]

---

### Post by t0mppa on 2009-04-11
[http://packages.ubuntu.com/intrepid/ndisgtk]("http://packages.ubuntu.com/intrepid/ndisgtk")

As an added bonus, the page also lists the required packages you need to have installed in order for it to work. Note that this is the download URL for Intrepid (8.10), if you have some other version, remember to get a package suited to it.

---

### Post by Curbside Jimmy on 2009-04-11
The following from the link is what I am guessing I need to download.

Do I need to download all of them?
Once I have them downloaded and decompressed, how do I get them into ubuntu?

I have never used linux before. 

Thanks

James


File Size (in kB) MD5 checksum 
ndisgtk_0.8.4-1.dsc 1.1 kB 781367bcefc7bc0f2ec59d3170552c7a 
ndisgtk_0.8.4.orig.tar.gz 27.4 kB fda997171a9b01cf4cbb515a5551f585 
ndisgtk_0.8.4-1.diff.gz 3.1 kB 173dda4c6877c1ae86c9704b604a8047 







> **t0mppa said:**
> [http://packages.ubuntu.com/intrepid/ndisgtk]("http://packages.ubuntu.com/intrepid/ndisgtk")

As an added bonus, the page also lists the required packages you need to have installed in order for it to work. Note that this is the download URL for Intrepid (8.10), if you have some other version, remember to get a package suited to it.

---

### Post by t0mppa on 2009-04-11
Allright then, to save you quite a bit of clicking and me writing a long instructions post on what to do, try this: Open up a terminal and write into it ```
sudo apt-get update
sudo apt-get install ndisgtk
```

That's if you've wired internet access on your laptop. Otherwise you're going to have to download the packages with another computer/OS and copy them over.

---

### Post by Curbside Jimmy on 2009-04-11
I have Vista running on one partition and obuntu on another.
Wireless is running fine on Vista. This is all on one computer although I have other computers all over the house that are wired also. They are all windows based at the moment.

Is there a way I can go to a terminal on Vista and 
have the program end up on the ubuntu partition in the right place?

The big problem I have is that I can't get oline yet using ubuntu.

Yestereday when I used a ternminal on ubuntu to fine out my driver was not working, that was the first time I had ever used a terminal,
I am just making mouse clicks and following instructions.


Thanks

James



> **t0mppa said:**
> Allright then, to save you quite a bit of clicking and me writing a long instructions post on what to do, try this: Open up a terminal and write into it ```
sudo apt-get update
sudo apt-get install ndisgtk
```

That's if you've wired internet access on your laptop. Otherwise you're going to have to download the packages with another computer/OS and copy them over.

---

### Post by t0mppa on 2009-04-11
Not the easiest of solutions either.Ok, if you still have your LiveCD left, you should be able to use that for installing ndisgtk. Insert the CD in the drive, open up Synaptic, go to Settings / Repositories / Third Party Software / Add CD-ROM and once you get the CD set up on the sources, try searching for the ndisgtk package again.

---

### Post by Curbside Jimmy on 2009-04-11
The live cd that I have is the ubuntu installation cd that I made from an iso image. It is the standard download from the ubunto site. When trying to add it ubuntu didn't recognize the cd and I got the following message.

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."


> **t0mppa said:**
> Not the easiest of solutions either.Ok, if you still have your LiveCD left, you should be able to use that for installing ndisgtk. Insert the CD in the drive, open up Synaptic, go to Settings / Repositories / Third Party Software / Add CD-ROM and once you get the CD set up on the sources, try searching for the ndisgtk package again.

---

### Post by Curbside Jimmy on 2009-04-11
I was able to find the file one the disk after fishing around for it on the CD with Windows Explorer. I copied it and pasted it into a folder I made on the ubuntu partition. Is that of any help.

Thanks

James

> **t0mppa said:**
> Not the easiest of solutions either.Ok, if you still have your LiveCD left, you should be able to use that for installing ndisgtk. Insert the CD in the drive, open up Synaptic, go to Settings / Repositories / Third Party Software / Add CD-ROM and once you get the CD set up on the sources, try searching for the ndisgtk package again.

---

### Post by Curbside Jimmy on 2009-04-11
Somehow I got ndisgtk to show up on the synaptic manager menu.

When I try and install it I get the following message

"please insert the disk labeled: 
Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) 
in drive /cdrom/"

Then the program doesn't recognize the disk in the cd drive.

---

### Post by snickity on 2009-04-11
I am not sure how helpful this suggestion is. But reading this thread I thought you had said there are other computers in your residence and that they are wired? 

Are you trying to configure a laptop for wireless? If so the easiest method would be to make a wired connection temporarily. And then download ndisgtk.

---

### Post by Curbside Jimmy on 2009-04-11
> **t0mppa said:**
> Not the easiest of solutions either.Ok, if you still have your LiveCD left, you should be able to use that for installing ndisgtk. Insert the CD in the drive, open up Synaptic, go to Settings / Repositories / Third Party Software / Add CD-ROM and once you get the CD set up on the sources, try searching for the ndisgtk package again.

I have done exactly what you suggest. ubuntu does not recognize the disk.

I can find the file with windows explorer on the ubuntu disk.
For some reason ubuntu cannot read the disk. This is the same disk that I used to install the program.

I have also managed to get all of the files discussed on a seperate data disk. ubunto does not read that disk either.

By saving the ndisgtk on the Vista partition, I managed to get onto the Synaptic screen. When I click to install it, ubuntu asks for the live disk to be put in the CD drive. It is there but it isn't recognized.
I am thinking that I am missing a driver for the CD rom.

What do you think?

Thanks

James

---

### Post by t0mppa on 2009-04-12
I think snickity has a good point there, if at any way possible, get connected to internet with wired, as that is by far the simplest thing to do. I don't know how to help getting Ubuntu to read the CD and downloading the packages with another computer/OS can become quite a mess as well.

---

### Post by Curbside Jimmy on 2009-04-12
> **snickity said:**
> I am not sure how helpful this suggestion is. But reading this thread I thought you had said there are other computers in your residence and that they are wired? 

Are you trying to configure a laptop for wireless? If so the easiest method would be to make a wired connection temporarily. And then download ndisgtk.

I already have ndisgtk downloaded. It is in a file in ubuntu. ndisgtk shows up in the synoptic screen as being addable. 

However, ubuntu will not add ndisgtk or any other program without going to the installation disk.

The problem now is that ubuntu is not recognizing disks in the cdrom/dvd drive. 

The problem changed a number of messages back from not having ndisgtk to not being able use the CDrom drive to assist in installation. 

I am having the same problem adding any of the programs on the list.

Thanks


James

---

### Post by t0mppa on 2009-04-12
Yes, I know you do. But if you didn't download the other packages yet, it would be easiest to do so with internet access through a wired connection. If you downloaded all 5 .deb files though, then it's just simply a matter of double clicking them in the right order. Don't worry they won't let you do it in the wrong order, so it's a trial and error period ahead.

To get Synaptic back on track, you should disable the CD from the sources, since it's not cooperating with your system.

---

### Post by Curbside Jimmy on 2009-04-12
I appreciatre everyone's help. I am going to have to give up until next weekend.  

Thanks

James

---

### Post by matikk on 2010-03-05
Why not visit [www.virtualsaver.co.uk](www.virtualsaver.co.uk)

---

