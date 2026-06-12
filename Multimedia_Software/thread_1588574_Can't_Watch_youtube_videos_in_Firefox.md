---
title: "Can't Watch youtube videos in Firefox"
date: 2010-10-05
forum: Multimedia Software
---

### Post by Jonny87 on 2010-10-05
Can't seem to get youtube videos to play in firefox. has anyone else encounted this? Does anyone know a solution?

Would really love to get this sorted as I want to convince my wife to change her laptop from XP to Linux but as she loves watching youtube, she'll see it as another reason to stay on Windows.

---

### Post by copyright201 on 2010-10-05
Hi Jonny87,

Do have have flash player installed?  I can't remember if Youtube still requires it but it's a good first shot...

```

sudo apt-get install flashplugin-installer

```

---

### Post by sikander3786 on 2010-10-05
> I can't remember if Youtube still requires it but it's a good first shot...

It actually requires flash player.

---

### Post by Jonny87 on 2010-10-05
Nope I have flashplayer installed. The page just comes up with;
> Warning: this video is not set to use HTML5. If you have not, go to [http://www.youtube.com/html5](http://www.youtube.com/html5) and join the beta.

But the quoted page seems to suggesting to use a beta version, I don't want to use a beta though. any ideas?

---

### Post by TBABill on 2010-10-05
Did you install the ubuntu-restricted-extras as well? Could just be a codec/java issue as well.
 
Edit: You also have to restart Firefox once you install any add ons like codecs.

---

### Post by Jonny87 on 2010-10-05
Yes I have the restricted extras installed.

---

### Post by Darkness Falls on 2010-10-05
Which version of Firefox are you using? When I got the latest update, FF started calling itself "Namoroka", and it messed up my YouTube watching ability at first as well; the solution was a very small icon at the bottom of the window where all the add-ons were listed, that let me manually change the player away from swfdec (which it had reverted to following the update) and onto something more useful. I don't know if that's the case in your situation, but it's possible that it might still be trying to use swfdec despite having flashplayer and java all installed and running fine.

D.F.

---

### Post by Jonny87 on 2010-10-05
> **Darkness Falls said:**
> Which version of Firefox are you using? When I got the latest update, FF started calling itself "Namoroka", and it messed up my YouTube watching ability at first as well; the solution was a very small icon at the bottom of the window where all the add-ons were listed, that let me manually change the player away from swfdec (which it had reverted to following the update) and onto something more useful. I don't know if that's the case in your situation, but it's possible that it might still be trying to use swfdec despite having flashplayer and java all installed and running fine.

D.F.

I'm using firefox 3.6.10
Thanks I'll check it out.

---

### Post by lovinglinux on 2010-10-05
Looks like the browser is trying to play the video as HTML5 (without plugin).

Please provide the link to the YouTube video.

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

### Post by Jonny87 on 2010-10-05
> **lovinglinux said:**
> Looks like the browser is trying to play the video as HTML5 (without plugin).

Please provide the link to the YouTube video.

Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:
Thanks for your help, I'll have to get back to you on that one as I'm not at home at the moment. I'll run it when I get home then post the result.

I like the idea of that list of commands to generate a report like that. if you have a chance would you be able to please Private Message me one that would give just a general all round report for any system that would show the likes of linux version etc through to the hardware and software on the machine, and anything that would be useful for diagnosing issues. I could really use something that and while I know some of those commands I'm guessing you'd probably more of them.

---

### Post by lovinglinux on 2010-10-05
> **Jonny87 said:**
> I like the idea of that list of commands to generate a report like that. if you have a chance would you be able to please Private Message me one that would give just a general all round report for any system that would show the likes of linux version etc through to the hardware and software on the machine, and anything that would be useful for diagnosing issues. I could really use something that and while I know some of those commands I'm guessing you'd probably more of them.

Unfortunately there are too many scenarios and commands. I did that one because I usually help other users with Firefox and Flash issues, so I know what to look for based on hundreds of threads I have already replied. I wouldn't know where to start to make a general report.

---

### Post by Jonny87 on 2010-10-06
Here is the out put of those commands;

> 
Ubuntu Architecture  Linux jonny-desktop 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=10.04 DISTRIB_CODENAME=lucid DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"  Firefox Packages  firefox						install firefox-branding				install firefox-gnome-support				install kubuntu-firefox-installer			install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-3.6.10/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources   Flash packages  adobe-flashplugin				install flashplugin-installer				deinstall  Plugin locations  /usr/lib/adobe-flashplugin/libflashplayer.so  /usr/lib/firefox/plugins/flashplugin-alternative.so /usr/lib/iceape/plugins/flashplugin-alternative.so /usr/lib/iceweasel/plugins/flashplugin-alternative.so /usr/lib/midbrowser/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/xulrunner/plugins/flashplugin-alternative.so /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  Flash symlinks  /usr/lib/firefox-addons/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/firefox-addons/plugins/libflashplayer.so' (No such file or directory) /usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 


Any ideas?

---

### Post by lovinglinux on 2010-10-06
> **Jonny87 said:**
> Here is the out put of those commands;



Any ideas?

Looks normal to me, but I still need the info from **about[noparse]:[/noparse]plugins** and the link to the YouTube video you are experiencing issues.

---

### Post by Jonny87 on 2010-10-06
Here is the firefox version;
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.2.10) Gecko/20100915 Ubuntu/10.04 (lucid) Ant.com Toolbar 2.0.1 Firefox/3.6.10Attached is a screen shot of the plugin info.

And the link is [http://www.youtube.com/watch?v=YqAEvkNtJ6A&feature=aso](http://www.youtube.com/watch?v=YqAEvkNtJ6A&feature=aso) but that not the only video it doesn't play. So far it only has trouble with youtube. I've had videos on other sites playing fine.

---

### Post by lovinglinux on 2010-10-06
> **Jonny87 said:**
> Here is the firefox version;
Attached is a screen shot of the plugin info.

And the link is [http://www.youtube.com/watch?v=YqAEvkNtJ6A&feature=aso](http://www.youtube.com/watch?v=YqAEvkNtJ6A&feature=aso) but that not the only video it doesn't play. So far it only has trouble with youtube. I've had videos on other sites playing fine.

Disable Ant Video Downloader extension and try again.

---

