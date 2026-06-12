---
title: "Need Help With Graphics Card"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Ranja on 2008-05-03
Hello. I need help installing drivers for my Radeon 2600 HD graphics card. I downloaded the file "ati-driver-installer-8-4-x86.x86_64.run" from ATI's website, but when I try to run it, I get "gedit has not been able to detect the character coding. Please check that you are not trying to open a binary file. Select a character coding from the menu and try again." It only gives me two options for character coding and neither one works. What Do I Have To Do To Make This Work. Thanks In Advance.

---

### Post by divague on 2008-05-03
try openning a terminal and typing:

sudo ./ati-driver-installer-8-4-x86.x86_64.run

---

### Post by Ranja on 2008-05-07
I tried to, but it keeps telling me "command not found".
What do I do? My linux is running in low graphics mode and it's driving me nutty!

---

### Post by divague on 2008-05-08
maybe makeing it executable

chmod +x ati-driver-installer-8-4-x86.x86_64.run

and then:

sudo ./ati-driver-installer-8-4-x86.x86_64.run

if that doesn't work take a look at these instructions
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by Ranja on 2008-05-08
I don't know anything about making it an executable, BUT, the wiki article helped greatly. I followed all instructions and I am finally out of the "low-graphics mode". Here is the problem now. When I go to verify, the opengl string still reads mesa instead of ati. In my restricted drivers manager, it shows ati accelerated graphics driver as "enabled", but the status is "not in use". This is what I get in the terminal: $ sudo less /var/log/Xorg.0.log |grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) Unable to locate/open config file
(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to load module "type1" (module does not exist, 0)
(EE) open /dev/fb0: No such file or directory
(EE) AIGLX: Screen 0 is not DRI capable
The article does not mention any of this. What next?

---

### Post by lessgov2007 on 2008-05-09
Not 100% sure about this but you might try...
 

sh ati-driver-installer-8-4-x86.x86_64.run

---

