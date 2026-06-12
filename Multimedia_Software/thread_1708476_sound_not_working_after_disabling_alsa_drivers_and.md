---
title: "sound not working after disabling alsa drivers and installing oss"
date: 2011-03-16
forum: Multimedia Software
---

### Post by loai.ghoraba on 2011-03-16
Hi

I'm somehow new to Ubuntu so I need some help :)

I'm using Ubuntu 10.10 and I had the sound on my Toshiba satellite laptop working and everything is fine-except for the built in mic..no response at all, I had to switch to windows whenever I want to use the mic "etc, skype calls"

I Googled a little bit and upon this advise [http://ubuntuforums.org/showthread.php?t=932896](http://ubuntuforums.org/showthread.php?t=932896) I disabled alsa drivers using the commands

[B]sudo update-rc.d -f alsa remove
sudo update-rc.d -f alsa-utils remove 
[/B]and then downloaded oss debian package and installed it, as the advise said.

But the result now is that I have no sound at all !!:( no mice nor speakers...any clue how  to fix this ? how to enable alsa drivers again and return to "speakers working-mic not working ?"

and ofc if there a solution to get my mic also working this will be great :)

any help ?

---

### Post by johntaylor1887 on 2011-03-16
In your case I would just go into synaptic and remove the oss drivers first. Then while still in synaptic, go to settings>repositories>other software>add button then put in **ppa:alsa-backports/ppa**

Close window and reload when asked. You can then search synaptic for alsa and reinstall it. You will now have the latest version of alsa which may even fix your mic problem. 

Be sure to check your sound properties to make sure you're using the alsa drivers also.

---

### Post by Yellow Pasque on 2011-03-16
Ubuntu/Canonical went out of their way to disable OSS in the kernel and the devs have no interest in fixing it. Attitude of Debian devs is a bit better, but definitely not enthusiastic. Run Arch Linux if you want to experiment with OSS4.

---

### Post by loai.ghoraba on 2011-03-17
@Johntaylor: thanks a lot , I uninstalled oss already and the sound is back again

P.S. : I try to added the repository you said, but synaptic failed to fetch from it :
Failed to fetch [http://ppa.launchpad.net/alsa-backports/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/alsa-backports/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/alsa-backports/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/alsa-backports/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

seems that there are no such pages, so I'm back to my original problem: speakers and no mic..

@Tem: I think I won't change Ubuntu for a while , thx for the advise anyway :)
[B]
[/B]

---

### Post by Yellow Pasque on 2011-03-17
What kind of laptop is it? Better yet, run and post alsa-info script [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by loai.ghoraba on 2011-03-17
My laptop is Toshiba satellite L655

and I downloaded the script, but how to run it ? :D " as I said, I'm kinda new to Ubuntu"

---

### Post by Yellow Pasque on 2011-03-17
Mic seems to be a common issue. [http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

---

### Post by loai.ghoraba on 2011-03-17
Thanks loads !! this fixed my issue , the mic is working perfectly now.
thanks a gain :D :D

---

