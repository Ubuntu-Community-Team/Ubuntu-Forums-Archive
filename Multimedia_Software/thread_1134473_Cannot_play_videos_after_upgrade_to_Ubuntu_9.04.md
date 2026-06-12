---
title: "Cannot play videos after upgrade to Ubuntu 9.04"
date: 2009-04-23
forum: Multimedia Software
---

### Post by ytimer on 2009-04-23
After upgrading from Ubuntu 8.10 to Ubuntu 9.04 beta, none of my video formats are playing (.avi, .mp4, wmv). The video player starts up and closes immediately without giving any error. This behavior is seen on both Totem Movie Player and VLC, whether I'm starting the video's directly by double clicking the file or indirectly opening them via the players. I also tried installing VLC from scratch without any change in results.
 I played a couple audio files (mp3 and mid) and they seem to work perfectly, so it can't be an audio issue.


Any help would be appreciated!

---

### Post by zero777zero on 2009-04-23
install restricted extras via the add/remove, make sure you choose show: all applications

---

### Post by ytimer on 2009-04-23
I tried it. Unfortunately it didn't work.

---

### Post by gfe on 2009-04-23
I would check Preferences with each player to see which video driver is being used. Both [FONT="Courier New"]vlc[/FONT] and [FONT="Courier New"]mplayer[/FONT] crash on me unless I'm using the X11 driver (the defaults don't work). This may have nothing to do with your situation, but it's worth a try.

---

### Post by nelsonm on 2009-04-23
I had no problem playing videos.

---

### Post by DDM on 2009-04-23
Can't really help any, but my X crashes back to gdm when I play videos fullscreen. Also seems to happen when I use the volume keys on my keyboard (I blame the notification thingy). 

I have another Ubuntu HTPC for playing video so I'm not in need of an immediate fix, but I thought I should chime in. Also, I'm having a little trouble finding error messages related to it, so that's all I have for now.

---

### Post by robo100 on 2009-04-24
I have an issue as well, but its a little different than your issue. I convert a lot of videos for my PS3 using handbrake and had no problems viewing the MP4 converted files. After installing 9.04 the videos play fine after initial boot up but after about 3 minutes if you try to view an MP4 file it will play but has severe glitches. If I reboot then everything is ok for a few minutes. I am not sure if its just the playback or if this is also an issue for converting files. I will play around with it to see what happens. With version 8.10 I never had any problems at all.

---

### Post by RalphPS on 2009-04-24
I have the same issue with AVI's using VLC and the standard movie player since upgrading this morning.  I applied the restricted extras but no-go and VLC will not play a DVD file.

---

### Post by robo100 on 2009-04-24
I dont know if this will help debug anything but here is what I noticed:

- I can open a window with the MP4 file and it may or may not play. It is pretty random as far as playing correctly. It really has nothing to do with the time the machine has been on. I can double click on the MP4 file and it will play fine. If I close the Viewer and click on the same MP4 file it wont play at all or it has a lot of glitches.

Here is what I have
- AMD X2 6000+ Processor
- 4Gb Ram
- 1TB SATA hard disk (400GB free)
- NVIDIA GEFORCE 7600
- Running X64 version of Ubuntu
- All restricted extras installed

I noticed that when an MP4 file plays correctly CPU usage is under 20%. When there is an issue with the file both CPU cores goto 100%. Memory utilization stays under 20%. Again I dont know if this information will help anybody to figure out whats going on. Thanks for reading...

---

### Post by Don DeGregori on 2009-04-24
**Wait for the updates! What do want for nothing! I'm sure the hard working gurus at Ubuntu will soon have a fix**

---

### Post by vgrisham on 2009-04-24
> **Don DeGregori said:**
> **Wait for the updates! What do want for nothing! I'm sure the hard working gurus at Ubuntu will soon have a fix**

Huh?

---

### Post by AKADAP on 2009-04-24
> **Don DeGregori said:**
> **Wait for the updates! What do want for nothing! I'm sure the hard working gurus at Ubuntu will soon have a fix**

If the developers do not know there is a problem, there will never be any updates.

Keep the complaints coming, and hope there is an update.

---

### Post by dthomsen on 2009-04-24
I too am having this issue. Switching to X11 in mplayer is not really an option as doing that no longer lets you resize the video and doesn't fix VLC.
   I have seen some other threads mentioning Intel drivers. I am running an intel video card, how about everyone else?

   What log should I be looking at to tell me why X crashes?

---

### Post by vgrisham on 2009-04-24
> **dthomsen said:**
> I too am having this issue. Switching to X11 in mplayer is not really an option as doing that no longer lets you resize the video and doesn't fix VLC.
   I have seen some other threads mentioning Intel drivers. I am running an intel video card, how about everyone else?

   What log should I be looking at to tell me why X crashes?

I hadn't thought about the video driver. That must be it. Video playback is working perfectly on my both of my computers with nvidia cards, but it itsn't working on my computer that uses an Intel video card.

---

### Post by vgrisham on 2009-04-24
[This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I don't see where a GPG key is published for their repo, but it works anyway (although you'll get an error message upon reloading your repositories). Also, you'll need to reboot your system after making the change.

---

### Post by ytimer on 2009-04-24
Switching my video output to X11 seems to fix the problem. However in full screen mode the video is a bit choppy (enough to be annoying).

---

### Post by vgrisham on 2009-04-24
> **ytimer said:**
> Switching my video output to X11 seems to fix the problem. However in full screen mode the video is a bit choppy (enough to be annoying). I have also filed a bug report here:
[https://bugs.launchpad.net/ubuntu/+bug/362087](https://bugs.launchpad.net/ubuntu/+bug/362087)

Everyone who is seeing the issue please post there so the developers know its not an isolated issue. Thanks!

ytimer, see my post above. You can fix it by reverting your intel xorg driver to 2.4.

Also, loading up the bug with "me too" posts is frowned upon on launchpad and it is actually counterproductive (every time someone posts, everybody who is subscribed to the bug will get an e-mail). Those who want an updates on the bug's progress, can just click subscribe on the top right of the bug report, and it will list everyone who is subscribed (which will show that this is not isolated). 

Anyway, the above fix worked great for me. Give it a shot.

---

### Post by Shidian Ou on 2009-04-24
I had this problem too and spent hours working on it only to figure out it was a GRUB problem for me (I have a Windows partition too).  

8.10 was the first time I'd installed Ubuntu so it was a clean install.  When I upgraded to 9.04, it said it wanted to overwrite my menu.lst, but I didn't know if I should let it as I didn't want mess up my Windows line.  I tried looking at the diff option but it was just a mess of text so I just said to keep the original.  That was probably a bad idea.  

I finally decided to forget about the video for a bit and go back and see if I didn't mess anything up with my GRUB choice.  My menu.lst still said "8.10" which I didn't think was a good thing, so I looked at the kernel and init options in the menu.lst vs the ones in /boot and there was my problem, I was still loading 2.6.27 and I should have been loading 2.6.28.  

I changed my menu.lst options to point to the right kernel, rebooted, and viola, my video started working properly again.

---

### Post by ytimer on 2009-04-24
> **vgrisham said:**
> [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I don't see where a GPG key is published for their repo, but it works anyway (although you'll get an error message upon reloading your repositories). Also, you'll need to reboot your system after making the change.

Awesome! This works for me. I'm running Ubuntu on an old Intel machine on the side and that seemed to be the exact problem. Thank you very much!

---

### Post by san_terre on 2009-04-24
Thanks, this worked for me also on my Sony VGN-47TX.  

It also fixed my Ricoh camera (ID 05ca:183a Ricoh Co., Ltd) unless it was just a coincidence. :)

---

### Post by RalphPS on 2009-04-24
I am more than willing to wait for the updates.  If we did not mention the issues here then they may not be aware. ** Please don't talk so loud.**

---

### Post by RalphPS on 2009-04-24
[b]1
[/b]

---

### Post by CRIMPS on 2009-04-25
> **DDM said:**
> Can't really help any, but my X crashes back to gdm when I play videos fullscreen. Also seems to happen when I use the volume keys on my keyboard (I blame the notification thingy). 


Whoa!  I just found this happens to me as well.  Have you seen this reported yet?  I may look through launchpad just to make sure.

---

### Post by Strongman332 on 2009-04-25
i was reading the replace note apparently now you have to :confused: "pay" for proprietary formats in 9.04

[http://www.ubuntu.com/products/whatisubuntu/904features/music/](http://www.ubuntu.com/products/whatisubuntu/904features/music/)

---

### Post by hashan17 on 2009-04-25
Try removing your exsiting versions of VLC by
sudo apt-get remove vlc

then try installing it again then problems will be solved
sudo apt-get install vlc

---

### Post by braigetori on 2009-04-25
> **vgrisham said:**
> [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I don't see where a GPG key is published for their repo, but it works anyway (although you'll get an error message upon reloading your repositories). Also, you'll need to reboot your system after making the change.

oh this is great - i am extremely pleased with the quality of both this operating system and it's users. too bad we can't find the GPG key though... i was getting excited about learning how to use them :)

thanks !

:b

---

### Post by vgrisham on 2009-04-25
> **braigetori said:**
> oh this is great - i am extremely pleased with the quality of both this operating system and it's users. too bad we can't find the GPG key though... i was getting excited about learning how to use them :)

thanks !

:b

You're welcome. GPG keys are very easy to import. When a site posts their GPG key, just click the link, select and copy the text from the section labeled Public Key Block, save the file to a suitable location (I have mine saved in a folder I created and named .keys in my Home directory), then just double click the file and the Import Key program should pick it up. If for some reason it doesn't, you can manually import it from the Software Sources section of the System-->Administration menu.

If you want to try it, the excellent personal finance application kmymoney has a great repo for their software. See [here]("https://launchpad.net/%7Eclaydoh/+archive/ppa") for more info.

---

### Post by dthomsen on 2009-04-25
> **Shidian Ou said:**
> I had this problem too and spent hours working on it only to figure out it was a GRUB problem for me (I have a Windows partition too).  

8.10 was the first time I'd installed Ubuntu so it was a clean install.  When I upgraded to 9.04, it said it wanted to overwrite my menu.lst, but I didn't know if I should let it as I didn't want mess up my Windows line.  I tried looking at the diff option but it was just a mess of text so I just said to keep the original.  That was probably a bad idea.  

I finally decided to forget about the video for a bit and go back and see if I didn't mess anything up with my GRUB choice.  My menu.lst still said "8.10" which I didn't think was a good thing, so I looked at the kernel and init options in the menu.lst vs the ones in /boot and there was my problem, I was still loading 2.6.27 and I should have been loading 2.6.28.  

I changed my menu.lst options to point to the right kernel, rebooted, and viola, my video started working properly again.

Dude! You nailed my issue. I thought it was the intel driver but... It was the fact that I was booting with the old kernel. I multiboot and it was using the GRUB files from my 64 bit Ubuntu. I can see why downgrading the intel driver would "fix" this but I think anyone having this issue needs to make sure GRUB is configured to boot with the correct kernel.

---

### Post by braigetori on 2009-04-28
interesting solution.

i checked my menu.lst and also made the changes you recommended. it made no difference. looks like the only way to make it work is to downgrade the driver.

its great to be able to watch vids again, but the quality is noticeably worse then before upgrading. for example, now VLC only plays in an independent window, and i cannot watch full screen videos on youtube or normal sized videos on vimeo (jerky, slow, etc.)

is there some way to install the driver that was used in 8.10? the quality then was fantastic. what video drivers would you recommend?
thanks for all your support.

:b

---

### Post by enstardavid on 2009-04-28
Hi,

I had the same inability to play .avi, .wmv etc on 9.04 on a Dell Dimension 2400 desktop (so, an older machine) after upgrading from 8.10 to 9.04

It turns out that it was the Intel video driver - and reverting to the '2.4 Driver' that was used with 8.10 solved the issue for me.

This page explains pretty clearly what to do:
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Initially I didn't grasp the comment about GPG keys (which is important!) so it failed the first time I did it - but working through again SLOWLY got it right.

Couple of things I found hard to get first time too - this instruction tells you to add a couple of lines to this file: /etc/apt/sources.list

1 - To do that you locate the file - double click it and a control dialog opens (who'd have guessed), and then add the lines - one at a time - to the dialog.

2 - When you save the key file from the GPG section - save it a something.key  not something.txt   like I did first time round :redface:

... and when you are done, and have rebooted - VIDEO again.

Well - it worked for me.

David

---

### Post by konsty on 2009-04-28
> **vgrisham said:**
> [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I don't see where a GPG key is published for their repo, but it works anyway (although you'll get an error message upon reloading your repositories). Also, you'll need to reboot your system after making the change.

Thanks! worked for me.

---

### Post by maxclimber1w on 2009-04-28
When I try to play HD video, my whole machine crashes and I have to do a hard reboot.

Everything else is working great, including Compiz...

Any ideas about this?

---

### Post by maxclimber1w on 2009-05-01
shameless bump!

---

### Post by vgrisham on 2009-05-01
> **maxclimber1w said:**
> shameless bump!

If you have an Intel video card (older ones it seems), you might want to downgrade your driver. See my post on the previous page. It's easy to take care of.

To find out what video card you have, fire up your terminal and code:
> lspci -vScroll up and look for "VGA Compatible Controller" and note what is immediately after the colon. If it's Intel, you've got an easy fix earlier in the thread.

Again, [here]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") is the link for instructions on how to revert the Jaunty Xorg driver.

---

### Post by maxclimber1w on 2009-05-02
No, I've got an ATI Radeon 2400 HD

---

### Post by mousestalker on 2009-05-02
FWIW, I was merrily playing DVD's in VLC on a fresh install of Jaunty. I installed the recommended Nvidia driver and VLC immediately started refusing to play DVD's. Removing the Nvidia driver and reverting to the OS driver fixed the problem.

What good is a commercial driver if it won't allow anything useful to be done?

People use graphics cards for either playing media or playing games. The Linux game playing is somewhat limited, so most people who use Linux probably use their graphics card for media. And Nvidia has rendered that at least partially futile.

/rant

---

### Post by wordsmyth on 2009-05-07
Another frustrated Ubunbtu 9.04 user - I can play DVDs okay on VLC and Totem, but I cannot play video content on websites. This is a damned nuisance, which I've not encountered in previous releases. is there a simple solution? And if not, PLEASE FIX THIS, GUYS!!! Meantime, it's back to Windows for me ...

---

### Post by sarahlizz3 on 2009-05-07
> **vgrisham said:**
> [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I followed the instructions on that link and it fixed mine, thank you!

---

### Post by alibro on 2009-05-25
I had exactly the same problem with an old Fujitsu Siemens PC with an Intel video chipset. ie all videos tried to play then died. Reverting the Jaunty Xorg intel driver to 2.4    [https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)     fixed the problem for me too. 
I have to say I am very disappointed with Ubuntu 9.04. The reason I was using the onboard video was I had to remove the slimline ATI card which was installed in the PC. As it is an old PC the ATI card was old too and apparently 9.04 is hopeless on an old ATI card. I was always led to believe that Linux is better than Windows on an old PC but now I'm not so sure. 
Just by the way I also had problems getting the sound to work (also Intel chipset) it seems everything was turned down and muted by default?????

---

### Post by xophere on 2009-05-26
changing the video out to the X driver worked for vlc but don't see how to do that in totem  oh well one more reason not to use it.

---

### Post by manusbattersby on 2009-06-03
> **gfe said:**
> I would check Preferences with each player to see which video driver is being used. Both [FONT=Courier New]vlc[/FONT] and [FONT=Courier New]mplayer[/FONT] crash on me unless I'm using the X11 driver (the defaults don't work). This may have nothing to do with your situation, but it's worth a try.


cool..... i had the same problem.... and that just fixed it..

thanks

---

### Post by DeltaHF on 2009-06-05
> **vgrisham said:**
> [This]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4") fixed video playback on my computer with an Intel video card.

I don't see where a GPG key is published for their repo, but it works anyway (although you'll get an error message upon reloading your repositories). Also, you'll need to reboot your system after making the change.
As many others have, I just want to say **thank you** for sharing this link here.  I was working with an older Dell Optiplex 170L with onboard Intel graphics, and this solved the problem of playing WMV files in VLC.  Thanks again!

---

### Post by vgrisham on 2009-06-05
You're welcome. That Ubuntu Wiki is a powerful resource.

---

### Post by Marky-boy on 2009-06-07
I have the same problem, but I'm on 8.10.   I'm on 64-bit, with Nvidia Drivers.

In VLC I tried many of the video output options. Nothing seems to work except playing in ASCII mode. (which is not gonna cut the mustard, I'm afraid)

I paste below the results running VLC from terminal. Highlight in red where it seems to be going wrong.

Any assistance warmly welcomed, as without ability to play videos i might as well go back to windows after using ubuntu exclusively for 2 years.
 

VLC media player 0.9.4 Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.4 Grishenko - (c) 1996-2008 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=x86_64-linux-gnu' '--enable-maintaner-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=1ubuntu3' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-arts' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-x264' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-alsa' '--enable-dv' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[COLOR="Red"][????????] x11 video output error: X11 request 2.0 failed with error code 8:
 BadMatch (invalid parameter attributes)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  2 (X_ChangeWindowAttributes)
  Serial number of failed request:  677
  Current serial number in output stream:  678
Locking assertion failure.  Backtrace:[/COLOR]
#0 /usr/lib/libxcb-xlib.so.0 [0x7f613d67f9fc]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x17) [0x7f613d67fb77]
#2 /usr/lib/libX11.so.6 [0x7f61443f48c0]
#3 /usr/lib/libXrender.so.1(XRenderFreePicture+0x46) [0x7f613e155a26]
#4 /usr/lib/libQtGui.so.4 [0x7f613f73bcfb]
#5 /usr/lib/libQtGui.so.4 [0x7f613f73c680]
#6 /usr/lib/libQtGui.so.4(_ZN7QPixmap5derefEv+0x53) [0x7f613f731fa3]
#7 /usr/lib/libQtGui.so.4(_ZN7QPixmapD2Ev+0x24) [0x7f613f732334]
#8 /usr/lib/libQtGui.so.4 [0x7f613f737193]
#9 /usr/lib/libQtGui.so.4 [0x7f613f73779f]
#10 /usr/lib/libQtGui.so.4 [0x7f613f736e85]
#11 /lib/libc.so.6(exit+0x9d) [0x7f6147c666ad]
#12 /usr/lib/libX11.so.6 [0x7f61443ed5ed]
#13 /usr/lib/vlc/video_output/libglx_plugin.so [0x7f613299b6ea]
#14 /usr/lib/libX11.so.6(_XError+0xf4) [0x7f61443ed784]
#15 /usr/lib/libX11.so.6 [0x7f61443f520f]
#16 /usr/lib/libX11.so.6(_XReply+0x18a) [0x7f61443f55ba]
#17 /usr/lib/libX11.so.6(XInternAtom+0xb2) [0x7f61443d7892]
#18 /usr/lib/libQtGui.so.4 [0x7f613fbf9411]
#19 /usr/lib/libQtGui.so.4 [0x7f613fbf9770]
QWaitCondition: cv destroy failure: 
QWaitCondition: mutex destroy failure:

---

