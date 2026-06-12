---
title: "HDMI not connecting. HP Pavilion dv4 1280us"
date: 2011-07-02
forum: Multimedia Software
---

### Post by WanchoPiskado on 2011-07-02
Hello there and thanks for attention,

I have a HP Pailion dv4 1280us and a Panasonic TC-L42U22X lcd tv.

On Windows, both HDMI video and HDMI audio work beautiful.

But if I boot Ubuntu 10.04, even if the HDMI cable is correctly connected, the tv doesn't receive any HDMI signal from the pc. The Sound panel of Ubuntu shows something that I guess regards HDMI  audio, but nothing comes out of the tv speakers. Of course I already  installed the restricted drivers that are automatically suggested by  Ubuntu when I go to Administration - Additional Drivers.
But I want to use HDMI video and audio with Ubuntu.

May I please ask for your help ?

Cheers,

Wancho

---

### Post by WanchoPiskado on 2011-07-05
Bump..:evil:

Are there drivers missing? Is that a possibility?

I regret that the HDMI is not working. Everything else worked straight out of the box. 
Runs smooth. 
Quick startup. 
Wanted to impress my friends, but this HDMI thing is bugging me.

---

### Post by WanchoPiskado on 2011-07-05
I am now going to try to update my drivers:

> 
[SIZE=3]**Part B (Safe/Optimal)**[/SIZE]
*Users who wish to try the Safe **or** Optimal configurations must follow this part.*

1. Add the [X Updates PPA]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/") to your sources.list:

Edit /etc/apt/sources.list:
     Code:
     $ gksudo gedit /etc/apt/sources.list 
Add these entries to the end of your sources.list file (if they do not already exist):
     Code:
     deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) jaunty main #X-Updates PPA 
2. Import the X Updates PPA key, update your apt sources, and perform an upgrade:
     Code:
     $ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9 $ sudo apt-get update $ sudo apt-get dist-upgrade 
[COLOR=Blue]**N.B.:** If you are asked to remove any  packages, immediately cancel the process. The expected behaviour is only  to upgrade packages, not to remove.[/COLOR]

3. If you want to use the Safe configuration, you're finished - proceed to the **Important Note** section. If you want the Optimal configuration, continue to Part C.

(from [http://ubuntuforums.org/showthread.php?t=1130582&highlight=4500mhd+driver](http://ubuntuforums.org/showthread.php?t=1130582&highlight=4500mhd+driver) )

Should i do this or would it do potentially more harm?

---

### Post by martinob on 2011-09-25
any news?I have the same problem!

---

### Post by WanchoPiskado on 2012-08-06
Nope, nothing yet. In the meantime I have 12.04 LTS installed. Still nothing.

---

### Post by WanchoPiskado on 2013-01-10
FINALLY!
Solved. It was not ubuntu or drivers. It was just a nasty connector. I cleaned the HDMI port with a sharp knife, et voila!
It works!
:popcorn:-time!

---

