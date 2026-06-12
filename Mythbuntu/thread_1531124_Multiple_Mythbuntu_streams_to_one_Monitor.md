---
title: "Multiple Mythbuntu streams to one Monitor?"
date: 2010-07-14
forum: Mythbuntu
---

### Post by adamecook on 2010-07-14
**Multiple Mythbuntu streams to one Monitor?** 			
 			 			 		   		 		 		OK, I am  considered not only a new Unbuntu user, but a new MythTV user as well. 

Issue:
We use Mythbuntu at work to ingest news programs, and I need a way to  monitor the live video feeds from 3 different Mythbuntu boxes ingesting 2  channels a piece (6 channels total) over our internal network for  display on ONE monitor, so that a loss of video feed triggers an alarm.

Question:
Is there a software application or internal Mythbuntu setting, that will  stream the live feed from both tuners to a monitoring  system?

Additional Information:
I am currently trying to use CyeWeb 2.2 from NovoSun to create the  multiple live feed environment, but still have no valid way to tie in  the MythTV feed.

Thanks for any and all insight I can get!!!

Mythbuntunoob

---

### Post by tgm4883 on 2010-07-14
Not entirely sure what you are trying to do, but it doesn't sound like MythTV is the right answer for you.

---

### Post by adamecook on 2010-07-14
I simply (or maybe not so simply) need to be able to monitor the live feeds from my 6 tuners at one time, using one interface, instead of going through and checking the 6 feeds individually once an hour.

---

### Post by tgm4883 on 2010-07-14
I'm not sure if it will help or not, but have you taken a look at [http://www.zoneminder.com/](http://www.zoneminder.com/)

---

### Post by adamecook on 2010-07-14
This looks like a similar application to what I am using now, although I am wary about the stated purposes being for CCTV. I know that a video feed is a video feed, and a long as I can get Mythbuntu to stream it, I should be able to capture it using this type of application, but how do I get MythTV to stream the live feed?

Thanks for your help!

---

### Post by nickrout on 2010-07-16
mythtv is not the solution for you. You can get two streams via PIP but no more.

But it is open source, you could look at the PIP code and adapt it?

---

### Post by adamecook on 2010-07-16
Thanks for your input, all. I was just informed that our project was picked up, so I have been authorized to pick up 300 channels recording 24H/day. MythTV was a good stepping stone, but it looks like I need to design a whole new system.

---

### Post by LowSky on 2010-07-16
300 channels, what the heck are you monitoring?

You really need something a bit more industrial

---

### Post by itlarson on 2010-07-16
Couldn't he run six instances of the frontend, each with it's interface size set to 1/6 of his monitor?

---

