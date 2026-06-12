---
title: "Problem connecting to network printer"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by UT_Libertarian on 2012-12-27
I have Ubuntu 12.04 LTS, with a Canon MF4450 connected via USB to my router.  A windows machine on the same network uses the printer just fine, but I cannot install/connect from Ubuntu.  I can access the internet through the router, just not the printer.

---

### Post by chadk5utc on 2012-12-27
How does the printer showup on the network does it get an IP address? or is it shared through some software? to the windows machine

---

### Post by ahallubuntu on 2012-12-27
~

---

### Post by UT_Libertarian on 2012-12-27
Windows machine uses port IP_192.168.100.2

---

### Post by UT_Libertarian on 2012-12-27
When I try to install as a network printer, Ubuntu ask for host name.  since it's connected to the router, there is no host, so I am lost.

---

### Post by chadk5utc on 2012-12-27
I dont know what router or setup you have exactly, but I use Linux at work and we have tons of network printers from coast to coast there is usually a place to set the printer hostname and ipaddress. but being set up through a usb port on the router I have doubts that it will be seen as a network printer. If for some reason your unable to get this working they do make cheap network print servers.

---

### Post by ahallubuntu on 2012-12-27
~

---

### Post by UT_Libertarian on 2012-12-27
Now having trouble locating PPD file to install drivers.  I thought you could find ANYTHING on the internet.   Anything but a Canon MF4450 PPD file for other than windows or mac.....

---

### Post by ahallubuntu on 2012-12-27
~

---

### Post by UT_Libertarian on 2012-12-27
That got me UK drivers tested thru Ubuntu 9.10, but not a PPD file....

I already have a more current driver,  just not a PPD file

---

### Post by UT_Libertarian on 2012-12-27
"You can use the IP address in place of the hostname if you don't know it - 192.168.100.2 ."


I did this, but it won't let me specify where to look for the driver to install.  The choices it gives me do not include the printer I have, it gives me the option of supplying a PPD file which I don't have,  or have it search for a driver which it can't find and won't let me indicate where to look.

---

### Post by UT_Libertarian on 2012-12-27
Bypassing the router and connecting the printer directly to the computer via USB, it sees the printer, does not find a driver and will not talk after specifying a PPD file.

---

### Post by kurt18947 on 2012-12-28
Is this thread of any help?

[http://ubuntuforums.org/showthread.php?t=2091209](http://ubuntuforums.org/showthread.php?t=2091209)

There is a link to a canon-asia site for a driver.

---

### Post by UT_Libertarian on 2012-12-28
> **kurt18947 said:**
> Is this thread of any help?

[http://ubuntuforums.org/showthread.php?t=2091209](http://ubuntuforums.org/showthread.php?t=2091209)

There is a link to a canon-asia site for a driver.

Thanks, but tried that already.  Didn't help.  Don't know if it's because it says that driver is for x86 machines and mine is AMD, but no response.

---

### Post by kurt18947 on 2012-12-28
> **UT_Libertarian said:**
> Thanks, but tried that already.  Didn't help.  Don't know if it's because it says that driver is for x86 machines and mine is AMD, but no response.

On older distros it was necessary to install one or more packages (ia-32libs sticks in my mind) in order for 64 bit distros to run 32 bit software.  I don't know when that was no longer required (multi-arch support).  12.04 perhaps?  I favor Brother printers because they have pretty good linux support and ink is reasonable.  There were directions on their site to 'do this before installing the printer drivers'.  Among the requirements were making sure certain packages were installed because all Brother printer drivers for linux are 32 bit, even those running on 64 bit OS s.  This may or may not apply to Canon.  Sorry I can't be of more help.

---

### Post by speedygarth on 2013-01-29
I also have a canon MF8330 printer that couldnt print, but since i stumbled upon some help pages i have been reaping the full printing benefits!! just folllow these steps

1 Answer ACTIVEOLDESTVOTES
up vote
3
down vote
+100
A native 64-bit driver package is now available!
The only real solution is to install the native 64-bit drivers, but unfortunately Canon only provides 32-bit DEB packages.

After a lot of experimentation and a borrowed Canon MF4350dn all-in-one, I've managed to build the drivers and get them to work. They are available in a PPA.

How to install:
Important: you must first install the libxml2:i386 package (which pulls in the 32-bit libc6 and zlib packages which are also needed). This manual step is necessary because the alternative is to force people to install the 250 MB+ ia32-libs package.

Start by opening a terminal and typing:

sudo apt-get install libxml2:i386
Add the PPA with:

sudo apt-add-repository ppa:auanswers/canon64
Update with sudo apt-get update

Install the North American version:

sudo apt-get install cndrvcups-ufr2-us
or the European version

sudo apt-get install cndrvcups-ufr2-uk
Make sure your printer's device in Settings...Printing is the cnusb: device:





Help! I got a warning, installation failed, now what!?



This just means you forgot to install the i386 dependencies. Type sudo apt-get install libc:i386 zlib1g:i386 libxml2:i386, and then try again with sudo apt-get install cndrvcups-ufr2-us (or -uk)

---

### Post by speedygarth on 2013-01-29
from there selecting which folders contain your PPD files is a piece of cake!! good luck!!

---

### Post by pdc on 2013-01-29
so I think you aren't spelling everything out here Garth ............

.......you are talking about using the UFR II driver from Canon; at its 2.50 iteration at present ............. available from Canon Asia, Canon Europe and Canon US sites ............

and it has 32bit deb packages; and 32bit rpm packages .........

....but only 64bit packages;

so the solution you posted is for 64bit Ubuntu; is that correct?

for the 32bit Ubuntu one needs to install the common package first: [COLOR="SeaGreen"]cndrvcups-common_2.50-1_i386.deb[/COLOR]

and the [COLOR="SeaGreen"]cndrvcups-ufr2-uk_2.50-1_i386.deb[/COLOR]

for the 64bit, the advise is install the rpm packages via alien:

..again one would install the [COLOR="SeaGreen"]cndrvcups-common-2.50-1.x86_64.rpm
[/COLOR]
....and then the [COLOR="SeaGreen"]cndrvcups-ufr2-uk-2.50-1.x86_64.rpm[/COLOR]

......as I don't see you mentioning install the common package first; (which Canon say one must do): I just wonder if registering the ppd alone was the feature that enabled printing.....I don't know..just speculating

---

### Post by speedygarth on 2013-01-30
I followed the steps i outlined and yes i did forget to mention the common packages, but doing the other steps i outlined made it work and yes i am using 64bit systems. i hope my solution helps those who have 64bit ubuntu!

---

### Post by UT_Libertarian on 2013-05-30
Okay, trying again to get this thing to work.  First, I disconnected the printer from the router, and connected directly to the pc via usb.  Went to the Canon US site, downloaded the current driver package and extracted.  it contained an html installation guide, which I followed, Everything SEEMED to go fine, until it told me to "Register the printer (PPD) with the print spooler."  I followed the sample command in the TERMINAL window as best I could.  It said # /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -E
not knowing exactly what to use for [Printer Name] or [device file location] i guessed the best I could.  At that point, I realized I had not yet located the folder with the .ppd files, so I went in search of those.  When I realized I had not yet extracted those, i did so, and, remembered that as an option in installing a new printer from System Settings.  So I went into System Settings, and went through the steps to add a new printer.  Since it still would not find the appropriate driver, it did give me the option of providing a PPD file, which I did.  It seemed to complete the installation, but when I try to print a test page, it says it's sending data to the printer, nothing happens, then says the printer is idle.  When I look at the print queue for that printer, it says the printer is stopped.  I tried turning off the printer, and the printer status indicates it is unplugged or off, then when I turn it back on, it indicates idle, and if I attempt to print a test page, same thing.  nothing out, reports as idle, and queue shows printer stopped.  Tried rebooting pc, and printer, no difference.

---

### Post by pdc on 2013-05-30
so which printer are you wanting to get working; and are you using 32bit Ubuntu; and which version please?

and it was the UFR driver you downloaded.....and which version please

---

### Post by UT_Libertarian on 2013-05-30
Also, when attempting to install this as a new printer, it says searching for drivers, but doesn't find them.  I don't know where it's looking for them, or I would move them to where it's looking to save me the trouble of doing everything through TERMINAL.  Any advice in that regard would be appreciated as well.

---

### Post by UT_Libertarian on 2013-05-30
Printer is Canon MF4450, using 12.04, 32-bit (though until just now I thought it was 64-bit) downloaded UFR2 version 2.60
I think that covers all your inquiries.....

---

### Post by pdc on 2013-05-30
off to work; will reply in 12hrs

you obviously have worked through the guide in the driver package..

---

### Post by Jhon smith on 2013-05-30
hi friend some time printer is not connecting properly.Printer drives not support .so instal drives.

---

### Post by UT_Libertarian on 2013-05-30
UPDATE - Having just realized everything I've done in the last 36 hours was under the impression that I was running a 64-bit version of 12.04 instead of the actual 32-bit version, I'm going to attempt to undo everything, and try again with the 32-bit drivers.....   

Results to follow as they become available....

---

### Post by UT_Libertarian on 2013-05-30
having now undone the 64-bit driver install and completed the 32-bit install, and attempted to let ubuntu find the printer, it still could not find the ppd file, so I indicated where it was.  Same results - when I try to print a test page, it says sending data to printer, but when i view printer queue, it shows printer stopped...

---

### Post by UT_Libertarian on 2013-05-30
using the guide in the driver package, I attempted to check the driver version.  I entered the sample command, and all I got was a new terminal prompt.

---

### Post by wilsonmr77 on 2013-05-30
the workplace 2 doors removed from mine includes a printer connected to 1 of the 2 computers there, however the second PC cannot connect with the printer, and each computers ar on the network, the printer is shared however, it connects to the printer in my workplace, thus anytime we have a tendency to get disturbed by the guy from consecutive workplace once there's a printer connected to his colleagues pc we've tried severally to attach him with the printer in his workplace. any plan why the PC will-not connect with the printer in his workplace via the network however can connect with the printer in our workplace via an equivalent network?


Note
We had a portable computer in our workplace too that didnt connect with the printer in our workplace however might access the network files.

How do i solve the matter and what am i able to do if i realize myself within the state of affairs once more
[ASP NET Web Hosting](http://www.aspwebhosting.com.au/)

---

### Post by pdc on 2013-05-30
Hi UT_Libertarian;

I am not clear about how this MF4450 is connected to your computer; 

what does 

> [COLOR="#FF0000"]sudo /usr/sbin/lpinfo -v[/COLOR] give please if you can paste the results back please

.......obviously with the printer all plugged in and warmed up etc

I wasn't clear if you had located where the Canon driver had placed the ppd files: it usually seems to be /usr/share/cups/model/

In one of their guides, Canon mention that it can be helpful to spell out the full path to a ppd file (if using -P)

the example they give is

"[COLOR="#EE82EE"]/usr/sbin/lpadmin -p iRC5180 -P /usr/share/cups/model/CNCUPSIRC5180ZK.ppd -v lpd://192.168.1.10/iRC5180 -E[/COLOR]"

where the printer is iRC5180 and the ppd file is CNCUPSIRC5180ZK.ppd (the K is for english and a J ppd is for Japan) and the full path to the ppd is /usr/share/cups/model/CNCUPSIRC5180ZK.ppd

_____________________________________________________________________________

I thought if we covered that ground first and then backtracked on what you had done

________________________________________________________________________________-

when you said

> [COLOR="#A52A2A"]I attempted to check the driver version. I entered the sample command, and all I got was a new terminal prompt[/COLOR]. 

did you mean you had entered the command

> [COLOR="#FF0000"]sudo dpkg -l | grep cndrvcups[/COLOR]

if you COPY and paste the above command again for us please, and copy and paste back the result if any result emergis please

---

### Post by UT_Libertarian on 2013-05-30
> **pdc said:**
> Hi UT_Libertarian;

I am not clear about how this MF4450 is connected to your computer; 

what does 

 give please if you can paste the results back please

.......obviously with the printer all plugged in and warmed up etc

I wasn't clear if you had located where the Canon driver had placed the ppd files: it usually seems to be /usr/share/cups/model/

In one of their guides, Canon mention that it can be helpful to spell out the full path to a ppd file (if using -P)

the example they give is

"[COLOR=#EE82EE]/usr/sbin/lpadmin -p iRC5180 -P /usr/share/cups/model/CNCUPSIRC5180ZK.ppd -v lpd://192.168.1.10/iRC5180 -E[/COLOR]"

where the printer is iRC5180 and the ppd file is CNCUPSIRC5180ZK.ppd (the K is for english and a J ppd is for Japan) and the full path to the ppd is /usr/share/cups/model/CNCUPSIRC5180ZK.ppd

_____________________________________________________________________________

I thought if we covered that ground first and then backtracked on what you had done

________________________________________________________________________________-

when you said



did you mean you had entered the command



if you COPY and paste the above command again for us please, and copy and paste back the result if any result emergis please

Originally, this printer was connected to a usb port on my router, where it was accessible to my kids' laptops and my wife's Windows pc, but not by my ubuntu machine.  So yesterday, I decided to (temporarily) connect it to my ubuntu machine directly via usb to establish communication and functionality, and then return it to the router and work on the technicalities of finding it there.

When I enter the command [COLOR=#ff0000][/COLOR][COLOR=#FF0000]sudo /usr/sbin/lpinfo -v [/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]I get the following:

network http
network https
network ipp14
network ipp
network ipps
network lpd
network socket
network beh
direct scsi
network smb
direct usb://Canon/MF4400%20Series?serial=1116A5202457&interface=1
direct usb://Canon/MF4400%20Series%20FAX?serial=1116A5202457&interface=2

In the extraction process, I have no idea where it put the ppd files, so i downloaded again, and saved it to a directory I knew where they were, and in trying to get the auto-detect to install the printer, I pointed it there to get the ppd file.

When I tried to check the driver version, I used the rpm command listed in the guide. 

Since we last communicated this morning, I made a few other attempts at getting it to work, and ended up (trying to) undo everything I did, so that when you again became available this afternoon, I could start with (nearly) a clean slate.  Therefore, when I now enter [COLOR=#ff0000][/COLOR][COLOR=#FF0000]sudo dpkg -l | grep cndrvcups[/COLOR] I just get the terminal prompt back, no output.

Sorry this is a little slow, when I reply with a quote, the requested commands do not show up in the edit box, and I have to open another tab with the post there to see what was listed.

---

### Post by pdc on 2013-05-30
OK; 

well we need to install the common driver first [COLOR="#008000"]cndrvcups-common_2.60-1_i386.deb[/COLOR and then the specific [COLOR="#008000"]cndrvcups-ufr2-uk_2.60-1_i386.deb[/COLOR]

assuming you downloaded the package [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR] to your Downloads directory; 

> [COLOR="#FF0000"]cd Downloads[/COLOR] ........then the command > [COLOR="#FF0000"]ls[/COLOR] should show you what's in that directory; and the package [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR] should be there ..so..

> [COLOR="#FF0000"]tar -zxvf Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR] ......and that creates a directory called [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN[/COLOR] and then you need to drill inside it to the Debian directory so the command should be

> [COLOR="#FF0000"]cd Linux_UFRII_PrinterDriver_V260_uk_EN/32-bit_Driver/Debian/[/COLOR] .........and if you again type > [COLOR="#FF0000"]ls[/COLOR]........you should see two packages 

............ [COLOR="#008000"]cndrvcups-common_2.60-1_i386.deb[/COLOR] and [COLOR="#008000"]cndrvcups-ufr2-uk_2.60-1_i386.deb[/COLOR]

Ubuntu uses Debian packaging, so you are using deb packages .............

so the next two commands to install these are

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-common_2.60-1_i386.deb[/COLOR]

and then 

> [COLOR="#FF0000"]sudo dpkg -i cndrvcups-ufr2-uk_2.60-1_i386.deb[/COLOR]

then restart cups

> [COLOR="#FF0000"]sudo service cups restart[/COLOR]

_____________________________________________________________________________________________

then Canon say to **[COLOR="#A52A2A"]Register the printer (PPD) with the print spooler[/COLOR]**.

Your list of programmes on your Ubuntu desktop should have one called "Search": on mine, if I type in [COLOR="#A52A2A"]ppd[/COLOR] and ask it to look through the [COLOR="#A52A2A"]file system[/COLOR], it finds a list of ppd files, and the Canon ones seem to get installed in [COLOR="#008000"]/usr/share/cups/model/[/COLOR] and usually [COLOR="#0000FF"]lpadmin[/COLOR] knows where to look

_________________________________________________________________________________________________-

the command Canon says to register is

> [COLOR="#A52A2A"]sudo /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -E[/COLOR]

so for you it should be 

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p MF4450 -m [PPD file] -v usb:/dev/usb/lp0 -E[/COLOR]

________________________________________________________________________________________________

I think it is likely the name of the ppd file is something like CNCUPSMF4450K.ppd and its correct name should be entered in the above

.....then you should have a driver and be able to print

---

### Post by UT_Libertarian on 2013-05-30
Okay, so I installed the two package listed above, except that I have the US package instead of the UK package, and made the corresponding adjustment to the install command.  Then I made sure to change dir to the one containing the ppd file, which, again, was the US variety, to register the printer with the spooler.  All went well.  I still had a previous version of something installed, because when I looked in the system settings under printing, there was the old one, and the newly installed MF4450.  When I opened the MF4450 and attempted to print a test page, it showed up in the print queue of both printers.  I deleted the previous printer, and cancelled the processing job for the MF4450, then re-started the test page.  That was a few minutes ago, and it still shows in the print queue as "Processing".  This is an improvement over previous attempts, in that before, the queue showed the printer as "Stopped".  The incoming data light on the printer never flickered, so I don't know what to make of that.  If this still doesn't pan out, I will uninstall both packages and try again after having deleted the printer listed in system settings.  Hopefully then a clean pass through all steps listed above should clear all hurdles.

---

### Post by UT_Libertarian on 2013-05-30
Backed out through all steps, and repeated a clean install.  Print queue still shows "processing" after several minutes, but nothing at the printer.  Trying to hurry through this, my fingers are getting tongue-tied.....

Correction - in the print queue, it states "Processing" but under printer properties, it states the status as "Processing - Waiting for printer to become available."

---

### Post by pdc on 2013-05-30
as you said the printer was now USB to your computer, I was hoping a simple /dev/usb/lp0 would suffice

However I see you got 

> usb://Canon/MF4400%20Series?serial=1116A5202457&interface=1

on the command "sudo /usr/sbin/lpinfo -v"

as I understand it, when you register the printer the name you enter......is what appears on Ubuntu, so you can call it anything.....so if we call this latest try [COLOR="#0000FF"]MF4451[/COLOR]

and try the command 

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p MF4451 -m [COLOR="#A52A2A"][PPD file][/COLOR] -v usb://Canon/MF4400%20Series?serial=1116A5202457&interface=1 -E[/COLOR]

........again I don't know what the ppd file was called .......perhaps you let us know as it may be useful to someone else........

---

### Post by UT_Libertarian on 2013-05-30
I got those results from [COLOR=#ff0000]sudo /usr/sbin/lpinfo -v[/COLOR] after having used the command [COLOR=#ff0000][/COLOR][COLOR=#ff0000]sudo /usr/sbin/lpadmin -p MF4450 -m CNCUPSMF4400ZS.ppd -v usb:/dev/usb/lp0 -E[/COLOR]  the guide from the download package mentioned if there were connecting problems, to try the command you suggested, which I did, with no change in results.  It still shows the status "idle - waiting for printer to become available"

---

### Post by pdc on 2013-05-30
I see again the Canon guide says

> [COLOR="#A52A2A"]If you are connected via USB to a device that requires bi-directional communication, specify "cnusb" instead of "usb" in commands[/COLOR]. 

and your device seems bi-directional

they also say

> In such cases, you can confirm [COLOR="#0000FF"][device file location][/COLOR] by executing the "/usr/lib/cups/backend/cnusb" command (in the case of 32-bit operating systems) with administrator privileges.

so what does 

> [COLOR="#FF0000"]sudo /usr/lib/cups/backend/cnusb[/COLOR] give you 

I guess we are heading towards some sort of 

sudo /usr/sbin/lpadmin -p MF4451 -m CNCUPSMF4400ZS.ppd -v cnusb://Canon/MF4400%20Series?serial=1116A5202457&interface=1 -E

---

### Post by UT_Libertarian on 2013-05-30
After entering [COLOR=#FF0000]sudo /usr/lib/cups/backend/cnusb[/COLOR] I get the result [COLOR=#ff0000]direct cnusb:/dev/usb/lp0 "Canon MF4400 Series" "Canon MF4400 Series CNUSB #1"[/COLOR] and when I enter the command you suggested, I get the following result

[COLOR=#ff0000][1] 4985
-E: command not found
[1]+  Done                    sudo /usr/sbin/lpadmin -p MF4451 -m CNCUPSMF4400ZS.ppd -v cnusb://Canon/MF4400%20Series?serial=1116A5202457


[/COLOR][COLOR=#000000]Now I show two printers, 4450 and 4451.  4450 states idle - not connected.  4451 states stopped.
[/COLOR]

---

### Post by pdc on 2013-05-30
I see Canon say

> **Do not register the printer** using the "lpadmin" command before restarting CUPS.

so we had better use the command

> [COLOR="#FF0000"]sudo service cups restart[/COLOR] ............as I understand that, it sort of "reboots" CUPS ........

_____________________________________________________________---


well it seems like your printer is seen as 

> [COLOR="#A52A2A"]cnusb:/dev/usb/lp0[/COLOR]

so the syntax from Canon is 

> # /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v usb:[device file location] -E

so if we try 

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p MF4452 -m CNCUPSMF4400ZS.ppd -v cnusb:/dev/usb/lp0 -E[/COLOR] ........if you copy and paste that ...........looking for an MF4452 created ............

---

### Post by UT_Libertarian on 2013-05-31
[SIZE=7]It's ALIVE!!!![/SIZE]

Now if I can reconnect it to the router and talk to it there, I'll be set.....

---

### Post by pdc on 2013-05-31
...........great! .............maybe just enjoy it for a little while before unplugging again!!

I see for a network connection Canon say

> /usr/sbin/lpadmin -p [Printer Name] -m [PPD file] -v lpd://[Device IP address or FQDN]/[Printer Name] -E

so looks like if you fill in the blanks, you are good to go ! Enjoy!

(You can edit the title of the thread to add SOLVED ...........if you feel it is sort of solved for now ................

---

### Post by UT_Libertarian on 2013-05-31
I'd consider editing the title to add SOLVED, except the thread originated trying to talk to the printer via the router in the first place, just gravitated here to make sure it wasn't just a communication error via the router.

---

### Post by UT_Libertarian on 2013-05-31
Status returns[COLOR=#ff0000] Idle - The printer is busy.[/COLOR]  I'm wondering if it has something to do with the cnusb bidirectional communication stuff.....

---

### Post by UT_Libertarian on 2013-05-31
Went back to System Settings and had it find the printer on the network by the address used by the Windows machine, and told it where to find the ppd file, and, as they say,
                [SIZE=7]the Eagle has landed.[/SIZE]

---

### Post by UT_Libertarian on 2013-05-31
Having trouble editing thread title to add SOLVED......

---

### Post by pdc on 2013-05-31
> Went back to System Settings and had it find the printer on the network by the address used by the Windows machine, and told it where to find the ppd file, and, as they say, the eagle has landed!!


well that is marvellous; enjoy

when you say

>  told it where to find the ppd file .........did you have to spell out the full path .............and had Canon put it in /usr/share/cups/model/ ............as you can see, I am keen to quiz you to find out as many details for future enquiries ..............

---

### Post by UT_Libertarian on 2013-05-31
From System Settings, I added a printer, where I selected the Network Printer option.  It asked for the hostname, and I entered the IP address used by my wifes Windows machine, and it filled in the Port information.  It went searching for drivers, I doubt it found them, and asked me to choose from:

Select printer from database
Provide PPD file
Search for a printer driver to download

I selected the ppd file option, and it gave me a pull down location for the ppd file.  It gave as an option to use the recently used PPD file, or the file structure menu where I could step through to identify the folder containing the PPD file.  I chose the recently used PPD and away we went.  Happy camper.

No, the folder you listed was empty.  I will move it there, though.

I was able to edit the title of a post, but not for the thread.  I've done it before, but it's been so long I can't remember how.

---

