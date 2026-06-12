---
title: "Mythbuntu PVR500 and DishNetwork"
date: 2007-10-17
forum: Mythbuntu
---

### Post by karlec on 2007-10-17
I have finally decided that Mythbuntu will be my "distro" of choice and would like to know if my setting will work.  I have DishHD and a PVR500.  I have tried several distros with MythTV so far with no luck, I have not been able to make it work.
I would like to know if my current setting will work or do I need to buy a different tuner right now?  For now all I need is to have SD on my Myth box and I have not been able to do so.  Can someone please point me in the right direction to get things working?

Appreciatively,
Karlec.

---

### Post by tgm4883 on 2007-10-17
Well you will need a way to change channels on the dish box, whether you have the dish box do this or have a blaster do it (or manually do it, ugh) it should work.  

Basically the PVR-500 will stay on a single channel (like 3, think of VCR's and TV's), and the box will always transmit on that channel, and will tune itself.

---

### Post by karlec on 2007-10-17
I have a usb-uirt ir blaster for the channel changing, however being a newbie I have not been able to find comprehensive directions on how to actually connect the system to my "dish-source" to be able to watch tv or record anything.
I have tried a lot of different combinations so far without much luck (splitting the signal, connecting tuner from the receiver etc...).  So my conclusion (again keep in mind that I'm a newbie) was that maybe I got the wrong tuner.  That is why I need to know if the tuner-card is ok and also I need some serious directions.

Thanks.

---

### Post by stevetv on 2007-10-18
what are the video outputs from the set top box?  if its coax, svideo or composite, then youre pvr will be fine.

if its component, or some digital connection to go into a modern tv.. then youre life will become more complicated.

like tgm said.. you should think of connecting your settopbox to mythtv the same as connecting you vcr to your tv.  substitute the vcr for the set top box, and the tv for the input into the tuner card.

after the settopbox is connected, you'd just need to turn it on, set it to a channel, and then go into the backend setup and scan for channels.  you'll only get one channel.. which will be the channel that picks up the signal been input from the settopbox.

you can watch tv now.. but you'd have to change the channel manually via the settopbox.  a nicer way is to get mythtv to change the channel on your settopbox for you..

google "ir blaster" and "mythtv" for some guides.

heres one.  [http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV](http://www.mythtv.org/wiki/index.php/Using_an_IR_Blaster_with_MythTV)

---

### Post by karlec on 2007-10-26
Ok,  I have made some headway, at least one tuner is working now.  I have many other issues (unable to record from guide, remote not working, out of focus screen resolution on my LCD,etc...)
I need to get the second tuner on the PVR500 to receive a signal before I try to resolve the other problems.  I am making the assumption that I should be able to receive a signal on tuner 2 just like I do on tuner 1, it is not working out that way so far.  
I have tried to test tuner 2 manually by running the following (my connection is through compposite):
```
v4l2-ctl -i 4 -d /dev/video1
```
I have cycled through composite 1 and 2 for /dev/video1, I have manually set/changed the channel on the tuner to 3, 4 using IVTV-TUNE but there is no indication of received signal like the one received for /dev/video0.

This is definitely an interesting learning experience!:popcorn: Any help is appreciated,  thanks.

Karlec

---

### Post by karlec on 2007-10-26
Wow, not even one response:(

---

### Post by stoobers on 2010-01-11
Hi, I have a question:

I am building a mythbuntu device.  It can play back the channel that I set the box to.  My ir blaster and receiver will be showing up in the mail shortly.  When I look at the part to manually schedule a recording, it gives me the choice of channels 3 or 4.

The problem:
Only two channels are listed.

My questions:
How will the blaster know what channels I want to switch to?
How do I sync up my blaster with mythbuntu so I can tell it to record channel "107" at a certain time and then have it do so?

I think I can figure out how to make the blaster and receiver work, but how do I make mythbuntu able to record from its interface when there are only two channels (of which only channel 3 is used)?

---

### Post by pilesofspam on 2010-01-11
Stoobers:  these threads are very old and more or less unrelated to what you want.  This causes a problem when somebody (me in this case) searches the forum for a similar problem and turns up all this useless info.  Start a new thread!

---

