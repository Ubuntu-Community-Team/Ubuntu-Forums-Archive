---
title: "Microphone problems"
date: 2008-11-08
forum: Multimedia Software
---

### Post by benhayman on 2008-11-08
Hi, I'm using an acer laptop with ubuntu on it, and I've been having some problems with my microphone.

Back in spring I tried using a mic, and it didn't work, so I searched on the internet for solutions and eventually got it working, though I don't remember what I did. Then a few weeks later it stopped working. It was an old and cheap mic so I figured that was the problem.

Today I bought a new one and it didn't work either, so I started searching for a solution again. I tried following the instructions here: [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Does_Not_Work) and when I rebooted after installing the package I found my computer now has no sound at all.

Can anyone help me get my sound working again, and hopefully my microphone?

---

### Post by sirebral on 2008-11-08
What version is your distro?

---

### Post by benhayman on 2008-11-08
It's 7.10

---

### Post by sirebral on 2008-11-08
Aspire 5573? 

[http://junal.wordpress.com/2008/02/29/solving-sound-problem-in-ubuntu-for-acer-aspire-5573-model/](http://junal.wordpress.com/2008/02/29/solving-sound-problem-in-ubuntu-for-acer-aspire-5573-model/)

---

### Post by benhayman on 2008-11-08
Aspire 5100.

I'll try that though.

---

### Post by sirebral on 2008-11-08
A solution for 6.10 Edgy:

[http://ubuntuforums.org/showthread.php?t=362980](http://ubuntuforums.org/showthread.php?t=362980)

---

### Post by sirebral on 2008-11-08
One more post while I wait.  This might be the issue itself.

[http://www.tomshardware.com/forum/47713-35-acer-aspire-5100-5102wlmi-issue](http://www.tomshardware.com/forum/47713-35-acer-aspire-5100-5102wlmi-issue)

In this fix it looks like you just need to setup the volume.

---

### Post by benhayman on 2008-11-08
Thanks, any idea how I find the directories in the instructions "sudo ./configure --with-cards=hda-intel" and "sudo ./snddevices"?

---

### Post by sirebral on 2008-11-08
./configure is a command you run while you are compiling source.

./configure
make
make install

Those are commands, not directories.

---

### Post by benhayman on 2008-11-08
"sudo: ./configure: command not found"

---

### Post by sirebral on 2008-11-08
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Did you read that?

---

### Post by benhayman on 2008-11-09
I've got sound again, thanks for the assistance.

---

