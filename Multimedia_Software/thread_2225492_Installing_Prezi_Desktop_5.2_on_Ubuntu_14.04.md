---
title: "Installing Prezi Desktop 5.2 on Ubuntu 14.04"
date: 2014-05-21
forum: Multimedia Software
---

### Post by majdi on 2014-05-21
I had Prezi Desktop 4 installed and working on Ubuntu 12.04. I have recently installed Ubuntu 14.04 and tried repeating the install steps for the latest version of Prezi Desktop 5.2 on my Ubuntu 14.04. But I'm getting the following error when trying to run Prezi;

$ sudo /opt/adobe-air-sdk/bin/adl -nodebug /opt/airapps/prezi-desktop/META-INF/AIR/application.xml /opt/airapps/prezi-desktop

(adl:3021): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(adl:3021): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(adl:3021): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(adl:3021): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
error while loading initial content

Has anyone got Prezi Desktop 5 working on Ubuntu 14.04?

I did the following to install it;

1. Installed getlibs-all.deb

2. Add the following lines to your /etc/apt/sources.list This will make it possible to install other needed packages

# Added by Majdi, for installing libhal-storage1 to run Prezi
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) lucid main 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main

3. sudo apt-get update

Install the following packages;

sudo apt-get install libhal-storage1 libgnome-keyring0 lib32nss-mdns lib32z1 lib32ncurses5 lib32bz2-1.0 libasound2 libcanberra-gtk-module:i386

4. Run the following comands

sudo getlibs -l libgnome-keyring.so.0.2.0

sudo ln -s /usr/lib/i386-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0

5. Download Adobe AIR from the latest Adobe release for linux:

[http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRSDK.tbz2](http://airdownload.adobe.com/air/lin/download/2.6/AdobeAIRSDK.tbz2)

Create the folder /opt/adobe-air-sdk/
Move the downloaded file to this folder then extract it using

sudo tar -xjvf AdobeAIRSDK.tbz2

6. Download the source
Download the latest Mac OS X version using the following link and choosing the right version number which you find in the release notes:

[http://prezi-a.akamaihd.net/desktop/Prezi_5.2.0.dmg](http://prezi-a.akamaihd.net/desktop/Prezi_5.2.0.dmg)

Extract the dmg file using 7z

sudo apt-get install p7zip-full

run the command;
7z x Prezi_5.2.0.dmg

You will get

0.hfs
run the command;
7z x 0.hfs

It will extract files to the following folder; Prezi

7. Edit application.xml

Prezi/Prezi.app/Contents/Resources/META-INF/AIR/application.xml

from <application xmlns="http://ns.adobe.com/air/application/3.8">; 
To <application xmlns="http://ns.adobe.com/air/application/2.6">;

8. Create folder /opt/airapps/prezi-desktop

move the contents of Resources to /opt/airapps/prezi-desktop
Prezi/Prezi.app/Contents/Resources

9. Create a file called /usr/share/applications/prezi-desktop.desktop with the following content:

[Desktop Entry]
Name=Prezi Desktop
Exec=/opt/adobe-air-sdk/bin/adl -nodebug /opt/airapps/prezi-desktop/META-INF/AIR/application.xml /opt/airapps/prezi-desktop
Comment=An application for creating canvas presentations
Type=Application
StartupNotify=true
Path=/opt/airapps/prezi-desktop
Icon=/opt/airapps/prezi-desktop/assets/icon/app/icon_48x48.png
Categories=Office
Terminal=false

---

### Post by majdi on 2014-05-22
Fixed the error;

Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

By installing;

sudo apt-get install gtk2-engines-murrine:i386
Now I'm left with;

(adl:3021): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
error while loading initial content

Anyone has a fix for this?

---

### Post by elcalamar on 2014-08-26
Hello there,
I am not able to start Prezi. I get the following error: error while loading initial content
Based on search it seems like there is something wrong with the application.xml file, but I do not know what or how to fix it. Anyone having the same issue? If you were able to fix it, could you please share the solution?
Thank you!

---

### Post by ibjsb4 on 2014-08-26
And you are not getting this?

[ATTACH=CONFIG]255851[/ATTACH]

There does seem to be a work-a-round.

[https://getsatisfaction.com/prezi/topics/installing_prezi_desktop_5_2_on_ubuntu_14_04](https://getsatisfaction.com/prezi/topics/installing_prezi_desktop_5_2_on_ubuntu_14_04)

Good luck

---

### Post by juan-magana-org on 2014-10-12
I haven't been able to install Prezi 5, but following those steps and the link to the previous version works for me without problems:

[http://prezi-a.akamaihd.net/desktop/PreziDesktop4.6.0.dmg](http://prezi-a.akamaihd.net/desktop/PreziDesktop4.6.0.dmg)

My guess is that since they don't maintain AdobeAir any longer, this is causing issues with new versions.

Hope it helps.

---

