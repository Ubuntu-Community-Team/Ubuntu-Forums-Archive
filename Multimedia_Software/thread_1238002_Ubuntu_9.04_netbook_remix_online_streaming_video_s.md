---
title: "Ubuntu 9.04 netbook remix online streaming video skipping"
date: 2009-08-12
forum: Multimedia Software
---

### Post by ashishj885 on 2009-08-12
hey everyone, new to the ubuntu experience and so far its been very positive.

I have a dell mini 9 Intel ® Atom(TM) Processor N270 (1.60GHz, 533MHz, 512K cache)
512MB 533MHz Dual Channel DDR2 SDRAM
4GB Solid State Hard Drive
Integrated Intel® Graphic Media Accelerator 950

its running ubuntu 9.04 netbook remix.

I upgraded the ram to 1GB, but anyways onto my issue...

I have installed the latest flash player ( atleast I think I went to adobes site and got it ) and when I watch online streaming videos ( hulu, youtube ) the audio comes in fine but the video skips/lags. Is there any way to fix this problem, or is it a issue of my hardware not being good enough ( my old dell laptop had pretty much the same specs and it worked fine, it also had XP ) ?

if there is a soultion I may need some easy to follow instructions as I am completly new to the linux universe, thanks in advance for any help!

---

### Post by zkriesse on 2009-08-12
Did you do an update? Try this...in your terminal...if you don't know how to get there do this...Go to Applications/Accessories/Terminal. In the terminal type the following.

sudo apt-get update

It will ask you for your password which when you type you will NOT see. This is normal. After you type that then type this.

sudo apt-get upgrade

After you do that copy the results/close the terminal and paste results here. Also do a synaptic update by going to the following location. System/Administration/Update Manager. Do that and get back to me.

---

### Post by rmp5s on 2009-08-26
I too am having this same problem on pretty much the same hardware (HP Mini 1030NR, 1GB RAM, ATOM processor, NBR 9.04, etc) so I did what you said.  Here are the results:

me:~$ sudo apt-get update
[sudo] password for me: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done
me:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me:~$ 

Now what do I do?  I'm pretty new to Linux so I'm still learning the ropes.  This thing is SO FAST online now...it's awesome...I really like the NBR so far.  Now, if I can just get this streaming meadia issue sorted out (some sites won't load anything at all...some load and play but don't play well and the pause/seek bar/volume buttons don't work...Pandora.com gets to where the player loads but nothing ever happens...they're all a bit different) and get world of warcraft to work on here, I'll be SET!

On the World of Warcraft front, I have Crossover Games and, while trying to install WoW with it, the install gets to 41% and stops.  Any ideas why?  Anyone have another idea as to how to run WoW on here?

---

