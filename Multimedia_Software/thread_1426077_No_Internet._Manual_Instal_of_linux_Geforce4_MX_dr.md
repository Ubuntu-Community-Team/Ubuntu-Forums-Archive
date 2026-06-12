---
title: "No Internet. Manual Instal of linux Geforce4 MX drivers SOLUTION"
date: 2010-03-09
forum: Multimedia Software
---

### Post by ho0ola on 2010-03-09
Problem Solved!!!!:grin:

Running Linux ubuntu 9.10 w/ Gnome. Trying to manually install GeForce4 MX integrated graphics drivers. No Internet.


Here are the successful steps I used to Install Geforce 4 MX chipset Driver: First Get your correct linux driver/ drivers from manufacturers website (NVIDIA, ATI etc) use a flash drive preferrably.  Copy drivers from flash or whatever onto your Gnome desktop.

In gnome - press ctrl+alt+f1 to bring you to command prompt

- login

- type : sudo service gdm stop (to turn off X server) or default display

- then type : sudo bash 

- then : cd ~/Desktop 

- then : '. /your file name EXACTLY       *Note: no spaces btwn `. /


Exact commands to type after ctrl+ alt+ f1:

sudo service gdm stop

sudo bash

cd ~/desktop 
( this just allows computer to be looking for driver in the right spot, mine was on desktop)

'. /NVIDIA-Linux-x86-96.43.16-pkg1.run' Or whatever driver u are manually tying to install.

Note: the ' and the ' are VERY important!! make sure to include both ' and ' at beginning and end of your drivers name

Next follow through with installer and reboot. Make sure when it asks you which X server to use,  use your new one, not the previous. 

When in desktop, check out -Application>system tools to see if your driver and its control center is there. (Maybe not the same for all)

Change resolution and enjoy Ubuntu how its supposed to be!!! i am running in 1600x1050 beautifully :)

If this doesn't work for you, I am sorry, But with NVIDIA Geforce4 MX it WILL!!! Try reading around other forums for support with your Video card/Driver issues. ThankS

---

### Post by visigothwarrior on 2010-03-26
I am new to Ubuntu (as of today).  I have installed Ubunut 9.10, but have been having problems with getting the driver for my Geforce 4 MX card.  I have been reading forums for about 5 hours now, looking at the history of problems related to drivers related to this and other 'legacy' video cards.

I am under the impression that with newer Ubuntu distributions, the main Nvidia driver (the one that installs when one selects to run the Nvidia X Server, as recommended by 9.10, which presently installs 96.43.13) will not work with these older cards, and we would have to use legacy drivers.

The one I am attempting to install, is the one you have listed in this post. (although I saw 96.43.16 listed under a few linux systems options on the Nvidia site, such as AMD64, etc).  Could this be my problem or are all the 96.43.16 s the same?

I read on one post that mentioned that as of Dec09, it would be a few months for Nvidia to roll out some support (updated drivers) that would be able to help.  I've noticed that the driver here is listed on the Nvidia site as being rolled out in Feb10.

So, I've been trying to install it for a few hours now with no success.

So, I got very excited when I saw your post.  I've been attempting stuff, which I am now guessing, were all older terminal executions prior to Ubuntu 8 and 9, using SusE, and a whole bunch of other xorg, and file manipulations.  Way over my head as a noob, but am learning a little, I believe.

I then eventually saw the legacy drivers on Nvidia's site (as mentioned in a forum here).  However, I could not get them to install as stated on Nvidia's website, which was just saying type 'sh filename'.  It would not open the dang file.  So, I was lost.  I then got the file to execute in the terminal (after some more forum digging), and got a message about must be in root (or equivalent type of message) while in terminal.

Then I came across this post. But, I'm still having problems (told you I was a NOOB).
I now have 3 questions when following the suggested directions

1) cd ~/Desktop  and  cd ~/desktop were referenced in the directions.  I'm guessing that cd ~/Desktop is the correct one?  I attempted cd ~/desktop and it said couldn't find file or directory, but then ok with Desktop.  I am new, but I thought case sensitive wasn't important in linux, but I guess so.
2) I typed the './name of file' for the driver located on my desktop, but only get a > with a blinking cursor afterwards.  Directions say "follow through with installer and reboot".  What does follow through with installer mean?  I'm guessing my driver didn't install.  What could I be missing here?
3) I am now wondering if it matters if the previous driver would have to be installed for this one to install over it? 96.43.16 is the one I'm trying to install, and the out of the box Ubuntu 9.10 goes and grabs 96.43.13 from NVidia.  Does 96.43.13 have to be up and running for this to work?  Does it matter at all?

Please Help!

I feel that I'm so close and am missing something simple.

Thanks for any help.

---

### Post by visigothwarrior on 2010-03-26
Well, approximately 15 minutes after posting the previous post, I got it to work.  For some reason, (not known to me since it's my first day), when I tried the CTRL/ALT/F1 thing again, I attempted the original post directions using "sh filename" instead of " './filename' ", and it installed. Yay!

So, being a noob, i now have a question... why the difference to get this to work?
I am running Ubuntu 9.10 w/ Gnome also.
Why are the original directions using ' , and I didn't need to?

learning as I go.

Anyone have any suggestions on where to go for intro command line learning for linux?
sh, sudo, etc. are all new to me. I'm just guessing at things like gdm is 'graphics display module' or some equivalent.  AFter reading forums for a few hours, I'm interested, but still pretty much lost beyond, package manager and playing around with graphical interfaces.

thanks!

---

