---
title: "how to install Nvidia Drivers..the Right and easy way"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by redheat on 2007-07-10
Ok folks..

 I came across this incredible post on nvidia's forums on how to install your Nvidia drivers on ubuntu, and If you're having a problem with Tseliot's installation program "envy" and, from what I read on the IRC channels it isl causing some problem especially when you try to reconfigure your xserver interface, then you are left with one viable option which is to install the nvidia drivers using the normal method but how can you do that? ..this is how: 

[http://www.nvnews.net/vbulletin/showthread.php?t=94072](http://www.nvnews.net/vbulletin/showthread.php?t=94072)

this post builds on Nvidia's sticky which could be found here: [http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490) yet it gives the instruction in a more elaborate and easy-to-follow instructions and you won't have to go through that runlevel name-changing process that I had to go through before, and in case that post was not to be found. I post it here again:

Note: "to know which packages are installed on your system go to synaptic manager if you're using Ubuntu, or if you're using Kubuntu go to package manager, I think its called "package manager" and type in search the name of the package you're looking for" 

```
- first you need to install the build-essentials which includes 
development tools like make and gcc.
sudo apt-get install build-essential

- Then you should install the linux-headers package matching the installed Linux kernel.
sudo apt-get install linux-headers-generic #If you use generic kernel

you can look which kernel is in use with the following command

uname -r

it should print something like that
2.6.20-16-generic

- Then install the following packages
sudo apt-get install pkg-config
sudo apt-get install xserver-xorg-dev

- Uninstall all nvidia drivers that are installed from ubuntu.
You have to look which driver is installed so I give you an example how this command could look like.
sudo apt-get remove --purge nvidia-glx

If I am right there is a nvidia-glx-new package, but you have to take a look what is installed.

- change permission of the Nvidia-installer.
chmod 777 NVIDIA-Linux-x86-100.14.11-pkg1.run

Now you have to switch to console, by pressing strg+alt+F1

login and then stop current gdm

sudo invoke-rc.d gdm stop

install the driver.

$ sudo ./NVIDIA-Linux-x86-100.14.11-pkg1.run

If installation is complete you should take a look at your xorg.conf

sudo nano /etc/X11/xorg.conf

Change the driver to nvidia
The Device Section should look like this.

Section "Device"
Identifier "Geforce 6200"
Driver "nvidia"
EndSection

save and exit nano.

now you could start gdm
sudo invoke-rc.d gdm start

Now everything should work.

hope this helps.
```
With great thanks to Mr.A from Nvidia forums..of course I didn't get her/his permission.. but who cares in this world of open thievery ;-)

regards to you all
redheat

---

### Post by I'd_rather_be_____'ing. on 2007-07-11
Hey AWESOME!!  Just did this and it worked.  And I was even halfway through that blasted generic linux guide nvidia has up.  I'm still on the low end of the Linux Learning Curve and brand new into Ubuntu, so this was timely (synaptic YAY! / up2date BOO!).

I'm using 7.04 with the 2.6.20-16-generic kernel and installing an 8500gt; following these instructions works and so does Synaptic P.M. for missing packages, aside from those "remove --purge" lines.

Here's what I had to add (others were already there, but I'd done a few updates already): 
build-essentials
xserver-xorg-dev

Here's what I removed(with Synaptic):
linux-generic
linux-restricted-modules-2.6.20-15-generic
linux-restricted-modules-2.6.20-16-generic
linux-restricted-modules-generic
nvidia-kernel-common
restricted-manager
[these were all the installed packages that showed "nvidia" when searched in Synaptic, except xserver-xorg-video-nv, which i decided to leave there for reasons unbeknownst to me]

Here's what I removed manually:
/etc/init.d/nvidia-kernel

Everything else worked like it should (compiling from source) and now I'm squinting to see my nice tiny fonts!

Thanks, redheat, for stealing this off Mr. A and sharing it.

---

### Post by Beatbreaker on 2007-07-12
Redheat - I tried your solution and it didn't work

(BTW theres a sp mistake in it "sudo apt-get install xsverver-xorg-dev" should be "sudo apt-get install xserver-xorg-dev")

i'm still getiing the following output and having to switch to "nv" for it to get me in again

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by DavidCar on 2007-07-12
Hi!

I installed nvidia restricted drivers, but I'm having a rather strange problem. I have to install the drivers EACH time I restart my computer. The first time I installed the drivers everything worked out and I even tried beryl (AT LAST!!!:P), but then, after I restarted my PC the X server wasn't working with the driver and i got this message in the log.

(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***

Thnx in advance and sorry for my bad english.

---

### Post by whpsh on 2007-07-12
I'm so new to Linux it's frustrating but this worked for me with a small addition...

I backed up my xorg.config file the very first thing as soon as the install was finished updating.

I followed the OP's directions entirely but after checking the new xorg.config had all the right information in the Section "Device", I tried to start gdm and got a black screen and the login drums o' doom.

I went back to the console thinking all was lost. I stopped the gdm, ran:

sudo cp /etc/X11/xorg.config_backup /etc/X11/xorg.config

then started gdm again and everything is working perfectly (using nvidia drivers and getting 10x the resolution options).

---

### Post by redheat on 2007-07-17
hi all and so so sorry for not replying earlier. Honestly this is the first time I log in back to the forums since the last time I posted this message

 I'd_rather_be__'ing  you can't imagine how happy I was to see that someone really made use of my sonorous and endless self-help rants. Good for you, now go and enjoy beryl. No argument there..that program is awesome

Beatbreaker, First thank you for highlighting that spelling mistake..it was Mr. A's mistake and I copycat it without giving it a second look. So on behalf of Mr.A, the present absentee, and me Thank You. I had your exact problem. To work around it I had to reformat and reinstall Ubuntu and right after that I updated ubuntu and then followed Mr.A's instructions. To put it simple, I installed the nvidia drivers on a RAW Operating system. I didnot install any nvidia drivers using synaptic manager or anything like that. I just did it on an almost RAW installation of the OS, therefore, I guess, the installation had no problem whatsoever, the driver installed smoothly. But this doesnot negate the fact that I actually have a problem that's been keeping me from Ubuntu for a while, and it has nothing to do whatsoever with Ubuntu, but it has everything to do with my video card which I by accident fried. Ok here's the problem that I have, my video card is an XFX 8600 GT video card with dual DVI link I connected it to my High Definition TV using an analog cable, and there was no adapter in the middle and guess what? I screwed up my video card to the point that one of the two DVI port sees my monitor as LCD and the other sees it as DFP, some kind of a lower quality, but as you can see I have no problem whatsoever the Driver installation and Ubuntu which is an awesome OS along with that headbanging thingy called Beryl. To know more details about my problem go here: [http://www.tomshardware.com/forum/241396-33-help-connect-hdtv-dual-video-card](http://www.tomshardware.com/forum/241396-33-help-connect-hdtv-dual-video-card)

 Yet when it comes to installing the driver properly and all the 3D features are fine and working as they should yes they are no question there from my 16x AntiAliasing to my 16 Anistropic Filtering to everything else it is more than okay. So my advice again, as I did it, was to follow what Mr.A posted above if not, you can post to him directly with the problem.  Sorry, I really wish if I knew more. By the way, all the other methods to install the NVIDIA drivers for the new breed of cards always gave me that "no usable configuration" even the one posted on Nvidia's sticky post also gave that error because that post is not complete I thought I should include it as a reference only, but the first one to apply it properly was Mr.A from nvidia forums. Sorry for baraging you with all this jabbering. Again, a recap, what I did was a fresh install of ubuntu, update it, oh and don't forget when you install the drivers you have to be logged in as a "root" user not ordinary user. of course you know that. 

DavidCar, thanks for your reply, and sorry it didn't work for you, but I also faced that same problem when I used the Tseliot's envy program and also when I tried to install the Nvidia Drivers using the Nvidia way and it gave that error you got. all i can say this problem went away the moment I followed Mr.A isntructions down to the smallest detail. just try it again, and don't use the restricted manager to install any drivers. use Mr. A again. Or if it doesn't work, which I highly doubt, I ask you to post to Mr. A, and dude your english, and who am I to judge you since I'm not a native english speaker myself, but your english rocks. unless you're apologizing on behalf of the log file entries..you know (EE)..err..etc. 

whpsh my friend, I'm happy that it finally worked for you, and thank you for providing the command on how to restore a backup, since that was the only command I was looking for I know how to backup but I don't know how to restore.

Finally, for those who are noobs like me in Ubuntu and linux in general I came across this wonderful article by the dude himself who runs one of the most famous linux website on the internet [www.distrowatch.com](www.distrowatch.com)  read this opinion article its called "learning linux" it can't get any more obvious than that: [http://distrowatch.com/weekly.php?issue=20070507](http://distrowatch.com/weekly.php?issue=20070507)

regards and best wishes to you all
redheat

---

### Post by redheat on 2007-09-30
hi everyone

 this is a quicky update, but first of all let me start with this..Mr.A you rock my man..you rock. your post on nvnews.net, and how you simplified and filtered the main sticky post on [www.nvidia.com](www.nvidia.com) forum regarding linux driver installation is AWESOME.

 For the second time ladies and gentlemen, I have followed Mr. A notes on installing the NVIDIA drivers provided by NVIDIA, and for the second time it works like a Charm. This time I've installed it on Gutsy Gibbon, the second beta release, and it ROCKS!

 this is what I did, either you upgrade to Gutsy using your update manager, or you're making a fresh install. Here's what you're gonna do.

1. First of all, after finishing the installation, and booting or restarting back into your new system, you'll probably see an icon, that looks like a piece of hardware near the upper panel with a flashing icon telling you to " if you want to use 3d hardware or 2d rendering of some items you are required to use some " restricted drivers" and then it temps you, and sorry for using such biblical language, to click it which will start an automatic downloading of "nvidia drivers" straight from ubuntu servers. My Advice, don't click or use them, though they work correctly, no problem there. Just don't do it, cause if you wanna install the nvidia drivers by downloading them manually from Nvidia's website, where later on you'll be asked, according to the above post, to remove their nv-glx-new, or whatever the name of the package you downloaded when you clicked on the settings manager, they won't go away nicely even if you tried to purge them using the purge command, or even if you tried to disable them using the restricted manager interface. For they won't allow a clean install and identification of your nvidia drivers.

 so after you download the nvidia drivers to your system. Don't do anything. head again to the update manager. Check for updates, make sure that all the updates are downloaded and installed. restart. then go back again and follow the above directions.

 to simplify it:

1. start by opening your synaptic manager which is located under system=>Administration. Click on search and then type (make), and scroll down till you see the make package, which is usually installed, and notice this its called just (make) not (make) +(something else) just make.

again, do another search, and this time type (gcc), this time too..check for a (gcc) package, you might in both cases find other packages by the word gcc something or make something which are already installed, these come by default. No problem there, but just make sure that packaged called make and gcc are installed.

2. now try to install the build essentials using the following command: sudo apt-get install build-essential

 you might be asked to enter your installation CD do it and continue installation.

3. search for the linux headers. by typing, of course all commands are typed in your terminal window. which is located under applications=>accessories=>terminal. of course all of the above typing must happen from a root account. to access your root account. you can do that by logging out from your ordinary user account and login back again as root, or if you didn't have that property enabled  you can do it right from your terminal. just type  sudo -i (you'll be asked for a password, type it and there you go, your  command prompt starts with the word root@something. which means you're using the terminal under the root privilages).  now start searching for the linux headers that match your kernel version. You can check that by typing uname -r and you should see you're kernel version as 2.6.22-12-generic
then type the following command to get the linux headers:
sudo apt-get install linux-headers-generic 2.6.22-12

 you might get a message that says linux-headers generic is already the newest version. which means you're ok. Now move to the following step.

4. now type the following two commands to get the following packages:
sudo apt-get install pkg-config
sudo apt-get install xserver-xorg-dev

5. uninstall any nvidia drivers you got by using the following command. Hopefully you didn't download any of them after you upgraded to gutsy gibbon. Another way to say what type of nvidia drivers you have installed go to synaptic manager, and type in search the word (nvidia), and it will give you a list of all possible packages relating to nvidia, notice something, not all of them are drivers there might be packages that relate to the nvidia drivers development or implementation process but they are not drivers themselves. Like the nvidia settings manager program that is known as xserver which you've just installed from the above step. anyway, you will find a description next to each package telling you what it is. now type the following command into your terminal:

sudo apt-get remove --purge nvidia-glx

 or nvidia-glx-new if you have the new package, if a message came up saying that no nvidia packages exist, because they were not downloaded in the first place..then that's good luck. Move on to the final step.

6. go to the place where you put your downloaded nvidia linux driver. For example if you put them on the desktop then type in your command prompt:  cd Desktop (capital letter for d) and I recommend to put there so as to downsize the directories that you have navigate through to reach your file. now type 

 chmod 777 NVIDIA-Linux-x86-100.14.19-pkg1.run (the 14.19 is the latest one released by nvidia)

 important note: sorry that I didn't bring this up earlier, after you update your ubuntu through the update manager remember to restart, even if they don't ask you to do..just do it.

now do the following:

press on the ctrl+alt+F1 buttons simultaneously this should take you to a black screen or a black command prompt screen like the Dos screen you used to see under windows.

now you should be standing at a command prompt that says root@something which is the root account.

7. now type the following    sudo invoke-rc.d gdm stop  this command should stop the gdm or the "fancy"  interface from working. think of it this way. remember when you used to log out of your windows, wasn't the windows still working in the background? it was. So think of this command as a way to kill that windows interface, and letting you work only from the black command prompt screen.

8. now navigate to where you did put the downloaded nvidia drivers. Assumingly, we saind it should be found on the desktop: therefore type in your command prompt:

cd Desktop

you should see your command prompt with a Desktop followed by a forward slash showing that you are in the desktop directory.

9. Now type the following: sudo ./NVIDIA-Linux-x86-100.14.19-pkg1.run

and that should start the installation process.

 you will be asked to accept the user agreement, which I bet no one has ever read since windows 3.11 till today, click accept, and then some other blah blah blah about how windows will try to locate some package to install your graphics card, click ok, after that another "scary"  sign telling you that no packaged could be found for installing your driver, and they will try to download it, which they also won't be able to find, still click ok. finally, after you pull a few hairs, the program will ask you to build a kernel from scratch, say yes. then you will see a bar showing the progress of that " building"  process. Then presto!! it's finished now to restart your ubuntu again and to test it. repeat the above command you used to end the graphical insterface but this time replace stop with start:

sudo invoke-rc.d gdm start

 you'll find yourself staring at the login screen type in your login name and enter. You will see the restricted manager flashing and telling you that "restricted drivers are in use" meaning that it has used your nvidia drivers as the new restricted drivers instead of the ones you could have downloaded from ubuntu. now go to applications=> system tools=> and you should see something called nvidia xserver settings.

 one more thing which I forgot to mention, during the installation process of the nvidia driver, a message pops up asking you to allow nvidia to use it automatic utility to configure the xserver settings, and it will back up the original xserver settings. Click no. Don't let nvidia's automatic utility set the xserver settings for you. Just follow me on this, cause if you did that and allowed nvidia to do it for you, it will mess up the whole thing and you won't even be able to get your system working. So do this after you insert the above start gdm command and go back to your desktop, and head to the xserver settings under application, a message will pop up telling you that you don't have xserver settings or that they're not loaded. and it tells you that they are located under the following directory /etc/X11/xorg.conf, the file containing them is called xorg.conf

 The next time you get to install your nvidia driver for any reason, click yes, and let NVIDIA replace your xserver for you. You won't have to go through the whole steps above. 

 and this is it ladies and gents. 

 this is how I got my groovy ubuntu in less than 30 minutes.:lolflag:

best regards
redheat

---

### Post by redheat on 2007-09-30
By now, most of you know that Beryl, the 3D desktop effects program has been replaced by Compizfusion. to be able to use the different settings in compiz fusion

 Go to your terminal window type  sudo apt-get compizconfig-settings-manager   Alternatively you can get it from the synaptic manager. Just scroll down till you get to compizconfig-settings-manager package and tick next to it. 

regards
redheat

---

### Post by Saosin on 2007-10-01
help!!
im having a problem, i installed the drivers of the nvdia but i dont know how to exit the commmand prompt. i rebooted after installing the drivers and then typed 

sudo invoke-rc.d gdm start

but it keeps in teh commman prompt, maybe it sounds noobish but i would like to know how to exit the command prompt 
i have a geforce6200 of 256mb

it gives me the following message
"Failed to start the X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"

thx

---

### Post by posdnuos on 2007-10-01
Why did he [FONT="System"]chmod 777[/FONT] the installer instead of [FONT="System"]chmod +x[/FONT] ?

---

### Post by redheat on 2007-10-02
don't know..

---

### Post by Dr. Akam on 2007-10-02
> **Saosin said:**
> help!!
im having a problem, i installed the drivers of the nvdia but i dont know how to exit the commmand prompt. i rebooted after installing the drivers and then typed 

sudo invoke-rc.d gdm start

but it keeps in teh commman prompt, maybe it sounds noobish but i would like to know how to exit the command prompt 
i have a geforce6200 of 256mb

it gives me the following message
"Failed to start the X server (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"

thx

The command

sudo invoke-rc.de gdm start

should bring you back to Gnome.

As you noticed there seems to be something wrong with your installation.

Could you please post the xorg.log which you can finde in /var/log/Xorg.0.log
or you generate a bug report the nvidia way.

Take a look at this.
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678)

to get a wider audience it would be better to post your problems at the nvidia forum.

I hope this will help you.

Dr. Akam

---

### Post by redheat on 2007-10-02
Thank you Dr. Akam for your reply.

---

### Post by calicojack on 2007-10-03
Awesome.  Worked just fine... Once I got over my n00bness.  It has been way too long since I have messed with Linux of any flavor.  But this guide helped out a lot.  I ditched my Windows OS and am going with Ubuntu to sharpen my skills.

---

### Post by redheat on 2007-10-05
> **calicojack said:**
> Awesome.  Worked just fine... Once I got over my n00bness.  It has been way too long since I have messed with Linux of any flavor.  But this guide helped out a lot.  I ditched my Windows OS and am going with Ubuntu to sharpen my skills.

 yes yes and HOOoah

:cool:

regards
redheat

---

### Post by redheat on 2007-10-06
ok I'm just gonna write this post to remind to update you on what happened today with the release of the new kernel. First of all, like a big thank you to all the great folks over at Ubuntu+1 irc channel for their support guys/gals you Rock. 

 Second, and foremost, developer dudettes/dudes..give us a break from releasing new kernels till the final release. Or at least, and please do this, just throw us a reminder when a big update like a new kernel is coming out. Just for the Kernels.

 Ok guys, this is what happened today, I have Kubuntu installed on my system. if you don't know how to install it head over to this great website [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

 and look at this part of how to install Kubuntu, think of Kubuntu as another interface to your desktop. So today, I clicked on a program called adept-adapter, which is an update program like the update program you have under ubuntu. I chose update, and it turned out there was like 240 MB or more of updates. So I waited till the updates were finished, and then a two-interwined arrows appeared near the bottom right corner telling me to restart..so I did..and boy oh boy..after I restarted and while looking at the grub which is the equivalent of windows vista boot-loading menu..I saw the unbelievable, a new kernel  was released the last one that was 2.6.22.12 the new one is 2.6.22.13 , before the screen even flickered and ushered the way to ubuntu login screen. The screen resoluion suddenly went low, and an ugly-looking message popped up telling me you're using low-graphic mode continue or configure. I chose configure, tried to choose a resolution that would make the desktop readable like 1024x768 or something near that since the system can not see my monitor or my video card. Right after I chose the resolution I wanted, I logged in and headed over to the xserver settings, clicked it, but it gave me a message " it seems that xserver config is not configured correctly just open your nvidia-config as root (that is from the terminal), and then restart your xserver) my advice to you all.. don't do anything of that..absolutley nothing cause the system can't even see your video card or monitor, cause this is a something called a " failsafe mode". It simple means, your previous settings are gone, and good luck trying to figure out what they are.

 To overcome wasting your time trying to know the exact timing modes of your monitor, reinstall the nvidia driver again. But this time, you won't have to redo all the previous steps we did, just start from the step where you open the terminal head over using the CD command to directory where you put the nvidia driver and then type:

chmod 777 NVIDIA-Linux-x85-100.14.19-pkg1.run 

now type exit to leave the terminal.

 now press ctrl+alt+f1 to leave the xserver..that is your desktop

now start an ordinary installation process from your black screen or "command prompt screen", and and when confronted with let nvidia automatic configuration utility configure your xserver, choose yes. and restart into the xserver and it should work again fine.

 so the moral of today's lesson my faithful disciples " thou shall not update to new kernel without reinstalling your video drivers again" 

regards
redheat

---

### Post by redheat on 2007-10-07
ok guys..this is a another breakthrough, man I should turn this post into a blog. yesterday, right after that debacle with installing the new kernel and updating KDE, I got another problem, the compizfusion settings wouldn't start. 

 I mean no matter what the setting I choose, it just won't run. just dead as a door knob. I tried everything. so I googled a little on the net and I came across this article on softpedia: 

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

 don't do anything about the other settings, just the last two parts, the one that says:

FOR KDE USERS:

sudo apt-get -y install compiz compiz-kde compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-kconfig

past it into your terminal right while you're still logged inside your KDE 

and then open up the commad prompt by pressing ALT+F2 then type 

compiz --replace

if it works with no errors then this is great. and everything should work as silk.

now restart and Voila! everything should be working fine..

regards
redheat.

---

### Post by gdubbus on 2007-10-15
Hey all,

   I recently had a video card die on me, I had installed it via this method and currently have Nvidia-Linux-x86-100.14.11-pkg1 installed. My backup card is even older and obviously won't work woth this package, any ideas on how to remove Nvidia-Linux-x86-100.14.11-pkg1 or uninstall it so I might be able to get the right package for an MX installed via the command prompt?

thanks!

---

### Post by usarmykr on 2007-10-15
Ive got that message before, but when I used envy to install my drivers, then a kernel update came out, and the kernel update broke the drivers.  If you updated the kernel you will have to reinstall drivers.

---

### Post by FredB on 2007-10-15
Besides envy, why not using restricted driver manager ?

One click, and a restart... Simpler than all I've seen in the thread. At least, it works this way on gutsy.

---

### Post by Stop-state-terrorism on 2007-10-20
redheat , thank you so much for your step by step infos, worked great, my 2 monitors are also working, i thought i would have had to install some other manager for dual screen, but no, the nvidia xconfig server worked it out great

i aint going to windows (except for playin or 3dstudio max)


ps: you might not in your tutos that for kubuntu the invoke command is on KDM not GDM

thx,

---

### Post by mattengland on 2007-10-21
For what it's worth, I put together my own procedure here, derived from this and other threads:

[http://www.nvnews.net/vbulletin/showpost.php?p=1419835&postcount=6](http://www.nvnews.net/vbulletin/showpost.php?p=1419835&postcount=6)

---

### Post by coffee-n-cream on 2007-10-23
im beginning to pull whatever hair that is left on my head after i cant get my nvidia to work.i got everything installed correctly,following redheat's method.now i stop the x server,run as root nvidia-xconfig or edit xorg.conf replacing "nv" with "nvidia",i start x again by typing "startx" or "sudo invoke-rc.d gdm start" my x wont start at all.it will give me a black blank screen and hang there.i have to use "nv" again to restart my x server.its getting really frustrating.i have this problem with feisty too.i thought with gutsy all my nvidia problems are solved.im suspecting its my hardware problem coz i installed feisty on my old pc n managed to get nvidia running by simply enabling restricted driver manager.

anyways here r my not so new specs:
AMD 3700
OCZ 520watts PS
DFI Lanparty SLI-DR
EVGA 8800gts sc
2gb ram
Hitachi 500gb (for windoze) and WD 160gb (for ubuntu)

pls can anybody help me before i shed my hair way faster than my cat :mad:

---

### Post by coffee-n-cream on 2007-10-24
help anybody??

---

### Post by redheat on 2007-10-27
> **coffee-n-cream said:**
> help anybody??

coffee-n-cream..sorry my friend I just logged in and saw your post..why are you trying to change the driver section from nv to nvidia? don't bother yourself doing that from the command prompt screen. Listen do this. Do a clean reinstallation of your driver, do not, and I repeat, do not uninstall the restricted modules, just the new-nv-lgx driver. and then go through the steps again. 

the gcc and make, the linux headers..etc. till you come to the screen where you are asked to let the nvidia driver configure the xconfig file for you automatically. Just say yes and let it do it. After you login successfuly, and you will, go straight to the nvidia settings manager and you will find on the window that display the resolution settings, and you will see an option called save to configuration xconfig server..do there's an option called preview. you can use that preview, instead of logging out to change whatever settings you wanna change.
coffee-n-cream, we'll walk through this together..just stop pulling your hair out..cause it never grows back unlike your cat..and if you're a dude, which is what I suspect, you'll be bold in no time. Dudettes, don't pull their hair, they eat their fingernails,,more gruesome..

 so please just reply to this post..tell me in simple steps, how did you go through it..and piece of advice..the moment you move to the command prompt screen, the black screen, during the installation process, let everything go automatically from there, in simple words..keep saying yes to whatever pops on the scree, don't edit the xconfig, or do anything after you install the driver. 

regards
redheat

---

### Post by redheat on 2007-10-27
ok coffe-n-cream, gonna show you how I installed the nvidia driver on my new DELL XPS m1330 laptop,which comes with an NVIDIA 8400 GS video card preinstalled. FIrst of all, change your videocard's name to the default value, if it was nv, just leave it as it is so we can log-in back into the destkop. Now let's do a fresh installation.(by the way, as I was writing to you the previous reply to your post, I was installing the nvidia drivers for the laptop and it took less than 5 minutes to finish it all)

1. search for make and gcc, in your synaptic manager, do a search for them. You will come across a lot of files that have these name plus numbers..ignore them completely..just plain "make"  and plain "gcc" They most likely come preinstalled with the system, so you should see their checkboxes with green marks in them indicating that they're already installed.

2. go to your terminal type: sudo apt-get install build-essential. You might download some files here, but most of them should be installed already on Gutsy Gibbon's cd.

3. now type in your terminal :   uname -r this command will list your kernel type and number for example 2.6.22-14-generic 

right after typing that fetch the linux headers for that type of kernel by typing: 

sudo apt-get install linux-headers-generic 2.6.22-14

4. type the following two commands:

sudo apt-get install pkg-config
sudo apt-get install xserver-xorg-dev

 you can get the above two files (pkg-config and xserver-xorg-dev) by searching for them in synaptic manager.

now you have everything ready..

go to your terminal: type chmod 777 NVIDIA-LInux-x86-100.14.19-pkg1.run and then type exit to leave the terminal

press control+Alt+F1 to exit xserver..now you should be in the main black or command prompt or terminal screen..

type root at that command prompt line andthen your password for root.

now type:  sudo invoke-rc.d gdm stop (to stop the xserver from working in the background)

 now to the grand finale:

 type: sudo ./NVIDIA-Linux-X86-100.14.19-pkg1.run

the installation should start with no problems at all..

 a number of messages will appear that will tell you that you don't have precompiled kernel, and they will precompile it for you ..choose yes..then you will come to the final one that says if you want to let NVIDIA configure your xserver automatically so it stars each time your start your sytem choose yes..and continue.

 now your installation should finish, right after that you will find yourself back at the command prompt, retype the command to end your xserver 

sudo invoke-rc.d gdm stop (only change stop to start so it should look something like this)

sudo invoke-rc.d gdm start

you will instantly be taken back to your login screen with new resolution and everything...

now you can log in to your desktop head to the xserver settings which are located under applications=>System Tools=>xserver-settings..and head to the second page to get and look at the preview section to see how does the xserver.config file look alike from the inside..and you can do changes to it if you like.

and that's it..

that's exactly what I did..dont' do anything more than this.
regards
redheat

p.s. if you like dribbling in the xserver courtyard..try this website, probably best explanation of how to create, backup and restore xconfig files..

[http://docs.pclinuxos.com/XorgConf](http://docs.pclinuxos.com/XorgConf)

---

### Post by Kool_Kat on 2007-10-28
redheat

I tried your approach and it does not work for me.

I am trying to load the latest Nvidia driver NVIDIA-Linux-x86_64-100.14.19-pkg2 for 64 bit Linux on AMD with Gutsy Gibbon.

I have also tried all the other guides to installing the Nvidia drivers and they do not work either.

I have had all sorts of errors, including unable to load Nvidia kernel module and API mismatches. I have tried envy and the standard restricted drivers load. All of the "manual" approaches to loading the Nvidia drivers give me the same error - which is a Signal 11 - as noted below and in my previous post to this forum which has not elicited any response.:(

[http://ubuntuforums.org/showthread.php?t=594281&highlight=gusty](http://ubuntuforums.org/showthread.php?t=594281&highlight=gusty)

Backtrace:
 0: /usr/bin/X(xf86SigHandler+0x6d) [0x48670d]
 1: /lib/libc.so.6 [0x2b638a1fb7d0]
 2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv00 1174X+0x36) [0x2b638c6af986]
 
 Fatal server error:
 Caught signal 11. Server aborting
 
I have tried variants of your approach - including taking some tips from here:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
i.e. either removing the packages or disabling the modules - but both result in the same error above.

After each failure I have undertaken a clean install of Kubuntu to remove any chance of debris from failed attempts messing things up- so I am getting somewhat tired of installing now - especially as the install process sometimes grinds to a halt without finishing properly. Also keep getting the error with UUIDs changing [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)
....so I have to keep editing my fstab to put the swap partition back with the right UUID. Grrrrr:twisted:

Any ideas - anyone please?:confused:

---

### Post by sanderma on 2007-10-30
Having followed all the tips 'n tricks on this (and other) forums, I managed to install and use the Nvidia driver from their website.

The only problem I now have, is that I have to boot in recovery mode, and manually start my X-server.

When I boot normally, I get a blank screen.
You would say that I misconfigured something, but then again, why would it work in recovery mode, without any modifications :confused:

I just have to start my X and it works...

Any idea where I should look to get my 8800GTS to work in normal mode?

Next step in line is to use [[COLOR="Navy"]Envy[/COLOR]]("http://www.albertomilone.com/nvidia_scripts1.html") and reconfigure the whole lot  ](*,)

P.S.

Is it possible to get the live cd to work by adding nvidia drivers at startup? I did see the option, but didn't try it yet...

thnx in advance!

Sanderma

EDIT:

After turning my brain on, I found the solution.

In GRUB, stand on the first boot option to (K)Ubuntu and edit the line with kernel in it.
There remove quiet splash at the end.

The reason my setup wouldn't boot was the splash screen at the beginning.

---

### Post by coffee-n-cream on 2007-10-30
ok redheat,ive reinstall gutsy again n followed ur steps exactly.after typing sudo invoke-rc.d. gdm start,my computer would hang.the blue indicator light on the lcd would turn to orange.no login screen,juz a pitch black screen. :confused:

---

### Post by redheat on 2007-10-31
> **Kool_Kat said:**
> redheat

I tried your approach and it does not work for me.

I am trying to load the latest Nvidia driver NVIDIA-Linux-x86_64-100.14.19-pkg2 for 64 bit Linux on AMD with Gutsy Gibbon.

I have also tried all the other guides to installing the Nvidia drivers and they do not work either.

I have had all sorts of errors, including unable to load Nvidia kernel module and API mismatches. I have tried envy and the standard restricted drivers load. All of the "manual" approaches to loading the Nvidia drivers give me the same error - which is a Signal 11 - as noted below and in my previous post to this forum which has not elicited any response.:(

[http://ubuntuforums.org/showthread.php?t=594281&highlight=gusty](http://ubuntuforums.org/showthread.php?t=594281&highlight=gusty)

Backtrace:
 0: /usr/bin/X(xf86SigHandler+0x6d) [0x48670d]
 1: /lib/libc.so.6 [0x2b638a1fb7d0]
 2: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv00 1174X+0x36) [0x2b638c6af986]
 
 Fatal server error:
 Caught signal 11. Server aborting
 
I have tried variants of your approach - including taking some tips from here:
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)
i.e. either removing the packages or disabling the modules - but both result in the same error above.

After each failure I have undertaken a clean install of Kubuntu to remove any chance of debris from failed attempts messing things up- so I am getting somewhat tired of installing now - especially as the install process sometimes grinds to a halt without finishing properly. Also keep getting the error with UUIDs changing [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/105490)
....so I have to keep editing my fstab to put the swap partition back with the right UUID. Grrrrr:twisted:

Any ideas - anyone please?:confused:


Kool_Kat, gott a suggestion, and it is in noway an informed suggestion, I'm still noob to this whole linux stuff, but could it be you got that swap problem because you, like so many others, don't let Ubuntu do the partitioning for you? this is only a suggestion, I usually savor some unallocated space on my hard for Ubuntu and let it do its magic. (self-guided installation), and never gotten an issue like that. The swap changes, it must be something you've done that upsets the way how Ubuntu sees the partitions everytime. This is just me, I mean in noway, does this have anything to do with Ubuntu support or programming, just plain old run-of-the mill speculation. Don't get bored of installing and reinstalling this like so many other linux system, a fairly new OS system that is being pushed to the limit. Just keep trying it, you won't believe how many times I had to reinstall because of a simple error or an installation process that decided to die in the middle.

 About that installation issue, I don't know what to tell you, all I can I tried that only on a 32 bit system. Yet there's one thing need mentioning, I had a "no signal" symptoms before that is when I turn on the PC, the screen goes dead and it gives me "no signal"  where it goes black and its front side panel lights turn to orange as if I was hybernating it or forcing it to go to sleep. But it was actually a hardware problem and I had to change my video-to-monitor connection from Digital=DVI to Analog=VGA. I can't say the seem, but it has to do with the driver and your 64 bit system. I really wish if I was more helpful.

---

### Post by dumplinknet on 2008-01-09
for some reason when i type "chmod 777 NVIDIA-LInux-x86-100.14.19-pkg1.run" into the terminal, i get the message
> chmod: cannot access `NVIDIA-Linux-x86-100.14.19-pkg1.run': No such file or directory


what am i doing wrong. I went to nvidia website and download the 100.14.19 driver and placed it onto my DESKTOP. Is that where its supposed to be? 

also when i try to type "cd Desktop" I get > -bash: cd: Desktop: No such file or directory


whats wrong?

is there something i am suppoed wayy before to do before i do everything here?

please note that i did a clean install of ubuntu and i have not done anything except updated the computer via update manager. NOTHING else. i downloaded the nvidia drivers and thats about everything. i havent install anything else.

---

### Post by dumplinknet on 2008-01-09
if i try to type > sh NVIDIA-Linux-x86-100.14.19-pkg1.run into terminal, i get this image 
[[IMG]http://img161.imageshack.us/img161/8254/screenshoteq7.png[/IMG]](http://imageshack.us)

what is it?

---

### Post by dumplinknet on 2008-01-09
anyone?

---

### Post by eduardoeltortuga on 2008-01-09
If it's on your desktop you have to cd there. "cd /home/yourusername/Desktop" This will take you to your desktop. I installed the drivers this way, but it didn't work for me. Envy didn't work either. Good luck!

---

### Post by Shazaam on 2008-01-09
Another way is to use the tilde (~) key when you cd. Ex. cd ~/Desktop
Also, once you get to the /Desktop folder do an ls to make sure the nvidia driver is there. Then you have to prepend sudo in front of sh Nvidia-Linux-driver.run.

```
sudo sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```

---

