---
title: "Compiz not working?"
date: 2011-03-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vaskark on 2011-03-13
Hi. I just upgraded to Natty and am having some trouble getting compiz to work. There's no Visual Effects tab in the Appearance prefs window anymore. I'm in Classic Mode right now because I encountered some difficulty with the Unity 2D Desktop.

So how can I start compiz? Do I just do 'compiz' in the run dialog?

Thanks.

---

### Post by ejket on 2011-03-13
I'm wondering the same thing.  I started with Kubuntu, then added xubuntu-desktop and ubuntu-desktop.  I finally installed nvidia-current today after having had a disaster with it previously, and all is well in KDE.  However, I still get no panel at all with Ubuntu (Unity, I guess) and no effects in Ubuntu Classic.

---

### Post by cariboo on 2011-03-13
You don't need to do anything compiz starts automagically when you select the Ubuntu Desktop from the session menu. Make sure you have the correct graphics driver installed to enable 3D. Keep in mind that the ATI/AMD closed source driver does not work with the current Xorg-xserver yet.

---

### Post by vaskark on 2011-03-13
Thanks for the replies.
Compiz was working beautifully on Maverick before I decided to upgrade to Natty (my graphics card is NVIDIA GeForce 6200 512Mb DDR2). It says I'm using the recommended driver in the Additional Drivers window.

---

### Post by cariboo on 2011-03-13
Have you installed compizconfig-settings-manager?

---

### Post by vaskark on 2011-03-13
> **cariboo907 said:**
> Have you installed compizconfig-settings-manager?
Yes. It opens fine.

---

### Post by cariboo on 2011-03-13
Is compiz running?

```
ps ax | grep compiz
```

the output should look something like this:

```
ps ax | grep compiz
 1401 ?        Sl     2:29 compiz
 4166 pts/0    S+     0:00 grep --color=auto compiz
```

---

### Post by vaskark on 2011-03-13
```
ps ax | grep compiz
 1675 ?        Ss     0:00 /bin/sh -c /usr/bin/compiz-decorator
 2098 pts/0    D+     0:00 grep --color=auto compiz
```

As far as I know compiz isn't currently running, according to System Monitor.

---

### Post by vaskark on 2011-03-13
Hmm. Now compiz is working in Ubuntu Desktop Session, but not Classic or Unity 2D.

---

### Post by Amaranth on 2011-03-13
Unity2D specifically doesn't use compiz because it is... 2D. Not sure why the Classic Session wouldn't run it, as far as I know it runs when possible unless you choose the Classic Session (failsafe) or whatever it is called.

---

### Post by vaskark on 2011-03-14
> **Amaranth said:**
> Unity2D specifically doesn't use compiz because it is... 2D.
Hahaha oops. Long day :(

---

### Post by vaskark on 2011-03-14
I went into Ubuntu Classic again and ran 'compiz --replace':

```
compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing composite options...done
Initializing opengl options...done
Initializing decor options...done
Initializing wobbly options...done
Initializing commands options...done
Initializing mousepoll options...done
Initializing gnomecompat options...done
Initializing cube options...done
Initializing rotate options...done
Initializing expo options...done
Initializing scale options...done
Initializing ezoom options...done
Setting Update "run_command_terminal_key"
Setting Update "expo_edge"
Setting Update "initiate_edge"
Segmentation fault (core dumped)
```
But compiz is working in Ubuntu Desktop session. Sigh.

---

### Post by Fitoschido on 2011-04-02
@vaskark: After doing that I obtain:

```
dell@dell-Latitude-E6400:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (opengl) - Fatal: glXCreateContext failed
compiz (bailer) - Info: Ensuring a shell for your session
dell@dell-Latitude-E6400:~$ Cannot register the panel shell: there is already one running.

```

I think that Ubuntu says me that cannot register panel shell because I'm running GNOME-Panel, but I can't kill gnome-panel because it reappears instantly.

I want to use Unity desktop, but both Unity and Classic sessions have gnome panel (and no Compiz compositing and effects). I upgraded from Maverick but since that it's impossible to use Unity :(

---

### Post by osarusan on 2011-04-02
Having the same problem here:

```
osarusan@GLaDOS:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (opengl) - Fatal: Software rendering detected
compiz (bailer) - Info: Ensuring a shell for your session

```

---

### Post by SmSpillaz on 2011-04-07
> **Fitoschido said:**
> @vaskark: After doing that I obtain:

```
dell@dell-Latitude-E6400:~$ compiz --replace
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
compiz (opengl) - Fatal: glXCreateContext failed
compiz (bailer) - Info: Ensuring a shell for your session
dell@dell-Latitude-E6400:~$ Cannot register the panel shell: there is already one running.

```

I think that Ubuntu says me that cannot register panel shell because I'm running GNOME-Panel, but I can't kill gnome-panel because it reappears instantly.

I want to use Unity desktop, but both Unity and Classic sessions have gnome panel (and no Compiz compositing and effects). I upgraded from Maverick but since that it's impossible to use Unity :(

3D Acceleration is not supported on your hardware.

---

### Post by encefalocardia on 2011-04-07
Compiz is behaving weird on my end. It does not start automatically. It works ok if I run compiz --replace but I would like it to start automatically.

---

### Post by zarquon42 on 2011-04-07
I experienced the same thing after upgrading. Try creating a new user and log in as this user. If compiz starts automatically, this is is caused by a conflicting personal setting. After removing all settings from my home directory (folders starting with "." - make a backup of course) everything works just fine now.

---

### Post by ajarmoniuk on 2011-04-14
I had the same. After upgrading to Natty, my hardware was no longer supported. ;)

Launch gconf-editor and go to /apps/metacity/general and
make sure if "compositing_manager" is checked.

In my case, it made my hardware suddenly being supported.

---

### Post by osarusan on 2011-04-16
I'm still getting this "compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing" error... Using an ATI Radeon HD 4550 with the open source drivers, I can't get Compiz to load at all.

Checking marking the compositing_manager in gconf-editor as ajarmoniuk suggest won't fix compiz -- it just enables Metacity's compositing instead of Compiz. It will let you use Unity, but it doesn't fix the underlying problem here.

Is anyone else having this problem with the ATI (non-fglrx) drivers?? Anyone know how to fix this? I have tried reinstalling compiz, to no avail.

---

### Post by PatrickVogeli on 2011-04-16
for me compiz --replace, but it crashes were freqüently with segfaults in libregex... completely unusable.

---

### Post by vmp on 2011-04-17
I have the same problem. Compiz segfaults, there is no desktop effects tab on appearance, compiz-fusion-icon crashes and so on.

I have an ATI radeon based laptop and compiz has been working perfectly since hardy, with proprietary drivers in the past and the open source drivers for more than a year now.

Unity does not even start and gnome classic loads without compiz and with a few crash reports.

---

### Post by PatrickVogeli on 2011-04-20
one week until the official release and compiz still won't work... hope it gets solved

---

### Post by cobra1984 on 2011-04-22
I had this same issue I attribute it to me not downloading and installing update packages during the installation progress of the OS, so as a result it booted my computer with generic graphics drivers until i downloaded the proper ones for my card (Nvidia Geforce 8400 GS). I found that "compiz --replace" brought back my ability to use compiz temporarily until i rebooted. I added a startup for compiz in the "startup applications". I named it Compiz with the command "compiz --replace". Now i got effects everytime i reboot. Now i justs need to figure out how to get unity back after uninstalling and reinstalling compiz :confused:

---

### Post by cobra1984 on 2011-04-23
got Unity back went to Synanptic Package manager and installed "Unity" and reinstalled all packages listed green under Unity search. :-)

---

### Post by PatrickVogeli on 2011-04-27
one day to release and compiz still not working.. segfaults very frequently due to libregex problems.

Am I alone?

---

