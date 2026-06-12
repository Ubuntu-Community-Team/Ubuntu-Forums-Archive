---
title: "Inputstream not working with Kodi 18.6"
date: 2023-02-06
forum: Multimedia Software
---

### Post by vnandi2 on 2023-02-06
I have an old machine with Ubuntu 20.04 it has an old onboard nvidia ion card i am using nvidia 340 driver because of this i am stuck with kernel 5.4.0-137.
The problem i have is that i want to use Kodi to watch Disney+ the only working version is 18.6 which is missing an addon called InputStream Adaptive so cant watch anything on Disney+
I know kodi 19.1 works with Disney+
i have it another partition with a Debian install. Tried to install other Kodi versions from flatpak from ppa xbmc current nightly version even tried debian versions all of them give me black screen the flatpak version says could not initialize Gui.
Flatpak version of Kodi dosnt works on Debian 11 either. What could be the problem? I read somewhere that Nexus has newer python version but the flatpak supposed to be picked up on that or i am wrong? Need a newer kernel to run kodi 19.x with ubuntu 20.04? I read that someone patched the 340 nvidia driver so a newer kernel could utilize it.Would that make Ubuntu 20.04 compatible with Kodi 19.x- 20.x?

---

### Post by monkeybrain20122 on 2023-02-07
How did you install kodi? The official repo's version is crippled [https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux#Installing_Kodi_on_Ubuntu-based_distributions_with_Team_Kodi_PPA](https://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux#Installing_Kodi_on_Ubuntu-based_distributions_with_Team_Kodi_PPA)
You have to get it from kod team's [ppa]("https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa").

---

### Post by vnandi2 on 2023-02-07
yes i tried the PPA version of Kodi it says :
ERROR: Unable to create GUI. Exiting

don't even create a log file

if i comment out from .bashrc the following
 export DISPLAY=localhost
it starts but just blank sreen.
Only version 18.6 works which
part of the distro but that has no
inputstream

---

