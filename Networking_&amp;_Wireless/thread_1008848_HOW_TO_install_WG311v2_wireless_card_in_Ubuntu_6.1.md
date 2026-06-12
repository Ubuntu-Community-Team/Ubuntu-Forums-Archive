---
title: "HOW TO: install WG311v2 wireless card in Ubuntu 6.1"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by rmcghee on 2008-12-11
For the complete newbie, step-by-step guide

Assumptions:
------------

1. You are new to UNIX but have familiarity with computing
   environments (navigating a file system, editing files,
   scrolling through lists)
2. Ubuntu 6.1 has just been installed and booted
3. You remember the password you used during installation
4. You have your router information handy (SSID, WEP key, etc.)
5. You have your installation CD for wg311v2 or have downloaded
   the wg311v2 driver files for Windows and have them (unzipped)
   on a CD, DVD or USB stick.


Overview: (step-by-step guide is below)
---------------------------------------

1. Install ndiswrapper
   a. Load package: ndiswrapper
   b. Launch a terminal window
   c. Install package: ndiswrapper

2. Edit the interface file

3. Install driver files for wb311v2

4. Configure the system

5. Reboot

6. Test


------------------------------------------------------------------

1.  Install ndiswrapper
-----------------------
Note: ndiswrapper allows you to use a driver that is not
specifically supported in Ubuntu by the manufacturer.


1a. Load the package: ndiswrapper
---------------------------------
Note: ndiswrapper is on the installation CD, so you can just
load it (no network connection necessary).

After Ubuntu has booted (desktop appears and mouse responds):
Insert your installation CD, DVD or USB stick for wg311v2.
After a few seconds, a pop-up window will appear:
"A volume with software packages has been detected"
Click the button to "start the package manager"
When asked, enter your password and click OK
(Read introduction, click Close when finished.)

When the Synaptic Package Manager window pops up,
on the left, select "All" (should already be selected).
On the right, scroll down to find "ndiswrapper-utils-1.8"
and "check" the box next to it, then click "Mark for
installation" when the pop-up appears.  When the "Mark
additional required changes?" dialog appears, click the
"Mark" button. 

In the Synaptic Package Manager, find the "Apply" control
(green check near top center) and click it.
When the "Summary" dialog appears, click the "Apply" button.
Pop-ups will inform you of the progress. Finally, you will
click "Close" on the "Changes applied" dialog.

Now, you can close the Synaptic Package Manager and any
other windows that are open on the desktop.

------------------------------------------------------------------

1b. Launch a terminal window
----------------------------
Note: We need "super-user" privileges for system operations.
So, we will use the "super-user do" command (sudo) below.

If you already know how to launch a terminal and are familiar
with prompts, launch a terminal and proceed to step 1c.

At the top left of the screen on the menu bar is the
"Applications Menu."  Click "Applications", then navigate to the
"Accessories" submenu and click "Terminal".
Shorthand: Applications->Accessories->Terminal

A "terminal" in UNIX provides a way to type commands at a prompt.
When the "terminal" pops-up, a command prompt will appear that
looks something like this:

myname@mysystem:~$

To keep things clear below, you can change your prompt.  This
will not permanently change your prompt.  If you make a mistake
changing your prompt, you can just close the window and bring up
a new terminal.  The purpose here is to make your prompt look
*exactly* like the prompt in the instructions below.

Note that upper and lower case are significant in Unix so you
can't substitute one for the other.  Carefully type the following
after the prompt (note the placement of the single quotes):

myname@mysystem:~$ PS1='prompt> '
prompt>

If you see, "prompt> " for the prompt now, proceed to the next
step.  If not, carefully check what you did and try again, start
over or skip the prompt-setting step.

1c. Install package: ndiswrapper:
---------------------------------

prompt> sudo apt-get install ndiswrapper-utils
... 
(several lines of output)
... 
Do you want to continue [Y/n]? Y
...
prompt>

------------------------------------------------------------------

2. Edit the interface file:
---------------------------

You need to edit the file: /etc/network/interfaces:
prompt> sudo gedit /etc/network/interfaces

Add the following "wireless" lines at the bottom of the file:
    Replace <stuff in angle brackets> with your correct values:
    Don't include Notes:

wireless-mode managed
wireless-essid <your SSID from your wireless router>
wireless-channel <your channel>  Note: check your router
wireless-rate 54MBs              Note: omit if negotiated
wireless-key1 <your router WEP key> Note: or other key
wireless-defaultkey 1            Note: may have more than one key
wireless-keymode open            Note: open/shared (see router)

So, the added lines might look like this:

wireless-mode managed
wireless-essid teddybears
wireless-channel 1
wireless-rate 54MBs
wireless-key1 12345678901234567890123456
wireless-defaultkey 1
wireless-keymode open

Now, save the file (as interfaces) and close the Text Editor:
Shorthand: File->SaveAs
or Click Save

------------------------------------------------------------------

3. Install driver files for wb311v2
-----------------------------------

Insert the driver disk that came with your network card in the CD
drive (or insert some CD or USB stick that has the drivers,
unzipped and ready to go...).  In a few seconds, a File Browser
window will pop. You can close the File Browser.

Navigate to the location where the file "wg311v2.inf" is.
(If you know how to do this, go ahead, then skip to step 4.)

First, change directory to where the drivers are:
prompt> cd /media/cdrom
or
prompt> cd /media/usbdisk

For example, if you have driver version 1.2b6 on a USB stick:
prompt> cd /media/usbdisk
prompt> dir
1.2b6

prompt> cd 1.2b6
prompt> dir
Acrobat     autorun.exe Boingo Driver     Utility
autorun.apm autorun.inf Data   setup.exe

prompt> cd Driver
prompt> dir
Windows 2000  Windows 90  Windows ME  Windows XP

Note: quotes are used here because there's a space in the
directory name:
prompt> cd "Windows XP"
prompt> dir
fw1130.bin   FwRad17.bin   netwg311_XP.sys
FwRad16.bin  netwg311.cat  wg311v2.inf
prompt>

When you've found wg311v2.inf in the current directory.
proceed to the next step.

------------------------------------------------------------------

4. Configure the system
-----------------------

Use ndiswrapper to "wrap" and install the driver:
Note: -i means install, -l means list, -h means help
(If you make a typo error, use -h to see -e option to
fix your error)

prompt> sudo ndiswrapper -i wg311v2.inf
Installing wg311v2
prompt> sudo ndiswrapper -l
wg311v2        driver installed, hardware present

Write module alias for "all devices"
prompt> sudo ndiswrapper -da

Write configuration for modprobe:
prompt> sudo ndiswrapper -m

Final steps:
Close the terminal window:
prompt> exit

Close any other open windows.
If you want to Remove your CD or USB stick safely, 
right click on the appropriate icon (CD or USB disk)
on the desktop and click "Eject".

------------------------------------------------------------------

5. Reboot
---------

Click the red power button at the top, right of the desktop, and
click Restart.

6. Test
-------

After restarting, click the Firefox icon on the menubar at the
top of the screen and navigate to your favorite website.

If you cannot surf, you need to carefully review these
instructions and review your router information.  If it still
doesn't work, you should visit "The Ultimate Guide" (see link
below) for more specific information and help with troubleshooting.

[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

---

