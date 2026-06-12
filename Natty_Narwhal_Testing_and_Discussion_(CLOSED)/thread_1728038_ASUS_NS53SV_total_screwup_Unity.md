---
title: "ASUS NS53SV total screwup Unity"
date: 2011-04-13
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by komasoftware on 2011-04-13
Hi,

Installed natty beta 1 without probles
Unity not showing sidebar, did a unity --reset as adviced here somewhere down this forum, no luck.
Alot of reports on crahsing components, compiz cannot be enabled.

Got alot of updates and installed them through update manager.
After reboot i get a message that my hardware is insufficient to run Unity (i know it is NOT, 8 cpu duh!), and that my desktop is switching back to default ?

Doing a unity --reset gives me this output :

koen@N53SV:~$ unity --reset
WARNING: Unity currently default profile, so switching to metacity while resetting the values
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Initializing bailer options...done
Initializing detection options...done
Initializing composite options...done
Xlib:  extension "GLX" missing on display ":0.0".
Compiz (opengl) - Fatal: Root visual is not a GL visual
Compiz (bailer) - Info: Ensuring a shell for your session

I know that other people have no issues running the same hardware... any advice ??
what is wrong ? and how do i get compiz to run ?

thx

Koen

this is what it looks like :

---

### Post by dino99 on 2011-04-13
your first problem seem to be compiz: so remove/purge into synaptic everything about compiz and unity, then reinstall compiz only and be sure you can enable it, later if you succeed you reinstall unity. Of course first check additional drivers activation before all.

Looking your snapshot: GLX extension missing
what is your graphic card and installed driver ? Seems wrongly installed.

if xorg.conf exist, remove it and let the kernel doing the job:
sudo rm /etc/X11/xorg.conf

---

### Post by komasoftware on 2011-04-13
ahhh, the story of the graphics card in the asus N53SV !

It is optimus hardware so a combination of onboard intel graphics and nvidia geforce gt540m. I know already from reading up over the last week that i will never be able to use the nvidia card running linux as optimus is not support and requires a thorough rewrite of xorg, mesa and related. 

But i know that others manage to run compiz smoothly on the intel IGP only.
My prob must be related to my xorg setup, is my guess.
Definitely the installer didnt get it right.

Purging unity, will i be left without GUI ? Any experience doing so ?

---

### Post by komasoftware on 2011-04-13
PS no xorg.conf present

---

### Post by dino99 on 2011-04-13
> **komasoftware said:**
> ahhh, the story of the graphics card in the asus N53SV !


Purging unity, will i be left without GUI ? Any experience doing so ?

no, you get the "classic" gnome2 as previouly on maverick. Is your bios giving you the choice to deactivate either igp or nvidia ? About nvidia, into synaptic, remove/purge then reinstall nvidia-current, nvidia-common, nvidia-settings

The latest choice is to work with the latest drivers from:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Dont forget to watch Asus forum and post there your questions too

---

### Post by komasoftware on 2011-04-13
marking unity and/or compiz for complete removal will also take ubuntu-desktop, empathy etc etc etc down.

---

### Post by dino99 on 2011-04-13
> **komasoftware said:**
> marking unity and/or compiz for complete removal will also take ubuntu-desktop, empathy etc etc etc down.

ubuntu-desktop is a meta package, so no worry simply reinstall the removed apps you want to use. On my system i have removed all the metapackages because i dont want/need lot of useless stuff.

---

### Post by komasoftware on 2011-04-13
> **dino99 said:**
> no, you get the "classic" gnome2 as previouly on maverick. Is your bios giving you the choice to deactivate either igp or nvidia ? About nvidia, into synaptic, remove/purge then reinstall nvidia-current, nvidia-common, nvidia-settings

The latest choice is to work with the latest drivers from:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Dont forget to watch Asus forum and post there your questions too


No option in BIOS. I know i need both drivers (intel & nvidia) to use vga_switcheroo to power down the Nvidia at the end of the day. No way to use nvidia as it is hardwired to the IGP and no direct hardware path to the display. so only optimus can do magic on this.

somehow ubuntu is using nvidia as my display card and then falls back to a safety mode since it cannot address the nvidia card.

---

### Post by komasoftware on 2011-04-13
> **dino99 said:**
> ubuntu-desktop is a meta package, so no worry simply reinstall the removed apps you want to use. On my system i have removed all the metapackages because i dont want/need lot of useless stuff.

ok, going for it. hope to be back up here soon ):P

---

### Post by dino99 on 2011-04-13
i've googled around this model but have not found many posts, so you can ask and expose your problem directly to devs:

[https://answers.launchpad.net/ubuntu/+questions](https://answers.launchpad.net/ubuntu/+questions)

or file a bug using terminal: ubuntu-bug linux
(need to create an account on launchpad first)

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by dino99 on 2011-04-13
some more findings googling around optimus: (ubuntu+optimus+graphic)

[http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)

[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

---

### Post by komasoftware on 2011-04-13
dropped to shell at startup, re-installed unity

apt-get install unity-*

and here i am :-)

---

### Post by komasoftware on 2011-04-13
still no compiz though.

desktop effects tab not there in 'Appearance'

---

### Post by cariboo on 2011-04-13
Compiz starts by default when running Unity. You may want to install compizconfig-settings-manager to access  the Unity settings.

---

### Post by Starks on 2011-04-13
Don't use vga_switcheroo with your laptop. Nothing will happen.

Use acpi_call to see if your Nvidia GPU can be turned off and test_off to actually turn it off.

---

### Post by komasoftware on 2011-04-13
did that before, and yes it is possible.
i understood that vga_switcheroo is the advised way of turning it off.
but now i see, it is meant to switch between GPUs , and that wont work indeed

---

### Post by komasoftware on 2011-04-13
> **cariboo907 said:**
> Compiz starts by default when running Unity. You may want to install compizconfig-settings-manager to access  the Unity settings.

I did but none of the modifications i make seem to make any impact... any suggestions ?

---

### Post by komasoftware on 2011-04-13
Sidebar in Unity... i understand it is somewhat early adopted and needs to grow. still some questions :


- How do I setup a launcher in the sidebar. I know it's been asked before. It works for officially installed apps by right clicking the app in the b ar and selecting 'keep in launcher'. But e.g. I start Eclipse from a terminal, then there is no such option present. Where are the config files so I might hard code my launcher ?

- How do you keep the sidebar from auto-hiding and setup transparancy for the side bar ?

thx!

---

### Post by cariboo on 2011-04-13
Create a launcher on the desktop and drag it on to the launcher, for apps that aren't Unity aware.

You can change some of the launcher settings using compizconfig-settings-manager, just click the unity icon.

Merged two threads.

---

### Post by komasoftware on 2011-04-13
> **cariboo907 said:**
> Create a launcher on the desktop and drag it on to the launcher, for apps that aren't Unity aware.

You can change some of the launcher settings using compizconfig-settings-manager, just click the unity icon.



Cool, got a launcher now for my development !! thx thx

compiz mgr : what ever i try in there, has no effect whatsoever. maybe somebody can export its settings and attach m ?

> **cariboo907 said:**
> 
Merged two threads.
 => that was confusing :o

---

### Post by donalgodon on 2011-04-15
I hope that we can somehow arrive at a simple solution that works out of the box for this entire video driver mess that Optimus has created.

I've not crossed off most of the newer laptops I was looking at because they are all plagued/blessed with Optimus graphics, including the one which started this discussion. 

There's just no better value in the SanyBridge Core i7 right now, but I refuse to use Win-doze as a matter of principle. 

I don't know where to focus my wishful thinking energy. Is this entirely nvidia's fault?

---

### Post by komasoftware on 2011-04-15
Actually, I had almost given up and worked on Win7 for a few days.... horror. Glad to be back.
And if the Optimus mess isn't bad enough, Unity proves to be anything but stable too. Hope that will improve with the final release.

The good news : the power of this Asus NS53SV is mind blowing.

---

### Post by Starks on 2011-04-15
Don't bother with Optimus.

The HP dv6t Select and Quad editions come with a Radeon 6770M and they're better than the 540M by miles. Plus, they work with the new Catalyst and Radeon drivers.

---

