---
title: "Dial-up Redux"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Bartender on 2010-01-10
DIAL-UP REDUX

A few years back I started a thread on [dial-up]("http://ubuntuforums.org/showthread.php?t=480717").  It was an impertinent thing to do, considering I didn't know much about dial-up.  But with input from duncan and some others I'd like to think that we helped a few people.  Ubuntu has come a long way since then.  Dial-up support has not.  Some would say it's regressed.  Wvdial has been absent from the default installation since Jaunty, and Karmic has a problem with USB-connected modems.  Some of the &#8220;official&#8221; dial-up documentation is difficult to follow and outdated.

On the other hand, Dell's winmodem drivers have helped some folks, and US Robotics/3Com recently introduced the 5637, which has helped others to get online.

I thought it was time to start another dial-up post.  I'm going to stick to what I know.  Not going to delve into 3G modems.  I aim to keep this as straightforward as possible, since some of the readers will be new to Linux.

Almost every modem in every PC is a winmodem, or softmodem.  That means it's a device that pawns some of its workload off to the CPU.  To do that the winmodem relies on drivers that talk to Windows.  Hence the &#8220;win&#8221; in winmodem.  Winmodems are inexpensive.  That's why the PC manufacturers love 'em.  Dial-up is a backwater, so there has not been a tremendous amount of effort to reverse-engineer winmodems.  There are a few resources, such as Linuxant, but I've never done that.  From the posts I've seen winmodems for the most part are still a hassle.

I'm going to recommend just one type of modem.  The serial hardware external modem, best represented by the US Robotics 5686's.  &#8220;Serial&#8221; refers to the old serial port.  &#8220;Hardware&#8221; refers to the fact that the modem has a smarter processor and doesn't rely on the OS.  Hardware modems could be thought of as little computers that do just one task &#8211; try to get you online at the fastest speed they can negotiate.  &#8220;External&#8221; means it sets outside your computer, taking up desk space.  I hated the extra clutter at first, but now have come to appreciate it for two reasons.  The USR's have 7 LED's on the bezel.  Whenever the connection is acting goofy I can glance over at those LED's to see what's happening.  I know immediately if the ISP has dropped me.  The volume dial is handy too.  Turn off the speaker when everything's working like it should, turn it up for testing.

The USR's are expensive new, but relatively cheap on eBay or craigslist.  

All is not lost if you don't have a serial port on your PC.  Just use a serial-to-USB adapter cable.  These cables are different than most cables.  There's a little chipset in the cable.  You want to get one that's compatible with Linux.  I have the Sabrent SBT-USC1M.  It works.  It's supported at the kernel level. There are others.

_Phase 1 &#8211; New Install, Get Online_

ISP &#8211; You need to find an ISP that's compatible with Linux.  &#8220;Compatible&#8221; is not the same as &#8220;supported&#8221;.  Almost every ISP will say they don't support Linux.  What they mean is they don't understand it, Linux isn't mainstream, and they don't want to get thrown into that briar patch.  In the U.S., Copper.net, BasicISP, frys.com, natblast, and hundreds of others will work.  The ones you hear about, the ones with an advertising budget, often won't work because they want you to install their proprietary, Windows-based, software.  PeoplePC and Juno are good examples of ISP's to avoid.

Don't put the cart before the horse.  Until you have a modem, and an ISP, that will work with Linux it's pointless to try connecting.  You will need to have your ISP username, such as &#8220;[COLOR="Blue"]newlinuxuser@natblast.com[/COLOR]&#8221;, your ISP password, and all local phone numbers before beginning to configure dial-up.

On January 9, 2010 I installed Karmic from scratch using a LiveCD that was burned about a month after 9.10 was released.  I did this so that people reading this post can have some confidence in the following directions.  Wvdial was dropped in the 9.04 release, so as far as I know you have just one tool in a fresh installation to establish a dial-up connection.  In Applications>Accessories find the Terminal.  Right-click on it, then left-click on &#8220;Add this launcher to panel&#8221;.  You now have a launcher for the terminal in the upper panel.  Open a terminal, and type in (or copy/paste directly from this post):

```
sudo pppconfig
```

and hit the &#8220;Enter&#8221; key.  Type in your password at the prompt, then hit Enter again.  You'll get an archaic piece of software that utilizes an awkward combination of tab, space bar, Enter key, and the up/down arrow keys.  So read the directions and pay attention.  There are some guides on the internet.  If I can find a good one I'll include it here.

Pppconfig isn't technically challenging.  You don't need a Unix degree.  It's just odd and confusing the first time or two.  You can open pppconfig at any time and blow away or edit a botched config so try to get it right but don't panic if you set it up with &#8220;Static&#8221; DNS instead of &#8220;Dynamic&#8221; and you have to go back and fix it.  I plugged in my ISP username, the ISP password, one of the local phone numbers (you can add [COLOR="Blue"]*70,[/COLOR] to the number if you have call-waiting), set DNS to &#8220;Dynamic&#8221;, left the connect speed at the default, accepted &#8220;provider&#8221; as the name for the configuration, manually entered my modem as /dev/tty/S0 (first serial port), and left the handshake at the default PAP.  You can set up more than one phone number in pppconfig, but you have to create a new configuration from scratch, with a different &#8220;provider&#8221; name.  I've done it, but for now let's stick to your best bet - picking one good phone number and using it.    

I'm just rattling off the settings from memory, so the above description of pppconfig settings isn't in order.

_Note:_  With a serial-to-USB adapter, the USR is usually recognized at /dev/tty/ACM0.  However, I remember seeing it recognized as tty/usbsomething-or-other on one PC.  You should be able to type 

```
lsusb
```

into the terminal to find where the modem is located.

Addition: Here are some [directions]("http://ubuntuforums.org/showpost.php?p=8720689&postcount=193") posted by George Vita for finding your modem:

[COLOR="Blue"]ttyS0-ttyS3 are the h/w serial ports (com1-com4 at old PCs).
Although these ports are not all (0-3) physically implemented, they exist for compatibility reasons (some h/w addresses and interrupts are reserved).

ttyUSBx is used for a typical USB peripheral that most times can be used as a serial communication port. A 'general' driver (usbserial/option) is used.

ttyACMx, ttyHSx, ttyHSFx, etc. are other 'names' for USB communication ports created by more 'specific' drivers (Linuxant creates ttyHSFx).

Puppy Linux integrates more drivers for dial up modems (also sometimes it goes better with 3g).

wvdial and wvdialconf search for /dev/modem /dev/ttySx and /dev/ttyUSBx (by default). To test another port you can firstly see if it is created (dmesg or 'ls /dev/ttyXYZ') and then try to communicate with it. Easier communication can be done with the command screen (read more using 'man screen').
Code:

screen /dev/ttyUSB0

Note: screen command may 'lock' this port (reboot to be sure). You can 'release' any port by 'killing' screen' processes. Check with 'ps -A | grep -i screen' and 'sudo kill xxxx' any 'screen' process.

When the modem is 'external', tests can be done with the following procedure:

- Boot without modem, wait for the system to load
(if you are using USB to RS232 cable or i/f DO NOT attach it)
- do NOT RUN any communication/connection program
- open a terminal window and try: sudo dmesg -c
(this will show all system activity till then and will 'clear' this log. Next simple dmesg will show only 'new' activity)
- from terminal: lsusb
- attach modem, power it ON
- wait 30-40 seconds
- from terminal: dmesg
- from terminal: lsusb

Notice any changes comparing 'lsusb' outputs. The 'new line' must be the modem.
Quote:
Bus 001 Device 004: ID 19d2:2000 ONDA Communication S.p.A.
The vendorID : productID numbers are your 'search string' to find help. For above output you must search for '19d2:2000' and their HEX definitions '0x19d2 0x2000'

Second 'dmesg' will show all system activity, possible drivers used and any communication port created. If you see something like ttyUSB0 you can 'list it' using: ls /dev/ttyU*

In general, most new communication ports created can be listed with:
Code:

ls /dev/ttyU* /dev/ttyA* /dev/ttyH*

If you need help, add the output of the terminal command: uname -a
[/COLOR]

If you set up pppconfig correctly, you can open a terminal and type

```
pon
```

You will get an error message, something about not being a member of the dip/dialout group.  Easily fixed.  Close the terminal if you want and open a new one, or just use the existing prompt.  The username that you type into the next two commands is your Ubuntu username, the one that you gave the computer when you first installed Ubuntu.  NOT your ISP username.  Type in 

```
sudo adduser [COLOR="Blue"]username[/COLOR] dip
```

and hit &#8220;Enter&#8221;

Then type in 

```
sudo adduser [COLOR="Blue"]username[/COLOR] dialout 
```

and hit Enter.

I want to make sure we have this clear.  If my Ubuntu username is &#8220;[COLOR="Blue"]jib[/COLOR]&#8221;, and my Ubuntu password is &#8220;jab&#8221;, the above two commands would be

sudo adduser [COLOR="Blue"]jib[/COLOR] dip
sudo adduser [COLOR="Blue"]jib[/COLOR] dialout

Then you have to reboot the PC.  The dip and dialout changes will not take hold without a reboot.

Now try &#8220;pon&#8221; again at the terminal prompt.  Watch the lights on your modem.  As soon as you see the lights start to flicker, and/or hear the modem starting to squawk, type &#8220;plog&#8221; at your terminal prompt to get a basic log of what's happening.  The last two times I set up a new pppconfig profile, I had to try &#8220;pon&#8221; several times before it finally connected.  On this new install I tried about seven times before pon connected.  Don't know why that is; I didn't do anything any differently the seventh time.  I thought it was going to connect, then the process stopped abruptly and the modem went back to just the one &#8220;on&#8221; light.  If you're not sure what happened, type 

```
poff
```

into terminal.  This turns off pppconfig.  If you get a message that says something about &#8220;no pppconfig running&#8221;, then you know that pppconfig failed to connect and already shut itself down.  If you don't get an error message with poff, then pppconfig was still trying to connect.

Once you have pppconfig properly set up, there are just 3 commands to deal with.  That's pon to start your dialer, plog for the log, and poff to get offline and release the modem.

Easy, eh?  

_Phase 2 &#8211; Synaptic Package Manager and gnome-ppp_

The first time this happened to me several months ago, I thought Synaptic was broken.  I had tried to search for some packages with a brand-new installation and Synaptic couldn't find anything.  However, the exact same thing happened with this fresh Karmic install.  I opened Search and typed in &#8220;gnome-ppp&#8221;, nothing.  Typed in &#8220;wvdial&#8221;, no response.  The fix is to Reload the packages.  Fire up the terminal, type in pon, get online, start Synaptic, click the Reload button, and have yourself a cup of coffee 'cause this is gonna take a while.  We usually get about 40Kbps at our house.  I asked Synaptic to Reload its package lists late in the evening when the lines are less busy.  It still took over an hour.

[COLOR="Red"]DETOUR &#8211; DETOUR - DETOUR[/COLOR]
  
Do you have a laptop, or does a friend have a Linux PC and broadband?  If so, there's a pretty easy way to get all the updates for the dial-up PC.  If you're interested, follow these extra steps.  Got a 1GB+ USB thumbdrive?  Plug it in to the Linux PC.  Create a folder on the thumbdrive.  Give it a descriptive name, something you'll recognize later.

Now, go back to Synaptic after it's finished Reloading the package lists, and click on &#8220;Mark All Upgrades&#8221;.  Then go to File>Generate package download script.  You'll get your typical Save window.  Give the file a name, and save the file (actually a script) to the folder you created on the thumbdrive if it shows up in the list.  If you don't see the thumbdrive in the list, save the script to the Desktop.  The reason why I say save it to the Desktop is that on January 9 I tried to save the script directly to the thumb drive and it wouldn't let me.  So I saved it to the Desktop, then went to the script's properties.  For some reason the permissions were restricted so I changed them to &#8220;read and write&#8221;.  Only then was I able to drag/drop the script to the new folder in the thumbdrive.  Eject the thumbdrive.  Then go to [this thread]("http://ubuntuforums.org/showthread.php?t=1238954") for more discussion about what to do with the thumbdrive.  The topic comes up at post #132.  Simple updates are pretty darned easy.  Getting optional packages can be a little more complicated but if I could figure it out so can you.

[COLOR="Red"]FINISHED WITH DETOUR &#8211; BACK ON THE MAIN PATH[/COLOR]

After Synaptic has finished updating there are two ways to go.  If you Marked All Upgrades, as described in the Detour above, you have to close Synaptic.  You'll get a message saying that settings will be lost.  Quit anyway.  Then re-open Synaptic.  

If you did not take the detour and did not Mark All Upgrades, you just let it Reload all packages and then did nothing else, click on the Search button (make sure you've maximized the Synaptic window or you may not see it) and type in 

```
gnome-ppp
```

Synaptic will find gnome-ppp.  Mark it for installation.  Synaptic will say it needs some other packages.  That's exactly what we want.  Click OK, then Mark All Upgrades and let Synaptic go get 'em.  Of course, this will only work if you're still online!

Thankfully, it'll take much less time to download the packages needed to install gnome-ppp then it took Synaptic to update.  When it's done installing, you'll find GNOME PPP under &#8220;Applications>Internet&#8221;.  Right-click on it and put a launcher on the panel like you did for the terminal.  Then you can click on the launcher and configure Gnome-ppp.  Gnome is easier to navigate than pppconfig.  If you successfully set up pppconfig, Gnome will be a breeze.  Go into Setup, the external should be detected when you click the &#8220;Detect&#8221; button.  If it isn't you know where it is already from pppconfig.  You can add several phone numbers, just make sure to click &#8220;Enter&#8221; after each one or they won't be saved.  Same with init strings.  I was experimenting with init strings and couldn't figure out why they kept disappearing.  GeorgeVida got me straightened out.

I don't understand init strings, but will point you to [the thread]("http://ubuntuforums.org/showthread.php?t=1238954&page=16") where we talked about them.  My Windows init string is at Post #154.  The ones I copied from the Windows side of our dual-boot PC seem to be working fine.  Are there better strings?  I don't know.  Probably.  The ones described seem to work pretty well with our USR 5686E.  But no init strings at all seemed to work OK too!  If you delete the one init string that's supplied in Gnome-ppp, save it to an OpenOffice or &#8220;text editor&#8221; document so you can copy/paste it back in if necessary.

Gnome-ppp will place an icon &#8211; a monitor overlapping another - in the upper right panel when it's online.  Whoops, no it won't, not automatically anyway.  Open Gnome-ppp, click on "Setup", click on "Options", and activate the "Dock in notification area" option next to "On connection:"  

Now you'll get an icon in the upper right panel.  You can click on that icon to disconnect.  As soon as you do that the main Gnome-ppp window will pop up again on the main screen.  I've found it's helpful to click &#8220;Quit&#8221; in the main window to make sure that the modem is released.  Sometimes I didn't do that, and the modem got hung.  Couldn't dial out until I &#8220;Quit&#8221; Gnome-ppp and restarted it.

If you're running Karmic and a serial external with a USB adapter, or any USB modem, there's a bug that complicates things.  You have to remove modemmanager.  Doesn't appear to be difficult.  I'll include a [link]("https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/482971").  Post #7

Oh, something else &#8211; there's been an ongoing annoyance with Firefox and dial-up for a couple of years now.  Firefox would always start in off-line mode.  There's a simple fix, described in Post #2.  I did not have to do anything to Firefox with this new installation.  It came up in Online Mode.  Yay!  I'm guessing that the Offline problem remains in earlier distros

I'm sure I missed some things, so ask and maybe we can get some screenshots and stuff added to make things clearer.  I'll be adding links and comments to this over the next few days/weeks.

Good luck!

---

### Post by Bartender on 2010-01-11
Here's a link with the instructions to stop Firefox from starting in Offline Mode...

[http://support.mozilla.com/en-US/forum/1/231957?s=downloads](http://support.mozilla.com/en-US/forum/1/231957?s=downloads)

Here's the pertinent text...

[COLOR="Blue"]To get firefox to stop starting in the offline mode:

1.Start firefox
2.Type &#8220;about:config&#8221; in the address bar (without the quotes)
3.acknowledge that you promise to be careful
4.Type &#8220;toolkit&#8221; in the filter bar that comes up
5.Look for the line that says &#8220;toolkit.networkmanager.disable&#8221;
6.Double click on this line to toggle it to &#8220;TRUE&#8221;
7.Exit firefox
8.On the next restart the &#8220;work Offline&#8221; box should be unchecked.[/COLOR]

As mentioned in above post, this does not appear to be a problem in Karmic.  Expect to deal with it in all earlier versions.

---

### Post by SecretCode on 2010-01-11
Great thread topic, Bartender. Hope somebody benefits from it! :D

---

### Post by Bartender on 2010-01-11
Thanks, Secret -
I'd like to make a guide with more screenshots and stuff, but this will have to do for now.  If I had broadband I'd probably try to make a YouTube video.

duncan passed on a [link]("http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html") that illustrates pppconfig pretty well.  

The problem is that you can't just copy what this person entered.  Everyone's pppconfig is going to be different!  However, you *can* pretty much leave everything at default except username, password, and phone #.  Don't forget to set DNS to dynamic.  And if you're only going to create one profile, you can leave the "provider" page just the way it is too.

I'll keep adding to this as anything noteworthy comes up, or if someone points out mistakes.  There's at least one post in development.  After waiting around for the Karmic PC to "Reload" all the package lists, I created a Package Download Script.  That script is saved to a thumbdrive.  In the next coupla days I'll take our laptop into town and run the script, then attempt to install the packages to the Karmic desktop.  The laptop's running 9.04, not 9.10.  I'm pretty sure that the Jaunty laptop can run the script for Karmic packages but want to try it before saying anything more.

Another thought rattling around...  If someone wants to install an optional package such as hugin or hplip, maybe we can help each other by sharing PDS files (?)

---

### Post by Bartender on 2010-01-11
OK, new problem and the more experienced folks are probly gonna laugh at me.  On the Karmic machine, when I ask Synaptic to create a Package Download Script, the PDS is owned by root.  I have very little experience with permissions.  If someone knows an easy answer to get Karmic to stop doing that, please share.

Here's my so-called solution.  **Save the PDS to the Desktop**.  Right-click on the file, left-click on Properties, left-click on Permissions.  If all the options are grayed out and it says "You are not the owner.." along the bottom, open a terminal and type 

```
cd Desktop
```

and hit Enter.  For this example let's say that your username is [COLOR="Blue"]super[/COLOR] and you named the PDS [COLOR="Red"]vlc[/COLOR].  The following command will change the file's ownership from root to super.  Type 

```
sudo chown [COLOR="Blue"]super[/COLOR] [COLOR="Red"]vlc[/COLOR]
```

The vlc file will now be owned by you, and you can move it, save it to a thumbdrive, what have you.

I'm sure there are better answers to this problem (and it seems to be a Karmic thing because Jaunty's not doing it) but this will work for now.

---

### Post by pdc on 2010-01-11
good work bartender for setting this up; some do still use dial-up and great to point them this way;

---

### Post by Bartender on 2010-01-12
A few comments on the USR Sportster modems. I attached a picture of two Sportsters. The beige one has a "56K" sticker on the front, the black one says "V.92".

As you probably guessed, the groovy black ones are newer than the boring beige ones. If you're shopping for these on craigslist or eBay, there are a few things to watch out for. Older beige models can be much slower, with stickers on them saying 28.8 and 36.6. 

US Robotics offers a Windows-based flash utility (it can be done in Linux too but I'm pretty sure it's easier in Windows) on their website that will allow you to flash the firmware.  It's possible that the firmware update will bump a slower modem up to 56K. But I don't know about that. So I made sure to buy newer ones that could run 56K out of the box, then I flashed them anyway just because.
If you're buying a used one, be aware that the wall wart power supply must be 1000mA or better. I tried running one of these with a Radio Shack 800mA wall wart. The lights came on, and everything seemed fine, but it would not connect. As soon as I plugged in a US Robotics 1000mA wall wart, the modem worked.  Another odd thing about the USR wall warts - they're AC output, not DC.  Maybe the modem has a small AC to DC converter inside?

There are eight little tiny switches on the back. 3, 5, and 8 should be in the "down" position. That's the way they come from the factory, and I imagine that most people never change them.

In the picture you can see the short cable with the blue ends. That's a Sabrent serial-to-USB adapter cable. As mentioned previously, if you don't have a serial port these adapter cables work great.

There are other serial hardware external modems available, and it would be great if some people posted with ones that work. There are a lot of old Actiontec external modems floating around from the days when AOL was handing them out like candy. I tried one a few months ago. I didn't spend a lot of time trying to get better performance out of it, just downloaded/installed the latest Windows drivers, swapped it out for our USR, and ran it on the Windows XP side of our dual-boot home PC for a few days. The Actiontec connected at about 2/3 the speed of the USR. I have no idea if the USR's are just better modems or what, but I'm sticking with what works.

EDIT: A quick comment for right now until I get it sorted out a little better - the US Robotics 5610 internal PCI modems are hardware-based too.  I'm typing this from a PC equipped with a 5610.  When I have a little bit better notes I'll expand on this.  For right now, here's a link to a [thread]("http://ubuntuforums.org/showthread.php?t=1397947") that explains briefly what I did.

---

### Post by Bartender on 2010-01-12
Some notes on getting Package Download Scripts (PDS) 

OK, so I'm at the library wearing out my welcome.  I had 5 PDS's to download so tried a few things.  The screenshot is our laptop running five PDS's at the same time.  You don't have to do them one at a time!  You know how you can't run Synaptic and Update Manager at the same time?  I thought that maybe the same restrictions would apply but that's not the case.  

You don't get a "Done!" message or anything when the PDS is finished.  So next time I try this I'll double-click on the script while on the dial-up PC at home, and choose "Display".  Then I'll count the number of packages listed in the script and include that in the folder name.  Such as "hugin_14". 

[COLOR="Blue"]*Additional note on this:* the basic idea works well, but I forgot to mention that the script itself counts as one file within the folder.  So count up the packages, then add one for the script.  For instance, "hugin_14" would become "hugin_15".  I tried some more downloads at the library and this worked fine.  It appears that the folder doesn't count the package files until they've been completely downloaded, then placed into the folder.  

To open the packages while you're at home on the dial-up PC, I think the better option is to right-click on the PDS, then pick "Open with" and find gedit or text editor, depending on your version of Ubuntu.  They're the same program, just described differently in Karmic.  Once you have the PDS opened in gedit, the easiest way to count up the packages is to maximize the window so all packages take up only one line.  Then go to Tools>Document Statistics.  This window reports the number of lines in the document.  As long as all packages are only taking one line, you subtract one for the very first line (#!/bin/sh), then you know how many packages there are.  Then close gedit. [/COLOR]

When you're in town and ready to download, you click on the script, then click "Run" and it'll take off.  The script icon remains highlighted.  Click off the icon into an empty part of the field so that the icon isn't highlighted anymore.  That way you'll get a readout in the lower left corner of each window that tells you how many files are accumulating in the folder.  Compare the name of the folder, such as "hugin_15", to the number of files accumulated and you'll have a good idea when it's almost finished.

The little wireless activity light on our laptop blinks continuously while downloading.  The thumb drive light blinks less frequently, so don't use the thumb drive light as an indicator that you're done!

NEXT DAY EDIT:  Was able use the Jaunty laptop to download the Karmic packages.  I updated the Karmic PC, which was a huge download.  Then ran "restricted extras" PDS, then ran "vlc" PDS.  The goal was to download the tools I'd need to watch some movies on the Karmic desktop PC.   The only problem I had was that the "mscoretruefont" package (or whatever it's called - something like that) from the restricted extras PDS did not install so it was skipped.  I'll probably look that package up from Synaptic and see if I can create a functional PDS for just that one package.  Maybe a dependency got skipped?

---

### Post by Bartender on 2010-01-13
As described earlier, I used the Synaptic PDS tool to do a complete upgrade of our Jaunty desktop PC.  It worked.  I went online with the desktop PC after installing the truckload of packages and Synaptic said it was updated.

I tried doing the same thing with the Jan. 9 Karmic desktop install.  Asked Synaptic to give me a PDS of all upgrades to bring it up to date.  

Attached is the error message I got regarding mscorefonts, referred to in previous post, when I tried installing the "restricted extras" PDS.  

I figured what the hey.  Connected the Karmic PC to a USR modem, went online, asked Synaptic to get ttf-mscorefonts-installer.  Synaptic went to work, and I clicked the "Details" arrow.  Synaptic was accessing sourceforge, not the Ubuntu servers.  Maybe that's why PDS failed to pick up the mscorefonts?

It took about 28 minutes on our dial-up connection to retrieve the package.  I think everything's OK now.  I had no idea that Synaptic went anywhere but Ubuntu servers!

So just a heads-up to anyone who tries to run a "restricted extras" PDS.  You'll have troubles with the mscorefonts.  I'd suggest installing mscorefonts via dial-up first, then ask Synaptic to generate a "restricted extras" PDS.

---

### Post by Bartender on 2010-01-14
Anyone want to try an experiment?

I'd like to see if we can share Package Download Scripts.  Maybe there's a quicker way, but here's what I want to try today.

I'll post the guts of a PDS I created.  If someone could copy the entire contents to a blank Package Download Script (PDS) then try and run the script on a broadband connected PC, that would be super helpful!

Here goes.  This is the entire PDS for **Extreme TuxRacer** on **Jaunty**.  I tried it, and Tux Racer installed successfully.  

```
#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libm/libmikmod/libmikmod2_3.1.11-a-6ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/smpeg/libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/sdl-mixer1.2/libsdl-mixer1.2_1.2.8-5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/tcl8.5/tcl8.5_8.5.6-3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/e/extremetuxracer/extremetuxracer-data_0.4-1ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/universe/e/extremetuxracer/extremetuxracer_0.4-1ubuntu1_i386.deb
```

It's extremely easy to create a blank PDS.  Well, almost blank anyway, you'll see what I mean if you create one.
1) Open Synaptic
2) Go to File>Generate Package Download Script.
3) Give it a name, save it to your Desktop.

As long as you don't Reload or search for any packages, Synaptic will create an (almost) empty PDS.  

OK, this is weird.  Now Jaunty is creating locked PDS's too.  Well, as described a few posts back it's easy to change.  Attached is a screenshot showing what I had to do to change permissions on the "mt" PDS.  

"MT", empty, get it?? :D

So even though I have no idea why the Jaunty Synaptic is now choosing to create locked PDS'es, it's no big deal to change them.

If someone would be so kind as to 
1 - create a blank PDS, 
2 - copy the above script, 
3 - open their blank PDS, 
4 - erase the short line of text inside, 
5 - paste the above script into their PDS, 
6 - run the script on a broadband connected PC,
7 - save the resulting PDS to a thumbdrive,
8 - install the PDS to a Jaunty PC that does not have TuxRacer by opening Synaptic, going to File>Add Downloaded Packages, and opening the thumbdrive to Run the PDS

We'll know if it's possible to share these things.  

I wonder what would happen if someone tried to install an entire update PDS to a PC that had never gone online to Reload packages?  Maybe you'd have to force the update??  I created a PDS for our dial-up Jaunty PC just a few days ago that would have everything except gnome-ppp and wvdial...

---

### Post by GeorgeVita on 2010-01-14
Hi **Bartender**, nice thread!

**UPDATE: success using Puppy Linux**

1 - create a blank PDS,
2 - copy the above script,
3 - open their blank PDS,
4 - erase the short line of text inside,
5 - paste the above script into their PDS,

Create new folder 'BT_tests'
Open text editor **copy** all script lines from your post and **paste** into text editor. **Save** new text file named 'BT_pds'.

6 - run the script on a broadband connected PC,

Using Puppy Linux, from a terminal window: ```
cd ~/my-documents/BT_tests
sh BT_pds
``` Ubuntu needs 'sudo sh ...'
Download can be resumed if stoped due to **-c** parameter at **wget** command.

7 - save the resulting PDS to a thumbdrive,

8 - install the PDS to a Jaunty PC that does not have TuxRacer by opening Synaptic, going to File>Add Downloaded Packages, and opening the thumbdrive to Run the PDS

>>> **Successful** installation but the 'game is very slow' to my netbook.

**New update**: worked also with a Greek variant of Ubuntu 9.04

Regards,
George

---

### Post by GeorgeVita on 2010-01-14
Another note:
If we copy all .deb files from **/var/cache/apt/archives/** directory of a fully updated system amd paste them to the same directory of the 'low connection speed' PC, we need only **sudo apt-get update**. This method minimises the download volume for the 2nd PC.

>>> Q: Can we copy also the 'update lists' to manage a fully 'offline' update/dist-upgrade?

**UPDATE:** Just tested above and worked fine!

- Delete any .deb package at /var/cache/apt/archives/
- Run Synaptic Package Manager on a existing 9.04 (broadband connected)
- click on '**S**' column (green means installed)
- hold 'Shift key' pressed and use 'Page Down' to select all installed
- right click on any 'selected package' and 'Mark for Reinstallation'
- click Apply
- click **Download package files only**
- click Apply

This will 'reload' the latest 'installed' packages. **It takes a lot to download.**

Copy /var/cache/apt/archives/*.deb to an USB memory stick into a directory named: **archives904/**

Move to the 'slow internet' PC.

>>> I used a fresh installation from the 9.04 LiveCD and then:

- connect to internet
- change 'software sources' to local/faster mirror
- 'sudo apt-get update' downloads 10 MBytes of data <<< THIS MUST BE DONE ONLINE!
- disconnect
- 'sudo apt-get dist-upgrade' shows 'Need to get 246MBytes of archives'
- attach USB memory stick
- 'sudo cp /media/myUSBmem/archives904/*.deb /var/cache/apt/archives/'
- 'sudo apt-get dist-upgrade' shows 'Need to get 528KB/246MB'
.... possibly due to a h/w difference between two PCs
- connect to internet
- run dist-upgrade
>> Result 'Full upgrade' with only 10.5 MBytes downloaded data on the 'slow internet' PC.

Regards,
George

---

### Post by Bartender on 2010-01-15
Hi, George!

I was very happy to read your posts.  Having your help is like tripling the thread's IQ :D

You moved the goalposts way out there, my friend.  I'm gonna have to print out your responses, reheat the coffee, and read them very carefully.

I think I understand the "mscorefonts" problem more thoroughly now.  First I have to describe what's going on here.  There are three PC's involved in my current weird science experiments.  

- PC1 is a **laptop** running Jaunty.  That's my rig for getting these packages.
- PC2 is our **main desktop PC**, also running Jaunty.
- PC3 is a Pentium 4 **test** box running a new install of Karmic.  It's shoved out of the way when not in use, unlike the main PC.  PC3 is the rig referred to in the first post, the one that got a fresh Karmic install.

All three PC's can get online via dialup at home, but only PC2 is usually wired up to do so.  

With PC3, I created a "restricted-extras" PDS, went into town and got the packages, then tried to install.  As described earlier, I got error messages on the ttfmscorefonts installer.  Fixed the problem by connecting via dialup and downloading the fonts.

So this morning I decided to install ttfmscorefonts installer to PC2 (the main PC) by simply going online and asking Synaptic to go get it.  PC2 does NOT have "restricted-extras" packages installed.  Synaptic identified three small programs, and downloaded them.  Then it started the install process.  I was wondering how come it didn't have to download very much.  Then the installer stopped at about 80% complete, judging by the progress bar.  I clicked on Details, and found out that Synaptic was online, downloading the msfonts from sourceforge!  So the ttfmscorefonts installer is just that, it's an *_installer_* for the fonts and if the PC isn't online the installer can't complete its task.  That's why I got errors when trying to run the "restricted extras" PDS on PC3, which was offline when I installed it.

Gawd, I talk a lot.  Here's the short version: AFAICT, you cannot install ttfmscorefonts via an offline PDS transfer.  Well, maybe you can, but for those of you on dial-up, the simplest thing to do is open Synaptic, type "mscorefont" into Search, then click on the ttfmscorefonts installer and ask Synaptic to go get it.  Our dialup runs about 40Kbps and it took roughly a half hour to install mscorefonts installer, then let it get the fonts from sourceforge.  That way, if you create a "restricted-extras" PDS from Synaptic, run it on a broadband PC, and bring it back home to install, you should be good to go.

---

### Post by TopEnder on 2010-01-16
Bartender great post, well worth saving it for later use, even though I have had no problems in the past install and using an external modem.

For Info:

A few modems that I have found that works with all versions of Ubuntu since 2005.

Rockwell H52PT-3020 (56k) Data / Fax /Voice
Hayes Accura 56k + Fax
(The above are showing their age just like me but still work well).
Swann Smart Pro Surfer 56k / Fax
SwannSmart Turbo (model: E210).

---

### Post by Bartender on 2010-01-16
TopEnder -
Thank you for the list of modems!  That sort of information is incredibly helpful for someone who's just getting started.

BTW, I'm planning to buy a couple of US Robotics 5610's.  They're hardware modems, but internal, and that causes some sort of trouble because they want to set themselves up as COM 5.  If I can put together a fool-proof guide I'll bring it here.  There are always 5610's on eBay.  Though I must say from the selection today each seller seems to think they have the last one on the planet...

---

### Post by Bartender on 2010-01-22
OK, here's a PDS for **Jaunty**.

I installed Jaunty fresh on January 21 to a PC, then asked Synaptic to Reload.  Below are the results.  Anyone who can put together the necessary infrastructure at their end (thumb drive, and a broadband Windows PC with the correct tools installed or broadband Linux PC with wget installed) should be able to use this PDS to update their dial-up (or maybe completely offline?) Jaunty PC.  Well, wait a minute, anyone in the U.S.  I honestly don't know what would happen if you did this from another country?  Maybe just a slower download??

This is 235MB of updates! 

```
#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gzip/gzip_1.3.12-6ubuntu2.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.10.0-19ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.9-4ubuntu6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.9-4ubuntu6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.9-4ubuntu6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.28-17.58_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.10.0-19ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.10_5.10.0-19ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.10.0-19ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-modules_1.0.1-9ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.32.dfsg-5ubuntu4.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-15ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/w/wget/wget_1.11.4-2ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/foomatic-db-engine/foomatic-db-engine_4.0.0-0ubuntu6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.2.12-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.20.1-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2-11_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnutls26/libgnutls26_2.4.2-6ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup2.4-1_2.26.0-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/sqlite3/libsqlite3-0_3.6.10-1ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsoup2.4/libsoup-gnome2.4-1_2.26.0-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgweather/libgweather-common_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgweather/libgweather1_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal1_0.5.12~rc1+git20090403-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxi/libxi6_1.2.0-1ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxklavier/libxklavier12_3.9-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.26.1-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse0_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-pulseaudio_0.10.14-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.14-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_9.04+20090803.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_9.04+20090803.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/expat/libexpat1_2.0.1-4ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-dri_7.4-0ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libgl1-mesa-glx_7.4-0ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.28-17-generic_2.6.28-17.58_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules/linux-restricted-modules-common_2.6.28-17.22_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-restricted-modules/linux-restricted-modules-2.6.28-17-generic_2.6.28-17.22_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-emailmerge_3.0.1-9ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_9.04.10_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglu1-mesa_7.4-0ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mesa/mesa-utils_7.4-0ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam-runtime_1.0.1-9ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pam/libpam0g_1.0.1-9ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id1_141-1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-base_4.0-0ubuntu0.9.04.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009u~repack-0ubuntu9.04_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cron/cron_3.0pl1-105ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-client_3.1.1-5ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dhcp3/dhcp3-common_3.1.1-5ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/file/file_4.26-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/file/libmagic1_4.26-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/newt/python-newt_0.52.2-11.3ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/newt/libnewt0.52_0.52.2-11.3ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-2_2.1.22.dfsg1-23ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.22.dfsg1-23ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/lsb/lsb-release_4.0-0ubuntu0.9.04.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/libbluetooth3_4.32-0ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libck-connector0_0.3.0-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/consolekit_0.3.0-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.2.12-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez_4.32-0ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_141-1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/newt/whiptail_0.52.2-11.3ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-40_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg40_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc40_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc45_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns45_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.4~beta1-5ubuntu2.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns46_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres40_9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb1_1.1.93-0ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.9-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/synaptic/synaptic_0.62.5ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.111.10_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.111.10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/acpid/acpid_1.0.6-9ubuntu4.9.04.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-ubuntu/app-install-data_0.7.6.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_11.9.04.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.0-0ubuntu5.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.0-0ubuntu5.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.0-0ubuntu5.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.0-0ubuntu5.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-app-install/gnome-app-install_0.5.24-0ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygobject/python-gobject_2.16.1-1ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apturl/apturl_0.3.3ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluetooth_4.32-0ubuntu4.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-alsa_4.32-0ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.3.9-17ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.8.2-11ubuntu0.9.04.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.3.9-17ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler4_0.10.5-1ubuntu2.5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.10.5-1ubuntu2.5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.3.9-17ubuntu3.4_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.3.9-17ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-cups_4.32-0ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-gstreamer_4.32-0ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bluez/bluez-utils_4.32-0ubuntu4.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.26.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media0_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/libhal-storage1_0.5.12~rc1+git20090403-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pm-utils/pm-utils_1.2.2.4-0ubuntu5_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/h/hal/hal_0.5.12~rc1+git20090403-0ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox_0.7.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox-gtk_0.7.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.8.2-0ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity-common_2.25.144-0ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/libmetacity0_2.25.144-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compizconfig-backend-gconf/compizconfig-backend-gconf_0.8.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.8.2-0ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.8.2-0ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-wrapper_0.8.2-0ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.8.2-0ubuntu8.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.8.2-0ubuntu8.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.3.9-17ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.3.9-17ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.2.12-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/dnsmasq/dnsmasq-base_2.47-3ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nspr/libnspr4-0d_4.7.5-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-11_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nss/libnss3-1d_3.12.3.1-0ubuntu0.9.04.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-14_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebackend1.2-0_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libical/libical0_0.43-2ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata1.2-1_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libgdata-google1.2-1_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/ekiga/ekiga_3.2.0-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument1_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview1_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.10.5-1ubuntu2.5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.26.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxcb/libxcb-render0_1.1.93-0ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-exchange/evolution-exchange_2.26.0-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.17+nobinonly-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9.0.17+nobinonly-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0.17+nobinonly-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0-branding_3.0.17+nobinonly-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-3.0_3.0.17+nobinonly-0ubuntu0.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox_3.0.17+nobinonly-0ubuntu0.9.04.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.0/firefox-gnome-support_3.0.17+nobinonly-0ubuntu0.9.04.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.6-0ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.6-0ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7-gtk_0.2.8.4-6ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libw/libwmf/libwmf0.2-7_0.2.8.4-6ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.6-0ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal-data_2.26.0-0ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-terminal/gnome-terminal_2.26.0-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/libgvfscommon0_1.2.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-fuse_1.2.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-bin_1.2.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.3.2-1ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.3.2-1ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs-backends_1.2.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gvfs/gvfs_1.2.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector_0.4.2.3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-selector/language-selector-common_0.4.2.3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcompress-raw-zlib-perl/libcompress-raw-zlib-perl_2.015-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3-gnutls_7.18.2-8ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-noxpm_2.0.36~rc1~dfsg-3ubuntu1.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.20.1-0ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.59-1ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu38_3.8.1-3ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickwand1_6.4.5.4.dfsg1-1ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openexr/libopenexr6_1.6.1-3ubuntu1.9.04.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/imagemagick/libmagickcore1_6.4.5.4.dfsg1-1ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_2.0.1-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-runtime_2.0.1-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_2.0.1-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_2.0.1-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_2.0.1-4ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-2.0-gac_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-posix2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-getoptions2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-i18n2.0-cil_2.0.1-4ubuntu0.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/mpfr/libmpfr1ldbl_2.4.0-1ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/neon27/libneon27_0.28.2-6.1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/consolekit/libpam-ck-connector_0.3.0-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulse-browse0_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libsndfile/libsndfile1_1.0.17-4ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/libpulsecore9_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple-bin_2.5.5-1ubuntu8.5_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.5.5-1ubuntu8.5_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.5.5-1ubuntu8.5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.4.1~dfsg-12ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp15_5.4.1~dfsg-12ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libthai/libthai-data_0.1.9-4ubuntu0.9.04.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libt/libthai/libthai0_0.1.9-4ubuntu0.9.04.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/tracker/libtrackerclient0_0.6.93-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_141-1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.2.0.dfsg-3.1ubuntu0.9.04.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.2.0.dfsg-3.1ubuntu0.9.04.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.2.0.dfsg-3.1ubuntu0.9.04.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.32.dfsg-5ubuntu4.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-generic_2.6.28.17.22_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.28.17.22_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-meta/linux-restricted-modules-generic_2.6.28.17.22_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-17_2.6.28-17.58_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.28-17-generic_2.6.28-17.58_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.28.17.22_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/m/metacity/metacity_2.25.144-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.26.2-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.26.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.7.1~rc4.1-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p4+dfsg-7ubuntu5.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ure_1.4.1+OOo3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/uno-libs3_1.4.1+OOo3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_3.0.1-9ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_3.0.1-9ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_3.0.1-9ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base-core_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_3.0.1-9ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8g-15ubuntu3.4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.5.5-1ubuntu8.5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-esound-compat_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-gconf_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-hal_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-utils_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/pulseaudio/pulseaudio-module-x11_0.9.14-0ubuntu20.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/python-cupshelpers_1.1.3+git20090218-0ubuntu19.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.32.dfsg-5ubuntu4.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.3.2-1ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.3.2-1ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/screen-profiles/screen-profiles_1.44-0ubuntu1.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/splix/splix_2.0.0-0.1ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-common_1.1.3+git20090218-0ubuntu19.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-config-printer/system-config-printer-gnome_1.1.3+git20090218-0ubuntu19.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.26.1-0ubuntu5.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-plugins_2.26.1-0ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-gstreamer_2.26.1-0ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.26.1-0ubuntu5.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.26.1-0ubuntu5.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-gtk_1.51-0ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/transmission/transmission-common_1.51-0ubuntu3.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.6.3-0ubuntu9.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.26.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.26.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.22.2-0ubuntu4_i386.deb
```

If you've partially updated your PC since installing Jaunty I'm pretty sure apt-get will just ignore the packages it doesn't need.  

Here are a couple of links that help explain the Package Download Script. 
[https://help.ubuntu.com/community/Synaptic/PackageDownloadScript](https://help.ubuntu.com/community/Synaptic/PackageDownloadScript)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

I tried to explain PDS earlier in this thread, plus in the wvdial thread referred to in the first post of this thread.

---

### Post by Bartender on 2010-01-22
Before I forget, I wanted to mention another weird phenomena that may help explain some of the "I just installed Ubuntu and it says there aren't any hardware drivers for my video card" threads.

Right after re-installing Jaunty and setting up pppconfig I went to "Hardware Drivers" in Administration.  The PC is running an ASUS EN8400GS card and I knew there were nvidia drivers.  The Hardware Drivers utility said none were in use on this PC!! :confused:

Asked Synaptic to Reload.  Only then did the Hardware Drivers utility correctly identify the drivers needed for the video card.

---

### Post by SecretCode on 2010-01-22
> **Bartender said:**
> Well, wait a minute, anyone in the U.S.  I honestly don't know what would happen if you did this from another country?  Maybe just a slower download??


It will work, for sure, but it may well be slower. Also, some of us in broadband-starved countries also have different limits for local vs international traffic.

Maybe you could put the server name in a variable? Something like:
```
#!/bin/sh
SERVER=us.archive.ubuntu.com
wget -c http://$SERVER/ubuntu/pool/main/g/gzip/gzip_1.3.12-6ubuntu2.9.04.1_i386.deb
...
```

---

### Post by Bartender on 2010-01-23
Here's a PDS for **Ubuntu 9.10** -

Should bring a fresh installation of **Karmic** up to date or nearly so - again, these are US servers...

```
#!/bin/sh
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python_2.6.4-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/python-defaults/python-minimal_2.6.4-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysvinit-utils_2.87dsf-4ubuntu12_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/sysv-rc_2.87dsf-4ubuntu12_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/sysvinit/initscripts_2.87dsf-4ubuntu12_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/upstart/upstart_0.6.3-11_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/x11-common_7.4+3ubuntu10_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.31-17-generic_2.6.31-17.54_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libudev0_147~-6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2009u-0ubuntu0.9.10_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/adduser/adduser_3.110ubuntu7_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.22.3-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-data_2.22.3-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/r/rsyslog/rsyslog_4.2.0-2ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/fuse-utils_2.7.4-1.1ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/fuse/libfuse2_2.7.4-1.1ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_147~-6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/sreadahead_0.90.3-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ureadahead/ureadahead_0.90.3-2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor_2.3.1+1403-0ubuntu27.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor1_2.3.1+1403-0ubuntu27.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/libapparmor-perl_2.3.1+1403-0ubuntu27.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apparmor/apparmor-utils_2.3.1+1403-0ubuntu27.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libgssapi-krb5-2_1.7dfsg~beta3-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5-3_1.7dfsg~beta3-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb5support0_1.7dfsg~beta3-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/krb5/libk5crypto3_1.7dfsg~beta3-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns53_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres50_9.6.1.dfsg.P1-3ubuntu0.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.126.9_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.126.9_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-partner/app-install-data-partner_12.9.10.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_1.9.3-0ubuntu4.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_1.9.3-0ubuntu4.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_1.9.3-0ubuntu4.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_1.9.3-0ubuntu4.2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core6_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.20-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/libgstreamer-plugins-base0.10-0_0.10.25-2ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.18.3-1ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail18_2.18.3-1ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-common_2.18.3-1ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/gtk2-engines-pixbuf_2.18.3-1ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-0_2.18.3-1ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.28.1-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/brasero/libbrasero-media0_2.28.2-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/udev/libgudev-1.0-0_147~-6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbis0a_1.2.0.dfsg-6ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisenc2_1.2.0.dfsg-6ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base_0.10.25-2ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/b/brasero/brasero_2.28.2-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox-gtk_0.8.6_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/checkbox/checkbox_0.8.6_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupscgi1_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsdriver1_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsimage2_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsmime1_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/libcupsppdc1_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler5_0.12.0-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.12.0-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-common_1.4.1-5ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-bsd_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups-client_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/cups/cups_1.4.1-5ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/d/devicekit-disks/devicekit-disks_007-2ubuntu4_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy30_2.28.1.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-common_2.28.1.1-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/enchant/libenchant1c2a_1.5.0-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-gtk28_2.28.1.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/libempathy-gtk-common_2.28.1.1-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libindicate/libindicate3_0.2.3-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libi/libindicate/libindicate-gtk1_0.2.3-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy_2.28.1.1-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/empathy/empathy-doc_2.28.1.1-0ubuntu1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevdocument1_2.28.1-0ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/libevview1_2.28.1-0ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib4_0.12.0-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.28.1-0ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2-11_2.28.1-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.28.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.28.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.28.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/f-spot/f-spot_0.6.1.5-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/alsa-lib/libasound2_1.0.20-3ubuntu6.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1-gnome-support_1.9.1.7+nobinonly-0ubuntu0.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.1/xulrunner-1.9.1_1.9.1.7+nobinonly-0ubuntu0.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-gnome-support_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5-branding_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-3.5_3.5.7+nobinonly-0ubuntu0.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/f/firefox-3.5/firefox-gnome-support_3.5.7+nobinonly-0ubuntu0.9.10.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcalctool/gcalctool_5.28.2-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.28.1-0ubuntu2.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.6.7-1ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.6.7-1ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.6.7-1ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.28.1-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.28.1-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.28.0-0ubuntu3.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-alsa_0.10.25-2ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-plugins-base-apps_0.10.25-2ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-base0.10/gstreamer0.10-x_0.10.25-2ubuntu1.2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.18.4-1ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines-murrine/gtk2-engines-murrine_0.90.3-1ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/libibus1_1.2.0.20090927-2ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/ibus_1.2.0.20090927-2ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/python-ibus_1.2.0.20090927-2ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/i/ibus/ibus-gtk_1.2.0.20090927-2ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-gtk_0.5.5-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/j/jockey/jockey-common_0.5.5-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/k/kerneloops/kerneloops-daemon_0.12+git20090217-1ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-gobject0_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-ui0_0.6.25-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/c/clutter-gtk/libclutter-gtk-0.10-0_0.10.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgd2/libgd2-xpm_2.0.36~rc1~dfsg-3ubuntu1.9.10.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgtk2.0-bin_2.18.3-1ubuntu2.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libh/libhtml-parser-perl/libhtml-parser-perl_3.61-1ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/p/postgresql-8.4/libpq5_8.4.2-0ubuntu9.10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/libv/libvorbis/libvorbisfile3_1.2.0.dfsg-6ubuntu0.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libwbclient0_3.4.0-3ubuntu5.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.25_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.31.17.30_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.31.17.30_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-17_2.6.31-17.54_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.31-17-generic_2.6.31-17.54_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.31.17.30_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.31-17.54_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.28.1-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.28.1-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/ntp/ntpdate_4.2.4p6+dfsg-1ubuntu5.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/n/nvidia-common/nvidia-common_0.2.15.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/a/avahi/python-avahi_0.6.25-1ubuntu5.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client-gnome_1.0.2-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/ubuntuone-client_1.0.2-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/u/ubuntuone-client/python-ubuntuone-client_1.0.2-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_0.12.5-0ubuntu5_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.4.0-3ubuntu5.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.4.0-3ubuntu5.3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common-bin_3.4.0-3ubuntu5.3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/system-tools-backends/system-tools-backends_2.8.2-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-gabble/telepathy-gabble_0.8.7-1ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-plugins_2.28.2-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_2.28.2-0ubuntu3_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem_2.28.2-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-mozilla_2.28.2-0ubuntu3_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsplash/ubuntu-xsplash-artwork_0.8.5-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-video-all_7.4+3ubuntu10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg-input-all_7.4+3ubuntu10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xserver-xorg_7.4+3ubuntu10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/xorg_7.4+3ubuntu10_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsane/xsane_0.996-2ubuntu1.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsane/xsane-common_0.996-2ubuntu1.1_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/x/xsplash/xsplash_0.8.5-0ubuntu1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-documentation-en_2.28.1-0ubuntu2_all.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/e/evolution-indicator/evolution-indicator_0.2.4-0ubuntu3.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/gnome-settings-daemon/gnome-settings-daemon_2.28.1-0ubuntu2_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.97~beta4-1ubuntu4.1_i386.deb
wget -c http://us.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.4.0-3ubuntu5.3_i386.deb
```

---

### Post by GeorgeVita on 2010-01-24
Hi **Bartender**, your post above came at the right time!

I just did my 1st dual boot installation and 'need to check' some ideas of this thread!
Ubuntu 9.10 installed from LiveUSB, packages downloaded at a 'free wifi' place using your PDS (previous post) using US repos.

After installation, Synaptic did nothing with 'File > Add downloaded packages' so I copied all packages to /var/cache/apt/archives/ directory, connected via 'slower' mobile broadband, did an 'sudo apt-get update && sudo apt-get dist-upgrade'. Total download 10MB for the update plus 35MB more for other packages (I used Greek repos to update). Possibly the difference is my EeePC versus your laptop (?). I did not used localisation.

So a total of 45MB to get instead of 150-200 MB needed.

>>> Still missing is the offline 'sudo apt-get update'

Regards,
George

---

### Post by Bartender on 2010-01-24
Hi, George -
What you describe dovetails nicely with my latest experience.  A few days ago I screwed up the Jaunty install on PC2, our main desktop PC.  A smarter person would have known how to fix it.  I reinstalled.  Figured I could just re-use some of the PDS packages I'd created several days ago for the same PC, but Synaptic looked at the PDS'es and wanted to download 10 to 12MB.  So I built new PDS'es, went back to the library, etc. etc. and these new packages installed without any fuss.  Except the "restricted-extras" PDS, which I'll explain below.

So.  After creating, downloading and installing a couple of dozen PDS'es I have two comments.
 
First, if we were to round up 1000 PC's running Ubuntu and compare their package lists, maybe 3 of them would be identical.  Thank God apt-get can keep track of what's needed.

Second, apt-get seems to be fairly forgiving.  It'll skip over packages that it doesn't need.  And as you saw, instead of just throwing its hands up when it doesn't have all the packages, it'll tell you what else it needs.  

When I tried to install the "restricted-extras" PDS to the fresh Jaunty installation on PC2 just yesterday, apt-get said it needed a couple of packages.  I stopped right there, clicked on gnome-ppp, got online, then went back to Synaptic and clicked OK.  It downloaded a couple of small packages, then it turned back to the PDS and installed everything! :)

Thanks for describing your work-around if Synaptic doesn't automagically start installing the PDS.  Good to know there's more than one way.  I wonder why Synaptic balked?

---

### Post by Bartender on 2010-01-24
George Vita -

I want to make sure we got this right.  Synaptic didn't start installing the packages, so you had to do a few distinct tasks -

1 - Copy all the packages from the PDS on thumbdrive or desktop or wherever into /var/cache/apt/archives
I attached a screenshot of what that folder looks like from the Nautilus browser - did you have to "sudo" anything, or was this a simple drag-and-drop?

2- The command you ran from terminal - was that one command or two?  Is this what you did?

```
sudo apt-get update && sudo apt-get dist-upgrade
```

And you'd want to be online **before** running the above command, correct?

---

### Post by GeorgeVita on 2010-01-24
My procedure to make my EeePC 1000H a 'dual-boot' with semi-offline update:

a. All .deb (PDS) downloaded
- PDS (post#19) copied to a text file into a directory ('arch910') at USB mem
- from terminal: 'cd ...' into that directory, and 'sudo sh get910pds'
- all .deb files downloaded into that directory

b. Fresh installation
- Boot LiveUSB with Ubuntu 9.10 desktop
- 'install Ubuntu', re-partition 'D' drive (sda2) to have '/' ext3 and swap
- reboot on new installation

c. Synaptic > File > Add downloaded packages > point to USB mem directory
- NO ACTION! (did not used the downloaded packages)

d. 3g connected and 'sudo apt-get update'

e. disconnected

f. Synaptic > File > Add downloaded packages > point to USB mem directory
- ALL INSTALLED OK (a small delay + grey screen appears in the start of this process)

g. 3g connected, 'sudo apt-get dist upgrade'
> 1st try: 35MB more needed and downloaded
> 2nd try: manually added all .deb files from /var/cache/apt/archives/ directory into the USB mem (PDS .deb + that of 1st try) resulting to 0MB needed

Final check (+1) to another desktop:
- Boot LiveCD (9.10) and install
- System > Administration > Synaptic Package Manager
- Add downloaded packages = NO ACTION
- Connected to internet
- 'Reload' at synaptic
- Disconnected
- Add downloaded packages (pointing to USB mem directory) made FULL update
- Restart
- Connected and checked that was updated (via 'check' of Update Manager, or 'Reload' at Synaptic)

Regards,
George

P.S. Double+1 checked with triple+1 formatted Ubuntu partition. (+1 = other PC)
>>> **Still missing the offline 'sudo apt-get update'**

---

### Post by Bartender on 2010-01-27
There are three compact USB modems 

[http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005](http://www.newegg.com/Product/Product.aspx?Item=N82E16825164005)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006](http://www.newegg.com/Product/Product.aspx?Item=N82E16825104006)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825115031](http://www.newegg.com/Product/Product.aspx?Item=N82E16825115031)

that have positive Linux reviews.  I'm very curious about these.  I believe they did not work very well when first introduced but kernel revisions may have solved the problems?

Well, except for the modemmanager problem mentioned with 9.10.  Does anyone have any feedback on these?  I'd like to test them all but don't have that level of discretionary income :D

---

### Post by dotborg on 2010-02-11
Just wanted to say a big thankyou to Bartender, George Vita and lkraemer for their info on getting dial up working.
If it wasn't for guys like you I'd be looking at a couple of months of wasted effort and probably abandoning Ubuntu - again - so thanks & keep up the good work!

---

### Post by Bartender on 2010-02-11
Well, thanks for the thanks!  I'm not an expert on dial-up, but don't need to be.  I just figured it was time to try and pick everybody's minds for good stuff, then collect it as well as can be done within the forum environment. 

Forums can be great, but there's definitely a random factor to the quality of help you'll get.  Depending on time of day, whether a new release just came out, if someone who had the exact same problem as you just happens to be online, etc.  As we've all probably found out, "searching" the forum can be an exercise in futility.

Add to that a really big problem with dial-up.  Most of the active forum members have broadband.  Within a few days of getting broadband, people probably purge their minds of the horrible dial-up experience.  So we lose lots of smart people who, if they were all still stuck on dial-up, would be sharing their knowledge.

And what we've got here is far from definitive.  I'm concerned that new USB-based modems like the little Rosewill RNX-56 are a far better solution than scrounging eBay for ancient USR externals, but I haven't seen the RNX-56 in action so don't want to make a recommendation.

We gotta stick together!  Of course, if Qwest EVER runs DSL up the valley, I'll eBay most of my USR modems and it'll be hasta la vista, baby

---

### Post by DustStuff on 2010-03-01
This post does not really refer to most (or all?) of what people have been posting here, but I think it does fit under the subject of this thread, so I thought I'd go ahead and post it here.

If you are using a USB modem and were using wvdial (or possibly another dialer) successfully in Ubuntu 9.04, but it no longer works (with the same settings) in Ubuntu 9.10, then you might want to check out [this post]("http://ubuntuforums.org/showthread.php?p=8899463#post8899463") for a workaround solution.

---

### Post by GeorgeVita on 2010-04-01
Good news:
> **From [https://bugs.launchpad.net/bugs/400573](https://bugs.launchpad.net/bugs/400573)**
Steve Langasek  wrote 15 hours ago:  	  #9
wvdial is now seeded in the liveCD bundled archive.
Changed in ubuntu-meta (Ubuntu):
status: 	New &#8594; Fix Released 

Regards,
George

---

### Post by Xemnova on 2010-05-02
Hello,
      
         Perhaps you could help me seeing as you've gotten dial-up to work for you. I have Ubuntu 10.04 and I do have wvdial and gnome-ppp. Gnome-ppp can't find my modem at all and I even downloaded the closest drivers I could find to the ones that a program told me to get from the Linuxant website. Do you think you could point me in the right direction to getting connected? I have a Conexant modem in my computer. Any help would be appreciated :D

              -Thank you

---

### Post by DustStuff on 2010-05-02
Xemnova, I haven't had the chance yet to try 10.04, and haven't done much with gnome-ppp, but you may be able to find some helpful info via the following Google search pages:

--Scanning [this page]("http://www.google.com/#hl=en&source=hp&q=%22ubuntu+10.04%22+wvdial+gnome-ppp&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=a86c207b1c79523e") suggests that the problem you're having with gnome-ppp not working is a known bug, and if you poke around a bit in the various links you might be able to find a workaround to use until they get it fixed. If you can't get it working, there's a good chance you can use wvdial to get it to work, although you might have to sacrifice the graphical user interface (GUI).
--[This page]("http://www.google.com/#hl=en&q=%22ubuntu+10.04%22+wvdial+conexant+modem&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=a86c207b1c79523e") gives a few links related to your particular modem (Conexant), but I'm not sure if anything there will be helpful.

Not sure where you're at as far as experience with using a Linux system, but [this page]("http://g4jc.net84.net/wordpress/2010/03/ubuntu-lucid-lynx-to-include-wvdial-and-how-to-dial-up/") has a basic how-to on using wvdial with 10.04. If it works, great, but like I said, it's basic, and I know I've had to do a bit more tweaking with the modem I have to get it to work. If you're familiar with running scripts or want to take the time to learn how (it's probably easier than writing the script :) ), you might want to check out [this page]("http://code.google.com/p/linuxshellscripts/") where there's a script available that provides a user interface for configuring the wvdial settings. I haven't tried either of these solutions myself, but they might be worth checking out if you're interested.

Other combinations of searches via Google or within these forums will possibly give you some helpful information. Also, when dealing with a modem that no one else seemed to be using, I found it helpful to do some more general searches using something like 'wvdial' and 'usb modem' or something like that. Doing that will probably help you find out some ways to figure out how you will need to configure wvdial to get things to work. Just from what I've seen so far on these Google pages, my advice would be to try to get your connection to work with wvdial first, and then once that's working, focus on the problem with gnome-ppp.

Hope this helps by giving you some ideas of where to start in solving your problem. There's also people on these forums who have more experience and knowledge than I do who might be able to help you, but your best chance at getting them to respond is to do as much research and troubleshooting as you can yourself, and then do a post with relevant details about what you've tried, error messages you've gotten, etc.

Cheers! :)

---

### Post by DustStuff on 2010-05-02
By the way, in reference to the news in post #28 about wvdial being included in the 10.04 package, I wonder if that also means wvdial should be able to work in 10.04 without a problem? Is there anyone else who had wvdial working in 9.04, had it stop working in 9.10, and then had it start working in 10.04? I haven't made the move to 10.04 yet on this system, but probably will in the fall, and it would be great if wvdial would work again. The main question in my mind is whether it's an issue (bug) with Ubuntu or wvdial or whether it's an issue with my system. But I haven't pursued a solution since I've been able to come up with a funky workaround that requires running wvdial first, cancelling it, and then running a mile-long pppd command from the terminal line. :)

---

### Post by GeorgeVita on 2010-05-03
Hi **DustStuff**,
an update should work but in case of 9.04 to 9.10 the 'new' modem-manager may cause some problems. For a new installation below is my summary:

**wvdial** and dependencies are not included into CD of **9.04** and **9.10** (exists on DVD). You can install it if you have an internet connection (sudo apt-get install wvdial) or download and install the packages needed:
[wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790").

Ubuntu **9.10** initial version (liveCD) has [bug#446146]("https://bugs.launchpad.net/bugs/446146") which affects most 3g modems. An **update using any other connection** (ethernet or wifi) 'repairs' it.

Ubuntu **10.04** includes **wvdial** and dependencies but are NOT installed! ([bug#400573]("https://bugs.launchpad.net/bugs/400573"))
To install them read [wvdial offline installation]("http://ubuntuforums.org/showthread.php?p=7245790#post7245790")

>>> Additionally: from Ubuntu 9.10, **modem-manager** tries to setup/control modems. In many 'dial-up' cases causes troubles and need to be removed!

Regards,
George

---

### Post by Xemnova on 2010-05-08
Hey DustStuff,

    Thank you for the help. I will hopefully be getting a USB modem from my cousin that says its Linux compatible so I should be all set. 

      -Xemnova

---

### Post by Bartender on 2010-07-03
Good morning!
Haven't visited the Forums in a while...
In case the question's come up, I got online with a trusty USR Sportster modem with 10.04 exactly the same way as previous versions of Ubuntu.

Installed 10.04 to a test PC that was running 9.10.

Plugged in a USR 5686E external modem.  I've tried other old serial externals like an ActionTech and a Boca; none work as well as the USR's.

SET UP PPPCONFIG:  Open a terminal, type "sudo pppconfig", enter password, go thru the clunky pppconfig interface to enter our ISP username, password, set for Dynamic DNS, all the things discussed previously in this and other threads.  Save the configuration.

Open a terminal, type in "sudo adduser *yourname* dip" then Enter.  "Yourname" is your Ubuntu username, not your ISP username.  I always type in "sudo adduser *yourname* dialout" too but I don't think it's actually necessary.

Turn off the PC, turn it back on.  For some odd reason the adduser command doesn't work until you turn off the PC then turn it back on.

GO ONLINE WITH PPPCONFIG:  Open a terminal, type in "pon", hit Enter.  As usual, the modem squawked and chirped and failed to connect.  This almost always happens the first time that I try to use pppconfig on a new install.  It'll fail two or three or several times before I get a connection.  This time pon only failed to connect the first time.  The second time it connected and I was online.  

RUN SYNAPTIC:  Opened Synaptic and reloaded all the packages.  That took roughly an hour.  

GET GNOME PPP:  Using Search box in Synaptic, I typed in "gnome-ppp".  Synaptic found the necessary packages and I asked it to install just those, NOT the 222MB of other packages that were identified to bring this PC up to date.

MAKE A PACKAGE LIST:  Using the steps described earlier in this thread, I asked Synaptic to Mark all updates, then created a package list.  Will go to the library with the laptop and a thumbdrive and get them, bring them home, and install.  

Should be up to date then, or maybe there will be more packages.  If I have to go back to the library, so be it  

Then all I have to do is get Handbrake and a few other things installed, and the test PC will be good to go.  It's a hassle to go to the library and get the packages, but it's a method that works.  222 MB via our dial-up connection ain't gonna happen!

Getting the Ubuntu restricted packages is also a bit of a hassle because the fonts need to be downloaded via dial-up, as described earlier.

---

### Post by solomonhomicz on 2010-07-04
WvDial is included in the 10.04 CD but is not installed by default. For some reason the packages didn't show up right away when I added the CD to the repository list. So I just went to wvdial in the synaptic package manager clicked install (with no internet connection), an error message comes up that includes the names of the packages you need (wvdial, fakeroot and I think two others). All the packages are on the CD, I just copied them into a folder named wvdial_stuff and used synaptic manager to install (->file ->add downloaded packages).
Run ~$ sudo wvdialconf, then edit your wvdial file with phone number username and password. Add a launcher to run wvdial in terminal and away you go.

I use a ZOOM telephonics USB modem, wvdial worked great in 8.04, 8.10 and 9.04 but 9.10 would not find the modem again after disconnect. I found that the port would wander from tty/ACM0 to ACM5 and anywhere in between. I had to run wvdialconf every time before connecting. The interesting thing was that if I ran wvdialconf consecutively 3 or more times my average connection speed would increase from around 3 kb/s to about 6.5 kb/s (I ended up calling a bash script with a launcher that would run wvdialconf 3 times and then wvdial). I dug around looking for answers to the "wandering port" and found a 64bit conexant driver that involved a real pain in the *** to install, I ended up executing some module commands I didn't really understand but the install worked. My port stayed put and my connection speed increased to about 9 kb/s with periodic spikes of a couple seconds up to 14 kb/s! I was jazzed, this was the greatest thing...,I thought. When I got to a wireless connection no wi-fi, the broadcom driver would not attach to the device - I never figured that one out. I run two ubuntu systems (a stable and an unstable) and a windows system, I just worked in 8.04 around wifi and 9.10 at home with the dial-up, while I waited for 10.04. I'm thinking about checking out Linux Mint in my 8.04 partition.

I'm living with connection speeds between 2.9 and 5.0 kb/s now. Maybe someday I'll venture into the world of modem drivers again. I found last time that anything with a conexant chipset will work on linux. I also found that there are drivers available from conexant for linux that run circles around the drivers in slmodemd (the 3 "smart" modem drivers included in ubuntu). However to perform a clean install you better have your act together, just finding the necessary info (let alone understanding it) and packages is a real pain.

---

### Post by Bartender on 2010-07-04
I wonder if your problems with the port wandering around are unique to your hardware, or something that's come up with other folks?  I don't know how to write a bash script, so I'd be freakin out if I had your problems with wvdial.

I haven't messed with it lately, but never had any problems with the ports when using our laptop's USB port, a Sabrent serial-to-USB cable, and a trusty USR Sportster modem.  I set it up at ACM0 and that's where it stayed.  That was with 8.10.  I haven't installed 10.04 to the lappy yet.

It's maddening that dial-up is still a confusing, primitive mess while so many things in Linux have gotten so much easier.

---

### Post by solomonhomicz on 2010-07-06
I'm not sure what the deal with the wandering port was all about. It only happened with 9.10 and not initially after the upgrade but the the following kernel update. My dialup port began wandering and my wifi became particularly troublesome but still workable. I began exploring the conexant modem drivers, the 32 bit ones are easy to find, however the 64bit driver was really hard to find and involved installation of kernel modules and even included a workaround for the wandering port problem. It was pretty involved and I didn't understand most of it, but I decided to go for it since this was my "unstable" os (I always maintain a stable and unstable linux partition, so I can screw stuff up and still have a working linux). After this the port no longer wandered and my dial-up speed was DRASTICALLY better. But I completely nuked my wifi, it seems alot of people were having Broadcom wifi driver problems in 9.10.
What kind of dial-up speed do you get? The literature I read about the drivers was really interesting and I'm going to venture into it again someday. Does your serial modem outperform my plain usb modem (avg speed of around 3 kb/s, sometimes up to 4.4 or 5 kb/s sporadically)?
You should really check out shell scripting, here's a good tutorial [http://bash.cyberciti.biz/guide/Main_Page]("http://bash.cyberciti.biz/guide/Main_Page"). Basically it's just any command you would execute in a command shell written in an executable (sudo chmod +x <filename>.sh) text file. You execute it like any other program (./<filename>.sh), and it just reads the file line by line and executes the commands just as if you were typing them in and pressing enter after every line. Simple Simon, you'll be able to write and execute simple scripts in less than an hour. Great stuff, you should really check it out.

---

