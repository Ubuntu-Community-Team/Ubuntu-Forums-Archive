---
title: "I just want dual displays !!!!"
date: 2009-03-07
forum: Multimedia Software
---

### Post by gbswales on 2009-03-07
I really am trying (for the 5th time!) to get to try Linux to work properly (ie the way I want it) but althugh a much smoother install it still gets technical on me.  For example, even though I have installed the nVidia drivers this only runs one of my displays - I have two and like to have different programmes in each window - I tried playing with settings in the nVidia X panel (grr how helpful is that tool nVidia) The best i achieved was to get the wallpaper on both windows but no access to drag windows across to the main display - also no matter which one i set as the main display it still puts all the menu bars on my second screen.  I keep getting so near and so far - the other problem is now that it wont save new configurations after I set them

I have read a few posts but it goes into command line detail where I dont want to go - in windows I just select which display I want and how I want them to work and it just....works. I run a free piece of software to put different wallpaper on each screen and bingo I have the set up I want.  I just want to do the same thing in Linux (to be fair its the last barrier I think because the install really has got much better)

My graphics card is nvida 7300

Sorry if this is already posted somewhere but the search returns an error in IE8

---

### Post by hansdown on 2009-03-07
Hi gbswales.

Hopefuly this helps.

[http://www.google.ca/search?q=+dual+displays++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+dual+displays++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by gbswales on 2009-03-08
> **hansdown said:**
> Hi gbswales.

Hopefuly this helps.

[http://www.google.ca/search?q=+dual+displays++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=+dual+displays++in+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Yes I had found these already, google is always my first stop, but most of them illustrate my problem with Linux - all of them suggest writing lines of code and editing files - I havent yet found out where all these files are stored or how to get to a command line in Ubuntu - however I dont think that many non technical end users would want to do this.  I think however that the main problem is that when I make changes through the gui and try to save them it tells me it cant save (but doesnt say why)- I suspect it is because the programme does not prompt me for my admin password - is there someway I can force ubuntu to keep me logged in as admin - I tick the remember for session box but it doesnt seem to work.

I wonder could my issues be connected with running Ubuntu virtually using Wubi?. I wanted to install on a resized partition from the live CD but the sparse information in the new partitioner tool made me nervous to do so as there was nothing there which showed any of my other drives  - I only want to create a small partition for linux and work with files which are in my windows folders. Wubi however is not a solution as I cant mount my C drive because it is where the host file is stored

---

### Post by norwoods on 2009-03-08
you are correct that you cannot save the settings without admin  .
you get a command line by starting Applications--Accessories--Terminal
you get admin privileges by starting a program with sudo or gksu for gnome programs:
sudo nvidia-settings
or 
gksu nvidia-settings

---

### Post by gbswales on 2009-03-08
> **norwoods said:**
> you are correct that you cannot save the settings without admin  .
you get a command line by starting Applications--Accessories--Terminal
you get admin privileges by starting a program with sudo or gksu for gnome programs:
sudo nvidia-settings
or 
gksu nvidia-settings

:(yoyu lost me aound line 3 - I am not sure which one to use - also if I do this will it open the nvidia gui interface? Surely ubuntu should be intelligent enough to remember I am an admin and open settings programmes with the right privileges?

I really am trying to love linux because one day soon I may no longer have access to free windows upgrades or home use microsoft sofware.  However I dont really have much time at the moment to sit and learn new stuff just trying to find easy ways to do what I want. When I retire I may have more time to get interested but for now I just need idiots guides.

Thanks for the help though - I am not unappreciative 
Clive

---

### Post by gbswales on 2009-03-08
> **gbswales said:**
> :(yoyu lost me aound line 3 - I am not sure which one to use - also if I do this will it open the nvidia gui interface? 

I should add that I know nothing about what interfaces I am using - it is a default Wubi install and all that has been added is the nvidia driver package that it reccommended (before that I had to start up in safe graphics mode or I just got coloured patterns on my two screens) In safe graphics i see both screens replicated - I need them to operate like one long desktop though preferably with their own wallpaper - I should also mention that they are different screen sizes, one is widescreen 19" (1440x900)connected by DVI the other a standard 17" monitor (1280x1024)connected by vga

---

### Post by norwoods on 2009-03-08
> **gbswales said:**
> :(yoyu lost me aound line 3 - I am not sure which one to use - also if I do this will it open the nvidia gui interface? Surely ubuntu should be intelligent enough to remember I am an admin and open settings programmes with the right privileges?

Thanks for the help though - I am not unappreciative 
Clive

OK, i will pick one of the two for you.  since the nvidia gui interface is a gnome application, type:
gksu nvidia-settings
and your password when it asks.

the ubuntu philosophy is to operate at minimal privilege, not admin mode, unless necessary.  ubuntu is intelligent enough to remember I am an admin and open settings programmes with the right privileges if you set them.  open System--Preferences--Main Menu.  under Menus:, click System Tools.
under Items:, click NVIDIA X Server Settings. click properties.  in the Command: text box, insert "gksu " in front of 
/usr/bin/nvidia-settings. click close. click close. 
now when you open Applications--System Tools--NVIDIA X Server Settings, it will ask for a password and you will be in admin mode.

when the nvidia gui interface is running, click X Server Display Configuration.  click Configure... . click the TwinView radio button.  click OK.  set up anything you want. click Save to X Configuration File.  click Quit.

---

