---
title: "How do I make my headless server act as a PulseAudio server on startup?"
date: 2009-02-28
forum: Multimedia Software
---

### Post by Endolith on 2009-02-28
If I login, it creates a PulseAudio server, but when I log out the server shuts down. How do I get it to act as a server without anyone logged in?

---

### Post by amauk on 2009-02-28
what exactly are you trying to achieve?

---

### Post by markbuntu on 2009-02-28
It is not reccomended to run pulseaudio as a system wide daemon due to security issues since it will be running with root permissions but if you really want to you just need to edit the /etc/pulse/daemon.conf file and change

;system-instance = no 

to yes and uncomment it.

---

### Post by Endolith on 2009-03-02
> **amauk said:**
> what exactly are you trying to achieve?

I'm trying to get my headless server to act as a PulseAudio server on startup.

So I can send audio to it without logging into it.

Same question here:

[https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/61859](https://answers.launchpad.net/ubuntu/+source/pulseaudio/+question/61859)

---

### Post by l3iggs on 2009-03-10
i've been smashing my head into this problem for the past few hours and i think i've got it figured out now. what a mess these stupid pulse config files are. try following these steps on a fresh pulseaudio install:

edit your /etc/default/pulseaudio file so that:
PULSEAUDIO_SYSTEM_START=1
DISALLOW_MODULE_LOADING=0

now put the following three lines in the bottom of your /etc/pulse/system.pa file:
load-module module-esound-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;192.168.0.0/16
load-module module-zeroconf-publish

you can remove the auth... junk from the first two lines there if you want, they just prevent any IP other than a local one from connecting to your server (although it might be cool for a few minutes if someone else started playing music on your speakers)

make sure you've got the pulseaudio-module-zeroconf package installed

now you can: sudo etc/init.d/pulseaudio start
you should get an [OK] from this command, if so, you're done
your sound server should start on boot before anyone logs in

good luck

hopefully the time i've spent on this benefits someone other than just me

---

### Post by Endolith on 2009-03-10
> **l3iggs said:**
> edit your /etc/default/pulseaudio file so that:
PULSEAUDIO_SYSTEM_START=1
DISALLOW_MODULE_LOADING=0

now put the following three lines in the bottom of your /etc/pulse/system.pa file:
load-module module-esound-protocol-tcp auth-ip-acl=127.0.0.1;[192.168.0.0/16]("http://192.168.0.0/16")
load-module module-native-protocol-tcp auth-ip-acl=127.0.0.1;[192.168.0.0/16]("http://192.168.0.0/16")
load-module module-zeroconf-publish

Can you show where you got this info from?  I'm always wary of copying and pasting something from a forum post.

---

### Post by markbuntu on 2009-03-10
> **l3iggs said:**
> 

hopefully the time i've spent on this benefits someone other than just me

Don't worry about that, I just linked your post into the 10,000 page guide. Thanks for that very clear and concise explanation. Hopefully you can stick around and help people with questions about it.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

regards,
mark

---

### Post by Endolith on 2009-05-18
According to the file /etc/pulse/default.pa these are supposed to be configured using the GUI:

### Network access (may be configured with paprefs, so leave this commented
### here if you plan to use paprefs)
#load-module module-esound-protocol-tcp
#load-module module-native-protocol-tcp
#load-module module-zeroconf-publish

---

### Post by Endolith on 2009-11-23
Much simpler solution:  Set the computer to auto-login, and then lock the screen after logging in.  :)

---

### Post by kangarooks on 2010-11-27
Hey all

I managed to setup a headless network pulse audio system to which i connect my laptop and my desktop. It is mostly based on this thread, but also created with the help of others. I hope you'll like it. It works, so if you have any other questions please tell me so :)

[http://pleasanthacking.com/2010/11/28/linux-media-network/](http://pleasanthacking.com/2010/11/28/linux-media-network/)

enjoy :popcorn:

---

