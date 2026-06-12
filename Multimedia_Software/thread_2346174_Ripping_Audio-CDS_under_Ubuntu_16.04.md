---
title: "Ripping Audio-CDS under Ubuntu 16.04"
date: 2016-12-12
forum: Multimedia Software
---

### Post by ulli-basel on 2016-12-12
Hello, 

ripping of audio CDs does not work on my Ubuntu 16.04 PC since setting up the system. I installed all codecs (I am aware of) as well as  "restricted extras". Any audio CD is recognized when inserted and played  well by both VLC and Rhythmbox. But both Asunder and Sound Juicer do  not show any content of the CD (i.e. artist, tracks, etc.). 


  With 12.04-based elementary OS ("Luna") being installed in another  partition on the same box Asunder works perfectly and ripping CDs has  never been an issue. 


  Does anybody know how to fix this? 
thx in advance 
Ulrich

---

### Post by speartip on 2016-12-16
CDs rip fine for me on 16.04 using Asunder.
First thing to do is check that Asunder correctly identifies the location of your drive, in preferences/general. It's default is something like /dev/cdrom. In my case it needed changing to /dev/sr0.
Second, make sure things like lame & flac are installed. They aren't by default, but are needed by Asunder.

---

### Post by drumkitcat on 2016-12-19
I tried over the weekend to install Asunder in Ubuntu Studio 16.10, but it couldn't be found in the repository - I was using it recently on another computer using Linux Mint.

Is there a particular setting somewhere I need to change so that I can have the software installer find Asunder?

---

### Post by howefield on 2016-12-19
Asunder is in the Ubuntu 16.10 repositories so you should be able to get it.

[http://packages.ubuntu.com/yakkety/asunder](http://packages.ubuntu.com/yakkety/asunder)

Have you the "*universe*" repository enabled ?

---

### Post by drumkitcat on 2016-12-20
Yes, I checked that yesterday - I have the universe repository enabled, and still it shows that Asunder is not available.  I had it do a reload and everything.
There must be something else I'm missing there.
I wonder if I should redirect where it looks to the server - right now it's pointing to Canada; would that matter though?

---

### Post by mc4man on 2016-12-20
> **drumkitcat said:**
> Yes, I checked that yesterday - I have the universe repository enabled, and still it shows that Asunder is not available.  I had it do a reload and everything.
There must be something else I'm missing there.
I wonder if I should redirect where it looks to the server - right now it's pointing to Canada; would that matter though?
you could try another mirror or use the USA one.  Check first with 
```
apt-cache policy asunder
```

---

### Post by howefield on 2016-12-20
> **drumkitcat said:**
> There must be something else I'm missing there.

How have you tried to install the application ?

There have been issues with the Software Centre not showing some applications, perhaps this is one of them. Have you tried in a terminal..

```
sudo apt install asunder
```

---

### Post by drumkitcat on 2016-12-20
Thanks for the replies - I will try to mirror a different software source, like USA or something - as well as the apt cache policy asunder command.

I did try the **sudo apt install asunder** but I got a message saying something was locked in the dpkg folder (sorry I am not near that computer at the moment)

I have used Asunder in Linux Mint, and it's a very useful program for my music activity, so I'm very eager to get it on Ubuntu Studio.

---

### Post by howefield on 2016-12-20
> **drumkitcat said:**
> I did try the **sudo apt install asunder** but I got a message saying something was locked in the dpkg folder (sorry I am not near that computer at the moment)

May well have had more than one package manager running to get the lock message.

---

### Post by drumkitcat on 2016-12-20
Ok, thank you all, it worked... turns out I did have more than one package manager running before - which is why I got the error.
I did a reboot and tried it again tonight and it worked first crack using the sudo apt install asunder.

This is fantastic - so thanks very much to you all, greatly appreciated!!!!

---

### Post by howefield on 2016-12-21
> **drumkitcat said:**
> Ok, thank you all, it worked... 

Cool, glad you sussed it out, feel free to mark the thread as solved. :)

---

### Post by shantiq on 2016-12-22
Another really nice route you can take with your terminal is this >>



* To copy an audio CD in the most accurate way, first run*

```
 icedax dev=/dev/cdrom -vall cddb=0 -B -Owav
```
for external drive adjust sr1 to your drive name  >>
```
icedax dev=/dev/sr1 -vall cddb=0 -B -Owav
```


* and then to write run*

```
 wodim dev=/dev/cdrom -v speed=2 -dao -useinfo -text *.wav
```

  for external adjust sr1 to your drive name
```
wodim dev=/dev/sr1 -v speed=2 -dao -useinfo -text *.wav
```

---

