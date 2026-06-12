---
title: "Does Netgear WNA1100 USB Adapter work in Ubuntu"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by lund on 2010-04-05
Hi,

I just bought the following new wireless USB adapter:

Netgear Wireless-N 150 USB Adapter WNA1100

I'm currently running a dual-boot with Windows Vista & Ubuntu 9.04 (64 bit).  Of course the adapter came with Windows drivers so that was easy. However, I have not seen any posts for getting this adapter to work in Ubuntu.

If anyone has tried (and succeeded) then please let me know how it was done. I have to move my computer and do not have access to a physical network connection anymore. 

My options are to get wireless working on Ubuntu or just stop using the OS. 

Please help!

Thanks!

---

### Post by papawapa on 2010-05-16
Hello,

I have been able to get my Netgear WNA1100 to work under Ubuntu 10.04 32-bit desktop.  I don't know if anyone still needs a guide for this, but essentially I installed ndiswrapper via synaptic and used the .inf from an xp install.  I extracted the .inf and other setup files using a VirtualBox Windows Xp install.  

As a side note I had previously tried this approach using a .inf from a Win 7 64-bit install in linux mint 8.0 and had no success.

Once I installed with ndiswrapper I was able to see my available wireless access points in NetworkManager Applet.  Also of note my Access Point is only through a linksys wrtg54 (G) router.  Considering the proximity of my router (~10 ft with a wall) my signal seems a bit weaker than I'd expect (~60%).  I also cannot assess the performance of (N) speeds and connectivity.

---

### Post by wwwookie on 2010-05-16
I use a netgear WPN111 at my studio - not same as yours but could work...ndisgtk is available in the synaptic and is very easy to use. When ndisgtk asks you for the .inf file it needs to come with another file, .sys or something, in the same directory. I'm not sure of the exact name as I'm not at that computer at the moment. If it's not clear which one you need, just copy the entire folder C:\Program_files\NETGEAR\WNA110\Driver\ from windows to your ubuntu partition, there should only be about 45 or 5 files in it.

---

### Post by IndyGunFreak on 2010-05-16
Were you using arusb_8p.inf?  If not, could you provide the file name of the .inf file you were using.. the above doesn't work.  What files did you point ndiswrapper at?

IGF

---

### Post by Slave2Metal on 2010-05-18
I directed ndiswrapper to arusb_xp.inf and sys file and no joy.  Installs the driver with no error, but not recognizing wireless.

---

### Post by Lostboi45 on 2010-07-11
> **Slave2Metal said:**
> I directed ndiswrapper to arusb_xp.inf and sys file and no joy.  Installs the driver with no error, but not recognizing wireless.


I used the file netathuw.inf and it works perfectly!

---

### Post by jbatista on 2010-08-06
> **Lostboi45 said:**
> I used the file netathuw.inf and it works perfectly!

You did that on a 32-bit or on a 64-bit kernel?
If you do
```
uname -m
```
on a gnome-terminal console, do you get "x86_64" or "i386" ?

Because it seems that Netgear bundles its driver only for 32-bit Windows, and ndiswrapper on a 64-bit Linux cowardly ;) refuses to load that driver!

---

### Post by ravensqu on 2010-08-20
I installed the netathuw.inf as well on lucid x32. No error messages and when i run

```
ndiswrapper -l
```

netathuw shows up in the list of installed drivers, but I cannot find any wireless networks in the Network Manager Applet.

---

### Post by SantiSolari on 2010-08-20
SAME PROBLEM HERE!! i need help, i've installed ndiswrapper and installed the netathuw.inf file, with the sys file athuw.sys in the same folder when executing "ndiswrapper -i netathuw.inf". when i executed that it showed me no errors and when i put "ndiswrapper -l" it says that the driver netathuw is installed and the device is present. when i run "lsusb" it shows the device "NETGEAR, Inc" but the device's ligth doesn't turn on and the wirelless network is not visible.

but then i used "modprobe ndiswrapper" and the device started blinking, like 4 or five times then stops, for like 30 or 40 secs and it starts blinking again, 4 or 5 times and stops again, and it keeps doing that over and over again but nothing happens!

Please somebody help

---

### Post by SantiSolari on 2010-08-25
Sorry for double posting, but that last one was 5 days ago and this, i think, is very important for anyone who may need it.

what i did in my last post DID WORK, but i didn't check the available wireless networks after running

```
sudo modprobe ndiswrapper
```

and they were there!! ready to be selected! and i got my connection with no more problems! so the answer for the question of this thread is YES, The NETGEAR WNA1100 USB WIRELESS ADAPTER does work with ubuntu (with the mentioned driver). but i got another problem later. The problem is described perfectly on this thread first post, and it has its solution! 

[http://ubuntuforums.org/showthread.php?t=1145788](http://ubuntuforums.org/showthread.php?t=1145788)

well if someone out there still has problems with this adapter feel free to post, but i think this is solved!.

---

### Post by Saeger on 2010-09-12
Can you tell us, step by step exactly what you did to get the Netgear WNA 1100 to work?  Myself and countless others have followed similar steps only to find that Ndiswrapper believes that the driver is working, yet Ubuntu sees no wireless networks.

Thank you in advance from both myself and the entire Ubuntu Community.

---

### Post by rb0 on 2010-09-28
I am trying to install my WNA1100 card and it isn't working yet.
I followed all the steps listed so far, but my inf is named netathur.inf - not netathuw.inf

It installed correctly via ndisgtk - and it says hardware is present.
I did modprobe ndiswrapper, and nothing happened/changed, except for the warning about config files - so I assume it worked.
ndiswrapper -l prints out my driver and says the correct device is present (0846:9030)
lsusb shows on Bus 001 Device 004 I have (0846:9030 NetGear. Inc.)

But this is where I am stuck at.
Is there a command I have to use to activate the driver/device?

I've used ubuntu in the past, but it's been a couple years.
The laptop I have it on is 6 or 7 years old and I wiped hard drive to install ubuntu.

---

### Post by rb0 on 2010-09-28
OK, I looked in the stickied comprehensive ndiswrapper troubleshooting thread, and I got up to Section 4.

Apparently ndiswrapper is failing to import something:

[24.094242 ndiswrapper (import:242) unknown symbol: ntoskrnl.exe: 'RtlIsServicePackVersionInstalled'

There are several of these (I can print them all out of necessary), going through to NDIS.SYS and such.

Ends with failing the load_sys_files:206 part.

Googling around, it looks like I may be able to fix it with building ndiswrapper from source or something? However this computer has no internet access at all at the moment, so does anyone know a specific version or file to download so I can extract from a usb drive?

---

### Post by mad hamish on 2010-09-30
Hi, an alternative approach which worked for me was to install the **ath9k_htc (Atheros Linux Driver)**
[http://ubuntuforums.org/showthread.php?p=9909230#post9909230](http://ubuntuforums.org/showthread.php?p=9909230#post9909230)

---

### Post by walt.smith1960 on 2010-10-20
Using Vagrale13's .deb file worked perfectly for me in Lucid.  It will not work in Maverick because theoretically Maverick has kernel support for Ath9k adapters and the .deb package refuses to install.  I say theoretically because my Maverick install did not recognize the Netgear WNA1100.  I downloaded NDIS-GTK via synaptic and that worked perfectly. I'm not certain the throughput is quite as good using the NDIS solution but it did work for me, no tinkering required.  I copied the /driver folder containing the .inf & .sys files from an XP install.

Edit after 1 week.  

Vagrale13's .deb file is revised and is supposed to work with Maverick Meerkat now.  I haven't tried it. I was having some issues with the WNA1100 not wanting to resume after suspending. Apparently NetworkManager is at fault and there is a fix but the fix hasn't found its way to Ubuntu yet.  Here's what I found and typed. I've done 15-20 suspend resume cycles and so far it has always resumed properly. Obviously, do not type the #, just sudo then the commands.

#sudo service network-manager stop
#sudo rm /var/lib/NetworkManager/NetworkManager.state
#sudo service network-manager start

I just checked that path in Nautilus and the NetworkManager.state file exists so it may be recreated upon reboot or something.  Anyway, so far my suspend/resume appears to be working as advertised.  I gather those 3 lines fix other wireless adapters with suspend/resume problems, not just Netgear.  I guess this is why switching to WiCD also seems to fix the suspend/resume issue.

---

### Post by Messier 66 on 2010-10-22
Hi community. 
Follow this tutorial if you want to see the wna1100 blue led blinking and working. It even works in BackTrack 4!
[http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100](http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100)

---

### Post by devilcode on 2010-12-19
Hi All,

I have been running through the forum/net trying to solve this issue of getting the WNA1100 Netgear USB WiFi dongle working on Ubuntu an easy way and so I hope the following helps.

**Step 1:**
Download and install the following in this order:

[LIST]
[*]**ndiswrapper-common**
[*]**ndiswrapper-utils**
[*]**ndisgtk**
[/LIST]
In attachment  ([ndisfiles.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178899&stc=1&d=1292795499")     (132.1 KB) ).



**Step 2:**

Once you have installed the above in order of Step 1 you need to get a copy of the XP driver for the WNA1100 USB WIFI card. If you don't have it you can download it from the attachment to this post: [WinXP2000.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178900&stc=1&d=1292795955")     (537.3 KB) 

to uncompress the files either right click on it and Extract Here... or via command line type  > *tar* xvf filename.*tar.gz * so for the files listed  would be:

[LIST]
[*]**tar xvf ndisfiles.tar.gz**
[*]**tar xvf WinXP2000.tar.gz**
[/LIST]

**Step 3:**

Now you need to install the XP driver to get the USB WiFi to work. So via command line in the Terminal. 
% **gksudo**
then type '**ndisgtk**' under run and make sure its as user root. Then click ok.
it will ask you to put in your su password and press ok.

The a GUI will pop up with Wireless Network Diver. Click the '**Install New Driver**' and select **netathuw.inf **

Then plug in the the WNA1100 USB WIFI and all should be good.

+++++++++++++++++++++++++++++++++++
Im new ish to linux so feel free to comment or correct.

---

### Post by walt.smith1960 on 2010-12-19
NdisWrapper does work.  I found what seemed like a little better performance using the installer, however.

[http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/) 

The only downside to the installer is that if you have any other Wireless connections, they may be disabled.  I'm not sure about wired connections.  But the installer itself worked quite reliably on the 2 machines i tried it on.

The good news is that Natty Narwahl (11.04) looks like it will support the Netgear WNA1100 and RealTek 8192SU (TrendNet TEW-649UB) natively.  I tried both adapters on a live session and both came alive and connected on WPA2 networks.

---

### Post by Fizzasist on 2010-12-26
Thank you Devilcode!! Your write-up worked perfectly! Can't thank you enough.....was banging my head against the wall for a while on this one!

You are a gentleman and a scholar! :D

---

### Post by Huffers on 2011-01-08
I recommend ath9k_htc ( [http://sourceforge.net/projects/ath9k-htc/](http://sourceforge.net/projects/ath9k-htc/) ) - it worked perfectly with my Netgear N150 WNA1100.

Devilcode's method also worked... but Devilcode's method wasn't perfect because I could only connect to networks without security, or with WEP or Dynamic WEP security (not WPA2-PSK which I use).

---

### Post by diviner0516 on 2011-02-07
Thanks for the great work everybody!


Observation:
I couldn't get this to work using the .sys file from my own windows install (Vista not XP), but the files posted above worked perfectly.

---

### Post by egswy on 2011-02-10
Hello,
I hate to be a complete idiot:confused:, but I have gone through several iterations trying to get my computer to recognize the Netgear WNA1100 USB Adaptor on my computer with no luck.  

I first downloaded Steves document on with no luck.  First went through it his way, 
[http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100](http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100), and got everything he indicated but no blinking light on my usb adapter.  

I then tried the driver loaded in maverick, and got what Bristol_Green had, but no blinking light.  

I then tried it this way, no luck.  I'm pretty much at a stand-still.  I've also gone through 2 versions of Ubuntu, lucid and maverick.  Still no luck.  

Several things to note.  
1). If I do an 'ifconfig', it does not show wlan0.   Just the original ports of eth0 and lo.  

2). If I do a ndiswrapper -l, it shows shows the netathuw driver installed with the device number of the netgear device, 0846:9030.  

What in the world am I doing wrong?   I hate to say, I may have to punt and go back to Windows.  Transferring files to a pen drive on one computer and then porting to my linux box gets old.  Any help would be appreciated.
Ed

---

### Post by TubbyBeef on 2011-03-09
devilcode's solution from December 19th, 2010                           worked for me on Ubuntu Desktop 10.10.  

One thing to note, in step one I could not seem to get the files supplied in his/her attachment to work.  I found similarly named files (perhaps more recent?) on my live cd in the \pool\main\n directory.  I copied both the ndisgtk and ndiswrapper folders from there to my Ubuntu desktop and went from there.  As devilcode states, I did find it necessary to install them in order.

Thanks for the solution devilcode and thanks for supplying the .inf files, finding them on my windows machine was proving to be a real PITA, lol.

---

### Post by TubbyBeef on 2011-03-15
Does anyone have the stand alone 64 bit drivers?  I'm now running Ubuntu 10.10 Server (64 bit) and ndiswrapper is not happy about me trying to use the 32 bit drivers devilcode so kindly provided.

I downloaded and installed the NetGear software package v1.1.4.32 (containing driver version 2.0.057) on my Winblows 7 (64 bit) machine.  When I checked the the device's driver details I found two .sys files rather than one .sys and one .inf.  The files are:

C:\\Windows\System32\Drivers\authurx.sys
C:\\Windows\System32\Drivers\vwifibus.sys

Any suggestions for pulling the .inf files out of this Setup.exe I downloaded?

---

### Post by Alex-Thess on 2011-04-05
> **devilcode said:**
> Hi All,

I have been running through the forum/net trying to solve this issue of getting the WNA1100 Netgear USB WiFi dongle working on Ubuntu an easy way and so I hope the following helps.

**Step 1:**
Download and install the following in this order:

[LIST]
[*]**ndiswrapper-common**
[*]**ndiswrapper-utils**
[*]**ndisgtk**
[/LIST]
In attachment  ([ndisfiles.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178899&stc=1&d=1292795499")     (132.1 KB) ).



**Step 2:**

Once you have installed the above in order of Step 1 you need to get a copy of the XP driver for the WNA1100 USB WIFI card. If you don't have it you can download it from the attachment to this post: [WinXP2000.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178900&stc=1&d=1292795955")     (537.3 KB) 

to uncompress the files either right click on it and Extract Here... or via command line type   so for the files listed  would be:

[LIST]
[*]**tar xvf ndisfiles.tar.gz**
[*]**tar xvf WinXP2000.tar.gz**
[/LIST]

**Step 3:**

Now you need to install the XP driver to get the USB WiFi to work. So via command line in the Terminal. 
% **gksudo**
then type '**ndisgtk**' under run and make sure its as user root. Then click ok.
it will ask you to put in your su password and press ok.

The a GUI will pop up with Wireless Network Diver. Click the '**Install New Driver**' and select **netathuw.inf **

Then plug in the the WNA1100 USB WIFI and all should be good.

+++++++++++++++++++++++++++++++++++
Im new ish to linux so feel free to comment or correct.

so so so many thanks!!! :)

this :  WinXP2000.tar.gz  i need and i found it only from you here!!! thanks a lot again!!! :) simple i install it via ndiswrapper graphical interface and then works perfectly!! :)

i love you!!! :):guitar::lolflag:

---

### Post by MrMattCF on 2011-05-07
Same here thanks I could not find it and had no axcess to XP.

---

### Post by MrMattCF on 2011-05-07
I have the 64 bit drivers.  I do not know how to send them though through this.

---

### Post by salemboot on 2011-06-03
wna1100 works out of the box on Ubuntu Natty 11.04.

For Ubuntu 10.04 Lucid, technically you should just be able to include the kernel PPA and install 2.6.38-8 along with it's wireless component. ( I forgot how it's named in Synaptic )

ath9k_htc supports this chipset.  Unfortunately I had issues tracking down the correct firmware file for /lib/firmware.

_NDISWrapper_
32-Bit 10.04 worked with the NDISWrapper.
64-Bit 10.04 kept issuing invalid command 12.

I believe I even had NDISWrapper 1.56 on both machines.  It's a real pain trying to get the .inf files from the installer.

I'd recomend uniextract to pull out the various installation files.  Otherwise you'll be installing to physical Win32 machines to get the .inf and supporting drivers.  I had to install a 64bit WinOS to get the 64-Bit version of the driver.

I was trying to write a script to use Wine/uniextract but I ran into some problems I'm trying to iron out.

---

### Post by salemboot on 2011-06-07
I had to boot 11.04 and drop to a terminal and zip up the firmware directory.  Which I later unzipped into my 10.04 firmware directory.

USB Key's work great for these little fixes.

---

### Post by nouvellestechno on 2011-07-21
It works for me in few seconds !

Ubuntu 11.04 / **64 bits**


[LIST]
[*]Buy a Netgear N150 Wireless USB Adapter WNA 1100
[*]Download here the last version of the plugin Atheros
 [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
[*]Execute the .deb packet (double-click)
[*]Connect the WiFi adapter
[*]It works !
[/LIST]

---

### Post by aruhela on 2011-10-22
Many Many thanks to you.
Regards,
Amit Ruhela


> **devilcode said:**
> Hi All,

I have been running through the forum/net trying to solve this issue of getting the WNA1100 Netgear USB WiFi dongle working on Ubuntu an easy way and so I hope the following helps.

**Step 1:**
Download and install the following in this order:

[LIST]
[*]**ndiswrapper-common**
[*]**ndiswrapper-utils**
[*]**ndisgtk**
[/LIST]
In attachment  ([ndisfiles.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178899&stc=1&d=1292795499")     (132.1 KB) ).



**Step 2:**

Once you have installed the above in order of Step 1 you need to get a copy of the XP driver for the WNA1100 USB WIFI card. If you don't have it you can download it from the attachment to this post: [WinXP2000.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=178900&stc=1&d=1292795955")     (537.3 KB) 

to uncompress the files either right click on it and Extract Here... or via command line type   so for the files listed  would be:

[LIST]
[*]**tar xvf ndisfiles.tar.gz**
[*]**tar xvf WinXP2000.tar.gz**
[/LIST]

**Step 3:**

Now you need to install the XP driver to get the USB WiFi to work. So via command line in the Terminal. 
% **gksudo**
then type '**ndisgtk**' under run and make sure its as user root. Then click ok.
it will ask you to put in your su password and press ok.

The a GUI will pop up with Wireless Network Diver. Click the '**Install New Driver**' and select **netathuw.inf **

Then plug in the the WNA1100 USB WIFI and all should be good.

+++++++++++++++++++++++++++++++++++
Im new ish to linux so feel free to comment or correct.

---

### Post by kurt18947 on 2011-10-22
> **nouvellestechno said:**
> It works for me in few seconds !

Ubuntu 11.04 / **64 bits**


[LIST]
[*]Buy a Netgear N150 Wireless USB Adapter WNA 1100
[*]Download here the last version of the plugin Atheros
 [http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)
[*]Execute the .deb packet (double-click)
[*]Connect the WiFi adapter
[*]It works !
[/LIST]


Not quite, there's another step necessary. I'm working from memory so this may not be exact terminology -- I haven't had a 10.xx install for months. The first step is to install the .deb package as stated above. The **second** step is to do applications -> system ->ath9K installer. Now restart.  The benefit to this is that a kernel upgrade will kill the adapter.  Rerunning step 2 will bring the adapter back just like recompiling the driver but simpler.

---

### Post by hiakaash on 2011-12-15
This thread helped me to connect my Netgear150.
It's really very helpful:guitar:
THANX A LOT!

---

### Post by lmac82 on 2012-01-09
Hi,  I'm new to ubuntu and I'm trying to install this NIC too.  Step one seems to be install ndiswrapper.  This is where I'm stuck, there is no such thing listed in the synaptic package manager.  Now what....

> **papawapa said:**
> Hello,

I have been able to get my Netgear WNA1100 to work under Ubuntu 10.04 32-bit desktop.  I don't know if anyone still needs a guide for this, but essentially I installed ndiswrapper via synaptic and used the .inf from an xp install.  I extracted the .inf and other setup files using a VirtualBox Windows Xp install.  

As a side note I had previously tried this approach using a .inf from a Win 7 64-bit install in linux mint 8.0 and had no success.

Once I installed with ndiswrapper I was able to see my available wireless access points in NetworkManager Applet.  Also of note my Access Point is only through a linksys wrtg54 (G) router.  Considering the proximity of my router (~10 ft with a wall) my signal seems a bit weaker than I'd expect (~60%).  I also cannot assess the performance of (N) speeds and connectivity.

---

### Post by imortalninja161 on 2012-04-11
CONFIRMED ALEX-THESSES drivers on Back Track 5 R2 GNOME /64..  Thanks alot man saved me alot of time..

---

