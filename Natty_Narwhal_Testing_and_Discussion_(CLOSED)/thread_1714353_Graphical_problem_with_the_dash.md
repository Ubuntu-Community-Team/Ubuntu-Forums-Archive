---
title: "Graphical problem with the dash"
date: 2011-03-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Chris180775 on 2011-03-25
Before reporting this as a bug I want to be sure that this problem doesn't affect only me. Here is the steps to reproduce it:

1) Click "Applications" or "Files & Folders" icon to open the dash;
2) Open the menu in the top-right of the dash without selecting any item on it
3) Now click on the desktop

I've made a screenshot to explain the problem.
In addition when I open the dash, the button to maximize appear like a corrupted image

Thanks in advance.

---

### Post by dino99 on 2011-03-25
have you checked for missing package(s) installation, or made a reconfig ?

---

### Post by Chris180775 on 2011-03-25
> **dino99 said:**
> have you checked for missing package(s) installation, or made a reconfig ?

How I can do that? Sorry but I'm totally newbie with command line. Thanks!

---

### Post by lucazade on 2011-03-25
I can't check this now, I don't have Unity3D here, but I remember that combobox/dropdown menu was a bit buggy.. I had a vertical line in the middle of dropdown menu when opening and closing it

---

### Post by dino99 on 2011-03-25
> **Chris180775 said:**
> How I can do that? Sorry but I'm totally newbie with command line. Thanks!

oops, i've seen "user since 2005", so i doubt you still a noob :)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure unity

---

### Post by Chris180775 on 2011-03-25
> **lucazade said:**
> I can check this now, I don't have Unity3D here, but I remember that combobox/dropdown menu was a bit buggy.. I had a vertical line in the middle of dropdown menu when opening and closing it

I suspect that this problem maybe can depend on my graphic card. I'm using an ati hd4200 igp.

---

### Post by Chris180775 on 2011-03-25
> **dino99 said:**
> oops, i've seen "user since 2005", so i doubt you still a noob :)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure unity

Unfortunately I'm still a noob :D
Thanks, I've tried this command but the problem remain... maybe I will try to reboot to see if something change.

---

### Post by ngsupb on 2011-03-25
> **Chris180775 said:**
> Before reporting this as a bug I want to be sure that this problem doesn't affect only me. Here is the steps to reproduce it:

1) Click "Applications" or "Files & Folders" icon to open the dash;
2) Open the menu in the top-right of the dash without selecting any item on it
3) Now click on the desktop

I've made a screenshot to explain the problem.
In addition when I open the dash, the button to maximize appear like a corrupted image

Thanks in advance.

Confirming. This bug exists for me too (nvidia card + nouveau driver).

When open any application the white square disappears.

---

### Post by cariboo on 2011-03-25
I can confirm that it also happens on an nVidia card running the restricted drivers.

---

### Post by r-senior on 2011-03-25
I've just done an update and tried it. No such problems for me. lspci reports my graphics card as:

Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller

EDIT: Those menus are working for me too now. They weren't yesterday. It was like they were "behind" the Dash somehow and nothing could be selected from them.

---

### Post by cariboo on 2011-03-25
I don't have the problem on my netbook running the  945 Intel chipset. Mind you I rebooted the netbook yesterday, and I haven't rebooted my desktop yet.

---

### Post by cariboo on 2011-03-25
I don't have the problem on my netbook with Intel 945 chipset. I'll reboot my desktop later today to see if the problem is solved.

---

### Post by VMC on 2011-03-25
> **Chris180775 said:**
> Before reporting this as a bug I want to be sure that this problem doesn't affect only me. Here is the steps to reproduce it:

1) Click "Applications" or "Files & Folders" icon to open the dash;
2) Open the menu in the top-right of the dash without selecting any item on it
3) Now click on the desktop

I've made a screenshot to explain the problem.
In addition when I open the dash, the button to maximize appear like a corrupted image

Thanks in advance.

It took me a while to figure out what you were saying, but yes I can duplicate the problem. Its left over from that menu. If you once again open dash it disappears. If you want to create a bug report, I will sign up.

---

### Post by Chris180775 on 2011-03-25
> **VMC said:**
> It took me a while to figure out what you were saying, but yes I can duplicate the problem. Its left over from that menu. If you once again open dash it disappears. If you want to create a bug report, I will sign up.

I'm sorry for my horrible english :P
Anyway this afternoon I've created a bug report but now I'm seeing that mine result as a duplicate.
The original is here: [https://bugs.launchpad.net/null/+bug/741842](https://bugs.launchpad.net/null/+bug/741842)
Thanks to all!

---

### Post by VMC on 2011-03-25
> **Chris180775 said:**
> I'm sorry for my horrible english :P
Anyway this afternoon I've created a bug report but now I'm seeing that mine result as a duplicate.
The original is here: [https://bugs.launchpad.net/null/+bug/741842](https://bugs.launchpad.net/null/+bug/741842)
Thanks to all!

Thanks. By the way, it had nothing to do with your English, just me following your instructions while online. I'll follow up on that bug report. thanks.

---

