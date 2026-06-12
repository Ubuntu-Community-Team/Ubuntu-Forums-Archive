---
title: "Computer freezing related to video problem?"
date: 2011-09-28
forum: Multimedia Software
---

### Post by kiwibrit on 2011-09-28
I am new to Ubuntu and have recently installed  11.04 into my EeePc which formerly ran on Xp.  From time to time the  computer freezes.  There is no apparent pattern, it just hangs up.  The  mouse freezes, and keyboard input becomes impossible - even  Ctrl+Alt+Delete.  The only way out is the off switch.  Looking for an  error log, I was pointed at xsessions errors.  Just after the last  freeze, I took a copy very soon after reboot of the tail end of that  log. From what I saw, I thought that I had a network problem - but I've been told the problem is a video one.  Can you confirm that? Here is the copy of the log:

```
(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net  usershare' returned error 255: net usershare: cannot open usershare  directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1167): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1168): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/nick/.xsession-errors
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1168): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/nick/.xsession-errors
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (process:1168): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1152): DEBUG: MaximizeIfBigEnough: window mapped and already maximized, just undecorate
```Video details:

```

lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

```

```
lshw -c video
WARNING: you should run this program as super-user.
  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f7f00000-f7f7ffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:f7ec0000-f7efffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7f80000-f7ffffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

```

---

### Post by jonnyboysmithy on 2011-09-29
What driver are you using?
I had an experimental driver installed that kept locking upon me, now I got the proprietary one and it doesn't happen anymore.

---

### Post by kiwibrit on 2011-09-29
I don't know what driver I am using - and even after extensive searching on Google, I can't find out how to do so.  I think the problem may stem from not selecting a 3D driver during installation.  As I am not running 3D CAD - and don't expect to be handling 3D PDFs, I saw no reason to do so - but I gather that Ubuntu runs best with a 3D driver.

FWIW, I have now switched to Gnome, so at least I now find advice saying that I should use the 'System' tool bar makes sense!

---

### Post by kiwibrit on 2011-09-29
Downloaded the zip file for what appeared to be the appropriate Linux driver for the chip set  from Intel.  Moved the zip file to  the Home folder,  and extracted there.  Attempted to run the .exe file, and failed with this error message:

```

Archive:  /home/xxxx/IEGD_10_3_1_GOLD/IEGD_10_3_1_GOLD_1550.exe
Zip file size: 128196608 bytes, number of entries: 45568

warning [/home/xxxx/IEGD_10_3_1_GOLD/IEGD_10_3_1_GOLD_1550.exe]:  end-of-central-directory record claims this
  is disk 26627 but that the central directory starts on disk 43162; this is a
  contradiction.  Attempting to process anyway.
error [/home/xxxx/IEGD_10_3_1_GOLD/IEGD_10_3_1_GOLD_1550.exe]:  missing 1097972840 bytes in zipfile
  (attempting to process anyway)
error [/home/xxxx/IEGD_10_3_1_GOLD/IEGD_10_3_1_GOLD_1550.exe]:  attempt to seek before beginning of zipfile
  (please check that you have transferred or created the zipfile in the
  appropriate BINARY mode and that you have compiled UnZip properly)

```

What fun.

---

### Post by nothingspecial on 2011-09-29
Hello again kiwibrit :)

I'm going to move your thread again to Multimedia & Video this time.
```

sudo lshw -C display
```

Will output your video information.

You cannot run .exe files with linux, are you sure that it was a linux driver you downloaded.

If you get a complete lock up in future, rather than holding down the off button you can try one of 2 things to shut your computer down cleanly.

Either press Ctrl-Alt-F1 and log in to tty1, then type

```
sudo shutdown -r now
```

or hold down Alt-RysRq and keeping both those buttons held down, type **R,S,E,I,U,B** in that order.

Cheers.

---

### Post by kiwibrit on 2011-09-29
Thanks for moving me to the right place, nothingspecial :)  Driver was for the 945GME chipset for Linux Fedora 10(kernel 2.6.27, X.org 1.5.X.server.1.53) allegedly.  It was my best guess as to what I needed.

Ctrl+Alt+Delete wouldn't do the shut down - but I'll follow up on the Ubuntu computer with your other points.  

Thanks.

---

### Post by kiwibrit on 2011-09-29
Hmm.  Well, the first thing to say is that since switching from Unity to Gnome, there have been no more crashes.  So I've stumbled on a more stable interface which, for me, is also easier to follow.

However, I would like to see this thing through - firstly because in the process I am learning how Ubuntu works, and, secondly, I want to make sure I have the optimum video drive.

So onwards..... From this

```

  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GME Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f7f00000-f7f7ffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:f7ec0000-f7efffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f7f80000-f7ffffff

```I take it that the video driver is i915?
  
Is the configuration correct? 

Is there a better driver out there which will run in Umbuntu?

I was looking here for [drivers]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Embedded+Components+and+Flash+Memory&ProductLine=Embedded+Chipsets&ProductProduct=Mobile+Intel%C2%AE+945GME+Express+Chipset"), BTW.

---

### Post by kiwibrit on 2011-09-29
Argh.  It just froze.  Mind you that is the first time today.  Even so, I need to get this sorted. I see that the [i915 driver]("http://www.intel.com/support/chipsets/sb/cs-011594.htm") is not for my graphics chipset - so I suppose it is not surprising that I have problems.

Next step is to find a Linux driver for the Mobile 945 GME in a format I can load.  If I can do that I will update this thread - meanwhile if some can advise me, I'd appreciate that, too.

---

### Post by jonnyboysmithy on 2011-09-30
If you open terminal (Ctrl+Alt+T) then type ```
jockey-gtk
```
It should tell you what drivers are available to install.

---

### Post by kiwibrit on 2011-09-30
Thanks, it tells me that there are no proprietary drivers to install.  However, looking [here]("http://ubuntuforums.org/archive/index.php/t-158885.html") I see others have had problems with this chopset and the driver installed by Ubuntu by default - and that the i810 driver may be the answer.  Could you tell me how to install the substitute driver?

---

### Post by kiwibrit on 2011-09-30
Yuk.  The [list of supported video]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel") says that there is a freeze screen bug with i945. So go to [bug 445056]("https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/445056") and scroll down to bottom.  Aha! says that 

> As per last comment, this is believed fixed.So go to usr/lib/dri  . Nope.  i915 and i965 are there, but no i945.  Not in dri_alternates, either.

Hmm. [Spot the documentation on binary drivers]("https://help.ubuntu.com/community/BinaryDriverHowto") . Maybe the answer lies in[SIZE=1] Xorg.conf.d[/SIZE]?  says it is in usr/lib/Xll/[SIZE=1]Xorg.conf.d.  No it's not - I guess that assumes I have plugged in something  else. 

As a newcomer, this is all getting a bit above my pay grade.  Is there someone out there who can tell me where the driver is that the hardware support people now believe has its bug fixed?
[/SIZE]

---

### Post by kiwibrit on 2011-09-30
Hmm.  Going to the Software centre, I see the 'fixed' driver is what I have installed.  I suspect that it is not fixed, and that my problem is one I cannot solve.  I'd be delighted to be proved wrong, though.

---

### Post by jonnyboysmithy on 2011-09-30
One of the guys on the launchpad site said it wouldn't lockup on him when he had desktop effects turned off, you could try that.

---

### Post by kiwibrit on 2011-09-30
Thanks, I'll try that if I come back to Ubuntu - have switched to Linux Mint to see how that does - since it supports my graphic chipset more specifically.  So far, it looks promising.  Straight out of the box, it recognised my wireless card, and so far (touch wood) it hasn't frozen.  I didn't know about Xubuntu before I switched, but apparently that's something to keep in mind, too.

Thanks for your interest -and may the ABs win the World Cup!

---

### Post by jonnyboysmithy on 2011-10-02
> **kiwibrit said:**
> Thanks, I'll try that if I come back to Ubuntu - have switched to Linux Mint to see how that does - since it supports my graphic chipset more specifically.  So far, it looks promising.  Straight out of the box, it recognised my wireless card, and so far (touch wood) it hasn't frozen.  I didn't know about Xubuntu before I switched, but apparently that's something to keep in mind, too.

Thanks for your interest -and may the ABs win the World Cup!

Well, what would you guess? today I also got linux mint! I was tired of having ubuntu 11.10 beta.
It was slow on my hardware, although it supported my graphics nicely it just didn't cut it.
yes go the ABs!!

---

### Post by jonnyboysmithy on 2011-11-20
Just want to let you know that this was in update manager today:  This package provides the driver for the Intel i8xx and i9xx family of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945 and i965 series chips. This package also provides XvMC (XVideo Motion Compensation) drivers for i810/i815 and i9xx and newer chipsets. More information about X.Org can be found at:  This package is built from the X.org xf86-video-intel driver module.

---

