---
title: "Flash on Firefox broken"
date: 2010-06-08
forum: Multimedia Software
---

### Post by jimmyisland on 2010-06-08
I recently upgraded to 10.04 and now firefox is having problems with flash. Chrome plays flash videos without problem. All I get is a black screen, no sound, when watching youtube and the like on Firefox. I checked Firefox plugins, and I have both Flash 9.0 r999 and the latest Flash 10.0 r22. I disabled Flash 9 and enabled Flash 10. Now flash videos come up warnings "the plugin for this content has been disabled. Click here to manage your plugins." Enabling/disabling the opposite also doesn't help (blank screen again), enabling both doesn't help (blank screen) etc. Firefox -safe-mode with other add-ons disabled does not fix the problem.

I did a complete remove of Flash in synaptic, and reinstalled. Same problem. It seems to me that it is Firefox that is the problem. I see some other threads with similar problems, but no solution.

Some output:
j@laptop:~$ locate libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

Would a complete removal/reinstall of Firefox help? Any help appreciated
J

---

### Post by gandaran on 2010-06-08
if you disable one version of flash it also disables flash completely in firefox, the fix is to remove one version, you can only have one installed if you don't want any problems.
and check of you have flashblock addon installed, the black window is probably due to this addon.

---

### Post by lovinglinux on 2010-06-08
Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by jimmyisland on 2010-06-08
Thanks for the prompt responses. I have installed Flash AID and it did not remove the multiple copies of Flash plugin (9 & 10). I still have the same problem viewing video.

How do I go about deleting the plugins. The only options firefox seems to give is to 'Disable' them or not (which does not fix the problem). 
Thanks

---

### Post by lovinglinux on 2010-06-08
> **jimmyisland said:**
> Thanks for the prompt responses. I have installed Flash AID and it did not remove the multiple copies of Flash plugin (9 & 10). I still have the same problem viewing video.

How do I go about deleting the plugins. The only options firefox seems to give is to 'Disable' them or not (which does not fix the problem). 
Thanks

Have you restarted the browser after running FLASH-AID? Did you get any errors from the terminal output?

---

### Post by jimmyisland on 2010-06-08
Yes I restarted Firefox. I have rerun FlashAID and I have noticed the following warning while running the sequence which purges the system of other flash versionsL

-----------------------
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/firefox/plugins' not empty so not removed.
-----------------------

I do get Terminal output when running firefox from terminal:

-----------------------
Ensuring the plugin stays in memory did not work.
This happens when the plugin was copied from its installed location at /usr/lib/swfdec-mozilla/libswfdecmozilla.so.
Please use the --with-plugin-dir configure option to install it into a different place.
-----------------------


Alas, I don't know what the output means. I feel i need to explicitly remove the extensions from ./mozilla, or remove ./mozilla all together. I would prefer not to though because I don't want to remove all of the addons,

Thanks again.

---

### Post by lovinglinux on 2010-06-08
> **jimmyisland said:**
> Yes I restarted Firefox. I have rerun FlashAID and I have noticed the following warning while running the sequence which purges the system of other flash versionsL

-----------------------
dpkg: warning: while removing flashplugin-installer, directory '/usr/lib/firefox/plugins' not empty so not removed.
-----------------------

I do get Terminal output when running firefox from terminal:

-----------------------
Ensuring the plugin stays in memory did not work.
This happens when the plugin was copied from its installed location at /usr/lib/swfdec-mozilla/libswfdecmozilla.so.
Please use the --with-plugin-dir configure option to install it into a different place.
-----------------------


Alas, I don't know what the output means. I feel i need to explicitly remove the extensions from ./mozilla, or remove ./mozilla all together. I would prefer not to though because I don't want to remove all of the addons,

Thanks again.

No need to remove your ~/.mozilla folder.

Please post the output of these commands:

```
ls /usr/lib/firefox/plugins
```

```
locate libswfdecmozilla.so
```

```
sudo apt-get purge swfdec-mozilla
```

---

### Post by jimmyisland on 2010-06-09
here it is, looks like libsfwdecmozilla.so is missing:

james@james-laptop:~$ ls /usr/lib/firefox/plugins
flashplugin-alternative.so  libjavaplugin.so  nppdf.so
james@james-laptop:~$ locate libswfdecmozilla.so
james@james-laptop:~$ sudo apt-get purge swfdec-mozilla
[sudo] password for james: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  texlive-extra-utils texlive texlive-fonts-recommended texlive-pstricks-doc
  libqt4-core texlive-pstricks prosper tipa texlive-latex-recommended-doc pgf
  texlive-latex-recommended texlive-generic-recommended
  texlive-fonts-recommended-doc ps2eps latex-beamer texlive-font-utils
  latex-xcolor lacheck
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
james@james-laptop:~$

---

### Post by lovinglinux on 2010-06-09
Open Firefox, type **about[noparse]:[/noparse]config**, then type **plugin.expose_full_path** in the filter, double-click the preference in the results in order to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, copy and paste here the version and file path of the Shockwave plugin.

Also post he output of the command below:

```
file /usr/lib/firefox/plugins/flashplugin-alternative.so
```

---

### Post by jimmyisland on 2010-06-09
Thanks.
I definitely have 2 versions of Flash
Output from about:plugins
---------------
Shockwave Flash

    File: /usr/lib/firefox-addons/plugins/flashplugin-alternative.so
    Version: 
    Shockwave Flash 9.0 r999
---------------
LATER ON IN THE SAME PAGE
---------------
Shockwave Flash

    File: /usr/lib/flashplugin-installer/libflashplayer.so
    Version: 
    Shockwave Flash 10.0 r45
---------------

Output to file /usr/lib/firefox/plugins/flashplugin-alternative.so
---------------
james@james-laptop:~$ file /usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/firefox-flashplugin'
james@james-laptop:~$ 
---------------

---

### Post by lovinglinux on 2010-06-09
Do this:

```
sudo rm -f /usr/lib/firefox-addons/plugins/flashplugin-alternative.so
```

Restart Firefox and check the version again and if it works.

---

### Post by jimmyisland on 2010-06-09
thanks, that worked! an explicit remove was what it needed.

---

### Post by Pazystamas on 2010-06-13
I use flash-aid and today it updated from 64bit to 32bit flash version (security update, no adobe suport for 64bit version). Now flash don't respond to mouse clicks.
in about: plugins shows:
**Shockwave Flash**

 Failas:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Laida:   Shockwave Flash 10.1 r53

how to go back to 64bit flash version? looks like flash-aid don't have normal settings...

---

### Post by lovinglinux on 2010-06-13
> **Pazystamas said:**
> I use flash-aid and today it updated from 64bit to 32bit flash version (security update, no adobe suport for 64bit version). Now flash don't respond to mouse clicks.
in about: plugins shows:
**Shockwave Flash**

 Failas:  /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
Laida:   Shockwave Flash 10.1 r53

how to go back to 64bit flash version? looks like flash-aid don't have normal settings...

Try this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line:

```
GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

I do not recommend re-installing the 64bit, but if the above doesn't work, then run these:

```
sudo apt-get purge flashplugin-nonfree
sudo apt-get purge flashplugin-installer
sudo rm -f /usr/lib/firefox-addons/plugins/libflashplayer.so
sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
tar xvf libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so
```

---

### Post by Pazystamas on 2010-06-14
I removerd 32bit flash and from "Unubtu tweak" source center instaled "Adobe flash PPA (x86-64). Now it works ok. I know that this version has security bug, i hope some day adobe release new 64bit version.

---

### Post by lovinglinux on 2010-06-14
> **Pazystamas said:**
> I removerd 32bit flash and from "Unubtu tweak" source center instaled "Adobe flash PPA (x86-64). Now it works ok. I know that this version has security bug, i hope some day adobe release new 64bit version.

I strongly advise to use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/) and allow only trusted sites.

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
Sorry for multiple posts.  ubutunforums was not behaving.

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by mckemie on 2011-01-20
After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

---

### Post by lovinglinux on 2011-01-20
> **mckemie said:**
> After long trials and tribulations, I finally got shockwave flash working on my 10.04 64 bit along about November 2010.  Version currently installed is:
Shockwave Flash 10.3 d162
I believe I downloaded it from the adobe site and then linked it into Firefox.  Life was good!  Hulu worked!

ALAS! Sometime along about mid-December an "upgrade" from the prompted automatic upgrade Ubuntu feature broke it.  Attempts to display flash, including youtube and hulu, just result in blank screen areas.

What to do?

Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by mckemie on 2011-01-20
> **lovinglinux said:**
> Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

Great stuff!  Once I figured out to select the new little icon at the end of the URL bar, everything went swimmingly.  Everything seems to work now.  Gracias.  Donation in the works.

I wonder why this addon didn't pop up in my google searches on "broken flash" and such?

---

### Post by lovinglinux on 2011-01-20
> **mckemie said:**
> Great stuff!  Once I figured out to select the new little icon at the end of the URL bar, everything went swimmingly.  Everything seems to work now.  Gracias.  Donation in the works.

I wonder why this addon didn't pop up in my google searches on "broken flash" and such?

You are welcome and thanks for the support. Let me know if you need any  additional help.

I don't know why you didn't find it via search, but I reply to users with similar flash problems every day here.

---

