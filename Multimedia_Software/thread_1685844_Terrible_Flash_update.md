---
title: "Terrible Flash update"
date: 2011-02-11
forum: Multimedia Software
---

### Post by Swagman on 2011-02-11
What the heck is wrong with the latest (32 bit) Flash update ?

I have ** NEVER** had a single issue with flash but since this latest update it regularly crashes... glitches, all sorts of weird stuff.

I've used synaptic to completely remove it.. rebooted.. installed it. That seemed to cure it but after a couple of minutes playing it's glitching again.

Anyone else getting this problem and does anyone know how to cure it ?

**Yes** I'm using a nVidia GPU (8800GT)

[edit]

Is there anyway to roll back - reinstall the earlier version ?

---

### Post by sandfire on 2011-02-11
I have had problems too, since the last update.

Prior to that I could log into youtube and view videos with Firefox. Now I cannot.

I have to use Google Chrome instead.

Has anyone got any answers or possible solutions, please?

Cheers,

Sandfire

---

### Post by TBABill on 2011-02-11
I'm not sure if something is borked in the Flash available in the repos, but I'm assuming that's the plugin causing you issues. Can you install Flash Aid from the web? If you aren't familiar, it's an extension that removes your current flash plugin and gets the latest from Adobe.

---

### Post by RedSingularity on 2011-02-11
I understand its a 32bit upgrade, but what system architecture are you running?

---

### Post by beew on 2011-02-11
> **TBABill said:**
> I'm not sure if something is borked in the Flash available in the repos, but I'm assuming that's the plugin causing you issues. Can you install Flash Aid from the web? If you aren't familiar, it's an extension that removes your current flash plugin and gets the latest from Adobe.

+1 to that. Lovinglinux rules. :)
[https://addons.mozilla.org/af/firefox/addon/flash-aid/](https://addons.mozilla.org/af/firefox/addon/flash-aid/)

---

### Post by msmx5s on 2011-02-11
WTF is going on?

I've done some updates in the last few days, and now Flash Player does not work at all.

Wherever it is needed it says "Missing Plug-in"

This is a nightmare!

---

### Post by Sylos on 2011-02-11
What version of flash it that is installed?

I only ask as I was recently made aware of a new flash version out that supports hardware acceleration for NVIDIA cards via the VDPAU lib. Might it be teething problems with this that are the source of the issue?

---

### Post by RedSingularity on 2011-02-11
> **msmx5s said:**
> WTF is going on?

I've done some updates in the last few days, and now Flash Player does not work at all.

Wherever it is needed it says "Missing Plug-in"

This is a nightmare!


Does firefox give you an idea of what the plugin is?  IcedTea for example..?

---

### Post by msmx5s on 2011-02-11
I have no idea what the version is, but it isn't just a firefox problem. It's affected Chrome, Chromium, and Chrome Plus too.

---

### Post by msmx5s on 2011-02-11
OK I updated manually the flash player in FireFox to 10.2 R152 and now it works.

Unfortunately, I use Chrome based browsers the most, and that hasn't helped

---

### Post by msmx5s on 2011-02-11
Restarted Ubuntu after the Firefox flash update, and that solved the Chrome problems too. 

Sorted. :)

---

### Post by sandfire on 2011-02-11
> **RedSingularity said:**
> Does firefox give you an idea of what the plugin is?  IcedTea for example..?

Please excuse my ignorance. I am not in any way knowledgeable on matter Ubuntu. What I have done
is accesses add-ons in Firefox and the only reference to Flash is Shockwave Flash10.1 r999. Gnash 
0.8.8 .

My system is 32 bit Ubuntu 10.10. 

If that is enough info for someone to help me, I'd be grateful.

Sandfire

---

### Post by msmx5s on 2011-02-11
Remove that plugin, then go to a page that needs flash. I had 3 options to choose from. The 2nd one I tried worked. Sorry, I didn't notice which one it was.

---

### Post by TBABill on 2011-02-11
> **sandfire said:**
> Please excuse my ignorance. I am not in any way knowledgeable on matter Ubuntu. What I have done
is accesses add-ons in Firefox and the only reference to Flash is Shockwave Flash10.1 r999. Gnash 
0.8.8 .

My system is 32 bit Ubuntu 10.10. 

If that is enough info for someone to help me, I'd be grateful.

Sandfire
Probably can just go into Synaptic and search "GNASH", then remove it. It conflicts with Flash.

---

### Post by savaan on 2011-02-11
I'm having the same issues...but on Chromium. My wife uses Firefox and she's having the same issues. We're both on 10.10 and running the newest flash right from Adobe's site

---

### Post by Cracklepop on 2011-02-11
Are there still this many people using 32 bit gear in 2011?! 

Flash Square 64 bit is up to it's third revision now, and is working perfectly for me.

---

### Post by RedSingularity on 2011-02-11
> **sandfire said:**
> Please excuse my ignorance. I am not in any way knowledgeable on matter Ubuntu. What I have done
is accesses add-ons in Firefox and the only reference to Flash is Shockwave Flash10.1 r999. Gnash 
0.8.8 .

My system is 32 bit Ubuntu 10.10. 

If that is enough info for someone to help me, I'd be grateful.

Sandfire


Try this,

sudo apt-get autoremove --purge gnash

Then see if the problem is solved.

---

### Post by hansdown on 2011-02-11
Hi sandfire.

Click 

system> administration> synaptic package manager.

Install

```
flashplugin-installer
```

Thanks to lovinglinux.

It will remove any unwanted plugins, and install the correct one for your system.

---

### Post by garagepoort on 2011-02-11
> **TBABill said:**
> I'm not sure if something is borked in the Flash available in the repos, but I'm assuming that's the plugin causing you issues. Can you install Flash Aid from the web? If you aren't familiar, it's an extension that removes your current flash plugin and gets the latest from Adobe.

Thank you!! This fixed not only firefox but chrome also. I was having some serious trouble getting this to work again. 
Silly me not checking the forum first.
Hats off to you kind sir :)

David

---

