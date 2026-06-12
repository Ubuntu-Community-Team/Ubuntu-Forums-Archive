---
title: "Intel 945G Express + Ubuntu 12.04 = No sound, video garbled, crash"
date: 2012-05-13
forum: Multimedia Software
---

### Post by jemdos on 2012-05-13
Greetings from Sunny Spain 8)

Thanks in advance for reading this. Please forgive my terrible grammar and my awful spelling. 

I've spent a fine Sunday trying to install Ubuntu 12.04 on my girlfriends' old PC, and now my manhood is in doubt 'cause is been a failure.

I've tried before installing Ubuntu 12.04 on a Parallels VM (went OK and smooth) and on a Dell laptop I own (went OK, but not as smooth). I don't know if I prefer 12.04 to 10.04 but I thought I could give her some fresh OS that also looks less menacing.

Unfortunately:
a. Video display gets pixelated, garbled after a few minutes of use. Backgrounds look ugly, text cannot be read. Sometimes is even fun, but it's not what's supposed to do.
b. No sound at all.
c. Finally gets slow to crawl, and crashes hard. Hard reset or unplugging the computer, no less.

Computer is a 2005 Dell Dimension 5100, P4, 512 MB RAM, 80GB HDD, 945G Chipset. 

I cannot get to her computer to try 1,568 things in order to get running the PC flawlessly. Her place is 30 Kms from mine, and I have better things to do when I am with her than... well. I am toying with the idea of installing 10,04 instead after reading thinks like this ([https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/180248](https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/180248)) but I thought I could ask the comunity for some fresh ideas or thinks I could try to get running 12.04 on that ancient computer, or wisdow about how it's merely impossible to run 12.04 on that piece of junk.

Suggestions about buying new hardware (videocard, soundcard...) is not what I am looking for. RTFM are accepted if you give me some pointer to TFM in the first place.

---

### Post by woxuxow on 2012-05-13
My motherboard chipset is almost the same as your girl friend and i have the same problem with graphic but not as bad as her. mine is 945GZ

There is no graphic driver built by intel 
so you have to use the free driver (ALSA) that it is not as good as intel windows driver

for your graphic you can not do anything just leave it alone

what is her sound card model

512MB ram is not good enough to installing ubuntu, 1GB is recommended 
in my opinion try xubuntu to get advantage of having a old system

---

### Post by cryptotheslow on 2012-05-13
I think you are going to struggle with only 512MB of RAM. Running Ubuntu 12.04 and Firefox with just 2 tabs open is using 633MB here.

I suggest trying a distribution with a lighter desktop environment such as Lubuntu (LXDE) or Xubuntu (XFCE)
[http://lubuntu.net/](http://lubuntu.net/)
[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by jemdos on 2012-05-14
Greetings from Sunny Spain 8)

Thanks for your answers.

According to [https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#System_Requirements) the minimun requeriments are just 384 MB. I did not expect great speed, I did expect a working (but slow) computer.

If I cannot get 12.04 running the plan is trying 10.04 instead. Or even 8.04. What I need is (a) Graphical UI support (b) Web Browser (c) Flash. 

Video problem is a big issue, cause you cannot even read the text on the screen, so I have to solve it. And also the sudden crashes, of course. 

PC has no soundcard, is integrated with the Chipset (the same happens with video) and according to Dell handbook, is a "Sigmatel STAC9220". Did not check that at her place because I was focusing on video and crash issues, and I don't even know if it is related or not.

Again, thanks a lot.

---

### Post by woxuxow on 2012-05-14
i have the same chipset and the same ubuntu but my graphic issue is not like yours and it's not emergency. i can watch movies (not as good as win) , reading and anything which anyone else can do

i think your problem that you have to fix is not ubuntu 12.04 and is not graphic driver. try ubuntu 11.10 live cd or a GNU/Linux dist else to make sure that your problem is what it is

---

