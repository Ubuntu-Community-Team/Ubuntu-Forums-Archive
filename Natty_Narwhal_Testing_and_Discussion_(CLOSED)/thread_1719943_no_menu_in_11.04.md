---
title: "no menu in 11.04"
date: 2011-04-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by varun23 on 2011-04-02
hi,

i just upgraded to 11.04 beta, but i do not see Unity or Gnome. How can I go about fixing this?
I did get a message that bclr was not updated when i first booted into 11.04.

Any help is appreciated.

Thanks,
varun

---

### Post by giant420 on 2011-04-02
If you dont see gnome or unity, What do you see?

---

### Post by varun23 on 2011-04-02
i can only see the desktop. i can open the files on the desktop, but no menus.

---

### Post by varun23 on 2011-04-02
update on problem:

when i boot into fail safe graphics mode i get the following message:

" Ubuntu is running in low graphics mode

Your screen, graphics card and input device settings could not be detected correctly. You will need to configure them yourself"

Clicking OK brings up another menu with options to"

Run Ubuntu in low graphics mode ...
Reconfigure graphics


Choosing "Run Ubuntu in low graphics mode ..." brings up the unity interface but the desktop width and height is lesser than the screen width and height (desktop does not fill the monitor)

any thoughts?

---

### Post by cariboo on 2011-04-02
You are probably running the Classic desktop, you need to enable 3D graphics in order to use Unity. Click the Home button (the Ubuntu logo) in the top left corner and select System->Administration->Additional Drivers, and see if there is a closed source driver available. If there is nothing available in additional driver, could you let us know what grahics adapter your system has. If you don't know, open a terminal and type:

```
lspci | grep VGA
```

and paste the results in your next post.

---

### Post by varun23 on 2011-04-02
i installed unity through synaptic and i am now able to use unity through failsafe - low graphics mode. however for this to work properly (run unity so that it takes up the full resolution of the monitor) i had to uninstall the proprietary driver. 
booting into ubuntu regularly with the proprietary video driver uninstalled gives me -desktop without unity


reinstalling the proprietary driver and then booting into failsafe low graphics  - desktop WITH unity but i will not fill the monitor
re installing the proprietary driver and then booting into ubuntu regularly gives me - desktop WITHOUT unity

the output after i ran the code is:
varun@varundtop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Redwood PRO [Radeon HD 5500 Series]

---

