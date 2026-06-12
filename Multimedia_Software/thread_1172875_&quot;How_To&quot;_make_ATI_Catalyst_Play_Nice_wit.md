---
title: "&quot;How To&quot; make ATI Catalyst Play Nice with  Compiz - Xserver"
date: 2009-05-29
forum: Multimedia Software
---

### Post by HunterThomson on 2009-05-29
[SIZE="3"][COLOR="Blue"]How To make ATI Catalyst work with Compiz - Xorg Server[/COLOR][/SIZE]
by, HunterThomson - HowTo's that WORK !

_**This will install a patched Xserver so compiz will work with out problem like lag on window resize or window move.**_

_>Ok so you need to add a new source to your repo's_

_>Fist open the "Software Sources" GUI_

```
System/Administration/Software Sources
```

_>Then select the tab "Third-Party Software_

_>Then Add... these two APT lines by clicking on the "Add..." button and cut/past them in. Add them "ONE at a Time"_

```
deb http://ppa.launchpad.net/bryceharrington/violet/ubuntu lucid main
deb-src http://ppa.launchpad.net/bryceharrington/violet/ubuntu lucid main
```

_>OK good stuff, Now you just need to enter it's GPG Key_

_>Fist follow this link_

[http://keyserver.ubuntu.com:11371/pks/lookup?search=0x510DE9AC846B40EB94EDB3AEFBB49579B75FECB0&op=index](http://keyserver.ubuntu.com:11371/pks/lookup?search=0x510DE9AC846B40EB94EDB3AEFBB49579B75FECB0&op=index)

_>Click the "B75FECB0" or whatever that # is at the time._

_>Then it should take you to a page with the GPG/PGP key and looks like this_

```
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXU/AgEEAKoekOpV/jh1IjQHqchz9y5L/TJgzB4XCZMfu3FJO4N48e4q/tKH6fWnspKt
04SlVtbOliEQdn95KB2UfsPIKFncHl/sAYvWBwaq8ZOkcRmTLgyJdn+T+5scDc47gnPEWF+8
0KT3FIbhfppyH1yMuH/8a/bfZm2lDIa8SqIW5lGvABEBAAG0IkxhdW5jaHBhZCBQUEEgZm9y
IEJyeWNlIEhhcnJpbmd0b26ItgQTAQIAIAUCSXU/AgIbAwYLCQgHAwIEFQIIAwQWAgMBAh4B
AheAAAoJEPu0lXm3X+ywKl8D/04Zch7S8BocT9ARlPEbZAMAnq9IUSG5e0edYBY+MnD6Mt6f
kuUjWqC+IY5PMhx9Pw/QMERWthyDZCGIjsON4lzD2P992GMPTGGuRRcC6v+gInfQn5/Vr4E1
xtnQTHykJf/c9FB2YzQlGt4GmUDLgwfmeEwZ8N2fklfHnioJDmes
=uWJH
-----END PGP PUBLIC KEY BLOCK-----

```

_>Now open up gedit or any text editor you like and Cut+Past in the whole key. Then save the file with any name, like NewRepoKey_1_

_>Back in the "Software Sources" GUI click on the "Authentication" Tab_

_>Then click on the "Import Key File..." button and navigate to the key you saved and click OK._

_>Now click "close"_

_>Now take a brake and have a e-smoke._

_>Now you can upgrade you system through any of the multitudes of GUI's Ubuntu preinstalls_

Or just
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by robgolding63 on 2009-06-06
Nice HowTo, thanks for this.

I found that shameless copy on someone's blog post - glad you put a comment with a link here though!

Rob

---

### Post by HunterThomson on 2009-06-06
> **robgolding63 said:**
> Nice HowTo, thanks for this.

I found that shameless copy on someone's blog post - glad you put a comment with a link here though!

Rob

Glad to hear it.

Ya, I meen I torrent a lot of stuff and I am big on Opensource... But it is just like I am not makeing money and now he is... And it's like he didn't even give me credit :( And it is a Google blog so now his blog is the first thing that pops up under google when before this thread was and now my thread is not even on the first page of google.

And this is not going to work forever. So it is better to just read this which I will change when things change.

---

### Post by josepcoves on 2009-06-08
Hi,

I solved the problem installing this patched xserver and I got no lag on maximizing or minimizing. 

The problem now is in playing videos. I cannot play videos at fullscreen (I get black screen) and if I try to increase video size I lose image and player (VLC) hungs with CPU 100%.

Anyone has a fix for this?

---

### Post by HunterThomson on 2009-06-08
> **josepcoves said:**
> Hi,

I solved the problem installing this patched xserver and I got no lag on maximizing or minimizing. 

The problem now is in playing videos. I cannot play videos at fullscreen (I get black screen) and if I try to increase video size I lose image and player (VLC) hungs with CPU 100%.

Anyone has a fix for this?

Hum, I never had that problem. Dose that only happen when compiz is running or is is all the time?

Also, can you post your xorg.conf file. You can find it by doing this.

```
sudo gedit /etc/X11/xorg.conf
```

Also, what card do you have?

---

### Post by nilbus on 2009-06-16
I love you!  Life is so much better with this fix.

I had lag with all kinds of operations on my ATI video laptop. Now it's all gone. :-)  Thanks!

---

### Post by HunterThomson on 2009-06-16
> **nilbus said:**
> I love you!  Life is so much better with this fix.

I had lag with all kinds of operations on my ATI video laptop. Now it's all gone. :-)  Thanks!

No problem.
Really I read this on the bug listing on launchpad but it took me weeks to find it so I figured it would help people out to write this step by step and put it on the more high profile ubuntuforums. I know I always look here first and launchpad last. Also, workarounds like this tend to get lost in the shuffle in launchpad.

---

### Post by Th3_uN1Qu3 on 2009-06-19
Thanks. Thanks. Thanks a million. I have just finished installing Ubuntu 9.04 on my brand new extra shiny HP DV5 lappy, and after getting sound to output through the speakers i really wasn't up for another challenge. Your post made it simple to stop Compiz from lagging and there is no graphics corruption at all.

I will get back to you if i experience issues with watching video like other users have had.

Specs: Athlon64 X2 QL-62 2.0GHz, 2GB RAM, ATi HD3450 512MB, IDT HD Audio reported as STAC92xx, 160GB HDD. Great machine, though a bit warm, and in need of an extra battery as it barely runs for 1.5hrs.

Edit: The ATi drivers do play nice with Compiz, but apparently they're the only thing that does. With Compiz enabled all games exhibit abnormal behaviour - flickering screens in OpenGL based games and menus scrolling on their own in SuperTux. I'll just keep the eye candy turned off for now. I don't know whether it has to do with the patch or Compiz itself, as i have not uninstalled the patch, just disabled Compiz, and all games i've tried run just fine like this.

---

### Post by mosimea on 2009-06-19
Thank you!

Catalyst 9.6 driver
ATI Mobility Radeon HD 3670

The lag when resizing or restoring a minimized window is  gone!

---

### Post by HunterThomson on 2009-06-19
> **Th3_uN1Qu3 said:**
> Thanks. Thanks. Thanks a million. I have just finished installing Ubuntu 9.04 on my brand new extra shiny HP DV5 lappy, and after getting sound to output through the speakers i really wasn't up for another challenge. Your post made it simple to stop Compiz from lagging and there is no graphics corruption at all.

I will get back to you if i experience issues with watching video like other users have had.

Specs: Athlon64 X2 QL-62 2.0GHz, 2GB RAM, ATi HD3450 512MB, IDT HD Audio reported as STAC92xx, 160GB HDD. Great machine, though a bit warm, and in need of an extra battery as it barely runs for 1.5hrs.

Edit: The ATi drivers do play nice with Compiz, but apparently they're the only thing that does. With Compiz enabled all games exhibit abnormal behaviour - flickering screens in OpenGL based games and menus scrolling on their own in SuperTux. I'll just keep the eye candy turned off for now. I don't know whether it has to do with the patch or Compiz itself, as i have not uninstalled the patch, just disabled Compiz, and all games i've tried run just fine like this.

I had that same problem in Ubuntu. I am using Archlinux now. I too thought it had something to do with the Catalyst but then I had no problem in Archlinux. DanaG posted this in responce to my talking about this problem.

DanaG
> Oh yeah, that "acts like joydown is pressed": try blacklisting lis3lv02d -- that's the driver that presents the accelerometer as a joystick. By default, the calibration has the X and Y axes swapped; I had to put this in my /etc/rc.local:
jscal -u 3,1,0,2,0 /dev/input/js0 2>/dev/null || true

I don't know if your laptop also has an accelerometer but that may be the problem.

Therad:
[http://ubuntuforums.org/showthread.php?t=1166667](http://ubuntuforums.org/showthread.php?t=1166667)

---

### Post by houseonfire on 2009-07-06
I cannot thank you enough for this guide.
My ATI 4850 didn't seem to be able to get out of its own way while maximizing VLC or any other window.
Now it runs just fine.

Thanks

---

### Post by HunterThomson on 2009-07-07
> **houseonfire said:**
> I cannot thank you enough for this guide.
My ATI 4850 didn't seem to be able to get out of its own way while maximizing VLC or any other window.
Now it runs just fine.

Thanks

Glad to here it.

I just can't wait until the Open Source driver gets 3D.

---

### Post by Philip Farrugia on 2009-07-26
Found this thread while looking for a solution to ubuntu crashing when watching tv with the ati drivers installed. All's well with default ubuntu driver.

My card is HD4670 radeon.

Anyone know of a solution?

Waiting for the open source drivers to include 3D or ATI to play nice with the X video driver.

---

### Post by HunterThomson on 2009-07-28
> **Philip Farrugia said:**
> Found this thread while looking for a solution to ubuntu crashing when watching tv with the ati drivers installed. All's well with default ubuntu driver.

My card is HD4670 radeon.

Anyone know of a solution?

Waiting for the open source drivers to include 3D or ATI to play nice with the X video driver.

Well make it crash. Then you can see any errors in the log file and maybe you can fix them. Like on my card I have to turn ACPI off (sudo aticonfig --acpi-services=off) otherwise the Kernel will panic when Xserver starts.

This command will show you all the Errors (all error lines in the log file start with (EE) all the warnings start with (WW).
```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by jacks2k on 2009-07-30
Ey!

At first, thanks a lot for this small guide. It's very helpful!!

Unfortunately, as soon I updated my xorg to this modified version, ubuntu has not boot again... i got black screen and i don't know what to do after that to run X...

Any idea?

PS.- I'm a noob so ... slow, plz.
PS2.- My Catalyst version is 9.7.
Thans a lot in advance, and, of course, sorry for my English.

---

### Post by jacks2k on 2009-07-30
Solved. I have uninstall the latest version of Catalyst, and then I used jockey to put the private drivers of ATI again... and *violá*, it works now.

But... i have still one problem. Sometimes, watching some video, when i switch to full screen, then the screen goes to black, and the system hangs... but i think that it also happened with previous versions of Catalyst so ... anyone knows something about it?

---

### Post by Philip Farrugia on 2009-07-30
Thanks for your reply.  The last atempt crashed so bad I had to reinstall the os.  Given up for now due to lack of time to keep faffing around with crashes and re-installing.

---

### Post by HunterThomson on 2009-07-31
> **Philip Farrugia said:**
> Thanks for your reply.  The last atempt crashed so bad I had to reinstall the os.  Given up for now due to lack of time to keep faffing around with crashes and re-installing.

Owe, if it is all messed up and you want to uninstall this pached Xserver. All you have to do is.

>Reboot and when the Grub is counting down form 3sec's hit enter.

>Then select the Recovery mode.

>When you get to the GUI arrow down and select "Root Shell"

((Ok now I am not using Ubuntu I am using Archlinux so I don't know where exactly the files are))

Ok now your at the terminal and you can do anything :) You need to find the sources list. You know that one that you added that repo in that SoftwareSources application. The file should be in /etc/aptitude or just in /etc It should be called like sorces.lst or like aptitude.conf or sources.conf Somewhere then you just edit that file to take out the repo address you added.

After you got the sources address's you added out of the list and then. Reinstall xorg.

???I am using archlinux so I don't know the exact name of the package in Ubuntu???
```
apt-get install xorg
```

--------------------------------------------

I will set up a VMubuntu tomorrow and write out a section on how to uninstall this if it messes everything up.

---

### Post by HunterThomson on 2009-07-31
> **jacks2k said:**
> Solved. I have uninstall the latest version of Catalyst, and then I used jockey to put the private drivers of ATI again... and *violá*, it works now.

But... i have still one problem. Sometimes, watching some video, when i switch to full screen, then the screen goes to black, and the system hangs... but i think that it also happened with previous versions of Catalyst so ... anyone knows something about it?

You said you fixed it. Hum, so you just had to reinstall the Catalyst ?

Well if you computer works better with the normal Xserver then you that. The Catalyst dose suck so it could just be that.

---

### Post by Philip Farrugia on 2009-10-05
Just want to report that my problem has solved itself.

Installed Karmic 64bit beta. Added the ATI driver via the Hardware Driver menu.

Also had to install linux-firmware non-free and libxine-all-plugins to get kaffeine to work! Kaffeine version 1.0 was installed via synaptic.

Hooray! TV and desktop effects enabled!

Keeping my fingers crossed this continues to work!

---

### Post by houseonfire on 2009-10-10
Hey, I installed 9.10 on my computer and I have an ATI 4850. Can I just change the names on your instructions and use it just the same?

---

### Post by xaber1488 on 2009-10-19
Same for me! I just installed karmic koala beta, but I see the repos are for jaunty... Is it the same if use them?

---

### Post by xaber1488 on 2009-10-19
> **Philip Farrugia said:**
> Just want to report that my problem has solved itself.

Installed Karmic 64bit beta. Added the ATI driver via the Hardware Driver menu.

Also had to install linux-firmware non-free and libxine-all-plugins to get kaffeine to work! Kaffeine version 1.0 was installed via synaptic.

Hooray! TV and desktop effects enabled!

Keeping my fingers crossed this continues to work!

You didn't do anything more to make the drivers work well? Neither using this thread's guide? You simply installed the drivers from the menu drivers and everything was well?

---

### Post by Philip Farrugia on 2009-11-04
Just checking old posts and saw your reply.

Yes no more problems with Karmic and Kaffeine with dvb-t and ati4670ultimate and effects.  Some shearing of video occasionally. The wobbley tv window is weird!  Guess the x-org guys have been busy getting newer cards to play nice.  Only problem was I tried to install latest catalyst from ati and that screwed things up. Must remember to stick to the repositories for stability.

---

### Post by ozkhalsa on 2009-11-06
I get these errors on my V7700 ATI FireGL Pity cannoteven run 3D on linux. need help otherwise have to go Back  to M$

```
$ cat /var/log/Xorg.0.log | grep EE

Current Operating System: Linux Ubuntucosmos 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
```

---

### Post by HunterThomson on 2010-01-06
> **ozkhalsa said:**
> I get these errors on my V7700 ATI FireGL Pity cannoteven run 3D on linux. need help otherwise have to go Back  to M$

```
$ cat /var/log/Xorg.0.log | grep EE

Current Operating System: Linux Ubuntucosmos 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 13:22:24 UTC 2009 x86_64
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.
(EE) fglrx(0): PPLIB: PPLIB is not initialized!.
```


Sorry, I haven't checked the thread in a long time.

I have a FireGL v5700 and it is really a HD3650. I think your FireGL is really a HD3870.

What steps have you taken to install the Catalyst?

-----------
Dam last activity November 5th 2009
Darn ATI driving away would-be Linux users :mad:

---

### Post by MarcoPau on 2010-03-13
I don't understand if we can try the same thing with karmic by changing the ppa repos. I'm stuck with kwin as kde4-window-decorator crashes when launching compiz.

---

### Post by HunterThomson on 2010-05-19
Ya, AMD/ATI Still have not fixed this. Heck they have even come out with new graphics cards that have this problem....

In any case. Ya, you need to install a patched Xserver with "No-Backfill" if your having problems. If the ppa I link to is no longer good (I bet it is not) and just changing the name to the current vertion of Ubuntu will not work. Then you will have to find an uptodate one. If you find it please post here and I will update the HowTo.

As of now I sold my elitebook with the HD 3650 and am using nvidia now.

One thing I will say, If you don't play games all the time I'd use the Open driver. That is what I did when I had my elitebook with a HD 3650. The the Open driver is not as good with 3D but is rocks the house in every other aspect. You can still play "Quake Live" and "Tribal Truble 2" and even Open Arena is playable. I think also Super Tux Kart.

The xf86-video-ati

Owe also the Open Source driver has limited power saving features depending on what GPU you have. So, it "could" get hotter.

---

### Post by alphacrucis2 on 2010-05-19
> **HunterThomson said:**
> Ya, AMD/ATI Still have not fixed this. Heck they have even come out with new graphics cards that have this problem....

In any case. Ya, you need to install a patched Xserver with "No-Backfill" if your having problems. If the ppa I link to is no longer good (I bet it is not) and just changing the name to the current vertion of Ubuntu will not work. Then you will have to find an uptodate one. If you find it please post here and I will update the HowTo.

As of now I sold my elitebook with the HD 3650 and am using nvidia now.

One thing I will say, If you don't play games all the time I'd use the Open driver. That is what I did when I had my elitebook with a HD 3650. The the Open driver is not as good with 3D but is rocks the house in every other aspect. You can still play "Quake Live" and "Tribal Truble 2" and even Open Arena is playable. I think also Super Tux Kart.

The xf86-video-ati

Owe also the Open Source driver has limited power saving features depending on what GPU you have. So, it "could" get hotter.

I prefer the backclear patch rather than no backfill.

[https://launchpad.net/~bryceharrington/+archive/violet]("https://launchpad.net/~bryceharrington/+archive/violet")

---

### Post by HunterThomson on 2010-05-21
Ya, your right. I here the backclear is WAY better, because it doesn't splash that garbage on the screen for the split second when a window is opening.

I'll up date this HowTo to use that one.

EDIT: Done. Updated to use that one. Thanks

---

### Post by jacks2k on 2010-06-01
> **HunterThomson said:**
> Ya, your right. I here the backclear is WAY better, because it doesn't splash that garbage on the screen for the split second when a window is opening.

I'll up date this HowTo to use that one.

EDIT: Done. Updated to use that one. Thanks

How can I replace no-backfill with backclear??

Thanks a lot in advance :)

---

