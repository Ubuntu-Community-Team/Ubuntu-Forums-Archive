---
title: "Flash Player - No Video"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by kshane on 2007-07-18
I have installed the Flash plugin.  Everything appeared to install properly.  When I attempt to watch a video online, I get only audio - no video...  I have uninstalled/re-installed and re-downloaded the most recent release. In looking through the forums, I found a checksum problem work-around which I used.  Nothing helps!  It continues to play sound, but no video.

Any ideas?

Thanks...

Kevin

---

### Post by NilsE on 2007-07-18
Are you using desktop effects?  Try turning it off and see if you get the video.

Either way, we can go from there but provide system details like video card, sound card etc.

---

### Post by Gremlinzzz on 2007-07-18
Post the video link .:guitar:

---

### Post by kshane on 2007-07-18
> **NilsE said:**
> Are you using desktop effects?  Try turning it off and see if you get the video.

Either way, we can go from there but provide system details like video card, sound card etc.

Not using the Desktop Effects.  

I have an AMD Sempron (1.6ghz) CPU 
Sis sound card built in to MB
ATI Radeon X-1650 graphjics card w/256MB
Running Feisty

Does that help?

THANKS in advance!

Kevin

---

### Post by kshane on 2007-07-18
Any Flash Video on Fox News  (foxnews.com)

---

### Post by Gremlinzzz on 2007-07-18
See if it works here
[http://www.earthcam.com/](http://www.earthcam.com/)

---

### Post by NilsE on 2007-07-18
OK, lets start with the basics.

```
How did you install Flash?

```
```
When you do an about:plugins on the location bar do you see this?

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
```

```
And does it show as enabled?
```

```
Does it work on any sites?

```
Go to the following site and try the flash and if it is not installed correctly Firefox will probably tell you to install so let it try.

[http://www.linspire.com/file_types/filetypes.php](http://www.linspire.com/file_types/filetypes.php)

---

### Post by kshane on 2007-07-18
> **Gremlinzzz said:**
> See if it works here
[http://www.earthcam.com/](http://www.earthcam.com/)

Yes.  When I right-click on the picture, I get a LOT of menu options.  At Fox News (and most others) I get a very small menu with only an Options and About to click on.  "Options" has NO VIDEO settings...  Also, Fox spawns a new window for the player...  And still, video, no sound...

---

### Post by Gremlinzzz on 2007-07-18
If flashplayer is working on  earthcam then i don't think your problem is flash but media plugin. i wont go on fox news web site  out of moral principles so i;m guessing..
:guitar:

---

### Post by kshane on 2007-07-18
> **NilsE said:**
> OK, lets start with the basics.

```
How did you install Flash?

```

I used the installs shown here ...  [http://ubuntuforums.org/showthread.php?t=497826&highlight=flash+player](http://ubuntuforums.org/showthread.php?t=497826&highlight=flash+player)

```
When you do an about:plugins on the location bar do you see this?

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
```

Yes:
    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

```
And does it show as enabled?
```

Yes.

```
Does it work on any sites?

```

Yes, here:  [http://www.earthcam.com/usa/michigan/grandhaven/lakemichigan/](http://www.earthcam.com/usa/michigan/grandhaven/lakemichigan/)

Go to the following site and try the flash and if it is not installed correctly Firefox will probably tell you to install so let it try.

[http://www.linspire.com/file_types/filetypes.php](http://www.linspire.com/file_types/filetypes.php)

I get a video (picture) that doesn't change and there is sound.

---

### Post by kshane on 2007-07-18
> **Gremlinzzz said:**
> If flashplayer is working on  earthcam then i don't think your problem is flash but media plugin. i wont go on fox news web site  out of moral principles so i;m guessing..
:guitar:

(Believe me when I say I don't go there for the company)...  :)

---

### Post by NilsE on 2007-07-18
It just seems to me something is out of sync so I think at this point your best choice is to uninstall and reinstall Flash.

Try it this way in the terminal:

```
sudo apt-get --purge remove flashplugin-nonfree

sudo apt-get install flashplugin-nonfree

```

---

### Post by kshane on 2007-07-18
> **NilsE said:**
> It just seems to me something is out of sync so I think at this point your best choice is to uninstall and reinstall Flash.

Try it this way in the terminal:

```
sudo apt-get --purge remove flashplugin-nonfree

sudo apt-get install flashplugin-nonfree

```

Done..  Here's what I get:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Kevin

---

### Post by Gremlinzzz on 2007-07-18
first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

---

### Post by kshane on 2007-07-18
> **Gremlinzzz said:**
> first remove the old paste this in terminal
sudo apt-get remove flashplugin-nonfree
rm ~/.mozilla/plugins/*flash*
then download and save the new to the desktop click the link and get Option 1: .tar.gz
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)
now paste these commands in the terminal one line at a time and hit enter
cd Desktop
tar -xvzf install_flash_player_9_linux.tar.gz
sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/

Done!

I'm back to where I was at the beginning of this post.  

Any ideas?

---

### Post by jacob01 on 2007-07-18
did you install macromedia flash player most online vids are macromedia

[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

does it say flash player is installed
if not thats your problem

another thing try to install the the flash player by downloading the installer from the website and installing i think itts a  shell script 
so download the file unzip cd to that directory and type                sudo sh flashplayer-installer                                   
download the tar.gz file from [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")

this is how i got it working and is working fine for me

---

### Post by kshane on 2007-07-18
> **jacob01 said:**
> did you install macromedia flash player most online vids are macromedia

[http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/)

does it say flash player is installed
if not thats your problem

Everything "appears" to be installed and working until I try Fox News videos and most other online content that spawns a viewer to a new window.

Here's what Mozilla says about the plugins:


[B]Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48
[U]
MIME Type [/U]	                           _Description_ 	                        _Suffixes _	_Enabled_
application/x-shockwave-flash 	Shockwave Flash 	       swf 	          Yes
application/futuresplash 	      FutureSplash Player 	     spl 	         Yes[/B]

(Didn't come out cleanly...)  But everything APPEARS to be working until....

Kevin

---

### Post by jacob01 on 2007-07-18
hmm just yesterday tried to watch a simpons the movie trailer lol and i could not so i installed shock wave flash player have you tried that
there are more than one type of flash player there are macromedia and shock wave and probably m,ore but those are the 2 main ones. for example youtbe uses macromedia flash player try to watch a vid on youtube.com

---

### Post by kshane on 2007-07-18
> **jacob01 said:**
> hmm just yesterday tried to watch a simpons the movie trailer lol and i could not so i installed shock wave flash player have you tried that
there are more than one type of flash player there are macromedia and shock wave and probably m,ore but those are the 2 main ones. for example youtbe uses macromedia flash player try to watch a vid on youtube.com

I get sound and video off youtube.

It seems to be when Flash spawns a new window to view a vid, I get sound and no video...

---

### Post by jhuff on 2007-07-19
Go to this thread and read about installing the  greasemonkey extension and the FoxNews Script.

[http://ubuntuforums.org/showthread.php?t=374836&highlight=Fox+News+Flash](http://ubuntuforums.org/showthread.php?t=374836&highlight=Fox+News+Flash)

It works great and it takes out the commercials.

---

### Post by kshane on 2007-07-31
> **jhuff said:**
> Go to this thread and read about installing the  greasemonkey extension and the FoxNews Script.

[http://ubuntuforums.org/showthread.php?t=374836&highlight=Fox+News+Flash](http://ubuntuforums.org/showthread.php?t=374836&highlight=Fox+News+Flash)

It works great and it takes out the commercials.

:popcorn:        :KS             :popcorn:

Yes!  It does!  Thanks....  Now I'm content..     :biggrin:

Kevin

---

