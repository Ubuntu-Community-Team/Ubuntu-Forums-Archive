---
title: "[SOLVED] Java Runtime Environment Plugin Problem"
date: 2008-07-12
forum: Multimedia Software
---

### Post by AlexPozz26 on 2008-07-12
Hi,

Every time I visit a website using Firefox that has a Java application, it says that I need to install a missing plugin. When I click "install missing plugin," it says that the plugin is not available, and that I can't install it.

Please help,

Alex

---

### Post by gandaran on 2008-07-12
open your synaptic package manager and look for **sun-java6-plugin** just check-mark this item for install and click the apply button, all the rest of dependencies like java jre and java bin will be also installed.
this is if you running ubuntu 32-bits, for amd64-bits systems you have to install the iced-tea-plugin as there is no 64-bits sun java.
if you don't find the sun-java package in synaptic make sure you have all the repositories enabled and click the refresh/reload button.

---

### Post by AlexPozz26 on 2008-07-12
I did both of these things, and I still get a message telling me that I need to install a plugin on Firefox.

---

### Post by gandaran on 2008-07-12
> **AlexPozz26 said:**
> I did both of these things, and I still get a message telling me that I need to install a plugin on Firefox.

which firefox are you using FF3 OR FF2? and the ubuntu os version?

---

### Post by AlexPozz26 on 2008-07-12
I'm using Firefox 2, on Ubuntu 8.04

---

### Post by gandaran on 2008-07-13
> **AlexPozz26 said:**
> I'm using Firefox 2, on Ubuntu 8.04

find this **libjavaplugin.so** file in your file system (java plugin) and make a copy to /usr/lib/mozilla/plugins folder, it's just that simple, it'll work.
normally you find this file in /usr/lib/xulrunner-1.9/plugins/libjavaplugin.so, but I don't know if the java plugin is installed if you don't have firefox 3

---

### Post by AlexPozz26 on 2008-07-13
I found the file on my system, and upon trying to paste it into the mozilla plugins folder, It will not allow me. I "copied" the file from its original location, but when i click "paste," the paste option is grayed out and will not let me paste into the mozilla plugins folder.

---

### Post by gandaran on 2008-07-13
you need root permission to do this, type **sudo nautilus** in the terminal/console and press enter.

---

### Post by AlexPozz26 on 2008-07-13
sudo nautilus allowed me to copy and paste the file to where you specified, however, the same problem still persists :-(

---

### Post by gandaran on 2008-07-13
> **AlexPozz26 said:**
> sudo nautilus allowed me to copy and paste the file to where you specified, however, the same problem still persists :-(

did the file properties change while coping/pasting? does the file look the same as the original one?
it should work in the /usr/lib/mozilla/plugins folder, but you can also try other plugins folders like /usr/lib/firefox (or firefox2) plugins.
I have it working in /usr/lib/flock/plugins, flock is a firefox 2 web-browser clone.

edit:
    if all of this does not work for you, delete the libjavaplugin.so file you copied/pasted.
open the terminal/console and type the following commands.
first one
  **cd /usr/lib/firefox/plugins**
second one
  **sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so**
hope this will work!

---

### Post by AlexPozz26 on 2008-07-13
Ok, java seems to be working now...and it also seems that the website I was testing it on was bad anyway, so the problem may have been solved a few posts back ](*,)    thanks a bunch for your help, though!

---

### Post by gandaran on 2008-07-13
glad you got it working, please mark the thread as solved.

---

### Post by desideratha on 2008-07-30
I have the same problem, try all the solutions above and nothing works! :confused: i am utterly frustrated. Help anyone please...

---

### Post by gandaran on 2008-07-30
> I have the same problem, try all the solutions above and nothing works!  i am utterly frustrated. Help anyone please...

how about some details, ubuntu version and firefox version?

---

### Post by desideratha on 2008-07-30
ok,

Ubuntu studio, latest i think 8 
firefox 3

thanks

---

### Post by gandaran on 2008-07-31
> **desideratha said:**
> ok,

Ubuntu studio, latest i think 8 
firefox 3

thanks

if you running firefox 3 with ubuntu 8.04 then you should have no problem at all with java.
open your synaptic package manager, scroll down to **sun-java6-plugin** package, if it's not installed, check-mark for install and click the apply button, this is if have ubuntu 32-bits system, for 64-bits just install the icedtea-java plugin.
if it's 32-bits, install only sun-java6 packages and remove any open-java/open-jdk packages.

---

