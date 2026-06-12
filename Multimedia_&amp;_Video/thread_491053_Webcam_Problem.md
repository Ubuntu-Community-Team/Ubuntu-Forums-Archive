---
title: "Webcam Problem"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by Hilton on 2007-07-03
I have a dual-boot PC - Windows XP / Ubuntu Linux.

My NGS SpinCam 2 works perfectly with Windows but under Linux - nothing, not even the 'power-on' light.

Does this mean this particular Webcam is not recognized by Linux, or do I have to do something else - like install a driver (which NGS don't seem to have).

One program (forgotten which) said 'No Device Connected' which is obviously wrong, because it works under Windows.

Help please - Thanks.

I'm new to Linux, so nothing too complicated please

---

### Post by linuxwizard on 2007-07-04
Check these maybe can find something that will help
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

[https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam)

---

### Post by Hilton on 2007-07-05
Thanks for your help, but the suggested web page(s) may as well be in a foreign language.

The first instruction is - Add the following line to your** /etc/apt/sources.list**

Where is it?  What is it?  How do you do it?

Once again Linux is user-unfriendly.

Thanks

---

### Post by DannyW on 2007-07-05
sources.list is the name of the file you are wanting to edit. It is in the /etc/apt/ directory.

You have to open the file with root privileges with your favourite text editor (gedit in Ubuntu, kate in Kubuntu).

To do this open up the terminal and execute:
sudo gedit /etc/apt/sources.list

or

sudo kate /etc/apt/sources.list

sudo is used before a command to execute it as the root account, you will be prompted for your password.
gedit or kate is the text editor
/etc/apt/sources.list is the file to edit.

---

### Post by linuxwizard on 2007-07-05
What is a repository? What is the sources.list file?

Repositories are particular locations on the web which contain the thousands of packages (each containing programs, applications, etc) that you would need on your computer. The sources.list file contains the list of all the repositories that will be used to download packages in Synaptic (see SynapticHowto) and APT (see APTPage); it is located in /etc/apt/. Since /etc is the directory for system-wide configurations, you will require root privileges to edit it (see RootSudo). 

[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

---

