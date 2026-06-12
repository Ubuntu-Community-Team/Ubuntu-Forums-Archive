---
title: "getting xubuntu mp3 support with no internet"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by whereami on 2008-02-02
i recently installed xubuntu on an old laptop that has no way to receive internet

i would like to be able to play mp3s on it but i cannot figure out how to get the codecs or plugins i need installed without an internet connection on that computer.

i searched through some other threads on this topic but nothing that i tried has worked. 

any help is appreciated, thanks!

---

### Post by carlinuxlearner on 2008-02-02
You could try installing "APTonCD" on a x/k/ubuntu computer that's connected to the Internet. (I believe it's just a "sudo apt-get install aptoncd") just install stuff you want on that computer , burn a disk (with APTonCD) and put the disk in the laptop.
Or you could do what I did, just download Linux Mint [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php) and install it, (it comes with all those codecs, and it's very similar to Ubuntu(I think basicly is ubuntu)).

C@RL

---

### Post by whereami on 2008-02-02
thanks for the reply!

unfortunantly i dont really have any other computers with linux on them connected to the internet. my main computer (the one i'm using now) is running xp pretty smoothly and i would rather not go through the effort of installing a new OS. 

is there some way i can find the packages or software i need from this computer, download it, then either put it on a CD or flash drive to transfer? i just dont know where to find the files i need to transfer to make it work.

---

### Post by carlinuxlearner on 2008-02-05
If you just Google the packages you need (whatever.deb), it will find them. The reason I told you to go with Linux Mint, is because I tried to do the same thing, it was a royal pain, and I never got it to work! (until I installed Linux Mint)

C@RL

---

### Post by murali on 2008-02-07
[B]Well, I also need the same solution. Is there any mp3 software available to download 
into an xp system, and then can be installed in ubuntu? Anybody help?[/B]

---

### Post by carlinuxlearner on 2008-02-09
Ok, After some research I came up with this. Try downloading this, [http://ftp.ussg.iu.edu/linux/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.5.debian-1_i386.deb](http://ftp.ussg.iu.edu/linux/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.5.debian-1_i386.deb)
copy it to the desktop on your Ubuntu computer, open up a terminal and type in this "cd Desktop" then type in this "sudo dpkg -i gstreamer0.10-fluendo-mp3_0.10.5.debian-1_i386.deb"
let me know if it works. If it doesn't please copy any error messages that you get and post them here.

C@RL

---

