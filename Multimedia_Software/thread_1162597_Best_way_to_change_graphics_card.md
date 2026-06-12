---
title: "Best way to change graphics card"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Stolea on 2009-05-17
I run Ubuntu 9.04 and am about to change my graphics card from a Nvidia ge7600 to an ATI 4350PE. What do I have to watch out for so that I don't wind up with a blank screen?

---

### Post by Arup on 2009-05-17
Just make sure to remove the older drivers, if you installed via hardware drivers applet, just select remove from there, reboot and then shut off to install the newer card.

---

### Post by lilychef on 2009-05-17
I WISH I HAD KNOWN THIS!  Why doesn't Ubuntu provide this documentation?????  And if it IS there already, why is it so seemingly hard to find?!?!?!?

---

### Post by Stolea on 2009-05-17
Its a stock standard out of the box installation. The driver is the one Ubuntu installs, all I had to do was set the visual effects to the higher setting and reboot.
Anything that I have to watch for or do?

---

### Post by lilychef on 2009-05-17
Good luck!  Thought this would be a simple thing myself... Now I'm in Windows trying to get back into Jaunty.... And replies are hard to come by.  Snore.

---

### Post by Arup on 2009-05-18
Even in Win world, when you change cards, its strongly advised to remove the drivers or else putting new card will get you BSOD or worse, no boot.

---

### Post by Stolea on 2009-05-18
Followed the instructions and am now in front of my visually enhanced screen powered by my ATI card. :)

I have been using Ubuntu now for 12 months and after some initial problems would not swap it for Windoze for any reason. The changeover from Windoze to Linux can be a bit traumatic for somebody who is not versed in command line work. But the support for problems and questions is always there. Providing the user is willing to learn and try something new that might be pretty scary at first, Ubuntu is no more daunting than Windoze. And its a hell of lot more stable than any Windoze incarnation. And what's more, its free.

---

### Post by lilychef on 2009-05-18
Can you tell me how to remove old drivers from the command prompt?  I can't boot into Ubuntu to do it... maybe because the old video drivers are conflicting?  Sure wish I had known I had to do this before I installed the card...  because now it won't boot even when I take the card back out and try to go with onboard graphics...

---

### Post by Arup on 2009-05-18
> **Stolea said:**
> Followed the instructions and am now in front of my visually enhanced screen powered by my ATI card. :)

I have been using Ubuntu now for 12 months and after some initial problems would not swap it for Windoze for any reason. The changeover from Windoze to Linux can be a bit traumatic for somebody who is not versed in command line work. But the support for problems and questions is always there. Providing the user is willing to learn and try something new that might be pretty scary at first, Ubuntu is no more daunting than Windoze. And its a hell of lot more stable than any Windoze incarnation. And what's more, its free.

In case you wish to bypass command line, you can use synaptic to add remove and also install nautilus-gksu to have windows style browsing system folders and deleting or adding into system folders, as usual, extert caution when playing with system folders.

---

### Post by Arup on 2009-05-18
> **lilychef said:**
> Can you tell me how to remove old drivers from the command prompt?  I can't boot into Ubuntu to do it... maybe because the old video drivers are conflicting?  Sure wish I had known I had to do this before I installed the card...  because now it won't boot even when I take the card back out and try to go with onboard graphics...

Depending on your brand of card, at the command prompt in case you are running gnome execute sudo /etc/init.d/gdm stop and in case of kde just use kde instead of gdm

Then if it was ATI just do a sudo apt-get --purge remove nvidia* or if ATI just do a sudo apt-get --purge remove ati

---

### Post by lilychef on 2009-05-18
Thanks...  I will try... How do I know whether I'm running gnome or kde?  Ha!  Forgive me - I'm still new to linux/ubuntu...  Then after I remove the drivers, will Ubuntu boot up with the new card?  If ound this link from AMD, but not sure how to download and/or run it wihout actually being in Ubuntu...

[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.22&lang=English)

---

### Post by Arup on 2009-05-18
If you installed Kubuntu, you have KDE and if you installed Ubuntu, you have Gnome. Before you install the ati driver, make sure to do a sudo apt-get install build-essential and then run the ati installer.

---

### Post by lilychef on 2009-05-18
Thanks... I'll give it a go and let you know... Do I do the "build-essential" part from the grub prompt before attempting to boot into Ubuntu?

---

### Post by Arup on 2009-05-18
> **lilychef said:**
> Thanks... I'll give it a go and let you know... Do I do the "build-essential" part from the grub prompt before attempting to boot into Ubuntu?

You need to be in tty to do that and logged in as well.

---

### Post by lilychef on 2009-05-18
Ok - I did all that from root prompt.... Everything appeared to work... Even though it said it couldn't find either ati OR nvidia, so there's obviously no driver there... So it still won't boot... How do I install the driver from the prompt?  Is it some kind of "sudo apt-get install ati-something"?  Thanks again for our help

---

### Post by Arup on 2009-05-18
> **lilychef said:**
> Ok - I did all that from root prompt.... Everything appeared to work... Even though it said it couldn't find either ati OR nvidia, so there's obviously no driver there... So it still won't boot... How do I install the driver from the prompt?  Is it some kind of "sudo apt-get install ati-something"?  Thanks again for our help

Since you haven't downloaded the driver yet, in your case, easiest way for you would be to do a sudo apt-get install envyng

Then do a sudo envyng -t 

This program will fetch the drivers for you automatically and set it up for you.

---

### Post by lilychef on 2009-05-18
Jeez!  Sounds easy enuff!  I'll give it a go... Thanks for hanging in there with me...

---

### Post by Arup on 2009-05-18
> **lilychef said:**
> Jeez!  Sounds easy enuff!  I'll give it a go... Thanks for hanging in there with me...

You are welcome, just report back on the status.

---

### Post by lilychef on 2009-05-18
> sudo apt-get install envyng -T

This gave me:
"Option -T requires an argument"

So I dropped the "-T" for kicks and it came back with,
"couldn't find package envyng"

---

### Post by lilychef on 2009-05-18
Did a little digging, and found it should have been

sudo apt-get install envyng-qt, with no space between envyng and -qt.

I tried to install the driver, but it wanted to install an older one than what AMD says is the newest one, so I simply deleted whatever was there, and behold, Ubuntu booted up....  Not sure how to check what driver is running my vid card at the moment, but from what I've read, Jaunty only supports 2d for this card...  No big deal; I was really only trying to stop the choppy video I was getting with the onboard stuff...  and that appears to have worked...

I'm wondering if I even need to worry about installing the new driver now...   Thoughts?  Can you tell me how to check what's running my vid card?

Thanks so much again - I'm just happy to be out of that awful Windows...


And now I have a NEW problem... My sound card! Ha!

---

### Post by Arup on 2009-05-18
> **lilychef said:**
> Did a little digging, and found it should have been

sudo apt-get install envyng-qt, with no space between envyng and -qt.

I tried to install the driver, but it wanted to install an older one than what AMD says is the newest one, so I simply deleted whatever was there, and behold, Ubuntu booted up....  Not sure how to check what driver is running my vid card at the moment, but from what I've read, Jaunty only supports 2d for this card...  No big deal; I was really only trying to stop the choppy video I was getting with the onboard stuff...  and that appears to have worked...

I'm wondering if I even need to worry about installing the new driver now...   Thoughts?  Can you tell me how to check what's running my vid card?

Thanks so much again - I'm just happy to be out of that awful Windows...


And now I have a NEW problem... My sound card! Ha!

In a non GUI environment, you don't need envyng-qt which is for KDE actually. The plain vanilla envyng would suffice. The driver envyng would have installed is the oen from the Jaunty repository which would be older than the one from ATI site. You can now download ATI drivers from their site and then install them by doing ctrl+alt+F1 and then logging in and doing a sudo /etc/init.d/gdm stop

Then if you have placed the ATI driver in your home folder simply type sudo .sh and type the name of the driver and follow the instructions. If you don't want all that hassle just enable the [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/) in your repository. As for your sound problems, marbuntu has an excellent guide on how to wiggle out of sound issues in Ubuntu.

---

