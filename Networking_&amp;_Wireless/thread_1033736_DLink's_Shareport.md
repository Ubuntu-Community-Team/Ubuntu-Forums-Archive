---
title: "DLink's Shareport"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by qaissi on 2009-01-07
Of course there is no Linux version of this program available that I have found as of yet.  So I was just wondering if anybody had any ideas as to how one would go about trying to access the usb port a DLink DIR 655.

---

### Post by digitldrug on 2009-03-10
I'd be interested about this as well.

It seems that most USB to Network adapters that support bi-directional communication (for MFP printers, and USB based
storage devices) do so through a custom USB over ethernet driver.

I recently purchased a Netgear print server to place my parent's
MFP printer on the network and ran into this problem. I also own
the DLink DIR-655 router myself (which now supports this functionality and more).  Both are windows only.

I am a complete linux/Ubuntu noob, but would love to hear more if
there is a solution.

---

### Post by wbrokow1 on 2009-03-21
I am also interested, if someone has a solution.
Thanks

---

### Post by Berner on 2009-03-28
I'd also like to see some solution to this... 'problem' might be a bit to strong.

The best solution I could think of would be if someone could come up with a firmware for the DIR-655 (and it's cousins) that supported samba.

---

### Post by kire68 on 2009-04-16
has anyone found a solution for the USB Shareport wireless feature on the dlink dir-655 router?  I've got a USB 1 TB hd connected with music and videos that i cant access with Ubuntu Hardy

---

### Post by tad1073 on 2009-04-16
This is kinda off topic but would it be possible to connect a USB hub to the share-port so you can connect multiple devices such as printers, storage etc,

---

### Post by bradtacdc on 2009-04-19
> **tad1073 said:**
> This is kinda off topic but would it be possible to connect a USB hub to the share-port so you can connect multiple devices such as printers, storage etc,

Yes it is. I have done this with my 4500 and it works fine. I have 2 Printers hooked up and one external Hard Drive.:)

---

### Post by tad1073 on 2009-04-20
cool, the wireless router where I live stopped working the other day, so I am hoping that my mom will get the one I have suggested which is [ this one ](http://www.bestbuy.com/site/olspage.jsp?skuId=8040121&type=product&id=1157068454881)

---

### Post by bradtacdc on 2009-04-20
> **tad1073 said:**
> cool, the wireless router where I live stopped working the other day, so I am hoping that my mom will get the one I have suggested which is [ this one ](http://www.bestbuy.com/site/olspage.jsp?skuId=8040121&type=product&id=1157068454881)

Yea, my friend has that router. Its fast and keeps up with multiple computers playing COD4. Its a good buy. :)

---

### Post by tad1073 on 2009-04-21
> **bradtacdc said:**
> Yea, my friend has that router. Its fast and keeps up with multiple computers playing COD4. Its a good buy. :)

My biggest worry/problem is location. The router will be in the kitchen on the first floor, my room is above the garage on the second floor. I am only about 20' away but the signal is traveling through walls floors and other wireless interference.

---

### Post by bradtacdc on 2009-04-26
> **tad1073 said:**
> My biggest worry/problem is location. The router will be in the kitchen on the first floor, my room is above the garage on the second floor. I am only about 20' away but the signal is traveling through walls floors and other wireless interference.

Well 20' isnt that much. But depending on how many walls are there you may have a problem. It also depends on what you want to use the router for. If your just going to be surfing the web, you should be fine. If your going to be playing Online games like COD4, Your signal may be a little less than perfect, but again you should be ok. 

Hope that helps :)

---

### Post by lamps06 on 2009-05-22
Curious if anyone has had any luck getting the USB port on their D-Link router to be seen in Ubuntu.  I have a DIR-825 with a USB port that I would love to network with Ubuntu.

---

### Post by Shvetaketu on 2009-08-12
Hi, I'm thinking of buying a Dlink Dir 685. Will a HP officejet 6300 connected to the shareport be accessible in ubuntu?

---

### Post by Dypek on 2009-08-13
I am running a 4-port USB hub, running a usb hdd, a printer, and an occasional usb stick successfully through Shareport (in Windows).  

I am planning on installing Ubuntu Server Edition and would also like to somehow get this app to work with the OS.  Would it be possible to somehow mount the router as a USB device, and access it's filesystems?

---

### Post by Dypek on 2009-08-13
> **Shvetaketu said:**
> Hi, I'm thinking of buying a Dlink Dir 685. Will a HP officejet 6300 connected to the shareport be accessible in ubuntu?


It should be fine, as long as the drivers for the printer are installed on your machine(s).

---

### Post by Shvetaketu on 2009-08-14
sorry dypek, but r u sure? I have looked in the forums and it seems ubuntu doesn't even see the shareport usb port and dlink don't have a linux driver for the port. and I do have the hp drivers for the printer installed in ubuntu 64 bit and it is working fine as a network printer with the wireless router I've got right now which is a speedstream 6520.

---

### Post by merciadriluca on 2009-10-09
Using DIR-635, same question, same issue. Even with Wine, Shareport does not want to install. Is there any alternative to this?

---

### Post by mcDavid on 2009-10-30
I just tried installing the shareport application with Wine, but no success... 

Still no other way to get this to work?

---

### Post by merciadriluca on 2009-10-30
I have still not found any solution to this problem. This is annoying and frustrating, as I thought that it would have worked in a straightforward way. I am even not able to contact D-Link in my country (Belgium), as their ``form is still unfinished, and is only here for design reasons''!

Which error do you encounter when you use wine for it? Did you succeed with the installation? I think that your problem is the installation, isn't it? I had the same problem, and I never solved it.

Did you contact D-Link? 

Thanks.

---

### Post by Saftkorg on 2010-02-04
I found a way to get to my external hdd which is connected to the router. It isn't pretty but here it goes. I start the shareport utility on my windows computer, then i login to browse the folder on the windows computer with my Ubuntu computer and then i can access the external hdd through it.

---

### Post by merciadriluca on 2010-02-05
> **Saftkorg said:**
> I found a way to get to my external hdd which is connected to the router. It isn't pretty but here it goes. I start the shareport utility on my windows computer, then i login to browse the folder on the windows computer with my Ubuntu computer and then i can access the external hdd through it.
It surely works, but it needs to use a Windows computer, and you might have no such computer. But thanks! ;)

---

### Post by Talar on 2010-02-09
I have a DIR-855, same problem here. I have a USB printer but there does not seem to be any solution for this :(

---

### Post by merciadriluca on 2010-02-09
The biggest problem is the lack of motivation coming from D-Link. Sources are closed, and thus nothing is possible without their consent.

---

### Post by IvarTJ on 2010-06-20
Yet another with the same problem. If I get the skills together I might use Wireshark or something to figure out how the SharePoint utility works, but if we get a new router it sure wont be D-Link unless they have fixed this ****.

---

### Post by cprofitt on 2010-06-20
I believe the new Netgear routers advert their Linux compatibility, but I have not as of yet heard of anyone using them with Linux.

---

### Post by merciadriluca on 2010-06-20
> **IvarTJ said:**
> Yet another with the same problem. If I get the skills together I might use Wireshark or something to figure out how the SharePoint utility works, but if we get a new router it sure wont be D-Link unless they have fixed this ****.
Well, I've got the skills, but I do not have the time! Please tell us about this once you'll have used wireshark or another derivative to find how this stuff works.

---

### Post by merciadriluca on 2010-06-26
Hi.

Good news, I had some spare time, and I used Wireshark under Windows, with SharePort connected/not connected, and I have the following kinds of results:
[LIST]
[*]router->computer: openwebnet (20005) > tr-rsrb-port [ACK] (1996)
[*]router->computer: openwebnet (20005) > tr-rsrb-port [PSH, ACK] (1996)
[*]computer->router: tr-rsrb-port (1996) > openwebnet [PSH, ACK] (20005)
[/LIST]

That is, D-Link's SharePort utility apparently uses the openwebnet protocol. 

We might consult [http://en.wikipedia.org/wiki/OpenWebNet#Syntax]("http://en.wikipedia.org/wiki/OpenWebNet#Syntax").

**Edit:** related linux.debian.user discussion: [http://groups.google.com/group/linux.debian.user/browse_thread/thread/4687fdad6d2f838e#]("http://groups.google.com/group/linux.debian.user/browse_thread/thread/4687fdad6d2f838e#").

---

### Post by ep42 on 2010-07-16
This would be cool.

---

### Post by ganewbie on 2010-08-06
Any luck guys?

---

### Post by merciadriluca on 2010-08-07
Has someone tried what I said, and checked for openwebnet?

---

### Post by ganewbie on 2010-08-07
Here is a link to their forum.
[http://www.myopen-legrandgroup.com/modules.php?name=Forums](http://www.myopen-legrandgroup.com/modules.php?name=Forums)
Done nothing after that.

---

### Post by merciadriluca on 2010-08-07
Nice. But I can't see what I could do.

---

### Post by ganewbie on 2010-08-09
Sorry but I do not what to ask, I just like to use the d-link share port?

---

### Post by merciadriluca on 2010-08-09
Well, I'd like too, but I have no solution under Linux. So, if you find one, please let me/us know.

---

### Post by omega0 on 2010-08-14
I have not tried it yet, but it may be possible to use[ DD-WRT]("http://www.dd-wrt.com/site/support/router-database") firmware on the router and share [USB]("http://www.dd-wrt.com/wiki/index.php/USB") devices to computers running any OS.  Using this firmware would probably void the manufacturer's warranty, unless it could be re-flashed with factory firmware.  If anyone has tried this with the DIR-825 please let us know how it worked as I have this router and would like to try it.

---

### Post by merciadriluca on 2010-08-15
Are you sure that this functionality would then be available?

---

### Post by David Mulligan on 2010-08-20
Is it possible to share a printer over shareport so that it is not exclusively owned by one computer at a time?

---

### Post by merciadriluca on 2010-08-20
If you've got a network printer, the idea is useless, evidently. But if this is an USB printer, maybe under Windows. For the rest, still waiting for a solution from D-Link...

---

### Post by Sam_amaya on 2010-10-29
A new release version of Shareport for Windows only has the ability to automatically release the printer after the print job is completed. PC SharePort Utility 3.0

Download from:  [www.dlink.com/products/?tab=3&pid=DIR-655&rev=DIR-655]("http://www.dlink.com/products/?tab=3&pid=DIR-655&rev=DIR-655")

---

### Post by merciadriluca on 2010-10-30
What's the link with Linux?

---

### Post by ganewbie on 2010-10-30
Does it hep us here?
What is your point?

---

### Post by djakku on 2010-11-18
Hey all, I'm new to the forums,
i'm a *not-so-proud* dlink-855 owner.
I thought the usb port was as cool as the linksys WAG320N wich I also have..
I just realised that there is no linux shareport support, yet.
Has anyone tried to run shareport on a virtualmarchine under linux?
That's actually what i'm gonna try since wine failed.
It's not the cleanest or simplest solution...

EDIT : Now that I think of it some might say it's off-topic since running windows on a VM under Linux is still meaning running windows :P

---

### Post by groovomata on 2010-12-30
I too have a D-Link DIR-825 router and would very much like to be able to access the USB storage device plugged into it. I'm looking at OpenWrt or DD-Wrt to replace the firmware, which should, hopefully, solve the problem. Has anyone heard anything about OpenWrt or DD-Wrt and which is better?
Regards,
Erik.

---

### Post by ganewbie on 2010-12-31
I am not brave enough to try that however if it works I will go for it for sure.
Please post your findings if you do not mind.

---

### Post by ganewbie on 2010-12-31
I am not brave enough to try that however if it works I will go for it for sure.
Please post your findings if you do not mind.

---

### Post by groovomata on 2011-01-01
I went through the websites for OpenWrt and DD-Wrt and I think I'm going to try OpenWrt. DD-Wrt's site seemed to be quite disorganized.
I'll be happy to report back.
Best,
Erik.

---

### Post by merciadriluca on 2011-01-01
Please tell us back. Thanks again.

---

### Post by groovomata on 2011-01-02
I installed OpenWrt for the D-Link DIR-825 and it was no problem. 
The page for it is here: 
> [http://wiki.openwrt.org/toh/d-link/dir-825](http://wiki.openwrt.org/toh/d-link/dir-825)
All I did was upload the firmware from:
> [http://downloads.openwrt.org/backfire/10.03.1-rc4/ar71xx/openwrt-ar71xx-dir-825-b1-squashfs-factory.bin](http://downloads.openwrt.org/backfire/10.03.1-rc4/ar71xx/openwrt-ar71xx-dir-825-b1-squashfs-factory.bin)
The web interface works no problem.
The only issue is that I cannot yet access the internet. When I figure it out I'll report back.
Regards,
Erik.

---

### Post by ganewbie on 2011-01-02
What kind of internet do you have? DSL or Cabel. I will search the forum for you to see if anybodu reported any issues for accessing the net through the router.
How  do you access the USB devices now? Is it through ftp address?

---

### Post by groovomata on 2011-01-02
I use cable for internet. I couldn't find an answer. However I will state that the OpenWrt seems to be for advanced users (of which I am not). 

I restored D-Link's firmware and then tried to flash DD-Wrt's firmware but had no luck. The DIR-825 kept stopping the flash process saying the file was incorrect. I think I may return it and try the Netgear WNDR3700. At least it appears to support Linux for usb storage, though has no option for a usb connected printer.

---

### Post by groovomata on 2011-01-02
> **ganewbie said:**
> What kind of internet do you have? DSL or Cabel. I will search the forum for you to see if anybodu reported any issues for accessing the net through the router.
How  do you access the USB devices now? Is it through ftp address?

If I knew how to access my usb storage via ftp, I'd try it.

---

### Post by groovomata on 2011-01-02
Alright, I finally got some success with the D-Link DIR-825 router. I didn't have any luck getting connected to the internet with OpenWrt. I also was unable to flash DD-Wrt onto my router as D-Link's firmware kept saying that I was trying to install a corrupted file. So I flashed OpenWrt onto it, and then flashed DD-Wrt onto that and voila, it worked. I got internet connection with my cable immediately and now I'm typing this wirelessly. 
To try this, follow the OpenWrt install instructions here:
> [http://wiki.openwrt.org/toh/d-link/dir-825](http://wiki.openwrt.org/toh/d-link/dir-825)
The DD-Wrt DIR-825 install page can be found here: 
> [http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-825](http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-825)

Now to try and get the usb hard drive feature working. I'll report back. Oh, btw, the DD-Wrt web interface for the router worked much much better for me than the OpenWrt.
Regards,
Erik.

---

### Post by ganewbie on 2011-01-02
Excellent news, you are the man. Waiting for your final word ;-)

---

### Post by jackmetal on 2011-01-03
:lolflag: - well, I decided to move my old router to DD-Wrt to see if I could help others with setting up the USB/SharePort connectivity and found that it's not supported (D-Link DIR-625).  

Now I need to figure out what the best 'consumer' router is that actually supports Linux with USB connectivity.  :guitar:

---

### Post by groovomata on 2011-01-03
> **jackmetal said:**
> :lolflag: - well, I decided to move my old router to DD-Wrt to see if I could help others with setting up the USB/SharePort connectivity and found that it's not supported (D-Link DIR-625).  

Now I need to figure out what the best 'consumer' router is that actually supports Linux with USB connectivity.  :guitar:

Jackmetal, that's a very interesting question. I definitely wouldn't have bought the D-Link if I knew that it didn't support Linux for usb storage. So much for a company that profits by using GPL'd Linux for their devices, are probably using some sort of samba to interface with Windows computers, yet can't be bothered to build native Linux support into their products. I'm sure many people would be very interested in a company that does. I looked at the Netgear WNDR3700. It, apparently, supports ext3 for usb storage, however they don't support usb printing.

---

### Post by jackmetal on 2011-01-03
> **groovomata said:**
> Jackmetal, that's a very interesting question. I definitely wouldn't have bought the D-Link if I knew that it didn't support Linux for usb storage. So much for a company that profits by using GPL'd Linux for their devices, are probably using some sort of samba to interface with Windows computers, yet can't be bothered to build native Linux support into their products. I'm sure many people would be very interested in a company that does. I looked at the Netgear WNDR3700. It, apparently, supports ext3 for usb storage, however they don't support usb printing.


Yep!  Unfortunately there are a lot of companies that profit from Linux and yet they don't support it.  It's a shame!  

I'm going to do some research and see what I come up with.  I want a really good router - at the very least something as good or better than the D-Link DIR-855, but one that supports Linux.  I'm not sure what kind of luck I'll have, but I'm going to at least try. :-)

Update:
Well, thus far not so much luck with typical "consumer" routers, although the Netgear N600 (WNDR3700) looks pretty good!  I didn't think about it at the time, but I don't believe any of them would work for me, as I use encryption on ALL of my drives (internal and external, with either TrueCrypt or Linux FS Encryption).  :-(  So, it looks like I'll stick with a Linux Based Firewall distro instead of a typical router (trying to decide between ClearOS and Zentyal since they can do just about everything I could imagine wanting in a firewall/gateway type setup giving more than something like smoothwall or pfsense).

---

### Post by merciadriluca on 2011-01-04
Do you have any news concerning the USB capabilities with your new firmware?

---

### Post by groovomata on 2011-01-04
> **merciadriluca said:**
> Do you have any news concerning the USB capabilities with your new firmware?

When I get a little time, I'm going to work on getting a hard drive connected via usb to the router accessible through the network. 
For more information check out the following:

Here is the DD-Wrt D-Link DIR-825 page:
[http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-825](http://www.dd-wrt.com/wiki/index.php/D-Link_DIR-825)

Here is the DD-Wrt main page: 
[http://www.dd-wrt.com/site/index](http://www.dd-wrt.com/site/index)

Here is the main page of the DD-Wrt wiki:
[http://www.dd-wrt.com/wiki/index.php/Main_Page](http://www.dd-wrt.com/wiki/index.php/Main_Page)

Here is the tutorial page:
[http://www.dd-wrt.com/wiki/index.php/Tutorials](http://www.dd-wrt.com/wiki/index.php/Tutorials)

---

### Post by merciadriluca on 2011-01-05
Thanks for the pointers.

---

### Post by groovomata on 2011-01-23
Well Folks, I did manage to connect my external drive to my D-Link DIR-825 router and mount it. In order to get it to work, I had to format the drive according to the instructions here: [HTML]http://www.dd-wrt.com/wiki/index.php/How_to_-_Format_and_Partition_External_Storage_Device[/HTML] I simply used GParted to do the formatting. I then followed the instructions on this page [HTML]http://www.dd-wrt.com/wiki/index.php/USB_storage#General_intro_to_the_dd-wrt_folder_structure[/HTML]

I can access my drive using FTP, however I'm having issues actually transferring files as larger files don't seem to complete properly. That issue I now have to troubleshoot. At any rate I'm getting closer to a solution that works.

---

### Post by merciadriluca on 2011-01-24
Nice to hear this! Continue to tell us how this is going on: this will surely become the method (at least for now) to work with these routers and the HDDs...

---

### Post by groovomata on 2011-02-12
Okay folks, here's the deal so far: 
I was having issues copying files to my network drive, until I figured out that I was mounted onto the wrong partition (the 'Optware' partition I made was too small to fit the file I was transferring over). Anyways I found another howto in Lifehacker: [http://lifehacker.com/#!5756233/get-more-out-of-your-dd+wrt-router-with-an-external-drive]("http://lifehacker.com/#!5756233/get-more-out-of-your-dd+wrt-router-with-an-external-drive"). These instructions seem more straight forward. I didn't worry about anything beyond actually mounting the drive. Anyways now I can read and write to it and copy files back and forth. Right now I'm actually performing a backup of my system and so far it seems to be happening without any problems. 

One question though, when I copy a larger file to my network drive, for instance a video. I can see that it is exactly the same byte size as the original. However, if I try to play it in vlc or movie player it won't play. Other files though, such as documents seem to open up with no problems. Connectivity shouldn't be an issue as I'm using an ethernet cable. So as a backup storage device it seems to be working, however I'd really rather be able to play some files (i.e. videos) from my network drive to free up space on my laptop. Does anyone have any ideas?

---

### Post by dmizer on 2011-02-12
Try mounting the ftp folder in /etc/fstab as that may give you better performance and allow you to watch video.

[http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html](http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html)

---

### Post by groovomata on 2011-02-13
> **dmizer said:**
> Try mounting the ftp folder in /etc/fstab as that may give you better performance and allow you to watch video.

[http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html](http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html)
Thank you dmizer! 
I installed curlftpfs, but I seem to be having some problems mounting the ftp in /etc/fstab. The instructions call for > curlftpfs#ftpUsername:ftpPassword@ftp://ftpUrl /localDirectory fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto,utf8  0   1 to be added to /etc/fstab. I put it in as:
> curlftpfs#my_ftp_username:my_ftp_password@ftp://192.168.1.1         /localDirectory fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto,utf8  0   1
But I get this result:
Error connecting to ftp: Couldn't resolve host 'ftp:'
Any ideas what I'm doing wrong?

---

### Post by groovomata on 2011-02-14
Hello All, have a router with a network drive attached, which I currently use for backups. I've connected to it via ftp with nautilus and I can browse my files. I can open normal documents no problem, however, I've noticed that I when I try to play a video it won't play. Neither vlc or movie player can play it. Someone suggested that I mount the ftp folder to a local directory as per this tutorial in Ubuntu Geek: [HTML]http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html[/HTML]
Unfortunately I can't seem to make it work. 
I installed curlftpfs, but I seem to be having some problems mounting the ftp in /etc/fstab. The instructions call for:
> curlftpfs#ftpUsername:ftpPassword@ftp://ftpUrl /localDirectory fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec, auto,utf8 0 1
to be added to /etc/fstab. I put it in as:
> curlftpfs#my_ftp_username:my_ftp_password@ftp://192.168.1.1 /localDirectory fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec, auto,utf8 0 1
But I get this result:
> Error connecting to ftp: Couldn't resolve host 'ftp:'
Any ideas what I'm doing wrong?

---

### Post by groovomata on 2011-02-15
Alright, I think I've got it mostly figured it out. From this page: [http://www.backports.ubuntuforums.org/showthread.php?t=1036636]("http://www.backports.ubuntuforums.org/showthread.php?t=1036636")
I put this into /etc/fstab:
> curlftpfs#ftp_username:ftp_password@ftp_server.com /home/erik/Network_Drive fuse rw,allow_other,auto,user,_netdev 0 0
And then entered: sudo mount -a
And it mounted and I was able to stream a video from my network drive to my computer.

However, my computer did tell me something. Does anyone know what this means and what I should do about it?
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

---

### Post by groovomata on 2011-02-15
Alright, I think I've got it mostly figured it out. From this page: [http://www.backports.ubuntuforums.org/showthread.php?t=1036636](http://www.backports.ubuntuforums.org/showthread.php?t=1036636)
I put into /etc/fstab this:
```
curlftpfs#ftp_username:ftp_password@ftp_server.com /home/erik/Network_Drive fuse rw,allow_other,auto,user,_netdev 0 0
```
And then entered: sudo mount -a
And it mounted and I was able to stream a video from my network drive to my computer.

However, my computer did tell me something. Does anyone know what this means and what I should do about it?
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

---

### Post by groovomata on 2011-02-15
I just completed a reboot and my network drive has remounted and I can still play or stream video files from my network drive onto my computer. Success! 
If anyone can tell more about:
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
I would appreciate it.
Cheers,
Erik.

---

### Post by groovomata on 2011-02-15
I just completed a reboot and my network drive has remounted and I can still play or stream video files from my network drive onto my computer. Success! 
If anyone can tell more about:
> fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option
I would appreciate it.
Cheers,
Erik.

---

### Post by dmizer on 2011-02-16
Not empty means that there is a file in the /home/eric/Network_Drive folder. You should unmount the drive and check for any file in that directory. You should never mount an external drive in a folder that has files in it.

---

### Post by groovomata on 2011-02-16
Okay, this threat is not yet solved. I am now unable to transfer files to the network drive using Nautilus via my mounted network drive. Anytime I try, the transfer stops at 3.1 megs and stops. I can, though, use Filezilla and ftp files over, so my connection is not flaky. As well, I still can play videos on my network drive, which I could not do before. 
Does anyone know what I'm doing wrong?

---

### Post by groovomata on 2011-02-16
Thank you dmizer, I'll check that out further. 
I commented out this line in /etc/fstab
```
curlftpfs#username:password@192.168.1.1 /home/erik/Network_Drive fuse rw,allow_other,auto,user,_netdev 0 0
```rebooted my machine manually connected nautilus to my network drive and now I can transfer large files again no problem. However, I can no longer play the videos on my network drive. So it's a problem with that line in fstab. Does anyone have any ideas?
Thank you,
Erik.
(please note, the smiley face is actually a colon and a 'p' and not a smiley face)

---

### Post by groovomata on 2011-02-16
When I add this line to /etc/fstab
```
curlftpfs#username:password@192.168.1.1 /home/erik/Network_Drive fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto,utf8  0   1
```I get this error:
> Error connecting to ftp: QUOT command failed with 500
Does anyone know how to resolve this?

(please note, the smiley face is actually a colon and a 'p' and not a smiley face)

---

### Post by dmizer on 2011-02-16
> **groovomata said:**
> (please note, the smiley face is actually a colon and a 'p' and not a smiley face)

This does not happen if you use code [code] tags instead of quote [quote] tags. Also, quote tags force line feeds, so quote tags insert arbitrary spaces to make the line fit the forum formatting. All of that (including the smiley) is fixed if you use a code tag instead of a quote tag :)

Not sure what to say about your new error though ...

---

### Post by groovomata on 2011-02-17
Thank you for the posting tips...
I emailed Robson Braga Araujo (one of the CurlFtpFS project administrators) about my error and, he said:
> It seems that your server does not support the utf8 option. Can you try removing it?So I did, resulting in this:
```
curlftpfs#username:password@192.168.1.1 /home/erik/Network_Drive fuse rw,uid=1000,umask=0777,user,suid,allow_other,exec,auto  0   1
```
And it worked! I can play videos on my network drive, however I still can't successfully copy over a large file. I asked Robson about that but he hasn't gotten back to me yet. 
Regards,
Erik.

---

### Post by dhughes on 2011-05-15
I should have done my homework I too am stuck with this router being fooled by the "Open Source" sticker and the Linux Tux logo on the CD case. That's bordering on fraud, close but not quite.

 Other than the USB not working with storage or printer it's a good router but I specifically bought it due to the open source support and the USB port.

 I may just wipe it and put Tomato on it if that supported or DD-WRT.

---

### Post by erictlara on 2012-03-01
I'll ask you guys who have a lot of experience making work the USB port in a D-Link router. My case is the following: I want to share a printer in my network that it's connected to a DIR-655 router. Of course, like many of you I don't want to depend on a PC to print. Even more, I want to be able to airprint from iPad. By reading at your posts, I figure out that installing the DD-Wrt firmware is one step to go. Any suggestions on how to share a printer from there? How about registering it with Bonjour so it can be located by the iPad? Thanks a lot.

---

### Post by gamez on 2012-06-13
If your target is to share a printer (and not an external harddisk as often discussed above) through the USB-port of a D-Link router, then you may try [this procedure]("http://ubuntuforums.org/showthread.php?t=2002840").

Best regards,

g.

---

