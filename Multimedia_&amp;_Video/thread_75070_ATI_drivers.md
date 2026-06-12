---
title: "ATI drivers"
date: 2005-10-13
forum: Multimedia &amp; Video
---

### Post by SilverTab on 2005-10-13
Ok I know some people were able to get the ATI drivers to work in Breezy...

anyone can share how they did it?? I keep seeing partial answers but nothing definitive....

I tried most of the how-tos and nothing did it....

---

### Post by KingBahamut on 2005-10-13
Can you list out what you have tried first, before we go into a long spiel of how to do it?

---

### Post by SilverTab on 2005-10-13
First, I tried the official how-to (that worked in hoary):
([http://www.ubuntuforums.org/showthread.php?t=65276](http://www.ubuntuforums.org/showthread.php?t=65276) )

problem is that the link to the driver (on ATI's website) doesn't work anymore, and the new versions cant be installed...(everyone who tried them got the same error:
dpkg: error processing fglrx-6-8-0_8.18.6-2_i386.deb (--install):
 unable to create `./usr/X11R6/lib/libGL.so.1.2': No such file or directory
 dpkg-deb: subprocess paste killed by signal (Broken pipe)
 Errors were encountered while processing:
 fglrx-6-8-0_8.18.6-2_i386.deb)

Next, I tried installing via synaptic...and running fglrxconfig... still didnt work...

---

### Post by KingBahamut on 2005-10-13
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=27)

link still works , you can grab the ATI installer and it will generate a deb for you as well.

---

### Post by SilverTab on 2005-10-13
I downloaded the xorg 6.8 drivers (the RPM)

then I used alien to generate the .deb package...and when I tried to dpkg it I got the error I pasted above (and so did 3-4 other person who tried it)

---

### Post by dcarpenter on 2005-10-13
There is actually a very easy way to do it.. open up synaptic and search for fglrx... install xorg-driver-fglrx.  Next you want to open up a terminal and:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (incase u mess up)

sudo gedit /etc/X11/xorg.conf

find the device section.. you should see  driver     "ati"
make this line say      driver     "fglrx"
restart x, or simply restart your computer and 3d acceleration should be working properly. 

to test this, type fglrxinfo into a terminal and the output should be something like this:
  display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

---

### Post by bytter on 2005-10-13
I think he wants the 8.18.6 instead of the 8.16.20 that comes with breezy.

---

### Post by dcarpenter on 2005-10-13
oh sorry :(

---

### Post by eMuNiX on 2005-10-13
[QUOTE=dcarpenter]There is actually a very easy way to do it.. open up synaptic and search for fglrx... install xorg-driver-fglrx.  Next you want to open up a terminal and:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (incase u mess up)

sudo gedit /etc/X11/xorg.conf

find the device section.. you should see  driver     "ati"
make this line say      driver     "fglrx"
restart x, or simply restart your computer and 3d acceleration should be working properly. 

to test this, type fglrxinfo into a terminal and the output should be something like this:
  display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)[/QUOTE]

I did similar to dcarpenter suggests above but using the official ATi installer and latest rpm driver from the ATi site, worked a treat for me.

---

### Post by eMuNiX on 2005-10-13
[QUOTE=dcarpenter]There is actually a very easy way to do it.. open up synaptic and search for fglrx... install xorg-driver-fglrx.  Next you want to open up a terminal and:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (incase u mess up)

sudo gedit /etc/X11/xorg.conf

find the device section.. you should see  driver     "ati"
make this line say      driver     "fglrx"
restart x, or simply restart your computer and 3d acceleration should be working properly. 

to test this, type fglrxinfo into a terminal and the output should be something like this:
  display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)[/QUOTE]

I did similar to dcarpenter suggests above but using the official ATi installer and latest rpm driver from the ATi site, worked a treat for me.

---

### Post by flargen on 2005-10-13
Mine worked first time with the new ATI installer thing with 8.18.6. I tried generating .debs, but that was a pain to install all of them and then manually make a kernel module. So I stuck to the automatic install, and all is great. I didn't have to edit my xorg.conf file, because it was already configured with an fglrx section from before.

I believe that the 8.18.6 drivers come with a utility called aticonfig which can create an fglrx section in your xorg.conf, add resolutions, etc etc. This might help.

---

### Post by SilverTab on 2005-10-13
[QUOTE=eMuNiX]I did similar to dcarpenter suggests above but using the official ATi installer and latest rpm driver from the ATi site, worked a treat for me.[/QUOTE]


ok so you downloaded the 59mb ATI driver installer (Version: 8.18.6), run it, and, edit xorg.conf and replace 'ati' with fglrx ??? and that did the trick??

---

### Post by SilverTab on 2005-10-13
BTW thanks to everyone trying to help! :)
really appreciated!

---

### Post by dcarpenter on 2005-10-13
[QUOTE=SilverTab]BTW thanks to everyone trying to help! :)
really appreciated![/QUOTE]

No problem mate, thats what we are here for :cool: 

Let us know when you get it all worked out.

---

### Post by cbudden on 2005-10-13
Only thing is that you will not be able to use hibernate because after resuming the screen becomes messed up and you cannot do anything.

---

### Post by SilverTab on 2005-10-13
mmm weird problem:

I'm trying to download the ATI Drivers installer (the run script)..

and firefox keeps opening it as a text file....
there's no way I can download it!  (I cant right-click save as, since the "link" to download it is an "Accept" button and obviously I cant right-click it...)

Cant copy/paste the url eighter since it requires a Secure connection (https)...

I tried with other browsers...didnt work :(

---

### Post by eMuNiX on 2005-10-13
[QUOTE=SilverTab]ok so you downloaded the 59mb ATI driver installer (Version: 8.18.6), run it, and, edit xorg.conf and replace 'ati' with fglrx ??? and that did the trick??[/QUOTE]
Yes after I rebooted I had 3D up and running, restarting X would have worked too :rolleyes:

---

### Post by eMuNiX on 2005-10-13
[QUOTE=cbudden]Only thing is that you will not be able to use hibernate because after resuming the screen becomes messed up and you cannot do anything.[/QUOTE]
Do you find that the screen gets messed up when you switch users too?

---

### Post by cbudden on 2005-10-13
Have not tried that eMuNiX but i will now.

---

### Post by dcarpenter on 2005-10-13
SilverTab.. see if this works :)

[https://a248.e.akamai.net/f/674/9448/1m/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.18.6-i386.run](https://a248.e.akamai.net/f/674/9448/1m/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.18.6-i386.run)

right click, save-as... have fun!

EDIT: Sorry ignore this link, it doesnt work for some reason... ATI really messed up big time with this, there doesnt seem to be a way to download it in firefox... have you tried wget from a terminal?

---

### Post by ShiftyPowers on 2005-10-13
I got this working fine with the installer from ATI for some reason.  I'm not going to ask any questions but it does work :p 

BTW, these new drivers fixed the widescreen problem I was having above 1024x768.  I am now running 1280x720 to my Optoma H30 projector

---

### Post by SilverTab on 2005-10-13
[QUOTE=ShiftyPowers]I got this working fine with the installer from ATI for some reason.  I'm not going to ask any questions but it does work :p 

BTW, these new drivers fixed the widescreen problem I was having above 1024x768.  I am now running 1280x720 to my Optoma H30 projector[/QUOTE]


you downloaded the 59mb version?? It keeps opening as text for me :(

I even tried in windows with IE and FF *shrugggs* :confused:

---

### Post by Amaranth on 2005-10-13
So, let me make sure I'm understanding you: right clicking on [this link](https://a248.e.akamai.net/f/674/9448/1m/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.18.6-i386.run?) and choosing Save Link As doesn't work?

**Edit:** Ack, I guess not.... ATI has really fscked this one up.

---

### Post by SilverTab on 2005-10-13
[QUOTE=Amaranth]So, let me make sure I'm understanding you: right clicking on [this link](https://a248.e.akamai.net/f/674/9448/1m/dlmdownloads.ati.com/drivers/linux/ati-driver-installer-8.18.6-i386.run?) and choosing Save Link As doesn't work?[/QUOTE]


sure it works, but if I run it I get to the ATI page, saying:
 Unauthorized download 
We're sorry, but this download request cannot be authorized. As an option, you may visit any of the pages below for information about ATI services and products:

---

### Post by SilverTab on 2005-10-13
probably an SSL Authorization problem...you need to download it from the ATI site since you need to be in a SSL Session to have a valid download...

problem is, I can't download it form ATI's website because it opens it as text..(a freaking huge text file actually)

---

### Post by Amaranth on 2005-10-13
[QUOTE=SilverTab]probably an SSL Authorization problem...you need to download it from the ATI site since you need to be in a SSL Session to have a valid download...

problem is, I can't download it form ATI's website because it opens it as text..(a freaking huge text file actually)[/QUOTE]
Actually the problem is wget needs to send a referer otherwise it thinks you're a leech. I can't remember the syntax for that though.

---

### Post by SilverTab on 2005-10-13
[QUOTE=Amaranth]Actually the problem is wget needs to send a referer otherwise it thinks you're a leech. I can't remember the syntax for that though.[/QUOTE]

actually I dont even get the "leech" page from ATI's website....

when I right-click save as  the link you gave me, it saves it as an html page....
(/home/silvertab/Desktop/ati-driver-installer-8.18.6-i386.run.html)

that html page is telling me the unauthorized download access error...


hence why I thought it was an SSL problem... (the link is an https link)

---

### Post by ShiftyPowers on 2005-10-13
[QUOTE=SilverTab]you downloaded the 59mb version?? It keeps opening as text for me :(

I even tried in windows with IE and FF *shrugggs* :confused:[/QUOTE]
what you can do if it downloads as text, which it did for me, is just do a save page as.... and it will give you the option to save the HTML page as a file with the correct name ending in .run

---

### Post by SilverTab on 2005-10-13
[QUOTE=ShiftyPowers]what you can do if it downloads as text, which it did for me, is just do a save page as.... and it will give you the option to save the HTML page as a file with the correct name ending in .run[/QUOTE]


wow, I should've thought about that earlier! LOL

Thanks for the tip! I'm giving it a try right now and i'll report back! (the ATI site is painfully slow right now)

---

### Post by Olav on 2005-10-13
[QUOTE=SilverTab](the ATI site is painfully slow right now)[/QUOTE]
Aha. So that's **you** who's keeping their server occupied. Well, that's okay. Sure. Take your time. I'll wait...

/me drumming tabletop impatiently with fingertips
:p ;)

---

### Post by dcarpenter on 2005-10-13
The ATI server was getting hammered earlier due to the release of the 5.10 catalystis for windows i think... kept getting service unavailable messages.

---

### Post by Olav on 2005-10-13
Got it. Once the connection was available it was not so bad - 80 kB/s

---

### Post by SilverTab on 2005-10-13
I opened it as text (well firefox did it by default)...I saved it on the desktop, now its there, but the first line is
<http> blabla....

so it is displayed as a text document...I tried to edit it, to remove the first line, and I was told that I cant edit a binary file, even though I set the permisions ro RW-RW-RW, and unchecked "Executable"...I still cant edit the damn thing...

wow, I wonder if im ever gonna get this to work...

---

### Post by Olav on 2005-10-13
[QUOTE=SilverTab]wow, I wonder if im ever gonna get this to work...[/QUOTE]
Just wait a minute, I know something that is going to work.

---

### Post by SilverTab on 2005-10-13
[QUOTE=Olav]Just wait a minute, I know something that is going to work.[/QUOTE]

*waiting patiently with my fingers crossed*


I tried everything LOL installing different text editors...I tried in konqueror, firefox, nothing will do :(....

no way I can get this damn installer!

---

### Post by SilverTab on 2005-10-13
wait! I tried with opera! it asked me to save it to the desktop! Now its downloading! Cant wait to try it...

if it works, I promise to use opera more LOL

---

### Post by drogoh on 2005-10-13
[QUOTE=SilverTab]*waiting patiently with my fingers crossed*


I tried everything LOL installing different text editors...I tried in konqueror, firefox, nothing will do :(....

no way I can get this damn installer![/QUOTE]

It isn't "kosher" but: [http://www.stanchina.net/~flavio/debian/fglrx-installer.html](http://www.stanchina.net/~flavio/debian/fglrx-installer.html)

He makes debs of the fglrx driver..

---

### Post by SilverTab on 2005-10-13
I might have to try it....


I installed the ATI drivers, I edited xorg.conf and changed the driver from ATI to fglrx and I still get extremely poor results in glxgears (and I get bash: fglrxinfo: command not found   when I try to run fglrxinfo)....

:( :( :(

---

### Post by Olav on 2005-10-13
[QUOTE=SilverTab]wait! I tried with opera! it asked me to save it to the desktop! Now its downloading! Cant wait to try it...

if it works, I promise to use opera more LOL[/QUOTE]
Ah, so you don't need me anymore? Suit yourself, buddy ;)
I was just uploading to my webspace on my ISP's server, cancelled that.

What I did (using plain Firefox) to fetch the file was just clicking the "accept" button at ATI's license blahblah, then when it started to fill the browser window with the file hit Cancel. Then chose "Save as" from the File menu, it started downloading from the beginning of the file again - and saving it actually.

All this because ATI can' t be bothered to send a proper Content-type header with their crap. Oh well. :-({|=

---

### Post by drogoh on 2005-10-13
[QUOTE=SilverTab]I might have to try it....


I installed the ATI drivers, I edited xorg.conf and changed the driver from ATI to fglrx and I still get extremely poor results in glxgears (and I get bash: fglrxinfo: command not found   when I try to run fglrxinfo)....

:( :( :([/QUOTE]

Regenerate the entire xorg.conf by 'sudo dpkg-reconfigure xserver-xorg'.  I had to do that with my X600.

As far as fglrxinfo, it's in some directory that isn't in your $PATH (I think, not sure, would have to check it out at home but I get off at midnight)  Do 'find /usr -name fglrxinfo' in a term and it should find it, if it exists.

---

### Post by SilverTab on 2005-10-13
dpkg-reconfigure: xserver-org is not installed



ok I think I really messed things up...no idea how since the only thing I did was trying to install ATI's official installer on a clean kubuntu install...

---

### Post by drogoh on 2005-10-13
[QUOTE=SilverTab]dpkg-reconfigure: xserver-org is not installed



ok I think I really messed things up...no idea how since the only thing I did was trying to install ATI's official installer on a clean kubuntu install...[/QUOTE]

Look at your package again, it's xserver-**xorg**

---

### Post by Olav on 2005-10-13
The ATI installer is driving me mad too (not that you'd need do much...).

I told it specifically to generate a .deb file. So I got error messages of missing utilities. Installed all of those through Synaptic. Finally the installer is satisfied, and says it has made my package. But the package is nowhere to be found. I feel cheated somehow...

---

### Post by SilverTab on 2005-10-13
I reconfigured the xserver-xorg and still:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)



seems like nothing will do the trick

---

### Post by SilverTab on 2005-10-13
Olav: Any luck?

---

### Post by dcarpenter on 2005-10-13
Sorry but I still dont know why you are wanting to install the ATI driver from the site and not just use the synaptic package?  Were there any substantial performance increases or bug fixes with the newest release?

---

### Post by mlomker on 2005-10-13
[QUOTE=dcarpenter]The ATI server was getting hammered earlier due to the release of the 5.10 catalystis for windows i think... kept getting service unavailable messages.[/QUOTE]

They also released the 8.18.6 version of their linux drivers today.  I haven't had much luck getting them to work on amd64 Breezy.  The built-in 8.16.20 drivers work fine, though, and I've put a how-to into the video & sound forum.

---

### Post by bytter on 2005-10-13
[QUOTE=dcarpenter]Sorry but I still dont know why you are wanting to install the ATI driver from the site and not just use the synaptic package?  Were there any substantial performance increases or bug fixes with the newest release?[/QUOTE]

Power Management, actually :) It will make your computer cooler :D
It seems that they implemented a new feature called *Dynamic Clock Gating*, which, according to ATI:

> This feature allows the supported graphics cards to deactivate components when they are not being used. 

New features include *Enhanced Support for OpenGL Development*, *Dual Link Monitor Support*, *Xinerama Support* and a *New X Server Configuration Utility*. Though for start, I would first try to get the Ubuntu 8.16.20 drivers working through synaptic, and then try these ones.

Cheers!

---

### Post by SilverTab on 2005-10-13
[QUOTE=dcarpenter]Sorry but I still dont know why you are wanting to install the ATI driver from the site and not just use the synaptic package?  Were there any substantial performance increases or bug fixes with the newest release?[/QUOTE]


I wanted to try this one because the Synaptic package didnt work LOL....

I installed it, edited xorg.conf and it kept showing Mesa driver when I ran fglrxinfo....

so I decided to try it by downloading the package...and it happens to be a new version...and the trouble started...

I just want a working ATI driver, I dont care if it's the latest version or not...

---

### Post by SilverTab on 2005-10-13
[QUOTE=mlomker]They also released the 8.18.6 version of their linux drivers today.  I haven't had much luck getting them to work on amd64 Breezy.  The built-in 8.16.20 drivers work fine, though, and I've put a how-to into the video & sound forum.[/QUOTE]

hehe I know I read your terrific howto on this subject and it worked several times for me in the past! :)  (in hoary)...


however, with the new version on ATI's website, I cant follow the walkthrough...its just not working anymore with the new version of the driver! :(

---

### Post by mlomker on 2005-10-13
> however, with the new version on ATI's website, I cant follow the walkthrough...its just not working anymore with the new version of the driver! :(

I worked on it for 5 hours today and it doesn't work yet.  Everyone should stick with 8.16.20 until someone figures it out (unless you like figuring things out, of course :) ).

The biggest fix is the misdetection of resolution on a handful of monitors.  It doesn't offer any performance improvements.

---

### Post by dcarpenter on 2005-10-13
SilverTab, my experience with breezy has been i go to synaptic and install xorg-driver-fglrx, then gedit the xorg.conf to change ati to fglrx then reboot and i have 3d.. i have a 9800xt.  Dunno why you are having trouble with this?  What model card do you have and all that good stuff?

---

### Post by Olav on 2005-10-13
[QUOTE=SilverTab]Olav: Any luck?[/QUOTE]
Well, not really I guess. I reported back in [this post]("http://ubuntuforums.org/showthread.php?p=408616#post408616").

---

### Post by ModusOperandi on 2005-12-18
[QUOTE=dcarpenter]SilverTab, my experience with breezy has been i go to synaptic and install xorg-driver-fglrx, then gedit the xorg.conf to change ati to fglrx then reboot and i have 3d.. i have a 9800xt.  Dunno why you are having trouble with this?  What model card do you have and all that good stuff?[/QUOTE]

I'm wishing to enable hardware acceleration, but when i do that, the next time I reboot, I get the command line, and attempting to start KDE result in errors. When i try to access the control panel in KDE, I get the following error:

> 
Driver does not provide the FireGL X11 extensions! Panel components will operate only partially.


I'm using the drivers from the repository.

---

