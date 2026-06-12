---
title: "GIMP - problem with returning to stable version"
date: 2016-10-30
forum: Multimedia Software
---

### Post by dominik15 on 2016-10-30
Hello this is my first post and i have a little problem with GIMP (i hope that i choose good section of forum, if not please mods move it to good section). I wanted to check new GIMP 2.9.5 and now i can't return to stable version.
 I have this error message:

The following packages have unmet dependencies.
 gimp : Depends: libgimp2.0 (<= 2.8.18-z) but 2.9.5~20-0x0~ppa~6813dd0 is to be installed
        Depends: gimp-data (<= 2.8.18-z) but 2.9.5~20-0x0~ppa~6813dd0 is to be installed
I typed in terminal:
sudo apt install ppa-purge && sudo ppa-purge ppa:otto-kesselgulasch/gimp-edge

and now i can't install both versions of GIMP :/

If someone would tell me what to fix i will be thankful

---

### Post by ian-weisser on 2016-10-30
1) Uninstall the PPA version of Gimp. (sudo apt purge gimp, sudo apt autoremove)
2) Clean the PPA packages from your apt cache so they don't get promptly reinstalled. (sudo apt clean)
3) Delete the PPA from your sources so they don't get re-downloaded to your apt cache. (ppa-purge or a text editor)
4) Since you changed your sources, update your package database. (sudo apt update)
5) Check for the current installation candidate(s) of Gimp. (apt-cache policy gimp)
6) If the source of the candidate Gimp is the Ubuntu repos instead of a PPA, then install Gimp. (sudo apt install gimp)

---

### Post by dominik15 on 2016-10-30
i did what you told me and still have problem with installing GIMP 2.8.18:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 gimp : Depends: libgimp2.0 (<= 2.8.16-z) but 2.9.5~20-0x0~ppa~6813dd0 is to be installed
        Depends: gimp-data (<= 2.8.16-z) but 2.9.5~20-0x0~ppa~6813dd0 is to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by dominik15 on 2016-10-30
Sorry for double-post but i resolve rest of problems i ve delete those 2 libraries 
sudo aptitude purge libgimp2.0
sudo aptitude purge gimp-data 
and install Gimp from Ubuntu repo 

Thanks @ian-wesser for quick help

---

### Post by monkeybrain20122 on 2016-11-02
You should have used ppa-purge since the ppa might have upgraded other dependencies and you may encounter problems later on (e.h libpng might have been upgraded to 1.6.5 or something as required to build gimp from source)

To use ppa-purge, re-enable the ppa you want to purge if you have disabled it

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:otto-kesselgulasch/gimp-edge
```

I assume you are using the gimp-edge ppa, if not, replace it with the appropriate one. 
With ppa-purge all packages you installed from the ppa will be downgraded smartly (so repo's version of gimp will be installed if you haven't removed Gimp2.9 since Gimp 2.8 would be a downgrade)

---

