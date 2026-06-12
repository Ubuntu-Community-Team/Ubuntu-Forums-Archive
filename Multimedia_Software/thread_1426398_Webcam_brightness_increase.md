---
title: "Webcam brightness increase?"
date: 2010-03-10
forum: Multimedia Software
---

### Post by Senuf on 2010-03-10
Hello. I know this topic has somehow been covered, but I could find no answer to this specific problem.

Ubuntu, in its most recent version (9.10) has stopped to support certain webcams that it previously supported with just plug-and-play simplicity. After many searches on the web, I could somehow managed to make my old webcam (Logitech QuickCam Traveler) work. Skype couldn't see it, but adding the command *[COLOR="Gray"]bash -c 'export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so; skype'[/COLOR]* to the launcher, worked the miracle.

Whatever, the image was very dark, and in a new web search I found a solution ([http://wiki.eeeuser.com/howto:installskype20beta#controlling_the_brightness_contrast_etc_of_video_in_skype]("http://wiki.eeeuser.com/howto:installskype20beta#controlling_the_brightness_contrast_etc_of_video_in_skype")).
As stated there, I opened the Terminal and entered:

```
v4lctl bright 100%
```

All is OK, brightness gets up, I can finally see my face (not a great view, but I somehow got away with it) in Skype's test, but I need that change to be PERMANENT, so every time my parents open Skype (it's my parents' computer) they won't have to mess with Terminal (they're 69 and 72 years old, it's their first computer, so **I CAN NOT** expect them to use Terminal, they just want to open Skype and use it, as they did when they used Windows (until two weeks ago, when I finally convinced them to switch).

Thanks a lot in advance.

Senuf

---

### Post by shrimpy89 on 2010-03-10
I'm no script genius, so someone correct me if I'm wrong.  But I believe this would work:

Open a new window in gedit, copy:
```
#!/bin/bash
v4lctl bright 100% && skype;
```

save it as .skype_launch.sh in your home directory.
in the terminal, type

```
chmod a+x .skype_launch.sh 
```

Then set this script to the desktop/menu launcher as Skype.  It should run your command each time you open it.

---

### Post by Senuf on 2010-03-10
Thanks a lot for coming in aid, shrimpy89!
I did something like that, but it seemed that for the brightness correction to function, Skype has *already* to be up and running, so to speak.

What I finally did was this:
I added a launcher with no more than "v4lctl bright 100%" as a command, and "Brillo" (brightness, in spanish) as its name (for the tooltip's sake). Then, in inkscape I made a beauuuutiful icon (well, sort of), and then, after saving it as an svg file, selected it as the icon for said launcher up there in the panel/menu, just besides a Skype icon. Then, I'll tell my parents this: "open skype with a click on that light blue icon. Once it's open, click that beautiful brightness icon besides the light blue one."
Not the best of solutions but, hey, not bad for a *know-nothing*!

---

### Post by Atilana on 2010-03-10
When you already instal the software, check on options and change the brightness

---

### Post by shrimpy89 on 2010-03-10
Glad you were able to find a simple solution!  Maybe in my script you could swap v4lctl bright 100% and skype, so skype launches first.  But then again, "if it isn't broke, why fix it?" :P

---

### Post by Senuf on 2010-03-10
> **Atilana said:**
> When you already instal the software, check on options and change the brightness

Sorry, I haven't found that option in Skype. At least not in this version and with this webcam. If it's there, I **BEG** you to tell me where!!!


And to Shrimpy: Yup, I tried doing in one command the skype thing first and then, after the "&&", the brightness trick, but had no luck. Dunno why.

Well, thanks A LOT for the answers, and if there are no more ideas in a few hours, this thread will be considered solved.

Greetings from Buenos Aires (far down south, for most of you).

Senuf

---

### Post by no2498 on 2010-03-10
skype may help you more
i have a nice how to from skype works good on this computer with 804
dose not work at all on the other computer with 910
ubuntu went an added  all webcam drivers together can not adjust but the brightness 
you may try setting the brightness in ekiga softphone 
i have seen it work on all cam settings at times

---

### Post by Senuf on 2010-03-10
> **no2498 said:**
> skype may help you more
i have a nice how to from skype works good on this computer with 804
dose not work at all on the other computer with 910
ubuntu went an added  all webcam drivers together can not adjust but the brightness 
you may try setting the brightness in ekiga softphone 
i have seen it work on all cam settings at times

Thanks a lot for your suggestion. The thing is... Most relatives ofmy parents live abroad and use Skype, which doesn't get along well with Ekiga (not to say that they don't get along at all or, to be more precise, that Skype despises standard protocols, which Ekiga use).

Yup, I kinda remembered that I COULD adjust brightness in Skype under Ubuntu 8.04. Now, through your post, I see it was so and not a trick of my faulty memory.

As things are, especially for my parents, coming from Skype under Windows, I'll let them stay with Skype and the unorthodox solution I found for 'em.

Thanks a lot to all of you!



Senuf

---

### Post by majster on 2010-11-15
Unfortunately not working for me :(
This is what i get:

```
# v4lctl list
ioctl: VIDIOC_G_STD(std=0x804f07bbff44e48 [PAL_H,PAL_D1,PAL_N,PAL_Nc,PAL_60,?,SECAM_G,SECAM_K,SECAM_K1,SECAM_L,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
attribute  | type   | current | default | comment
-----------+--------+---------+---------+-------------------------------------
norm       | choice | (null)  | (null)  |
input      | choice | zc3xx   | zc3xx   | zc3xx
contrast   | int    |     128 |     128 | range is 0 => 255
Gamma      | int    |       4 |       4 | range is 1 => 6
Auto Gain  | bool   | off     | on      |
Light freq | choice | NoFlike | NoFlike | NoFliker 50 Hz 60 Hz
Sharpness  | int    |       2 |       2 | range is 0 => 3

```There is no "bright" there... so i tried:
```
v4lctl "Auto Gain" off
```outpu:
```
# v4lctl "Auto Gain" off
ioctl: VIDIOC_G_STD(std=0x804f07bbfa31478 [PAL_H,PAL_I,PAL_D,PAL_D1,PAL_Nc,NTSC_M,SECAM_B,SECAM_D,SECAM_K1,?ATSC_8_VSB,ATSC_16_VSB,(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)]): Invalid argument
no handler for Auto Gain

```And no changes in "v4lctl list" and no changes i capture ( still dark )
but i noticed that when i run XawTV and change Auto Gain option to OFF it change it in v4lctl list as well. 
The problem is it is going back to default after reboot.

Any ideas ?

[ Ubuntu 10.10, Logitech, Inc. QuickCam E2500 series ]

---

### Post by no2498 on 2010-11-15
try this


for other cameras, you'll want to adjust to different values.

My optimal settings were:
Gamma: 4
Red: 290
Green: 310
Blue: 315

Go to the the Linux Video settings directory:
CODE
cd /sys/module/gspca/parameters/


EVERY FOLLOWING COMMAND MUST BE RUN AS ROOT! (sudo doesn't handle the ">" redirection stuff elegantly without weird escaping, which I haven't mastered yet)

CODE
sudo su


And echo new values to the gamma and color files:
CODE
echo 4 > /sys/module/gspca/parameters/gamma
OR
echo 290 > /sys/module/gspca/parameters/GRed
OR
echo 310 > /sys/module/gspca/parameters/GGreen
OR
echo 315 > /sys/module/gspca/parameters/GBlue

After tweaking with these, right click the skype systray icon, and chose "Options", then "Video Devices", then click the video "Test" button to check it out. You'll need to close and reopen the options window after each change.

Once you've tweaked to the best config possible, save the module settings permanently to /etc/modprobe.d/options:

Add these lines (with your values) to the "/etc/modprobe.d/options" file:
CODE
options gspca gamma=4
options gspca GRed=290
options gspca GGreen=310                       sudo gedit /etc/modprobe.d/options 
options gspca GBlue=315

---

### Post by majster on 2010-11-15
Thanks for respond!

In /sys/module i got only "gspca_zc3xx" and "gspca_main" folders and none of them contains :

/parameters/gamma
/parameters/GRed
/parameters/GGreen
/parameters/GBlue

```
gspca_zc3xx/
|-- drivers
|   `-- usb:zc3xx -> ../../../bus/usb/drivers/zc3xx
|-- holders
|-- initstate
|-- notes
|-- parameters
|   `-- force_sensor
|-- refcnt
|-- sections
|   |-- __mcount_loc
|   `-- __param
`-- srcversion

6 directories, 6 files

``````
gspca_main/
|-- holders
|   `-- gspca_zc3xx -> ../../gspca_zc3xx
|-- initstate
|-- notes
|-- parameters
|   `-- debug
|-- refcnt
|-- sections
|   |-- __kcrctab
|   |-- __ksymtab
|   |-- __ksymtab_strings
|   |-- __mcount_loc
|   `-- __param
`-- srcversion

5 directories, 9 files

```

---

### Post by no2498 on 2010-11-16
sorry this was to be over more

sudo gedit /etc/modprobe.d/options

you need to make it yourself

---

### Post by majster on 2010-11-16
Update to my issue:

webcam works ok in cheese... but if i change resolution ( in cheese ) from 640x472 to 320x232 the capture goes dark... ( the same as in skype, XawTV and Camorama )
When i switch it back to 640x472 brightness coming back again...

In skype, XawTV and Camorama for first 2-3sec. it works ok, and them it going dark ( visible but very dark ) 

I also tried to edit $home/.Skype/$username/config.xml with:
<Video> 
   <CaptureHeight>480</CaptureHeight> 
   <CaptureWidth>640</CaptureWidth> 
</Video> 

But no luck...
:confused:


Also i tried make a file /etc/modprobe.d/options and /etc/modprobe.d/options.conf
still no luck...



How can cheese works just fine and rest not ?? cant stand it....

---

### Post by no2498 on 2010-11-17
ubuntu/linux give cheese all the webcam settings
as of late my 2 cams went to heck
cant change any settings at all now
804 and 10.04

---

### Post by majster on 2010-11-21
I manage to fix my brightness  camera problem :):popcorn:

this is what i done:


Install this package ( because the v4lctl couldn't change "auto gain" option on my cam.:
```
sudo apt-get install uvcdynctrl
```and then to startup skype file add this line on 2nd line:
```
uvcdynctrl -s 'Auto Gain' -- off
```
Maybe it will help someone

---

### Post by jtbo on 2011-05-28
v4lctrl is not installed, you can install it by apt-get install xawtv.

xawtv is not available, it is replaced by v4l-config

v4l-config is already installed.

However there is nothing that can be done with it...

So apt-get install uvcdynctrl .... There are no packages containing uvcdynctrl...

Is it really necessarily to change names of these little programs every 6 months or so? 

All that I would need to do in Windows would be to click with mouse on box that says "Outdoor" so that Creative NX Pro would not be so insanely bright, but it surely is not very simple as all guides point to programs that are not to be found, not even as I have added and changed repos etc.

As none of help in this thread is not working, what next, where to get those packages for programs mentioned?

---

### Post by nerdy_kid on 2011-05-28
> **jtbo said:**
> v4lctrl is not installed, you can install it by apt-get install xawtv.

xawtv is not available, it is replaced by v4l-config

v4l-config is already installed.

However there is nothing that can be done with it...

So apt-get install uvcdynctrl .... There are no packages containing uvcdynctrl...

Is it really necessarily to change names of these little programs every 6 months or so? 

All that I would need to do in Windows would be to click with mouse on box that says "Outdoor" so that Creative NX Pro would not be so insanely bright, but it surely is not very simple as all guides point to programs that are not to be found, not even as I have added and changed repos etc.

As none of help in this thread is not working, what next, where to get those packages for programs mentioned?

try v4l2ucp

---

### Post by jtbo on 2011-05-28
> **nerdy_kid said:**
> try v4l2ucp

Thank you from suggestion, it seems that my installation does not find even that package anymore, it has not been online after installation, I did read Jaunty from somewhere, so I guess that is too old to get any software?

It is machine that just monitors activity via webcam and other machine takes files from it and pushes to ftp, very old machine also, so updates are usually more trouble than worth for it. 

Maybe I need to rebuild (PITA) with some LTS version instead trying to fix. I really would like to have set it and forget it installation, just needed to replace webcam and this one option would need to be set, I find rebuilding system is bit of overkill for it?

edit: So I did install new distro, Mint as it is so much praised all over, remembered then why I did wanted new one, dvd drive was broken, wifi driver had to be downloaded and no wired network available, but worst of all issues is that webcam goes connection to camera lost with these new distros every 30 seconds or so (it is truly random really), then it randomly gets either ok pic or way too bright pic. In those short moments when it does work image quality is better of course. Old half broken equipment is tough to deal with sometimes.

However now I got v4l2ucp and I do have some control over the gamma settings, which is at least something.

Using now Mint 10, Motion 3.2.12, Creative NX Pro (very old, 2004 or so, still better image in dark than most new ones, but it has fault in pcb as sometimes need to twist it to get colours right in picture) and POS Acer Aspire 3100, which has motherboard fault so typing need to be done gently or it does freeze, reusing some old junk here.

---

### Post by nerdy_kid on 2011-05-30
> **jtbo said:**
> Thank you from suggestion, it seems that my installation does not find even that package anymore, it has not been online after installation, I did read Jaunty from somewhere, so I guess that is too old to get any software?

It is machine that just monitors activity via webcam and other machine takes files from it and pushes to ftp, very old machine also, so updates are usually more trouble than worth for it. 

Maybe I need to rebuild (PITA) with some LTS version instead trying to fix. I really would like to have set it and forget it installation, just needed to replace webcam and this one option would need to be set, I find rebuilding system is bit of overkill for it?

edit: So I did install new distro, Mint as it is so much praised all over, remembered then why I did wanted new one, dvd drive was broken, wifi driver had to be downloaded and no wired network available, but worst of all issues is that webcam goes connection to camera lost with these new distros every 30 seconds or so (it is truly random really), then it randomly gets either ok pic or way too bright pic. In those short moments when it does work image quality is better of course. Old half broken equipment is tough to deal with sometimes.

However now I got v4l2ucp and I do have some control over the gamma settings, which is at least something.

Using now Mint 10, Motion 3.2.12, Creative NX Pro (very old, 2004 or so, still better image in dark than most new ones, but it has fault in pcb as sometimes need to twist it to get colours right in picture) and POS Acer Aspire 3100, which has motherboard fault so typing need to be done gently or it does freeze, reusing some old junk here.

I'm using natty, and v4l2ucp is in the repos here...
[edit]
oh you are saying you are using jaunty?  hmm, not sure about that, I'd upgrade to at least 
[edit2]
yeah, jaunty is unsupported, so I'd upgrade if you can.

---

### Post by wayfarer_boy on 2012-01-19
Thanks for the tip, nerdy_kid.  My own webcam, rather than capturing too dark, would begin by working perfectly and then increase in brightness over time, finally becoming a bleached-out sea of white.

I'd tried lots of tools to correct the brightness, most of which couldn't connect to the webcam while I was using it (in Google Hangouts, for example).  If I stopped the webcam to access it via the tool, the problem would immediately go away.

v4l2ucp allows me to access the webcam while it's running, and so correct the brightness problem (running GoogleTalkPlugin in Oneiric, that is).

---

