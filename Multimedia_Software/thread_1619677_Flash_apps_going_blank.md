---
title: "Flash apps going blank"
date: 2010-11-12
forum: Multimedia Software
---

### Post by Wanderin_ponderer on 2010-11-12
Hi everyone,

I've been having this problem for some time now, but none of the fixes for other flash problems have worked (re-installing Flash, installing Flash-aid, disabling compiz, upgrading Firefox, etc), and I can't seem to find a similar thread.

My issue is this, if I go to a site in Firefox that uses flash like youtube, megavideo, grooveshark, or slacker.com and begin to load a video, song, or station, I can't open any other windows or switch to another desktop without the app freezing and going blank; sometimes it just shows white space as if nothing were ever posted, other times it shows a grey box where the app was, but no longer works.  If I right click in these spaces, nothing happens as when I right click on, say, a megavideo video and get a drop-down list.  The only thing that solves the problem is refreshing the page.

I never had this problem with older versions of ubuntu like jaunty, and it's rather annoying since I can't do anything else while a video is loading or music is playing.

Any advice that doesn't advise me simply to switch to Chrome would be greatly appreciated, but if there's nothing else to be done, so be it.

Thanks in advance!

---

### Post by lovinglinux on 2010-11-12
See [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Wanderin_ponderer on 2010-11-15
Thanks for the speedy reply lovinglinux (I've been too busy to respond). I actually found this page earlier when the buttons weren't working, and it worked great for that issue (so long overdue thanks!), but the only one that seems similar to my current problem is the 'choppy,...' issue, and I tried both solutions in turn, but the problem persists.  A couple times a month I search the forums for new solutions, but I finally decided to post since the most up-to-date thread was from June. It's beginning to look like it may just be a hardware problem since no one else seems to be experiencing the same thing.

Oddly enough, I accidentally discovered that if I start the video loading, then hit the maximize button to take said window out of full screen, it doesn't seem to freeze.  Not sure if this has just been coincidental a few times or if it's a genuine, fluke solution, but if I find it continues to solve the problem I'll change the thread to [solved].

Cheers!

---

### Post by Wanderin_ponderer on 2010-11-29
Apparently that wasn't the fix I was hoping for, but I'm still not having any luck finding a solution.  I'm wondering if it's just the 64 bit version I'm running.  It's the first time I'm running a 64 bit OS and it's also the first time I'm having multiple software problems.

I'll leave this up a little longer (crossing my fingers), then look into deleting it when I have a bit more time

---

### Post by lovinglinux on 2010-11-30
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

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
echo 'Flash packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'flash*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Plugin locations' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate libflashplayer.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
locate flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Flash symlinks' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/lib/firefox-addons/plugins/libflashplayer.so  >> ~/Desktop/firefox-report.txt
file /usr/lib/mozilla/plugins/flashplugin-alternative.so  >> ~/Desktop/firefox-report.txt
file /etc/alternatives/mozilla-flashplugin  >> ~/Desktop/firefox-report.txt
file /var/lib/flashplugin-installer/npwrapper.libflashplayer.so  >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by Wanderin_ponderer on 2010-12-01
I apologize lovinglinux, I stopped checking this thread regularly, and I was having multiple problems that seemed to be stemming from me upgrading to the 64 bit version when I upgraded to Lynx (flash problems, difficulty finding drivers, random GUI crashes, etc.), so I switched to a 32 bit version.

I didn't realize you had posted again until I came back to get the link to your flash page for the flash-aid link (didn't come up in my firefox add-on search for some reason).

Anyways, I really appreciate all the help you offered (I love how helpful the Linux community is!) So, thank you very much.

I'll mark this as solved, but since it's so short, if it would be preferable to delete it I can do that too.

Cheers!  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by lovinglinux on 2010-12-01
> **Wanderin_ponderer said:**
> I apologize lovinglinux, I stopped checking this thread regularly, and I was having multiple problems that seemed to be stemming from me upgrading to the 64 bit version when I upgraded to Lynx (flash problems, difficulty finding drivers, random GUI crashes, etc.), so I switched to a 32 bit version.

I didn't realize you had posted again until I came back to get the link to your flash page for the flash-aid link (didn't come up in my firefox add-on search for some reason).

Anyways, I really appreciate all the help you offered (I love how helpful the Linux community is!) So, thank you very much.

I'll mark this as solved, but since it's so short, if it would be preferable to delete it I can do that too.

Cheers!  [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

You are welcome.

---

### Post by VicAve on 2010-12-13
I have been experiencing the same problems as Wandering ponderer so I wonder if I could piggy back some advice here.  Original problem was the white screen where flash video was running, which occurred after opening another web page with FLV media.  

I've tried disabling all the add ons, running Firefox in safe mode, disabling hardware acceleration and installing Flash Aid  1.0.18.  By running the 64 version in Flash Aid I have progressed from the white screen mentioned, to a window with links to reload the flash video and send a crash report.  Nevertheless, the crashes still persist, and the site I use to stream films doesn't support Express Install and the version of (Flash 10.0) I have installed. 

 Any advice to resolve or improve this would be really helpful.

**Shockwave Flash:**  

File:  /usr/lib/mozilla/plugins/libflashplayer.soVersion:   Shockwave Flash 10.3 d162

[B]
Mozilla:[/B]

Mozilla/5.0 (X11; U; Linux x86_64; en-GB; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.04 (lucid) Firefox/3.6.13


[B]System info:

[/B]Linux ubuntu 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox                        install
firefox-branding                install
firefox-gnome-support                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

lucid-partner.list
medibuntu.list

Flash packages


Plugin locations

/usr/lib/firefox/plugins/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

---

### Post by lovinglinux on 2010-12-13
Have you tried the fix from my tutorial?

Have you tried to disable Compiz?

Does it happen with all sites?

---

### Post by VicAve on 2010-12-14
Thanks for your response lovinglinux. 

Yes, I have tried the fix from your tutorial recently:   Ran **sudo mkdir /etc/adobe** and disabled hardware acceleration.  Haven't applied any of the other fixes as the symptoms don't match.

Following your last posting I have disabled Compiz and all its plugins, which I thought had cracked it.  But then after half an hour of flicking through my usual sites flash has just crashed again.  Interesting that you ask about particular sites associated with the problem, as both [independent.co.uk]("http://www.independent.co.uk") and Yahoo mail have been the main ones that seem to trigger crashes; and this is the page which was the culprit this time[ http://www.independent.co.uk/opinion/leading-articles/]("http://www.independent.co.uk/opinion/leading-articles/")

Is it worth me considering installing Firefox 32 bit?  I'm reading that there may be less conflicts with this version.  Thanks again for your input on this.

---

### Post by lovinglinux on 2010-12-14
> **VicAve said:**
> Thanks for your response lovinglinux. 

Yes, I have tried the fix from your tutorial recently:   Ran **sudo mkdir /etc/adobe** and disabled hardware acceleration.  Haven't applied any of the other fixes as the symptoms don't match.

Following your last posting I have disabled Compiz and all its plugins, which I thought had cracked it.  But then after half an hour of flicking through my usual sites flash has just crashed again.  Interesting that you ask about particular sites associated with the problem, as both [independent.co.uk]("http://www.independent.co.uk") and Yahoo mail have been the main ones that seem to trigger crashes; and this is the page which was the culprit this time[ http://www.independent.co.uk/opinion/leading-articles/]("http://www.independent.co.uk/opinion/leading-articles/")

Is it worth me considering installing Firefox 32 bit?  I'm reading that there may be less conflicts with this version.  Thanks again for your input on this.

The 32bit is more stable for sure, since the new 64bit is only at alpha stage. Besides, before the square preview, Adobe had suspended 64bit support. So you never know when they will do that again. Running the 32bit with nspluginwrapper on 64bit should also be less stable.

---

### Post by VicAve on 2010-12-14
I may well try that.  Cheers again for your input on this.  

All the best.

---

