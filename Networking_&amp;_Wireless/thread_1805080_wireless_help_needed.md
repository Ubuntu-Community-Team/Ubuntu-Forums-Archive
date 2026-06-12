---
title: "wireless help needed"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by borincano on 2011-07-15
i would like to point out im am a complete noob in every sense of the word so please dont assume i know anything when giving me instructions.
 
i just installed ubuntu 10.04 lts fully updated on my toshiba nb255-n250. when i go to the network manager on the top panel and try to connect to a public unsecured wireless signal it will try to make the connection about a minute or two but fails. i have a wifi router in my house that i can connect to though wich has me confused as to why it wont work. Now under windows 7 i have no problem connecting to the same public unsecured signal. this is the same computer with both OS on dual boot. i really enjoy ubuntu but if i cant solve this issue i will have no choice but remove it since im always on the move and my netbook goes everywhere with me. thanks.

---

### Post by borincano on 2011-07-15
50+ views and no one has single possible solution? Help me out guys, I really like this OS, its fun to use and very light on resources and so much faster than windows 7 on my netbook. I really need a solution.

---

### Post by ratcheer on 2011-07-15
It is hard to know what is wrong when it works at home but not with a public hotspot. Obviously, since it works at home, the wireless card is apparently configured and operating, correctly. I have no idea how to help you.

Tim

---

### Post by borincano on 2011-07-15
I failed to mention that the service is provided as a DSL where i have to input my username and password every time I connect to the internet on this public hot spot. Its a sort of pay as you go thing. On windows 7 I can connect to this signal even with out putting in the username and password I just wont have internet access. In Ubuntu It wont even connect to the signal. I hope this clears things up a bit.

---

### Post by atomicben on 2011-07-15
From a noob to a noob all I can suggest is installing newer drivers and crossing your fingers.

**DO YOU HAVE ALL THE STUFF IT TAKES TO COMPILE??** - If so here are the steps, if you aren't sure, scroll down and find those instructions - do this first (especially if you aren't sure, you won't blow anything up by running the stuff below first!)


**Installing newer drivers:**
Open a terminal and:

wget [http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6-stable/v2.6.39/compat-wireless-2.6.39-1.tar.bz2)

sudo mkdir /usr/src/drivers
sudo cp compat-wireless-2.6.39-1.tar.bz2 /usr/src/drivers
cd /usr/src/drivers
sudo tar jxvf compat-wireless-2.6.39-1.tar.bz2
cd compat-wireless-2.6.39-1
sudo make                                       
sudo make install
sudo reboot


Description of steps above:
1. download newer stable drivers
2. make a new directory where we will extract the source code
3. copy the compressed file to the new directory
4. change into our new folder
5. un-compress the new drivers (this also makes a new directory)
6. change into the new directory where the files were un-compressed
7. compile the drivers (this will take a while)
8. install our new drivers
9. reboot your system

10. I'd appreciate it if you would let me know if thinks worked or not.


**Getting the stuff you need to compile source code:**
To get the stuff you need to compile do this:

Open a terminal and:

sudo dpkg --configure -a && sudo apt-get install -f && sudo apt-get update

sudo apt-get install linux-headers-$(uname -r) build-essential make  patch gcc gettext autoconf python-psyco subversion tcl8.5 openssl zlib1g  zlib1g-dev libssh2-1-dev libssl-dev libnl1 libnl-dev libpcap0.8  libpcap0.8-dev python-scapy cracklib-runtime

---

### Post by borincano on 2011-07-22
turns out a issue with the specific router i was trying to connect to. thanx for the input though.

---

