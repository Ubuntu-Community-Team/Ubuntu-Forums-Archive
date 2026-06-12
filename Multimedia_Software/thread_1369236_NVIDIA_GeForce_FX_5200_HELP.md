---
title: "NVIDIA GeForce FX 5200 HELP"
date: 2009-12-31
forum: Multimedia Software
---

### Post by ddr3XD on 2009-12-31
Ok first of all like a lot others here, i'm EXTREMLY NEW to Ubuntu. So first I just want to take the time out to say that I LUUUUUUUUUUUUUUUUUUUUUUUUUVVVVVVV UBUNTU!!! XD
 

 So on to the problem...After a fresh install I try to enable visual effects but it hits me with error message “Desktop effects could not be enabled”. So after reaming a few threads and a little experimenting, I found out that I had to install drivers for my graphics card (which is a GeForce FX 5200). So I went to Hardware Drivers and downloaded and installed the recommended drivers. Then rebooted(cz it said to). But after I reboot my screen resolution was set to 800x600(it was 1024x768).
 When I tried to change it back using the default Display software it said “It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?” So I choose yes which brought me to NVDIA X Server settings thingy. I changed the resolution back 1024x768 successfully but when I try to enable desktop effects again it still doesnt enable, giving me the same error message. So I restarted but when I restart the resolution was set back to 800x600 and it turns out after every restart it automatically gets set back to it. What do I do???? Can someone please guide me in the right direction? Ur help will be greatly appreciated!
 

 Ubuntu 9.10
 NVIDIA GeForce FX 5200
 Old CRT monitor

---

### Post by mmmichael on 2009-12-31
There's a trick to using the Nvidia X Servers Settings - you need to open it with administrative privileges if you want to keep the settings.
Open a terminal (Applications>Accessories>Terminal) and enter:```
gksudo /usr/bin/nvidia-settings
``` ,press enter, then enter your password.
When the settings window opens, select X Server Display Configuration.
Set your resolution and then click on "Save to X Configuration File".
When you reboot you should have your desired resolution and you can try to enable desktop effects again.

---

### Post by ddr3XD on 2009-12-31
I was really hoping that would work but it didnt XD. When I click Save to X Configuration file it gives the error message “Failed to parse existing X config file '/etc/X11/xorg.conf'!”. And in the terminal it gives me this:  
 VALIDATION ERROR:  Data incomplete in file /etc/X11/xorg.conf. 
 Undefined Device "(null)" referenced by Screen "Default Screen".
 after I press 'Save to X Configuration file' also. What now?
 

 Thanks for the help:)

---

### Post by mmmichael on 2009-12-31
OK, the Nvidia software is having trouble editing your xorg.conf file.Try this:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then try the advice from my previous post. This way a fresh file will be generated. If it doesn't work you can restore your original file by typing```
sudo rm /etc/X11/xorg.conf && mv /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
Just be careful to type exactly and observe upper and lower cases (or just copy and paste commands).

---

### Post by mmmichael on 2009-12-31
If you get any errors, do not reboot until you have restored your original xorg.conf!

---

### Post by HappyFeet on 2009-12-31
Do:
```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
gksudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button lableled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo gedit /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by ddr3XD on 2009-12-31
OK. HALF WAY THRU!!!
 NVIDIA X Server  saved settings
 BUT Desktop effects still cant be enabled(same error message)
 

 I used mmmicheals method because when I tried HappyFeet's it said &#8220;rm: cannot remove `/etc/X11/xorg.conf': No such file or directory&#8221;
 

 But like I said desktop effects still cant be enabled.
 When I click 'Normal' visual effects it says &#8220;Searching for drivers&#8221; then all my windows disappear and then reappear then it says &#8220;Desktop effects could not be enabled&#8221;.
 Any suggestions?
 

 Thanks for your help HappyFeet and mmmicheals.

---

### Post by mmmichael on 2009-12-31
There is a script called compiz-check that may help diagnose the problem. You can install it in your home directory by typing```
wget http://blogage.de/files/9124/download -O compiz-check
```
Then make the script executable by typing```
chmod +x compiz-check
```
Then run it with ```
./compiz-check
```
and post the output here.

---

### Post by ddr3XD on 2009-12-31
This is what I get:
 

> jamey@jamey-desktop:~$ ./compiz-check 
  
 Gathering information about your system... 
  
  Distribution:          Ubuntu 9.10 
  Desktop environment:   GNOME 
  Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
  Driver in use:         nv 
  Rendering method:      None 
  
 Checking if it's possible to run Compiz on your system...  [SKIP] 
  
  Checking for hardware/setup problems...           [SKIP] 
  
 At least one check had to be skipped: 
  Error: No rendering method in use (AIGLX, Xgl or Nvidia)  
  
 Would you like to know more? (Y/n)  
 

 When I type y for the “Would you like to know more? (Y/n)” question, this is what I get:
 

> Would you like to know more? (Y/n) y
  
  The nv driver is not capable of running Compiz, you need to install 
  the proper driver for your graphics card.  
 

 Check if there's an alternate (proprietary) driver available? (Y/n) y 
 jamey@jamey-desktop:~$  
 Then after it takes me to the Hardware Drivers thingy, but then I realize the driver I installed is not installed anymore. And when I try to run the NVIDIA X Server app, it says: “You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.”
 

 Should I reinstalled the driver again?
 If yes am I not doing the same thing over again?
 

 Wow what a long post  :P

---

### Post by mmmichael on 2009-12-31
A couple of weeks after I upgraded to karmic my desktop effects stopped working. I ran 
```
compiz --replace
``` and got an error message twice. The third time it worked. Apparently repetition is sometimes helpful?

open the Hardware Drivers app and make sure you enable driver version 173. Then log out and back in and see what happens.

---

### Post by ddr3XD on 2009-12-31
right back where we started XD

---

### Post by Mia1990 on 2009-12-31
Try running compiz in your terminal it could find some problems

applications>accessories>terminal
copy and past in the terminal
> compiz

---

### Post by mmmichael on 2009-12-31
It may seem futile, but I would repeat the previous steps. Then run ```
compiz --replace
```

---

### Post by ddr3XD on 2010-01-01
Ok guys...got lots of info for ya. This is what I get when I run compiz:
 

> jamey@jamey-desktop:~$ compiz  
 Checking for Xgl: not present.  
 xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log  
 Blacklisted PCIID '8086:2562' found  
 aborting and using fallback: /usr/bin/metacity
This is what I get when I run compiz &#8211;replace:

> 
 jamey@jamey-desktop:~$ compiz --replace 
 Checking for Xgl: not present.  
 xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log  
 Blacklisted PCIID '8086:2562' found  
 aborting and using fallback: /usr/bin/metacity
 Basically the same thing.
 Question: How do I exit the compiz command?
 The reason why I asked that is because when I try to close the teminal it says: &#8220;There is still a process running in this terminal. Closing the terminal will kill it.&#8221; And then I close it anyways and then my screen locks up(cant minimize or maximize windows) then I have to restart.
 

 BUT...I did found the problem to my NVIDIA X Server settings(for real this time). It turns out that I didnt have an xorg.conf file...why? I have no idea. The file that the nvidia xserver app was saving(when I clicked 'Save to X configuration file'), were saved in my home directory, when they should be saved in etc/X11/. So I found one and ran nautilus with root permissions and copy and paste it in etc/X11/. There was indeed a backup of my xorg.conf file(named 'xorg.conf.back' which is most likely came from when I was trying one of the suggestions from previous post by backing it up then recreate a fresh one. So I restored it but when I try the 'Apply to x configuration file' thing it says &#8220;Failed to parse existing X config file '/etc/X11/xorg.conf'!&#8221;...which means it must be corrupted op sumthing. So I just used the working ones which I found in my home directory and now the screen resolution is working fine(not setting back to 800x600 anymore).
 

 Sorry if I bored yall:lolflag:

---

### Post by ddr3XD on 2010-01-01
So i still cant enable desktop effects! Which is no biggy

---

### Post by mmmichael on 2010-01-01
Can you run ./compiz-check again? The last time it showed you were using the nv driver, but now it should show the proprietary driver (v.173). Let's see what it says.
When I lost my desktop effects I somehow got them back by  repeating the same steps a few times, so don't give up.

---

### Post by Mia1990 on 2010-01-01
when you ran compiz in the terminal it shows blacklisted you have a internal card and you added the nvidia card?Most likely compiz is picking up on the internal card without un blacklisting that one you will not be able to run compiz if compiz is still not running type or copy this in the terminal
> sudo gedit /usr/bin/compizYou will need to edit this file. Look for the lines like this (the lines that need editing are in bold.
# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2a02 " # Intel GM965
**T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"
unset T

Comment out the lines pertaining to your particular video card if you want to comment out the references to the Intel card there in bold the entry would look like this

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2a02 " # Intel GM965
**#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"
unset T

This should let you run compiz you will need to fine the entry '8086:2562' and put a # by it.But  don't blame me if it don't it worked on my laptop.

---

### Post by ddr3XD on 2010-01-02
IT WORKED!!!!!!! FINALLY :P

 So I ran ./compiz-check again. This is what I got:
 
> jamey@jamey-desktop:~$ ./compiz-check 
  
 Gathering information about your system... 
  
  Distribution:          Ubuntu 9.10 
  Desktop environment:   GNOME 
  Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
  Driver in use:         nvidia 
  Rendering method:      Nvidia 
  
 Checking if it's possible to run Compiz on your system... 
  
  Checking for texture_from_pixmap...               [ OK ] 
  Checking for non power of two support...          [ OK ] 
  Checking for composite extension...               [ OK ] 
  Checking for FBConfig...                          [ OK ] 
  Checking for hardware/setup problems...           [WARN] 
  
 Something potential problematic has been detected with your setup: 
  Warning: PCI ID 8086:2562 detected.  
  
 Would you like to know more? (Y/n)  
So I answerd yes...
 
> Would you like to know more? (Y/n) y 
  
  Your particular graphics chip may be blacklisted on certain distributions. 
  However that does not necessarily mean you will not be able to run Compiz. 
  
  You can skip this blacklist -- but keep in mind that you did so. 
  Do not complain if you encounter any problems with Compiz afterwards.  
  
 Do you want to skip blacklist checks by Compiz? (y/N)
 Yes again...
 
> Do you want to skip blacklist checks by Compiz? (y/N) y 
 So I ran it again to see if anything had changed...this is what I got afterwards:
 
> jamey@jamey-desktop:~$ ./compiz-check 
 
 Gathering information about your system... 
  
  Distribution:          Ubuntu 9.10 
  Desktop environment:   GNOME 
  Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
  Driver in use:         nvidia 
  Rendering method:      Nvidia 
  
 Checking if it's possible to run Compiz on your system... 
  
  Checking for texture_from_pixmap...               [ OK ] 
  Checking for non power of two support...          [ OK ] 
  Checking for composite extension...               [ OK ] 
  Checking for FBConfig...                          [ OK ] 
  Checking for hardware/setup problems...           [COLOR=DarkGreen][ OK ] [/COLOR]
  
 jamey@jamey-desktop:~$  
 Then I went to enable desktop effects...AND IT WORKED :P

 THANKS FOR ALL UR HELP!!! AND HOPE THIS WILL HELP OTHERS OUT THERE WITH SAME PROBLEM TOO...
 
I LUV UBUNTU!!!!!!!!! :guitar:

---

### Post by hongquan1987 on 2010-07-10
My Ubuntu 10.04 machine can't enable Compiz with GeForce FX 5200 card although I have let it out of blacklist.
The compiz-check say:
Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

But Compiz is still not able to run.

---

### Post by WarriorIng64 on 2010-12-27
I am running Ubuntu 10.10 32-bit on an older desktop with an NVidia GeForce FX 5200 installed, and I can get things like glchess running in 3D but I can't enable desktop effects. I did run "sudo nvidia-xconfig" to get the glchess 3D effects working (as a test), but that's about it.

Afterwards, I tried the compiz-check script, and it gives me this:

```
christopher@Barney:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2562 detected. 

Would you like to know more? (Y/n) y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N) y
christopher@Barney:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

christopher@Barney:~$ 

```

I still could not enable desktop effects, after neither run of the compiz-config script. I next went to edit the /usr/bin/compiz file (as shown in #17), but it's apparently only a binary executable and not a text file, so I don't know where to even find the blacklist.

Again, this is an older Dell desktop I got from a cousin who didn't want it anymore, and I'm just using it as a test system for various things. Thus, if anything gets "busted", it's not a problem at all. The only changes I made to it were upgrading the RAM and installing the video card, in addition to replacing Windows XP with Ubuntu. :) Any ideas?

---

### Post by rabbits on 2010-12-27
I would suggest you start a new thread instead of continuing of this old thread. Your issue is probably not similar to this old problem with Ubuntu-9.10  Anyway, you can try this quick attempt at a solution.,,,,,

I suspect you have not installed the proprietary "nvidia-173" driver. glchess might be using the non-proprietary 2D driver.  Since you are running 10.10, this should work :
Try >System >Admin >Additional Drivers ; and see if you are offered the "nvidia-173" driver (proprietary) for installation.  Some other nvidia drivers may also be offered to you, but you can try -173 first.

Good luck. Let me know if it works.

---

### Post by WarriorIng64 on 2010-12-27
Whoops, sorry if I forgot to mention that in my original message! I already had that exact driver installed, activated and "in use" through the Additional Drivers utility. However, the issues I described earlier still exist.

By the ways, that was also the only (graphics-related) driver offered to me. It seemed just a little odd, since I also use Nvidia integrated graphics with proprietary drivers on my main Ubuntu 10.04 desktop with no problems, and that gave me multiple drivers to choose from, but I digress.

> glchess might be using the non-proprietary 2D driver.
I'm a bit puzzled by this. glchess IS giving me 3D graphics...it would not allow me to turn them on at first until I ran that "sudo nvidia-xconfig" command mentioned earlier, but now it does. Is this because the 3D graphics are only pre-rendered or something? I apologize if I'm missing something here, but maybe it's also possible that I can only get my drivers to work for that game but not for the desktop itself...just a guess.

At any rate, again, this is just basically a small fun project I set up for myself with older hardware, just to see if I can make it work. If it doesn't, it's no big deal. I posted here since it seemed like this issue might still be relevant for anyone trying to use this older graphics card with newer versions of Ubuntu for whatever reason, but if you think a separate post might be a better idea then I might try that.

---

### Post by rabbits on 2010-12-27
Warrior, sorry I didn't realise you are already familiar with Ubuntu.

I installed 10.10 onto my laptop with nvidia 6150 integrated graphics using nvidia-173 driver; very smooth, no need for &quot;nomodeset&quot; etc.  I think only with 10.04 and earlier that &quot;nomodeset&quot; was required during installation.

The only other suggestion I have for you, is to try &quot;nvidia-96&quot; driver instead of -173. You can install using Synaptic. Documentation from Synaptic says -96 will support up to GeForce7.

Good luck.

---

### Post by sk4tec on 2011-05-17
> **Mia1990 said:**
> when you ran compiz in the terminal it shows blacklisted you have a internal card and you added the nvidia card?Most likely compiz is picking up on the internal card without un blacklisting that one you will not be able to run compiz if compiz is still not running type or copy this in the terminal
You will need to edit this file. Look for the lines like this (the lines that need editing are in bold.
# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2a02 " # Intel GM965
**T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"
unset T

Comment out the lines pertaining to your particular video card if you want to comment out the references to the Intel card there in bold the entry would look like this

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
T="   1002:5954 1002:5854 1002:5955" # ati rs480
T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
T="$T 8086:2a02 " # Intel GM965
**#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)**
BLACKLIST_PCIIDS="$T"
unset T

This should let you run compiz you will need to fine the entry '8086:2562' and put a # by it.But  don't blame me if it don't it worked on my laptop.

I understand in principle what your saying but I can't do it. Compiz is a binary file... no? Another post said that I need to use a Hex editor - tried that and couldn't find the relevant values to remove.

how can I do what this wiki says to do?

[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

ie skip checks? I tried to edit a compiz-decoration script file but my linux wasn't up to editing it as Sudo.:(

---

