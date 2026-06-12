---
title: "First install - very confused - 9.04 mythbuntu"
date: 2009-08-12
forum: Mythbuntu
---

### Post by HW_Hack on 2009-08-12
Been doing Linux for awhile - but this video stuff is totally new to me.

-initial install is complete
-hauppauge 1600 is detected
-I have a schedules direct account and a line-up chosen
-I've got the MCE compatible remote working
-I'm hooked up to our basic cable feed
-I'm hooked up to our TV via svideo

At this point I'm pretty clueless on how to proceed in an orderly fashion to config this thing. In the sticky threads I found this link
[http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user)

But am a bit confused on if I need to do all the stuff posted below ?
[http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user)

Or do I just start configing the back end etc.

Is there a general setup flow for mythbuntu ?

I don't want to hash-up this install by just randomly doing stuff

THANKS

---

### Post by dano1 on 2009-08-12
configure backend first, then frontend. i use jya's repos for updates:

deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) intrepid release

---

### Post by klc5555 on 2009-08-12
> **HW_Hack said:**
> Been doing Linux for awhile - but this video stuff is totally new to me.

-initial install is complete
-hauppauge 1600 is detected
-I have a schedules direct account and a line-up chosen
-I've got the MCE compatible remote working
-I'm hooked up to our basic cable feed
-I'm hooked up to our TV via svideo

At this point I'm pretty clueless on how to proceed in an orderly fashion to config this thing. In the sticky threads I found this link
[http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user)

But am a bit confused on if I need to do all the stuff posted below ?
[http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user](http://www.mythtv.org/wiki/User_Manual:Initial_Installation#Creating_the_mythtv_user)

Or do I just start configing the back end etc.

Is there a general setup flow for mythbuntu ?

I don't want to hash-up this install by just randomly doing stuff

THANKS

The link text is intended for (some of) those who have (maybe compiled and) installed mythtv on top of some full-blown Linux distro and now want to semiautomagicalize it at startup for a dedicated Home Theater.  

Having installed Mythbuntu, all this has already been done for you. You mostly just need to do the backend setup. As described in either the relevant section of the mythtv wiki here: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

or with screenshots in the spiffy Mythbuntu installation pdf here: 

[http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf](http://www.mythbuntu.org/documentation/mythbuntu_8.10_installation.pdf)

It hasn't changed between 8.10 and 9.04.

In Capture Devices/Input Connections sections, setting up the digital side of the 1600 _may_ end up being just a standard dvb tuner setup, if your signal strength is strong enough. (Cross your fingers.) 

If you set up the analog half of the card, there is a trick: the analog tuner is an MPEG-2 type card, but sometimes Myth will not let you add it that way --it claims the card cannot be opened. But, if you instead add the card as a standard V4L analog card and save the setting, you will then be able to reopen this screen in Capture Devices, and re-edit the screen to MPEG-2 card, and now`the MPEG-2 configuration will save correctly. 

One of the quirks of this card and its driver that sometimes make you think your head is about to explode.

---

### Post by HW_Hack on 2009-08-12
THANKS MUCH FOR THE QUICK RESPONSES !!!!!

Got a few things to do and will tackle this later in the day.

Question on the 1600 --- should I be connecting the cable feed to the NTSC (analog) input or the ATSC input ??

---

### Post by klc5555 on 2009-08-12
> **HW_Hack said:**
> THANKS MUCH FOR THE QUICK RESPONSES !!!!!

Got a few things to do and will tackle this later in the day.

Question on the 1600 --- should I be connecting the cable feed to the NTSC (analog) input or the ATSC input ??

You have to connect to the input that corresponds to the type of channels you're trying to receive.

If it's like most cable is nowadays, and you want to receive the freely provided clear QAM digitals along with the smattering of legacy analog stations that haven't been nuked yet by your provider, you'll have to connect to both inputs. You'll need a 2-way splitter. 1600 quirk number two.

---

### Post by dano1 on 2009-08-13
forgot, when configuring the 1600 analog side configure as mpeg, exit, and reconfigure as mpeg2. Digital will show as samsung xxx dvb tuner. i have also updated v4l drivers just coz ;).upgraded firmware also. 

see this for 1600 install:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)

card works well for me now after getting over the linux/myth learning curve. Any other questions and i'll try to help.

danny

forgot to mention avenards repos are geared towerd nvidia graphics cards, otherwise use weekly builds in the sticky.

---

### Post by HW_Hack on 2009-08-13
Dano - Thanks for the help !  Making good progress 

-channel line up is working
-able to watch TV -- (no audio yet)
-a couple of test recordings worked fine

Also have a minor display size issue - the image being sent to the TV is just a hare too big so some of the info at the edges is not viewable 

Plan to hack some more on the 1600 and get audio working - then try and get the display tweaked. At which point I will nuke the drive and do a fresh install then add the known setup tweaks

---

### Post by HW_Hack on 2009-08-14
Thanks for the help in this thread - and to the whole community as I did many helpful searches.

I was able to watch and record last night but the audio was barely audible and had a loud hum. Tried several things with no luck - was using on board audio on a fairly new ASUS MB. 

So I nuked the old install  and popped in a trusty SoundBlaster card - went thru the setup and its working. 

Will no doubt have some questions as I do some minor tweaks and try to get mythweb working.

Or is there a better way to view web content (streaming etc.) on mythTV ?

---

