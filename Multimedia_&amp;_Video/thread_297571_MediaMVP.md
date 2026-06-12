---
title: "MediaMVP"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by blackest_knight on 2006-11-11
Hi
The MediaMVP from haupage is a thinclient device with the single purpose of delivering Media (audio, video and pictures to your TV from your network)

it is fairly small cheap and comes in wireless and wired versions and it runs linux. 

Using it under windows is pretty straight forward a simple install , search for media and its ready to go when it turns on it looks for its boot server (the windows box you installed the software on) and downloads a file called dongle.bin This is its O/S from then on it communicates with the window box letting you choose what you want to play via the remote.

It works its easy and providing you don't mind running a windows box on your network and the ugly interface haupage have put on it that is all you need to do. I have found at least 3 versions of the Windows Software each a small improvement on the last. 

But it runs Linux so why do I need to run a Windows Box to serve Media to it and boot the Device? The answer is you don't but its a lot easier if you do. 

After several hours last night I came to the conclusion working without windows isn't easy with this device and the information is confusing non ubuntu specific and is likely to drive you nuts rather than give you a working system that your granma could use.

MVPMC is an alternative to the haupage software. The Dongle.bin file haupauge supply is replaced by the mvpmc version which looks to be much nicer more configurable and so far I haven't been able to use it.

I did get it loaded thou.

First lets look at what needs to happen to get this mediamvp up and running.

when it turns on the device trys to get an ipaddress find a server with its os and downloads and boots into that and then gets the media lists from the media server and plays anything you choose.

ok the boot server,
you can get your ubuntu box to act as the boot server, however its very hard to do. 
you need to download and install a dhcp server and set things up so when the MVP comes looking your ubuntu box serves it the OS it needs.
The big problem here for me is that apart from being hard to setup is that my router is my dhcp server and you need to stop it assigning an IP for both your boot server and the mediaMVP.

well theres no effective way on my belkin router to tell it not to give an ip address to the mediamvp. you can stop it acting as a dhcp server and then use your ubuntu box as a dhcp server for your network or manually set IP addresses on your other boxes. 

Personally I don't want the grief, I don't think it matters who hands out the dhcp lease as long as everyone gets an ip address. 
remember this is just to boot the mediamvp once it is booted it shouldn't need rebooting often. 

Ok so for me I did it the quick and easyway
copy the mvpmc dongle you downloaded precompiled from sourceforge to the windows box where the haupage software is installed and replace thier dongle.bin with your mvpmc dongle (renamed dongle.bin)

pull the power from the mediamvp and then plug it in again and the mediamvp will find the bootserver and boot the mvpmc software.

now we have mvpmc running on the mediamvp. hoorah no more electric blue.

no dhcp server, boot server headache just works. (probably could do this in a vm to save having an xp box do this).
 
well thats as far as i have got for now 
Mvpmc installed on the mediamvp using the haupage software to load it.

[http://www.rst38.org.uk/mediamvp/mvpserver.html](http://www.rst38.org.uk/mediamvp/mvpserver.html)
looks interesting  probably will act as the media server for the mvpmc 

good luck and sorry for the long ramble hopefully other people will contribute to this thread.

---

### Post by MJN on 2006-11-18
Timely post there Black_knight..... I've got a MediaMVP and have yet to get round to starting the endless nights that it'll no doubt need to get up and running with my Kubuntu server.... and this is despite me getting it as a Christmas present 11 months ago!

I'll hopefully start later this week - you have raised a good point about using an XP machine to get the required firmware on the box - my router (D-Link DI604) also appears to only provide an all-or-nothing DHCP solution and for various reasons I don't want to use my server for the DHCP function (not yet anyway) so your 'workaround' sounds useful.

Have you got any further with your setup? Hopefully if I can find some time soon I'll start messing around with it and will contribute my findings here.

Mathew

P.S. I initially started a battle with MythTV but have all but given up.... Sometimes I really miss Windows...

---

### Post by bluesxman on 2006-11-21
> **MJN said:**
> 
P.S. I initially started a battle with MythTV but have all but given up.... Sometimes I really miss Windows...

I've just stumbled upon [this guide]("http://www.parker1.co.uk/mythtv_ubuntu.php").  I haven't tried it yet, but it looks straightforward!! Once I get myth sorted, I'll have a go with my MVP - if I have any luck I'll post back.

---

### Post by MJN on 2006-11-21
Looks good..

Unfortunately for me I'm using Breezy on my server and whilst I can afford to upgrade to Dapper without much concern pushing it to Edgy would be too much.

I'd be interested to hear how you get on nevertheless.

Mathew

---

### Post by bluesxman on 2006-11-22
Sorry, didn't spot you kubuntu version when I posted...

Myth installation was a piece of cake! Hopefully, I'll tackle the MVP tonight.

---

### Post by MJN on 2006-11-22
That's good to hear anyway... By the time I get round to dabbling with Myth/MediaMVP Edgy will probably in maintstream release anyway! ;)
 
Do keep us informed - I know both Myth and MediaMVP are real head scratchers for a hell of a lot of people. Indeed, the problems seem to be so severe yet unclear that people tend to given up as they're not even sure where to start to ask for help!
 
Mathew

---

