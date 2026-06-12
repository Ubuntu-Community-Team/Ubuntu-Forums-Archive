---
title: "card 1 (type mpeg2ts) is set to start on channel 0 which does not exist"
date: 2016-09-13
forum: Mythbuntu
---

### Post by stroupman on 2016-09-13
I'm upgrading from mythtv running on 12.04lts to mythbuntu 16.04. I have hdhomerun networked tuners. My pc is an HP elitebook 8510w which is the same one I have been using with the 12.04 set up (which works). The menus have changed a bit from 12.04 to 16.04 so I have been using the configuration guide at [https://www.mythtv.org/wiki/Mythtv-setup](https://www.mythtv.org/wiki/Mythtv-setup). After completing configuration and escaping out of backend setup, I am confronted with message "card 1 (type mpeg2ts) is set to start on channel 0 which does not exist." I get the same message with cards 2 and 3. I can't figure out where channel 0 is coming from.

---

### Post by khPWXxF on 2016-09-15
I think there is a setting in backend setup.  Called something like starting channel.
Set it to a channel which is always transmitting. 
Phil

---

### Post by stroupman on 2016-09-15
> **khPWXxF said:**
> I think there is a setting in backend setup.  Called something like starting channel.
Set it to a channel which is always transmitting. 
Phil
It is set to channel 3 which is our local PBS. In the frontend I get a message when I try to enter Program Guide: "{You don't have any channels defined in the database. The program guide will have nothing to show." In setup when I scan channels, it stops at channel 69 I have waited at least 30 minutes and nothing more happens. I always click on finish and it seems to terminate ok. But at the top of the dialog window it still indicates that it is scanning. I have run mythfill which seems to terminte ok. I don't know what all of this indicates.

---

### Post by stroupman on 2016-09-16
I started scan in setup (determined to let it run all day if necessary). To my surprise it blew passed channel 69 and ran to completion. I ran mythfill and started the frontend. Live tv did not work. I looked at the program guide which showed 9 strange looking channels like this: 33-1, 42-1, 92-128, 92-131, 92-132, 92-137, 92-138. There are no program schedules in the guide. I can view tv using the hdhomerun  gui where I see the channels with normal numbers.

---

### Post by stroupman on 2016-09-17
OK I still have the original problem with the channels starting at zero. But I found a big mistake. In video sources I selected "north america (data direct) xmltv" Should have been "north america (data direct) internal" Should have selected retrieve not scan. Now my channels are correct and I have actually recorded something. Still don't have live tv or sound, but I think that may be a separate investigation. If anyone can figure out why I still get those messages about the channels, I'd really like to know.

---

