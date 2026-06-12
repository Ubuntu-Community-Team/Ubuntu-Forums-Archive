---
title: "Flash stopped working after update"
date: 2011-05-19
forum: Multimedia Software
---

### Post by boxcorner on 2011-05-19
Update Manager prompted me to run an update, which I did, then Flash stopped working after I ran ran the update.

I first noticed the problem when I was using Chromium, trying to view a video on the BBC website, which displayed the message "Cannot play media. You do not have the correct version of the flash player. Download the correct version".

So, I clicked on the download link, which took me to the Adobe site where I selected APT for Ubuntu 10.04+, but that didn't make any difference, so I then tried to view the same video using Firefox, but that displayed the same message.

Could someone please tell me what I need to do, in order to get Flash working again?  Everything was working fine, before I ran the update!  Thanks in advance.

---

### Post by boxcorner on 2011-05-19
Problem solved.  I did a search using Google and found that there's an extension for Firefox called Flash-Aid, which "removes conflicting flash installations and installs the appropriate version according to the Ubuntu system architecture".  It did the trick, so now BBC videos works fine, in both Firefox and Chromium.

---

### Post by lovinglinux on 2011-05-19
> **boxcorner said:**
> Problem solved.  I did a search using Google and found that there's an extension for Firefox called Flash-Aid, which "removes conflicting flash installations and installs the appropriate version according to the Ubuntu system architecture".  It did the trick, so now video works fine, in both Firefox and Chromium.

I was about to suggest that :-)

I am the developer btw.

---

### Post by boxcorner on 2011-05-19
> **lovinglinux said:**
> I was about to suggest that :-)

I am the developer btw.
Thanks for your help in getting videos on the BBC website working, but it seems I spoke too soon, because now I have discovered that YouTube videos no longer run in Chromium, whereas Firefox works fine!  The video display window in Chromium is black, and no error message is displayed.  Any suggestions?

**_Addendum_**
Well, now Chromium is working again.  Most peculiar.  Not sure what the problem was but I closed and re-started it, and now it seems fine.

---

### Post by SpookyAction on 2011-05-21
I had the same problem but was able to fix it just by uninstalling the flashplugin-installer package, purging it's files and reinstalling the package:

```
sudo apt-get remove flashplugin-installer
sudo dpkg --purge flashplugin-installer
sudo apt-get install flashplugin-installer
```

---

### Post by boxcorner on 2011-06-03
> **SpookyAction said:**
> I had the same problem but was able to fix it just by uninstalling the flashplugin-installer package, purging it's files and reinstalling the package:

```
sudo apt-get remove flashplugin-installer
sudo dpkg --purge flashplugin-installer
sudo apt-get install flashplugin-installer
```
Thanks for the tip.

---

### Post by eks on 2011-06-18
But it keeps breaking in every single update... isn't there a way to prevent this?

Btw, marking the package for complete reinstall on Synaptic also works to fix it. But since flash is quite often updated, having to do this every week or so is annoying...

---

### Post by Elktro on 2011-06-25
I have exactly the same problem. I tried to remove and reinstall the "flashplugin-installer", and it didn't work.

Then I installed the flash-AID, but it said something about some Wizard in really long text box, which I could understand at first glance. I am now so frustrated that I need to fight with flash *again*.

What do I do next?

---

### Post by lovinglinux on 2011-06-25
> **Elktro said:**
> I have exactly the same problem. I tried to remove and reinstall the "flashplugin-installer", and it didn't work.

Then I installed the flash-AID, but it said something about some Wizard in really long text box, which I could understand at first glance. I am now so frustrated that I need to fight with flash *again*.

What do I do next?

When you install Flash-Aid, it adds an icon to the Navigation Toolbar, from where you can start the Wizard. If you can't see that icon, then right-click on the toolbar, select *Customize*, then drag the Flash-Aid icon to the toolbar. Flash-Aid is pretty simple to use. Just follow the Wizard instructions. For more info, see the extension documentation at [http://www.webgapps.org/add-ons/flash-aid/documentation](http://www.webgapps.org/add-ons/flash-aid/documentation)

---

### Post by Elktro on 2011-06-25
> **lovinglinux said:**
> When you install Flash-Aid, it adds an icon to the Navigation Toolbar, from where you can start the Wizard. If you can't see that icon, then right-click on the toolbar, select *Customize*, then drag the Flash-Aid icon to the toolbar. Flash-Aid is pretty simple to use. Just follow the Wizard instructions. For more info, see the extension documentation at [http://www.webgapps.org/add-ons/flash-aid/documentation](http://www.webgapps.org/add-ons/flash-aid/documentation)

Thank you for quick response. Yes now I found it, I tried to search the icon from the "tools"-menu. :roll:

I couldn't get the bbc flash player work yet, but I have to try later. I am now way too tired and cranky to fix the computer.

---

