---
title: "unparsable xorg.conf when using nvidia-settings in karmic"
date: 2009-10-29
forum: Multimedia Software
---

### Post by aze555666 on 2009-10-29
Hi.
I installed Karmic (64bits) with nvidia drivers 185 today, but I can't get my dual screen back : when i use "sudo nvidia-settings", set my secondary screen to "activate -> Separate X Screen" and then hit the "Save to x confguration file" button, I get an error message stating that "Failed to parse existing X config file '/etc/X11/xorg.conf".

Here is my xorg.conf : 
```

feanor@feanor-desktop:~$ cat /etc/X11/xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```[FONT=Verdana]

As you can see, it is very short. I think this is why nvidia-settings can't parse it : some parts must be missing.
[/FONT]I also tried to replace my xorg.conf with an old one found on the jaunty I still have on a hdd (I moved to ssd some months ago), but it failed (my main screen was shifted some pixels up and left. The second one was active but only with 2 empty panels, the login wallpaper and impossibility to do anything on it)


Thanks

---

### Post by realzippy on 2009-10-29
was it an error or just "warning" ?Remember a parsing warning during former nvidia installation.It can be ignored.Your xorg.conf looks fine (mine is the same) ;-)

**edit:
confirm,nvidia-settings not seems to write to xorg.conf anymore...

---

### Post by wiebeest on 2009-10-29
> **realzippy said:**
> 
**edit:
confirm,nvidia-settings not seems to write to xorg.conf anymore...

Really? What a relief. I was like WTF too when trying to save changes after sudo nvidia-setting and got the same error. 

So nvidia doesn't write to xorg.conf anymore? So how does it then keep the settings after reboot? We'll see it reminds my settings after reboot. Keep you informed.

---

### Post by realzippy on 2009-10-29
Found a workaround:

delete or rename your xorg.conf,open terminal and let nvidia xconfig create a new one:

**sudo nvidia-xconfig**

gksudo nvidia-settings,no more parsing error.

---

### Post by aze555666 on 2009-10-29
I tried again, the windows which displays the message has no title, but the icon on it looks like it is a warning. But the only button is "validate". Wether I validate or close it, the result is the same : xorg.conf doesn't change.
I also tried to run it with a 2>/dev/null, the error goes through it (I mean, it is displayed on terminal anyway).

Here is the terminal version of the error : 
```

feanor@feanor-desktop:~$ sudo nvidia-settings 2>/dev/null

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Erreur de segmentation

```
(in which "Erreur de segmentation" means "segmentation error" in french^^)

---

### Post by realzippy on 2009-10-29
> **aze555666 said:**
> I tried again, the windows which displays the message has no title, but the icon on it looks like it is a warning. But the only button is "validate". Wether I validate or close it, the result is the same : xorg.conf doesn't change.
I also tried to run it with a 2>/dev/null, the error goes through it (I mean, it is displayed on terminal anyway).

Here is the terminal version of the error : 
```

feanor@feanor-desktop:~$ sudo nvidia-settings 2>/dev/null

VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf.
Undefined Device "(null)" referenced by Screen "Default Screen".

Erreur de segmentation

```
(in which "Erreur de segmentation" means "segmentation error" in french^^)

..yep,I tested it,same error.But deleting xorg helps  ;-)

---

### Post by aze555666 on 2009-10-29
I was writng my message while you posted this :-)
Thank you very much for the idea, I just did it and the file was successfully written.
I'll now restart X server.

---

### Post by aze555666 on 2009-10-29
Doesn't work with compiz : shifted 1st screen, bugged 2nd one (not able to click, and logn wallpaper).
I runned a "matacity --replace" and now both screen are working well (even : the apps i launch from the menu on 2nd screen apear on 2nd screen (a bug made them appear on 1st screen with jaunty))
But the 1st screen is still shifted.

So there are still 2 problemes to be solved: 
- make it work properly with compiz
- get the left and top pixels back on main screen !

---

### Post by realzippy on 2009-10-29
..2 new threads  ;-).

You should set this thread to solved (unparsable xorg.conf when using nvidia-settings in karmic),there might be lots of nvidia users...

---

### Post by KingBongo on 2009-10-29
I am having the same problem. xorg.conf cannot be parsed. I tried to remove every file with xorg.conf in it from terminal, then 

sudo nvidia-xconfig

gksudo nvidia-settings

with no luck. The new xorg.conf can still not be parsed. I am trying to start "Separate X screen" but if xorg.conf cannot be parsed then no luck. I have been patiently waiting for 9.10 to be released thinking that would do it, but no. 

Any ideas?

---

### Post by realzippy on 2009-10-29
That is strange.Tested it a second time;no more parsing error.Shure you deleted the xorg.conf?

---

### Post by KingBongo on 2009-10-29
I GOT IT WORKING! Finally S-Video on my old TV.

The trick is to remove the xorg.conf file ( sudo rm xorg.conf* ) and start Nvidia-settings ( sudo nvidia-settings ). Then make your changes, save to xorg.conf and then restart X (or computer). Works every time.

---

### Post by HappyFeet on 2009-10-29
> **KingBongo said:**
> I GOT IT WORKING! Finally S-Video on my old TV.

The trick is to remove the xorg.conf file ( sudo rm xorg.conf* ) and start Nvidia-settings ( sudo nvidia-settings ) make your changes, **save to xorg.conf** and then restart X (or computer). Works every time.

You forgot to mention you need to make a new empty xorg.conf first.

I'm still pissed this "bug" made it into the final release.

---

### Post by KingBongo on 2009-10-29
HappyFeet:
Actually I do not have to create a new one. It works anyway, for me at least. It says something like "cannot open existing xorg.conf" but you just have to specify the name yourself ("xorg.conf", check the path!) and a new one is created.

Yes, this is an annoying bug which should not have made it to the final release. I waited forever for the official 9.10 release to get this fixed, for nothing. But hey, at least it can be made to work. This bug will most likely be fixed quickly.

---

### Post by realzippy on 2009-10-30
> **HappyFeet said:**
> You forgot to mention you need to make a new empty xorg.conf first.

I'm still pissed this "bug" made it into the final release.



Who is able to read...;)

[http://ubuntuforums.org/showthread.php?t=1304897](http://ubuntuforums.org/showthread.php?t=1304897)

---

### Post by Shane10101 on 2009-11-08
> **realzippy said:**
> 
You should set this thread to solved 

Not quite yet.  None of the suggestions above solved the problem...at least not for me.  Help!

---

### Post by slick_nick on 2009-11-08
Had the same problem, deleting xorg.conf did work!

---

