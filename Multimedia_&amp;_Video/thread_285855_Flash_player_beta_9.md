---
title: "Flash player beta 9"
date: 2006-10-27
forum: Multimedia &amp; Video
---

### Post by digimars on 2006-10-27
I installed the Flash player 9 beta to my /usr/lib/mozilla/plugins directory, but when I check about:plugins, it doesn't show up.  So I copied it to my home/me/.mozilla/plugins directory and it doesn't work from there either.  I even restarted the computer just for good measure but flash just doesn't show up as a plugin.  Thoughts?

---

### Post by pay on 2006-10-27
```
sudo aptitude install flashplugin-nonfree
sudo update-flashplugin
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/ 
```

---

### Post by digimars on 2006-10-27
thanks, that worked.  Now it shows up in the plugins.  But a brand new problem for me (it appears that others have it too now) is that when I go to a flash enabled site, firefox immediately crashes.

---

### Post by pay on 2006-10-27
hmm, I've always had a problem with the Ubuntu's version of firefox for some reason. I use the Mozilla's version.

---

### Post by digimars on 2006-10-27
I cleared it up by changing my bit depth in xorg.conf from 16 to 24.  Odd, but that's all that it took to fix it.

---

### Post by Bosambo on 2006-10-28
I'm getting the following...any one have a clue what it means?
```
tes@tes-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/15.9kB of archives.
After unpacking 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 133654 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.68~ubuntu3_i386.deb) ...
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...  done.
return: 212: Illegal number: -1

```

---

### Post by IusedTObeSOMEONEelse on 2006-10-28
how do I get Iceweasel to use flashplayer 9 Beta? I used the codes provided in this thread but when Iceweasel searches for plugin's only gnash shows up

---

### Post by pay on 2006-10-28
Try putting it in /path/to/iceweasel/plugins

---

### Post by IusedTObeSOMEONEelse on 2006-10-28
Thanks for your reply pay.Being the **'Dumb Blonde'** that I am, how and where do I find this path thingy? :confused:

---

### Post by blitzer on 2006-10-28
> **Bosambo said:**
> I'm getting the following...any one have a clue what it means?
```
tes@tes-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/15.9kB of archives.
After unpacking 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 133654 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_7.0.68~ubuntu3_i386.deb) ...
Setting up flashplugin-nonfree (7.0.68~ubuntu3) ...
Downloading...  done.
return: 212: Illegal number: -1

```

Same here  :-k

---

### Post by pay on 2006-10-28
@MustangSallydd
I think it is /usr/lib/iceweasel/plugins/ (if you installed it with a .deb file or repository). If your on amd64 and installed it with automatix it's most likely in /opt/iceweasel/plugins.

---

### Post by IusedTObeSOMEONEelse on 2006-10-28
Hi pay! Thanks, but I do not seem to rmember where Iceweasel was put. I tried the /usr/lib/iceweasel/plugins, it tells me no path. How do I find where iceweasel is?

---

### Post by pay on 2006-10-28
@MustandSallydd
```
find / -iname iceweasel
```should find it

---

### Post by IusedTObeSOMEONEelse on 2006-10-28
It showed up in 3things, what would be the one to use? Thanks pay! ---   /home/myname/.gnuzilla/iceweasel
/home/myname/Iceweasel
/home/myname/iceweasel-1.5.0.7-g1-i386/iceweasel

---

### Post by pay on 2006-10-29
I think that this one will do.
/home/myname/.gnuzilla/iceweasel/plugins
But that would mean the plugin will only be available to that user and noone else. But since that the install path of iceweasel is in your home path i'm guessing you are the only user that is using it.

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
I am all confused now! I have tried all combos but keep comming up no path. I checked prefered applications and Iceweasel is under'custom' and under command-/home/sally/iceweasel. I cannot find mozilla plugins anywhere on my machine. What is going on? Everything is all f*^%k$d up. Excuse my 'potty mouth'

---

### Post by pay on 2006-10-29
I recomend installing the debian file of iceweasel. Delete the old browser but not the /home/myname/.gnuzilla/iceweasel directory. That contains bookmarks and things
```

rm -r/home/myname/Iceweasel
rm -r /home/myname/iceweasel-1.5.0.7-g1-i386/iceweasel
wget http://safeweb.sitesled.com/iceweasel/builds/iceweasel_1.5.0.8pre-2.deb
sudo dpkg -i iceweasel_1.5.0.8pre-2.deb
sudo update-flashplugin
wget http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz
tar xvzf FP9_plugin_beta_101806.tar.gz
sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/
```Then I think that it will work.

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
Thanks pay. I'm gonna work on that now,wish me luck!!!

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
ok, I did every thing in the code box, please, where do I go from here as far as opening Iceweasel?

---

### Post by pay on 2006-10-29
Open the terminal and type```
iceweasel
```you can make a launcher for it with alacarte.

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
I did Iceweasel twice and firefox keeps opening. Isn't there a sudo to whip up to get the job done?

---

### Post by pay on 2006-10-29
sudo just means root user access. To use iceweasel you must have all instances of firefox closed before you type inceweasel into the terminal.

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
~$ Iceweasel
bash: Iceweasel: command not found--I had nothing open, i am sorry to keep dragging you through my lack of knowledge. I am about ready to give this up as I don't know what else to do

---

### Post by Somniis on 2006-10-29
> **MustangSallydd said:**
> ~$ Iceweasel
bash: Iceweasel: command not found--I had nothing open, i am sorry to keep dragging you through my lack of knowledge. I am about ready to give this up as I don't know what else to do

Have you tried Opera? :p

---

### Post by pay on 2006-10-29
> **MustangSallydd said:**
> ~$ Iceweasel
bash: Iceweasel: command not found--I had nothing open, i am sorry to keep dragging you through my lack of knowledge. I am about ready to give this up as I don't know what else to do

Linux is case sensitive ```
Iceweasel
```won't work```
iceweasel
```will work (hopefully).

---

### Post by IusedTObeSOMEONEelse on 2006-10-29
actually I just got iceweasel and flash was working as well. Thank you so much  "pay" for sticking in there for me or I would have given up. I am posting how it was done so no one should have to go through  the crap I did. I hope this helps others and thanks to 'pay' :-D :p  Here's how it went down: I followed pays codes for Iceweasal and flash 9 Beta.  Then after alot of trial and error and closing down firefox, I  clicked on Panal and then Add to Panal and the Iceweasel icon was there(cute icon the weasel wrapped around globe) so clicked the icon. Then I right clicked on the Iceweasel icon , then clicked Properties and the little Launcher Properties window opened and I saw were it sad 'Command:  iceweasel su. So Iwent to my ole friend the 'terminal'  and entered iceweasel su and oh my god, it opened Iceweasel with the plugin working!!

---

