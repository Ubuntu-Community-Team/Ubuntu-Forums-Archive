---
title: "Myth TV"
date: 2010-03-17
forum: Mythbuntu
---

### Post by archeryrob on 2010-03-17
Are Mythbuntu and MythTV the same? I can't get a clear picture. Stuff on the net says MythTV and show Mythbuntu. Are they the same? Or is mythTV a user friendly front to mythbuntu?

Also, I am familar with Ubuntu and having to use Samba for file share and such with windows. If I use Mythbuntu to make a DVR server can the content be accessed from a windows laptop? I have an extra laptop I can configure with Mythbuntu or Ubuuntu and clear win xp off of it. But all other house users have Win7 computers that they use VLC player right now to load and play movies/video from the file server. 

Also did a search on capture cards and did not get much on hits. What system specs have any of you all used?

---

### Post by SiHa on 2010-03-17
Mythbunu is basically Ubuntu prepackaged with MythTV and with most of extra productivity applications removed. Actually, I think it's more accurately Xubuntu, as it uses the XFCE desktop.

So you can install Mythbuntu, or you can install Ubuntu then install MythTV on top. Personally, I find that a Mythbuntu install is the easiest way to go, and I've done both.

Another advantage to the Mythbuntu approach is in answer to your second question.
Not sure if this holds true for earlier versions, but certainly since 9.10, a default install of Mythbuntu enables Samba and NFS shares of the four main Mythbuntu media directories (/var/lib/mythtv/recordings, videos, music, pictures).
I was quite surprised when I upgraded to 9.10 (a fresh install), turned on my Windows box and found four network drives just sitting there waiting to be used. All I had to do was edit /etc/smb.conf to enable proper write access from the Windows machine (except for recordings, for obvious reasons).

For capture cards, there's quite a comprehensive list of Linux-Supported carts at [[COLOR="Blue"]_LinuxTV.org_[/COLOR]](http://linuxtv.org/wiki/index.php/Main_Page). 
Speaking for myself, for DVB-T/S, I use Hauppauge Nova-T 500 (Dual), Nova-T (Single) and Nova-S (Single), all PCI. The Nova-T 500 needs a few tweaks to enable the on-board amplifier and the Remote can be a bit fiddly I understand - I use a homebrew receiver myself.
The above are all MPEG capture cards - they capture the MPEG stream direct, so there is no encoding, hence little system overhead.

---

### Post by archeryrob on 2010-03-17
I went to the hauppauge USA website and everything now shows a WIN before the product name and all specs spell out "Microsoft® Windows® 7, Windows Vista Premium or Ultimate with Media  Center." Not seeing Linux as an option.

I don't see the NOVA's on their site and more, only the WINTV stuff.

---

### Post by archeryrob on 2010-03-17
This laptop has a wireless card and the route is WPA personal. I tried setting it up and it will not connect. How do you check drivers and such?

---

### Post by klc5555 on 2010-03-17
> **archeryrob said:**
> I went to the hauppauge USA website and everything now shows a WIN before the product name and all specs spell out "Microsoft® Windows® 7, Windows Vista Premium or Ultimate with Media  Center." Not seeing Linux as an option.

I don't see the NOVA's on their site and more, only the WINTV stuff.

Hauppauge doesn't support Linux themselves --it's the 3rd-party developers that do that. So for information on supported cards, you need to go to the link SiHa gave you, and to the mythtv wiki: [http://www.mythtv.org/wiki/Category:Video_capture_cards](http://www.mythtv.org/wiki/Category:Video_capture_cards) Though there are an awful lot of cards that work just fine on Linux (as you'll see from the docs) the only capture-card company that supports Linux openly, in preference to Windows, and out-of-the box is PcHDTV and their HD-5500

When your mythtv server is configured correctly, you will have several options for playing server-recorded content on a Windows laptop. You can direct stream or download to the laptop using mythweb, and play the content on the laptop using your favorite player. You can use a freeware Windows frontend-player like the mythtv player for windows. You can try to configure a remote frontend using the windows port of mythtv itself (probably the least satisfactory option). And these would be just some options not requiring Samba.

But mythtv is not particularly beginner-transparent and has a significant learning curve, even with a hand-holding distro like mythbuntu. So you'll need to do some research and hit the docs on the mythtv wiki pages early and often, starting with the manual at [http://www.mythtv.org/wiki/User_Manual:Index](http://www.mythtv.org/wiki/User_Manual:Index)

Good luck!

---

### Post by David Grigor on 2010-03-17
When I first started mythtv just over a year ago( 8.10 ), one of the frustrating parts when troubleshooting was that you could find resolutions via google. Some may use ubuntu type tools ( Mostly related to sound ) that may not be present when using the mythbuntu. That added some level of frustration when your not able to follow past solutions when you don't really know what your missing or how to get it.  

With each version of mythbuntu you keep hoping the troubleshooting gets less and less necessary.

---

### Post by azmyth on 2010-03-17
> **archeryrob said:**
> This laptop has a wireless card and the route is WPA personal. I tried setting it up and it will not connect. How do you check drivers and such?
The driver is based on the chipset inside the card. I assume it's usb so you can do a lsusb and it will tell the chipset usually and it will give you an ID number for example 0ace:1215 which you can drop into google to find more info.

---

### Post by klc5555 on 2010-03-17
> **azmyth said:**
> The driver is based on the chipset inside the card. I assume it's usb so you can do a lsusb and it will tell the chipset usually and it will give you an ID number for example 0ace:1215 which you can drop into google to find more info.

If the Wifi is built-in, then google something along the lines of your laptop model, wireless, and linux (or ubuntu), and generally you'll find the information you need. Usually it will  be a simple matter of loading the correct module (or set of modules) with modprobe (since often ubuntu can't find the right one automatically). When it works by hand, you then normally put the correct loading command(s) in the /etc/rc.local file to load at every boot. 

If the wireless is an addon card, then google the precise card model and linux (or ubuntu). The ubuntu laptop forum will be the place to get more precise answers to enabling wireless networking on a laptop (a bit of a mess in ubuntu) rather than the mythbuntu forum.

If the machine has loaded some driver for the interface, it should be discernable from the outputs of lspci (which should list the networking chip) and lsmod (which will show the loaded drivers) commands. If a networking interface has been enabled (even if misconfigured and therefore unusable) the interface should appear in addition to that for local host (lo) in the output of the ifconfig command. Then it will become a matter of configuration to connect correctly with your network.

---

### Post by archeryrob on 2010-03-18
Still having trouble with the wireless. It's a dell inspiron 1501 with a 1390 internal wireless card. I can figure this out.

A few things I do not understand. The first is Mythbuntu is not taking well to the hibernate when they laptop is closed. Does it have hibernate? When I open it back up the fan runs and it sounds like it starting up, but then it just black screens, forever. Then it's pull the battery and restart. Power management settings where in "suspend" and I changed them to "hybernate". This time I closed it and 5 minutes later it's like I pulled the battery, but it reloads with the little TV and then to a black screen now and sits dead again. Loads to a recovery screen and then load Mythbuntu fine. It's not taking the closing of the lid very well.

Also, I do not have a back end, but I do have a windows network drive on another machine with movies, videos and music stored on it until I build a back end server. I do not see Samba and you need it to use a windows machine, right? I also do not software addon manager like I had when I had Ubuntu 9.1 Karmic Koala installed on another machine where it accessed and download Samba from the server. Would I be better using Karmic Koala and laying MythTV over it, instead of the prepackaged Mythbuntu?

---

### Post by archeryrob on 2010-03-18
Also, do they make DDR2 flash RAM? Just wondering why I need a hard drive if I build a front end? If I made a new small front end machine, I could load all files to Flash ram and it would power up faster and be ready to go.

---

### Post by SiHa on 2010-03-18
Re: Hibernation and Suspend.
One of the things Ubuntu still seems to struggle with is resuming from one of the above. Mostly, the issues are to do with the video BIOS not being initialised correctly on restart.
Not sure what routine the is called when the lid is closed, but you might want to experiment with the **pm-suspend** function. From a terminal type:```
sudo pm-suspend
```This should suspend the lappy. Now try and restart. If you still have issues you can try calling pm-suspend with the various quirks that are available, see the manpages [[COLOR="Blue"]_here_[/COLOR]](http://www.manpages.spotlynx.com/gnu_linux/man/pm-suspend.8) for a full list.
If you can get it to work like this, you could modify the frontend settings for shutdown to call pm-suspend instead.

Re: DDR & Flash.
No. They are completely different animals. However you do have a couple of different options. You could use a USB flash drive and voot from that, or a CompactFlash IDE/sata adapter. Or you can netboot from an image on the backend.
These options will enabke you to get rid of a HDD that's whirring away, but won't AFAIK give you much in the way of a startup boost. If you can get suspend to work, that's the best way to go. My old machine used to resume in about 6s, I haven't bothered to set it up on the new frontend yet.

---

### Post by archeryrob on 2010-03-18
Thanks, I was not thinking for the lap top but for a sidways DVR type front end. You can turn it off and it would just resume as all would be in memory, because there is nothing to load. I was looking to play with it.

Is Koolu boxes still around? I could not find their site and I wondered if they closed up.

---

### Post by archeryrob on 2010-03-18
No one replyied as to why I can not find Samba or see out on the network when I hooked up the LAN cable. I want to play with this as a front end and see if I can load videos from my windows computer with shared hard drive. I could with Ubuntu 9.10 so i am installing that on the laptop.

MythTV seems to be missing some of the things like Samba. I got into this as Win Media center will not play torrents as VLC will and the later seems to be bundled with Linux nicely.

So after 9.10 karmic Koala installs I might setup samba and install MythTV and see if it shares better, or plays with the windows network better. :D

---

### Post by SiHa on 2010-03-18
Mythbuntu (As opposed to Ubuntu + MythTV) installs Samba and by default shares the default MythTV media directories. You should need to do nothing else to be able to see them from Windows(see attached picture).

---

### Post by archeryrob on 2010-03-18
I want to see the windows files from the MythTV machine, that is what I am not seeing. I want to connect the Mythbuntu machine to the TV and load movie to watch for now off the windows shared drive. Then later connect cable to a capture card in a DVR back end later.

Right now I can not see how to see the windows drive from the MythTV computer.

---

### Post by SiHa on 2010-03-18
Ah I see. That's out of my realm (and I think a little more complicated).

---

### Post by timconradinc on 2010-03-18
[Here's a guide on mounting windows shares from Linux]("http://webscript.princeton.edu/%7Epug/faqwiki/index.php?title=Using_SAMBA/CIFS_to_access_Windows_Shares").

The most important thing when looking at these types of guides is to make sure you're using CIFS and not SMB/SMBFS. The SMB protocol has a limitation on the size of files that can be used with it, which is 2GB. It's actually a limitation in the protocol, some counter is 32 bit only, which means there's a 2 GB max file size.

Mounting remote file systems like this in Linux isn't to be taken lightly. You're likely to have some weirdness if the file sever gets rebooted without the share being unmounted. It doesn't always happen, though.

I'm not sure why/how your TV shares files via SMB, but to automatically copy files in either direction, you might want to look at the [rsync utility]("http://everythinglinux.org/rsync/"). I use it to back up things on my system. You could, also, i suppose, add the SMB share as another movie directory so you're not actually copying the movie over. This makes quite a few assumptions, though, mostly that you know how to navigate that path and the files are named something that makes sense.

---

### Post by archeryrob on 2010-03-18
The windows this is not meant to be a permanent things, just what I am doing now as I "learn" and play with the stuff I have. I might always have windows computers for work and office applications. 

The plan is bring in cable or satelitte and distribute per a dedicated switch. Have not figured managed or unmanaged yet. I mean is TV on MythTV a cast type application or a multi-cast operation broadcasting every channel? Kind of setting up a VLan for MythTV for all rooms and runing a CAT6 cable to each room and ditch the coax. The house is all laptops and Ipods fo wireless for computers and the pods and wired for TV and AV.

---

