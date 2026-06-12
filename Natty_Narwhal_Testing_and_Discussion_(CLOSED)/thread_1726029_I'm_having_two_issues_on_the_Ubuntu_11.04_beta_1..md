---
title: "I'm having two issues on the Ubuntu 11.04 beta 1."
date: 2011-04-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by KingHanco on 2011-04-10
Sometime I click on the square box (zoom in or out on the screen.) on the top left corner of anything that I open and then it crashes Ubuntu 11.04. I can't shut it down or anything. Just frozen up. I can move the mouse though.

Another thing is that there is two updates showing and I can't install those on the Update Manger. I tried check the boxes but it stay unchecked.

Only two problems that I have.

---

### Post by bodhi.zazen on 2011-04-10
*Thread moved to **Natty Narwhal Testing and Discussion**.*

Natty is in testing, use the testing section and be prepared to file bug reports =)

---

### Post by cubeist on 2011-04-10
> **KingHanco said:**
> Sometime I click on the square box (zoom in or out on the screen.) on the top left corner of anything that I open and then it crashes Ubuntu 11.04. I can't shut it down or anything. Just frozen up. I can move the mouse though.

Another thing is that there is two updates showing and I can't install those on the Update Manger. I tried check the boxes but it stay unchecked.

Only two problems that I have.

In reverse order, some updates need other packages to update first before they are available, don't worry about it, check back in a day or two...lots of packages get changed/updated during beta status.

Second, turn of all mipmaps in ccsm (use advanced search for mipmaps). Also turn of sync to vblank in ccsm and ati/nvidia control panel. This fixed for me.

---

### Post by KegHead on 2011-04-10
Hi!

Have you tried:

Sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f


KegHead

---

### Post by Blasphemist on 2011-04-10
I agree with the post that said this too will pass.

I just did an update and two new updates showed up, Gnome translations for language English and translations for language English. These appear to be the same thing in this case. I have had items that don't update and stay in the list as available but can't be checked. 

Eventually it seems another update comes thru that does let them install.

Sorry but no help on the zoom issue.

---

### Post by KingHanco on 2011-04-11
Those are the 2 updates that is showing. [[IMG=http://img196.imageshack.us/img196/6338/screenshotago.png][/IMG]](http://img196.imageshack.us/i/screenshotago.png/)

I found another bug on the Firefox 4.0 or what ever it came with this Ubuntu. The slider thing on the right side appear to be missing sometime. Noway to move up and down without it on Google search or any website. Most of time it there. Kind of odd.

---

### Post by KingHanco on 2011-04-11
Whoops here is the snapshot of the missing slider thing on Firefox. [[IMG=http://img834.imageshack.us/img834/9523/screenshotsgy.th.png][/IMG]](http://img834.imageshack.us/i/screenshotsgy.png/)

---

### Post by MonolithImmortal on 2011-04-11
> **KingHanco said:**
> Sometime I click on the square box (zoom in or out on the screen.) on the top left corner of anything that I open and then it crashes Ubuntu 11.04. I can't shut it down or anything. Just frozen up. I can move the mouse though.

You mean it causes Unity to crash. If this happens just hit ctrl+alt+f1 to switch to tty1 and then login, then run ```
sudo reboot
```
It's not a permanent solution, but its better than a hard reset.

---

