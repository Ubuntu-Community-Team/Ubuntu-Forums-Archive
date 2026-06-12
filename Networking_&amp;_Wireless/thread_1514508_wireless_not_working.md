---
title: "wireless not working"
date: 2010-06-21
forum: Networking &amp; Wireless
---

### Post by newtmontrose on 2010-06-21
Can anyone help me !
I've installed ubuntu 10.04 on my desktop at first i thought everything was O K but when i tried to install a usb wireless adapter it would not install from the CD.
I bought this usb stick after asking if it would work with ubuntu 10.04 and was told it would.
Does anyone out there know of a wireless usb or a pci card that will work straight out of the box.
If anyone can give me a link that would be great.
Thanks a million

---

### Post by carlexpc on 2010-06-21
please tell us what chipset your wireless USB is using. follow the steps below:

1. open a terminal. 
2. type the command *lsusb *
3. post the result of the command on this thread.

---

### Post by wojox on 2010-06-21
You will probably need this [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by newtmontrose on 2010-06-23
> **carlexpc said:**
> please tell us what chipset your wireless USB is using. follow the steps below:

1. open a terminal. 
2. type the command *lsusb *
3. post the result of the command on this thread.
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07ab:fcdf Freecom Technologies 
Bus 001 Device 003: ID 046d:08c9 Logitech, Inc. QuickCam Ultra Vision
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Hope this helps

If i uninstall ubuntu 10.04 and install a wireless pci card then reinstall ubuntu 10.04 will the installation then find the pci card and install the drivers from the new installation.
If this would work is there a pci card that would be the best to get ?
I'm looking for an easy way to get wireless on my desktop but as i'm new to ubuntu were wireless is concerned i think i'm needing an easy way to get my wireless going, So if i would be better putting a pci card in my desktop i would do that instead as a lot of the tech talking about the terminal is just going over my head maybe it's my age but i would still like to have a go with the wireless instead of being wired.

Thanks for your help.

---

### Post by MartinHansell on 2010-06-23
Hi,

Please don't be offended when I say that, irrespective of operating system or age, if you want real help your question doesn't really reflect that.  Most people will just ignore your request simply because your question is not a good one.  "...I bought (a wireless) usb stick" is like saying "there's a lamp post on the street corner where I am standing now" - not enough information to tell you which way to turn next.  Furthermore, if you adopt this approach and just "install a pci card" you might find yourself back where you started only lighter of pocket.  You need to be more specific to get a useful answer.

To find out if your usb is compatible with Ubuntu you need to get some basic information, such as
[LIST]
[*]name of the manufacturer
[*]model/number of your wireless usb
[/LIST]
This information should be on the box, or the receipt, or phone your supplier who told you it was compatible with Linux and get him to put his money where his mouth is.

When you have found this information out, post it here, and someone may tell how to find out if your wireless really is usable or not.

On the subject of the command line... if you have enough aptitude to open a box and install a pci card, you are selling yourself short to think you cannot handle the learning curve involved with Ubuntu.  I know it's tough to start with, but if you plan to enjoy the full benefits of free software (which I think is an amazing offering to the world) you do need to be willing to make a little investment effort of your own - it's worth it!

Hope that helps.

---

### Post by newtmontrose on 2010-06-23
Thanks for reply.
The reason i'm getting frustrated is because all i can find on the box is realtek usb ver 1.1-rtl 
it says op systems windows 2000 xp vista windows 7 and linux
When i put the disc in the drive i get this message ( an error occurred while loading the archive ) and the box below has this message (Archive:  /media/cdrom0/Setup.exe
[/media/cdrom0/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Setup.exe or
          /media/cdrom0/Setup.exe.zip, and cannot find /media/cdrom0/Setup.exe.ZIP, period.)
 
I bought it from ebay as it was the only place i could find a wireless usb that said it worked with linux.
I looked on ebuyer amazon novotech and could not find anything that said ubuntu compatible. 
It cost me £14 not a lot of money but now think i would have been better off with a pci card.
My thinking was that like my windows 7 computer that i put together that the drivers would be on the cd or that they would be found on line.
I went to the realtek site but was at a loss as there are so many and with nothing on the box it could have been any! 
Thanks again

---

### Post by MartinHansell on 2010-06-24
Hi,

Thanks for the info... I have done some digging.  This info is quite basic, coz I'm not sure how much experience you have, so forgive me if it's too low-level.

First things first - a .exe file (setup.exe) is a windows only file and cannot run on Linux.  [This is not totally true - with [Wine]("http://www.winehq.org/") you can use some Windows programmes, but you won't be able to set up a wireless device with this, I don't think anyway.  And Wine is a bit flaky so I end up throwing in the towel most of the time.]

Next - what are you using as your wireless router?  Can you provide details of this?

Next - assuming your wireless router is set up ok.....  I did some searching on the wireless usb you are using, and it does seem as if there are [one or two bugs]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/336372") with it, but [this post shows]("http://rtl-wifi.sourceforge.net/wiki/Installing") that the required driver has been a part of Ubuntu main distro for a while, and it should therefore just work.  So try this...

[LIST]
[*]connect yourself to the Internet with a wired connection
[*]close everything on your desktop (except Ubuntu itself :))
[*]plug in your wireless usb
[*]check to see if it's recognized - you will see it attempting to connect to your internet, and it might even lead you to the next steps; if not....
[*]left-click on the internet icon in the top bar of your screen - it's a little radar which will have an exclamation mark on it until the usb is connected to the router
[*]in the drop-down list can you see your own wireless router as an option to connect to?
[*]if yes, select it - you will be asked for the password to your router
[*]that should be enough to get you going
[/LIST]

if no...  
[LIST]
[*]open a (dreaded) terminal - on the main menu look for "Applications/Accessories/Terminal
[*]type "sudo apt-get update" - enter the root password when prompted
[*]when that's finished, type "sudo apt-get upgrade"
[*]now check your wireless to see if it's recognized (by doing the same steps above)
[/LIST]

If these steps don't work, record the details including error messages, and post them here... I am not an expert, and I might soon run out of ideas, but someone else may be able to help.

---

### Post by pxr on 2010-06-24
I've recently been messing with a 2.5G USB modem, so I might be able to help you out on this.

Usually Ubuntu recognises the USB for what it is and loads the necessary kernel module...referred to in Windoze as a driver.

For some reason these USB thingamajigs want to present themselves to the system as a cdrom - probably a work around for Windoze.

Anyway, first trick to try....

If once you install the USB you get an icon on your desktop, right click on it and choose 'Eject'. This gets rid of it as a 'cdrom' and allows the system to see it as a wireless interface.

Give it a minute or 2 and see if it has popped up as an option in Network Manager if so you're good to go, just choose it to connect.


If that fails - after you've done the right click - Eject thing - - open a terminal & type

tail -n 20 /var/log/messages  >>message.txt

That should put a file named message.txt in your home directory, then post the contents of the file, and we can see if it has been recognised or not.

---

