---
title: "HOWTO:  TVUplayer under Wine with Channel List"
date: 2008-10-10
forum: Multimedia Software
---

### Post by mocha on 2008-10-10
I was trying to get the Windows TVUplayer P2P TV program to work under Wine and was having problems with the channel list showing up within the program.  I finally figured out a way to do it and thought I would share with everyone.

Install version 2.2.3 of TVUplayer using Wine.  Search Google for "TVUPlayer2.3.3beta2.zip" and you should find it.  I didn't try with a newer version, perhaps the newer versions work, I don't know.

Open the Wine configuration tool and make an applications settings entry for the TVUplayer.exe under your ~/.wine/drive_c/Program Files

Click the TVUPlayer.exe on the applications tab, switch to Windows NT 4.0 as the windows version.
Then go to the Graphics tab and make the following changes:
Uncheck "Allow window manager to decorate the windows"
Uncheck "Allow window manager to control the windows"
Check "emulate a virtual desktop", set it to 800x600
Uncheck "Allow Pixel Shader (if supported by hardware)"

Click Okay.

Now you have to execute the TVUplayer from the launcher in the Wine menu.  You need to execute it and quit it about 3 times.  The 3rd time you run it you should see the channel list text within the application.

It's strange, the fonts within the channel list tend to change size and face when you follow this procedure.  Usually the first time you run it there is no text, the second time it is a small unreadable text, and usually by the third time it is a readable text.

So anyway, once you can see the text, double click the channel you want to watch and then you should see the video within the player window, then run vlc or mplayer like this:

vlc [http://127.0.0.1:8901](http://127.0.0.1:8901)

This method will open vlc (or mplayer) and give you audio in sync and allow you to go fullscreen, or move it to a second monitor, or whatever you want...

I'd appreciate any feedback or suggestions, especially if someone can figure out why the channel list does such strange things with the fonts.

---

### Post by prince_niceguy on 2008-10-30
thank you... wanted to see some india vs australia test match :)... now i am able to watch it using the beta version... the latest version does not work gives some weird erros....

---

### Post by Easy Rider on 2009-07-05
Hello Mocha ...
I am using Ubuntu 9.04 Kernel 2.6.28-13-Generic and I have tried installing an older version of TVUPlayer (2.3.2beta19) and also the latest beta version.  When I click on the icon to start TVU (both versions, separately) I would get nothing, just my desktop image, after I tried what you suggested, I would get an 800x600 blue screen with the TVU icon for a second or two, then again nothing.  I had uninstalled and rebooted between the two different version installs.

My files are located: /home/[name]/.wine/dosdevices/c:/Program Files/TVUPlayer.

I also have the latest version of Windows Media Player for Ubuntu installed.  Any help or thoughts would be greatly appreciated. I have TVU on Windows XP and really enjoy the programming.

Thanks .... Easy Rider

---

### Post by prince_niceguy on 2009-07-05
check this [out....]("http://linux4humanbeing.blogspot.com/2009/04/how-to-install-tvuplayer-on-linux.html") I used it and the installation was a breeze...

---

