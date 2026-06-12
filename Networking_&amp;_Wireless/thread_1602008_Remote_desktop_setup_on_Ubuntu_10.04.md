---
title: "Remote desktop setup on Ubuntu 10.04"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by wzhao6898 on 2010-10-20
Hi there,

I've been searched around for a while for a simple and straight forward remote desktop configuration for ubuntu 10.04. it almost seemed that such solution should be so natural given it's LINUX os, but I haven't been able to found any yet. 
What I want to do is:
install ubuntu 10.04 desktop, configure remote desktop so I can connect from my Mac or Windows machine without being physically be at the ubuntu machine, and I won't have a dedicated monitor for the ubuntu box either. And I want to have root access to everything via remote desktop or VNC.

What I have tried: system->preferences->remote desktop to enable remote desktop, I can connect and see the desktop, the mouse clicks would only show on the directly connected monitor, not in my VNC session.
Then I tried to install TightVNC server, start a at display :1, I can also connect, but every time any action requires a root access, such as installing a package using Ubuntu Software Center, the root password prompt would only show up on the directly connected monitor.

I also install xrdp package, and followed instructions here: [http://www.liberiangeek.net/2010/07/connect-ubuntu-10-04-lucid-lynx-remote-desktop-windows-machines/](http://www.liberiangeek.net/2010/07/connect-ubuntu-10-04-lucid-lynx-remote-desktop-windows-machines/)
It actually worked using Remote Desktop application from my Mac or Windows box for a little while until I restarted the machine, thinking I can unplug the monitor and connect via remote desktop from then on. Then it stopped working.

Any help will be greatly appreciated.

David

---

### Post by wzhao6898 on 2010-10-22
is this just me, nobody else had problem with remote desktop on Ubuntu 10.04?

---

### Post by luvshines on 2010-10-22
You mean when you are connected to the desktop, the activity that you perform remotely are not visible on your system but on a directly attached monitor only ??
If I guess correctly, the screen that you get when connected is not being refreshed, right ?

---

### Post by haihovu on 2010-10-24
I use xrdp to connect to my Ubuntu servers daily for years now so I know it does work.
Xrdp works with VNC and currently (10.10) can use tightvnc, vnc4server, plus another one that I am not familiar with. In the past though xrdp appeared to work best with tightvnc, as such you should/must install tightvnc prior to installing xrdp. Most vnc implementation present to clients a new desktop session for each new connection, only x11vnc presents the same main console desktop to every client session, which sounds like your problem. If you have x11vnc, I'd replace it with tightvnc. GUI activities requiring elevated permission (such as Synaptic) need .Xauthority which may not be present in your home dir, if you don't see .Xauthority under your home dir create one, I find the easiest way to create this is to run vncserver (from a terminal), then stop it by executing vncserver -kill :1

---

### Post by wzhao6898 on 2010-10-24
> **haihovu said:**
> I use xrdp to connect to my Ubuntu servers daily for years now so I know it does work.
Xrdp works with VNC and currently (10.10) can use tightvnc, vnc4server, plus another one that I am not familiar with. In the past though xrdp appeared to work best with tightvnc, as such you should/must install tightvnc prior to installing xrdp. Most vnc implementation present to clients a new desktop session for each new connection, only x11vnc presents the same main console desktop to every client session, which sounds like your problem. If you have x11vnc, I'd replace it with tightvnc. GUI activities requiring elevated permission (such as Synaptic) need .Xauthority which may not be present in your home dir, if you don't see .Xauthority under your home dir create one, I find the easiest way to create this is to run vncserver (from a terminal), then stop it by executing vncserver -kill :1

Thanks, I'll give it a try (installing tightvnc before xrdp). I sort of got it to work, following instructions [here]("http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/"), but I don't know what made it work, what not, and I still don't have the full root access for some action. For instance, if I want to share a folder, and install sharing services, I'll have to do this on the attached display, I'm getting a "Unable to copy user's xauthorization file" error. It's a shame I had to jump all these hoops to get a remote desktop server set up.
I'll give this another try, thanks!

David

---

### Post by haihovu on 2010-10-25
I normally ran vncserver just to create the .Xauthority file for me but this thread described a much simpler way of doing this: [http://ubuntuforums.org/showthread.php?t=1138337](http://ubuntuforums.org/showthread.php?t=1138337)

---

### Post by wzhao6898 on 2010-10-29
> **wzhao6898 said:**
> Thanks, I'll give it a try (installing tightvnc before xrdp). I sort of got it to work, following instructions [here]("http://markbrewster.wordpress.com/2010/02/04/ubuntu-9-10-not-starting-up-at-full-resolution-with-tv-turned-off/"), but I don't know what made it work, what not, and I still don't have the full root access for some action. For instance, if I want to share a folder, and install sharing services, I'll have to do this on the attached display, I'm getting a "Unable to copy user's xauthorization file" error. It's a shame I had to jump all these hoops to get a remote desktop server set up.
I'll give this another try, thanks!

David

Still sorta got it to work, writing this down in case somebody needs to do what I'm trying to do:
Here is what I did:
1. clean install of ubuntu 10.04 LTS
2. run update manager to bring the system up to date
3. install tightvncserver first as suggested by haihovu
4. install xrdp
5. run alt-f2, then gksu gnome-terminal
6. connect from my mac using CorD remote desktop viewer
7. tested both with monitor attached and detached and shutdown by pulling the power cable, all worked
8. then I moved the system upstairs to stash it away, right after restart, remote desktop worked as well. but wouldn't connect after a hour or so. I suspect this has something to do with the screen saver kicking in (?), but tired of this whole thing (spent too much time on this), I ssh into the machine, killed all screensaver instances, didn't help, still not working. Then I did a "ps -efww | grep vnc", I found there was a vncserver running at :10 display (don't know why it was there), so I used chicken of VNC connect to it, voila, I was in (display is kinda crappy, but at least I can see and control the desktop). 
The machine has been running serveral days now.
Thanks for all your help!

David

---

### Post by mrmikefm on 2011-01-09
The answer is here!!!
 
[http://ubuntuforums.org/showthread.php?p=10337515#post10337515](http://ubuntuforums.org/showthread.php?p=10337515#post10337515)

---

