---
title: "Printing Windows XP -&gt; Ubuntu?"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by sethmahoney on 2006-06-27
Can anyone point me to a good guide (that works for Dapper - I'm a little leery about following the one on the Ubuntu wiki that is for Breezy) to setting up a printer connected to my Ubuntu computer so that Windows XP computers can print to it?

---

### Post by dannythomas13 on 2006-06-28
hi, i am a newbie and this is my first post. first let me apolagize for jumping on this post but i too need the same help.
i am working with ubuntu dapper, now this pc of mine is connected to my printer , which is an Epson R300, via a usb cable. now my home computer connects to the internet via my netgear router.
now my brother has a wireless laptop with windows xp installed on it and i would like for him to be able to use my printer wirelessly (which i managed to set up after a lot of fiddling when i too used xp). now im guessing i need to set up a network on my ubuntu pc that my brother can find wirelessly. but i dont know how to go about it as i am a newbe to ubuntu and dont really know much about networking. also note that my pc isnt wireless it just hooks straight into the router.
can anyone plz help
thanks, and i hope to hear from some of you soon
Daniel =)

---

### Post by skirkpatrick on 2006-06-28
This is very easy to do with XP computers.  First, the file you need to change on Ubuntu might be located in two different places.  Use the following command to change Cups to listen for other connections:
     **sudo gedit /etc/cups/cupsd.conf**

Search for "631" so that you'll have this new line in the area of the other listen commands.  On a new line, add **Port 631**.  This will cause Cups to listen to all print requests on port 631.  Now you need to restart cups.
     **sudo /etc/init.d/cupsys restart**

You will have to install your XP printer driver manually, not by allowing it to download and install from the server like Windows normally wants to do.  When you go to install your printer on Windows, tell it it's a network printer and that you have a URI (or an IPP printer, I can't quite remember).  Then, if your Ubuntu machine is called PapaBear and your printer on it is called Deskjet-5550, for example, the URI you want to use is **[http://PapaBear:631/printers/Deskjet-5550](http://PapaBear:631/printers/Deskjet-5550)**.  Print a test page and you should be good to go.

---

### Post by dannythomas13 on 2006-06-28
thanks for the reply but it doesnt seem to work when i try to locate the printer from the xp machine, does anyone else know how i can set up a network?
thanks

---

### Post by skirkpatrick on 2006-06-28
You can't browse for the Ubuntu printer from XP unless you share it through Samba.  That's why I said you had to tell XP it has a URI and you have to type it in.

You can setup your Ubuntu to share through Samba (mine shares through both) but I found that the print response with XP was faster talking directly to Cups where Win98 machines had better response through Samba.

---

### Post by dannythomas13 on 2006-06-29
ok, i will try and find a tutorial on samba but i did try the cups method as you said but the xp machine could not find it. now im not sure if this is because both are connected througha router and not directly...i'm not sure

---

### Post by skirkpatrick on 2006-06-30
If the two machines can ping each other, it won't be a problem.

---

### Post by rlgoddard on 2006-07-03
Hi,

I am having the same problem myself.  I tried the wiki that was suggested, but that does not work.  Windows cannot find the printer! :(  My two machines can connect to each other just fine and dandy.  Weird!

[quote=skirkpatrick]If the two machines can ping each other, it won't be a problem.[/quote]

---

### Post by rlgoddard on 2006-07-03
Hi again,

I went ahead and installed samba.  I can now see the printer that is connectd to my Xubuntu box in the Windows XP box.  However, Windows wants to download a printer driver from Xubuntu.  When I click OK, Windows complains of not being able to find the printer driver.  Also, using [http://joey:631/printers/DeskJet-5650](http://joey:631/printers/DeskJet-5650) does not work.  Neither does [http://192.168.1.100:631/printers/DeskJet-5650](http://192.168.1.100:631/printers/DeskJet-5650).  What else do I need to do?

Take care,
Russ

---

### Post by skirkpatrick on 2006-07-03
[QUOTE=rlgoddard]Hi again,

I went ahead and installed samba.  I can now see the printer that is connectd to my Xubuntu box in the Windows XP box.  However, Windows wants to download a printer driver from Xubuntu.  When I click OK, Windows complains of not being able to find the printer driver.  Also, using [http://joey:631/printers/DeskJet-5650](http://joey:631/printers/DeskJet-5650) does not work.  Neither does [http://192.168.1.100:631/printers/DeskJet-5650](http://192.168.1.100:631/printers/DeskJet-5650).  What else do I need to do?

Take care,
Russ[/QUOTE]

You need to install the drive on the XP box using either the CD that came with the printer or download and install the driver from the manufacturer.

The URI's only work if you have Cups setup to listen instead of going through Samba.  I am at work right now so XP won't let me pull up the properties of the shared printer since I'm not connected to it but I will check tonight and post here.

---

### Post by skirkpatrick on 2006-07-04
If you install the driver on your XP box and you shared it using Samba, you should be able to just browse for it on XP.

---

### Post by rlgoddard on 2006-07-05
[quote=skirkpatrick]If you install the driver on your XP box and you shared it using Samba, you should be able to just browse for it on XP.[/quote]
 
Hi,
 
That's what I ended up doing: installing Samba in Ubuntu to enable printer sharing. I also modified cupsd.conf and commented out the "include" lines (the original cupsd.conf was trying to include two conf files that conflicted with what was in the main cupsd.conf file). I took the code from the Printer Networking wiki and pasted it in the original cupsd.conf and also deleted the "include browser-conf" file that was in the wiki. It works great now!
 
A side effect of this successful configuration is that I am now able to run hp-toolbox in Ubuntu. Previously, I couldn't do that. I think because I switched from a usb: backend to an hp: backend.
 
Thanks for your help! I appreciate it!
 
Take care,
Russ

---

### Post by Madmat on 2006-07-05
Please excuse me for seeming a little dense on the subjuect, but I haven't been able to get either Windows box to see my Dapper box.  
I am running Kubuntu on my third box and don't have any problems seeing either XP or 98se.  I can move files to and from them while I am working on Dapper.
I set up my network manually on all three computers so I could dial out from each and not use a router.
Is there something I need to do to get the Windows boxes to see Dapper?
Thank you.
Matt

---

### Post by skirkpatrick on 2006-07-05
rlgoddard,

Yeah, I had the same problem but I'd swear I was using the USB backend in Breezy.


Madmat,

Dapper should be able to see computers on a Windows network by default but I'm not sure if it will show itself to others.  Go to System->Help->System Documentation.  Then select Ubuntu Server Guide and go to Windows Networking.  You might get a little confused with setting up the config file.  If so, either search the forums here or ask away.

---

### Post by Regenerate on 2006-07-07
Hi all,

Is the reverse also possible (eg. Printing from Ubuntu to a printer connected to Windows XP)? The problem is I cannot find a linux driver for the printer so the printer needs to be connected to the XP machine. Being able to print from the ubuntu machine would be nice though :). TIA!

---

### Post by ktneely on 2006-07-07
> **skirkpatrick said:**
> The URI's only work if you have Cups setup to listen instead of going through Samba.  

Does this mean that if you want to use Samba + Cups, that you need to disable or comment out the 'Listen' parameters for Cups in either cupsd.conf or ports.conf?

My current problem is that I can print locally, can print directly from XP using the URI (server:631), and can see the printer(s) via windows network browsing.  However, when I print to the printers via Samba, the job spools to the server, but the job fails with 
"Unable to print file to hp_usb_DESKJET_810C - client-error-not-possible" in the samba log for that specific client.

It's really confusing me   :confused:


Regenerate:  Yes, you need to use smbclient to do the printing.  This might help you:  
[http://www.ubuntuforums.org/archive/index.php/t-32190.html](http://www.ubuntuforums.org/archive/index.php/t-32190.html)

---

### Post by skirkpatrick on 2006-07-08
Regenerate,
If you don't have a Linux driver to use the printer locally, it won't work over the network because you still have to have a Linux driver.  Unless you can get an XP driver that will make it look like a generic Postscript printer or something.


ktneely,
If you are using Samba to print, it doesn't matter if the Listen commands are commented out or not.  If you can print using the URI, why do you want to use Samba?  I have found in my network that XP prints faster using the URI but Win98 prints faster using Samba.

---

### Post by ktneely on 2006-07-08
> **skirkpatrick said:**
> 
commands are commented out or not.  If you can print using the URI, why do you want to use Samba?  I have found in my network that XP 

Well, I ought to be able to do both, I think.  On the one hand, it just drives me nuts that I cannot get it to work, even if I would never use it afterwards, but mostly, it is for ease of use for the other clients.  

Failing the standard Samba browse-to-printer thing, is there a way to have the printer drivers installed for the Windows clients, like you can with the print$ share?  Does the print$ share work even with the URI?

---

### Post by vkohli on 2006-07-08
Hello:

I have had similar problems trying to print from XP to a printer connected to my Ubuntu machine. To make matters worse I am running vmware and have installed XP as a virtual machine. In addition I have a laptop running XP as well connected to my home network. 

To make a long story short, I have managed to get XP to print (from both the virtual machine and from the laptop) to my printer attached to my Ubuntu machine. Here is what I did:

Similar to other posts you need to modify your cupsd.conf file. Edit your cupsd.conf file and make sure that the line of code is added:

Include /etc/cups/cups.d/ports.conf and Listen localhost:631 is commented out.

Now edit your ports.conf file (in the cups.d directory) and comment out the line of code saying:

Listen localhost:631
(You should have a line of code in the file saying Listen /var/run/cups/cups.sock already. If not add it)

At the top of the ports.conf file add the following:

Port 631

When all of this is done restart cups by typing: sudo /etc/init.d/cupsys restart.

Assuming that your host machine is Ubuntu and this is the machine your printer is connected to, than make sure you have already installed your printer and have set it to local default. Make note of your printer name and the ip address of your host machine. If you do not know your host ip address, in terminal type ifconfig. 

Now as stated in another post to get your printer working in XP you must point to the address that your printer is connected to. 

Here is the kicker. If you are behind a firewall and you have not enabled port 631 as an allowed service than you will never be able to print over your network. Even more, when you add a network printer in XP an error message will say it cannot find the printer. Make sure you have allowed incoming traffic through this port. 

In XP add a network printer. In the connect to this printer box type:

[http://(your](http://(your) ip address of your hostmachine):631/printers/(name of your printer you installed on your host machine). Click next. It should now ask you for a printer model and make. Install the driver and set the installed printer as your default printer.

Test by printing. 

* If you still get a printer error in XP than you have not enabled port 631 properly. If you are running the firewall firestarter, click policy and right click in the allow service box and add a rule. Do not worry about the service name. In the Port box type 631. The Name will automatically be assigned as Ipp. Click Add followed by clicking Apply Policy. Close firestarter. 

* I did not have to install samba to get this to work.

Hope this helps!

Cheers,
vkohli

---

### Post by indytim on 2006-07-09
skirkpatrick,

Just a brief note of thanks for your "quick approach" to network printing.  Worked well once I took the "leap-of-faith"  (aka "Port 631" and not Localhost:631).

IndyTim

---

### Post by skirkpatrick on 2006-07-10
ktneely,
No, there is no way to be able to download the driver using the URI.


indytim,
Yeah, Localhost:631 tells it to only listen to requests on port 631 coming from the localhost where Port 631 tells it to accept all requests coming in from port 631.

---

### Post by Schnoidz on 2006-07-14
Thanks vkohli, it worked perfectly on my Samsung ML-1710

---

### Post by vkohli on 2006-07-15
Schnoidz,

Glad to hear it worked well!

Cheers,
vkohli

---

### Post by Scunizi on 2006-07-16
I'd like to throw in a little twist.  I've got a Samsung ML-2010 that works great on the windows side both locally and through the home network.  On the Ubuntu side I can only get it to work using the ML-4500 driver.  Since the printer is plugged into the xp/linux box, which driver should be used on one of my remaining networked Wdz boxes?  ML-4500 driver for when linux is booted and ML-2010 driver for when xp is booted?  I know this is item specific and a little unusual but I'm sure there are other printers out there that work or work better in linux with a slightly different driver than the "correct" one designed for it.

---

### Post by vkohli on 2006-08-19
Scunizi,

It really is a matter of taste. It all depends on which driver works best for you. Personally, I have a MFP printer that is obviously fully supported by the windows driver. When I try the ppd file from the manufacturer as the linux driver, I can print fine, but all of the extra features my printer has to offer do not work. It is all a work in progress. Some printers are fully supported under linux and others are not. So, if your printer is not a multi functioning printer (MFP) and all you care for is printing with a few extra features, than you can use either driver. On the other hand if features of your printer are supported more by your windows driver I would use this one. 

I had a very similar problem trying to determine which driver to use. I'm running XP as a virtual machine in vmware. I found that I could be easily satisfied if I installed the printer in linux and than installed the windows driver in XP. When I need the full functionality of the printer I print using windows through the URI to my Ubuntu box. Otherwise print directly from linux. 

Cheers,
Vkohli

---

### Post by Scunizi on 2006-08-19
It's been a while but thanks for finding this thread and your input.  Since it's not a pressing issue I haven't tried printing from one of my windows boxes through samba to the linux box.  

On a side note.. I'm also using VMware on a clean install of Ubuntu on a totally different drive on my PC as a test.  WinXP installed perfect and seems to run almost as fast.  What I'd really like to do is quite a project.  Erase my Sda1 (80g), Sdb1&2 (120g) & Hda1&2 (300g), reinstall XP on sda1, Ubuntu on Sdb, use Hda for extra data.. running VMware Server to boot XP while in Ubuntu.  That way if VMware crashes I can still dual boot into either system.  But that's a topic for another thread. :D  Dealing with all my data is another issue before formatting.  In the mean time, I've gotta fix fstab on Hda's install.

---

