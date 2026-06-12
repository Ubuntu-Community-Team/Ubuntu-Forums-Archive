---
title: "Kubuntu forcing me to reinstall nvidia drivers every boot"
date: 2005-12-13
forum: Multimedia &amp; Video
---

### Post by wolfe on 2005-12-13
Here is my problem, and I am completely perplexed.  I am using the latest nvidia drivers, the 8xxx series.  I install from the console with no gui loaded.  I have no errors doing this.  I edit my xorg.conf, and start X with either "sudo startx" or "sudo kdm."

Now the system runs flawlessly with this.  But if I reboot my computer, when it attempts to start kdm, it fails, with no error message, and the tty that X would be running on has only a blinking cursor.  At this point, I have to pgrep for kdm's pid, and then kill it.  I then have to reinstall the nvidia driver.  I had this issue on 5.04 as well, and it seems it has persisted into 5.10 ( at least for me it has)

Does this sound familiar to anyone?

---

### Post by jquintero on 2005-12-13
same exact problem here on a fresh install of ubuntu 5.10. 
the error i get is that it says something about loading the 7xxx series of nvidia drivers, but i've never installed those.

---

### Post by MartinG on 2005-12-13
I'm not sure if this is the answer for you, but when I installed the new drivers I did it with the nvidia installer.  Apart from the new driver this also built a new kernel module, which worked fine, until I rebooted. Sound familiar?

What I had to do was uninstall the restricted kernel modules   (linux-restricted-modules-2.6.xxxx) for my kernel, to prevent the system booting with the old kernel module (which is incompatible with the new driver).

Try it and see.

---

### Post by wolfe on 2005-12-13
jquintero, you're right, I do get that message too.

And Martin, I'll try that when I get home, I'm at work on my mandriva box.

---

### Post by jquintero on 2005-12-13
That did the trick! I wonder though, are the restricted modules installed by default or  did I unknowingly install them somehow?

---

### Post by wolfe on 2005-12-13
I'm trying to do this through adept, and it wants to remove the package "linux-386" this doesnt seem safe, or is it?

---

### Post by MartinG on 2005-12-14
[QUOTE=wolfe]I'm trying to do this through adept, and it wants to remove the package "linux-386" this doesnt seem safe, or is it?[/QUOTE]

AFAIK, linux-386 is a meta-package representing the complete kernel and its "bits". It is installed by default, and therefore the restricted modules are installed by default (jquintero's question).  By removing one of the bits you break the meta-package, so it has to be removed.  It didn't hurt me when I had it removed with the restricted modules :-)

---

### Post by wolfe on 2005-12-14
thanks for the help, this one's resolved.

---

