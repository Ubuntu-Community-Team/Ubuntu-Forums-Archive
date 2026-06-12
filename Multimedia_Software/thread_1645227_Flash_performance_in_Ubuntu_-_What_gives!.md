---
title: "Flash performance in Ubuntu - What gives?!"
date: 2010-12-14
forum: Multimedia Software
---

### Post by wilko666 on 2010-12-14
Hello all,
 
I have a question that has been partially answered in other posts and forums but I am still unclear. Please can someone help me out?
 
I was previously using an Intel Atom 1.6GHz, 1GB RAM and the onboard Intel graphics adaptor for use as a media center PC. This was running Lubuntu and I could use Flash at full screen without any issues.
 
I have since decided to upgrade to an Acer Revo R3610 (Dual core Intel Atom 1.6GHz, 4GB RAM, Corsair SSD and Nvidia ION grpahics). I thought that as this machine was more powerful than my previous one, I could get away with ditching Lununtu and go for Ubuntu 10.10 (x86).
 
I have updated the machine and installed the latest Nvidia drivers. When I browse to a Flash based site all runs fine until I go to full screen then I get about 10FPS (sound remains fine). The video is unwatchable.
 
I rebuilt the machine using Windows 7 Ultimate (x86) and tested again. Under Windows the video plays perfectly.
 
I have also tried using the 10.2 beta version of Flash under Ubuntu and this gives the same terrible results.
 
I am at a loss as to where the issue lies. Is it with Nvidia's driver, Adobe's Flash under Linux or is it my Ubuntu build?
 
Any help will be greatly recieved (I really dont want to have to run Windows!!).
 
Many thanks in advance,
Wilko.

---

### Post by gdawg on 2010-12-14
Hi, I recently discovered that 'gnash' and adobe flash do not mix well. I subscribe to a local newspaper and view it via internet. After upgrading to Ubuntu 10.10 I was unable to view the paper and I knew it required the Adobe Flash Player. I un-installed and re-installed flash but it still wouldn't work. I un-installed 'gnash' and now it works fine. Hope this helps you with your situation.

---

### Post by wilko666 on 2010-12-14
Hi gdawg,
 
Many thanks for your swift reply. I will try your fix tonight when I get hom from work. Do you know if gnash is installed by default, as I dont remember installing that?
 
Thanks again,
Wilko.

---

### Post by wilko666 on 2010-12-15
Hello all,
 
I checked gdawg's fix last night, but I do not have gnash installed.
 
Please can someone help me out with my issue? The Mrs is giving me grief about watching her catch up TV and I dont want to have to revert to Windows.
 
Thanks in advance,

---

### Post by SeijiSensei on 2010-12-15
You might consider trying the beta version of Flash player available [here]("http://labs.adobe.com/downloads/flashplayer10.html").  It doesn't install the same way normal Ubuntu packages do, however.  You need to download the file and extract the libflashplayer.so payload.  Then copy it (as root with sudo) to /usr/lib/mozilla/plugins.  If there's already a libflashplayer.so there, rename it libflashplayer.old first, just in case something goes wrong.

Unfortunately Flashplayer doesn't take advantage of hardware decoding like that provided by nvidia's VDPAU technology.  You can also try watching flash videos with an mplayer-based video player.  My favorite is [smplayer]("http://smplayer.sourceforge.net/") (sudo apt-get install smplayer).

---

### Post by wilko666 on 2010-12-16
Hi SeijiSensei,
 
Many thanks for your reply. I have installed the 10.2 beta using the method you explained below and still get the issue. I was under the impression that the 10.2 beta should use hardware acceleration? I have checked that this is enabled on my setup via the right click menu.
 
I will try your smplayer suggestion tonight when I get in.
 
Also, please can you clarify if I need to install VDPAU as well as the Nvidia proprietary driver or is it included? If its included, is it on by default? Sorry if this is a n00b question.
 
Thanks in advance.

---

### Post by cchhrriiss121212 on 2010-12-16
You could try these tips:
Go back to Lubuntu
Disable compiz completely
Uncheck the hardware accel. box on the flash right click menu (many users report an improvement like this)

> Also, please can you clarify if I need to install VDPAU as well as the  Nvidia proprietary driver or is it included? If its included, is it on  by default? Sorry if this is a n00b question.
After installing the nvidia driver all you need to do is install smplayer then select vdpau video output in the preferences menu. It should all work out of the box.

---

### Post by SeijiSensei on 2010-12-16
> **wilko666 said:**
> Also, please can you clarify if I need to install VDPAU as well as the Nvidia proprietary driver or is it included? If its included, is it on by default? Sorry if this is a n00b question.

The VDPAU libraries will  usually be installed along with the proprietary driver.  If not, install "libvdpau1" manually.

---

### Post by wilko666 on 2010-12-17
Hello all, many thanks for your replies. I have tried the suggestions below:
 
> **cchhrriiss121212 said:**
> You could try these tips:
Go back to Lubuntu
Disable compiz completely
Uncheck the hardware accel. box on the flash right click menu (many users report an improvement like this)

 
Interestingly, Lubuntu on this hardware gives me the same issue with Flash. I tried it last night with the latest Nvidia drivers and not only do I get this issue with flash, but all of the text within the OS becomes tiny. Odd. This only happened after loading the Nvidia drivers.
 
Before installing Lubuntu, I disabled Compiz and all visual effects, which gives the same fault. I then completely uninstalled Compiz core and get the same issue.
 
I tried to check and uncheck the hardware accelleration box, restarting the browser inbetween, with the same issue occuring.
 
I cant imagine I'm the only Revo user than is running Linux and wants to watch Flash in full screen. Seems odd other people are not reporting the same fault.
 
You guys got any other ideas please?

---

### Post by cchhrriiss121212 on 2010-12-17
What kind of cpu usage are you seeing when watching flash?
Have you tried using another browser like chrome?
Also what driver version are you using? I know you said latest, but Nvidia are constantly updating them. I recently had a fullscreen video problem with 260.19.10 that was fixed by updating to 260.19.29.
You could also try out a 64bit OS with the 64bit beta flash plugin, it will perform better than the 32 (your Atom 330 does support 64bit in case you wondered).

---

### Post by spidermagicat on 2011-01-04
I've got the answer for you!

go to this thread I made [http://ubuntuforums.org/showthread.php?t=1659949](http://ubuntuforums.org/showthread.php?t=1659949)

With this I'm able to run 1080p from youtube no problem with a very similar spec :-D

give it a go

---

