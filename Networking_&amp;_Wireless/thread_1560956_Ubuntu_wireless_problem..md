---
title: "Ubuntu wireless problem."
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by cramie10 on 2010-08-25
Before I start I would just like to make it clear that I am COMPLETELY new to linux, I have no fore knowledge whatsoever, however I am an advanced windows user.

 So, I just installed a beginners kit distro of Ubuntu onto my computer after creating a fresh partition for it. I'm currently on the web on my XP partition of the computer, but Ubuntu has successfully installed. I have a bit of a problem.
 So I need to use the internet. Of course to do that I need to connect with my Local Wireless network unsing my 'Edimax EW-7711UTn' wifi adapter, which works perfectly on my Xp, as we can see. I've checked and as far as I can see it IS a supported Wifi card, however I will need to get the drivers myself. It apparently has the Linux drivers on the disk for my network adapter, and having tried running them (God knows if that's what I'm meant to do on Linux) it says 'This is an executable text file' would I like to run it. I click yes and nothing happens. I've rooted around the whole file and as of yet have got nowhere.
 So I thought maybe it had just automatically given the drivers to linux without my own intervention, I don't know if it actually can do that or not. So I went on network managing and it doesn't actually LIST any of the LAN's of my area at all. When trying to 'connect to hidden network' I have to write the SSID of my network and the key and that doesn't work. So I suspect It just doesn't have the drivers or something and it just won't register my wifi adapter. Of course I can't execute the windows driver because as I've discovered Ubuntu doesn't execute files. And I can't put the WINEHQ system on Linux because that requires internet which I don't have. It's all a bit of a problem. 
 Basically my problem is getting the linux driver for my wifi adapter onto my linux system.
Many Thanks
Matt Staniforth

---

### Post by bkratz on 2010-08-25
You might look at this thread esp. post 14

[http://fostergrant.ubuntuforums.org/showthread.php?t=1326232&page=2](http://fostergrant.ubuntuforums.org/showthread.php?t=1326232&page=2)

---

### Post by cramie10 on 2010-08-25
I'm sorry, I find that difficult to understand... Where do I alter the code from? And how do I find it? And what is a vodoo? And where do I insert that piece of code? I
 I'm sorry, like I said I am a complete n00bster at all this... My little guide that came with Linux was rubbish! 
Many Thanks
Matt

---

### Post by Sealbhach on 2010-08-25
> **cramie10 said:**
> I'm sorry, I find that difficult to understand... Where do I alter the code from? And how do I find it? And what is a vodoo? And where do I insert that piece of code? I
 I'm sorry, like I said I am a complete n00bster at all this... My little guide that came with Linux was rubbish! 
Many Thanks
Matt

Hi. I'll try to help if I can. Don't worry, it's really not that complicated. 

This command:

```
sudo mousepad /etc/modprobe.d/blacklist.conf
```sudo = escalates user privileges to admin

mousepad = a text editor, which you will use to open and edit a config file.

/etc/modprobe.d = location of config file

blacklist.conf = the config file (it contains a list of modules i.e. drivers, that you want to blacklist)

However, it's probably easier for you to use gedit as your text editor, so run, in the Terminal:

```
sudo gedit /etc/modprobe.d/blacklist.conf 
```OK, so this will open up the config file for editing. Next, just copy and paste what that guy wrote in his message:

```
# Excellent fix from cyberhood and chili555 
# see [http://ubuntuforums.org/showthread.php?t=1444420](http://ubuntuforums.org/showthread.php?t=1444420)
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```Just copy and paste that in. 

The first two lines have a # before them, so they will be ignored, they are just commentary. The last three lines say that those modules should be blacklisted - not loaded when the system boots up.

The next bit, the voodoo, is bit of voodoo:

```

$sudo su
$echo rt2870sta >> /etc/modules
$exit

```Not really voodoo. These are commands to be entered in the terminal, one line at a time.

echo = a command that inserts text into a file or outputs it on a screen. Run "echo hello" in a terminal and you'll see what I mean.

 rt2870sta = the name of the module i.e. driver

>> = indicates that the text is to go into the following file

/etc/modules = location and name of that file.

/etc/modules is a text file that contains a list of the modules that should be loaded at boot time. That command adds rt2870sta to that list, so that it will be loaded at boot time.

This last command

```
sudo modprobe rt2870sta
```temporarily loads the module rt2870sta for this session. 

So, other people on that thread have said that this solution works for them, so why not give it a go?

.

---

### Post by cramie10 on 2010-08-25
Ahh thankyou :) I'll give it a shot... I just want to get as much detail as possible BEFORE switching to the Linux partition so that I don't have to switch back and ask more questions before returning again. I'll give that a go. Knowing me and Linux so far I'll get it wrong... Theres probably a special place to insert that sode or something but nvm
Many Thanks
Matt

---

### Post by cramie10 on 2010-08-31
Hi again, so obviously as expected I had a few issues.

I completed the first command in the terminal successfully, I then seemed to successfully blacklist those 3 things... whatever they are :S, I didn't get any sort of confirmation but I dno if I was supposed to or not.
 My problem came when I re-opened the terminal. I typed sudo su, and that seemed to just take me to a different directory where the sign at the start of the command was no longer a $ sign, but a # sign. This would seem to make a difference, as I know the # sign is for comments. But I then tried to do the $echo rt2870sta >> /ect/modules command, whereupon the system tells me there is no such file / directory as /ect/modules. I tried it both with and without the $ infront of the # sign and it made no difference, there is apparently no such folder. The final command seemed to complete successfully, but again with no confirmation. I'm not really sure what to do once I have written the commands in the terminal. Can I just exit? Or must I used $exit as show in one command? After failing the command as I said I tried to exit and it said the terminal was still in an operation and that quitting would kill it. Is that significant? Great apologies for being such a MAHOOSIVE noob at this stuff.
Many Thanks
Matt

---

### Post by cramie10 on 2010-08-31
Hi, I'm having a similar problem, not with the same adapter though. I am a COMPLETE noob at linux, to put this into perspective just then I had to go on help to find the terminal... But yeah Im on a dual boot with ubuntu and it seems just not to detect my wifi card at all. I don't know how to tell whether it KNOWS my wifi card is there at all. Of course an even bigger problem is the linux drivers on my installation disk seem not to work and you can't get drivers off the internet for a wifi adapter when you have no internet! It's all a bit of a pickle... I think my next plan is to attempt to get the drivers downloaded onto the windows side of things and see if I can get them across. Sorry I'm completely rambling on the wrong thread to do it. My point is those are my few and feeble suggestions, and it seems that you're not alone in your troubles!

---

### Post by cramie10 on 2010-08-31
Paha, I rebooted and it worked anyway! lord knows exactly what fixes it. Probably those blacklists... seing as though thats the only thing that I made work! Hah!

---

### Post by Sealbhach on 2010-08-31
Oh, I see you made it work. OK, ignore my PM then. Congratulations! :D

.

---

### Post by Iowan on 2010-09-02
Merged post from another thread on this topic.

---

