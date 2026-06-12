---
title: "Playing Xvid for Vista/Windows newbie"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by darussian12 on 2007-05-09
just installed Ubuntu on a new partition after going from being a Mac user and trying YDL alongside Tiger, then bought a PC and been using XP/Vista for the past year and have become sick of using Windows so googled what the easiest flavor of linux was and Ubuntu was the one. After trial and error got my broadcom wireless card to work but the only other thing stopping me from ditching Vista completely is I download a lot of movies and burn them to DVD. The problem is  i can't get my Xvid movies to play. After the clean install of Feisty and i try to open the .avi's ubuntu asks me to download the required codecs and tells me they are restricted and i agree but after the install/download when i click on the file the default program opens then immediately closes. I D/l VLC because it played anything and everything when I used windows but it does the same thing. VLC would open then immediately close.  i searched the forums for Xvid playback and found the sticky for enabling multimedia on Feisty at [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626). the only thing is i am a total retard with linux for the moment and thought just getting my broadcom card to work was a intensive process but opening the sources.list file is only "read only" so i dont even know how to open it with write privileges.  doing what the sticky says through the command line editor still gives me a warning about changing a read only file so my first question is how the heck do i even open it with write privileges.  I just figured letting ubuntu download the required restricted codecs would let me watch the xvid files because im not going to attempt to convert me avi's to dvd when i cant even get them to play on the laptop. im ready to finally delete the windows partition but without getting a successful DVD burned im not ready to. So i guess my question is  since i cant edit the sources.list file, how do i even do that because i thought maybe editing the sources.list file through the Vim command line text editor would do it but it didnt because when i went to install the win32 codecs i got this

alex@alex-laptop:~$ sudo apt-get install libdvdcss2 w32codecs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

please help a rookie.



secondary and totally off topic questions would be i used the synaptics driver on Vista for my mouse because i hated being able to tap the mouse to select items but in system-->prefrences-->mouse there is no option to deselect tapping. thanks and im sure ill be back with more questions in the approriate forums.

---

### Post by mishimasan on 2007-05-09
Oh dear god, I can't believe that no one has replied yet.  I'm in exactly the same shoes as you... well, almost.. I didn't get that far yet.  I gave up after I couldn't play xvid in the movieplayer.

---

### Post by zoexii on 2007-05-09
hit alt+F2
type
gksu gedit /etc/apt/sources.list

when the dialouge appears, type your password,
edit the sources list to suit your needs, save and exit.

In my own experience, I've had no problems playing Xvid with VLC, but if nothing else works, try installing mplayer and using that.

---

### Post by zoexii on 2007-05-09
as for the the trackpad, I recently had the same problem.  Open your xorg.conf file:
alt+F2
gksu gedit /etc/X11/xorg.conf

and look for the input devices section, specifically something like this:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"		"0"
EndSection

The "MaxTapTime" is the option that controlls the tap clicking, when it is followed by a 0 in quotes, the feature is off.  If these lines don't appear, add them to the same section where your other input devices are found, then check the "SeverLayout" section:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

and check to make sure that Synaptics Touchpad is listed.

Also, it is a very good idea to make backups of config files in case something goes wrong.  In this case the command to do that is:
cp /etc/X11/xorg.conf /etc/X11/xorg.backup.conf

---

### Post by darussian12 on 2007-05-09
zoexii, 
thanks for the info, yeah i know VLC will play anything and everything and thats why i used it as my al in one video player on windows, im just having issues with having any of the video players to stay open when i select the video file. mplayer, totem, and VLC all just quit immediately after loading....I did 

> hit alt+F2
type
gksu gedit /etc/apt/sources.list

and then followed the directions on the sticky page to enable multimedia and all the packages unpacked and installed but i still have the same problem, I open with any of the video players and they all immedaitely shut down once launched. what am i doing wrong...is there a log file of some sort i need to post for more clarification and if so where would i get it?

I also added the "MaxTapTime" line and set it to 0 in quotes and i can still tap with my trackpad...do i need to do anything else like restart since i am used ot restarting everytime i do anything in windows...not sure yet how any change i make effects Linux yet. thanks

---

### Post by mishimasan on 2007-05-10
Darussian12.... is there any sources that you can paste into here for me in order to enable the xvid codecs?  (or at least try to encode them)  I have no idea where to get sources from.  Where should I go?

Thanks,

Mish

---

### Post by ninjaprawn on 2007-05-10
if you edit your xorg.conf file, you need to restart X after youve saved. kill X by doing ctrl+alt+backspace.
hopefully that will stop tapping!

for me, to get divx/xvid working in feisty, i just went to add/remove in the applications menu, changed the top right drop down menu to all available, then typed in divx to the search, it then gives all the codecs, tick the package i wanted, and everything plays perfectly!!

---

### Post by mishimasan on 2007-05-10
> **ninjaprawn said:**
> if you edit your xorg.conf file, you need to restart X after youve saved. kill X by doing ctrl+alt+backspace.
hopefully that will stop tapping!

for me, to get divx/xvid working in feisty, i just went to add/remove in the applications menu, changed the top right drop down menu to all available, then typed in divx to the search, it then gives all the codecs, tick the package i wanted, and everything plays perfectly!!

If this works for the codecs, send me ur address - coz I'll send you a cake hrhrhrhr.  Thanks m8, gonna try it when I get home - I gotta use Windows at work coz I'm using the Adobe suite.... Sucks :(

---

### Post by darussian12 on 2007-05-10
> for me, to get divx/xvid working in feisty, i just went to add/remove in the applications menu, changed the top right drop down menu to all available, then typed in divx to the search, it then gives all the codecs, tick the package i wanted, and everything plays perfectly!!

yeah its not of matter of not having the codecs installed because I have done every process I could find on these boards and the Wiki page and terminal says they are installed and what not...its a problem of getting any of my media players tp stay open more then a brief second after launching. If theres some sort of log file made by VLC or mplayer that would help anyone help me, let me know how i find it so I can copy and paste it because Im pretty lost at this point regarding getting any sort of video files to play.

Thanks, and yes the tapping was taken care of after restart because in another thread i needed help getting my SD slot working and they helped my in the appropriate forum.

---

### Post by mishimasan on 2007-05-10
UM.... ok.  I tried what ninjaprawn said earlier, and now I think that I have more or so the same problem as Darussian12 has.... my VLC player refuses to even play the file, it just quickly stops (probably after realising that it's pointless even trying).  The program stays open but the file never plays.  Not even a wink of it.

The file is a copy of the DVD Half Nelson, it's encoded in xvid.  NOTHING wants to play it.  I've installed the unsupported avi codecs like divx and xvid, all the packages that I can find and it still doesn't want to play.

Other videos are ok, like .ogg and .mpeg.  Xvid is being plain stubborn.  Any ideas?

Yours Faithfully,

Mish

---

### Post by darussian12 on 2007-05-11
For me I can open any of the video players by going to Applications--->Sound &Video---> and then selecting the appropriate application and none of them will quit when there is no video file loaded. But once i select a video file or a DVD the opened application, be it Totem, VLC or Mplayer, will close/crash and i get no notice of anything or why.

---

### Post by mishimasan on 2007-05-11
You know, maybe if you can, set up a different version of Linux on another hard drive or partition - like Kubuntu or Fedora and see if the same thing happens.... I'm going to do this on another hard drive with a different OS.  That way I can tell if it is a system setting or a global hardware issue.  But in all honesty, if this only happens with the xvid codec, then... how's that gonna be a hardware issue? :P  Still.... maybe it will work on the other OS - and then you can really compare the settings and see what the issue may be...

---

### Post by RawMustard on 2007-05-11
> **mishimasan said:**
> UM.... ok.  I tried what ninjaprawn said earlier, and now I think that I have more or so the same problem as Darussian12 has.... my VLC player refuses to even play the file, it just quickly stops (probably after realising that it's pointless even trying).  The program stays open but the file never plays.  Not even a wink of it.

The file is a copy of the DVD Half Nelson, it's encoded in xvid.  NOTHING wants to play it.  I've installed the unsupported avi codecs like divx and xvid, all the packages that I can find and it still doesn't want to play.

Other videos are ok, like .ogg and .mpeg.  Xvid is being plain stubborn.  Any ideas?

Yours Faithfully,

Mish
If you've enabled all your repositories then try in a terminal:
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-ffmpeg gstreamer0.8-dvd gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.8-xvid
```

Have you read this guide? [[COLOR="Blue"]_Enabling Multimedia in Feisty (HOW-TO)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=413626")  There's nothing I can't play after following that guide!

I know some of you guys think it's bulldust to have to type commands in a terminal to get stuff working in linux, it's just that it would take us 10 pages to explain to you how to do it from your desktop.  It's much easier from a terminal.  Remember Linux is much more powerful and efficient than windows :)

---

### Post by mishimasan on 2007-05-11
> **RawMustard said:**
> If you've enabled all your repositories then try in a terminal:
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-dbg gstreamer0.10-ffmpeg gstreamer0.8-dvd gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad-multiverse-dbg gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-ugly-multiverse-dbg gstreamer0.8-xvid
```Have you read this guide? [[COLOR=Blue]_Enabling Multimedia in Feisty (HOW-TO)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=413626")  There's nothing I can't play after following that guide!

I know some of you guys think it's bulldust to have to type commands in a terminal to get stuff working in linux, it's just that it would take us 10 pages to explain to you how to do it from your desktop.  It's much easier from a terminal.  Remember Linux is much more powerful and efficient than windows :)

By looking at the thread that you have shown me here, I actually think that this is going to work!  Many thanks in advance, even if it doesn't...

Mish

---

### Post by RawMustard on 2007-05-11
No probs - Let me know how you get on :)

---

### Post by darussian12 on 2007-05-11
i lived by that sticky topic and i did all the commands in it after ubuntu  told me I needed the appropriate codecs and that didnt fix my problem i followed the sticky about multimedia but it made no difference. I dont know if its all the different ways i installed the codecs that are conflicting and causing my media players to crash or if thats even possible because when the first way of Ubuntu telling me i needed the restrcited codecs and installing them did not make my media players work i went to the next way i could find and so on. SO far i have prob done 3 different ways at least of installing the required playback codecs and still in the same boat of no video playback. I know plenty of windows people get overwhelmed by the whole terminal thing but as long as i have clear instructions for what code to copy paste, i honestly dont think its such a difficult thing to be scared off by and I came in expecting to make terminal my best friend before I tried Ubuntu. I just wish i could get my videos to work. Its not just Xvid, it seems to be any video loaded that makes my players crash. Because i finally tried a DVD i burned that worked on Vista and my home DVD players and my media players in linux still close immediately when i load the DVD. Im not sure how adventurous i want to get with partitioning again because all i have is the Vista and the Ubuntu partitions and was happy to just not lose anything on vista after the repartition, and having to do a few different methods of getting my wireless card to work eventually. Not really feeling like going through that again until i get the hang of Linux a little better. Because once i get everything working like I like and am able to burn a sucessful DVD, i would like to make my whole HD linux and be done with Vista and just follow all my posts on here to get everything functioning after a clean install of Ubuntu.

---

### Post by mishimasan on 2007-05-11
Ok.  It didn't work.....

ERROR:

Could not determine type of stream.

Damn.... this is starting to get irritating now - my girlfriend has been hassling me about watching this movie for a week almost lol.

Let's go back to the drawing board on this one please....

---

### Post by darussian12 on 2007-05-11
here if this helps anyone help me get to the root of my problem, mplayer is the only program to give me any sort of message.... the screenshot is uploaded and also the screenshot of the properties of the video file to show thats its not some uncommon file format i am trying to play but a run of the mill xvid...but the same thing happens for other video...just gets a little frustrating when i cant get any video players to play a common file format because this is about the only problem ive had in migrating to Ubuntu. anyone?

---

### Post by RawMustard on 2007-05-11
@darussian12

What video card and drivers are you using, do you know?

Have you tried right clicking in an mplayer window and selecting preferences, then on the video tab select xv X11/Xv and clicking OK
[ATTACH]32385[/ATTACH]

What I can see from your screen shots, is that Nautilus knows and is recognising the files but for some reason your chosen player is having difficulty playing them.  Nautilus wouldn't generate thumbnails if you didn't have the correct codecs installed.

---

### Post by darussian12 on 2007-05-12
the intel 915 something or other. I posted the screenshot from device manager to be more specific. I figure the codecs would be installed since ive tried every way i could find for installing them but just no luck with any video player to play them. It sucks having to boot up Vista just to convert all my video files to DVD, never mind that i left barely enough HD space free on that partition just to get by since i thought i would be able to delete it pretty quickly. Any other suggestions?

kind of on a semi related note...when trying to burn a audio CD  using banshee all the burn options range from 18-73x when I am using a CD-RW which can burn at 4x max. And when after i selected the lowest possible speed of 18x even though not correct the mp3 files converted but the burning progress bar just kep bouncung back and forth and the CD was def not being written to or any sort of acitvity with it. WHAT THE HECK?...or to go along with me not being able to watch video files, the burning abilty of CD/DVD burner doesnt function either? prob more appropriate for hardware thread but thought i would throw it in since im having little luck with the whole video players crashing thing.

---

### Post by RawMustard on 2007-05-12
Have you tried launching mplayer or totem from a terminal window and then open a video file from there, this will tell you more what's happening.  I don't know about your cd burning problem, I only use Nautilus for my burning needs and it seems to work well.

---

### Post by darussian12 on 2007-05-12
all ive done in terminal is copy and paste codes that were given to me, so havent mastered opening files with my preferred player in terminal. other then typing in mplayer, i dont know what command opens a specific file.

---

### Post by darussian12 on 2007-05-13
so anyone have any idea...im ready to get rid of vista or ubuntu from my partition and so far when i cant do basic stuff like watch a simple video file ubuntu seems like an expirament gone wrong. i have been able to get help and answeres to my other issues like hardware and general info about how Linux works in the right threads but somehow this whole getting video files to play seems to be a problem, I dont get how there isnt anyone that can help me solve it. im going from the first steps to the end of making ubuntu a windows replacement and when i cant get past the baby step of getting a simple video to play,  I honestly dont know what else I can do?

---

### Post by RomeReactor on 2007-05-13
Hi. To open MPlayer from the terminal, just type:

```
gmplayer
```

and right click on it, select "Open", then "Play File" and choose a video from the dialog; when it crashes, see what messages it leaves in the terminal. Same goes for totem:

```
totem
```

with the difference that you can drag and drop files to it after it opens. Also, do you have totem-gstreamer or totem-xine? I recommend you give totem-xine a try if you haven't already:

```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libxinerama1
```

---

### Post by mishimasan on 2007-05-14
Darussian...... have you tried downloading the file again?  Perhaps it is a corrupted file.  I downloaded mine again and now it seems to be working.  Since everything else was playing in the player before, I know that this was always a possible cause.

Thanks for the help guys.

---

### Post by swudee on 2007-05-14
Hi 

I had a similar problem with some codecs a while back.
The cause The files I was trying to play back were corrupted!!!
Actually there was nothing wrong with VLC, Totem or Kaffeine.

It might pay to check:)

---

### Post by darussian12 on 2007-05-15
i doubt it can be corrupted files, because i have tried multiple files ive downloaded plus a burned DVD and all the files play with VLC on my vista boot after installing a program to access my linux partition from vista plus the DVD plays fine in any home DVD player. will give  terminal a try and report back the messages. thanks for the additional suggestions.

heres the message I got in terminal. hopefully this finally helpes someone point me in the right direction

> alex@alex-laptop:~$ gmplayer
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.50GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

Playing /home/alex/Videos/The Messengers.avi.
AVI file format detected.
VIDEO:  [XVID]  608x320  12bpp  23.976 fps  937.9 kbps (114.5 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.2 (build 2540/release)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.

heres the error message for a different file, seems to have a different message for the same codec though...

> alex@alex-laptop:~$ gmplayer
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.50GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

Playing /home/alex/Videos/The Shield S06E10.avi.
AVI file format detected.
VIDEO:  [XVID]  576x432  24bpp  23.976 fps  1396.0 kbps (170.4 kbyte/s)
Clip info:
 Software: MEncoder dev-SVN-rUNKNOWN-4.1.2
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.

heres the VLC terminal log for a different video file

> alex@alex-laptop:~$ vlc
VLC media player 0.8.6 Janus
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

** (.:6653): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
pure virtual method called
alex@alex-laptop:~$ 


---

### Post by RomeReactor on 2007-05-15
> /home/alex/.themes/Green Glass/gtk-2.0/gtkrc:54: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:55: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/alex/.themes/Green Glass/gtk-2.0/gtkrc:56: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

It looks to me that, since this message appears using either VLC or Mplayer, maybe the theme has something to do with it; if you change to the Human theme (or another), does the problem persist? I think you have the necessary codecs installed as someone else suggested, since the thumbnails *do* show up on Nautilus.

---

### Post by mishimasan on 2007-05-15
> **RomeReactor said:**
> It looks to me that, since this message appears using either VLC or Mplayer, maybe the theme has something to do with it; if you change to the Human theme (or another), does the problem persist? I think you have the necessary codecs installed as someone else suggested, since the thumbnails *do* show up on Nautilus.

I agree.... looks like a theme issue here.

---

### Post by darussian12 on 2007-05-15
after switching to the mist theme, i dont get any of the theme conflicting messages but everything else is still there...

alex@alex-laptop:~$ gmplayer
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Celeron(R) M processor         1.50GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/alex/Videos/The Shield S06E10.avi.
AVI file format detected.
VIDEO:  [XVID]  576x432  24bpp  23.976 fps  1396.0 kbps (170.4 kbyte/s)
Clip info:
 Software: MEncoder dev-SVN-rUNKNOWN-4.1.2
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)
alex@alex-laptop:~$

---

### Post by mishimasan on 2007-05-15
They're both saying that they're having trouble locating the file - that there is "no such file or directory".  This is perhaps the real problem?

Have you tried copying and pasting them into a different directory?  When you downloaded them, were there any problems?

---

### Post by darussian12 on 2007-05-15
related question, ive been asking another linux pro about my issues and his suggestion is...

> In my very humble opinion, it sounds to me like conflicting codecs (Xvid can be very flakey). It's not uncommon to have remove all the old codecs and reinstall just the ones you need. Here's an ubuntu forum web page with many comments, tips and links dealing with installing codecs and codec problems: 

[http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278) 

T Hope this helps

checking out that thread it looks pretty dated with the most recent post over 6 months ago and the recent version of Ubuntu coming out less then a month ago. how would I go about doing a clean install of the codecs other then searching for Xvid and the win 32 and libccss in synaptic to remove them. would that completely remove them and what is the ideal way of installing proprietary playback. the thread he pointed me to or the thread i posted earlier thats a sticky on here about enabling multimedia in Fesity? Im tempted to give this one more go with a clean install of Ubuntu and start from scratch but i wanted to get my video playback straightened out first, but it seems like my players refuse to cooperate with my current set up. any ideas before i start backing up stuff and doing a reainstall from the start?

---

### Post by darussian12 on 2007-05-15
> They're both saying that they're having trouble locating the file - that there is "no such file or directory". This is perhaps the real problem?

Have you tried copying and pasting them into a different directory? When you downloaded them, were there any problems?

I used Azuerus to D/L them and recieved no problems when Azuerus checks the files after d/l completes. and the desktop is my default save directory and when the files finish I relocate them to my videos folder in my home directory i created. I have tried playing them from the desktop and from the home/videos directory with the same result of crashing player each time.

*edit. last night i tried to open one of the files in avidemux and it would load it and i could play it through there with audio/video fine, but that isnt an ideal way for me to watch video files since its meant for video conversion. I installed it as one of the progrmams i want to try for DVD conversion but havent tried to encode until i can playback the files in Linux, so wouldnt that suggest that the actual file exists and can be found by Ubuntu yet somehow my video players dont want to play them?

---

### Post by RomeReactor on 2007-05-15
> **darussian12 said:**
> ... last night i tried to open one of the files in avidemux and it would load it and i could play it through there with audio/video fine, but that isnt an ideal way for me to watch video files since its meant for video conversion... yet somehow my video players dont want to play them?

It looks like something is wrong with your video players' configuration. You could try uninstalling them from Synaptic (choose "Completely remove, including configuration files" and afterwards deleting the hidden folders the corresponding programs make on your home folder (**.mplayer**, in the case of vlc i suppose it's **.vlc**) and installing them again. Does Totem still have the same problem?

---

### Post by darussian12 on 2007-05-15
any of the video programs i have tried, all shut down immediately after opening. If I am lucky and try to play a video file that has audio at the very beginning i might hear a split second of it, but thats it.

*edit. found and deleted the VLC and Mplayer hidden files but dont see anything labeled "totem" or related. I see a Xine hidden folder but wasnt sure if that was the "totem-Xine" or Xine itself is something seperate so I left it be for now.

---

### Post by darussian12 on 2007-05-16
after reinstalling Mplayer and VLC through synaptic, i get the exact same messages as posted earlier in Terminal with none of the selected video files willing to be played by the programs.....ughhhh

---

### Post by mishimasan on 2007-05-16
It may be worth looking at this from all angles.

You say that it's the xvid codec that is not playing, and that is the only codec yes?  Can we try downloading another xvid encoded file?

And possibly downloading the SAME file, but renamed?  I want to see if the problem is inherent to the codec or the file... or neither.  It should only take one night to download the corresponding files :)  Then we can see what happens.

---

### Post by darussian12 on 2007-05-16
when i began this thread, i had only tired playing Xvid videos at the time. But since none of the Xvid files would play i tried a home made DVD that works on standalone players and under Vista, but it causes the same result with any of the programs I tried. I have kept on downloading Xvid encoded files but have had to watch them under vista till I get this worked out eventually, hopefully!

---

### Post by darussian12 on 2007-05-16
wooo...great news. I got tired of trying all sorts of things with no happy results so I decided to screw it and went for a clean install and followed the instructions for the "enabling multimedia" sticky and all is well now. I can play all the XVID files my heart desires. I guess with all the different ways I had tried to install them before, because i began installing the restricted stuff with the wiki instaruction and so on and tried every way i could find under google, but I guess if i had just found the sticky first and gone with that I would have saved myself a whole lot of hassle. And now that i have the other threads i started for help i have an easy refrence so set up my mouse and SD card reader. now i just have to figure out which method i used to get my broadcom 4318 card working because that was a royal pain going through a half dozen methods before finding one randomly that worked and I cant remember off the top of my head what method I used. thanks everyone again

---

### Post by mishimasan on 2007-05-16
> **darussian12 said:**
> wooo...great news. I got tired of trying all sorts of things with no happy results so I decided to screw it and went for a clean install and followed the instructions for the "enabling multimedia" sticky and all is well now. I can play all the XVID files my heart desires. I guess with all the different ways I had tried to install them before, because i began installing the restricted stuff with the wiki instaruction and so on and tried every way i could find under google, but I guess if i had just found the sticky first and gone with that I would have saved myself a whole lot of hassle. And now that i have the other threads i started for help i have an easy refrence so set up my mouse and SD card reader. now i just have to figure out which method i used to get my broadcom 4318 card working because that was a royal pain going through a half dozen methods before finding one randomly that worked and I cant remember off the top of my head what method I used. thanks everyone again

Glad to hear it dude... believe me, I was in the same boat as you when I realised that my movie wouldn't play because it was corrupt. The world of computers ey.

P.S.  That's why I bookmark every page that helps me for something that I've been trying to crack for ages.

---

### Post by darussian12 on 2007-05-16
bookmarks wouldnt have done me much when i completely wiped the paritions and did a clean install of ubuntu...but i got even the wireless card to go now....quick question to close out this thread at least for me. Once i get a successful DVD burned, is there a proper way to go about deleting the dual boot aspect of my laptop and getting rid of VISTA and just expanding my /home partition into the free space. Is there any certain lunix way of doing it because any time ive messed with paritions ive gone in expecting stuff to be lost so I back up stuff and used to the winows way or managing the disks I think i could expand my OS parition into available free space. just wanting to know.

---

### Post by darussian12 on 2007-05-16
i spoke way too soon....because i tried playing the Xvid files after a clean install and enabling multimedia and all was good and had me excited. then most of the day i have been messing with themes and window managers like compiz and beryl and got my OS to looks great, but now when i try to play the video files again the exact same thing is happening like before. the players crash immediately. Is there some sort of conflict with beryl that I do not know. the terminal log is a little different from before but not much. here is the copy and paste version
> 
alex@alex-laptop:~$ vlc
VLC media player 0.8.6 Janus
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84
pure virtual method called
terminate called without an active exception
Aborted (core dumped)


all that catches my eye is the insufficient resources text and that was there in the previous issues I had. Before i was running the compiz manager and this install of ubuntu i have both installed but ussing "beryl manager" to designate Beryl as my window manager and decorator. how could i have "insufficient resources when Linux takes up way less the Vista ever could with all the crap it runs in the background and i could do multiple things like running resource hog azurues and play video file at the same time. i really need to get to the bottom of this. my laptop isnt some state of the art POS but a 1.5 Ghz celeron junk inside with only 500mb Ram. i have attached a screenshot of the resource monitor and by the looks of it I am barely using any processing power but using a a lot of my RAM, when all i have open is Opera, GAIM and whatever runs in the background for Beryl/Emerald ughhhhhh...what next

*edit.
disabled and deleted everything to do with Beryl and tried running compiz effects instead and got the same result of crashing players. Then only disable compiz and my my CPU usage went to single digits and RAM to the low 50's % but was able to play my videos. So is there any way I am going to be able to use the eye candy of Linux and still able to play my video. As in it is a conflict error of some sorts where the window managers cause a conflict with my video playback or does the 10% difference in RAM used with the eye candy on make me SOL on playing video files at the same time? i guess i just dont see how that little of difference in resources used causes my video players to crash.

---

### Post by mishimasan on 2007-05-17
VERY strange my friend.  Very strange.....

Well - at least we know that the problem occurs when installing themes.... now all we gotta do is fish it out of there - and I'm no Linux whizz so I'll wait for the rest of the dudes to get on here before saying anything else.  Seems wierd though, that it would be a resources issue - I mean, why NOT play the videos?  They aren't exactly demanding, unless you're talking HD 960p+.....

---

### Post by darussian12 on 2007-05-17
no its none of the high def codecs by any means just plain ole Xvid, in the  range of 720x480 depending on source and if widescreen or not. I even tried activating compiz while a video was playing and the player immediatey crashed after checking the "enable GL effects" or whatever that option is. Wish i could get to the bottom of it or someone help me get to it

---

### Post by mishimasan on 2007-05-17
> **darussian12 said:**
> no its none of the high def codecs by any means just plain ole Xvid, in the  range of 720x480 depending on source and if widescreen or not. I even tried activating compiz while a video was playing and the player immediatey crashed after checking the "enable GL effects" or whatever that option is. Wish i could get to the bottom of it or someone help me get to it

Am I right in assuming GL means "Open GL" and that, perhaps Open GL is having an issue with your video playback?

---

### Post by darussian12 on 2007-05-17
yeah, its the compiuz manager installed on my ubuntu. in the window title it says something about Compiz Prefrences. but when i had beryl manager to manage my beryl settings and using emerald themer as window decorator/manager the players still crashed. I just uninstalled everything with beryl cause i didnt know how to stop it, only to switch between the different managers, ie...compiz, beryl, and the generic gome. I only know how to deactivate compiz hence why its all still installed and deactivated.anyone know how to fix my window manager conflicts with my video players?

*attached what i use as the COMPIZ manager but now has to be deactivated to play any video.

---

### Post by darussian12 on 2007-05-17
great news....i found what should hopefully be the final solution and able to use beryl/compiz. i seache for beryl  on this website and came across this thread
[http://ubuntuforums.org/showthread.php?t=419742&highlight=beryl](http://ubuntuforums.org/showthread.php?t=419742&highlight=beryl)

and tried the>  It's to do with the default video output for gstreamer, doesn't seem to autodetect properly through beryl sometimes. You may be able to fix it using the gstreamer config tool, run the command (Alt+f2): gstreamer-properties
In the video tab, change the default output plugin. I fixed this issue on my laptop by using X Window System (No Xv)

I also have an intel graphics card, anyone suppose this is a factor?

and it after enabling compiz after applying what the quote says i was able to play my videos. then i installed everything to do with beryl from synaptic and used emerald themer through beryl manager and my videos still played. thanks to STEX a million times for helping me. Im guessing its a problem with the whole inegrated intel graphics thing because the other posters on the thread had the intel crap, maybe not the exact same but intel inegrated BS but hey its cheap. hopefully future migrators will be able to find this thread useful since i used Xvid plenty of times in my posts so hopefully they can go to that thread or the quote here. im so happy, i get the best of everything now, because i knew it couldnt be a resource issue even with my RAM somehow being used a ton, but I wonder what the deal is?.

* sidetrack question....my RAM is being used an ungodly amount, is it really beryl/compiz because even with them off I use over 50%. I thought linux was pretty lightweight. on the other hand i have seen anything from making my swap space from double the ram if less then 500mb to equal the ram if over 500mb. i went overboard or whatever and set it to 1.4 for whatever reason yet even when i was doing video conversion last night, i never used more then 40 some odd MB of swap. did i go overkill y giving more then a few hundred MB or am i missing out on how to utilize swap?  thanks everyone for everything and getting me to become a seasoned Linux user. I knew it was going to be troublesome to being but was told there was an enourmous amt of documentation online to help even the most retarded so i figured I was a little smarted then "retard" and gave it a ago and so far I like what i see!

---

### Post by mishimasan on 2007-05-17
Lol... good to see you've finally cracked it.  I'm sat here scratching my head for various reasons...... 

Add me if you would to your messenger program, my contact is [email]clamped@hotmail.com[/email].

I'd like it if we stayed in contact since I'm trying desperately to get Linux user contacts on my list for support :P

See you,

MishimaSan

---

### Post by darussian12 on 2007-05-17
will add....last question for me in this thread to lose it out in my case. Am i better off asking questions about the whole compiz/beryl conflict n this thread or start a new one...dont want to begin a new one for no reason but I have absolutely seen no one that can answer my compiz/beryl questions here and had to do my own solving through the process of elimination of suggestions here. Mish you will be my new best friend when it comes to Linux because you seem pretty new at this and if you can solve a problem I have, then i know i can and hope i can do the same. Go ROOKIES. hope I can hellp you out at some point. I dont feel great giving out my AIM/MAN on a message board but send me a PM if you want a newbies contact info to exchange info with because I will be more then happy to giv eout my AIM/Email that way

---

### Post by m0uco on 2007-05-17
I was having the same problem, and once I ran the gstreamer-properties and made sure I had totem-gstreamer (plus all the codecs mentioned on this thread) I was finally able to get my videos running again... Thanks y'all!

---

