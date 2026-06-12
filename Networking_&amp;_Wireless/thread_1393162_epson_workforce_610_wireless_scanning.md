---
title: "epson workforce 610 wireless scanning"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by gcolvin on 2010-01-29
I have read quite a bit about the difficulty of getting epson printer/scanners to work with Linux. My printer worked out of the box with Ubuntu 9.10. The scanner setup was another story.  Suffice it to say I learned a good deal about my new OS trying to get my scanner to work wirelessly. Xsane just didn't work for wireless devices, even after mucking around in a lot of files (config, saned, inetd etc.). So I downloaded iscan from synaptics package manager. This didn't work either. I gathered from the Sane project that it would with the iscan-network-nt plugin, from Avasys, a Japanese software company. The Nabble forum stated that the workforce 610, among other scanners, would work with iscan and work wirelessly with the plugin. The problem is that there is no clear direction to the software, and that once you get to Avasys, many of the models that are said to be supported, by Avasys and by the Sane folks, have no links for iscan or for said network plugin. In fact, there is no link or download for the plugin anywhere on the site. I did finally find a link on google to the iscan-network-nt plugin here:[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb)  Lo and behold, it scans wirelessly now without a hitch.  It seems that most Epson scanners, printers and all-in-ones are now supported via wireless with the  iscan application and the network  plugin, which for some reason, does not come bundled with the iscan program (maybe b/c it's very beta at this point).
Finally, you have to go into the file  etc/sane.d/epkowa.conf and uncomment (remove the # sign) one of the last lines at the bottom of the page that begins with #net. and add the network address of your device so that it reads, for example:   net  197.168.0.166. On the 610 you can get this info by going to the menu on the front of the printer, selecting "setup," then "confirm network setting." At the bottom the IP address of your printer/scanner is listed. You can also print a status sheet from here by hitting the "start" button. This is full of info, like your IP address, device i.d., workgroup name, port in use and so on. It can come in handy. Put the IP address from here into the epkowa.conf file and save it. You will need privileges to do so, of course. I did not need to change anything in the inet.d file, the sane.d file or any others, as was mentioned in much of the Xsane help.
I hope this is useful to someone. It was actually a very good way to start to learn using Linux.
BTW, the epson website doesn't even mention Linux on their website, much less tell you that image scan (iscan) is an available software support option, which means you have to go look for yourself, which can be a very tedious process. There is a PDF out on the web written by Epson describing how to get their scanners working with Image Scan. It is however, a very convoluted and complicated 26 page document requiring many steps, and facility with the command line. I did not find you needed to manipulate all the files they listed, in particular, the inetd file. Regardless, the company seems to have little interest in the Linux user, probably because of customer support issues they cannot defer to a third-party software vendor. Understandable, but I would suggest using a different manufacturer given the choice. Too bad, they otherwise offer excellent value.
Good Luck

---

### Post by maxtorqe on 2010-02-20
Thanks for this information.  I configured the printer via the built-in Ubuntu (9.10) network printer configuration, then I downloaded the iscan-network plugin via your link and installed it and it works! :)

---

### Post by gcolvin on 2010-02-24
I'm glad that the post was helpful. Best wishes and thanks for the reply
gcolvin

---

### Post by seeklinux on 2010-03-20
I appreciate the pointers on how to set up the scanner also. I was able to get my scanner working via wireless without issue.  

However, I think you are being a little hard on Epson.  While they may not mention Linux at their site (I didn't try), doing a Google search of "epson linux drivers" took me to the [Avasys site]("http://avasys.jp/eng/linux_driver/").  There it was easy to use the Avasys web site to enter my printer type, at which point it showed me the set of drivers. They also have both RPM and deb packages and their [FAQs]("http://avasys.jp/eng/linux_driver/faq/") helped me figure out an install issue when there was a missing dependency (for libltdl3). Their instructions also told me exactly how to set up CUPS so that when I added a new printer, my printer type was listed. In the past, with a new printer I would have to experiment with drivers for other (similar) models to find one that would work.

I have for a long time eschewed getting an all-in-one printer because of lack of Linux support for some functions (often all that anyone got working was the printer).  I appreciate that Epson went to the trouble and expense of contracting with Avasys to provide drivers.  Yes, some other manufacturers provide Linux drivers as well, while others don't really seem to care about Linux at all. I won't mention any names, but I am thinking of a company based in Lexington.

So I appreciate you for providing information that made the scanner set up easier, and I appreciate Epson for having Avasys provide drivers and update them (they made updates in March).  Having been a Linux desktop user for over 10 years, I actually researched the Linux driver issue before deciding to purchase the WorkForce 610.

Now as for how quickly the ink runs out and the cost of new ink, that I don't appreciate so much.;)

Thanks again for providing the information on your experience.

---

### Post by jpschubert on 2010-03-27
I have the 610 connected to my network via router w/wired connection.  Printer works fin but can't get scanner to work.  Tried downloading the file you suggested and get an error saying wrong architecture.  My P4 is 64bit.  Couldn't find a 64bit file for ubuntu.  Can you help?

---

### Post by Dybbuk on 2010-05-11
@gcolvin - Great post! just what I needed to get my workforce 610 scanning, tyvm!!

@jpschubert - I have 10.0.4 64bit, here is what I had to do to get the scanner to work, I am sure its the same for 9.10

1. download [http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_amd64.deb)
2. open it and have it install
3. download [http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb)
4. open it and install it
5. Follow gcolvin instructions and open /etc/sane.d/epkowa.conf 
```
sudo vi /etc/sane.d/epkowa.conf
```6. add your printer's IP address to the end of the file like this:
```
net 192.168.1.30
```(make sure you have "net" at start and replace 192.168.1.30 with your printer's IP)
if all goes well go to "Applications >> Graphics >> Image Scan! for linux" and start scanning, good luck! :)

Note - this is my first post so I am not sure if the links will work.. so i am attaching a zip with the files I listed

---

### Post by mikefreeman on 2010-05-22
Followed these instructions, but Image Scan cannot find the scanner. I get the following:

Could not send command to scanner.
Check the scanner's status.

I can print fine to the printer, so I know it is connected and functioning. I confirmed that the IP for my printer is correct in my epkowa.conf file on the uncommented net line.

I am running 64-bit Linux Mint 9 (which is Ubuntu 10.04 with some extra programs, all non-free codecs installed, and some driver configuration mods). I followed Dybbuk's 64-bit install instructions, as well as Gcolvin's original instructions.

Any ideas? Thanks!

---

### Post by SoFl W on 2010-06-01
Just wanted to thank you and let you know this information helped out and worked.  This went quickly and smoothly, I think the time from taking it out of the box to my first print, to my first scan was about a half hour.

[COLOR=Blue]An important note:[/COLOR]  I did set up the unit with a static IP.  (Epson calls it manual set up)  I think it is important to set up the printer/scanner with a static IP when it comes to scanning because of the configuration file "/etc/sane.d/epkowa.conf"  This way you are sure the address doesn't change.

 I want to thank the users on this page and the other page listed above for their help.

I found [this other page]("http://ubuntuforums.org/showthread.php?t=1407631") of use also
[http://ubuntuforums.org/showthread.php?t=1407631](http://ubuntuforums.org/showthread.php?t=1407631)

---

### Post by SoFl W on 2010-06-01
> **mikefreeman said:**
> Followed these instructions, but Image Scan cannot find the scanner. I get the following:

Did you make sure you edited the "/etc/sane.d/epkowa.conf" file correctly?  You need to sudo edit this file.   You also need to make sure the IP addresses match in the config and the address the scanner uses.  This is why I recommend manually using a IP address.

I should ask if you downloaded the correct version 32bit or 64 bit

---

### Post by SoFl W on 2010-06-01
I was able to get it to work on my 9.10 64bit ubuntu-studio machine, however on my 10.4 32bit ubuntu-desktop laptop it wants to scan, I hear the scanner start but it crashes.  This is with sane not the default simple scan.  simple scan doesn't even locate the scannner.

I was not able to download the packages as you described, there was a version conflict. The printer works fine.

I **was** able to get memory card access from ether machine, even tried these directions
[http://ubuntuforums.org/showthread.php?t=1285845](http://ubuntuforums.org/showthread.php?t=1285845)

EDIT: 
I was able to get the memory card to work.  You have to have at least one file on the SD  card.  Also on the original print out of my setup there were several  "NONE" fields.  Once I made corrections and scanned to a PDF on the  memory card the memory card features worked.

---

### Post by SoFl W on 2010-06-05
Have you experienced trying to scan something, the scanner will start then it stops, you get an error and the printer has many lights flashing in unison but nothing on its LCD display?  Cycling the power on the 610 seems to fix the problem, sometimes a boot is required.

Occasionally after powering back on it would tell me I need to reinsert all of the print cartridges.

This has happened on two machines, one using 9.10(64) and the other 10.4 (32)  I am using the 610 over the wireless network with a static IP.

---

### Post by SoFl W on 2010-06-24
How to set up the link to the memory card on the printer (if in use)

Goto Places-> connect to server

Server Type: Windows Share
Server: (The IP address of the printer)
Share: MEMORYCARD
Folder: (blank)
User Name: (Your user name)
Domain Name: WORKGROUP

If you want add a bookmark so you don't have to repeat the process each time.  The bookmark will appear in the places menu.  You use your username and when it asks for a password use your login password.
I am not sure why, sometimes when I click the bookmark in Places it gives me a read error, I clear the error and click again it is fine.

See attached picture for set-up info.

---

### Post by xltrigger on 2010-06-24
I used these instructions on my 10.04 64bit machine and it worked great. Thank you Dybbuk. I'm scanning right now using the ADF. I really wish these companies would start supporting linux users. What's ironic is that although I haven't found a way to gain access to the shell, the Epson Workforce 610 is actually running embedded Linux. 

The 610 is one of the best printers I have every owned. I outdoes much more expensive printers (I got mine for $99 from Newegg.)

I also have an old memory card that I stuck in there so I can just scan to the memory card when necessary (i.e. scanning something for a guest. They don't need to install anything. Just browse to the share.)


> **Dybbuk said:**
> @gcolvin - Great post! just what I needed to get my workforce 610 scanning, tyvm!!

@jpschubert - I have 10.0.4 64bit, here is what I had to do to get the scanner to work, I am sure its the same for 9.10

1. download [http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.24.0/iscan_2.24.0-4.ltdl7_amd64.deb)
2. open it and have it install
3. download [http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_amd64.deb)
4. open it and install it
5. Follow gcolvin instructions and open /etc/sane.d/epkowa.conf 
```
sudo vi /etc/sane.d/epkowa.conf
```6. add your printer's IP address to the end of the file like this:
```
net 192.168.1.30
```(make sure you have "net" at start and replace 192.168.1.30 with your printer's IP)
if all goes well go to "Applications >> Graphics >> Image Scan! for linux" and start scanning, good luck! :)

Note - this is my first post so I am not sure if the links will work.. so i am attaching a zip with the files I listed

---

### Post by charlesviper on 2010-07-16
In /etc/sane.d, I only have 'epjitsu.conf', 'epson.conf' and epson2.conf'. Can anybody post their epkowa.conf for me to save in /etc/sane.d?

I am trying to scan over USB. XSane scans for devices and says 'no devices found'.

---

### Post by crashingpain on 2010-12-10
I just reinstalled Ubuntu and was looking over this. I am having a very hard time trying to find iscan. I cant find it under synaptic and when I go to the developers website I cant find the workforce 610 version, just all these perfection models.

---

### Post by BuddyLee13 on 2011-01-21
Thanks to the original poster for this info, it got me on the path to being able to scan!

I did run into one issue, hope this helps someone else.  When running iscan or xsane or anything using the sane backend, I was getting errors like the one below:

```

*** buffer overflow detected ***: iscan terminated

```

Searching for info on it, I found [this post]("http://web.archiveorange.com/archive/v/LLXmLY03jJKLdoD7pzmM#pOOohi7qy2qEDIf") which suggests commenting-out the "net autodiscovery" line in the /etc/sane.d/epson2.conf file, which I did.  That got rid of the error BUT my scanner wasn't found.  I ended-up getting things working by putting the same "net epson" in the epson2.conf file that this thread has us putting in the epkowa.conf file (epson is an entry in my /etc/hosts file)

With regards to finding the AVASYS drivers, I too had some difficulty finding them but keyed off the URL and grabbed them by just browsing through [here]("http://linux.avasys.jp/drivers/") and below are the links to the folders that got me what I needed:

iscan-data (dependency for iscan):
[http://linux.avasys.jp/drivers/iscan-data/1.6.0/](http://linux.avasys.jp/drivers/iscan-data/1.6.0/)

iscan itself:
[http://linux.avasys.jp/drivers/iscan/2.26.1/](http://linux.avasys.jp/drivers/iscan/2.26.1/)

iscan-network-nt:
[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/)

---

### Post by libuntux on 2011-09-10
> **gcolvin said:**
> I have read quite a bit about the difficulty of getting epson printer/scanners to work with Linux. My printer worked out of the box with Ubuntu 9.10. The scanner setup was another story.  Suffice it to say I learned a good deal about my new OS trying to get my scanner to work wirelessly. Xsane just didn't work for wireless devices, even after mucking around in a lot of files (config, saned, inetd etc.). So I downloaded iscan from synaptics package manager. This didn't work either. I gathered from the Sane project that it would with the iscan-network-nt plugin, from Avasys, a Japanese software company. The Nabble forum stated that the workforce 610, among other scanners, would work with iscan and work wirelessly with the plugin. The problem is that there is no clear direction to the software, and that once you get to Avasys, many of the models that are said to be supported, by Avasys and by the Sane folks, have no links for iscan or for said network plugin. In fact, there is no link or download for the plugin anywhere on the site. I did finally find a link on google to the iscan-network-nt plugin here:[http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb](http://linux.avasys.jp/drivers/scanner-plugins/iscan-network-nt/1.1.0/iscan-network-nt_1.1.0-2_i386.deb)  Lo and behold, it scans wirelessly now without a hitch.  It seems that most Epson scanners, printers and all-in-ones are now supported via wireless with the  iscan application and the network  plugin, which for some reason, does not come bundled with the iscan program (maybe b/c it's very beta at this point).
Finally, you have to go into the file  etc/sane.d/epkowa.conf and uncomment (remove the # sign) one of the last lines at the bottom of the page that begins with #net. and add the network address of your device so that it reads, for example:   net  197.168.0.166. On the 610 you can get this info by going to the menu on the front of the printer, selecting "setup," then "confirm network setting." At the bottom the IP address of your printer/scanner is listed. You can also print a status sheet from here by hitting the "start" button. This is full of info, like your IP address, device i.d., workgroup name, port in use and so on. It can come in handy. Put the IP address from here into the epkowa.conf file and save it. You will need privileges to do so, of course. I did not need to change anything in the inet.d file, the sane.d file or any others, as was mentioned in much of the Xsane help.
I hope this is useful to someone. It was actually a very good way to start to learn using Linux.
BTW, the epson website doesn't even mention Linux on their website, much less tell you that image scan (iscan) is an available software support option, which means you have to go look for yourself, which can be a very tedious process. There is a PDF out on the web written by Epson describing how to get their scanners working with Image Scan. It is however, a very convoluted and complicated 26 page document requiring many steps, and facility with the command line. I did not find you needed to manipulate all the files they listed, in particular, the inetd file. Regardless, the company seems to have little interest in the Linux user, probably because of customer support issues they cannot defer to a third-party software vendor. Understandable, but I would suggest using a different manufacturer given the choice. Too bad, they otherwise offer excellent value.
Good Luck

I am glad it all worked so well for you. Unfortunately I am unable to set-up the printer properly. You said it worked out of the box. Can you clarify little bit how did you go about setting it up? I did change the epkowa.conf file as mentioned in other message but I am unable to see the printer. Is it supposed to discover the printer on its own?

thanks much in advance

---

### Post by vis9 on 2012-09-04
Thank you gcolvin, after having modified  etc/sane.d/epkowa.conf I was able to use the scanner and the printer (BX320FW). Now it's possible to download the driver and the network plugin from the epson site too:

[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

---

### Post by bipa on 2013-02-16
Thanks all, that helped.
For what is worth, I confirm that this same simple procedure worked for me to enable network scanning from a network-attached Epson Workforce WF-7525 (although the Epson site does not currently list this model as supported by the iscan network plugin). Therefore, if you specify WF-7525 (or WF-7520 in the US), the site won't offer the plugin among the download options: I worked around this by selecting an officially supported model (Workforce 610, which is the initial subject of this thread). The plugin installed perfectly (x64 OpenSUSE 12.2 here, so I used the x86_64 RPM) and iscan found the scanner (identified as "Epson WF-7520 series") and so far seems to work flawlessly (including A3 format originals and duplex ADF source selection).

---

