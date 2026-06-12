---
title: "VLC Not Working - Choppy Video"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by MarshyTheKid on 2007-10-06
I just reformatted a few days ago to the newest version of Ubuntu. I installed VLC again and attempted to watch an .avi file(One that I know works) and the video is very very choppy. It seems to play a few frames, then jump back a few frames and continue. The sound works properly. I searched a bit and couldn't find anything to help me. I tried reinstalling VLC but nothing changed.

---

### Post by shad0w_walker on 2007-10-06
Have you got your proper graphics drivers installed? It might just be a performance issue from those (If your running vesa drivers thats almost certainly it)

---

### Post by JBAlaska on 2007-10-06
Try going to settings, preferences, video, output modules and change the module;
Good Choices (Depending on your H/W and x setup) are:
Default
OpenGL
X11
and XVideo

See if you can find one that get's along with your setup

---

### Post by MarshyTheKid on 2007-10-06
> **shad0w_walker said:**
> Have you got your proper graphics drivers installed? It might just be a performance issue from those (If your running vesa drivers thats almost certainly it)I downloaded and installed the ATI drivers, but my text seems stretched out and not clear, so I am not sure.
I am running MSI Radeon X1300Pro.

---

### Post by MarshyTheKid on 2007-10-06
Oh and I guess I do have a vesa driver installed.
xserver-xorg-video-vesa
What should I replace it with?

---

### Post by MarshyTheKid on 2007-10-07
I tried removing xserver-xorg-video-vesa and trying it again, but it didn't work.

Any more suggestions?

---

### Post by shad0w_walker on 2007-10-07
Thats just the installed module, doesn't mean you are using it (And i assume by the fact you removed it and your still running X that you weren't)

Have you tried using any other media players? It might help narrow it down a little, if its just VLC its probably some strange configuration problem.

EDIT:
Missed the part about xorg-video-vesa not being removed. Try running this command in a terminal and see if produces any output.

```
cat /etc/X11/xorg.conf | grep vesa
```

---

### Post by MarshyTheKid on 2007-10-07
> **shad0w_walker said:**
> Thats just the installed module, doesn't mean you are using it (And i assume by the fact you removed it and your still running X that you weren't)

Have you tried using any other media players? It might help narrow it down a little, if its just VLC its probably some strange configuration problem.

EDIT:
Missed the part about xorg-video-vesa not being removed. Try running this command in a terminal and see if produces any output.

```
cat /etc/X11/xorg.conf | grep vesa
```
I tried using Totem(I think that was the name) and it worked fine. I looked through the settings of VLC and didn't see anything that might be out of whack. I suppose I could try deleting the configuration file. Do you know where/what it is?

Also, that command didn't output anything.

---

### Post by MarshyTheKid on 2007-10-08
Any thoughts?

---

### Post by shad0w_walker on 2007-10-08
Sorry about the lag, lots of stuff to do. Anyway, the command not giving any ouput means you are definitely not using the vesa drivers. If its working in other player then your problem probably lies with VLC. You should be able to find the VLC configuration folder in your home directory, it should be called

```
.vlc
```

It will be hidden by default so make sure you make nautilus show hidden files (Ctrl+H)

---

### Post by MarshyTheKid on 2007-10-08
Well deleting the files in .vlc did nothing to fix the problem.

---

### Post by MarshyTheKid on 2007-10-08
I don't think I have my video drivers installed properly. I have the ATI driver installed but my text is weird looking. I thought I installed the correct one, but I don't know.

---

### Post by MarshyTheKid on 2007-10-26
Okay, well when I upgraded to Gutsy, it was working fine. Then I tried to rip some MP3s and went through this:
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

I tried removing some of the packages, but nothing changes. Also in totem the color has gone all wacko now too. 

Any help? This is very inconvenient

---

### Post by elvin11 on 2007-10-26
all you need is the libdvdcss2 file install.I did that and dvd movies on my pc.

---

### Post by MarshyTheKid on 2007-10-26
> **elvin11 said:**
> all you need is the libdvdcss2 file install.I did that and dvd movies on my pc.There is no libdvdcss in the package manager. Nor libdvdcss2.

---

### Post by MarshyTheKid on 2007-10-27
Help?

---

### Post by conchpapa on 2007-10-27
> **MarshyTheKid said:**
> There is no libdvdcss in the package manager. Nor libdvdcss2.

I think you have to get that from the medibuntu repositories. If that is part of Synaptic's repository, then you can have synaptic install it for you.

---

### Post by MarshyTheKid on 2007-10-27
Well I tried that and VLC still doesn't work properly.

---

### Post by DeadToad on 2007-10-27
Marshy,
livdvdcss2 is NOT in any repository, I searched til the cows came home and could not find it.
It IS here: [http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb](http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb)

Just click the link, then (do NOT save it) "open" it with the default selection.
Then click "install software", and let it finish.
After that, VLC will play your DVDs real nice.
Have fun.
DeadToad

---

### Post by DeadToad on 2007-10-28
HOW TO GET VLC AND MPLAYER TO PLAY DVDs
(the Step-by-Step method, nothing left out!)

Installation instructions for libdvdcss2 and w32codecs in Ubuntu, to play DVDs in MPlayer and VLC:

To add libdvdcss2 and win32codecs to your Ubuntu installation, you have to add the Medibuntu package repository to your /etc/apt/sources.list file.

To do this, you have to:
1. Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
gksudo gedit /etc/apt/sources.list to open it in the GUI text editor
or
sudo vim /etc/apt/sources.list to open it in the Vim command line text editor

2. Add the following lines to add the Medibuntu repository to the file:

## Medibuntu - Ubuntu 7.10 “gutsy gibbon”
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) gutsy free non-free

If you are running Feisty or some other release, other than gutsy, replace the word “gutsy” in the three lines above with the name of the release you are using.

3. Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:
To do this, run the following command from the terminal:
wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

4. Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:
In a terminal execute the following command:
sudo apt-get update

5. Now you can install libdvdcss2 and w32codecs using the following command:
sudo apt-get install libdvdcss2 w32codecs

Close terminal window.

6. To install/reinstall VLC Media Player:
Open Synaptic (System -> Administration -> Synaptic Package Manager).
Type your password.
Click Settings -> Repositories.
Under "Ubuntu Software" check the first four items, making sure you have the "universe" repository checked.
Do NOT check "source code".
Under "Third-Party Software" check all items.
Under "Updated/Ubuntu Updates" check all items.
Click "Close", twice if necessary.
Now back at the Synaptic Package Manager main window:
Click "Search".
Type "vlc".
Click "Search" button.
"vlc" will be shown in the left window. left-click it once to highlight it.
In the right window, click on these additional files: vlc-plugin-esd and mozilla-plugin-vlc, then click "Mark for installation" for each file.
(libdvdcss2 which will be installed later, as it is NOT in a repository).
Click "Apply".
Click "Apply" again, if necessary to begin download.
After "Changes applied", click "Close".
Close "Synaptic Package Manager" window.

7. Now, you just need to REINSTALL livdvdcss2 to get VLC and MPlayer to play DVDs:
livdvdcss2 is NOT in any repository, I searched til the cows came home and could not find it.
It IS here: [http://download.videolan.org/pub/lib...2.9-1_i386.deb](http://download.videolan.org/pub/lib...2.9-1_i386.deb)

Just click the link, then "open" it with the default selection (do NOT save it).
Then click "install software", and let it finish.
After that, VLC and MPlayer will play your DVDs real nice.
Have fun.
DeadToad

---

### Post by MarshyTheKid on 2007-10-29
Okay, I had already installed that and it didn't fix it. I'm not worried about playing dvds, I'm just trying to get ANY video to work properly on VLC. At this point neither Totem nor VLC work correctly.

---

### Post by slugicide on 2007-10-29
> **MarshyTheKid said:**
> Okay, I had already installed that and it didn't fix it. I'm not worried about playing dvds, I'm just trying to get ANY video to work properly on VLC. At this point neither Totem nor VLC work correctly.

I have a fresh install of Gutsy.  Default video player crashes on initiation and VLC plays the video all jittery.  I think this is similar to your problem.  In VLC I went to Video>Deinterlace and Chose "X."  This got rid of the jittery playback, but it looks like shite.

---

### Post by eye208 on 2007-10-29
sudo aticonfig --ovt Xv

will enable the XVideo extension in the proprietary ATI video driver. VLC uses XVideo by default.

---

### Post by BigSilly on 2007-10-29
I also have this problem too with VLC. I managed to get Totem working OK with DVD's, thanks to a tutorial elsewhere on this forum, but VLC just won't have it. I re-installed libdvdcss2 and restarted the PC as has been suggested, but video playback is still jittery. Shame, as I always felt VLC had the better picture quality on my old Dell monitor, hence my persistence in trying to find a fix for it. If anyone knows how to get this working good please post it up! :)

---

### Post by DeadToad on 2007-10-29
Marshy,
My apologies.  Choppy video is caused because you do not have DMA enabled for the cdrom drive.
To fix this, enable DMA for the cdrom drive.

If DVD playback is noticeably choppy or burning a CD/DVD is slower than it should be, then you may need to enable DMA transfer for the DVD drive. See the DMA (Direct Memory Access) page for details: [https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

DeadToad

---

### Post by slugicide on 2007-10-29
> **eye208 said:**
> sudo aticonfig --ovt Xv

will enable the XVideo extension in the proprietary ATI video driver. VLC uses XVideo by default.

Worked like a charm.  Thanks.

---

### Post by MarshyTheKid on 2007-10-29
Opening a video and changing the Deinterlace to X worked, but the sudo aticonfig --ovt Xv didn't do anything.

```
~$ sudo aticonfig --ovt Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1

```

Any way to get VLC to automatically use the X deinterlace?

---

### Post by stefanuswiely on 2007-10-29
> **eye208 said:**
> sudo aticonfig --ovt Xv

will enable the XVideo extension in the proprietary ATI video driver. VLC uses XVideo by default.

What command I should do if I have nvidia card? I have problem play some avi files using totem-xine. Thank you.

---

### Post by eye208 on 2007-10-30
> **stefanuswiely said:**
> What command I should do if I have nvidia card?
XVideo is enabled by default in the Nvidia driver.

---

### Post by stefanuswiely on 2007-10-30
OK, thanks for the info.
But i still have glitches while playing some of AVI. There is something I can do to fix the glitch?

---

### Post by kasulstyls on 2007-11-10
Deadtoad you DMA find worked good for me on my mythbuntu box.  Thanks so much!!!

---

### Post by bwallum on 2007-11-10
Did you get Meibuntu repos installed?

If not go to System>Administration>Software Sources. Select the third party tab and add this repository:-

[http://packages.medibuntu.org/gutsy](http://packages.medibuntu.org/gutsy)

I don't think this is the problem but the medibuntu directory is good to have for streaming codecs..

I have had no end of trouble with VLC on Gutsy. My problem is that the video cuts out 10 minutes after the last mouse/keyboard event. Its not being taken seriously as a bug either.

For your issue try resetting VLC to its default settings when you have medibuntu on line.

Rgds
Bob

---

### Post by bwallum on 2007-11-10
Not too sure if you tested if DMA is on ..

This code should tell you, assuming your drive is device named cdrom

```
sudo hdparm /dev/cdrom
```

...

---

### Post by bwallum on 2007-11-10
Do you have "ubuntu-restricted-extras" installed?

If not search for them in Synaptic and install if not present.

---

### Post by DeadToad on 2007-11-10
> **kasulstyls said:**
> Deadtoad you DMA find worked good for me on my mythbuntu box.  Thanks so much!!!

kasulstyls,
anytime...........
glad to be of assistance.
DeadToad

---

### Post by RichieRich on 2007-11-24
I've just had a similar experience of choppy .avi playback in vlc after installing Gutsy and found it was because the deinterlace mode was set to none. When changing the deinterlace mode from the video menu to blend they worked fine but the deinterlace mode reverted to none after closing. Here is how I got it to persist.

In nautilus, right-click on the .avi file, choose "Open with / Open with other application"
From the list click on VLC Media Player, then click the arrow for "use a custom command". 
In the custom command box type

vlc --vout-filter deinterlace --deinterlace-mode blend

and click open.

Now when I launch an .avi through nautilus it sets the deinterlace mode to blend automatically.

I hope this helps someone.

---

### Post by OisinT on 2008-02-05
> **shad0w_walker said:**
> Sorry about the lag, lots of stuff to do. Anyway, the command not giving any ouput means you are definitely not using the vesa drivers. If its working in other player then your problem probably lies with VLC. You should be able to find the VLC configuration folder in your home directory, it should be called

```
.vlc
```

It will be hidden by default so make sure you make nautilus show hidden files (Ctrl+H)

what should I do if the command DOES produce an output?
```

oisint@OisinT1:~$ cat /etc/X11/xorg.conf | grep vesa
# values from the debconf database and some overrides to use vesa mode.
    BoardName      "vesa"
    BoardName      "vesa"

```

---

### Post by OisinT on 2008-03-14
> **OisinT said:**
> what should I do if the command DOES produce an output?
```

oisint@OisinT1:~$ cat /etc/X11/xorg.conf | grep vesa
# values from the debconf database and some overrides to use vesa mode.
    BoardName      "vesa"
    BoardName      "vesa"

```

anyone help with this? Changing the deinterlace doesn't seem to solve the problem or change it.

---

### Post by kyotolee on 2008-04-14
OisinT, if the command tells you that you have vesa drivers installed, you need to search for the proper drivers to use for your video card.

To get deinterlace to stay on without having to mess with custom commands, just go to settings and preferences. Then, double click video, filters, deinterlace. Choose which one you want to use and then click save. Everytime you use vlc it should automatically be using deinterlace from now on.

---

