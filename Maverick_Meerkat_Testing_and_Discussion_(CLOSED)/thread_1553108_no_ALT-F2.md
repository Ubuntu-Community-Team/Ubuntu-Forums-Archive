---
title: "no ALT-F2"
date: 2010-08-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Thomas Garman on 2010-08-14
I just upgraded to Ubuntu 10.10 Alpha 3 on my ACER ASPIRE ONE D250.  The GNOME desktop is now gone one the machine, by which I mean I cannot get any of the menu items that are usually at the top of the screen to appear, although the icons that were on my desktop still appear.  I cannot get ALT-F2 to do anything.  I hit ALT-F2 and nothing at all happens.

This is a problem because the way the BUG TRACKER for Ubuntu works now you cannot just go to Launchpad and file a bug.  You have to hit ALT-F2 and then type ubuntu-bug and a series of menus will take you through the bug process.

So, does anyone know how to get the gnome desktop back or how to get ALT-F2 to appear or how to get a terminal to open when there are no menus and ALT-F2 does nothing?

Of course, recovery mode works.  And startx will allow me to use nautilus.  The way I got the browser I am typing this into to open was I opened nautilus and searched for "firefox" and then I clicked on a .html file and it opened a browser...

---

### Post by Thomas Garman on 2010-08-14
OK.  I wanted to be helpful and try out Ubuntu 10.10 Alpha 3 and report bugs and suchlike.  Now, I installed Ubuntu 10.10 Alpha 3 on my Acer Netbook and now I cannot get ALT-f2 to do ANYTHING AT ALL and I have no menus for the gnome desktop and I cannot open a terminal AT ALL.  So, it makes it basically impossible to even file a bug report through launchpad since it seems that the developers have restricted bug reporting to: ALT-F2 ubuntu-bug so that they can gather information about your system.

This means that I cannot even use the OS at all for anything not even bug reporting.

DOES ANYONE know how to get the terminal to open if ALT-F2 doesn't even work and there are no gnome menus?  All my computer shows is a black expanse of useless nothing.  The only thing that will work at all is my keyboard just happens to have a "search" button pre-programmed on it and if I hit that then a nautilus window will open and I can search for an html file and then if I click "open" that will spawn a browsers.  The machine is connected to the internet via wifi.  So network manager works.

---

### Post by Iowan on 2010-08-14
Moved to Maverick Meerkat Testing and Discussion

---

### Post by ranch hand on 2010-08-14
The first thing that I would do is boot to recovery and run the option "dpkg fix broken packages".

When that is finished you want return to normal boot which will give you a text login.  Log in.  Then, at the prompt, type   startx  .  This should take you to your desktop which will hopefully work.

If not you should try booting to the failsafe gnome session but you probably have auto login so I do not know how you would do that.

---

### Post by Thomas Garman on 2010-08-14
...I booted into recovery from grub and I ran fix broken packages and also then I did startx and it came back the same as before, which is to say that the desktop is completely unusable and ALT-f2 does nothing at all.

NO CHANGE AT ALL.  Still broken.

It is as if the desktop is set to be viewed on a 32" Monitor and I am only seeing a tiny little corner of it on my Netbook screen, because the icons are there and also the wall paper but there is no way to get it to show the "Applications Places System" in the upper left and also ALT-f2 does not work at all.

---

### Post by 23dornot23d on 2010-08-14
NVIDIA GeForce 8400 graphics card ............ seems like the graphics card needs to be set
up ...... properly.

So many things happening with graphics I am not sure what to tell you .....

Used to be able to just add xorg.conf to solve these type of problems .....

[nvidia-xconfig]("http://linux.die.net/man/1/nvidia-xconfig")

Now I am not so sure as they keep altering things .....

If you could get to ...........

System Administration Hardware Drivers ..... it may just be a case of adding the latest driver.

If ubuntu-desktop is not loaded up properly .....

in a console you can type 

apt-get install ubuntu-desktop

but from what you are saying ..... its probably working ok ..... and you are just seeing a tiny portion of the screen 
so cannot see the things needed to set things right ...... therefore you will have to work from the console.
_______________________________________________________________

  So ..........

Can you press Ctrl+Alt+F1 and get to the console ...... and see the cursor ok ? and a login prompt

Ctrl+Alt+F7 ,,,, will bring you back again ..... note this before going out ...

_______________________________________________________________
[COLOR=Red]Is Plymouth causing this to happen ... seems to be lots of people on the forums with graphic issues of late.
or the Nouveau drivers .... 
I know once the graphics are set up ok its fine ..... but a pain for the people not managing to do this first time.[/COLOR]

---

### Post by Thomas Garman on 2010-08-14
I do NOT have the NVIDIA GeForce 8400 video card installed on my ACER ASPIRE ONE netbook.  I have a compaq desktop with the video card but that is a TOTALLY DIFFERENT system.  

I have an ACER ASPIRE ONE D250 completely unmodified and totally exactly what you would buy at any store without any extra graphics card or any modifications whatsoever.

The ACER ASPIRE ONE D250 had Ubuntu 10.04 on it and it worked perfectly fine.  I started with Ubuntu 9.04, then upgraded to 9.10 and then upgraded to 10.04 and each system worked perfectly fine.

I upgraded to Ubuntu 10.10 Alpha 3 and now ALT-F2 will not open the run box like it ordinarily should.  there are no gnome bars at top of the screen that give "applications places system" menus there is no way to open a terminal.

Of course, if I start in recovery then I get the recovery terminal and of course I can sudo synaptic and get a synaptic window etc etc.

---

### Post by 23dornot23d on 2010-08-14
Ok lets start again ,,

From what you have told me ,, it should be a [Intel GMA 950 chipset]("http://www.umpcportal.com/products/Acer/Aspire%20One%20D250/") for your graphics ...... on the [ACER ASPIRE ONE D250]("http://www.notebookcheck.net/Review-Acer-Aspire-One-D250-Mininotebook.17823.0.html").

The screen size and resolution .... 
The **10.1&#8221; LED Display** from SEC has the usual netbook WSVGA resolution of 1024x600 pixels


Struggling to find info on the [950 working well]("http://www.google.com/search?hl=en&q=maverick+intel+950+xorg+950resolution&aq=f&aqi=&aql=&oq=&gs_rfai=") in Maverick also seem to be lots of problems on earlier releases too .....

This is the best I can find at the moment ..... 

**I do not work with Intel so if anybody has better advice .... please shout up**

___________________________________________________________________________

I hope you do realise .... this is the test version you are running and things do break ....... 
and you really do need to know how to put them right ...... to continue testing .... them ....
read the [stickies at the beginning of the Maverick Testing.]("http://ubuntuforums.org/forumdisplay.php?f=385")
____________________________________________________________________________

[COLOR=Red]This seems to be the settings for your system ...... but you need to check these ....... might be the old way of
doing things - because things are different on the test version and not everything works as it should do .....

_________________________________________________
[/COLOR][COLOR=Red]sudo apt-get install xserver-xorg-video-intel

sudo apt-get install 915resolution

sudo gedit /etc/default/915resolution

mode=7e
XRESO=1024
YRESO=600
BIT=32[/COLOR]
__________________________________________________

---

### Post by Thomas Garman on 2010-08-14
As for the sudo apt-get suggestions here is what I get...

sever xorg-video-intel is already the newest version

Package 915resolution is not available
Package '915resoltion' has no candidate

sudo: gedit: command not found

because I am running all of this through the recovery console provided at the login screen.

When I actually log in I cannot access a terminal AT ALL nor does ALT-F2 yield any actions.

---

### Post by ranch hand on 2010-08-14
And if you could boot to the live CD and change so that you at least have a timed login, I think that pulls up the login screen in spite of auto login (still logs in auto but you can view the options on the lower panel) you could get to the failsafe gnome session which I believe would work so that you could change some setting more easily.

---

### Post by mc4man on 2010-08-14
As far as bug report - 
there is a way to cli and save an apport report, then file from another location(install or machine.

But why don't you try here in a browser
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

---

### Post by Thomas Garman on 2010-08-14
I am not on Auto Login.  I have all of the options for login including failsafe gnome.  When the login screen comes up it stops and I have to select a user and then I enter a password and from that screen I can also choose several login options

Ubuntu desktop
Ubuntu desktop failsafe
recovery terminal
kde

I am not on Auto Login at all.

---

### Post by mc4man on 2010-08-14
As far as a terminal for use on the desktop I'd  try to create one.

If you can r. click on the desktop then create an empty file,
don't name yet and paste this in 

```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Terminal
Comment=Use the command line
TryExec=gnome-terminal
Exec=gnome-terminal
Icon=utilities-terminal
Type=Application
X-GNOME-DocPath=gnome-terminal/index.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.30.2
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-terminalex.html
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-terminal
X-GNOME-Bugzilla-Component=BugBuddyBugs
X-GNOME-Bugzilla-Version=2.30.2
Categories=GNOME;GTK;Utility;TerminalEmulator;
StartupNotify=true
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-terminal
```
Then save, r. click rename to this and make executable

```
gnome-terminal.desktop
```

If you can use nano it could maybe be done from recovery prompt

---

### Post by 23dornot23d on 2010-08-14
If all else fails ..... you could try this ......... go in in safe mode .....

( Seems you have the correct driver - its your resolution that's possibly set wrong  ......)



**cd /etc/X11**

**ls**
(ls lists the files just check you are in the correct directory ..... **capital X**11)

 (this does a backup of your existing configuration)

**sudo mv xorg.conf xorg.conf.backup**

(this creates a new configuration)

**sudo Xorg -configure**
  
This has generated the file in /etc/X11/xorg.conf.new.
  
(now we need to make it available to the system)

[B]sudo mv xorg.conf.new xorg.conf
[/B]  
(display what you have)

**less xorg.conf**

ctrl Q gets you out of this ....... its just so you can look and see what you have produced looks ok

then reboot ....... hopefully everything will be the right size for your screen ...... 

**look for the 1024 x 600** .... you need that for the correct resolution to be displayed.

 _______________________________________

 

 You should get something like this ........
(it will possibly be slightly different ... this is just an example of what you should have created)
 

```

Section "InputDevice"
    Identifier   "Synaptics Touchpad"
    Driver       "synaptics"
    Option       "SendCoreEvents"
    Option       "Protocol"              "auto-dev"
    Option       "SHMConfig"             "on"
    Option       "TapButton1"            "1"
    Option       "TapButton2"            "2"
    Option       "TapButton3"            "3"
EndSection

Section "Device"
    Identifier   "Intel Mobile 945GME"
    Driver       "intel"
EndSection

Section "Monitor"
    Identifier   "LCD Monitor"
    DisplaySize  223 125
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Monitor      "LCD Monitor"
    Device       "Intel Mobile 945GME"
    DefaultDepth 24

    [B]SubSection   "Display"
        Depth    24
        Modes    "1024x600"
    EndSubSection[/B]
EndSection

Section "ServerLayout"
    Identifier   "Default Layout"
    Screen       "Default Screen"
    InputDevice  "Synaptics Touchpad"    "CorePointer"
EndSection


```

---

### Post by ranch hand on 2010-08-14
Have you tried the failsafe option.  That usually works even if the graphics may be a bit off.

---

### Post by Thomas Garman on 2010-08-14
@mc4man

Yes, the launchpad url works and I filed a bug on there:

[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/618046)

But the code you gave me to get a terminal to open does not work.  I right clicked and saved the code you gave me and saved it on my desktop and then right clicked it and opened it in terminal (as was one of the options) and the terminal that appeared immediately disappeared.  It was like like a brief millisecond appearance of a terminal that immediately went away.

---

### Post by libssd on 2010-08-14
> **Thomas Garman said:**
> DOES ANYONE know how to get the terminal to open if ALT-F2 doesn't even work and there are no gnome menus? 
Have you tried Ctrl-Alt-T ? This should be a universal sequence for starting a terminal session, although if you have so many other problems, it may not work either.

---

### Post by cariboo on 2010-08-14
If you are running the UNE, you can select the gnome-desktop from the login screen, where everything works as expected. Alt+F2 is on the wish list for Unity, there was a bug created back in May.

**Edit**: Bug #[lpbug]580295[/lpbug]

---

### Post by mc4man on 2010-08-14
> saved it on my desktop and then right clicked it and opened it in terminal 
You wouldn't do that - it is a desktop launcher for gnome-terminal - if you made it executable (r. click - properties - permissions) then just double left click on the icon to open a terminal

Once made executable it should show up as a terminal icon named "Terminal"

---

### Post by Thomas Garman on 2010-08-14
I got a terminal to open by doing ALT+CTL+T...  in safe mode I did cd /etc/X11
ls

and I discovered that there is no xorg.conf file.  I rebooted and selected the recovery mode from the login UNE screen and I again did

cd /etc/X11
ls

and here is what it says I have (which I am typing into this window because I have no network access on the box I am talking about here)...

app-defaults
rgb.txt
Xreset
Xsession.d
cursors
default-display-manager
fonts
X
xinit
xorg.conf.failsafe
Xreset.d
XvMConfig
XWrapper.config

When I try to run sudo Xorg -configure whether I am in any of the recovery or safe mode options offered by any screen at all or in the terminal I always get

Server is already active for display 0

---

### Post by 23dornot23d on 2010-08-14
This will stop gdm ..... but do it from safe mode ...... at the command line ...

sudo /etc/init.d/gdm stop

then you can create the xorg.conf

---

### Post by Thomas Garman on 2010-08-14
OK...  I booted into recovery mode and stopped gdm and then I was able to use

sudo Xorg -configure 

to create a xorg.conf file and then I moved it to the /etc/X11 directory which I verified but upon reboot nothing has changed.

---

### Post by 23dornot23d on 2010-08-14
Does this appear in the xorg.conf file ?

[B]SubSection   "Display"
        Depth    24
        Modes    "1024x600"
    EndSubSection[/b]




( If you type "xrandr -q"  is that resolution listed  ? )

---

### Post by Thomas Garman on 2010-08-14
@23dornot23d...

No, the 1024 X 600 does not appear in my xorg.conf file.  What I am getting is just this (at the point where the screen size should appear...)
Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Viewport   0 0
                Depth     1
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
   
 SubSection "Display"
                Viewport   0 0
                Depth     4
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection

---

### Post by Thomas Garman on 2010-08-14
yes... if I put xrandr -q in the terminal I get this:

Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1024x600       60.1*+
   800x600        60.3     56.2  
   640x480        59.9

Looking at the sticky at the top of the forum that this thread is a part of makes me think that the x-server is broken in way that will not be fixable and that this is somehow related to why I am having this problem.  

I think I picked a bad day to upgrade to an alpha release.

---

### Post by 23dornot23d on 2010-08-14
You need to edit the xorg.conf file and add this into it

you can do it from another computer and copy it back across to it .....

but this needs to be in it to change the screen resolution ....

Cut the existing from
Section "Monitor"
to
Endsection
out of the existing file and replace with this ......below .....
___________________________________
Section "Monitor"
    Identifier   "LCD Monitor"
    DisplaySize  223 125
EndSection

Section "Screen"
    Identifier   "Default Screen"
    Monitor      "LCD Monitor"
    Device       "Intel Mobile 945GME"
    DefaultDepth 24

    [B]SubSection   "Display"
        Depth    24
        Modes    "1024x600"
    EndSubSection[/B]
EndSection
_____________________________________


Just a thought ..... do you have a xorg.conf as a backup file from your previous version ......
if that ran ok .........

_______________________________________

> 

Looking at the sticky at the top of the forum that this thread is a part  of makes me think that the x-server is broken in way that will not be  fixable and that this is somehow related to why I am having this  problem.  

I think I picked a bad day to upgrade to an alpha release.
Yep possibly not the best timing ..... as this is what they are currently working with ......

But I do think you may be better off if the resolution is set correctly for your computer ......
at 1024 x 600 .....

if the xorg.conf ..... still picks up ok ......

---

### Post by Thomas Garman on 2010-08-15
I went into recovery mode and used the vi text editor:

sudo vi /etc/X11/xorg.conf

which allowed me to edit the xorg.conf file... in that file I added 

Modes "1024x600"

in the place you seem to be indicating it should be, which is after Display 24 but before EndSubsection

and then I saved the new xorg.conf with :wq

reboot

Same as before.

---

### Post by 23dornot23d on 2010-08-15
Double Post for some strange reason.

---

### Post by 23dornot23d on 2010-08-15
You could install updates ...... and do 
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude safe-upgrade 

as each new day passes new files come out ....... for 10.10
if you want to carry on testing .... but that's what can
break things ..... then we report back and tell them its broke, 

They then try to fix it ...... ( "They" - being the Developers)
_________________________________

or you revert back to Lucid 10.04 
Until Maverick 10,10 comes out on 10.10.2010 ......
Things do not always work as we want here ....... 
but if your computer is a production machine .... 
you should use Lucid 10.04.

The xorg.conf would be where I would expect to be able to
do alterations ..... but they may have stopped using this now ....
it always used to pass the information across if you had one there ....
who knows what alterations are taking place here at the moment,

( maybe someone else will pick this up ...... )

The graphics also get set at boot ...... by something called plymouth ......
maybe this is where the problem really lies.
But I do not know enough about what they are doing here to help you.

Sorry I can not help you anymore .....

---

### Post by Thomas Garman on 2010-08-15
@23dornot23d  Thanks for your help.  At least through this process I learned how to edit a file with the vi editor in a terminal.

I don't think they have the X server set up to recognize the monitor correctly, so my changes to the xorg.conf file are pointless.

I really appreciate your effort.

This is not a production machine.  In my Signature you will see I have a desktop, a laptop and then a third machine: the netbook.

I am doing all of this on the netbook, which I hardly use for anything anymore other than running BOINC processes.

I am not really understanding why the developers would consider an Ubuntu release with no functioning X Server to be ALPHA 3 since that makes it impossible to get a working desktop and at least from the point of view of the philosophy of Ubuntu releases (ease of of use for beginners) I would say that if you cannot get the X Server to function properly then you are really not even beyond ALPHA 1.

---

### Post by VMC on 2010-08-15
> **Thomas Garman said:**
> ...
When I try to run sudo Xorg -configure whether I am in any of the recovery or safe mode options offered by any screen at all or in the terminal I always get

Server is already active for display 0

Reboot and run in "Single" mode
Edit:By "single" I mean "recovery" mode as below.
```
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,7)'
	search --no-floppy --fs-uuid --set cc7db4b9-b039-4d6b-aa77-6d59cce1e317
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=cc7db4b9-b039-4d6b-aa77-6d59cce1e317 ro **single** 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
```

---

### Post by Thomas Garman on 2010-08-15
I am not running Ubuntu 10.10 Alpha 3 NETBOOK REMIX.  I have never run NETBOOK REMIX with any version of Ubuntu on my Acer Aspire ONE D250.  I first put Ubuntu 9.04 on the Netbook with the full desktop version about a year ago and then I have upgraded every time and it has worked perfectly fine.  There has never been a Netbook Remix version on this computer.  The current Alpha 3 for Ubuntu 10.10 was obtained by upgrade from Ubuntu 10.04.  My Ubuntu 10.04 install was the full desktop version and it worked perfectly fine on the ACER ASPIRE ONE D250.  There is NO NEED for the netbook remix and the fact that I am not running it here is not the source of the problem.  The problem is with the X server.

---

### Post by mdmcginn on 2010-09-06
I thought I had a screen resolution problem too. But I think it was a problem with no taskbars. I restored my taskbars this way. (Ctrl-Alt-T gets a terminal):

screen
gnome-panel
Ctrl-A D

Once I did that, I once again had an Applications - Places - System menu at the top, and a taskbar of running programs on the bottom.

But first..

aptitude safe-upgrade

which restored a whole bunch of important programs that Update Manager had removed. Alt-F2 works now too.

---

### Post by rburkartjo on 2010-09-06
it seems to working fine now with the beta release

---

