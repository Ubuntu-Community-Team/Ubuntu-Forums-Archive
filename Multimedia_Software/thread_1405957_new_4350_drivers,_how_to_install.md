---
title: "new 4350 drivers, how to install"
date: 2010-02-13
forum: Multimedia Software
---

### Post by karrank% on 2010-02-13
Running 8.04 and just installed a MSI 4350 radeon card. found the new drivers off amd.com but can't seem to find  a tutorial on how to install that I can follow correctly. installed on an ASRock 780full hd board. 

Got incomprehensible display until I figure this out. Does someone know where to point me?

Thanks for looking.

---

### Post by markbuntu on 2010-02-13
Here, try this.


**Step 1; Remove old drivers.**
Note: ATI recommends you uninstall the ATI Proprietary Linux
Driver before installing a newer version.

If you have installed the driver and it is giving you problems it may be mis-installed so removing it and starting again clean is often faster and easier than trying to figure out what went wrong.

If you are using a driver that you downloaded from the ati site and installed it using the installer there is a removal script that you can use:
```

sudo sh /usr/share/ati/fglrx-uninstall.sh

```


If you installed the driver using  Jockey (hardware manager) then that means the driver is from the Ubuntu repository and has been packaged a little differently so you will need to remove it as follows (you may also need to use this method if you used dpkg to build and install the driver):
```

sudo apt-get purge xorg-driver-fglrx fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx-dev

```
The driver also may replace the following files with proprietary versions so you may need to restore them to their generic state:
```

sudo apt-get --reinstall install libgl1-mesa-glx xserver-xorg-core

```

If you use Envy to install the driver, use Envy and chose remove completely.

If you are replacing an Nvidia card and used the nvidia proprietary driver the driver should also be removed completely BEFORE REMOVING THE CARD. This will save you a lot of headaches.

reboot into recovery kernel and use the fix-x option or "repair broken packages" to get to the generic VESA driver working.  You can verify that the VESA driver is in use by checking in /var/log/Xorg.0.log. 

**STEP 2:Shutdown the system and install the new card.**
If you are replacing an old card or installing a new card or adding a new card to a system that was previously using integrated graphics then you must enter the bios and make sure that the correct card is recognized and enabled and the IGP disabled. 

Boot up the system and again use the fix-x or repair broken packages option. This is necessary because even the VESA driver needs to be initialized again for a different card
...continue....
If you want you can check again in /var/log/Xorg.0.log to make sure everything is OK.
You may not have a maximum resolution display and no desktop effects but do not change anything yet, you still need to install the new driver.

**Step3:Install the new driver.**
Go to the ati site and download the latest driver for your card to your Desktop (You can also do this before you start)

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Open a terminal and navigate to the Desktop

```

cd Desktop

```
Make the installer executable by right clicking on it and choosing Properties/Permissions and checking the box next to Execute: and close the window.
Run the installer
```

sudo sh ./ati-driver-installer.....

```
You can finish the rest of the line with the full name of the driver file including the .bin. You will be asked for your password, just type it in and the installer should run. When the driver stops and asks you questions just hit enter.

After the driver is finished installing return to the terminal and type
```

sudo aticonfig --initial

```

You should get some message like "found uniitalized file xorg.conf blah bah blah....
 If you have an X2 card, which has 2 gpus, or multiple cards you should use
```

sudo aticonfig --adapter=all --initial

```
If you get an error you can try
```

sudo aticonfig --initial -f

```
This will force aticonfig to overwrite the old xorg.conf.

reboot

** Post Installation tips**
Do not use Preferences/Display or Screen Resolution to adjust your display. 
The driver comes with the Catalyst Control Center for adjusting the display and configuring the driver. It will be in your menu. You need to use the superuser mode to make most changes. If it does not launch from the menu you can launch it from a terminal with
```

sudo amdcccle

```
There is also the command line utility aticonfig which has more options than CCC and is useful for setting up crossfire and a bunch of other useful stuff you can do to tweak the driver. For a full list of aticonfig options you can use
```

aticonfig --help

```

Be very careful using these utilities, they can be a little buggy and do not like more than one change at a time before you reboot.

There are many old guides around and a lot of their advice is outdated. For one thing it is no longer necessary to build the packages yourself since the installer will now recognize Ubuntu and build the proper packages itself. Many of the old xorg.conf options they tell you to use are also no longer necessary and do not work for all cards so be very careful if you try them.

---

### Post by karrank% on 2010-02-14
Thanks for the advice! Will look into this & post any news.

---

### Post by karrank% on 2010-02-15
That did the trick, thanks for saving my bacon, Markbuntu

What had been holding me up was not "making the installer executable"--never knew about that til now.

How can we mark this as solved?

-sorry, just figured that last thing out.

---

### Post by heliophobus on 2011-07-22
Finally everything went well, until the "aticonfig" command/s. I get the error message "aticonfig: No supported adapters detected".
And without this command nothings seems to be working. When I try to start the CCC it says: "  p, li { white-space: pre-wrap; No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."


:/


Can anyone help me? Thanks in advance!

---

