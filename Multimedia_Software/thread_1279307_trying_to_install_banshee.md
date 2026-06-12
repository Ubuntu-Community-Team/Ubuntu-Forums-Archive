---
title: "trying to install banshee"
date: 2009-09-30
forum: Multimedia Software
---

### Post by blackmamba123 on 2009-09-30
I'm trying to install Banshee so I can update my ipod. When at their site ( [https://edge.launchpad.net/~banshee-team/+archive/ppa](https://edge.launchpad.net/~banshee-team/+archive/ppa) ) it tells me to enter the APT line below, but it doesn't tell me what the APT line is. Please help!

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
Here goes:
 
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) 
 
see ya....

---

### Post by blackmamba123 on 2009-09-30
sorry, im pretty dumb when it comes to these things, could you explain to me what im looking for in the links? it seems like i keep clicking the links and it keeps pulling up more and more options to choose from

---

### Post by pawhtiobo on 2009-09-30
HI :)
 
Here nobody is dumb :D...no silly questions...we are all equal :)
 
Those lines are to be added to your sources lists, this way banshee will be present in the package manager e can be automaticly updated using the Ubuntu update.
 
Just do as the page says:
 
This PPA contains the latest stable debs of Banshee for Ubuntu. To install Banshee, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
 
deb [[COLOR=#444444]http://ppa.launchpad.net/banshee-team/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu") 
 
deb-src [[COLOR=#444444]http://ppa.launchpad.net/banshee-team/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu") 
 
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "banshee" from Synaptic, or using the command below:
sudo apt-get install banshee
 
See ya...

---

### Post by Yellow Pasque on 2009-09-30
Those are the APT links you need in Step 4. Copy and paste them.

---

### Post by blackmamba123 on 2009-09-30
ohhhhhh!!! haha thanks a bunch!

---

### Post by blackmamba123 on 2009-09-30
when i tried to copy/paste the debs i got this error: 

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

it also says in a text box : " Some index files failed to download, they have been ignored, or old ones used instead."

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
You can install this:
 
[https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9)
 
In the apllications -> third party source, you can add directly the Banshee repository.
 
[IMG]http://farm4.static.flickr.com/3543/3358473903_1061518d55.jpg[/IMG]
 
see ya...

---

### Post by blackmamba123 on 2009-09-30
when i clicked that link i didnt see a download icon or anything, so i clicked the "project: ubuntu tweak" link and tried figuring it out from there but i dont think i did it right. but going from what your saying, how do i add directly the repository

---

### Post by pawhtiobo on 2009-10-01
[SIZE=2]Hi :)

The link i posted [https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9) in the bottom you have the files for download in the section that says "[/SIZE][SIZE=2]**Download files for this release**", just choose yours and install it.
The other way add it directly to the repository is the previous posts or:

The following commands are use to install Banshee in Ubuntu, launch the console and:

Code:

**sudo gedit /etc/apt/sources.list **and add the following lines to the file:

[U]deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main[/U]

then,

[B]sudo apt-get update

[/B]and
[B]sudo apt-get install banshee
[/B]
I hope this helps :)


[/SIZE] [B]
[/B]

---

### Post by blackmamba123 on 2009-10-01
pawhtiobo thanks for your continued patience and assistance. i am running ubuntu gnome and didnt see an download option for my version, so i went with the most popular download (jaunty i386). it then gave me this error: 

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

i then went to system-admin-synaptic manager and once it opened i got this error:

E: Type 'ted' is not known on line 49 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

any ideas?

---

### Post by pawhtiobo on 2009-10-01
Hi :)

No problem man, we are here to help :)

First question? Which version of ubuntu are you running?

Can you paste in the next post, the contents of the sources.list, it says you have an error in line 49...i need to see it plz :)

see ya...

---

### Post by blackmamba123 on 2009-10-01
i think im running ubuntu-jaunty-jakelope (i saw the right download i needed from that list but it still errored)... when i put the sudo gedit/etc/apt/sources.list this is what it pulls up: 

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restric
ted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu)

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
I found the error :D
 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [[COLOR=#444444]http://help.ubuntu.com/community/UpgradeNotes[/COLOR]]("http://help.ubuntu.com/community/UpgradeNotes") for how to upgrade to
# newer versions of the distribution.
 
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty main restricted
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates main restricted
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty universe
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty universe
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates universe
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty multiverse
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty multiverse
deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates multiverse
deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-backports main restricted universe multiverse
# deb-src [[COLOR=#444444]http://us.archive.ubuntu.com/ubuntu/[/COLOR]]("http://us.archive.ubuntu.com/ubuntu/") jaunty-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [[COLOR=#444444]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") jaunty partner
# deb-src [[COLOR=#444444]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") jaunty partner
 
**[COLOR=blue]deb [/COLOR]**[**[COLOR=blue]http://security.ubuntu.com/ubuntu[/COLOR]**]("http://security.ubuntu.com/ubuntu")**[COLOR=blue] jaunty-security main restric[/COLOR]**
**[COLOR=blue]ted[/COLOR]**
deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") jaunty-security main restricted
deb [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") jaunty-security universe
deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") jaunty-security universe
deb [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") jaunty-security multiverse
deb-src [[COLOR=#444444]http://security.ubuntu.com/ubuntu[/COLOR]]("http://security.ubuntu.com/ubuntu") jaunty-security multiverse
**[COLOR=blue]deb [/COLOR]**[**[COLOR=blue]http://ppa.launchpad.net/banshee-team/ppa/ubuntu[/COLOR]**]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu")**[COLOR=blue] deb-src [/COLOR]**[**[COLOR=blue]http://ppa.launchpad.net/banshee-team/ppa/ubuntu[/COLOR]**]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu")
 
The lines that are wrong are in bold:
 
the first one "**ted**" should be in the line above to complete the word "restricted"
 
The last line sould be like this:
 
**deb **[[COLOR=#444444]**http://ppa.launchpad.net/banshee-team/ppa/ubuntu**[/COLOR]]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu")
**deb-src **[[COLOR=#444444]**http://ppa.launchpad.net/banshee-team/ppa/ubuntu**[/COLOR]]("http://ppa.launchpad.net/banshee-team/ppa/ubuntu")
 
You can also remove the **#** from this to lines to enable them:
 
# deb [[COLOR=#444444]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") jaunty partner
# deb-src [[COLOR=#444444]http://archive.canonical.com/ubuntu[/COLOR]]("http://archive.canonical.com/ubuntu") jaunty partner
 
See ya...

---

### Post by blackmamba123 on 2009-10-01
awesome! i made the fixes, tried installing again, and got an error still. so i went to system- admin- synaptic package manager and it gave me this error:

E: Malformed line 54 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

how do i correct line 54?

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
Can you please paste the new lines here :)
 
see ya...

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
I was checking my sources.list, and i realize that the banshee repository is not in it, it is in a separated folder, maybe this is the reason for the last error about line 54... my **banshee.list** is located at **/etc/apt/sources.list.d** and inside exists a **banshee.list** (text file) with this line inside:
 
[http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) jaunty main 
 
Maybe the best way to solve your issue is to delete the last two lines related to banshee from the **sources.list**, and use the **Ubuntu Tweak** to add them automatically, or to use the utility in the administration menu of Ubuntu...then tell us how it went :)
 
see ya...

---

### Post by mc4man on 2009-10-01
The main issue here is that when copying the lines from the ppa you're not first **expanding the drop down and picking jaunty**
the proper lines should look like this (for jaunty), noting that these are 2 separate lines
The 2nd line is only needed if you intend to build the sources, the first line will be sufficent to get banshee

```
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu jaunty main 

```

Edit : already noted above

---

### Post by blackmamba123 on 2009-10-01
i made the fix and got this error:

E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
Just dowload it again:
 
[http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb](http://launchpad.net/ubuntu-tweak/0.4.x/0.4.9/+download/ubuntu-tweak_0.4.9-1~jaunty1_i386.deb)
 
and choose reinstall.
 
Hope it helps :)
 
[[]]

---

### Post by blackmamba123 on 2009-10-01
i got this error:

could not open ubtuntu tweak ect ect ect.. "the package might be corrupted or you are not allowed to open the file. check the permissions of the file"

---

### Post by pawhtiobo on 2009-10-01
Hi :)
 
Let's try another thing, try to locate in the synaptic package manager Unbuntu Tweak and do a complete remove, then install again the package you download...or
type the following in terminal:


Code:
 sudo apt-get remove --purge ubuntu-tweak
 
see ya...

---

### Post by blackmamba123 on 2009-10-01
when i open the synaptic manager i get this error:

E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

as soon as i cancle the error window or click ok, it closes the synaptic manager right away. also, at the menu ontop of my screen theres an error icon (next to my wireless icon) when i put my mouse over it it says: An error occurred, please run package manager from the right click menu or apt-get in a terminal to see what is wrong. bla bla bla bla bla, this usually means that your installed packages have unmet dependencies.

---

### Post by pawhtiobo on 2009-10-02
Hi :)

You can try this code to fix the brocken package:

sudo apt-get -f install

see ya...

---

### Post by blackmamba123 on 2009-10-02
did that and it still gave the same error.

---

### Post by blackmamba123 on 2009-10-02
ok, so i finally finished getting my music installed, and i am able to open it with banshee. so i guess i have banshee installed and it works, so i guess my problem is solved :-D however i still have all the same errors.

---

