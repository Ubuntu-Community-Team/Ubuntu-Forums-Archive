---
title: "Flash audio problem."
date: 2010-08-17
forum: Multimedia Software
---

### Post by RBTR on 2010-08-17
This happens nearly anytime I watch any relatively lengthy flash video on youtube or other online flash players. I watch the video, and the audio is fine for a few seconds, but then the audio cuts off as the video continues to play.

Sometimes, when I move the scrollbar of the screen/pause and replay the movie, it starts back up again for a few seconds then shuts off or plays the audio I just heard.

Anyone have any advice on this?



Also, please tell me what info you need to see to help me.

---

### Post by lovinglinux on 2010-08-18
Please provide the output of the following commands and instructions. This will make sure I will have a good understanding of your Firefox and Flash installations, so I don't need to guess what might be happening to your system:

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

### Post by RBTR on 2010-08-19
Okay. Attached is the information you asked for.

---

### Post by lovinglinux on 2010-08-19
I couldn't find anything wrong with your setup based on the report.

See the sound solution at [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

If that doesn't help, try to create a new Firefox profile, just for testing and if it still doesn't improve, try to create a new Ubuntu user to see if the problem persists.

---

### Post by arjunatwombly on 2010-10-09
> **lovinglinux said:**
> I couldn't find anything wrong with your setup based on the report.

See the sound solution at [http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

If that doesn't help, try to create a new Firefox profile, just for testing and if it still doesn't improve, try to create a new Ubuntu user to see if the problem persists.

i'm having the same problem, and it's happening in all browsers (firefox, chrome and opera). i created a new Ubuntu user account and the problem went away. so, how do i export the settings from this new account back into the old one? where are they stored?

thanks!

---

### Post by lovinglinux on 2010-10-09
> **arjunatwombly said:**
> i'm having the same problem, and it's happening in all browsers (firefox, chrome and opera). i created a new Ubuntu user account and the problem went away. so, how do i export the settings from this new account back into the old one? where are they stored?

thanks!

Are you sure you want to do that? Have you tried the suggested solution on my previous posts?

If you are sure you to reset ALL your settings, then go to your home folder, press CTRL+H to display hidden folders, then select all folders that start with a dot and copy them to somewhere safe in order to use them as backup if something goes wrong.  Then delete all folders that start with a dot and reboot. When you login again, the configuration files will be recreated. Please keep in mind this will reset ALL your personal settings for all applications including your gnome panels and theme, Firefox bookmarks and so on.

---

