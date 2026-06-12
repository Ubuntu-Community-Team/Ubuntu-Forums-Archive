---
title: "Entering script"
date: 2009-01-10
forum: Mythbuntu
---

### Post by mmann on 2009-01-10
Hi,
I'm a first time user of any Linux software. 
Can anyone tell me how I enter script into Linux?
I'm having trouble with my MythTV install and I found a site that seems to tell me how to fix it ( [http://parker1.co.uk/mythtv_novafw.php](http://parker1.co.uk/mythtv_novafw.php) ).
but to do it they say that I need to...

use the get_dvb_firmware script, which is distributed as part of the Linux source code, to fetch it off the internet. Run the script, telling it which firmware to fetch (the clue is in the error message above, in this case tda10045).

get_dvb_firmware tda10045

...But I cant find anywhere to type this into to get it to work.
And I have no idea where to put the file once it's downloaded. I cannot find the firmware directory...

This downloads a file such as tt_budget_217g.zip, which contains a dvb-fe-tda10045.fw firmware file. Copy it into the firmware directory:

cp dvb-fe-tda10045.fw /lib/firmware

...Please help.
Thanks

---

### Post by arvevans on 2009-01-10
"script" refers to Shell-Script commands.  This is somewhat like command language batch files in Windows, but much more powerful.  Individual one-liner shell-script commands can be typed into a terminal screen ( goto Applications/terminal, if running gnome) and hitting ENTER at the end of the line you have typed into that screen.

Multiple shell-script commands may be grouped together in a text file and after making the file executable (chmod +x filename) you can run the file as a program by simply typing it's name.

There are many possible commands, and many options for these commands, in the Linux system.  Some of these can be seem by going to a terminal screen and typing 'man bash' and others are stand-alone commands which are not part of the bash shell-script interpreter.

To learn more about shell-script programming, you might want to visit these URLs:
[INDENT][URL="http://lowfatlinux.com/linux-shell-script.html"]

[http://www.usd.edu/~sweidner/lsst/]("http://www.usd.edu/~sweidner/lsst/")[/URL][/INDENT]

Hope that gets you started with shell-scripting language.

_._

---

### Post by uMuppet on 2009-01-11
I have a similar card that requires that firmware and found it a real pain to find and install.  I think that guide you are looking at is outdated or maybe one of the links are at least.

I have the firmware on my site [here]("http://mythkiwi.com/index.php/remository?func=select&id=6") or go to download sectin at mythkiwi.com

Download the file and it should end up on your desktop.  The just copy the firmware to /lib/firmware and the card will start working instantly, no reboot needed.

Here is how to copy it, open the Terminal.  Applications -> Accessories -> Terminal
And type 
```
cd Desktop
``` case sensitive!
```
sudo cp dvb-fe-tda10045.fw /lib/firmware
```

You will be prompted for a password because you are changing things in the main system but you can probably use your own login password.

---

