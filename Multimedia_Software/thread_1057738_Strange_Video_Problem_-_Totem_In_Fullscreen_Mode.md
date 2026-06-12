---
title: "Strange Video Problem - Totem In Fullscreen Mode"
date: 2009-02-02
forum: Multimedia Software
---

### Post by -kg- on 2009-02-02
I just noticed this problem, though I have not used Totem in Full Screen Mode for several days, and have added a few packages in the interim.

I have an mp3 that, from time to time, I play to aid in sleep (Liquid Mind - Serenity).  When I launch this mp3, in the past I would put the display to Full Screen Mode (FSM).

This morning, when I launched FSM, the screen went completely blank and I could not recover except by hard shutdown.  I noticed another video problem upon reboot (one that I solved by changing a setting in Startup Manager, which I have just installed), then tried FSM in Totem again, to the same result.

This time, I used ctrl-alt-del and hit enter, which did nothing (of course) then tried ctrl-alt-del and <tab>, which of course logged me out.  Still no video.

So I hard shutdown again and rebooted into Ubuntu.  I resolved to try one more time, but this time I pulled up the shutdown menu and discovered that 6 tabs took me to restart and 7 tabs to complete shutdown, so I once again launched Totem and tried FSM, with the same result - completely blank screen.  This time, of course, I was able to reboot successfully.

Any idea what the problem might be and how to resolve it?  I haven't tried any other software that goes into FSM to see if it happens globally...I just noticed the problem a few minutes ago.

I'm just starting to feel a little comfortable with Linux, but this really blind-sided me!  :p

Oh, and you'll pardon me if I don't reply to any inquiries right away...as I said, I just discovered this problem, and I'm due to go to work in about 1/2 hour.

---

### Post by Cscoundrel on 2009-02-02
sudo apt-get install totem-gstreamer

i would uninstall totem and  reinstall because gnome is  prone  to media  problems and  it  could of done somthing funny when u last updated you could aso possibly try a new  media  player  i prefer VLC anyway it  uses les  system  and  it  has codec  for everything 

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

hope  it  works

---

### Post by -kg- on 2009-02-02
> **Cscoundrel said:**
> sudo apt-get install totem-gstreamer

i would uninstall totem and  reinstall because gnome is  prone  to media  problems and  it  could of done somthing funny when u last updated you could aso possibly try a new  media  player  i prefer VLC anyway it  uses les  system  and  it  has codec  for everything 

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

hope  it  works

I've already installed vlc through Synaptic.  I guess I'm going to have to see if I can set it as the default player.

I've noticed some strange settings in my menu.lst, as well, and kind of wonder if that might have an effect on it.  My original entry(ies) were:

```
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```

Now, the entries look like this:

```
title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=0eed7f51-4808-4e8b-8483-e78f8df77d05 ro quiet splash [COLOR="Red"]vga=773[/COLOR]
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

```

Notice the extra setting in my current menu.lst in red.  I'm pretty sure that Startup Manager, which I just installed last night, is probably guilty of putting it there, but I am unfamiliar with what this setting does.

Thanks!

---

