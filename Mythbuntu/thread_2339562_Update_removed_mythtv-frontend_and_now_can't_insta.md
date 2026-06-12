---
title: "Update removed mythtv-frontend and now can't install it."
date: 2016-10-10
forum: Mythbuntu
---

### Post by melevittfl on 2016-10-10
Hi,

Running mythbuntu 14.04. I ran "apt-get dist-upgrade" this morning and didn't notice the following:

```
The following packages will be REMOVED:
   mythgallery (0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5)
   mythmusic (0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5)
   mythtv (0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5)
   mythtv-frontend (0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5)
```

Now, if I try and install mythtv-frontend, I get:
```
myth@mythtv-front:~$ sudo apt-get install mythtv-frontend
...
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mythtv-frontend : Depends: mythtv-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

And if I try and install mythtv-frontend and mythtv-common, I get:

```
myth@mythtv-front:~$ sudo apt-get install mythtv-frontend mythtv-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mythtv-common is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mythtv-common : Breaks: mythtv-frontend (< 2:0.28.0+fixes.20161010.38d9ba2-0ubuntu0mythbuntu4) but 2:0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5 is to be installed
E: Unable to correct problems, you have held broken packages.
```

Any ideas?

---

### Post by rxm307 on 2016-10-10
Appears there are some packing issues in todays build download the builds from 7th Oct

[http://ppa.launchpad.net/mythbuntu/0.28/ubuntu/pool/main/m/mythtv/mythtv-frontend_0.28.0+fixes.20161007.8580a41-0ubuntu0mythbuntu5_amd64.deb](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu/pool/main/m/mythtv/mythtv-frontend_0.28.0+fixes.20161007.8580a41-0ubuntu0mythbuntu5_amd64.deb)
[http://ppa.launchpad.net/mythbuntu/0.28/ubuntu/pool/main/m/mythtv/mythtv-common_0.28.0+fixes.20161007.8580a41-0ubuntu0mythbuntu5_amd64.deb](http://ppa.launchpad.net/mythbuntu/0.28/ubuntu/pool/main/m/mythtv/mythtv-common_0.28.0+fixes.20161007.8580a41-0ubuntu0mythbuntu5_amd64.deb)

then run

sudo dpkg -i *.deb

Cheers,

Anthony

---

### Post by melevittfl on 2016-10-10
Hi,

Thanks! I installed the two packages manually and that seems to have worked and I'm now back to a usable system. 

Yes, the packages seem broken as I'm still getting complaints from apt-get if I tell it to update:
```
[COLOR=#000000][FONT=Menlo]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Building dependency tree       [/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]You might want to run 'apt-get -f install' to correct these.[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]The following packages have unmet dependencies:[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo] mythweb : Depends: mythtv-common (>= 2:0.28.0+fixes.20161010.7c91ab6-0ubuntu0mythbuntu5) but 2:0.28.0+fixes.20161007.8580a41-0ubuntu0mythbuntu5 is installed[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]E: Unmet dependencies. Try using -f.[/FONT][/COLOR]

```

If I try using -f, it wants to remove mythtv-frontend again. 

Thanks again for your help.

---

### Post by gottabefoss on 2016-10-10
Came to post this bug. 

Saw what the upgrade was going to do and declined the update. And then came here to post about the package error!

EDIT: posted bug report on launchpad: [https://bugs.launchpad.net/mythbuntu/+bug/1632015](https://bugs.launchpad.net/mythbuntu/+bug/1632015)

---

### Post by marcw on 2016-10-10
> **gottabefoss said:**
>  posted bug report on launchpad: [https://bugs.launchpad.net/mythbuntu/+bug/1632015](https://bugs.launchpad.net/mythbuntu/+bug/1632015)

Thanks.  Saved me some time.

---

### Post by thomi_ch on 2016-10-12
check build status for mythtv 0.28: [https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28](https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28)

as soon, as it is rebuild, we can re-install mythtv-frontend ;)

---

### Post by roburk on 2016-10-12
Any idea when it's due?

---

### Post by mtbdrew on 2016-10-12
> **roburk said:**
> Any idea when it's due?


Ya nothing like having a bunch of shows recorded that I can't watch because the frontend was removed!

---

### Post by tgm4883 on 2016-10-12
New builds are out now

---

### Post by thomi_ch on 2016-10-13
confirmed, mythtv-frontend back and running..
check also bug comments [https://bugs.launchpad.net/mythbuntu/+bug/1632015](https://bugs.launchpad.net/mythbuntu/+bug/1632015) and package status [https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28](https://launchpad.net/~mythbuntu/+archive/ubuntu/0.28)

---

### Post by roburk on 2016-10-13
> **mtbdrew said:**
> Ya nothing like having a bunch of shows recorded that I can't watch because the frontend was removed!

Heh, no doubt! Fortunately my primary FE is Kodi, I only really use the mythtv frontend for testing and stuff on the backend.
 
Glad to see it’s back though!... Particularly as when it happened I just naturally assumed it was something I had broken :D

---

