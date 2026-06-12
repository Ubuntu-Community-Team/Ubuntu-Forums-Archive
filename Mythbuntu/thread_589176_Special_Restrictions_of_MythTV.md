---
title: "Special Restrictions of MythTV?"
date: 2007-10-23
forum: Mythbuntu
---

### Post by jabagawee on 2007-10-23
I'm gonna ask a really dumb question, so those of you who are infinitely smarter than me may want to resist the urge to scream at the idiot posting. In my area, we receive television through coax cable from the cable company. However, the company forces us to rent a small box, with which we tune to channel 3 on the set and then change channels on the rented box with a proprietary remote. If I go with a HDHomeRun or any tuner, will I need one of these cable boxes right before my tuner? (eg. Company-Coax-Box-Cable-Tuner)

Help! I'm really confused.

---

### Post by tgm4883 on 2007-10-24
well the HDHomerun will only tune unencrypted and drm free channels, so it really depends on if that is what is being broadcast.  Are you able to tune any channels with just your TV?   What country do you live in?

---

### Post by jabagawee on 2007-10-24
Without the cable box, a TV can get channels 1-99. I live in the US and use Time Warner Cable. However, I really want channels 100-999 (or whatever I have)/

---

### Post by tgm4883 on 2007-10-24
Ok, then for that, you will probably need to stream via firewire.  You may be able tune the other channels with a HDHomerun, although it kinda depends on how it is being broadcast.  

You can check which channels you would be likely to stream by doing what the wiki says.  Instead of going to D11, you go to D5 or D6 I believe.  What you are looking for are 2 settings.

Copy Free
CC (or is it CCI)

You want both of these to read either Free, 0x0, 0, none, etc.  Basically the equivent of no.  You will have to do that for every channel you want to know about.

From the Firewire Mythtv Wiki
> On the 62xx STB, you can check for an active connection through the diagnostic mode. Make sure the firewire cable is connected and power on the STB and the TV attached to it. Press the Power button to power off the STB and then quickly press and hold OK/SELECT on the STB remote. A diagnostic screen will appear. Using the STB remote, arrow-down to D11 Interface Status" and press OK. There you will see the status of the firewire port (labeled "1394 ports") and whether or not it is active ("1"). If it shows "0", power the computer down, switch the firewire cable to the other port on the STB and try it again.

---

### Post by jabagawee on 2007-10-24
Wow, all of these big words hurt my head. I'm only 14, for Pete's sake. :P 

Let's just say I want to record all available channels. How would I go about doing that? Hint, I would like to use the HDHomeRun for this.

Also, for another question: Do I need a video card for my backend? Do I need one for my frontend? What if I transcode my recordings once in a while? Will a video card help with that? If it does, tell me what video card I need as a minimum, and what video card I need to properly transcode video in a non sluggish manner (meaning that it takes a decent amount of time to encode a 30 minute show to xvid, etc. (hopefully less than 5 minutes, is that reasonable?)).

---

### Post by jabagawee on 2007-10-28
*bump* anyone?

---

### Post by rusty0101 on 2007-10-30
> **jabagawee said:**
> Wow, all of these big words hurt my head. I'm only 14, for Pete's sake. :P 

Let's just say I want to record all available channels. How would I go about doing that? Hint, I would like to use the HDHomeRun for this.

The easiest solution is to set up SchedulesDirect for your local digital cable service. Do a get of the channel lineup and schedule. Now select 'Watch Live TV' and start surfing for working channels. Make a list of those channels you can can watch. Now go back to the channel editor and delete those channels you can not watch. Do the same with your sources in Schedules Direct. 

One of the problems that I've had with this is that if I tune to a channel that I can not watch on the HDHomeRun, I encounter various errors. That's why there are instructions that say how to find out if a channel is encrypted or not ahead of time.

> Also, for another question: Do I need a video card for my backend? Do I need one for my frontend? 

Only if you want to watch anything you record. I can envision building a bunch of back ends without video cards, but front ends or even back ends with front ends that are going to be used do need a video card to make it possible to watch recordings, etc.

> What if I transcode my recordings once in a while? Will a video card help with that? 

Generally transcoding is done in software. It may be able to use hardware decoders and encoders, but at the moment that is fairly expensive hardware. I don't know of any specific video cards that are handy for this. 

>  If it does, tell me what video card I need as a minimum, and what video card I need to properly transcode video in a non sluggish manner (meaning that it takes a decent amount of time to encode a 30 minute show to xvid, etc. (hopefully less than 5 minutes, is that reasonable?)).

If you go through the threads, you'll see that there are a variety of 'minimums' that are needed for doing various things. As an example, the recommended minimum processor speed for watching HDTV content is 3Ghz. You can get away with a 2.66 Ghz processor if you have an nVidia 6200 or better video card, but it's really pushing such a system.

The real minimum for a video card is that it can use the capabilities of whatever you are using as a display system. If you have a projector that does quad hd resolution, you will need a video card that will drive that. If you have a display that does 1280x768, the requirements for a video card will usually be significantly less.

I know one family who built a back end client system that pulls HD content video off the back end, transcodes it, then puts it back on the back end, so they can watch their shows without having to upgrade all of their front end systems. I have not asked how they are doing that, just relating that it is possible. I presume that you don't have the resources to add a computer to your system just for that however. If you do, I would recommend using gigabit ethernet to connect the two so that your network doesn't become the primary bottleneck.

Your experience will vary from mine, and those about me.

---

### Post by jabagawee on 2007-10-30
Okay, so now I see how to receive unencrypted channels throught MythTV. However, there may be instances where I want to watch/record the encrypted channels. My question is: how does one do that?

Edit: After much surfing across Google and documentation pages, I found out about LIRC. I think this may be the solution to what I need. Anyone got a tutorial on how to get it wokring?

---

### Post by rusty0101 on 2007-10-30
Don't know of a good way to record from encrypted channels. Legal precedence in the US currently states that even pointing to ways to bypass copy controls is illegal as well. Additionally the systems in use outside of the US are not often found in the US, and vice versa. I'm not passing judgement on the opinion. It's just the way things are.

The question regarding LIRC is up next. If you are looking to use it to control a cable box, you need what is called an IRBlaster. Some of the most common ones plug into a serial port. You then use irsend to send characters and commands to the irblaster. There are a few scripts that simplify how that happens. Esentially you edit the script or a configuration file identifying the port the irblaster is on, and what device you are controling with it. You then modify the setup of mythtv to tune to channels by setting your capture card (hdhomerun in your case so far) to channel 3 (or 2, or 4, whichever is available and usable.) MythTv then tunes to the appropriate channel by sending the necessary channel information to the cable box.

The down side to this is that in almost all cases the output of the cable box is going to be an analog signal, or possibley through a firewire port. As a result the hdhomerun box will not be of much use (it only handles digital channels not analog.) Also many cable providers and content providers will limit the quality of the signal being sent if it is possible that someone will be capturing the output. If the cable box doesn't recognize the device that is attached via firewire, or is recognized as a recorder or pc, then instead of sending a 1900x1080 stream across the firewire interface, it sent at 800x480, or some other lower resolution.

That's not to say that the output isn't better than you will get off analog TV, just that it is not HD.

---

### Post by jabagawee on 2007-10-31
I actually don't plan on watching HD any time soon anyways. Analog quality would be fine by my standards. So what I should be doing would be to: hook up an IRBlaster from MythTV to the cable box, find a tuner card that accepts an analog signal, configure MythTV to change the channel right before a scheduled recording and start recording?

Does that sound right?

---

### Post by rusty0101 on 2007-11-02
That sounds about right. Though as noted if your cable box has a firewire out port, you may be able to use that with a firewire card, and no need to use either an irblaster or a capture card. Teh big advantage of that is that anything you can watch on the cable box would be available at a bit better resolution than through a capture card.

That said, I've been pretty happy with the PVR-250 cards. I've heard pretty good things about the 150 and 500 cards as well. Before getting a usb interface receiver, check the various forums for information on it. Individually they may be less expensive, but if they are not supported, it doesn't matter.

Have fun, and good luck.

---

### Post by jabagawee on 2007-11-02
[http://www.timewarnercable.com/nc/products/cable/firewire.html](http://www.timewarnercable.com/nc/products/cable/firewire.html)

I found this after a bit of searching. Anyone care to tell me what this means to me? The DTCP DRM scheme sounds bad and incompatible with Ubuntu. It seems that I can only get FireWire through the HD service, which I don't plan to get. I'm getting really confused here.

---

