---
title: "Mythbuntu 12.04 Update Manager Annoyances"
date: 2013-02-01
forum: Mythbuntu
---

### Post by tji on 2013-02-01
I was running an old version of Mythbuntu for a long time, and was very happy with it.

I recently wanted to upgrade to 0.26, so I upgraded both my frontend and backend to Mythbuntu 12.04.  In general, it's still fantastic..  I really like Mythbuntu, great job guys!

But, one thing that is constantly recurring is that the update manager pops up for one reason or another.   So, when I go turn on my system, I have MythTV in the background and some update manager related dialog in the foreground.

In my past years of mythbuntu usage, I only used my IR remote.  Once in a while I would ssh in to check things out.  Very rarely would I connect via VNC to interact with the desktop, and virtually never connected a keyboard and mouse.   Now, it seems like every time I want to watch something I have to first connect via VNC and close the windows to get back to MythTV.


I used the Mythbuntu Control Center to set update manager to operate in the background.   But, still got another dialog today telling me I needed to do a partial update.

To make the problem worse, the VNC connection constantly closes, requiring me to re-connect.   For whatever reason, it happens most often when I get the "enter password" popups to start an update.

I'll have to dig a bit deeper and stop the update manager from running automatically.   The current behavior seems like the wrong default.  Mythbuntu is typically controlled via IR remote, anything requiring control outside of that should be rare.

---

### Post by topcat5 on 2013-02-02
I agree that Update-manager is an Ubuntu annoyance.  Nothing like having that popup on a FE with no keyboard/mouse.    I removed update-manager and simply do updates from a command line.  Since I have several FEs this allows me to handle all the updates remotely with a simple SSH session.   

```

sudo apt-get update
sudo apt-get dist-upgrade

```

I also removed that program crash notifier too for the same reasons.   (forget the name of it)

---

### Post by ibjsb4 on 2013-02-02
You could also remove and replace update-manager and the software-center with Synaptic Package Manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

@topcat5

You thinking of Apport

---

