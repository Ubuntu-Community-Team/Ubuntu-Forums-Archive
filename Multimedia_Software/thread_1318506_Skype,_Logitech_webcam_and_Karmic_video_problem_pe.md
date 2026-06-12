---
title: "Skype, Logitech webcam and Karmic video problem persists"
date: 2009-11-07
forum: Multimedia Software
---

### Post by relic70 on 2009-11-07
I used Skype ver 2.0 seamlessly in Jaunty and earlier versions of Ubuntu. When I did a fresh install of Karmic I had to install Skype 2.1 and had the following problem. I've had the same results with the deb download from Skype and Skype in medibuntu.

Problem: No video on Test in Video options of Skype. I've tried quite a few of the suggestions in the forums regarding the Logitech QuickCams but none of them worked for me. Here's the information on my setup and some results in Karmic with the webcam

1. Output from command lsusb

Bus 001 Device 003: ID 046d:09a6 Logitech, Inc. QuickCam Vision Pro


2. webcam displayed in Skype Video options 
	UVC Camera (046d:09a6)(/dev/video0)

3. Script in Skype shell
#!/bin/sh
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype.real "$@"

If the shell commands are given in the terminal the following error message is given when webcam is tested in the Video options

"X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes)"

4. /usr/lib/libv4l  directory contains 'v4l1compat.so' and v4l2convert.so'

The Logitech Vision Pro is a v4l2 compliant webcam. Receive the same error message given above if I use 'v4l2convert.so' in the script.

5. using 'gstreamer-properties' command in terminal good Video was  produced from webcam in Multimedia Systems Selector with the Plugin: Video for Linux 2 (v4l2), Device: UVC Camera (046d:09a6)

Other available plugin "Video for Linux (v4l)"  gives cannot get or set resource message
	
6. Good video produced from webcam UVC Camera (046d:09a6) in GUVCViewer

Any information that would help getting Skype to show video in the video options test would be appreciated.

---

### Post by relic70 on 2009-11-08
Problem solved for me.

I followed some Skype forum links that led me to Cairo-Dock forum. There I found a solution that worked.

It involves the use of cairo-dock, which I use.

Stop Cairo-Dock. Make certain it is removed from Startup Applications.

Restart the xserver in the terminal with the commmand

sudo /etc/init.d/gdm restart

After this the Test video in Skype worked for me. :D

Compiz is still running, so apparently doesn't interfere with Skype in my case.

Hope this helps someone else with similar problems in Skype video.

---

### Post by totalhealth on 2009-11-10
I had the same problem.  I was able to solve it by starting cairo-dock with "cairo-dock -c" instead of  "cairo-dock -o".  It looks like the -o option is causing the problem.

---

### Post by Aviendha09 on 2009-11-11
Yuck! that has to be the most awful workaround yet! I have to "not load" cairo-dock at boot to use skype? Nuts!
I'll see if I can find something better! 
I saw some compatibility issues with remote latest Windows client. Meanwhile, I'll be retesting Ekiga.

---

### Post by slumbergod on 2009-11-11
I went back to the old version of skype. That always worked for me.

---

### Post by Aviendha09 on 2009-11-11
Yeah? I looked for it in a few places, where did you get it?

edit: found it [here]("http://download.skype.com/linux/skype-debian_2.0.0.72-1_i386.deb"), yet to be tested.

---

### Post by relic70 on 2009-11-14
> **totalhealth said:**
> I had the same problem.  I was able to solve it by starting cairo-dock with "cairo-dock -c" instead of  "cairo-dock -o".  It looks like the -o option is causing the problem.

I tried the -c option, which is "no OpenGL", and Skype does work with the dock running. But, it doesn't quite have the zip it does when its running under "OpenGL" or the -o option.

So, I guess it's whatever tickles your tummy!

---

### Post by fabounet on 2009-11-16
This is a problem in Qt4, not in Cairo-Dock.
there is a workaround for it :
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```
(also work for VLC, Smplayer, and any Qt applications that do video)

---

### Post by NarsilAnduril on 2009-11-16
> **fabounet said:**
> This is a problem in Qt4, not in Cairo-Dock.
there is a workaround for it :
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```
(also work for VLC, Smplayer, and any Qt applications that do video)

Sorry for the newbie question, but what should I do with this command line ?

---

### Post by oscarmeyer51 on 2009-11-17
See this thread for a couple of alternate solutions.

[http://ubuntuforums.org/showthread.php?p=8338722#post8338722](http://ubuntuforums.org/showthread.php?p=8338722#post8338722)

---

### Post by relic70 on 2009-11-19
> **fabounet said:**
> This is a problem in Qt4, not in Cairo-Dock.
there is a workaround for it :
```
export XLIB_SKIP_ARGB_VISUALS=1 && skype
```
(also work for VLC, Smplayer, and any Qt applications that do video)

That works for the current session with the -o option, openGl in cairo-dock, however it doesn't persist into the next login session.

Anyway to make it persistent from one login session to the next?

---

### Post by pickarooney on 2009-11-21
doing the above gives me a green screen in the video test window. Do I somehow have to combine the LD and export commands with the skype launch command?

I tried ```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usrin/skype
``` but no luck

---

### Post by hirumono on 2009-11-26
> **pickarooney said:**
> doing the above gives me a green screen in the video test window. Do I somehow have to combine the LD and export commands with the skype launch command?

I tried ```
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usrin/skype
``` but no luck

First of all, thanks to relic70 who solved my problem with Skype.

Yes pickarooney, you have to integrate both the preload section and the export commands. I solved it in a very simple way: I right-clicked on the "Applications" menu and chose "modify menu" to bring forth the menu editor, and under "Internet -> Skype" I changed the "command" section of Skype's launcher from /usr/bin/skype to:

sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'

(mind the vertical apostrophes!)

This way I can keep my OpenGL Cairo Dock and use Skype at its fullest! Yeah!  :p

---

### Post by relic70 on 2009-12-01
> **hirumono said:**
> First of all, thanks to relic70 who solved my problem with Skype.


sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'

(mind the vertical apostrophes!)

This way I can keep my OpenGL Cairo Dock and use Skype at its fullest! Yeah!  :p

Yep! Works like a charm for me too. Thanks to your extra help hirumono.

---

### Post by fleghorn on 2009-12-01
Tried sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype' but still get the fuzzy green video. Here is the output I get:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": /usr/lib/gtk-2.0/modules/libglobalmenu-gnome.so: wrong ELF class: ELFCLASS64

Any ideas what went wrong?

---

### Post by relic70 on 2009-12-03
> **fleghorn said:**
> Tried sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype' but still get the fuzzy green video. Here is the output I get:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "gnomenu-panel": libgnomenu-panel.so: cannot open shared object file: No such file or directory
Gtk-Message: Failed to load module "globalmenu-gnome": /usr/lib/gtk-2.0/modules/libglobalmenu-gnome.so: wrong ELF class: ELFCLASS64

Any ideas what went wrong?

I'm only guessing here, but you many not have all of those files installed, particularly those that indicate "no such file or directory". Check the synaptic package manager to see if they are installed.

---

### Post by marin123 on 2009-12-13
i have a 64 bit karmic... do i have to write  LD_PRELOAD=/usr/lib64/ instead of  LD_PRELOAD=/usr/lib/ ?
i tried this and cant get my video to work.. my cam works fine with cheese, but not with skype... i can get sound from my webcam but no video and i see the video of the other person, just cant start my video...

---

### Post by Linuxforall on 2009-12-13
> **marin123 said:**
> i have a 64 bit karmic... do i have to write  LD_PRELOAD=/usr/lib64/ instead of  LD_PRELOAD=/usr/lib/ ?
i tried this and cant get my video to work.. my cam works fine with cheese, but not with skype... i can get sound from my webcam but no video and i see the video of the other person, just cant start my video...

Skype from the medibuntu repos worked fine but the one downloaded from Skype site gives me the same issue with my cam, I get sound but only green stripes for video. The cam works fine in Cheese, I am on Karmic x64.

---

### Post by marin123 on 2009-12-13
> **Linuxforall said:**
> Skype from the medibuntu repos worked fine but the one downloaded from Skype site gives me the same issue with my cam, I get sound but only green stripes for video. The cam works fine in Cheese, I am on Karmic x64.

i hope you solved the problem with links from that other thread :)

---

### Post by Linuxforall on 2009-12-13
> **marin123 said:**
> i hope you solved the problem with links from that other thread :)

Yep, just thinking in long run, it needs to be back in the repo for now. Many of those who switch to Ubuntu here from Windows depend on Skype as its the only audio video messenger for Linux so the medibutnu way makes it far easier than telling them to download from specific site.

---

### Post by marin123 on 2009-12-14
> **Linuxforall said:**
> Yep, just thinking in long run, it needs to be back in the repo for now. Many of those who switch to Ubuntu here from Windows depend on Skype as its the only audio video messenger for Linux so the medibutnu way makes it far easier than telling them to download from specific site.

i agree, but there is a reason why they are removing it from medibuntu (i guess skype demanded to remove it), so the only way is to back it up on some server... i can use mine (just need to renew my password to be able to access it, then i'll put a link into my signature)...
and you can also use video+audio in amsn (also very good for ppl switching to ubuntu)

---

### Post by Linuxforall on 2009-12-14
Yep I have it saved too and would be glad to upload it to any of the file sharing serivices. Judging by the video thread on Skype forums, many are having issues with the Skype version provided by them.

---

### Post by marin123 on 2009-12-16
[http://adria.fesb.hr/~mbareta/skype/](http://adria.fesb.hr/~mbareta/skype/)

here you have newest skype versions, both i386 and amd64 with skype-common debs...
download and enjoy :)

---

### Post by Linuxforall on 2009-12-16
> **marin123 said:**
> [http://adria.fesb.hr/~mbareta/skype/](http://adria.fesb.hr/~mbareta/skype/)

here you have newest skype versions, both i386 and amd64 with skype-common debs...
download and enjoy :)

Very nice of you, may I post this link at the Skype for Linux forums as well as there are many there with Ubuntu having video and audio issues.

---

### Post by alanix on 2009-12-17
Also having same issue with the latest from Skype - 2.1.0.47.  I get green screen in the Video set up section, I also get it in Cheese, but GUVCVideo works fine.  I tried the command suggested above, but got a similar error:
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm in Karmic... this is really disapointing.  I can't download the medibuntu version either :(

---

### Post by marin123 on 2009-12-17
> **alanix said:**
> Also having same issue with the latest from Skype - 2.1.0.47.  I get green screen in the Video set up section, I also get it in Cheese, but GUVCVideo works fine.  I tried the command suggested above, but got a similar error:
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

I'm in Karmic... this is really disapointing.  I can't download the medibuntu version either :(

LD PRELOAD doesnt work for me... i also had green screen in skype but cheese worked fine... i have 64 bit karmic and everything works fine.. just install common deb and skype deb and it should work fine...
but before you install medibuntu skype:
sudo apt-get remove skype  (and search for skype and manually delete files that are left in your system...)
this worked for me... :)

EDIT: have you tried my links? it should work... here it is:

[http://adria.fesb.hr/~mbareta/skype/](http://adria.fesb.hr/~mbareta/skype/)

---

### Post by Linuxforall on 2009-12-17
Make that sudo apt-get --purge remove skype and also delete the .skype folder in your home.

---

### Post by saltmore on 2009-12-17
Here is my full launcher for skype. Name it skypelauncher.sh or something similar. Make it executable and prosper. It is in the same directory as skype itself. /usr/bin in my case. Then can edit main menu launcher and startup applications so this launches instead. Very easy workaround, and works great.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

---

### Post by fromgi on 2009-12-18
> **marin123 said:**
> 

EDIT: have you tried my links? it should work... here it is:

[http://adria.fesb.hr/~mbareta/skype/](http://adria.fesb.hr/~mbareta/skype/)

I must be doing something wrong with this link.  When I try to download Syype, I get a "Forbidden" message.  Help!

---

### Post by marin123 on 2009-12-19
sorry about links that are not working, i forgot to set permissions :(
now its working, i tested it...
and you can put this link wherever you want, i wont delete this files...
if you have any more problems, just let me know... :)

---

### Post by fromgi on 2009-12-19
> **marin123 said:**
> sorry about links that are not working, i forgot to set permissions :(
now its working, i tested it...
and you can put this link wherever you want, i wont delete this files...
if you have any more problems, just let me know... :)


Thank you VERY MUCH!

---

### Post by Timbo337 on 2009-12-22
> **fromgi said:**
> Thank you VERY MUCH!

These files also worked great for me! Thank you!

System:
Ubuntu 9.10 64 bit
Logitech Quickcam Chat 046d:08af

---

### Post by wetinwales on 2009-12-23
This thread is for 9.10 but I think the problem is still the same in Jaunty 9.04.

I am running jaunty 9.04 on a four core amd 64bit with the deb skype 2.1.0.47 installed from skype website. 
I have a Logitech QuickCam Messenger which works good in Cheese.

As you all guessed... I get the green or multicolored hash in the Skype Video test.
Finger accross camera changes colours etc.

I have tried every version of solution I can find in forums - Preload v4l1, renaming of /usr/bin/skype.real etc etc... all to no avail.

I have checked the libs and they all seem to be "newest versions"

I think I am now lost.

Here is terminal output clue?

me@comp:~$ ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

So many posts claim success for various solutions. None for me !!!!

Can anybody help ? 

Thanks

---

### Post by marin123 on 2009-12-24
have you tried installing skype-common packages or skype packages from medibuntu?

---

### Post by Jimtheplanner on 2009-12-24
Ah Medibuntu.....

Anyone know why the Skype packages are missing form Medibuntu for Karmic???

Edit:~ Ah I found the answer... 

[https://bugs.launchpad.net/medibuntu/karmic/+bug/494564](https://bugs.launchpad.net/medibuntu/karmic/+bug/494564)

They no longer maintain Skype

---

### Post by wetinwales on 2009-12-24
Thanks Marin 123
Tried that and this is the error I get in terminal:-

Selecting previously deselected package skype-common.
(Reading database ... 171955 files and directories currently installed.)
Unpacking skype-common (from .../skype-common_2.0.0.72-0medibuntu1.1_all.deb) ...
dpkg: error processing /home/daf/.opera/temporary_downloads/skype-common_2.0.0.72-0medibuntu1.1_all.deb (--install):
trying to overwrite '/etc/dbus-1/system.d/skype.conf', which is also in package skype
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/me/.opera/temporary_downloads/skype-common_2.0.0.72-0medibuntu1.1.deb

Thanks for any more help?!

---

### Post by marin123 on 2009-12-25
i suggest you first remove any of skype installations that you had before:
sudo apt-get remove skype

and manually delete all of the skype files that are left in your computer, then install skype-common2 deb and then skype deb and this should work, it worked for me... try this and post if you had sucess.. good luck!

---

### Post by wetinwales on 2009-12-25
I removed all of skype manually as the "sudo apt-get remove skype" could not find skype at all.
That done, I'm now trying to remember how to install skype-common but cannot find a reference to skype-common2 deb.

I have found a list of skype-commons here:
[http://packages.medibuntu.org/pool/non-free/s/skype/](http://packages.medibuntu.org/pool/non-free/s/skype/)

If I undewrstand this webcam problem correctly, we all must find older versions of skype or skype-common when using Jaunty. My problem is further worsened by using amd 64bit.

So which skype-common do I choose from the above list?
Do I then re-install skype from the skype.com downloads page and choose the 'deb' version for 64bit?

Merry Christmas all!!:)

---

### Post by marin123 on 2009-12-25
i used latest common files and skype deb from _medibuntu_...
it works fine on my amd64 karmic, i suppose it should work with you too...
merry christmas!

---

### Post by wetinwales on 2009-12-25
As 'jimtheplanner' refers above, Medibuntu no longer holds skype in its repositories.
I think this means 'do without webcams' till skype sorts it out.

It's just too complicated and time consuming for the value of having a webcam (for me)

Many thanks for all help.

---

### Post by marcond on 2010-01-29
Hello

Just to keep you folks informed, I've been lucky enough to get Skype working with Logitech QuickCam Messenger under Ubuntu 9.10 32bits, by following the steps below:

1) Installed a fresh Ubuntu 9.10
2) Installed Medibuntu repos ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu))

[FONT=Courier New][SIZE=2]sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update[/SIZE][/FONT]

3) I've used Ubuntu 9.10 32 bits, so I installed w32codecs and ubuntu-restricted-extras

[FONT=Courier New][SIZE=2]sudo apt-get install w32codecs ubuntu-restricted-extras[/SIZE][/FONT]

*Really I don't think that Medibuntu nor w32codecs nor restricted-extras are needed at all, but I've included this anyway because I did installed them before Skype, with other purposes. You may skip this (well, I guess...)*

4) Downloaded latest Skype from:

[http://www.skype.com/intl/pt/download/skype/linux/choose/](http://www.skype.com/intl/pt/download/skype/linux/choose/)
(of course, get the skype download according your language, mine is portuguese)

The  downloaded file was [FONT=Courier New][SIZE=2]skype-ubuntu-intrepid_2.1.0.81-1_i386.deb[/SIZE][/FONT] .

5) Install Skype (simply clicked the downloaded file and select install).

6) Renamed the [FONT=Courier New][SIZE=2]skype[/SIZE][/FONT] executable located on [FONT=Courier New][SIZE=2]/usr/bin[/SIZE][/FONT] to [FONT=Courier New][SIZE=2]skype.real[/SIZE][/FONT] on the same directory

7) Created a batch file under [FONT=Courier New][SIZE=2]/usr/bin[/SIZE][/FONT] named [FONT=Courier New][SIZE=2]skype[/SIZE][/FONT] containing:

[FONT=Courier New][SIZE=2]#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real "$@"
exit 0[/SIZE][/FONT]

8_) Made this script executable by chmod

[FONT=Courier New][SIZE=2]chmod +x skype[/SIZE][/FONT]

9) Adjusted the mic volume on System/Preferences/Sound **and** on the tab Input selected the source *QuickCam Messenger Analog Mono*.

That's it, YMMV.

Marcond

---

### Post by mahiyar on 2010-02-17
Thanks to this thread I have learnt a lot of things, on one of my machines I was facing problem in VLC, on one laptop in Skype, and the best part I learnt is right clicking "Application" on the bar shows edit menu (thanks hirumono)

---

### Post by ahbart on 2010-02-18
I just installed this new package skype-ubuntu-intrepid_2.1.0.81-1_i386.deb from skype website and noticed the video problem with my logitech:
ID 046d:08da Logitech, Inc. QuickCam Messanger
The webcam did not start.

Your instructions worked to fix this issue.
Thanks

---

### Post by toogooda on 2010-04-29
> **NarsilAnduril said:**
> Sorry for the newbie question, but what should I do with this command line ?

Just paste it in the command line and hit enter it will launch Skype and video works (just tried :)

I added the line to the command of the launcher in Cairo so always works for me now.

---

### Post by SGAZ on 2010-05-02
**@marin123 ** -- Thanks for the older Skype debs!  My Skype Video hasn't worked since 9.10 and now it's back.  Much appreciated.

Now I just have to make sure I don't update it. :D

---

### Post by jurgen32 on 2010-05-19
Hello

I'm working with Lucid 64 bit.
My logitech quickcam pro 4000 is working fine under cheese but not with Skype if I enabled Cairo-dock with open-gl.

So I took this topic and started to fiddle around and came up with this solution:

I added this repository:
*deb [http://ppa.launchpad.net/darcio53/darcio/ubuntu](http://ppa.launchpad.net/darcio53/darcio/ubuntu) lucid main*
Then update and install the newest version of Skype. Watch out for other applications because maybe they are not compatible with your system, so to be sure only install Skype.
Then you can disable the repository

Then open Konsole or gnome-terminal
type: *sudo kate (or gedit) /usr/bin/skype*
Here you see the following:

[I]#!/bin/sh

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype.bin "$@"[/I]

Change this in:

[I]#!/bin/sh

[COLOR="Red"]export XLIB_SKIP_ARGB_VISUALS=1 && [/COLOR]LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype.bin "$@"[/I]

Save the file and now you can use the newest version of Skype and Cairo-Dock with open-gl!

Good luck,
Jurgen

---

### Post by Old Jimma on 2010-05-22
Hi Ubuntu Community:

I read this entire thread and others. My problem was that video with Skype (newly downloaded on May 22, 2010) didn't work.

I have a 64 bit Lucid OS....

I found something that worked for me:

I found the web page: [http://linux.dipin.info/2010/03/resolve-skype-video-chat-web-cam-issue.html]("http://linux.dipin.info/2010/03/resolve-skype-video-chat-web-cam-issue.html")

It gives the following prescription that worked:

> I installed Skype on Ubuntu 10.04 (64 bits) as described here*Install Skype in Ubuntu 10.04 Lucid Linux.

After installing the 64 bit version of Skype for Ubuntu, I found that the color webcam display looked ''green''.

I had faced the same issue when i installed and used skype in ubuntu 9.10.
The fix show below helped me at that time, it does rescue me this time also.

To view the webcam properly in Skype use this piece of code:
$  LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype

To make this a permanent solution, follow the step below:
$ sudo mv /usr/bin/skype /usr/bin/skype.bin
$ sudo chmod 755 /usr/bin/skype.bin
$ sudo gedit /usr/bin/skype
(use anyother editor of your choice instead of gedit if u want)
add the following lines to it and save & close
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.bin
$ sudo chmod 755 /usr/bin/skype


Hope it works for you!

All the best,
Phil Smith
Duluth, GA

---

### Post by ischliky on 2010-05-27
great help in this thread, for me simply changing the menu item and cairo dock call both to 

sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && skype-wrapper'

fixed it completely for me.  i was using a logitech c600, which worked perfectly in cheese but just gave lots of 

X Error, request 133, minor 18, error code 8 BadMatch (invalid parameter attributes) 

errors before i made the change.  simple change to get it all working, thanks for the tip

using 10.04 64-bit

---

### Post by labinnsw on 2010-06-05
> **ischliky said:**
> great help in this thread, for me simply changing the menu item... What menu item?

The solution that finally worked for me was found [here]("http://ubuntuforums.org/showpost.php?p=8163641&postcount=8")

---

### Post by labinnsw on 2010-06-06
> **labinnsw said:**
> What menu item?

The solution that finally worked for me was found [here]("http://ubuntuforums.org/showpost.php?p=8163641&postcount=8")

As it turned out, this was only a part of the solution.
The complete thing is set out below.

[From here:]("http://ubuntuforums.org/showpost.php?p=8163641&postcount=8")
1.   From synaptic install lib32v4l-0 (if it is not yet installed)
2.   If you installed from skype's website (the new beta) there will be no skype.real but only a skype executable. You need to rename it to skype.real (If you already have a skype.real don't worry about it)

[From here and amended]("http://ubuntuforums.org/showpost.php?p=9328030&postcount=46")
3.   Create a launcher called skype, saved in your home directory, and containing this script: ```
#!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype.real "$@"
```
4.   Change all other skype launcher commands to ```
/home/yourusername/skype
```

Now only one thing remains. When run from the terminal, the script command produces an error:> Gtk-Message: Failed to load module "globalmenu-plugin": /usr/lib/gtk-2.0/modules/libglobalmenu-plugin.so: wrong ELF class: ELFCLASS64It does not stop anything from working, but I sure would love to be rid of it.
[SIZE="4"]
EDIT[/SIZE]
Some time after I did this, I did an update and Skype video stopped working. I installed camorama to see if the camera was working there and that fixed Skype video again.

---

### Post by hebetude on 2010-08-04
Thanks this fixed the problem.  However, before I do this my webcam shows me right side up, after doing this my webcam is upside down.

I have the same problem on Windows...

---

### Post by labinnsw on 2010-08-04
> **hebetude said:**
> Thanks this fixed the problem.  However, before I do this my webcam shows me right side up, after doing this my webcam is upside down.

I have the same problem on Windows...

[This solution is a couple of years old but might still work]("http://ubuntuforums.org/showpost.php?p=5718814&postcount=8")
[URL="http://www.google.com.au/search?hl=en&lr=&as_qdr=all&q=Webcam+video+upside+down&aq=f&aqi=&aql=&oq=&gs_rfai="]
You can check these out to see  if you can find a Windows solution[/URL]

---

### Post by madan_amilus on 2010-11-07
this thread was a big help :)
i'm using cairo-dock and changing its startup entry from cairo-dock -o to cairo-dock -c fixed the problem fer me

---

### Post by freshmeatz on 2010-11-16
when is doubt "search" fixed my issue to add sh to command line. Thanks..

---

### Post by tlfcbb on 2010-11-17
When i set skype to load on start up my webcam will not work.  However if I manually start it after booting up the system it works fine.  I am not using ciaro dock but am using docky.  Any ideas?

---

### Post by guntu on 2010-11-30
> **relic70 said:**
> Problem solved for me.

I followed some Skype forum links that led me to Cairo-Dock forum. There I found a solution that worked.

It involves the use of cairo-dock, which I use.

Stop Cairo-Dock. Make certain it is removed from Startup Applications.

Restart the xserver in the terminal with the commmand

sudo /etc/init.d/gdm restart

After this the Test video in Skype worked for me. :D

Compiz is still running, so apparently doesn't interfere with Skype in my case.

Hope this helps someone else with similar problems in Skype video.


THANKS SO MUCH! This did it for me, it was so annoying. I got rid of Cairo All together because I noticed it had been giving me problems.

---

### Post by rivosuoth on 2011-02-04
> **saltmore said:**
> Here is my full launcher for skype. Name it skypelauncher.sh or something similar. Make it executable and prosper. It is in the same directory as skype itself. /usr/bin in my case. Then can edit main menu launcher and startup applications so this launches instead. Very easy workaround, and works great.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

Works like a charm!
After trying all methods (simple ones ^_^), this one works well! I'm using Asus Notebook F Series. GT 220M. 

USB2.0 UVC 1.3M WebCam (/dev/video0) as shown in skype's video devices setting.
Ubuntu 10.10 64 bit (fresh installation and full cairo-dock installed ^^).

JUST copy and paste these codes into Terminal (Applications > Accessories >Terminal) and ENTER
> #!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

Compiz is not turned off, and cairo-dock as well. :D:D:D:D
Thank you

---

### Post by ACGilbert on 2011-03-02
> **hirumono said:**
> First of all, thanks to relic70 who solved my problem with Skype.

Yes pickarooney, you have to integrate both the preload section and the export commands. I solved it in a very simple way: I right-clicked on the "Applications" menu and chose "modify menu" to bring forth the menu editor, and under "Internet -> Skype" I changed the "command" section of Skype's launcher from /usr/bin/skype to:

sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'

(mind the vertical apostrophes!)

This way I can keep my OpenGL Cairo Dock and use Skype at its fullest! Yeah!  :p
Thanks hiromomo
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
your post #13 command and instructions worked for me.
64 bit Lucid and Cairo Dock.
AC

---

### Post by dabl on 2011-04-11
> **saltmore said:**
> Here is my full launcher for skype. Name it skypelauncher.sh or something similar. Make it executable and prosper. It is in the same directory as skype itself. /usr/bin in my case. Then can edit main menu launcher and startup applications so this launches instead. Very easy workaround, and works great.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

Yep, this works perfectly for Skype 2.2 Beta on Debian Sid, kernel 2.6.38-2, 64-bit system w/KDE 4.6.1 desktop, and Logitech Quickcam Connect STX.

Thanks!

---

