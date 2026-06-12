---
title: "Problems with flash player in Ubuntu 11.10"
date: 2011-10-14
forum: Multimedia Software
---

### Post by Friwise on 2011-10-14
Hi all!!
I have just (some hours ago) updated from 11.04 to 11.10. I am really happy for the result.
However, I have a huge problem with flash player. It seems that firefox decided to disable my outdated version and asks me to install the new one. 
I try to download the new one but it seems that I cannot really do it. When I push the download button I am directed to my Ubuntu Software Centre where I can see the package I have already installed.

Any advice?
Thanks in advance

Friwise

---

### Post by Shazaam on 2011-10-14
Have you looked at Flash-Aid (add-on for Firefox) yet? You can find it here-

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

It is made by one of our own forum members :)

---

### Post by Friwise on 2011-10-14
Thank you so so so much!!!
Also, huge thanks to the angel/s who created this application.
It is really magical and easy to use.
I was wondering if it is ok to link this application to the greek ubuntu forum where I also tried to find solution but I had no luck.


Thank you so much again:KS

---

### Post by korben88 on 2011-10-16
Thanks for the link. But I'm still having issues. you tube videos and espn videos will not play, I just get a message that says I need to install flash player.

I already tried installing from adobes site. And installed the flash aid.

Any other suggestions would be appreciated..

FYI I am totally new to ubuntu

---

### Post by garvinrick4 on 2011-10-16
> And installed the flash aid.After installed will be a little red circle with f in the middle.
Click on that box make choice of which one of the 3 to run and will then do it for you.
Removes old and installs new and a bit more.

> Also, huge thanks to the angel/s who created this application.His name is lovinglinux and he is a Forum member a Ubuntu member and a Moderator
in these forums. He is around all the time, when you see him give him a thanks. (Wow lovinglinux you are up to an Angel.) (Ubuntu member, Name in Red and now an Angel.) Movin on up.

---

### Post by korben88 on 2011-10-16
Ah I got it... Thank you!!!

---

### Post by StormMyst on 2011-10-17
[QUOTE=garvinrick4;11354921]After installed will be a little red circle with f in the middle.
Click on that box make choice of which one of the 3 to run and will then do it for you.
Removes old and installs new and a bit more.

I don't see this little red circle, and hulu.com keeps telling me to upgrade my flash player...fairly new to Ubuntu, help is appreciated :) Also of note, I use Chrome...Thanks !

---

### Post by garvinrick4 on 2011-10-17
@StormMyst
> I don't see this little red circleYou have to add "flash aid" as a addons in firefox under tools drop down menu in Firefox
Just type "Flash aid" in search window in Add on window and then red circle with f in middle will be
in upper right of Firefox, click on pick one of 3 methods and it will do it for you. Run this and it will
make Chromium Flash work also.

---

### Post by garvinrick4 on 2011-10-17
@korben88
Welcome to the Forums, enjoy your Ubuntu. 
> Ah I got it... Thank you!!! 	
Pass it down when you get the opportunity. Have a nice day.

---

### Post by cretsiah on 2011-10-17
My kid downloaded an update to view youtube, however it disabled right-click (in firefox) and the menu (ie file, edit etc) the only way I can access the drop down menu (file, edit, tools) is to hold the cursor over the main menu heading and using arrow keys to select (including quit/exit). 

attempts to rectify it has now caused firefox and chromium to lose dns resolving capabilities (cant get on the net) however synaptic package manager still works.

---

### Post by brobodude on 2011-10-17
I am having a very similar problem with Chrome. After updating to 11.10 I found that no flash pages were working, and about:plugins shows no flash plugins. I go to the Ubuntu Software center, and I select to install Flash Plugin 10, but... it only says that the package can't be found. I tried to install from the adobe website but I run into the same problem. I can't find anyone else online who is having the same problem as I am. Can anyone help? Thanks in advance!

---

### Post by garvinrick4 on 2011-10-17
> **brobodude said:**
> I am having a very similar problem with Chrome. After updating to 11.10 I found that no flash pages were working, and about:plugins shows no flash plugins. I go to the Ubuntu Software center, and I select to install Flash Plugin 10, but... it only says that the package can't be found. I tried to install from the adobe website but I run into the same problem. I can't find anyone else online who is having the same problem as I am. Can anyone help? Thanks in advance!
Are you running 64 bit? Do you still have firefox installed?
```
uname -a
```

---

### Post by cricketsamya on 2011-10-18
It perfectly worked with 11.10.. Worked for chrome also.. 
Thanks..
:KS

---

### Post by brobodude on 2011-10-18
> **garvinrick4 said:**
> Are you running 64 bit? Do you still have firefox installed?
```
uname -a
```
Yes, I am running 64 bit, and I still have firefox installed, but the same problem exists on firefox.

---

### Post by garvinrick4 on 2011-10-18
@brobodude
Worse comes to worse and you cannot get flash aid to work for you, just do these. Flash aid does do
this but here is something line for line to run in a terminal copy and paste them. Just removes everything that just about
could be flash and installs anew.
[COLOR=Red]Make sure Firefox is not running at all[/COLOR].

```
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
``````
sudo rm -f /usr/lib/mozilla/plugins/*flash*
``````
sudo rm -f ~/.mozilla/plugins/*flash
```*
```
sudo rm -f /usr/lib/firefox/plugins/*flash*
``````
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
``````
sudo rm -rfd /usr/lib/nspluginwrapper
``````
sudo apt-get install flashplugin-installer
```

---

### Post by brobodude on 2011-10-19
@garvinrick4

Thank you for your help... However, it did not work. I got through all the steps, and the last one looked like it would work, but then I got this error:
```
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any other help would be much appreciated... :(

---

### Post by garvinrick4 on 2011-10-19
Open Firefox and now try Tools to Addons to type flash aid in search box
install flash aid restart firefox and in upper right will be a red circle with an f in it.
click on it and choose one of three ways to run and should fix you up.

---

### Post by garvinrick4 on 2011-10-19
Run this for me:
```
uname -a
```and show output of.
I will show you how to install from tarball from adobe.com so in future you will have another
way if all else fails. I think you have some unusual thing going on here I have no problem anymore installing Flash at all.

---

### Post by garvinrick4 on 2011-10-19
Go to adobe.com and download 64 bit in tar.gz to DESKTOP.
```
cd Desktop
```
```
ls
```
```
tar zxvf install_flash_player_11_linux.x86_64.tar.gz
```
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
Done:

---

### Post by rplantz on 2011-10-20
When I was trying to get flashplayer to work, my system became very slow. I quit and restarted firefox. Still no flashplayer. Finally, I rebooted the system, and now everything works!

I do not recall everything I did. My firefox Add-ons Manager shows Shockwave Flash 11.0 r1 and Flash-Aid 2.2.1 installed. And I have the following files in my system:
```

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so -> /usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```
Note that there are two files here, libflashplayer.so and npwrapper.libflashplayer.so, with pointers to them from other locations.

---

### Post by garvinrick4 on 2011-10-21
Must have been flash-aid that got you going. Lovinglinux's script removes all things flash,
installs and does some tweaking. 99% of time seems to work very easily for users who
seem to have trouble installing Flash. Once you try 2 or more times you have remnants
of flash all over the place and have to be removed first before installing anew. Flash aid
does that so works.

---

### Post by elstud1 on 2011-10-21
remove adobe and flash aid and  install lightspark from software center

---

### Post by northwestuntu on 2011-10-25
> **garvinrick4 said:**
> Go to adobe.com and download 64 bit in tar.gz to DESKTOP.
```
cd Desktop
```
```
ls
```
```
tar zxvf install_flash_player_11_linux.x86_64.tar.gz
```
```
sudo cp libflashplayer.so /usr/lib/mozilla/plugins
```
Done:

thank you.  been looking for the location everywhere.

---

### Post by garvinrick4 on 2011-10-25
> thank you.  been looking for the location everywhere.I bit of a hint:
 If you want to find out where things go and what they do google to find a script on the
subject and download the script and then break it down so as to understand each bit of
the script. 
Below is an old Flashplayer Script to remove and add new from adobe forget where I found it but should have who wrote it but does not. But anyway explains well. blah_blah_blah is just the version of Flash that is out now. The linking is not really in use but explains when. The removing is good when a user has tried to install flash over and over and has got it a bit botched and want to remove all remnants so as to install correctly.
There is an add-on in Firefox called Flash aid that will do all of this for you and has 3 ways to install with different scripts for beginner to advanced that I feel is the best for new users with Flash problems. Take a peak at it, install it and in upper right corner will be a red circle with f in the middle click on it and choose your script. It will run for you. Written by lovinglinux a Ubuntu member and a moderator in these Forums. Look at his scripts if you care to. Anyway good way to gain some knowledge is looking at scripts and or finding users who are good in a certain "skill set" and grab on to his or her coattails and look at their posts and or tutorials written. Will give you a bit more (Grub) drs305 and oldfred)(Wubi) rubi1200 and bcbc
Wireless (chili555 is tops and wildemanne39 is making good headway in subject) Flashplayer and Firefox (lovinglinux) All skill sets (users in Burgundy (admin staff) you can learn a lot from most have good tutorials written, will be in signature usually) There are more of course and most will say Ubuntu member above their avatar and or Staff, most but Not All.  ( For any new users reading this there are a lot of different drivers for Video, Network and such so not all new found powers work on everyones machines always according to drivers in use and are users good in all these skill sets. If you have a particular network card or Video card look them up and learn them, ask questions and google.

Back to original subject here is the old script. Edit found name of original script writer, Romeo-Adrian Cioaba, this is just some pieces of it below broke down.
```
echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player"
Download flash player
 http://www.adobe.com/
tar zxvf libflashplayer-blah_blah_blah
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-blah_blah_blah

```Is broke down to a bunch of single line code and if in trouble or user in trouble can always just remove the old and put in the new. (Just works and you can really see how and why) 
Removes flash from everywhere and installs new with fresh look.

---

### Post by northwestuntu on 2011-10-26
what i do is just drop the file in the folder.  i just forgot where it goes.  ive heard that flash aid works good, but this is easier for me.

---

### Post by garvinrick4 on 2011-10-26
@northwestuntu
> what i do is just drop the file in the folder.  i just forgot where it  goes.  ive heard that flash aid works good, but this is easier for me. Dragging and dropping is fine, it works.
Yes was in a session where I felt like giving some info that day. Mostly for new users
that were reading Thread. Must have had to much coffee.

---

### Post by garvinrick4 on 2011-10-26
@northwestuntu
> ive heard that flash aid works good, but this is easier for me. 	
I was actually meaning use addon and then click on red circle with f in upper right and look
at the scripts used to install with, all different and worth understanding. Just to see the
scripts written and what they do. For those with a thirst for such things.

---

### Post by wildest on 2011-10-26
**[SIZE=3]I  just upgraded ubuntu 10.10 to 11.04. I tried to install adobe flash  plugin but in the middle it stopped. Then I tried to remove but its not  removing. Please provide me assistance. Sorry, I couldn't find any other  place to ask my question.[/SIZE]**

---

### Post by garvinrick4 on 2011-10-27
Open firefox and click on Tools go to Addons.
Open Addons and type flash aid in search window.
Install flash aid and then close Firefox.
Open firefox and will be a red circle with an f in it in right upper side of window:
click on red circle and choose one of three options to install.
When done restart firefox and Flash should be installed correctly.

## By the way why is your font so big in your post it is obtrusive to look at.

---

### Post by northwestuntu on 2011-10-28
> **garvinrick4 said:**
> @northwestuntu
 Dragging and dropping is fine, it works.
Yes was in a session where I felt like giving some info that day. Mostly for new users
that were reading Thread. Must have had to much coffee.

i know that having too much coffee feeling :lol:

i just installed xubuntu the other day after trying lubuntu and weird it didnt have a usr/lib/mozilla/plugins folder at all?  couldnt figure out where to put it?

could i have made one? i had firefox installed.

i added the adobe source using apt and that worked for the install.

---

### Post by garvinrick4 on 2011-10-28
@northwestuntu
> i added the adobe source using apt and that worked for the install. That is good as any. Installs lots of packages, take a look if you care to when
purging.
Use this code below and find out where it installed: most likely used nspluginwrapper.
```
locate libflashplayer.so
```I just installed same as you and get:


rick@rick-sda15:~$ locate libflashplayer.so
/home/rick/Downloads/libflashplayer.so (just a copy I had in Downloads)
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/share/ubufox/plugins/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so
rick@rick-sda15:~$

Then purged flashplugin installer and autocleaned and then just ran remove all remnants (overkill but why not just takes a second)
Make sure no Firefox running.
```
sudo killall -9 firefox
``` And below one at a time```
sudo apt-get purge flashplugin-installer 
sudo apt-get autoclean 
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rf /usr/lib/nspluginwrapper
```Now I get this below after installing from adobe.com 64 bit. Extracting and copy to /usr/lib/mozilla/plugins/

rick@rick-sda15:~$ locate libflashplayer.so
/home/rick/Downloads/libflashplayer.so (this is the Download from adobe.)
/usr/lib/mozilla/plugins/libflashplayer.so (this is only place libflashplayer.so installed) (flash is working fine)
rick@rick-sda15:~$

### this all is just a learning thing so as to know what installing in different styles actually installs in your file system with northwestuntu, nothing more than that.
##If anyone ever gets stuck with Flash not working "Flash aid" addon in firefox will remove and reinstall in its scripts and make you well.

---

### Post by northwestuntu on 2011-10-31
oh cool i didnt know about that locate command.  i ran it and it came back with only 1 location

/usr/lib/adobe-flashplugin/libflashplayer.so

ok weird now the /usr/lib/mozilla/plugins is found?  

how can i tell if i have the the 64 bit version installed?

---

### Post by garvinrick4 on 2011-10-31
> **northwestuntu said:**
> oh cool i didnt know about that locate command.  i ran it and it came back with only 1 location

/usr/lib/adobe-flashplugin/libflashplayer.so

ok weird now the /usr/lib/mozilla/plugins is found?  

how can i tell if i have the the 64 bit version installed? This would be a good time
to install Flash in all the different ways and see what is installed where. Install flashplugin-installer 11.0.1.152ubuntu1 from repo's and see what is installed.  
 Sometimes it is nice just to keep a test partition active for such an occasion. Best way
I have found to learn is to do something practical instead of just in theory for myself.
> how can i tell if i have the the 64 bit version installedIf you downloaded from adobe.com and have a 64 bit Operating System will give you 64 bit
download. Here is my download from adobe.com as of late. 
/home/rick/Downloads/install_flash_player_11_linux.[COLOR=Red]x86_64[/COLOR].tar.gz

Right click on any flash playing will tell you version of flash.

---

