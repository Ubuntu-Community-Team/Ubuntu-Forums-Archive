---
title: "[SOLVED] Sopcast to work in 7.10 ?"
date: 2008-02-22
forum: Multimedia &amp; Video
---

### Post by iheartubuntu on 2008-02-22
Has anyone been able to get Sopcast to work in Ubuntu 7.10? If so please help! Thanks.

---

### Post by ryukent on 2008-02-22
This should work:

[http://ubuntuforums.org/showthread.php?t=703409](http://ubuntuforums.org/showthread.php?t=703409)

---

### Post by iheartubuntu on 2008-02-22
Thanks for the info. Im still rather new with Ubuntu codes and using the terminal.

I got so far as to downloading the Sopcast binary.

I dont know how to unzip, so I dragged the folder out of the zip to the desktop. It seemed to work fine. I have a folder now on the desktop with the files in it. When I try to do "cd sp-auth" to go into that new folder, it says no such thing.

Any tips?

---

### Post by ryukent on 2008-02-22
Say you put it on your desktop and right hand clicked on it and selected extract here, it would put it in a directory called "sp-auth". But that is in your 'Desktop' directory uder your user in /home. So when you open the terminal, try

cd ~/Desktop/sp-auth

That should put you in the sp-auth directory within your desktop. The ~ is for the current user.

---

### Post by iheartubuntu on 2008-02-22
Thanks. I got through all the instructions and started qsopcast and no video comes up. Ive got VLC installed, I got the config set properly. I can see some chinese channels and when I launch one it gets up to 100% but after that, nothing after pressing player.

---

### Post by ryukent on 2008-02-22
Right, it could be the qualiy of the channel, it could be that for some reason it's using a codec that VLC doesn't have access to.... very unlikely.

Can you try this channel please. Paste it into qsopcast and hit launch. Make sure the player button is selected.

sop://broker1.sopcast.com:3912/6002

Can you confirm... does your player (VLC) actually launch. If it does, what is the readout in the bottom right corner?? See my screenshot. It says [http://127.0.0.1:16655](http://127.0.0.1:16655)

---

### Post by iheartubuntu on 2008-02-22
Nothing happens when I click search or launch. 

I am having some problems with my sound card not working and a gstreamer problem, but no one can fix it. Ive got some sound like Amorak, and some games too, but generally no other system sounds or movie sounds work.

Well, some channels finally appeared within sopcast and its at 100% or there abouts but clicking player does nothing for me.

---

### Post by iheartubuntu on 2008-02-22
I even got the Firefox linking to work, but still no video pops up.

---

### Post by ryukent on 2008-02-22
OK, can you check your config in QSopcast is set to the same as mine. Your save directory will be different obviously.

Note... I'm currently experiencing problems with the sopcast server. I think their system is temporarily down. That shouldn't affect your player popping up though.

---

### Post by iheartubuntu on 2008-02-22
BEAUTIFUL! It works!  Thanks!

---

