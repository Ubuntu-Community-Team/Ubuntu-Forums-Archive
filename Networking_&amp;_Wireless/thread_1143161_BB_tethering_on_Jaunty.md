---
title: "BB tethering on Jaunty"
date: 2009-04-29
forum: Networking &amp; Wireless
---

### Post by victorbrca on 2009-04-29
Anyone able to tether using BB on Jaunty? I was wondering if this post ([http://ubuntuforums.org/showthread.php?t=617811](http://ubuntuforums.org/showthread.php?t=617811)) is still the only way or if it's a bit easier on Jaunty.


Vic.

---

### Post by hamannp on 2009-04-29
Greetings.  I had endless problems on both intrepid and jaunty with Barry.  In particular, I have the BlackBerry Pearl that has problems with bcharge grabbing the network interface.  If you have a different model, you might be fine installing from the repository.  If you're comfortable with compiling, I would recommend that you build it from source.  If you don't have git installed, I'd recommend that you do:

sudo aptitude install git-core
sudo git clone git://theblackberrygiturl

I followed the instructions CAREFULLY from the barry website.  Make sure that you install all of the pre-requisites.  I found a guy that did a tutorial with the bash command with every pre-req included.  I did some googling, and couldn't find it again.  Sorry for not having the link.  I also had trouble installing a fortran library that was required.  Apt-get couldn't come up with a solution, but aptitude did.  I recommend that you use aptitude.  Finally, the gotcha that caused me problems is that the default install directory is different than the default configuration files.  This fact is in the instructions on the barry site if you look carefully.  I went and edited the files.  It's probably easier to specify the correct directory on the command line when you do ./configure.  Again, it's in the instructions.

I hope that some of that helps.  FWIW, I've now got it working awesome. I'm having trouble with my KVM network being slow [I've got an open thread about it], but I have it rigged so that my VM's all share the barry connection.  It's really cool.  

Good luck!
Paul

P.S. Ubuntu rocks!

---

### Post by hamannp on 2009-04-29
Here's the line.  It will say something about g77 not being available.  If you use aptitude instead of apt-get, it will propose a solution.  Take it.


sudo aptitude install opensyncutils libopensync-dev opensync-plugin-* libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglademm-2.4-dev libevolution3.0-cil doxygen doxygen-gui g++ gawk gcc-avr libgcj8-dev g77


I need to install barry on another machine.  I'll write a bash script when I get to it.  It will probably take me a week to get to it though.

Cheers! Paul

---

### Post by victorbrca on 2009-04-30
Thanks a lot for the reply and all the information Paul. I was able to get it working with [Berry4All]("http://www.berry4all.com/"). Very easy!! :)


Vic.

---

### Post by hamannp on 2009-04-30
Very interesting.  At the time, I got the original BBtether working before I got barry working.  The trouble was that I wasn't getting broadband -- just 14.4 or so.  Also, while it generally worked with BBtether and BB Pearl, bcharge would still sporadically grab the interface.  I know that the 8130 was a PITA beyond all others.

Just curious, what speeds are you getting?  I'm on Sprint.  W/ barry I realize speeds of about 50-80k with a peak about 115k or so.  I guess 3g is layer 2???????

Anyhoo, congrats on getting a connection working.

Cheers! P

---

### Post by victorbrca on 2009-04-30
Hey Paul,


  I actually haven't really tested the speed on the phone. I know I got it working but I have avoided using as I need to check with my provider (Rogers/CA) if they charge extra for tethering. I know when I first got the phone they did, but I can't find anything on their site anymore.

  I'm also using EDGE and not 3G, so I that will make it even worse.

  Now connection on the 3G wireless stick (that a lot of providers are introducing) is fairly fast: [Results]("http://www.speedtest.net/result/459460701.png")

 Vic.

---

