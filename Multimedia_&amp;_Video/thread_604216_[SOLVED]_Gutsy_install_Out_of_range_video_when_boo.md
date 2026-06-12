---
title: "[SOLVED] Gutsy install Out of range video when bootup"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Tony3286 on 2007-11-05
I have read and reread posts concerning the 'Out of range" for the video and have had no luck! I went into startup manager - it originally showed 640 x480 - I changed  it to my
correct resolution 1024X768. I then rebooted and same thing - Black screen , no splash screen, get a red out of range box that keeps moving down and to the right and finally get logon screen.  I'm using a OptiQuest 19 inch monitor Q9 and I'm running a Sony Vaio desktop model PCV-RX850. In Windows, it states the video chipset type is SIS 651 Rev00 and lists it as SIS 650-651-750. When I try and choose these setting in "Screens and Graphics" under System-administration and do a TEST , I get a small herringbone design and then get a message "Configuration test failed" and it reverts back to Graphic driver of - Vesa - generic vesa.  I also went into my Xorg.config and strangely it shows a resolution of 640 x 480 Below is a copy of my Xorg.conf.
PLEASE, if anyone could help, it would be greatly appreciated. I am running Gutsy but had the same problem under Feisty for the last 2 months. If I have to edit the Xorg.config, I would appreciate step by step directions - very new to Linux.
Thanks soooooooo much

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-80
        VertRefresh     55-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by Tony3286 on 2007-11-08
[SIZE="3"]No suggestion after all this time ??   Going once, twice - BLANK SCREEN[/SIZE]

---

### Post by erginemr on 2007-11-08
> **Tony3286 said:**
> [SIZE="3"]No suggestion after all this time ??   Going once, twice - BLANK SCREEN[/SIZE]

Hello, I have just read your message. No promises, but I will do my best to try to help you as much as I can.

For starters, can you see the initial stage of your boot up process?

That is, when you boot your computer, can you see Grub menu at boot, and the Ubuntu splash screen with the orange progress bar?

I suppose, you lose the monitor during the login stage afterwards. Am I correct?

---

### Post by Tony3286 on 2007-11-08
Thank you soooo much for at least responding

When I turn on my system - Grub does appear - I choose to boot in Linux, thats when the
"Out of range box" appears. It does it walk across  the screen from right to left and when it nears the right side of my monitor the login comes up - No splash screen or orange progress screen.Everthing from logon screen forward is fine, just prior to that.

Thank you again

---

### Post by erginemr on 2007-11-08
You are welcome. I am not sure but it seems there is a problem with the Ubuntu splash screen resolution. I am also using Gutsy and my default splash screen had a very high resolution by default. The file to change is:
/etc/usplash.conf

Mine looks like this:
# Usplash configuration file
xres=1024
yres=768

Can you start with editing this file, first backing up the original just in case with:
sudo cp /etc/usplash.conf /etc/usplash.bak

Then edit it with:
gksu gedit /etc/usplash.conf

and change the resolution as 
xres=800
yres=600

Do it and reboot to see if there is any progress. Otherwise, we shall attack xorg.conf.

---

### Post by erginemr on 2007-11-08
While you are checking it, let me list part of my own xorg.conf file:

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes	"1024x768_75"	"800x600_75"	"640x480_75"
	EndSubSection
EndSection

Section "Module"
	Load		"glx"
EndSection

I remember having messed my screen by using the program "Screens and Graphics", thinking of it highly as something out of this universe first, but staring at a black screen next on my next boot. Fortunately, I had taken a copy of my xorg.conf file.

There are two things that I did not like in your xorg.conf file. First, horizontal and vertical refresh rates have been given explicitly. I believe Xorg is capable of detecting the refresh rates correctly. Secondly, your default depth is 24 bits and your modes section with Depth 24 starts with 1280x1024, which AFAIK says your desktop to start with a resolution of 1280x1024, which might cause our monitor to shut itself down.

So, after backing up your xorg.conf file with:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak

you may try to edit it as follows to see the effects:

1. Comment out the explicit refresh rates with:
# HorizSync 30-80
#VertRefresh 55-75

2. Change the modes line with under Depth 24 as:
SubSection "Display"
Depth 24
# Modes "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
Modes	"1024x768_75"	"800x600_75"	"640x480_75"
EndSubSection

The "_75" part means to use 75 Hz refresh rate. (If I don't use it, my monitor tries to load with 85 Hz, but fails miserably with a blurry screen.)

---

### Post by Tony3286 on 2007-11-08
[SIZE="2"]Do you really want me to change the etc/usplash to
 xres 800
yres 600     My resolution is suppose to be 1024x768 like yours or is this just for the splash screen?

One other question if I blow my system how do I replace my xorg.conf file? Can I boot to safe mode and enter something there?

Again, I can't thank you enough, even if your ideas don't work, you were kind enough to take the time and try and help. I'm presently at work now but as soon as I get home, I'm going to try your suggestions!
Tony[/SIZE]

---

### Post by erginemr on 2007-11-08
You are most welcome. After all, we are here to help each other. The most important thing here is your problem to be solved.

I have suggested 800x600 just to be on the safe side. You may try 1024x768 first in 
/etc/usplash.conf.
usplash.conf is just for the splash screen. It is the xorg.conf, which handles your Gnome desktop.

If your system blows up, it can blow up in two ways:

1. Most probably, your desktop will not open after our edit on xorg.conf and you will drop to the black screen (a.k.a. Linux console or terminal). Then all you need to do is to restore your xorg.conf backup:
sudo cp /etc/X11/xorg.bak /etc/X11/xorg.conf

2. A slight possibility is that you may not be able to see anything with an "Out of range" message. No problem with that if your login screen comes up later on, that means our edit in the usplash.conf has nothing to do with your problem. You can restore your orginal config file with:
sudo cp /etc/usplash.bak /etc/usplash.conf

If worse comes to worst, then you can still boot from your Ubuntu Live CD, access the  files on your hard disk and edit the usplash.conf file from there. (But in doing so, make sure you do not confuse your real hard disk with the virtual hard disk of the Live CD.)

I suggest you to jot these notes down or print them out while you are in the office.

And most of all, good luck!..

---

### Post by FSHero on 2007-11-08
Hello there,
Sorry to interject, but I have a similar problem with the Kubuntu 7.10 (Gutsy) live-cd. I can see the bar moving back and forth, and I press ctrl+alt+F1 to see the start up messages (I always do this ;)).

But then, I get an "out of range" warning from my monitor, whose maximum resolution is 1024x768. I have to run
```

sudo /etc/init.d/kdm stop
sudo dpkg-reconfigure xserver-xorg

```

and deselect from one of the screens "1280x1024". On the next screen (I think), it asks me what the default monitor resolution is. I select 1024x768 @ 60 Hz.

After this, if I do
```

sudo /etc/init.d/kdm start

```
everything works fine; I'm brought to the Kubuntu desktop.

If I were a bit more of a newbie... I would be stuck. It seems like the default resolution on the live-cd is 1280x1024 (evidence: I saw a friend run the Ubuntu live-cd, and the resolution of his screen appeared to be 1280x1024).

Is this a bad design error on Ubuntu's part? Also, I hope this post helps someone else.

---

### Post by Tony3286 on 2007-11-08
Believe me, as a newbie to linux, I print out EVERYTHING -LOL
**AND** always make sure I backup everything, thats why I appreciate that you had the patience to
type step by step directions.
I'll let you know the outcome!

Tony

---

### Post by erginemr on 2007-11-08
Hi FSHero, no problem.

Your post actually renewed my faith in that usplash.conf may be the true culprit in Tony's problem.

My original config file in the Gutsy Live CD was also set to 1280x1024 too, and I said to myself what the heck, as the Ubuntu logo and orange progress bar was hardly visible (OK, I exaggerated a little bit, but you get the idea.)

I think you may be right, the Ubuntu developers hight be hard pressed to release Gutsy on time, so that they may have left behind a few hiccups such as this one, who knows?

---

### Post by erginemr on 2007-11-08
> **Tony3286 said:**
> Believe me, as a newbie to linux, I print out EVERYTHING -LOL
**AND** always make sure I backup everything, thats why I appreciate that you had the patience to
type step by step directions.
I'll let you know the outcome!

Tony

):P Okey dokey. Take care, both of you...

---

### Post by eye208 on 2007-11-08
The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash

to apply the changes. This step will copy the usplash config file into the ramdisk image used by the kernel on startup.

If the out-of-range warning appears _after_ the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg

Choose manual monitor configuration, then pick the appropriate resolution(s) from the list. When configuration is done, press Ctrl-Alt-Del to reboot.

---

### Post by erginemr on 2007-11-08
> **eye208 said:**
> The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash

to apply the changes. This step will copy the usplash config file into the ramdisk image used by the kernel on startup.

If the out-of-range warning appears _after_ the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg

Choose manual monitor configuration, then pick the appropriate resolution(s) from the list. When configuration is done, press Ctrl-Alt-Del to reboot.

:???: Strange... Maybe it is just me, but I didn't need to apply:
sudo dpkg-reconfigure -phigh usplash
after the change in the config file. 

Thank you anyway for the extra information.

---

### Post by eye208 on 2007-11-08
> **erginemr said:**
> Maybe it is just me, but I didn't need to apply:
sudo dpkg-reconfigure -phigh usplash
after the change in the config file.
The second step was necessary with earlier versions of Ubuntu. Maybe the file is now being monitored for changes to simplify the procedure. Thanks for the info.

Edit: I checked this with a fresh Gutsy install last weekend. Reconfiguring usplash is still necessary to apply the changes in /etc/usplash.conf. Of course there are other ways to trigger update-initramfs, but it has to be done, one way or the other.

---

### Post by Tony3286 on 2007-11-08
Well theres good news and not so good. Changing the Usplash config
to 800 and 600 didn't work - ( I left it that way at 800 and 600)
However I commented out the Horizsync and Vertical AND in Depth 24 Commented out all
the Modes and used your recommendation to put 1024x768_75 in front.

I rebooted and YES the splash screen appears with the orange line going across
then grub appears - I choose Linux THEN** (OH NO)** the red "Signal Out of Range" appears for a split second,goes away and then comes back and does its dance across the screen till it hits the right side- disappears and the login screen appears. Then everything is fine.

I have never gotten the "signal out of range" prior to Grub - always after, and that still occurs
But I NEVER got the splash screen BEFORE and now I do - A Positive !

So I'm 1/2 there - LOL - any further suggestions that may help?

Tony

---

### Post by Tony3286 on 2007-11-08
Here is the NEW Xorg.config file
**NOTICE** - I definitely used **1024x768_75** and yet the new file shows**1024x768@60** which according to my Monitor manual is  OK and in fact all the resolutions changed  and are ok according to the manual????? AND the Horisync & VertRefresh are back with **different **values. (should I change them to my monitors defaults that are in my manual  horiz 30-80 and vertical 55-75 ?)-  After the reboot, I went into administration-screens and graphic - I really think that area is buggy. Because I go in there and now My monitor was changed to Plug and Play from LCD 1024x768 and when I got out and reboot I got an error message "error in Gnome setting" I get a little green running stick figure in the right corner and everything froze for about 3 minutes - I quickly changed the setting back to LCD 1024x768 rebooted and was back to my normal screen - NO, I still have the red 'Out of Signal" after grub


Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "ServerFlags"
EndSection

---

### Post by erginemr on 2007-11-09
OK, First of all, forget about "screens and graphic" as I also believe that since it is a new feature, is not mature yet. Since we have solved the splash screen problem, it is the xorg.conf problem that remains.

Remember you had backed up your first xorg.conf file to xorg.back before all this (where your login process after grub was OK)? Your first step should be restore that one to see if it works.

If not, you can try
sudo dpkg-reconfigure -phigh xorg.conf

and see what happens.Finally, try
sudo dpkg-reconfigure xorg.conf
which will ask you some questions before changing your xorg.conf file.

But I believe your initial back-up file is the key.

---

### Post by namanbagga on 2007-11-09
[This]("http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html") is what worked for me

---

### Post by erginemr on 2007-11-09
> **Tony3286 said:**
> 
.......
I rebooted and YES the splash screen appears with the orange line going across
then grub appears - I choose Linux THEN** (OH NO)** the red "Signal Out of Range" appears for a split second,goes away and then comes back and does its dance across the screen till it hits the right side- disappears and the login screen appears. Then everything is fine.
.......
Tony

Hi, Tony. there are some tidbits to clarify:

- The method proposed by namanbagga involves the editing of grub "menu.lst" config file in addition, which is definitely worth a try. (Hopefully, this will one work.)

- You said above that the grub menu appears after the splash (the one with the Ubuntu logo and progress bar). Are you sure? Normally, when my computer boots, I see the grub menu first after a few seconds, from where I can select Ubuntu Linux or MS Windows. 

- It is after this step that the Ubuntu splash screen shows up, followed by the login screen and the desktop. Could you please clarify this?

- FYI, you may also try 1024x768_60 to get a screen with 60 Hz refresh rate instead of 75 Hz. The sign @ did not work for me, I had to use _ to get the effect. 

- The "screens and graphic" applet is dangerous if you save the settings, but sure is useful as a test bed, to try different resolutions and refresh rates for your monitor. But the problem is the fact that you get the screen back after the login screen, which either means your xorg.conf works OK and is the wrong place to look at, or means that it is set wrong but Gnome or the X graphics server fails first, understands it somehow and falls fack to a failsafe resolution after a while.

---

### Post by zeifertstc on 2007-11-09
Hey, I just wanted to pipe and let you know that most LCD screens I have come across (which it sounds like you're using as I am) can only use refresh rates of 60 and lower. I believe that your refresh rate may be locking itself at something like 75 and the screen is protecting itself by giving you the "out of range" box that is "dancing" across your screen. Make sure that refresh rate is locked in at 60 or lower.

Other than that, it does sound like the resolution itself is running a bit high. The install CD seems to be bent on forcing 1280x1024 resolutions on all of us. I was lucky that I had my dual monitor setup working when I tried installing my copy. My secondary monitor allowed me to reset the screen size to 1024x768 and everything else just fell into place.

Hope the tip on the refresh rate helps.

---

### Post by Tony3286 on 2007-11-09
Ok sorry for the confusion - The startup is like this:
Turn on computer
goes to Grub and choose linux
**then** out of range for a second and then it comes back and dances across the screen
Finally login appears and all is well
Now at shutdown I see the splash screen (YES at SHUT DOWN -seems backwards to me LOL) and it shuts down fine

What I , in a bumbling way ,was saying in my previous post was when I was a**lready **in Gutsy and I press restart, THATs  when I saw the splash screen and then the gub screen.

So to clarify in clean start from system completely off - NO SPLASH , then grub then "out of range"

When already in Gutsy for** restart**, I see the splash screen then grub then out of range warning
then login.

Also, one question - why do you want me to revert back to my backed up Xorg.conf?  With the
tweeked of Xorg.conf you instructed me to do ,  now at least I get a splash screen even if its at shutdown. Really appreciate your input !

Again I'm back at work so will try previous post concerning "Ubuntu 7.10 bootup resolution problem"
when I get home and see if that works

---

### Post by Tony3286 on 2007-11-09
One other question - Because I'm a newbie , in the link that Namanbagga posted - I have a question
on where to put 'vga=791'.791 from step 2 - is it right after "generic root (hd0,9) on a seperate  line? Thanks again for all your patience.


2.	Step 1 should solve the shut-down problem.To solve the start-up problem,you need to follow step2 and step3.Now edit /boot/grub/menu.lst by typing 'sudo gedit /boot/grub/menu.lst' or 'sudo nano /boot/grub/menu.lst' .In this file reach the line
## ## End Default Options ##
By default the next paragraph will have the boot information for the option you choose while booting up.It will say something like-
title Ubuntu 7.10, kernel 2.6.22-14-generic
root (hd0,9)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=ebddbc03-0e71-41dd-babd-278109f26a95 ro quiet splash
initrd /boot/initrd.img-2.6.22-14-generic
quiet
[B]At the end of the line next to kernel,next to splash add 'vga=791'.791 is the code for 1024X768 resolution in 16 Bits.What this does is that it changes the screen resolution of all following steps but not of the xserver.You can select any other resolution which your monitor is comfortable with
[/B]

---

### Post by erginemr on 2007-11-09
> **Tony3286 said:**
> Ok sorry for the confusion - The startup is like this:
Turn on computer
goes to Grub and choose linux
**then** out of range for a second and then it comes back and dances across the screen
Finally login appears and all is well
Now at shutdown I see the splash screen (YES at SHUT DOWN -seems backwards to me LOL) and it shuts down fine

What I , in a bumbling way ,was saying in my previous post was when I was a**lready **in Gutsy and I press restart, THATs  when I saw the splash screen and then the gub screen.

So to clarify in clean start from system completely off - NO SPLASH , then grub then "out of range"

When already in Gutsy for** restart**, I see the splash screen then grub then out of range warning
then login.

Also, one question - why do you want me to revert back to my backed up Xorg.conf?  With the
tweeked of Xorg.conf you instructed me to do ,  now at least I get a splash screen even if its at shutdown. Really appreciate your input !

Again I'm back at work so will try previous post concerning "Ubuntu 7.10 bootup resolution problem"
when I get home and see if that works

Hi Tony,

So to clarify in clean start from system completely off - NO SPLASH , then grub then "out of range"

:lolflag: Ha ha! Very funny and very elementary indeed!

OK, we got the idea. I believe that the 800x600 setting in usplash.conf works, because you can see it when shutting down (or rather, rebooting) the computer.

I have suggested playing with xorg.conf because I believed that the config applet in Gnome has somehow screwed it up. But as long as you are happy with the appearance of the desktop after the login screen, then I'd say, my fault, you are right, keep your settings as they are, because xorg.conf only deals with the stage that involves the desktop (the X Window System, literally speaking) at and after the login screen.

But also you should heed the advice of zeifertstc on not using any refresh rate higher than 60 Hz on some LCD screens, and I was wrong once again in giving you the resolutions as *_75, sorry.. :-#

But I honestly believe that this vga thingy will be the remedy for your problem, because we have narrowed down the possibilities. The web page proposed by namanbagga and the table therein states "vga=791" for 1024x768 16 bit screens, but you can also try "vga=792" for a 24 bit screen.

To your second question above, AFAIK, you will add it at the end of the line:
kernel /boot/vmlinuz........... ro quiet splash
as
kernel /boot/vmlinuz........... ro quiet splash vga=791 (or 792)

in the file /boot/grub/menu.lst, all the while backing it up first again by:
sudo cp /boot/grub/menu.lst /boot/grub/menu.bak

Good luck second time. Keep us informed of the result...

---

### Post by Tony3286 on 2007-11-09
You Guys are GREAT! Thanks once again for the step by step directions - Can't wait to try them after work.  Hopefully ** someday** I'll also be able to help someone at the forum. This is what makes Ubuntu work - all the fantastic people willing to give up their time to help people like me - Computer off - screen blank -LOL

Tony

---

### Post by Tony3286 on 2007-11-09
Well Guys - I went into /boot/grub/menu.lst and believe it or not the **VGA=791** was already entered in there. The whole menu reads:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=219b742b-08ac-4190-b76c-14de23ed24e4 ro quiet vga=791 splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=219b742b-08ac-4190-b76c-14de23ed24e4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=219b742b-08ac-4190-b76c-14de23ed24e4 ro quiet vga=791 splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet

title		Ubuntu 7.10, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=219b742b-08ac-4190-b76c-14de23ed24e4 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

Any other suggestions? I'm fit to be tied and I bet your running out of patience too !

---

### Post by Tony3286 on 2007-11-09
Ok this is what I just tried. Since JUST changing the splash screen to 800x600 didn't work **by itself** UNTIL I had changed my xorg, I figured lets put the usplash BACK to 1024x768 like it was - **WRONG**  I restarted and no splash screen again. I now went back to usplash and put it back to 800x600 - **BOOM** splash screen appears on restart. So I figure lets go to /boot/grub/menu.lst and change VGA=791 to VGA=788 to match my 800x600 resolution -** NOPE** - that didn't work - upon restart, splash screen appears but when it boots AFTER grub still same "OUT OF RANGE". I went back to the grub menu and put it back to VGA=791 like it had been.

I just looked at my Xorg and it lists  Horizsync 31.5- 48.0
                                                   Vertrefresh 56.0 - 65.0

Could this be the problem? My Monitor manual states    Horizontal frequency must be in range 30 -80 KHz
                                                                                Vertical frequency in the range 55-75hz

What if I change the Xorg to these setting - do you think I'll blow up anything - LOL or will it help?
The monitor manual states a "Signal Over Range" is a warning that the** input**
signal frequency does not match those supported by the monitor and gives the above ranges and make sure my input signal is within these ranges.

OTHERWISE   I'M LOST ! ! !

---

### Post by Tony3286 on 2007-11-09
I FINALLY GOT IT !!!!!

eye208 WAS RIGHT  !! I was at the end of my rope so figured, what the heck, lets try it!
I didn't change any of the Horizontal or vertical setting in Xorg
BUT you do have to use sudo dpkg-reconfigure -phigh usplash
**AFTER **you change your settings in  gksu gedit /etc/usplash.conf.

So for anyone that is having this** "OUT OF RANGE"** problem:

First thing to do is backup before editing you usplash.conf by using
sudo cp /etc/usplash.conf /etc/usplash.bak
then edit your usplash.config by typing gksu gedit /etc/usplash.conf and making sure
the values are
xres=1024
yres=768
Or what your monitor resolution is - mine, the only resolution that worked was 800x600
Save it,  THEN use eye208's tip type sudo dpkg-reconfigure -phigh usplash

Reboot and see if the out of range disappears - if not go back to the link
Namanbagga  has posted - you will be brought to a page titled 'Ubuntu 7.10 Bootup Resolution Problem"

Also **Many Many thanks to erginemr** - he was the one who walked me through the entire process - step by step - posting every fine detail on backing up, where to place what, etc. Read his posts here relating to the Xorg file.

Thanks to all again!! :)

---

### Post by erginemr on 2007-11-10
Hello Tony,

You are most welcome. You deserved many credits as well with your positive and modest attitude, which has drawn other peoples' attention and will to help you. I have seen a few (fortunately not many) people here who have a problem and ask for help, but in a cocky, arrogant fashion as if other people were paid to help him/her, who then start blaming Ubuntu for his/her problems, who really deserve a RTFM (read the funny ;) manual) response, who then... OK, you get the idea. :p

Anyway, I am very glad that you have solved your problem. Actually, this is the essence of working under Linux. You run into a problem, you read, you sweat, you curse, but in the end, the satisfaction of facing the challenge and beating it in the end is immense. \\:D/ It is like an adventure, it is the soul we had lost long ago with each M$ version trying to hold our hand across the street (but fails miserably).

And guess what, you said you wanted to help other people too, but you have already started helping other people in your last post and thus started your second, underground career as a Linux Consultant. Way to go, bro!

All the best,,,

---

### Post by Cerebrum on 2007-11-18
> **eye208 said:**
> 
If the out-of-range warning appears _after_ the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg



This was my case(splash screen was fine, but out-of-range warning after splash, at the login screen) and I fixed it following your instructions. The only thing that I did differently was that I executed sudo dpkg-reconfigure -pmedium xserver-xorg in a terminal(Applications->Accessories->Terminal). No need to Ctrl-Alt-F2.

thanks!

---

### Post by rtimai on 2007-11-21
I have additional information that might be helpful to Ubuntu newcomers like me, plus a question that's related to the symptoms described here. 

INFO - After a live upgrade to Gutsy I found that TTY1-6 (Ctrl-Alt-F1...F6) were no longer functional -- I got a black screen and flashing cursor, no login prompt, no keyboard input, just a stationary flashing cursor. Fortunately, Alt-Ctrl-F7 still returned me to the Gnome desktop. 

I eventually fixed the TTY1-6 lockup by running Startup Manager (not to be confused with Bootup Manager,) selecting the Advanced tab, and pressing the Restore Defaults button. On closing Startup Manager a back-and-forth progress bar displayed indicating changes were being registered (whatever the correct terminology for this..)  I restarted, and TTY1-6 were functional again. I checked later, and found that Startup Manager removed the VGA=xxx entries from the "kernel" lines in the boot menu list. I think this change fixed the TTY1-6 lockup. Anyway, HTH. 

QUESTION - As others have described, I also see the Signal Out of Range monitor error on startup immediately after the boot menu. But then I see several flashes, as though the video card is successively trying out different resolutions. The monitor then appears to "recover," because a huge full-screen white nVidia logo then appears, followed by the Gnome orange splash screen with the progress bar and scrolling orange text, and then the "face" login prompt. Everything is good. My question is, should I be concerned about the Signal Out of Range error if everything else appears to be working normally? Does the error suggest potential hardware damage? Should I be trying to prevent this error? If so, how? 

Before I switched to Ubuntu from Windows XP Pro, I was seeing this error on this system also. I didn't worry about it, because it appeared to "recover" and proceed normally. Now I am a little worried about it. I have an old setup, nVidia RIVA TNT2 video, Delta DC-770 monitor (max refresh 87,) nVidia Legacy driver.

:confused:

---

### Post by jerrylamos on 2007-11-21
Me too.  

As Gutsy was installed, /etc/usplash.conf was set to 1280x1024.  No way!! The Phillips 150P2 LCD monitor max is 1024x768.

Thanks much, I changed it and will give it a try.

Has anyone made a launchpad bug on this?

Thanks, Jerry

---

### Post by reech on 2007-11-22
I'm having the same issue with gutsy.  I'm using the radeon (OSS) driver,  my LCD monitor is native 1280x1024. The usplash settings are for 1280x1024 and I've tried all the relevant grub vga modes. I've also updated the initramfs with fb modules.

I am at the end with this one - any ideas?

---

### Post by erginemr on 2007-11-23
> **reech said:**
> I'm having the same issue with gutsy.  I'm using the radeon (OSS) driver,  my LCD monitor is native 1280x1024. The usplash settings are for 1280x1024 and I've tried all the relevant grub vga modes. I've also updated the initramfs with fb modules.

I am at the end with this one - any ideas?

Hello,

Did you folllow all the instructions given in this thread, especially those by me and eye208?

> **eye208 said:**
> The proper method to change the splash screen resolution is to edit /etc/usplash.conf and then run

sudo dpkg-reconfigure -phigh usplash

to apply the changes. This step will copy the usplash config file into the ramdisk image used by the kernel on startup.

If the out-of-range warning appears _after_ the splash screen, then you have to reconfigure X.org. This can be done by pressing Ctrl-Alt-F2 (to switch to terminal 2), logging in, and then running

sudo dpkg-reconfigure -pmedium xserver-xorg

Choose manual monitor configuration, then pick the appropriate resolution(s) from the list. When configuration is done, press Ctrl-Alt-Del to reboot.

---

### Post by reech on 2007-11-23
> **erginemr said:**
> Hello,

Did you folllow all the instructions given in this thread, especially those by me and eye208?

Well I did now - tried 800x600 and it worked a treat! - Thank you all.

---

### Post by erginemr on 2007-11-23
Okey dokey. Happy 'bunting, then!

---

### Post by Tsume on 2007-12-11
I love you forever!

I had this same problem and in usplash.conf it listed my res as 1440x1440.  D'oh!  Who the heck has a SQUARE monitor??????

Your fix saved my life now I can see the awesome ubuntu splash, even though it is only there for like 2 seconds because it's such a fast os :p

> **Tony3286 said:**
> I FINALLY GOT IT !!!!!

eye208 WAS RIGHT  !! I was at the end of my rope so figured, what the heck, lets try it!
I didn't change any of the Horizontal or vertical setting in Xorg
BUT you do have to use sudo dpkg-reconfigure -phigh usplash
**AFTER **you change your settings in  gksu gedit /etc/usplash.conf.

So for anyone that is having this** "OUT OF RANGE"** problem:

First thing to do is backup before editing you usplash.conf by using
sudo cp /etc/usplash.conf /etc/usplash.bak
then edit your usplash.config by typing gksu gedit /etc/usplash.conf and making sure
the values are
xres=1024
yres=768
Or what your monitor resolution is - mine, the only resolution that worked was 800x600
Save it,  THEN use eye208's tip type sudo dpkg-reconfigure -phigh usplash

Reboot and see if the out of range disappears - if not go back to the link
Namanbagga  has posted - you will be brought to a page titled 'Ubuntu 7.10 Bootup Resolution Problem"

Also **Many Many thanks to erginemr** - he was the one who walked me through the entire process - step by step - posting every fine detail on backing up, where to place what, etc. Read his posts here relating to the Xorg file.

Thanks to all again!! :)

---

