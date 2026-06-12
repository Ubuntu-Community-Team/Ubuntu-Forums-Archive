---
title: "How-to easy mythtv install to Kubuntu 18.04"
date: 2018-06-19
forum: Multimedia Software
---

### Post by vidtek on 2018-06-19
Setting up mythtv on kubuntu 18.04  19th June 2018

In their infinite wisdom, the developers of KDE have crippled Dolphin, so install Thunar to facilitate the sudo functions removed from Dolphin-(this will save you lots of unnecessary angst).

Ensure your tv card or usb stick and video card drivers are correctly installed, test with Kaffeine.

For nvidia- add to: /etc/X11/xorg.conf the following if you have small fonts on login screen:

 add these lines to "monitor option"

Option         "UseEdidDpi" "FALSE"
Option         "DPI" "100 x 100"


and to "Screen" section to stop cogging on video playback:

eg. Option         "metamodes" "1920x1080_50 +0+0 {ForceCompositionPipeline=On, ForceFullCompositionPipeline=On}"
(This last can also be changed from the nvidia-settings > advanced tab via the gui)

Mythtv should be in the repos, but if not for you, or you want a different version add the repo:  sudo add-apt-repository ppa:mythbuntu/0.XX  where XX is your version required.

Then sudo the following commands:

apt-get install mythtv-backend-master;mythtv;mythtvplugins;mythtv-theme-mythbuntu  # this is just for a backend only, if you want a combined be/fe add mythtv to this command.

then sudo the following with your users names in place of the asterisks

adduser *** mythtv
adduser *** video
adduser *** audio

find password generated on install in:
 /etc/mythtv/config.xml
eg. NPUjqo3j

Reboot

Ensure all copies of config.xml are identical or--- 
delete all except one and create symlinks to it from these locations:
/etc/mythtv
/home/mythtv/.mythtv
/home/<your user>/.mythtv
/home/root/.mythtv

Run mythtv-setup using above password

then change password as below to your own if required.

# mysql -u root -p mysql
myqsl> GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'localhost'
    -> IDENTIFIED BY 'mythtv' WITH GRANT OPTION;
mysql> UPDATE user SET authentication_string=PASSWORD('YOUR_PASSWORD_HERE') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
mysql> quit

reboot

Then run mythtv-setup and complete configuration.

gotchas:

Folder permissions on the default/default/live/videos/ 
and all the other art directories ensure they are r/w

config.xml files, check ALL the above locations twice

If you find that your playback and mythtv menu gui are set to the same size but the all tv and video playback is in a box, make sure
on the setup configuration in the settings>appearance>theme-screen settings menu  the "use fixed window size" is ticked
this caused me many hours of head-scratching.


Tony

edit:  I have found Double Commander is almost as good as Dolphin for a gui file manager.  [https://doublecmd.sourceforge.io/]("https://doublecmd.sourceforge.io/")

It is in the repos so synaptic will have it.

30 July 2019 EDIT-
I have just re-installed my system using Kubuntu 19.04, and used this guide as a basis for mythtv installation.  19.04 allows root use of Dolphin after some tinkering, so one less aggravation to contend with there...   However the install command no longer works properly.  I found it would not install ```
mythtv: command not found
mythtvplugins: command not found
mythtv-theme-mythbuntu,mythtv: command not found
```

so I just used Synaptic to install them.
Tony

---

### Post by imeric on 2018-08-13
> **vidtek said:**
> Setting up mythtv on kubuntu 18.04  19th June 2018

In their infinite wisdom, the developers of KDE have crippled Dolphin, so install Thunar to facilitate the sudo functions removed from Dolphin-(this will save you lots of unnecessary angst).

Ensure your tv card or usb stick and video card drivers are correctly installed, test with Kaffeine.

For nvidia- add to: /etc/X11/xorg.conf the following if you have small fonts on login screen:

 add these lines to "monitor option"

Option         "UseEdidDpi" "FALSE"
Option         "DPI" "100 x 100"


and to "Screen" section to stop cogging on video playback:

eg. Option         "metamodes" "1920x1080_50 +0+0 {ForceCompositionPipeline=On, ForceFullCompositionPipeline=On}"
(This last can also be changed from the nvidia-settings > advanced tab via the gui)

Mythtv should be in the repos, but if not for you, or you want a different version add the repo:  sudo add-apt-repository ppa:mythbuntu/0.XX  where XX is your version required.

Then sudo the following commands:

apt-get install mythtv-backend-master,mythtv,mythtvplugins,mythtv-theme-mythbuntu

then sudo the following with your users names in place of the asterisks

adduser *** mythtv
adduser *** video
adduser *** audio

find password generated on install in:
 /etc/mythtv/config.xml
eg. NPUjqo3j

Reboot

Ensure all copies of config.xml are identical or--- 
delete all except one and create symlinks to it from these locations:
/etc/mythtv
/home/mythtv/.mythtv
/home/<your user>/.mythtv
/home/root/.mythtv

Run mythtv-setup using above password

then change password as below to your own if required.

# mysql -u root -p mysql
myqsl> GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'localhost'
    -> IDENTIFIED BY 'mythtv' WITH GRANT OPTION;
mysql> UPDATE user SET authentication_string=PASSWORD('YOUR_PASSWORD_HERE') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
mysql> quit

reboot

Then run mythtv-setup and complete configuration.

gotchas:

Folder permissions on the default/default/live/videos/ 
and all the other art directories ensure they are r/w

config.xml files, check ALL the above locations twice

If you find that your playback and mythtv menu gui are set to the same size but the all tv and video playback is in a box, make sure
on the setup configuration in the settings>appearance>theme-screen settings menu  the "use fixed window size" is ticked
this caused me many hours of head-scratching.


Tony

edit:  I have found Double Commander is almost as good as Dolphin for a gui file manager.  [https://doublecmd.sourceforge.io/](https://doublecmd.sourceforge.io/)

It is in the repos so synaptic will have it.

I wish I had read this post first it would have saved me hours of troubleshooting!!..Thx

---

