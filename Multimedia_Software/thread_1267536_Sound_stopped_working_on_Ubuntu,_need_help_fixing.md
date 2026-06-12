---
title: "Sound stopped working on Ubuntu, need help fixing"
date: 2009-09-15
forum: Multimedia Software
---

### Post by humanist on 2009-09-15
[SIZE=1]Hi,[/SIZE]
 [SIZE=1]
[/SIZE]
[SIZE=1]I have a Lenovo IdeaPad Y530. I tried to find more information on my computer's operating parameters, but with no success so far. (I suppose I can find that out in a terminal, but I don't know what command to type in.)
[/SIZE]
[SIZE=1]
[/SIZE] 
 [SIZE=1]Anyway, earlier this summer I switched my operating system from Windows to Ubuntu 8.4 (I'm pretty sure it's the .4). For a while it worked fine, then, after a couple weeks, the sound stopped working. It still plays music when I boot up, so I know the trouble's not with the hardware, it's with Ubuntu.[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]Everything in the volume control is unmuted and running full blast. Not a peep.[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]I've tried consulting the Comprehensive Sound Problems Solutions Guide here: [/SIZE][SIZE=1][COLOR=#0000ff]_[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_[/COLOR][/SIZE][SIZE=1]. I got as far as Step 3, which instructed me to go to a website ([/SIZE][SIZE=1][COLOR=#0000ff]_[http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/)_[/COLOR][/SIZE][SIZE=1]) and “search for your sound card (chipset)[/SIZE][SIZE=1] manufacturer in the dropdown box.”[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]I couldn't find a dropdown box, but a link in the Parent Directory which said “Is my soundcard supported?” I clicked this, and then clicked “Intel” for the manufacturer. [/SIZE] 
 [SIZE=1]
[/SIZE] 
 [SIZE=1]From Step 2 of the Comprehensive Sound Problems Solutions Guide I know that my Audio device is an ICH9 Family, which is not listed on the soundcard list for Intel. The Guide says that “If you don't find the driver, I can't help you.”[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]However, I know my soundcard can work with this version of Ubuntu, so that means the problem should be fixable, right?[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]I also googled my Audi device's information from the terminal window (“Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/SIZE]
 [SIZE=1]”) and came across this: [/SIZE][SIZE=1][COLOR=#0000ff]_[http://ubuntuforums.org/showthread.php?t=940689](http://ubuntuforums.org/showthread.php?t=940689)_[/COLOR][/SIZE][SIZE=1].[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]This, in a nutshell, was the advice:[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]“open a terminal;
write:
sudo gedit /etc/modprobe.d/alsa-base
give your password when asked;
it's normal that nothing is shown when you are writing your password;
a text document will open;
all you have to do is to past the three lines at the end of the text document;
and finally reboot your system.”[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]The three lines in question being:[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]“options snd-hda-intel model=3stack-dig
options snd-hda-intel enable_msi=1
options snd-hda-intel single_cmd=1”[/SIZE]
 [SIZE=1]
[/SIZE] 
 [SIZE=1]I have followed these instructions and had no luck. I am now at my wits' end. Anybody have some ideas?[/SIZE]

---

