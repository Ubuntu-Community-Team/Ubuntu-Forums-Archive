---
title: "Getting Presonus Firebox to work (ubuntu/linux beginner)"
date: 2010-05-20
forum: Multimedia Software
---

### Post by doctorbot on 2010-05-20
Hey there!

I just installed ubuntu and have absolutly no linux experience what so ever, just to make that clear ;)

So far everything is working fine, but I have trouble getting my Presonus Firebox soundcard to work since Presonus doesn't offer linux drivers.

I read that it's possible to use it via [http://www.ffado.org/](http://www.ffado.org/), but since I am such a noob it would be very nice if someone could help me step by step to get it to work 


thanks !

---

### Post by caprice on 2010-06-22
bump

im in the same situation

---

### Post by cchhrriiss121212 on 2010-06-23
Using firewire on linux distros takes a bit of preparation, so be prepared to spend some time on this. Firewire devices only work with the jack sound server plus ffado, and functionality is built into the kernel which is why you don't get linux drivers. Use synaptic package manager to install the recommended packages.

Here's a simple step by step modified from [this thread]("http://ubuntuforums.org/showthread.php?t=1512702&page=2"):

[LIST=1]
[*]Install the 2.6.31-10-rt kernel (called "linux-rt" in synaptic)
[*]Install startup manager and use it to select the rt kernel as default
[*]Install jack and Ubuntu studio controls
[*]Install libffado, ffado-tools, ffado-mixer-qt4 and ffado-dbus-server
[*]Go into System>Users & Groups and add your user account to the audio and video groups
[*]Open system>studio controls and check raw1394 access box
[*]Enable real time access, from [this guide]("https://help.ubuntu.com/community/UbuntuStudioPreparation"):
[/LIST]
 > Since Ubuntu 10.04 the permissions to enable real time access for "audio" group users are set in the file */etc/security/limits.d/audio.conf*. In versions prior to 10.04 these settings were done in */etc/security/limits.conf* 

These value are suggested by [http://jackaudio.org/faq](http://jackaudio.org/faq). The memlock line determines how much of your memory can be locked by audio processes. Some recommend setting this as half of your total memory (RAM, in KB). The nice setting has been commented out with a purpose, according to one of the main authors of JACK [allowing users to renice processes is not necessary]("http://wiki.linuxmusicians.com/doku.php?id=system_configuration#limits.conf"). Thanks to Scott Lavender for precision about the new file configuration. Don't forget to add your username to the "audio" group (System - Administration - Users and Groups). In other words you need to edit a system file by opening a terminal and pasting this:
```
sudo gedit /etc/security/limits.d/audio.conf
```
And then paste this into the file at the bottom:
@audio - rtprio 99 
@audio - memlock unlimited

If you are still there after all that then you should have a working firewire device. Let me know if you need any clarification on anything.

---

### Post by aquamammal on 2010-09-08
I have a Firestudio Mobile. I think I might have to dual boot the computer with Window's 7 and Ubuntu. Shieet...

Anyone figure this out?

---

### Post by cchhrriiss121212 on 2010-09-08
AFAIK the firestudio range is not supported, but the [FFADO web-page]("http://www.ffado.org/?q=node/35") states that Presonus are working on a driver, that was 2 years ago though so I would not hold your breath.
If you really do not want to dual boot you could always trade it in for a fully supported model, there are plenty out there.

---

### Post by orbesnet on 2011-01-08
[cchhrriiss121212]("http://ubuntuforums.org/member.php?u=948514") is your advice above still the best option at this point?
re:kernel and everything else?

I'm hitting walls left and right trying to get my firebox to make some sounds and I think I've followed your directions....

---

### Post by cchhrriiss121212 on 2011-01-08
^Everything is changing regarding firewire on Ubuntu, by 11.04 it should be more plug and play. But I see from another post that you use 10.04 so the "old" steps above should still apply.

Firewire is only functional through the jack sound server, if you want audio from movies for example you will need to use VLC with the jack plugin. If you want a jack aware music player, try Aqualung.

---

### Post by bomanizer on 2011-02-11
Hi there.
My band mates and me are most likely to buy the Presonus Firestudio Mobile.
I have a dual boot Win7 and Lucid Lynx.
I'll let you know how it goes under Lucid :)

---

### Post by orbesnet on 2011-02-16
Ok, I've actually gotten it running, thanks.

Still experiencing xruns, but I haven't adjusted memlock yet... just happy to get some sound!

Edit:
just checked it out, how's this look to you cchhrriiss:
@audio   -  rtprio     99
@audio   -  memlock    unlimited
#@audio   -  nice      -19

---

### Post by Brendo613 on 2011-02-28
the "#" in the beginning of a line of code comments it out, so that line will no have no effect.  I've read that this may not be needed, though

---

