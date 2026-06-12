---
title: "Help Getting Wintv PVR 150 MCE to work"
date: 2009-02-01
forum: Multimedia Software
---

### Post by ricouzuki on 2009-02-01
Hello All

I just Installed Ubuntu 8.10 With all updates and NVIDIA "restricted drivers".

I Have Installed in my PC the Hauppauge WINTV PVR-150 MCE edition which is the "dude im a frickin broke *** mofo" version

I want to watch tv with this card. 

First of all my PC specs:
Brand: HP gray and blue color generation 
model: pavillioneopn some **** like that 
Pentium 4 "Northwood" 1.9Ghz 
512MB PC 2100 DDR RAM
Geforce 2 MX 32MB<--yea baby hot **** right there you know you want it
A keyboard and mouse that says "DELL" on them

Now that Ive listed my PC specs, I will tell you what I have already attempted:

1st I went to this site: [http://www.hauppauge.com/Pages/faq/support_faq_linux.html](http://www.hauppauge.com/Pages/faq/support_faq_linux.html)

it took me to linuxtv.org, from there i compiled V4L-DVB from scratch but got stuck on the make install command. It threw back ERROR 2. Using "The Google"[SIZE="2"](tm)[/SIZE] I discovered that everyone wants to be jerks and not actually explain what that error means to others who have asked so im still not sure what went wrong but I still refuse to follow the normal advice of linux doods, which is to buy better hardware then this piece of **** from the depths of ebay. Instead I went to the other link from the original webpage

[http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page) 
Luckily I did not have to compile, instead that wonderful gift from heaven the Synaptic package manager, was able to come to my rescue and install the software from the second driver site. Still no luck though. Im not sure if its the drivers or the software though. 

Earlier I ran some hardware detection program that was suggested somewhere and it identified the chipset of the card so im not sure if the drivers are installed or not. The first driver site mentioned that the drivers ALREADY COME WITH UBUNTU!! I was like LOL WUT? but unfortunately I still cant watch tv.

I tried installing tvtime and even though it looked very pretty and I really really wanted it to work, it did not. I installed XAWTV but that stuff just had me staring at a blank screen for 30 mins while it went scanning through every frequency at 0.25MHZ PER SECOND!!!! (what a joke) 

Now for the worst part of it all. Installing MYTHTV. Oh my god if there was ever a piece of software that would make you kick your pc out the window and then shoot it with a shotgun from afar and then closely just to make sure it was dead, it would be MYTHTV!!!! 

Ive heard nothing by praise about this software and now I finally get a chance to finally try it, it ends up being a nightmare. I dont want to configure a damn SQL server!! I dont want to sit while my hard drive starts clicking to the beat of a clock!! I dont want to find out that I cant close the process that is causing my HDD to act like this BECAUSE ITS NOT LISTED IN THE PROCESS MANAGER!!! So i finally deleted the damn crap and my problems went away....but still no TV.

So OOOBUNNTOOO community, plaese make sure that the only thing I dislike about the linux community is the crappy color scheme in ubuntu and not also the fact that a tuner card that normally causes random BSODs in windows due to **** drivers does not work in linux.

If you come this far then one more thing:

SOME MORE INFO: 
This card has hardware MPEG2 decoding so that may help solve the puzzle.

 Ricouzuki

---

### Post by ricouzuki on 2009-02-01
comon guys I heards you guys help noobs like me

---

### Post by punx45 on 2009-02-01
you should be able to test the card without extra software getting in the way

cat /dev/video0 > test.mpg 

or pipe it to VLC, mplayer, etc

cat/dev/video0 | vlc

might need to tune the card to a channel first

see here:

[http://ivtvdriver.org/index.php/Troubleshooting#Use_.22cat_.2Fdev.2FvideoX_.3E_test.mpg.22_to_test](http://ivtvdriver.org/index.php/Troubleshooting#Use_.22cat_.2Fdev.2FvideoX_.3E_test.mpg.22_to_test)

i have  the 150 working in a 2.6 kernel, however i rememer reading a while ago that Hauppage switched the chipset on the 150 quietly, and its compatibility was suspect.   in terminal do lspci and look for the listing for the card.   here is mine:

00:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

google the chipset and see if you have a good one or not.

---

### Post by unix1980 on 2009-02-01
Yes, be sure you tune in a channel if you're watching cable or broadcast TV.   Install ivtv-utils, then use ivtv-tune to tune to a channel.  I could never get xawtv to work for me.  I use vlc or mplayer.  I have a satellite dish so I generally have to tune once and then select stations using the sat remote.

You might also want to issue this command to see if there were any problems during bootup:

grep ivtv /var/log/syslog

---

### Post by Macintosh SE on 2009-02-01
I'm not sure if the following will apply to 8.10, but I did this on both 7.04 and 8.04:

1. Install the ivtv-utils package from Synaptic.
2. Go to Terminal and type:
```
ivtv-tune -c 53
```
   Be sure to replace 53 with the number of the channel you want to watch/record.

3. Type in Terminal:
```
totem /dev/video0
```
   This will open Totem with the live broadcast from the channel you just tuned.

4. If the above worked, I can post my shell scripts for watching/recording TV for you to use. The reason I wrote shell scripts is due to the same frustration you are experiencing. I bought this EXACT TV Tuner in December 2007. I tried MythTV, tvtime, etc. None worked. I actually thought my card was broken. Rather, ALL of the GUI tools I tried were broken!

Do not give up. There is a solution (but it is not with GUI programs).

---

### Post by cmargolin on 2009-02-02
I have a Hauppauge WinTV-HVR-950Q and I found this page [http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/](http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/)
useful.

I use Kaffeine as the viewer.  It has a channel scanning utility and a channel selection window.

---

### Post by olangelsa on 2009-04-03
In response to Macintosh SE.

Thank you so much for your advice. It worked like a charm for me.

Could you please post those scripts you are referring to? I would really like to both change channels and record tv by using a bit more automated routines.

I am running Intrepid Ibex and have a Hauppage PVR150. Same chipset as was mentioned by punx45.

Thanks in advance.

---

### Post by saedelaere on 2009-04-13
> **olangelsa said:**
> In response to Macintosh SE.

Thank you so much for your advice. It worked like a charm for me.

Could you please post those scripts you are referring to? I would really like to both change channels and record tv by using a bit more automated routines.

I am running Intrepid Ibex and have a Hauppage PVR150. Same chipset as was mentioned by punx45.

Thanks in advance.

Hi,

I'am developing a small gui to watch and record TV for devices with a hardware mpeg encoder. You can download it [here]("http://home.arcor.de/saedelaere/download_eng.html").
I recommend using 0.8b1 because it offers much more than latest stable release and it is working quite stable. Be sure to read the readme about System Requirements!

Regards

---

### Post by mars76 on 2009-10-18
HI saedelaere,

  Could you pls post the Debian version of your software on your site..

thanks
mars

---

### Post by saedelaere on 2009-10-29
> **mars76 said:**
> HI saedelaere,

  Could you pls post the Debian version of your software on your site..

thanks
mars

There is no special Debian version. Use the source file and install it. Should be no problem, if someone can provide packages I'll be glad to host them :)

---

