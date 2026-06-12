---
title: "Do not upgrade to Natty if you use proprietary graphics drivers!!!"
date: 2011-04-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Dlambert on 2011-04-04
Natty no longer supports Nvidia drivers and therefor installs the open source version, and in my case Ubuntu wont even boot now. I had to run it in failsafe x just to try and install Nvidia's drivers again, but i would need to purge the open source one. This is too much work only to not be able to use the proprietary drivers of my choice.

I'm afraid this is the end of Ubuntu on my gaming rig, i might try Debian squeeze or Linux Mint Debian Edition

---

### Post by gyussz on 2011-04-04
My 9800 GT works just fine with proprietary driver on the latest Natty release.

---

### Post by the_jlx on 2011-04-04
same with my nvidida 450gts works just fine
did you install both open soure and proprietary?
if so then no wonder

---

### Post by sandy8925 on 2011-04-04
What card do you have in the first place?

---

### Post by Dlambert on 2011-04-04
Gts 450, Natty uninstalled proprietary and installed open source. And i couldn't re-install.

---

### Post by Quackers on 2011-04-04
Is that a new graphics card? My 8600M GT works fine in 3 Natty installs.

---

### Post by Dlambert on 2011-04-04
2010.

---

### Post by Harry33 on 2011-04-04
> **Dlambert said:**
> Natty no longer supports Nvidia drivers and therefor installs the open source version, and in my case Ubuntu wont even boot now. I had to run it in failsafe x just to try and install Nvidia's drivers again, but i would need to purge the open source one. This is too much work only to not be able to use the proprietary drivers of my choice.
...


Natty does support nvidia proprietary drivers well and
with the latest stable xserver (1.10).
You just have to use the latest beta nvidia-current, which is in the official repos.
NVidia 450GTS is supported too.

---

### Post by rondackcpu on 2011-04-04
Great trouble here with Natty and an older GeForce 5200 card.  System won't boot under any thing I've tried.  Complaints go by on the screen very quickly, but I think it is saying something about "can't find GeForce chip".  Maverick works just fine.

Any ideas would be greatly appreciated.

CRS

---

### Post by terry_gardener on 2011-04-04
my gtx 460 works with the nvidia driver. 

i have recently did a reinstall of beta before i installed the nvidia driver i installed the experimental one in additional drivers app and then rebooted but unity didn't work so i uninstalled the experimental opensource one rebooted and installed the nvidia one and rebooted. 

i did all this from the additional drivers application built into ubuntu and works perfectly well and easy to do.

---

### Post by stanca on 2011-04-04
My Geforce 8400 GS works as well.:)

---

### Post by cariboo on 2011-04-04
That last nVidia driver I see for that graphics card was released in October of 2010, unless there is a newer one, that driver won't work with the latest version of xorg-xserver.

Can you boot using failsafeX from the recovery menu?

---

### Post by VanR on 2011-04-04
8400GS working fine for me in 11.04

---

### Post by Starks on 2011-04-04
> **rondackcpu said:**
> Great trouble here with Natty and an older GeForce 5200 card.  System won't boot under any thing I've tried.  Complaints go by on the screen very quickly, but I think it is saying something about "can't find GeForce chip".  Maverick works just fine.

Any ideas would be greatly appreciated.

CRS

driver 173 and driver 96 aren't supported yet. your card uses 173.

---

### Post by thiebaude on 2011-04-04
8400 gs propietary drivers work , np at all.Just can't wait til they fix the high ram usage.

---

### Post by cariboo on 2011-04-04
I have a 6600GT, 8400GS, 9400GT and a GT210, all work really well with the proprietory drivers.

---

### Post by bluenova on 2011-04-04
No problemo here with nVidia proprietary drivers, except for the large memory footprint but that is being worked on.

---

### Post by CaptainMark on 2011-04-04
Mine works better than ever no probs

---

### Post by Dlambert on 2011-04-05
> **rondackcpu said:**
> Great trouble here with Natty and an older GeForce 5200 card.  System won't boot under any thing I've tried.  Complaints go by on the screen very quickly, but I think it is saying something about "can't find GeForce chip".  Maverick works just fine.

Any ideas would be greatly appreciated.

CRS
Same prob. wont boot

---

### Post by Dlambert on 2011-04-05
I download drivers straight from Nvidia.

---

### Post by Vadi on 2011-04-05
So how would switching to another distro of the same, new X server version that's breaking the driver exactly help?

---

### Post by alexcckll on 2011-04-05
This is concerning - will this be fixed in time for the next LTS?  Or will I have to throw away my Ideapad S12 (with NVidia ION) and buy a new Linux laptpp when Lucid goes end of life?

---

### Post by cariboo on 2011-04-05
@Dlambert, it would help if you told what model graphics card you have. Why would you download the driver from nVidia, when there is one available in the repositories, if you have a supported device?

---

### Post by Dlambert on 2011-04-05
> **cariboo907 said:**
> @Dlambert, it would help if you told what model graphics card you have. Why would you download the driver from nVidia, when there is one available in the repositories, if you have a supported device?

Asus Engts 450 Top. Nvidia Gts 450.

Because id rather get them straight from the developers. No problems with this card until Natty. Downloading BETA ISO on my (now) windows machine to try again.

---

### Post by Dlambert on 2011-04-05
[http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html]("http://www.nvidia.com/object/linux-display-amd64-260.19.44-driver.html")

---

### Post by terry_gardener on 2011-04-05
> **Dlambert said:**
> Asus Engts 450 Top. Nvidia Gts 450.

Because id rather get them straight from the developers. No problems with this card until Natty. Downloading BETA ISO on my (now) windows machine to try again.

out of curiosity have you tried the one from the repos using the normal additional drivers app, to see if it works.

the one in the repos is version. 270.30

---

### Post by cariboo on 2011-04-05
If you aren't using the drivers from the repositories, there are no guarantees that the driver you are using will work with Natty, plus you have to reinstall it every time there is a new kernel, and we've had enough kernel updates during this cycle to make that get old really fast.

---

### Post by Dlambert on 2011-04-07
I'm fine with reinstalling it. Im using Linux Mint now, maybe i will go back. I really don't want unity. (and yes i know gnome is still featured in 11.04, but it wont be in 11.10)

---

### Post by ELD on 2011-04-07
Are threads like these jokes? More and more seem to crop up with each dev release.
 
@Dlambert you realise this isn't a stable release yet....right? Why would you expect everything to work like that? Try any other dev release from any other distro and you will find the same problems - it's the new xorg not Ubuntu.
 
If your on a "gaming" machine as you say, then stick to stable releases.

---

### Post by macstevejb on 2011-04-07
I think you'll find that yes, Ubuntu 11.04/Unity will work fine with the latest nvidia drivers _BUT_ your system Ram memory usage will increase by anything up to 100%.

Being told that a fix is in hand, just hope it will be soon with final release only a few weeks away now.

regards

---

### Post by manzdagratiano on 2011-04-07
> **Dlambert said:**
> I'm fine with reinstalling it. Im using Linux Mint now, maybe i will go back. I really don't want unity. (and yes i know gnome is still featured in 11.04, but it wont be in 11.10)

Is your issue with the graphics card or Unity? I have had issues with Nvidia before, and I fixed them by following this guide:
[HTML]
http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/[/HTML]

If you rather prefer to install the drivers from the vendors, who do** not **make them for a particular flavor of GNU/Linux, you are asking for trouble! I have to install my wifi drivers from the vendors for Slackware/Gentoo, and I hate having to recompile them every time there is a kernel upgrade. The version in the repos are the ones tested to work with most supported hardware, which clearly you are not going with, and if you wish to warn people about not upgrading because they have proprietary hardware, you should be making clear your context, and also not making ludicrous statements like Natty not supporting proprietary nvidia drivers. Experienced users will take your words with a pinch of salt, but new ones trying to test a new upgrade for the first time will be forewarned once and for all without knowing what the context is.

---

### Post by gyussz on 2011-04-07
> **Dlambert said:**
> I'm fine with reinstalling it. Im using Linux Mint now, maybe i will go back. I really don't want unity. (and yes i know gnome is still featured in 11.04, but it wont be in 11.10)

Gnome (gtk3) will be featured in 11.10, but not the classic (gtk2) Gnome. The classic will be officially phased out anyway by Gnome 3. (By officially I mean the Gnome team will focus on Gnome 3 instead of the old one)

---

### Post by andrek on 2011-04-07
Please change the topic title as it might be misleading as hell.

---

### Post by manzdagratiano on 2011-04-07
> **andrek said:**
> please change the topic title as it might be misleading as hell.

+10

---

### Post by Dlambert on 2011-04-07
> **ELD said:**
> Are threads like these jokes? More and more seem to crop up with each dev release.
 
@Dlambert you realise this isn't a stable release yet....right? Why would you expect everything to work like that? Try any other dev release from any other distro and you will find the same problems - it's the new xorg not Ubuntu.
 
If your on a "gaming" machine as you say, then stick to stable releases.

Its not x-org giving me problems, it was nouveu. I wanted to see if unity would run, and so far no joy. I will retry natty but for now i am using Linux mint. And yes i have a gaming Pc. I built it myself.

---

### Post by Dlambert on 2011-04-07
> **andrek said:**
> Please change the topic title as it might be misleading as hell.

And how would i do that?

---

### Post by Dlambert on 2011-04-07
Close this thread please. Or change the title

---

### Post by cariboo on 2011-04-07
Thread closed by request.

---

