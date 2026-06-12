---
title: "Fresh 10.10 install, homebrew ir blaster no longer works"
date: 2010-11-10
forum: Mythbuntu
---

### Post by nikosapi on 2010-11-10
I just did a fresh install of Mythbuntu 10.10 on a box that was previously running 9.10. I can't seem to figure out how to get my IR blaster working again, it's the standard diode-resistor-led serial transmitter from the lirc website and it worked flawlessly for over a year.

I have it configured for use with a scientific atlanta cable box and irsend doesn't report any errors when sending commands; the cable box doesn't seem to receive them. I've checked the serial port and sure enough, each time I send a command the voltage on pin 4 fluctuates. This leads me to believe it's a software issue, lirc mustn't be sending the right commands.

How can I debug this further?

---

### Post by nikosapi on 2010-11-10
Quick update:

I just tried a mythbuntu 9.04 live cd and my ir blaster works perfectly. So why doesn't it work in 10.10? :(

---

### Post by nikosapi on 2010-11-10
Update #2:

I installed the version tagged "lirc-0_8_7pre1" from the lirc git repo and it works, here's a direct link to the snapshot: [http://lirc.git.sourceforge.net/git/gitweb.cgi?p=lirc/lirc;a=snapshot;h=0128802650dca6adcec443687f0b8d25ec9694da;sf=tgz](http://lirc.git.sourceforge.net/git/gitweb.cgi?p=lirc/lirc;a=snapshot;h=0128802650dca6adcec443687f0b8d25ec9694da;sf=tgz)

I guess I'll report the regression to the lirc people, hope this helps someone.

---

### Post by LowSky on 2010-11-10
> **nikosapi said:**
> Quick update:

I just tried a mythbuntu 9.04 live cd and my ir blaster works perfectly. So why doesn't it work in 10.10? :(

try copying the lirc config file from the older version and pasting it into 10.10

---

### Post by nikosapi on 2010-11-10
> **LowSky said:**
> try copying the lirc config file from the older version and pasting it into 10.10

All the config files were identical, but I seem to have fixed it for the time being. Thanks for the suggestion.

---

### Post by sdevine01 on 2011-02-05
Thanks for the Tip, fixed my problem too.  Similar situation here, 10.10 broke my home-brew lirc tansmitter.

---

### Post by gregmcc on 2011-02-08
I'm also having problems getting lirc to work with 10.10

I've downloaded lirc-0128802.tar.gz
When I run "./setup.sh && make install"

I get "dialog not found!" 

Where am I going wrong? :(

---

### Post by Gadgetman on 2011-02-13
> **nikosapi said:**
> All the config files were identical, but I seem to have fixed it for the time being. Thanks for the suggestion.
Besides copying config files 10.04, what else did you do to fix the problem?
My Configs are identical to my 10.04 installation (which I still have up and running), yet IRSEND does not work on 10.10. No errors reported anywhere, but the DTR pin does not toggle, and hence my home brew IR Blaster does not work!

---

### Post by SiHa on 2011-02-15
> **Gadgetman said:**
> Besides copying config files 10.04, what else did you do to fix the problem?
My Configs are identical to my 10.04 installation (which I still have up and running), yet IRSEND does not work on 10.10. No errors reported anywhere, but the DTR pin does not toggle, and hence my home brew IR Blaster does not work!

It's been a while since I played with Mythbuntu, but I found I had to ```
sudo dpkg-reconfigure lirc
``` to get my homebrew receiver working whenever I'd done a fresh install. This should sort out the serial port properly (well, it always did for me...)

---

### Post by tegwilym on 2011-03-18
Thanks for the tip!  I had the same problems with Mytbuntu 10.10 and had copied my lirc config files from my 9.04 install.  Nothing worked. 
I installed the older lirc and it worked right away!  took a while to figure that needed svgalib and dialog installed with apt-get.

---

