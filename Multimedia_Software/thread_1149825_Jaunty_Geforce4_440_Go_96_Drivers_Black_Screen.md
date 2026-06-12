---
title: "Jaunty Geforce4 440 Go 96 Drivers Black Screen"
date: 2009-05-05
forum: Multimedia Software
---

### Post by mikeycantoon on 2009-05-05
I've done a lot of searching for this problem but I keep finding guides for the wrong version or guides too complicated for me to figure out.  I'm new to linux but I am a computer/network tech so I'm not totally ignorant of computers.

I'm runny Ubuntu 9.04 Jaunty on a Dell Inspiron 8200 that has a Geforce 4 440 Go video card.  Every time I try to activate the 96 drivers under Hardware drivers, after I reboot I hear the startup sounds but the monitor goes blank.  I can revert back to the original settings but the desktop runs a bit slow because of Jaunty using a basic driver.

Is there any way to install this driver to work correctly?
Thanks in advance.

---

### Post by mikeycantoon on 2009-05-05
I'm still trying to find a way to make this happen, but so far I'm finding posts that people are saying they've never gotten it fixed with later versions of ubuntu.  Am I just screwed with this particular video card or what?  Any reply would be greatly appreciated.

-Mikey

---

### Post by ofb on 2009-05-06
I can extend sympathy, but that's about it.

As far as I've been able to figure out Nvidia dropped some legacy support around the time of 8.10, but I gather they've improved those drivers since then. I've been looking through the forums for indication that support in 9.04 is in fact improved, but so far I'm not sure, and plan to experiment this weekend.

The 8.10 release notes had a warning about this, but the 9.04 notes do not.
[http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support](http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support)
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

FWIW, my Duron sans SSE with GeForce4 MX440SE wouldn't even boot a new 8.10 install. Ditto with FX5200. The MX440SE is fine with 8.04, but the FX5200 cannot do 3D (no GoogleEarth). And I've just now tested a P3 450 (has SSE) GeForce2 MX400 with 9.04 and everything works fine.

Legacy Nvidia seems to be such a mixed bag. My only suggestion is try to find people running exactly the same hardware as you. Other advice will probably just confuse things.


If you're getting nowhere, what you might do for now is go with 8.04LTS, as it is supported till next April, and it seems relatively unaffected by the Nvidia legacy issues. Do more research on the current problem when you have time, and more users have converted.

Caveat: search the forum for 'Dell Inspiron 8200' first, just to make sure there were no 8.04 issues. Hopefully not, but the last thing you need now is more surprises.

---

### Post by sheppardwolfeyes on 2009-05-07
I have a satellite 2435 and I'm having the same problem with the drivers. If installed it switches to the vga monitor and the screen I get is off. But I still hear the sounds and can even log in. If I use envy and install the 71 drivers that it says are compatible but not recomended. Then graphic drivers don't load and I go thru this series of windows trying to start in low graphics mode. ect.  If someone has a fix for this I would really appreciate it thanks. 

Sheppard.

---

### Post by sheppardwolfeyes on 2009-05-07
Okay so I got the drivers to work, took alil screwing around. But ended up with a few Issues as the result.. First howl I got the drivers to work.  I loaded the drivers and plugged in a external monitor then restarted. I had to restart twice for it to see and set the correct resolution of the external monitor.  My laptop monitor stayed off.  So now that I could get into the nvidia settings I first set the laptop monitor to run as its own X version. and when I went to save to conf I hit the preview button and copied the txt then opened a terminal and switched to root then from there I did a sudo nano /etc/X11/xorg.conf and once the file was opened i deleted everything in it and pasted the new info then ctrl O to save the file, then ctrl X to close the program and restarted.. It now loaded both screens after I logged in.  Next I had to disable the main monitor which was the crt and again went to the preview for the conf and copied and pasted. Same procedure as the first one. shut the system down and then unplugged the crt and started the pc up again and it saw my laptop screen and worked.  My Issues where when I tried to open a terminal in X it would just be a white box.  When I opened pretty much anything that required my password for root it would be a white box, but if i typed my password and hit enter it loaded the program.  Ended up using envy to unistall the video drivers and went back to the ones built in that don't work good.. But atleast I can see and use everything.  If anyone had a Idea for a fix to those issues i'd try again...  I did try to reinstall the terminal and other programs before I reverted to the base drivers. :confused:

---

### Post by ofb on 2009-05-08
Minor comments: 

You can run nvidia-settings as root, to save messing around with copy&paste&nano.

```
gksu nvidia-settings
```

And of course it's a good idea to back up a system file before modification.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.confBAK
```


Otherwise that's an interesting approach. Did you have the white box problem on both the CRT and LCD? And when you say the "ones built in" do you mean the nv driver, or the proprietary Nvidia driver?


Other thing I've learned in the past is I have to launch nvidia-settings at startup if I want my settings remembered properly.

Go System > Preferences > Sessions, make new item:

```
nvidia-settings -l
```

---

### Post by sheppardwolfeyes on 2009-05-11
Sorry it took me so long to reply but been busy the last few days.. I might have to try using that code just to see what happens.. I already have the conf file that i need done and saved so all I have to do is swap it out for the old one again.. As to the question about the windows being white.. No they worked just fine on the crt.. It wasn't till i turned on the lcd as a secondary montior.  Then it continued on when I had it set to just use the lcd.. so maybe if i load these drivers up.. swap out the conf file and set it to load them when it restarts.. maybe just maybe it will work.. I'll have to give it a try soon and let you know.. Before I forget the drivers I was mentioning reverting too was the basic ones that loaded stock with ubuntu. 
Thanks ;oP

Sheppard

---

### Post by Rasputan on 2009-05-12
Thanks alot for the direction guys. i got my geforce4 440 card in my Dell Latitude C840 to work and render things in 3D. unfortunately, like previously stated in this forum, my terminal windows and root permission windows are blank white boxes as well but i think thats a small price to pay to be able to play video games on my laptop. when i go to shut down, i notice that if i have any terminal windows open, for a brief second as its shutting down, you catch a glimpse of the terminal window working so i dont know if that helps you guys any. thanks again for the help

---

### Post by ofb on 2009-05-13
Suggestion: go System > Preferences > Appearance. On the Visual Effects panel select None.

You will retain 3D performance for applications. This only shuts off the desktop eyecandy. See if that fixes the white box issue.

---

### Post by planetlarg2 on 2009-05-14
I hd the same problem on my Dell Inspiron 8200 with  a 1400x1050 display. After hours of pain and much pondering of 

[LIST]
[*][http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=79650&page=2)
[*]/var/log/Xorg.0.log
[*]/etc/X11/xorg.conf
[/LIST]
I learned these things can go wrong 

[LIST]
[*] some laptops shipped with a duff samsung panel with a faulty EDID chip giving out the wrong info
[*] everything is auto-detected OK, but output is sent to the wrong screen -  CRT-0 instead of DFP-0 (Default Flat Panel).
[/LIST]
My problem was the second one. i don't have a CRT-0. I ended up doing this.

[LIST=1]
[*][ctrl][alt][f1]
[*]login
[*]sudo /etc/init.d/gdm stop
[*][ctrl][alt][f7] to check gnome is gone
[*]sudo cp /etc/X11/xorg.conf /home/planetlarg/
[*]sudo vi /etc/X11/xorg.conf
[*]add one line to the config -   Option "UseDisplayDevice" "DFP-0"
[*]sudo /etc/init.d/gdm start
[/LIST]
 
My final config looks like this. 

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
        Option "UseDisplayDevice" "DFP-0"
EndSection
```

Any use?

---

