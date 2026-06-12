---
title: "Window problems"
date: 2010-11-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-25
When a window is maximised I have a top bar and max/min buttons.
When it is unmaximised the buttons disappear and the window is completely unmovable.
Alt and click doesn't move it, if I click on the top bar (if there is one!) and try to drag it, it doesn't move, and the alt space bar and R only moves the contents of the window, not the window itself.

Any suggestions would be good, thanks :-)

---

### Post by linux-hack on 2010-11-25
Do you have compiz activated ? if so try deactivating it

---

### Post by Quackers on 2010-11-25
Yes I do. 
I would like to try your advice, but anything compiz related tends to lock up one of the cpu's, so I'm a little apprehensive :-)
Actually, I'll try it on the other testing system first (which is already partly borked) :-)
Thanks for the info, I'll be back :-)

Edit, would unchecking the box for "enable desktop integration" deactivate compiz or not?

---

### Post by linux-hack on 2010-11-25
No you need to replace the window handler witch  is compiz with the default of ubuntu ...
I think its somthing like ```
nautilus --replace
```

---

### Post by sikander3786 on 2010-11-25
> **linux-hack said:**
> No you need to replace the window handler witch  is compiz with the default of ubuntu ...
I think its somthing like ```
nautilus --replace
```
Shouldn't it be

```
metacity --replace
```

:-k

---

### Post by Quackers on 2010-11-25
I think metacity --replace too.
That's what I used and guess what!
Compiz completely locked up one cpu at 100% and nothing was clickable any more! Happens every time.
I had to REISUB to reboot.

---

### Post by sikander3786 on 2010-11-25
I advise installing fusion-icon again and again in order to cure the problem easily.

> would unchecking the box for "enable desktop integration" deactivate compiz or not?

Unless it has changed in Natty, setting Visual Effects to None will disable compiz.

---

### Post by Quackers on 2010-11-25
Unfortunately compiz fusion icon is a no-no in natty. :-(
I liked that too :-)

---

### Post by cariboo on 2010-11-25
Just out of curiosity, what drivers are you using? I've got two system running Unity, one with the Nvidia restricted drivers and another using nouveau drivers. I'm not seeing any of the problems you seem to be running into.

---

### Post by Quackers on 2010-11-25
I have the nvidia 260.19.21 which came originally from xswat which was updated by the nvidia-current which came with the natty upgrade.

You can see in the screenshot that the top bar of the window is missing and the window is partially hidden by the panel. The window, and others like it all go to the top left of the screen and are unmovable.
I am not using unity.

---

### Post by susema on 2010-11-25
I have the same problem and there is no any compiz or visual effects :(

---

### Post by Quackers on 2010-11-25
I have given up trying to set visual effects :-)
It looks for a driver and doesn't seem to find one, then sometimes it allows the setting to be changed to "extra" and asks if I want to keep the settings. I answer yes and exit. Within a couple of hours it has magically changed back to "none" :-)
It's like it forgets there is a nvidia driver installed.

---

### Post by susema on 2010-11-25
@Quackers, solved :)

---

### Post by Quackers on 2010-11-25
> **susema said:**
> @Quackers, solved :)

What is :-)
Please enlighten me ;)

---

### Post by susema on 2010-11-25
I didn't do anything special. Only, I chose normaly visual effects. Computer froze, then I gave up and solved. That's it: D

---

### Post by cariboo on 2010-11-25
What version of compiz are you using? Affects don't work with the version that has been modified to work with Unity.

On this system (netbook running 11.04 UNE) I have compiz 0.9.2.1+glibmainloop-0ubuntu3

---

### Post by Quackers on 2010-11-25
cariboo907, I'm just re-installing Nasty, sorry Natty again on my initial test drive. I'll get back to you when I'm back in natty version 2 or after I've updated the new install.
All I can remember is that compiz was 0.9.2 something. The installation was fully updated though, and a number of compiz updates had run.

---

### Post by 12apennachi on 2010-11-25
That happened to me sometimes and after a compiz --replace it worked but it was a pain in the *** so I removed Compiz, it was never very smooth anyways.

---

### Post by cariboo on 2010-11-25
I ran into something similar on the system I was running gnome-shell on. After an update this afternoon, I lost the panel on gnome-shell, and with it all functionality. The way I solved my problem was to use ppa-purge to get rid of ricotz testing and rictoz staging. After purging the ppas, gnome-shell from the repositories was installed, so I had to purge that too. I then purged Unity, and reinstalled it, enabled the Unity plugin, where it asked me if I wanted to enable openGL and compiz. Once that was done, I now have a working Unity desktop.

On that system, I have a Nvidia 9400GT using the latest nvidia-current (260.19.21) drivers.

---

### Post by Quackers on 2010-11-25
Hi all, I'm back :-)
Re-install no 9 seems to have gone quite well. Not perfect, but more stable.
Desktop effects can be set to normal, which is new :-) 
All the panel applets failed to load and gave errors, but most of them returned on hitting the reload box.

Cariboo907 my current version of Compiz is 1:0.9.2.1 + glibmainloop-0ubuntu3.

On a different note, I tried to uncomment the Recovery=true line in /etc/default/grub and on saving the changes I get an error in the terminal
```
natty64@natty64-VGN-AR51SU:~$ gksu gedit /etc/default/grub

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FV35LV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VZWLMV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```
which seems odd.
Maybe I should start a new thread for that. Maybe it's a bug?

---

### Post by Quackers on 2010-11-25
Back to square one.
Anything to do with compiz just locks it up.
Compiz --replace or even trying to set desktop effects to "normal" just freezes everything on the desktop. Have to reboot using REISUB.
Also if no desktop effects are attempted the system reboots with all the panel applets appearing normally. On the odd occasion where desktop effects were running (I can tell by the shape of the Cairo dock display) some applets go missing.

---

### Post by cariboo on 2010-11-25
> **Quackers said:**
> Hi all, I'm back :-)
Re-install no 9 seems to have gone quite well. Not perfect, but more stable.
Desktop effects can be set to normal, which is new :-) 
All the panel applets failed to load and gave errors, but most of them returned on hitting the reload box.

Cariboo907 my current version of Compiz is 1:0.9.2.1 + glibmainloop-0ubuntu3.

On a different note, I tried to uncomment the Recovery=true line in /etc/default/grub and on saving the changes I get an error in the terminal
```
natty64@natty64-VGN-AR51SU:~$ gksu gedit /etc/default/grub

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FV35LV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VZWLMV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory


```
which seems odd.
Maybe I should start a new thread for that. Maybe it's a bug?

Use sudo when starting an app that needs root permissions from a command line. Use gksu when starting a graphical app from the run dialogue box eg:

Press Alt-F2

[IMG]http://i.imgur.com/XLLtS.png[/IMG]

---

### Post by Quackers on 2010-11-25
I did, didn't I?
```
natty64@natty64-VGN-AR51SU:~$ gksu gedit /etc/default/grub

```

This is how I have changed /etc/default/grub previously, without problems.

---

### Post by Quackers on 2010-11-25
```
natty64@natty64-VGN-AR51SU:~$ sudo gedit /etc/default/grub

(gedit:2397): Gtk-WARNING **: Unable to rename '/root/.recently-used.xbel': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.O3WHMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9FQNMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6D8DMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
natty64@natty64-VGN-AR51SU:~$ 

```
same, same :-( but different gedit code

---

