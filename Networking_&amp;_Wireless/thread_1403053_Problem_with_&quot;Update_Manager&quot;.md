---
title: "Problem with &quot;Update Manager&quot;"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by bamdl001 on 2010-02-09
Hi all, I was updating my new install of KK 9.10 and got about 80% done when Update manager displayed this error message:

[COLOR=Red]W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.18.3-1ubuntu2.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gtk+2.0/libgail-common_2.18.3-1ubuntu2.1_i386.deb)
  404  Not Found [IP: 91.189.88.45 80][/COLOR]

I'm a complete newbie to Linux so could someone shed some light on this please.

Many Thanks

---

### Post by suseendran.rengabashyam on 2010-02-10
Hi,

Try the following steps and let me know if it works

1) See whether you can access the Internet, you need to have a proper connection to install any packages.

2) There might me some intermittent problem with [http://au.archive.ubuntu.com/](http://au.archive.ubuntu.com/) . You can change the repository and try update again. Go to System->Administration->Synaptic Package Manger->Settings->Repositories, in the 'Download From:' drop-down menu select the 'Main Server'. Don't forget to click the 'Reload' button and then try installing a package.

---

### Post by bamdl001 on 2010-02-10
Thanks suseendran rengabashyam, it worked and your help was much appreciated. One more thing if I might ask.. I don't suppose you would know why my screen keeps going black after about 5-10 minutes, it's ok when I move the mouse but then 5-10 minutes later it goes black again. It's almost like it's a screen saver or monitor sleep or something like that. I've had a look at desktop/display settings but I'm still none the wiser.. Many thanks[URL="http://ubuntuforums.org/member.php?u=986845"]
[/URL]

---

### Post by suseendran.rengabashyam on 2010-02-11
Hi,

I guess you problem might be related to the "Blank Screen" screensaver.

Go to System->Preferences->Screensaver, if your Screensaver theme is "Blank Screen" you can change it or you can move the slider near "Regard the computer as idle after:" to delay the screensaver.

Let me know if this helps.

---

### Post by bamdl001 on 2010-02-11
Once again this worked.. sorry about that, I know my way around Windows but Ubuntu is still unfamiliar. But I vow to become an Ubuntu addict. Many thanks

---

