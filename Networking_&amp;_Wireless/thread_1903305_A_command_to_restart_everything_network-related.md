---
title: "A command to restart everything network-related"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by tjoff on 2012-01-02
I have a laptop with ubuntu 10.04 that I use in on several wired and wireless networks. I like to use the hibernate function, but more often than not I experience problems connecting to the network when the machine resumes. This happens especially if i resume on another network than the one that was use when the machine hibernated.
If i reboot the machine, it always connects without problems, but then I lose my hibernated session.

Since I assume that the problem is due to some setting being out of sync or some process not resuming, I want to run everything related to networking, as it is run during a clean boot-up. 
Is there a command to restart everything network-related?

---

### Post by SeijiSensei on 2012-01-02
I assume you want to do this from the GUI interface?

I run KDE whose Network Manager applet has an "enable networking" check box.  If I uncheck that, or more often uncheck the "enable wireless" box, then recheck it, that will force the network to restart.  I'd be surprised if you don't have the same options in GNOME.

---

### Post by tjoff on 2012-01-02
> **SeijiSensei said:**
> I assume you want to do this from the GUI interface?
I run KDE whose Network Manager applet has an "enable networking" check box.  If I uncheck that, or more often uncheck the "enable wireless" box, then recheck it, that will force the network to restart.  I'd be surprised if you don't have the same options in GNOME.

Actually I do prefer a shell command.
The equivalent GNOME applet also has "enable networking" and "enable wireless" checkboxes, but using those does not work in the situation i referred to in my initial post. Since rebooting works, I figure there must be a difference between what the network manager does and what is done at bootup.

---

### Post by Lars Noodén on 2012-01-02
If you prefer using the shell then the following should restart the networking:

```

sudo /etc/init.d/networking restart 

```

---

### Post by nothingspecial on 2012-01-02
reloading your wireless module should work.

type ```
sudo lshw -C network
```

in the information for you wireless interface it will list the kernel module used under driver=?

After you resume try

```
sudo modprobe -r ?
sudo modprobe ?
```

Where ? is the wireless module/driver

---

### Post by tjoff on 2012-01-04
Thanks for your answers.

I tried the suggestions by Lars Noodén and nothingspecial, but none of them got the connection up and running.

Then I realized that I left out some information that might be important.

I said that rebooting works, but it is a truth with modifications.
Just rebooting does actually not work. What works is to set the hardware switch for the network adapter to "off", then reboot, and then set the hardware swich back to "on". Then wifi autodetection starts and works.
Toggling the hardware switch back and forth without rebooting does not help.

I am going to test your suggestions in combination with use of the hardware switch, but if the commands you provide do the same as using the GUI network manager does, it is not going to work.

---

### Post by tjoff on 2012-01-07
I have now done the test. The result is as foreseen:

What works:
1. Setting hardware switch to network adapter to "off".
2. Reboot.
3. Setting hardware switch to network adapter to "on".
4. Laptop autoconnects succesfully to the wireless network.

What does not work:
Any combination of commands  suggested in this thread, clicking around in the Network Manager GUI and toogling the hardware switch to network adapter, that does _not_ include rebooting.

Reminds me of my Windows days: Don't try to understand, just reboot ;) 

It simply must be possible to connect to a wireless network without having to reboot. If anyone can give me any [pointers]("http://xkcd.com/138/") to a diagnose or even a solution, I'll be glad.

---

