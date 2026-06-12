---
title: "How to change my screen refresh rate"
date: 2008-08-18
forum: Multimedia Software
---

### Post by Billnowar on 2008-08-18
My video card is Ati Radeon 7500.It's old enough.Fglrx doesn't support it.
    Yesterday I installed Ububtu8.04.Everything is OK.
    But the screen refresh rate is only 60Hz..And it cannot change.
    I tried to change like this
> Open the file /etc/X11/xorg.conf in your favorite text editor. I'll assume 

you are using nano for an editor as it is fairly straight forward: 
sudo nano /etc/X11/xorg.conf
Now look for a section in that file called Section "Monitor". Once you find this section, look at the lines of text between Section "Monitor" and EndSection. There should be two lines in there that begin with the words HorizSync and VertRefresh. If those lines don't appear there, don't worry. There is a good chance that we've found the problem already! You will need to gather two bits of information for your monitor now, either from your Monitor User's Manual, the command line, or from online. Finding these values usually just involves searching Google with the model of your monitor. One extensive list is at the Lapis forum We need the horizontal sync frequency (usually measured in kHz) and the vertical refresh rate (usually in Hz). Both of these values are typically given in a range such as "30-98 kHZ" or "50-160 Hz". Alternatively, if your monitor supports it, you can just run 

the following command (install the 'xresprobe' package if the command is not available): 
sudo ddcprobe | grep monitorrange
The first two values returned are your HorizSync rates, the second pair is your VertRefresh values. There are two ways to enter your monitor information into the file. One way is to run the following commands which will regenerate the file and ask you 

for the values in the process: 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
md5sum /etc/X11/xorg.conf |sudo tee /var/lib/xfree86/xorg.conf.md5sum
sudo dpkg-reconfigure -plow xserver-xorg
The second way is to simply add those values to our /etc/X11/xorg.conf file with a text editor. But first, lets make a backup of that file just in 

case an error is made: 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Editing this file so that it works involves adding two extra lines to the Section "Monitor" section of that file. For example, mine is shown below. 

Section "Monitor"
     Identifier         "FLATRON 995F"
     Option             "DPMS"
     HorizSync          30-96
     VertRefresh        50-160
EndSection
  Don't change anything that is written in the file for now. Just add the two lines. The snippet from my file is just an example and may not apply to your hardware. More importantly if your monitor is not detectable, the Identifier will be called `Generic Monitor`. In which case, don't change the Identifier to anything else otherwise X will fail to load and report that it can't find the a Monitor.  

Now save the file, close all open applications, and press CTRL-ALT-Backspace to restart X. Assuming all goes well, you will be prompted to log into your session again. (Note: If you do not want to shut down your current applications and at the same time enjoy a safer way of trying out your new configuration, you can try the advice on this page: [http://ubuntuforums.org/showthread.php?p=4211618](http://ubuntuforums.org/showthread.php?p=4211618)) 

  If you are using XFree86 then you needed to edit /etc/X11/XF86Config-4.  

(See this launchpad bug about low resolutions when horizontal/vertical sync frequencies are incorrect/missing for details about why this can happen and future work being done to prevent this problem in later versions of Ubuntu) Also if you have an issue where only 800x600 is available in the dropdown for screen resolution, then modifying the Modes line within the section in that file called Section "Monitor" and adding the required resolution could solve this. 

        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"

    But it didn't work!My screen refresh rate didn't  have any change.
    This is my xorg.conf
> Section "InputDevice" 
Identifier "Generic Keyboard" 
Driver "kbd" 
Option "XkbRules" "xorg" 
Option "XkbModel" "pc105" 
Option "XkbLayout" "cn" 
EndSection 

Section "InputDevice" 
Identifier "Configured Mouse" 
Driver "mouse" 
Option "CorePointer" 
EndSection 

Section "Device" 
Identifier "Configured Video Device" 
EndSection 

Section "Monitor" 
Identifier "Configured Monitor" 
Option "DPMS" 
HorizSync 30-72 
VertRefresh 50-160 
EndSection 

Section "Screen" 
Identifier "Default Screen" 
Monitor "Configured Monitor" 
Device "Configured Video Device" 
SubSection "Display" 
Depth 24 
Modes "1024x768" "800x600" "640x480" 
EndSubSection 
EndSection 

Section "ServerLayout" 
Identifier "Default Layout" 
Screen "Default Screen" 
EndSection
    I used to use windows,but I really want to use Ubuntu,Ubuntu is great!
    But the refresh rate is so low that my eyes can't stand!
    Can you help me?Thank u!  My English isn't good enough ,sorry..

---

### Post by tuxxy on 2008-08-18
Doesnt the ATI catalyst manager allow you to?

---

### Post by Billnowar on 2008-08-18
> **tuxxy said:**
> Doesnt the ATI catalyst manager allow you to?
My Video Card is very old.fglrx doesn't support it.
ATI catalyst manager can't detect it.

---

