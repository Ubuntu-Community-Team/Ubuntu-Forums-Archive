---
title: "Workaround to get sound on HP mini 1000 (or 1120 NR) with Jaunty"
date: 2009-04-24
forum: Multimedia Software
---

### Post by mozillar on 2009-04-24
After a clean install of Jaunty on my HP mini 1120 NR, there was no sound from the speaker. Sound from the headphone jack did work, however.

This is a known bug ([#318942]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942")) and is identified in the release notes as a known issue for the HP mini.

I did manage to find a workaround to use until an official fix is released:

In Synaptic:

   Add these to your repository sources:

   deb [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main
   deb-src [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main

   Click "Reload" and "Mark all Upgrades"

   Also make sure these two packages are installed:

      alsa-source
      module-assistant

   Click Apply to apply changes.


As root, edit /etc/alsa/alsa-source.conf
   On line 11 you should have:
   ALSA_CARDS="hda-intel"

In terminal:
   sudo m-a a-i alsa-source

Reboot and then un-mute headphone & speaker in volume control.

You should now have sound from both the speaker and headphone jack.

Caveats:
- You may need to un-mute the headphone and speaker to hear sounds after each reboot. Click the volume control and un-mute.
- You may want to mute the PC beep. Click the volume control, click "Preferences" and select the checkbox for PC Beep to make that track visible. Then mute the PC Beep.
- Haven't tested the mic, so I don't know if that works.

---

### Post by Downtuned on 2009-04-29
Awesome, I'll give it a try tonight and post the results : D

---

### Post by Rafzepersian on 2009-04-29
Hey thanks for the workaround, however I tried it on my HP Mini 1000, but still no sound....not from the front speakers or the headphone jack. I used to have 8.10 on it and while downloading updates, went ahead and updated the distro to 9.10. By the way when I go to System>Preferences>Sound and test for sound, I don't hear anything. Everything is set to ALSA hda-intel everywhere.

---

### Post by mozillar on 2009-04-29
Please confirm you have opened volume control and verified:
- Speakers are not muted
- Volume sliders are not set to minimum volume

If both those check out ok, I would see the comments re: the HP 1035 fix here...

[https://bugs.launchpad.net/netbook-remix/+bug/318942]("https://bugs.launchpad.net/netbook-remix/+bug/318942")

It sounds like the fix maybe slightly different depending on which HP mini model you have. I have a HP 1120NR. 

I'm hoping an official fix is released soon, at which point I plan on backing these changes out and using just the official repos. In the meantime, this fix continues to work for me. You can track progress on the bug here...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/+activity]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942/+activity")

---

### Post by kevindubrow on 2009-05-02
Hi, I'm trying to get this working, but I'm getting an error saying:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D86553DB9220067F

This happens after I add the sources and reload. How can I fix this? Thanks!

---

### Post by mozillar on 2009-05-02
To add the key, in Synaptic Settings..Repositories..Authentication see if 
you can import or accept the key for the trusted software source.

Alternately, you can add the key in terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 9220067F

Then launch Synaptic..Reload..Mark All Upgrades

Post back if this resolves the issue for you, thanks!!

---

### Post by kevindubrow on 2009-05-03
The way to fix the issue with the package manager didn't work, but the terminal did. The sound works perfectly! Thanks so much. Now I just need to get hibernate and suspend working properly, haha.

Edit- actually there is a problem. Even though I muted the pc beep, my computer stil makes an....incredibly loud and surprising beep when I shut it off.

---

### Post by mozillar on 2009-05-03
This is worth a try...

uncheck "Use sound to notify in event of error" in
System->Preferences->Power Management->General

I'm not experiencing your new "beep when shutting off" issue, so I'm just guessing now. :P

Please continue posting back with results. Thanks

---

### Post by kevindubrow on 2009-05-03
Umm, I followed these steps to get my mic working:

[http://ubuntuforums.org/showthread.php?p=6263260](http://ubuntuforums.org/showthread.php?p=6263260)

now I have no sound, do you think you can help?

---

### Post by mozillar on 2009-05-03
Sure, I'll see what I can do. The forum post you referenced for the mic I'm sure worked under Intrepid 8.10, but it may not work under Jaunty. Ideally, if you could back those changes out, that might be a better starting point. Before we start. your profile says you are running Gutsy, but I assume you are running Jaunty 9.04 now. What release are you currently running?

---

### Post by kevindubrow on 2009-05-03
9.04, sorry.

Edit: I undid all of the changes to my computer that would make my microphone work, but I still have no sound. I had a hunch anyway that that was not the problem, I randomly was no longer able to make calls in skype because of audio problems.

Edit 2: Sound randomly started working again. I still have all of the changes to fix the mic removed. Do you know of a different way to make the internal mic working without messing up the sound? Do you even think the changes were related to the sound going out? Thanks a lot...i know this is a lot to deal with.

---

### Post by mozillar on 2009-05-04
I tested my internal mic and it doesn't work with the fix I posted earlier. That's about what I expected. The focus so far seems to be more on the no sound from the speaker issue. There was a recent posting here that involves trying an update to the alsa driver, but that fix had it's own issues with volume control for me.

---

### Post by kevindubrow on 2009-05-04
Yeah, I'll try it tonight and edit this post to get back to you. Should I remove the fix you gave me first? If so, how should I go about doing that seeing as the package manager gave me a ton of extra packages when I selected the two you mentioned.

Oh and you want me to try the microphone fix after I use the fix from the link you just gave me, right?

---

### Post by mozillar on 2009-05-04
Removing the original fix would probably be best.

In Synaptic..Settings..Repositories: remove the two repos you added per my original fix. Then click reload.
In Synaptic..File..History: see what packages were added

I expect that will include:
+ alsa-source (1.0.19.dfsg-3ubuntu0~ppa0)
+ build-essential (11.4)
+ debconf-utils (1.5.26ubuntu3)
+ debhelper (7.0.17ubuntu4)
+ dpkg-dev (1.14.24ubuntu1)
+ fakeroot (1.12.1ubuntu1)
+ g++ (4:4.3.3-1ubuntu1)
+ g++-4.3 (4.3.3-5ubuntu4)
+ gettext (0.17-6ubuntu2)
+ html2text (1.3.2a-5)
+ intltool-debian (0.35.0+20060710.1)
+ kernel-package (11.015)
+ libmail-sendmail-perl (0.79.16-1)
+ libstdc++6-4.3-dev (4.3.3-5ubuntu4)
+ libsys-hostname-long-perl (1.4-2)
+ module-assistant (0.10.11ubuntu1)
+ patch (2.5.9-5)
+ po-debconf (1.0.15ubuntu1)

And these packages were likely updated:
+ alsa-base (1.0.18.dfsg-1ubuntu8) to 1.0.19.dfsg-3ubuntu0~ppa0
+ alsa-utils (1.0.18-1ubuntu11) to 1.0.19-2ubuntu0~ppa0
+ gdm (2.20.10-0ubuntu2) to 2.20.10-0ubuntu3~ppa0~xses1
+ libasound2 (1.0.18-1ubuntu9) to 1.0.19-1ubuntu0~ppa0
+ linux-sound-base (1.0.18.dfsg-1ubuntu8) to 1.0.19.dfsg-3ubuntu0~ppa0

Remove the packages that were added ONLY. 

Also click the Status button and look under the Installed (local or obsolete) section. If alsa-modules-2.6.28-11-generic is there, you can safely remove it. You should now be back where you started from.

Yeah, it's a lot of work. I'm hoping the update to alsa will be a less involved way of fixing the sound issue.

---

### Post by kevindubrow on 2009-05-04
I'm just going to keep a log of what happens:

Ok, I removed every package you mentioned, including the one in the Installed (local or obsolete) section.

I restarted. When everything loaded up, the front and headphone controls in the volume control were still muted at start up like they were when I had your fix installed. When I unmuted them, I had no sound so I ignored it as anything.

After running the sudo dpkg -i alsa-driver-linuxant_1.0.19.2_all.deb command from the steps given in the link, the terminal hung for awhile before I got an error box that said "volume control has shut down unexpectedly. Reload. Don't reload." I picked don't reload and the speaker icon disappeared from the taskbar. After this happened, the terminal was done with the process that it was hanging on.

I was supposed to add "options snd-hda-intel model=laptop" to "the end of the alsa-base file" but there was nothing in it...so I couldn't really put it in at the end...I just threw it in there and hit save.

I then had to add "options snd-hda-intel model=laptop" (the same thing) to the "end of the options file" but yet again, there was nothing previously in there so I just threw it in there and saved.

I restarted the computer according to the steps, and still noticed that there was no speaker icon in the taskbar.

I opened the sound manager through the terminal like the steps told me and unmuted everything and **I have sound.**



-Just some issues though. 

I have no sound icon, whys that?

My volume bar (via the volume up and down buttons on the keyboard) only goes halfway down before I can not hear anything from the speakers.



Ok, I'm glad this worked! Now...shuld I try to see if that microphone fix works?

---

### Post by mozillar on 2009-05-05
Your alsa-base.conf file should not have been empty. I think you created a new alsa-base. when you wanted alsa-base.conf

/etc/modprode.d/alsa-base.conf  is the full path to the file

As for the missing volume control, I've got no idea.

I took another look at the mic fix you originally tried. You can try implementing that again, but I have a feeling some of those changes will overwrite/break the speaker fix you just applied, especially the alsa-base package. So for the time being, you may have to choose speaker sound over the mic. I hoping some progress can be made on bug [#318942]("https://bugs.launchpad.net/netbook-remix/+bug/318942") soon, so there isn't this trade-off.

---

### Post by kevindubrow on 2009-05-05
The file you told me about in your last post didn't exist on my computer.

I used the terminal to open the alsa file, but when I tried to add the options snd-hda-intel model=laptop line to it, I got an error that said that the file did not exist.

---

### Post by mozillar on 2009-05-05
Sorry, I am stumped then. If you find a solution, please post back here.

If/when Ubuntu releases a fix, I will post it here as well.

---

### Post by kevindubrow on 2009-05-05
Sure thing. Thanks a lot for the help!

---

### Post by Downtuned on 2009-05-05
Sadly I tried everything on this thread and read every related post I could find, still nothing, I made a bootable usb drive with 8.4 on it and tried it on my mini and like I expected there was not a problem with sound at all, or anything else for that matter, so I decided to install it and now my wireless isn't working Dx
When i click connect to network and after I enter in the encryption key and click connect it seems like rejects my key after a while even though I've checked a thousand times it's typed in correctly, weird.

The proprietary drivers for my card where disabled by default, after enabling them and rebooting it still won't connect.

---

### Post by mozillar on 2009-05-05
yeah, the wireless issues are why I skipped right to Jaunty. Just as a wild idea, would trying the HP MIE interface work for you?

Here's some pics:

[http://kerbaukuat.wordpress.com/hp-mini-mie/]("http://kerbaukuat.wordpress.com/hp-mini-mie/")

Here's the link to HP's site to download.

[http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=ob-68020-1&jumpid=reg_R1002_USEN]("http://h10025.www1.hp.com/ewfrf/wc/genericSoftwareDownloadIndex?cc=us&dlc=en&lc=en&softwareitem=ob-68020-1&jumpid=reg_R1002_USEN")

The HP MIE is a tweaked Ubuntu Hardy 8.04 installation. I believe you HAVE to put this on a USB drive to install and it wipes out everything on your drive. My HP 1120NR came with this and the mic, sound and wireless all worked with that. But I like to run with scissors and so I put on Jaunty instead. lol

---

### Post by 30otsix on 2009-05-05
> **mozillar said:**
> My HP 1120NR came with this and the mic, sound and wireless all worked with that. But I like to run with scissors and so I put on Jaunty instead. lol

lol, me too. Just wanted to say thanks. Your solution fixed the sound issues on my 1120NR in about 5 minutes.

---

### Post by Downtuned on 2009-05-06
> **mozillar said:**
> yeah, the wireless issues are why I skipped right to Jaunty. Just as a wild idea, would trying the HP MIE interface work for you?

I'm pretty sure it would solve the problem but I only have 1 gig thumb drives, nothing bigger D: but it's cool I'm gonna keep reading up on this issue and see what I find. If all else fails I'll just borrow a 4 gig drive from a friend or something, once there's an official fix to the sound bug in jaunty I'll probably switch back to it haha.

---

### Post by 30otsix on 2009-05-08
> **30otsix said:**
> Your solution fixed the sound issues on my 1120NR in about 5 minutes.I guess I spoke to soon. After a reboot the next day, the entire install was fubar'd...back to 8.10 for now.

---

### Post by roachdaniel on 2009-05-31
To all I tried the items in the following post [http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html](http://www.ubuntugeek.com/workaround-to-get-sound-on-hp-mini-1000-or-1120-nr-with-jaunty.html)
it is basically the same to get the sound working and a guy in the reply section added a method for getting the mic to work. So now I have speaker sound and built in mic functioning for skype calls. my question is, "is ther a way to make these changes stick so I don't have to unchech and recheck everything every time I reboot?

Thanks to everyone, i had xp on my netbook switched to Jaunty NBR  then to the HP Mini MI and back to Jaunty NBR in about 4 days. I am sticking at this point.

---

### Post by kevindubrow on 2009-06-02
Thanks so much for the link! I really want to get the mic working for Skype, but I am having trouble upgrading to the 2.6.28.12-generic kernel.

I just have no clue how to do that and its a required step. Any ideas? Thanks a lot!

---

### Post by aysiu on 2009-06-02
Since some people appear to still have issues, I'm just going to put in a cheap plug here. I created a Ubuntu remix of Jaunty specifically to address sound issues on the HP Mini 1120nr (it may work for the other 1000 series netbooks, but I'm not sure).

If anyone wants to try it, I've got a little project page for it here:
[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

---

### Post by xsunxspotsx on 2009-06-06
Whenever I try to do this, I get a 404 Not Found errors when it searches for [http://ppa.launchpad.net](http://ppa.launchpad.net).  This is the only fix I could find for the HP mini sound in Jaunty so far

---

### Post by aysiu on 2009-06-06
> **xsunxspotsx said:**
> Whenever I try to do this, I get a 404 Not Found errors when it searches for [http://ppa.launchpad.net](http://ppa.launchpad.net).  This is the only fix I could find for the HP mini sound in Jaunty so far
Try my HP Mini Remix. I've done all the sound fixes for you.

---

### Post by kevindubrow on 2009-06-18
Hey, if I try your OS will I still be able to get the regular Ubuntu updates? 

And is there a way to upgrade to it so I don't have to move my files and reinstall all of my programs?

---

### Post by aysiu on 2009-06-18
> **kevindubrow said:**
> Hey, if I try your OS will I still be able to get the regular Ubuntu updates? It's not my OS. It's not a fully separate distro. It's a Ubuntu remix. All it means is I've taken Ubuntu, modified some config files, changed a few packages and settings, and then made an .iso out of it.

It is fully Ubuntu-compatible, as it uses only Ubuntu repositories. At a very basic level, it's just Ubuntu but with a sound fix for the HP Mini 1120nr. Some people have reported good results for other HP Mini models, but the only one I have tested it on is the 1120nr.

> And is there a way to upgrade to it so I don't have to move my files and reinstall all of my programs? No. I'm not a programmer. If I were, I could make a .deb metapackage that would draw in the appropriate new packages, take out the appropriate old packages, and make the config files tweaks.

---

### Post by btron on 2009-06-23
thank you thank you thank you thank you aysiu!!! i was trying alllll day yesterday to get my sound back! it was working at first, but i wanted to do a clean install and start from scratch so i wouldn't have all these excess sound programs that i had added due to trial and errors -- very few of them actually worked anyway. 

but once i tried the usual fix (the one at the beginning of this thread) which normally worked -- didn't. so all day long i was thrashing to figure out wtf was going wrong, until i was about to give up and try mandriva to see if it were any better, i remembered seeing your post (which i was hesitant because i don't have the same hp model as you) but i downloaded, installed and vioala! sound! not a bad color scheme either ;) 

and i don't even have to unmute everytime! 
plus no maximus! phew! thanks so much again! mad props! 
thanks so much for setting up that iso. had no problems with it.

---

### Post by aysiu on 2009-06-23
Glad it worked for you!

---

### Post by wiigee on 2009-06-27
I did this workaround after installing jaunty a while back and it worked great. but a few days ago, i lost all sound. i cant figure out why, i made no changes to anything other than the system updates from ubuntu. i really have no idea what to do or what could have caused this. anyone else run into this?

---

### Post by mozillar on 2009-06-27
Every time there is a kernel update, you will need to 

sudo m-a a-i alsa-source

and then reboot for sound to be fixed again with this workaround.

I'm beginning to think there won't be an official fix for Jaunty...EVER. So when you see kernel updates in Update Manager, you will need to manually do this after applying the kernel updates. Fun!

---

### Post by wiigee on 2009-06-27
it didnt work =(

---

### Post by Geister on 2009-06-27
Okay,

What is the work around for us HP Mini users that have LPIA processors???
The HP MINI 1000 doesn't use a PPA processor it has a LPIA?

I tried everything to try to get sound working! Nothing works so far

> **mozillar said:**
> After a clean install of Jaunty on my HP mini 1120 NR, there was no sound from the speaker. Sound from the headphone jack did work, however.

This is a known bug ([#318942]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942")) and is identified in the release notes as a known issue for the HP mini.

I did manage to find a workaround to use until an official fix is released:

In Synaptic:

   Add these to your repository sources:

   deb [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main
   deb-src [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main

   Click "Reload" and "Mark all Upgrades"

   Also make sure these two packages are installed:

      alsa-source
      module-assistant

   Click Apply to apply changes.


As root, edit /etc/alsa/alsa-source.conf
   On line 11 you should have:
   ALSA_CARDS="hda-intel"

In terminal:
   sudo m-a a-i alsa-source

Reboot and then un-mute headphone & speaker in volume control.

You should now have sound from both the speaker and headphone jack.

Caveats:
- You may need to un-mute the headphone and speaker to hear sounds after each reboot. Click the volume control and un-mute.
- You may want to mute the PC beep. Click the volume control, click "Preferences" and select the checkbox for PC Beep to make that track visible. Then mute the PC Beep.
- Haven't tested the mic, so I don't know if that works.

---

### Post by kevindubrow on 2009-06-30
I thought LPIA was a kernel, not a processor.


That being said, I only know of two versions of Ubuntu that use LPIA: the HP MIE and Aysiu's Ubuntu Remix and both of those versions have sound working out of the box.

If you are using a regular flavor of Ubuntu or Ubuntu Netbook Remix and this workaround didn't work for you, its probably because of some update you did (I updated and lost my sound).

You should really check out Aysiu's remix. Personally I haven't tried it, but it looks like it would be great for some people.

EDIT:
Once I ran "sudo m-a a-i alsa-source" my sound started working again. Fun! :D

---

### Post by Geister on 2009-06-30
LPIA - Low Powered Intel Architecture, as far from what I understand it is achtitecture for the ATOM CPU.
 
With that out of the way,
 
I tried the  Aysiu's remix and it fixes sound BUT BREAKS Bluetooth! Also per his webpage he only supports the HP MINI 1120, hence maybe why the BT doesn't work.
And YES I did already tried to recomplie the Broadcom LTA drivers and it still doesn't work.
 
So right now, there isn't one Distro out that makes the HP MINI 1000 100% functional.
 
 
> **kevindubrow said:**
> I thought LPIA was a kernel, not a processor.
 
 
That being said, I only know of two versions of Ubuntu that use LPIA: the HP MIE and Aysiu's Ubuntu Remix and both of those versions have sound working out of the box.
 
If you are using a regular flavor of Ubuntu or Ubuntu Netbook Remix and this workaround didn't work for you, its probably because of some update you did (I updated and lost my sound).
 
You should really check out Aysiu's remix. Personally I haven't tried it, but it looks like it would be great for some people.
 
EDIT:
Once I ran "sudo m-a a-i alsa-source" my sound started working again. Fun! :D

---

### Post by aysiu on 2009-06-30
I'd help fix Bluetooth, except that I have no Bluetooth devices...

---

### Post by Geister on 2009-06-30
You don't need a physical bluetooth periphal, just as long as the HP mini you have has the Broadcom WiFi/Bluetooth card. 
 
If the Distro recognizes the Bluetooth interface it will show the symbol on the upper right hand. Once that symbol appears then there is really no need to attached to another bluetooth device, unless you want confirmation. A good device I use for testing is my cell phone.
 
Currently your distro does not recognize it and only shows the WiFi bars.
 
> **aysiu said:**
> I'd help fix Bluetooth, except that I have no Bluetooth devices...

---

### Post by aysiu on 2009-06-30
> **Geister said:**
> You don't need a physical bluetooth periphal, just as long as the HP mini you have has the Broadcom WiFi/Bluetooth card. 
 
If the Distro recognizes the Bluetooth interface it will show the symbol on the upper right hand. Once that symbol appears then there is really no need to attached to another bluetooth device, unless you want confirmation. A good device I use for testing is my cell phone.
 
Currently your distro does not recognize it and only shows the WiFi bars.
Maybe check in System > Preferences > Startup Programs to see if Bluetooth is enabled?

---

### Post by Geister on 2009-06-30
Maybe I should have qualified some facts, I am not the typical idiot user, I made sure BEFORE making posts on this board to check that FIRST. The driver that is being used does not recognize the BT part of the WiFi module.  I have already troubleshooted the system to confirm that it is a driver issue and not a "soft switch" in the operating system. 

> **aysiu said:**
> Maybe check in System > Preferences > Startup Programs to see if Bluetooth is enabled?

---

### Post by aysiu on 2009-06-30
> **Geister said:**
> Maybe I should have qualified some facts, I am not the typical idiot user, I made sure BEFORE making posts on this board to check that FIRST. The driver that is being used does not recognize the BT part of the WiFi module.  I have already troubleshooted the system to confirm that it is a driver issue and not a "soft switch" in the operating system. I didn't mean to imply you were an idiot. I just wanted to make sure all the bases were covered. If it is a driver issue, I'm not sure there is an easy fix for it. I'm just using the restricted Broadcom driver Ubuntu automatically installs.

My guess is you would have to use some kind of special *ndiswrapper* or *fwcutter* workaround.

---

### Post by Geister on 2009-06-30
Are you using the latest one? Because if you are, I should it listed as "Proprietary Driver" when I open up the Hardware Drivers, and it is not listed, so I don't think you are usng the Latest Broadcom Linux ATA driver for the Broadcom Wifi/BT cards.

> **aysiu said:**
> I didn't mean to imply you were an idiot. I just wanted to make sure all the bases were covered. If it is a driver issue, I'm not sure there is an easy fix for it. I'm just using the restricted Broadcom driver Ubuntu automatically installs.

My guess is you would have to use some kind of special *ndiswrapper* or *fwcutter* workaround.

---

### Post by fooman on 2009-07-08
> **aysiu said:**
> Since some people appear to still have issues, I'm just going to put in a cheap plug here. I created a Ubuntu remix of Jaunty specifically to address sound issues on the HP Mini 1120nr (it may work for the other 1000 series netbooks, but I'm not sure).

If anyone wants to try it, I've got a little project page for it here:
[http://www.psychocats.net/hpminiremix](http://www.psychocats.net/hpminiremix)

hey aysiu...i have installed your iso on a hp mini 1035nr

everything works great right out of the box,  thank you very much!  :p

one question...i like my desktop to be clean...how do i hide all of those desktop folders (documents, music, video, etc, etc...)??

thanks

---

### Post by aysiu on 2009-07-08
> **fooman said:**
> hey aysiu...i have installed your iso on a hp mini 1035nr

everything works great right out of the box,  thank you very much!  :p

one question...i like my desktop to be clean...how do i hide all of those desktop folders (documents, music, video, etc, etc...)??

thanks
Did you install the 090704 release? I thought I'd fixed this problem in the latest release.

Edit the ~/.config/user-dirs.dirs file with Gedit or Nano.

Change ```
XDG_DESKTOP_DIR="$HOME/"
``` to ```
XDG_DESKTOP_DIR="$HOME/Desktop"
``` You may have to log out to have the setting take effect.

---

### Post by fooman on 2009-07-09
hey that worked!!  :p

thank you.

---

### Post by aysiu on 2009-07-09
> **fooman said:**
> hey that worked!!  :p

thank you.
Do you know if you were using the June 30 or July 4 release?

That was still a problem in the June 30 one, but I *think* it should have been fixed in the July 4 release.

---

### Post by fooman on 2009-07-09
> **aysiu said:**
> Do you know if you were using the June 30 or July 4 release?

That was still a problem in the June 30 one, but I *think* it should have been fixed in the July 4 release.

it was: hp-mini-remix-9.04-090704.iso ...if that helps.

runs really well on here, btw....  i was not quite sure what to expect when i picked this thing up (used from craigslist....with 2 gigs ram installed).  i was surprised at how fast the pre-installed xp booted up,  but i immediatlely put your iso on a usb stick and installed onto here,  completely wiping xp along with it. 

not really surprised,  but overjoyed non the less when i found that after the install had completed, and i booted into ubuntu the first time....everything was working!!  ....wireless, webcam, sound, scroll function in the trackpad, compiz...all working without me having to lift a finger!  :p

thanks again.

---

### Post by aysiu on 2009-07-09
> **fooman said:**
> it was: hp-mini-remix-9.04-090704.iso ...if that helps. It doesn't help, but it's good to know. I guess that's just some kind of weird Remastersys bug. I thought I'd fixed that, but maybe it can't be fixed. Thanks for confirming that.

> runs really well on here, btw....  i was not quite sure what to expect when i picked this thing up (used from craigslist....with 2 gigs ram installed).  i was surprised at how fast the pre-installed xp booted up,  but i immediatlely put your iso on a usb stick and installed onto here,  completely wiping xp along with it. 

not really surprised,  but overjoyed non the less when i found that after the install had completed, and i booted into ubuntu the first time....everything was working!!  ....wireless, webcam, sound, scroll function in the trackpad, compiz...all working without me having to lift a finger!  :p

thanks again. Glad you like it!

---

### Post by wiigee on 2009-07-10
can someone help me reverse this? it worked for jaunty for a bit then stopped (as stated earlier) i decieded to switch to Linux Mint. The headphone port worked just fine but the speakers didnt same as in jaunty. Whin i did all these steps it killed the port. im just trying to get that to work again, i can live without speakers. anything i can do to reverse this?
also for those that dont know, Mint is ubuntu based and is pretty much the same at its core, so any ubuntu fixes to this should work in mint.

edit: sorry didnt see that this was explained on page two.

---

### Post by gnu.enri on 2010-02-18
> **mozillar said:**
> After a clean install of Jaunty on my HP mini 1120 NR, there was no sound from the speaker. Sound from the headphone jack did work, however.

This is a known bug ([#318942]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/318942")) and is identified in the release notes as a known issue for the HP mini.

I did manage to find a workaround to use until an official fix is released:

In Synaptic:

   Add these to your repository sources:

   deb [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main
   deb-src [http://ppa.launchpad.net/minichoco-team/ppa/ubuntu](http://ppa.launchpad.net/minichoco-team/ppa/ubuntu) jaunty main

   Click "Reload" and "Mark all Upgrades"

   Also make sure these two packages are installed:

      alsa-source
      module-assistant

   Click Apply to apply changes.


As root, edit /etc/alsa/alsa-source.conf
   On line 11 you should have:
   ALSA_CARDS="hda-intel"

In terminal:
   sudo m-a a-i alsa-source

Reboot and then un-mute headphone & speaker in volume control.

You should now have sound from both the speaker and headphone jack.

Caveats:
- You may need to un-mute the headphone and speaker to hear sounds after each reboot. Click the volume control and un-mute.
- You may want to mute the PC beep. Click the volume control, click "Preferences" and select the checkbox for PC Beep to make that track visible. Then mute the PC Beep.
- Haven't tested the mic, so I don't know if that works.
HI !

I have a mini 110c and i had the same problem with the audio, but i installed ubuntu 9.10 and everything is running now !! !!

Only one advertisement, the wireless did not work, I had to install the "These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware." a driver not free, you can install it or the free one in "System" >"administration"> "hardware drivers" (you need internet, so with a wire).

buona fortuna per tutti
ciao

---

