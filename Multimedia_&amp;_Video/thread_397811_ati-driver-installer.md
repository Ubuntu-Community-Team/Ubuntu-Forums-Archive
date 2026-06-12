---
title: "ati-driver-installer"
date: 2007-03-31
forum: Multimedia &amp; Video
---

### Post by captgadget on 2007-03-31
I downloaded ati-driver-installer-8.28.8.run to my desktop. I double click it and get a message like this: Could not open the file /home/captgadget/Desktop…iver-installer-8.28.8.run using the Unicode (UTF-8) character coding.

Can someone tell me what I need to do now?

Thank you

---

### Post by r4ik on 2007-03-31
Try Envy,

 What is Envy?:

"Envy" is an application for Ubuntu Linux written in Python and PyGTK which will:
1) detect the model of your graphic card (ATI and Nvidia cards are supported). However "Manual installation" is also available
2) download the right version of the proprietary driver for your ATI or Nvidia card from ATI or Nvidia's websites
3) handle the dependencies (compilers, OpenGL, etc.) (according to your OS version and kernel) required to build the module
4) install/uninstall the driver
5) set up your xorg.conf (i.e. the configuration file of the Xserver) for you (according to your system specifications)
6) restart the Xserver for you (if you wish so) (this feature is available only in the textual interface)



[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Joseph IronEagle on 2007-03-31
Look here    [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) 

This where I solved my driver install trouble by following the appropriate manual install guide.  
Perserverance has it's own reward good luck.

---

### Post by cantormath on 2007-03-31
> **captgadget said:**
> I downloaded ati-driver-installer-8.28.8.run to my desktop. I double click it and get a message like this: Could not open the file /home/captgadget/Desktop…iver-installer-8.28.8.run using the Unicode (UTF-8) character coding.

Can someone tell me what I need to do now?

Thank you

try envy

---

### Post by crudolphy on 2007-04-01
I used the following HowTo very successfully:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

ATI Radeon 9600 Pro with 128MB - Asus A7N8X Deluxe Mobo - 1GB Corsair TwinX ram - Dapper 6.06 - 2.6.15-28-386 kernel

> lspci -n | grep 300
0000:02:00.0 0300: 1002:4150

> lspci | grep VGA
0000:02:00.0 VGA compatible controller ATI Technologies Inc. RV350 AP [Radeon 9600]


Prior to installation of this driver if I ran glxgears my fps was about 160fps, post install my frame rates are 4100 to 4200 fps.

Since installation of this driver I have installed XGL and Beryl, with great success.  The only problem I have with XGL/Beryl is if you copy and paste with your mouse to fast ie:

> left click to select text
right click on selected text to bring up context menu
left click selection in context menu such as copy
move mouse pointer
right click to bring up context menu again
left click to choose selection such as paste

It will freeze up your Xsession.  I have to then "CTL-ALT-F1" to a tty, login in as root, and restart GDM.

I have never used "Envy" so can't comment but based on previous post if it works that would make things real easy.:) 

Hope this helps

Chuck

---

### Post by kellemes on 2007-04-02
> **captgadget said:**
> I downloaded ati-driver-installer-8.28.8.run to my desktop. I double click it and get a message like this: Could not open the file /home/captgadget/Desktop&#8230;iver-installer-8.28.8.run using the Unicode (UTF-8) character coding.

Can someone tell me what I need to do now?

Thank you

chmod +x ati-driver...
./ati-driver...

I got this driver working fine using there own installer.

---

### Post by sdowney717 on 2007-04-02
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
this does not work with my radeon 9600 in feisty.

After I go thru the process I am stuck with mesa.

Envy works well, when will Envy work with feisty?

---

