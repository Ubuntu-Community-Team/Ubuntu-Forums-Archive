---
title: "Entering WEP security code does jack ****. Intel Corporation PRO/Wireless 4965 AG"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Swashy on 2009-04-24
My wired internet works fine but as I said when I put in the WEP security code, which works on my Vista dual boot and any other wireless computer I've tried at home, it does nothing. The icon acts like its doing something useful for a bit, connecting to the network, but then gives up and asks for the code again.

I read some stuff about ndiswrapper and how it was an alternative driver for my wifi card, but I honestly have no idea how anything more complicated than automatically installing programs on the Synaptic Package Manager works. I threw some sudo-y lines into the terminal suggested in some other supposed howto threads, but it kept saying ndiswrapper had no utils. Does anyone mind helping out a Ubuntu nub?

---

### Post by kmoz on 2009-04-24
same problem here for WPA2 personal code.  Tried TKIP and AES ciphers, code works fine on same laptop in XP.  When I edit the connection and click "show password", the password is changed to entirely alphanumeric, not sure if this is a security feature or not.  If it's not, it's changing the password I'm entering.

Running Jaunty on an Acer Inspire ONE, wireless is "working" in that it's detecting other networks.

---

### Post by lisati on 2009-04-24
A couple of possibilities come to mind.

There are two entry modes for passphrases: hex and ascii. The first thing to check is that you're using the appropriate choice.

Another thing to check is to see if your router is set to use MAC address filtering (this is unlikely to be the problem if you are able to use the same machine to connect using Windows)

A third possibility is that there is some kind of conflict with another wireless network in your area. This can happen if a neighbour's access point (router) is broadcasting on the same channel (frequency) as yours.

Other forum users might have suggestions for other things to check.

---

### Post by jimv on 2009-04-24
This has been happening to me since an update to 9.04 a few weeks ago.  Works fine if I disable encryption, and 8.10 works fine too.  I also noticed that if I use the Linux driver for my card then WPA works...but this particular driver is unstable, so I'm using Ndiswrapper.

I tried the latest build (compiled from the latest source) of Ndiswrapper, and it did not help.

---

### Post by kmoz on 2009-04-24
Followed these steps, made a new connection, it works:
[https://bugs.launchpad.net/ubuntu/+bug/350352](https://bugs.launchpad.net/ubuntu/+bug/350352)

Not sure who to report this bug/workaround to.

it's the damn athk5 module not being used.  Instructions follow:


```
I have this working by doing the following:

1: Add the following lines to /etc/modprobe.d/blacklist.conf

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi

2: Add the following line to /etc/modules

ath5k

3: Install the linux-backports to get the latest ath5k driver

sudo apt-get install linux-backports-modules-jaunty

4: Remove any currently installed modules

modprobe -r ath5k acer_wmi ath_pci ath_hal

5: Install the ath5k modules

modprobe ath5k

At this point you should be good to go.

```

---

### Post by Swashy on 2009-04-24
> **lisati said:**
> A couple of possibilities come to mind.

There are two entry modes for passphrases: hex and ascii. The first thing to check is that you're using the appropriate choice.

Another thing to check is to see if your router is set to use MAC address filtering (this is unlikely to be the problem if you are able to use the same machine to connect using Windows)

A third possibility is that there is some kind of conflict with another wireless network in your area. This can happen if a neighbour's access point (router) is broadcasting on the same channel (frequency) as yours.

Other forum users might have suggestions for other things to check.

I've tried every code, id and number on the side of my router for every passcode option on here and none work. There are also at least 5 other wireless connections around my house but I don't see why that would affect it.

Kmoz could you explain that code? I see that you put soem just straight in console but how do you add lines to other files?

---

### Post by Swashy on 2009-04-24
E: Couldn't find package linux-backports-modules-jaunty

I can't install the latest ath5k driver.

---

### Post by kmoz on 2009-04-25
> **Swashy said:**
> I've tried every code, id and number on the side of my router for every passcode option on here and none work. There are also at least 5 other wireless connections around my house but I don't see why that would affect it.

Kmoz could you explain that code? I see that you put soem just straight in console but how do you add lines to other files?

you need to use an editor, i like nano, so:

```
sudo nano /etc/modules
```

will bring up the modules file to edit.  I can't stress it enough, before you begin, BACKUP ALL THE FILE YOU EDIT

so something like:

```
sudo cp /etc/modules /etc/modules_bak
```

then use nano to edit the files - all the instructions should have sudo in front of them, such as 'sudo modprobe ath5k'

hope that helps

---

### Post by chili555 on 2009-04-25
> **kmoz said:**
> Followed these steps, made a new connection, it works:
[https://bugs.launchpad.net/ubuntu/+bug/350352](https://bugs.launchpad.net/ubuntu/+bug/350352)

Not sure who to report this bug/workaround to.

it's the damn athk5 module not being used.  Instructions follow:


```
I have this working by doing the following:

1: Add the following lines to /etc/modprobe.d/blacklist.conf

blacklist ath_pci
blacklist ath_hal
blacklist acer_wmi

2: Add the following line to /etc/modules

ath5k

3: Install the linux-backports to get the latest ath5k driver

sudo apt-get install linux-backports-modules-jaunty

4: Remove any currently installed modules

modprobe -r ath5k acer_wmi ath_pci ath_hal

5: Install the ath5k modules

modprobe ath5k

At this point you should be good to go.

```
And what, pray tell, does this have to do with the original poster's Intel 4965ABG?

---

### Post by kmoz on 2009-04-26
same symptom, different system, pointing to larger issues with Jaunty wireless support perhaps.  If it helps great, if not, no harm in posting now is there?

---

### Post by chili555 on 2009-04-26
> no harm in posting now is there?I strongly disagree. The original poster is trying to figure out how to enter all this ath5k code with the hope, fueled by your post, that it's going to help his Intel 4965AGN connect to a WEP encrypted access point.> If it helps greatYou know perfectly well that messing about with ath5k can't possibly help. Why send the poor guy down a dead-end road? Your post only frustrates a new user.

---

### Post by RD1 on 2009-04-26
Ok .... This may have nothing to do with the OP's problem but I have to bring it up.

The OP specifies WEP and the responses seem to be speaking toward WPA. These are two different security protocols.

The problem may be as simple as trying to use a WPA code for WEP. It just won't work.

---

### Post by Swashy on 2009-05-04
Mmmm it did nothing unfortunately. Thanks for trying though. Funny thing is, my wireless works fine at my friends house, but not with this intel thingy. Should I find out what kinda wireless router my friends is using or is that useless informmation?
> **RD1 said:**
> Ok .... This may have nothing to do with the OP's problem but I have to bring it up.

The OP specifies WEP and the responses seem to be speaking toward WPA. These are two different security protocols.

The problem may be as simple as trying to use a WPA code for WEP. It just won't work.

Umm... theres no option to enter WPA. Or are you saying my router's code is WPA but Ubuntu doesn't have that option? Maybe I could translate the code into WEP somehow? The options are: 
WEP 128-bit
WEP 64/128-bit Hex
WEP 64/128-bit ACSII
LEAP

Thanks for all your help!

---

### Post by chili555 on 2009-05-04
I think that Network Manager thinks your router is set for WEP, and it's waiting to see if you enter the correct code. Does your WEP key have 5, 10, 13 or 26 characters? If it has 10 or 26 characters, it's HEX, otherwise it's ASCII, which is a bit rare but not unknown. If you have a 10 character key, I'd try dropping it in WEP 64/128-bit Hex.

Please let us know your progress.

---

### Post by Swashy on 2009-05-05
Its a 5 character code, and I'm pretty sure I tried WEP Hex and ASCII. I guess I'll try it again tomorrow when I get home, I'll let you know. Thanks!

---

### Post by chili555 on 2009-05-05
If it's 5 characters, it's ASCII. When you enter the 5 character code in 'WEP 64/128-bit ACSII,' does it connect? Does *dmesg | tail*, run after you try to connect, give us any clues as to what's happening under the hood?

---

