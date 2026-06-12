---
title: "Adobe Flash Plugin in Lubuntu"
date: 2010-05-26
forum: Multimedia Software
---

### Post by cutman on 2010-05-26
Hey all, just got an old Gateway Solo 9300 laptop back in business by installing Lubuntu. It's pretty awesome, especially for a beta release. One thing that I was confused about though was installing the Adobe Flash Plugin. How do I go about doing that? I was trying to watch a youtube video and I clicked the link to download it but it gave me several linux options. Which one is correct?

---

### Post by 3rdalbum on 2010-05-26
The correct way to install Adobe Flash Player is to use the repositories. Search for "flash plug-in" in Ubuntu Software Center, and then install it from there.

Or run this command:

```
sudo apt-get install flashplugin-nonfree
```

Pretty much the correct way to install ANYTHING in Ubuntu is through the repositories.

---

### Post by cutman on 2010-05-26
That didn't work. It said it couldn't find the plugin.

---

### Post by niowfi on 2010-06-02
Run this command to install  flashplugin-installer

```
sudo apt-get install flashplugin-installer
```

---

### Post by nipunshakya on 2011-09-08
@OP - goto synaptic package manager and install Lubuntu-restricted-extras if you cant install "flash plug-in" in Ubuntu Software Center. Hope it works....Goodluck

Regards, WinuxUser

---

### Post by amjjawad on 2011-09-10
Lubuntu does NOT have Software Center, it has Synaptic as the Graphical Front End.

To install Flash Plugin:

```
sudo apt-get update && sudo apt-get install adobe-flashplugin -y
```

or

```
sudo apt-get update && sudo apt-get install flashplugin-installer -y
```

I have installed the first package and both my Chromium and Firefox (latest versions for both) are working fine.
Not quite sure what are the difference between these two packages.

By the way, this thread is old :)

---

### Post by Perfect Storm on 2011-09-10
> **amjjawad said:**
> 
By the way, this thread is old :)

Agreed.


Thread closed.

---

