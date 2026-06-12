---
title: "Skype doesn't show image and can't receive microphone signal"
date: 2010-01-05
forum: Multimedia Software
---

### Post by zanox on 2010-01-05
Hi to all! i've 2 issues with skype:

1) I made some tests and the webcams works, both other people and me are not able to see my image (any library for video decoding missing?). The cam works fine with cheese.

2) Integrated microphone doesn't work, whereas an external one works. The integrated microphone works with "sound recorder" application.

My is a Packard Bell netbook
CPU Atom N270 @1.6GHz, 1GB RAM, 160GB HD
O.S. Ubuntu Karmic Koala 9.10

Thank you in advance :guitar:

---

### Post by egruber on 2010-01-05
I have a similar issue.  I have a Thinkpad T40 with Koala and a Logitech cam.  I finally got the internal mike to work, but the receiving video had tremedous lag.  Maybe 30 seconds.  The other person could see me, but their video kept freezing on my T40.  And my 'monitor' window did not show me, even though the caller could see it.

But there is something funky with the mic.  The sound quality was poor.  Under SKYPE options, it would not show me the mic in the webcam.  But the Sound Recorder app could see it.

I tried it with a Windows 7 PC right afterwards, and it worked fine.  Is there some sort of setting that needs to be checked?

---

### Post by zanox on 2010-01-05
I also wrote on italian ubuntu forum and on skype forum, let wait the answers! ;)

none can help us??

---

### Post by gradinaruvasile on 2010-01-13
The camera:

Press alt+f2, type in:

gstreamer-properties

Go to the video tab, select pc camera (or whatever is available as "Device" besides "Default"), press Test. May involve changing the input plugin from "Video for Linux" to "Video for Linux 2", but the camera should be available under video for linux 2. 
If its working, the webcam is configured by the system correctly.

For Skype, first make sure you are using the latest version (2.1.0.47, available on the Skype site), then try the following:
Open a terminal and launch skype by typing (copy-paste):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and press enter. See if you can test the webcam from Skype's Options.

The mic:

First of all,make sure UNTICK the damn "Allow Skype to automatically adjust my sound levels" from Skype -> Options -> Sound devices.

Then right-click on the sound icon in the system tray -> Sound Preferences -> Input. Check the record level. It may be lowered by the Skype's automatic adjustments.
Tap the laptop (better the mic if you know where it is located) with your fingers (fingernails is best) to see if there is any input on the input level indicator.

---

### Post by zanox on 2010-01-14
So, I tried.

The terminal gave me this error:

"X Error, request 132, minor 18, error code 8 BadMatch (invalid parameter attributes) "

skype is the last from site and gstreamer test works. Webcam works! I said it! Other people can see me, I can't see them (and myself)

Micro doesn't work too, I tried also with Audacity and works fine, so it isn't a hardware issue... other suggestions?

---

### Post by gradinaruvasile on 2010-01-14
Ok, so your webcam works. Then no need for the ld_preload thingie.

Then it should be an xv overlay issue (driver).
Disable desktop effects if they are on (System -> Preferences -> Appeareance -> Visual effects). And launch gstreamer-properties and set the vide o out device to xv.

Launch skype in a terminal to test it.


Also, check in Skype in the Options -> Sound Devices Menu what device is associated with the input. 
And in the systems sound preferences menu check if you have an option to select manually the microphone.

---

### Post by zanox on 2010-01-14
So, before to try it I must say that I found on skype's forum that closing cairo dock (and also removing it for starting applications, rebooted pc), skype works correctly except that when I close it it gives this error and crashes: "X Error, request 42, minor 0, error code 8 BadMatch (invalid parameter attributes)". I have to test it calling, then I'll report it here..

For sound it gives me only "pulseaudio" option... I can change it from pulseaudio settings whatever.. but it doesn't work..

Calls works perfectly with external microphone, internal one works with pulseaudio input monitor but gives no signal in audio preferences... external works in both... and how to bypass closing cairo and rebooting?

I forgot... Thank you for your help!!

p.s. it stopped crashing on closing

ok! Serching lead me to this:

"this is a know Qt4 issue
you have to set XLIB_SKIP_ARGB_VISUALS before launching a Qt4-based program"

chaging launcher to: "export XLIB_SKIP_ARGB_VISUALS=1 && skype"

it works!!!!!

now remain the microphone issue...

---

### Post by Arla on 2010-01-14
Have you tried the Alsa-backports? I know I had internal mic issues with Ubuntu until I added in the Also-backports and then it worked perfectly.

Module is linux-backports-modules-alsa-... (not sure what the latest one is)

---

### Post by egruber on 2010-01-14
> **zanox said:**
> ok! Serching lead me to this:

"this is a know Qt4 issue
you have to set XLIB_SKIP_ARGB_VISUALS before launching a Qt4-based program"

chaging launcher to: "export XLIB_SKIP_ARGB_VISUALS=1 && skype"

it works!!!!!

now remain the microphone issue...

I would like to try this, but I don't know how to change the launcher.  Can you provide some guidance?  And what is QT4 anyway?  Thanks!!

---

### Post by zanox on 2010-01-14
You may try the trick simply copying and pasting the line  in a terminal too. If it works, see the following lines.. ;-)

I have menus in italian, so I try to translate. Go to main menu -> (system) preferences -> main menu. You get a window showing the links to applications divided by type. Enter in Skype's one (maybe "internet") e then double click on its link or click "edit" at the right in the window, then you have link parameters. Change "skype" with the posted one and then confirm editing. ecit menus and start skype. You may try the trick simply copying and pasting the line  in a terminal too.

I'm not a software builder, I think Qt4 is an interface, like GTK+...

---

### Post by egruber on 2010-01-14
I will have to test this.  It did execute in the terminal and launch skype.  But when I put it in the launcher, I get an Error box pop up which says "Could not launch SKype.   Failed to execute Child Process 'Export' (no such file or directory)."

> **zanox said:**
> You may try the trick simply copying and pasting the line  in a terminal too. If it works, see the following lines.. ;-)

I have menus in italian, so I try to translate. Go to main menu -> (system) preferences -> main menu. You get a window showing the links to applications divided by type. Enter in Skype's one (maybe "internet") e then double click on its link or click "edit" at the right in the window, then you have link parameters. Change "skype" with the posted one and then confirm editing. ecit menus and start skype. You may try the trick simply copying and pasting the line  in a terminal too.

I'm not a software builder, I think Qt4 is an interface, like GTK+...

I did test this.  I launched skype via the terminal command you supplied, left the terminal window open and made a video call. The audio was fine.  The other person could see me and hear my audio.  But I could only hear their audio.  When they started their video, I only saw a blank screen.  But the terminal windows showed a bunch of these messages

X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation) 
X Error, request 132, minor 18, error code 11 BadAlloc (insufficient resources for operation) 

Any ideas???  Do I not have enough memory or something?

I got past the error.  I went to my PC's Appearance settings and turned off the Visual Effects (it was previously set to normal).  Then I stopped getting terminal errors I listed above.  I guess the Visual Effects was taking up video resources and memory.


And Skype doesn't seem to perform much differently with the terminal command you supplied or just starting it with 'Skype' via the launcher.  Any comments???

---

### Post by gradinaruvasile on 2010-01-14
zanox:

Launch alsamixer in a terminal. Press tab to go to the "capture" view. Take a screenshot of it and post it here. You might have problems with low mic capture levels settings in the alsa setup.

---

### Post by av8rbri on 2010-01-14
> **gradinaruvasile said:**
> The camera:

Press alt+f2, type in:

gstreamer-properties

Go to the video tab, select pc camera (or whatever is available as "Device" besides "Default"), press Test. May involve changing the input plugin from "Video for Linux" to "Video for Linux 2", but the camera should be available under video for linux 2. 
If its working, the webcam is configured by the system correctly.

For Skype, first make sure you are using the latest version (2.1.0.47, available on the Skype site), then try the following:
Open a terminal and launch skype by typing (copy-paste):

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

and press enter. See if you can test the webcam from Skype's Options.

The mic:

First of all,make sure UNTICK the damn "Allow Skype to automatically adjust my sound levels" from Skype -> Options -> Sound devices.

Then right-click on the sound icon in the system tray -> Sound Preferences -> Input. Check the record level. It may be lowered by the Skype's automatic adjustments.
Tap the laptop (better the mic if you know where it is located) with your fingers (fingernails is best) to see if there is any input on the input level indicator.



I am having issues with no vid in skype [running 8.04] and everything BEFORE the LD preload thing works -- including the video......  when I C+P verbatim the code in a term. window, I get this:   

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

and then the skype login window pops up.......  no idea what to do next?

Thanks.

---

### Post by gradinaruvasile on 2010-01-14
Are you using the 64-bit version of Ubuntu 8.04? 
Then the path is slightly different:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Also, i dont know that 8.04 has these compatibility libraries included by default.

---

### Post by av8rbri on 2010-01-15
> **gradinaruvasile said:**
> Are you using the 64-bit version of Ubuntu 8.04? 
Then the path is slightly different:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Also, i dont know that 8.04 has these compatibility libraries included by default.

Hi there. No, it is not 64 bit.....   

I neglected to say that it works with luvcview, cheese, NOT camorama, and it works with aMSN......  It is a Logitech Webcam c600  which according to [http://linux-uvc.berlios.de/#devices](http://linux-uvc.berlios.de/#devices), should have worked...... and i do have the latest 2.1.0.47 installed right now. The sound works, just no video...

just tried the above - got this:  ERROR: ld.so: object '/usr/lib32/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.


Thanks,
B

---

### Post by zanox on 2010-01-16
Do you have that file? Maybe you have to install some library... try to search "v4l1compat" in synaptic and install it (if is there)

---

### Post by egruber on 2010-01-21
Skype just released a new version for Ubuntu on their website.  Try it and see if it works better.

---

### Post by JaseP on 2010-06-27
Using "export XLIB_SKIP_ARGB_VISUALS=1 && skype" worked for me using Skype 2.1 with Ubuntu 10.04 Lucid Lynx, solving the no video with a Logitech QuickCam MP S5500 problem,... (figured I'd tag this message with as many search terms as possible, to help others).

Thanks for the tip, Xanox...

---

### Post by drumour on 2010-08-02
argb visuals fix in post above got video/desktop sharing working for me too.Using Ubuntu lucid 32bit, Cairo-dock and Logitech web cam - everything was already working at Ubuntu level.

---

### Post by ahbart on 2010-08-02
> **gradinaruvasile said:**
> The mic:
First of all,make sure UNTICK the damn "Allow Skype to automatically adjust my sound levels" from Skype -> Options -> Sound devices.

Then right-click on the sound icon in the system tray -> Sound Preferences -> Input. Check the record level. It may be lowered by the Skype's automatic adjustments.
Tap the laptop (better the mic if you know where it is located) with your fingers (fingernails is best) to see if there is any input on the input level indicator.

Did you try this! 
Have you checked the Skype Call Testing Service. (found as a button on the sound settings tab). It happened to me more then ones, that problems were caused by settings on the other end of the line. ;-)

I've always had more success with alsamixer/gnome-alsamixer. It could be a muted mic or lowered capture level.
Bart

---

### Post by ahbart on 2010-08-02
> **av8rbri said:**
> I am having issues with no vid in skype [running 8.04] .......  no idea what to do next?
Thanks.

@av8rbri: It would be better if you opened a new thread for this. Two questions in one thread is very confusing.

---

### Post by Nick Brohman on 2010-08-02
> **zanox said:**
> Hi to all! i've 2 issues with skype:

1) I made some tests and the webcams works, both other people and me are not able to see my image (any library for video decoding missing?). The cam works fine with cheese.

2) Integrated microphone doesn't work, whereas an external one works. The integrated microphone works with "sound recorder" application.

My is a Packard Bell netbook
CPU Atom N270 @1.6GHz, 1GB RAM, 160GB HD
O.S. Ubuntu Karmic Koala 9.10

Thank you in advance :guitar:

1) Did you use the Skype test as asked in a post here? Make sure the options for Skype Video and Start My Video are enabled? Do you have Cheese running simultaneously with Skype? If so, close it. It is hogging the video! Are you receiving Video? Sorry if that's been asked and answered, can't recall seeing a ref.to that.

Run gstreamer-properties in a terminal and set your video devices Output to X Window System (X11/XShm/Xv) [COLOR=Magenta]***not Xv***[/COLOR], that will get the graphics card doing the work in lieu of the CPU working it's b...off. De-select Default for what the Device box offers.[COLOR=Red]*** Video for Linux 2 (v4l2)***[/COLOR] in Input and that the Device is your camera, not default

2) That seems to be a Koala/Pulse thing. [COLOR=Red]***Either***[/COLOR] get rid of Pulse _[COLOR=Blue]***carefully***[/COLOR] as some of the packages are needed_ by Skype [COLOR=Red]***OR***[/COLOR] just grimace and bear using an[COLOR=Teal] **external mic..**[/COLOR] that [COLOR=Teal]**is the easiest way to fix**[/COLOR] the audio out other than ensuring that your Volume Control is optioned correctly....it can be a devil and mute itself when shutting down/booting up.

I assume that you have no trouble receiving audio from the phone.

With my Athlon X2, I had to remove Pulse and always have the ALSA mixer open. A different story with my Presario CQ61 T3000 Celeron CPU as it was virtually plug and play with that Pulse monster.

It's well after the witching hour and I need my ugly sleep, I'll post some links later today, that may/may not be of use....g'nite..

---

### Post by Joe Driller on 2010-08-30
Hi all, using:

       export XLIB_SKIP_ARGB_VISUALS=1 && skype

on a console works fine on my Presario C735EM on ubuntu 10.4 64 bits, video problem is solved but its impossible to launch Skype from menu launcher with that code. What's wrong??? I am not a Ubuntu gurú so any help wil be wellcome.


Thanks in advance.

---

### Post by pablotdl on 2010-09-10
> **zanox said:**
> ok! Serching lead me to this:

"this is a know Qt4 issue
you have to set XLIB_SKIP_ARGB_VISUALS before launching a Qt4-based program"

chaging launcher to: "export XLIB_SKIP_ARGB_VISUALS=1 && skype"

it works!!!!!

now remain the microphone issue...

This did the trick for me! Thanks!

---

### Post by pablotdl on 2010-09-10
Add this line in /usr/bin/skype-wrapper, before the line that executes the skype command

> export XLIB_SKIP_ARGB_VISUALS=1

Worked for me

---

### Post by antti64 on 2010-09-11
> **gradinaruvasile said:**
> Are you using the 64-bit version of Ubuntu 8.04? 
Then the path is slightly different:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Also, i dont know that 8.04 has these compatibility libraries included by default.

Thanks! This did work for me. I have had Skype working fine in Ubuntu 8.04, but it has failed in 9.10 and 10.04. I have AMD-64bit engine and Skype 2.1.0.82. The above works great. I can see video output in gstreamer-properties, but in Skype. 

My next problem is to replace Skype starter in Desktop-bar. Internet->Skype. How can I alias that with LD_PRELOAD options?

Antti

---

### Post by antti64 on 2010-09-11
> **pablotdl said:**
> Add this line in /usr/bin/skype-wrapper, before the line that executes the skype command



Worked for me

Sorry? I don't have skype-wrapper. How do you implement this? Do you rename executable skype, which you call by /usr/bin/skype then?

Antti

---

### Post by Protocol84 on 2010-10-30
To implement this create a skype.sh file as thus:

#/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1 && skype

mark it as executable and point your launcher at it

(this is the first bash file I have ever made :) isn't it cute!?!?)

---

### Post by patanaheen on 2010-12-02
1. make a new file from terminal 

sudo gedit /usr/local/bin/skype-wrapper

2. paste the following lines in it 

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export XLIB_SKIP_ARGB_VISUALS=1
skype &

3. change it to executable from terminal 

sudo chmod 755 skype-wrapper

4. go to preferences > main menu > internet > skype  and click properties and in the command textbox type

/usr/local/bin/skype-wrapper

After this executing skype-wrapper from terminal or clicking skype from menu item all works .. i have ubuntu 10.10 and needed both variables exported for the webcam to work ..

---

### Post by Protocol84 on 2010-12-02
Is there any way to make skype use these commands automatically? Whenever I start up my computer skype starts automatically from being remembered from the last session and the video doesn't work.

I have made a startup script to launch skype at startup with the arguments, but then I have 2 instances of skype at startup, 1 remembered that doesn't work and is logged in and 1 that will work when I shut the other one down and log in.

IDK can I rename the skype launcher in /usr/bin/ and then make a script named skype that will launch the renamed original launcher with the arguments provided even when the program is started automatically by the system? 

^^edit^^
well that worked as far as making so I can just type in skype to the terminal and my video works, but still no video at startup, so I guess when it "remembers" it doesn't simply run the skype command to bring it back.
^^edit^^

Kind of a round about way of doing it I suppose... I am trying to find out if I can exclude skype from being remembered in my desktop session so my startup script will do the loading. There is a way to do this in KDE but I am still trying to find a work around for GNOME.

---

### Post by tin22ooo on 2011-01-15
> **patanaheen said:**
> 1. make a new file from terminal 

sudo gedit /usr/local/bin/skype-wrapper

2. paste the following lines in it 

export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export XLIB_SKIP_ARGB_VISUALS=1
skype &

3. change it to executable from terminal 

sudo chmod 755 skype-wrapper

4. go to preferences > main menu > internet > skype  and click properties and in the command textbox type

/usr/local/bin/skype-wrapper

After this executing skype-wrapper from terminal or clicking skype from menu item all works .. i have ubuntu 10.10 and needed both variables exported for the webcam to work ..

Thanks' Patanaheen !! your solution worked for me, on hp notebook, intel 945 grafics, and a4tech webcam. !!

---

### Post by ExemplarUbuntu on 2011-02-13
I've just tried that to try to get the Skype mic working but skype crashes as soon as a connection is made.

---

