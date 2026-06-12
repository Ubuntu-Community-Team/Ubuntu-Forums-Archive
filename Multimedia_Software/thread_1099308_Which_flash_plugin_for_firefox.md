---
title: "Which flash plugin for firefox?"
date: 2009-03-18
forum: Multimedia Software
---

### Post by wire42 on 2009-03-18
The Firefox "Install Missing Plugins" helper suggests the following options for playing Flash:
[LIST]
[*]Adobe Flash Player
[*]Swfdec SWF Player
[*]Gnash SWF Player
[/LIST]

Which one should I choose? Are there performance issues with the Adobe player? How do the other players compare in terms of features and functionality?

---

### Post by johnjohn2 on 2009-03-18
adobe works the best for me and is is nice to have the support for a 64 bit system at long last

---

### Post by wire42 on 2009-03-18
Looks like Adobe's player is the only one compatible with hulu.com, so that's going to have to be the choice for me, too.

I tested out the other two first, simply by installing them from the firefox plugin finder and then later removing the installed package with Synaptic. This technique avoids any possible problems with editing the plugins directory directly. The next time firefox runs after the package has been removed, it just re-prompts to find a missing plugin.

The packages use pretty obvious names: flashplugin-nonfree, swfdec-mozilla, and mozilla-plugin-gnash.

---

### Post by BillyBoy0001 on 2009-03-25
I'm new to the Linux scene and am having trouble with getting adobe flash to work with firefox. I am running Ubuntu 8.04 LTS and after downloading through adobe I chose .deb for linux 8.04. It installed the package as it said "installation complete" but how do you get it to work? I've looked in different places but can't find it anywhere. If I go to the same site again it says "reinstall?" Any help would be appreciated..

---

### Post by kiridude on 2009-03-25
Billyboy, open a terminal and type: 

sudo apt-get install flashplugin-nonfree

hit return, enter your password and you should be good to go.

---

### Post by BillyBoy0001 on 2009-03-25
I already installed the package but it still doesn't work. I've been trying to view the new trailer for Star Trek movie at
[http://www.vh1.com/partners/microsoft/playvideo.jhtml?vid=217249](http://www.vh1.com/partners/microsoft/playvideo.jhtml?vid=217249)

Like said I'm new.. Is there something else I need to point firefox to or something? The below was on the terminal screen..


Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  space-orbit-common libgnome-device-manager0 libsdl-mixer1.2 starfighter-data
  libsdl-image1.2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by BillyBoy0001 on 2009-03-25
I don't know where my manners went.. Thanks kiridude...

---

### Post by kiridude on 2009-03-25
:)

It should be automatic. Have you tried restarting your machine?

---

### Post by BillyBoy0001 on 2009-03-25
Didn't work either..

Tried some stuff from redroad55 that didn't work either. Not sure what to do next. Keep looking I guess...thanks

---

### Post by radriderx on 2009-03-25
> **BillyBoy0001 said:**
> Didn't work either..

Tried some stuff from redroad55 that didn't work either. Not sure what to do next. Keep looking I guess...thanks

Hi BillyBoy,
I had exactly the same problems as you - running Ubuntu 8.04 and the bbc iplayer doesn't work, I tried installing adobe flashplayer and although it seemed to install properly it still didn't work. Tried various things suggested on the forum to no avail and even started to think about putting XP on the machine!

As a last resort I went to FireFox missing plugins - still didn't work:confused:
Finally opened update manager to look for updates to Ubuntu and it said there were 277 updates available - went for them all (took nearly 30 minutes) restarted the machine and ........ success! BBC iplayer now working:P

Only problem now is that I've got 4 different versions of flash player on my system, so do I delete some of them or leave it alone since it is now working?

Incidently when I went to firefox 'about plugins' the flash player says shockwave flash as the player - don't know how I managed to install that:lolflag:

Hope this helps a bit

R

---

### Post by azmo35 on 2009-03-25
Hello, guys myself had this problem but i fund that many adobe flash will cause firefox goes grey not responding. What you need is shockwave flash 10.0 r22 you can check this writing on your address bar about:plugins.See my thead about flash-nonfree [here]("http://ubuntuforums.org/showthread.php?t=1094007")

---

