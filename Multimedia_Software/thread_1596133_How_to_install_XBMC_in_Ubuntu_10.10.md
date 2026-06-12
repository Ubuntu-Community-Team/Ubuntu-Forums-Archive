---
title: "How to install XBMC in Ubuntu 10.10"
date: 2010-10-13
forum: Multimedia Software
---

### Post by stephanecharette on 2010-10-13
There is lots of confusing information on how to get XBMC installed.  I took some of the information from [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher") and figured out how to make it work in Ubuntu 10.10:

Start by running this command:

[INDENT][COLOR="DarkGreen"]sudo add-apt-repository ppa:team-xbmc[/COLOR][/INDENT]

Now click on [FONT="Courier New"][COLOR="DarkGreen"]System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software[/COLOR][/FONT].

Select the first ppa for team-xbmc, then click on "[FONT="Courier New"][COLOR="DarkGreen"]Edit...[/COLOR][/FONT]"

Change the Distribution to "[FONT="Courier New"][COLOR="DarkGreen"]lucid[/COLOR][/FONT]".  Click [FONT="Courier New"][COLOR="DarkGreen"]OK[/COLOR][/FONT].

Select the 2nd ppa for team-xbmc, and make the same the same change to "[FONT="Courier New"][COLOR="DarkGreen"]lucid[/COLOR][/FONT]".

Reload the packages, and then install "[COLOR="DarkGreen"]xbmc[/COLOR]" as well as "[COLOR="DarkGreen"]xbmc-standalone[/COLOR]".  If you want to use the command-line instead of Synaptic Package Manager to do this, here are the relevant commands:

[INDENT][FONT="Courier New"][COLOR="DarkGreen"]sudo apt-get update
sudo apt-get install xbmc xbmc-standalone[/COLOR][/FONT][/INDENT]

You should now have XBMC in [FONT="Courier New"][COLOR="DarkGreen"]Applications->Sound & Video->XBMC Media Center[/COLOR][/FONT].

---

### Post by mbryne on 2010-10-14
thanks for that, worked a treat!

---

### Post by jcer93705 on 2010-10-16
> **stephanecharette said:**
> There is lots of confusing information on how to get XBMC installed.  I took some of the information from [http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher]("http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Installing_XBMC_Ubuntu_9.10_Karmic_or_higher") and figured out how to make it work in Ubuntu 10.10:

Start by running this command:

[INDENT][COLOR="DarkGreen"]sudo add-apt-repository ppa:team-xbmc[/COLOR][/INDENT]

Now click on [FONT="Courier New"][COLOR="DarkGreen"]System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software[/COLOR][/FONT].

Select the first ppa for team-xbmc, then click on "[FONT="Courier New"][COLOR="DarkGreen"]Edit...[/COLOR][/FONT]"

Change the Distribution to "[FONT="Courier New"][COLOR="DarkGreen"]lucid[/COLOR][/FONT]".  Click [FONT="Courier New"][COLOR="DarkGreen"]OK[/COLOR][/FONT].

Select the 2nd ppa for team-xbmc, and make the same the same change to "[FONT="Courier New"][COLOR="DarkGreen"]lucid[/COLOR][/FONT]".

Reload the packages, and then install "[COLOR="DarkGreen"]xbmc[/COLOR]" as well as "[COLOR="DarkGreen"]xbmc-standalone[/COLOR]".  If you want to use the command-line instead of Synaptic Package Manager to do this, here are the relevant commands:

[INDENT][FONT="Courier New"][COLOR="DarkGreen"]sudo apt-get update
sudo apt-get install xbmc xbmc-standalone[/COLOR][/FONT][/INDENT]

You should now have XBMC in [FONT="Courier New"][COLOR="DarkGreen"]Applications->Sound & Video->XBMC Media Center[/COLOR][/FONT].

I have trouble i don't see it when u said
Now click on System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software.

Select the first ppa for team-xbmc, then click on "Edit..."

also when i do sudo apt-get install xbmc xbmc-standalone

jaime@jaime-Satellite-L505D:~$ sudo apt-get install xbmc xbmc-standalone
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Als when i do a reload on synaptic it says

---

### Post by jcer93705 on 2010-10-16
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by jcer93705 on 2010-10-16
Then i clicked on the link and haha well........ Whats wrong? Wrong url?

---

### Post by Nakaleen on 2010-10-16
> **jcer93705 said:**
> I have trouble i don't see it when u said
Now click on System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software.

Select the first ppa for team-xbmc, then click on "Edit..."

also when i do sudo apt-get install xbmc xbmc-standalone

jaime@jaime-Satellite-L505D:~$ sudo apt-get install xbmc xbmc-standalone
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


Did you have Synaptic Package Manager open when you typed that? I did and caused that error. Just close Synaptic and it works fine.

---

### Post by jcer93705 on 2010-10-16
> **Nakaleen said:**
> Did you have Synaptic Package Manager open when you typed that? I did and caused that error. Just close Synaptic and it works fine.

Nope

---

### Post by axept on 2010-10-22
"[I]Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz](http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz](http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz) 404 Not Found[/I]"


I get this too !!!! :(

Why?

---

### Post by roguebuck on 2010-10-23
> **axept said:**
> "[I]Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz](http://ppa.launchpad.net/team-xbmc/p...rce/Sources.gz) 404 Not Found
Failed to fetch [http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz](http://ppa.launchpad.net/team-xbmc/p...86/Packages.gz) 404 Not Found[/I]"


I get this too !!!! :(

Why?

same thing here, from what i can tell, its a bad url?

---

### Post by shantiq on 2010-10-23
try this?



to install xbmc

=====================


Code:
```
sudo apt-get install python-software-properties pkg-config

```Code:
```
sudo add-apt-repository ppa:team-xbmc

```found it was not happy on maverick so had to relabel to lucid in software sources

click on System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software.

Select the first ppa for team-xbmc, then click on "Edit..."

Change the Distribution to "lucid". Click OK.
Select the 2nd ppa for team-xbmc, and make the same change to "lucid".

Code:
```
sudo apt-get update

```Code:
```
sudo apt-get install xbmc xbmc-standalone

```Code:
```
sudo apt-get update

```

---

### Post by jcer93705 on 2010-10-23
> **shantiq said:**
> try this?



to install xbmc

=====================


Code:
```
sudo apt-get install python-software-properties pkg-config

```Code:
```
sudo add-apt-repository ppa:team-xbmc

```found it was not happy on maverick so had to relabel to lucid in software sources

click on System->Administration->Synaptic Package Manager->Settings->Repositories->Other Software.

Select the first ppa for team-xbmc, then click on "Edit..."

Change the Distribution to "lucid". Click OK.
Select the 2nd ppa for team-xbmc, and make the same change to "lucid".

Code:
```
sudo apt-get update

```Code:
```
sudo apt-get install xbmc xbmc-standalone

```Code:
```
sudo apt-get update

```

Thank you that did work for me :).

---

### Post by x117a on 2010-11-14
Thank You sir worked a treat!

---

### Post by Tr1p on 2010-11-15
still have the same error ...

---

### Post by Apple.boi on 2010-11-16
Don't capitalize lucid. my first try i got the same error because i like to use capitals, it's case sensitive. I did it over in all lower case and got no problem and just finished installing it. hope that helps! :)

---

### Post by iosuna86 on 2010-12-17
It worked for me too!

Thanks!

---

