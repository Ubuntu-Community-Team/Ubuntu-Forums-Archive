---
title: "Flash plugin behaving differently in different user accounts"
date: 2010-08-06
forum: Multimedia Software
---

### Post by kaiwi on 2010-08-06
Hi there

My wife and I share a PC, each of us having his/her own user account. 

In my account, the Adobe Flash Plugin for Firefox works perfectly. 

In my wife's account, the Flash Plugin does not work. It is installed but it either crashes or is not loaded.

In both accounts, the Flash-Aid add-on is installed. 

I don't know to which extent the Firefox installation is the same for different user accounts. 

Can I tell Ubuntu to execute Firefox and the Flash plugin
in my wife's account in the same way (i.e. correctly) as in my account? Perhaps by exporting user parameters from my account to my wife's account?

Any suggestions are welcome

Cheers

---

### Post by lovinglinux on 2010-08-07
If you are using FLASH-AID, then you should have the same flash for both accounts. BTW, you don't have to install FLASH-AID on both profiles. 

Please login with her account and provide the info below. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

**1 - Flash Version**

Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here. it should look lie the image below:

[IMG]http://tinyurl.com/287j7on[/IMG]

**2 - Firefox version and architecture**

To find Firefox version and architecture, click "Help >> About Mozilla Firefox" in the menu. The info will be located at the bottom of the info dialog:

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

### Post by kaiwi on 2010-08-08
Hi lovinglinux, 

firstly, thank you for your help!

In my wife's account, Firefox gives the following info:

**1 - Shockwave Flash**

    File: /usr/lib/adobe-flashplugin/libflashplayer.so
    Version: 
    Shockwave Flash 10.1 r53

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

**2 - Firefox Version:**

version 3.6.8
Mozilla Firefox for Ubuntu
canonical - 1.0

**3 - System Info**

Please see the attached file, firefox-report.txt

---

### Post by lovinglinux on 2010-08-08
I don't see anything wrong with her setup.

You could try to remove adobe-flashplugin and install flashplugin-installer. They are essentially the same thing, but sometimes installing one or the other makes some difference.

```
sudo apt-get purge adobe-flashplugin
sudo apt-get install flashplugin-installer
```

If that doesn't help, try to create a new Firefox profile on her account to see if there is something like an extension interfering.

You can access the profile manager with:

```
firefox -P
```

---

### Post by kaiwi on 2010-08-08
Thanks lovinglinux. 

I followed your suggestions (in particular deleted my wife's firefox profile and created new one), but to no avail. I tested Firefox Flash plugin by going to [http://www.adobe.com/software/flash/about/]("http://www.adobe.com/software/flash/about/"). The plugin still works fine in my account but crashes in hers.


> **lovinglinux said:**
> 
You could try to remove adobe-flashplugin and install flashplugin-installer. They are essentially the same thing, but sometimes installing one or the other makes some difference.

```
sudo apt-get purge adobe-flashplugin
sudo apt-get install flashplugin-installer
```

If that doesn't help, try to create a new Firefox profile on her account to see if there is something like an extension interfering.

You can access the profile manager with:

```
firefox -P
```

---

### Post by lovinglinux on 2010-08-08
It must be some gnome settings on her account that are messing with flash. Try to create a third user to see if the problem persists.

Do you have Moonlight extension installed? Check if you have the  libmoon package and remove it.

---

### Post by kaiwi on 2010-08-08
Brilliant idea, lovinglinux! For my new test user, the plugin works. I think I'll simply create a new account for my wife and delete her existing one. 

I haven't got the Moonlight extension installed.

I think the problem is solved for me. I'm not going to mark the thread as 'solved' yet, as we haven't identified the actual cause of the trouble.

Thank you very much for your kind assistance!!



> **lovinglinux said:**
> It must be some gnome settings on her account that are messing with flash. Try to create a third user to see if the problem persists.

Do you have Moonlight extension installed? Check if you have the  libmoon package and remove it.

---

### Post by lovinglinux on 2010-08-08
> **kaiwi said:**
> Brilliant idea, lovinglinux! For my new test user, the plugin works. I think I'll simply create a new account for my wife and delete her existing one. 

I haven't got the Moonlight extension installed.

I think the problem is solved for me. I'm not going to mark the thread as 'solved' yet, as we haven't identified the actual cause of the trouble.

Thank you very much for your kind assistance!!

You are welcome. I wish we could pinpoint the source of the problem, but I'm more convinced now that the troubles with flash in Firefox are caused by Ubuntu+Gnome+Flash and not Firefox itself. You are not the first one with this scenario.

---

