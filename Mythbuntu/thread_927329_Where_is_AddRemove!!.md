---
title: "Where is Add/Remove?!?!"
date: 2008-09-22
forum: Mythbuntu
---

### Post by t_hutch on 2008-09-22
Greetings...

I'm a newbie to both Ubuntu and Mythtv. I just installed mythbuntu 8.04 on a system. Everything I've read in these forums always points towards Add/Remove as the easiest way for us Newbies to install packages. However, it does not come up on my installation!!!

I've tried everything I could track down on the forums. I added the launcher manually, but nothing happens when I click it. 

Any suggestions?

Thanks!

---

### Post by matt79 on 2008-09-22
Click on the Applications on the top right and go to the very bottom. It should be there :-)

---

### Post by t_hutch on 2008-09-22
That is exactly the problem....it's not there. I've even tried a new, fresh install paying special attention to all selections during installion to make sure I didn't miss anything.

---

### Post by hansdown on 2008-09-22
Hi t_hutch.

First you need to activate it in system> preferences> main menu.

Now it should show up in applications.

---

### Post by jpeddicord on 2008-09-22
You said it doesn't launch when you click it. Would you mind opening a Terminal (Applications > Accessories > Terminal) and running the following command, and paste the output back here? 

```
gnome-app-install
```

We might be able to find out if something is wrong or not. Of course, if the Add/Remove manager pops up, then is works, but something is wrong with the menu item.

---

### Post by t_hutch on 2008-09-23
I tried the following

```
gnome-app-install
```

I got the following:


```
The program 'gnome-app-install' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-app-install
bash: gnome-app-install: command not found
```


I did as suggested and it successfully installed the add/remove app. Thanks for your suggestion. Is this the way the mythbuntu install should go?

---

### Post by joho500 on 2008-09-24
In Mythbuntu it's different from the normal Ubuntu isntallation. In mythbuntu u use Synaptic package manager which u can find under System in the Applications menu.

Joost

---

