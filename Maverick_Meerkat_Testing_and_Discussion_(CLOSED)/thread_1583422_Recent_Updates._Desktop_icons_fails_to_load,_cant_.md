---
title: "Recent Updates. Desktop icons fails to load, cant right click,open any folder, CPU Hi"
date: 2010-09-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2010-09-27
Recent updates : Desktop icon fails to load, cant right click on desktop or open folders, and CPU is running high. Also, the mouse cursor never stop loading/spinning. I have no idea as to which update may have caused this but I bothered to right down all that was just installed.

```
gnome-power-manger upgraded, libgtk2.0-common upgraded, libstdc++6 upgraded, libgutenprint2 upgraded, gcalctool upgraded, libcupsppdc1 upgraded, libcupsimage2 upgraded, libglib2.0-data upgraded, libcupsdriver1 upgraded, udisk upgraded, empthy-common upgraded, gnome-terminal upgraded, cups-client upgraded, lubindicate-gtk2 upgraded, python-indicate upgraded, libgomp1 upgraded, empathy upgraded, software-center upgraded, zeitgeist-datahub upgraded, zeitgeist upgraded, grub-pc upgraded, libglib2.0-0 upgraded, gcc-4.4 upgraded, lib32gcc1 upgraded, gconf-editor upgraded, libgcc1 upgraded, python-aptdaemon upgraded, debconf-i18n upgraded, gnome-system-tools upgraded, libcups2 upgraded, cups-driver-gutenprint upgraded, python-vte upgraded, libvte9 upgraded, vino upgraded, aptdaemon upgraded, gnome-terminal-data upgraded, cups upgraded, python-aptdaemon-gtk upgraded,cups-bsd upgraded, libgnomeui-common upgraded, libgnome-keyring0 upgraded, zeitgeist-ore upgraded, gcc-4.5-base upgraded, debconf upgraded, cpp-4.4 upgraded, lib32stdc__6 upgraded, grub-common upgraded, libcupsmim1 upgraded, nautilus-sendto-empathy upgraded, libgnomecanvas2-common upgraded
```

---

### Post by dinamic1 on 2010-09-27
uh, thanks :D i'll skip updates 'till tomorow

---

### Post by TBerk on 2010-09-27
It looks to be a run away File Manager bug; ie: Nautilus.

I just was trying to post this stream of continuousness post:

> Well,I too saw that, I went w/ it, I am currently rebooted into 'through the looking glass' mode, in that I have a great deal of open folders or shortcuts in the task bar down below (as if a key was stuck on  he keyboard that was creating new folders or something...) It's running wild, doing _something_.

I can't get Administration:System monitor to load, even though I can see the small app up near the date/time/weather- my dual CPUs are being slammed right now, the even the fan on the mother boards kicked it up a notch.

I am able to run Synaptics, again, it wants to download...

(what looks like the same upgrades I installed moments ago)

Wait, It's installing software and all the extra boxes or winds down below have stopped, and the CPU meter is back to a nominal state.

All this goes on while I type this post btw.

OK, I'm going to post, and reboot now...

(Firefox wont let me post, it wants me to 'close Firefox..".

After I rebooted the second time I went with APT-GET and discovered that the windows opening (and eventually closing) at the bottom of the screen would finally stop opening new ones and settle down to a 'normal' OS experience.

One more update and it 'patched' Nautilus (and mousetweeks, but I think it's unrelated)


I'll reboot again later, but for now it seems there is a sync lapse int he upgrade files- which might have just now gotten caught up.


TBerk
feeling less and less Mr. Wizard-ish w/ this latest release...

---

### Post by tad1073 on 2010-09-27
> **tjeremiah said:**
> Recent updates : Desktop icon fails to load, cant right click on desktop or open folders, and CPU is running high. Also, the mouse cursor never stop loading/spinning. I have no idea as to which update may have caused this but I bothered to right down all that was just installed.

```
gnome-power-manger upgraded, libgtk2.0-common upgraded, libstdc++6 upgraded, libgutenprint2 upgraded, gcalctool upgraded, libcupsppdc1 upgraded, libcupsimage2 upgraded, libglib2.0-data upgraded, libcupsdriver1 upgraded, udisk upgraded, empthy-common upgraded, gnome-terminal upgraded, cups-client upgraded, lubindicate-gtk2 upgraded, python-indicate upgraded, libgomp1 upgraded, empathy upgraded, software-center upgraded, zeitgeist-datahub upgraded, zeitgeist upgraded, grub-pc upgraded, libglib2.0-0 upgraded, gcc-4.4 upgraded, lib32gcc1 upgraded, gconf-editor upgraded, libgcc1 upgraded, python-aptdaemon upgraded, debconf-i18n upgraded, gnome-system-tools upgraded, libcups2 upgraded, cups-driver-gutenprint upgraded, python-vte upgraded, libvte9 upgraded, vino upgraded, aptdaemon upgraded, gnome-terminal-data upgraded, cups upgraded, python-aptdaemon-gtk upgraded,cups-bsd upgraded, libgnomeui-common upgraded, libgnome-keyring0 upgraded, zeitgeist-ore upgraded, gcc-4.5-base upgraded, debconf upgraded, cpp-4.4 upgraded, lib32stdc__6 upgraded, grub-common upgraded, libcupsmim1 upgraded, nautilus-sendto-empathy upgraded, libgnomecanvas2-common upgraded
```

got the same thing here.

---

### Post by tjeremiah on 2010-09-27
> **dinamic1 said:**
> uh, thanks :D i'll skip updates 'till tomorow

welcome :(

---

### Post by Aearenda on 2010-09-27
I hit this too. The file ~/.xsession-errors has the message > nautilus: symbol lookup error: nautilus: undefined symbol: g_application_get_type repeatedly. Using Synaptic Package Manager I force-downgraded from the Elementary version to the stock Maverick version of Nautilus and the problem went away. I expect the Elementary version will get fixed pretty soon!

Edit: Or maybe not. See [this bug]("https://bugs.launchpad.net/nautilus-elementary/+bug/621736").
But there is hope: See [here]("http://ammonkey.posterous.com/maverick-nautilus-elementary-ppa-again-operat").
Actually, I suspect these refer to older problems. Anyway, I've gone back to the stock Nautilus for now.

---

### Post by Anduu on 2010-09-27
Strange...I updated a couple of hours ago and again just now and rebooted and no issues here.

aptitude safe-upgrade is holding back packages,however those that have been listed here are not among them.

---

### Post by tjeremiah on 2010-09-27
> **Aearenda said:**
> I hit this too. The file ~/.xsession-errors has the message  repeatedly. Using Synaptic Package Manager I force-downgraded from the Elementary version to the stock Maverick version of Nautilus and the problem went away. I expect the Elementary version will get fixed pretty soon!

Edit: Or maybe not. See [this bug]("https://bugs.launchpad.net/nautilus-elementary/+bug/621736").
But there is hope: See [here]("http://ammonkey.posterous.com/maverick-nautilus-elementary-ppa-again-operat").
Actually, I suspect these refer to older problems. Anyway, I've gone back to the stock Nautilus for now.

Thanks! This is clearly now a nautilus elementary problem. The moment I downgraded, my icons reappeared, CPU went down, and I can right click.

---

### Post by Aearenda on 2010-09-27
> **Anduu said:**
> Strange...I updated a couple of hours ago and again just now and rebooted and no issues here.

aptitude safe-upgrade is holding back packages,however those that have been listed here are not among them.

I'm pretty sure it is updates to other packages not listed here, GTK-related perhaps, that have broken Nautilus-elementary.

---

### Post by Anduu on 2010-09-27
> **Aearenda said:**
> I'm pretty sure it is updates to other packages not listed here, GTK-related perhaps, that have broken Nautilus-elementary.

It's all becoming clear to me now.

I forgot that I had ditched nautilus-elementary last week because of the problems it had/has been having re: [http://ammonkey.posterous.com/multiple-problems-about-nautilus-nautilus-ele](http://ammonkey.posterous.com/multiple-problems-about-nautilus-nautilus-ele)

I am actually running erik anderson's RGBA patched version of nautilus at the moment.

This > [http://ammonkey.posterous.com/maverick-nautilus-elementary-ppa-again-operat](http://ammonkey.posterous.com/maverick-nautilus-elementary-ppa-again-operat) ,however is good news.I'll have to keep tabs on this thread and give nautilus-elementary another shot once things get sorted out.

---

### Post by jdorenbush on 2010-09-27
I'm dealing with the same issue right now. :(

```
nautilus: symbol lookup error: nautilus: undefined symbol: g_application_get_type
```

---

### Post by ace586 on 2010-09-28
Having the same issue. It definitely seems to be related to nautilus elementary. For a quick temporary fix, use the following:

```
sudo aptitude install nautilus=1:2.31.92-0ubuntu2
```

This will return you to the standard version from the Maverick repositories.

Hopefully this gets solved soon. I'd really like to get nautilus elementary back.

---

### Post by TBerk on 2010-09-28
Within the space of a half an hour I had run Synaptics three times and it broke and then 'fixed' the problem.

You might want to look at the current available updates by the time you read this.


TBerk

---

### Post by jdorenbush on 2010-09-28
This thread has related information. [http://ubuntuforums.org/showthread.php?t=1583260](http://ubuntuforums.org/showthread.php?t=1583260)

Now, I've got a few packages aside from just nautilus that are having upgrade/dependency problems.

---

### Post by Aearenda on 2010-09-28
I arrived at the Nautilus-elementary problem without allowing any partial upgrades, and I don't have any other package problems - so the partial-upgrades thing is probably just muddying the water as far as this Nautilus-elementary issue is concerned.

---

### Post by ammonkey on 2010-09-28
hello,

glib dropped gapplication so we had to revert back to libunique. The packages are now updated to 2.32.0 in the PPA.

---

### Post by tjeremiah on 2010-09-28
> **ammonkey said:**
> hello,

glib dropped gapplication so we had to revert back to libunique. The packages are now updated to 2.32.0 in the PPA.

Thanks for the heads up. I just downloaded/updated and the problem appears to be fixed. I'll give it an hour or two for other users to try before I mark thread as solved.

---

### Post by Aearenda on 2010-09-28
The updated packages work fine for me. Thanks, ammonkey - you're doing a great job!

---

