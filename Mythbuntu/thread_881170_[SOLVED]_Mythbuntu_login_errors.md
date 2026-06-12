---
title: "[SOLVED] Mythbuntu login errors"
date: 2008-08-05
forum: Mythbuntu
---

### Post by dmdbdd on 2008-08-05
Good afternoon:

RE: Mythbuntu 8.04.1

When I login, I get 14 screens of the following error:

  "-bash: /dev/null: Permission denied"

OK, so now I try to start MythTV

  "sudo mythtv"

I get the following error:

  "mythtv: cannot connect to x server"

Well, let's try to start x server

  "sudo startx"

I get the x server window, however my mouse is frozen.

I'm attaching a copy of /var/log/Xorg.0.log. Perusing
through this file, it appears the there might be a problem
with my AGP video card and the OS.

Can anyone verify this or tell what the problem is?

Regards,

dmdbdd

---

### Post by Lester_Burnham on 2008-08-06
Can you get to a command prompt and make a backup of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then open your xorg.conf and delete everything in it
```
sudo nano /etc/X11/xorg.conf
```
when finished, hit ctrl+X, then Y then ENTER to save.
Reboot and see if things are detected enough to get back in.

---

### Post by dmdbdd on 2008-08-06
Good morning Lester:

Thanks for responding.

I tried your suggestions and got the exact same results.

MythTV can't find x server. When I manually start x server my mouse is dead.

Regards,

dmdbdd

---

### Post by dmdbdd on 2008-08-06
Good afternoon:

OK, just for kicks, I downloaded, burned and booted the Ubuntu 8.04.1 CD (no Myth). It booted just fine, although there were a couple of errors messages just prior to the desktop loading.

So, what does this mean? I believe that it verifies that I don't have a Linux hardware problem. At this point from my experience with software, I would say that the Mythbuntu distro has one or more bugs.

Should this problem be reported as a bug? Where do I go from here?

Regards,

dmdbdd

---

### Post by Lester_Burnham on 2008-08-06
Hi,

What are your hardware details? It will help others reading this thread also.

Lester

---

### Post by nickrout on 2008-08-06
> **dmdbdd said:**
> Good afternoon:

RE: Mythbuntu 8.04.1

When I login, I get 14 screens of the following error:

  "-bash: /dev/null: Permission denied"

OK, so now I try to start MythTV

  "sudo mythtv"

I get the following error:

  "mythtv: cannot connect to x server"

Well, let's try to start x server

  "sudo startx"

I get the x server window, however my mouse is frozen.

I'm attaching a copy of /var/log/Xorg.0.log. Perusing
through this file, it appears the there might be a problem
with my AGP video card and the OS.

Can anyone verify this or tell what the problem is?

Regards,

dmdbdd

OK so I assume you got mythbuntu installed ok. 

you don't start mythtv by running ```
sudo mythtv
```. 

When you say "log in" do you mean that you are logging into a console screen or to the gdm login screen? You shouldn't need to log in. The usual behaviour is that X is started, and the user you set up on install is logged in automatically and then mythfrontend is run. Also you don't start X with startx, if X isn't starting automatically then something is really up, but the correct way is ```
sudo /etc/init.d/gdm restart
```

---

### Post by dmdbdd on 2008-08-07
Good morning guys:

OK, to answer Nickrout's questions, yes I got Mythbuntu installed OK. What I mean by 'logging in', is that after the boot up process finishes barfing all over itself with all of the previously detailed error messages, I get the terminal command line Login prompt - 'dmdbdd Login:'. I'm guessing that is what you refer to as the 'console screen'. You'll have to forgive me, as I'm new to all of this Linux lingo. No mythfrontend is running here!

When I execute the command 'sudo /etc/init.d/gdm restart' as you suggested, I get the following:

    *Stopping GNOME Display Manger... [OK]
    *Starting GNOME Display Manger... [OK]

And now I'm back to the terminal command line prompt again.

As Lester_Burnham suggested here are my hardware details:
[INDENT]PSU: JGE ATX-450W

MB: Intel D875PBZ

CPU: Pentium 4 (2.4GHz/512/800)

RAM: Corsair TWINX 256MB PC3200 DDR 400MHz (2x 256) 
         Corsair TWINX 2048MB PC3200 DDR 400MHz (2x 1024)

HDD: Quantum Fireball EX5.1A  5.1GB PATA (Mythbuntu installed)
         Seagate Barracuda ST380013AS 80GB SATA-150 (WinXP installed -          60 GB reserved for Myth backend)

Sound card: Turtle Beach Santa Cruz

Video card: Sapphire Radeon 9600 Atlantis AGP 256MB DDR V/D/VO

Network Card:  Buffalo WLI2-PCI-G54S IEEE 802.11b/g 32-Bit PCI Bus Wireless-G

CD/DVD: Sony DRU840A EIDE 20x DVD+/-RW

Tuner Card: Dvico FusionHDTV 5 RT Gold

Remote: FusionREMOTE
[/INDENT]

---

### Post by dmdbdd on 2008-08-08
This issue has been resolved - thanks to everyone who tried to help :)
 
 OK, out of shear desperation, I elected to employ an old mainframe (most probably don't remember mainframes) trick that sometimes worked. I took off all my cloths and danced naked around the machine while all the time waving a rubber chicken as I did yet another reinstall.
 
 Seriously, I did a complete reinstall taking all of the defaults. MythTV now boots, although so far the only thing that works is the CD player using xine. So, I'll have to address the problems one at a time in separate threads, after I tinker with it some more.

Regards,

dmdbdd

---

