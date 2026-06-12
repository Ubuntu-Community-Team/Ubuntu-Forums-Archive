---
title: "South East of TV settings with a mce pvr-150 Help!!!!!!!!!!!!!!!!!"
date: 2009-03-29
forum: Mythbuntu
---

### Post by chrisginger26 on 2009-03-29
Hi Guys 

This is my first try at installing mythbuntu previously my pc was running winxp mce2005.

I have some experience with ubuntu/xubuntu/kubuntu and so I am not afraid of terminal.

I have burnt a mythbuntu cd and installed it onto my pc (see bottom of post for detailed full specs of pc) to my surprise my wireless adapter was recognised and worked with the restricted drivers straight out of the box and my nvidia graphics card was also recognised and is working well. I installed flash and turned the master channel of sound up on alsamixer to get my sound working. After that I set about looking mythtv set up I changed the folder containing videos to point at my lacie external disks and my video collection all worked along with my pictures and music.

At this point I was really excited as I felt really confident about porting my media center to linux.

My problems have arrived with tuner card it is an hauppauge pvr-150 mce kit I have ( [http://www.ciao.co.uk/Hauppauge_WinTV_PVR_150_MCE_Kit__6637111](http://www.ciao.co.uk/Hauppauge_WinTV_PVR_150_MCE_Kit__6637111)  I think its this one)

It comes with a capture card an mce remote a usb ir blaster and satelite channel changer.

The thing that threw me wast that the remote works fine I can navigate round mythtv but for all my trying I cannot get the capture card to tune in.

I live in Heathfield in east sussex so the freeview signal is pretty poor in windows I had a coxial aerial from my thompson skydigi box going into my pvr-150 and media center found sky on channel zero and configured the guide settings from there I was hoping to be able to do the same.

Mythtv recognises the card and I have tryed tuning it in several different ways and all I get is watch tv flashes black and then back to the main myth tv menu. I tryed following this guide with no luck [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) and I can't get mplayer/xine  to play any tv I also installed tvtime and digital television and they say no tuner device.

Is this some sort of driver issue and how do I set it up for the south of england?

Please help me I'd love to have this running 

thanx chris

FULL SPEC

Asus p5v800 motherboard
pentium 4 3.00ghz
nvidia geforce6200fx
atheros 802.11g wireless adapter
512meg kingston 400mhz ram
hauppauge mce-pvr-150 mce kit

---

### Post by tobiz on 2009-03-29
Why don't you let Mythbuntu setup do the scanning for you?  This is what I've done, I've never had to do anything like the site you reference.  On the desktop drop down menu you should have an entry for 'MythTV Backend Setup, if you go through the options you'll find one to Scan for Channels run that, that's all I do and after about 5 minutes all the channels my card can see from here in West Yorkshire are tuned in.  My experience is there's not too much need to resort to the command line for a standard MythTV set up. Have I had to? Yes, but that was getting HDMI audio working and an unbranded remote.

---

### Post by chrisginger26 on 2009-03-30
Hi tobiz

I understand how to use the backend program from inside applications-settings-mythtv backend set up. This is what I first used to set the system up but whenever I go to watch tv all I get is a quick flash to a black screen and then back again to the "watch tv" option.

In myth tv backend setup

I have the general tab set to PAL 

Inside capture cards there are two options for my card which come up mpeg or anologue they both show my card as recognised in probing (I think thats how its written can't look at the mo my sons watching cbeebies!!). 

In input connections I gave the display name 'tv ' and tryed using europe-west and ireland as there does not seem to be a uk option what did you use ? 

When I go to channel listings it lists a whole bunch of channels as unnamed and nothing works in 'watch tv'!!!

This is what lead me to test my cature card with [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) as I thought it might need drivers to run ?

thanx again 

chris

---

### Post by chrisginger26 on 2009-03-30
Hi guys 

I now realise tha this card is anorlogue and therefore can't recieve a dvb signal am I correct ? 

therefore this guide [http://parker1.co.uk/mythtv_dvb.php](http://parker1.co.uk/mythtv_dvb.php) won't work.

So from the two settings in capture cards i ned to set it to anorlogue not mpeg ?

I was hoping that mythtv would see my 4 anorlogue channels + sky on a 5th channel ?

Can anyone help me with the settings am i going in the right line ???

thanx again

chris

---

