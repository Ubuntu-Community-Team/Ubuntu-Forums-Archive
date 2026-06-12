---
title: "how do i install the NVIDIA *.run package?"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by jklslvch on 2007-06-17
hey i tried to su root and sudo to execute init 3 but nothing happens when i type init 3 whats the deal?? how do i make the init command work i tried init 1 and that worked (killing everything though) becaues i want to install the nvidia drivers .run file i downloaded

---

### Post by Reugen on 2007-06-17
You can install the drivers through the repository: "sudo aptitude install nvidia-kernel-common nvidia-glx" (iI think youcan do this throught synaptic/adept as well.  Then run "sudo dpkg-reconfigure xserver-xorg"  in a terminal, and select nvidia when asked about driver.
If you want to use the official nvidia:
init 3 if for SuSe. what you need to to is close all the apps you have running in gnome or kde, then hit ctrl F1 which will bring you to a terminal.  from there you log in.  Then you type "/etc/init.d/gdm stop" subsitude gdm with kdm if your usng kubuntu.  Then change to the directory you downloaded the installer to eg:"cd ~/Desktop"-if you downloaded it to your desktop.  then type "sudo sh NVIDIAxxx.xxx.xx.run".  This will run the nvidia installer.

---

### Post by steveneddy on 2007-06-17
> **Reugen said:**
> what you need to to is close all the apps you have running in gnome or kde, then hit ctrl F1 which will bring you to a terminal.  from there you log in.  Then you type "/etc/init.d/gdm stop" subsitude gdm with kdm if your usng kubuntu.  Then change to the directory you downloaded the installer to eg:"cd ~/Desktop"-if you downloaded it to your desktop.  then type "sudo sh NVIDIAxxx.xxx.xx.run".  This will run the nvidia installer.

Yes - it has to be done from the terminal screen, not a terminal emulator in the Gnome environment.

There should be directions either with the file in a read me or on the nvidia website.

---

### Post by digz6666 on 2007-06-19
When installing NVIDIA *.run with commands (My shell is bash):
chmod +x NVIDIA *.run
./NVIDIA *.run
following error occured:
"Run as a root".

I'm an user of administrator group. I created user in root group and logged in. Then tried to install it but not work, same message returned. 

Then I tried to login as a root. I typed root in user name at Login screen.
"System administrators are not allowed to login from here" message returned.

How do I install NVIDIA driver?

---

### Post by deanjm1963 on 2007-06-19
First you need to have a root user passwd - open a terminal and type

sudo passwd root

and give yourself a root user password


Then need open up the login manager and allow root login.

Then you need to install build-essential and the kernel-headers for your particular kernel.

Log out to the login screen and hit Ctrl+Alt+F1 - which will put you in full screen terminal mode. Not a terminal in an active graphical session.

log in as root

type 

/etc/init.d/gdm stop

then

sh /path_to_where_driver_is/NV - then hit the tab key (it will fill in the rest of the NVIDIA-etc for you) then hit enter

Follow the prompts

Once done type

/etc/init.d/gdm start

I suggest doing a reboot at that stage.

Hope it works - works for me

---

### Post by Reugen on 2007-06-19
in your case you don't need to login to gui as root, you can't run the nvidia installer while an xserver is running.  to login as root at a terminal type sudo su.

---

### Post by cogadh on 2007-06-19
> **jklslvch said:**
> hey i tried to su root and sudo to execute init 3 but nothing happens when i type init 3 whats the deal?? how do i make the init command work i tried init 1 and that worked (killing everything though) becaues i want to install the nvidia drivers .run file i downloaded

At the top of this forum is a "HOW TO" sticky specifically for installing the nVidia drivers. Use "Method 2" from that doc to install the nVidia *.run package correctly.

**Note to everyone in this post:**
You do not need to login as root or create a root password to install this, it works perfectly fine using sudo. You will almost never need to login as root on Ubuntu, you can do everything root can using sudo.

---

