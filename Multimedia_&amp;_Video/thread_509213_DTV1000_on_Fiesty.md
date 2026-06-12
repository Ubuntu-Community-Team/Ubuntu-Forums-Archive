---
title: "DTV1000 on Fiesty"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Revolution on 2007-07-25
I've seen a few posts asking for help with Fiesty Fawn and Leadtek DTV1000 tuner cards.

Firstly, I jumped in and plugged in the DTV1000 card and crossed my fingers.
I installed Kaffeine from Synaptic Package Manager.

(If you are a beginner, click System - Administration - Synaptic Package Manager then search for Kaffeine. Click the box next to Kaffeine and then click 'Apply')

Kaffeine should install happily.
You'll probably find when you run it that it does not see the DTV1000 card.

The kernel at this point didnt have the DVB modules installed so I edited /etc/modules and added the DVB kernel modules.

Open a terminal (click Applications - Accessories - Terminal. In the terminal window enter:
cd /etc
You should now be in the /etc directory.
Now enter: sudo gedit modules
(enter your administrator password) and you should now have gedit open.
add these modules to your list.
cx88-dvb
dvb-core
cx88-alsa

Save and close gedit.

I had to install the decoders for Xine (or else you just get a black screen in Kaffeine).

Open Synaptic Package Manager again.
Search for libxine
Tick the box next to libxine1-plugins
Click on 'Apply'

Once the Xine plugins are installed close Synaptic.

Run Kaffeine and this time it should find your card.
Click on the Digital TV button in Kaffeine.
Run the auto-tune fuction and it should find your local stations.

Good luck.

---

### Post by nami on 2007-07-29
doesn't seem to work.  i just bought this very card...

---

### Post by Revolution on 2007-08-04
Hi Nami.

In order to help you (this is the purpose of the forums) I'll need a bit more information.
I gave a step-by-step instruction above and I wonder which part you had trouble with?

---

### Post by nami on 2007-08-05
Hi

The problem was that in kaffeine, it would not detect any channels.

---

### Post by aliasfreq on 2007-08-14
Try ```
sudo modprobe cx88-dvb
```

---

### Post by Revolution on 2007-08-25
> **nami said:**
> Hi

The problem was that in kaffeine, it would not detect any channels.

I'd say your card is dead.
Or possibly the 'Tuner Control' interface is not working.
There is a specific driver for controlling the tuner. Its possible that didn't install correctly.

I'd try getting another card or find a Windows PC and install the original windows software.
If it works on a WinPC then you know to look at your Linux install.

---

### Post by nami on 2007-08-26
Installed it on windowxp and it detects no channels...

HELP

---

### Post by bfbf on 2007-08-27
I think that would suggest a bad card then. In XP have you selected your area and in come cases your TV area rather than where you live.

e.g I have to select London rather than the South east.

Anyway I am about to try this guide to get my card working in Ubuntu :)

---

### Post by nami on 2007-08-27
yes i selected london using the software provided with the card in xp.  still nothing...  gonna phone them tomorrow and ask for a replacement.

or, is there a better card that i can get?

---

### Post by ministoat on 2007-09-04
thanks for the guide..i have got stuck on the scanning channels..kaffiene is finding locks but not adding any channels. i've been able to pick up all the local providers with the same card/aerial in my flat before.

is there anything in particular i could set that might help it find the channels? i've made sure that it's scanning my closest broadcasting place too

---

### Post by ministoat on 2007-09-04
> **bfbf said:**
> I think that would suggest a bad card then. In XP have you selected your area and in come cases your TV area rather than where you live.

e.g I have to select London rather than the South east.

Anyway I am about to try this guide to get my card working in Ubuntu :)

 /wave from byo  (jikslee)

---

### Post by beechmore on 2007-09-11
Hello Revolution.

Until I read your post I was really struggling with my TV card and trying to get it to work. It's a Leadtek WinFast DTV1000 T and I'm running Ubuntu 7.04. However, after I found your post and followed your instructions it's now working like a dream and I can watch all the Freeview digital channels here in the UK.

A big thankyou from a very happy Pom.

beechmore

---

### Post by nami on 2007-09-11
Any chance you can take a pic of your antenna cable and post it here, because I am in the uk in a freeview area and it does not work.

also, do you need to freeview box?

---

### Post by beechmore on 2007-09-11
Hello nami,

I'll do what I can. However, would you clarify. Do you need a pic of the cable when connected to the card? 

Also, not sure what you mean by your second request about the freeview box.

Regards

beechmore

---

### Post by iSplicer on 2007-12-18
Hey guys

On wikipedia ([http://en.wikipedia.org/wiki/Kaffeine](http://en.wikipedia.org/wiki/Kaffeine)) it says you need KDE to use Kaffeine. So does that mean I need to install kubuntu to use Kaffeine?

THanks

---

### Post by nami on 2007-12-19
> **beechmore said:**
> Hello nami,

I'll do what I can. However, would you clarify. Do you need a pic of the cable when connected to the card? 

Also, not sure what you mean by your second request about the freeview box.

Regards

beechmore

no need anymore beechmore.  i gave the card back.  both did not work so i don't know what is going on.  i don't understand why i cannot get freeview to work on my computer.  so far i have tried 2 different cards.

---

### Post by beechmore on 2007-12-19
Hi iSplicer

No I don't think so. I'm currently using Kaffeine with with a standard Ubuntu Gutsy 7.10 install and I previously used it with Ubuntu Fiesty 7.06 and it works fine with both.

Hope that helps

beechmore

---

