---
title: "Nvidia Powermizer defaults to adaptive mode? :("
date: 2010-05-09
forum: Multimedia Software
---

### Post by travlemon on 2010-05-09
Hey everybody,

So, I am running Ubuntu 10.04 on my laptop.  I just did a clean install (instead of upgrade) about a week ago or so.  I've been tackling a couple of issues and one of the last ones on my list is with my Nvidia card in the laptop.  

Nvidia appears to have kindly designed a power saving mode (Powermizer) for our video cards, by clocking down the GPU. However, mine is defaulting to Adaptive mode for Powermizer, and causes much annoyance.  While I'm able to switch it to Preferred Performance mode in the Nvidia X server settings, it resets back to Adaptive mode every time I restart the computer.  I've tried using the button to save the settings to Xorg.conf, but I think that only saves display configurations such as resolution.  

I also tried a couple tricks I found online where you can manually edit the xorg.conf file to disable Powermizer completely, but no luck on that either.

Does anybody know if it's possible to disable Powermizer in Ubuntu 10.04? or default it to Preferred Performance mode? While it's not a huge deal, just very annoying. 

Thanks in advance!

---

### Post by sojusnik on 2010-05-11
I'm struggling with the same issue. Hope to find a fix soon for this!

Did you had luck with this tutorial?

[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)

If yes, please write how you did it.

---

### Post by travlemon on 2010-05-11
> **sojusnik said:**
> I'm struggling with the same issue. Hope to find a fix soon for this!

Did you had luck with this tutorial?

[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)

If yes, please write how you did it.

Hi, thanks for responding!  That is the same tutorial I was working with.  There are two main problems with that tutorial, in our case.  

1.  It focuses on helping people do the exact opposite of we want to do.  Instead only lists the commands for xorg.conf to decrease performance, so we are totally blind on how to even use the file to our advantage.

2.  It looks like this tutorial was written for an older driver, and the commands we're trying to use in xorg.conf may not even work anymore. 

I've tried using "PowerMizerEnable=0x0", which I read somewhere that should disable it.  It just won't disable it for me, below is my xorg.conf Device section:

Section "Device"
    Identifier          "Device0"
    Driver              "nvidia"
    VendorName    "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
    Option              "RegistryDwords" "PowerMizerEnable=0x0"
EndSection

I'm going to keep playing around with this and see if any options effect Powermizer's behavior.  Let me know if you make any progress!

---

### Post by sojusnik on 2010-05-12
Some time ago, I've found the following solution, that is working for me:

> Create a file called /etc/modprobe.d/nvidia.conf with this in it:

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

I used this in karmic, but hoped that finally in lucid this annoying bug has vanished.

Does it work for you?

It seems that I have to use the above mentioned method again...

---

### Post by travlemon on 2010-05-12
> **sojusnik said:**
> Some time ago, I've found the following solution, that is working for me:



I used this in karmic, but hoped that finally in lucid this annoying bug has vanished.

Does it work for you?

It seems that I have to use the above mentioned method again...


Yes! I used your method and it now seems to be clocked at full performance!  I'm not sure where you found the fix, but thank you very much for the tip! It was driving me nuts, having to set it each time.  I'll be marking this as solved and printing a PDF copy to my database of fixes. 

Thanks again!

---

### Post by sojusnik on 2010-05-12
That's kinda wired, my fix doesn't seem to work for me under lucid.

Can you describe each step you did to manage powermizer to work at max. perf.?

---

### Post by travlemon on 2010-05-12
> **sojusnik said:**
> That's kinda wired, my fix doesn't seem to work for me under lucid.

Can you describe each step you did to manage powermizer to work at max. perf.?

Sure thing!

**Step 1:** I opened the terminal and I executed this command:

sudo gedit /etc/modprobe.d/nvidia.conf

Since the file does not exist yet, Gedit should open up anyway.  When we later click save, it saves as the filename and location that I typed in the above command.

**Step 2:** I copied and pasted the following line (provided by you) in Gedit: 

options nvidia NVreg_RegistryDwords="PerfLevelSrc=0x2222"

I made sure that there were no hidden spaces before or after the text, and that it was the very first line in Gedit.  Then, I simply clicked save.  I closed Gedit and then rebooted my laptop.

**Conclusion: **I'm going to try to attach screenshots to this post.  I'm new to the forum, so I might screw it up.  Anyway, if I do it correctly, you should see a print screen of what my nvidia.conf file looks like when opened in Gedit. Also, I'll post a screenshot of the Nvidia settings.  

The drop down menu in the Powermizer section still says "Adaptive", but the clock has been consistently on 500mhz (the highest).  Also, Performance Mode reports that it is in "Maximum performance" mode.  You will see what I mean in the screenshots.

[ATTACH]156678[/ATTACH]
[ATTACH]156679[/ATTACH]

---

### Post by sojusnik on 2010-05-13
That's so depressing, this method isn't working for me anymore...

Can you remove the [solved], so that maybe others can help too?

---

### Post by travlemon on 2010-05-13
> **sojusnik said:**
> That's so depressing, this method isn't working for me anymore...

Can you remove the [solved], so that maybe others can help too?

Sure! I marked it as unsolved again.  I'm sorry to hear that it's not working.  I don't know enough about Linux or Ubuntu to give you any suggestions.  The best suggestion I could try giving you is to delete nvidia.conf and then try reinstalling the driver, and make sure it's the latest driver from Nvidia.com?

Let me know if that works (though maybe you've tried it already)

---

### Post by 85stang on 2010-05-19
travelmon, what version of ubuntu are you running?  my nvidia settings does not have the drop down box like that.  I need to lock this power mizer thing becasue i think it is freezing X on me when it changes modes.  I tried the xorg.conf line and it didnt work for me in Lucid.  I tried the solution you did but then X would not start.

---

### Post by travlemon on 2010-05-19
> **85stang said:**
> travelmon, what version of ubuntu are you running?  my nvidia settings does not have the drop down box like that.  I need to lock this power mizer thing becasue i think it is freezing X on me when it changes modes.  I tried the xorg.conf line and it didnt work for me in Lucid.  I tried the solution you did but then X would not start.

Hi,

I'm running on Lucid (10.04) 32-bit.  Have you installed the latest drive? Dumb question, I know!  I'm still fairly new to Linux and I'm not much help yet.  When you create the nvidia.conf file, you're using all lowercase letters, right?  As I've realized, Linux handles folders and filenames with case sensitivity.  My nvidia.conf is all lower case. 

Sorry I'm not much help! I'm quite surprised that this fix has worked wonderfully for me and not for anyone else.

---

### Post by Perturbed Penguin on 2010-05-30
sojusnik, perhaps it might be a text formatting issue? If you copied the text into the file try instead actually typing it out to avoid any possible strange or oddly formatted text. This probably wont help but its worth a shot.

---

### Post by Perturbed Penguin on 2010-06-01
Ah actually that did not work for me either. I got it working now though using the method shown on both sites below:

(last post of the following archived thread)
_[http://ubuntuforums.org/archive/index.php/t-1311946.html](http://ubuntuforums.org/archive/index.php/t-1311946.html)_
_[http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html)_

Basically, at least in Ubuntu 10.04 (64bit, if it matters) you have to edit the xorg.conf file and not the file that was recommended for editing previously in this thread. The xorg.conf file, in case you are not familiar with it, can be found at '/etc/X11/xorg.conf'.

So one way to edit it is to open a terminal and type in:
**sudo gedit /etc/X11/xorg.conf**
and enter your password when prompted of course.

Then look for the 'Device' section of the document (you can use gedit's search function to find it if you need.) Under this section you will want to add the two lines:
**# added manually:**

**Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"**

...the '# added manually:' is unnecessary I just like to make a habit of making a comment anywhere I edit any file to tell myself that I have edited or added that part manually so if I ever come back to the file I have a better idea of what was or is going on.

The 'Option... ...AC=0x1' part is the single line of code you need to add to this section to inhibit the adaptive scaling for your card.

If you want to read a little further on the topic to better understand what the code does take a look at the links I provided, especially the second one; supposedly the line I provided will set it to max using AC and to adaptive when on battery but since I am only using this adjustment on my nvidia-driven desktop I have not tested to see if it actually works the way it should in regard to switching to adaptive handling when on battery. Hope this helps! :)

---

### Post by sojusnik on 2010-06-01
@ Perturbed Penguin

A huge THANK YOU to you!

It works like a charm!\\:D/

---

### Post by travlemon on 2010-06-01
> **sojusnik said:**
> @ Perturbed Penguin

A huge THANK YOU to you!

It works like a charm!\\:D/

Great! I'm glad you got this resolved!  It's strange, it seems I'm the only Ubuntu 10.04 user in existence that cannot get it to work through editing xorg.conf.  Either way, we all have it fixed now!  I'm going to mark this thread as solved!

---

### Post by Perturbed Penguin on 2010-06-07
Thats awesome, glad we all got this working. That is really strange that your install of 10.04 reacts differently travlemon but as you said at least you have it working. :)

---

### Post by travlemon on 2010-06-07
> **Perturbed Penguin said:**
> Thats awesome, glad we all got this working. That is really strange that your install of 10.04 reacts differently travlemon but as you said at least you have it working. :)

Yes sir! Wish I knew why it was like that, but it doesn't bother me.  And anyone who sees this will now have two different options to try. Especially the ones who were tearing their hair out, like I did, when it wouldn't work by editing xorg.conf!

---

### Post by petex on 2010-06-15
did not work for me plus it might have screewed my system (stoped booting with graphics crash though I'm not sure if it is related or just coincidence as i did not observe when exeactly the problem started appearing)

---

### Post by travlemon on 2010-06-15
> **petex said:**
> did not work for me plus it might have screewed my system (stoped booting with graphics crash though I'm not sure if it is related or just coincidence as i did not observe when exeactly the problem started appearing)


if your xorg.conf file became erroneous, your system might have automatically backed it up.  start up in recovery mode and navigate to the /etc/X11 folder. you might see a backup of the xorg.conf file. it may be named something like xorg.conf.backup. 

you would need to simply remove the corrupt xorg.conf file and and then make a copy of the backup and rename it to xorg.conf.  if you're able to boot up in low graphics mode, it might be easier to do this via GUI than command line.

---

### Post by Perturbed Penguin on 2010-06-17
This fix only applies to Nvidia cards you are using an Nvidia card correct? I am truly sorry you've had such troubles though!

---

### Post by petex on 2010-06-17
i actually solved it already by removing vga line from grub and addding nomodset to kernel line but i just wannted to let you know this might happend

---

### Post by travlemon on 2010-06-17
> **petex said:**
> i actually solved it already by removing vga line from grub and addding nomodset to kernel line but i just wannted to let you know this might happend

interesting! i'm still new to linux and don't know anything about GRUB really...other than the fact that it's a boot loader. i'm glad you got it worked out!

i'm happy i got this thread going, now there's a solid thread here to address the nvidia issue. it seemed that it wasn't talked about too much before i posted.

---

### Post by Perturbed Penguin on 2010-06-17
Glad you got things fixed! That is good to know that it may have issues on some setups. So what exactly did you do to fix your problem? Could you explain on this forum in case others fall victim to the same issue, maybe post some links too? Thanks!

---

### Post by calebrey on 2010-07-06
Please its not working for me if theres something wrong with my xorg.con file anything am doing wrong here is my set up


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 256.35  (buildmeister@builder97.nvidia.com)  Wed Jun 16 19:15:05 PDT 2010

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 256.35  (buildmeister@builder97.nvidia.com)  Wed Jun 16 19:14:45 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 220"
    Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-2"
    Option         "metamodes" "DFP-0: 1440x900_60 +1680+75, DFP-2: 1680x1050_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by kanin_te_sova on 2010-08-24
Hi, I have the same problem. I can't change the Powermizer settings. 

I think it does not work if you have TwinView enabled, as I also have. Tried diffrent methods to no avail.

Well maybe in the future it will be implemented if the card supports it I guess ('til that happens my GPU probably would have crashed and burned by long - hot hot hot).

Cheers!

---

### Post by repilce on 2010-09-03
Before you can see some of the settings in nvidia-settings you have to add to the device section of your xorg.conf :

```
"Coolbits" "1"
```Then you should be able to see the Peformance level window along with overclocking options.

I would also wonder if this works with saving the overclocking settings of "performance" as well, i wouldn't even mind leaving the adaptive enabled if it would keep the oc after reboot.

---

### Post by replicat on 2011-02-26
editing my .xorg file in gedit worked for me using geforce 9300m gs on 10.10

thanks alot!!!

ps...it still shows that adaptive is available but the card is at full clock 24/7

---

### Post by travlemon on 2011-02-27
> **replicat said:**
> editing my .xorg file in gedit worked for me using geforce 9300m gs on 10.10

thanks alot!!!

ps...it still shows that adaptive is available but the card is at full clock 24/7

Glad it worked! Yes, I am pretty sure the drop down menu, to choose between adaptive and max performance, still appears as if you are able to choose one of those options.  But no matter what you choose in that menu, after applying the fix, it should report that your gpu is fully clocked.

One other thing I'd like to note, this deficiency should no longer be an issue.   I noticed that on the latest drivers, at least for my cards, there is an "nvidia-settings Configuration" section on the left of the Nvidia X Server Settings window.   If you uncheck Powermizer checkbox on that screen, it looks like it disables it. 

The wording in the description makes it sound like it's just a monitor for Powermizer, but I haven't had performance issues since I unchecked it.  Make sure to click "Save current configuration".

Hope this helps

---

### Post by BicyclerBoy on 2011-02-27
AFAIK
If you have more than 1 display/monitor attached to 1 video card, then the nvidia driver will always set the adaptive clocking to maximum performance.
(This assumes the attached displays are active with a X server)

That's the way I read the nvidia docs..
It makes sense for the low powered GPUs.

---

### Post by travlemon on 2011-06-08
> **Perturbed Penguin said:**
> Ah actually that did not work for me either. I got it working now though using the method shown on both sites below:

(last post of the following archived thread)
_[http://ubuntuforums.org/archive/index.php/t-1311946.html](http://ubuntuforums.org/archive/index.php/t-1311946.html)_
_[http://linux.aldeby.org/nvidia-powermizer-powersaving.html](http://linux.aldeby.org/nvidia-powermizer-powersaving.html)_

Basically, at least in Ubuntu 10.04 (64bit, if it matters) you have to edit the xorg.conf file and not the file that was recommended for editing previously in this thread. The xorg.conf file, in case you are not familiar with it, can be found at '/etc/X11/xorg.conf'.

So one way to edit it is to open a terminal and type in:
**sudo gedit /etc/X11/xorg.conf**
and enter your password when prompted of course.

Then look for the 'Device' section of the document (you can use gedit's search function to find it if you need.) Under this section you will want to add the two lines:
**# added manually:**

**Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"**

...the '# added manually:' is unnecessary I just like to make a habit of making a comment anywhere I edit any file to tell myself that I have edited or added that part manually so if I ever come back to the file I have a better idea of what was or is going on.

The 'Option... ...AC=0x1' part is the single line of code you need to add to this section to inhibit the adaptive scaling for your card.

If you want to read a little further on the topic to better understand what the code does take a look at the links I provided, especially the second one; supposedly the line I provided will set it to max using AC and to adaptive when on battery but since I am only using this adjustment on my nvidia-driven desktop I have not tested to see if it actually works the way it should in regard to switching to adaptive handling when on battery. Hope this helps! :)

Thank you for this fix!  This worked for me, but I had some issues.  As part of my efforts to help make this thread as informative as possible for other users, I'll add a quick note about it.

I copied and pasted the line you provied into my xorg.conf as the last line in the Device section before the "EndSection" line.  I saved the file and restarted X only to find that X would not start.

It turns out that apparently xorg.conf and/or Nvidia is extremely picky in how the options lines need to be entered.  I didn't have enough spaces between the word Option and the "RegistryDwords".  The line must be setup exactly how the other lines are set up in xorg.conf.  I'm going to paste a before and after here, since that will make much more sense than how I'm trying to explain it. 

This is the Before, how I pasted the line and it did not work.  Notice there is only one space between Option and "RegistryDwords", and that "RegistryDwords" does not line up with the other quoted options:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
    Option "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection
```Here is the after, the one that works.  All of the text with quotes line up:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9600M GT"
    Option         "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x3322; PowerMizerDefaultAC=0x1"
EndSection
```Sadly, that actually constitutes the difference between enjoying your Linux distro and frustratingly staring at a computer that won't fully boot up.  For those of you who may have to remove a bad line in xorg.conf to get back into the system, you can edit the file via command line by doing this:

Press CTRL + ALT + F1 (or F2, F3, F4).  There should be a login prompt, simply login with your user credentials.  Once in, run the following command and press enter:

```
sudo nano /etc/X11/xorg.conf
```You'll see the contents of your xorg.conf come onto the screen.  Simply move the cursor to the line you need to remove, and modify the file accordingly.  Press CTRL+X to exit, and press Y to save the changes.  Then press Enter.  That should do it, then try restarting X!

---

### Post by Padraig Notlad on 2012-09-29
This worked for me just as described.

---

### Post by wildmanne39 on 2013-04-03
Thread closed. Please do not post in old threads.

---

