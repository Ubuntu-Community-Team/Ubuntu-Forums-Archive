---
title: "Unstyled themes, settings not recalled (AMD64)"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Sockerdrickan on 2010-10-03
[B]Edit: It works on i386 builds

[/B]This is what I get on a fresh install. It's plain unstyled GTK. The password for the wireless network is not remembered for each reboot and the same goes for the Nvidia driver, it's not applied at the next reboot.

I have tried RC, 20101002 20101003 with USB / CD. **AMD64!**

Does anyone else have this problem? With close to final release this should be looked into as fast as possible!

---

### Post by MacUntu on 2010-10-03
With *this* thread title I bet you'll get a quick fix personally delivered by a developer!

---

### Post by madverb on 2010-10-03
It looks like MacUntu got to it first; don't put up stupid titles. If you want help you should be more informative with your title.
Maybe attaching logs would be more helpful too. Stuff like that makes you seem like less of a whiny tool.

---

### Post by Sockerdrickan on 2010-10-03
The irony in all this is that it works great in live mode, I can even install the Nvidia proprietary driver and do
```
sudo service gdm restart
```
and I will have hw acceleration live. Seems to be some kind of session bug, I didn't find anything interesting in the logs.

---

### Post by Sockerdrickan on 2010-10-03
> **madverb said:**
> It looks like MacUntu got to it first; don't put up stupid titles. If you want help you should be more informative with your title.
Maybe attaching logs would be more helpful too. Stuff like that makes you seem like less of a whiny tool.
Whatever, it's not like a thread title is gonna be a base for a deep discussion, you should read the first post, I described what my problem is exactly. :)

```
robin@PC:~$ cd ~
robin@PC:~$ ls -a
.              .esd_auth        .gvfs             .pulse-cookie
..             .evolution       Hämtningar        .recently-used.xbel
.bash_history  .fontconfig      .ICEauthority     Skrivbord
.bash_logout   .gconf           .local            .sudo_as_admin_successful
.bashrc        .gconfd          .mission-control  .thumbnails
.cache         .gksu.lock       .mozilla          .xsession-errors
.config        .gnome2          .nautilus
.dbus          .gnome2_private  .profile
.dmrc          .gtk-bookmarks   .pulse

```
Anything missing here?

---

### Post by philinux on 2010-10-03
> **Sockerdrickan said:**
> This is what I get on a fresh install. It's plain unstyled GTK. The password for the wireless network is not remembered for each reboot and the same goes for the Nvidia driver, it's not applied at the next reboot.

I have tried RC, 20101002 20101003 with USB / CD. **AMD64!**

Does anyone else have this problem? With close to final release this should be looked into as fast as possible!

Have you got a launchpad account. Posting here will not get anything fixed.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by Sockerdrickan on 2010-10-03
> **philinux said:**
> Have you got a launchpad account. Posting here will not get anything fixed.

[http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
Okay I'll post an LP report.

**This issue is isolated to the AMD64 version!**

---

### Post by SeijiSensei on 2010-10-03
Just a note to say Kubuntu 10.10 amd64 works great and has fixed my wifi issues.

---

### Post by terry_gardener on 2010-10-03
> **Sockerdrickan said:**
> the same goes for the Nvidia driver, it's not applied at the next reboot.

was the system fine before you installed the nvidia driver or have you always had this problem.
goto system-administration and additional drivers and make sure that it says drivers activated and in use. 

i have always found when i install the nvidia drivers and try to change the screen res it doesn't hold. 

so to get round this i load the nvidia-setting using root privileges and then do the change that i want and save it to x configuration file.

then the screen res holds after each reboot.

with regard to wireless, not tested wireless on maverick since i use lan cable, but normally when i type the password in the first time it asks for keyring password to be setup and then you just enter keyring password after logon.  

also i agree with the above dont just but 10.10 is useless, use a descriptive title and supply as much info as possible and you will get better response.

---

### Post by nlsthzn on 2010-10-03
I just had a quick check and I have found many uses for 10.10.

---

### Post by wojox on 2010-10-03
> **Sockerdrickan said:**
> 
**This issue is isolated to the AMD64 version!**

Not here it isn't.

---

### Post by Sockerdrickan on 2010-10-03
> **wojox said:**
> Not here it isn't.
Interesting, do you have any of the problems I described, on i386?

I am running todays i386 10.10 and everything works fine.

---

### Post by ronacc on 2010-10-03
I have 3 maverick installs , all AMD64 , all Nividia . 2 nvidia-current and 1 the latest Nvidia beta hand installed , no res problems with any of them , how are you setting the res ?

---

### Post by Sockerdrickan on 2010-10-03
> **ronacc said:**
> I have 3 maverick installs , all AMD64 , all Nividia . 2 nvidia-current and 1 the latest Nvidia beta hand installed , no res problems with any of them , how are you setting the res ?
I was trying to use the nvidia-settings but it appears that Ubuntu was running in some kind of settings-read only mode, not saving any per-account data. And on top of that unstyled gnome-panel

---

### Post by 23meg on 2010-10-03
Fixed the title for you. Be advised that starting threads with provocative titles to get attention is frowned upon.

Is gnome-settings-daemon running, or even installed? Try running it if not.

---

### Post by cocopuffz on 2010-10-03
sometimes even in 10.4, the nvidia driver won't see that x was stopped. Is it stopped? who knows? ahha.

What works for me is dropping to single user mode ... type "init 1"
that should kill everything including the kitchen sink.

Then in the next menu, select the termimal... 

then go back up to runlevel 3. type "telinit 3"

The nvidia driver needs this runlevel to write to the kernel...

then CD to the file, make sure it's executable "chmod +x filename.run"

then run it...

---

### Post by ktp on 2010-10-03
can you check to see if you have gnome-settings-daemon installed and running?

---

### Post by Sockerdrickan on 2010-10-06
So an update on this. Build 20101006 AMD64.

1.
Themes work with
```
killall gnome-settings-daemon
gnome-settings-daemon
```2.
Ubuntu hanged at login after a reboot requested by installing the Nvidia driver. I'm thinking this might be related to [http://ubuntuforums.org/showthread.php?t=1589268](http://ubuntuforums.org/showthread.php?t=1589268)

---

### Post by cariboo on 2010-10-06
I had a similar problem earlier in the testing phase, it seems I was starting safe graphics mode. :)

---

### Post by cioma on 2010-10-06
I had the same problem with GTK theme: for some reason it defaults to "Raleigh" (instead of "Ambiance") with nvidia drivers. I fixed it by adding the following in my .gtkrc-2.0 :

```
include "/usr/share/themes/Ambiance/gtk-2.0/gtkrc"
```And if you want proper icons with it then also add:
```
gtk-icon-theme-name = "ubuntu-mono-dark"
```

---

### Post by Sockerdrickan on 2010-10-06
Thanks for the replys, I'll try this with 20101007 tomorrow!

---

### Post by Sockerdrickan on 2010-10-07
It worked today with the gtkrc-2.0 fix above. Seems like wireless connection is no longer set to default "connect automatically"

But I have another problem with todays build. it feels like someone is playing with me, I have now have to listen to a specific sound that plays each time an event has occurred like closing a window or opening firefox.
**/usr/share/sounds/ubuntu/stereo/button-pressed.ogg**
I set the sound theme to nothing but that did not help.

---

