---
title: "Ati 8.5 ???"
date: 2008-05-21
forum: Multimedia Software
---

### Post by Ski-lleR on 2008-05-21
Hi there

i tried to download ati 8.4 official drivers, but for test, i tried to replace the url by 8-5, and it works!

The file is 3 Mb bigger than 8.4, so...beta, non finished drivers ?

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-5-x86.x86_64.run)

---

### Post by toyish on 2008-05-21
Nice idea to change version in url :)

I downloaded and tried to install this version, I got a little ATI logo on the right corner on the screen and a big cross sign over it say NO 3D.
When I logged in I got white screen and no desktop, probably because I have compiz enabled and the driver has no 3D support???

---

### Post by Ski-lleR on 2008-05-21
8.5 are officialy in download on ati website :guitar:

---

### Post by eriksallstrom on 2008-05-21
I got the "No 3D" and white screen to, but a reboot solved that problem (instead of just restarting X). They forgot to remove the testing logo in the right bottom corner of the screen, but there is a fix here:

[http://www.phoronix.com/forums/showpost.php?p=32696&postcount=13]("http://www.phoronix.com/forums/showpost.php?p=32696&postcount=13")

The driver is supposed to [improve 2D performance]("http://www.phoronix.com/scan.php?page=article&item=catalyst_85_linux&num=1"), but I see no difference. The only difference I found is that I can't use XVideo for video output anymore...

---

### Post by peakshysteria on 2008-05-21
> **Ski-lleR said:**
> 8.5 are officialy in download on ati website :guitar:

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

Can someone please tell me how this one is running? Have no luck with earlier versions (and no luck with ENVY or the Hardware drivers manager).

The kids are climbing the walls....we need tv out fast and we need it now.....could this be the right time to give it a millionth chance?

:confused:

---

### Post by Melcar on 2008-05-21
It runs very well.  As pointed out earlier, they screwed up an released an unsigned copy; I was told that a signed copy will be available shortly.  As for the driver itself, it has a few improvements and additions, like more 3D options in CCC (custom AA filters, mipmap detail level, Catalyst AI), but some problems still are there (for me at least) like video tearing with Xv/OpenGL and horribly slow scrolling in FF when Compiz is running.

---

### Post by excogitation on 2008-05-21
How long does it usually take until you can get an updated driver like this through the repositories?

---

### Post by Eestlane on 2008-05-21
Up to one week? Not sure, though.

---

### Post by eldragon on 2008-05-21
> **Eestlane said:**
> Up to one week? Not sure, though.

i didnt know they would make it to the repos.

im used to to this the windows way. (download, unpack, install, reboot)

never hurt me.

gonna test them when i get to my ati-box.

---

### Post by Eestlane on 2008-05-21
> **eldragon said:**
> i didnt know they would make it to the repos.

im used to to this the windows way. (download, unpack, install, reboot)

never hurt me.

gonna test them when i get to my ati-box.
Ubuntu's Restricted Drivers Manager is much easier to use and more foolproof.

---

### Post by Melcar on 2008-05-21
Well, seeing as the driver for Gutsy never really got updated, I don't have hopes for the one for Hardy to be either.
The signed copy should be out in ATI's website now, so no need for the hotfix to remove the watermark.

---

### Post by eldragon on 2008-05-21
> **Eestlane said:**
> Ubuntu's Restricted Drivers Manager is much easier to use and more foolproof.

repos usually get the latest driver available when reaching the code freeze deadline previous to a release.

being able to replace manually the ati drivers always gets you the latest and greatest the day they are out. considering the nature of a binary blob, it either works or not, and having a repo or not wont change a thing (dont quote me on this one) so it doesnt hurt to test it and revert if it fails.

if you wish to install the latest drivers, just download, create the debs.
uninstall the drivers from the repos. and install the drivers from the newly generated packages, then you have to reboot. (yes, ala windows reboot, restarting xorg doesnt work).

this procedure worked for me since the release of the drivers that support aiglx.

---

### Post by excogitation on 2008-05-22
Thanks for clearing that up, eldragon.

---

### Post by Jade767 on 2008-05-22
Did anyone notice a difference in 3D fps through the update? I'm currently using EnvyNG to install my ATi driver, but I might as well udpate them myself now since there hasn't been an update released. I'd only do it if it would improve the overall fps in WoW though, since everything runs smooth currently on my HD 2600 mobility. Although the fps in WoW is much lower then when I ran it on the same machine with Windows XP.

---

### Post by eldragon on 2008-05-22
i didnt notice any difference from 8.4 to 8.5 if thats what you mean. the ati control panel has more features...

thats about all i found ...

---

### Post by funnypanks on 2008-05-22
> **eldragon said:**
> i didnt notice any difference from 8.4 to 8.5 if thats what you mean. the ati control panel has more features...

thats about all i found ...

+1
except the watermark... so i have the pleasure of being annoyed now.

---

### Post by Eestlane on 2008-05-22
> **eldragon said:**
> repos usually get the latest driver available when reaching the code freeze deadline previous to a release.

being able to replace manually the ati drivers always gets you the latest and greatest the day they are out. considering the nature of a binary blob, it either works or not, and having a repo or not wont change a thing (dont quote me on this one) so it doesnt hurt to test it and revert if it fails.

if you wish to install the latest drivers, just download, create the debs.
uninstall the drivers from the repos. and install the drivers from the newly generated packages, then you have to reboot. (yes, ala windows reboot, restarting xorg doesnt work).

this procedure worked for me since the release of the drivers that support aiglx.
Thanks, I shouldn't had said anything actually, I'm a total noob on this field. I thought the repos of drivers are updated more regurarly, but ok.

---

### Post by excogitation on 2008-05-22
> **funnypanks said:**
> +1
except the watermark... so i have the pleasure of being annoyed now.

If you use --buildpkg ubuntu/hardy and install those there's **no watermark**.
([you can also get those *.deb's here]("http://ubuntuforums.org/showthread.php?p=5022007"))

I also had the watermark doing automatic? install.

---

