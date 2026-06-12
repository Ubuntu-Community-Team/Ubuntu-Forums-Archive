---
title: "Kodak Camera will not mount"
date: 2009-05-18
forum: Multimedia Software
---

### Post by egwest on 2009-05-18
Info:
Bus 006 Device 005: ID 040a:05b8 Kodak Co. Digital Camera

Kodak Digital Camera V803

Here is my problem, up until 8.10 I could connect my camera and I could import the pictures using Piasca, Camera or F-Spot or just go in to the folder and drag and drop over to my harddrive.

But after updating to Jaunty, my camera will not mount anymore and I get the following message:

Unable to mount Kodak Co. Digital Camera
Error initializing camera: -60: Could not lock the device

Anyone got any ideas?

I can still mount it on my Acer Netbook just fine, it is only in Jaunty that I am having problems.

---

### Post by xc3RnbFO8P on 2009-05-18
Check if you got **gvfs-bin** installed (Synaptic Package Manager).

---

### Post by egwest on 2009-05-18
> **Ringi said:**
> Check if you got **gvfs-bin** installed (Synaptic Package Manager).

yes, they are all installed

gvfs-bin
gvfs-fuse
gvfs
gvfs-backends
libgvfscommon0

---

### Post by xc3RnbFO8P on 2009-05-18
You could reported it here:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083")

---

### Post by egwest on 2009-05-18
> **Ringi said:**
> You could reported it here:
[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083")

That was my next step, thank you. I just wanted to see if the problem had already been discovered and fixed first.

Thank you for your response.

---

### Post by mrmark24 on 2009-06-14
I, too, have a Kodak digital camera (model C340).  I do not use F-Spot; instead, I use Showfoto, which has never given me any problems under GNOME in the past.  This seems immaterial.

Maybe I'm reading the Launchpad replies incorrectly, but I got the feeling people were saying this is an issue with F-Spot; I don't think this is the case.

I've set my Ubuntu computer to "Do Nothing" when a digital media, such as a camera, is detected---I prefer to manage things on my own.  It gives me a somewhat different error message it gave egwest; mine says:

Error initializing camera: -1: Unspecified error

My camera's communication/indicator light then begins to blink red and, for a few minutes after I unplug the USB, the camera tries telling me the batteries are dead, even though they're brand new Lithiums!

From 7.04 all the way through 8.04 I never had this problem (never tried it using 8.10).  My thought is that it's a bug with Jaunty (the OS) versus a program installed, or downloaded and used with, it :-\  Where is the recourse with an OS issue???

---

### Post by steelcommuter on 2009-06-14
I'm having the same problem, too.  I can't mount the Z7590 Kodak camera that mounted fine in Hardy Heron.  This is pretty frustrating, and if anyone hears of a fix please post it to this thread.

---

### Post by peterx14 on 2009-06-17
Same problem as the original post for me -- I'm trying to connect a Kodak C330 camera.

---

### Post by wltdwiz on 2009-07-04
if your camera uses a sd card just get a usb card reader problem solved 
this worked for me;)

---

### Post by majdi on 2009-11-08
I'm running Ubuntu 8.04 (hardy) and I'm trying to connect my Kodak EasyShare M340 via USB but ubuntu will not detect it. Any fix for this?

---

### Post by Cobracommand0 on 2009-11-10
Same error with a Kodak M1033, it'd be nice to figure this one out!

---

### Post by HappyFeet on 2009-11-10
> **majdi said:**
> I'm running Ubuntu 8.04 (hardy) and I'm trying to connect my Kodak EasyShare M340 via USB but ubuntu will not detect it. Any fix for this?

As suggested in the post above yours, use a usb card reader.

---

### Post by fiver22 on 2009-11-12
Same problem with my Kodak DX4530 under 9.10 and 9.04. While a card reader might work it's not the fix I was hoping for. Judging by search results this issue is affecting alot of people. I'm surprised not to have come across a fix yet -or even an explanation of the problem. Cannot open via Places>Computer either so I don't think it's only an F-Spot issue.

---

### Post by majdi on 2009-11-14
> **HappyFeet said:**
> As suggested in the post above yours, use a usb card reader.

thanks HappyFeet, 

So are you saying there is no other fix for this?

---

### Post by DavidFourer on 2009-11-17
I got this error trying to download phtos:
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
someone suggested closing the software and unmounting the camera (look under places in the main menu, then right-click on the camera and select unmound, or something like that)
Then load your favorite photo software, such as gthumb image viewer or f-spot photo manager, from the applications menu.  That was a simple fix for me.

Before Karmic, I had similar problems with older versions of Ubuntu, something to do with permissions for the usb devices.  I set the permissions for some dev file, but can't figure out what I did.

---

### Post by bokkie on 2009-11-20
> **fiver22 said:**
>  Cannot open via Places>Computer either so I don't think it's only an F-Spot issue.

I have the same problem with Karmic (9.10) and a Kodak DX6490.  Tried removing F-Spot and installed Gthumb instead, but problem persists.

---

### Post by mattman on 2009-11-20
I'm having the same problem in Karmic with two different Kodak cameras. A DX3600 and DX4330.

---

### Post by fiver22 on 2009-11-24
This is a summation of the info in this thread with a few new pieces of information.

Camera will not mount. Specific errors: 

"Unable to mount Kodak Co. Digital Camera
Error initializing camera: -60: Could not lock the device"
likely related (when Gnome is set to 'Do Nothing' when it detects the camera): "Error initializing camera: -1: Unspecified error"
Cameras affected: Kodak EasyShare ZD710, Kodak EasyShare DX4530, Kodak EasyShare M340, Kodak DX6490, Kodak V803, Kodak C340, Kodak Z7590, Kodak C330, Kodak M1033, Kodak DX3600, Kodak DX4330. -So all cameras mentioned are Kodak -is that significant, or is it just because Kodaks are ubiquitous?

For me, at least, F-Spot crashes as soon as it loads, and gThumb crashes once I select File>Import Photos...
Camera does not mount in Gnome.
Both my cameras (Kodak EasyShare DX4530, and Kodak EasyShare ZD710) worked at one point with 9.04. Then they both stopped working with the errors described (Unable to Mount/Could Not Lock Device, etc.) -I assume it was after an update but not sure which one (suspect it might have been a kernel update, but not positive). Now neither camera works with 9.04, or 9.10 (separate machines).

Suggestions that have failed most people so far:
-Don't use F-Spot, use (insert any photo manager) here. -I've tried many and this doesn't seem to help -Note that the error occurs in Gnome upon detection of the camera.
-Unmount the camera manually then launch a photo manager -Again, Gnome isn't mounting the cam. in the first place.
-It's an F-Spot issue. -It doesn't seem likely (see above).
-Use a card reader. -this is a non-fix, a temporary work-around, at best, that isn't an option for some people.

I *really* find it weird that this problem seems to affect so many users yet there seems to be no solution yet. I'd settle for an explanation of 'why' it's happening at this point. I think it's pretty likely that someone knows what's happening with this issue -we're just not finding that info.

---

### Post by harmonica98 on 2009-11-24
I have found a partial solution here from Petr:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681)

> Quick fix - run script in terminal "sudo killall gvfs-gphoto2-volume-monitor" then connect the camera.

Long-term fix (Prevent the process from starting) - run script in terminal "sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor"

Then go to System -> Preferences -> Removable drives and media -> Cameras and remove the "f-spot-import" with "gthumb --import-photos" or etc...The quick fix works for me, have just tried it.  However, there is no 'Removable drives and media' menu in Karmic so I don't know how to complete the action.  Hopefully someone more knowledgeable can chime in.

Tom

---

### Post by fiver22 on 2009-11-24
Tried "sudo killall gvfs-gphoto2-volume-monitor" and am still running into the same problems (upon launching F-Spot crashes, when selecting Import gThumb crashes).
Damn -wish it would have worked for me. 
(I'm curious where Removable drives and Media went, too.)

> **harmonica98 said:**
> I have found a partial solution here from Petr:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681)

The quick fix works for me, have just tried it.  However, there is no 'Removable drives and media' menu in Karmic so I don't know how to complete the action.  Hopefully someone more knowledgeable can chime in.

Tom

---

### Post by chris282 on 2009-11-30
Hi folks, first time caller here.

I'm also experiencing this problem - Karmic 9.10, Kodak Easyshare C300.

No luck with the quick fix so I'd appreciate any updates.

Cheers,

Chris.

---

### Post by spillz on 2009-11-30
> **chris282 said:**
> Hi folks, first time caller here.

I'm also experiencing this problem - Karmic 9.10, Kodak Easyshare C300.

No luck with the quick fix so I'd appreciate any updates.

Cheers,

Chris.

try opening nautilus (file manager) then goto:
edit->preferences->"media" tab->photos->"open folder"

plug in your camera and see if you can browse your camera from nautilus. if that is successful then try switching back to your import tool...

report back what you find.

---

### Post by chris282 on 2009-12-01
Hi spillz,

Many thanks for both a swift and an effective response!

Having switched my preferences to "open folder" I still see the error message "Error initialising camera: -60: Could not lock the device" although I am able to browse my photos.  

I can also seemingly open them using F-Spot, though if I try to do anything with them, such as zoom or rotate, either nothing happens or I get an error message along the lines of "Could not load image '000_0004.JPG'. Failed to open input stream for file" - after which point I am unable to open them again.

If I avoid F-Spot altogether and open the photos in Gimp, it's all smiles and sunshine.

After checking that I could open the photos using Nautilus I switched preferences back, and reverted to the original problem - "Error initialising camera: -60: Could not lock the device" and F-Spot crashes.

From here, it seems to be an F-Spot issue, but I know very little indeed and am happy enough to be able to access my photos. :D

Thanks again, and best wishes,

Chris

---

### Post by spillz on 2009-12-01
> **chris282 said:**
> Hi spillz,
I can also seemingly open them using F-Spot, though if I try to do anything with them, such as zoom or rotate, either nothing happens or I get an error message along the lines of "Could not load image '000_0004.JPG'. Failed to open input stream for file" - after which point I am unable to open them again.


try f-spot again, but this time:
* have the "open folder" setting in media handling activated and let the camera mount
* manually unmount the camera from nautilus (click the camera's "eject" button in the nautilus sidebar) 
* start f-spot and try importing.

> 
Having switched my preferences to "open folder" I still see the error message "Error initialising camera: -60: Could not lock the device" although I am able to browse my photos.

this is still a bug. shouldn't happen. I've had this happen in Jaunty a few times only to have the problem go away...

---

### Post by chris282 on 2009-12-01
Same problem again, I'm afraid.

[quote=spillz;8422889]try f-spot again, but this time:
* have the "open folder" setting in media handling activated and let the camera mount

As soon as I attach the camera I'm seeing that original error message, though I'm now able to browse the photos.

* manually unmount the camera from nautilus (click the camera's "eject" button in the nautilus sidebar) 

I note that there are two identical Kodak C300 icons displayed - that may be irrelevant, but perhaps it isn't.

* start f-spot and try importing.

Importing from source: Kodak C300, and F-Spot crashes.

---

### Post by Quamper on 2009-12-08
For what it's worth I'm in the same exact boat as chris282. I turned of the importing and I can at least browse the files but I still get an error everytime I turn the camera on plugged into the pc. Same deal as well with two different icons on the desktop

---

### Post by chris282 on 2009-12-09
Same/similar camera?
 
- Chris

---

### Post by bokkie on 2009-12-09
> **Quamper said:**
> For what it's worth I'm in the same exact boat as chris282. I turned of the importing and I can at least browse the files but I still get an error everytime I turn the camera on plugged into the pc. Same deal as well with two different icons on the desktop

Same for me, but with Kodak DX6490 camera, and using gThumb.  

FWIW, about the two icons that you see: One is for the internal memory of the camera, and the other is for the removable memory.

---

### Post by AaronWyatt on 2009-12-14
This is not just a problem with f-spot.  I posted the following to [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/258083)

If anyone can suggest a better place for this bug post please let me know.  Maybe gvfs-mount?

This is also a problem in Google's Picasa version 3.0.5744-02 (this is the testing version which uses wine) with a Kodak EasyShare C813 camera.

Picasa is default application to use to open multimedia folders, and therefore the symptoms are:

Connect camera via USB cable and turn on.

Receive error: Unable to mount KODAK EasyShare C813 Zoom Digital Camera; Error initializing camera: -60: Could not lock the device.

Two icons for the camera are present on the desktop.  The permissions tab under properties for one icon shows the error: "The permissions of "store_00010001" could not be determined."  The other shows the same error message but instead with "store_00020001"

gvfs-mount -l  shows the following lines:

Volume(0): KODAK EasyShare C813 Zoom Digital Camera
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
  Mount(0): KODAK EasyShare C813 Zoom Digital Camera -> gphoto2://[usb:005,004]/store_00010001
    Type: GProxyShadowMount (GProxyVolumeMonitorGPhoto2)
Volume(1): KODAK EasyShare C813 Zoom Digital Camera
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)
  Mount(0): KODAK EasyShare C813 Zoom Digital Camera -> gphoto2://[usb:005,004]/store_00020001
    Type: GProxyShadowMount (GProxyVolumeMonitorGPhoto2)
Mount(2): KODAK EasyShare C813 Zoom Digital Camera -> gphoto2://[usb:005,004]/
  Type: GDaemonMount

---

### Post by Mlava on 2009-12-20
HELP!!

I've tried loading photos from my Kodak EasyShare C340 for months.
It doesn't work!!  ](*,)
I am going home for Christmas and would like to show my family some photos
but can't unload them from the camera onto Ubuntu.

Please help, I am also complete beginner.
I see many people have this problem.
Please step me through how to solve it.
Thank you!!!!

---

### Post by Cotopaxi on 2009-12-27
What I found out so far for my Kodak M340:

You can't install the Windows Software under Wine.

The Macintosh Software from the Kodak web-page can't be installed either.

Web-page for the M340:

[http://wwwuk.kodak.com/global/en/service/downloads/dln_ekn036196.jhtml?pq-path=14648/14649](http://wwwuk.kodak.com/global/en/service/downloads/dln_ekn036196.jhtml?pq-path=14648/14649)

So far, no bloody way to connect the camera to a (K)ubuntu laptop! Set's me off, actually!

---

### Post by Cotopaxi on 2009-12-27
One more comment:

the page for selecting your individual model is this one:

[http://www.kodak.com/eknec/PageQuerier.jhtml?pq-path=10&pq-locale=en_GB]("http://www.kodak.com/eknec/PageQuerier.jhtml?pq-path=10&pq-locale=en_GB")

---

### Post by Cotopaxi on 2009-12-27
One more data:

I installed both &#8220;gtkam&#8221; and &#8220;digikam&#8221; (both in the repositories) and it did not work for my camera (Kodak M340).

Anyhow, there are many camera models the two softwares work with, so it is well worth giving them a try!

Both softwares seem to be based on &#8220;gPhoto&#8221;

Their webpage:

[http://www.gphoto.org](http://www.gphoto.org)

From their faq page:

[http://www.gphoto.org/doc/manual/FAQ.html#FAQ-easyshare-dock](http://www.gphoto.org/doc/manual/FAQ.html#FAQ-easyshare-dock)

&#8220;I have a Kodak EasyShare&#8482; camera, and gphoto2 can't detect it. What shall I do ?
	
Just press the button on the dock so that the USB device gets detected by the system and that gphoto2 software can detect it.&#8221;

I hope this helps!

---

### Post by blueridgedog on 2009-12-28
Same issue here.  M753.

From /var/log/messages:

```
Dec 28 18:14:53 Ripstop kernel: [175676.700012] usb 3-2: new full speed USB device using uhci_hcd and address 3
Dec 28 18:14:54 Ripstop kernel: [175676.999143] usb 3-2: configuration #1 chosen from 1 choice
```

and:

```
james@Ripstop:~$ lsusb
Bus 003 Device 003: ID 040a:059f Kodak Co. Digital Camera
```

Device is not recognized and can't be mounted manually.  It opens fine in a windows VM.  Not my camera, but one I picked up for my kid.

---

### Post by trx64 on 2009-12-29
> **harmonica98 said:**
> I have found a partial solution here from Petr:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/331681)

Quick fix - run script in terminal "sudo killall gvfs-gphoto2-volume-monitor" then connect the camera.

Long-term fix (Prevent the process from starting) - run script in terminal "sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor"

Then go to System -> Preferences -> Removable drives and media -> Cameras and remove the "f-spot-import" with "gthumb --import-photos" or etc...

The quick fix works for me, have just tried it.  However, there is no 'Removable drives and media' menu in Karmic so I don't know how to complete the action.  Hopefully someone more knowledgeable can chime in.

Tom

Worked form me (Kodak EasyShare Z915). It's a bug in Ubuntu, Mandriva recognized my camera out of box.

Try to right-click in the system menu, and select "Edit Menus". The "Removable drives and media" is probably there, it's just disabled. Homever, you can execute it with:

$ gnome-volume-properties

---

### Post by trx64 on 2009-12-30
> **trx64 said:**
> 
Try to right-click in the system menu, and select "Edit Menus". The "Removable drives and media" is probably there, it's just disabled. Homever, you can execute it with:

$ gnome-volume-properties

Sorry, in Karmic, that package was removed from default install. Install it with:

$ sudo apt-get install gnome-volume-manager
(it will remove Brasero so reinstall it with)
$ sudo apt-get install brasero

---

### Post by Girya on 2009-12-31
I have the same problem; I get an error message about not getting a lock on the camera. To work around the error I installed the command line app gphoto2. then I ran the script that kills gvfs:

```
sudo killall gvfs-gphoto2-volume-monitor
```
plug in the camera 
cd into a directory where you want the photos downloaded and run

```
gphoto2 --get-all-files
```

and all the photos downloaded.

---

### Post by grandmaster-g on 2010-01-04
After going from 8.04 to 9.10, my Kodak CX7430 would not mount.. (Grrrr).. 
I read through all 4 pages of posts, with no answers, so I embarked on my own thoughts.

I opened up Synaptic Package Manager, and searched for "camera", and found a file called "GTKAM", and it said that is was to connect your camera to Ubuntu.  I have been using F-spot photo manager for that in the past.  

I clicked to install GTKAM (from the Synaptic Package Manager) and installed it.  I still had F-Spot up and running, and the camera still hooked up but OFF.  Once the package was installed, and doing nothing more than turning the camera on, PRESTO!  It WORKED!!!!!!

Now, I can not guarentee it will work with your brand, but who knows?  Perhaps since GTKAM (or gtkam) was NOT installed with the upgrade to 9.10, that is all that is needed!

Try it, and let me know if it works, God knows the frustrations we all shared with this problem!

Good Luck!

GrandMaster-G

---

### Post by Cotopaxi on 2010-01-08
Grandmaster-g:

Your camera Kodak CX7430 is listed as &#8220;supported&#8221; in the &#8220;gphoto&#8221; library.

The link:

[http://www.gphoto.org/proj/libgphoto2/support.php](http://www.gphoto.org/proj/libgphoto2/support.php)

Every camera, that is listed there, should work without problem, either in &#8220;gtkam&#8221; or &#8220;digikam&#8221;, which are both based on gphoto.

The problem is, what do those people do, whose camera is NOT listed there?

Anyhow, I would recommend ANYONE to look up, if his model is listed there and then get either the &#8220;gtkam&#8221; or the &#8220;digikam&#8221; application.

Anyone, who PLANS TO BUY a new digital camera, I would also recommend him to look up if his model is supported, so he knows he will have no hassles!

Good luck!

---

### Post by Cotopaxi on 2010-01-08
Guys, this one is amazing!:P

My &#8220;Kodak M340&#8221; is not listed in the &#8220;gphoto2&#8221; list of supported cameras, but I switched the camera ON and in PHOTO SHOOTING MODE, connected it afterwards to the computer and it was recognized immediately by &#8220;digikam&#8221;.

My system is Kubuntu 9.10

Good luck

---

### Post by titianmom on 2010-01-20
FWIW, I'm having the same problems with a Kodak Z612 on Mint 8 (a spin off of Ubuntu).
 
I'll try some of these ideas on mine.  At least I know it isn't me that's brain dead or something.
 
Kim
 
(First couldn't detect the camera, then io-library ('Could not lock the device'): Camera is already in use.)

---

### Post by DougZ on 2010-01-20
I am having the same problem with a Fuji FinePix F50fd.

Originally I came on here looking because I was having issues using the camera when 2 users are logged in at the same time.

The camera would mount on the inactive user (even though all options to automount are disabled) and the active user would get error about not being able to lock the device.

Switching to the other user, unmounting the device, switching back to other user, manually launching application and choosing to import worked.

But what a pain.  

After reading this thread realized maybe it wasn't the fact that I have 2 users going, but is more serious.

Now I'm trying it with just 1 user logged in and its actually worse.

Upon plugging in the camera I get 2 error messages:

> The folder contents could not be displayed
Operation not supported

> An error occurred in the io-library ('Could not lock the device'): Camera is already in use.

---

### Post by sjnims on 2010-02-18
Same issue here, I Kodak Z7950 camera...error -60, all solutions posted here so not fix!

---

### Post by blueridgedog on 2010-02-19
I just dumped the camera...Canon from now on.

---

### Post by sjnims on 2010-02-19
> **blueridgedog said:**
> I just dumped the camera...Canon from now on.

Not an option...

---

### Post by Sushi_Sue on 2010-02-21
Hi, everybody !

Maybe I FOUND A SOLUTION for this:

I have a Nikon P50 and I tried to import the pics
either with gtkam either with F-spot.
Actually I prefer F-spot, so I tried to fix it. 

I tried to mount/unmount the cam several times,
then I checked gvfs and I got crazy !

Here what I did :

1- unistall f-spot with apt-get 
2- install libflickrnet2.1.5-cil_25277-6_all
3- install libgnome2.0-cil_2.20.1-1_i386.deb
4- install libgtkhtml3.16-cil_2.20.1-3_all.deb
5- install f-spot_0.4.4-1_i386

you can find these *.deb  here --> [http://packages.debian.org/](http://packages.debian.org/)

then 
6- turn on the camera and unmount it ( from shell or from Desktop)
7- open f-spot and import the camera

By the way, I am not sure if this is the correct way, nevertheless it worked
out very well for me .

Easy and Dirty... and probably also brute !!!

Bye

---

### Post by b9k9kiwi on 2010-02-21
I have two Kodak cameras (the model numbers don't matter) neither of which have ever mounted successfully in any version of Ubuntu.

My understanding is that Kodak employ a non-standard USB protocol designed to interface with Kodak Easyshare software in a Windows environment.  The Kodak philosophy is still very 'snapshot' orientated, hence the obsession with Easy share and sharing photos.  Kodak are aware of the issue we are discussing, but don't see it as a problem as they have no intention of producing Linux software.

This info comes from more than one reliable source in professional photography.  I am open, of course, to the possibility of there being counter opinion to this.

Nevertheless, and with this view in mind, there are instances where Kodak cameras successfully connect to Linux software - so, it is therefore seen that failure to connect is a software problem when it is actually a camera firmware problem.

This results in Linux users spending time and energy trying to fix a Linux/software problem that does not, in effect, exist - it is successful connection that is intermitant and user dependant, not unsuccessful connection.

I have given up trying to connect my Kodak cameras to my Linux box as they talk quite happily to Easyshare software on my Windows box.

This is just my take on this issue which is easily fixed, as it happens, by replacing Kodak cameras with some other brand with a proven record of reliable connection - which is what I intend to do.

By the way, one of those who advised me of the non-standard USB protocol quietly said, in conclusion (and with a benign smile on his face), "of course, any decent photographer wouldn't be caught dead with a Kodak".

---

### Post by Laeys on 2010-03-13
My kodak (C653) is on the list of supported models yet it still doesn't work with digikam or gtkam.  After getting the error -60 and turning on gtkam it says "cannot initialize camera"
Bummer time

---

### Post by no2498 on 2010-03-14
Laeys does you cam use fire wire i do not think the programs you are trying to use let usb cam work 
try takeing the card out an plug it in turn it on see what happens 
put the card back in plug the cam back in turn it on see what happens
some thing should come up on the desk top window

---

### Post by philip5 on 2010-03-15
> **Laeys said:**
> My kodak (C653) is on the list of supported models yet it still doesn't work with digikam or gtkam.  After getting the error -60 and turning on gtkam it says "cannot initialize camera"
Bummer time
Do you use the latest version of libgphoto2? libgphoto2 is usually the library that handles communications with your camera in most Linux software if it's a camera that use the ptp2 protocol. I think that would help in your case. Either install it your self or even better use an updated package for your Ubuntu version. If you want then you'll find the latest version of libgphoto2 on my Launchpad PPA that you can read more about in my signature.

---

### Post by Laeys on 2010-03-15
Thanks philip5, I'll try that.

---

### Post by peterx14 on 2010-03-25
I just tried my Kodak C330 with the 10.04 beta 1 live CD [NOTE: I just booted that CD and did not attempt to update it], and it *still* has the same bug! That said, it did manage to open F-spot and show the photos on the camera... but it took a long time to get there.

Also for information, this camera did work perfectly with older Ubuntu releases -- I think it was probably as far back as 7.10 when it worked right.

If the newer libgphoto2 libraries are working correctly, does anyone know if these are likely to make it into 10.04 final?

---

### Post by philip5 on 2010-03-26
> **peterx14 said:**
> I just tried my Kodak C330 with the 10.04 beta 1 live CD [NOTE: I just booted that CD and did not attempt to update it], and it *still* has the same bug! That said, it did manage to open F-spot and show the photos on the camera... but it took a long time to get there.

Also for information, this camera did work perfectly with older Ubuntu releases -- I think it was probably as far back as 7.10 when it worked right.

If the newer libgphoto2 libraries are working correctly, does anyone know if these are likely to make it into 10.04 final?
I don't think there will be any updates from what's already in Lucid now if it's not some security/bugg fix updates or something like that in form of patches. The window for Lucid is by now pretty closed I think.

---

### Post by harryscode on 2010-03-27
> **spillz said:**
> try opening nautilus (file manager) then goto:
edit->preferences->"media" tab->photos->"open folder"

plug in your camera and see if you can browse your camera from nautilus. if that is successful then try switching back to your import tool...

report back what you find.

Love you man!!!.. i did what you wrote and works. Still appears the message of error 60 can't mount, but opens nautilus with the photos in the folders. So I can work and download those into my pc. Thanks again and appologize for my english.

---

### Post by Cotopaxi on 2010-03-30
Sorry guys, let me just repeat what I found out so far:

0)
If you have the camera switched off and you plug it into the USB port, the camera only goes into BATTERY CHARGING MODE without any identification of the operative system!

So, if you want the camera to be recognized by the operative system:

1)
BEFORE plugging the camera into the computer's USB port, SWICH IT ON and put the camera on PHOTO SHOOTING MODE! 

2)
NOW you plug the camera into the USB port of your computer and the camera should be recognized immediately. If you have &#8220;gphoto2&#8221; and &#8220;gtkkam&#8221; (for Ubuntu) or gphoto2 and &#8220;digikam&#8221; (for Kubuntu) the respective program opens up immediately and you are ready to go!

Good luck!

---

### Post by chris.olive on 2010-03-30
Same problem all worked fine with 9.04 but 9.10 with Nikon Coolpix 990,  Picasa or F.spot.
Picasa informs me " no pictures on card" Oh yes there are.
F spot cannot mount Nikon 990.
O/S tells me it does not have drivers for your camera?!
Any ideas meanwhile I will beaver away looking for an answer.

---

### Post by philip5 on 2010-03-30
> **chris.olive said:**
> Same problem all worked fine with 9.04 but 9.10 with Nikon Coolpix 990,  Picasa or F.spot.
Picasa informs me " no pictures on card" Oh yes there are.
F spot cannot mount Nikon 990.
O/S tells me it does not have drivers for your camera?!
Any ideas meanwhile I will beaver away looking for an answer.
I can only give the same general advice to you too. Get an updated version of libgphoto2 as that is the lib that handles all communication with your camera even if you use f-spot, gphoto2, digikam or something else. Cameras that use libgphoto2 usually doesn't show up in the same way as cameras that work as any other usb-media (i.e work like usb-memory, etc) as they usually need some kind of application that browse and commit tasks with the camera it self and the pictures on it.

A bit of topic but anyone who also would like to install the latest (at the moment) digikam 1.2.0 and kipi-plugins 1.2.0 will find them form Karmic on my PPA on Launchpad. Information about the PPA can be found following the link in my signature.

---

### Post by fiftywatt on 2010-04-12
This seems to work for me....not a complete fix,but will get your photos into f-spot.
Plug camera in and turn on.
Let camera load messages including errors.
Click the close box X for messages and errors.
On desktop you might see two camera icons.
Open the lower icon or the icon which contains the DCIM folder.
Click and drag the DCIM folder to the desktop to be copied.
Now open f-spot.
Drag the DCIM folder into f-spot to be copied.

I really enjoy my Kodak camera even though there seems to be a glich when using it with
Ubuntu.Kodak makes a really good camera and I will continue to use them.

---

### Post by philip5 on 2010-04-22
Just thought I should let you all know that I updated libgphoto2 in my PPA for Karmic to version 2.4.9.1. That would help in many cases for you guys who use cameras that don't function as a usb-memory/stick. Have fun!

Here is the complete changelog of libgphoto2 since version 2.4.6 that comes with official Ubuntu Karmic. If you find any fixes or new features regarding your camera then you should get the update:

```
libgphoto2 2.4.9
This is a 2.4 release branch update. 
ptp2 driver
•Fixed EOS viewfinder capture speed (2 images/s -> 20 i/s) 
•EOS event handling cleaned up, so that we can also have dual image capture (RAW+JPEG). 
•New Canon EOS properties: autoexposuremode, cameraoutput, evfmode, uilock. 
•New Nikon property: exposuredelaymode 
•Fixed a Canon Powershot configuration bug that caused hangs. 
•Fixed a Nikon Coolpix configuration bug that caused hangs. 
•Fixed shutterspeed setting to be more generic. 
•New IDs added: 
&#9702;Nikon Coolpix 8800, P6000, L20, L19 
&#9702;Panasonic FS62 
&#9702;Olympus FE4000/X920/X925, 
&#9702;Canon EOS 550D 
&#9702;Canon Powershot A2100IS, SD970IS, SX20IS, IXUS 120IS 
&#9702;Fuji FinePix S1500, Z35, S2500HD 
&#9702;Apple iPhone 3GS 
•Some bugs fixed, some memory leaks closed. 
•music-players.h merged from libmtp, bringing new MTP devices. 
ST2205 Driver
New Pictureframe driver from Hans de Goede. st2205 based frames present themselves as a regular usb mass storage device, but cannot be used as a normal disk! Communication with the device happens by a special protocol which consist of reading / writing sectors of the disk at certain magic offsets. Also included is a "usbdiskdirect" port driver, which allows the direct sector access the camlib for these devices needs. 
AX203 Driver
New Pictureframe driver from Hans de Goede. ax203 based frames present themselves as a usb mass storage cdrom, which contains the windows software. Communication with the device happens by issuing special (custom) scsi commands. Also included is a "usbscsi" port driver, which allows sending the custom scsi commands. Note that if your ax203 frame has a usb-id of 1908:1315, you need to tell Linux not to touch the HID device this version also presents in its USB descriptor. To do this add the following on the linux kernel cmdline: "usbhid.quirks=0x1908:0x1315:0x4" 
digita
Made to work again hopefully after breakage due to filesystem changes. 

--------------------------------------------------------------------------------

libgphoto2 2.4.8
This is a 2.4 release branch update. 
libgphoto2
•Updated translations. 
•Added read-only flag for Widgets. gp_widget_set_readonly / gp_widget_get_readonly. 
•GP_EVENT_CAPTURE_COMPLETE event added from trunk. 
•Some bugfixes. 
ptp2
•New USB IDs for cameras: 
&#9702;Kodak Z915 
&#9702;Nikon CoolPix S220, S225, 
&#9702;Nikon DSLR D5000, D3000, D300s 
&#9702;Canon PowerShot SD770 IS, A580, SD1200, IXUS 95 IS, G11, IXY 220IS, SD940IS 
&#9702;Canon EOS 7D 
&#9702;Fuji S5 Pro 
&#9702;Sea & Sea 2G 
&#9702;Also merged new libmtp deviceids. 
•Fuji S5 Pro capture support. 
•Bugfixes in Canon EOS preview code. 
•Fixed NIKON DSLR shutterspeed not able to set bug. 
•Nikon error decoding. 
•Several Canon EOS configuration and capture additions and fixes, focus pulling. 
•PTP protocol stability improvements. 
•Lots of bugfixes. 
sierra
•restrict list of choices for Nikon Coolpix 4300 
directory
•Merged from TRUNK to gain the good stuff. 
libgphoto2_port/usb
•Updated translations. 
•Check for MTP devices by string descriptor first and by OSD later. 

--------------------------------------------------------------------------------

libgphoto2 2.4.7
This is a 2.4 release branch update. 
libgphoto2
•Translation updates from translationproject.org. 
•Widget and choice lists now dynamic, to be able to create longer ones. 
•3rd generation UDEV rules emission, now able to emit "post HAL" UDEV rules. 
print-camera-list udev-rules version 136 > /lib/udev/rules.d/40-libgphoto2.rules 
•Dsabled LRU of images. Not really useful in times of USB 2.0, aso disabled by at least Debian und Ubuntu already. 
libgphoto2_port / USB
•If we detached a USB driver, reattach it on close. This allows using e.g. cheap camera as both webcam with in-kernel driver and still camera with libgphoto2. 
PTP2 driver:
•Renamed various configuration options and changed values to match a unified model. Some common names have changed: 
&#9702;owner->ownername 
&#9702;exptime->shutterspeed 
&#9702;eos-* -> non-eos prefixed variants 
&#9702;etc. 
You will need to review configuration setting code if you have any. 
•Create config submenus /actions for action triggers and /status for read-only values, moved stuff there. 
•New IDs: 
&#9702;Kodak M863 
&#9702;Canon Digital IXUS 110IS, IXUS 100IS, Powershot SX200IS, SD780 IS, A1100IS 
&#9702;Canon EOS 500D 
&#9702;Fuji Finepix F200 EXR 
&#9702;Apple iPod Touch first generation 
•Lots of Canon EOS capture improvements, for card capture, for LiveView, and for property setting. More properties are now possible. 
•Canon EOS Bulb mode support (available in newer canons). --set-config bulb=(0|1) 
•Fixed Nikon DSC shutterspeed setting (also for times < 1/1000) 
•Enable Viewfinder on demand for Canon Powershot, not for all capture things. 
•Generic PTP Property Get/Set in the configuration handling. 
•Decode more Nikon DSC properties (for D90 now nearly complete). 
•Turned several PTP generic commands to macros to reduce number of functions. 
•MTP player list synced with libmtp 1.0. 
•Lots of bugfixes. 
Canon driver:
•Renamed various configuration options and changed values to match a unified model. 
```

---

### Post by Makyui on 2010-05-18
Philip, I don't know if it was the fresh install of Lucid or your update  of libgphoto2, but my EasyShare ZD710 works beautifully with F-Spot,  now, whereas before, I had to do the killall trick before it would work.  It downloads the photos without problem, at least.

I forgot to test it after I installed Lynx and before I updated the  file, sorry. But since the problem returned the first time I upgraded  from Karmic to Lucid through Synaptic, I suspect it was your update that  did it. Thanks, man.

---

### Post by ayllu on 2010-05-25
The only solution i foun is: 
sudo killall gvfs-gphoto2-volume-monitor 
after plung and turn on the camera, and  I import the photos with digikam; and its works. But, in the 10.04 I can't find gnome-volume-manager, so I can't make digikam to auto-start when the camera is on.

---

### Post by maryalesia on 2010-07-27
This isn't really a "fix" to the problem, but most kodak cameras can use a micro SD card. That way, you can use your camera w/o having to connect the camera and all the crap that goes along with that.

---

### Post by shosto on 2011-07-10
My wife has a similar problem. Her camera is sometimes automounted and others times it isn't. Did some research and came up with a small shell script to use with nautilus to mount it, when automount fails. Instructions are contained in the script itself.

---

### Post by awatt on 2011-09-05
This is just my two cents, but I've noticed that when I plug in my Kodak camera, I get the error messages that the device could not be locked etc. *But* they show up on the desktop and in Nautilus as mounted. If I unmount them and then go to "Import" in digikam, I can access my photos without any problems.

---

### Post by rimibchatterjee on 2011-11-05
I'm just using Nautilus to grab my photos off the camera for now. Nothing fancier is really needed. You just ignore the error messages and treat the files as data. You can navigate to the camera using the mounted camera icons in the left strip. Or just open a browser window.

---

### Post by bach on 2011-12-11
Same problem here with a Canon Powershot SX230 HS. I run Linux Mint 12 (i.e., Ubuntu 11.10). When I plug the camera to a USB port I get the following message: "Error initializing camera: -60: Could not lock the device"

---

### Post by johnobuttons on 2011-12-16
I just noticed that my Kodak C143 has a setting locked away on one of it's menus.  The setting allows me to choose between Easyshare and other computer use.

I flipped that setting and it worked!
I guess Kodak finally realized that they needed to do something about this.

---

