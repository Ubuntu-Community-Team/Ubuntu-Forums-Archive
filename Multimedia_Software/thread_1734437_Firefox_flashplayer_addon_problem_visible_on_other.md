---
title: "Firefox flashplayer addon problem: visible on other windows"
date: 2011-04-20
forum: Multimedia Software
---

### Post by baronKarza on 2011-04-20
I have a great problem with flash add on: when I open a web page containing a flash object, that object remains visible on all desktops and over other windows ([see image here]("http://www.vega.it/Photo0024.jpg")).

The problem persists also if I close firefox. To solve I have to restart X.
I tried to reinstall the addon, to remove the .mozilla directory but nothing changes.
Any idea?
Thx in advance

---

### Post by mynameisnotbob on 2011-04-20
you could try chromium.
```
sudo aptitude install chromium
```
that's how you get it.
it might not have the same issue.

---

### Post by collisionystm on 2011-04-20
Are you using 64 bit Ubuntu? Where did you get your flash file

---

### Post by baronKarza on 2011-04-20
I'm using 32 bit kernel

```
$ uname -a
Linux lore-laptop 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

```

The plugin is that provided by the distribution. I also tried to download the flash plugin from adobe but the problem remains unresolved.

---

### Post by baronKarza on 2011-04-20
> **mynameisnotbob said:**
> you could try chromium.
```
sudo aptitude install chromium
```
that's how you get it.
it might not have the same issue.

Thanks, I already tried Google Chrome and I have no problem.
But I need Firefox ;-)

---

### Post by baronKarza on 2011-04-20
> **collisionystm said:**
> Are you using 64 bit Ubuntu? Where did you get your flash file

I'm using 32 bit kernel

```
$ uname -a
Linux lore-laptop 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

```

The plugin is that provided by the distribution. I also tried to download the flash plugin from adobe but the problem remains unresolved.

---

### Post by mynameisnotbob on 2011-04-20
have you tried resetting firefoxes settings completely?
you could completely uninstall firefox and reinstall
```
sudo apt-get purge firefox && sudo apt-get install firefox
```

---

### Post by baronKarza on 2011-04-20
> **mynameisnotbob said:**
> have you tried resetting firefoxes settings completely?
you could completely uninstall firefox and reinstall
```
sudo apt-get purge firefox && sudo apt-get install firefox
```

Already done. Nothing changes.
As I said above, I also manually deleted the .mozilla dir in my home.
Is there another place where firefox stores settings? Or maybe is the plugin that stores something somewhere? :confused:

---

### Post by collisionystm on 2011-04-20
Turn off visual effects and see if it still happens. Could be compiz.

---

### Post by mynameisnotbob on 2011-04-20
you dont have to restart X, just GDM. put this in terminal(CTL+ALT+F2):
```
sudo /etc/init.d/gdm restart
```
or if you're a GUI hater, make 'restart' 'stop':)
Note that this will bring you back to the login screen, but you will already be logged in. All you have to do is type your password.

---

### Post by WannabeFantasma on 2011-04-20
> **baronKarza said:**
>  What he said

**Disable hardware acceleration** that works.

For previous posters:
Nothing to do with compiz,  I have NO desktop effects at all and I have it.
Happens only with Flash 10.2(+ latest version of it) not with 10.1

Wish there was a solution without disabling hardware acceleration, I have an Atom 330 and even full screen 360P on an HD screen stutters without it.

For reference: 
My second youtube video on this problem ([http://www.youtube.com/watch?v=OqufCyU4AEU](http://www.youtube.com/watch?v=OqufCyU4AEU)) 
Got a thread on this forums on the "General Help" part ([http://ubuntuforums.org/showthread.php?t=1688323](http://ubuntuforums.org/showthread.php?t=1688323))

Hope that helps you out a bit :)

---

### Post by mynameisnotbob on 2011-04-20
Do you have any ideas about what could be the cause of this problem? Put in a bug report. Maybe they'll fix it in a update.

---

### Post by WannabeFantasma on 2011-04-20
> **mynameisnotbob said:**
> Do you have any ideas about what could be the cause of this problem? Put in a bug report. Maybe they'll fix it in a update.

No idea at all...
Maybe graphics drivers? I have Nvidia, don't have an ATI machine to see if they have it..

Never put in a bug report, don't even know where to put it :$. 
(can you give me a link? or a How to?)

---

### Post by mynameisnotbob on 2011-04-21
go to here, it has instructions:
[Bug Reporting]("https://help.ubuntu.com/community/ReportingBugs")

---

### Post by baronKarza on 2011-04-22
> **collisionystm said:**
> Turn off visual effects and see if it still happens. Could be compiz.

I hate compiz. Never installed. 
I noted that not all flas objects generate the problem: only youtube player and many advertisings...

---

### Post by baronKarza on 2011-04-22
> **mynameisnotbob said:**
> Do you have any ideas about what could be the cause of this problem? Put in a bug report. Maybe they'll fix it in a update.

No, I have no idea. And I'm not sure to be always able to reproduce it.
For example, at present, I have no problems with the same video I posted the screenshot. The only thing I did is to Disable and then re-enable the "Shockwave Flash" plugin in the Plugins tab of the Add-on window.

---

### Post by WannabeFantasma on 2011-04-27
> **baronKarza said:**
> No, I have no idea. And I'm not sure to be always able to reproduce it.
For example, at present, I have no problems with the same video I posted the screenshot. The only thing I did is to Disable and then re-enable the "Shockwave Flash" plugin in the Plugins tab of the Add-on window.


tried some stuff earlier, worked but at second video it f'ed up again :D

gonna try your solution hope that helps for me :D

---

### Post by Yellow Pasque on 2011-04-27
> **mynameisnotbob said:**
> Do you have any ideas about what could be the cause of this problem?

Since it only seems to be happening to nvidia owners, it probably has something to do with the new Stage Video (Flash acceleration using vdpau)  that was added to Flash 10.2...

---

### Post by WannabeFantasma on 2011-04-27
> **Temüjin said:**
> Since it only seems to be happening to nvidia owners, it probably has something to do with the new Stage Video (Flash acceleration using vdpau)  that was added to Flash 10.2...

could be, only happens when you enable hardware acceleration...

---

