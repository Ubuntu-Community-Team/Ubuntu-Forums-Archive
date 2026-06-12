---
title: "Why my UI looks so ugly?"
date: 2011-03-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aRagnis on 2011-03-11
When I log in, my UI looks normal for couple of seconds. But then it changes to that gray ugly "theme".
It looks something like Windows Classic theme.

It worked well, before doing an update.

[http://www.upload.ee/image/1186497/Screenshot.png](http://www.upload.ee/image/1186497/Screenshot.png)

---

### Post by lucazade on 2011-03-11
> **aRagnis said:**
> When I log in, my UI looks normal for couple of seconds. But then it changes to that gray ugly "theme".
It looks something like Windows Classic theme.

It worked well, before doing an update.

[http://www.upload.ee/image/1186497/Screenshot.png](http://www.upload.ee/image/1186497/Screenshot.png)

known issue, temporary workaround:

```
killall gnome-settings-daemon
gnome-settings-daemon &
```

---

### Post by ikt on 2011-03-11
> **lucazade said:**
> known issue, temporary workaround:

```
killall gnome-settings-daemon
gnome-settings-daemon &
```

Do you happen to have a link to the launchpad bug report?

---

### Post by cariboo on 2011-03-11
I've seen that on a fresh install, a reboot usually cures the problem.

---

### Post by lucazade on 2011-03-11
> **ikt said:**
> Do you happen to have a link to the launchpad bug report?

unfortunately I don't have.. if I remember well was a race condition of gnome-settings-daemon.

---

### Post by Harry33 on 2011-03-11
> **ikt said:**
> Do you happen to have a link to the launchpad bug report?

This is the bug, still in progress:
Bug #649809
It is an upstream bug in gdm, caused by a race situation.

This is the workaround:
Add a delay (here 1 sec) before gnome-settings-daemon starts.
Change the line of the file /etc/xdg/autostart/gnome-settings-daemon.desktop:
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c "sleep 1; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

---

### Post by rapiertg on 2011-03-11
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Is it this bug?

/Harry33
You were faster

---

### Post by Harry33 on 2011-03-11
> **rapiertg said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

Is it this bug?

Yes it is.

---

### Post by BigSilly on 2011-03-11
> **cariboo907 said:**
> I've seen that on a fresh install, a reboot usually cures the problem.

Doesn't cure it. It comes back over time repeatedly. It's currently plaguing Maverick, and there's a big discussion about it [here]("http://ubuntuforums.org/showthread.php?t=1575703").

Very sad to see this bug now continuing through the Maverick cycle and into Natty. For me personally, this is sadly going to affect my adoption of the distro as my main OS, and I'm currently looking to move. :(  There's been a number of silly little bugs over time that have gone untouched for one reason or another, be they Ubuntu's fault, or Gnome, or whoever. I think this one though was the straw that broke the camels back for me.

Still, I hope it works out for Ubuntu in the future.

---

### Post by Harry33 on 2011-03-11
> **BigSilly said:**
> Doesn't cure it. It comes back over time repeatedly. It's currently plaguing Maverick, and there's a big discussion about it [here]("http://ubuntuforums.org/showthread.php?t=1575703").

Very sad to see this bug now continuing through the Maverick cycle and into Natty. For me personally, this is sadly going to affect my adoption of the distro as my main OS, and I'm currently looking to move. :(  There's been a number of silly little bugs over time that have gone untouched for one reason or another, be they Ubuntu's fault, or Gnome, or whoever. I think this one though was the straw that broke the camels back for me.

Still, I hope it works out for Ubuntu in the future.

OK, but there is a very handy workaround for it, at least.

---

### Post by BigSilly on 2011-03-12
There is? No one told me, as I've tried all the fixes in the thread I linked to, and none of them worked. :(

If there's a working fix please let me know. :)

---

### Post by Harry33 on 2011-03-12
> **BigSilly said:**
> There is? No one told me, as I've tried all the fixes in the thread I linked to, and none of them worked. :(

If there's a working fix please let me know. :)

This is the workaround:
Add a delay (here 1 sec) before gnome-settings-daemon starts.
Change the line of the file /etc/xdg/autostart/gnome-settings-daemon.desktop:
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c "sleep 1; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

---

### Post by BigSilly on 2011-03-12
Will give that a go. Thanks.

---

### Post by BigSilly on 2011-03-13
> **Harry33 said:**
> This is the workaround:
Add a delay (here 1 sec) before gnome-settings-daemon starts.
Change the line of the file /etc/xdg/autostart/gnome-settings-daemon.desktop:
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
to
Exec=bash -c "sleep 1; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"

Sadly this fix didn't work. On boot up this morning the issue returned. :(

---

### Post by Harry33 on 2011-03-13
> **BigSilly said:**
> Sadly this fix didn't work. On boot up this morning the issue returned. :(

OK, then you might of course increase the sleep time from 1 sec to 2 secs.
Try this:
```
Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
```

Usually you get this bug with a fast SSD or very fast HDD.
I have WD Velociraptor HDD (10,000 rpm).

---

### Post by jennybrew on 2011-03-13
The problem has been with us for quite a significant length of time and, given the importance attached to the bug report (Low), I would suggest it may be around for quite a while longer.
Harry33 seems to have discovered a work around and Im sure its much appreciated.
But hey shouldnt issues like this be given more attention and importance once reported as a bug?

---

### Post by BigSilly on 2011-03-14
> **Harry33 said:**
> OK, then you might of course increase the sleep time from 1 sec to 2 secs.
Try this:
```
Exec=bash -c "sleep 2; /usr/lib/gnome-settings-daemon/gnome-settings-daemon"
```

Usually you get this bug with a fast SSD or very fast HDD.
I have WD Velociraptor HDD (10,000 rpm).

Sadly again, changing the sleep variable has made no difference, and the bug still returns. :(  I don't have an SSD or a particularly fast HD, and I don't think if I'm honest that this bug is confined only to those who do. It's a fairly prolific problem that affects a wide range of regular PC users, just going on forum posts here and around the net.

---

### Post by Harry33 on 2011-03-14
> **BigSilly said:**
> Sadly again, changing the sleep variable has made no difference, and the bug still returns. :(  I don't have an SSD or a particularly fast HD, and I don't think if I'm honest that this bug is confined only to those who do. It's a fairly prolific problem that affects a wide range of regular PC users, just going on forum posts here and around the net.

Do you see this error message in the file xsession-errors (located in your Home Folder):

"** (gnome-settings-daemon:1941): WARNING **: You can only run one xsettings manager at a time; exiting"

---

### Post by BigSilly on 2011-03-14
No, I get this in mine:

```
** (gnome-settings-daemon:1823): WARNING **: Got less number of items in credentials hash table than expected!
```

Thanks for your attention to this. I suppose I'm very much in the wrong forum, and I would like to state again, so I don't upset anyone, that I'm actually running Maverick and not Natty. My original comment was sadness that this bug was spilling over from Maverick and into Natty, just to avoid any confusion.

---

### Post by Harry33 on 2011-03-14
> **BigSilly said:**
> No, I get this in mine:

```
** (gnome-settings-daemon:1823): WARNING **: Got less number of items in credentials hash table than expected!
```

Thanks for your attention to this. I suppose I'm very much in the wrong forum, and I would like to state again, so I don't upset anyone, that I'm actually running Maverick and not Natty. My original comment was sadness that this bug was spilling over from Maverick and into Natty, just to avoid any confusion.

Yes, the bug I was refering to is present in Natty, but also in Maverick.
Still, you might want to take a look at the other bug reports concerning
gnome-settings-daemon, like this:
Bug#713186
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/713186](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/713186)

Also you might try to search for similar bugs (gnome-settings-daemon) here:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by Harry33 on 2011-03-29
Now there is fix proposal out to solve this race condition.

See here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

For me it fixed the issue (gnome-desktop-settings not starting after gdm).

---

### Post by isaacahloe on 2011-03-29
the link was shortened/doesn't work. would you mind reposting/editing. i'd like to take a look. thanks

edit. got it i think. code has full address, plus link below it

[CODE]https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809[/CODE
][https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

edit2


didn't fix my problem, but i my gnome-settings-daemon would start and then later crash, which is different than not starting after gdm.

i think my problem is the original problem on this thread, but i hope the race issue thing fixes some other people's problem

---

### Post by isaacahloe on 2011-03-29
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/554280](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/554280)

that is the bug report pertaining to my problem, gnome-settings-daemon crashes randomly after a few minutes or less of usage. it affects 32 people who make bug report

---

### Post by encefalocardia on 2011-04-01
Now I-m experiencing this after today's update :/

---

### Post by loukingjr on 2011-04-02
> **lucazade said:**
> known issue, temporary workaround:

```
killall gnome-settings-daemon
gnome-settings-daemon &
```

this did work for me.but I have to do it everytime I change themes.

running ubuntu 11.04 beta in virtualbox.

edit: I take that back. it patially works but maybe this is the problem. the equinox engine is 1.20 and there is a 1.30 in the wild. I remember having to get 1.30 installed because several themes I tried required it else I would get the "generic" look. I'm hunting for a 1.30 version now.

---

### Post by lucazade on 2011-04-02
> **loukingjr said:**
> this did work for me.but I have to do it everytime I change themes.

running ubuntu 11.04 beta in virtualbox.

Unfortunately bug is still under investigation, there are still some issues under virtualbox and vmware.. we should wait for a better fix!
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

---

### Post by loukingjr on 2011-04-02
> **lucazade said:**
> Unfortunately bug is still under investigation, there are still some issues under virtualbox and vmware.. we should wait for a better fix!
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809)

well, I found out something interesting. I installed the Atolm theme and it works fine in root but not with a user. if I run sudo nautilus it comes up with the theme. if I just open nautilus normally it has the "generic" look. It should be the other way around.

here's nautilus running as root...
[IMG]https://lh3.googleusercontent.com/_sA9c938TUEU/TZbSbGPEaFI/AAAAAAAAG10/1AeTTavXhlI/s400/Screenshot.png[/IMG]
here's nautilus running "normally"
[IMG]https://lh5.googleusercontent.com/_sA9c938TUEU/TZbTJpbs4EI/AAAAAAAAG14/Qg-In-beHvA/s400/Screenshot.png[/IMG]

just to try it, I installed thunar and it adopts the theme without running as root.

---

### Post by loukingjr on 2011-04-02
could this be a users/groups problem? maybe the user doesn't belong to a group that he/she should?

---

### Post by lucazade on 2011-04-02
> **loukingjr said:**
> could this be a users/groups problem? maybe the user doesn't belong to a group that he/she should?

The problem is that gnome-settings-daemon (which store and manage user preferences like theme, fonts..) doesn't start properly after gdm login screen.

So after a few seconds it automatically switch to a not themed session, like your second screenshot.

---

### Post by cariboo on 2011-04-02
Have you created a new user to see if the problem still show up?

---

### Post by loukingjr on 2011-04-02
> **lucazade said:**
> The problem is that gnome-settings-daemon (which store and manage user preferences like theme, fonts..) doesn't start properly after gdm login screen.

So after a few seconds it automatically switch to a not themed session, like your second screenshot.

okay. I was just wondering why after restarting the gnome-settings daemon a theme works correctly except for nautilus. It only adopts the theme if launched as root. Thunar doesn't have the same problem...

here's a screenshot of Unity 2d with nautilus running as root again.
[IMG]https://lh6.googleusercontent.com/_sA9c938TUEU/TZbY7rJd4kI/AAAAAAAAG2I/Z_etnK-EZ9s/s400/Screenshot.png[/IMG]

---

### Post by loukingjr on 2011-04-02
> **cariboo907 said:**
> Have you created a new user to see if the problem still show up?
not yet but I will.

---

### Post by lucazade on 2011-04-02
> **loukingjr said:**
> okay. I was just wondering why after restarting the gnome-settings daemon a theme works correctly except for nautilus. It only adopts the theme if launched as root. Thunar doesn't have the same problem...

here's a screenshot of Unity 2d with nautilus running as root again.
[IMG]https://lh6.googleusercontent.com/_sA9c938TUEU/TZbY7rJd4kI/AAAAAAAAG2I/Z_etnK-EZ9s/s400/Screenshot.png[/IMG]

after restarting gnome-settings-daemon you should kill nautilus as well

```
killall nautilus

```
this way nautilus will be reloaded with correct settings, the same happens here.
nautilus is loaded very early when you open a session because it draws the desktop, so needs to be restarted.

if you launch an application as root, settings are loaded on the fly so are correctly skinned.. hope this help you.

(looking at your screenshot also unity panel is not skinned in indicator area: "killall unity-2d-panel" solves it... obviously these are only workarounds)

---

### Post by loukingjr on 2011-04-02
> **lucazade said:**
> after restarting gnome-settings-daemon you should kill nautilus as well

```
killall nautilus

```this way nautilus will be reloaded with correct settings, the same happens here.
nautilus is loaded very early when you open a session because it draws the desktop, so needs to be restarted.

if you launch an application as root, settings are loaded on the fly so are correctly skinned.. hope this help you.

(looking at your screenshot also unity panel is not skinned in indicator area: "unity --reset" solves it... obviously these are only workarounds)

 I see, thanks.

edit: "unity --reset" may not work with Unity 2D or in VirtualBox. I get this...
Traceback (most recent call last):
  File "/usr/bin/unity", line 194, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 79, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'

---

