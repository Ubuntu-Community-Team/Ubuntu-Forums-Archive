---
title: "Setting up Dish Network with MythTV"
date: 2009-10-05
forum: Mythbuntu
---

### Post by Jeconti on 2009-10-05
I think I already know the answer to this, but I'll ask anyway to see if someone has thought of something I haven't.

The apartment I just moved in to comes with Dish Network and a STB provided. My Mythbox has a Happauge HVR-1600 card inside. Is there any way to make this work?

---

### Post by stonebit on 2009-11-16
I sure as crap hope so! This is what I'm trying to do right now! Did you get it setup? I am using the HP 1600 and DishNet too! I'm new to Myth, so i'm having a rough time getting it up.

---

### Post by tgm4883 on 2009-11-16
> **stonebit said:**
> I sure as crap hope so! This is what I'm trying to do right now! Did you get it setup? I am using the HP 1600 and DishNet too! I'm new to Myth, so **i'm having a rough time getting it up.**

They have a little blue pill for that ;) (sorry, couldn't resist).

To use MythTV with an STB, you will need to do 2 things

1) You will need to use an IR blaster to change the channel on the STB

2) You will need to use an analog tuner to record from the STB

---

### Post by neuronworld on 2011-03-17
I have  the same setup needed to be done. It will be great for talented members to put the detailed info on how to setup. I like this article from Andrew - [http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#comment-202](http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#comment-202) but I need little more detailed as I am getting stuck on channel retrieval.
I setup as mentioned by Andrew. I am stuck at setting up video sources and setting up schedulesdirect info. I don't get channels and it  always say no channels. I added lineup on schedulesdirect website.

---

### Post by LowSky on 2011-03-18
> **tgm4883 said:**
> They have a little blue pill for that ;) (sorry, couldn't resist).

To use MythTV with an STB, you will need to do 2 things

1) You will need to use an IR blaster to change the channel on the STB

2) You will need to use an analog tuner to record from the STB

You already have a HVR-1600 it can tune in by analog (480i). The other option is to get an Haupauge HD PVR and record High Definition.

Also depending on the STB you can change channel (and maybe record) over Firewire)

> **neuronworld said:**
> I have  the same setup needed to be done. It will be great for talented members to put the detailed info on how to setup. I like this article from Andrew - [http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#comment-202](http://andrewmanugian.wordpress.com/2009/07/26/andrewsmythtvguide/#comment-202) but I need little more detailed as I am getting stuck on channel retrieval.
I setup as mentioned by Andrew. I am stuck at setting up video sources and setting up schedulesdirect info. I don't get channels and it  always say no channels. I added lineup on schedulesdirect website.

This stuff might help both of you

Type in an external channel change command to learn more about those see this...
[http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat](http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat)
for direct tv channel changing I found this
[http://www.mythtv.org/wiki/Controlling_DirectTV_D11_via_USB](http://www.mythtv.org/wiki/Controlling_DirectTV_D11_via_USB)

this from mythtv terms on the backend
[http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend)

setting up the system
**[http://www.mythtv.org/wiki/User_Manual:MythTV_structure](http://www.mythtv.org/wiki/User_Manual:MythTV_structure)**

hope those help

---

### Post by neuronworld on 2011-03-18
Thank you LowSky. I setup as mentioned. I am  getting hard time **_CONFIGURE MYTHTV BACKEND_: **especially the capture card, video sources and input connections. 
I bought Hauppauge HVR-1600. It came with IR blaster and remote.
I have [DISH Network 311 Receiver]("http://cgi.ebay.com/DISH-Network-311-Receiver-/320664438410?pt=LH_DefaultDomain_0&hash=item4aa917068a")
I installed Mythbuntu 10.10.
I signed up for schedules direct.

After intallation done. I see /dev/video0 for all my input devices - ATSC, NTSC and svideo1.
I am confused there it gives /dev/video0 for all and Andrew said to give /dev/video1 for svideo1 which it doesnot allow.
My goal is 
1. to get my mythtv to show me my dish channel. I can start with changing channel on dish remote.
2. watch Live TV by changing channels on dish remote.
3. record shows by changing channels on dish remote.
4. setup channel changing script and make IR blaster control my dish receiver.
5. watch hulu on mythtv.
6. setup dumping my personal media (audio, video, pictures) and watch from outside my home. Like Slingbox.

Being set my goals. Started working on first goal.
1. Followed [http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat#Svideo_or_Composite_from_the_STB](http://www.mythtv.org/wiki/Connecting_Tuner_Card_To_Cable_Sat#Svideo_or_Composite_from_the_STB) to setup 


[LIST]
[*] Set up your lineup using Data Direct or other **Done**
[*] run the [mythtv-setup**   Done**]("http://www.mythtv.org/wiki/Mythtv-setup")
[*] Add your capture card if you have not yet done so **Done**
[*] Create a video source and connect it to your channel lineup which includes the channels you want from the STB [B]Done I think I made one mistake starting channel also I put as 3. Is that a problem? I didnot use any channel script. For goal 1 it is ok
[/B]
[*] Go into Input Connections. Look for the Svideo in or Composite in for your card (see pictures above).I am confused as it shows all as vidoe0 and andrew says to put video1
[*] Select the input and configure. You will need to add the channels from data direct, and also set the channel change command. [B]Done. I don't need for goal 1. I did the schedules direct userid and password.
[/B]
[/LIST]
When I say scan for channels. It says failed to get channels.
When I say Fetch from listing source (don't know the difference). It says failed to get channels.

This is where I am stuck.
By the way Going with HD PVR is not an option as I have basic dish receiver and no HD channels. I might get it in future if my mythtv is works well.

---

### Post by rhpot1991 on 2011-03-18
Any Sattelite setup should be using [Hauppauge HD PVRs]("http://www.amazon.com/gp/product/B0018LX0DY/ref=as_li_ss_tl?ie=UTF8&tag=baablogicnet-20&linkCode=as2&camp=1789&creative=390957&creativeASIN=B0018LX0DY") for their tuners.

---

### Post by neuronworld on 2011-03-19
Please help me understand the function of HD PVR compared to HDPVR 1600. They both seem to me as High Definition Personal Video Recorders. HD PVR looks like an external product where as HDPVR 1600 is an internal one.  I tried a similar USB kind of one (WinTV-HVR-950Q) external. It didnot work and so I got HDPVR 1600.
 
Anyways coming to my point - I don't have HD content on my Dish network. I have basic TV. I want to get it up running with my mythbuntu install.

---

### Post by tomgra73 on 2012-01-23
Hello all I am hoping someone can help me or point me in the right direction. I had my Hauppauge 2250 working fine, but the video quality was horrible from my HDTV. I moved to the Hauppauge HD PVR. I am not sure how to connect this or get it to scan channels. I have component cables from my cable box to the hauppauge hd pvr and the usb cable from the hauppauge hd pvr to the pc and hdmi from cable box ot the tv. As you can see below when I run modinfo hdpvr my hauppauge is found. But when I set the card to H.264 HDPVR my Hauppauge is listed and I am not able to scan any channels. Why is this happening?


```
filename:       /lib/modules/2.6.38-13-generic/kernel/drivers/media/video/hdpvr/hdpvr.ko
description:    Hauppauge HD PVR driver
author:         Janne Grunau
license:        GPL
srcversion:     B900EE1C8C22D2BAE7E5F93
alias:          usb:v2040p4903d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4982d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4902d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4901d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2040p4900d*dc*dsc*dp*ic*isc*ip*
depends:        videodev,v4l2-common
vermagic:       2.6.38-13-generic SMP mod_unload modversions 686 
parm:           video_nr:video device number (-1=Auto) (array of int)
parm:           hdpvr_debug:enable debugging output (int)
parm:           default_video_input:default video input: 0=Component / 1=S-Video / 2=Composite (uint)
parm:           default_audio_input:default audio input: 0=RCA back / 1=RCA front / 2=S/PDIF (uint)
parm:           boost_audio:boost the audio signal (bool)

```

---

### Post by nickrout on 2012-01-24
Have you read the instructions?

[http://www.mythtv.org/wiki/HDPVR](http://www.mythtv.org/wiki/HDPVR)

---

### Post by joker35 on 2012-02-05
With HDPVR you don't scan channels as you will connect to a receiver using one of the inputs on the HDPVR. Being in US I use Scheduledirect to provide me with the channel line-up offered by my satellite service provider.

---

