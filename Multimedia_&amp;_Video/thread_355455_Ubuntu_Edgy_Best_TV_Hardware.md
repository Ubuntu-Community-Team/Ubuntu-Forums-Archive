---
title: "Ubuntu Edgy Best TV Hardware"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by NoVista on 2007-02-07
If I wanted the best quality TV picture available on my computer, the TV hardware to buy would be what?

A little background:

I am a Linux noob of about 8 weeks.
TV cards owned in the past ATI AIW 8500, AIW 9600, and an AIW x800xt agp, which is now my current card, (and not fully workable on Linux, no TV). I always settled on the AIW's for a few reasons, such as:
   1. Tuner/Video card integration on a single agp port.
   2. The AIW's usually offered the best quality TV picture around.
   3. Easy TV recording/scheduling and a great TV Guide in  GuidePlus+ (I'm not afraid to                         admit it).
    
So I need hardware that will let me have a great *[I]managable*[/I] picture that can fill up my Dell 20.1 inch wide-screen LCD (1680/1050). By manageable I mean I can also resize it to any size I want, and move it anywhere on my screen. 

Is the TV card on a motherboard still the best way to go? The industry has also moved into external  self contained tuners that just feed the output to your video card/capture card input. Do these offer better quality?

Lastly, being a Linux noob, I need all around easy installation and setup to get TV running on Edgy. From what I've researched, the  WinTV-PVR-150 or 500 running with MythTV would be a grandma setup, right?

I've been researching all this ever since I have switched over to Ubuntu.
I still am undecided as to what I should purchase/implement.

Advice please .. ..

---

### Post by NoVista on 2007-02-10
Just a bump ..

---

### Post by Shay Stephens on 2007-02-10
I have only been loosely following the whole tv/mythtv thing.  In the next 6 months or so, I hope to setup my own box for it.  The tv cards most talked about are the Hauppauge types:
[http://www.hauppauge.com/pages/prods_pvr.html](http://www.hauppauge.com/pages/prods_pvr.html)

Most common I have seen is the 150 model, but more research would no doubt turn up more.

I found this how-to, but have not tried it yet:
edit: link broken, I am looking for the working link.
edit: Looks like the site got hacked and they lost a bunch of content, including the how to.  The good news is I have a copy of it

**Installing MythTV**
used to be from: [http://tvease.net/support/e107_plugins/content/content.php?content.5](http://tvease.net/support/e107_plugins/content/content.php?content.5)

**Prerequisites**
Now we're almost ready to install MythTV. However, we'll install the MySQL database package first.

```
sudo apt-get install mysql-server 
```

**Myth TV**
Now we can finally install MythTV itself:

```
sudo apt-get install mythtv mythtv-themes
``` 

It will ask you for the root database password. Hit enter if you haven't changed it. The installation will have created a mythtv user. We'll login as him from now in, so set his password:

```
sudo passwd mythtv
``` 

It also makes sense to grant access rights to the mythtv user. To do this, edit the file /etc/group and mythtv to all groups that your original user is in. This will allow him to use sudo, access the cdrom etc. For example:

```
. admin:x:106:garry,mythtv . 
```

Note that mythtv gets created with the default shell as /bin/sh. If you want /bin/bash, then set this in the /etc/passwd file. Now, logout of your X session and login as mythtv at the GDM screen.

**Myth TV Setup**
To configure Myth for the first time, you run the mythtv-setup utility and step through the options:

```
mythtv-setup
``` 

Note that I've cheated and used the MythCentre theme for the screenshots, which isn't the default... it just looks so much nicer!

**General**
All I changed was the TV standard to PAL and the channel-frequency-table to europe-west.

**Capture Card**
Select (New capture card). For a DVB card, change the Card Type to "DVB DTV capture card (v3.x)". It should detect it and show your card details.

**Video Source**
This defines the source of the schedule listings. We'll be using the 14 day radio times guide, which is downloaded via the internet. There's also a guide transmitted over Freeview, but it's only 7 days and contains much less programme information.Select (New video source). Enter a video source name of "uk_rt". Select XMLTV listings grabber to be "United Kingdom alternative". Pressing "Finish" will display an error message. Don't worry, we'll sort this out later.

**Input Connections**
This associates our DVB card with the video source. A good "Display Name" would be "Freeview". Set the Video source to the one we've just defined, "uk_rt".Hit "Scan for channels" and set the correct country. Hopefully, this will find a load of channels and radio stations.

**Channel Listings**
Go here and check you have all the channels you need. If there are any you don't want, uncheck the "Visible" box.

**Testing the Configuration**
Now you can exit the setup utility and start the backend. Note that this will start automatically when the system is rebooted.

```
sudo /etc/init.d/mythtv-backend start
```                              


Check for error messages:

```
tail -f /var/log/mythtv/mythbackend.log
``` 


Now run the frontend as the mythtv user:

```
mythfrontend
``` 

At this point, you should be able to watch TV.  So, that's the basic system installed.

---

### Post by NoVista on 2007-02-11
Yes, I realized the Hauppauge cards are brought up a lot, and that the 150 card even more.
But are they the cards to use to get the best quality picture?

Being an audiophile and to a lesser extent a videophile, I am after a quality TV picture on my computers Dell wides-screen LCD monitor, which has a resolution of 1680/1050. The tuner needs to accept a cable TV input, at minimum (US). AM/FM radio tuner would be nice also.

Thanks for the input on the DVB DTV capture card/Myth install.

Anyone else have some hardware recommendations?

---

### Post by barney_1 on 2007-02-11
@NoVista

If you are a "videophile" then you probably won't be happy with the PVR-150 or it's siblings because you are still recording an analog signal coming in on coaxial cable from your cablebox (or just from your analog cable connection).  This is the kind of setup I have so I'm sorry to say I can't tell you what a better option would be.  But I'm happy with the picture quality I get.  If you really want an archive quality recording of your programs you should purchase the DVD (or HD-DVD, Blu-Ray) versions when they are released.

@Shay Stephens

I've tried several different guides for setting up MythTV.  The one I found to be the easiest and most comprehensive is from the ubuntu wiki:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by Shay Stephens on 2007-02-11
> **barney_1 said:**
> I've tried several different guides for setting up MythTV.  The one I found to be the easiest and most comprehensive is from the ubuntu wiki:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Cool beans!  Thank you for the link, I have updated my list :-)

---

### Post by Jovec on 2007-02-11
I've been loathe to mess with MythTV on my desktop, since all I want to do is watch live TV on my second monitor while I'm doing something else.  I have a Hauppauge PVR-150, and was surprised (due to my ignorance) that it doesn't work with TVTime, since the PVR-x50 line is a mpeg encoder and TVTime won't decode the mpeg stream.  Be careful which Hauppauge card you buy, as a few aren't ivtv driver compatable (IIRC the PVR-150 MCE or something).  You'll want the models with true hardware mpeg encoding.

I didn't try mplayer or xine, but using VLC, I just open the PVR device (I properly configured the ivtv drivers and /dev/video0) and watch the stream.  I change channels via "$ivtv-tune -cXX -d/dev/video0"... /shrug It works

---

### Post by NoVista on 2007-02-12
Thanks Barney. I had that link already. Quality of live TV is what I am after, on my pc, while I am using my computer for other things, in most cases. So you use the PVR-150?

Yes, Jovec, hardware encoding would be a wanted feature also. Taking all the processing off the cpu is a big plus, and certainly the best way to go for PVRing. So when I look at the Hauppauge line, the WinTV-HVR-1600 looks to be the most advanced card? Hardware encoding, and the ability of either analog/digital input. 
And would this card be recognized and easily setup with Myth? The last thing I want to have happen is purchasing something that will not work with Ubuntu.

---

### Post by Jovec on 2007-02-12
> **NoVista said:**
> Yes, Jovec, hardware encoding would be a wanted feature also. Taking all the processing off the cpu is a big plus, and certainly the best way to go for PVRing. So when I look at the Hauppauge line, the WinTV-HVR-1600 looks to be the most advanced card? Hardware encoding, and the ability of either analog/digital input. 
And would this card be recognized and easily setup with Myth? The last thing I want to have happen is purchasing something that will not work with Ubuntu.

Any ivtv driver supported card is probably your best bet.  I'd suggest looking around [http://ivtvdriver.org](http://ivtvdriver.org) for supported cards and maybe read the mailing lists for other people's opinions.

The WinTV-HVR-1600 is not supported under Linux at all according to [here]("http://ivtvdriver.org/index.php/Supported_hardware").   If you go with Hauppauge, be very careful which card, model, and revision you get (again, see the [supported hardware list for ivtv]("http://ivtvdriver.org/index.php/Supported_hardware")).

---

### Post by barney_1 on 2007-02-12
I don't think there is support for ASTC encoder cards under linux yet but I could be wrong.

@NoVista

I actually use a WINTVPP2 encoder card that is much like the PVR-250.  I get this from lspci:
```
00:0b.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
```

It works for me!

---

### Post by Patrick Dixon on 2007-02-13
> **Shay Stephens said:**
> 
I found this how-to, but have not tried it yet:
edit: link broken, I am looking for the working link.
edit: Looks like the site got hacked and they lost a bunch of content, including the how to.  The good news is I have a copy of it
Here's a link that works:-  [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by NoVista on 2007-03-10
Well I settled on the PVR-350.

The install went without a hitch, now on to learn the software side of MythTV.

Initial reactions:

Good enough quality recordings "outta the box."
FM radio not working, have sound, appears to be a common problem, needs a post of its own.
CPU usage is only about 28 percent of my AMD64 3400 when live video is up on the screen.

Thanks again everyone for all the input.

---

