---
title: "AMD HD Series Graphics Guide: Optimizing Video Playback for MythTV, Mplayer, &amp; Others"
date: 2010-01-20
forum: Multimedia Software
---

### Post by sports.car.guy on 2010-01-20
[SIZE=2][U][B][SIZE=3]Updated:
[/SIZE][/B][/U]**[SIZE=3] January 29, 2010[/SIZE]**[SIZE=3]
[SIZE=2]
[FONT=Arial]Hello everyone. Since I wrote this tutorial nine days ago a few things have been going on. AMD / ATI released version 10.1 of the Catalyst Control Center for starters. This driver release will be the official driver for this guide. The other drivers should work for you, but this is the first driver to really have AMD going in the right direction with Linux Support.

It appears they re-setup the driver to install the XvBa files. This is looking like they think the driver with the Catalyst Control Center 10.1 is ready for wider testing by individuals. They have also added new setup switches to aticonfig, like for TLS showing they are working on driver that can take advantage of X-Windows better and visa versa.

It is now time for us AMD graphics people to be able to have totally tear free video playback, and even in some cases full hardware acceleration on top of that. Prior to this driver the use of Xv could bring an occasional tear when watching video, not ones that destroy enjoyment, but enough of one to say you can notice it once in a blue moon.

With the release of Catalyst Control Center 10.1 almost two days ago, yesterday I went to work on seeing what other things I could do to improve the video playback experience using AMD GPU's. I have finally done it. I now have OpenGL rendering working fully and tear free with MythTV. No drawing / overlay issues anymore. It is all a thing of the past.

I know this can all be easily replicated on other systems. Because of this new turn of events, it now makes tear free playback in MythTV perfect, not everyone will need to go the route of compiling the hardware accelerated MPlayer to enjoy perfect video playback, though I will say I personally prefer the quality difference between the hardware decoding over FFMpeg software decoding for MPEG4 based files.

This guide when I am done should also flow a little better and make a little more sense as well for some who are hesitant needing to see it isn't as bad as it sounds. I hope these changes make some people's lives easier. 

I am getting a lot of questions regarding the GPU's prior to what this guide has been written for, namely the HD3xxx series. From what I have gathered from others out here who have tried parts of this guide, is that XvBA should work for you, but not XvMC. The new OpenGL settings I have come up with and proper rendering in MythTV I am not sure about, but would think that should work for you as well and be tear free like it is for me. That is depending on your actual Catalyst Control Center OpenGL settings being set correctly and not too high for the system to handle of course.

So I will say this, if you are running the AMD proprietary drivers, then this guide should benefit you in some way, shape, or form. How is that?..lol.
[/FONT][/SIZE][/SIZE][U][B][SIZE=3]

Please Note:
[/SIZE][/B][/U][/SIZE][I]
This tutorial is for Ubuntu 9.10 and its derivatives. It should be relevant to earlier releases of Ubuntu such as the 8.x generations and up. It should also be relevant to most Debian based distributions as well, along with non Debian derivatives.[/I]

Also I take no responsibility if anything you do here causes damage to your computer, causes it to blow up, or even if it leads to cats and dogs living together and mass hysteria (Sorry felt like paraphrasing that from Ghostbusters).

[SIZE=3]_**Introduction**_[/SIZE]

A guide of this nature needed to be written for quite some time now. So many of us, myself included, have had some issues, call them quirks, with using our AMD / ATI based graphics cards. This has been regardless of us using AMD's proprietary drivers or the ones the developers in the Open Source community have graciously created for our use. For the most part with the three drivers available, the proprietary and the two available from the community, the complaints have been about the sames types of issues for the most part.

The complaints tend to center around video playback and acceleration. This really has tended to give a bad impression of AMD GPU's and Linux. This is truly not how it should be. The video cards based on AMD GPU's  are far from junk.

AMD based video cards work beautifully under Windows, and that is sadly due to how Gates and Microsoft managed to leverage their places in the marketplace. This part of the history why can bring about a lot of debate. Some would say smart business decisions, others would say unfair business tactics, that is beyond the scope of this guide though. What it did do was create a large gap in hardware support for other operating systems. 

Where Windows has been such the dominant OS, it was only logical to place focus on driver development with it. AMD was not the only GPU maker to go this route. nVidia has done so in the past as well. They learned from having a focus such as this as have other hardware makers.

nVidia got the head start in the Linux market, but that started to change. ATI before the buyout by AMD, changed their focus from developing two separate driver code bases. They unified the code for both Widows, Linux, and it appears MacOSx has been incorporated as well. This has allowed for jumps in driver performance that has been quite large with Linux compared to before the code consolidation. AMD has continued this focus ATI started of bringing Linux into the fold, making improvements on driver capabilities, along with adding support of hardware features the Windows and Mac worlds have had access to. 

AMD is now truly giving nVidia a run for their money when it comes to Linux and the GPU market in general. As PC users, we are starting to see the results. Not only with the products on the market from AMD currently, but also in the leaps fgrlx has seen in performance compared to price point.

I have done a lot of research on the quest to get the absolute optimum from my Sapphire AMD HD 4670 video card. One reason I purchased it, was AMD's UVD and UVD2 technologies which were supposedly coming to Linux through AMD / ATI direct, with support provided through fglrx. Compared to nVidia's VDPAU, it as a technology has definite benefits. Unlike VDPAU, which is a means to support features originally intended to be supported by Windows through DirectX interfaces, XvBA is designed to have API calls that are platform and DirectX independent. XvBA had been designed to be this way from moment one, VDAPU was not, it was adapted.

Sadly, it has taken some time for the reality of XvBA being cross platform to happen. Regrettably, it had to happen after the finalizing of a new MythTV version, which would benefit greatly from adding the means to use XvBA decoding to it. This is because the interface used to access the hardware level of the GPU benefits more then just AMD users.

Accessing XvBA is done through the VA-API interface. This interface was originally designed by Intel for it's own GPU's, but it has grown to allow for nVidia to use it besides AMD. The support base for VA-API has grown including the ability for other GPU makers' technologies to share it's interface. A solution finally has arrived which now allows for code to be written once, it does not matter that each GPU being called by it has totally different coding and hardware structures. That is how it has been for the Windows world with DirectX allowing for interfacing such as this using hooks in the driver API calls. Now this capability on Linux to have code written once and interface with many GPU's allows for us AMD users to have access to hardware accelerated decoding of video and it's playback. Which is definitely something the Linux nVidia camp has rubbed in our faces.

It has allowed for AMD to keep their code for UVD proprietary, only needing a intermediary interface to acces it. This was the majority of code AMD has not been able to release. It is because in UVD / UVD+ / UVD2 capable GPU's, it appears AMD / ATI placed a lot of the hardware decoding features into them with hard linkings to the DRM on each GPU's die.  There was no need to have DRM as part of it, but it does make for implementing HDCP compliant  connectivity and DRM  decoding such as with Blueray in theory easier, just not use under Linux thanks to NDA agreements and our community is all thieves according to groups like the MPAA. Thankfully with the use of VA-API AMD can keep the specs and code agreed to under the NDA internal and we get full hardware accelration and decoding of video.

Now we need to actually look at what you are getting into. From here there are a few things that you will need to know before starting. There are a couple of things you will need or should do before starting.

[U][B]
[SIZE=3]Before Getting Started:[/SIZE][/B][/U]

This guide has been written for Radeon 4000 and 5000 series GPU's. Originally the drivers used in it, were the ones provieded with Catalyst Control Center 9.10 and 9.12 Hotfix. You can still use these drivers, but AMD has released version 10.1 of the Catalyst Control Center and it is the reccomended version to use. If a newer version is available then 10.1 it should be safe to choose that one where AMD is increasing it's efforts to have the VA-API access XvBA.


You can not use any drivers then the ones specified from AMD. Versions of Catalyst Control Center prior to 9.10 are not capable of hardware accelerated decoding and playback of MPEG4 base video. For version 9.12 it is necessary that it is the Hotfix version, otherwise support is broken. As stated, this guide now uses 10.1 and there should be no reason to use the older driver versions. Eventually they will be removed from this guide entirely.

You will be making some changes to your configuration files. So make sure to back them up before making any changes. This way if you do something that makes your graphic interface unusable, you can restore it back to prior the modifications easily.

[SIZE=3][U][B]
Needed Files:[/B][/U][/SIZE]

AMD Drivers:

[COLOR=Blue][Catalyst Control Center Download]("http://support.amd.com/us/gpudownload/Pages/index.aspx")[/COLOR]
*[SIZE=1]*This link takes you directly to the main driver download page for AMD graphics. You can download from here any of the driver versions this guide uses. If using Catalyst Control Center 9.12 Hotfix, you still need to download the original release of it and install it before the Hotfix.[/SIZE]*

[Catalyst Control Center 9.12 Hotfix]("http://support.amd.com/us/kbarticles/Pages/ATICatalyst912Hotfix.aspx")
*[SIZE=1]*Places a watermark in the bottom right of the screen stating "AMD Testing use only" once installed, a reason to consider 10.1.[/SIZE]*

VA-API Files:

[GB's Corner (Developer's Page)]("http://www.splitted-desktop.com/%7Egbeauchesne/")
*[SIZE=1]*The developer has been nice enough to include .deb files for all of the VA-API files[/SIZE].*

You will be downloading the following files:

[LIST]
[*][COLOR=black][libva1]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva1_0.31.0-1+sds9_amd64.deb")
[/COLOR][I][SIZE=1]*This link will directly download the VA-API library binary. It can be updated periodically but not to the point it could not be linked directly here. I will try to keep this link up to date, but if you want to make sure you have the latest go to the developers site using the link above.

[/SIZE][/I]
[*][libva-dev]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva-dev_0.31.0-1+sds9_amd64.deb")
*[SIZE=1]*This link will directly download the VA-API library development files. It can be updated periodically but not to the point it could not be linked directly here. I will try to keep this link up to date, but if you want to make sure you have the latest go to the developers site using the link above.[/SIZE]*
[*][libva1-dbg]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva1-dbg_0.31.0-1+sds9_amd64.deb")
*[SIZE=1]*This link will directly download the VA-API library debug files. It can be updated periodically but not to the point it could not be linked directly here. I will try to keep this link up to date, but if you want to make sure you have the latest go to the developers site using the link above.[/SIZE]*
[*][xvba-video]("http://www.splitted-desktop.com/%7Egbeauchesne/xvba-video/")
*[SIZE=1]*The XvBA interface for VA-API is updated quite frequently with it still being in it's infancy so to speak. I have found it to be very stable even though young, don't let it's short life so far scare you off. This link places you into the directory for it. Make sure to download the latest version.[/SIZE]*
[*][mplayer-vaapi]("http://www.splitted-desktop.com/%7Egbeauchesne/mplayer-vaapi/")
*[SIZE=1]*MPlayer is constantly under development and it appears that the XvBA VA-API interface developer is keeping up with it. Not only for that reason, but also for stability ones I am sure with XvBA and MPlayer as well. This link places you into the directory for it. Make sure to download the latest version[/SIZE]*
[/LIST]
[FONT=Verdana]

[SIZE=2][SIZE=3]**[FONT=Arial]_File Installation:_[/FONT]**[/SIZE][B][FONT=Arial]
[/FONT][/B][FONT=Arial]

Catalyst Control Center:

In order to install the Catalyst Control Center you need to make sure of the following:

[/FONT][/SIZE][/FONT]
[LIST]
[*][FONT=Verdana][SIZE=2][FONT=Arial]This file must be made executable. You can do so through the properties window in your graphics manager or by using the command which will make it so everyone can read write or execute it. Crude but effective for new users:

chmod 777 [/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial]ati-driver-installer-10-1-xx-x86.x86_64.run

[/FONT][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][FONT=Arial]It is recommended to have the file saved in a directory without spaces. The reason is it can error trying to executing the installer. A way around this that should work is to enclose the path and filename in quotes.
[/FONT][/SIZE][/FONT]
[/LIST]
[FONT=Verdana][SIZE=2][FONT=Arial]
sudo sh ati-driver-installer-10-1-xx-x86.x86_64.run --buildpkg Ubuntu/karmic
*[SIZE=1]*This will create a package for installation by apt-get or one of the graphical package managers. Note for Catalyst Control Center 10.1 and Ubuntu 9.10, this option is broken but there is a work around on this forum. It is not the preferred method for this guide and should not be in general. It compiles modules to the current system kernel. If you update the kernel then you are applying old modules to it and that is not the best thing to be doing under any circumstances.[/SIZE]*

or

[/FONT][/SIZE][/FONT][FONT=Verdana][SIZE=2][FONT=Arial]sudo sh ati-driver-installer-9-xx-x86.x86_64.run 
[SIZE=1]**Go through the menus and choose to *[/SIZE][/FONT][/SIZE][/FONT][FONT=Arial][SIZE=1]*install the drivers without using a package. This is the way I prefer. You will have to go in under "safe mode" and rerun this command with every kernel update from the directory where you have it saved, but seems to have less issues then the drivers from packages.*[/SIZE][/FONT]

If you are using Catalyst Control Center 9.12, you will have to install 9.12, then the Hotfix. You can not just install the Hotfix itself which is just the driver files. You also need the Catalyst Control Center as well for this Guide from the non Hotfix Catalyst 9.12.

Once installed you will need to run the following commands:

sudo aticonfig --initial

or

sudo aticonfig --initial -f
*[SIZE=1]*Using the -f option will cause a clean xorg.conf to be written.[/SIZE]*

You will need to make sure there are two files installed with these drivers. For some reason on this pretty fresh install of Karmic they didn't get installed with Catalyst Control Center 9.12. When I upgraded to 10.1 I was unable to see if these files were installed having this setup prior.

The two files are the libraries that VA-API's XvBA interface will be calling to, and the installer seems to neglect X86_64 when installing them. Supposedly, the 32bit binaries for them get installed on both 32bit and 64bit installs but I have no way to confirm this. (If they do not please post here so others will be aware of it.)

The two files should be in either of these locations

/usr/lib

or

/usr/lib64

The missing files:

libAMDXvBA.so.1.0

and

libXvBAW.so.1.0

If they are not on your system, you will need to extract them from the driver .deb. This is easy. Use the following command in the terminal.

sh ati-driver-installer-9-xx-x86.x86_64.run --buildpkg Ubuntu/source

This will create an archive in the same directory as the driver's .deb file. You need to extract this archive, and find the lib64 directory in /x86_64/usr/X11R6/lib64. Inside of it are the files you will need if they were not installed onto your system.

These files will need to be symlinked like the following example once copied there:

sudo ln -s libXvBAW.so.1.0 libXvBAW.so.1

If this is not done, Xv Binary Acceleration errors will arise with the VA-API and it won't work. All you will get is sound and a few errors in the terminal window.

Once you are at this point there needs to be some configuration made to optimize fglrx.

First is to modify your xorg.conf. I have done a lot of research on this particular part of this guide and in your xorg.conf all you should need is the following options set in the driver section under where it says Driver  "fglrx".

su gedit /etc/X11/xorg.conf

or 

su kedit /etc/X11/xorg.conf 

This snippet allows for OpenGL Rendering to work properly in MythTV, reduces tearing greatly if not removes it for Xv, specifically tells X which monitor to overlay on (Should be enabled even if a single monitor setup.), and also enables FastTLS an AMD optimization.

```

    Option        "TexturedVideoSync" "on" #HD4xxx & HD5xxx use textured video to render Xv. This helps to remove tearing.
    Option        "Capabilities" "0x00000800" #This option also turns on vertical syncing as well. Both can and do work well together.
    Option        "OpenGLOverlay" "off" #This is for workstations and certain commercial graphics applications for them. Nothing as Linux user that we do needs this so disabled.
    Option        "UseFastTLS" "on"
    Option        "OverlayOnCRTC2" "0" #For some reason when only using one monitor it should see this and use overlay on it correctly and does not. This I believe is what caused some of the MyThTV issues. This needs to be set to 0 for a single monitor application and in a multiple monitor to the one MythTV is displayed on.

```Now it is time to reboot your machine and configure the Catalyst Control Center:

Open as administrator from your machine's launch menu or by the means below the Catalyst Control Center

$ amdxdg-su -c amdcccle

or

$ sudo amdcccle

Now we need to adjust several settings here before continuing.

Note before starting that these settings work on the HD4670 without issue. On the older GPU's supported by the proprietary driver or even a lower 4XXX model, these settings may be too much for system to handle and run smoothly. There might have to be some tweaking to your specific system.

Go to the 3D section of the options list on the left. These settings actually effect 2D rendering in Linux as well to some extent. It doesn't say it does, but they do. It is because rendering even when not using OpenGL in Linux still uses it for things like vertical syncing, also we will be using OpenGL rendering in a large part of this guide for rendering and playback.

You are going to manually override the system settings on each of the options for 3D to their max settings. I have absolutely no problems with rendering doing so and the quality difference is quite noticeable. If your system has problems handling the workload they will have to be brought back from max settings a little.

Anti-Aliasing:
Override and set to 8x

Adaptive Anti-Aliasing:
Override and set to Quality

Anisotropic Filtering:
Override and set to 16x

MipMap Detail
Override and set to High Quality

More Settings:
Wait for Vertical Refresh
 Set to on unless application specifies off
[SIZE=1]** This is the second to last option. You can set to be always on, but no need for it. If an application wants no refresh rate syncing let it. Plus having it on is actually better in my opinion. What is so great getting 10,000 frames a second if the display can't reproduce it. Visually all you will see perceive is what the display is capable of.*[/SIZE]

Enable Catalyst AI:
You want to enable and set to advanced.

You will need to at minimum log out and back in for these settings to take effect, but I would suggest a reboot to be safe. Sometimes fgrlx settings don't want to take unless there is a reboot involved, and the nature of the beast so to speak.

VA-API Files:

Install in this order. If you try to install in any other order it should throw an error.

[LIST]
[*][COLOR=black][libva1]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva1_0.31.0-1+sds9_amd64.deb")[/COLOR][I][SIZE=1]
    
[/SIZE][/I]
[*][URL="http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva-dev_0.31.0-1+sds9_amd64.deb"]libva-dev

[/URL]
[*][URL="http://www.splitted-desktop.com/%7Egbeauchesne/libva/pkgs/amd64/libva1-dbg_0.31.0-1+sds9_amd64.deb"]libva1-dbg

[/URL]
[*][URL="http://www.splitted-desktop.com/%7Egbeauchesne/xvba-video/"]xvba-video

[/URL]
[/LIST]
[FONT=Verdana][SIZE=2][FONT=Arial]Mplayer Compile and Install:

Before starting please note. If you are using the nightly stable or tree builds of MythTV you will encounter your package manager wanting to remove MythTV. The reason being is MythTV is using a new VDAPU library and MPlayer needs the old one to have it's dependencies met. I am currently trying to get it to work around this, but to little success. If you want to compile your own you will have to let it remove the newer MythTV, or I do have two pre-compiled versions of MPlayer that I made before switching to the nightly builds of MythTV 0.22.

One is a strict MPlayer without GUI, the other is compiled for a the GUI and because of it buggy as all hell. They have been compiled for X86_64 on an AMD AM2 based processor but should in theory run on any X86_64 system. I have created a tarred bziped file of them. It is too big to include here, but if there is enough interest I will find a place to setup a link to from here. Message me or post here if you you like me to include a link to them.


To build your own:
[/FONT][/SIZE][/FONT]
[LIST=1]
[*]$ sudo apt-get build-dep mplayer
[*][FONT=Verdana][SIZE=2][FONT=Arial]Extract the bzip2 file containing MPlayer and enter the extracted directory.[/FONT][/SIZE][/FONT]
[*][FONT=Verdana][SIZE=2][FONT=Arial]$ ./checkout-patch-build.sh
[/FONT][/SIZE][/FONT]
[/LIST]
Let it build MPlayer. It could take a few for the compiling of MPlayer. If you smoke, now would be a good time to go have one. It took on my AM2 Dual Core less then 10 minutes, about a cigarette to be honest, and that was applying the patches besides the compile.

This is just mplayer, no gmplayer is compiled with the script. It is best for use with keyboard shortcuts and / or Lirc on the note of controls. Remember though this version of Mplayer was given to us through the generosity of the VA-API XvBA interface and it's developer so don't be going awwwww man or complaining.

To start this VA-API enabled Mplayer for Testing:

*[SIZE=1](*Below was taken from the readme word for word)[/SIZE]*
$ cd mplayer-vaapi
$ ./mplayer -vo vaapi -va vaapi <URI>

<URI> can be a pathname or an URL.

For OpenGL rendering:
$ ./mplayer -vo vaapi:gl -va vaapi <URI>

For OpenGL rendering with reflection effect:
$ ./mplayer -vo vaapi:gl:reflect -va vaapi <URI>

The reflect option is as it sounds, and kinda trippy..lol.

It provides a mirrored copy of the file you are playng inside the MPlayer window.

Test MPlayer at this point with an MPEG4 stream such as AVC1, WM3 aka WM9, or VC1. It uses either Xv and GL rendering, Regardless of which renderer you choose, everything should be working for you beautifully on the note of hardware acceleration. I personally find the picture quality a little bit better using the openGL renderer and it is absolutely tear free besides. Plus it actually uses a bit less processor on my system then Xv, go figure.

You can compile this version of MPlayer to use the GUI, but will have to go into the directory yourself to do so. In order to do this, you need to either manually patch the source or let the script run to do it and make the default MPlayer that it does.

Then go into the directory, and do a make clean after the script has completed. You can do the make-config, make, etc yourself now. Remember you will have to pass the options to MPlayer for it to compile with VA-API support.

This is how you would do it:
$ ./configure --enable-vaapi --disable-vdpau

Then you need to configure the GUI and OSD for it:
$ ./configure --enable-gui --enable-menu

Finally Compile it:
$ make

If you are satisfied with how it is working and want to install it:
*[SIZE=1]*Remember this is experimental and I will not take responsibility for doing this. You will need to have the packaged version of MPlayer removed to do so as well.[/SIZE]*

$ make install

Please Note: 

There is a patch for VLC to use the VA-API library. It has not been mainstreamed into the code at this point. If you were to want VLC you need to get this patch, apply it, and compile your own copy of it. I do not have the patch or the source code for VLC linked here. You can go to the [VideoLan]("http://www.videolan.org") website for it.

I would like to setup a VA-API PPA for 9.10 and other releases as well. If someone wants to build packages of compiled versions of MPlayer in 32bit or 64bit, VLC, etc., message me here and I will get it all setup. Ubuntu really needs to have one easy setup repository for doing this.

[SIZE=3]_**At this Point:**_[/SIZE]

Now your system is ready to have your video applications configured, in the case of this guide MythTV and Mplayer primarily. In order to do so properly lets look at what we have done up till this point and also what has been added to the fgrlx driver but not widely documented. It will all start to click with seeing everything listed here.


_**Hardware Decoding / Acceleration:**_

_MPEG1&2 Decoding and Acceleration:_
It is little known that as of Catalyst Control Center 9.10, maybe even before this release of it, AMD re-enabled hardware decoding of these streams through the AVIVO now UVD interface using XvMC not XvBA. It works very well, and for the most part is fully compatible with the VIA implementation that nVidia also supports in their older GPU's. HD MPEG2 streams decode on my system use almost no processor and only 30% of the GPU at peak hits to it decoding, heavy action scenes are an example, but the core is keeping itself at the minimum clocking when under 30% load. This is using MythTV, which was itself using the processors at around 10% combined on a dual core AM2.

This capability is only available on HD4xxx and higher GPU's from what some members out here are finding out. This may change at some point though and dependent on AMD supporting it through their proprietary driver. If someone on a GPU prior to the HD4xxx's tries this and it is a success let me know or post it here so this section can be corrected.

[U]MPEG4, AVC, WM3 aka WM9, and VC1 Decoding and Acceleration:
[/U]Even though "experimental", you now have hardware accelerated decoding of MPEG4 based streams. Personally I have found the results to be far superior then ffmpeg decoding with no artifacts, not had one crash using it so far, and would not consider this to be experimental myself at this point, but who am I to argue.

Update January 29, 2010:

I have currently tested the hardware decoding with a variety of "non-supported" formats. I have tried the old Windows hacked DiVX 3 along with the legal version 5 encoded files and they playback flawless. They do have a tendency to tax the GPU a little, especially DiVX 3, but regardless play very well for me. I have also tried ffmpeg and Xvid encoded videos with great success as well. From my experience, I will say with relative safety that it will play nearly all MPEG4 formats.


**_No More Tearing:_**

Making the changes you have to your xorg.conf and Catalyst Control Center should now have tearing as a thing of the past. For Xv rendering it is substantially reduced to nearly non existent levels. You may on a rare occasion see a tear or line cutting through the picture, usually in very high speed movement, but not what it was before then.

OpenGL, whether with or without the use of XvBA hardware decoding and acceleration, will be absolutely 100% tear free. With the settings of Catalyst Control Center, the picture quality should be better then Xv as well.  You may have to increase the brightness settings a little though. This is from my experience of course, and your's may vary.

With the update of this guide, you are now presented with choices in rendering using MythTV owning an AMD GPU finally. We have never been able to properly run OpenGL rendering with MythTV and I have seen posts to this extent going back several years.

No offense meant to the MythTV developers, but they have never truly addressed the owners of ATI / AMD GPU's. We are like the red headed stepchildren of the MythTV community of users. While the favorite son, nVidia, has received all of your love with us over in the corner, neglected, even ridiculed and made fun of.

When MythTV 0.22 was in development, the VA-API which would have benefited a large number of GPU's including both AMD and nVidia was neglected, yet VDAPU wasn't. This limited hardware acceleration of MPEG4 to only nVidia. That is to extent proof to this favoritism and being the red headed stepchild. This lead me to rebel like us red headed stepchildren tend to do and find my own solution, and I did eventually.


**_No More Pulling Your Hair Out:_**

Watching video without tearing, until now using AMD GPU's has been a pull your hair out, and want to scream situation. The distributions should help minimize this, and help it from not happening offering compiled binaries of these drivers for use. Yet they don't. These are settings I provided for the xorg.conf are common to nearly all AMD graphics using proprietary drivers, especially HD4xxx and higher. The other settings in the Catalyst Control Center can be set I am sure to default to what I have found to be optimal assuming detection of the GPU is done correctly. If not a pop up windows saying hey you have this driver installed and these settings should be made to not encounter tearing, etc, would be nice.

The MythTV developer's focus on nVida to an extent hasn't help with hair pulling. There is little to no documentation on getting the most out of AMD graphics with MythTV from them, yet there is post after post on many forums asking for solutions and help. Then at least in my experience, when going out actively searching for a solution or a suggestion to improve playback on the MythTV IRC channels instead of anything constructive I am told to go out and purchase an nVida card far inferior to my AMD and nearly costing the same. How is that a solution?

So to save you from pulling your hair out, I did instead. I jokingly say to some it is why I began buzzing my head down. Because my hairline couldn't take much more of dealing with getting MythTV and it was the only way to keep the hair I still got..lol.

Now it is time that we have all the components to put them all together and have them play nice.

[SIZE=3]_**Putting it all Together**_[/SIZE]

It is time to setup MythTV and MPlayer. The way described here does not replace the existing install of MPlayer you have. Where this software is considered experimental I deemed it best to create a bin directory in the user's home directory, and then call it like any other application from a modification to the bashrc script for the account being used. Lets see how everything goes together.

_**Getting MPlayer to Work with Shortcuts and by Calling it Directly:**_

We now need to setup this version of MPlayer to be able to be called by command line by name and also by shortcuts without providing paths.

Create a directory called bin in your home directory as follows:

~$ mkdir /home/{username)/bin

Now move your compiled MPlayer directory into the bin directory you just created:

You can do this but need to have the name change if directly in bin, otherwise the symbolic link won't work properly. The other options would be to set it inside another directory. Then there will be no issue. That is how I actually did mine.

~$ mv /home/{username}/{directory where you extracted the whole archive}/mplayer-vaapi-20100114/mplayer-vaapi /bin/mplayer

Now we need to symlink mplayer and gmplayer if you compiled a graphics enabled version to be executable the way we want. You will need to make 3 symlinks for this to work properly. One of these symlinks is needed if only using MPlayer created by the script.

 *All these commands are assuming that you are in the bin directory you created.*

Needed Symlink:
ln -s mplayer-vaapi /mplayer/mplayer

Optional gmplayer Symlinks:
ln -s /mplayer/gmplayer /mplayer/mplayer

ln -s gmplayer-vaapi /mplayer/gmplayer
*[SIZE=1]*This one can also link directly to the mplayer binary file itself as well. I figured this way it is consistent.[/SIZE]*

Now we need to make it so when you are in a terminal or click on a shortcut bash knows what to do. You need to have your bin directory declared in one of two files. It can be declared locally or globally in bashrc. If you declare it globally, regardless the account you are in, you should create a bin directory for it, even if there is nothing in it at all.

_Declaring in Bash Locally:_

To Open the File:

$ gedit ~/.bashrc

$ kate ~/.bashrc
[U]
Declaring in Bash Globally:[/U]

$ su gedit /etc/bash.bashrc

$ su kate /etc/bash.bashrc

Add the Following at the Bottom of bashrc:

PATH=$PATH:~/bin
export PATH

Log out or reboot. If declaring globally, to be safe I would reboot. Honestly I would just reboot regardless. Now you should be able to call Mplayer and GMplayer by the names of the symlinks that you created. To test it open up a terminal and try it.

Example (If gmplayer config was done before making the binaries)
$ gmplayer-vaapi

If you want to try MPlayer (This example uses the openGL renderer. I had an issue with the bottom of the video cut off in full screen my self):
$ mplayer-vaapi -vo vaapi:gl -va vaapi <URI>

To create shortcuts, refer to your desktop's documentation.

[SIZE=2]_**Setup of MythTV 0.22:**_[/SIZE]

MythTV in my opinion, is one of the best HTPC applications out there. It is not only very powerful, It is very flexible. It allows for you to configure a lot of parameters to try to get the best out of your setup. In particular we will be looking at the features associated with its decoding and playback capabilities, such as the actual decoder choices, deinterlacers, and renderers. Those are the only ones really of concern for this tutorial.

Before we start, I want to state that because of the lack of knowledge that AMD had reinstated XvMC decoding in their drivers there are some deinterlacing issues that were there for all the x2/2x deinterlacers in version .021. They have since been corrected in Xv and OpenGL rendering with 0.22, just not with XvMC with the it's releases.

MythTV also, as of the release of version 0.22 does not support as stated, the VA-API natively. I have searched to see if there has been a patched version made, but no luck on it. I may have found a patch for the source code though. As I said I would like to setup a PPA for all of this. If someone would like to compile a version that includes support for the VA-API interface I can point you in the right direction to that possible patch and we can go from there.

If it turns out not to be a patch for it, and someone has MythTV coding experience that wants to get this working, you can modify the code and I will include it in the PPA.

Now lets get into the settings of MythTV.

First off you are going to have to make some decisions at this point. These are going to be based off of personal preference, and your hardware beyond the AMD video cards this guide has been written for. If your system is slower processor wise, you are going to have to compromise obviously.

For example, I have also found a bug in OpenGL rendering with MythTV on all levels that has me making compromises, but now it is workable, not perfect, but workable. I can not get it to render properly with menus at all using the OpenGL renderer for them. It is not the distortion bug they have corrected. It is rendering on the note of placement of windows. This could be a drawing issue with OpenGL and MythTV in relation to AMD because they are the only application using OpenGL that I have seen this happen.

The ew windows you go into remain under the one you are on, at least it appears to be like that. My solution to get to the next window is to switch to a terminal and then go back to my desktop session using Ctrl+Fn1 then Ctrl+Fn7. That is how I manage to go in to switch back to Qt rendering for menus.

This issue happens when you are using the Xv or other render options too with OpenGL menus it does not matter. Then with the OpenGL rendering and Qt for menus it will happen without the additions to the xorg.conf I added to it recently. What happens is the guide is rendered once if you are lucky then it does not get to be on top again at all unless you exit Live TV and then it is sketchy on seeing it again without a full restart of MythTV. You can also do the same terminal switch workaround I use with the menus to it.

I am also finding the One  Field deinterlacer for XvMC renderer to be nasty when it comes to standard definition cable coming off the firewire port on my cable box. It is all pixelated and rough looking. You would think that the same would be true for high definition 4:3 as well, but it is not. It actually looks very watchable. As is high definition 16:9.

Knowing that, you may and probably will encounter these types of issues, here are my settings that I have come to tweaking things. Remember my system is more then capable of handling a heavy of load. It is an AM2 Athlon X2 5.4GHz (2.7GHz per core), 2GB of ram, with a Sapphire HD4670 sporting 1GB GDDR3. If you are working with a less powerful system these settings probably won't work the best for you. I am providing them as a baseline for you to go by.

**_MythTV Rendering Settings:_**

Here you are going to have to make a choice. If the system is under high demand say acting as both a frontend and backend with multiple connections, then you will probably want to consider the use of XvMC for MPEG2 decoding. If not, then with how OpenGL provides absolute tear free watching, you should consider it. So you may want to take a moment now, think about these types of considerations, and decide which route you will want to go. Personally the system I am using for this guide is used strictly as a frontend in regards to MythTV, so I run OpenGL and software decoding through ffmpeg for MPEG2 decoding off my cable box and ATSC/QAM tuner.

Now you can setup multiple decoder profiles with MythTV and this can be very helpful, or it can lead to the proverbially shooting yourself in the foot. You just need to make sure that you think first and not just go oh okay this should work. There are a couple of different profiles we are going to setup for MythTV in this guide, lets look at them.

On your frontend you are now going to start it and go into the settings of MythTV.

Utilities/Setup>Setup>TV Settings>Playback

Screen 1:

[LIST]
[*]Check off picture controls[SIZE=1][I]
This will allow for you to make color corrections if necessary.

 [/I][/SIZE]
[*]Optionally you can check Enable OpenGL vertical Sync for timing, but it may conflict with what we have set otherwise and cause the picture to get jittery even though it is supposed to stop jitter.
[/LIST]

Screen 2:

Skip it. It does not pertain to what we are doing here.

Screen 3:

[LIST]
[*] Current Playback Profile I have set to High Quality where I tend to watch a majority of my programming and videos in HD.
[*] You should now see four playback profiles. The first two are your primary choices and the second two are the fall backs so to speak. If the video's format does not match the first two it will use the second two.
[*]You are now at the point where you should have decided on how you are going to have MythTV render video. We are going to setup MythTV according to what you have decided. Below are two examples of changes to make. The first is for setting up MythTV to playback using ffmpeg for decoding and OpenGL for rendering. The other example is for setting up MythTV to use hardware decoding for MPEG2. Please note, I have depreciated the value of XvMC in this guide, but it is still relevant for those of you looking for a hardware decoding solution.
[*]You can mix and match these decoder profiles to suit your needs as well. Decoding of MPEG2 HD content you may want to set to use hardware decoding because of overhead, no worries you can do that.
[*]Changes to Playback Profiles OpenGL Rendering:
[LIST]
[*]If rez is >= 1920x1080 (Ranked 1)
[LIST]
[*]Decoder leave at Standard.
[*]Video Renderer Set to: OpenGL
[*]OSD Renderer Set to: OpenGL2
[*]Next Screen (Deinterlacers)
[LIST]
[*]Primary Deinterlacer Set to: Bob(2x,HW)
[*]Fallback Deinterlacer Set to: Linear Blend(HW)
[/LIST]
 
[*]Click Finish.
[I][SIZE=1]*Your primary profile for 1080p/i has now been created. Now to create a profile for standard definition through to 1080p/i.
[/SIZE][/I]
[/LIST]
 
[*]If rez is >= 0x0 (Ranked 2)
[LIST]
[*]Decoder leave at Standard.
[*]Video Renderer Set to: OpenGL
[*]OSD Renderer Set to: OpenGL2
[*]Next Screen (Deinterlacers)
[LIST]
[*]Primary Deinterlacer Set to: Bob(2x,HW)
*[SIZE=1]*You may notice occasionally some slight interlacing on standard definition content using this deinterlacer, but the picture quality out weighs this.[/SIZE]*
[*]Fallback Deinterlacer Set to: Linear Blend(HW)
[/LIST]
 
[*]Click Finish.
*[SIZE=1]*Your primary profile for standard definition up through 1080p/i has been created.[/SIZE]*
[/LIST]
 
[*]If rez is >= 1920x1080 (Ranked 3)
[LIST]
[*]Decoder leave at Standard.
[*]Video Renderer Set to: xv-blit
[*]OSD Renderer Set to: softblend
[*]Next Screen (Deinterlacers)
[LIST]
[*]Primary Deinterlacer Set to: Greedy HighMotion(2x)
[*]Fallback Deinterlacer Set to: Greedy HighMotion
[/LIST]
 
[*]Click Finish.
  [I][SIZE=1]*Your fallback profile for 1080p/i has now been created. Now to create a profile for standard definition through to 1080p/i.

[/SIZE][/I]
[/LIST]
 
[*]If rez is >= 0x0 (Ranked 4)
[LIST]
[*]Decoder leave at Standard.
[*]Video Renderer Set to: xv-blit
[*]OSD Renderer Set to: softblend
[*]Next Screen (Deinterlacers)
[LIST]
[*]Primary Deinterlacer Set to: Greedy HighMotion(2x)
[*]Fallback Deinterlacer Set to: Greedy HighMotion
[/LIST]
 
[*]Click Finish.
  *[SIZE=1]*Your fallback profile for standard definition up through 1080p/i has been created.[/SIZE]*
[/LIST]
 
[/LIST]
 
[*]Changes to Plaback Profiles for XvMC:
[I][SIZE=1]*Note these changes are presented separate because they have been depreciated in this guide to some extent, but are still pertinent and useful. It looking to lower overall system load these are the settings to consider. An example would be rendering HD MPEG2. The fallback decoders have been seet to use Xv in this example of settings but the settings for OpenGL can be substituted in their place.
 [/SIZE][/I]
[LIST]
[*]If rez is >= 1920x1080 (Ranked 1)
[LIST]
[*]Decoder change to VIA XvMC
[I][SIZE=1]I noticed a difference between standard XvMC and VIA XvMC so you might want to try both and judge it yourself.[/SIZE]

[/I]
[*]Next Screen (Deinterlacers)
[I][SIZE=1]I had Issues with the Bob x2 deinterlacer under XvMC where it would render 2 pictures, one on top the other. Picture looks good on 1080p display using these settings. If sending to a television you may want to set to none and let the television do deinterlacing where it will probably produce better results.[/SIZE]

[/I]
[LIST]
[*]Primary Deinterlacer set to One Field
[*]Fallback Deinterlacer set to One Field
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST]
[*]If rez is >= 0x0 (Ranked 2)
[LIST]
[*]Decoder change to VIA XvMC
*[SIZE=1]I noticed a difference between standard XvMC and VIA XvMC so you might want to try both and judge it yourself. You might want to leave this one set to standard if you watch a lot of standard definition television and choose through the deinterlacers for Xv rendering because it gets extremely pixelated using One Field. [/SIZE]*[I][SIZE=1]If sending to a television you may want to set to none and let the television do deinterlacing where it will probably produce better results.

[/SIZE][/I]
[*]Next Screen (Deinterlacers)
[I][SIZE=1]I had Issues with the Bob x2 deinterlacer under XvMC where it would render 2 pictures, one on top the other.[/SIZE]

[/I]
[LIST]
[*]Primary Deinterlacer set to One Field
[*]Fallback Deinterlacer set to One Field
[/LIST]
 
[/LIST]
 
[*]If rez is >= 1920x1080 (Ranked 3)
[SIZE=1][I]Without this profile the internal player for MythTV is only capable of rendering MPEG2, technically the second ranked one if set to standard will correct that, but we are not using it on standard in the setup. This is only useful if you are using standard as the number 2 profile and I would still set the others as well to be safe.

[/I][/SIZE]
[LIST]
[*]Decoder leave at Standard.
[LIST]
[*]Video Renderer Set to: xv-blit
[*]Next Screen:
[LIST]
[*]Primary Deinterlacer Set to: Greedy High Motion (2x)
[*]Fallback Deinterlacer Set to: Greedy High Motion
[/LIST]
 
[/LIST]
 
[/LIST]
 
[*]If rez is >= 0x0 (Ranked 4)
[LIST]
[*]Decoder Leave at Standard[I][SIZE=1]

[/SIZE][/I]
[LIST]
[*]Video Renderer Set to: xv-blit
[*]Next Screen:
[LIST]
[*]Primary Deinterlacer Set to: Greedy High Motion (2x)
[*]Fallback Deinterlacer Set to: Greedy High Motion
[/LIST]
 
[/LIST]
 
[/LIST]
 
[/LIST]
 
[/LIST]
Exit out of these options by clicking finish when complete.


Now that we have MythTV setup for optimal playback, and we have a version of MPlayer that takes advantage of hardware acceleration, lets make them play nice together. ;) :D

_**MythTV and our Version of MPlayer Playing Nice Together:**_

This is pretty easy to accomplish, and MPlayer has been the default player in previous versions of MythTV along with as of version 0.22 the alternative player by default. This is true at least with Ubuntu variants.

We now need to change some settings in another part of MythTV. If you are still in the settings for television, back out a couple of screen to the main part of MythTV setup. From there you want to migrate to video player settings.

From the main menu:

Utilities/Setup>Setup>Media Settings>Video Settings>Player Settings

We are going to change Alternate Player, not the primary one. You are probably asking why. Simply, it is easy to have a video start playing with the alternate player, this is still experimental and may not support all of your files, and I am not going to have a bunch of people say I told them to make it the primary if they encounter issues or it doesn't play a file..lol.


Under Player Settings Change the Alternate Player to:

mplayer-vaapi -channels 6 -fs -cache 8192 -vo vaapi:gl -va vaapi

The above is assuming you have a 5.1 speaker system setup on your computer using the -channels 6 switch and if you are accessing any of your files over the network on a mounted NFS or Samba share, add the switch -cache 8192. This is so you don't have audio and video syncing issues. It is also assuming you use Alsa's default output.

That is pretty much it. If you are using PulseAudio and have it all setup, now whether you open a video with a 2.0 or 5.1 audio track, all of your speakers will work.

If you are using Alsa and don't want to have to change any settings on your device out in the video player alternate player settings, for like up-mixing, I am sorry to say there is no way around it currently except to manually specify a unique player for the file under metadata settings and tell it to pass the sound to the device you created for upmixing.


That is pretty much it for setting this up. To use the MPlayer that you have created in MythTV, when on a video in the media library click i on the keyboard or info on your remote. If you then select play it gives the choice of using the default or alternate player, choose alternate and away MPlayer goes. Nothing could be simpler on the note of being able to pick and choose when you want to use the benefits of XvBA. :D

Now we need to setup our other players. I have found that the OpenGL renderers tend to look better and reproduce better playback. It is tear free afterall. This means other players can benefit from the tweaks as well. Lets get into those.

[SIZE=3]_**Other Video Players:**_[/SIZE]

Go into the settings on these other video players like VLC, Xine, etc, and select OpenGL or OpenGL2 for rendering. That is pretty much it. You can use the Xv rendering, but I noticed with all of the settings as they are from the tweaking, the quality is much better for me including absolutely fluid and and flawless playback.

[SIZE=3]_**At the End of it All**_[/SIZE]

I hope that someone finds this guide useful and is thankful for it, not taking it for granted. I spent a lot of time researching from multiple outlets, many untold hours actually, and decided to share my experience and knowledge in this arena. I didn't want to see anyone go through what I have looking everywhere for answers and loose time that could be better spent, like with family enjoying the HTPC. In doing so, I spent several days working on this guide besides.

If you find it useful all I ask is for you to take a second and say thank you by leaving a post in this thread. I would also like for you to let the others know if you do how it is working for you, good, bad, or otherwise. This way others will get your opinions, and also you might find settings that others could find useful, maybe even me. I still haven't tried every combination.

I hope this becomes a sticky here as well so it is easy to gain access to by other Ubuntu users and other Linux users in general so they can get the most out of their AMD HD4xxx and HD5xxx series video cards.

Enjoy
Sports Car Guy

---

### Post by sports.car.guy on 2010-01-20
I just found one issue I am trying to figure a solution out with. For some reason using XvMC when watching an ISO backup, a legal one mind you, and also a DVD from disc, there are major audio syncing issues. This appears to be a kink in the chain so to speak.

I am looking online for a solution like passing to the internal player to use the standard Xv and then what to deinterlace with in the settings for DVD player.

If you know a solution let me know make a post and I will edit the guide to reflect it. I will do that if and when I find it as well.

---

### Post by lenkiatleong on 2010-01-20
My goodness. I can imagine how many hours you had spent writing the good stuff above for the benefit of everyone!!

Very quickly, i'm using Ubuntu 9.10 (64bit), Intel DP35DP, Nvidia 8600GT, Q6600 CPU. Using VLC with H264 decoding set to "all", i can play m2ts file from my Sony cam (HDR-CX520E) relatively smooth but not as good as playing directly from the cam to HDTV or with windows media player 12 in windows7 which is clear, crispy and smooth. The VLC playback is not smooth, sometimes with artifacts and very blur when i pan the camera quickly.
According to several good forumers who tried the video i posted [http://www.mediafire.com/file/jdjthekzlj5/00003.MTS ]("http://www.mediafire.com/file/jdjthekzlj5/00003.MTS"), the problem lies with Ubuntu, VLC and the AVCHD codec which my current rig could not make it (procrastinating to switch to win7 now).

At first, i was thinking to change my Nvidia 8600 to ATI 5000 series and that's why i bumped into your good thread while researching. Your posting would absolutely help me if i change to ATI card. But before that, can you please help me confirm that you could play my video file in your rig and see whether the playback is smooth or not with the optimising done. Thanks in advance.

---

### Post by sports.car.guy on 2010-01-20
> **lenkiatleong said:**
> My goodness. I can imagine how many hours you had spent writing the good stuff above for the benefit of everyone!!

Very quickly, i'm using Ubuntu 9.10 (64bit), Intel DP35DP, Nvidia 8600GT, Q6600 CPU. Using VLC with H264 decoding set to "all", i can play m2ts file from my Sony cam (HDR-CX520E) relatively smooth but not as good as playing directly from the cam to HDTV or with windows media player 12 in windows7 which is clear, crispy and smooth. The VLC playback is not smooth, sometimes with artifacts and very blur when i pan the camera quickly.
According to several good forumers who tried the video i posted [http://www.mediafire.com/file/jdjthekzlj5/00003.MTS ]("http://www.mediafire.com/file/jdjthekzlj5/00003.MTS"), the problem lies with Ubuntu, VLC and the AVCHD codec which my current rig could not make it (procrastinating to switch to win7 now).

At first, i was thinking to change my Nvidia 8600 to ATI 5000 series and that's why i bumped into your good thread while researching. Your posting would absolutely help me if i change to ATI card. But before that, can you please help me confirm that you could play my video file in your rig and see whether the playback is smooth or not with the optimising done. Thanks in advance.


I just checked it out using both VLC and the modified Mplayer. Under Xv rendering in VLC it tore a little, but not badly. Using OpenGL with VLC no go. Using the modified MPlayer, there were some syncing issues with both Xv and OpenGL. The syncing issues could be a couple things though with MPlayer. 

The state of the code and support for the actual MPEG data inside the container file could be why. Not all MPEG4 is fully supported through the VA-API for XvBA or the cache for MPlayer needs to be cranked up. Well checking again it looks like it is maxing the GPU, but I think that is the state of the code and supporting the MPEG4 data. If VLC can play it using the CPU and Xv, then offloading to the video card shouldn't have the issues it did.

Sad part is even though each company licenses H264 we will say, it doesn't stop them from messing with it and causing compatibility issues when it is a standard. I am betting once the code matures hardware accelerated playback will work on my system and your clip flawless.

Also take into account the HD4xxx and HD5xxx series are a little different. I am betting the HD5xxx would do better with it.

I have tested it on 15 GB Blueray backups and not had one problem at all.

This is now got me wondering on if it is the format of the H264 itself.

---

### Post by lenkiatleong on 2010-01-20
> **sports.car.guy said:**
> I just checked it out using both VLC and the modified Mplayer. Under Xv rendering in VLC it tore a little, but not badly. Using OpenGL with VLC no go. Using the modified MPlayer, there were some syncing issues with both Xv and OpenGL. The syncing issues could be a couple things though with MPlayer. 

The state of the code and support for the actual MPEG data inside the container file could be why. Not all MPEG4 is fully supported through the VA-API for XvBA or the cache for MPlayer needs to be cranked up. Well checking again it looks like it is maxing the GPU, but I think that is the state of the code and supporting the MPEG4 data. If VLC can play it using the CPU and Xv, then offloading to the video card shouldn't have the issues it did.

Sad part is even though each company licenses H264 we will say, it doesn't stop them from messing with it and causing compatibility issues when it is a standard. I am betting once the code matures hardware accelerated playback will work on my system and your clip flawless.

Also take into account the HD4xxx and HD5xxx series are a little different. I am betting the HD5xxx would do better with it.

I have tested it on 15 GB Blueray backups and not had one problem at all.

This is now got me wondering on if it is the format of the H264 itself.

Thanks for trying out my video clip. Its quite confirm that VLC in Ubuntu/Windows did not play AVCHD as well as WMP12 in Win7. WMP12 is quite awesome. You can try it.

Its good to know that you could run bluray backups well in Ubuntu. This is the next thing i am trying out. Still waiting for bluray drive price to come down. I reckon that you are using MPlayer. Did VLC works with your bluray? Can any media player stream Dolby TrueHD or DTS HD MA to your AV receiver? I'm looking for ATI 5000 series card to do this but i have yet to purchase any. Still researching....

My ultimate aim is use Ubuntu as HTPC to stream video/audio via hdmi to AV receiver that supports all codecs available today. I am now half way there, i.e., using VLC to stream lower grade Dolby/DTS 5.1 via optical port. Would be good to hear your comment on how to achieve this with ATI card.

---

### Post by n3had on 2010-01-20
Hi before i say anything !thankyou! for this great thread and putting all this time for all the ubuntu'ers to benefit and i want to ask couple of questions here

1. I have onboard ATI HD4200 graphics so does it have the HD acceleration you are talking about? 

2. I have tried the propriety drivers before and had issues with compiz and also video playback. Compiz used to crash every now and then(that maybe due to improper uninstallation of nvidia drivers)

3. Switched to opensource Drivers no issues at all except very poor 3D performance as its in experiment mode.

Now should i give this tut a try?

---

### Post by sports.car.guy on 2010-01-20
> **lenkiatleong said:**
> Thanks for trying out my video clip. Its quite confirm that VLC in Ubuntu/Windows did not play AVCHD as well as WMP12 in Win7. WMP12 is quite awesome. You can try it.

Its good to know that you could run bluray backups well in Ubuntu. This is the next thing i am trying out. Still waiting for bluray drive price to come down. I reckon that you are using MPlayer. Did VLC works with your bluray? Can any media player stream Dolby TrueHD or DTS HD MA to your AV receiver? I'm looking for ATI 5000 series card to do this but i have yet to purchase any. Still researching....

My ultimate aim is use Ubuntu as HTPC to stream video/audio via hdmi to AV receiver that supports all codecs available today. I am now half way there, i.e., using VLC to stream lower grade Dolby/DTS 5.1 via optical port. Would be good to hear your comment on how to achieve this with ATI card.

I haven't used Windows in quite some time and I would put money that WMP12 has stolen code from Media Player Classic or MPC Home Cinema. That is what Microsoft does. It is a fact and was proven that Gates gave the order to steal the TCP/IP stack from BSD for Win2k and up. They couldn't get their in house one to work properly.

Someone for the open source community noticed some of it's calls in memory looked familiar and proceeded to reverse engineer it to confirm before a decompile. He wanted to make sure he wasn't doing something illegal just in case it was close but no cigar. He was more then confident it was and did the decompile.

Gates and Microsoft freaked when it came out. They got caught and had the balls to try to get this guy arrested and all this other stuff for theft when they stole the TCP/IP stack. That was when they couldn't get him to shut up about it and he was letting the world know. They never paid the BSD community for use and till this day use the TCP/IP stack they stole in Windows without giving the credit BSD licensing requires.

If you think WMP 12 is fast, check out the original Media Player Classic or the Home Cinema Edition. It has always been feature rich, more so then WMP and  with so much of a smaller footprint memory and processor wise.

---

### Post by sports.car.guy on 2010-01-20
> **n3had said:**
> Hi before i say anything !thankyou! for this great thread and putting all this time for all the ubuntu'ers to benefit and i want to ask couple of questions here


You're welcome. ;)

 After going through what I went through I figured this could be something of help to others out here. There are still a few things to iron quirk wise. I did an update to this system last night, and since an occasional slight tear appeared with rendering through Xv and Mac Quartz Accelerated that was not there. It isn't really noticeable unless I am looking for it, which I am now..lol.

I am going to see what the libraries were that got updated and try a rollback. I finished this post, which I tested for a couple weeks, not one tear or hiccup before writing this post, and then I said to myself hey this system needs an update. Oh yeah, now I am trying to figure out which non X related library is the culprit.

> 
1. I have onboard ATI HD4200 graphics so does it have the HD acceleration you are talking about? 


The onboard HD 4200, according to what I have read online supports at least UVD 2 if not UVD 2.2. I believe the 785G is UVD 2.0, which is perfectly fine for using XvBA through the VA-API. It should be compatible with XvMC as well.

What I am getting at is, yes it definitely should.

2. I have tried the propriety drivers before and had issues with compiz and also video playback. Compiz used to crash every now and then(that maybe due to improper uninstallation of nvidia drivers)

It sounds like it could be an issue like you are talking about. I have read about the on board GPU's and they are usually pretty stable. On the note of Compiz, why? It is just eye candy that truly does not add any functionality, while consuming unnecessary resources. There might be a quirk or two but people have it running the fglrx driver with composting. Look at this thread and if you install the proprietary drivers follow my suggestion with this guide and install the newest drivers from AMD's website.

> 
3. Switched to opensource Drivers no issues at all except very poor 3D performance as its in experiment mode.

Now should i give this tut a try?

I don't think you will encounter hell on earth or anything if you were to try this guide. As long as you back up your xorg.conf before you change over to AMD's proprietary drivers, so you can just switch it out if you has issues, no harm no foul. I am sure you will notice a big jump in its performance using the VA-API to XvBA interface.

Honestly when I watched my first HD content in AVC MPEG4 after the tweaks on MPlayer with VA-API and it was absolutely flawless and visually pristine I was like a little kid on Christmas. It was a whole new experience with my HD4670 using hardware decode.

Give it a shot. I am sure a lot of other users with the HD4200 on board GPU would be interested in knowing how it performs. Reading about some of the things people encountered on prior drivers, I would use Catalyst Control Center 12 and it's Hotfix and deal with the watermark in the bottom right corner for a couple weeks because I have read that Catalyst Control Center is supposed to be coming out around the end of this month, beginning of next.

Good Luck

---

### Post by sports.car.guy on 2010-01-20
[U][B]An Update:

[/B][/U]I just performed some more testing with MPlayer using the VA-API on different MPEG4 streams, ones that are not supported, like the old hacked DiVX Windows codec. They played and well actually for the most part. A few it seems had some issue and choked the GPU. It is hit or miss. So sort of supported at the moment..lol.

One thing I did notice is the improvements going through the hardware are very visually quantifiable. I was beyond surprised. I was experimenting with Kdenlive because i needed to reinstall my MythTV server and wanted to get to watch what was on it for TV episodes. I needed to play catch up and decided to try out the hardware decoding and acceleration.

Kdenlive uses ffmpeg for encoding, as would MythTV, MPlayer normally, Xine and it's derivatives, along with VLC I believe for decoding. Encoding video no matter what I did, there would be vertical lines, kind of like visual artifacts in it. On playback I did notice with VLC they were not as visible then the others. Well, hardware XvBA through the VA-API puts VLC to shame on image quality. The lines are even less pronounced then VLC.

The only time they were really were at all noticeable was during very dark, almost pitch black scenes. I am really impressed with the quality.

On another note to do with the XvBA interface. For some reason I want to say that it exposes the Mac accelerated driver to the hardware more. Even though there is no ability in MythTV to add a de-interlace profile, the picture seemed to have, at least partially, de-interlacing done on it.

Since installing the VA-API and XvBA interface for it, I haven't really messed with the Mac accelerated driver really. I decided to last night a little. It appeared to be de-interlacing only when necessary. It was weird. Not quite fluid transitions from interlaced and de-interlaced. I figure it is because exposing the hardware capabilities, which is still under development. There is a type of de-interlacing that does just this, but I can't remember the name of it, another reason I am thinking it might be the case.

 I also tried messing with every conceivable setting and configuration I could think of to get my MythTV frontend to get along with OpenGL for at least rendering and well no luck. I spent a lot of time googling it as well.

Any help would be appreciated by me and I am sure others using this thread to get their AMD HD 4xxx and 5xxx cards working at optimal.

_Additional Note:_

I tried to get help in the MythTV-users IRC channel with our GL rendering problems. One flat out told me to get an nVidia who I guess is a registered member of the MythTV community, a regular, and no one else cared to actually help solve the issues. They were like well that is AMD for you. Now that is not right when no where on MythTV's site does it say hey we will only like you in our community if you got nVidia, otherwise you're on your own. 

If someone on the MythTV project could get back to me on this set of OpenGL drawing issues and see what we can do to fix it, the community at large who are now looking at AMD cards from when they were exclusively in Windows land, or it came on the mother board I am sure would appreciate it. Or they could be like me an idiot with brand loyalty..lol.

I like underdogs.. I rooted for the Patriots in the 86 Super Bowl if that gives you a clue..

Yeah we sure did bury the Bears..lmao

---

### Post by pwzhangz on 2010-01-21
Will this mess up my suspend capability (i.e., are you still able to suspend your machine)?  Thanks.

---

### Post by sports.car.guy on 2010-01-21
> **pwzhangz said:**
> Will this mess up my suspend capability (i.e., are you still able to suspend your machine)?  Thanks.

If it goes into suspend now using the fglrx driver then you should be safe.

In all honesty I haven't tried a full suspend on this machine. I have power management setup with it so that it spins down drives, monitor shuts completely down (It itself suspends), stuff like that. I don't have the whole machine go down. This frontend has a dual role in my master bedroom / office. It is my work machine at home, and also my bedroom home theater. I want and need it to be there at a moment's notice.

I have never had power management problems with this machine. I normally have the MythTV frontend up when I am not directly sitting at the machine working. The reason why I don't suspend is my remote won't activate it and bring up the machine, monitor, etc. Plus I like my hardware to last as long as possible. When you boot a system it is the most taxing on the hardware and most likely when it will fail. 

Because of my use of machine and wasting some electricity to keep it running, I can't tell you from a full suspend. Then it would be near impossible to bring my machine out with the current bug in 9.10 for bluetooth keyboards and mice. Karmic is unable to swap them from usb HID mode to bluetooth's equivalent, sorry it's name escapes me at 3:15am. 

I will go into my closet and look for a usb keyboard after some sleep and my day's obligations and see what happens.


As I said though there is no real reason why it shouldn't go in and out of suspend.

---

### Post by n3had on 2010-01-21
```
sudo **ln -s** libXvBAW.so.1.0 libXvBAW.so.1
```

is that the device section you are talking about in xorg.conf?

UPDATE: I am not getting the gdm black screen after boot and trying gdm start on tty1 gives 
Warning unable to find users no seat_id found

---

### Post by sports.car.guy on 2010-01-21
> **n3had said:**
> ```
sudo **ln -s** libXvBAW.so.1.0 libXvBAW.so.1
```is that the device section you are talking about in xorg.conf?

UPDATE: I am not getting the gdm black screen after boot and trying gdm start on tty1 gives 
Warning unable to find users no seat_id found

Nope the device section is:

```

Option  "TexturedVideoSync" "on" #HD4xxx & HD5xxx use textured video to render Xv. This helps to remove tearing.
Option   "Capabilities" "0x00000800" #This option also turns on vertical syncing as well. Both can and do work well together.
Option    "OpenGLOverlay" "off" #This is for workstations and certain commercial graphics applications for them. Nothing as Linux user that we do needs this so disabled.
```

What you are referring to is how to symlink the library needed for hardware decode.

When grub goes to load hit escape till it brings up a boot menu.. You then want to choose the second option from the top. It is your current kernel's "safe mode".

It will load up the kernel partially and provide you with a menu with several booting options. Choose to go to a root command prompt.

When there type in to be safe we will start with a fresh xorg.conf:

```
aticonfig --initial -f
```

When it is done type:
reboot

Let it boot normally and you should be all set with black screens. Remember doing a driver install this way, each time the kernel gets an update you have to repeat the driver install itself and reboot.

Now once in X go to /etc/xorg.conf and place the code in the code window up top. either log out or reboot to get it to take effect. I would reboot.

Now check for the binaries and also install the others and setup mplayer, etc.

I hope this helps you.

---

### Post by n3had on 2010-01-21
> **sports.car.guy said:**
> Nope the device section is:

```

Option  "TexturedVideoSync" "on" #HD4xxx & HD5xxx use textured video to render Xv. This helps to remove tearing.
Option   "Capabilities" "0x00000800" #This option also turns on vertical syncing as well. Both can and do work well together.
Option    "OpenGLOverlay" "off" #This is for workstations and certain commercial graphics applications for them. Nothing as Linux user that we do needs this so disabled.
```

What you are referring to is how to symlink the library needed for hardware decode.

When grub goes to load hit escape till it brings up a boot menu.. You then want to choose the second option from the top. It is your current kernel's "safe mode".

It will load up the kernel partially and provide you with a menu with several booting options. Choose to go to a root command prompt.

When there type in to be safe we will start with a fresh xorg.conf:

```
aticonfig --initial -f
```

When it is done type:
reboot

Let it boot normally and you should be all set with black screens. Remember doing a driver install this way, each time the kernel gets an update you have to repeat the driver install itself and reboot.

Now once in X go to /etc/xorg.conf and place the code in the code window up top. either log out or reboot to get it to take effect. I would reboot.

Now check for the binaries and also install the others and setup mplayer, etc.

I hope this helps you.
[http://yfrog.com/j121012010304j](http://yfrog.com/j121012010304j)

Startx gives me the above error

---

### Post by sports.car.guy on 2010-01-21
> **n3had said:**
> [http://yfrog.com/j121012010304j](http://yfrog.com/j121012010304j)

Startx gives me the above error


Okay right now I can see the problem. X is loading and it is looking in xorg.conf for AMD's fglrx driver and it is not finding them. I know why. You now have the entry in xorg.conf but no driver on the system.

When you ran the install script did you go through a bunch or menus / screens? If not you didn't install the driver on the system.

The install script for Catalyst Control Center needs to be made executable once you download it. AMD changes the permission to not executable.

You need to make it executable, then install the 9.12 non hotfix version first. This is assuming you 

chmod 740 ati-driver-installer-9-12-x86.x86_64.run

sudo sh ati-driver-installer-9-12-x86.x86_64.run

Reboot and go into "safe mode"

Then you need to run the aticonfig comand

sudo aticonfig --initial

or

sudo aticonfig --initial -f

Reboot

Install the hotfix now. Extract the archive and repeat the steps to make it executable if it isn't and run the installer for the hotfix. You then need to add if you haven't the code to xorg.conf in the driver section under fglrx. You now need to reboot.

Everything should be up and working on the note of X now.

Then move onto making sure the files are installed for the Xvba, the ones if not on your system you need to pull out of the .deb as I explained in the guide. Also install the AV-API and its XvBA interface.

That should be it for the graphics side of things.

It doesn't look like it is a hardware issue of anything like that, just a configuration one. No biggie.

---

### Post by n3had on 2010-01-21
i am really sorry i don't remember whether i've mentioned this i upgraded to lucid which got latest xorg and propriety drivers won't get properly installed.

[http://www.phoronix.com/forums/showthread.php?t=21294](http://www.phoronix.com/forums/showthread.php?t=21294)

I'll try [downgrading xserver related packages]("ubuntuforums.org/showpost.php?p=8541579&postcount=6") and then catch you later. Sorry i am being such a noob here

UPDATE: ok i am done downgrading all xserver related packages including xorg to karmic and now i get a different error Here's the Xorg log

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux tru3m0sl3m 2.6.32-11-generic #15-Ubuntu SMP Tue Jan 19 20:38:41 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=//vmlinuz-2.6.32-11-generic root=UUID=a169f6f3-7436-4077-af9c-656762f16a2b ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 22 16:58:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9710:1565:1704 ATI Technologies Inc RS880 [Radeon HD 4200] rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.68.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 1.4.99.906, module version = 8.68.2
	Module class: X.Org Video Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.68.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.682.2                  
(II) ATI Proprietary Linux Driver Build Date: Dec 14 2009 17:48:33
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9710) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is unsigned
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[32] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[33] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[34] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[35] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x12c56e0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "Capabilities" "0x00000800"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "TexturedVideoSync" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
drmDynamicMajor: failed to open /proc/ati/major
drmDynamicMajor: failed to open /proc/ati/major
(--) fglrx(0): Chipset: "ATI Radeon HD 4200" (Chipset = 0x9710)
(--) fglrx(0): (PciSubVendor = 0x1565, PciSubDevice = 0x1704)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(--) fglrx(0): I/O port at 0x0000d000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS880
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 393216 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x18000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000080, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 56ce  Serial#: 117673
(II) fglrx(0): Year: 2009  Week: 2
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 138.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
(II) fglrx(0): Monitor name: W2261
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff001e6dce56a9cb0100
(II) fglrx(0): 	0213010380301b78ea3d85a6564a9a24
(II) fglrx(0): 	125054a76b80b30081808140714f0101
(II) fglrx(0): 	0101010101011a3680a070381f403020
(II) fglrx(0): 	3500dd0c1100001a023a801871382d40
(II) fglrx(0): 	582c4500dd0c1100001e000000fd0038
(II) fglrx(0): 	4b1e530f000a202020202020000000fc
(II) fglrx(0): 	0057323236310a2020202020202000a4
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Output DFP2 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): EDID vendor "GSM", prod id 22222
(II) fglrx(0): Using EDID range info for horizontal sync
(II) fglrx(0): Using EDID range info for vertical refresh
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP2 using initial mode 1920x1080
(II) fglrx(0): Display dimensions: (480, 270) mm
(II) fglrx(0): DPI set to (101, 101)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): NoDRI = NO
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[17] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[18] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[19] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[20] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[21] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[22] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[23] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[27] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[28] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[29] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[30] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[31] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[32] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[33] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[34] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[35] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[36] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[37] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[38] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[39] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[40] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc5600000 FBMappedSize: 0x10000000
(II) fglrx(0): Reserved 0x05600000 bytes of sideport memory for power saving
(EE) fglrx(0): FB pci_device_map_range error!(EE) fglrx(0): Failed to map FB memory
(II) fglrx(0): === [atiddxScreenInit] === end

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(EE) fglrx(0): Failed to disable interrupts. Errorcode -9
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
 ddxSigGiveUp: Closing log
```

---

### Post by sports.car.guy on 2010-01-22
> **n3had said:**
> i am really sorry i don't remember whether i've mentioned this i upgraded to lucid which got latest xorg and propriety drivers won't get properly installed.

[http://www.phoronix.com/forums/showthread.php?t=21294](http://www.phoronix.com/forums/showthread.php?t=21294)

I'll try [downgrading xserver related packages]("http://ubuntuforums.org/showpost.php?p=8541579&postcount=6") and then catch you later. Sorry i am being such a noob here

UPDATE: ok i am done downgrading all xserver related packages including xorg to karmic and now i get a different error Here's the Xorg log

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux tru3m0sl3m 2.6.32-11-generic #15-Ubuntu SMP Tue Jan 19 20:38:41 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=//vmlinuz-2.6.32-11-generic root=UUID=a169f6f3-7436-4077-af9c-656762f16a2b ro quiet splash
Build Date: 14 November 2009  05:48:57PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 22 16:58:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "aticonfig Layout"
(**) |-->Screen "aticonfig-Screen[0]-0" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]-0"
(**) |   |-->Device "aticonfig-Device[0]-0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:5:0) 1002:9710:1565:1704 ATI Technologies Inc RS880 [Radeon HD 4200] rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, 0xfe900000/1048576, I/O @ 0x0000d000/256
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="FireGL - ATI Technologies Inc."
    compiled for 7.4.0, module version = 1.0.0
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.4.0, module version = 1.0.0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.68.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
    compiled for 1.4.99.906, module version = 8.68.2
    Module class: X.Org Video Driver
(II) ATI Proprietary Linux Driver Version Identifier:8.68.2
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.682.2                  
(II) ATI Proprietary Linux Driver Build Date: Dec 14 2009 17:48:33
(II) Primary Device is: PCI 01@00:05:0
(WW) Falling back to old probe method for fglrx
(II) Loading PCS database from /etc/ati/amdpcsdb
(--) Chipset Supported AMD Graphics Processor (0x9710) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:5:1) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is unsigned
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) fglrx(0): pEnt->device->identifier=0x12c56e0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): PCI bus 1 card 5 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "Capabilities" "0x00000800"
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "TexturedVideoSync" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
drmDynamicMajor: failed to open /proc/ati/major
drmDynamicMajor: failed to open /proc/ati/major
(--) fglrx(0): Chipset: "ATI Radeon HD 4200" (Chipset = 0x9710)
(--) fglrx(0): (PciSubVendor = 0x1565, PciSubDevice = 0x1704)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfeaf0000
(--) fglrx(0): I/O port at 0x0000d000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 10.94
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RS880
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
(II) fglrx(0): UMA/SP interleave mode is enabled in the BIOS
(--) fglrx(0): Video RAM: 393216 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Hasn't establisted DRM connection
(II) fglrx(0): [FB] MC range(MCFBBase = 0xc0000000, MCFBSize = 0x18000000)
(WW) fglrx(0): No DRM connection for driver fglrx.
(II) fglrx(0): RandR 1.2 support is enabled!
(II) fglrx(0): RandR 1.2 rotation support is enabled!
(==) fglrx(0): Center Mode is disabled 
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) fglrx(0): ***Display: ConnectedDisplayTypes=0x00000080, disabled=0x00000000
(II) fglrx(0): Connected Display1: DFP on secondary TMDS [tmds2i]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: GSM  Model: 56ce  Serial#: 117673
(II) fglrx(0): Year: 2009  Week: 2
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max Image Size [cm]: horiz.: 48  vert.: 27
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off
(II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.648 redY: 0.339   greenX: 0.292 greenY: 0.603
(II) fglrx(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) fglrx(0): Supported established timings:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 832x624@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): 1152x870@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported standard timings:
(II) fglrx(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) fglrx(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) fglrx(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 138.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
(II) fglrx(0): Supported detailed timing:
(II) fglrx(0): clock: 148.5 MHz   Image Size:  477 x 268 mm
(II) fglrx(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) fglrx(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 150 MHz
(II) fglrx(0): Monitor name: W2261
(II) fglrx(0): EDID (in hex):
(II) fglrx(0):     00ffffffffffff001e6dce56a9cb0100
(II) fglrx(0):     0213010380301b78ea3d85a6564a9a24
(II) fglrx(0):     125054a76b80b30081808140714f0101
(II) fglrx(0):     0101010101011a3680a070381f403020
(II) fglrx(0):     3500dd0c1100001a023a801871382d40
(II) fglrx(0):     582c4500dd0c1100001e000000fd0038
(II) fglrx(0):     4b1e530f000a202020202020000000fc
(II) fglrx(0):     0057323236310a2020202020202000a4
(II) fglrx(0): End of Display1 EDID data --------------------
(II) fglrx(0): Output DFP2 using monitor section aticonfig-Monitor[0]-0
(II) fglrx(0): Output CRT1 has no monitor section
(II) fglrx(0): EDID vendor "GSM", prod id 22222
(II) fglrx(0): Using EDID range info for horizontal sync
(II) fglrx(0): Using EDID range info for vertical refresh
(II) fglrx(0): Printing DDC gathered Modelines:
(II) fglrx(0): Modeline "1920x1080"x0.0  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz)
(II) fglrx(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) fglrx(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) fglrx(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) fglrx(0): Output DFP2 connected
(II) fglrx(0): Output CRT1 disconnected
(II) fglrx(0): Using exact sizes for initial modes
(II) fglrx(0): Output DFP2 using initial mode 1920x1080
(II) fglrx(0): Display dimensions: (480, 270) mm
(II) fglrx(0): DPI set to (101, 101)
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): QBS disabled
(==) fglrx(0):  PseudoColor visuals disabled
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.2.1
    ABI class: X.Org Video Driver, version 5.0
(==) fglrx(0): NoDRI = NO
(**) fglrx(0): Capabilities: 0x00000800
(**) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 1.4.x.y with x.y >= 99.906
(WW) fglrx(0): could not detect X server version (query_status=-1)
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc5600000 FBMappedSize: 0x10000000
(II) fglrx(0): Reserved 0x05600000 bytes of sideport memory for power saving
(EE) fglrx(0): FB pci_device_map_range error!(EE) fglrx(0): Failed to map FB memory
(II) fglrx(0): === [atiddxScreenInit] === end

Fatal server error:
AddScreen/ScreenInit failed for driver 0


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(EE) fglrx(0): Failed to disable interrupts. Errorcode -9
(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
 ddxSigGiveUp: Closing log
```


There were two errors from what I am reading. Since your downgrade it is having problems with detecting the X server version and was also unable to enable dri.

In your downgrade did all the packages for the X server get downgraded?

---

### Post by n3had on 2010-01-22
i downgraded the xserver* packages that were already installed and as you said fglrx wasn't loading itself to the kernel 2.6.32.11 (i am saying it incorrectly but i hope you get it)

After some googling i found at launchpad that lucid is not yet ready for the proprietary drivers so i guess i will wait till then and i reverted to the radeon driver. Thankyou once again for everything.

---

### Post by sports.car.guy on 2010-01-22
> **n3had said:**
> i downgraded the xserver* packages that were already installed and as you said fglrx wasn't loading itself to the kernel 2.6.32.11 (i am saying it incorrectly but i hope you get it)

After some googling i found at launchpad that lucid is not yet ready for the proprietary drivers so i guess i will wait till then and i reverted to the radeon driver. Thankyou once again for everything.


Alright man, not a problem, I understand. I was hoping you would follow it till the end so there could be an example of it running on the integrated HD4200. No biggie though.

Hopefully they will support the proprietary drivers in the version of X you upgraded to and are using soon.

---

### Post by bbruenfl on 2010-01-25
Wow, hope for video without tearing on amd hardware.  You just made my week.

Unfortunately, I ran into a little snag while compiling mplayer-vaapi.

The build-dep command says I need nvidia-185-libvdpau-dev that depends on nvidia-185-libvdpau.  Ok, fair enough.  I try to install those and apt tells me I need to remove most of mythtv and the vdpau packages I just installed.

I'm thinking I missed something but I can't find it.  So, I did what it suggested and built the thing using nvidia's libvdpau.  As one might expect, the vaapi output doesn't work.  With the nvidia libs installed, my system freezes and with the vdpau packages from gbeauchesne it returns...
```

MPlayer interrupted by signal 11 in module: vo_check_events

```

In the interests of full disclosure I should also mention I installed the vdpau packages in a different order than suggested because dpkg wouldn't install the first two (libva-dev and libva1-dbg) without libva1.
 
Any thoughts on where I might have gone astray?

---

### Post by bbruenfl on 2010-01-26
A quick update...
Over breakfast, it occurred to me to allow apt to install the nvidia lib, do the build-dep then remove the nvidia, reinstall mythtv and the vdpau drivers, then run the config script.  Woo-hoo, one cup of coffee later (I don't smoke anymore) we have a working mplayer executable.

I had a look at two streams.  An episode of Dollhouse capped from a digital broadcast (720p, mpeg2) and the 720p copy of The Lionshare (x264).  There appears to be a problem with the colorspace in the Dollhouse (everyone is blue) and the Lionshare crashes with the same errors as mentioned above.

I then moved onto mythtv using the settings given for TV Playback.  Checking the logs it looks like mythvideo can't figure out how to use XvMC, vdpau, etc so it reverts to ffmpeg and xv-blit.  Below is the relevant portion of the log with important,general,player chosen for output.

```

2010-01-26 08:04:18.243 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-01-26 08:04:18.243 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): OpenFile(/var/lib/mythtv/recordings/1351_20100121210000.mpg, 12)
2010-01-26 08:04:18.244 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): CalcReadAheadThresh(0 KB)
             -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-01-26 08:04:18.295 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-01-26 08:04:18.295 TV: Elapsed time since TV constructor was called: 130 ms
2010-01-26 08:04:18.454 AFD: Stream #0, has id 0x1e0 codec id MPEG2VIDEO, type Video, bitrate 19000000 at 0x56da2a0
2010-01-26 08:04:18.455 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.455 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.456 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.456 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.457 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.457 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.458 VideoOutputXv: XvMC version: 1.1
2010-01-26 08:04:18.458 XvMCSurfaceTypes::find(w 1280, h 720, chroma 1, vld 1, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 131, 134 <=p, port, surfNum)
2010-01-26 08:04:18.458 Trying XvMC port 131
2010-01-26 08:04:18.464 Trying XvMC port 132
2010-01-26 08:04:18.464 Trying XvMC port 133
2010-01-26 08:04:18.464 Trying XvMC port 134
2010-01-26 08:04:18.464 XvMCSurfaceTypes::find(w 1280, h 720, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 131, 134 <=p, port, surfNum)
2010-01-26 08:04:18.464 Trying XvMC port 131
2010-01-26 08:04:18.464 Trying XvMC port 132
2010-01-26 08:04:18.464 Trying XvMC port 133
2010-01-26 08:04:18.465 Trying XvMC port 134
2010-01-26 08:04:18.465 Using 2 CPUs for decoding
2010-01-26 08:04:18.465 AFD: InitVideoCodec() 0x573c280 id(MPEG2VIDEO) type (Video).
2010-01-26 08:04:18.465 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2010-01-26 08:04:18.465 AFD: Using ffmpeg for video decoding
2010-01-26 08:04:18.465 AFD: Looking for decoder for MPEG2VIDEO
2010-01-26 08:04:18.465 AFD: Opened codec 0x573c280, id(MPEG2VIDEO) type(Video)
2010-01-26 08:04:18.465 AFD: Stream #1, has id 0x80 codec id AC3, type Audio, bitrate 448000 at 0x5739b30
2010-01-26 08:04:18.465 AFD: codec AC3 has 6 channels
2010-01-26 08:04:18.465 AFD: Looking for decoder for AC3
2010-01-26 08:04:18.465 AFD: Opened codec 0x56d9800, id(AC3) type(Audio)
2010-01-26 08:04:18.466 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): CalcReadAheadThresh(0 KB)
             -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-01-26 08:04:18.472 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.472 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.506 mixer unable to find control Master 1
2010-01-26 08:04:18.510 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.510 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.546 mixer unable to find control Master 1
2010-01-26 08:04:18.546 Dec: Trying to select track (w/lang)
2010-01-26 08:04:18.546 Dec: Selecting first track
2010-01-26 08:04:18.546 Dec: Selected track #1 in the Unknown language(0)
2010-01-26 08:04:18.546 Dec: Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2010-01-26 08:04:18.566 Position map filled from DB to: 155086
2010-01-26 08:04:18.566 Dec: SyncPositionMap prerecorded, from DB: 9970 entries
2010-01-26 08:04:18.566 Dec: SyncPositionMap, new totframes: 155086, new length: 2587, posMap size: 9970
2010-01-26 08:04:18.566 AFD: Position map found
2010-01-26 08:04:18.566 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1351_20100121210000.mpg". novideo(0)
2010-01-26 08:04:18.568 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.568 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.607 mixer unable to find control Master 1
2010-01-26 08:04:18.616 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2010-01-26 08:04:18.616 VideoOutput: Allowed renderers (filt: ffmpeg): xlib,xshm,xv-blit,opengl,vdpau
2010-01-26 08:04:18.624 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.624 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.624 VideoOutput: Trying video renderer: 'vdpau'
2010-01-26 08:04:18.629 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.629 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.629 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.629 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.641 VideoOutWindow::SetPIPState. pip_state: 0]
2010-01-26 08:04:18.641 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.641 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.641 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.641 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.641 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.641 VDP: SetVideoRenderer(vdpau)
2010-01-26 08:04:18.641 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.641 VDP: New preferences: rend(vdpau) osd(vdpau) deint(none,none) filt()
2010-01-26 08:04:18.642 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2010-01-26 08:04:18.642 VideoOutput: Actual display dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.642 VideoOutput: Estimated window dimensions: 708x398 mm  Aspect: 1.77889
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2010-01-26 08:04:18.642 VDPAU Error: Error at mythrender_vdpau.cpp:1325 (#1, Unknown)
2010-01-26 08:04:18.642 VDPAU Error: Failed to create VDPAU device.
2010-01-26 08:04:18.642 VDPAU Error: No VDPAU device
2010-01-26 08:04:18.642 Failed to create VDPAU render device.
2010-01-26 08:04:18.643 VidOutVDPAU Error: Failed to initialise VDPAU
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames(1)
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1): 
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames():  -- done()
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1):  -- done
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames() 3:  -- done()
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames(1)
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1): 
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames():  -- done()
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1):  -- done
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames() 3:  -- done()
2010-01-26 08:04:18.643 VideoOutput: Trying video renderer: 'xv-blit'
2010-01-26 08:04:18.670 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.670 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.670 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.670 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.671 VideoOutputXv: ctor
2010-01-26 08:04:18.671 VideoOutWindow::SetPIPState. pip_state: 0]
2010-01-26 08:04:18.672 VideoOutputXv: Creating gc
2010-01-26 08:04:18.672 VideoOutputXv: XJ_screen_num: '0'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_curwin:     '44040198'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_win:        '44040198'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_root:       '180'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_gc:         '0x5dfbea0'
2010-01-26 08:04:18.672 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.672 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.672 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.672 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.672 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.672 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2010-01-26 08:04:18.672 VideoOutput: Actual display dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.672 VideoOutput: Estimated window dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.672 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,xlib
2010-01-26 08:04:18.672 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2010-01-26 08:04:18.672 VDP: SetVideoRenderer(xv-blit)
2010-01-26 08:04:18.673 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.673 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.692 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2010-01-26 08:04:18.692 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.692 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-26 08:04:18.697 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-26 08:04:18.697 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2010-01-26 08:04:18.697 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.697 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-26 08:04:18.697 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2010-01-26 08:04:18.697 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.697 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-26 08:04:18.697 VideoOutputXv: Here...
2010-01-26 08:04:18.697 VideoOutputXv: Grabbed xv port 131
2010-01-26 08:04:18.697 VideoOutputXv: XVideo surface found on port 131
2010-01-26 08:04:18.697 VideoOutputXv: XV_SET_DEFAULTS is supported on this port
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #0 is 'YV12'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #1 is 'I420'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #2 is 'YUY2'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #3 is 'UYVY'
2010-01-26 08:04:18.698 VideoOutputXv: Using XVideo Format 'YV12'
2010-01-26 08:04:18.698 VideoOutputXv: CreateShmImages(32): video_dim: 1280x720
2010-01-26 08:04:18.741 VDP: SetVideoRenderer(xv-blit)
2010-01-26 08:04:18.741 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2010-01-26 08:04:18.742 VideoOutputXv: Chromakeying not possible with this XVideo port.
2010-01-26 08:04:18.742 VideoOutputXv Error: Disabling ChromaKeyOSD as colorkeying will not work.
2010-01-26 08:04:18.742 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2010-01-26 08:04:18.742 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.764 Over/underscan. V: 0, H: 0
2010-01-26 08:04:18.765 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2010-01-26 08:04:18.765 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.765 VDP: LoadBestPreferences(1280x720, 59.9401)
2010-01-26 08:04:18.776 NVP(0): LoadFilters(''..) -> 0x0
2010-01-26 08:04:18.777 OSD Theme Dimensions W: 1280 H: 720
2010-01-26 08:04:18.963 NVP(0): ClearAfterSeek(1)
2010-01-26 08:04:18.963 VideoOutputXv: ClearAfterSeek()
2010-01-26 08:04:18.963 VideoOutputXv: DiscardFrames(0)
2010-01-26 08:04:18.963 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:18.963 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2010-01-26 08:04:18.964 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:18.965 playCtx: StartDecoderThread(): took 357 ms to start player.
2010-01-26 08:04:18.965 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2010-01-26 08:04:18.965 SendReceiveStringList(MESSAGE,COMMFLAG_REQUEST 1351 2010-01-21T21:00:00) called from UI thread
2010-01-26 08:04:18.966 TV: Changing from None to Watching WatchingPreRecorded
2010-01-26 08:04:18.967 Using realtime priority.
2010-01-26 08:04:18.968 TV: HandleStateChange(0) -- end
2010-01-26 08:04:18.968 VDP: GetFilteredDeint() : xv-blit -> 'none'
2010-01-26 08:04:18.969 Couldn't load deinterlace filter none
2010-01-26 08:04:18.969 Using deinterlace method 
2010-01-26 08:04:18.970 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2010-01-26 08:04:18.970 Using audio as timebase
2010-01-26 08:04:18.970 Video timing method: RTC
2010-01-26 08:04:18.970 Refresh rate: 16666, frame interval: 16683
2010-01-26 08:04:18.970 NVP(0): Waiting for prebuffer..  0 LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:18.975 Detect Letterbox: YV12 frame format detected
2010-01-26 08:04:18.975 Detect Letterbox: The source is already in widescreen (aspect: 1.77778)
2010-01-26 08:04:18.996 ScreenSaverX11Private: ResetTimer -- begin
2010-01-26 08:04:18.996 ScreenSaverX11Private: StopTimer
2010-01-26 08:04:18.996 ScreenSaverX11Private: StartTimer
2010-01-26 08:04:18.996 ScreenSaverX11Private: ResetTimer -- end
2010-01-26 08:04:19.053 VideoOutputXv: UpdatePauseFrame() uLAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.055 AFD: DoFastForward(1479 (1), do discard frames)
2010-01-26 08:04:19.055 Dec: DoFastForward(1479 (1), do discard frames)
2010-01-26 08:04:19.056 Dec: FindPosition(1479, search not adjusted) --> 
            [95:1471(43124750),96:1486(43544590)]
2010-01-26 08:04:19.056 AFD: SeekReset(1471, 8, do flush, do discard)
2010-01-26 08:04:19.056 AFD: SeekReset() flushing
2010-01-26 08:04:19.056 VideoOutputXv: DiscardFrames(1)
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(1): UAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2010-01-26 08:04:19.056 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:19.119 NVP(0): ClearAfterSeek(0)
2010-01-26 08:04:19.134 NVP(0): Waiting for prebuffer..  1 AAAAAAaAALaAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.187 NVP(0): progressive frame seen after 2 interlaced  frames
2010-01-26 08:04:19.207 Set video sync frame interval to 16683
2010-01-26 08:04:19.207 Disabled deinterlacing
2010-01-26 08:04:19.291 NVP(0): Video is 3.68261 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.323 NVP(0): Video is 4.11059 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.356 NVP(0): Video is 4.19181 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.390 NVP(0): Video is 4.01301 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.424 NVP(0): Video is 3.62411 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.458 NVP(0): Video is 3.07768 frames ahead of audio,
            doubling video frame interval to slow down.
'video_output' mean = '18037.09', std. dev. = '5527.35', fps = '55.44'
2010-01-26 08:04:21.230 Dec: Selected track #1 in the Unknown language(0)
2010-01-26 08:04:22.620 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-01-26 08:04:22.620 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-01-26 08:04:22.663 TV: HandleStateChange(0) -- begin
2010-01-26 08:04:22.663 TV: Attempting to change from Watching WatchingPreRecorded to None
2010-01-26 08:04:22.663 TV: StopStuff() for player ctx 0 -- begin
2010-01-26 08:04:22.663 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-01-26 08:04:22.663 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-01-26 08:04:22.663 TV: StopStuff(): stopping ring buffer
'video_output' mean = '16718.91', std. dev. = '3301.89', fps = '59.81'
2010-01-26 08:04:22.669 NVP(0): Exited decoder loop.
2010-01-26 08:04:22.677 TV: StopStuff(): stopping player
2010-01-26 08:04:22.677 TV: StopStuff() -- end
2010-01-26 08:04:22.677 TV: Changing from Watching WatchingPreRecorded to None

```It looks like it is trying to call an nvidia lib at 08:04:18.642 that isn't installed.  

Could it be because I'm using the trunk build (r23270)?  I'm familiar with the dev's attitude toward ATI hardware.  Perhaps they are leaving ATI support issues till last.  Anyway, I hope someone can shed some light on this for me.  Thanks.

---

### Post by sports.car.guy on 2010-01-27
> **bbruenfl said:**
> A quick update...
Over breakfast, it occurred to me to allow apt to install the nvidia lib, do the build-dep then remove the nvidia, reinstall mythtv and the vdpau drivers, then run the config script.  Woo-hoo, one cup of coffee later (I don't smoke anymore) we have a working mplayer executable.

I had a look at two streams.  An episode of Dollhouse capped from a digital broadcast (720p, mpeg2) and the 720p copy of The Lionshare (x264).  There appears to be a problem with the colorspace in the Dollhouse (everyone is blue) and the Lionshare crashes with the same errors as mentioned above.

I then moved onto mythtv using the settings given for TV Playback.  Checking the logs it looks like mythvideo can't figure out how to use XvMC, vdpau, etc so it reverts to ffmpeg and xv-blit.  Below is the relevant portion of the log with important,general,player chosen for output.

```

2010-01-26 08:04:18.243 TV: Attempting to change from None to Watching WatchingPreRecorded
2010-01-26 08:04:18.243 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): OpenFile(/var/lib/mythtv/recordings/1351_20100121210000.mpg, 12)
2010-01-26 08:04:18.244 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): CalcReadAheadThresh(0 KB)
             -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-01-26 08:04:18.295 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- begin
2010-01-26 08:04:18.295 TV: Elapsed time since TV constructor was called: 130 ms
2010-01-26 08:04:18.454 AFD: Stream #0, has id 0x1e0 codec id MPEG2VIDEO, type Video, bitrate 19000000 at 0x56da2a0
2010-01-26 08:04:18.455 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.455 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.455 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.456 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.456 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.456 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.457 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.457 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.457 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.458 VideoOutputXv: XvMC version: 1.1
2010-01-26 08:04:18.458 XvMCSurfaceTypes::find(w 1280, h 720, chroma 1, vld 1, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 131, 134 <=p, port, surfNum)
2010-01-26 08:04:18.458 Trying XvMC port 131
2010-01-26 08:04:18.464 Trying XvMC port 132
2010-01-26 08:04:18.464 Trying XvMC port 133
2010-01-26 08:04:18.464 Trying XvMC port 134
2010-01-26 08:04:18.464 XvMCSurfaceTypes::find(w 1280, h 720, chroma 1, vld 0, idct 0, mpeg2, sub-width 0, sub-height 0, disp, p<= 131, 134 <=p, port, surfNum)
2010-01-26 08:04:18.464 Trying XvMC port 131
2010-01-26 08:04:18.464 Trying XvMC port 132
2010-01-26 08:04:18.464 Trying XvMC port 133
2010-01-26 08:04:18.465 Trying XvMC port 134
2010-01-26 08:04:18.465 Using 2 CPUs for decoding
2010-01-26 08:04:18.465 AFD: InitVideoCodec() 0x573c280 id(MPEG2VIDEO) type (Video).
2010-01-26 08:04:18.465 detectInterlace(Detect Scan, Interlaced Scan, 59.9401, 720) ->Progressive Scan
2010-01-26 08:04:18.465 AFD: Using ffmpeg for video decoding
2010-01-26 08:04:18.465 AFD: Looking for decoder for MPEG2VIDEO
2010-01-26 08:04:18.465 AFD: Opened codec 0x573c280, id(MPEG2VIDEO) type(Video)
2010-01-26 08:04:18.465 AFD: Stream #1, has id 0x80 codec id AC3, type Audio, bitrate 448000 at 0x5739b30
2010-01-26 08:04:18.465 AFD: codec AC3 has 6 channels
2010-01-26 08:04:18.465 AFD: Looking for decoder for AC3
2010-01-26 08:04:18.465 AFD: Opened codec 0x56d9800, id(AC3) type(Audio)
2010-01-26 08:04:18.466 RingBuf(/var/lib/mythtv/recordings/1351_20100121210000.mpg): CalcReadAheadThresh(0 KB)
             -> threshhold(64 KB) min read(0 KB) blk size(32 KB)
2010-01-26 08:04:18.472 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.472 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.506 mixer unable to find control Master 1
2010-01-26 08:04:18.510 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.510 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.546 mixer unable to find control Master 1
2010-01-26 08:04:18.546 Dec: Trying to select track (w/lang)
2010-01-26 08:04:18.546 Dec: Selecting first track
2010-01-26 08:04:18.546 Dec: Selected track #1 in the Unknown language(0)
2010-01-26 08:04:18.546 Dec: Resyncing position map. posmapStarted = 0 livetv(0) watchingRec(0)
2010-01-26 08:04:18.566 Position map filled from DB to: 155086
2010-01-26 08:04:18.566 Dec: SyncPositionMap prerecorded, from DB: 9970 entries
2010-01-26 08:04:18.566 Dec: SyncPositionMap, new totframes: 155086, new length: 2587, posMap size: 9970
2010-01-26 08:04:18.566 AFD: Position map found
2010-01-26 08:04:18.566 AFD: Successfully opened decoder for file: "/var/lib/mythtv/recordings/1351_20100121210000.mpg". novideo(0)
2010-01-26 08:04:18.568 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-01-26 08:04:18.568 Opening ALSA audio device 'iec958:{ AES0 0x02 }'.
2010-01-26 08:04:18.607 mixer unable to find control Master 1
2010-01-26 08:04:18.616 VideoOutput: Allowed renderers: xv-blit,xshm,xlib,opengl,vdpau
2010-01-26 08:04:18.616 VideoOutput: Allowed renderers (filt: ffmpeg): xlib,xshm,xv-blit,opengl,vdpau
2010-01-26 08:04:18.624 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.624 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.624 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.624 VideoOutput: Trying video renderer: 'vdpau'
2010-01-26 08:04:18.629 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.629 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.629 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.629 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.641 VideoOutWindow::SetPIPState. pip_state: 0]
2010-01-26 08:04:18.641 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.641 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.641 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.641 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.641 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.641 VDP: SetVideoRenderer(vdpau)
2010-01-26 08:04:18.641 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.641 VDP: New preferences: rend(vdpau) osd(vdpau) deint(none,none) filt()
2010-01-26 08:04:18.642 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2010-01-26 08:04:18.642 VideoOutput: Actual display dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.642 VideoOutput: Estimated window dimensions: 708x398 mm  Aspect: 1.77889
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
2010-01-26 08:04:18.642 VDPAU Error: Error at mythrender_vdpau.cpp:1325 (#1, Unknown)
2010-01-26 08:04:18.642 VDPAU Error: Failed to create VDPAU device.
2010-01-26 08:04:18.642 VDPAU Error: No VDPAU device
2010-01-26 08:04:18.642 Failed to create VDPAU render device.
2010-01-26 08:04:18.643 VidOutVDPAU Error: Failed to initialise VDPAU
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames(1)
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1): 
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames():  -- done()
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1):  -- done
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames() 3:  -- done()
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames(1)
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1): 
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames():  -- done()
2010-01-26 08:04:18.643 VideoBuffers::DiscardFrames(1):  -- done
2010-01-26 08:04:18.643 VidOutVDPAU: DiscardFrames() 3:  -- done()
2010-01-26 08:04:18.643 VideoOutput: Trying video renderer: 'xv-blit'
2010-01-26 08:04:18.670 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.670 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.670 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.670 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.671 VideoOutputXv: ctor
2010-01-26 08:04:18.671 VideoOutWindow::SetPIPState. pip_state: 0]
2010-01-26 08:04:18.672 VideoOutputXv: Creating gc
2010-01-26 08:04:18.672 VideoOutputXv: XJ_screen_num: '0'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_curwin:     '44040198'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_win:        '44040198'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_root:       '180'
2010-01-26 08:04:18.672 VideoOutputXv: XJ_gc:         '0x5dfbea0'
2010-01-26 08:04:18.672 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.672 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.672 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.672 Display Rect  left: 0, top: 135, width: 1920, height: 810, aspect: 1.33333
2010-01-26 08:04:18.672 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.672 VideoOutput: Pixel dimensions: Screen 1920x1080, window 1920x1080
2010-01-26 08:04:18.672 VideoOutput: Actual display dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.672 VideoOutput: Estimated window dimensions: 708x398 mm  Aspect: 1.77889
2010-01-26 08:04:18.672 VideoOutputXv: InitSetupBuffers() render: xvmc-blit, allowed: xv-blit,xshm,xlib
2010-01-26 08:04:18.672 VideoOutputXv: Desired video renderer 'xvmc-blit' not available.
            codec 'MPEG2' makes 'xv-blit,xshm,xlib,' available, using 'xv-blit' instead.
2010-01-26 08:04:18.672 VDP: SetVideoRenderer(xv-blit)
2010-01-26 08:04:18.673 VDP: Old preferences: rend(xvmc-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.673 VDP: New preferences: rend(xv-blit) osd(chromakey) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: Accepting: cmp(>= 1920 1080) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: Accepting: cmp(>= 0 0) dec(xvmc-vld) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-26 08:04:18.688 VDP: LoadBestPreferences(1280x720, 60)
2010-01-26 08:04:18.692 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask XvImageMask  18
2010-01-26 08:04:18.692 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.692 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-26 08:04:18.697 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-26 08:04:18.697 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask XvImageMask  8
2010-01-26 08:04:18.697 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.697 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-26 08:04:18.697 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask XvImageMask  10
2010-01-26 08:04:18.697 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-26 08:04:18.697 VideoOutputXv: Has XVideo flags...
2010-01-26 08:04:18.697 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-26 08:04:18.697 VideoOutputXv: Here...
2010-01-26 08:04:18.697 VideoOutputXv: Grabbed xv port 131
2010-01-26 08:04:18.697 VideoOutputXv: XVideo surface found on port 131
2010-01-26 08:04:18.697 VideoOutputXv: XV_SET_DEFAULTS is supported on this port
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #0 is 'YV12'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #1 is 'I420'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #2 is 'YUY2'
2010-01-26 08:04:18.697 VideoOutputXv: XVideo Format #3 is 'UYVY'
2010-01-26 08:04:18.698 VideoOutputXv: Using XVideo Format 'YV12'
2010-01-26 08:04:18.698 VideoOutputXv: CreateShmImages(32): video_dim: 1280x720
2010-01-26 08:04:18.741 VDP: SetVideoRenderer(xv-blit)
2010-01-26 08:04:18.741 VDP: SetVideoRender(xv-blit) == GetVideoRenderer()
2010-01-26 08:04:18.742 VideoOutputXv: Chromakeying not possible with this XVideo port.
2010-01-26 08:04:18.742 VideoOutputXv Error: Disabling ChromaKeyOSD as colorkeying will not work.
2010-01-26 08:04:18.742 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2010-01-26 08:04:18.742 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.764 Over/underscan. V: 0, H: 0
2010-01-26 08:04:18.765 Display Rect  left: 0, top: 0, width: 1920, height: 1080, aspect: 1.77778
2010-01-26 08:04:18.765 Video Rect    left: 0, top: 0, width: 1280, height: 720, aspect: 1.77778
2010-01-26 08:04:18.765 VDP: LoadBestPreferences(1280x720, 59.9401)
2010-01-26 08:04:18.776 NVP(0): LoadFilters(''..) -> 0x0
2010-01-26 08:04:18.777 OSD Theme Dimensions W: 1280 H: 720
2010-01-26 08:04:18.963 NVP(0): ClearAfterSeek(1)
2010-01-26 08:04:18.963 VideoOutputXv: ClearAfterSeek()
2010-01-26 08:04:18.963 VideoOutputXv: DiscardFrames(0)
2010-01-26 08:04:18.963 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:18.963 VideoBuffers::DiscardFrames(0): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2010-01-26 08:04:18.964 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:18.965 playCtx: StartDecoderThread(): took 357 ms to start player.
2010-01-26 08:04:18.965 TV: StartPlayer(0, Watching WatchingPreRecorded, main) -- end ok
2010-01-26 08:04:18.965 SendReceiveStringList(MESSAGE,COMMFLAG_REQUEST 1351 2010-01-21T21:00:00) called from UI thread
2010-01-26 08:04:18.966 TV: Changing from None to Watching WatchingPreRecorded
2010-01-26 08:04:18.967 Using realtime priority.
2010-01-26 08:04:18.968 TV: HandleStateChange(0) -- end
2010-01-26 08:04:18.968 VDP: GetFilteredDeint() : xv-blit -> 'none'
2010-01-26 08:04:18.969 Couldn't load deinterlace filter none
2010-01-26 08:04:18.969 Using deinterlace method 
2010-01-26 08:04:18.970 DRMVideoSync: Could not open device /dev/dri/card0, No such file or directory
2010-01-26 08:04:18.970 Using audio as timebase
2010-01-26 08:04:18.970 Video timing method: RTC
2010-01-26 08:04:18.970 Refresh rate: 16666, frame interval: 16683
2010-01-26 08:04:18.970 NVP(0): Waiting for prebuffer..  0 LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:18.975 Detect Letterbox: YV12 frame format detected
2010-01-26 08:04:18.975 Detect Letterbox: The source is already in widescreen (aspect: 1.77778)
2010-01-26 08:04:18.996 ScreenSaverX11Private: ResetTimer -- begin
2010-01-26 08:04:18.996 ScreenSaverX11Private: StopTimer
2010-01-26 08:04:18.996 ScreenSaverX11Private: StartTimer
2010-01-26 08:04:18.996 ScreenSaverX11Private: ResetTimer -- end
2010-01-26 08:04:19.053 VideoOutputXv: UpdatePauseFrame() uLAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.055 AFD: DoFastForward(1479 (1), do discard frames)
2010-01-26 08:04:19.055 Dec: DoFastForward(1479 (1), do discard frames)
2010-01-26 08:04:19.056 Dec: FindPosition(1479, search not adjusted) --> 
            [95:1471(43124750),96:1486(43544590)]
2010-01-26 08:04:19.056 AFD: SeekReset(1471, 8, do flush, do discard)
2010-01-26 08:04:19.056 AFD: SeekReset() flushing
2010-01-26 08:04:19.056 VideoOutputXv: DiscardFrames(1)
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(1): UAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:19.056 VideoBuffers::DiscardFrames(1): AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done
2010-01-26 08:04:19.056 VideoOutputXv: DiscardFrames() 3: AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA -- done()
2010-01-26 08:04:19.119 NVP(0): ClearAfterSeek(0)
2010-01-26 08:04:19.134 NVP(0): Waiting for prebuffer..  1 AAAAAAaAALaAAAAAAAAAAAAAAAAAAAA
2010-01-26 08:04:19.187 NVP(0): progressive frame seen after 2 interlaced  frames
2010-01-26 08:04:19.207 Set video sync frame interval to 16683
2010-01-26 08:04:19.207 Disabled deinterlacing
2010-01-26 08:04:19.291 NVP(0): Video is 3.68261 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.323 NVP(0): Video is 4.11059 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.356 NVP(0): Video is 4.19181 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.390 NVP(0): Video is 4.01301 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.424 NVP(0): Video is 3.62411 frames ahead of audio,
            doubling video frame interval to slow down.
2010-01-26 08:04:19.458 NVP(0): Video is 3.07768 frames ahead of audio,
            doubling video frame interval to slow down.
'video_output' mean = '18037.09', std. dev. = '5527.35', fps = '55.44'
2010-01-26 08:04:21.230 Dec: Selected track #1 in the Unknown language(0)
2010-01-26 08:04:22.620 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-01-26 08:04:22.620 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-01-26 08:04:22.663 TV: HandleStateChange(0) -- begin
2010-01-26 08:04:22.663 TV: Attempting to change from Watching WatchingPreRecorded to None
2010-01-26 08:04:22.663 TV: StopStuff() for player ctx 0 -- begin
2010-01-26 08:04:22.663 TV: SetActive(0,w/o OSD) 0 -> 0 -- begin
2010-01-26 08:04:22.663 TV: SetActive(0,w/o OSD) 0 -> 0 -- end
2010-01-26 08:04:22.663 TV: StopStuff(): stopping ring buffer
'video_output' mean = '16718.91', std. dev. = '3301.89', fps = '59.81'
2010-01-26 08:04:22.669 NVP(0): Exited decoder loop.
2010-01-26 08:04:22.677 TV: StopStuff(): stopping player
2010-01-26 08:04:22.677 TV: StopStuff() -- end
2010-01-26 08:04:22.677 TV: Changing from Watching WatchingPreRecorded to None

```It looks like it is trying to call an nvidia lib at 08:04:18.642 that isn't installed.  

Could it be because I'm using the trunk build (r23270)?  I'm familiar with the dev's attitude toward ATI hardware.  Perhaps they are leaving ATI support issues till last.  Anyway, I hope someone can shed some light on this for me.  Thanks.


Hi, sorry I haven't been out. I haven't had a chance to look all this over. I will and definitely get back out here shortly. I have been totally revamping my MythTV setup, along with other computer things around here such as getting everything set for a Xeon server to act as file storage, through a VM, a Magic Jack server for phone and fax, and a print server as well. It has a TB of SCSI drives on a raid controller and almost 3 GB of ram with what I am adding to it. Getting everything square with that and my MythTV revamp has taken a bit of my focus and I am sorry about it.

Comcast in my area is finally making their digital transition and I needed to address this where it would cut me down to only the HD cable box on a firewire cable. I had to break down and get a tuner with ATSC/QAM capabilities and cheap. That main one being cheap, no more then $80 was my cap, and I was not wanting to spend that much. I already have an ATSC/QAM card, it just so happens it is the only model of Geniatech/Mygica that has absolutely no support in V4L.

Anyways, I purchased a Hauppauge  USB WinTV-HVR 950Q. It was on sale at Best Buy for the same as New Egg, with no shipping, and local. It cost me only a couple dollars more, that's it. So I went to set it up and was not liking a couple of things MythTV decided to do on it's own.

Because I had already setup the backend, it wanted to assign XMLID's to every channel, along with icons, etc. It was a mess and for some reason it would overwrite the XMLID's I corrected. It turned out where it was close to a fresh setup to just blow it out and start over again. It was a pain, but I bet less of one then the XMLID issues getting fixed.

I also then wiped this system while I was at it too because with Evolution running it kept locking up if I let it set unattended for any time period. I paused TV one day when I went to hit the shower, came back to find the system totally locked up GUI wise and unresponsive except for the ability to get to a terminal thank god. It was after installing it that my system became unstable too. I had for almost a month used this system setup as described here, not one hiccup at all, then evil Evolution tempted me away from Kontact, never again.

Now onto what I got to see so far reading:

[I]From glancing at this post and the last one, I never encountered that issue. I believe I disabled the vdapu support of MPlayer on the compile passing a flag / switch.

On the note of XvMC it is enabled with only a limited number of driver versions at this point. The two versions I have listed here I know work with those two. I have tested them both. Are you using one of these two drivers? The Xvmc will work on 9.12 without the hotfix applied for reference. My testing included Xine's XvMC and VLC's as well, besides MythTV. I am stumped on why you are having it not work for you.

What version of MythTV are you using again? You said it is a trunk version right? I think that could be an issue. I am using the stable release branch with daily builds from the Mythbuntu development team and so far it actually improved my performance of MythTv 0.22. Just on the note of tuning hardware I was having major issues with having to switch to the 950Q like 3 or 4 times before it would actually get initialized and now it seems to fire up first call to it. It also improved my video performance as well at least to my eyes. It seemed cleaner and smoother.

One thing I was reading is the development trunk version is not optimized at all. I am wondering if that could be part of the issue. It seems that it is looking for any fall back render it can get it's hands on and just is not liking something. I never encountered colorspace issues with either MythTV or Mplayer, that one I am stumped on too. Have you tried to manually correct the colors?

The thing with Mplayer is currently there is only support for MPEG4 variants, in relation to fgrlx and hardware acceleration. Was it in MPlayer you tried playing the MPEG2? That could be why it choked.

I am confused there.

Get back to me on those things and lets see what we can do from here.
[/I]

---

### Post by sports.car.guy on 2010-01-27
OK.. There is no VDAPU support for AMD. I notice you keep referencing in your posts. It uses VA-API, a totally different animal. Having anything trying to reference VDAPU on AMD based graphics will choke and lock up the system.

VA-API started out as focused on one GPU manufacturer then grew from there. It in itself on those systems works as the hardware interface, AMD and even nVidia are supported, but differently. The way it works with our cards and nVidia is it is an intermediary layer between the native interfaces. On the note of nVidia that is through VDAPU, while AMD is through X Video Bit Acceleration, AMD, well ATI's response to hardware acceleration that is supposed to be hardware independent. VDAPU is not. VDAPU is a hack to be honest but no one wants to say anything about that because yeah it works. That is not the point though, it is not a proper interface. nVida uses VDAPU to access the hardware acceleration designed for access by DirectX, a totally different animal then what is used in the Linux world.

Because of how VDAPU had to be implemented, it is not a native interface for starters, it is more an interpreter then anything, a virtual Windows environment of sorts. It takes what Linux says, translates it, then passes it onto the hardware. That is how I understand it and if wrong, please correct me on it. XvBA does not have this short coming. It is just not easy to support on Linux because of groups like the MPAA and others.

Before the buyout of ATI, the plan was to fully implement XvBA cross platform and they expected no problems to do so with the consolidation of driver code cross platform, then one did appear. AMD is the ones having to deal with it though.

In the GPU die, for some reason ATI had tied a majority of the XvBA code and programming interface into the DRM code, not a bad thing at all either, unless you want to support the OS with a stigma, we all know and love as Linux. It has earned a bit of a bad reputation but that has had nothing to do with anything negative the Linux community has done.

It is because these groups are convinced because our OS of choice is "free", that the whole Linux community is made up bootleggers and pirates. That is why there is no support for CableCards with Linux to be honest. Centon was releasing their new card for both Windows and Linux, right after the announcement of its upcoming release and support, they recanted on Linux, pulled all documentation of it off their site, and now are all quite about it. The sad part is that every DRM for the most part that has been circumvented has been done on their OS of choice, Windows. Not only that, it is the pirates OS of choice, look at how many WYSWYG applications there are to "backup" movies whether DVD or Blueray, nevermind it is the most pirated software on the Internet.

Windows in all flavors has had so many bootlegs made that is is far from funny if you're Bill Gates, but if you're us in the Open Source community it is a fall on the floor laughing thing for sure. In Asia it is the most popular OS, and surprisingly it is one of the markets Microsoft has the least sales in. It is also the part of the world where the majority of bootlegs come from regardless of if software or multimedia. That is a fact and it is the movie companies' own fault.

 They send copies of these movies to be replicated in Asia, like in countries such as China for sale around the world. The movie companies then blame us for bootlegging. Simply why, is because China has little to no laws against bootlegging and if they did they would never allow an American company to persue Chinese nationals legally within their boarders or extradite them to face charges abroad. So simply we are the scapegoats both as consumers and Linux users. 

Most of us are upstanding citizens who work, pay our taxes, don't cheat or steal, etc, but because of all of this DRM integration, AMD is legally bound to keep the documentation of this interface confidential. They have actually stated this, and how their hands are tied. It is on Phronix somewhere I can't remember the page. Luckily someone managed to get access to this code with the only thing being he can not release any source to the public in the agreement made with AMD. It is not because they want to keep the interface proprietary either.

AMD has stated openly they want to move towards a completely Open Source driver and let the community support the hardware seeing how fast of a turn around there is with video driver development under Linux. It is the DRM and licensing they made that is causing the problem. The DRM in question HDCP ironically was circumvented even before it was implemented. I believe it was someone at MIT that pointed it out too to the committee setting it's standard before finalization and they ignored him.

Regardless of this, we should be greatful that AMD found a way to get support for it working under Linux, even if it is in binary only form, and closed source. You just need to make sure you are using VA-API and not VDAPU though.

Are you using the VA-API or VDAPU?

---

### Post by sports.car.guy on 2010-01-27
I now see what you are talking about with VDPAU. I figured I would compile a new gmplayer where i only compiled the one with the script. That is so annoying when trying to get the build dependencies needed for MPlayer. There is no need to have it as a mandatory package when asking for the build deps without asking if using a nVidia GPU.

I am going to look up all the dependencies minus that requirement because I was able to compile everything minus the GUI which required additional libraries.

Will post more info for that once I have it.

---

### Post by bbruenfl on 2010-01-27
Wow!  That is a lot to digest.  I'm going to try to answer your questions as best I can.  

I'm using the daily trunk builds; ostensibly those are 0.23rWhatever.  I could revert to 0.22-fixes, at least temporarily to see if that is part of the problem.  (If I have time I'll do that tonight.)  

As to vdpau, I saw it in two places.  First in the build-dep for mplayer (as you discovered) which I circumvented by just doing as the thing asked then removing the nvidia thing, reinstalling mythtv et al and the vaapi stuff before compiling mythplayer.  

The second place I saw it was in the logs for mythfrontend when I tried to use VIA Xvmc.  Rereading the logs it looks like mythfrontend tries 4 ports (131-4) on my hardware and doesn't get a response it likes and says "Oh ****!" and grabs for whatever is handy (vdpau) which also fails with another expletive and finally tries Xvideo which works but looks terrible.

I should also mention that Standard Xvmc doesn't even get that far.  It fails with a segmentation fault.  I attached the logs for that below but I think the trunk build is the most likely cause for all my ills.

```

2010-01-27 19:54:11.483 Trying XvMC port 131
2010-01-27 19:54:11.490 Got data on select
2010-01-27 19:54:11.490 Processing ready reads
2010-01-27 19:54:11.490 MythSocketThread(sock 0x1f5bf00:35): socket is readable
2010-01-27 19:54:11.490 MythSocketThread(sock 0x1f5bf00:35): calling m_cb->readyRead()
2010-01-27 19:54:11.490 MythSocket(1f5bf00:35): readBlock(0x140504620689288, 8) called
2010-01-27 19:54:11.491 MythSocket(1f5bf00:35): readBlock(0x140504628232776, 749) called
2010-01-27 19:54:11.491 MythSocket(1f5bf00:35): read  <- 35 749     BACKEND_MESSAGE[]:[]RECORDING_LIST_CHANGE UPDATE[]:[]Human Target[]:[]Embassy Row[]:[]Chance races against time and crashes a black-tie party at the Russian embassy in order to find a friend's killer and stop an international arms deal, but as he moves deeper into the scheme he comes against a beautiful female counterpart.[]:[][]:[]1351[]:[]35_1[]:[]WOFL DT[]:[]WOFL DT[]:[]1351_20100126210000.mpg[]:[]1[]:[]-1956589404[]:[]1264557600[]:[]1264561200[]:[]0[]:[]0[]:[]0[]:[]mythtv-base[]:[]0[]:[]0[]:[]0[]:[]1[]:[]-3[]:[]10[]:[]0[]:[]15[]:[]6[]:[]1264557600[]:[]1264561200[]:[]0[]:[]5[]:[]Default[]:[]0[]:[][]:[]EP01157726[]:[]EP011577260003[]:[]1264564180[]:[]0.000000[]:[]2010-01-26[]:[]1[]:[]Default[]:[]0[]:[]0[]:[]Default[]:[]9[]:[]9[]:[]1[]:[]
2010-01-27 19:54:11.491 MythEvent: RECORDING_LIST_CHANGE UPDATE
2010-01-27 19:54:11.491 MythSocketThread: Total read time: 1ms, on sockets {35,1ms}
2010-01-27 19:54:11.491 Reacquired ready read lock
2010-01-27 19:54:11.491 ProcessAddRemoveQueues
2010-01-27 19:54:11.491 Construct FD_SET
2010-01-27 19:54:11.491 Waiting on select..
2010-01-27 19:54:11.494 Found a suitable XvMC surface 0
2010-01-27 19:54:11.494 MSqlQuery::exec() "SELECT name FROM displayprofilegroups WHERE hostname = 'mythtv-base' "
2010-01-27 19:54:11.501 MSqlQuery::exec() "SELECT profilegroupid FROM displayprofilegroups WHERE name     = 'High Quality' AND       hostname = 'mythtv-base' "
2010-01-27 19:54:11.503 MSqlQuery::exec() "SELECT profileid, value, data FROM displayprofiles WHERE profilegroupid = '4' ORDER BY profileid"
2010-01-27 19:54:11.503 VDP: Accepting: cmp(>= 1920 1080) dec(ffmpeg) cpus(2) rend(opengl) osd(opengl2) osdfade(enabled) deint(none,none) filt()
2010-01-27 19:54:11.503 VDP: Accepting: cmp(>= 0 720) dec(xvmc) cpus(2) rend(xvmc-blit) osd(chromakey) osdfade(enabled) deint(none,none) filt()
2010-01-27 19:54:11.503 VDP: Accepting: cmp(>= 0 0) dec(ffmpeg) cpus(2) rend(xv-blit) osd(softblend) osdfade(enabled) deint(none,none) filt()
2010-01-27 19:54:11.503 VDP: LoadBestPreferences(2048x2048, 0)
2010-01-27 19:54:11.503 VDP: LoadBestPreferences(2048x2048, 60)
2010-01-27 19:54:11.503 VDP: LoadBestPreferences(1280x720, 60)
2010-01-27 19:54:11.503 VideoOutputXv: @ j=0 Looking for flag[s]: XvInputMask  1d
2010-01-27 19:54:11.503 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-27 19:54:11.503 VideoOutputXv: Has XVideo flags...
2010-01-27 19:54:11.504 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-27 19:54:11.504 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-27 19:54:11.504 VideoOutputXv: @ j=1 Looking for flag[s]: XvInputMask  d
2010-01-27 19:54:11.504 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-27 19:54:11.504 VideoOutputXv: Has XVideo flags...
2010-01-27 19:54:11.504 VideoOutputXv: Missing XV_COLORKEY, rejecting.
2010-01-27 19:54:11.504 VideoOutputXv: @ j=2 Looking for flag[s]: XvInputMask  15
2010-01-27 19:54:11.504 VideoOutputXv: Adaptor#0: ATI Radeon AVIVO Video has flag[s]: XvInputMask XvImageMask 
2010-01-27 19:54:11.504 VideoOutputXv: Has XVideo flags...
2010-01-27 19:54:11.504 VideoOutputXv: Has XV_BRIGHTNESS...
2010-01-27 19:54:11.504 VideoOutputXv: Here...
2010-01-27 19:54:11.504 XvMCSurfaceTypes::find(w 1280, h 720, chroma 1, vld 0, idct 1, mpeg2, sub-width 0, sub-height 0, disp, p<= 131, 134 <=p, port, surfNum)
2010-01-27 19:54:11.504 Trying XvMC port 131
2010-01-27 19:54:11.504 Found a suitable XvMC surface 0
2010-01-27 19:54:11.504 VideoOutputXv: Grabbed xv port 131
2010-01-27 19:54:11.504 VideoOutputXv: XvMC surface found with IDCT support on port 131
2010-01-27 19:54:11.504 VideoOutputXv: XV_SET_DEFAULTS is supported on this port
Segmentation fault

```

I'll post again when I have a chance to run 0.22-fixes.

Thanks again for your help.

---

### Post by bbruenfl on 2010-01-27
ok, i reverted to an old copy of my database and rolled back to 0.22-fixes22594.  Unfortunately, I'm getting the exact same behavior.  I updated to 10.1 (released today) with the exact same behavior as under 9.10, 9.12, and 9.12 hotfix.  I wonder if my graphics card is the issue.  I know your guide only "officially" supports 4xxx and 5xxx but the xvba-video notes success using HD3300 (RS780D) under amd64 which just so happens to be what I am running.  Am I wrong to think that based on that at least the mplayer-vaapi should work correctly?

---

### Post by sports.car.guy on 2010-01-28
> **bbruenfl said:**
> ok, i reverted to an old copy of my database and rolled back to 0.22-fixes22594.  Unfortunately, I'm getting the exact same behavior.  I updated to 10.1 (released today) with the exact same behavior as under 9.10, 9.12, and 9.12 hotfix.  I wonder if my graphics card is the issue.  I know your guide only "officially" supports 4xxx and 5xxx but the xvba-video notes success using HD3300 (RS780D) under amd64 which just so happens to be what I am running.  Am I wrong to think that based on that at least the mplayer-vaapi should work correctly?

The VxMC issues, now I know exactly why it failed. I believe how the HD3300 handles the hardware decode of MPEG2 is not compatible with HD4XXX and higher GPU's. The HD3300 actually, as with the rest of the HD3xxx and prior uses the actual GPU and code on it's die. The HD4xxx and higher use the GPU and shaders I believe. Doing that has allowed for them to cram more on the die with later GPU's on the note of other capabilities with only a little increase in GPU overhead..

It is nice to see fglrx is still supporting models as low as the HD2400. I thought by now the HD3200 or HD3300 on board ones would be the oldest supported. In theory the UVD should work. I did encounter the same issue on the stable with updates. When I made my post about using it I forgot I had compiled prior. I did remember actually having compiling MPlayer with a GUI and letting it run.

I have two versions that are compiled to run on X86 64bit architecture. The one in the tutorial and the one with the GUI. I am thinking that I will zip up their directories and allow for others to download and use on 64bit Ubuntu. It is all because the VDAPU library changed from a versioned one matching the driver revisions, and MPlayer dependencies for Ubuntu have not been updated to reflect this.

_UPDATE:_

I just tested the GUI version of MPlayer, and it was not pretty. It does not like something when it comes to it and the OpenGL renderer. Normal MPlayer with VA-API works without a hitch. It could be my system though. I am going to zip both compiled versions' folders into on file, and add it to the tutorial. One thing I need to address is since I originally performed my install of 9.10 and this reinstall something changed with dependencies on VA-API files. Makes no sense you have to have the binary for VA-API on the system first before the source code, yet that is the requirement now. That is something new to me because I have never seen under Linux the binary of a file required for the source to be installed, which is what the dev package basically is.

I will be placing the archive and editing the guide later today.

---

### Post by sports.car.guy on 2010-01-29
This guide is getting a big update. I am in the process of writing it now. I have solved getting OpenGL rendering and MythTV to work happily together. It took a bit of tweeking, a couple changes to xorg.conf, and I am now watching a perfect, absolutely tear free, television.

Using XvMC or XVideo renders caused for an occasional slight tear usually at the bottom of the screen during normal playback. Testing my changes to get OpenGL working I have not seen one tear in the picture and I have been looking too.

There are also some other changes I need to make as well. For some reason now the VA-API development package requires the binaries for VA-API to be installed. I never encountered that issue till someone else brought it to my attention.

I can say officially that AMD can now give nVidia a run for its money in the HTPC arena thanks to Catalyst 10.1 and a couple xorg.conf tweeks.

---

### Post by AKADAP on 2010-01-30
I attempted to follow these instructions, but due to some bits being a bit unclear for a newbe, I have halted for the moment.

First bit of confusion:
Links to libva1, libva-dev, and libva1-dbg all directly download files

The link to xvba-video dumps me into a large directory. I was able to figure out which file to download from here though.

The link to mplayer-vaapi also dumps me into a large directory. In this one, it is not clear which file I should be downloading.

When attempting to find the two files that ATI neglected to install, running

sh ati-driver-installer-9-xx-x86.x86_64.run --buildpkg Ubuntu/source

failed because ati-driver-installer-10-1-x86.x86_64.run was in a directory who's name had a space in it.

When I put it in a directory path with no spaces, it ran properly.

Finding the missing files was problematic however because there are multiple lib64 directories in the tree.

I finally found the files in arch/x86_64/usr/X11R6/lib64

Once I got the files in place, I changed the owner, group & attributes to match other lib files in that directory, though this was not mentioned in the instructions.

I finally got stuck on the editing of the xorg.conf file.
There is no "driver" section in my copy of this file, and it is not clear how I should add a "driver" section.

The instructions should probably be added to the mythTV wiki.

---

### Post by sports.car.guy on 2010-01-30
> **AKADAP said:**
> I attempted to follow these instructions, but due to some bits being a bit unclear for a newbe, I have halted for the moment.

First bit of confusion:
Links to libva1, libva-dev, and libva1-dbg all directly download files

The link to xvba-video dumps me into a large directory. I was able to figure out which file to download from here though.

The link to mplayer-vaapi also dumps me into a large directory. In this one, it is not clear which file I should be downloading.

When attempting to find the two files that ATI neglected to install, running

sh ati-driver-installer-9-xx-x86.x86_64.run --buildpkg Ubuntu/source

failed because ati-driver-installer-10-1-x86.x86_64.run was in a directory who's name had a space in it.

When I put it in a directory path with no spaces, it ran properly.

Finding the missing files was problematic however because there are multiple lib64 directories in the tree.

I finally found the files in arch/x86_64/usr/X11R6/lib64

Once I got the files in place, I changed the owner, group & attributes to match other lib files in that directory, though this was not mentioned in the instructions.

I finally got stuck on the editing of the xorg.conf file.
There is no "driver" section in my copy of this file, and it is not clear how I should add a "driver" section.

The instructions should probably be added to the mythTV wiki.



I apologize I never got to finish the updating completely last night. It is still mostly the old guide. I haven't gotten to finish getting the links straight. The reason why those two links dump into a directory is because those files seem to update frequently. I am going to put a note under each link like that.

I am also going to explain better where in the xorg.conf those entries go.

I am really sorry things aren't complete. I have no excuse except my bed was looking too good.

It should be completely set by Monday the latest.

I still need to add the OpenGL render settings to MythTV as well now that I got that working properly.

---

### Post by AKADAP on 2010-01-31
> **sports.car.guy said:**
> I apologize I never got to finish the updating completely last night. It is still mostly the old guide. I haven't gotten to finish getting the links straight. The reason why those two links dump into a directory is because those files seem to update frequently. I am going to put a note under each link like that.

I am also going to explain better where in the xorg.conf those entries go.

I am really sorry things aren't complete. I have no excuse except my bed was looking too good.

It should be completely set by Monday the latest.

I still need to add the OpenGL render settings to MythTV as well now that I got that working properly.

leaving it incomplete is fine as long as there is a note telling us newbes that it is incomplete and not to try it until it is complete.

I'll have another go on Monday.

---

### Post by sports.car.guy on 2010-01-31
> **AKADAP said:**
> leaving it incomplete is fine as long as there is a note telling us newbes that it is incomplete and not to try it until it is complete.

I'll have another go on Monday.

The second version is incomplete. It is complete otherwise. The things I documented to do will all work for you. It is just updating for the purposes of getting it more current more then anything.

Again I am sorry. And the fact you are a newbie, I did lay out all of the commands, I stated to add the xorg.conf settings to the device section for the video card. I then also laid out the settings in MythTV, besides more. It is not like I said you are can get it to do this and left you high and dry. This is the most documentation you will find on this anywhere on the Internet.

I am writing this in my spare time, around establishing the company I started, and other considerations as well like living my life. I am doing this as a favor, simply because the MythTV community, when I have asked for help getting the AMD GPU's best with MythTV, I get told every time to buy an nVidia, by the people who are supposed to be helping. That is on the MythTV IRC channel where MythTV's documentation tells you to go for help first and foremost.

The links I have dump into a directory, that I haven't commented on yet. If there is nothing saying to get a particular version, I expected common sense to prevail and the most current one would be downloaded. I did assume on that as I moved on to get the bulk of the changes done. I guess I was wrong to assume and sorry for that too.

This took me hours on hours of research, along with trial and error. I am saving you all of that. There is no reason to get on me like you are. Everything for the first version of this guide is still up there and does work. I would not leave it so people are hanging.

---

### Post by jetpeach on 2010-02-01
thanks for the guide! you said this is for the 4000 and 5000 series amd cards, any idea if it would also work with the 3000 series? i have an hd 3600 in one of my computers that can't play hd worth crap right now... maybe the card is also just too old?

thanks again!

---

### Post by sports.car.guy on 2010-02-01
> **jetpeach said:**
> thanks for the guide! you said this is for the 4000 and 5000 series amd cards, any idea if it would also work with the 3000 series? i have an hd 3600 in one of my computers that can't play hd worth crap right now... maybe the card is also just too old?

thanks again!

I believe you will gain some benefit from the guide. The one thing I am seeing a problem with the HD3xxx's it their support of XvMC. They are still models that use the GPU die itself for decoding, completely through it. Where as the HD4000 series and higher do more of the decoding through shaders from what I have read, but I could be wrong on how they perform the decode.

The XvBA on the other hand I know should work for you. Someone started to make the effort, got it to work, and got a little discouraged when XvMC didn't work for him.

I believe the OpenGL tweeks I have made on my system could translate to yours with lower Catalyst settings on the note of MythTV too.

I  am working on getting the guide complete now. By tomorrow night I am going to say the absolute latest it will be complete.

---

### Post by AKADAP on 2010-02-01
> **sports.car.guy said:**
> The second version is incomplete. It is complete otherwise. The things I documented to do will all work for you. It is just updating for the purposes of getting it more current more then anything.

Again I am sorry. And the fact you are a newbie, I did lay out all of the commands, I stated to add the xorg.conf settings to the device section for the video card. I then also laid out the settings in MythTV, besides more. It is not like I said you are can get it to do this and left you high and dry. This is the most documentation you will find on this anywhere on the Internet.

I am writing this in my spare time, around establishing the company I started, and other considerations as well like living my life. I am doing this as a favor, simply because the MythTV community, when I have asked for help getting the AMD GPU's best with MythTV, I get told every time to buy an nVidia, by the people who are supposed to be helping. That is on the MythTV IRC channel where MythTV's documentation tells you to go for help first and foremost.

The links I have dump into a directory, that I haven't commented on yet. If there is nothing saying to get a particular version, I expected common sense to prevail and the most current one would be downloaded. I did assume on that as I moved on to get the bulk of the changes done. I guess I was wrong to assume and sorry for that too.

This took me hours on hours of research, along with trial and error. I am saving you all of that. There is no reason to get on me like you are. Everything for the first version of this guide is still up there and does work. I would not leave it so people are hanging.

I apologize if you thought I was unappreciative of your work. It was not my intent to complain, merely to point out that I did get stuck and what parts gave me trouble. Common sense is obtained via experience, since my experience is limited in this matter, so is my common sense.

I have been using my ATI 4850HD card for more than a year now with less than satisfactory video performance, and I am very appreciative that you are attempting to do something about it.

---

### Post by Bloemetjesgordijn on 2010-02-01
Thx sports.car.guy for your tutorial.

I have a one comment and a question

sudo ln-s libXvBAW.so.1.0 libXvBAW.so.1 ...should this be 
sudo ln -s libXvBAW.so.1.0 libXvBAW.so.1 (note the space between ln and -s)


As for the two missing files
in the /usr/X11R6/lib64 containts no files
/usr/X11R6/lib64/modules/dri containts three files:
fglrx_dri.so
libXvBAW.so.1
libAMDXvBA.so.1

I did in the modules/dri folder: 
sudo ln -s libXvBAW.so.1.0 libXvBAW.so.1 and 
sudo ln-s libAMDXvBA.so.1.0 libAMDXvBA.so.1  

 ...is this correct? 
Because when I enter "vainfo" in Konsole I get:
libva: libva version 0.31.0-sds4
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
XVBAWrapper: Could not load hardware specific XVBA library.
libAMDXvBA.so.1: cannot open shared object file: No such file or directory
libva error: /usr/lib/va/drivers/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

pls help..

Bloemetjesgordijn

---

### Post by sports.car.guy on 2010-02-01
> **Bloemetjesgordijn said:**
> Thx sports.car.guy for your tutorial.

I have a one comment and a question

sudo ln-s libXvBAW.so.1.0 libXvBAW.so.1 ...should this be 
sudo ln -s libXvBAW.so.1.0 libXvBAW.so.1 (note the space between ln and -s)



As for the two mising files
I only did: 
sudo ln -s libXvBAW.so.1.0 libXvBAW.so.1 ...is this sufficient? should I copy something??

But when I enter "vainfo" in Konsole I get:
libva: libva version 0.31.0-sds4
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
XVBAWrapper: Could not load hardware specific XVBA library.
libAMDXvBA.so.1: cannot open shared object file: No such file or directory
libva error: /usr/lib/va/drivers/fglrx_drv_video.so init failed
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit

pls help..

Bloemetjesgordijn

Yeah you need the files that I explain have to be extracted from the driver installer's created source package that you get issuing this command.

sh ati-driver-installer-10-1-xx-x86.x86_64.run --buildpkg Ubuntu/source

It creates a .tgz I believe, regardless it is a zipped archive, you extract it and go to /x86_64/usr/X11R6/lib64 inside it, they are in this directory. You then need to copy them over to /usr/lib in the case of Ubuntu. Another distro it might be /usr/lib64. Then you symlink them inside the directory as explained. That should solve your problem.

On the note of the symlinks. The space will work, at least it used to. That has been the proper way to do it for as long as I have used Linux. -s is a switch and all switches are not part of the command. Unless someone decided to get sloppy and change what was proper to that.

---

### Post by sports.car.guy on 2010-02-01
_**Updates are Complete:**_

Hello everyone,

I just got all of the updates to this guide complete. I believe I got a lot of the confusing aspects ironed out and made it easier to follow. I also added getting OpenGL rendering to work with MythTV.

The only bug I have encountered since getting it to work is trying to look at the guide while watching a recorded program. That is the only layering / rendering issue using OpenGL I have encountered so far. It should not effect your experience unless you are one to check out the guide while watching recordings. It works fine during Live TV and also when scheduling recordings so I don't see any problems arising from this.

I hope everyone gets a lot of use out of this and enjoys.

Sports Car Guy

---

### Post by sports.car.guy on 2010-02-01
> **AKADAP said:**
> I apologize if you thought I was unappreciative of your work. It was not my intent to complain, merely to point out that I did get stuck and what parts gave me trouble. Common sense is obtained via experience, since my experience is limited in this matter, so is my common sense.

I have been using my ATI 4850HD card for more than a year now with less than satisfactory video performance, and I am very appreciative that you are attempting to do something about it.


It is all good. I understand. Plus I bet a little frustration kicked in.


I think now you should see a lot better performance from your HD4850.

---

### Post by Bloemetjesgordijn on 2010-02-02
Sports Car Guy,

The two missing files were partially missing 

libXvBAW.so.1 is in both usr/lib and usr/ib32
libXvBAW.so.1.0 is in both usr/lib and usr/ib32

libAMDXvBA.so.1 is in usr/lib32
libAMDXvBA.so.1.0 is in usr/lib32

It seems that I dont have libAMDXvBA.so.1.0 in 64 bits 

And I cant find the file in usr/X11R6/lib64???

---

### Post by hicotton02 on 2010-02-07
Sports Car Guy,

First off, Thanks for the guide! I found this guide after searching for a reason my hvr-1600 was playing crappy video. There are a few things:

I too found those missing files to be in /usr/lib32/. btw i am running mythbuntu 9.10 with the nightly builds for .22. I have an ATI HD3200 integrated on the mobo.AMD X2 3.0Ghz and 4GB ram. All audio and video are going through my HDMI connection. After updating the catalyst driver and changing the playback setting i broke my livetv playback. when i click watch TV, all i get is :

2010-02-07 20:57:45.450 NVP(0): Timed out waiting for free video buffers.

this replicates until i kill mythfrontend, then one core of the cpu will spike to 100% until i restart the system. trying to kill the process does no good. All i get is "mythfrontend.real <defunct>" in top or anything else. everything else seems to work. ill do some more testing and get back with you. 

PS. I would like that mplayer that you have set up if it becomes available.

---

### Post by hicotton02 on 2010-02-07
Ok, so I unchecked the "enable OpenGL vertical sync" option and it started working again. The picture is soooo much smoother!! still looks like crap but what can you expect from an SD cable connection to a 1080p 52" lcd screen... did get these weird messages if it matters:
```
2010-02-07 21:18:51.675 TV: Changing from None to Watching WatchingLiveTV
2010-02-07 21:18:51.675 TV: State is LiveTV & mctx == ctx
2010-02-07 21:18:51.676 New DB connection, total: 3
2010-02-07 21:18:51.676 TV: UpdateOSDInput done
2010-02-07 21:18:51.676 TV: UpdateLCD done
2010-02-07 21:18:51.676 Connected to database 'mythconverg' at host: 127.0.0.1
2010-02-07 21:18:51.677 Realtime priority would require SUID as root.
2010-02-07 21:18:51.699 Video timing method: USleep with busy wait
2010-02-07 21:18:51.701 TV: ITVRestart done
2010-02-07 21:18:51.735 ScreenSaverX11Private: DPMS Deactivated 1
2010-02-07 21:19:04.937 WriteAudio: buffer underrun
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.995 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:04.996 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.713 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.713 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.714 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.715 [mpeg2video @ 0x7fa64be26820]Missing picture start code
2010-02-07 21:19:22.725 WriteAudio: buffer underrun
2010-02-07 21:20:13.354 TV: Attempting to change from Watching WatchingLiveTV to None
2010-02-07 21:20:14.996 TV: Changing from Watching WatchingLiveTV to None
2010-02-07 21:20:14.997 ScreenSaverX11Private: DPMS Reactivated 1

```

Also running a true 1080p video from my library looks incredible. albiet my amd is sweating(95+%) but it runs smoothly

---

### Post by linuxad on 2010-02-26
Hello, Thanks for guide.
My laptop has Mobility Radeon Hd 2400 and it supports hardware acceleration. I installed 10.2 driver and did what exactly you said. libXvBAW.so.1.0 and libAMDXvBA.so.1.0 are in /usr/lib. it said when i opened a mkv file;
```
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vo_vaapi] Using OpenGL rendering
libva: libva version 0.31.0-sds4
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: dlopen of /usr/lib/va/drivers/fglrx_drv_video.so failed: libva-0.31.0.5.so.1: cannot open shared object file: No such file or directory
libva: va_openDriver() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.
```

There is a solution about this?

---

### Post by psychok9 on 2010-03-01
I've tried any line of your guide, but don't work with my specs.
ATi Radeon 5850, Intel Q6600 2.4GHz, Ubuntu Karmic 9.10 and Catalyst 10.2.

```
sudo vainfo
libva: libva version 0.31.0-sds5
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.6.9
vainfo: Supported profile and entrypoints
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11

```
```
./mplayer -vo vaapi -va vaapi "Stars Comparison.mp4"
MPlayer SVN-r30589-4.4.1 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Stars Comparison.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  1280x720  24bpp  24.961 fps  1995.5 kbps (243.6 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
libva: libva version 0.31.0-sds5
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 127.4 kbit/9.03% (ratio: 15927->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 H.264 VA API Acceleration 
[vo_vaapi] Using 1:1 VA surface mapping
**FATAL: Cannot initialize video driver.**
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=0.
Unsupported PixelFormat 61
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=2.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=3.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 Planar YV12 
A:   1.9 V:   1.9 A-V: -0.000 ct: -0.015   0/  0 11% 16%  2.5% 3 0 
Exiting... (Quit)

```

---

### Post by psychok9 on 2010-03-01
I've tried glxgears, and It works flawless: 300 frames/5s with VSYNC ON, and 20.000 with VSYNC off (AMD CCC).
Launched "aticonfig --sync-vsync=on" and "aticonfig --sync-video=on" with no result.
I get a lot of video tearing, also with low resolution videos!

---

### Post by damvcoool on 2010-03-03
> **linuxad said:**
> Hello, Thanks for guide.
My laptop has Mobility Radeon Hd 2400 and it supports hardware acceleration. I installed 10.2 driver and did what exactly you said. libXvBAW.so.1.0 and libAMDXvBA.so.1.0 are in /usr/lib. it said when i opened a mkv file;
```
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1280x720  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vo_vaapi] Using OpenGL rendering
libva: libva version 0.31.0-sds4
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva error: dlopen of /usr/lib/va/drivers/fglrx_drv_video.so failed: libva-0.31.0.5.so.1: cannot open shared object file: No such file or directory
libva: va_openDriver() returns -1
[vo_vaapi] vaInitialize(): unknown libva error
Error opening/initializing the selected video_out (-vo) device.
```

There is a solution about this?

Only UVD2 is supported by this method, so anything older than AMD HD 4000 series is not going to work.

---

### Post by mchlor on 2010-03-13
> Then you need to configure the GUI and OSD for it:
$ ./configure --enable-gui --enable-menu

Thanks for the guide.  everything works great but mplayer-vaapi-latest-FULL.tar won't compile gmplayer.  It only compiles cli mplayer.

anyone know why?  is there smplayer for this build or maybe another front end?

---

### Post by the_king_men on 2010-03-15
damvcoool,
I had this problem with a radeon hd2600. 
I normally install ati driver using --buildandinstallpkg. When you use this method, the xvba package is not installed. You need to --buildandinstallpkg and then manually install "libamdxvba1_...".
Even if my hd2600 IS NOT on the list, and have a uvd1 IT STILL WORK. So I guess you still have chance. 
But.... even if it work, there so much restriction : high@4.1 max 4 ref frame max, when it work, the color are messy.... So, completly useless. 
If you want a real advice, try compiling a newer mplayer, there have been speed improvement in the h264 decoder, and you could also use the multithreaded ffmpeg decoder, faster on pc with > 1 core. 
With the mplayer recent version, I was able to play a 1080p video I was unable before because my system was to slow.

---

### Post by dmitneo on 2010-03-25
Apparently this thread is also avaliable with additional replies at  

[Click here: LinuxQuestions.org]("http://www.linuxquestions.org/questions/linux-desktop-74/amd-hd-series-graphics-guide-optimizing-video-playback-for-mythtv-mplayer-and-others-786335/")

---

### Post by turkosbon on 2010-04-24
hello i try wit ati y vaapi 

i have install catalyst 10.3 for my system x86_64, i my subdirectorie /usr/lib i have

i have ati HD4200 integrated in Gigabyte GA-MA785GT-UD3H
> 
libAMDXvBA.cap
libAMDXvBA.so.1 -> libAMDXvBA.so.1.0
libAMDXvBA.so.1.0
libXvBAW.so.1 -> libXvBAW.so.1.0
libXvBAW.so.1.0
> 
Linux htpc 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux 
i have compiling the last livba and install .deb
> 
libva1_0.31.0-1+sds12_amd64.deb
libva-dev_0.31.0-1+sds12_amd64.deb

xvba-video-latest.amd64.deb  -> xvba-video_0.6.11-1_amd64.deb
when i put vainfo get this result

> 
libva: libva version 0.31.0-sds6
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA API - 0.6.11
vainfo: Supported profile and entrypoints
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
xvba_video: XVBA_CreateContext(): status 11
it is correct ?

Thank you.

---

### Post by the_king_men on 2010-04-26
turkosbon, did you read my last post ? Try to install the xvba driver from the video driver. You have a hd2400 so your card may or may not work (because it is not officially supporter). My hd2600 was not supported but work anyway. 

Also, you installed libva ([http://www.splitted-desktop.com/~gbeauchesne/libva/](http://www.splitted-desktop.com/~gbeauchesne/libva/)) but did you install xvba-video ? ([http://www.splitted-desktop.com/~gbeauchesne/xvba-video/](http://www.splitted-desktop.com/~gbeauchesne/xvba-video/)) 
libva is a general framework for accelerated video stream. It can use either nvidia system or ati system, but for that you need to install one of these system. 
More info about the libva in wikipedia.

---

### Post by logan_2k6 on 2010-04-28
Hi,

It seems that compiling mplayer-vaapi with libva >*10 it will give this error.
You can try to change the -vo vaapi with whatever you wish for and it will work but i'm not so sure if it will use the GPU.
Don't know how to fix this one...i'm a noob
mplayer-vaapi compiled with libva *10 works but has some ugly "bug" with colors.


Edit:

Sorry for the above...seems that i am quite a beginner and i've installed the wrong version of xvba. After installing the latest xvba and libva everything works BUT the problem with colors going wrong is still there even with libva sds13.

---

### Post by jetpeach on 2010-05-03
is there a guide like this for lucid lynx? does this guide still apply for lucid or does it need upgrading?

---

### Post by Fill23 on 2010-05-04
> **jetpeach said:**
> is there a guide like this for lucid lynx? does this guide still apply for lucid or does it need upgrading?
I'm using Kubuntu Lucid and i just completed this guide to the point of working mplayer-vaapi, didn't try MythTV cause don't using it.

Now i have two questions:
1 - After i builded mplayer i got a folder full of files and no .deb one. How can i install this version of mplayer in the system? I want it because when i'm trying to install smplayer it automaticly tries to install original mplayer, because it thinks there is no mplayer installed in the system.

2 - During playback i sometimes see that overall color balance of a picture changes, like  1 sec it's slightly greenesh next sec it normal and then next second it's slightly bluesh. I know that problem is not the movie file, because on another computer it plays normal, without color changes, and md5 is same.

---

### Post by N.Simpson on 2010-05-05
Thanks for the tutorial. I know have this working on a 785G board (Radeon HD 4200) and can watch tear free video with CPU usage of ~5%.

I think you should change your libva links in the tutorial though as they no longer have the correct library version. The current links are to sds9, I used sds13 to get this working.

Thanks again though, the rest of it worked an absolute treat!

---

### Post by xzero1 on 2010-05-05
Simple nautilus script for playing the selected file fullscreen. After installing mplayer....

Place the following script into your nautilus-scripts folder i.e. ~/.gnome2/nautilus-scripts. 

```
#!/bin/bash
trap 'pkill -ALRM mplayer;exit(1)' INT 

mplayer -vo vaapi:gl -va vaapi -fs -ao pulse $1
# modify the mplayer line as you see fit
# note this only plays files compatible with the mplayer options

```Make sure to use the .sh suffix on the filename and make it executable. To use: right click selected file in nautilus, select 'scripts' and whatever you named it.

@sports.car.guy
Feel free to add this to your guide as you see fit.
Thanks for the guide.

---

### Post by n3had on 2010-05-16
```
tm@tm:~/mplayer2/mplayer-vaapi$ ./mplayer -vo vaapi -va vaapi /home/tm/video2.mp4
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
MPlayer SVN-r31027-4.4.3 (C) 2000-2010 MPlayer Team
138 audio & 301 video codecs
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/tm/video2.mp4.
libavformat file format detected.
[lavf] Audio stream found, -aid 0
[lavf] Video stream found, -vid 1
VIDEO:  [H264]  1280x720  24bpp  29.960 fps  2014.2 kbps (245.9 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: isomavc1mp42
libva: libva version 0.31.0-sds6
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 44100 Hz, 2 ch, s16le, 124.5 kbit/8.82% (ratio: 15561->176400)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=0.
Unsupported PixelFormat 61
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=2.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
[VD_FFMPEG] Trying pixfmt=3.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1280x720 => 1280x720 Planar YV12 
A:   2.5 V:   1.8 A-V:  0.733 ct:  0.059   0/  0 21% 122%  1.8% 50 0 

           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

No bind found for key 'MOUSE_BTN0'.-MOUSE_BTN0_DBL                         
No bind found for key 'MOUSE_BTN0_DBL'.                         14 0 
A:  59.5 V:  59.5 A-V: -0.002 ct:  0.028   0/  0 33% 29%  0.8% 314 0 

MPlayer interrupted by signal 2 in module: sleep_timer
A:  59.5 V:  59.5 A-V: -0.000 ct:  0.028   0/  0 33% 29%  0.8% 314 0 
Exiting... (Quit)
tm@tm:~/mplayer2/mplayer-vaapi$ 

```

The video is running fine except the cpu usage is still the same as it is using ffmpeg for decoding h264 video. Any idea where i am going wrong? 

Ubuntu 10.04 64bit with ati 10.4 drivers

---

### Post by boravl on 2010-05-21
hello everyone
i have some problems with playing mkv files in patched mplayer-vaapi
when i trying play mkv i see this picture:

[[IMG]http://i.piccy.info/i5/43/57/125743/Ekran_800.jpg[/IMG]](http://piccy.info/view3/125743/b98675b92b6e9433e96868c5d21797fc/orig/)

content from terminal:

```
root@ravl-home:~# mplayer-vaapi -vo vaapi:gl -va vaapi /mnt/tomas/video/hd/Avatar.mkv
MPlayer SVN-r31027-4.2.4 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /mnt/tomas/video/hd/Avatar.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/AVC), -vid 0
[mkv] Track ID 2: audio (A_AC3), -aid 0, -alang und
[mkv] Track ID 3: subtitles (S_VOBSUB), -sid 0, -slang ukr
[mkv] Track ID 4: subtitles (S_TEXT/UTF8), -sid 1, -slang und
[mkv] Track ID 5: subtitles (S_TEXT/UTF8), -sid 2, -slang und
[mkv] Track ID 6: subtitles (S_TEXT/UTF8), -sid 3, -slang und
[mkv] Track ID 7: subtitles (S_TEXT/UTF8), -sid 4, -slang und
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vo_vaapi] Using OpenGL rendering
libva: libva version 0.31.0-sds6
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/va/drivers/fglrx_drv_video.so
libva: va_openDriver() returns 0
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] VA API accelerated codec.
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [ffac3] afm: ffmpeg (FFmpeg AC-3)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Unsupported PixelFormat 61
[VD_FFMPEG] Trying pixfmt=1.
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [vaapi] 1920x1080 => 1920x1080 H.264 VA API Acceleration 
[vo_vaapi] Using 1:1 VA surface mapping
[VD_FFMPEG] XVMC-accelerated MPEG-2.
A:  13.1 V:  13.1 A-V:  0.000 ct: -0.000   0/  0 12%  5%  1.3% 10 0 
Exiting... (Quit) 
```



i have not such problem with "avi" and "ts" files and they playing normally

PS: sorry for my bad english

---

### Post by Tom 6 on 2010-06-26
Hi :)

Where can i get the 32bit version of libva?

The links are mostly to direct downloads now but i am sure they were to ftp type sites before which meant i could get the 32 bit versions.  Is this guide only for 64bit editions of Ubuntu? I am sure i used it for a 32bit edition fairly recently?

Many regards from
Tom :)

[Edit] Found my own way by 'hacking' the url. Used right-click to "Copy Link location" and then pasted into a url address bar at the top of the web-browsre and deleted off the 64bit folder & download. This got me to the ftp site where i navigated into 
[http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/i386/?C=M;O=D](http://www.splitted-desktop.com/~gbeauchesne/libva/pkgs/i386/?C=M;O=D)

---

