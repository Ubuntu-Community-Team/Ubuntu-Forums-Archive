---
title: "Hulu Stopped Working"
date: 2010-01-11
forum: Multimedia Software
---

### Post by deeptendu on 2010-01-11
Linux x86_64 Ubuntu/8.04 (hardy) Firefox/3.0.17

Hulu stopped working for me yesterday. I've been using hulu as long as I've had ubuntu and this is the first time I've ever had a problem with it.

Videos load and come up with the message "sorry we are unable to load this video at this time, please check your internet connection and try again". I also sometimes get error messages saying that a script is causing some adobe 10 to run slowly.
Everything else still works including youtube and ustream. The only changes to my computer that I've done recently is to download the firefox add-on "multi-links" and the music player "audacious", both of these have been uninstalled from my computer to no effect.

---

### Post by solotwit on 2010-01-11
same issue here. I'm using Chrome and can't find anything that helps so far. 

It also won't stream in Firefox either.

---

### Post by LuisGMarine on 2010-01-11
weird I got the same message and I thought it was my internet connection.  I just found out that it works through Firefox but not chrome.  Also downloading an app like Boxee doesn't fix the issue either.  I'm not sure what is going on here, but I know my internet connection is rock solid.  Must be something with either flash or something else.

---

### Post by deeptendu on 2010-01-11
Hmm so it works in your firefox? I wonder if hulu itself changed something in the last few days.
It's good to know that Boxee didn't help you any, that was the next thing I was going to try. Now, I'm sort of out of ideas since I uninstalled and reinstalled my flash and am getting the same problem.

---

### Post by LuisGMarine on 2010-01-11
I'm almost tempted to install 32 ubuntu to see if someone is having the same problem.  Can anyone confirm that this also happens on 32-bit and not just us with 64 bit systems?

---

### Post by Palanthas on 2010-01-11
Worked on mine...  Ubuntu 9.10 (Karmic) 64bit with Firefox 3.5.7 (no add-ons)

According to Hulu's Support site [Hulu Support]("http://www.hulu.com/support") you need firefox 1.5 or above...

> Software Requirements

To enjoy videos at Hulu, you will need the following software installed on your computer:

    * Internet Explorer 6.0 or above, Firefox 1.5 or above, or Safari 2.0 or above
    * JavaScript and Cookies must also be enabled
    * Adobe Flash Player 10.0.22 or above
    * Microsoft Windows XP SP2 or later, Macintosh OS X or Linux 

---

### Post by markbuntu on 2010-01-11
Hulu just changed their flash server so you need flash 10.  There is a update for hardy for that but it could put the libflashplayer.so in usr/lib/adobe-flash instead of usr/lib/flashplugin-nonfree where it needs to be in hardy so you might have to move it there to get it working with firefox.

---

### Post by LuisGMarine on 2010-01-11
Well I'm using the 64-bit flash beta/alpha (don't care what stage it is) from the adobe download center.  I've just downloaded the tar.gz and dropped the libflashplayer.so into

```
/usr/lib/mozilla/plugins
/usr/lib/firefox-addons/plugins
/usr/lib/firefox-3<hit tab>/plugins
```

and also 

```
~/.mozilla/plugins
```

Not sure about the last directory but some people recommend dropping it in there.

---

### Post by deeptendu on 2010-01-11
I have shockwave flash 10.0 r32. Right now libflashplayer.so is in ```
usr/lib/firefox-addons/plugins
``` as well as in ```
usr/lib/firefox-3.0.17/plugins
```.
I don't have an adobe-flash file in lib.

---

### Post by Ian9056 on 2010-01-11
Another 64-bit user here who had Hulu stop working this weekend.

What's strange is that Hulu's desktop client works still perfectly fine, though I'm not on the latest version of that.

---

### Post by zentu on 2010-01-11
Due to a number of hard to peg down issues, and one possibly major security issue, 64-bit users are actually on the older flash9.  Opening up synaptic (or your choice) and reading the version of all available /flashplugin-nonfree yields a line like this: 10.0.1.218+really9.0.260.0ubuntu1.

You'll note that in all available versions, the package maintainers offer only version 9.

Doing anything explained past this point removes embedded flash media management for webpages, AS WELL AS ANY EXPRESSED OR IMPLIED SECURITY RELATED THERETO from Canonical Ltd and places it in the hands of the individual administrator (if your able to do what follows, that'd be you).

IF! you value the "usability in media" experience more than security and/or haven't had many of those annoying flash for 64bit bugs, you can perform the following tasks:

Remove flashplugin-nonfree.
Obtain the latest 64bit flash from Adobe
 : [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)
And finally install into all three of the directories mentioned earlier
 - the reason being variation in policies and configuration choices.

Thereafter, the next time you start a browser (most browsers anyway), you will have your 64bit flash10 experience.

-- Private note:

Despite having had a short run doing this very thing, Hulu is now regularly giving me the 'unable to stream...check your internet connection' line.  I'm still unsure of this cause.

---

### Post by the_weekend on 2010-01-11
I'm having the same issue. Deleted all instances of macromedia flash and reinstalled their newest beta (10 r42). Ubuntu 8.04 64-bit. I thought that the upgrade from firefox 3.0.8 to 3.0.17 was causing the issue, but it won't let me "force version" in synaptic to test. The 3.0.8 files seem to have been wiped on the packages website and now have the 3.0.17 version. 

Update: It's not working in Chrome either, so I guess it's probably Hulu's fault somehow.

---

### Post by LuisGMarine on 2010-01-11
For some reason I'm now getting the error in Firefox too.  If you open up firefox preferences, set the option to "clean/delete cache when I close down firefox." Then close out firefox and launch it again and try hulu again it *should* work.

Doing this every time for me allows me to view at least 1 or 2 videos before I have to re-due it because of the error.

---

### Post by the_weekend on 2010-01-11
> **LuisGMarine said:**
> For some reason I'm now getting the error in Firefox too.  If you open up firefox preferences, set the option to "clean/delete cache when I close down firefox." Then close out firefox and launch it again and try hulu again it *should* work.

Doing this every time for me allows me to view at least 1 or 2 videos before I have to re-due it because of the error.

I tried that, but it doesn't work at all.

---

### Post by deeptendu on 2010-01-11
Clearing the cache doesn't help at all with me either.

---

### Post by emuller on 2010-01-12
Hulu stopped working for me this weekend as well.  I have been using it since 8.04  I am currently running Ubuntu 9.10x86_64.  My internet explorer is Firefox 3.5.5.  I currently have the Adobe 10.0.42.34ubuntu0.9.10.1 flashplayer (alpha), and I have no other flashplayers running.  Hulu worked with this setup until this weekend.  Also, my connection is fine (12Mbps cable) and I can still run hulu rebooting to Windows 7.  I hadn't updated any drivers/packages for a week or so before it suddenly stopped working so it is not due to a change in my computer.  I can still watch youtube videos, run pandora, etc.  Haven't tried downloading alternate ways of watching hulu yet.

---

### Post by kilroy0097 on 2010-01-12
Well [http://www.fancast.com](http://www.fancast.com) pulls up just fine and works. Also official adobe tests show my flash is working just fine. 
I have:

Adobe Flash 64bit install - v.10.0.32.18
Firefox 64bit install - v.3.0.17

I say it's Hulu who messed things up. Maybe they weren't satisfied with shutting down PS3 consoles streaming Hulu, they needed to also shut down Ubuntu? :popcorn:

---

### Post by Dennis N on 2010-01-12
In Ubuntu 8.04 32 bit the same problem also exists. 'flashplugin-nonfree' offered via in Synaptic is:

"10.0.1.218+really9.0.260.0ubuntu1".

In Firefox (3.0.17 - 32 bit), 'Tools > addons > plugins' shows flash version 9.0.260 in use. (location: /usr/lib/flashplugin-nonfree/)

Hulu apparently detects the flash version as 9, so it won't work. Adobe test page also indicates 9.0.260.

As suggested above by zentu, a solution may be to remove flashplugin-nonfree and put copies of adobe-flashplugin into the directories mentioned.

(*Note: I didn't do this, since I have a Karmic VM running under Hardy, and it plays Hulu without problems, so I just use that*.)

---

### Post by the_weekend on 2010-01-12
The Flash 9 theory would be great, however, many of us are using flash 10 and it won't work.

---

### Post by LuisGMarine on 2010-01-12
For 64-bit users.  Try downloading the alpha plugin from the link a few posts above. 

Then refer back to my post #8 and drop the libflashplayer.so into those 4 directories mentioned and try again.  I just did that and I'm not having any problems.  Wonder if its working for anyone else.

---

### Post by MooPi on 2010-01-12
Just loaded the most recent libflashplayer.so and Hulu still does not work UGH!:x

---

### Post by Dennis N on 2010-01-13
Got around to fixing the problem in post #18 for Ubuntu 8.04 32 bit. This got me a working ver. 10 flash player. It might help someone else with the same setup.

(method works for 32 bit Ubuntu 8.04 with Firefox 3.0.17)

1) Using Synaptic, mark 'flashplugin-nonfree' package for removal and apply. This also removes its directory.

2) Open 'System > Administration > Software Sources' and in the 'Third Party Software' tab mark the top box showing 'archive/canonical.com/ubuntu hardy partner' to include that source. This repo has the adobe flash player we need.

3) Reload package lists. Install 'adobe-flashplugin' package with Synaptic (if it is not offered as an update). 

This new adobe-flashplugin is installed into a directory (/usr/lib/adobe-flashplugin) where it is not detected by Firefox. So, take these additional steps using command line:

4) Re-create flashplugin-nonfree directory using command line:

```

cd /usr/lib
sudo mkdir flashplugin-nonfree

```

5) copy the adobe-flashplugin to this directory using command line:

```

cd /usr/lib/adobe-flashplugin
sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree

```
Restart Firefox. Check for correct plugin (shockwave flash 10.0 r42) in:

Tools > AddOns > Plugins 

Hulu now detects flash player 10 and works.

---

### Post by ubudv on 2010-01-13
hulu also stopped working for me, no reason at all. I am using 9.10 64bit with chrome and 64bit flash. It just stopped working a few days ago or so. huludesktop client will play fine for a few minutes and then I get an error and have to restart the video again.

---

### Post by joshkidd on 2010-01-13
I've had the same problem with Ubuntu 9.10 64-bit.  I've tried all of the things in this thread and nothing has helped me get Hulu working in a web browser again.  Hulu Desktop, on the other hand, has worked perfectly for me so far.  I would recommend anyone having difficulty try that.

---

### Post by archimedez on 2010-01-14
You can use Hulu's desktop client while the issues are being sorted out. 
[http://www.hulu.com/labs/hulu-desktop-linux]("http://www.hulu.com/labs/hulu-desktop-linux")

> **solotwit said:**
> same issue here. I'm using Chrome and can't find anything that helps so far. 

It also won't stream in Firefox either.

---

### Post by LuisGMarine on 2010-01-14
Hulu desktop works decently.  It plays most videos but there are some where it seems to lock up.  You can easily fix the problem by picking another video.  Usually the ones it locks up on are boring, so it does me a favor ... :popcorn:

---

### Post by DarkCloud9 on 2010-01-15
I had the same problem on 64-bit 9.10. I deleted every instance of libflashplayer.so on my machine, then installed the flashplugin-installer package via Synaptic.

Hulu works now.

---

### Post by LuisGMarine on 2010-01-15
> **DarkCloud9 said:**
> I had the same problem on 64-bit 9.10. I deleted every instance of libflashplayer.so on my machine, then installed the flashplugin-installer package via Synaptic.

Hulu works now.


I'm going to give that a try.  I've been having some serious issues with flash being extremely choppy now and I figured that it might have something to do with the beta.

---

### Post by pricetech on 2010-01-15
I haven't tried hulu, but fancast stopped working and so did youtube.  Opera and Seamonkey quit yesterday.  I downloaded the latest flash library and copied it to the relevant directories and nothing changed.  This morning firefox quit working.

As far as the installer, I didn't know that was fixed.  I recall being prompted to update a couple of weeks ago on my laptop, but that killed flash on it.  I haven't been prompted for any updates on my desktop.

I may try removing the library and using the installer.

---

### Post by tahoe on 2010-01-15
Very Nice...

I finally got Hulu to work using comment #27, so...

```
sudo updatedb
locate libflashplayer.so
# Remove those files
sudo aptitude install flashplugin-installer
# Restarted Firefox
```

---

### Post by the_weekend on 2010-01-15
Worked for me too. Cool! It looked like it installed a few more libraries than I had previously, so maybe that was the problem...

> **tahoe said:**
> Very Nice...

I finally got Hulu to work using comment #27, so...

```
sudo updatedb
locate libflashplayer.so
# Remove those files
sudo aptitude install flashplugin-installer
# Restarted Firefox
```

---

### Post by sese_k on 2010-01-17
First also had the problem with "We are unable to stream this video...".
Then I did this:

> **tahoe said:**
> Very Nice...

I finally got Hulu to work using comment #27, so...

```
sudo updatedb
locate libflashplayer.so
# Remove those files
sudo aptitude install flashplugin-installer
# Restarted Firefox
```

Then I once got the message "This video is currently unavailable..." and after that I got the "We are unable to stream this video..." message. Does anybody have an idea why these two different messages and why "This video is currently unavailable..." only once and then again the old message?

---

### Post by deeptendu on 2010-01-18
I'm having problems removing the old files. It says "permission denied", but I'm sudo. :(

---

### Post by LuisGMarine on 2010-01-18
One extra thing that you can do is run nautilus in root mode.  

```
gksudo nautilus
```

Then try navigating to the folder and deleting it that way.

---

### Post by dogooder on 2010-01-22
> **tahoe said:**
> Very Nice...

I finally got Hulu to work using comment #27, so...

```
sudo updatedb
locate libflashplayer.so
# Remove those files
sudo aptitude install flashplugin-installer
# Restarted Firefox
```

Thanks, worked for me.

---

### Post by stevo1977 on 2010-01-22
I'm still running 8.10 (too busy w/ school to mess the headache of upgrading), and the above worked for me except:

- There was no "flashplugin-installer" via aptitude or synaptic
- After deleting all instances of the suggested .so file, I told synaptic to reinstall "flashplugin-nonfree"

Restarted Firefox and went to Hulu and the vids started right up.  Thanks, everyone, for your help.

Cheers,
stevo

---

### Post by deeptendu on 2010-01-23
Flashplugin-installer doesn't show up in aptitude of synaptic. Downloading flashplayer-nonfree just gives me flash 9 back.:confused:

---

### Post by jlo_sandog on 2010-01-23
I'm still having no luck with hulu.com and firefox x86_64. The hulludesktop application does work. To see the desktop application on your browser go to [http://download.hulu.com/huludesktop.swf](http://download.hulu.com/huludesktop.swf)

---

### Post by dardack on 2010-01-23
Me too.  I will not use the wrapper, i use the beta/alpha from Adobe labs, 10.0.42 (Hope .1 is here soon).  Hulu will not work in chrome or in firefox.

The desktop does work, but didn't watch a full show so don't know if it quits after a time.  Annoying as all heck.

---

### Post by Uncle Spellbinder on 2010-01-24
Working fine here. Desktop, Firefox 3.5.7 and SeaMonkey 2.0.2

---

### Post by dardack on 2010-01-24
> **Uncle Spellbinder said:**
> Working fine here. Desktop, Firefox 3.5.7 and SeaMonkey 2.0.2

64bit Ubuntu and 64bit flash player?

---

### Post by Uncle Spellbinder on 2010-01-24
> **dardack said:**
> 64bit Ubuntu and 64bit flash player?

A 64 bit Karmic laptop install and my 32 bit Karmic desktop install. Neither has issues with Hulu Desktop or Hulu in a browser.

---

### Post by Electric Bill on 2010-01-25
Thanks for the tip about Hulu Desktop folks.
I tried every other suggestion i could find on on multiple forums and this was the only one that worked - plus I got a great new app.

Bill

---

### Post by mgmiller on 2010-01-25
Clean install of 64 bit karmic using the 64 bit flash plugin from adobe in the 3 locations mentioned in post #8.   I also tried setting up an account with hulu as others said that got it woriking.   No joy.  The only thing that works is the hulu desktop.

---

### Post by dardack on 2010-01-25
> **Uncle Spellbinder said:**
> A 64 bit Karmic laptop install and my 32 bit Karmic desktop install. Neither has issues with Hulu Desktop or Hulu in a browser.

64bit flash player or the wrapper to 32?

---

### Post by kazik on 2010-01-26
What works:

[LIST]
[*] default 32-bit wrapped flash in Firefox, in fresh 64-bit Karmic install
[*] 64-bit flash in 64-bit huludesktop on 64-bit Arch
[/LIST]

What doesn't work:

[LIST]
[*] 64-bit flash in Firefox or Chromium on 64-bit Arch
[/LIST]

Why am I still not happy? Simple. Want 64-bit flash in a web browser to work with hulu.

---

### Post by markbuntu on 2010-01-26
You should check the path that firefox and chromium use to look for the flashplayer. It is entirely probable that they are looking in the wrong place.

---

### Post by dardack on 2010-01-27
> **markbuntu said:**
> You should check the path that firefox and chromium use to look for the flashplayer. It is entirely probable that they are looking in the wrong place.

They aren't, since youtube and all other flash sites I visit works.  Only Hulu in the webbrowser doesn't work.

---

### Post by deeptendu on 2010-01-27
Same here, firefox recognizes and uses flash 10. It just doesn't work with hulu.

---

### Post by markbuntu on 2010-01-27
Are you sure that firefox is using flash10.r42?
I ask because it works for me on hulu but after i installed flash10 firefox was still using flash9 until I replaced the libflashplayer.so.

---

### Post by deeptendu on 2010-01-27
I uninstalled flash 9, made sure that firefox wasn't using any flash, and then got flash 10.

---

### Post by Electric Bill on 2010-01-30
When this all started I had lost Hulu after an update but I could still view Crackle, YouTube and the various news organization's flash videos.
Then while I was trying an assortment of prescribed fixes I lost all flash capability.

Yesterday I found this thread [http://ubuntuforums.org/showthread.php?t=1392171&page=2](http://ubuntuforums.org/showthread.php?t=1392171&page=2) and went to [https://launchpad.net/~mozillateam/+archive/firefox-stable]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable") and followed the directions to add the PPA to my software sources.
When I updated and rebooted my system I saw that I was now running Firefox 3.6 and once again flash worked everywhere except Hulu but since I had installed Hulu Desktop I was happy.

Just to see what would happen, this morning I ran Update Manager and installed the recommended updates.
This, once again, killed all flash.

I looked in Synaptic to see which flash plugin I was using and saw this:
flashplugin-installer 10.0.42.34ubuntu0.9.10.1.
I marked it for re-installation and now I'm back to where I was when this all started - Hulu only works through Hulu Desktop and Crackle, YouTube and the various news orginization's flash videos still work normally.

Bill

---

### Post by deeptendu on 2010-01-30
I broke down and finally got Hulu. At first it was not working for me. It said it can't locate the flash plugin, and that I need to modify ~.huludesktop with the correct location of libflashplayer.so. Looking in the ReadMe showed that in order for Huludesktop to recongnize flash it needed to be in the folder /usr/lib/flashplugin-installer. So I created this folder and copied libflashplayer.so and it seems to be working fine (besides the fact that I find it's setup irritating). Hulu itself still isn't working though, but at least I'll be able to watch what's in my queue.

---

### Post by Mikeoak on 2010-01-31
Yesterday I reinstalled Mint 8 on a 64 bit system, Gateway computer.  I was disappointed that Hulu stopped working.  In the browser I got nothing but the annoying message about not being able to play the selection, etc. and the desktop version kept saying that it couldn't find flash.

So, I went into my home folder> View> Show Hidden Files>.mozilla and created a new folder which I renamed **plugins**   I then copied libflashplayer.so into the folder and now the Hulu Desktop Player works again.

---

### Post by Electric Bill on 2010-02-01
Interesting development.

My Foxconn A7DA-S machine has 3 SATA hard drives - 250GB Seagate (Windows 7 Pro), 150GB WD Raptor (Windows XP Pro) and 160GB Maxtor (Ubuntu 9.04 w/ext4).
Because of the flash issues previously mentioned I didn't upgrade to 9.10.

Last night I decided to download a fresh ISO of Karmic and after resizing the Linux partition to 40GB with PartedMagic 4.8 I also added an additional 40GB partition and converted the remaining unallocated space to an NTFS partition.
I burned a new live CD and installed 9.10 on the new 40GB partition.

Strangely enough Hulu works just fine in Firefox 3.6 as well as YouTube, Crackle, etc. :popcorn:

On a side note I couldn't get **awn** to work on this new installation although it works fine on my Biostar TF720 and my ASRock 939DualSATA2,  which *are* running 9.10.
Then I found this installation guide:
[http://wiki.awn-project.org/Installation:Ubuntu#PPA](http://wiki.awn-project.org/Installation:Ubuntu#PPA).
This is a new and improved version so I'll probably be upgrading my other machines also.

Bill

---

### Post by deeptendu on 2010-02-03
Now hulu desktop is saying that I'm not in the united states, despite the fact that I most assuredly am. Why would it start doing this now?

---

### Post by Electric Bill on 2010-02-03
deeptendu - you might give [Crackle]("http://crackle.com/") a try if you haven't already.
According to this from [CrackleFAQ]("http://crackle.com/outreach/faq/") it is US only.
> **[B] I am outside the United States.  Why can’t I view Crackle’s content?**[/B]

  Unfortunately, Crackle’s content is restricted to the US only (not including US territories). We apologize for the inconvenience. At least it would rule out URL problems.

Lol, I'm still trying to figure out why a fresh install is working for me.
Perhaps the 9.10 64 bit ISO file has been updated.

Bill

---

### Post by Electric Bill on 2010-02-03
Well I cloned the 9.10 partition from my Foxconn A7DA-S to a spare hard drive and tried it on my bedroom computer (ASRock 939Dual-SATA2) since both computers are using ATI video cards.
It also works correctly now and Hulu runs in Firefox so I'm convinced that the 64 bit version of Karmic has been updated.
I should mention that both machines are using Firefox 3.6 from [launchpad]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable").

If anyone is interested I used PartedMagic to copy and paste the 40GB Karmic partition from a 160GB Maxtor SATA hd on to an empty 80GB Seagate IDE hd.
I usually use Acronis to clone Ubuntu sector by sector since it's too easy to get the drives mixed up when using the dd command but it wouldn't work because the drives were different sizes and it wouldn't let me select just a single partition.
Since grub was on another partition with Jaunty I also had to install it into the Master Boot Record (MBR) of the new drive.

Bill

---

### Post by deeptendu on 2010-02-04
Actually, my Hulu Desktop started working again. I didn't change anything, so it worries me that this may be a recurring problem. I'll try crackle if it happens again, but for not I'm still trying to just get Hulu to work but it's still refusing my attempts.

---

### Post by Electric Bill on 2010-02-05
Yesterday I cloned the partition I mentioned above on to an 80GB drive on my Biostar HTPC along side the older installation of 9.10.
After reconfiguring grub and changing the computer name in the host files I got it working nicely.
Like the 2 other newer installs I did Hulu is working in Firefox.
It still doesn't work on the earlier installations unless I use the Desktop app so it looks to me like there's been some changes to the OS perhaps at the kernel level.

Unfortunately just after I got everything dialed in I ran Update Manager and saw that there was a  kernel update so I installed it.
This resulted in killing my video and USB devices.
I eventually got the video and k/board working but had to use a PS/2 mouse until I booted to an earlier kernel (2.6.31-14) with grub.
 I started a new thread [here]("http://ubuntuforums.org/showthread.php?p=8780061#post8780061").

Bill

---

### Post by fomerz on 2010-06-10
Finally got Hulu to work using the below method!!!  Thanks !

> **Dennis N said:**
> Got around to fixing the problem in post #18 for Ubuntu 8.04 32 bit. This got me a working ver. 10 flash player. It might help someone else with the same setup.

(method works for 32 bit Ubuntu 8.04 with Firefox 3.0.17)

1) Using Synaptic, mark 'flashplugin-nonfree' package for removal and apply. This also removes its directory.

2) Open 'System > Administration > Software Sources' and in the 'Third Party Software' tab mark the top box showing 'archive/canonical.com/ubuntu hardy partner' to include that source. This repo has the adobe flash player we need.

3) Reload package lists. Install 'adobe-flashplugin' package with Synaptic (if it is not offered as an update). 

This new adobe-flashplugin is installed into a directory (/usr/lib/adobe-flashplugin) where it is not detected by Firefox. So, take these additional steps using command line:

4) Re-create flashplugin-nonfree directory using command line:

```

cd /usr/lib
sudo mkdir flashplugin-nonfree

```

5) copy the adobe-flashplugin to this directory using command line:

```

cd /usr/lib/adobe-flashplugin
sudo cp libflashplayer.so /usr/lib/flashplugin-nonfree

```
Restart Firefox. Check for correct plugin (shockwave flash 10.0 r42) in:

Tools > AddOns > Plugins 

Hulu now detects flash player 10 and works.

---

