---
title: "EnvyNg on Jaunty"
date: 2009-04-24
forum: Multimedia Software
---

### Post by Boludinux on 2009-04-24
Hi I just Intalled Jaunty tried to run EnvyNG to install my Nvidia 4mx 440, I had no problems installing it on kUbuntu Hardy and UbuntuStudio Intrepid but now I get this:

[php]ariel@ariel-desktop:~$ envyng -t


 +-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
 +----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version | Compatible | Recommended |
 |----------------------------------------------------------------------------|
 | 0      | 180.44-0ubuntu1    | -                 | -          | -           |
 |----------------------------------------------------------------------------|
 | 1      | 173.14.16-0ubuntu1 | -                 | -          | -           |
 |----------------------------------------------------------------------------|
 | 2      | 96.43.10-0ubuntu1  | -                 | +          | +           |
 |----------------------------------------------------------------------------|
 | 3      | 71.86.08-0ubuntu1  | -                 | +          | -           |
 +----------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
2

Dowloading the packages...
[=======>                           10.1%                                      ]result could not be parsed
Error in function pulse
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 75, in pulse
    self.newObject.updateUi(percent)
  File "interface.py", line 65, in updateUi
    numHashes = int(round(numHashes))
TypeError: an integer is required
/usr/bin/envyng: line 4:  5649 Fallo de segmentación  sudo python interface.py
ariel@ariel-desktop:~$ 
[/php]I have read similar posts, I tried installing again the python package which was the only approximate solution I found but had not luck.

Any help will be appreciated.

---

### Post by ArgusVision on 2009-04-24
OK dumb question. Where did you get envyng? I looked in the "universe" repository where it should be, and it isn't there? 
  I used EnvyNG just fine in Hardy by installing from the repo. Did you add a hardy or intrepid "universe" entry to your /etc/apt/sources.list?
And do you think that might work?

   Thanks

---

### Post by Boludinux on 2009-04-24
I do have it on my universe repository, havent touched anything. 
An if try to install the intrepid version on Envy if says that it requires python << 2.6

---

