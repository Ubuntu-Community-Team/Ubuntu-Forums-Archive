---
title: "Ubuntu 14.04 installed yet cannot play a DVD film"
date: 2014-08-14
forum: Multimedia Software
---

### Post by rossdotcom on 2014-08-14
Hi there,
I have recently installed Ubuntu 14.04 onto a Dell Inspiron 1525 laptop and all seems to work fine except trying to play a commerical DVD film Basically nothing happens, I try VLC or Video Player, and absolutely nothing happens, the film does not play nor are there any error messages etc. What do I need to do to be able to play a DVD film - Many thanks
Phil Ross

---

### Post by christon74 on 2014-08-14
Hello Ross
Here is something you can try. Open a terminal window _ sudo su (your password)
sudo synaptic [or click on synaptic to launch it quicker] then search for restricted extras and select them for download. This should do the trick_

---

### Post by kc1di on 2014-08-14
Hi Phil and welcome to Ubuntu,
You will have to install some proprietary Codecs to get DVD Playback.  Ubuntu can't ship them by default because in some countries it's illegal to install them
so install at your own risk. [ here is the page]("https://help.ubuntu.com/community/RestrictedFormats") that tells you how to do it - good Luck.

---

### Post by coffeecat on 2014-08-14
*Thread moved to **Multimedia**.*

Follow the link in kc1di's post. You need to install ubuntu-restricted-extras (you can use the Software Centre - you don't need Synaptic if you don't want it) but then you must run the install script for libdvdcss. If you don't do the latter, you won't be able to play commercial encrypted DVDs.

---

### Post by rossdotcom on 2014-08-14
Hi Guys and thanks so much.
I have attempted to download the packages etc ... and everything seems to go well until I receive this ...

"Data files for some packages could not be downloaded

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

ttf-mscorefonts-installer

This is a permanent failure that leaves these packages unusable on your system.  You may need to fix your Internet connection, then remove and reinstall the packages to fix this problem."

I am not sure what to do next ...?
Look forward to hearing from you
Phil Ross

---

### Post by coffeecat on 2014-08-14
The ttf-mscorefonts-installer package is included in the metapackage ubuntu-restriced-extras but is not needed for DVD playing or for multimedia. Nevertheless, it is a useful thing to have as it installs the MS core fonts which are needed to render many webpages the way the designers intended, and also necessary if you want Times New Roman or Arial, for example, in word processing. For the installer to install the actual fonts you have to agree a Microsoft EULA because of licensing restrictions. This is really only a formality. My guess is that you missed the EULA or perhaps aborted the installation of ubuntu-restricted-extras before it completed.

Let's hope it was the former. Open a terminal and run this command:

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

You will be prompted for your password but it will not be echoed to the screen. Just type it in and press ENTER. Don't leave the terminal unattended. After a few seconds you will be prompted with the EULA. Press the tab key to highlight OK and then ENTER. At the next screen use the left arrow key to highlight yes, and then ENTER.

If you don't see the EULA, post back and we'll add another command. Also - are your DVDs playing now?

---

### Post by rossdotcom on 2014-08-14
Hiya,
Many thanks - I have sorted out the ttfmscorefonts ... etc. As for DVD playback, I have downloaded and installed everything recommended so far that I can see and unfortunately the DVD wont play automatically, I have to open up VLC seperately with the DVD loaded and then click on the play button many times ... then eventually the film seems to load and play perfectly. Any suggestions as to how to get it to play automatically will be gratefully received. 
Thanks again - you are all stars !
Regards,
Phil

---

### Post by coffeecat on 2014-08-14
VLC isn't the only video player capable of playing DVDs. Search for "videos" in the dash for what used to be called Totem and is now called - er - Videos. Now that you have installed the restricted codecs and the libdvdcss library it should cope with commercial DVDs. Also, install smplayer, another capable general purpose video app. You may find one of them better than VLC for your purposes.

I must admit, I rarely play DVDs in Ubuntu now, so others will probably have better ideas.

---

### Post by yancek on 2014-08-14
You should be able to set that in the System Settings.  I'm using 12.04 so I don't know if this has changed but it has a 'Details' option under System Settings with a Default Applications option where you can set the the default player for video, music, etc.

---

