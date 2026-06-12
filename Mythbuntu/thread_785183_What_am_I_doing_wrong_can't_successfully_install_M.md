---
title: "What am I doing wrong: can't successfully install Mythbuntu"
date: 2008-05-07
forum: Mythbuntu
---

### Post by Crusty Juggler on 2008-05-07
I'm trying to install Mythbuntu 8.04 via the LiveCD.  I go through the whole installation process okay (at this point I'm just using the guided partition set-up praying that it will smooth the process) and once it's completed it just goes to the desktop with no prompts for the initial configuration page (with the General, Capture cards, Video sources, Input connections, Channel editor and Storage directories) and no obvious way to open such a page.  

If I reboot and take out the bootable CD, it goes through the whole splash screen but then I get the following: 

```
Starting up...
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/b4626e4c-0678-422f-81cc-e8398a0feb5d) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/b4626e4c-0687-422f-81cc-e8398a0feb5d
kinit: No resume image, doing normal boot...

Ubuntu 8.04 dell-desktop tty1

dell-desktop login:
```

Besides this being a big problem, the even bigger issue is that I can't type anything.  It won't register anything from my keyboard, so I can't enter any commands or do anything other than a hard reboot.  I've searched around and found other people with the whole "No resume image..." issue but they have been able to at least log-in.  

Thanks, I hope someone can help!

---

### Post by Crusty Juggler on 2008-05-07
I saw advice in another thread to boot to recovery mode.  When I did, it gave me three options: resume boot, boot to root or fix x or xorg server (if these are exactly correct it's because I'm going from memory).  I selected the third and it gave a message about possibly overwriting xorg.conf and then went straight back to the three choices.  I did the third again, got the same overwrite message and went back to the three choices.  So I selected resume boot.  One of the lines had a red "fail" notice, but I couldn't see what it was.  Once the boot was finished, I got to the same terminal-esque login request.  This time I was able to log in with my username and password and I got a screen full of:
```
 -bash: /dev/null: Permission denied 
```

Again, please help!

---

### Post by superm1 on 2008-05-07
> **Crusty Juggler said:**
> I'm trying to install Mythbuntu 8.04 via the LiveCD.  I go through the whole installation process okay (at this point I'm just using the guided partition set-up praying that it will smooth the process) and once it's completed it just goes to the desktop with no prompts for the initial configuration page (with the General, Capture cards, Video sources, Input connections, Channel editor and Storage directories) and no obvious way to open such a page.  

If I reboot and take out the bootable CD, it goes through the whole splash screen but then I get the following: 

```
Starting up...
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/b4626e4c-0678-422f-81cc-e8398a0feb5d) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/b4626e4c-0687-422f-81cc-e8398a0feb5d
kinit: No resume image, doing normal boot...

Ubuntu 8.04 dell-desktop tty1

dell-desktop login:
```Besides this being a big problem, the even bigger issue is that I can't type anything.  It won't register anything from my keyboard, so I can't enter any commands or do anything other than a hard reboot.  I've searched around and found other people with the whole "No resume image..." issue but they have been able to at least log-in.  

Thanks, I hope someone can help!
If you didn't get a dialog to launch other stuff such as mythtv configuration, something crashed (silently it would appear).

Either look at /var/log/installer/syslog of your target system or /var/log/syslog in the LiveCD right after running a failed install.

---

### Post by Crusty Juggler on 2008-05-07
I've installed on two different CDs now, without getting any prompt for the configuration. 

Should I download a new ISO?

---

### Post by ozybushwalker on 2008-05-07
I've had terrible troubles trying to install Mythbuntu 8.04 on two different systems, one of which successfully ran Mythbuntu 7.10. 
On one system booting the LiveCD resulted in a hung system. I was able to work around that by booting into single user mode and then starting the "startup" programs individually by shell commands. See [URL="https://bugs.launchpad.net/bugs/204057"]
https://bugs.launchpad.net/bugs/204057[/URL] for a description of what I did. Then when I saw the desktop I clicked on the install and when that seemed to complete I rebooted and ended up with a system which wasn't usable - it hung just like the LiveCD boot.

On the other system the LiveCD only occasionally booted to the first splash screen (the one on which you can select recovery mode, memtest, etc). Then I figured out a way to boot more successfully and installed (standard installation) a few times but each time the installer just quietly disappeared before reporting completion. I managed to complete installation by selecting advanced mode, primary backend only. But then on booting the backend started but very quickly exited reporting a problem with BackEndServerIP. (Discussed in [URL="http://ubuntuforums.org/showthread.php?t=772092"]
http://ubuntuforums.org/showthread.php?t=772092[/URL]). The installer doesn't seem to set up a valid configuration or the procedure for establishing a valid initial configuration in uncommonly obscure, at least in some cases.

The two systems on which I have tried to install Mythbuntu 8.04 both have GA-PCV2 motherboards, 512MB RAM. One has a 800MHz VIA C3 CPU and the other a 1GHz VIA C3 CPU.

---

### Post by superm1 on 2008-05-07
Crusty Juggler,

If this does boil down to be another installer issue (which is sounds that it might be), after we see some logs, we can see what's really happening.

---

### Post by ozybushwalker on 2008-05-07
I took a look at the syslog file for the last install I did - an install which reported completion. A considerable portion of the syslog was taken up with multiple reports:

```

May  7 09:07:45 ubuntu ubiquity: perl: warning: Setting locale failed.
May  7 09:07:45 ubuntu ubiquity: perl: warning: Please check that your locale settings:
May  7 09:07:45 ubuntu ubiquity: ^ILANGUAGE = "en_AU.UTF-8",
May  7 09:07:45 ubuntu ubiquity: ^ILC_ALL = (unset),
May  7 09:07:45 ubuntu ubiquity: ^ILC_CTYPE = "C",
May  7 09:07:45 ubuntu ubiquity: ^ILC_COLLATE = "C",
May  7 09:07:45 ubuntu ubiquity: ^ILANG = "en_AU.UTF-8"
May  7 09:07:45 ubuntu ubiquity:     are supported and installed on your system.
May  7 09:07:45 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").
May  7 09:07:46 ubuntu ubiquity: perl: warning: Setting locale failed.
May  7 09:07:46 ubuntu ubiquity: perl: warning: Please check that your locale settings:
May  7 09:07:46 ubuntu ubiquity: ^ILANGUAGE = "en_AU.UTF-8",
May  7 09:07:46 ubuntu ubiquity: ^ILC_ALL = (unset),
May  7 09:07:46 ubuntu ubiquity: ^ILC_CTYPE = "C",
May  7 09:07:46 ubuntu ubiquity: ^ILC_COLLATE = "C",
May  7 09:07:46 ubuntu ubiquity: ^ILANG = "en_AU.UTF-8"
May  7 09:07:46 ubuntu ubiquity:     are supported and installed on your system.
May  7 09:07:46 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").

```

I had set the time zone to Australia/Brisbane.

---

### Post by Crusty Juggler on 2008-05-07
> **ozybushwalker said:**
> I took a look at the syslog file for the last install I did - an install which reported completion. A considerable portion of the syslog was taken up with multiple reports:

```

May  7 09:07:45 ubuntu ubiquity: perl: warning: Setting locale failed.
May  7 09:07:45 ubuntu ubiquity: perl: warning: Please check that your locale settings:
May  7 09:07:45 ubuntu ubiquity: ^ILANGUAGE = "en_AU.UTF-8",
May  7 09:07:45 ubuntu ubiquity: ^ILC_ALL = (unset),
May  7 09:07:45 ubuntu ubiquity: ^ILC_CTYPE = "C",
May  7 09:07:45 ubuntu ubiquity: ^ILC_COLLATE = "C",
May  7 09:07:45 ubuntu ubiquity: ^ILANG = "en_AU.UTF-8"
May  7 09:07:45 ubuntu ubiquity:     are supported and installed on your system.
May  7 09:07:45 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").
May  7 09:07:46 ubuntu ubiquity: perl: warning: Setting locale failed.
May  7 09:07:46 ubuntu ubiquity: perl: warning: Please check that your locale settings:
May  7 09:07:46 ubuntu ubiquity: ^ILANGUAGE = "en_AU.UTF-8",
May  7 09:07:46 ubuntu ubiquity: ^ILC_ALL = (unset),
May  7 09:07:46 ubuntu ubiquity: ^ILC_CTYPE = "C",
May  7 09:07:46 ubuntu ubiquity: ^ILC_COLLATE = "C",
May  7 09:07:46 ubuntu ubiquity: ^ILANG = "en_AU.UTF-8"
May  7 09:07:46 ubuntu ubiquity:     are supported and installed on your system.
May  7 09:07:46 ubuntu ubiquity: perl: warning: Falling back to the standard locale ("C").

```

I had set the time zone to Australia/Brisbane.

I really hope that's not the issue...  I'm in Brisbane too.

Superm1- I'll get you the syslog info tonight, I'm currently at work.

---

### Post by Crusty Juggler on 2008-05-08
> **superm1 said:**
> Crusty Juggler,

If this does boil down to be another installer issue (which is sounds that it might be), after we see some logs, we can see what's really happening.

Okay, ran a new install with a newly dl'd and burnt iso. Same story.  Contents of livecd /var/log/syslog are attached.

---

### Post by superm1 on 2008-05-08
> **Crusty Juggler said:**
> Okay, ran a new install with a newly dl'd and burnt iso. Same story.  Contents of livecd /var/log/syslog are attached.
OK - 

It's something to do with your remote and/or transmitter.

You either didn't fully define the selections or you chose something that wasn't well tested that is causing crashes:

May  8 14:43:03 ubuntu python: Exception during installation:
May  8 14:43:03 ubuntu python: Traceback (most recent call last):
May  8 14:43:03 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 365, in <module>
May  8 14:43:03 ubuntu python:     install.run()
May  8 14:43:03 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 152, in run
May  8 14:43:03 ubuntu python:     self.configure_ir()
May  8 14:43:03 ubuntu python:   File "/usr/share/ubiquity/mythbuntu_install.py", line 284, in configure_ir
May  8 14:43:03 ubuntu python:     self.lirc.set_device(ir_device,"transmitter")
May  8 14:43:03 ubuntu python:   File "/var/lib/python-support/python2.5/mythbuntu_common/lirc.py", line 134, in set_device
May  8 14:43:03 ubuntu python:     self.transmitter_modules=device["transmitter_modules"]
May  8 14:43:03 ubuntu python: KeyError: 'transmitter_modules'
May  8 14:43:03 ubuntu python: 
May  8 14:43:03 ubuntu ubiquity[9932]: debconffilter_done: Install (current: None)
May  8 14:43:03 ubuntu ubiquity[9932]: Exception in GTK frontend (invoking crash handler):
May  8 14:43:03 ubuntu ubiquity[9932]: Traceback (most recent call last):
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/lib/ubiquity/bin/ubiquity", line 229, in <module>
May  8 14:43:03 ubuntu ubiquity[9932]:     main()
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/lib/ubiquity/bin/ubiquity", line 224, in main
May  8 14:43:03 ubuntu ubiquity[9932]:     install(args[0])
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/lib/ubiquity/bin/ubiquity", line 68, in install
May  8 14:43:03 ubuntu ubiquity[9932]:     ret = wizard.run()
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 259, in run
May  8 14:43:03 ubuntu ubiquity[9932]:     self.progress_loop()
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/lib/ubiquity/ubiquity/frontend/mythbuntu_ui.py", line 337, in progress_loop
May  8 14:43:03 ubuntu ubiquity[9932]:     (ret, realtb))
May  8 14:43:03 ubuntu ubiquity[9932]: RuntimeError: Install failed with exit code 1
May  8 14:43:03 ubuntu ubiquity[9932]: Traceback (most recent call last):
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 365, in <module>
May  8 14:43:03 ubuntu ubiquity[9932]:     install.run()
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 152, in run
May  8 14:43:03 ubuntu ubiquity[9932]:     self.configure_ir()
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/usr/share/ubiquity/mythbuntu_install.py", line 284, in configure_ir
May  8 14:43:03 ubuntu ubiquity[9932]:     self.lirc.set_device(ir_device,"transmitter")
May  8 14:43:03 ubuntu ubiquity[9932]:   File "/var/lib/python-support/python2.5/mythbuntu_common/lirc.py", line 134, in set_device
May  8 14:43:03 ubuntu ubiquity[9932]:     self.transmitter_modules=device["transmitter_modules"]
May  8 14:43:03 ubuntu ubiquity[9932]: KeyError: 'transmitter_modules'
May  8 14:43:03 ubuntu ubiquity[9932]: 

What specifically did you pick?  Please try an install with no transmitter selected.  (You can add it later)

---

### Post by Crusty Juggler on 2008-05-08
The remote I have is the WinTV 2000H and I wasn't sure what transmitter to choose (I assumed the transmitter is the IR device that plugs into the card to receive the remote signals), so I selected Custom and used the generic transmitters.xxxx (sorry, I can't remember the extension off the top of my head).  

Should I install again excluding both the remote and transmitter or just the transmitter?

---

### Post by Weidbrewer on 2008-05-09
> **Crusty Juggler said:**
> 

If I reboot and take out the bootable CD, it goes through the whole splash screen but then I get the following: 

```
Starting up...
Loading, please wait...
kinit: name_to_dev_t (/dev/disk/by-uuid/b4626e4c-0678-422f-81cc-e8398a0feb5d) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/b4626e4c-0687-422f-81cc-e8398a0feb5d
kinit: No resume image, doing normal boot...

Ubuntu 8.04 dell-desktop tty1

dell-desktop login:
```



This thread is pertinent to my interests.  I had the same install problem on a machine I've been trying to set up.  It's older equipment (for a frontend) and i can't help but wonder if that might be part of the problem.  Well, at least until I read a few threads this morning and see that others are having problems as well.

In regular 8.04 with MythTV frontend installed, it locks/crashes whenever I try to play something from the backend.  Last night, I installed Mythbuntu with the above error.


As for the "Out of Range" error someone mentioned above, this is something that solved that error for me in the past:  [http://www.hotubuntunews.com/blog_3.shtml](http://www.hotubuntunews.com/blog_3.shtml)

---

### Post by Weidbrewer on 2008-05-10
I have solved my issues.  I did a fresh install of Ubuntu 8.04, then installed Mythbuntu through the Control Center.  I had had some networking errors, but that actually seemed to be caused by the ATI driver - but that's another story.  The important part is:  My entire myth network is now up and running.

---

### Post by Crusty Juggler on 2008-05-11
Excluding the IR Transmitter from my install solved the issue of not being able to configure MythTV and the whole inability to sign in issue.

I've spent all night getting my Broadcom 4318 wireless card working...

Next is getting my HDTV to display to work...

Then is actually setting up MythTV and my capture card...

As great as it is to get something working, sometimes these things can get a bit overwhelming.

Marking thread as solved (oops, I would if I could), and thank you, Superm1!

---

### Post by timkeen on 2008-07-14
ozybushwalker, doesn't look like anyone addressed your post about not being able to install 8.04 on a machine where 7.10 worked.  You have VIA C3 processors in both of your machines.  I too had a machine with a C3 processor which ran 7.10 just fine, and would install 8.04, but not run it.  Seems there's a *feature* in the code as compiled in 8.04.  Google VIA C3 and CMOV, and you can read all about it.  But basically, Intel included an OPTIONAL instruction (CMOV, or conditional move) in their 686 instruction set, and VIA opted not to implement it (it is optional, after all).  The GCC compilers, when run with 686 optimization flags set, don't include additional logic to check for the availability of this instruction before trying to call it.  It just assumes all 686-compatible processors will have it.  The cpu does, in fact, report that the instruction is not available, but code compiled with 686 flags doesn't check, and so the code abends.

You can still "roll your own" by pulling down the Myth source and compiling on your own, sans optimization flags, but Mythbuntu 8.04 as compiled and delivered, won't work on your C3.  Bummer, I know.  I love these chips, too.

---

