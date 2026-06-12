---
title: "[SOLVED] How To Decrypt and Rip Your Dvds In Ubuntu"
date: 2009-01-25
forum: Multimedia Software
---

### Post by mikeuhlik on 2009-01-25
[COLOR="Red"]This guide is still on going and not complete it almost done it will be completed within the next few day please bare with me i do have to work LOL.[/COLOR]

:D Here is a complete guide to Decrypt and Rip Your Dvds In Ubuntu

[COLOR="Red"]Note: I am mot responsible for how this guide is used this is not for illegal use of backing up DVDs it is intended to make legal backups of purchased DVDs for the use of putting them on your pc to watch or make it fit on a portable device and also to have a legal backup of your disc in case it get scratched I some were that if you buy the DVD you are legally allowed to make on backup copy of your DVD. P.S. I am not a lawyer so don't take my word for it. Also i will not be held liable or legally responsible for anything anyone dose with this.[/COLOR]

Okay let get started it will be a long one.

First lets download all the software were going to need.

[COLOR="RoyalBlue"]1. Wine for linux you may use Synaptic Package Manager / Add/remove or Terminal[/COLOR]

Installing WINE

- Make sure your backports repository is enabled in the Software Sources dialog.
- You will also need a Windows box with a correctly installed and registered version of PS.
Keep in mind that not all Windows programs will work with Wine. Moreover, some programs won't work or will look ugly without the Windows fonts. There is however a way to install Windows fonts in Ubuntu by typing:

- Open a terminal and type
CODE
$ sudo apt-get update
$ sudo apt-get install wine wine-doors recode msttcorefonts


[COLOR="RoyalBlue"]2. k9copy download and install[/COLOR]

[http://archive.ubuntu.com/ubuntu/pool/multiverse/k/k9copy/k9copy_2.0.2-0ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/multiverse/k/k9copy/k9copy_2.0.2-0ubuntu1_i386.deb")

or use Synaptic Package Manager / Add/remove or Terminal

- Open a terminal and type
CODE
$ sudo apt-get update
$ sudo apt-get install k9copy

[COLOR="RoyalBlue"]3. k3b download and install[/COLOR]

[http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.5-1ubuntu6_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/k/k3b/k3b_1.0.5-1ubuntu6_i386.deb")

or use Synaptic Package Manager / Add/remove or Terminal

- Open a terminal and type
CODE
$ sudo apt-get update
$ sudo apt-get install k3b

[COLOR="Red"]After all this restart your computer to let wine, k9copy & k3b  set in[/COLOR]

[COLOR="RoyalBlue"]4. Free DVD 1.0 download to desktop well need this later[/COLOR]

[http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/Free-DVD.shtml]("http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/Free-DVD.shtml")

Also download this icon for the software well need this later

[http://www.softpedia.com/screenshots/ico/Free-DVD.GIF]("http://www.softpedia.com/screenshots/ico/Free-DVD.GIF")

[COLOR="RoyalBlue"]5.RipIt4Me 1.7.1.0 download to desktop well need this later
[/COLOR]
[http://www.softpedia.com/get/Multimedia/Video/Encoders-Converter-DIVX-Related/RipIt4Me.shtml]("http://www.softpedia.com/get/Multimedia/Video/Encoders-Converter-DIVX-Related/RipIt4Me.shtml")

Also download this icon for the software well need this later

[http://www.softpedia.com/screenshots/ico/RipIt4Me.gif]("http://www.softpedia.com/screenshots/ico/RipIt4Me.gif")

[COLOR="RoyalBlue"]6. DVD Shrink 3.2.0.15 download to desktop well need this later
[/COLOR]
[http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVD-Shrink.shtml]("http://www.softpedia.com/get/CD-DVD-Tools/CD-DVD-Rip-Other-Tools/DVD-Shrink.shtml")

[COLOR="RoyalBlue"]7. DVDDecrypter 3.5.4.0 download to desktop well need this later[/COLOR]

[http://www.mrbass.org/dvdrip/SetupDVDDecrypter_3.5.4.0.exe]("http://www.mrbass.org/dvdrip/SetupDVDDecrypter_3.5.4.0.exe")

[COLOR="RoyalBlue"]8.Microsoft DLL Files (contains msvcp60, riched20, quartz and mfc42 dlls) download to desktop well need this later[/COLOR]

[http://www.megaupload.com/?d=Q3LLABD3]("http://www.megaupload.com/?d=Q3LLABD3")

[COLOR="RoyalBlue"]Now we will install the above software[/COLOR]

[COLOR="RoyalBlue"]1. Intall microsoft dll files in wine[/COLOR]

Go to your wine system32 directory /home/yourname/.wine/drive_c/windows/system32

unzip the dll.zip extract all your files in the directory above and that all for this.

[COLOR="RoyalBlue"]2. Free dvd to install free dvd is pretty easy make sure you have [/COLOR]

Go to your wine program folder /home/yourname/.wine/drive_c/Program Files add a folder in there called FreeDVD know it should look like this /home/yourname/.wine/drive_c/Program Files/FreeDVD move your FreeDVD.exe to the FreeDVD folder you just made now take the icon picture for FreeDVD and move it to /home/yourname/.wine/drive_c/windows/temp/Free-DVD.GIF now you need to make a menu launcher so you can access it from your ubuntu menu. In your ubuntu menu open Main Menu located in Applications > Preferences > Main Menu on the left in the Menus: pick the Sounds & Video Section then click New Item then a create launcher window pops up you need to enter this info in the sections. In Name: FreeDVD in command: env WINEPREFIX="/home/yourname/.wine" wine "C:\Program Files\FreeDVD\FreeDVD.exe" in comment: FreeDVD Decrypter now click the top left icon to change it click the browse button and go to this location /home/yourname/.wine/drive_c/windows/temp/ and hit open now you need to click and highlight the Free-DVD.GIF icon and hit ok it should change in the top left corner then hit ok and close. You can test this software by going to your menu in the Sound & Video section find the software and click.

[COLOR="RoyalBlue"]3. RipIt4Me install[/COLOR]

Go to your wine program folder /home/yourname/.wine/drive_c/Program Files add a folder in there called RipIt4Me know it should look like this /home/yourname/.wine/drive_c/Program Files/RipIt4Me move your RipIt4Me.exe to the RipIt4Me folder you just made now take the icon picture for RipIt4Me and move it to /home/yourname/.wine/drive_c/windows/temp/RipIt4Me.gif now you need to make a menu launcher so you can access it from your ubuntu menu. In your ubuntu menu open Main Menu located in Applications > Preferences > Main Menu on the left in the Menus: pick the Sounds & Video Section then click New Item then a create launcher window pops up you need to enter this info in the sections. In Name: RipIt4Me in command: env WINEPREFIX="/home/yourname/.wine" wine "C:\Program Files\RipIt4Me\RipIt4Me.exe" in comment: RipIt4Me DVD Ripper & Decrypter now click the top left icon to change it click the browse button and go to this location /home/yourname/.wine/drive_c/windows/temp/ and hit open now you need to click and highlight the RipIt4Me.gif icon and hit ok it should change in the top left corner then hit ok and close. You can test this software by going to your menu in the Sound & Video section find the software and click.

[COLOR="RoyalBlue"]4. DVD Shrink install[/COLOR]

Right Click (Use the right button rather than left) on the DVD Shrink 3.2.exe Choose Open With wine or Open With Other Application or Wine Windows Program Loader. Scroll down until you see Wine Windows Program Loader. Left Click the Open button. After A Short Pause: your software&#8217;s installation program should start, and you can default on through the installation. now you need to make a menu launcher so you can access it from your ubuntu menu. In your ubuntu menu open Main Menu located in Applications > Preferences > Main Menu on the left in the Menus: pick the Sounds & Video Section then click New Item then a create launcher window pops up you need to enter this info in the sections. In Name: DVD Shrink 3.2 in command: env WINEPREFIX="/home/yourname/.wine" wine "C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe" in comment: DVD Shrink 3.2 DVD Ripper now click the top left icon to change it click the browse button and go to this location /home/yourname/.wine/drive_c/windows/temp/ and hit open now you need to click and highlight the 615b_dvd shrink 3.2.0.xpm icon and hit ok it should change in the top left corner then hit ok and close. You can test this software by going to your menu in the Sound & Video section find the software and click.

[COLOR="RoyalBlue"]5. DVDDecrypter install[/COLOR]

Right Click (Use the right button rather than left) on the DVDDecrypter.exe Choose Open With wine or Open With Other Application or Wine Windows Program Loader. Scroll down until you see Wine Windows Program Loader. Left Click the Open button. After A Short Pause: your software&#8217;s installation program should start, and you can default on through the installation. now you need to make a menu launcher so you can access it from your ubuntu menu. In your ubuntu menu open Main Menu located in Applications > Preferences > Main Menu on the left in the Menus: pick the Sounds & Video Section then click New Item then a create launcher window pops up you need to enter this info in the sections. In Name: DVD Decrypter 3.2 in command: env WINEPREFIX="/home/lordoshko-mike/.wine" wine "C:\Program Files\DVD Decrypter\DVDDecrypter.exe" in comment: DVD Decrypter now click the top left icon to change it click the browse button and go to this location /home/yourname/.wine/drive_c/windows/temp/ and hit open now you need to click and highlight the 48e9_dvddecrypter.0.xpm icon and hit ok it should change in the top left corner then hit ok and close. You can test this software by going to your menu in the Sound & Video section find the software and click.

[COLOR="Red"]Now you need to restart your computer for all software to set in.[/COLOR]

[COLOR="RoyalBlue"]Tweaking the above software to work correct in ubuntu[/COLOR] 
[COLOR="RoyalBlue"]
1. RipIt4Me tweaking & setup[/COLOR]

There have been quite a few who have received the "Failed to Copy" and "No DVD" message when clicking either Wizard Mode or 1-Click Mode. Hopefully, that's a thing of the past. You need to make some files and folders in wine to make this work properly open terminal and run this code

cd ~/.wine/drive_c/windows/temp && mkdir TempIFOs && echo "Welcome to RipIt4Me" > TempIFOs/RipIt4Me

This will make all the files & folders you need. Now you need to change some settings in RipIt4Me go to Logs/Settings > Preferences
Paths to programs
Path to Decrypter: C:\Program Files\DVD Decrypter\DVDDecrypter.exe
Path to Shrink: C:\Program Files\DVD Shrink\DVD Shrink 3.2.exe
Make sure it looks like this above.

[COLOR="RoyalBlue"]2. DVDDecrypter tweaking & setup[/COLOR]

Verify DMA is enabled for your DVD burner
hdparm /dev/hdd
It should say using_dma = 1 (on)
If not sudo /etc/hdparm.conf and append the following:
/dev/hdd {
dma = on
}
[COLOR="Red"]Now reboot and verify DMA is enabled[/COLOR]

[COLOR="Red"]Note DVD Decrypter uses DMA so I was able to rip at 11,200KB (8.1X) and also burn at 8X. However DVD Shrink does not use DMA mode[/COLOR]

For those of you having some difficulty getting drives recognized, after following the original post's directions, you might want to try this.

1. Open DVD Decrypter.
2. Click Settings | I/O
3. Check "ASPI",and hit OK.

When I originally installed, it was set to "SPTI - Microsoft". After selecting ASPI in I/O, everything magically worked, albeit somewhat slowly.

Also, I made sure that devices in $HOME/.wine/dosdevices were set up correctly to do this run this code in terminal.

cd ~/.wine/dosdevices
rm d:
ln -s /media/cdrom d: 

Also I recommend under Device tab to set it to Eject tray after read and write. Go to wine config to set up wine to run in windows version to NT 4.0

[COLOR="RoyalBlue"]3. DVDShrink tweaking & setup[/COLOR]

Edit | Preferences | Preview and set DirectX video renderer to Built-in Software Renderer this allows playback of video but no sound though. 

Because of this each time you open dvdshrink the left panel will be all grey. In DVDShrink just Maximize and Unmaximize Window to show left panel. Also you can resize it or move center bar to fix also. Yes you must do this each and everytime you open dvdshrink or just remove quartz.dll and do without video preview

Change the toolbar go to edit > toolbar buttons... then pick March by ZeF69 after changing the toolbar just close DVD Shrink and reopen it for it to display correctly.

Under File I/O tab you can disable burning with Nero. that it for DVDShrink it should be ready to go.

[COLOR="Red"]After all this restart your computer to let the setup and tweaks set in.[/COLOR]

[COLOR="RoyalBlue"]Decrypt & Rip your dvd in ubuntu you have 2 ways to do this Decrypt & Rip in wine or Decrypt in wine and rip in ubuntu[/COLOR]

[COLOR="RoyalBlue"]Decrypt & Rip in wine[/COLOR]

Here is how i do it all in wine you need to open RipIt4Me

[COLOR="Red"]Note: When using RipIt4Me the 1 click mode dose not work correctly when it want to pull up DVDShrink it freezes with a black screen so you need to use Wizard Method it good because RipIt4Me will run DVD Decrypter correctly kinda on auto pilot so you don't have to guess what to do which is nice.[/COLOR]

Now that we got that out of the way we can get started

1. Open click wizard mode the wizard mode step 1 will pop up click next then you will have a step 2 press Create PSL now you have step 3 click Rip DVD. Now DVD Decrypter window will pop up depending on the DVD i might pop up a DVD Decrypter sub window for region code usally it going to be 1 USA, Canada bt default click ok. It will start to crack the css and the open DVD Decrypter with the vob video files listed and highlighted in blue click the DVD, Green Arrow, & Hard drive button you'll get a progress bar that start let it do it's thing go for a coffe or smoke break it usally take 15 to 20 minute depending on your system. It will make a sound when it's finished and close DVD Decrypter. Now you have the RipIt4Me window updated to step 3b: IFO cleanup click Do It the process bar will start scanning VOB video files

[COLOR="RoyalBlue"]Decrypt in wine and rip in ubuntu[/COLOR]

[COLOR="RoyalBlue"]This process was tested with a new DVD I **[COLOR="Red"]bought[/COLOR]** Semi-Pro By New Line Home Entertainment 2008 with the newest encryption methods by the movie industry it should work on all new DVDs.[/COLOR]
[COLOR="Red"]
Final Note: Its a good idea to keep the proof of purchase on the DVD case to prove you bought the DVD you can find this on the plastic case on the back or in the cardboard case inside it best to just keep the case.[/COLOR]

[COLOR="Blue"]Best of luck on your DVD backups and hope all gose well please don't get your self in trouble do legal backups only hope this helped late.
P.S. i will update this guide as needed please let me know if you have updates[/COLOR]

:D

---

### Post by maverick340 on 2009-01-26
Its like you are pretty much using XP on ubuntu .. 
Nice guide though , but i think there may be other simpler ways :-)

---

### Post by mikeuhlik on 2009-01-26
Not really that I can see Linux dose not have a DVD Decrypter so that mean all new dvd with protection on it wont burn with any DVD ripper in linux like 

[COLOR="RoyalBlue"]Thoggen[/COLOR]

Rips DVDs and encodes them into Ogg files with Theora video and Vorbis audio.

[COLOR="RoyalBlue"]k9copy[/COLOR]

k9copy is a Qt based app that will make an exact copy of a DVD as an ISO file or as the normal DVD folder structure on the destination drive. It can also shrink and/or encode your DVDs to different formats such as AVI/MPEG-4, MPEG-2, Flash Video (FLV), Real Video and QuickTime.

[COLOR="RoyalBlue"]dvd::rip[/COLOR]

A DVD ripper that can also encode the ripped DVD to VCD/SVCD or AVI/MPEG-4 and split the file into 700MB chunks on the destination drive.

[COLOR="RoyalBlue"]ogmrip[/COLOR]

An application for ripping and encoding DVD into AVI, OGM, MP4 or Matroska files using lots of audio and video formats (Vorbis, MP3, PCM, AC3, DTS, AAC, MPEG-4 ASP, MPEG-4 AVC, Theora). OGMRrip calculates cropping parameters and scaling factors and supports multiple audio and subtitles streams encoding.

[COLOR="RoyalBlue"]HandBrake[/COLOR]

HandBrake is a DVD to MPEG-4 converter. An i386 binary is provided on the HandBrake website for 32bit Linux users, and the source code is available which compiles and runs in x86_64 and PowerPC Linux. HandBrake for Linux supports encoding in MPEG-4, including H.264. 

and others dont Decrypt so your ubuntu ripper will give errors when you try to backup and fail so you need to decrypt it first then run it in your favorite ripper and it should work.

[COLOR="Red"]Note that with some recent DVD films, *all* current Linux DVD rippers have problems reading the disc due to newer copy protection schemes such as ARccOS or RipGuard. The same is true even of the latest version of DVDshrink on Windows, and only certain tools like DVD2HDD, DVD Decrypter, and AnyDVD (Windows programs) can handle the newer copy protection mechanisms.[/COLOR]

That is why I made this guide DVD2HDD has bugs and wont work correctly on ubuntu anydvd wont work on wine so pretty much until you get a good DVD Decrypter for linux this is the only successful way I  have found to get the job done.;)

---

### Post by SqRt7744 on 2009-01-26
the reason the programs you listed won't decrypt is because you don't have the libdvdcss2 library installed (can't ship in default ubuntu because of US law "digital millenium copyright act".

see:
[http://www.medibuntu.org/](http://www.medibuntu.org/)
for install info. Another really good guide in the forums is this:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Thoggen is great, it's what I use. It has a clean interace.

But I'm not sure about the newest of the new DVDs, perhaps they have copy protection that libdvdcss2 can't break. It hasn't failed me yet however.

Finally, I'd just like to take the opportunity to mention the program DeVeDe, which you can use to burn mpeg, ogg, avi files etc. to a DVD or VCD that will play in your dvd player. Pretty handy...

p.s. you certainly don't have to restart your computer after installing the software you mention. Not after installing the linux software (wine, k9copy & k3b), nor after installing the windows software (although you may have to issue 'wineboot' for the windows software (alt-F2)). You will have to reboot after changing the DMA access however.

---

### Post by pnutzh4x0r on 2009-01-26
> **SqRt7744 said:**
> the reason the programs you listed won't decrypt is because you don't have the libdvdcss2 library installed (can't ship in default ubuntu because of US law "digital millenium copyright act".

Even if you have libdvdcss2 installed, you still can't rip DVDs encrypted with new protection schemes such as 
ARccOS or RipGuard as mentioned earlier.  That said, for the most part, HandBrake works fine for me with most old and new disks.  For the select few that do no work, I simply use HDDVDDecrypter from DVDFab in Wine and then HandBrake the output video_ts.

---

### Post by mikeuhlik on 2009-01-26
The libdvdcss2 library copyright protection is only for css protection and dose not work for any other method of newer copy protection schemes such as ARccOS or RipGuard and the sole purpose for this is to just let you play css protected DVDs not backup you need libdvdcss2 library to give support to your player to it can properly play the DVD on your pc but it also helps when backing up. This is a free way to do it with out having to buy software like DVDFab or AnyDVD a total free way to backup your dvd.

A free way the way the ubuntu worlds should be.
:popcorn:

---

### Post by zaphodbblx on 2009-02-10
I just couldnt't get ripit4me to work( it keept just disappearing after I clicked the wizzard button) but after many fustrating hours this is what I did


1)put ripit4me in this folder "/home/yourname/.wine/drive_c/windows/system32"

2)find the mfc.42 dll from dlldump.com the dll's .com version wont work 
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/M/mfc42.dll/6.0.400/download.html)


3) place this dll in" /home/yourname/.wine/drive_c/windows/system32"

4) make sure you run the "/.wine/drive_c/windows/temp && mkdir TempIFOs && echo "Welcome to RipIt4Me" > TempIFOs/RipIt4Me"

you can make a copy of the ripit4me.exe and place it on your desktop

now if you have finally gotten your dvd decrypter and shrink settings taken care of!

 1) insert your disk***(that you own...you have been warned)*** and let the disk mount 
2) click the exe.

ignore all the banter and enjoy

like a slice of fried gold!

:popcorn:

ps this work through is for 8.04 last updated 2/9/09

---

### Post by halibaitor on 2011-06-25
I have tried to follow your instructions, but don't understand step #4.  I did put the .exe in the system32 folder, along with the .dll you were talking about.

I run the .exe from there, but still can't get RipIt4Me to work.  I'm, using 10.04.2

Is there something else that needs to be done?

---

### Post by handy on 2011-06-25
If I strike a video that I can't rip with HandBrakeCLI then I'll just download it. 

It is so much quicker, simpler & less troublesome than installing all of these pieces of software & jumping through all of their hoops. imho anyway.

If you were going to rip it anyway, what's the difference?

The only people that this guide would be good for are those that don't have a suitable internet account.

Nice guide though. ;)

---

### Post by halibaitor on 2011-06-26
> **handy said:**
> 
If you were going to rip it anyway, what's the difference?

The only people that this guide would be good for are those that don't have a suitable internet account.


The difference being that to get a full resolution video out of it, your download would have to be over 4 GB in size.  Maybe your internet connection is a lot faster than mine...  ;)

If I could get RipIt4Me to work in WINE, I would have everything I want in a computer, and do it without Windoze.

Yeah I know.  It's WINE not Whine...  :lol:

---

### Post by handy on 2011-06-26
I'm happy with the resolution that I get out of the 1GB vids that I make with HandBrakeCLI. There are often a range of sizes available on the net.

I use a 1920x1200 24" display. Not owning a TV I don't know about the problems of displaying via the enormous size TV screens that people seem to think that they must have these days.

As far as download speed, I guess that comes down to just how slow your internet speed is. 1500kbs speed is plenty good enough to work with, from my experience anyway.

---

### Post by halibaitor on 2011-06-26
On a 24" display, I can see your reasoning.  

My internet speed is 1meg, and my TV set is a 42".  So my situation is a bit different from yours. :wink:

I'm still trying to figure out how to use RipIt4Me.  Others seem to have figured it out, but I haven't seen anything recent.  I need it to run in Ubuntu 10.04.2.  I have a spare computer that is running Win XP, and RipIt4Me works there.  It is an awesome program.  My "main" computer doesn't even have Windoze on it, which is why I would like to figure this thing out.

---

### Post by BicyclerBoy on 2011-06-26
IMO so could all be BS.
From side-by-side testing with same brand DVD drives..
DVD ripping/playback in 10.04 is not as good as 11.04.

All these have some effect:
0. DVD obfuscation of file structure, bad/missing sectors etc
1. optical drive brand/firmware
2. kernel version
3. libdvdcss
4. libdvdread4
5. libdvdnav  (static linked)
6. Application version

Explanation
0. This is the real problem with playback, navigation of the data structure.
DVD-video disc does not obey the rules of a computer filesystem.
1. hard to prove , some need regionset, RPC 1 firmware would be good
2. DVD & CD mount problems, filesystem validation issues.
3. 4. These have been updated in 11.04
5. this is the most important lib after css. statically linked so need an up-to-date build.
6. as above

DVD::Rip does not work very well because the build is years old.

For Linux access to troublesome DVDs..
The best foss app is HandBrake from nightly builds. this gets you the latest libdvdnav.
Maybe the most capable app is makeMKV.

Further Comments
My observation is as the DVD discs are getting harder to access, the disc have more junk filling them up & the video PQ is getting worse because of compression. All this is intended to push the consumer to Bluray.
The PQ on the recent release movies (DVD) are generally complete rubbish.
The best protection for studios comes from Bluray's complex protections & the shear size of the datafiles.

---

### Post by Hermansuco on 2011-07-03
Once wine is installed, wouldn't dvd43 should work to decrypt dvds?

:popcorn:

---

### Post by halibaitor on 2011-07-03
> **Hermansuco said:**
> Once wine is installed, wouldn't dvd43 should work to decrypt dvds?

:popcorn:

Depends on what you want to do with the results.  If you want to convert the movie to another format, then dvd43 might suit your needs just fine.  I want to create DVD backups, which is a whole different thing, and RipIt4Me works very well for what I want to do...  YMMV

---

