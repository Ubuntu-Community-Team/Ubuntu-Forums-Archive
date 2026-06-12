---
title: "How to Uninstall Namoroka and revert to Firefox 3.6.8?"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by 1234blizzard on 2010-08-17
I installed Firefox 4.0 beta on Ubuntu and it made Firefox into  Namoroka. Now I want to revert back to the stable Firefox but I am  unable to do it. I have tried uninstalling and reinstalling but none of  this works. 

Thanks in advance!

---

### Post by wilee-nilee on 2010-08-17
Go go to synaptic, search with firefox and you will see what's installed and what's not. After you get finished setting up what you want, go to home and show hidden files with ctrl-h and remove the extra firefox folders from the mozilla folder leaving the one your choosing to use.

---

### Post by xangua on 2010-08-17
did you added a ppa¿ use ppa-purge

sudo ppa-purge "ppa's name"

ppa-purge is incluided in maverick repositories, search a deb for lucid

---

### Post by lovinglinux on 2010-08-17
Go to "System >> Software Sources >> Other Software" and disable the repository you have used to install Firefox 4 (probably ubuntu-mozilla-daily), then run the following commands:

```
sudo apt-get purge firefox-4.0
sudo apt-get update
sudo apt-get install --reinstall firefox
```

Keep in mind Firefox 4 should be using a cloned profile, so if there is any bookmarks, passwords or other important files in your FF 4 profile, you might need to export them and import into your default profile. Firefox 4 profile is located at **~./mozilla/firefox-4.0** and your default is at **~/.mozilla/firefox**

For future reference see my Firefox 4 tutorial at [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

Why do you want to uninstall it? Although Firefox 4.0 is still beta, it is much better than 3.6.8. Perhaps I could help you solve the problems if you want to.

---

### Post by 1234blizzard on 2010-08-18
Thanks a lot!! This worked really well. I wanted to uninstall Namoroka because none of my add-ons worked with it such as ad-block. Hotmail.com also doesn't work. It thinks that Namoroka is a mobile browser so it's in mobile mode. Thanks again!

---

### Post by lovinglinux on 2010-08-18
> **1234blizzard said:**
> Thanks a lot!! This worked really well. I wanted to uninstall Namoroka because none of my add-ons worked with it such as ad-block. Hotmail.com also doesn't work. It thinks that Namoroka is a mobile browser so it's in mobile mode. Thanks again!

Namoroka is not a mobile browser. Mozilla has a mobile browser called [Fennec]("http://www.mozilla.com/en-US/mobile/"). Nevertheless, Namoroka is the codename for Firefox 3.6 development branch, so you wasn't really using Firefox 4 as you thought you were. When you add a PPA like ubuntu-mozilla-daily, it updates your current Firefox installation with the latest Firefox, in this case Namoroka 3.6.9pre. It also allows to install Firefox 4.0, codename Minefield, side-by-side with 3.6.x. Firefox 4 is installed on a different folder, has a different launcher located under "Internet >> Mozilla Developer Preview Web Browser" and uses a cloned user profile.

So, to avoid confusion, I would recommend not using the PPA, but downloading Firefox 4 from Mozilla. See my [tutorial]("http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html") for instructions.

AdblockPlus developer has already released a version compatible with 4.0b4pre, so you just need to update your add-ons. Have you done that?

While most extension won't work with Firefox 4 at this moment, you can override compatibility check to force some of them. Nevertheless, this needs to be done carefully, because Firefox 4 introduces several radical changes that break extensions compatibility. See my tutorial for instructions.

Hotmail is working with Firefox 4.0b3, so I suspect your problem is because you didn't update AdblockPlus. I had a similar problem with Gmail before updating Adblock to the latest version.

---

### Post by 1234blizzard on 2010-08-18
After I reverted back to Firefox 3.6.8, I tried one of your tutorials  using FoxTester. Hotmail.com still doesn't work in Minefield. It works  on my Windows machine but here on Ubuntu it doesn't.

---

### Post by 1234blizzard on 2010-08-18
After I reverted back to Firefox 3.6.8, I tried one of your tutorials  using FoxTester. Hotmail.com still doesn't work in Minefield. It works  on my Windows machine but here on Ubuntu it doesn't.

---

### Post by lovinglinux on 2010-08-18
> **1234blizzard said:**
> After I reverted back to Firefox 3.6.8, I tried one of your tutorials  using FoxTester. Hotmail.com still doesn't work in Minefield. It works  on my Windows machine but here on Ubuntu it doesn't.

Weird. Which Minefield version you are using?

BTW, did you like FoxTester?

---

### Post by 1234blizzard on 2010-08-18
I really like FoxTester. :) When I'm in Minefield, i click help and then about minefield. It says version 4.0b5. I also tried the stable 4.0b3 releases. 

Just a quick question, but in your 4.0 browser, does hotmail work?

---

### Post by lovinglinux on 2010-08-18
> **1234blizzard said:**
> I really like FoxTester. :)

Cool :)

> **1234blizzard said:**
> When I'm in Minefield, i click help and then about minefield. It says version 4.0b5. I also tried the stable 4.0b3 releases. 

Just a quick question, but in your 4.0 browser, does hotmail work?

Yes, it works here on 4.0b3. I haven't tested on b5pre yet.

---

### Post by 1234blizzard on 2010-08-18
That's really weird.

---

### Post by lovinglinux on 2010-08-18
> **1234blizzard said:**
> That's really weird.

I forgot to mention I'm using KDE, so it could make a difference. Sometimes Gnome settings can interfere with Firefox.

---

### Post by kageman on 2010-10-19
I had this same exact issue while trying to get Firefox 4.0.  Thanks for the post here on how to fix it.  My browser is (mostly) back to normal.  When I add Firefox to my Quicklaunch and load the program, I still get the Namoroka globe instead of the Firefox icon.  Also, when I type "Firefox" in the KDE App Launcher, it shows up "Namoroka Web Browser".  Anyway to fix these?

---

### Post by lovinglinux on 2010-10-19
> **kageman said:**
> I had this same exact issue while trying to get Firefox 4.0.  Thanks for the post here on how to fix it.  My browser is (mostly) back to normal.  When I add Firefox to my Quicklaunch and load the program, I still get the Namoroka globe instead of the Firefox icon.  Also, when I type "Firefox" in the KDE App Launcher, it shows up "Namoroka Web Browser".  Anyway to fix these?

Disable ubuntu-mozilla-daily ppa from Software Sources and re-install firefox.

```
sudo apt-get install --reinstall firefox
```

---

### Post by kageman on 2010-10-19
> **lovinglinux said:**
> Disable ubuntu-mozilla-daily ppa from Software Sources and re-install firefox.

```
sudo apt-get install --reinstall firefox
```
That's exactly what I did, but I still have that issue.

---

### Post by lovinglinux on 2010-10-19
> **kageman said:**
> That's exactly what I did, but I still have that issue.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox installations, so I don't need to guess what might be happening to your system:


**1 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog (you need to resize the window to see it):

[IMG]http://tinyurl.com/26b85o2[/IMG]


**3 - System Info**

Execute the following commands then copy the generated file, named **firefox-report.txt** from your Desktop and upload it here or paste the contents.

To execute those commands, select the entire content below, then go to "Applications >> Accessories >> Terminal" and click the terminal with the middle-mouse button.

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
```

---

### Post by kageman on 2010-10-19
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10

```
Ubuntu Architecture

Linux kjg-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-4.0-core                deinstall
firefox-branding                install
firefox-kde-support                install
firefox-launchpad-plugin            install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

conkyhardcore-ppa-lucid.list
conkyhardcore-ppa-lucid.list.distUpgrade
conkyhardcore-ppa-lucid.list.save
echidnaman-qapt-lucid.list
echidnaman-qapt-lucid.list.distUpgrade
echidnaman-qapt-lucid.list.save
jd-team-jdownloader-lucid.list
jd-team-jdownloader-lucid.list.distUpgrade
jd-team-jdownloader-lucid.list.save
kubuntu-ppa-backports-lucid.list
kubuntu-ppa-backports-lucid.list.distUpgrade
kubuntu-ppa-backports-lucid.list.save
kubuntu-ppa-ppa-maverick.list
kubuntu-ppa-ppa-maverick.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-mozilla-security-ppa-maverick.list
ubuntu-mozilla-security-ppa-maverick.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.distUpgrade
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.distUpgrade
ubuntu-wine-ppa-lucid.list.save

```

---

### Post by lovinglinux on 2010-10-19
> **kageman said:**
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100922 Ubuntu/10.10 (maverick) Firefox/3.6.10

```
Ubuntu Architecture

Linux kjg-laptop 2.6.35-22-generic #34-Ubuntu SMP Sun Oct 10 09:24:00 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox                        install
firefox-4.0-core                deinstall
firefox-branding                install
firefox-kde-support                install
firefox-launchpad-plugin            install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

conkyhardcore-ppa-lucid.list
conkyhardcore-ppa-lucid.list.distUpgrade
conkyhardcore-ppa-lucid.list.save
echidnaman-qapt-lucid.list
echidnaman-qapt-lucid.list.distUpgrade
echidnaman-qapt-lucid.list.save
jd-team-jdownloader-lucid.list
jd-team-jdownloader-lucid.list.distUpgrade
jd-team-jdownloader-lucid.list.save
kubuntu-ppa-backports-lucid.list
kubuntu-ppa-backports-lucid.list.distUpgrade
kubuntu-ppa-backports-lucid.list.save
kubuntu-ppa-ppa-maverick.list
kubuntu-ppa-ppa-maverick.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.save
ubuntu-mozilla-daily-ppa-maverick.list
ubuntu-mozilla-daily-ppa-maverick.list.save
ubuntu-mozilla-security-ppa-maverick.list
ubuntu-mozilla-security-ppa-maverick.list.save
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.distUpgrade
ubuntu-tweak-stable.list.save
ubuntu-wine-ppa-lucid.list
ubuntu-wine-ppa-lucid.list.distUpgrade
ubuntu-wine-ppa-lucid.list.save

```

You still have ubuntu-mozilla-daily and ubuntu-mozilla-security. Make sure both are disabled before re-installing firefox.

Please notice that you have not only ubuntu-mozilla-daily and ubuntu-mozilla-security, but also mozillateam-firefox-stable. I'm not sure if you have enabled all of them, but you shouldn't do that, since they provide different updates for the same packages. If you want to use the latest firefox (Namoroka), you should pick  ubuntu-mozilla-daily or ubuntu-mozilla-security and disable the other two. If you want the regular firefox, disable all of them or enable only mozillateam-firefox-stable.

---

### Post by kageman on 2010-10-21
> **lovinglinux said:**
> You still have ubuntu-mozilla-daily and ubuntu-mozilla-security. Make sure both are disabled before re-installing firefox.

Please notice that you have not only ubuntu-mozilla-daily and ubuntu-mozilla-security, but also mozillateam-firefox-stable. I'm not sure if you have enabled all of them, but you shouldn't do that, since they provide different updates for the same packages. If you want to use the latest firefox (Namoroka), you should pick  ubuntu-mozilla-daily or ubuntu-mozilla-security and disable the other two. If you want the regular firefox, disable all of them or enable only mozillateam-firefox-stable.

Even though those PPAs showed up in the generated txt file, they're not on my system.  They are not listed under Software Sources in KPackageKit and when I tried removing them using ppa-purge, I got an error saying they could not be found.  I don't understand why they did show up in the generated file.

---

### Post by kageman on 2010-10-21
Actually, never mind.  I just upgraded to Firefox 3.6.11 and the problem seems to have taken care of itself.  Thanks anyway.

---

### Post by -Sparx- on 2010-10-21
Hi!

I seem to have the same problem and was hoping that the weird new name would go away. Changing things I don't want to have changed is just a big red flag to me.

I did the purge and reinstall and manually removed the mozilla repositories from /etc/apt/sources.list.d/
Removed the folder firefox-4.0 from .mozilla as well

Im still in "Namoraka mode" however.

Firefox->help->about gives this:
Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.12pre) Gecko/20101020 Ubuntu/9.10 (karmic) Namoroka/3.6.12pre

This is the output from the script:

```

Ubuntu Architecture

Linux sparx-laptop 2.6.31-22-generic #67-Ubuntu SMP Sat Oct 16 18:51:35 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

Firefox Packages

firefox						install
firefox-3.5					install
firefox-3.5-branding				install
firefox-3.5-gnome-support			install
firefox-4.0-core				deinstall
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.12pre/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

loneowais-ppa-karmic.list
loneowais-ppa-karmic.list.save

```

The reason I don't  want to use firefox 4 at this time is the lack of addons and my setup right now makes the interface weird in firefox 4. For example, I can not move the menu and that means I cant get the top bar to disappear which makes for a lot of dead space if I move my address bar back to "tabs on top" mode. I hope this is something that will get fixed or if it's just me being stupid that someone will show me how not to be... that. 
Looking forward to firefox 4 though. Seems to have a lot of cool new ideas that will make for a nice webbing.

---

### Post by -Sparx- on 2010-10-21
So I solved this problem... a nightmare in and of itself. I'm just not cut out for beta testing. 

So what did I do? 
I noticed that I had firefox 3.6.12 prebuild installed for some reason
(probably a stupid update i said yes to from the ppa:daily-build 
repository) and this did not change with the reinstall of (firefox) that
build. The reinstall of anything in relation to firefox in synaptic 
changed nothing. So I tried a downgrade on the "firefox dummy package" 
entry in synaptic which was the only entry relating to 3.6.12. Synaptic 
promted me to remove ALOT of packages and reinstalling suspiciously few 
but I went ahead and did that anyways (a couple of 100Mb). 
Firefox was now gone..! Downgraded in to nothing, with some rest packages 
that didn't really go away for some reason. 
However the Ubuntu logo on the "firefox" dummy 
package had now reappeared(?) but I went ahead and uninstalld every 
firefox package. 
Restarted my computer... For no reason a bootscreen appeared which I 
don't usually see (WHY!). 
Anyways when I got back to Ubuntu i installed firefox (about 40Mb or 
something) and it is now working. Loosing 160-260Mb is just magic to me. 

So maybe I should just have?
1. Remove every firefox package. (backup ~/.mozilla!)
1.5 Reboot
2. Install firefox dummy package.

I'm no expert and maybe there is another way. This worked for me.
I'm now going to see if there's a safe way to try ff4 out.

PS: I also had to reinstall the sunjava plugin

---

### Post by lovinglinux on 2010-10-22
> **-Sparx- said:**
> I'm now going to see if there's a safe way to try ff4 out.

[FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/")

Also see [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

---

### Post by -Sparx- on 2010-10-25
> **lovinglinux said:**
> [FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/")

Also see [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

I will definitely try FoxTester when i get the time. I checked your tutorial page out and I am impressed! Very nice! Lots of info I've been looking for in a nice format.

I realize now that most of my problems came from my own stupidity. Even thunderbird got its share.

Thanks for the tip.

---

